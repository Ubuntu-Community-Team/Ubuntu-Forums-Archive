---
title: "Linksys WUSB100 wireless card working in Linux."
date: 2009-03-19
forum: Networking &amp; Wireless
---

### Post by Paul Paul on 2009-03-19
I managed to get the LinkSys wusb100 USB wireless adapter to work in Debian Linux. This will probably apply the same way in Ubuntu so I thought I would share my experience since these forums were very helpful to me.

I am by no means an expert at this but it does work. I hope this will help others.

Please note that this was posted in March 2009 and works for the RangePlus Wireless USB adapter version 1.0. In time things will change (and hopefully improve!)

You need the RT2780USB driver source code from [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html) You will need to compile this on your computer. 

I also needed the Firmware RT2870USB from the site above and install wireless-tools from your repository. The firmware is a proprietary binary. I noticed there is a rt2870.bin included in the source code under /common/ but I don't know if this one is used. I used the one from the link off the ralink site. I can't even say if the bin file is even needed. Beware that compiling will recreate the folder in /etc/Wireless.

Read the README_STA that comes with the  RT2780USB driver source code.
I set  'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y' in the config.mk file as per the readme but I can't say I understand exactly how this works.

Plug in the WUSB100. Run lsusb and look for its ID. You should see 
ID 1737:0070 Linksys

If not you need help from elsewhere.

Run dmesg. You should see “ Manufacturer: Cisco-Linksys” etc. If not, you need help from elsewhere. Beware if you get a low power warning. I did because I had too much running on one usb port. I simply plugged it into an empty port and checked dmesg again. No warning.

So here's the trick, the magic bullet that will put you dead in the water unless you know it. The source code does not list the USB ID for the WUSB100 and thus the module will never associate with it. In other words, your card will be ignored no matter how hard you try. But if you add the necessary USB ID into include/rt2870.h and compile with that mod, it will work. So add

	{USB_DEVICE(0x1737,0x0070)}, /* LinkSys */	
	\
to  include/rt2870.h before compiling (search for #define RT2870_USB_DEVICES). This matches the result from lsusb (ID 1737:0070 Linksys) but don't forget the 0x parts.

Compile as per the read me. make install as root. Check >modprobe -l | grep  rt2870sta 
If not there then do a  >modprobe rt2870sta

Look in /etc/Wireless. You should see a folder called RT2870STA. Inside there should be RT2870STA.dat file. You will need to configure this. Also you should put the rt2870.bin file in this folder. I set it to execute permissions but I don't know if this is needed. Below I list my settings for  RT2870STA.dat I have a LinkSys N access point (wrt160N) running WEP because I have old cards in other computers. WEP is NOT secure (hacked in under 3 minutes). If you can, use the newest WPA security. So my configuration may be different from yours. Read the iwpriv_usage.txt file that comes with the source code .

HUGE SUGGESTION: Get it working without security enabled FIRST, then enable security. Otherwise if it does not work, you will have no idea why. Also, you may want to test your card in Windows if you have an old dusty Windows machine kicking around (or *for* kicking around). 

When you plug the usb card in, you should see rt2870sta listed when you do a >lsmod. If you do not you are dead in the water and need help from elsewhere. Check dmesg for clues.

So, in theory your device is ready to function but you need to configure it. This took me hours of tinkering but in the end I managed to get it working. My mistake was enabling security before having it working. Once I turned off security and got it working then I knew my problem was with the security settings and not the rest of my setup. 

Note that the WEP key must be 10 or 26 characters. Dmesg will tell you if you have anything else. Always check dmesg. I repeat, always check dmesg (or you system logs).

Also, i modified /etc/modules by adding this line:
alias ra0 rt2870sta

and modified the /etc/network/interfaces file as per below. I could never get it to work without the iwpriv settings (which comes with wireless-tools). Use iwconfig to see what is going on. Nothing worked until I added the sleep lines which someone suggested on another forum. You can execute the  iwpriv*commands manually from the command line. ifup ra0 and ifdown ra0 should now work.

BTW, iwconfig lists 65Mb/s. I wish this was faster. Any tips appreciated or maybe this is all the card can do?

While I am no expert in this area I hope this posting will help others. There may be better ways of getting this working, if so, please post them. And lets keep pushing the manufacturers for Linux driver support!

Good luck,
Paul


My /etc/network/interfaces file (relevant section):

iface ra0 inet dhcp
	pre-up ifconfig ra0 up
	pre-up sleep 1	
	pre-up /sbin/iwpriv ra0 set NetworkType=Infra
	pre-up sleep 1	
	pre-up /sbin/iwpriv ra0 set AuthMode=SHARED
	pre-up sleep 1	
	pre-up /sbin/iwpriv ra0 set EncrypType=WEP
	pre-up sleep 1	
	pre-up /sbin/iwpriv ra0 set DefaultKeyID=1
	pre-up sleep 1	
	pre-up /sbin/iwpriv ra0 set Key1="1928374650"
	pre-up sleep 1	
	pre-up /sbin/iwpriv ra0 set SSID="softwind"
	pre-up sleep 1



My  RT2870STA.dat file (relevant parts):

#The word of "Default" must not be removed
Default
CountryRegion=0
CountryRegionABand=7
CountryCode=CA
ChannelGeography=1
SSID=softwind
NetworkType=Infra
WirelessMode=6
Channel=1
AuthMode=OPEN
EncrypType=WEP
WPAPSK=
DefaultKeyID=1
Key1Type=0
Key1Str=1928374650
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=

---

### Post by s7er01ds on 2009-10-11
Just wanted to stop in and say thank you for this help, and would like to keep your link updated, so here is the current link to get what is needed for wusb100

_General:_
[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

_Driver:_
[http://www.ralinktech.com/download.php?t=U0wyRnpjMlYwY3k4eU1EQTVMekE0THpJMEwyUnZkMjVzYjJGa01ERTFPVGs0TmpRMk1DNWllakk5UFQweU1EQTVYekE0TWpCZlVsUXlPRGN3WDB4cGJuVjRYMU5VUVY5V01pNHlMakF1TUM1MFlYST1D](http://www.ralinktech.com/download.php?t=U0wyRnpjMlYwY3k4eU1EQTVMekE0THpJMEwyUnZkMjVzYjJGa01ERTFPVGs0TmpRMk1DNWllakk5UFQweU1EQTVYekE0TWpCZlVsUXlPRGN3WDB4cGJuVjRYMU5VUVY5V01pNHlMakF1TUM1MFlYST1D)

_Firmware:_
[http://www.ralinktech.com/download.php?t=U0wyRnpjMlYwY3k4eU1EQTVMekF6THpNeEwyUnZkMjVzYjJGa056Z3hNamt4TURjd09TNTZhWEE5UFQxU1ZESTROekJmUm1seWJYZGhjbVZmVmpnPUM%3D](http://www.ralinktech.com/download.php?t=U0wyRnpjMlYwY3k4eU1EQTVMekF6THpNeEwyUnZkMjVzYjJGa056Z3hNamt4TURjd09TNTZhWEE5UFQxU1ZESTROekJmUm1seWJYZGhjbVZmVmpnPUM%3D)


Also: I noticed a couple of places u entered 2780, might want to change those to 2870.

Ty again for the help.

---

### Post by jandante on 2009-10-14
Hi,

My WUSB100 is recognized by Ubuntu 9.10.

At least i suppose, because i can see all available networks in range. (looks the same as the windows machine).

But everytime i try to connect to my access point it keeps asking for my WEP key. Then it try's to connect for 30 seconds and it asks the Wep key again. I've tried entering it in HEX and ASCII but no luck so far.

The access point can handle more then one computer (2 windows laptops, 1 desktop and ps3 at the same time works) but when i try ubuntu alone or in combination it keeps asking for my password.

the only strange thing I found was that the IP address i get from the access point (on a windows computer) is something like 78.21.208.90 and for another one 78.21.208.91. I didn't know the ip 78.21.208.XXX is for home use. I'm used to 192.168.1.1.

If networks are recognized by network-manager does this mean ther is nothing wrong in ubuntu but with my access point...???

---

### Post by jandante on 2009-10-14
Tried some new forum topics google searches but no answers...

I'm close I know it. Nobody had experience with this on ubuntu 9.10 or with the weird IP address?

according to this: [http://en.utrace.de/ip-address/78.21.208.91](http://en.utrace.de/ip-address/78.21.208.91) it belongs to my provider. But isn't it so that you get one ip like that and the access point uses the 192.168.1.XXX for computers after it.

Or should i put a router after my access point and is my access point ment for 1 computer?

thanks in advance

---

### Post by jandante on 2009-10-14
OK this is really annoying me now !!

Does anybody knows an USB stick that works out of the box for linux?

---

### Post by LaJuan on 2009-10-25
I went to the site and I can't seem to find that download. It's not there any more. Any ideas on how I can get my WUSB100 to work? I'm using 9.04 Ubuntu.

Thanks,

LaJuan

---

### Post by bkratz on 2009-10-25
> **LaJuan said:**
> I went to the site and I can't seem to find that download. It's not there any more. Any ideas on how I can get my WUSB100 to work? I'm using 9.04 Ubuntu.

Thanks,

LaJuan

The Replacement links given in post 2 seem to work for me.
Try those!

---

### Post by panamabill on 2009-12-11
I'm glad to see so much effort going into helping fix issues with 9.10, however, I know my limitations somewhat and will never be able to follow all those instructions without some sort of computer training course. I've been messing with Ubuntu for a couple of years now and can do some "copy/paste" type commands but "Holy tree frog Batman", and....with two separate issues. The WUSB100, and the graphics card accelerator hanging problems. Whew!!

---

### Post by johnsmyrna on 2009-12-11
> **jandante said:**
> OK this is really annoying me now !!

Does anybody knows an USB stick that works out of the box for linux?

A Belkin FSD7050.  It is sold at Walmart.  My on-board wireless quit working and I was at a friend's dog sitting who just happened to have the card so I tried it out and it was recognized.  Worked so I bought one.  - Running Ubuntu 9.10 - upgraded from 9.04 non clean upgrade.

---

### Post by jjrjr1 on 2010-01-28
Hi
 
Just wondering if this post is still alive.
 
I am trying to get a linksys WUSB600N up and running on Ubuntu Version 9.10.
 
I have downloaded the current deiver versions from ralink.com
 
lsusb shows the device 
 
after compile and install
 
I run the /sbin/insmod rt2870sta.ko
 
No errors yet....
 
If I run modprobe -l | grep rt2870
 
The module shows installed in the kernel like so
 
kernel/drivers/staging/RT2870STA/rt2870sta.ko
 
Now here is where it fails...
 
I run 
 
/sbin/ifconfig ra0 inet 192.168.1.102 up
 
I get the following error
 
SIOCSIFADDR: No Such Device
ra0: Error while getting interface flags
ra0: Error while getting interface flags
No Such Device.
 
Any ideas would be appreciated.
 
Thanks
 
John

---

### Post by jjrjr1 on 2010-01-28
Hi
 
Just a post to get me subscribed here.

---

### Post by jjrjr1 on 2010-01-31
Hi
 
Thought I would post a link to the solution here.
 
Cili555 & I (and an unknown poster) got it to work perfectly
 
[http://ubuntuforums.org/showthread.php?t=1392957](http://ubuntuforums.org/showthread.php?t=1392957)
 
Have Fun..

---

### Post by snugglenutz on 2010-03-19
I followed this how-to & it went beautifully.  Enjoy.

[http://ubuntuforums.org/showpost.php?p=8591348&postcount=6](http://ubuntuforums.org/showpost.php?p=8591348&postcount=6)

---

### Post by yrhen on 2010-04-12
So did I. And it seems to work: the Wusb100 is operating and with wicd in stead of networkmanager I can hook up to my network. But connection is highly variable. 44% and continuously varying between 37% and 86% - even when I am on top of the AP. 
With a Wusb100V2 should I try the 3070 in stead?

---

### Post by ki4anr on 2010-05-01
This is the best solution I have found to the WUSB100v2 issue. It seems that Lucid 10.04 & Karmic 91.0 both have the firmware and drivers already installed, so all that is needed is to copy/paste into the terminal with the instructions from the link below to get the kernel to recognize it. I did not have to download anything from the Ralink site, just using the terminal commands below, it started working flawlessly. Thanks to all who brought this to the forum. I used it in 9.10 and now in 10.04 with great results!

Sincerely,

Kevin


> **snugglenutz said:**
> I followed this how-to & it went beautifully.  Enjoy.

[http://ubuntuforums.org/showpost.php?p=8591348&postcount=6](http://ubuntuforums.org/showpost.php?p=8591348&postcount=6)

---

### Post by jmkdenver99 on 2010-05-11
[SIZE=4]Hay! **ki4anr** and all having problems with the WUSB100 Stick. I also found the link:[/SIZE]
[[SIZE=4]http://ubuntuforums.org/showpost.php?p=8591348&postcount=6[/SIZE]]("http://ubuntuforums.org/showpost.php?p=8591348&postcount=6")[SIZE=4] worked yet again. I have been trying for 2 weeks and ready to pull my hair out. I FINALLY! came upon this link. I used the commands posted to terminal and it is awesome. Got my WUSB100 working flawlessly in Ubuntu 10.4.[/SIZE]
[SIZE=4][/SIZE] 
[SIZE=4]NOW JUST GOTTA DEAL WITH THE FREEZE UP ISSUES! LOL.[/SIZE]
[SIZE=4]Thanks to all who keep posting useful links!!![/SIZE]
[SIZE=4][IMG]http://ubuntuforums.org/images/statusicon/post_old.gif[/IMG][/SIZE][SIZE=4] 1 Week Ago [/SIZE][SIZE=4]  #[/SIZE][**[SIZE=4][COLOR=#000000]15[/COLOR][/SIZE]**]("http://ubuntuforums.org/showpost.php?p=9212833&postcount=15")[SIZE=4] [/SIZE][[SIZE=4][COLOR=#000000]ki4anr[/COLOR][/SIZE]]("http://ubuntuforums.org/member.php?u=465312")

[SIZE=4][IMG]http://ubuntuforums.org/images/statusicon/post_old.gif[/IMG][/SIZE][SIZE=4] 1 Week Ago [/SIZE][SIZE=4]  #[/SIZE][**[SIZE=4][COLOR=#000000]15[/COLOR][/SIZE]**]("http://ubuntuforums.org/showpost.php?p=9212833&postcount=15")[SIZE=4] [/SIZE][[SIZE=4][COLOR=#000000]ki4anr[/COLOR][/SIZE]]("http://ubuntuforums.org/member.php?u=465312")

---

### Post by plaras444 on 2010-05-14
can someone just upload the compilled to lazy to do all this work -_- and the download links are dead

---

### Post by tooCanad on 2010-11-23
[http://ubuntuforums.org/showpost.php...48&postcount=6](http://ubuntuforums.org/showpost.php...48&postcount=6)


Awesome.

Straightforward and functional.

Thanks  TC

---

### Post by blukid on 2011-02-04
Hi, greenhorn here, having same issue. WUSB100 can see the networks but not connect (using 10.10). When I get home I will try the solution above (originally from flash63), but if it doesn't work I have a question. I downloaded the drivers and firmware on another computer and moved them to my Ubuntu machine, but I don't know where to extract them to (is there a specific location the drivers and firmware need to be extracted to?). Thanks to anyone who answers, if anyone's still checking this thread lol.

---

