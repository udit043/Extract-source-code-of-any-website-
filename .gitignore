#include <windows.h>
#include <wininet.h>
#include <iostream>
#include <conio.h>
#include <fstream.h>
fstream fs_obj;
using namespace std;

int main(int argc, char *argv[])
{
  char str[100];
  cin>>str;
  fs_obj.open("fb(openinbrowser).txt",ios::out | ios::app);  
  HINTERNET hInternet = InternetOpenA("InetURL/1.0", INTERNET_OPEN_TYPE_PRECONFIG, NULL, NULL, 0 );

  HINTERNET hConnection = InternetConnectA( hInternet, str, 80, " "," ", INTERNET_SERVICE_HTTP, 0, 0 );

  HINTERNET hData = HttpOpenRequestA( hConnection, "GET", "/", NULL, NULL, NULL, INTERNET_FLAG_KEEP_CONNECTION, 0 );

  char buf[ 2048 ] ;

  HttpSendRequestA( hData, NULL, 0, NULL, 0 ) ;
  string total;
  DWORD bytesRead = 0 ;
  DWORD totalBytesRead = 0 ;
  // To ensure all data is retrieved, an application must continue to call the
  // InternetReadFile function until the function returns TRUE and the
  // lpdwNumberOfBytesRead parameter equals zero. 
  while( InternetReadFile( hData, buf, 2000, &bytesRead ) && bytesRead != 0 )
  {
    buf[ bytesRead ] = 0 ; // insert the null terminator.
    textcolor(11);
//    puts( buf ) ;   
    textcolor(15);       // print it to the screen.
    total=total+buf;
    printf( "%d bytes read\n", bytesRead ) ;

    totalBytesRead += bytesRead ;
  }
  
  fs_obj<<total<<"\n--------------------end---------------------\n";
  fs_obj.close();
  printf( "\n\n END -- %d bytes read\n", bytesRead ) ;
  printf( "\n\n END -- %d TOTAL bytes read\n", totalBytesRead ) ;
  textcolor(13);
  cout<<endl<<total<<endl;
  textcolor(15);
  InternetCloseHandle( hData ) ;
  InternetCloseHandle( hConnection ) ;
  InternetCloseHandle( hInternet ) ;
  system("pause");
}
