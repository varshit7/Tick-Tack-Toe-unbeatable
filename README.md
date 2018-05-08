
#include<iostream>
using namespace std;
// player O computer X
char t[3][3];
int check(int);
void ai();
void display()
{
    cout<<"\n";
    for(int i=0;i<3;i++)
    {
        cout<<"\t\t\t";
        for(int j=0;j<3;j++)
        {    cout<<t[i][j]<<" ";
            
        
        }
        cout<<"\n";
    }
}
int cou;
int main()
{
    
    cou=0;
    int num=1,choice,temp=0;
    for(int i=0;i<3;i++)
    {
        for(int j=0;j<3;j++)
        {
            t[i][j]= num +'0' ;
            num++;
        }
    }
    display();
    do{
        int temp=0;
        int i=0,j=0;
        cout<<"\n\t\tEnter a position to mark: ";
        cin>>choice;
        if(check(choice)==1 || choice>9 || choice <0)
        {
            cout<<"\n Invalid input";
            continue;
        }
        cou++;
        
        for(i=0;i<3;i++)
            for(j=0;j<3;j++)
            {
                temp++;
                if(temp==choice)
                {
                 t[i][j]='O';
                    break;
                }
            }
        display();
        if(cou==5)
        { cout<<"\n\t Game over...Not bad for your age. Haha\n"; exit(0);}
        cout<<"\n\t\tComputers turn";
        if(cou==1)
        {
            if(choice==5)
                t[2][0]='X';
            else
                t[1][1]='X';
            display();
        }
        else if(cou==2)
        {
            if(t[1][1]=='O' && t[0][2]=='O')
            { t[2][2]='X'; display();}
            
            //player 2 corners
            else if((t[2][0]=='O' && t[0][2]=='O') || (t[0][0]=='O' && t[2][2]=='O'))
            { t[1][0]='X'; display(); continue; }
            //player 1 corner one edge
            
            //2 edges
            
            
                else if(t[1][0]=='O'&& t[2][1]=='O'){ t[2][0]='X'; display(); }
                else if(t[2][1]=='O'&& t[1][2]=='O'){ t[2][2]='X'; display(); }
                else if(t[1][0]=='O'&& t[0][1]=='O'){ t[0][0]='X'; display(); }
                else if(t[0][1]=='O'&& t[1][2]=='O'){ t[0][2]='X'; display(); }
                else //if(t[2][0]=='O' || t[0][2]=='O' || t[0][0]=='O' || t[2][2])
                {
                ai();
                }
               /* else if(t[0][0]=='O'){ t[2][2]='X'; display(); }
                else if(t[0][2]=='O'){ t[2][0]='X'; display(); }
                else if(t[2][0]=='O'){ t[0][2]='X'; display(); }
                else if(t[2][2]=='O'){ t[0][0]='X'; display(); }
                */
        }
        else ai();
        
        
        
        
        }while(1);
    
    return 0;
    
    
}

void ai()
{
    int i=0,j=0;
    //horizontal com
    int p=0,c=0;
    for( i=0;i<3;i++)
    {   for( j=0;j<3;j++)
        {
            if(t[i][j]=='O')
                p++;
            if(t[i][j]=='X')
                c++;
        }
        if((c==2 && p==0))
        {
            for(j=0;j<3;j++)
            {
                if(t[i][j]!='X' && t[i][j]!='O')
                {  t[i][j]='X';  display(); cout<<"\n\tLOL...Your skills are too bad.Computer Wins\n"; exit(0);}
            }
        }
        c=0; p=0;
    }
    //vertical com
    c=0;p=0;
    for( j=0;j<3;j++)
    {
        for( i=0;i<3;i++)
        {
            if(t[i][j]=='O')
            p++;
            if(t[i][j]=='X')
            c++;
        }
        if((c==2 && p==0))
        {
            for(i=0;i<3;i++)
            {
                if(t[i][j]!='X' && t[i][j]!='O')
                {  t[i][j]='X';  display(); cout<<"\n\tLOL...Your skills are too bad.Computer Wins\n"; exit(0);}
            }
        }
        c=0; p=0;
    }
    //right diagonal com
    c=0;p=0;
    for(i=0,j=0;i<3,j<3;i++,j++)
    {
        if(t[i][j]=='O')
        p++;
        if(t[i][j]=='X')
        c++;
    
    }
    if(c==2 && p==0)
    {
        for(i=0,j=0;i<3,j<3;i++,j++)
        {
            if(t[i][j]!='X' && t[i][j]!='O')
            {  t[i][j]='X';  display(); cout<<"\n\tLOL...Your skills are too bad.Computer Wins\n"; exit(0);}
            
        }
    }
    //left diagonal com
    c=0;p=0;
    for(i=2,j=0;i>=0,j<3;i--,j++)
    {
        if(t[i][j]=='O')
            p++;
        if(t[i][j]=='X')
            c++;
    }
    if(c==2 && p==0)
        for(i=2,j=0;i>=0,j<3;i--,j++)
        {
            if(t[i][j]!='X' && t[i][j]!='O')
            {  t[i][j]='X';  display(); cout<<"\n\tLOL...Your skills are too bad.Computer Wins\n"; exit(0);}
        }
    //horizontal player
    c=0;p=0;
    for(i=0;i<3;i++)
    {
        for( j=0;j<3;j++)
        {
            if(t[i][j]=='O')
                p++;
            if(t[i][j]=='X')
            c++;
        }
        if((p==2 && c==0))
        {
            for(j=0;j<3;j++)
            {
                if(t[i][j]!='X' && t[i][j]!='O')
                {  t[i][j]='X'; display(); return;}
            }
        }
        c=0; p=0;
    }
    //vertical player
    c=0;p=0;
    for(j=0;j<3;j++)
    {
        for(i=0;i<3;i++)
        {
            if(t[i][j]=='O')
                p++;
            if(t[i][j]=='X')
                c++;
        }
        if((p==2 && c==0))
        {
            for(i=0;i<3;i++)
            {
                if(t[i][j]!='X' && t[i][j]!='O')
                {  t[i][j]='X'; display(); return;}
            }
        }
        c=0; p=0;
    }
    //right diagonal player
    c=0;p=0;
    for(i=0,j=0;i<3,j<3;i++,j++)
    {
        if(t[i][j]=='O')
            p++;
        if(t[i][j]=='X')
            c++;
        
    }
    if(p==2 && c==0)
    {
        for(i=0,j=0;i<3,j<3;i++,j++)
        {
            if(t[i][j]!='X' && t[i][j]!='O')
            {  t[i][j]='X'; display(); return;}
            
        }
    }
    //left diagonal player
    c=0;p=0;
    for(i=2,j=0;i>=0,j<3;i--,j++)
    {
        if(t[i][j]=='O')
            p++;
        if(t[i][j]=='X')
            c++;
    }
    if(p==2 && c==0)
        for(i=2,j=0;i>=0,j<3;i--,j++)
        {
            if(t[i][j]!='X' && t[i][j]!='O')
            {  t[i][j]='X';  display(); return;}
        }
    
    
    if(cou ==2)
    {
        if(t[2][0]=='O') { t[0][2]='X'; display(); return; }
        if(t[2][2]=='O') { t[0][0]='X'; display(); return; }
        if(t[0][0]=='O') { t[2][2]='X'; display(); return; }
        if(t[0][2]=='O') { t[2][0]='X'; display(); return; }
    
    }
    //just in case lol
    
    if(t[1][0]!='X' && t[1][0]!='O'){ t[1][0]='X'; display(); return;}
    if(t[1][2]!='X' && t[1][2]!='O'){ t[1][2]='X'; display(); return;}
    if(t[0][1]!='X' && t[0][1]!='O'){ t[0][1]='X'; display(); return;}
    if(t[2][1]!='X' && t[2][1]!='O'){ t[2][1]='X'; display(); return;}
    if(t[0][0]!='X' && t[0][0]!='O'){ t[0][0]='X'; display(); return;}
    if(t[0][2]!='X' && t[0][2]!='O'){ t[0][2]='X'; display(); return;}
    if(t[2][0]!='X' && t[2][0]!='O'){ t[2][0]='X'; display(); return;}
    if(t[2][2]!='X' && t[2][2]!='O'){ t[2][2]='X'; display(); return;}
    
}
int check(int choice)
{
    int i,j,num=0;
    for( i=0;i<3;i++)
        for( j=0;j<3;j++)
        {
            num++;
            if(num==choice)
                if(t[i][j]!='O' && t[i][j]!='X')
                    return 0;
        }
    return 1;

}











