#include <stdio.h>
#include "conio.h"																					//completed on 19-06-15 03:07....
#include <iostream>
#include <windows.h>

using namespace std;

static int i=0;

HANDLE console = GetStdHandle(STD_OUTPUT_HANDLE);
COORD CursorPosition;

void gotoXY(int x, int y);

int checkuser(int x, int &y,int a[3][3])
{
	int j,k;
	i++;
	if(x-1==0)
	{
		if(y-1==0)
		{
			if((a[0][0]==1 && a[0][1]==1 && a[0][2]==1) || (a[0][0]==1 && a[1][0]==1 && a[2][0]==1) || (a[0][0]==1 && a[1][1]==1 && a[2][2]==1))
			{
				cout<<"User 1 wins\n";
			}
		}
		else if(y-1==1)
		{
			if((a[0][0]==1 && a[0][1]==1 && a[0][2]==1) || (a[0][1]==1 && a[1][1]==1 && a[2][1]==1))
			{
				cout<<"User 1 wins\n";
			}
		}
		else if(y-1==2)
		{
			if((a[0][0]==1 && a[0][1]==1 && a[0][2]==1) || (a[0][2]==1 && a[1][2]==1 && a[2][2]==1) || (a[0][2]==1 && a[1][1]==1 && a[2][0]==1))
			{
				cout<<"User 1 wins\n";
			}
		}
	}
	else if(x-1==1)
	{
		if(y-1==0)
		{
			if((a[1][0]==1 && a[1][1]==1 && a[1][2]==1) || (a[0][0]==1 && a[1][0]==1 && a[2][0]==1))
			{
				cout<<"User 1 wins\n";
			}
		}
		else if(y-1==1)
		{
			if((a[1][0]==1 && a[1][1]==1 && a[1][2]==1) || (a[0][1]==1 && a[1][1]==1 && a[2][1]==1))
			{
				cout<<"User 1 wins\n";
			}
		}
		else if(y-1==2)
		{
			if((a[1][0]==1 && a[1][1]==1 && a[1][2]==1) || (a[0][2]==1 && a[1][2]==1 && a[2][2]==1))
			{
				cout<<"User 1 wins\n";
			}
		}
		
	}
	else if(x-1==2)
	{
		if(y-1==0)
		{
			if((a[2][0]==1 && a[2][1]==1 && a[2][2]==1) || (a[0][0]==1 && a[1][0]==1 && a[2][0]==1) || (a[0][2]==1 && a[1][1]==1 && a[2][0]==1))
			{
				cout<<"User 1 wins\n";
			}
		}
		else if(y-1==1)
		{
			if((a[2][0]==1 && a[2][1]==1 && a[2][2]==1) || (a[0][1]==1 && a[1][1]==1 && a[2][1]==1))
			{
				cout<<"User 1 wins\n";
			}
		}
		else if(y-1==2)
		{
			if((a[2][0]==1 && a[2][1]==1 && a[2][2]==1) || (a[0][2]==1 && a[1][2]==1 && a[2][2]==1) || (a[2][2]==1 && a[1][1]==1 && a[0][0]==1))
			{
				cout<<"User 1 wins\n";
			}
		}
	}
	if(i==9)
	{
		for(j=0;j<3;j++)
		{
			for(k=0;k<3;k++)
			{
				if(a[j][k]==1)
				{
					gotoXY(2*k,j);
					cout<<"X ";
				}
				else if(a[j][k]==2)
				{
					gotoXY(2*k,j);
					cout<<"O ";
				}
				else
				{
					gotoXY(2*k,j);
					cout<<"_ ";
				}
			}
			cout<<"\n";
		}
		cout<<"Match is a Draw";
		exit (0);
	}
}

int checkcomputer(int &x,int &y,int a[3][3])
{
	int j,k;
	i++;
	if(i==2)
	{
		if(a[1][1]==0)
		{
			a[1][1]=2;
			//cout<<"Computer chooses position (x,y):5\n";
		}
		else
		{
			a[0][0]=2;
			//cout<<"Computer chooses position (x,y):1\n";
		}
	}
	//cases where computer wins..
	else if((a[0][0]==a[0][1] && a[0][1]==2 && a[0][2]==0))
	{
		a[0][2]=2;
		cout<<"Computer wins\n";
		return 0;
	}
	else if((a[0][0]==a[0][2] && a[0][2]==2 && a[0][1]==0))
	{
		a[0][1]=2;
		cout<<"Computer wins\n";
		return 0;
	}
	else if((a[0][2]==a[0][1] && a[0][1]==2 && a[0][0]==0))
	{
		a[0][0]=2;
		cout<<"Computer wins\n";
		return 0;
	}
	else if((a[0][0]==a[1][0] && a[0][0]==2 && a[2][0]==0))
	{
		a[2][0]=2;
		cout<<"Computer wins\n";
		return 0;
	}
	else if((a[0][0]==a[2][0] && a[0][0]==2 && a[1][0]==0))
	{
		a[1][0]=2;
		cout<<"Computer wins\n";
		return 0;
	}
	else if((a[2][0]==a[1][0] && a[1][0]==2 && a[0][0]==0))
	{
		a[0][0]=2;
		cout<<"Computer wins\n";
		return 0;
	}
	else if((a[0][0]==a[1][1] && a[0][0]==2 && a[2][2]==0))
	{
		a[2][2]=2;
		cout<<"Computer wins\n";
		return 0;
	}
	else if((a[0][0]==a[2][2] && a[0][0]==2 && a[1][1]==0))
	{
		a[1][1]=2;
		cout<<"Computer wins\n";
		return 0;
	}
	else if((a[2][2]==a[1][1] && a[1][1]==2 && a[0][0]==0))
	{
		a[0][0]=2;
		cout<<"Computer wins\n";
		return 0;
	}
	else if((a[0][1]==a[1][1] && a[0][1]==2 && a[2][1]==0))
	{
		a[2][1]=2;
		cout<<"Computer wins\n";
		return 0;
	}
	else if((a[0][1]==a[2][1] && a[0][1]==2 && a[1][1]==0))
	{
		a[1][1]=2;
		cout<<"Computer wins\n";
		return 0;
	}
	else if((a[2][1]==a[1][1] && a[2][1]==2 && a[0][1]==0))
	{
		a[0][1]=2;
		cout<<"Computer wins\n";
		return 0;
	}
	else if((a[0][2]==a[1][2] && a[0][2]==2 && a[2][2]==0))
	{
		a[2][2]=2;
		cout<<"Computer wins\n";
		return 0;
	}
	else if((a[0][2]==a[2][2] && a[0][2]==2 && a[1][2]==0))
	{
		a[1][2]=2;
		cout<<"Computer wins\n";
		return 0;
	}
	else if((a[2][2]==a[1][2] && a[1][2]==2 && a[0][2]==0))
	{
		a[0][2]=2;
		cout<<"Computer wins\n";
		return 0;
	}
	else if((a[0][2]==a[1][1] && a[0][2]==2 && a[2][0]==0))
	{
		a[2][0]=2;
		cout<<"Computer wins\n";
		return 0;
	}
	else if((a[0][2]==a[2][0] && a[0][2]==2 && a[1][1]==0))
	{
		a[1][1]=2;
		cout<<"Computer wins\n";
		return 0;
	}
	else if((a[2][0]==a[1][1] && a[2][0]==2 && a[0][2]==0))
	{
		a[0][2]=2;
		cout<<"Computer wins\n";
		return 0;
	}
	else if((a[1][0]==a[1][1] && a[1][0]==2 && a[1][2]==0))
	{
		a[1][2]=2;
		cout<<"Computer wins\n";
		return 0;
	}
	else if((a[1][0]==a[1][2] && a[1][0]==2 && a[1][1]==0))
	{
		a[1][1]=2;
		cout<<"Computer wins\n";
		return 0;
	}
	else if((a[1][2]==a[1][1] && a[1][2]==2 && a[1][0]==0))
	{
		a[1][0]=2;
		cout<<"Computer wins\n";
		return 0;
	}
	else if((a[2][0]==a[2][1] && a[2][0]==2 && a[2][2]==0))
	{
		a[2][2]=2;
		cout<<"Computer wins\n";
		return 0;
	}
	else if((a[2][0]==a[2][2] && a[2][0]==2 && a[2][1]==0))
	{
		a[2][1]=2;
		cout<<"Computer wins\n";
		return 0;
	}
	else if((a[2][2]==a[2][1] && a[2][2]==2 && a[2][0]==0))
	{
		a[2][0]=2;
		cout<<"Computer wins\n";
		return 0;
	}
	//cases where computer protects itself.
	else if(a[0][0]==1 && a[0][1]==1 && a[0][2]==0)
	{
		a[0][2]=2;
		//cout<<"Computer chooses position (x,y):3\n";
		return 1;
	}
	else if(a[0][0]==1 && a[0][2]==1 && a[0][1]==0)
	{
		a[0][1]=2;
		//cout<<"Computer chooses position (x,y):2\n";
		return 1;
	}
	else if(a[0][2]==1 && a[0][1]==1 && a[0][0]==0)
	{
		a[0][0]=2;
		//cout<<"Computer chooses position (x,y):1\n";
		return 1;
	}
	else if(a[0][0]==1 && a[1][0]==1 && a[2][0]==0)
	{
		a[2][0]=2;
		//cout<<"Computer chooses position (x,y):7\n";
		return 1;
	}
	else if(a[0][0]==1 && a[2][0]==1 && a[1][0]==0)
	{
		a[1][0]=2;
		//cout<<"Computer chooses position (x,y):4\n";
		return 1;
	}
	else if(a[2][0]==1 && a[1][0]==1 && a[0][0]==0)
	{
		a[0][0]=2;
		//cout<<"Computer chooses position (x,y):1\n";
		return 1;
	}
	else if(a[0][0]==1 && a[1][1]==1 && a[2][2]==0)
	{
		a[2][2]=2;
		//cout<<"Computer chooses position (x,y):9\n";
		return 1;
	}
	else if(a[0][0]==1 && a[2][2]==1 && a[1][1]==0)
	{
		a[1][1]=2;
		//cout<<"Computer chooses position (x,y):5\n";
		return 1;
	}
	else if(a[2][2]==1 && a[1][1]==1 && a[0][0]==0)
	{
		a[0][0]=2;
		//cout<<"Computer chooses position (x,y):1\n";
		return 1;
	}
	else if(a[0][1]==1 && a[1][1]==1 && a[2][1]==0)
	{
		a[2][1]=2;
		//cout<<"Computer chooses position (x,y):8\n";
		return 1;
	}
	else if(a[0][1]==1 && a[2][1]==1 && a[1][1]==0)
	{
		a[1][1]=2;
		//cout<<"Computer chooses position (x,y):5\n";
		return 1;
	}
	else if(a[1][1]==1 && a[2][1]==1 && a[0][1]==0)
	{
		a[0][1]=2;
		//cout<<"Computer chooses position (x,y):2\n";
		return 1;
	}
	else if(a[0][2]==1 && a[1][2]==1 && a[2][2]==0)
	{
		a[2][2]=2;
		//cout<<"Computer chooses position (x,y):9\n";
		return 1;
	}
	else if(a[0][2]==1 && a[2][2]==1 && a[1][2]==0)
	{
		a[1][2]=2;
		//cout<<"Computer chooses position (x,y):6\n";
		return 1;
	}
	else if(a[2][2]==1 && a[1][2]==1 && a[0][2]==0)
	{
		a[0][2]=2;
		//cout<<"Computer chooses position (x,y):3\n";
		return 1;
	}
	else if(a[0][2]==1 && a[1][1]==1 && a[2][0]==0)
	{
		a[2][0]=2;
		//cout<<"Computer chooses position (x,y):7\n";
		return 1;
	}
	else if(a[0][2]==1 && a[2][0]==1 && a[1][1]==0)
	{
		a[1][1]=2;
		//cout<<"Computer chooses position (x,y):5\n";
		return 1;
	}
	else if(a[2][0]==1 && a[1][1]==1 && a[0][2]==0)
	{
		a[0][2]=2;
		//cout<<"Computer chooses position (x,y):3\n";
		return 1;
	}
	else if(a[1][0]==1 && a[1][1]==1 && a[1][2]==0)
	{
		a[1][2]=2;
		//cout<<"Computer chooses position (x,y):6\n";
		return 1;
	}
	else if(a[1][0]==1 && a[1][2]==1 && a[1][1]==0)
	{
		a[1][1]=2;
		//cout<<"Computer chooses position (x,y):5\n";
		return 1;
	}
	else if(a[1][2]==1 && a[1][1]==1 && a[1][0]==0)
	{
		a[1][0]=2;
		//cout<<"Computer chooses position (x,y):4\n";
		return 1;
	}
	else if(a[2][0]==1 && a[2][1]==1 && a[2][2]==0)
	{
		a[2][2]=2;
		//cout<<"Computer chooses position (x,y):9\n";
		return 1;
	}
	else if(a[2][0]==1 && a[2][2]==1 && a[2][1]==0)
	{
		a[2][1]=2;
		//cout<<"Computer chooses position (x,y):8\n";
		return 1;
	}
	else if(a[2][2]==1 && a[2][1]==1  && a[2][0]==0)
	{
		a[2][0]=2;
		//cout<<"Computer chooses position (x,y):7\n";
		return 1;
	}
	//cases where computer has to think itself..
	else if(i==4)
	{
		if(a[1][1]==2)
		{
			if(a[0][0]==1 && a[1][2]==1)
			{
				a[2][1]=2;
				//cout<<"Computer chooses position (x,y):8\n";
				return 1;
			}
			else if(a[0][0]==1 && a[2][2]==1)
			{
				a[1][2]=2;
				//cout<<"Computer chooses position (x,y):6\n";
				return 1;
			}
			else if(a[0][0]==1 && a[2][1]==1)
			{
				a[1][2]=2;
				//cout<<"Computer chooses position (x,y):6\n";
				return 1;
			}
			else if(a[0][1]==1 && a[1][2]==1)
			{
				a[0][0]=2;
				//cout<<"Computer chooses position (x,y):1\n";
				return 1;
			}
			else if(a[0][1]==1 && a[2][2]==1)
			{
				a[1][0]=2;
				//cout<<"Computer chooses position (x,y):4\n";
				return 1;
			}
			else if(a[0][1]==1 && a[2][1]==1)
			{
				a[0][2]=2;
				//cout<<"Computer chooses position (x,y):3\n";
				return 1;
			}
			else if(a[0][1]==1 && a[2][0]==1)
			{
				a[1][2]=2;
				//cout<<"Computer chooses position (x,y):6\n";
				return 1;
			}
			else if(a[0][1]==1 && a[1][0]==1)
			{
				a[0][2]=2;
				//cout<<"Computer chooses position (x,y):3\n";
				return 1;
			}
			else if(a[0][2]==1 && a[1][0]==1)
			{
				a[2][1]=2;
				//cout<<"Computer chooses position (x,y):8\n";
				return 1;
			}
			else if(a[0][2]==1 && a[2][0]==1)
			{
				a[1][2]=2;
				//cout<<"Computer chooses position (x,y):6\n";
				return 1;
			}
			else if(a[0][2]==1 && a[2][1]==1)
			{
				a[1][0]=2;
				//cout<<"Computer chooses position (x,y):4\n";
				return 1;
			}
			else if(a[1][2]==1 && a[2][1]==1)
			{
				a[0][2]=2;
				//cout<<"Computer chooses position (x,y):3\n";
				return 1;
			}
			else if(a[1][2]==1 && a[2][0]==1)
			{
				a[0][1]=2;
				//cout<<"Computer chooses position (x,y):2\n";
				return 1;
			}
			else if(a[1][2]==1 && a[1][0]==1)
			{
				a[2][2]=2;
				//cout<<"Computer chooses position (x,y):9\n";
				return 1;
			}
			else if(a[1][2]==1 && a[0][0]==1)
			{
				a[2][1]=2;
				//cout<<"Computer chooses position (x,y):8\n";
				return 1;
			}
			else if(a[1][2]==1 && a[0][1]==1)
			{
				a[2][2]=2;
				//cout<<"Computer chooses position (x,y):9\n";
				return 1;
			}
			else if(a[2][2]==1 && a[1][0]==1)
			{
				a[0][1]=2;
				//cout<<"Computer chooses position (x,y):2\n";
				return 1;
			}
			else if(a[2][1]==1 && a[1][0]==1)
			{
				a[2][2]=2;
				//cout<<"Computer chooses position (x,y):9\n";
				return 1;
			}
		}
		else
		{
			if(a[1][1]==1 && a[2][2]==1)
			{
				a[0][2]=2;
			//	cout<<"Computer chooses position (x,y):3\n";
				return 1;
			}
		}
	}
	else if(i>=6)
	{
		for(j=0;j<3;j++)
		{
			for(k=0;k<3;k++)
			{
				if(a[j][k]==0)
				{
					a[j][k]=2;
					//cout<<"Computer chooses position (x,y):"<<j+1<<","<<k+1<<"\n";
					return 1;
				}
			}
		}
	}
}

int main()
{
	static int a[3][3],x,y,d,n,j,k,e;
		for(j=0;j<3;j++)
		{
			for(k=0;k<3;k++)
			{
				if(a[j][k]==1)
				{
					gotoXY(2*k,j);
					cout<<"X ";
				}
				else if(a[j][k]==2)
				{
					gotoXY(2*k,j);
					cout<<"O ";
				}
				else
				{
					gotoXY(2*k,j);
					cout<<"_ ";
				}
			}
			cout<<"\n";
		}
	while(1)
	{
		do
		{
			cout<<"enter value:";
			cin>>n;
			if(n==1)
			{
				x=1;
				y=1;
			}
			else if(n==2)
			{
				x=1;
				y=2;
			}
			else if(n==3)
			{
				x=1;
				y=3;
			}
			else if(n==4)
			{
				x=2;
				y=1;
			}
			else if(n==5)
			{
				x=2;
				y=2;
			}
			else if(n==6)
			{
				x=2;
				y=3;
			}
			else if(n==7)
			{
				x=3;
				y=1;
			}
			else if(n==8)
			{
				x=3;
				y=2;
			}
			else if(n==9)
			{
				x=3;
				y=3;
			}
		}while(a[x-1][y-1]==1 || a[x-1][y-1]==2);
		a[x-1][y-1]=1;
		e=checkuser(x,y,a);
		for(j=0;j<3;j++)
		{
			for(k=0;k<3;k++)
			{
				if(a[j][k]==1)
				{
					gotoXY(2*k,j);
					cout<<"X ";
				}
				else if(a[j][k]==2)
				{
					gotoXY(2*k,j);
					cout<<"O ";
				}
				else
				{
					gotoXY(2*k,j);
					cout<<"_ ";
				}
			}
			cout<<"\n";
		}
		d=checkcomputer(x,y,a);
		for(j=0;j<3;j++)
		{
			for(k=0;k<3;k++)
			{
				if(a[j][k]==1)
				{
					gotoXY(2*k,j);
					cout<<"X ";
				}
				else if(a[j][k]==2)
				{
					gotoXY(2*k,j);
					cout<<"O ";
				}
				else
				{
					gotoXY(2*k,j);
					cout<<"_ ";
				}
			}
			cout<<"\n";
		}
		if(d==0)
			return 0;
	}
	getch();
	return 0;
}
void gotoXY(int x, int y) 
{ 
CursorPosition.X = x; // Locates column
CursorPosition.Y = y; // Locates Row
SetConsoleCursorPosition(console,CursorPosition); // Sets position for next thing to be printed 
}
