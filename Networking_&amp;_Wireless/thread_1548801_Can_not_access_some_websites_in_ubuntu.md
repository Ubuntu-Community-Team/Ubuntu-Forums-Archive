---
title: "Can not access some websites in ubuntu"
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by ras123 on 2010-08-08
Hi,
I couldn't access some websites in Ubuntu, for example login page of sourceforge.net, [http://discussion.forum.nokia.com/forum/](http://discussion.forum.nokia.com/forum/) etc, it takes long time and the page never comes, but the same can be accessed with Windows with firefox.
I also tried with chrome in Ubuntu, but the same response.
Thanking You,
Ras

---

### Post by dineshs on 2010-08-09
I think you need to check DNS or MTU.How do you connect to internet?DSL or dialup?Are you using Network manager?

---

### Post by Peter09 on 2010-08-09
There is an on-going discussion here
 
[http://ubuntuforums.org/showthread.php?t=1505104](http://ubuntuforums.org/showthread.php?t=1505104)

---

### Post by lovinglinux on 2010-08-09
Disable ipv6 on Firefox Preferences, by setting the **network.dns.disableIPv6** preference to **true**.
[LIST=1]
[*]Type **about:config** in the address bar, press Enter.
[*]Find network.dns.disableIPv6 in the list.
[*]Right-click -> Toggle.
[*]Restart Firefox and try again.
[/LIST]

---

### Post by ras123 on 2010-08-12
> **Peter09 said:**
> There is an on-going discussion here
 
[http://ubuntuforums.org/showthread.php?t=1505104](http://ubuntuforums.org/showthread.php?t=1505104)

Hi, the thread haven't a solution yet.

I also disabled the ipv6, and tried another browser chrome. Formerely these sites be accessed,  with Lucid (ipv6 enabled), but I don't when it goes wrong. I regularly doing updates!!
Thanking You
Ras
> **dineshs said:**
> I think you need to check DNS or MTU.How do you  connect to internet?DSL or dialup?Are you using Network manager?
I am using DSL, and NetworkManager Applet 0.8

---

### Post by ras123 on 2010-08-15
Hi,
I faced this problem recently from about a 2/4 weeks ago. Certain websites do not open!!
My observations are
1. It works in Windows XP with the same version of Firefox i.e. 3.6.8
2. Also tried with google chrome, version 5.0.375.126 in ubuntu 
3. It will works in the same setup (i.e. Ubuntu and Firefox) in my office PC (but it uses proxy server to access internet)

I could' access the sites about a few weeks ago, so it may not a ipv6 problem (also it can access in office with the same setup). I updates my system on every available updates so I believe that it was gone with some kernel or other updates.

I use network manager 0.8, without proxy, with a Huwai MT882 modem. I also tried with Ubuntu Live (Make a usb startup disk), and it did't worked.

The sites are
[http://discussion.forum.nokia.com/forum/](http://discussion.forum.nokia.com/forum/)
login of sourceforge.net etc

I also installed Sun Java plugin.
Recently I installed ATI/AMD proprietary FGLRX graphics driver

Thanking You,
Ras
P.S Checked the link [http://ubuntuforums.org/showthread.php?t=1505104&page=6](http://ubuntuforums.org/showthread.php?t=1505104&page=6)

---

### Post by Iowan on 2010-08-15
The link opened for me (but that doesn't help you...)
Have you tried adjusting MTU?

---

### Post by ras123 on 2010-08-15
> **Iowan said:**
> Have you tried adjusting MTU?

How to do it? please give me some guide line, But formerly in the same settings, I can access all sites !!

---

### Post by Iowan on 2010-08-15
There may be better examples, but [this]("http://ubuntuforums.org/showthread.php?t=1376506") post (or contained links) covers it...

---

### Post by ras123 on 2010-08-15
ifconfig displays MTU size as 1500, so set to 1492 by the command

sudo ifconfig eth0 mtu 1492
Not working, also tried to set
sudo ifconfig eth0 mtu 1300
Not working

Also set these values in Networkmanger DSL tab (I used modem in bridged configuration).
Still not getting..

---

### Post by ras123 on 2010-08-15
A fresh installation after formating, will work?

---

### Post by ras123 on 2010-08-15
I reinstalled all the system!!, it didn't helped.
On windows I can get the modem control page at 192.168.1.1 without connecting or dialing anything. Since I configured modem as bridged connection, after connecting, will get websites and 192.168.1.1 page simultaneously. 

On Ubuntu, the default page is not available, to get this page (192.168.1.1), it need to configure auto eth0 in the network manager with the ip address, subnet mask, and gateway (192.168.1.1). To connect website, need to dial DSL connection, then the auto eth0 will disconnect, so page at 192.168.1.1 is not accessible simultaneously with the websites.

Is there any configuration mistakes?
Thanking You,
Ras

---

### Post by dineshs on 2010-08-16
First let us confirm it is not a DNS issue 
Riht click NM icon-edit connections-DSL tab-ipv4
Select Automatic PPPoE addresse only 
Give DNS as 4.2.2.1
apply 
Any progress?

By the way have you tried modem in PPPoE mode? ref post #2 in
[http://ubuntuforums.org/showthread.php?t=1457928&highlight=MT882](http://ubuntuforums.org/showthread.php?t=1457928&highlight=MT882))

---

### Post by ras123 on 2010-08-16
At last it worked.
I changed the bridged mode to pppoe and enabled DHCP, and deleted all connections in Network Manager, then restarted. On restart NM automatically connected to modem using auto eth0. After that I can surf all site without any modem.

But why I can't in pure bridged mode? I also tried bridged mode with DHCP (RFC2684 Bridged (DHCP))enabled.

Thanking You,
Ras

---

### Post by ubu_lin on 2010-08-17
> **ras123 said:**
> At last it worked.
I changed the bridged mode to pppoe and enabled DHCP, and deleted all connections in Network Manager, then restarted. On restart NM automatically connected to modem using auto eth0. After that I can surf all site without any modem.

But why I can't in pure bridged mode? I also tried bridged mode with DHCP (RFC2684 Bridged (DHCP))enabled.

Thanking You,
Ras

Hi Ras,
I m also having the same problem, and I want to know how u did this settings. Can u explain step by step in detail, 

thank you

---

### Post by dineshs on 2010-08-17
The steps are there in my link
post #13

---

### Post by ras123 on 2010-08-17
> **ubu_lin said:**
> Hi Ras,
I m also having the same problem, and I want to know how u did this settings.
The configuring options for different type of modems are listed here
[http://ernakulam.sancharnet.in/ernakulam/cpecfg.html](http://ernakulam.sancharnet.in/ernakulam/cpecfg.html)

Additionally I found that DHCP must be enabled. You can find the DHCP page enabling page of your modem, and just enables it with the default settings. For my case it was

Starting IP Address     192 . 168 . 1 . 2 
Ending IP Address     192 . 168 . 1 . 33 
[FONT=Verdana][SIZE=2]                  [/SIZE][/FONT]
I proceed as follows. First I do an hard reset (using a reset button of the modem), so it goes to the default settings with pure bridged mode. It is changed to ppp and then pppoe selected. Enter username and password for the connection. Apply but not rebbot your modem now. Ensure that DHCP and DNS are enabled and then reboot.

Deleted all connections including wired and DNS. Now restart ubuntu, the network manager automatically configure your connection. Now just browse.

---

### Post by ubu_lin on 2010-08-17
> **ras123 said:**
> The configuring options for different type of modems are listed here
[http://ernakulam.sancharnet.in/ernakulam/cpecfg.html](http://ernakulam.sancharnet.in/ernakulam/cpecfg.html)

Additionally I found that DHCP must be enabled. You can find the DHCP page enabling page of your modem, and just enables it with the default settings. For my case it was

Starting IP Address     192 . 168 . 1 . 2 
Ending IP Address     192 . 168 . 1 . 33 

I proceed as follows. First I do an hard reset (using a reset button of the modem), so it goes to the default settings with pure bridged mode. It is changed to ppp and then pppoe selected. Enter username and password for the connection. Apply but not rebbot your modem now. Ensure that DHCP and DNS are enabled and then reboot.

Deleted all connections including wired and DNS. Now restart ubuntu, the network manager automatically configure your connection. Now just browse.

WOW.. Thank you Ras, Thankyou so much, It worked for me, now I can access all websites, :D

---

### Post by ubu_lin on 2010-08-17
[URL="http://ubuntuforums.org/showthread.php?p=9732502#post9732502"].
[/URL]

---

### Post by ubu_lin on 2010-08-19
Hi Ras,

after the above setup, accessing websites working fine, but Firestarter (firewall) is not working, I am getting error "the device ppp0 is not ready". 
tried all kind of settings in Firestarter, but not working, any help for this ?

---

### Post by ubu_lin on 2010-08-21
DineshS

sorry for not reading ur comment before, It was very useful information. Finally Bridge mode worked with 'pppoeconf' comand. Thank you for that.. :)

Ras

Try 'pppoeconf' for Bridge mode, with that I can access all websites without problem and firewall also works.

---

### Post by thornspear on 2010-10-04
I'm having the same problem, but I can't even access **192.168.1.1 **to try and attempt to configure my modem. 

I get the following error: 

The connection has timed out
The server at 192.168.1.1 is taking too long to respond.


The error I normally get when trying to access some sites, eg.  [www.sait.ca]("http://www.sait.ca") is: 

Unable to connect
Firefox can't establish a connection to the server at [www.sait.ca]("http://www.sait.ca").

Tried with a bunch of different browsers, edited the about:config, tried foxy proxy - can't remember what else I've tried, but nothing's working for me so far. 

I'm running 10.04 dual boot with win 7.  Win 7 works fine in the web dept.  I'm going to try a Live USB Ubuntu 10.04.1 Desktop and see what happens

---

### Post by thornspear on 2010-10-04
With the live USB, I was able to access [www.sait.ca](www.sait.ca) no problem.

---

### Post by thornspear on 2010-10-05
Reinstalled Ubuntu.  Working again....

---

