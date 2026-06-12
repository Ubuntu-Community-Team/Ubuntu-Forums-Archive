---
title: "How to install kismet for BCM43XX!!!!!!"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by reltx on 2009-04-11
How do I install kismet on Ubuntu 8.10 on my dv6105ca.  I have a BCM4311 card and I don't understand how the " ./configure" and "make" comands work.  Can someone provide a complete n00b guide as to how to do this.

I already installed the drivers from the "How To: Broadcom BCM43xx" thread.

PLEASE HELP!

---

### Post by chili555 on 2009-04-11
Kismet is in the Ubuntu repositories and so there is no need to go through the agony of ./configure, make, etc. Simply open a terminal and do:```
sudo apt-get install kismet
```Then, when you want to set up your */etc/kismet/kismet.conf*, there is a nifty README:```
less /usr/share/doc/kismet/README.gz
```You will be especially interested in Sections 9 and 12 of the README. Post back if you need help.

---

### Post by reltx on 2009-04-12
thnx

---

### Post by chaser469 on 2009-08-13
hi im a complete noob to ubuntu, and am pulling my hair out trying to get kismet up and running

' You will be especially interested in Sections 9 and 12 of the README. Post back if you need help. 	'

i am trying to configure kismet.conf.in. apparently i need to specify the: source, and suiduser. 

eg. how do i specify the source from this:

*-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:db:68:65
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.100 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:4d:31:64
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 12:a5:b8:f3:0b:d2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

what exactly do i need to change the in the kismet.conf.in file and to what exactly.
please, any help would be greatly appreciated.

---

### Post by chili555 on 2009-08-14
The suiduser is your regular user name. Here are the relevant sections from my kismet.conf:```
# User to setid to (should be your normal user)
suiduser=chili
```And, also:```
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=ipw3945,wlan0,Intel
```Please post back if you have more questions.

---

### Post by governorphd on 2009-09-17
I've installed Kismet, changed the kismet.conf.  Now, How do I start kismet?
Or, where is it?

---

### Post by governorphd on 2009-09-17
How do I insure that Kismet is installed correctly?
I'm trying to start it with Terminal, and I get 'suid priv-dropping disabled'
In Kismet.conf, I use my user name that I use to log on to Ubuntu, Is that correct?
Kismet needs to have root access.  The README file says use 'make install' to grant this.  But on the forums, most say use 'sudo apt-get install kismet' , which is how I installed Kismet. does doing it this way grant root access?  

Also, my kismet.conf file is not in the default place, it's in /etc/kismet/kismet.conf
Is this a problem?
As behind as I may seem, this is still very fascinating to me.  I hope I can get this to work!
Thanks in advance.

---

### Post by governorphd on 2009-09-17
How do I insure that Kismet is installed correctly?
I'm trying to start it with Terminal, and I get 'suid priv-dropping disabled'
In Kismet.conf, I use my user name that I use to log on to Ubuntu, Is that correct?
Kismet needs to have root access. The README file says use 'make install' to grant this. But on the forums, most say use 'sudo apt-get install kismet' , which is how I installed Kismet. does doing it this way grant root access? 

Also, my kismet.conf file is not in the default place, it's in /etc/kismet/kismet.conf
Is this a problem?
As behind as I may seem, this is still very fascinating to me.  I hope I can get this to work!
Thanks in advance.
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=7964137") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=7964137")

---

### Post by chili555 on 2009-09-17
> **governorphd said:**
> I've installed Kismet, changed the kismet.conf.  Now, How do I start kismet?
Or, where is it?Open a terminal and do:```
sudo kismet
```Post back if you get stuck.

---

### Post by chili555 on 2009-09-17
> **governorphd said:**
> How do I insure that Kismet is installed correctly?Well, if it starts and runs and sees networks, it's installed correctly.
> I'm trying to start it with Terminal, and I get 'suid priv-dropping disabled'
In Kismet.conf, I use my user name that I use to log on to Ubuntu, Is that correct?Yes. Can we please see that section of your kismet.conf?
> Kismet needs to have root access.  The README file says use 'make install' to grant this.  But on the forums, most say use 'sudo apt-get install kismet' , which is how I installed Kismet. does doing it this way grant root access? Not entirely. Start it with:```
sudo kismet
```> Also, my kismet.conf file is not in the default place, it's in /etc/kismet/kismet.conf
Is this a problem?I believe this is the default location for Ubuntu.> As behind as I may seem, this is still very fascinating to me.  I hope I can get this to work! Thanks in advance.Post back if you need more help.

---

### Post by governorphd on 2009-09-17
In a terminal I used:
sudo kismet

Here's what I get:

Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (Broadcom): Enabling monitor mode for b43legacy source interface eth1 channel 6...
FATAL: Failed to set monitor mode: Invalid argument.  This usually means your drivers either do not support monitor mode, or use a different mechanism for getting to it.  Make sure you have a version of your drivers that support monitor mode, and consult the troubleshooting section of the README.
Done.

README file says to patch the drivers.  How do I do this?

It also says to make sure that there are no copies of the drivers in /lib/modules/kern-version/ directory.  
There are 2 directories in /lib/modules, 2.6.27.7.generic and 2.6.28-15-generic.  

Question:  Are these what is meant by 'kern-version?  Should they both be there?  

Here is how I set my kismet.conf file:

# User to setid to (should be your normal user)
suiduser=governor

# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=b43legacy,eth1,Broadcom

Is this correct?   

When I go to System-Administration-Hardware Drivers,
There is one driver listed that is enabled:  'Broadcom STA wireless driver'

What are b43 and b43legacy?  The Capture Sources section of the README file says
to use one of these.

When I look at wireless connection information it says:
Interface: 802.11 wifi (eth1)
Driver: wl
Security: WEP

This is where I'm at, and what I'm working with, along with the fact that I'm using a Compaq Presario running Ubuntu 9.04.
The wirless card and driver are working, I'm online.  It's just that I want to run Kismet, and can't yet.
Also now that I know how to start it, even though it isn't working yet, afterwards my browsers stops working.  I can't navigate to another page after trying to start kismet?

Wow!  I hope you can help me.

---

### Post by chili555 on 2009-09-18
> # YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=[COLOR="Red"]b43legacy[/COLOR],eth1,BroadcomWell, it's not correct if the driver you are actually using is *wl*. Kismet needs monitor mode in order to operate. Not all cards will go into monitor mode, however. I suspect yours, using *wl*, is one of them. Let's try:```
sudo ifconfig eth1 down
sudo iwconfig eth1 mode monitor
```Any errors or complaints? You can confirm if it went into monitor mode with:```
sudo iwconfig eth1
```We need to get this determined before we can fix (maybe) Kismet.

---

### Post by governorphd on 2009-09-19
No luck, I got errors.  
Reading the forums it seems that this STA driver will not go into monitor mode.
I should download and intall the b43 driver, 32 bit for my card.
That is where I'm at now.  I think I have found where to download this driver, now I am going to try to install it now.

Question:  If I'm asked what kernel version I'm using, how do I answer this?
I have in my /lib/modules directory, 2 folders:  2.6.27-7-generic and 2.6.28-15-generic.
What are these?  Are they kernel versions?  Which one should I be using?

Also, if I'm successful in downloading the driver, shouldn't I see it in System-Administration-Hardward Drivers?  

Thanks for getting back to me,  I'll keep you posted on my progress, which is slow, but advancing.

---

### Post by chili555 on 2009-09-19
> I should download and intall the b43 driver, 32 bit for my card.
That is where I'm at now. I think I have found where to download this driver, now I am going to try to install it now.It should be in your system now. Please do:```
sudo updatedb
locate b43.ko
```This will take a few moments; please be patient.> If I'm asked what kernel version I'm using, how do I answer this?You can do:```
uname -r
```Ordinarily, the boot process will automagically boot the newest kernel, which is what you want. It helps to have an older kernel on the system so that if you experiment so much that your system won't even run properly, you can interrupt the boot process at the GRUB menu and boot into your older, working kernel.

Off topic, that safety net has not yet been announced for Windows 7, I guess...

Let's see if we can use *b43.*  Please do:```
sudo rmmod -f wl
sudo modprobe b43 ssb
iwconfig
```Did *b43* attach to your card? You can tell if you have a wireless interface; it may be wlan0 instead of eth1.

---

### Post by governorphd on 2009-09-19
Here's my results:

governor@ubuntu:~$ uname -r
2.6.28-15-generic


governor@ubuntu:~$ locate b43.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/b43/b43.ko
/lib/modules/2.6.28-15-generic/kernel/drivers/net/wireless/b43/b43.ko




governor@ubuntu:~$ sudo modprobe b43 ssb
FATAL: Error inserting b43 (/lib/modules/2.6.28-15-generic/kernel/drivers/net/wireless/b43/b43.ko): 
Unknown symbol in module, or unknown parameter (see dmesg)

I looked at the results of dmesg, and that was scary! Not sure what to do now.
Also, removing the wl driver took me offline. 
So, I went to Sys-Admin-Hardware Drivers, and b43 was there!
I activated it, and BAM, back on line!
So now I have the b43 driver!!

So now I will try to insert it again.

It worked, I think, at least no error messages after I did sudo modprobe b43 ssb.

Then I did iwconfig:

governor@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"9IY75"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1F:90:CB:AE:24   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=78/100  Signal level:-55 dBm  Noise level=-68 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

You said that my interface may have changed, so I looked at the b43 driver connection info, and it did change to wlan0.
So I edited the kismet.conf file with; source=b43,interface=wlan0,Broadcom

I then did:  sudo kismet

and...................DAMN!   YOU ARE GOOD!  IT WORKS!!!!
Thanks for hanging in there.
Of course I don't have a clue how to use kismet.  But the first step is done.  It works!!!
Thanks again.  I appreciate your time and efforts, and especially, your patience!

---

### Post by chili555 on 2009-09-19
Whoa! Slow down a bit, there Guv...What is going to load up again upon reboot? You might try rebooting and see if you have eth1 or wlan0. If it is wlan0, then you are all set, if not, we need to take some remedial steps. Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add a single line:```
wl
```Proofread, save and close. Then do:```
sudo gedit /etc/modules
```Add two lines:```
b43
ssb
```Proofread, save and close. Now when you boot, the proper modules should load.

Good luck and have fun!

---

### Post by governorphd on 2009-09-19
How should I verify that I am using wlan0 now instead of eth1?
After rebooting the connection info says interface is wlan0.

I lso did:
sudo lshw -C network       (after rebooting and here are the results:)

*-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb

I think we did it.  If so, then the lines that may need to be added to blacklist and module files should already be there?  I will check them now.

---

### Post by chili555 on 2009-09-19
> I think we did it.I agree.> the lines that may need to be added to blacklist and module files should already be there?Not unless you put them there, but it really doesn't matter if it works correctly at boot. No need to fix what isn't broken. As long as it works correctly, there is no need to add anything.

---

### Post by governorphd on 2009-09-19
Network works fine, and kismet is now working.  any suggestions on a good 'How to' for kismet?
Also, there is one problem, I think.  When I start kismet, afterwards, I cannot use load any new pages with firefox?  The network still works, I can go backwards, but I must reboot to be able to load any new pages.  Is this normal for after using kismet?

---

### Post by chili555 on 2009-09-20
You are only able to backwards because you are no longer connected! Kismet puts your wireless card into monitor mode. In order to access the network, it needs to be in managed mode. Some cards work fine, some don't. Yours needs an extra step. First, bring the interface down:```
sudo ifconfig wlan0 down
```Now put the card back in managed mode:```
sudo iwconfig wlan0 mode managed
```Bring the interface back up:```
sudo ifconfig wlan0 up
```Some cards seem to respond better to:```
sudo ifdown wlan0
sudo iwconfig wlan0 mode managed
sudo ifup wlan0
```> any suggestions on a good 'How to' for kismet?Not any other than the README which is scant and assumes you know already! I just played with it and read the pop-up menus (press h). 

I think it's a tool used by password crackers, which I do not endorse. They always justify it by explaining that they want to audit the security of their own network. I say that if you have all unnecessary ports closed, WPA2 with a strong password and both a hardware firewall (in the router) and a software firewall (in the computer) then they already have done all they can reasonably do. A determined hacker ***will***, eventually, get in if he tries hard enough and long enough. However, as you will see when you play with Kismet a bit, there are plenty of WEP or completely unencrypted networks on your very block! The hackers will usually move on to one of those. End rant.

I have used it a few times at motels, coffee shops and my wife's doctor's office to see if I can easily locate a guest access point without encryption.

---

### Post by governorphd on 2009-09-20
You know, I piddled around and realized that I wasn't connected.  And I went back thru my notes and tried  the command to take the network down.  It didn't work because I used iwconfig, instead of ifconfig wlan0 down.  So, when you spell things correctly they tend to work so much better.

And as far as hacking, I respect people and their property, becuase I would hope to get the same back.  Although I would like to be able to see if I can get online when traveling.  Just to see if I can do it, without causing anybody any harm. 

 Actually, this is my first laptop, and I am just fascinated with the all this computing power being portable!  This is a great new toy!  And I'm glad I chose Ubuntu for an OS.  It was made for me.  I like trying new things, especially, programs.  Kismet was a challenge, but thanks to you, and this forum, and persistance, I got it working.  

But more important, I learned a hell of a lot about Ubuntu.  I'm hooked!  Thanks again!
I came, I saw, I Ubuntu!!!!

---

