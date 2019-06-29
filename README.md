#include <iostream>
#include <cmath>
using namespace std;
int main()
{
int p, q, e, f, d, P, n, c = 0;
unsigned long long int E;
cout << "add p: ";
cin >> p;
cout << "add q: ";
cin >> q;
n = p * q;
cout << "Enter your message (less " << n << "): ";
cin >> P;
f = (p - 1) * (q - 1);
if ((f % 2) != 0)
{
e = 2;
c = 1;
}
for (int i = 3; i < f; i++)
{ 
if (c == 1)
{
break;
}
for (int j = 1; j <= i - 1; j++)
{
if (((i % j) != 0) && ((f % i) != 0))
{
c = 1;
e = i;
break;				
}
}
}
cout << " Public key {" << e << ", " << n << "}" << endl;
int o = 1, x = 1;
while (o == 1)
{
if ((((x * e) % f) == 1)&&(x != e))
{
d = x;
o = -1;
}
x++;
}
cout << " private key {" << d << ", " << n << "}" << endl;
E = pow(P, e);
E = E % n;
cout << " Encrypted message: " << E << endl;
E = pow(E, d);
E = E % n;
cout << " Decrypted message: " << E << endl;
system ("pause");
return 0;
}
