---
title: "Ubuntu 11.04 tethering problem"
date: 2011-05-01
forum: Networking &amp; Wireless
---

### Post by atentik on 2011-05-01
I cannot tether in the newly released Natty Narwhal (11.04) with my N900 phone. I used to tether without problem in the previous ubuntu releases: 10.04 and 10.10. But now, I cannot get it to work. I'll appreciate it if anybody with solution can please post here.

Thanks.

---

### Post by Hansjoerg on 2011-05-01
same with iphone4
have somebody a solution?

---

### Post by eddiimonster on 2011-05-01
I've been searching and trying to resolve this problem for 3 days now. As of right now I'm using easytether. I installed drivers, started app then went to shell. Entered 
Easy tether connect ********
Sudo dhclient easytether0
It brings me back to another command line instead of acknowledging it has connect. After a few trees I managed to load good before it told me it was disconnected.
If someone could upload a link to the platform tools folder containing the full adb file from Android sdk that I could download  I can other wise resolve and post a different way. Being with no internet I can not update and install the adb through sdk

---

### Post by eddiimonster on 2011-05-01
Bump

---

### Post by successor84 on 2011-05-01
I have the same problem. I'm using an Asus EEEPc and I cannot connect to my Droid X anymore. It worked fine before on the previous version of Ubuntu - 10.10.

---

### Post by jmoney47 on 2011-05-03
Anyone have an answer? I have this problem as well

---

### Post by Burner50 on 2011-05-03
I have a similar problem and I have been working on troubleshooting...

Software:
Ubuntu 11.04
Motorola DroidX running Android Version 2.2.1 (Rooted)
Wireless Tether for Root Users downloaded from Android Marketplace

Hardware:
Compaq CQ60-215DX
Atheros AR5001 (Rev 1) wireless card (All results replicated on Belkin F5D7050)

1. I just switched from Windows 7 ultimate, and had zero problems using wireless tether.

2. I can connect via wifi to my home network without fail

3. Any other device I have tried to tether to my phone works flawlessly

4. When I attempt to use Ubuntu 11.04 to my phone using wifi and Wireless Tether properly configured, Ubuntu will try to connect for about 45 seconds then apparently time out and attempt a different wireless connection.

---

### Post by Burner50 on 2011-05-03
> **Burner50 said:**
> I have a similar problem and I have been working on troubleshooting...

Software:
Ubuntu 11.04
Motorola DroidX running Android Version 2.2.1 (Rooted)
Wireless Tether for Root Users downloaded from Android Marketplace

Hardware:
Compaq CQ60-215DX
Atheros AR5001 (Rev 1) wireless card (All results replicated on Belkin F5D7050)

1. I just switched from Windows 7 ultimate, and had zero problems using wireless tether.

2. I can connect via wifi to my home network without fail

3. Any other device I have tried to tether to my phone works flawlessly

4. When I attempt to use Ubuntu 11.04 to my phone using wifi and Wireless Tether properly configured, Ubuntu will try to connect for about 45 seconds then apparently time out and attempt a different wireless connection.



Also to add... I have been using EasyTether PRO no problem


Installing 10.10 solved all my problems.

---

### Post by anthonie on 2011-05-05
> **atentik said:**
> I cannot tether in the newly released Natty Narwhal (11.04) with my N900 phone. I used to tether without problem in the previous ubuntu releases: 10.04 and 10.10. But now, I cannot get it to work. I'll appreciate it if anybody with solution can please post here.

Thanks.

Same problem here. Also on the n900. Mobile Hotspot seems to work better than before, though. Downside is it consumes so much battery power.

---

### Post by vapor216 on 2011-05-05
Adding myself to this list also.

AR9285 Wireless Network Adapter
Motorola Droid X

---

### Post by jmoney47 on 2011-05-05
Does anyone know how to make this work?

---

### Post by jmoney47 on 2011-05-06
Another bump. I really need this to work. Please help someone

---

### Post by jmoney47 on 2011-05-06
I just talked to easytether support. It seems to be a bug in their program. They are going to be fixing it soon.

---

### Post by jocefus on 2011-05-08
Same problem. GSM connection through usb with my n900 (PC-Suite Mode) worked flawlessly before 11.04. Now... nothing.

---

### Post by Rouli1 on 2011-05-08
same problem as you all...

---

### Post by kaspar_silas on 2011-05-09
The built in tethering on Cyanogenmod 7 (wired and wireless) is working fine on my phones so this really sounds like one for the app developers.


If your totally desperate could you use a virtual machine of the older ubuntu release and tether the phone to this?

---

### Post by Hansjoerg on 2011-05-10
i am using ubuntu 11.04 with a laptop, toshiba tecra
tethering works fine again with my ipone with wireless connection (the cool part)

after lots of trouble get this work, i found a solution.
goto "edit connections" and make sure you click on "ingnore" for the IPv6 connection.

---

### Post by atentik on 2011-05-11
> **Hansjoerg said:**
> i am using ubuntu 11.04 with a laptop, toshiba tecra
tethering works fine again with my ipone with wireless connection (the cool part)

after lots of trouble get this work, i found a solution.
goto "edit connections" and make sure you click on "ingnore" for the IPv6 connection.

There is no option to ignore IPv6. I am glad you get it working for you. It is not working for me and maybe countless of others.

---

### Post by Martin_sensei on 2011-05-11
I may have the same problem:

Ubuntu 11.04 trying to connect to the built-in Wireless hotspot on Android 2.2

It all worked with Ubuntu 10.10, but stopped after the upgrade.

---

### Post by mike.1803 on 2011-05-12
find here my syslog:
ay  7 19:29:28 eee NetworkManager[404]: <info> (wlan0): supplicant connection state:  scanning -> associating
May  7 19:29:28 eee kernel: [  334.071214] wlan0: direct probe to a4:ed:4e:d4:db:3f (try 1/3)
May  7 19:29:28 eee kernel: [  334.268100] wlan0: direct probe to a4:ed:4e:d4:db:3f (try 2/3)
May  7 19:29:28 eee kernel: [  334.468123] wlan0: direct probe to a4:ed:4e:d4:db:3f (try 3/3)
May  7 19:29:29 eee kernel: [  334.668078] wlan0: direct probe to a4:ed:4e:d4:db:3f timed out
May  7 19:29:38 eee wpa_supplicant[458]: Authentication with a4:ed:4e:d4:db:3f timed out.
May  7 19:29:38 eee NetworkManager[404]: <info> (wlan0): supplicant connection state:  associating -> disconnected
May  7 19:29:38 eee NetworkManager[404]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
May  7 19:29:39 eee wpa_supplicant[458]: Trying to associate with a4:ed:4e:d4:db:3f (SSID='Milestone 1438' freq=2447 MHz)
May  7 19:29:39 eee NetworkManager[404]: <info> (wlan0): supplicant connection state:  scanning -> associating
May  7 19:29:39 eee kernel: [  345.085682] wlan0: direct probe to a4:ed:4e:d4:db:3f (try 1/3)
May  7 19:29:39 eee kernel: [  345.284140] wlan0: direct probe to a4:ed:4e:d4:db:3f (try 2/3)
May  7 19:29:40 eee kernel: [  345.484118] wlan0: direct probe to a4:ed:4e:d4:db:3f (try 3/3)
May  7 19:29:40 eee kernel: [  345.684096] wlan0: direct probe to a4:ed:4e:d4:db:3f timed out
May  7 19:29:43 eee NetworkManager[404]: <warn> Activation (wlan0/wireless): association took too long.
May  7 19:29:43 eee NetworkManager[404]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
May  7 19:29:43 eee NetworkManager[404]: <warn> Activation (wlan0/wireless): asking for new secrets
May  7 19:29:43 eee NetworkManager[404]: <info> (wlan0): supplicant connection state:  associating -> disconnected
May  7 19:29:49 eee NetworkManager[404]: <info> (wlan0): device state change: 6 -> 9 (reason 7)
May  7 19:29:49 eee NetworkManager[404]: <warn> Activation (wlan0) failed for access point (Milestone 1438)

The problem has to be the 11 ubuntu...another laptop with ubuntu 10 works fine.
Could you please post you syslog part of the connection?

Best Michael

---

### Post by mike.1803 on 2011-05-12
i also disabled ip6 in the /etc/sysctl.conf

michael@eee:~$ cat /proc/sys/net/ipv6/conf/all/disable_ipv6
1

but that doesn't fix the problem...

---

### Post by si14 on 2011-05-16
I have the same problem. N900, Ubuntu 11.04

---

### Post by iscalunga on 2011-05-17
Hi guys,

I got the same problem with my iPhone 4. I simpy solved it as following:
1. edit connection
2. select edit wired connection "Auto eth ..."
3. select IPv4 Settings tabs
4. select method "Link-Local only"

Hope it helps

---

### Post by Flip101 on 2011-05-18
I have ubuntu 11.04 and a Nokia N900

i followed this tutorial to setup tethering over USB cable:
[http://www.maemonokian900.com/maemo-news/tethering-on-the-n900-%E2%80%93-part-1/](http://www.maemonokian900.com/maemo-news/tethering-on-the-n900-%E2%80%93-part-1/)

It tries to connect and then gives a message: GSM network disconnected.

Setting Link-Local option, as suggested by iscalunga, did not work for me.


Some references of the bug:
[https://bugzilla.redhat.com/show_bug.cgi?id=583691](https://bugzilla.redhat.com/show_bug.cgi?id=583691)
[https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/434737](https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/434737)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/417786](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/417786)
[http://bugs.gentoo.org/show_bug.cgi?id=348849](http://bugs.gentoo.org/show_bug.cgi?id=348849)
And in general (more bug reports): [http://lmgtfy.com/?q=GSM+modem+enabled+failed+Serial+command+timed+out](http://lmgtfy.com/?q=GSM+modem+enabled+failed+Serial+command+timed+out)

People have reported wvdial does work (but i'd rather use the default GUI stuff)
Reference: [http://forums.internettablettalk.com/showthread.php?p=804214](http://forums.internettablettalk.com/showthread.php?p=804214)

---

### Post by mike.1803 on 2011-05-19
Setting Link-Local option, as suggested by iscalunga, did also not work for me. 

@iscalunga: could you give us more informations regarding you log files? and also the output of 
cat /proc/sys/net/ipv6/conf/all/disable_ipv6

thx
michael

---

### Post by irwindesigns on 2011-05-19
> **iscalunga said:**
> Hi guys,

I got the same problem with my iPhone 4. I simpy solved it as following:
1. edit connection
2. select edit wired connection "Auto eth ..."
3. select IPv4 Settings tabs
4. select method "Link-Local only"

Hope it helps

Thanks that did the trick for my Iphone 3GS

---

### Post by Flip101 on 2011-05-20
I tried wvdial because i really wanted to make use of tethering, it worked. These are the steps i took:

1. use synaptic to install wvdial
2. open terminal
3. connect Nokia N900, select PC-Suite Modus
4. run this command: sudo wvdial Phone=*99# Username=vodafone Password=vodafone
5. enter root password

It works.
Press CTRL + C to stop the program.

Still i'd rather use the default gui stuff :/

---

### Post by ve4cib on 2011-05-23
Add me to the list of users hoping for answers on this.  I'm another n900 user, fresh install of 11.04.  Everything worked straight out-of-the-box under 10.04 and 10.10, but now I'm getting that same "GSM Disconnected" message everyone else is reporting.

I'm downloading wvdial right now.  I'll give that a go, but I'd like it if the actual network manager GUI worked like it did before.

---

### Post by Whywindows on 2011-05-23
Have found a temporary workaround :
1. Installed wvdial, GNOME PPP & related pkg
2. Run GNOME PPP, under Setup, Detect modem, close
3. Attach & setup N900 with your mobile data service provider details with panel network applet .
4. Connect with panel applet
So far been using this workaround for 3 days now. Should for any reason connection is lost and the GSM disconnected error occurs, reboot PC and detect modem again.
Works for me. Seems like the problem is in OS detecting the N900 modem automatically.

---

### Post by winwalker on 2011-05-23
Another one with the same problem.

Nobody can't find a solution? mmmm It seems to be a serious problem  :(

---

### Post by ve4cib on 2011-05-23
> **Whywindows said:**
> Have found a temporary workaround :
1. Installed wvdial, GNOME PPP & related pkg
2. Run GNOME PPP, under Setup, Detect modem, close
3. Attach & setup N900 with your mobile data service provider details with panel network applet .
4. Connect with panel applet
So far been using this workaround for 3 days now. Should for any reason connection is lost and the GSM disconnected error occurs, reboot PC and detect modem again.
Works for me. Seems like the problem is in OS detecting the N900 modem automatically.

Thanks.  This work-around works for me too.

---

### Post by gsilves30 on 2011-06-07
Hi,

Sorry to bring back a slightly old thread but I have a related issue and wanted to see if any of you ran into it and found a fix. So I am also using the easytether app on android and the ubuntu program to tether my cell phone (Samsung Galaxy S I500) to my netbook. 

Here's where it gets weird. If I run

```
>> easytether enumerate
   xyz123  returned
>> easytether connect xyz123
>> sudo dhclient easytether0

```

I have moderate success. The phone is connected and I'm able to use for example chrome and browse the web. Now here is the strange part. The device never shows up in my networking->edit connections. As a side effect of this applications like Empathy do not work.But proof of concept that I'm tethering I'm posting this right now and the only thing hooked up (I'm outside) is my phone)

Just a note I'm a bit of a ubuntu novice so it may be something easy I'm missing. Thanks in advance if anyone has tips and let me know if there is something you would like me to run to post further info.

---

### Post by nkv1 on 2011-06-18
Let me join the club of those who cant connect usb modems
this is gnome ppp log print out, and it cant connect idk why
I am useing telenor usb modem e1552
```
--> WvDial: Internet dialer version 1.61
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT*99#
--> Waiting for carrier.
ATM1L3DT*99#
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Sun Jun 19 03:51:46 2011
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 8990
--> Using interface ppp0
--> Disconnecting at Sun Jun 19 03:51:48 2011
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
```

---

### Post by eleybourn on 2011-06-19
Try - [http://askubuntu.com/questions/48710/connecting-to-wlan-freezes-system-on-asus-eee-pc-1001p](http://askubuntu.com/questions/48710/connecting-to-wlan-freezes-system-on-asus-eee-pc-1001p)

---

### Post by txapelgorri on 2011-06-29
Check this out for N900 and Ubuntu 11.04: [http://www.paranoids.at/?x=entry:entry110516-233959](http://www.paranoids.at/?x=entry:entry110516-233959)

Is not a perfect solution, but is a solution :)

Cheers, Ibon.

---

### Post by nicolasdiogo on 2011-06-30
hello

another way of getting it to work that i found was to install in N900 the app:

**Mobile HotSpot**

available from the development repos of N900

set it up to use interface USB
plug cable between N900 and laptop

start the connection in the app and it gets recognised and functional in Ubuntu Natty


i am using Natty x64 and using it to write this.

hope it helps.

---

### Post by anthonie on 2011-06-30
Apart from other things like the switch to Unity and other interface experiments, I have become increasingly concerned with the stability and workability of recent Ubuntu releases. As a result of that I switched back to Debian. 

Concidering the fact that Ubuntu nowadays requires just as much fiddling around if you're in need of an install that is a bit different from a standard, out of the box installation, I could, no longer, find myself any argument not to switch back and do all the fiddling-work at the source rather than the deviation. 

If you're not afraid of the command line, you may be better of using Debian Squeeze and leave Ubuntu for the people switching over from propriarity OS's.

---

### Post by mrsurb on 2011-06-30
> **txapelgorri said:**
> Check this out for N900 and Ubuntu 11.04: [http://www.paranoids.at/?x=entry:entry110516-233959](http://www.paranoids.at/?x=entry:entry110516-233959)

Is not a perfect solution, but is a solution :)

Cheers, Ibon.


The rmmod/modprobe works for me - the imperfection being that you have to re-enter the commands each time you want to connect.

---

### Post by txapelgorri on 2011-07-04
Hi there,

To improve the workaround mentioned before I create another solution based on udev: [http://www.sinanimodelucro.net/index.php/2011/07/04/n900-and-ubuntu-natty-11-04-64-bits/](http://www.sinanimodelucro.net/index.php/2011/07/04/n900-and-ubuntu-natty-11-04-64-bits/)

Enjoy ;)

Ibon.

---

### Post by txapelgorri on 2011-07-04
> **nicolasdiogo said:**
> hello

another way of getting it to work that i found was to install in N900 the app:

**Mobile HotSpot**

available from the development repos of N900

set it up to use interface USB
plug cable between N900 and laptop

start the connection in the app and it gets recognised and functional in Ubuntu Natty


i am using Natty x64 and using it to write this.

hope it helps.
Hi nicolasdiogo:

You mean mobilehotspot version 0.3.4? I tried it, but doesn't seem to be the same app, because what I understand when I open it is that the N900 is going to become a wifi Access point, and then it will share the 3G connection via wifi with the laptop. Unfortunately this app doesn't seem to run fine out-of-the-box (at least on my case it says "HotSpot failed to start").

Cheers, Ibon.

---

### Post by nkv1 on 2011-07-04
> **nkv1 said:**
> Let me join the club of those who cant connect usb modems
this is gnome ppp log print out, and it cant connect idk why
I am useing telenor usb modem e1552
```
--> WvDial: Internet dialer version 1.61
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT*99#
--> Waiting for carrier.
ATM1L3DT*99#
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Sun Jun 19 03:51:46 2011
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 8990
--> Using interface ppp0
--> Disconnecting at Sun Jun 19 03:51:48 2011
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
```

my USB Modem is working now
no idea what i did except performing updates that have come

---

### Post by mrsurb on 2011-07-10
> **txapelgorri said:**
> Hi there,

To improve the workaround mentioned before I create another solution based on udev: [http://www.sinanimodelucro.net/index.php/2011/07/04/n900-and-ubuntu-natty-11-04-64-bits/](http://www.sinanimodelucro.net/index.php/2011/07/04/n900-and-ubuntu-natty-11-04-64-bits/)

Enjoy ;)

Ibon.

Brilliant! Works as advertised for me. And it's an elegant solution to the problem.

---

### Post by Whywindows on 2011-07-14
Hi All,
After this mornings (GMT +8 hrs) Ubuntu maintenance download of abt 54MB including latest kernel, my earlier reported problem & solution of recognizing N900 seems to be resolved. The network applet immediately recognizes my Nokia C6-00 as a USB modem without any other manual detecting process. I used the Gnome PPP dial up tool before to manually detect the phone. Have not tested with N900 yet cos only one active data SIM at the moment.
Any one else experience this improvement ?

---

### Post by ehaley on 2011-07-20
I have the problem that 11.04 will not tether to my cell phone I can put 10.10 in and it will connect fine 11.04 will connect to other wireless networks but not to cell phone wireless tethering like 10.10 it would be nice if could put manager from older ubuntu in 
or what ever the difference is because it is all over the web about people having this problem with no results to fix it.
with 10.10 I can even run from the cd and connect but 11.04 will not connect from cd or after install  :confused:

---

### Post by nicolasdiogo on 2011-07-27
honestly

Ubuntu is starting to wearing thin on me.
between versions - you can not expect thing to improve.
things just 'change'

---

### Post by thedarkdonut on 2011-07-31
I got mine working surprisingly.  I didn't want to roll back to 10.04 or 10.10.  Out of the two things I did it might have been the latter that fixed it.

First I installed kernel 3.0.  Then since my wireless driver, AR9285, didn't install with 3.0 I installed the drivers from  [**here**]("http://linuxwireless.org/en/users/Drivers/ath9k#Get_the_latest_ath9k_driver") for kernel 3.0.  Worked like a champ.

---

### Post by ehaley on 2011-09-16
11.10 didn't fix the problem so still have to use 10.10 or earlier

---

### Post by d3ejmz on 2011-10-05
This is the third time Ubuntu has broken something that was working for me in a previous version. What is this obsession with fixing stuff that isn't broken?

Come on, Ubuntu... I know you are better than this.

I've been all over the net looking for a fix to this problem, and the only ones that work require a USB cable connection. Well, that won't work for me. I need to connect 2 computers at once to my droid 2.

Please, devs... put it back the way it was? or at least provide some documentation as to what was changed so WE can fix it. And don't hide that documentation! (it's probably in there somewhere, hidden deep in the bowels of the system)

---

### Post by graufl on 2011-10-12
I am using a ZTE Blade with Cyanogen 7.1

Tethering works fine and without problems on Win7

With Ubuntu 11.04 my laptop connects with the ZTE (Wireles or USB connection is built up) BUT the ZTE is not used for DNS lookup.

So I can theoretically connect to each server on the web but only as long as I use the IP adresses, what is not really an option.

---

### Post by Maros_Norge on 2011-12-05
Same issue, Xubuntu 11.04 trying to tether wifi (or usb) from a HTC Glacier. Any ideas?

---

