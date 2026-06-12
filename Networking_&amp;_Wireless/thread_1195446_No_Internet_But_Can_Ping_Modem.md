---
title: "No Internet But Can Ping Modem"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by doogiekd on 2009-06-23
Friends, 

I have a 1386 operating with Jaunty with a wired connection to the modem.

I can ping the modem using network tools, but I cannot ping any outside site.

Also, the Firefox browser will not connect to the internet.

Please help.

Thanks, 

doogie

---

### Post by lavinog on 2009-06-23
The first thing most ISPs will ask you to do would be to unplug the power from the modem and router for 10 secs then plug it back in.
Sometimes the modem crashes.
Many times the dns server the isp uses goes down, or might be switched.
you can try using opendns servers for dns (208.67.222.222 and 208.67.220.220.)

---

### Post by paul_be on 2009-06-23
You may try resetting your modem.  No router???  Also you can run dhclient eth0(your ethernet device name) to renew ip information, if that does not work.

---

### Post by doogiekd on 2009-06-23
I unplugged the modem and reset it. This still does not resolve the problem.

I also ran dhclient eth0. This does not resolve the problem.

I will now try & change the DNS - but how do I change that?

Also, is it possible that Comcast changed the DNS? There was construction at my house & I moved out for two weeks and shut my computer off. When I returned home, the computer was no longer connecting to the internet.

---

### Post by doogiekd on 2009-06-23
changing the dns did not solve this issue. please help.

---

### Post by jhannah on 2009-06-24
After running dhclient, are you getting an IP address? Let me know what the below commands yield:

```

ifconfig eth0
route -n
cat /etc/resolv.conf

```It sounds like you are just missing a default route if you can reach the modem but nothing beyond that. Running 'route -na' should make that clear though.

---

### Post by doogiekd on 2009-06-24
Here are the results of the following commands:

dhclient eth0:

Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:30:f1:13:0c:26
Sending on   LPF/eth0/00:30:f1:13:0c:26
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.100 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.1.1
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.1.101 from 192.168.1.1
DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.101 from 192.168.1.1
bound to 192.168.1.101 -- renewal in 39473 seconds.
administrator@sun:~$ 

iconfig eth0:

eth0      Link encap:Ethernet  HWaddr 00:30:f1:13:0c:26  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:f1ff:fe13:c26/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:883 errors:0 dropped:0 overruns:0 frame:0
          TX packets:156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:75604 (75.6 KB)  TX bytes:50966 (50.9 KB)
          Interrupt:17 Base address:0x1000 

route -n:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

cat /etc/resolv.conf:

domain hsd1.wa.comcast.net.
search hsd1.wa.comcast.net.
nameserver 68.87.69.150
nameserver 68.87.85.102

The command sudo route -na was not accepted. Indicated illegal operation.

---

### Post by jhannah on 2009-06-24
The 'route -na' command was a typo on my part, 'route -n' is the correct command. From what you posted, it looks like your default gateway is 192.168.1.1 and that DHCP is properly setting that and your DNS servers.

What is the device with the 192.168.1.1 IP? Also, you might want to try to run a traceroute/mtr (which can be installed with sudo aptitude install mtr) to the IP address of something on the internet (ie 74.125.127.100 which is google.com). If you decide to use mtr,  you will get the most information but you should run it as follows so you can paste the results:

```
mtr -c 5 -r 74.125.127.100
```

---

### Post by Icky_Ev on 2009-06-24
Before toiling over settings, do some basic troubleshooting (apologies if you've already done & considered all this):

Is your modem connecting to the internet or just blinking at you?

Can other computers/devices see the internet but your machine cannot?

Is your computer plugged directly into the modem or does it go through a router? (Those network addresses look like a modem/switch is in there somewhere, but I'm hardly an expert on such things ;) )

Have you verified that your ISP can ping the modem from their end?

---

### Post by doogiekd on 2009-06-24
here is the result of the mtr command:

administrator@sun:~$ mtr -c 5 -r 74.125.127.100
HOST: sun                         Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. 192.168.1.1                   0.0%     5    0.7   0.8   0.6   1.2   0.2
  2. ???                          100.0     5    0.0   0.0   0.0   0.0   0.0
  3. 68.85.144.129                 0.0%     5   11.8  14.6   8.1  23.3   6.7
  4. 68.85.240.101                 0.0%     5   10.3  10.0   9.3  10.4   0.5
  5. 68.86.90.217                  0.0%     5   17.7  14.9  13.4  17.7   1.6
  6. 68.86.85.205                  0.0%     5   14.8  16.2  14.0  23.3   3.9
  7. 4.79.104.105                  0.0%     5   13.3  14.7  12.2  17.8   2.3
  8. 4.79.104.74                   0.0%     5   14.1  15.3  13.3  20.8   3.1
  9. 209.85.249.32                 0.0%     5   13.7  14.3  13.3  17.6   1.9
 10. 216.239.46.208                0.0%     5   23.4  22.1  19.5  24.4   2.0
 11. 64.233.174.127                0.0%     5   19.7  21.3  18.4  27.2   3.4
 12. 216.239.46.22                 0.0%     5   29.9  27.1  20.7  30.0   3.9
 13. 74.125.127.100                0.0%     5   20.4  20.4  19.5  21.3   0.7
administrator@sun:~$ 


notes:

there are several computers in the residence. all windows computers are connecting to the internet via a wireless router - no problems. the ubuntu box here, is wired directly to the wireless router (192.168.1.1) via ethernet cable. i have also tried a direct plugin to the modem with the same results. 

also, yes, i i have reset the modem & router several times. again, the windows computers can connect to the internet. given that, i'm really doubting that this is a modem/router issue.

---

### Post by dBuster on 2009-06-24
Could it be that the other computers in the home are connecting to a neighbors wireless connection?  After all it was windows which will try to connect to anything.

As far as your modem goes, can you get into the modem? I mean through a web page such as 192.168.1.1?  If so is it showing your connection being up or down?  Hence the one question asked if the modem is showing connection to the internet or not.  It may sound silly but back to the basics to check for those things.  

You did mention construction which caused you to move out, maybe a line was cut somewhere and now your modem is not connected.  Just some thoughts...

---

### Post by doogiekd on 2009-06-24
hi. yes, it is confirmed that all computers are connecting through the home wireless router and not another nearby wireless network. there are definately blinking lights on the modem - it is responding - and the line is undamged from the construction. i am just finding it very strange that the computer worked so well before turning it off for three weeks due to the construction and upon restarting it can't connect to the internet. perhaps something was updated during that time & the ubuntu box missed it. i've pinged both the router (it is wired to the router currently) & the modem and both pings work, only the browser cannot get to the internet. locally, everything seems to be working properly.

---

### Post by paul_be on 2009-06-24
has your computer been moved???  Is the ethernet adapter pci or onboard??  If the computer was moved a pci could have been jarred a bit which may cause some intermittent issues.

---

### Post by doogiekd on 2009-06-25
i have checked all of the connections, including making sure the pci card is seated properly in the box. again, still no internet.

---

### Post by dBuster on 2009-06-25
What are you using to manage your network connections?  WICD or Network Manager?  There was a kernel update just recently and maybe, just maybe your network manager is borked.

If you can connect to the modem through the router then you should have no issues with the browser.  Unless you have a modem that is also a 4 port router then that might be a different setting.  

So you can get to the modem and or router with a ping.  Have you, and I did not see where you said you could or couldn't, tried to get to the router with the browser?  You know to see the web portal for the device.  This would rule out the browser not being able to put up a web page for you and thus make it something with the routing...  If you have a router between you and the modem then first connect to that, if you can then try to connect, once again with the browser, to the modem.

I have two devices in my setup both are capable of putting out a wifi signal and only use the routers signal for normal use, more controllable for me since I have a different internal ip mapping.  But I do enable the wifi on the modem from time to time and with that I can not get anywhere purposefully due to the settings I have.  

It is one thing to ping a device but another to actually get into the devices web portal.  If you have never done a web portal open your browser and put the ip address of the device in the address line and see if it connects.

---

### Post by doogiekd on 2009-06-25
I am using Network Manager. I actually tried WICD, (by unistalling Network Manager and installing WICD from a package download from another computer via USB stick). Same issue with WICD, no internet. I uninstalled WICD, and reinstalled Network Manager again using the method described above. (Both were complete uninstalls). 

Regarding the router and pinging: I do not have a modem that is also a router. 

YES, I can connect to the router and make changes from the web browser (192.168.1.1). However, it will not connect to the internet.

My guess is that rather this being a hardware issue,  something was updated (probably the Kernel), and that broke something. I've had this computer for awhile, and it was working perfectly the whole time.

---

### Post by lavinog on 2009-06-25
It might have been that a driver update messed up your network connection.
what network card do you have?
post the output of 
```
lspci|grep Ethernet

```

---

### Post by doogiekd on 2009-06-25
Here are the results of lspci|grep Ethernet:

00:05.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)

Please note: The problem was first with a Belkin USB Wireless dongle, which worked perfectly out of the box many months ago. When the internet stopped working, I assumed it was the dongle. I moved the computer next to the wirless router in another room AND connected the computer to the router with an ethernet cable. Same problem, no internet. So maybe both drivers were updated somehow?

---

### Post by kimberlite on 2009-06-25
According to my understanding (I am newbie) you can see only IP addresses of sites (cf. mtr -c 5 -r 74.125.127.100) and no server names. I think you have problem with your DNS setting. Did anybody asking you about the result of cat /etc/resolv.conf?

---

### Post by doogiekd on 2009-06-25
no, i can only see my local wireless router (local ip 192.168.1.1). the ubuntu box is directly connected to my wireless router with an ethernet cable. The results of cat /etc/resolv.conf are posted on the previous page (along with previously requested system information) but posted here again:

domain hsd1.wa.comcast.net.
search hsd1.wa.comcast.net.
nameserver 68.87.69.150
nameserver 68.87.85.102

I really think this is NOT a hardware issue but, but like you stated a problem with some setting or kernel upgrade. how do i fix this?

---

### Post by lavinog on 2009-06-25
I appologize I miss read your first post and thought you were able to ping with ip addresses only.
Some sites block ping requests, so pinging is not always reliable for diagnosing network connections. (ex: I can ping google, but not microsoft)

Have you tried using the live cd and see if it works...if it does, we can narrow down the issue to a software/driver issue.

Also did you say all the other computers are connecting wirelessly? There is still the possibility that the network switch in the wireless router is damaged, and not the wireless switch. I have seen a switch become brain damaged after a lightning storm, along with some of the network cards attached while the the modem still worked perfectly.  We suspect that switching components are made cheaper than the other parts.
Don't rule out hardware until you try another computer using the ethernet port.

---

### Post by doogiekd on 2009-06-27
Friends, 

I tried the good suggestion to boot from a live CD.

The Ubuntu box DOES connect to the internet from the LIVE CD. (and right from the live cd without any configuration.)

Note: I had to reset the modem and router when switching to the live CD in order to connect to the internet. It would not connect otherwise.

I have tried several times to reset the modem and router when booting directly from the ubuntu box. Again, the ubuntu box does NOT connect.

---

### Post by lavinog on 2009-06-29
Have you tried booting to an older kernel?
It does look to be a regression. It may actually be fixed with a more recent update, but without internet it would be tough to update.
You may want to do a reinstall if booting with an older kernel doesn't work.

---

### Post by dBuster on 2009-06-29
> **doogiekd said:**
> I am using Network Manager. I actually tried WICD, (by unistalling Network Manager and installing WICD from a package download from another computer via USB stick). Same issue with WICD, no internet. I uninstalled WICD, and reinstalled Network Manager again using the method described above. (Both were complete uninstalls). 

Regarding the router and pinging: I do not have a modem that is also a router. 

YES, I can connect to the router and make changes from the web browser (192.168.1.1). However, it will not connect to the internet.

My guess is that rather this being a hardware issue,  something was updated (probably the Kernel), and that broke something. I've had this computer for awhile, and it was working perfectly the whole time.


Okay, your modem, if it is a high speed modem for either DSL or Cable is essentially a router.  Only real modems where those for dialup.  We have come accustomed to calling the specific routers as modems since they are required to connect to their respective carriers signals.  

Since you can connect to the router or if you want to call it a modem, with the web browser and make changes, view setting, Etcetera, I do not believe it is a hardware issue.  You are connecting to the router via a connection which means your Ubuntu box is communicating outside of itself. 

When you are connected to the router at address 192.168.1.1 is there a statistics page which shows the IP address it has received from the provider?  Do you happen to have a set number of internal ip addresses which can be assigned by that device?  I have my router set to only assign 5 ip addresses or in essence allow only 5 to connect and pass information to keep security down and limit outsiders trying to piggy back...

There could have been something with the kernel update, no doubt, but you have tried to boot a previous version of the kernel when you get to the grub screen have you not?  If not do so and see if it is resolved.  If it is then you know the kernel update has something broken and possibly needs to get reported.  A kernel update can not break your hardware, might have bad parts causing some drivers to not work properly.

---

### Post by lavinog on 2009-06-29
> **dBuster said:**
> Okay, your modem, if it is a high speed modem for either DSL or Cable is essentially a router.  Only real modems where those for dialup.  We have come accustomed to calling the specific routers as modems since they are required to connect to their respective carriers signals.  

> **dBuster said:**
> Okay, your modem, if it is a high speed modem for either DSL or Cable is essentially a router.  Only real modems where those for dialup.  We have come accustomed to calling the specific routers as modems since they are required to connect to their respective carriers signals.  

It is perfectly fine to refer to it as a modem for dsl/cable broadband since it still MOdulates/DEModulates the signals.
[http://en.wikipedia.org/wiki/Cable_modem](http://en.wikipedia.org/wiki/Cable_modem)
[http://en.wikipedia.org/wiki/DSL_modem](http://en.wikipedia.org/wiki/DSL_modem)

Also not all cable/dsl modems have routing capabilities.

The device the op has is most likely a modem with a builtin router/access point. It is pretty common down where I live for people to have AT&T's 2wire modems w/ wireless built-in. Many of their customers don't know how to tighten the security for these things which use WEP encryption. At home I see about 15 2wire APs with more than 50% signal strength.
For better support it does help to give the details of the modem/router though...some routers are not compatible with certain devices. (ex: Nintendo wireless devices don't seem to like belkin devices from walmart.)

I did have a client once refer to their monitor as the computer and the computer as the modem...It threw me way off when they mentioned putting a cd in the modem.

---

### Post by dBuster on 2009-07-02
> **lavinog said:**
> It is perfectly fine to refer to it as a modem for dsl/cable broadband since it still MOdulates/DEModulates the signals.
[http://en.wikipedia.org/wiki/Cable_modem](http://en.wikipedia.org/wiki/Cable_modem)
[http://en.wikipedia.org/wiki/DSL_modem](http://en.wikipedia.org/wiki/DSL_modem)

Also not all cable/dsl modems have routing capabilities.

The device the op has is most likely a modem with a builtin router/access point. It is pretty common down where I live for people to have AT&T's 2wire modems w/ wireless built-in. Many of their customers don't know how to tighten the security for these things which use WEP encryption. At home I see about 15 2wire APs with more than 50% signal strength.
For better support it does help to give the details of the modem/router though...some routers are not compatible with certain devices. (ex: Nintendo wireless devices don't seem to like belkin devices from walmart.)

I did have a client once refer to their monitor as the computer and the computer as the modem...It threw me way off when they mentioned putting a cd in the modem.

I work for a telecom company and we had those 2wire modems and yes they are in essentially routers.  The modem gets an ip address from the provider and then the modem assigns your computer(s) a different ip address which is thus causing the modem to route information from one to the other.  We do not think a single port device is a router in essence since it only has one port including those 2wire models but they do route traffic thus making them routers.  Now if they were internal modems then they could possibly only grab and use one ip address for everything thus then they would not be routing traffic from one to another.  I have in 15 plus years not seen a dsl/cable modem that did not have routing capabilities but then again I have not seen every single model out there.

We no longer use 2wire where I work but still support them.  The new modems, both single and four port, are called routers by the manufacturer even.  

I am not going to get into the age old debate and I did read the wiki.  In this case though with the original post the user is having trouble getting past the modem with his ubuntu machine.  When trying to trouble shoot it is handy to try and know which device the user is actually  connecting to via http...  I personally have here at home 3 routers up and running.  One of which is a single port model which I have another wireless router connected to and then I also have one of the four port models also connected and running.  I do have a network engineer background and have private ip address ranges assigned so I do not have or use the 192.168.1.1 ip address what so ever.  I am even using an outside the norm subnet mask which would confuse most.  I even have the number of available ip addresses restricted for connecting to my networks which helps keep unwanted devices off, meaning a new device can not get an ip address.

Just my 2 cents...

---

