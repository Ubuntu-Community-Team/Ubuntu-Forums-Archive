---
title: "Connect to My VPN - Help Required (Will be really grateful)"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by It's-Me on 2009-03-26
[FONT=Verdana][SIZE=2][COLOR=black]Hi guys & girls ...

I have successfully invoked VPN in Ubuntu 8.10, thanks to this great forum. Now i wanted to connect to the VPN. The problem is that i can't :(. I am connected to an Area LAN at my home and to use internet i have to dial a VPN connection.

The following is how i connect to the network on windows[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=black]

[/COLOR][/SIZE][/FONT]  [CENTER][FONT=Verdana][SIZE=2][COLOR=black][IMG]http://i201.photobucket.com/albums/aa134/My-Choice-Only/Tech/1.jpg[/IMG]

[IMG]http://i201.photobucket.com/albums/aa134/My-Choice-Only/Tech/2.jpg[/IMG]

[IMG]http://i201.photobucket.com/albums/aa134/My-Choice-Only/Tech/3.jpg[/IMG]

[IMG]http://i201.photobucket.com/albums/aa134/My-Choice-Only/Tech/4.jpg[/IMG]

[IMG]http://i201.photobucket.com/albums/aa134/My-Choice-Only/Tech/5.jpg[/IMG]

[IMG]http://i201.photobucket.com/albums/aa134/My-Choice-Only/Tech/6.jpg[/IMG]

[IMG]http://i201.photobucket.com/albums/aa134/My-Choice-Only/Tech/7.jpg[/IMG][/COLOR][/SIZE][/FONT][/CENTER]

---

### Post by It's-Me on 2009-03-26
[CENTER][FONT=Verdana][SIZE=2][COLOR=black][IMG]http://i201.photobucket.com/albums/aa134/My-Choice-Only/Tech/8.jpg[/IMG]

[IMG]http://i201.photobucket.com/albums/aa134/My-Choice-Only/Tech/9.jpg[/IMG]

[IMG]http://i201.photobucket.com/albums/aa134/My-Choice-Only/Tech/10.jpg[/IMG]

[IMG]http://i201.photobucket.com/albums/aa134/My-Choice-Only/Tech/11.jpg[/IMG][/COLOR][/SIZE][/FONT]      [/CENTER]
[FONT=Verdana][SIZE=2][COLOR=black]
[/COLOR][/SIZE][/FONT] [FONT=Verdana][SIZE=2][COLOR=black]When it comes to Networking i am a total noob in Xp as well. That's why i have posted all the instructions that i got to create a VPN on Xp to connect to my network.

Can anyone be generous enough to guide me how to connect to this network using Ubuntu 8.10? I will be really grateful.[/COLOR][/SIZE][/FONT]

---

### Post by superprash2003 on 2009-03-27
have you tried using the network manager..system->pref->network configuration

---

### Post by It's-Me on 2009-03-27
I am able to activate VPN already.

Now when i try to add a VPN, i fill the following details

Gateway: 10.101.10.2
UserName:<My User Id>
Passwrord: <My Password>

Then i go to advance menu

Uncheck PAP & CHAP
Uncheck: Use point-to-point Encryption (MPPE)

And then when i try to Connect, i get an error

'VPN Connection failed'

Pls. help me ... i am desperately looking forward to use Ubuntu 8.10. But Ububtu minus internet is really unimaginable for me :-s.

---

### Post by superprash2003 on 2009-03-28
in your terminal type **ifconfig** and post output.. so you arent able to access the internet? in your command prompt(in windows ) type **ipconfig** and post output..

---

### Post by It's-Me on 2009-03-28
**ipconfig**

> Windows IP Configuration


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : connect.net.pk
        IP Address. . . . . . . . . . . .          : 10.113.2.238
        Subnet Mask . . . . . . . . . . .        : 255.255.248.0
        Default Gateway . . . . . . . . .       :

PPP adapter Connect Blue (Custom):

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . .          : 118.103.235.237
        Subnet Mask . . . . . . . . . . .        : 255.255.255.255
        Default Gateway . . . . . . . . .       : 118.103.235.237**ifconfig**

> eth0    Link encap:Ethernet  HWaddr 00:12:3f:2e:e7:88
 
       inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0

        inet6 addr: fe80::212:3fff:fe2e:e788/64 Scope:Link
          
        UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

        RX packets:1173 errors:0 dropped:0 overruns:0 frame:0

        TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
 
        collisions:0 txqueuelen:1000    RX bytes:100488 (100.4 KB)    TX bytes:6538 (6.5 KB)
    
    Interrupt:16 



lo    Link encap:Local Loopback  
          
    inet addr:127.0.0.1  Mask:255.0.0.0
          
    inet6 addr: ::1/128 Scope:Host
          
    UP LOOPBACK RUNNING  MTU:16436  Metric:1
          
    RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          
    TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          
    collisions:0 txqueuelen:0    RX bytes:15408 (15.4 KB)    TX bytes:15408 (15.4 KB)Just in case if anything useful can be deduced from this (I am not sure though, saw this command while googling.)

**ipconfig / all**

> Windows IP Configuration

        Host Name . . . . . . . . . . . . : dexter
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Peer-Peer
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : connect.net.pk

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : connect.net.pk
        Description . . . . . . . . . . . : Broadcom NetXtreme 57xx Gigabit Cont
roller
        Physical Address. . . . . . . . . : 00-12-3F-2E-E7-88
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 10.113.2.238
        Subnet Mask . . . . . . . . . . . : 255.255.248.0
        Default Gateway . . . . . . . . . :
        DHCP Server . . . . . . . . . . . : 10.113.0.1
        DNS Servers . . . . . . . . . . . : 10.101.10.5
                                            10.101.10.10
        Primary WINS Server . . . . . . . : 10.113.0.1
        NetBIOS over Tcpip. . . . . . . . : Disabled
        Lease Obtained. . . . . . . . . . : Saturday, March 28, 2009 7:55:51 PM
        Lease Expires . . . . . . . . . . : Sunday, March 28, 2010 7:55:51 PM

PPP adapter Connect Blue (Custom):

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface
        Physical Address. . . . . . . . . : 00-53-45-00-00-00
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 118.103.235.237
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 118.103.235.237
        DNS Servers . . . . . . . . . . . : 10.101.10.5
                                            10.101.10.10

---

### Post by It's-Me on 2009-03-29
Looking forward to resolving this issue. I hope that i will keep up with this great OS :).

---

### Post by It's-Me on 2009-03-30
I have tried to do as much as i can through google and browsing this forum but to no avail :(.
I am still unable to connect to my VPN. Still trying to figure it out.
May be i get lucky and someone passing through will help me a bit :).

---

### Post by superprash2003 on 2009-04-01
how come in windows you are connecting with a 10.x.x.x ip and via linux you get a 192.x.x.x ip.. presuming 118x.x.x. is the ip given by vpn

---

### Post by It's-Me on 2009-04-01
I have no idea :-s. I just ran the commands that you have asked for.

What should i do!

---

### Post by jonobr on 2009-04-01
You should also watch the /var/log messages you get when you try to connect and post the results.

superprash2003 has hit on it thought.

You need to figure out why your windows machine gets and 10.x address and ubuntu shows a 192 address.

Are both machines on the same network connecting to a router?

DOes your ubuntu machine and windows machine have internet access through your router to the internet and does it work for both systems?

It almost looks as if you are showing a configuration for your windows machine from one network/location and the ubuntu from another.....

---

### Post by Narvinye on 2009-04-22
> **It's-Me said:**
> I am able to activate VPN already.

Now when i try to add a VPN, i fill the following details

Gateway: 10.101.10.2
UserName:<My User Id>
Passwrord: <My Password>

Then i go to advance menu

Uncheck PAP & CHAP
Uncheck: Use point-to-point Encryption (MPPE)

And then when i try to Connect, i get an error

'VPN Connection failed'

Pls. help me ... i am desperately looking forward to use Ubuntu 8.10. But Ububtu minus internet is really unimaginable for me :-s.

Hi again!  So when your connected to the VPN on windows you will get the 10.x address.  You will not receive this IP address in Ubuntu until you are connected to the VPN.  Then your IP will show as 10.x (once you authenticate to the domain).

As far as the connection settings are concerned I noticed that on your Windows connection you are using PAP and CHAP.  Are you leaving these options checked in whatever program you are using in Linux? I'd keep the settings as close as possible to the ones you are using on Windows.

Also when you receive the connection failed error when attempting to connect to the VPN look for more detailed information about the error and post it here. Good luck.

---

