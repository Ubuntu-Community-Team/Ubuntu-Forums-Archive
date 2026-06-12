---
title: "Solution to Broadcom 43xx Card Problem (12.04 - Precise Pangolin)"
date: 2010-10-24
forum: Networking &amp; Wireless
---

### Post by Sef on 2010-10-24
Problem in Precise Pangolin 12.04 with the Broadband 43xx Wireless Card: Unable to download firmware for wireless. (Also works for 11.10, 11.04, 10.10 and 10.04)

From the 'Additional Drivers' section:

> This package contains Broadcom 802.11 Linux STA wireless driver for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-basedhardware.Possible Solutions:

**Solution 1:** After installing with the alternate cd, I needed a cable and after updating, I was able to download the STA driver through the 'Additional Drivers' section.

**Solution 2: **Another option is [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers").

**Solution 3**: System > Administration > Synaptic Package Manager > Search: firmware-b43-lpphy-installer > Click Mark > Click install > Close (This has been removed starting with 11.10 - Oneiric Ocelot. It may be installed with the Ubuntu Software Manager.)

Kontza found the [solution]("https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/651010") (post #3), so thank him for it.

This solution fixed this problem on my Dell Inspiron 1545 with a Broadcom 4312 card. (Card Tech Specs: 0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01))

---

### Post by konsta82 on 2010-10-24
I already installed it,with all dependencies on my dell 1525 but in's not working on Kubuntu. On same laptop,ubuntu partition,evetything is fine.
Wired,isn't it ?!?

---

### Post by johnnytm on 2010-10-25
I also have an Inspiron 1545, with the same bcm4312 wireless card. I have never used the b43 driver, nor have I ever used fwcutter. All I have ver done is connect the wired connection right after install and enabled the sta driver. Any other time, even in prior releases, The b43 driver has caused me nothing but trouble and complication. I am really confused as to why so many people have had problems using the STA driver when it has always been such a straightforward simple solution.

---

### Post by Shepski4 on 2010-10-26
Thank you!

---

### Post by david.earney on 2010-10-29
I am new  to Linux, and Ubuntu. Two nights ago while on irc.freenode.com #kubuntu I was assisted by EagleScreen in fixing this problem. He has the same BCM4312. 

I was using the b43 driver by default in the install, and while my wireless NIC could detect networks, it could not complete the authentication process. 

Updating to the STA driver, and restarting fixed all, and now I'm starting to get happy about the switch to Linux. 

Now, if I can just find a fix for Bluetooth.....but that's another thread. 

This fix worked on my Dell Latitude e6500.

---

### Post by Darkmagic on 2010-10-30
> **johnnytm said:**
> I also have an Inspiron 1545, with the same bcm4312 wireless card. I have never used the b43 driver, nor have I ever used fwcutter. All I have ver done is connect the wired connection right after install and enabled the sta driver. Any other time, even in prior releases, The b43 driver has caused me nothing but trouble and complication. I am really confused as to why so many people have had problems using the STA driver when it has always been such a straightforward simple solution.

How did you install the STA driver and enabled it? Could you show me the steps (or maybe a link)?

---

### Post by johnnytm on 2010-10-30
> **Darkmagic said:**
> How did you install the STA driver and enabled it? Could you show me the steps (or maybe a link)?
I never really did anything Right after I installed Ubuntu I connected my ethernet card. awith the wored connection active now I went to system-->administration-->additional drivers My computer then did a search for availabe drivers and 2 drivers showed up, there was a b43 driver and the sta driver. I clicked o the sta driver and then pressed the activate button. After that all worked well. But I would recommend NOT using the b43 driver unless absolute last resort. I had that problem before. If you want the link where you can download the drivers from t not a problem, But the driver would have to be built first. Try this first though
```
 sudo apt-get --purge remove bcmwl-kernel-source
 sudo apt-get install patch  
 sudo apt-get install bcmwl-kernel-source         
 
``` if it still doesn't  work you can try
```
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source
```
One line at a time of course

---

### Post by vsh3r on 2010-10-31
Hi,

Is anyone else seeing some connectivity issues with the Broadcom BCM43224?  Is seems to connect just rather slowly compared to when I start the system with OSX.

V$H.

---

### Post by solnyshok on 2010-11-01
sudo iwconfig eth1 rate 54Mb

where eth1 is my wireless card
that fixes connection speed. but Icannot go higher for N speeds

---

### Post by kerosine on 2010-11-02
this solution doesn't work in my case.:(

---

### Post by sadeghi on 2010-11-02
After upgrading to 10.10 my wireless was gone. The wireless indicator was on but no success at connecting to network.
But after the following changes everything was fine:
```

sudo rmmod bc44
sudo rmmod bc43
sudo rmmod wl
sudo modprobe wl

```

---

### Post by blindfury37 on 2010-11-03
I just recently installed 10.10 and new to ubuntu.
I have a Dell Inspiron 600m with a broadcom 4306.

I was able to use another guide I found on here to get the wifi card working and it connects to open networks and WEP networks fine but I can't get it to connect to any WPA/WPA2 networks. Does anyone know any fixes for this?

Thanks in advance.

---

### Post by vsh3r on 2010-11-03
Hi,

My Broadcom WIFI will not reconnect to a *NEW NETWORK* after returning from Sleep Mode it will only reconnect to the old network.  However, if I reboot the computer it will connect.  

To reproduce this problem all you have to do is close your laptop lid and then when you open your laptop try to connect to a different network then the one that you first connected to.  

V$H.
:mad:

---

### Post by nklnsk on 2010-11-04
I have same problem on my lenovo g550 with Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01). When I first instal 10.10. I couldn't connect, and one night when I turn on my laptop, wireless just get connect (it was few weeks ago). Today I lost connection again. 
I red and try everything you said but still without connection. Im on wire now.

---

### Post by vsh3r on 2010-11-04
Hi,

I'm going to contact broadcom about this.  I noticed that on Broadcom just upgrade an update to their drivers on 10/18/2010.

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

The drivers that come with Ubuntu 10.10 are BCM43224 802.11a/b/g/n (rev 01).

From the command line it is possible to reinstall/update the drivers with the following command.

sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source

The version that I see here is 5.60.48.36 and the version that is on their website is 5.60.246.2.  

This may mean that we have to download the file from their website rather then doing an apt-get.  Has anyone tried the drivers at

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

How do we update the files on apt-get to reflect the latest broadcom drivers on their website?  

Give me a few and I'll build the latest broadcom drivers and let everyone know how that goes.

:popcorn:

V$H.

---

### Post by vsh3r on 2010-11-04
Hi,

I rebuilt the broadcom wl.ko module and am using it to do this posting.

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

If you were already running a previous version of wl, you'll want to provide
a clean transition from the older driver. (The path to previous driver is
usually /lib/modules/<kernel-version>/kernel/net/wireless)

# rmmod wl 
# mv <path-to-prev-driver>/wl.ko <path-to-prev-driver>/wl.ko.orig
# cp wl.ko <path-to-prev-driver>/wl.ko
# depmod
# modprobe wl

Works for me...  I'll let people know over the next few days it I see some of those same connectivity issues.  :)

Hopefully Ubuntu Update Manager will not overwrite the module? :mad:

:guitar:

V$H.

---

### Post by Darkmagic on 2010-11-04
> **johnnytm said:**
> I never really did anything Right after I installed Ubuntu I connected my ethernet card. awith the wored connection active now I went to system-->administration-->additional drivers My computer then did a search for availabe drivers and 2 drivers showed up, there was a b43 driver and the sta driver. I clicked o the sta driver and then pressed the activate button. After that all worked well. But I would recommend NOT using the b43 driver unless absolute last resort. I had that problem before. If you want the link where you can download the drivers from t not a problem, But the driver would have to be built first. Try this first though
```
 sudo apt-get --purge remove bcmwl-kernel-source
 sudo apt-get install patch  
 sudo apt-get install bcmwl-kernel-source         
 
``` if it still doesn't  work you can try
```
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source
```
One line at a time of course

Thank you!

---

### Post by vsh3r on 2010-11-05
Hi,

The packages available with apt-get and Ubuntu are not up-to-date with the release files at Broadcoms website the most recent stable release build is 5.60.246.2 not 5.60.48.36.

V$H.

---

### Post by Roasted on 2010-11-05
> **vsh3r said:**
> Hi,

I'm going to contact broadcom about this.  I noticed that on Broadcom just upgrade an update to their drivers on 10/18/2010.

V$H.

Good luck. Their support sucks. They haven't ever responded to me in the half dozen times I contacted them.

I solved my continual Broadcom 43xx card problems by getting an Intel Wireless N card on some web site I found via Google Shopping. Total cost? 15 dollah. All issues gone. :guitar:

---

### Post by modblues on 2010-11-07
Hi, I'm using a Broadcom 4311 wireless card, but my Ethernet (also Broadcom) ISN'T WORKING.

Therefore I can't do anything update related in Ubuntu 10.10, only try downloading debian packages in Windows and hoping it works.

So far I have dried the fw43cutter thing, ndiswrapper and direct download from Broadcom, and maybe I'm doing them wrong but NOT ONCE have I seen ANY drivers in the "Additional Drivers" box.

A lot of people have fixed this by getting online through ethernet. Is there no way a debian package or something can be put online that will fix the jockey problem?

BTW I am very new to Linux, so please don't just say something like "reinstall xorg.conf and blacklist your w43"....

---

### Post by Marcelo Ramone on 2010-11-07
> **Solution**: System > Administration > Synaptic Package  Manager > Search: firmware-b43-lpphy-installer > Click Mark >  Click install > Close

Thank you, is solved!

---

### Post by anspideog on 2010-11-09
I am currently pulling my hair out over this issue.
My wireless is massively unstable since installing Ubuntu, and is now working about 5% of the time. I am a newbie and must admit I understand only about a quarter of what's being said on the forums... Need help in plain English please!

My laptop is a Dell Inspiron 1525 (I've got a Vista dual boot going on) but my wireless chipset is BCM4315 (not 4312 as seems common here). 

I've tried the fixes on this thread so far without success. I'm obviously doing something wrong but I don't have a clue what.

Is anyone else using the BCM4315 chipset?

EDIT:
I've just checked in Terminal and actually it turns out my Chipset IS BCM4312. Go Figure.

Still need help though!

---

### Post by vsh3r on 2010-11-09
Can you please post what your errors are in your /var/log/messages file? or you can view your error messages in system->administration->logs

V$H.

---

### Post by cucu007 on 2010-11-12
Too many connectivity issues with BCm4312 using 10.10, i will try to compile the latest kernel and load the latest broadcom drivers to see if I see any improvement. The connection keeps dropping from the Access point and it appears that the driver I am using does not like the WPA2 security since the connection keeps dropping every minute. All sort of issues with this device and drive, I will report back when I finish compiling the latest source and adding the latest module from broadcom if it even compiles. :)

---

### Post by TBABill on 2010-11-12
All 4 of my laptops with the BCM4312 run flawlessly on 9.10, 10.04 and 10.10 using the STA driver. Why would the b43 be chosen instead, other than that it is listed first in the options list when going to system>administration>hardware? Wireless dropping seems very common with the 4312 and the b43 driver, but the STA has none of those issues that I found. And requires nothing more than connecting via ethernet, clicking STA, activate, reboot. I have 2 Dell computers and 2 Acers and they all go through exactly the same steps to configure and none of them drop signal/disconnect.

---

### Post by cucu007 on 2010-11-12
> **TBABill said:**
> All 4 of my laptops with the BCM4312 run flawlessly on 9.10, 10.04 and 10.10 using the STA driver. Why would the b43 be chosen instead, other than that it is listed first in the options list when going to system>administration>hardware? Wireless dropping seems very common with the 4312 and the b43 driver, but the STA has none of those issues that I found. And requires nothing more than connecting via ethernet, clicking STA, activate, reboot. I have 2 Dell computers and 2 Acers and they all go through exactly the same steps to configure and none of them drop signal/disconnect.


Well, I got tired after compiling and loading the latest driver from broadcom. I decided to hack my bios in the Lenovo G550 to allow any miniPCI to be loaded in the slot. IBM/Lenovo has some nasty routine in the bios that prohibit users from changing the minpPCI adapter to another brand. I swap the damm thing after some testing and I am running the Intel Pro 4965 flawlessly now. Ubuntu 10.10 is running great now. If anyone has the G550 and wish to change the adapter drop me a PM. I don't think broadcom and this release and in pair yet.

---

### Post by marjeo on 2010-11-13
I am using Windows XP now but I am planning to change my OS to Ubuntu because of many reasons. I tried Ubuntu by running it through my USB Flashdrive. It worked well and satisfied me except for one thing, the Broadcom 802.11 b/g WLAN (BCM43XX) (Adapter type Ethernet 802.3) of my HP Mini 1001TU is NOT working with Broadcom STA 802.11 of Linux.

What am I gonna do? Is it possible to solve this problem?

If i install Ubuntu, i wont have internet connection because i really solely to my wireless connection.

Please help me...

---

### Post by TBABill on 2010-11-13
Which Broadcom do you have? There are several drivers available depending upon your model. I was specifying the STA for the BCM4312, but it is not the proper driver for some of the other models.

---

### Post by jmullagh on 2010-11-13
> **Marcelo Ramone said:**
> Thank you, is solved!

Currently, this solved my issue as well however, you also have to, in Synaptic, remove the bcm43 driver which is, in Synaptic, 'firmware-b43-installer' the same time you install 'firmware-b43-lpphy-installer'. If you don't the system seems to get confused and reverts to the original driver driving you up the wall.... again.  Good Luck  !!!  :)

---

### Post by gnulab on 2010-11-14
> **Sef said:**
> 

**Solution**: System > Administration > Synaptic Package Manager > Search: firmware-b43-lpphy-installer > Click Mark > Click install > Close


Doesn't work for me. I'm using HP Probook 4420s.

> **johnnytm said:**
> 
The b43 driver has caused me nothing but trouble and complication. I am really confused as to why so many people have had problems using the STA driver when it has always been such a straightforward simple solution.

This solution works.

You'll need to uninstall any other solutions especially in the Synaptic Package Manager before the STA route will work.

Connect your laptop using a LAN cable in order to get the STA driver.
System -> Administration -> Additional Drivers

---

### Post by heytracy on 2010-11-16
I just tried this & had my wireless back- momentarily...:sad:

Now, it's back to showing 100% signal- but no internet?

I'm new to this- so if there's some sort of report or such that I can send to help clarify what's happening- please advise.


Cheers!

Dell Mini 910
2GB RAM
16GB STEC SSD
Ubuntu Netbook 10.10
Broadcom 4312

---

### Post by colio on 2010-11-16
Have tried everything in these posts and still no luck.  I have a 4312 and bottom line is when I click on network manager the wireless options are all blacked out.  I've re-booted several times after trying the commands and suggestions, again with no luck.

I can download the latest drivers from Broadcom as someone suggested but being a newbie I have no idea how to "build" them.  Growing very frustrated with all this since my wireless was working last week prior to updates...

---

### Post by heytracy on 2010-11-16
> **jmullagh said:**
> Currently, this solved my issue as well however, you also have to, in Synaptic, remove the bcm43 driver which is, in Synaptic, 'firmware-b43-installer' the same time you install 'firmware-b43-lpphy-installer'. If you don't the system seems to get confused and reverts to the original driver driving you up the wall.... again.  Good Luck  !!!  :)

Tried this- the lpphy is the only one installed (the other was removed already). Now what?

I just don't understand how it can work & then not? In fact, when it's "on" the range & speed is better than in XP. It even picked up my networked hub. The network details show it's been assigned an IP address from the router. 

My dilemma is getting it to work properly because I'm having my kids take this with them on an overseas trip- it'll be our only connection...I hate the thought of reverting back to XP but I won't have a choice if I can't get the wireless going.

:(

---

### Post by uttaradhaka on 2010-11-17
I have a broadcom 4321 card and had been using XP for a while on a Dell Mini 10v netbook. But, the wireless did not work properly. It used to connect, and then disconnect on its own.
 Then, I decided to install Ubuntu 10.10 in hopes that it would solve the problem. But, it has not. Connection comes and goes at will. Also, I am using a Windows 7 computer with connectify installed to act as the wireless hotspot. It uses WPA encryption. 

I am using the STA driver 5.60.48, which is not the latest, but is the only one available in the repositories. 

 I can't download the latest drivers from the Broadcom website and compile them myself. Then, what can I do to fix this problem? Please help.

I really really really need help soon. Please. I read this whole thread and tried them out, but no use.

Any help whatsoever will be appreciated.
 Thanks in advance.

---

### Post by colio on 2010-11-17
What exactly has to happen to get the latest driver in the repositories?

---

### Post by uttaradhaka on 2010-11-18
> **colio said:**
> What exactly has to happen to get the latest driver in the repositories?

Well I don't know exactly. I guess the update has to go through some kind of verification process and then it'll get to the repositories. 

 Honestly, I think the process should be a bit faster because its already been a while since the update has been release on the official website, so it should be coming on to the repositories soon; hopefully..

 Really hoping for a fix the this wireless problem really soon.

---

### Post by faheyd on 2010-11-18
> **Marcelo Ramone said:**
> Thank you, is solved!

OK, on my Mac Powerbook G4, I had to bring up Synaptics, 'search button' look for b43, remove any of those packages.
Then, reinstall b43-fwcutter and the b43 legacy fw installer
magic, I then have wireless connection to my WPA network

---

### Post by QwUo173Hy on 2010-11-20
NVM, I've started a fresh thread about this since my problem exists on Lucid also.

---

### Post by bulagump on 2010-11-24
Coolio,

Did you get this fixed yet?  I had the same problem with my PC but somehow I reinstalled some packages, and installed some new packages, restarted, my PC, and it worked.

I am not an expert in Linux at all...everything I did was either in System --> Administration --> Additional Drivers, or System --> Administration --> Synaptic Package Manager

1. ) Under Additional Drivers, I removed and reinstalled the proprietary driver ( not sure if this actually helped or not )
2.) Under the package manager, I installed broadcom-sta-common ( no idea if I needed it, but it said it supported my device, so I installed it )
3.) I also installed firmware-b43-installer ( again, not sure if this helped )
4.) Also, you can check to make sure the following are already installed: 
bcmw-kernel-source, broadcom-sta-source,b43-cutter, and bcmwl-modaliases
If they are not installed, install them.  I don't know if all of them are needed, but I have all of them installed.  Again, not sure if all of these steps are needed, but something in this process worked for me.

5.) The last thing I did was reinstall the network-manager package.  This is the software that I believe is responsible for GUI interface that allows you to select  your wireless network ( which you currently can't even do! )


You should be able to do 2-5 in the synaptic package manager tool .  Once all this is done, restart the computer, and hopefully your wireless will be working...

---

### Post by Podas okys on 2010-11-24
Hi, Everyone on the Forum, 

I am more than less a newbie to Linuxiana. I installed Ubuntu 10.10 (build: 2.6.35-23-generic-pae) onto a Dell Inspiron 1545 notebook, alongside with Win 7. No wireless extensions can be detected, although wireless was functioning properly before I upgraded to  2.6.35-23-generic-pae. In System>Administration>Additional Drives I have these 2 options: 1. Broadcom B43 Wireless driver: "Disabled"; 2. Broadcom STA Wireless driver: "Enabled but not in use".
As probably the only solution remaining, I was trying to "untar" and build Broadcom's Linux hybrid wireless driver, but with no success. (My wireless card, a Broadcom 4315 (rev 01), is not listed among the Supported Devices for this "hybrid wl", the 802.11 Linux STA driver, although it says "cards not listed may also work") Can anybody help me? either showing how to "untar" the "[COLOR=#666666][FONT=Verdana][SIZE=2]hybrid-portsrc_x86-32_v5.60.246.2.tar.gz" tar-file, or else, tell me how I can "put in use" the otherwise "enabled" [/SIZE][/FONT][/COLOR]Broadcom STA Wireless driver?I will be grateful for any help. I'm desperate...


Thanks,
Podas okys

---

### Post by nklnsk on 2010-11-24
Nope, still can not work :(

@ bulagump: did everything you said, but my wireless on my lenovo 550 wont work.
Hope solution will come soon. 
__

---

### Post by Zummy on 2010-11-25
I am 100% lost on how to get this internet running on my computer,  I have no option of wired internet, so I am stressing to the point of giving up (after a couple of days).  So now I am finally manning up and asking for help haha.

Here's what I got
(this is a lspci -vvnn | grep 14e4 command)
```
Broadcom Corporation BCM4318 [AirForce One 54g] 902.11g Wireless LAN Controller [14e4:4318] (rev 02)
```

This is using a live CD of Ubuntu 10.10 without internet, so what files/drivers do I need to put on an external harddrive to install?  Is the firmware/b43-fwcutter already pre installed?  I'm completely lost,  please help.  Thanks :D

---

### Post by Podas okys on 2010-11-25
Certain - but not all - kernels of Ubuntu 10.10 (2.6.35-23-generic-pae in my case) seem to be in a so far unsolvable conflict with some Broadcom WL chipsets. Until the necessary updates to solve this conflict are available in the repositories for download, I will, unwillingly though, go back to Windows.

Hoping for the best at the soonest possible,

Podas okys

---

### Post by Podas okys on 2010-11-25
After removing Broadcom STA wireless driver via the Synaptic Manager, I activated Broadcom B43 wireless driver, and my wireless straightaway rose from its dead. After rebooting, however, the wireless went away. I repeated the above action, and wl "came back". 
What is strange that in System > Additional Drives NEITHER of the two proprietary drivers appear activated! Still, wireless works - until the next reboot.
What shall I do to keep wl working after I restart my machine?

Podas okys

---

### Post by bulagump on 2010-11-26
nklnsk,

I am sorry that did not work for you. I have an aspire 3680

---

### Post by y789 on 2010-11-26
I spent hours reading forums, searching internet, but still there is a problem. I tried ndiswrapper, doesn't work. I tried anything, but still, there is no notification for wireless network. 

Before I trow my laptop out of my window, scream and wake my neighbours and kill the ubuntu-developers: maybe someone can help me? I mean, really help me? 

I have a Dell inspiron 1545, 64 bit.
lspci says:

09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)


So, i tried to install ndiswrapper, founded the right bcmwl6 driver: didn't do anything./
hardware presents: yes 
but i cant select wireless.

additional drivers says:
'green light' broadcom sta wirless driver

This driver is activated but not currently in use.

Thank you in advance for helping!

---

### Post by dylbud on 2010-11-27
Thanks to everyone here for posting all their various solutions. I just reinstalled everything on my computer, XP and Ubuntu 10.04. I also have the 4312 chip.

The first solution listed here didn't work for me because the packages firmware-b43-lpphy-installer and firmware-b43-installer are not in my repository. Even after apt-get update they are not there.

I tried everything else here, including last but not least downloading the driver from Broadcom at [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php).

I followed all the instruction in the readme file to the letter. It was the only thing that worked.

Thanks.

---

### Post by Podas okys on 2010-11-27
> **dylbud said:**
> Thanks to everyone here for posting all their various solutions. I just reinstalled everything on my computer, XP and Ubuntu 10.04. I also have the 4312 chip.

The first solution listed here didn't work for me because the packages firmware-b43-lpphy-installer and firmware-b43-installer are not in my repository. Even after apt-get update they are not there.

I tried everything else here, including last but not least downloading the driver from Broadcom at [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php).

I followed all the instruction in the readme file to the letter. It was the only thing that worked.

Thanks.

Dear Dylbud,
could you please let me know which "path" is exactly meant in this line of the readme file for Broadcom's 802.11 Linux STA diver: "# tar xzf <path>/hybrid-portsrc_x86-32_v5.60.246.6.tar.gz"?
Thanks a lot,
Podas okys

---

### Post by tiredofguessingusernames on 2010-11-28
> **Podas okys said:**
> 
What shall I do to keep wl working after I restart my machine?

Podas okys

Have you tried "sudo modprobe wl" after the restart? I have a similar problem - and that solved it.

If the modprobe command works, you can add "wl" to /etc/modules to have the wl module loaded at startup (I haven't tried adding it yet, as I have other wireless issues).

---

### Post by dylbud on 2010-11-28
Hey Podas okys.

 Upon review, it appears I lied. I did not follow all the instructions to the letter, but skipped this entire first step. All you're doing here is creating a folder and upcompressing the file into it. From my understanding, it doesn't matter where this folder is. However, I put mine in /usr/local/src as per the instructions at [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) -- it says to create it, if it's not there, but mine was. And it was empty. So that's a good place to do it.

Once you uncompress the file to the folder you want it in, then use a terminal to navigate to that folder and start running the commands starting at step 2 under Build Instructions of the ReadMe file.

Good luck!

---

### Post by sporty87 on 2010-11-28
Well I'm still pulling my hair out.  I have a Dell Latitude D600 with Broadcom's B4306 Rev 2 chip.  b43Legacy driver installed in UBUNTU 10.10 and was able to activate it one time and now all I get is an message stating:  "INSTALL ARCHIVES () FAILED"  
this is what I see under iwconfig.  

  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:16:05:41
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43legacy driverversion=2.6.35-23-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg

As you can see the network is DISABLED.  I cannot find firmware for this chip even from Broadcoms web site.  

Any suggestions.

---

### Post by sporty87 on 2010-11-29
Still playing with wireless on UBUNTU 10.10, see above post, tried uninstalling and reinstalling B43-fwcutter and get this error message:
E: firmware-b43legacy-installer: subprocess installed post-installation script returned error exit status 1

What's up with this??????  Pretty new at this but had this wireless working on 10.4 then I upgraded to 10.10 and haven't been able to connect to the wireless since.  I don't know what I'm doing wrong but obviously something isn't correct.  BUT WHAT!!!!!!!

---

### Post by sporty87 on 2010-11-30
I got tired of fighting UBUNTU 10.10 - SO I went back to UBUNTU 10.4.1 which had no problem and automatically loaded the b43legacy fwcutter and my wireless worked just fine.  I think there is a problem in 10.10 where the kernel and program are not communicating or some part is missing.  I needed my computer to work and I'm to green behind the ears to know what else I could do to fix this problem.

---

### Post by Podas okys on 2010-12-01
> **dylbud said:**
> Hey Podas okys.

 Upon review, it appears I lied. I did not follow all the instructions to the letter, but skipped this entire first step. All you're doing here is creating a folder and upcompressing the file into it. From my understanding, it doesn't matter where this folder is. However, I put mine in /usr/local/src as per the instructions at [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) -- it says to create it, if it's not there, but mine was. And it was empty. So that's a good place to do it.

Once you uncompress the file to the folder you want it in, then use a terminal to navigate to that folder and start running the commands starting at step 2 under Build Instructions of the ReadMe file.

Good luck!

To Everyone with the Broadcom~Maverick problem,

I eventually re-installed Ubuntu 10.10 (Linux kernel 2.6.35-23-generic - instead of what I had: 2.6.35-23-generic-pae), installed 802.11 Linux STA driver from [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php), and everything started to work again and still works flawlessly.
So my problem is SOLVED, at last. 
Thanks everybody for advices and descriptions of their problem, esp. Tiredofguessingusernames & Dylbud. 

Good luck!

Podas okys

---

### Post by SyphonX67 on 2010-12-01
Hi, I have a Broadcom BCM4312 on an HP Pavillion Dv2945se. I'm running 10.10 64 bit, and the wireless card used to work. Now it has just stopped working and it has not worked since. I installed Ubuntu 9.10, and the card worked fine. Then upgraded to 10.04, again successful. As soon as I update to 10.10 however, no luck. This is quite frustrating. I enable wireless, but the light on my wifi card is still red, meaning the card is not working. In the proprietary drivers area, it says that the STA (and B43) drivers are working fine, the light is green and that they are currently in use, when they clearly are not. If anyone has any suggestions to a noob like me, please.

---

### Post by zdenal on 2010-12-02
I had same problems with Broadcom driver on Lucid and Maverick.

In my post

[http://polach.cc/broadcom-wifi-adapter-wpa-access-fix-on-ubuntu-ii](http://polach.cc/broadcom-wifi-adapter-wpa-access-fix-on-ubuntu-ii)

I summarize some facts so you can check

a) If your Broadcom card is supported by the wl.ko driver
b) Use step by step HowTo to try fix your wireless problem

Hope this helps..

---

### Post by cariboo on 2010-12-02
> **SyphonX67 said:**
> Hi, I have a Broadcom BCM4312 on an HP Pavillion Dv2945se. I'm running 10.10 64 bit, and the wireless card used to work. Now it has just stopped working and it has not worked since. I installed Ubuntu 9.10, and the card worked fine. Then upgraded to 10.04, again successful. As soon as I update to 10.10 however, no luck. This is quite frustrating. I enable wireless, but the light on my wifi card is still red, meaning the card is not working. In the proprietary drivers area, it says that the STA (and B43) drivers are working fine, the light is green and that they are currently in use, when they clearly are not. If anyone has any suggestions to a noob like me, please.

I've got the same device in one of my systems. After installing Natty, I couldn't get a wireless connection, even though it works in Natty on another partition. Natty isn't different form Maverick yet, so this solution should work for you.

When I ran:

```
sudo lshw -C network
```

It was showing the card was  disabled, looking at the output I noticed there wasn't any firmware installed, to rectify the problem, I had to install firmware-b43-installer, it's in the repositories. Once the firmware was installed it shows:

```
firmware=410.2160
```

Now the device works like it should.

---

### Post by SyphonX67 on 2010-12-02
Alright, I'll give it a shot, thanks

---

### Post by SyphonX67 on 2010-12-02
apparently my box says that I have a BCM4315 now, it changed....

Anyways, I tried both solutions, and unfortunately, neither of them have worked

---

### Post by chicoharv on 2010-12-02
I have no wireless since I upgraded from 10.4 t0 10.10. Unfortunatly I have the dreaded bcm4318 card. It used to work on 10.4 by useing fwcutter and bc43xx. I have tried everything, including STA, still noy working.Anybody got any suggestions for this bcm4318. When I query it shows the bcm4318 as unclaimed. Both ACER laptops. Grrrr. Help.

---

### Post by lowkye on 2010-12-03
[FONT=Arial][SIZE=2]My card is a BCM43225 and fuctions fine running 10.10, I just used the supplied drivers on the CD. My problem is it's logical name is eth1 and I can't change it to wlan*, as aircrack-ng will not [FONT=Arial][SIZE=2]recognize[/SIZE][/FONT] it as wireless interface. I've edited the name in /etc/udev/rules.d/70-persistent-net.rules but 10.10 just adds another line with eth1 as it's name, this did work fine in 10.04.[/SIZE][/FONT]

---

### Post by carlingb on 2010-12-15
so, (lenovo s10-3t) my driver is also pretending to work (green light, no "network DISABLED" or any of that) BUT it doesn't recognize any wireless networks. ran sudo lshw -C network and got:

```
  *-network
       description: Wireless interface
       product: BCM4313 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth1
       version: 01
       serial: 00:26:82:58:9e:d0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f0200000-f0203fff

```

so, it's pretending to work, but is not working at all. it won't even take if i put in the information as though it's a hidden network. it's not a problem with the wifi, it's working on all the other computers in our house.

i've tried reinstalling everything, including ubuntu entirely, nothing is working. i also tried the firmware fix posted by cariboo907, no dice. i think it's because the computer thinks it's working or something? but it's not.

any help would be SO appreciated.

---

### Post by guntu on 2010-12-20
> **kerosine said:**
> this solution doesn't work in my case.:(


try this: 

[FONT=Arial][FONT=&quot]Make sure you have an internet connection by connecting directly with a DSL cable from your computer to your modem. 

1) Log in to Ubuntu
2) Open the "Synaptic" 
**    System** > **Administration** > "**Synaptic Package Manager**"
3) Click on "Reload".  When finished,
4) Click "Mark All Upgrades". When finished,
5) Click "Apply".  Wait for the programme to finish installing all the updates. Then,
6) Restart your computer.
7) Open Synaptic again. 
:cool: In the search window, type: bcmwl-kernel-source
9)  a) If it's not found, then you need to download it and install it. Here's how:
        1) Go to : [http://packages.ubuntu.com/da/karmic...-kernel-source]("http://packages.ubuntu.com/da/karmic/bcmwl-kernel-source")
        2) Choose your architecture: amd64 or i386 .  My HP Pavillion dv2000 laptop is amd64 - FYI. 
        3) Select a server near you. I'm in Europe so I chose the one from France. 
        4) Download it.
        5) Navigate to the folder where you saved the file to.
        6) Double click on it and it will install it for you. 

    b- If it finds it, right click on it (bcmwl-kernel-source) and if  you see the option to update it "Mark for update", then selected and  then click on "Apply" to update it. 
    b- It it finds it but you can't select "update", that's fine, that  means you have the lattest version. Simply close the window. 

10) Open "Hardware Drivers". **System** > **Administration** > "[B]Hardware Drivers"
[/B]11) If you see that the " Broadcom STA proprietary wireless driver"  wireless driver is installed (active), click on it and click on  "Remove". When finished, [/FONT][/FONT]
  [FONT=Arial][FONT=&quot]12) Locate the driver called "Broadcome 43 wireless driver" and click on "Activate".
12) Once it's finished installing this driver, you should see the  wireless networks available around you when clicking on the wireless  icon on the top bar. 

And that's it!  
[/FONT][/FONT]

---

### Post by topbayder on 2010-12-22
this doesnt work for the 4313. :(

everything i have tried hasn't managed to get this working for me. I haven't tried this though [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) and basically i have given up. so if anyone else tries that link and it works let me know please lol

i know they have released the open source code for the drivers and its all in the workshop to be added to synaptic but does anyone have any idea of when this will come? i simply cant handle doing it any other way. i just want to click a couple of buttons :) im just not smart enough for all the coding/shell work/scripting.

---

### Post by tjones00 on 2010-12-22
Neither driver is working for me 4312 in a HP Mini 1033CL. Ubuntu 10.10 32b.

I've tried the STA and B43. Tried purging the STA and a reinstall that didn't work either.

Both drivers can see the network but can't login the security is WPA WPA2 personal.

I had limited success using the  firmware-b43-lpphy-installer it connected once but dropped after about 20seconds and then failed to reconnect.

In Ubuntu 10.04 the STA driver worked fine on this machine.

Update:

Finally figured out someone decided to move their wireless channels to overlap mine. Both sta and b43 are working.

---

### Post by paulsjv on 2010-12-26
> **carlingb said:**
> so, (lenovo s10-3t) my driver is also pretending to work (green light, no "network DISABLED" or any of that) BUT it doesn't recognize any wireless networks. ran sudo lshw -C network and got:

```
  *-network
       description: Wireless interface
       product: BCM4313 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth1
       version: 01
       serial: 00:26:82:58:9e:d0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f0200000-f0203fff

```

so, it's pretending to work, but is not working at all. it won't even take if i put in the information as though it's a hidden network. it's not a problem with the wifi, it's working on all the other computers in our house.

i've tried reinstalling everything, including ubuntu entirely, nothing is working. i also tried the firmware fix posted by cariboo907, no dice. i think it's because the computer thinks it's working or something? but it's not.

any help would be SO appreciated.

So glad you posted this because I'm having the same problem.  The only difference I am having is that the wireless was working the other day after I installed the Broadcom drivers etc.  I go today and boot up the machine and it won't connect at all.  I go through hidden network and it won't connect.  

I'm at a loss any help would be awesome!

---

### Post by ThomasNovin on 2010-12-27
The STA driver worked without any problem on my system (which has a BCM47279).

However, I don't get any good speed, certainly not 802.11n. Does anyone know if the updated driver you can get from [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) has support for 802.11n? Doesn't seem like it looking through the README + some of the source-files.

I can see in the README that the latest version (2010-12-22) fixes some problems that are mentioned in this thread though.

---

### Post by ThomasNovin on 2010-12-27
> **ThomasNovin said:**
> The STA driver worked without any problem on my system (which has a BCM47279).

However, I don't get any good speed, certainly not 802.11n. Does anyone know if the updated driver you can get from [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) has support for 802.11n? Doesn't seem like it looking through the README + some of the source-files.

I can see in the README that the latest version (2010-12-22) fixes some problems that are mentioned in this thread though.

Noted that just to upgrade when you already have the STA driver active was very simple. After the upgrade I went from a 5.5-8Mbps connection to 72Mbps :) So I can warmly recommend upgrading the driver to latest release.

---

### Post by evanferneski on 2010-12-27
Thank you soo much you have no idea how grateful I am for this post. Yesterday I wanted to help out my sister with her netbook as the windows installation was so bogged down. I didn't want to reinstall it seeing as within 2 weeks it would be just as bad. 

so after installing ubuntu for netbooks, i spent literally, without exageration, 6 hours trying to get the wireless card to work! i googled EVERYTHING and tried EVERYTHING. i found about 5 threads on the issue all of which had solutions that didnt work for me. finally after deciding to post a new thread, i came across this (which odly enough did not show up at all in the google searches). this was SO easy and so quick it fixed it immediately! thank you so much

this solution worked for my Acer Aspire One D250 which had the B4312 in case anyone else is wondering if this worked

---

### Post by PatchesTheCaveman on 2010-12-29
Just FYI:  the 2.6.35-24-generic kernel update seems to break the STA driver, at least on my machine.  So if you update your system and it stops working, try selecting the 2.6.35-23-generic kernel from your GRUB menu and it should go back to working fine.

I posted another thread to see if I can try and get this resolved.  :-s

---

### Post by ohmboys on 2010-12-30
i have tried everything to work my b43-fwcutter i have had HP before  worked fine on my laptop i downloaded b43 driver .. went to  /usr/share/b43-fwcutter/ & i install the firmware.sh i remember that  was the way i did it before .. after installation i run modprobe -r b43  ssb wl .. modprobe b43 .. iwlist scan .. i get nothing but eth1 which i  already have a driver on my laptop dell latitude d600 .. ipw2200 .. i  need wlan0 driver so i can get mon0 or something or atheros .. i just  dont remember the steps i donno if i have to move b43-fwcutter folder to  somewhere else .. i've been trying for past 10 days its just not  working for me i read some of your posts it seems like u know what you  are saying .. i will post my lsmod .. & everything you need please  help me here .. i think i also downloaded after all updates upgrades  bcmwl-kernel-source i donno what file it went to cant find it cant find  the code to find the version .. i just need some help to have a b43  driver to work .. here is my lsmod

```
root@ubuntu:/home/dflpride# lsmod
Module                  Size  Used by
b44                    25574  0 
ssb                    38902  1 b44
mii                     4381  1 b44
wl                   1959598  0 
binfmt_misc             6587  1 
rfcomm                 33421  4 
sco                     7885  2 
bridge                 45614  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30624  16 rfcomm,bnep
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
fbcon                  35102  71 
tileblit                2031  1 fbcon
ac97_bus                1002  1 snd_ac97_codec
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
snd_pcm_oss            35308  0 
softcursor              1189  1 bitblit
snd_mixer_oss          13746  1 snd_pcm_oss
vga16fb                11385  0 
snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
vgastate                8961  1 vga16fb
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
radeon                676897  3 
pcmcia                 30784  0 
snd_rawmidi            19056  1 snd_seq_midi
ttm                    49943  1 radeon
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
drm_kms_helper         29329  1 radeon
snd_timer              19098  2 snd_pcm,snd_seq
drm                   162409  5 radeon,ttm,drm_kms_helper
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                  8740  0 
yenta_socket           20408  4 
i2c_algo_bit            5028  1 radeon
ipw2200               135216  0 
rsrc_nonstatic         10015  1 yenta_socket
snd                     54180  14  snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
libipw                 39896  1 ipw2200
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
ppdev                   5259  0 
video                  17375  0 
soundcore               6620  1 snd
dell_wmi                1793  0 
parport_pc             25962  1 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
intel_agp              24375  1 
output                  1871  1 video
lib80211                5046  3 wl,ipw2200,libipw
psmouse                63245  0 
btusb                  10957  2 
agpgart                31724  3 ttm,drm,intel_agp
dcdbas                  5422  0 
lp                      7028  0 
shpchp                 28820  0 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
serio_raw               3978  0 
parport                32635  3 ppdev,parport_pc,lp
tg3                   109324  0 

root@ubuntu:/home/dflpride# lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0  Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2]  Network Connection (rev 05) ..
``` 

i donno what more information you need  just ask me to run the code & i will send it to you but i think im  following every step possible on the internet but its kind of not  working for me i went to system / admin / hardware drivers .. all of  them are emply im using UBUNTU 10.__ THE LATEST ONE .. HOPE TO HEAR FROM  YOU SOON .. 

THANK YOU IN ADVANCE

---

### Post by PatchesTheCaveman on 2010-12-30
Hi ohmboys!

You have an Intel wireless card.  The b43 driver is for Broadcom cards.  It will not work on your machine.

It sounds like you're trying to enable monitoring mode on your wireless card (most likely for aircrack-ng).  You do not need a special driver to do this.  The default Ubuntu driver for your Intel wireless card can be used for that purpose.

For assistance in getting your card in monitoring mode and using aircrack-ng, I suggest you inquire on their forum:
[http://forum.aircrack-ng.org/](http://forum.aircrack-ng.org/)

They will have a lot more people who are familar with that software and the necessary steps to get monitoring mode working properly.

Good luck!

---

### Post by Felliph3 on 2011-01-02
My HP dv9000 has the wifi working in 10.10. HOWEVER, every time I boot, come back from a suspend, log in, etc the wifi takes 1 minute to start to connect!

I have tried to find a solution for weeks and nothing. The network manager wont scan for networks for about a minute b4 it start to reconnect. Someone has to know the answer, PLEASE help! =(

---

### Post by andrek on 2011-01-02
This is driving me batshit insane. It hasn't occurred to me before. None of these solutions worked for me and I JUST want to install the STA drivers. I also tried installing natty packages (bcmwl-kernel-source) and the one from broadcom site. NOTHING WORKS. Any ideas, what log should I look for?

Installing Natty alpha fixes the issue. Installing the STA driver from Additional Drivers JUST WORKS.

---

### Post by bevangg on 2011-01-04
I have an HP mini 110c with a broadcom 3412 wireless card running Maverick. The card picks up networks but will not connect, constantly tries to acquire a network address.This problem started when I turned off the wifi with the switch on the netbook. I have tried almost everything suggested on the forums and nothing works.

---

### Post by PatchesTheCaveman on 2011-01-04
Hi bevangg.  Happy New Year!

To figure out what's going on, we need to collect some diagnostic information.  Go to Applications > Accessories > Terminal on your top panel.  In the black box that appears, type each of the following commands, then press Enter:
```
lspci -vnn
lshw -C network
ifconfig -a
uname -r
sudo iwconfig
```

Once you've done that, copy and paste what appears in a reply to this thread.  We'll take a look at it and see what we can do.

---

### Post by bevangg on 2011-01-04
Hi Patches from Arizona love the handle and many thanks for your timely reply. I have tried to attach text file with the outputs of all the commands that you listed.For some reason the server refused to accept this file in any format so I have had to resort to copy and pasting the whole shooting match in this post.
PS The plot thickens... The netbook connected immediately to the wlan in the Pub. I have noticed that it seems to think it is trying to connect to the Pub network wherever it is. This must be a clue to what is going on here!
I hope this makes sense to somebody.
bevan@Mini-110c-1000:~$ lspci -vnn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:308f]
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device [103c:308f]
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fe180000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at dc80 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at fe140000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:308f]
	Flags: bus master, fast devsel, latency 0
	Memory at fe080000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:308f]
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at fe138000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: fe200000-fe2fffff
	Prefetchable memory behind bridge: 000000003f800000-000000003f9fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fe300000-fe3fffff
	Prefetchable memory behind bridge: 000000003fa00000-000000003fbfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: fe400000-febfffff
	Prefetchable memory behind bridge: 000000003fc00000-000000003fdfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device [103c:308f]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at dc00 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device [103c:308f]
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at d880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device [103c:308f]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at d800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device [103c:308f]
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at d480 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device [103c:308f]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fe137c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:308f]
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Hewlett-Packard Company Device [103c:308f]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at d400 [size=8]
	I/O ports at d080 [size=4]
	I/O ports at d000 [size=8]
	I/O ports at cc80 [size=4]
	I/O ports at cc00 [size=16]
	Memory at fe137800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:1508]
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fe2fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

02:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)
	Subsystem: Hewlett-Packard Company Device [103c:308f]
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at fe3c0000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at ec80 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: atl1c
	Kernel modules: atl1c

03:00.0 Multimedia controller [0480]: Broadcom Corporation BCM70012 Video Decoder [Crystal HD] [14e4:1612] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:2612]
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at febf0000 (64-bit, non-prefetchable) [size=64K]
	Memory at fe400000 (64-bit, non-prefetchable) [size=4M]
	Capabilities: <access denied>
	Kernel driver in use: Broadcom 70012 Decoder
	Kernel modules: crystalhd

bevan@Mini-110c-1000:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:fe2fc000-fe2fffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: 00:25:b3:65:a5:39
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A ip=192.168.0.14 latency=0 multicast=yes
       resources: irq:45 memory:fe3c0000-fe3fffff ioport:ec80(size=128)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:26:5e:08:95:bf
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-24-generic firmware=N/A multicast=yes wireless=IEEE 802.11bg
bevan@Mini-110c-1000:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:25:b3:65:a5:39  
          inet addr:192.168.0.14  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::225:b3ff:fe65:a539/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:844 errors:0 dropped:0 overruns:0 frame:0
          TX packets:488 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:566765 (566.7 KB)  TX bytes:66783 (66.7 KB)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2884 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2884 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:225448 (225.4 KB)  TX bytes:225448 (225.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:5e:08:95:bf  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:25284 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19091 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27853706 (27.8 MB)  TX bytes:2743566 (2.7 MB)

bevan@Mini-110c-1000:~$ uname -r
2.6.35-24-generic
bevan@Mini-110c-1000:~$ sudo iwconfig
[sudo] password for bevan: 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
bevan@Mini-110c-1000:~$ 
Thanks to all for bothering to look at this and trying to help. 
I dont know why these yellow faces have appeared in the text above.

BBoy

---

### Post by zippi07 on 2011-01-06
I have a strange symptome on my BCM4312.

My connection speed drops from 17Mbps to 5Mbps when I pull the cord of my laptop and run it on battery (tested with speedtest). It also seems to have some trouble connecting to websites. But it does so eventually, but slowly. 

I have a Dell Inspiron 1750 with BCM4312

Before ubuntu 10.10 my wirelesscard worked fine. That is, I ran it with the B43-driver together with ndiswrapper. After installing Ubuntu 10.10 my speed dropped to about 5Mbps. A wired connection gives me about 25Mbps.
I thought I fixed it by completely reinstalling the system and trying the STA driver instead. It worked right away. No need of nsdiswrapper.

But now I lose my speed when I go on battery. And Im not really satisfied with 17Mbps.

Any thoughts on this??


  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 70:1a:04:7f:bc:86
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=94.224.251.191 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f6cfc000-f6cfffff

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:207  Noise level:170
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

uname -mr
2.6.35-22-generic x86_64

---

### Post by bkratz on 2011-01-06
@zippi07--

The version of the STA driver you have is about 5 versions old. The repository has not been updated, see the readme on this page for more information.

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

It may not make a difference for your particular problems, but it might?

---

### Post by zippi07 on 2011-01-06
> **bkratz said:**
> @zippi07--

The version of the STA driver you have is about 5 versions old. The repository has not been updated, see the readme on this page for more information.

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

It may not make a difference for your particular problems, but it might?

I tried it: compiled a new STA driver.

But the endresult is the same:
17Mbps on netpower; 5Mbps on battery

Thanks for the tip. But no luck.

---

### Post by nm_geo on 2011-01-11
> **bevangg said:**
> I have an HP mini 110c with a broadcom 3412 wireless card running Maverick. The card picks up networks but will not connect, constantly tries to acquire a network address.This problem started when I turned off the wifi with the switch on the netbook. I have tried almost everything suggested on the forums and nothing works.

from your sudo lshw -C network 

```
*-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
```The only way I can simulate this is by turning my switch off and I can not just turn it back on I must reboot with it in the 
correct position.

It appears your switch is still disabled. If you can't tell turn it one way boot up (no wireless) then try the other way and reboot. You may need to check your BIOS as well.

---

### Post by KosakiHook on 2011-01-16
I have a Compaq 2195us with integrated Broadcom 802.11b/g wireless, driver version 3.70.17.0. I don't have much experience with Linux, but I tried both Puppy Linux and Ubuntu 10.10, and I simply cannot get the wireless to work. This is the only thing holding me back from switching or installing Linux on this machine. Any help  would be appreciated on how to get the wireless working. Are there any other drivers to try out? The driver on my Compaq is supposedly the latest.

---

### Post by KosakiHook on 2011-01-16
I have a Compaq 2195us with integrated Broadcom 802.11b/g wireless, driver version 3.70.17.0. I don't have much experience with Linux, but I tried both Puppy Linux and Ubuntu 10.10, and I simply cannot get the wireless to work. This is the only thing holding me back from switching or installing Linux on this machine. Any help  would be appreciated on how to get the wireless working. Are there any other drivers to try out? The driver on my Compaq is supposedly the latest.

---

### Post by KosakiHook on 2011-01-16
I have a Compaq 2195us with integrated Broadcom 802.11b/g wireless, driver version 3.70.17.0. I don't have much experience with Linux, but I tried both Puppy Linux and Ubuntu 10.10, and I simply cannot get the wireless to work. This is the only thing holding me back from switching or installing Linux on this machine. Any help  would be appreciated on how to get the wireless working. Are there any other drivers to try out? The driver on my Compaq is supposedly the latest.

---

### Post by SyphonX67 on 2011-01-18
Hello, my BCM4312 is still not working on unity 10.10 32bit. Is there anyway I could load the driver from a live CD of 9.10 or 10.04? the card works seamlessly on those two versions. Otherwise, I'm forced to use a wired connection, which is not really an option for me.

---

### Post by Pablo W on 2011-01-19
Thanks vsh3r, for your detailed [#16]("http://ubuntuforums.org/showpost.php?p=10073108&postcount=16") and [#15]("http://ubuntuforums.org/showpost.php?p=10073069&postcount=15") posts.

I think I have the same problem you had: no wireless in my HP Mini 5105 SSD netbook, runing Ubuntu 10.10 with a wireless Broadcom BCM43224 802.11a/b/g/n card with 5.60.48.36 driver version.

I have uderstood that I should to replace the old driver (version 5.60.48.36) with the new one available from the Broadcom website at [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) I also know that I have a 32 bit netbook and I have already downloaded the new driver. Being a newbie, I find it a bit hard to understand your instructions. My question is: how do I replace the old driver with the new one?

Detailed information on my netbook follow.
> **Pablo W said:**
> I have a HP Mini 5105 SSD netbook, runing Ubuntu 10.10 with 2Gb RAM. My wireless card is a Broadcom BCM43224 802.11a/b/g/n. Its driver is enabled and running. The wired network connection runs fine too.

The problem:
Wireless stopped working. When I right click on the network icon, the “enable network” option is clicked, but  the "enable wireless" option is listed in dark grey and cannot be clicked on. I have recently updated my kernel version to 2.6.35-24-generic.


What I have already tried:
Thanks to [this post]("http://ubuntuforums.org/showpost.php?p=10312711&postcount=5") and [this one too]("http://ubuntuforums.org/showthread.php?t=1653568&page=3") I got to know  there seems to be a problem with the 2.6.35-24-generic kernel. I have gone into the GRUB menu (it took some time to find out that you have to keep the Shift key pressed during startup for the GRUB menu to show), chosen the older kernel version (2.6.35-23-generic) and then removed the faulty one. Nevertheless, nothing has changed. I still cannot enable the wireless.

The outcome to lshw -C network is:
```
pablo@pablo-netbook:~$ lshw -C network
WARNING: you should run this program as super-user.
 *-network DISABLED      
      description: Wireless interface
      product: BCM43224 802.11a/b/g/n
      vendor: Broadcom Corporation
      physical id: 0
      bus info: pci@0000:08:00.0
      logical name: eth1
      version: 01
      serial: 00:26:82:38:d8:61
      width: 64 bits
      clock: 33MHz
      capabilities: bus_master cap_list ethernet physical wireless
      configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
      resources: irq:16 memory:e8000000-e8003fff
 *-network
      description: Ethernet interface
      product: 88E8072 PCI-E Gigabit Ethernet Controller
      vendor: Marvell Technology Group Ltd.
      physical id: 0
      bus info: pci@0000:20:00.0
      logical name: eth0
      version: 10
      serial: 18:a9:05:93:3b:86
      width: 64 bits
      clock: 33MHz
      capabilities: bus_master cap_list rom ethernet physical
      configuration: broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 multicast=yes
      resources: irq:44 memory:e0000000-e0003fff ioport:2000(size=256) memory:7fc00000-7fc1ffff
pablo@pablo-netbook:~$
```


I’m sorry to say I am a newbie who can hardly understand other than plain language instructions. Any help will be appreciated.

---

### Post by dufourf on 2011-01-22
Hello,

I am having problems connecting my Eee 1015PEM (broadcom 4313) to a WPA Enterprise network, and extensive use of my limited Google-fu failed me.

I have already downloaded the very latest driver from broadcom and installed it, under Kubuntu 10.10, Kubuntu 10.04 and Ubuntu 10.10, to no avail. I also tried the repo's older driver, to no effect.

I can connect to unencrypted networks just fine, but my university's WPA2 enterprise PEAP MSCHAPv2 (with Thawte premium server cert) just does not authenticate (at least, that's what the error message is, under WICD it tells me that I got a wrong password, which is not the case) even though the settings are correct.

Is there any solution to this? I absolutely need to get this working, as SSH from outside that specific network is forbidden, and I need to log into those computers...

Thank you for your help in advance.

---

### Post by jchw on 2011-01-23
A couple of days ago I had my BCM 4312 card working OK but then I had to reinstall and since then I have not got it to work again. I have tried all the advice on the forum without success including installing Ndiswrapper. 

I have now downloaded the driver and have three files on my desktop. Can anyone guide me as to what to do with these three files to install them?

---

### Post by superduperlinuxperson on 2011-01-24
Hi!!! 

This is how I did it:

[LIST=1]
[*]To find out if your wireless card is supported, on terminal run lspci -vnn | grep 14e4
[*]Look at the part that says 14e4
[*]Supported chips (for this driver):
[*]this list includes other drivers :) 
14e4:4301 
   supported 
   BCM4301? 
   b43legacy 
    14e4:4301 
   supported 
   BCM4303 
   b43legacy 
    14e4:4306 
   supported 
   BCM4306/2 
   b43legacy 
    14e4:4320 
   supported 
   BCM4306/2 
   b43legacy 
    14e4:4307 
   supported 
   BCM4306/3 
   b43 
    14e4:4311 
   supported 
   BCM4311 
   b43/wl 
    14e4:4312 
   supported (802.11g only) 
   BCM4312 
   b43 
    14e4:4312 
   not supported - ID is duplicated 
   BCM4312 
   b43/wl 
    14e4:4313 
   partially supported 2.6.33 and later 
   b43/wl/[brcm80211]("http://wireless.kernel.org/en/users/Drivers/brcm80211") 
    14e4:4315 
   partially supported 2.6.33 and later (PIO mode) 
   BCM4312 
   b43/wl 
    14e4:4318 
   supported 
   BCM4318 
   b43 
    14e4:4319 
   supported 
   BCM4311? 
   b43 
    14e4:4320 
   supported 
   BCM4306/3 
   b43 
    14e4:4320 (USB) 
   not supported by b43/b43legacy 
   [rndis_wlan]("http://wireless.kernel.org/en/users/Drivers/rndis_wlan") 
    14e4:4321 
   not supported 
   wl 
    14e4:4324 
   not supported? 
   wl 
    14e4:4323 (USB) 
   not supported
   ndiswrapper 
    14e4:4325 
   not supported 
   wl 
    14e4:4327 
   not supported 
   wl 
    14e4:4328 
   not supported 
   BCM4321 
   wl 
    14e4:4329 
   not supported 
   BCM4321 
   wl/[brcmfmac via brcm80211]("http://wireless.kernel.org/en/users/Drivers/brcm80211") 
    14e4:432a 
   not supported 
   wl 
    14e4:432b 
   not supported 
   BCM4322 
   wl 
    14e4:432c 
   not supported 
   wl 
    14e4:432d 
   not supported 
   wl 
    14e4:4353 
   not supported 
   BCM43224 
   wl/[brcm80211]("http://wireless.kernel.org/en/users/Drivers/brcm80211") 
    14e4:4357 
   not supported 
   BCM43225 
   wl/[brcm80211]("http://wireless.kernel.org/en/users/Drivers/brcm80211") 
    14e4:4727 
   partially supported 2.6.33 and later 
   BCM4313 
   wl/[brcm80211]("http://wireless.kernel.org/en/users/Drivers/brcm80211") 
    14e4:5354 
   supported ? 
   b43
[*]On the device that[FONT=Arial] yo[/FONT]u installed it on, go to the pool/main/b/b43-fwcutter and double click on it and click install
[LEFT]On a computer with Internet access download these things: [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o ]("http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o")and [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)[/LEFT]
[*]Extract them to the Desktop
[*]Run following commands on Terminal: 
[FONT=Arial]$ cd Desktop
~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
~$ sudo b43-fwcutter -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o[/FONT]
[*][FONT=Arial]Turn your wireless off, then on (with the switch), and then click on the icon at the top and your done.[/FONT]
[*][FONT=Arial]If you get an error on the first command on the Terminal, just skip it!:P[/FONT]
[FONT=Arial]
[/FONT]
[/LIST]

---

### Post by panzerboyNZ on 2011-01-31
I had the wireless working after a new install of 10.10 but then I ran the update manager and updated everything it wanted to and now the wireless doesn't work. The system->admin->aditional drivers no longer finds the broadcom driver. I tried the instructions above but nothing. This is a brand new install and I'm loathed to re-install because then I'll have wasted all the bandwidth I paid for with the update.
I don't uderstand what STA or ndiswrapper are.
I'm assuming some other wireless driver may be interferring after the update?

regards,
Jeremy Thomson

---

### Post by panzerboyNZ on 2011-01-31
Oops! I suppose I'd bettwr let y'all know what Wireless I have
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       configuration: latency=64
       resources: memory:e2000000-e2001fff

---

### Post by panzerboyNZ on 2011-01-31
Okay got the BCM4318 working. I did a full install but this time I was connected to the internet via cable. I ticked the option to install & update and when searching for driver found the Broadcom driver. Activated and had to put the internet cable back in do download the firmware.
Wifi back up and running!
Took a deep breath and then ran the update, after reboot the Wifi stayed.
I wonder if other folks have had problems by installing disconnected?

regards,
Jeremy Thomson

---

### Post by Dutchy71 on 2011-02-07
Hi all,

I have a Lenovo S10e netbook with a Broadcom BCM4312 (rev 01) wireless network controller and a Broadcom Netlink BCM5906M (rev 02) ethernet controller. Unfortunately both wired/wireless access isn't working for me since upgrading from Win XP to Ubuntu 10.10.  Therefore updates as per the solutions in this forum aren't on the table for me.

Are there any alternative solutions to this issue?  Please note this is my second day as a Linux user. My first day began with a successful upgrade from Win Vista to Ubuntu on my HP Pavilion laptop.  It was a seemless and a very pleasant experience. This current situation has been much less pleasant. :(

Any and all assistance is greatly appreciated.  Cheers.

---

### Post by jvtrain on 2011-02-11
> **superduperlinuxperson said:**
> Hi!!! 

This is how I did it:

[LIST=1]
[*]To find out if your wireless card is supported, on terminal run lspci -vnn | grep 14e4
[*]Look at the part that says 14e4
[*]Supported chips (for this driver):
[*]this list includes other drivers :) 
14e4:4301 
   supported 
   BCM4301? 
   b43legacy 
    14e4:4301 
   supported 
   BCM4303 
   b43legacy 
    14e4:4306 
   supported 
   BCM4306/2 
   b43legacy 
    14e4:4320 
   supported 
   BCM4306/2 
   b43legacy 
    14e4:4307 
   supported 
   BCM4306/3 
   b43 
    14e4:4311 
   supported 
   BCM4311 
   b43/wl 
    14e4:4312 
   supported (802.11g only) 
   BCM4312 
   b43 
    14e4:4312 
   not supported - ID is duplicated 
   BCM4312 
   b43/wl 
    14e4:4313 
   partially supported 2.6.33 and later 
   b43/wl/[brcm80211]("http://wireless.kernel.org/en/users/Drivers/brcm80211") 
    14e4:4315 
   partially supported 2.6.33 and later (PIO mode) 
   BCM4312 
   b43/wl 
    14e4:4318 
   supported 
   BCM4318 
   b43 
    14e4:4319 
   supported 
   BCM4311? 
   b43 
    14e4:4320 
   supported 
   BCM4306/3 
   b43 
    14e4:4320 (USB) 
   not supported by b43/b43legacy 
   [rndis_wlan]("http://wireless.kernel.org/en/users/Drivers/rndis_wlan") 
    14e4:4321 
   not supported 
   wl 
    14e4:4324 
   not supported? 
   wl 
    14e4:4323 (USB) 
   not supported
   ndiswrapper 
    14e4:4325 
   not supported 
   wl 
    14e4:4327 
   not supported 
   wl 
    14e4:4328 
   not supported 
   BCM4321 
   wl 
    14e4:4329 
   not supported 
   BCM4321 
   wl/[brcmfmac via brcm80211]("http://wireless.kernel.org/en/users/Drivers/brcm80211") 
    14e4:432a 
   not supported 
   wl 
    14e4:432b 
   not supported 
   BCM4322 
   wl 
    14e4:432c 
   not supported 
   wl 
    14e4:432d 
   not supported 
   wl 
    14e4:4353 
   not supported 
   BCM43224 
   wl/[brcm80211]("http://wireless.kernel.org/en/users/Drivers/brcm80211") 
    14e4:4357 
   not supported 
   BCM43225 
   wl/[brcm80211]("http://wireless.kernel.org/en/users/Drivers/brcm80211") 
    14e4:4727 
   partially supported 2.6.33 and later 
   BCM4313 
   wl/[brcm80211]("http://wireless.kernel.org/en/users/Drivers/brcm80211") 
    14e4:5354 
   supported ? 
   b43
[*]On the device that[FONT=Arial] yo[/FONT]u installed it on, go to the pool/main/b/b43-fwcutter and double click on it and click install
[LEFT]On a computer with Internet access download these things: [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o ]("http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o")and [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)[/LEFT]
[*]Extract them to the Desktop
[*]Run following commands on Terminal: 
[FONT=Arial]$ cd Desktop
~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
~$ sudo b43-fwcutter -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o[/FONT]
[*][FONT=Arial]Turn your wireless off, then on (with the switch), and then click on the icon at the top and your done.[/FONT]
[*][FONT=Arial]If you get an error on the first command on the Terminal, just skip it!:P[/FONT]
[FONT=Arial]
[/FONT]
[/LIST]

I <3 U.

New install of 10.10 with no wireless. Followed your steps after much searching. Instead of turning wireless off/on, I restarted ubuntu and when I rebooted, the magical "Wireless Networks Available" brought a smile to my face.

Incidentally:
BCM4318

---

### Post by Dutchy71 on 2011-02-11
Many thanks [jvtrain]("http://ubuntuforums.org/member.php?u=1241086"). That worked a treat.  Thanks again for the prompt and very helpful response. The Linux community is alive and well. :D

---

### Post by initialhit on 2011-02-13
For those who did know there is also sometimes an issue with rfkill on broadcom wireless cards... to fix it just simply install the rfkill package... then see if anything is being blocked or disabled by rfkill and if it is unblock using the package. Note that this requires some knowledge of CLI ;)

---

### Post by daneel6672 on 2011-02-13
I have a Lenovo S12 and I've spent many, many hours going through the many fixes in this thread and elsewhere. Wireless is still not working.

Here's the output of lspci -vnn

```

07:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:04b5]
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at c2100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl, ssb

```

and iwconfig give me something that looks promising

```
eth1      IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:off   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

The output of dmesg looks promising too

```

[   28.230609] wl 0000:07:00.0: PCI INT A -> Link[L1E4] -> GSI 19 (level, low) -> IRQ 19
[   28.230630] wl 0000:07:00.0: setting latency timer to 64
[   32.934494] lib80211_crypt: registered algorithm 'TKIP'
[   32.934849] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.60.48.36 

```

But crucially when I try to scan for networks I get

```

sudo iwlist eth1 scanning 
eth1      Failed to read scan data : Invalid argument

```

I tried looking at rfkill to see if that was the problem but it doesn't mention wireless

```

rfkill list
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

When I switch the wireless button on and off this is what happens:

```

rfkill event
1297605973.937877: idx 2 type 2 op 0 soft 0 hard 0

Switch off...

1297605983.922479: idx 2 type 2 op 1 soft 0 hard 0

Switch on

1297605988.246922: idx 3 type 2 op 0 soft 0 hard 0
1297605988.251869: idx 3 type 2 op 2 soft 0 hard 0

Switch off

1297605991.067578: idx 3 type 2 op 1 soft 0 hard 0

Switch on

1297605994.133275: idx 4 type 2 op 0 soft 0 hard 0
1297605994.133353: idx 4 type 2 op 2 soft 0 hard 0

```

Here's the output of lshw -C network

```

sudo lshw -C network
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth1
       version: 01
       serial: c4:17:fe:fa:b1:f1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:c2100000-c2103fff

```

I've tried ndiswrapper and although that seems to load okay iwlist still does not work and when I use wireshark I see no packets being sent on wlan0 when I run dhclient. At least with wl I can see packets being sent out over the eth1 interface.

Not sure what else to try.

---

### Post by ThomasNovin on 2011-02-14
For those of you who are running the STA driver provided by Broadcom (same as in Maverick 10.10 although newer version) and also experience that the network is very slow after resuming from suspend, try this.

Unload the 'wl' module along with suspend and the re-load it along with resume.

To do this automatically, create a file in /etc/pm/sleep.d/ called 05_broadcom_wl and make it executable (owned by root and mode 0755) with this content:

```
#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
	suspend|hibernate)
		modunload wl
		;;

	resume|thaw)
		modreload wl
                ;;
esac

```

Works great for me! Now the wireless is always fast and I haven't had a single problem since I did this "trick".

---

### Post by se7ensamurai on 2011-02-17
> **johnnytm said:**
> I never really did anything Right after I installed Ubuntu I connected my ethernet card. awith the wored connection active now I went to **system-->administration-->additional drivers** My computer then did a search for availabe drivers and 2 drivers showed up, there was a b43 driver and the sta driver. I clicked o the sta driver and then pressed the activate button. ...

Just wanted to let you know that I got an Inspiron 1546 today, and the STA drivers mentiond above worked beautifully. Thanks to johnnytm for his straightforward explanation! :p

---

### Post by ELEE on 2011-02-23
For what it is worth I am really new at solving this stuff just try to search and read.
I spent hours on this over the last few days and finally this morning.

I have an older laptop  (I split the drive so I can boot XP or Ubuntu... can't run Quickbooks on Wine:()

[COLOR=DarkOrange]HP  Pavilion zv5000   (zv5466c)[/COLOR]
with
[COLOR=DarkOrange]BCM4306 802.11b/g Wirless LAN Controller (rev 03)[/COLOR]

I found this place of Documentation on another thread and followed this code and it worked.

[COLOR=Red]Ubuntu Documentation > Community Documentation > WifiDocsDriverbcm43xx[/COLOR]
[COLOR=Blue]
TERMINAL COMMANDS

[/COLOR][COLOR=Blue]~$ sudo apt-get update
~$ sudo apt-get install bcmwl-kernel-source

~$ sudo modprobe -r b43 ssb w[COLOR=Red]l[/COLOR]
~$ sudo modprobe w[COLOR=Red]l[/COLOR][/COLOR]
My only problem was realizing it was w(little L) NOT w(number One) in the last two commands.

I hope this helps someone.

Thanks to all who give.

Long live Linux... may I grow wise before I die.

---

### Post by mr best buy on 2011-02-25
> **Sef said:**
> Problem in Maverik Meerkat, 10.10, with the Broadband 43xx Wireless Card: Unable to download firmware for wireless.

Error Message:



**Solution**: System > Administration > Synaptic Package Manager > Search: firmware-b43-lpphy-installer > Click Mark > Click install > Close

Kontza found the [solution]("https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/651010") (post #3), so thank him for it.

This solution fixed this problem on my Dell Inspiron 1545 with a Broadcom 4312 card. (Card Tech Specs: 0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01))

Ok, follow instruction, found as expected.  It cannot be installed because I have no internet connection and no ethernet port  on my computer.  I have it on my install disk but do not know how to install it from my install disk.  I found the package on install disk and when i tried to install it from the disk, it informed me I was not on the internet HELP.  I AM NEW

---

### Post by mr best buy on 2011-02-25
> **johnnytm said:**
> I never really did anything Right after I installed Ubuntu I connected my ethernet card. awith the wored connection active now I went to system-->administration-->additional drivers My computer then did a search for availabe drivers and 2 drivers showed up, there was a b43 driver and the sta driver. I clicked o the sta driver and then pressed the activate button. After that all worked well. But I would recommend NOT using the b43 driver unless absolute last resort. I had that problem before. If you want the link where you can download the drivers from t not a problem, But the driver would have to be built first. Try this first though
```
 sudo apt-get --purge remove bcmwl-kernel-source
 sudo apt-get install patch  
 sudo apt-get install bcmwl-kernel-source         
 
``` if it still doesn't  work you can try
```
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source
```
One line at a time of course

It wont happen because I have no wired connection.  I have the file on the install disk, but do not have the knowledge to install it from the install disk

---

### Post by mr best buy on 2011-02-25
> **johnnytm said:**
> I never really did anything Right after I installed Ubuntu I connected my ethernet card. awith the wored connection active now I went to system-->administration-->additional drivers My computer then did a search for availabe drivers and 2 drivers showed up, there was a b43 driver and the sta driver. I clicked o the sta driver and then pressed the activate button. After that all worked well. But I would recommend NOT using the b43 driver unless absolute last resort. I had that problem before. If you want the link where you can download the drivers from t not a problem, But the driver would have to be built first. Try this first though
```
 sudo apt-get --purge remove bcmwl-kernel-source
 sudo apt-get install patch  
 sudo apt-get install bcmwl-kernel-source         
 
``` if it still doesn't  work you can try
```
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source
```
One line at a time of course

tried both ways and came up with error 1.  I had the netnet before I had to reinstall, and I had the internet during the install. 
but now now.  what can I do?

---

### Post by bonewhat on 2011-03-01
Dell Latitude XT2 with BCM4322 (0x432b) and Ubuntu 10.10

The proprietary driver (STA) shipped with 10.10 disconnected at random and quite often rendering it unusable.


As someone has been mentioned earlier in this thread there is a new and updated driver available at [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) .

Current version available at their website is 5.100.82.3
Version shipped with Ubuntu 10.10 is 5.60.48.36

The numbers spoke for themselves so I tried installing the drivers from the site.

Synopsis of the steps:
- I removed anything installed that showed up after searching for "broadcom" in Synaptic Package Manager.
- Followed the instructions in the readme.txt provided on the page.

The instructions shamelessly mentioned a previously installed wl.ko, in my case it was something else. Check the current installed drivers with "ls -l /lib/modules/`uname -r`/kernel/net/wireless" (note: dont touch lib80211*)


Been up and running flawlessly for half a day now.
/success !

---

### Post by heavyhanded on 2011-03-02
I thought I'd try out ubuntu 10.10 on my acer aspire one d250 to see how things were going these days with ubuntu. 

No wireless of the bat, and none of the solutions in the repository worked for me.  The "install additional drivers" tool seemed to make my wireless interface disappear completely. 

I ended up downloading the driver from broadcom and compiling it.  This works. 

I'm surprised there are so many problems with the broadcom drivers still.  

Didn't think I'd be using "make" as one of the first linux commands in 2011 haha.  Not exactly user freindly.

Read the README.txt on the broadcom site and follow the instructions and you should be ok if you can interpret the commands. I had to change a few things for it to work for me.

---

### Post by Sef on 2011-03-02
> Originally Posted by Sef  
Problem in Maverik Meerkat, 10.10, with the Broadband 43xx Wireless Card: Unable to download firmware for wireless.

Error Message:



[QUOTE]Solution: System > Administration > Synaptic Package Manager > Search: firmware-b43-lpphy-installer > Click Mark > Click install > Close

Kontza found the solution (post #3), so thank him for it.

This solution fixed this problem on my Dell Inspiron 1545 with a Broadcom 4312 card. (Card Tech Specs: 0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01))

Ok, follow instruction, found as expected. It cannot be installed because I have no internet connection and no ethernet port on my computer. I have it on my install disk but do not know how to install it from my install disk. I found the package on install disk and when i tried to install it from the disk, it informed me I was not on the internet HELP. I AM NEW[/QUOTE]

If you have a computer that has access to the net, then you can go [here]("http://packages.ubuntu.com/maverick/") and find them. I do not have the time now to get which subcategory they are in. You would download the packages, make sure that you have all the dependencies needed, and burn them to a disk and then put the disk into the machine without internet.

Try Lucid - an older version or natty, which is in testing mode, so expect a lot of bugs.

---

### Post by false_chicken on 2011-03-03
I have this same netbook. The aspire one D250. Can I get a link to the wireless driver? Or some info about how to get it to work? I just installed 10.10 desktop and I have no wireless connection.

---

### Post by JCollierDavis on 2011-03-03
> **mr best buy said:**
> Ok, follow instruction, found as expected.  It cannot be installed because I have no internet connection and no ethernet port  on my computer.  I have it on my install disk but do not know how to install it from my install disk.  I found the package on install disk and when i tried to install it from the disk, it informed me I was not on the internet HELP.  I AM NEW

There's some good instructions on [Ubuntu Documentation]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") on installing drivers from the install media by [adding a CD as a repository]("https://help.ubuntu.com/community/Repositories/Ubuntu").

Essentially in your software sources, CDROM appears as a choice.  It's probably unchecked now.  Check it and it should ask for the Disc when you do an update.

I'm having the same problem as you except my LAN port doesn't do anything when the wire's plugged in.

---

### Post by solocommand on 2011-03-03
Just wanted to say thanks for the information here, saved me a lot of time and trouble :) Worked great for my BCM4312 chipset.

---

### Post by heavyhanded on 2011-03-04
The Broadcom driver is here:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Follow the readme carefully if you go this route. If you don't blacklist the old drivers it wont work once you reboot.

Like I said, it worked for me on an acer aspire one d250 with the (BCM4312 I believe) but YMMV.  

Well at least Broadcom is releasing proper linux drivers these days... no more ndiswrapper BS.

---

### Post by Birdman19 on 2011-03-05
Well i have the Bcm 4318 802.11 b/g airforce one wireless card and it doesnt want to send or receive signals i have the driver installed that ubuntu recomends. But it still wont do anything sept basicly say hey im here and i work but im not going to do anything. 

edit: Im running desktop ubuntu on my laptop a hp dv5000 it has an BCM4318 airforce one 54g 802.11b/g wireless modem. I have tried the steps on the first page and they will not get my wireless card to work i can see networks and try to connect but it wont connect. Is there any way i could use these steps or some other steps to get my card up and running

---

### Post by ptn107 on 2011-03-07
Anyone who's having trouble with maverick's wl driver (5.60.48.36) should try natty's (5.100.82.38) driver:

[_get the 32-bit package here_]("http://mirror.pnl.gov/ubuntu//pool/restricted/b/bcmwl/bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu2_i386.deb")
[_get the 64-bit package here_]("http://mirror.pnl.gov/ubuntu//pool/restricted/b/bcmwl/bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu2_amd64.deb")

---

### Post by bourgtai on 2011-03-08
I'm running on a Compaq Presario 2100 with a Broadcom 4306 card, and on the outset it wouldn't connect to my wireless network with the B43legacy wireless driver.  I tried several of the solutions outlined by various members of this fine forum, but to no avail.  And, in fact, after trying one solution, the "additional drivers" program stopped trying to activate the legacy driver, stopped returning an error code, and told me to look in /var/log/jockey or some such for details.  This file proved to be completely unreadable.

I'm honestly on the verge of reverting to Windows XP.  It's slow and it's ugly, but by God, I can use it away from my desk.

---

### Post by coccu on 2011-03-13
> **ptn107 said:**
> Anyone who's having trouble with maverick's wl driver (5.60.48.36) should try natty's (5.100.82.38) driver:

[_get the 32-bit package here_]("http://mirror.pnl.gov/ubuntu//pool/restricted/b/bcmwl/bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu2_i386.deb")
[_get the 64-bit package here_]("http://mirror.pnl.gov/ubuntu//pool/restricted/b/bcmwl/bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu2_amd64.deb")


The link you provided doesn't work!  can you point me to another mirror?
Thnx

---

### Post by bkratz on 2011-03-13
@coccu

Found the two (deb files) of them here


[https://launchpad.net/ubuntu/natty/amd64/bcmwl-kernel-source/5.100.82.38+bdcom-0ubuntu2](https://launchpad.net/ubuntu/natty/amd64/bcmwl-kernel-source/5.100.82.38+bdcom-0ubuntu2)

[https://launchpad.net/ubuntu/+source/bcmwl/5.100.82.38+bdcom-0ubuntu2/+buildjob/2157341](https://launchpad.net/ubuntu/+source/bcmwl/5.100.82.38+bdcom-0ubuntu2/+buildjob/2157341)

---

### Post by graffiX on 2011-03-14
Is everyone that is saying this "works" just using b and g speed?  I can get basic networking but can't get N speed.

I have tried what feels like hundreds of combinations, including updating to the natty STA.

Thanks

---

### Post by Sef on 2011-03-16
> Is everyone that is saying this "works" just using b and g speed? I can get basic networking but can't get N speed.


If a computer that is only b/g is on or added to the network, then the speed will only be b/g speed. If you are running N speed, it will drop to b/g speed. (Which one will depend on the card. The network will only go as fast as the slowest card.)

---

### Post by coccu on 2011-03-16
> **bkratz said:**
> @coccu

Found the two (deb files) of them here


[https://launchpad.net/ubuntu/natty/amd64/bcmwl-kernel-source/5.100.82.38+bdcom-0ubuntu2](https://launchpad.net/ubuntu/natty/amd64/bcmwl-kernel-source/5.100.82.38+bdcom-0ubuntu2)

[https://launchpad.net/ubuntu/+source/bcmwl/5.100.82.38+bdcom-0ubuntu2/+buildjob/2157341](https://launchpad.net/ubuntu/+source/bcmwl/5.100.82.38+bdcom-0ubuntu2/+buildjob/2157341)


Thanks you bkratz and all.

I got it up and running now.  It's much more stable than the version came w/ 10.10.  I'll keep you posted if there is issue running N network.

---

### Post by graffiX on 2011-03-16
> **Sef said:**
> If a computer that is only b/g is on or added to the network, then the speed will only be b/g speed. If you are running N speed, it will drop to b/g speed. (Which one will depend on the card. The network will only go as fast as the slowest card.)

Thanks for the input Sef.  But this doesn't correlate to my setup.  I am the only device on the network.  I have the router set to N only.  I can actually connect with no security settings, but even with the router 1 foot away from my laptop I only get 52 mbit/s.

If there are security settings, it doesn't let me connect at all.

---

### Post by shinchan75034 on 2011-03-18
Hi, can anyone help me out? I can't seem to find the fix that works for me. I have BCM4311 wireless card. when I did 
sudo lshw -C network
and it shows the card being disabled. 

My laptop does not have a switch for wireless. 

Broadcom STA wireless driver is activated and currently in use. 

My system is a Dell Inspiron E1505, running Ubuntu Studio 10.10 Maverick. 

Network Settings connections tab are all greyed out. 

Your help is appreciated.

---

### Post by gigaforce1111 on 2011-03-18
Hi all,

I have the following card:
Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
I can't find solution for the wireless problem I have.
I tried what you offered in the first post and no good.
When I install the driver (b43) from the "Additional Drivers" menu and don't restart, the wireless works.
After restart the wireless is not listed on the network manager and doesn't work.
I don't have physical switch and the key combination start and stop only the bluetooth.
In the bios the switch is enabled.

Please Help!
Thanks in advance!

---

### Post by gtari on 2011-03-19
hello i have notebook acer aspire 5610z and i instaled the last relase of ubuntu but the problem its in wifi i have card Broadcom Corporation BCM4318 802.11b/g i try all soltion but not success any of the driver want work my wifi .can i get help  .thank you

---

### Post by bkratz on 2011-03-19
> **gtari said:**
> hello i have notebook acer aspire 5610z and i instaled the last relase of ubuntu but the problem its in wifi i have card Broadcom Corporation BCM4318 802.11b/g i try all soltion but not success any of the driver want work my wifi .can i get help  .thank you



A person in the absolute beginners forum posted a utube video in response to this device. Here is the link to the video

[http://www.youtube.com/watch?v=hAHN-YnmrLw](http://www.youtube.com/watch?v=hAHN-YnmrLw)


and post 47 of this thread

[http://ubuntuforums.org/showthread.php?t=1700025&highlight=BCM4318&page=5](http://ubuntuforums.org/showthread.php?t=1700025&highlight=BCM4318&page=5)

---

### Post by gtari on 2011-03-19
> **bkratz said:**
> A person in the absolute beginners forum posted a utube video in response to this device. Here is the link to the video

[http://www.youtube.com/watch?v=hAHN-YnmrLw](http://www.youtube.com/watch?v=hAHN-YnmrLw)


and post 47 of this thread

[http://ubuntuforums.org/showthread.php?t=1700025&highlight=BCM4318&page=5](http://ubuntuforums.org/showthread.php?t=1700025&highlight=BCM4318&page=5)
  


thankyou so much all ok and work perfect

---

### Post by gigaforce1111 on 2011-03-20
> **gigaforce1111 said:**
> Hi all,

I have the following card:
Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
I can't find solution for the wireless problem I have.
I tried what you offered in the first post and no good.
When I install the driver (b43) from the "Additional Drivers" menu and don't restart, the wireless works.
After restart the wireless is not listed on the network manager and doesn't work.
I don't have physical switch and the key combination start and stop only the bluetooth.
In the bios the switch is enabled.

Please Help!
Thanks in advance!

Found solution here:
[http://ubuntuforums.org/showthread.php?t=1708831](http://ubuntuforums.org/showthread.php?t=1708831)

---

### Post by david.flights on 2011-03-25
Hello - I am running a Asus EEEpc 1015PE with Ubuntu 10.10. 

When I try this solution below:

Kontza found the [solution]("https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/651010") (post #3), so thank him for it.

This is my output in Synaptic:

E: firmware-b43-lpphy-installer: subprocess installed post-installation script returned error exit status 1

I am unable to access wireless internet. Have tried many solutions. Any help welcome.

---

### Post by DarkTide on 2011-03-26
I have this same netbook. The aspire one D250. Can I get a link to the  wireless driver? Or some info about how to get it to work? I just  installed 10.10 desktop and I have no wireless connection.

---

### Post by lostmonster on 2011-03-26
I have a BCM4321 wireless card and this solution did not work.  I downloaded the appropriate driver for the wireless card, but I do not know where to put the file or how to install it/activate it.  

I am running a dualboot system; win7 was already installed, installed ubuntu 10.10 on a partition.

wireless card works fine on windows.  I am a beginner to ubuntu but i can follow steps.

---

### Post by Sef on 2011-03-27
> I have a BCM4321 wireless card and this solution did not work. I downloaded the appropriate driver for the wireless card, but I do not know where to put the file or how to install it/activate it. 


Which solutions have you tried? Mine does not require any downloading and installing except from the repositories, but others do require you to download and install. Unless we know what you have tried and problems that you have, we cannot help you more, so please be as specific as possible.  Thank you.

---

### Post by Xbuntu1 on 2011-03-27
> **david.flights said:**
> Hello - I am running a Asus EEEpc 1015PE with Ubuntu 10.10. 

When I try this solution below:

Kontza found the [solution]("https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/651010") (post #3), so thank him for it.

This is my output in Synaptic:

E: firmware-b43-lpphy-installer: subprocess installed post-installation script returned error exit status 1

I am unable to access wireless internet. Have tried many solutions. Any help welcome.


u must first upadate ur software from update manager, then from synaptic remove every driver installed for broadcom chipset ...and then finally install only b43-fwcutter and b43-lpphy-installer....this should work

---

### Post by Xbuntu1 on 2011-03-27
it is really easy to activate the drivers once you know it...you can check this [link]("http://easiertechsolutions.blogspot.com/") on how to activate drivers,,,it has lot of snapshots

---

### Post by graffiX on 2011-03-30
> **Sef said:**
> Which solutions have you tried? Mine does not require any downloading and installing except from the repositories, but others do require you to download and install. Unless we know what you have tried and problems that you have, we cannot help you more, so please be as specific as possible.  Thank you.


Sef do you get N speeds?  I am still unable to get any decent speed.

I have resorted to using a router in client mode to reach the other access point downstairs.... hardly elegant!

---

### Post by d3v1150m471c on 2011-03-30
good to know when i upgrade. aircrack is useless without this driver on that card.

---

### Post by Tman5293 on 2011-04-03
Didn't know how to delete my post but I have resolved the problem.

---

### Post by Sef on 2011-04-03
> graffiX: Sef do you get N speeds?

No. My card is b/g.

> Tman5293: Didn't know how to delete my post but I have resolved the problem.

Please post how you solved your problem, so that others may benefit from your experience.

---

### Post by bigbooboo on 2011-04-05
Hi there,

Excuse my jumping in and commenting with something that some may think is completely irrelevant.

I'm a complete newbie on Ubuntu 10.10 having migrated from Kubuntu which drove me insane with the tiny tiny bugs. I'm still getting to terms with simple terminal commands! Thankfully Ubuntu just seems so solid and great to use so far. 

I searched for hours and days on how to actually get my wireless up and running. I had the Broadcom STA drivers installed but couldn't get wireless. I use a Dell 1564 core i3 laptop and stupidly didn't realise that the usual Fn+F2 key combination doesn't activate the wireless network. The key combination for activating the wireless is actually CTRL + F2 (although I may have pressed CTRL+Fn+F2, but don't wanna check in-case something silly happens). There seem to be numerous posts about wireless drivers but none pointed this simple error out except for this user on this forum:

[http://www.linuxquestions.org/questions/ubuntu-63/wireless-became-disabled-how-do-i-enable-858357/](http://www.linuxquestions.org/questions/ubuntu-63/wireless-became-disabled-how-do-i-enable-858357/)

Just thought I'd contribute and maybe this might help someone who does actually have the drivers installed and running. 

Sorry to impose

---

### Post by xXkanfirXx on 2011-04-05
I'm new to Ubuntu as well... just installed it. Running 10.10 on a Dell Latitude D620. Everything is working great except I'm confused because it seems that it can find my wireless and I tried connecting it and it says its connected, but Firefox and anything else that's Internet related (update manager) won't work. It's a Broadcom BCM4312.

---

### Post by Tman5293 on 2011-04-05
> **Sef said:**
> Please post how you solved your problem, so that others may benefit from your experience.

I have one of the older B43 cards. Mine is actually a 4306/3. I was having trouble getting the drivers to work properly. I had just gone to "Additional Drivers" and installed the B43 drivers provided by the Ubuntu repositories. But after they installed and I rebooted my laptop, the wireless card was working but no networks were showing up in the network manager applet. So after several attempts at fixing this problem, which included installing different drivers and reinstalling Ubuntu all together, I discovered that the wireless card light on the front of my laptop never turns off regardless of whether the card itself is on or off! I found this out because in my complete frustration I decided to click the wireless button on the front of my laptop and then networks started popping up. Therefore ending my frustration and solving my problem.

Not sure how my little story/rant will help anybody but there it is. :)

---

### Post by mbayabo on 2011-04-06
I have a bit of a problem with my Broadcom 43xx Card. "WMP54gs"

I installed the driver by doing the following:

> sudo apt-get update
# then i went to System > Additional Drivers and installed the suggested driver


it works okay, but the problem is that it constantly disconnects me from the internet. has anyone found a solution to this? I've read a few posts about broadcom drivers not being perfect but most of those posts complain about how they have no wireless at all.

---

### Post by xXkanfirXx on 2011-04-06
Still having issues with my wireless working. Broadcom BCM4312. Connects to my wireless network but Internet doesn't work. Any help would be much appreciated.

---

### Post by rsborn on 2011-04-07
@[mbayabo]("http://ubuntuforums.org/member.php?u=1273665")

I have the same issue as you and have not really found a fix. I tried adjusting some power management settings that appeared promising at first but I still have frequent disconnects. Just to ensure we are talking about the same thing, here are the symptoms I encounter:

When attached to an open access point (no WEP, no WPA, etc)
- Disconnects happen but everything reconnects silently, no user interaction required 

When attached to a WEP/WPA/WPA2 access point
- Disconnects and sometimes reconnects silently
- Other times I have to re-click connect (my password/keys are saved in profile so no reentry necessary

There seems to be no contributing factor, I have seen it disconnect under heavy load as well as virtually no load. There has also been times that it has gone a whole day with no disconnect.

I do run a VMWare image of a windows 7 machine but that does not seem to make it any worse either (although of course when I lose wireless, windows goes to "limited connectivity mode")

My hardware is a Dell Precision M4500 i7
LSPCI output for the card is:
Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)

---

### Post by TossTheTV on 2011-04-10
Download "Ndisgtk" in Software Manager (Ndiswrapper in Synaptic)
gtk = graphic front end :popcorn:

On Ubuntu will show up in System > Administration as "Windows Wireless Drivers"
I think Linux Mint comes with this preinstalled..

If  wireless networks don't show up right off the bat (with superb   reception by the way), then open the program and direct it to the .inf   file in the Broadcom drivers folder of your windows partition. If you   dont' have windows then at least download the Broadcom WinXp drivers,   extract, and shove them in Home folder or something.
 
Broadcom has terrible support!! Their STA drivers are poor and don't support all the models that the Mini 210 comes from.
 
In terminal type:
[PHP]lspci -n | grep 14e4[/PHP] To  see what Broadcom model you have.  Will be 43xx. The 4315 for example  isn't supported yet! The netbook has  only been out for 2 + years! 
These  are supported: 4311           4312 4313 4313           4321                4322 
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

You  will most likely boost your reception by using NDISwrapper even if  your  model is supported and already working. You shouldn't have to  uninstall  the linux drivers or anything.. If you could already see  wireless  networks but not join them for any length of time, it is not a  driver  issue but a linux (Ubuntu) one. Search a fix, there are a  few  possible causes. Might just need an rfkill,  etc

I'm sick of fixing this netbook for a friend. Sata drivers for XP weren't fun either!

---

### Post by staind94 on 2011-04-12
Hello, after a long while, I have returned to Ubuntu.  My recent Windows corruption has led me to Ubuntu and so far am excited for the transition.  I am currently running Ubuntu 32bit 10.10.  I have noticed like all other Ubuntu builds from 9.10 to now, my wireless internet doesn't work...  is it because of my wireless card?  Its a Broadcom 4318 Airforce.  Will be very willing to provide as much info as needed. 

Thanks in advance!

---

### Post by TossTheTV on 2011-04-14
Download Ndisgtk in software manager!
Then go to Administration > Windows Wireless Drivers
and point it to the folder of Broadcom drivers you downloaded from their website (for Windows Xp/7). Try both 32 & 64bit.

---

### Post by AlanR8 on 2011-04-15
Howdy

Have posted this elsewhere but I think it's worth a repost.

On my Compaq Mini 10, Broadcom BCM4312.

All connects OOTB with Natty that has probably updated to the latest Beta over the last couple of weeks. Peachy when connected via the mains but on battery power the network/internet performance is DIRE.

ANY suggestions would help.

It would appear to me that the card seems to have power saving on whilst on battery but not on mains supply. How can I check and how can I disable power save in the future......

---

### Post by minivan on 2011-04-21
Thanks for these tips. I was installing 10.10 on a friends laptop and ran into this problem with the Broadcom 4318 driver. I installed the additional drivers (system - administration - addtional drivers) I also downloaded from the Ubuntu software center, the Windows Wireless Drivers. I still had a problem. I rebooted several times and nothing. The funny thing I was able to join my neighbors unprotected linksys router but not my own WEP one. Then I did the ( **Solution**: System > Administration > Synaptic Package   Manager > Search: firmware-b43-lpphy-installer > Click Mark >   Click install > Close) only in my case I had to do a reinstall since it was already installed but when I reinstalled it worked! I hope this makes sense since I am not a tech savvy person. I spent a good part of this afternoon on this but reinstalling worked for me. The laptop is a Gateway mx6027.

---

### Post by Rafa_Akd on 2011-04-23
> **minivan said:**
> Thanks for these tips. I was installing 10.10 on a friends laptop and ran into this problem with the Broadcom 4318 driver. I installed the additional drivers (system - administration - addtional drivers) I also downloaded from the Ubuntu software center, the Windows Wireless Drivers. I still had a problem. I rebooted several times and nothing. The funny thing I was able to join my neighbors unprotected linksys router but not my own WEP one. Then I did the ( **Solution**: System > Administration > Synaptic Package   Manager > Search: firmware-b43-lpphy-installer > Click Mark >   Click install > Close) only in my case I had to do a reinstall since it was already installed but when I reinstalled it worked! I hope this makes sense since I am not a tech savvy person. I spent a good part of this afternoon on this but reinstalling worked for me. The laptop is a Gateway mx6027.

I tried to di this but when I instaled it, there came an error:

Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up hotot (1:0.9.6~hg775-0ubuntu0ppa1~maverick1) ...
Setting up libtiff4 (3.9.4-2ubuntu0.4) ...
Processing triggers for python-support ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up firmware-b43-lpphy-installer (4.174.64.19-4) ...
Not supported card here (PCI id 14e4:4311)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-lpphy-installer

Anyone knows why?

Thank you

My device is a BM4311 and I'm using a HP Pavillon 2423

Bye

---

### Post by badboyz107 on 2011-04-25
Hey if anyone can help it would be greatly appreciated.  I have tried to run maverik netbook remix on my laptop as a stopgap solution, my wife dropped it and crashed the HD tht was running windows vista (bleh).  I have a new drive on order and will put Ubuntu on it to run it.  

This laptop is a Dell Inspiron wth the BCM4312 wireless, and I have tried EVERYTHING on here reference that refereence that set.  Nothing works, AT ALL, and I'm at the end of my wits.  Am I going to have the same problem when I try to install the full version of Maverik when my drive comes in??

I have used Ubuntu off and on for several years now but my knowledge of terminal and all that is slim.  I can post exactly what I have done in terminal so far exactly according to this  site.  Damn I hate not being able to solve problems myself but this is kind of urgent!

[help.ubuntu.com/community/wifidocs/driver/bcm43xx]("help.ubuntu.com/community/wifidocs/driver/bcm43xx")

```

ubuntu@ubuntu:~$ lspci -vvnn | grep 14e4
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
ubuntu@ubuntu:~$ sudu apt-get update
No command 'sudu' found, did you mean:
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
 Command 'tudu' from package 'tudu' (universe)
sudu: command not found
ubuntu@ubuntu:~$ sudo apt-get update
Get:1 http://security.ubuntu.com maverick-security Release.gpg [198B]
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Get:2 http://archive.ubuntu.com maverick Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Get:3 http://security.ubuntu.com maverick-security Release [31.4kB]
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Get:4 http://archive.ubuntu.com maverick-updates Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Get:5 http://archive.ubuntu.com maverick Release [39.8kB]
Get:6 http://archive.ubuntu.com maverick-updates Release [31.4kB]      
Get:7 http://security.ubuntu.com maverick-security/main Sources [40.1kB]      
Get:8 http://archive.ubuntu.com maverick/main Sources [829kB]       
Get:9 http://security.ubuntu.com maverick-security/restricted Sources [14B]
Get:10 http://security.ubuntu.com maverick-security/main i386 Packages [142kB]
Get:11 http://security.ubuntu.com maverick-security/restricted i386 Packages [14B]
Get:12 http://archive.ubuntu.com maverick/restricted Sources [4,370B]
Get:13 http://archive.ubuntu.com maverick/main i386 Packages [1,492kB]
Get:14 http://archive.ubuntu.com maverick/restricted i386 Packages [5,992B]    
Get:15 http://archive.ubuntu.com maverick-updates/main Sources [100kB]         
Get:16 http://archive.ubuntu.com maverick-updates/restricted Sources [778B]    
Get:17 http://archive.ubuntu.com maverick-updates/main i386 Packages [278kB]   
Get:18 http://archive.ubuntu.com maverick-updates/restricted i386 Packages [1,797B]
Ign cdrom://Ubuntu-Netbook 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/main Translation-en
Ign cdrom://Ubuntu-Netbook 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/main Translation-en_US
Ign cdrom://Ubuntu-Netbook 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/restricted Translation-en
Ign cdrom://Ubuntu-Netbook 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/restricted Translation-en_US
Fetched 2,997kB in 1min 18s (38.0kB/s)
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  binutils dkms fakeroot gcc gcc-4.4 libc-bin libc-dev-bin libc6 libc6-dev
  linux-libc-dev manpages-dev patch
Suggested packages:
  binutils-doc gcc-multilib autoconf automake1.9 libtool flex bison gcc-doc
  gcc-4.4-multilib libmudflap0-4.4-dev gcc-4.4-doc gcc-4.4-locales libgcc1-dbg
  libgomp1-dbg libmudflap0-dbg libcloog-ppl0 libppl-c2 libppl7 glibc-doc
  diffutils-doc
The following NEW packages will be installed:
  bcmwl-kernel-source binutils dkms fakeroot gcc gcc-4.4 libc-dev-bin
  libc6-dev linux-libc-dev manpages-dev patch
The following packages will be upgraded:
  libc-bin libc6
2 upgraded, 11 newly installed, 0 to remove and 315 not upgraded.
Need to get 10.6MB/18.6MB of archives.
After this operation, 42.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ maverick-updates/main libc-bin i386 2.12.1-0ubuntu10.2 [739kB]
Get:2 http://security.ubuntu.com/ubuntu/ maverick-security/main linux-libc-dev i386 2.6.35-1028.50 [816kB]
Get:3 http://archive.ubuntu.com/ubuntu/ maverick-updates/main libc6 i386 2.12.1-0ubuntu10.2 [3,814kB]
Get:4 http://archive.ubuntu.com/ubuntu/ maverick-updates/main dkms all 2.1.1.2-3ubuntu1.1 [71.3kB]
Get:5 http://archive.ubuntu.com/ubuntu/ maverick-updates/main libc-dev-bin i386 2.12.1-0ubuntu10.2 [218kB]
Get:6 http://archive.ubuntu.com/ubuntu/ maverick-updates/main libc6-dev i386 2.12.1-0ubuntu10.2 [4,910kB]
Fetched 10.6MB in 26s (392kB/s)                                                
Preconfiguring packages ...
(Reading database ... 120331 files and directories currently installed.)
Preparing to replace libc-bin 2.12.1-0ubuntu6 (using .../libc-bin_2.12.1-0ubuntu10.2_i386.deb) ...
Unpacking replacement libc-bin ...
Processing triggers for man-db ...
Setting up libc-bin (2.12.1-0ubuntu10.2) ...
(Reading database ... 120331 files and directories currently installed.)
Preparing to replace libc6 2.12.1-0ubuntu6 (using .../libc6_2.12.1-0ubuntu10.2_i386.deb) ...
Unpacking replacement libc6 ...
Setting up libc6 (2.12.1-0ubuntu10.2) ...
Generating locales...
  bn_BD.UTF-8... done
  bn_IN.UTF-8... done
  de_AT.UTF-8... done
  de_BE.UTF-8... done
  de_CH.UTF-8... done
  de_DE.UTF-8... done
  de_LI.UTF-8... done
  de_LU.UTF-8... done
  en_AG.UTF-8... done
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NG.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... done
  en_ZA.UTF-8... done
  en_ZW.UTF-8... done
  es_AR.UTF-8... done
  es_BO.UTF-8... done
  es_CL.UTF-8... done
  es_CO.UTF-8... done
  es_CR.UTF-8... done
  es_DO.UTF-8... done
  es_EC.UTF-8... done
  es_ES.UTF-8... done
  es_GT.UTF-8... done
  es_HN.UTF-8... done
  es_MX.UTF-8... done
  es_NI.UTF-8... done
  es_PA.UTF-8... done
  es_PE.UTF-8... done
  es_PR.UTF-8... done
  es_PY.UTF-8... done
  es_SV.UTF-8... done
  es_US.UTF-8... done
  es_UY.UTF-8... done
  es_VE.UTF-8... done
  fr_BE.UTF-8... done
  fr_CA.UTF-8... done
  fr_CH.UTF-8... done
  fr_FR.UTF-8... done
  fr_LU.UTF-8... done
  xh_ZA.UTF-8... done
  zh_CN.UTF-8... done
  zh_SG.UTF-8... done
Generation complete.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package binutils.
(Reading database ... 120331 files and directories currently installed.)
Unpacking binutils (from .../binutils_2.20.51.20100908-0ubuntu2_i386.deb) ...
Selecting previously deselected package gcc-4.4.
Unpacking gcc-4.4 (from .../gcc-4.4_4.4.4-14ubuntu5_i386.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4.4.4-1ubuntu2_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.6-2ubuntu1_i386.deb) ...
Selecting previously deselected package dkms.
Unpacking dkms (from .../dkms_2.1.1.2-3ubuntu1.1_all.deb) ...
Selecting previously deselected package linux-libc-dev.
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.35-1028.50_i386.deb) ...
Selecting previously deselected package libc-dev-bin.
Unpacking libc-dev-bin (from .../libc-dev-bin_2.12.1-0ubuntu10.2_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.12.1-0ubuntu10.2_i386.deb) ...
Selecting previously deselected package bcmwl-kernel-source.
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package manpages-dev.
Unpacking manpages-dev (from .../manpages-dev_3.24-1ubuntu1_all.deb) ...
Processing triggers for man-db ...
Setting up binutils (2.20.51.20100908-0ubuntu2) ...
Setting up gcc-4.4 (4.4.4-14ubuntu5) ...
Setting up gcc (4:4.4.4-1ubuntu2) ...
Setting up patch (2.6-2ubuntu1) ...
Setting up dkms (2.1.1.2-3ubuntu1.1) ...
Setting up linux-libc-dev (2.6.35-1028.50) ...
Setting up libc-dev-bin (2.12.1-0ubuntu10.2) ...
Setting up libc6-dev (2.12.1-0ubuntu10.2) ...
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu5) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-22-generic
Building for architecture i686
Building initial module for 2.6.35-22-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.35-22-generic/updates/dkms/

depmod........

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
cp: cannot stat `/vmlinuz': No such file or directory
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up fakeroot (1.14.4-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up manpages-dev (3.24-1ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
cp: cannot stat `/vmlinuz': No such file or directory
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 bcmwl-kernel-source
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
ubuntu@ubuntu:~$ sudo modprobe -r b43 ssb wl
ubuntu@ubuntu:~$ sudo modprobe wl
```

---

### Post by badboyz107 on 2011-04-26
> **superduperlinuxperson said:**
> Hi!!! 

This is how I did it:

[LIST=1]
[*]To find out if your wireless card is supported, on terminal run lspci -vnn | grep 14e4
[*]Look at the part that says 14e4
[*]Supported chips (for this driver):
[*]this list includes other drivers :) 
14e4:4301 
   supported 
   BCM4301? 
   b43legacy 
    14e4:4301 
   supported 
   BCM4303 
   b43legacy 
    14e4:4306 
   supported 
   BCM4306/2 
   b43legacy 
    14e4:4320 
   supported 
   BCM4306/2 
   b43legacy 
    14e4:4307 
   supported 
   BCM4306/3 
   b43 
    14e4:4311 
   supported 
   BCM4311 
   b43/wl 
    14e4:4312 
   supported (802.11g only) 
   BCM4312 
   b43 
    14e4:4312 
   not supported - ID is duplicated 
   BCM4312 
   b43/wl 
    14e4:4313 
   partially supported 2.6.33 and later 
   b43/wl/[brcm80211]("http://wireless.kernel.org/en/users/Drivers/brcm80211") 
    14e4:4315 
   partially supported 2.6.33 and later (PIO mode) 
   BCM4312 
   b43/wl 
    14e4:4318 
   supported 
   BCM4318 
   b43 
    14e4:4319 
   supported 
   BCM4311? 
   b43 
    14e4:4320 
   supported 
   BCM4306/3 
   b43 
    14e4:4320 (USB) 
   not supported by b43/b43legacy 
   [rndis_wlan]("http://wireless.kernel.org/en/users/Drivers/rndis_wlan") 
    14e4:4321 
   not supported 
   wl 
    14e4:4324 
   not supported? 
   wl 
    14e4:4323 (USB) 
   not supported
   ndiswrapper 
    14e4:4325 
   not supported 
   wl 
    14e4:4327 
   not supported 
   wl 
    14e4:4328 
   not supported 
   BCM4321 
   wl 
    14e4:4329 
   not supported 
   BCM4321 
   wl/[brcmfmac via brcm80211]("http://wireless.kernel.org/en/users/Drivers/brcm80211") 
    14e4:432a 
   not supported 
   wl 
    14e4:432b 
   not supported 
   BCM4322 
   wl 
    14e4:432c 
   not supported 
   wl 
    14e4:432d 
   not supported 
   wl 
    14e4:4353 
   not supported 
   BCM43224 
   wl/[brcm80211]("http://wireless.kernel.org/en/users/Drivers/brcm80211") 
    14e4:4357 
   not supported 
   BCM43225 
   wl/[brcm80211]("http://wireless.kernel.org/en/users/Drivers/brcm80211") 
    14e4:4727 
   partially supported 2.6.33 and later 
   BCM4313 
   wl/[brcm80211]("http://wireless.kernel.org/en/users/Drivers/brcm80211") 
    14e4:5354 
   supported ? 
   b43
[*]On the device that[FONT=Arial] yo[/FONT]u installed it on, go to the pool/main/b/b43-fwcutter and double click on it and click install
[LEFT]On a computer with Internet access download these things: [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o ]("http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o")and [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)[/LEFT]
[*]Extract them to the Desktop
[*]Run following commands on Terminal: 
[FONT=Arial]$ cd Desktop
~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
~$ sudo b43-fwcutter -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o[/FONT]
[*][FONT=Arial]Turn your wireless off, then on (with the switch), and then click on the icon at the top and your done.[/FONT]
[*][FONT=Arial]If you get an error on the first command on the Terminal, just skip it!:P[/FONT]
[FONT=Arial]
[/FONT]
[/LIST]

Okay so after doing everything listed above I have wireless network signal, note I said signal.  I can see all the networks around me, but I cannot connect to any of them now.

WHAT do I need to post or give someone around here to help me out???

---

### Post by badboyz107 on 2011-04-26
Okkkaaayyy

So I'm not sure what happened but I was just about ready to go strip it all out, all the broadcom related stuff, like it says to do in this post
[http://polach.cc/broadcom-wifi-adapter-wpa-access-fix-on-ubuntu-ii]("http://polach.cc/broadcom-wifi-adapter-wpa-access-fix-on-ubuntu-ii")

When I went to Synaptic and searched Broadcom I found 3 packages that were not selected/installed.
bcm5700-source
broadcom-sta-common
broadcom-sta-source

I applied all 3 of these pakages and up came my wireless.  As in came up instantly.  WTF????

Glad it works was getting ready to shell out cash for Widowz 7

---

### Post by cdoebbler on 2011-04-26
I have a Compaq-HP 110c with a Broadcom 4312 modem. Clicking on wireless icon in top bar shows my wireless (WEP protected) network available. When I try to connect I get password screen and type in password, but it does not connect. Tried connection on Vista laptop and it works fine. 

I tried all the responses above that were relevant (15 pages worth) over five days, but still not luck. My wireless network shows up but my Mini 110c just does not connect.

Clicking on "Connection Information" in drop down menu under icon gets message "No valid connections found!"    

Ifconfig response is:

eth0      Link encap:Ethernet  HWaddr 00:26:55:cd:7f:75  
          inet addr:192.168.1.36  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:55ff:fecd:7f75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19678 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13459 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:15441320 (15.4 MB)  TX bytes:2683028 (2.6 MB)
          Interrupt:43 

eth1      Link encap:Ethernet  HWaddr 0c:60:76:5e:40:18  
          inet6 addr: fe80::e60:76ff:fe5e:4018/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:7114
          TX packets:68 errors:16 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7684 (7.6 KB)  TX bytes:9860 (9.8 KB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

---

### Post by jasonmanchu on 2011-04-26
If you have broadcom 4312 you should be able to get it working without ndiswrapper or b43 cutter. you can use the sta proprietary drivers. i explain the page here:
[http://ubuntuforums.org/showthread.php?t=1738740](http://ubuntuforums.org/showthread.php?t=1738740)

also try these commands:
```
 sudo lshw -C network 
```
```
 lspci -vvnn | grep 14e4 
```

---

### Post by acornty on 2011-04-28
i love you. SO MUCH! thank you so much for this! i tried it on ubuntu 11.04 and it worked like a charm! thanks again!

---

### Post by graffiX on 2011-04-29
When you guys say "it's working" do you mean you're getting N speed?  My 4321 "works" but I don't get N speed at all.  I'm floating around 25 mbps sitting 3 feet from the access point.  Thanks for any insight.

---

### Post by magowiz on 2011-04-29
I just installed Natty on an HP Pavillon dv6000 equipped with Broadcom 4311.
The setup correctly  loaded the sta driver, which appears to be activated and running. Yet the wife adapter is dead: the on/off switch on the front panel is NOT switching the adapter on/off, and no Wifi is searched

---

### Post by dtusek on 2011-04-30
> **magowiz said:**
> I just installed Natty on an HP Pavillon dv6000 equipped with Broadcom 4311.
The setup correctly  loaded the sta driver, which appears to be activated and running. Yet the wife adapter is dead: the on/off switch on the front panel is NOT switching the adapter on/off, and no Wifi is searched


after upgrade to 11.04 I have the same problem with Broadcom 4311

---

### Post by MrD_scifi on 2011-04-30
I have 4311 also and STA says it is activated in additional drivers, but in the network manager it does not show wireless as working at all.  Interesting "upgrade" this is from 10.10.

---

### Post by Idaho Dan on 2011-04-30
4318 here, I got nothing.
I'll keep looking though because I'm stubborn.

---

### Post by Sef on 2011-05-01
> I have 4311 also and STA says it is activated in additional drivers, but in the network manager it does not show wireless as working at all. Interesting "upgrade" this is from 10.10.

Did you uninstall the all the proprietary drivers before upgrading? If not, that is likely the cause of your problem.

---

### Post by northd_tech on 2011-05-01
> **Idaho Dan said:**
> 4318 here, I got nothing.
I'll keep looking though because I'm stubborn.

Hi Idaho Dan,

You might want to take a look at posts #27 and #28 on the following thread for a Broadcom 4318:

[http://ubuntuforums.org/showthread.php?t=1737629&highlight=broadcom+4318&page=3](http://ubuntuforums.org/showthread.php?t=1737629&highlight=broadcom+4318&page=3)

EDIT:  And just for everyone's convenience, here is the link to Broadcom's STA driver download page:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by jingglang on 2011-05-01
My Axioo CNWP-015 has Broadcom 4312 LP-PHY network card. In my case  installing firmware-b43-lpphy-installer from synaptic did the trick. In  the middle of installation progress, it downloaded the appropriate  driver.

---

### Post by misetusame on 2011-05-01
Whao, so many suggestions out there, and I don't get which ones apply to me.

I have a Lenovo S12 with Broadcom BCM4312.

The STA driver is installed since 10.10 and is enabled.

In 10.10, the wireless didn't start automatically, but I **was able** to just click "Enable Wireless" in network manager.

Now in 11.04, however, the Enable Wireless option is just disabled.

Any pointers on what I should try next?

---

### Post by northd_tech on 2011-05-01
> **misetusame said:**
> Whao, so many suggestions out there, and I don't get which ones apply to me.

I have a Lenovo S12 with Broadcom BCM4312.

The STA driver is installed since 10.10 and is enabled.

In 10.10, the wireless didn't start automatically, but I **was able** to just click "Enable Wireless" in network manager.

Now in 11.04, however, the Enable Wireless option is just disabled.

Any pointers on what I should try next?

Let's see what modules you have loaded (or what is not getting loaded properly).  Can you post the results of the following terminal commands, misetusame?

```
lsmod

dmesg | grep b43

dmesg | grep wl

ifconfig

iwconfig
```

---

### Post by techborn on 2011-05-01
Ok so i think I have found this issue out - atleast for me

I did what Sef said to do in the very first post on this thread

**Solution 1**: System > Administration > Synaptic Package  Manager > Search: firmware-b43-lpphy-installer > Click Mark >  Click install > Close

Kontza found the [solution]("https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/651010") (post #3), so thank him for it.

This solution fixed this problem on my Dell Inspiron 1545 with a  Broadcom 4312 card. (Card Tech Specs: 0c:00.0 Network controller:  Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01))

**Solution 2: **Another option is [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers").

Update: The Live USB of Natty Narwhal (11.04) automatically detected  that I needed the STA driver.  After installing it and rebooting, the  wireless worked. (No cable was needed for this.)

Update 2: After installing with the alternate cd, I needed a cable and  after updating, I was able to download the STA driver through the  'Additional Drivers' section.






_________
But that didnt work for me so I was hooked up via Ethernet and I decided to try ndiswrapper or what ever its called. that didnt work either, I pretty much tried everything, beleave me I had to reinstall Ubuntu 6 times. no jokes!
However I did finally get it to work like i said i followed the first step (didnt work) then i remembered that i didnt activate the STA driver or wheat ever its called, so i went  systems->admin>additional drivers and clicked it , then to my surprise i had 2 additional drivers and instead of clicking the STA i clicked on B43 additional driver, rebooted and it WORKED, I was connecting right when it finished booting up.

FYI i run Ubuntu 10.10 netbook remix on a Lenovo S10. My Wireless chip is also broadcom 4312.

---

### Post by number61971 on 2011-05-01
Like [misetusame]("http://ubuntuforums.org/member.php?u=1040621"), I have a Lenovo S12 -- which appears to use the 4312 card -- and wireless worked just fine in Ubuntu 10.04 and 10.10. I just tried upgrading to 11.04 this morning and it is totally useless.

Previously I used the STA driver. The 11.04 version of this driver appears to be totally broken. The wireless card isn't even recognized.

After much searching, I have attempted two different ways of installing the b43 drivers, one using the packages available via Synaptic, and one attempting to build the driver from source. Neither worked. (Both of these methods were obtained from topics in these forums.)

This is absolutely crippling, of course, and renders the system totally unusable. I've been using Ubuntu for years, and am used to hiccups upon major upgrades, but this is atrocious. Was this driver *really* tested? And how can neither the STA nor the b43 drivers function?

---

### Post by ubunwhat on 2011-05-01
Hoping someone can offer some help for me.  I am running a Compaq Presario and, of course, lost my wireless when I upgraded.  I have tried to re-install the installer and received the following error message:


E: firmware-b43-lpphy-installer: subprocess installed post-installation script returned error exit status 1

So... I can't fix it that way.  It's an internal card so the USB fix is a bit lost on me.  Really, any help, even if it's silly, is better than sitting here with absolutely no idea what to do next.

---

### Post by Rifester on 2011-05-01
[http://ubuntuforums.org/showthread.php?t=1700897](http://ubuntuforums.org/showthread.php?t=1700897)

I have a Lenovo S10-2 with the Broadcom 4312 card.   My wireless broke during testing 11.04 in March.   It looks like it was released with the same feature...   This thread may help you solve your problem.   I am no longer using the STA driver.

---

### Post by ubunwhat on 2011-05-01
> **Rifester said:**
> [http://ubuntuforums.org/showthread.php?t=1700897](http://ubuntuforums.org/showthread.php?t=1700897)

I have a Lenovo S10-2 with the Broadcom 4312 card.   My wireless broke during testing 11.04 in March.   It looks like it was released with the same feature...   This thread may help you solve your problem.   I am no longer using the STA driver.


Way over my head.  I'm fairly new to Linux.  They lost me with blacklists and gdeb-something.  Am I supposed to add a blacklist or comment out the one I have?  I can't uninstall my current driver.  I tried, but I got an error message.  I also cannot install new drivers as I get error messages there as well.  So, can't uninstall, can't re-install.  Can't... Oh hell, I'm just screwed.

---

### Post by Rifester on 2011-05-01
I could try to walk you through it if you wish...  If you are not feeling very confident, it may be best to install either the LTS 10.04 or 10.10.   I am very sorry that you are having to deal with this as I know how frustrating it is.   This should have been fixed prior to release and may take some time to be corrected with updates.   There are bug reports filed at Launchpad, let them know this problem effects you as well.

---

### Post by ubunwhat on 2011-05-01
> **Rifester said:**
> I could try to walk you through it if you wish...  If you are not feeling very confident, it may be best to install either the LTS 10.04 or 10.10.   I am very sorry that you are having to deal with this as I know how frustrating it is.   This should have been fixed prior to release and may take some time to be corrected with updates.   There are bug reports filed at Launchpad, let them know this problem effects you as well.

If you could just explain something to me it would help greatly.  I cannot uninstall the old STA driver without getting an error message: 

SystemError: installArchives() failed

And any attempts to install newer or different versions of the broadcom driver fail as well.  Is this supposed to be happening?  By that, I mean, is this the problem that everyone else is running into, or is there a problem with my installation itself on top of the broadcom issue?  I'm willing to pick my way through this whatever it takes.  I absolutely have to have this  machine working tomorrow and starting over is not an option as I have servers, development environments, and other projects that would take weeks to set up again.  This is my fault entirely for not backing up first and just trusting the system, but I have to find a way to put humpty dumpty back together again tonight.  I would feel better about this if I new that I am in the same boat as everyone else.  Can you please just explain the problem here in basic terms?

---

### Post by Rifester on 2011-05-01
How are you trying to remove the packages?   Are you using Synaptic or a terminal?

---

### Post by ubunwhat on 2011-05-01
> **Rifester said:**
> How are you trying to remove the packages?   Are you using Synaptic or a terminal?

Synaptic for now.  Actually, in trying to remove the STA I simply clicked on additional drivers and this one came up as both active and running.  When I clicked remove I got the aforementioned error message.  I have also tried the terminal using commands I found on launchpad, but met no success there either.  Specifically:


sudo apt-get remove --purge firmware-b43-installer
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I also tried removing anything broadcom or STA related in Synaptic but got no love there either.  I can't recall the exact error message but could recreate it if needed.

---

### Post by Rifester on 2011-05-01
"sudo apt-get remove --purge firmware-b43-installer
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/)" ,
"is another process using it?"

Yes, this is because either Synaptic or Software Center are running.  I cannot assure you that what fixed my problem will fix yours.  Do you know what wireless card you are using?
Open a terminal and enter: lspci and the post the results...

If your card matches mine :  Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)   The instructions from nm_geo  in the thread I posted should work.

---

### Post by ubunwhat on 2011-05-01
Results:


lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by Rifester on 2011-05-01
You have a different card:  Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

I have another computer with the same exact card you have, unfortunately I am running Fedora 15/Gnome 3 on that computer.   It uses the open source broadcom driver and works flawlessly out of the box.    I know you said you did not back anything up, but is your installation on the entire drive or is your data/home on another partition?  If you installed with your data on another partition it would not take long at all to get your wireless working by downgrading the installed version.   Sorry I couldn't be more help.   I hope this gets sorted out quickly.

---

### Post by ubunwhat on 2011-05-01
> **Rifester said:**
> You have a different card:  Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

I have another computer with the same exact card you have, unfortunately I am running Fedora 15/Gnome 3 on that computer.   It uses the open source broadcom driver and works flawlessly out of the box.    I know you said you did not back anything up, but is your installation on the entire drive or is your data/home on another partition?  If you installed with your data on another partition it would not take long at all to get your wireless working by downgrading the installed version.   Sorry I couldn't be more help.   I hope this gets sorted out quickly.

Rife,  I want to seriously and sincerely thank you for your help.  Once I got my mind right and just picked my way through the fix in the link that you suggested everything fell into place.  You were right.  The fix on that link worked perfectly and all is well again here.  Beyond that, with so many people having this problem and so many trolls out there more concerned about mocking them than helping them, you stepped up and did a service.  I can't tell you how much I appreciate that.  You saved my bacon tonight.  Much, much good karma your way, my friend.

---

### Post by Rifester on 2011-05-01
Thank you my friend!   Somebody helped me and I got the opportunity to help you.   This is the way things should work!   For what it is worth the STA driver has always worked fine for me on the 4311 card (the same one that you have).   Things are screwed up this release.   I appreciate your response, I wanted to suggest that you try the fix but was not sure it would work with your card.   Good job!

---

### Post by misetusame on 2011-05-02
To follow up on my [previous message]("http://ubuntuforums.org/showpost.php?p=10751841&postcount=162"), **BCM4312** on my Lenovo S12 is **now working again**.

*What I did:*
**Booted into Windows**. Noticed is wasn't connecting here either. Did a Windows Update, and **Broadcom driver was updated**. Restarted and had to press **Fn+F5 to re-enable **wireless. This got it back working in Windows. After restarting in Ubuntu, it immediately connected for me.

*Background:*
I had the STA driver installed. In 10.10, I would have to click "Enable Wireless" in network manager to get the wireless to start. After upgrading to 11.04, the "Enable Wireless" was simply greyed out, and I therefore could no longer get it to connect.

---

### Post by number61971 on 2011-05-02
> **Rifester said:**
> [http://ubuntuforums.org/showthread.php?t=1700897](http://ubuntuforums.org/showthread.php?t=1700897)

I have a Lenovo S10-2 with the Broadcom 4312 card.   My wireless broke during testing 11.04 in March.   It looks like it was released with the same feature...   This thread may help you solve your problem.   I am no longer using the STA driver.
That was actually the first topic I found in trying to solve the problem. Nothing I tried in there worked. As I stated, I tried using the b43 driver instead of the STA driver, and it still didn't work.

I should also add that I attempted to use the previous STA driver from 10.10 Maverick -- no dice. Same story when I tried to use the previous b43 driver from 10.10 Maverick -- no dice.

The ONLY solution has been to reinstall Ubuntu 10.10. :confused:

---

### Post by nm_geo on 2011-05-02
Let's see I have the following flavors running on the b43 driver on the same old Dell D620 laptop and I do have the BCM4312 chipset.

2 - installs of Natty fully updated
1 - Xubuntu Natty
1 - Lucid 10.04 (my main version)

And on same laptop with STA driver
1 - Maverick 

I always try the STA driver first just to see if it will install properly, if it doesn't I remove all blacklists (etc/modprobe.d) on the b43 and ssb and install b43 and it's firmware. If you try the STA driver or had it working it will blacklist b43 and ssb. 

Run this in terminal to see what you might have blacklisted

```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl'
```Yeah windoze XP for things I have to do also.

---

### Post by rdunnion on 2011-05-02
For what it's worth I had to run ```
sudo modprobe b43
``` to get the driver working after installing the bcmwl-kernel-source package. I then added 'b43' to /etc/modules to load the driver at boot.

---

### Post by nm_geo on 2011-05-02
> **rdunnion said:**
> For what it's worth I had to run ```
sudo modprobe b43
``` to get the driver working after installing the bcmwl-kernel-source package. I then added 'b43' to /etc/modules to load the driver at boot.

I am confused here??  The bcmwl-kernel-source is the STA driver package and the b43 is a different driver.  Could you do put this in terminal please

```
sudo lshw -C network
```

and paste here.

---

### Post by sci.fi.jerry on 2011-05-03
had problems finding a solution for my  BCM4318 card. here is how i did it

removed fwcutter and bcm kernel source

install bcm kernel source

then installed via apt - firmware-b43

worked

--------
sudo apt-get install bcmwl-kernel-source or remove it then reinstall it clean
sudo apt-get remove b43-fwcutter
sudo apt-get install firmware-b43-installer 

-----------
if your wireless isnt working on restart just run:
modprobe b43

i tried lots of steps listed in the forum posts. None worked. This is the only way Ive found that works with no problems

my pc= dell inspiron 1300

---

### Post by laurenblah on 2011-05-03
> **magowiz said:**
> I just installed Natty on an HP Pavillon dv6000 equipped with Broadcom 4311.
The setup correctly loaded the sta driver, which appears to be activated and running. Yet the wife adapter is dead: the on/off switch on the front panel is NOT switching the adapter on/off, and no Wifi is searched
 
 
I think I'm having a similar problem. I'm not familiar with Linux only put it on my computer since Windows crashed. I updated from 10.04 to this one and my wireless won't work. Won't locate any wireless when I know I have one and the on/off switch stays orange when it should be blue.
 
Also, opening different windows will have a big white spot and sometimes if I resize the window a lot it'll finally show the window.
 
I have HP Pavilion dv6000 broadcom corporation BCM4311 802.11b/g WLAN
 
Thank you to anyone who can help me out.

---

### Post by avenditt on 2011-05-03
None of these solutions work for me.  I'm on Ubuntu 10.10 with a dell inspiron 1520.  I have a Broadcom wireless and ethernet card.  The ethernet works fine, the wireless doesn't.  When I install bcmwl-kernel-source and restart my computer my ethernet will also not work, until I do a 

sudo modprobe wl

the output of lspci -vvnn | grep 14e4

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)

So its only seeing my ethernet card.  Any ideas?

---

### Post by avenditt on 2011-05-03
The plot thickens...I try to perform the steps here [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

it seems that I have to remove the ssb module.  But when I do a 

sudo rmmod ssb

it returns

ERROR: Module ssb is in use by b44

So it seems my ethernet card needs it?

---

### Post by bkratz on 2011-05-03
> **avenditt said:**
> None of these solutions work for me.  I'm on Ubuntu 10.10 with a dell inspiron 1520.  I have a Broadcom wireless and ethernet card.  The ethernet works fine, the wireless doesn't.  When I install bcmwl-kernel-source and restart my computer my ethernet will also not work, until I do a 

sudo modprobe wl

the output of lspci -vvnn | grep 14e4

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)

So its only seeing my ethernet card.  Any ideas?


Apparently the wl driver is not being loaded at boot time.

Try  

```
gksudo gedit /etc/modules
```

and see if it says both wl and lp or just lp. If just lp we will probably have to add the wl here so it will load when booting.  Also, the b44 driver requires ssb so no you can't blacklist it.

---

### Post by westie457 on 2011-05-03
I also had this problem of wireless not working with the Broadcom STA Wireless driver after up-grading to 'Natty Narwhal' on my Acer laptop with a Broadcom 4311 wifi module. A big thank you to all who posted before me even though the suggestions put forward did not work. However I found a work around this problem and I hope others may find it useful.
The solution in my case worked using a network cable and 'Synaptic Package Manager'. This is what I did:-
1) In Additional drivers I de-activated the STA driver
2) In 'Synaptic' I then removed them completely.
3) Went back into Synaptic and found 'b43-fwcutter' and 'firmware-b43-installer'. I installed both packages because I was not sure which one was needed.
4) After a reboot wireless signed in to the router and the cable removed

---

### Post by avenditt on 2011-05-03
> **bkratz said:**
> Apparently the wl driver is not being loaded at boot time.

Try  

```
gksudo gedit /etc/modules
```and see if it says both wl and lp or just lp. If just lp we will probably have to add the wl here so it will load when booting.  Also, the b44 driver requires ssb so no you can't blacklist it.

So I opened the /etc/modules file and there was only Ip and rtc there.  I added the wl and still no wireless.

---

### Post by bkratz on 2011-05-03
Did you reboot?

---

### Post by avenditt on 2011-05-03
> **westie457 said:**
> I also had this problem of wireless not working with the Broadcom STA Wireless driver after up-grading to 'Natty Narwhal' on my Acer laptop with a Broadcom 4311 wifi module. A big thank you to all who posted before me even though the suggestions put forward did not work. However I found a work around this problem and I hope others may find it useful.
The solution in my case worked using a network cable and 'Synaptic Package Manager'. This is what I did:-
1) In Additional drivers I de-activated the STA driver
2) In 'Synaptic' I then removed them completely.
3) Went back into Synaptic and found 'b43-fwcutter' and 'firmware-b43-installer'. I installed both packages because I was not sure which one was needed.
4) After a reboot wireless signed in to the router and the cable removed

This won't work for me.  It doesn't display the STA driver in 'Additional drivers' even after i've installed the bcmwl-kernel-source file.

---

### Post by avenditt on 2011-05-03
Yes I rebooted.  Just to be clear before when I said my ethernet was working until I did a 
sudo modprobe wl

it was my ethernet that got working, *not* my wireless.  My wireless still doesn't work.

Currenly, I have bcmwl-kernel-source installed and for some reason my ethernet is actually working even after reboot now.  However, still wireless is not working.

---

### Post by bkratz on 2011-05-03
> **avenditt said:**
> Yes I rebooted.  Just to be clear before when I said my ethernet was working until I did a 
sudo modprobe wl

it was my ethernet that got working, *not* my wireless.  My wireless still doesn't work.

Currenly, I have bcmwl-kernel-source installed and for some reason my ethernet is actually working even after reboot now.  However, still wireless is not working.

Well adding the command we did simply does the same as your sudo modprobe wl, what I don't understand is why that has any effect on the wired connection. The STA driver (wl) is for the wireless. How about showing us the contents of

lsmod

use the code tags<> to make the list shorter and more readable and also the contents of

cat /etc/modprobe.d/blacklist.conf

By the way that was LSMOD in lowercase.

---

### Post by avenditt on 2011-05-03
```

lsmod
Module                  Size  Used by
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
wl                   1965231  0 
nvidia              10221046  42 
joydev                 11395  0 
snd_hda_codec_idt      64699  1 
r852                   11348  0 
sm_common               4441  1 r852
nand                   38430  2 r852,sm_common
snd_hda_intel          26147  4 
snd_hda_codec         100951  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  3 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_wmi                3372  0 
uvcvideo               62379  0 
lib80211                6175  1 wl
dell_laptop             6722  0 
nand_ids                4443  1 nand
nand_ecc                4406  1 nand
mtd                    21479  2 sm_common,nand
dcdbas                  6910  1 dell_laptop
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
snd                    64181  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l2_compat_ioctl32    12614  1 videodev
psmouse                62080  0 
serio_raw               4910  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
usbhid                 42030  0 
hid                    84710  1 usbhid
uvesafb                25058  1 
b44                    31306  0 
firewire_ohci          24839  0 
firewire_core          54327  1 firewire_ohci
sdhci_pci               8115  0 
sdhci                  18400  1 sdhci_pci
ahci                   22210  2 
led_class               3393  1 sdhci
ssb                    46201  1 b44
crc_itu_t               1739  1 firewire_core
mii                     5261  1 b44
libahci                26148  1 ahci
video                  22176  0 
output                  2527  1 video
intel_agp              32334  0 

cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac



```

---

### Post by bkratz on 2011-05-03
Sorry, but I really don't see anything that stands out. You didn't happen to turn off the wireless card in the bios or anything like that?

---

### Post by avenditt on 2011-05-03
No.  Checked BIOS, everything seems to be set to the factory default.  

Its very weird I had wireless and wired working with 10.10 before.  I upgraded to 11.04 and wired worked but after enabling the sta driver neither wired nor wireless worked.  Couldn't figure out what happened so I re-installed 10.10 and now the wireless doesn't work here either.

---

### Post by Gye50 on 2011-05-03
[SIZE=2]A[/SIZE]fter spending 2 days working out a solution for installing my Broadcom compatible Linksys wireless card in a Dell Inpsiron laptop, i thought some might benefit from my brief experience with Ubuntu version 11.04.  When i first installed 11.04 it seemed that the card should be installed in the same way it worked with versions 10.04 LTS and 10.10 which was fairly easy with a wired ethernet connection.  Just go to the System > Proprietary Drivers menu and let the search begin for the wireless drivers.  Not so.  Nothing was found by 11.04.  Network manager showed that wireless firmware was not installed.

So i proceeded to try a number of suggestions found on this forum and slowly i gathered some information about how all of this should work and followed these steps:

1)  Uninstalled and removed all failed attempts to install the drivers by using the same process whether it be by the Synaptic Package Manager or the Ubuntu Software Center.

2) Determined the number and type of Broadcom wireless card i had by entering a command in the terminal which showed it was a Broadcom BCM4318 wireless  LAN controller.  This forum has many suggestions on what to type in.

3) Went to the Synaptic Package Manager and searched for "firmware-b43" which brought up several files so i read the descriptions of each file to find the one that was for my BCM4318 card.

4) Then installed the firmware-b43-installer file but it said it also needed the b43-fwcutter file so i added that to the install process.

5) Rebooted and disconnected the ethernet connection so the laptop would use the wireless card to search for the network which it did and after i selected my router and entered the password everything has been fine.

Only complaint is that 11.04 prompts me for a keyring security code before it connects and that this process is much harder than just downloading the Broadcom proprietary drivers.  Guess Broadcom stopped supplying these for Linux.

---

### Post by nm_geo on 2011-05-03
> **avenditt said:**
> No.  Checked BIOS, everything seems to be set to the factory default.  

Its very weird I had wireless and wired working with 10.10 before.  I upgraded to 11.04 and wired worked but after enabling the sta driver neither wired nor wireless worked.  Couldn't figure out what happened so I re-installed 10.10 and now the wireless doesn't work here either.

 I think you will find the STA driver has blacklisted the ssb module and your wired connection needs it.  I am not on my linux box with my network commands, but i will be right back. C u in a Minute

---

### Post by nm_geo on 2011-05-03
Avenditt

if you are still around try this string of code just copy and paste in terminal then paste here.

```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|ssb|witch|wl'
```

If we find what I think the ssb and b43 will be listed as blacklisted.

---

### Post by avenditt on 2011-05-03
```

 cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|ssb|witch|wl'
# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
# Warning: This file is autogenerated by bcmwl. All changes to this file will be lost.
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt
options iwlagn 11n_disable=1

```

---

### Post by nm_geo on 2011-05-03
Yeah it looks like your ssb module is blacklist and your wired b44 driver needs it.  First things first you need to get rid of that blacklist on ssb and I would recommend on the b43 driver too. We need to place a # sign in front of those blacklist lines.  You need to become sudo and use gedit to correct those file and save them.  Here is the easiest way I know 

```
gksudo gedit /etc/modprobe.d/*
```The file you seek is created by the STA driver install and listed in the cat command above.  The line should look like # blacklist ssb then save the file.

---

### Post by avenditt on 2011-05-03
> **nm_geo said:**
> Yeah it looks like your ssb module is blacklist and your wired b44 driver needs it.  First things first you need to get rid of that blacklist on ssb and I would recommend on the b43 driver too. We need to place a # sign in front of those blacklist lines.  You need to become sudo and use gedit to correct those file and save them.  Here is the easiest way I know 

```
gksudo gedit /etc/modprobe.d/*
```The file you seek is created by the STA driver install and listed in the cat command above.  The line should look like # blacklist ssb then save the file.


Ok, I found the file
blacklist-bcm43.conf

I commented out blacklist ssb and blacklist b43....I rebooted, still no wireless.

there's also a blacklist b43-legacy and a blacklist bcm43xx

should I comment those out as well?

---

### Post by nm_geo on 2011-05-03
> **avenditt said:**
> Ok, I found the file
blacklist-bcm43.conf

I commented out blacklist ssb and blacklist b43....I rebooted, still no wireless.

there's also a blacklist b43-legacy and a blacklist bcm43xx

should I comment those out as well?

no need to do that let's try something else now that you have those blacklist clear.

Are you connected to the wired now?  

```
sudo lshw -C network
```

---

### Post by avenditt on 2011-05-03
> **nm_geo said:**
> no need to do that let's try something else now that you have those blacklist clear.

Are you connected to the wired now?  

```
sudo lshw -C network
```

```

*-network               
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:c0:7d:e2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=142.151.171.197 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:17 memory:f9dfe000-f9dfffff

```

yes I am connected to the wired network

---

### Post by nm_geo on 2011-05-03
Well at least the wired is working again.  I see no wireless info.

Try 

```
lspci
```and then paste. Hit the # sign in the reply 2 line 3rd from right and paste the results in the middle of the CODES that are created.   

Also 

```
rfkill list
```

---

### Post by avenditt on 2011-05-03
> **nm_geo said:**
> Well at least the wired is working again.  I see no wireless info.

Try 

```
lspci
```and then paste. Hit the # sign in the reply 2 line 3rd from right and paste the results in the middle of the CODES that are created.   

Also 

```
rfkill list
```

```
 lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```

```
 rfkill list
0: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

ya, thats better than typing out explicitly the tags.

---

### Post by nm_geo on 2011-05-03
You had wireless before correct?  Sorry, I forgot what type box you have too laptop or desktop?  I might be missing something but I see no wireless.

---

### Post by avenditt on 2011-05-03
> **nm_geo said:**
> You had wireless before correct?  Sorry, I forgot what type box you have too laptop or desktop?  I might be missing something but I see no wireless.

Yes, I definitely had wireless working before with 10.10.  Everything started to go wrong when I upgraded to 11.04.  I tried to install the STA driver then both the wired and wireless internet didn't work.  So I installed 10.10 and for some reason the wireless doesn't work here either now.  You think my wireless card might be shot or something?

I have a laptop.  Dell Inspiron 1520.

---

### Post by nm_geo on 2011-05-03
> **avenditt said:**
> Yes, I definitely had wireless working before with 10.10.  Everything started to go wrong when I upgraded to 11.04.  I tried to install the STA driver then both the wired and wireless internet didn't work.  So I installed 10.10 and for some reason the wireless doesn't work here either now.  You think my wireless card might be shot or something?

it could be but I would not jump to that conclusion just yet.  i have seen where some users just open their box and cleaned the card and it all started working.  looking back i see you have a dell inspiron 1520. We have some more that we can look at too.

```
sudo apt-get install hwinfo grep
```Then 

```
sudo hwinfo --netcard
```

---

### Post by avenditt on 2011-05-03
> **nm_geo said:**
> it could be but I would not jump to that conclusion just yet.  i have seen where some users just open their box and cleaned the card and it all started working.  looking back i see you have a dell inspiron 1520. We have some more that we can look at too.

```
sudo apt-get install hwinfo grep
```Then 

```
sudo hwinfo --netcard
```

```
sudo hwinfo --netcard
> hal.1: read hal dataprocess 2875: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
26: PCI 300.0: 0200 Ethernet controller                         
  [Created at pci.318]
  Unique ID: rBUF.DyZpBwGvIn5
  Parent ID: 6NW+.5nvCr7YV8cA
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:03:00.0
  SysFS BusID: 0000:03:00.0
  Hardware Class: network
  Model: "Broadcom BCM4401-B0 100Base-TX"
  Vendor: pci 0x14e4 "Broadcom"
  Device: pci 0x170c "BCM4401-B0 100Base-TX"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x01f1 
  Revision: 0x02
  Driver: "b44"
  Driver Modules: "ssb", "b44"
  Device File: eth0
  Memory Range: 0xf9dfe000-0xf9dfffff (rw,non-prefetchable)
  IRQ: 17 (188298 events)
  HW Address: 00:1d:09:c0:7d:e2
  Link detected: yes
  Module Alias: "pci:v000014E4d0000170Csv00001028sd000001F1bc02sc00i00"
  Driver Info #0:
    Driver Status: b44 is active
    Driver Activation Cmd: "modprobe b44"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #20 (PCI bridge)
 
```

---

### Post by nm_geo on 2011-05-03
Yes we see no wireless.  I saw you checked the bios earlier but that might still be something to check.  Here is my hwinfo

```
bigdad@bigdad-Latitude-D620:~$ sudo hwinfo --netcard 
> hal.1: read hal dataprocess 2693: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
24: PCI c00.0: 0282 WLAN controller                             
  [Created at pci.318]
  Unique ID: y9sn.jJPmv8UzN_1
  Parent ID: qTvu.f86JBt6kfy7
  SysFS ID: /devices/pci0000:00/0000:00:1c.1/0000:0c:00.0
  SysFS BusID: 0000:0c:00.0
  Hardware Class: network
  Model: "Dell Wireless 1490 Dual Band WLAN Mini-Card"
  Vendor: pci 0x14e4 "Broadcom"
  Device: pci 0x4312 "BCM4312 802.11a/b/g"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x0007 "Wireless 1490 Dual Band WLAN Mini-Card"
  Revision: 0x01
  Driver: "b43-pci-bridge"
  Driver Modules: "ssb"
  Device File: wlan0
  Features: WLAN
  Memory Range: 0xefdfc000-0xefdfffff (rw,non-prefetchable)
  IRQ: 17 (126512 events)
  HW Address: 00:19:7d:c5:67:29
  Link detected: yes
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13 14
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472 2.484
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v000014E4d00004312sv00001028sd00000007bc02sc80i00"
  Driver Info #0:
    Driver Status: ssb is active
    Driver Activation Cmd: "modprobe ssb"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #13 (PCI bridge)

25: PCI 900.0: 0200 Ethernet controller
  [Created at pci.318]
  Unique ID: rBUF.9a4JKShdn02
  Parent ID: hoOk.hz_o80M8jj8
  SysFS ID: /devices/pci0000:00/0000:00:1c.2/0000:09:00.0
  SysFS BusID: 0000:09:00.0
  Hardware Class: network
  Model: "Broadcom NetXtreme BCM5752 Gigabit Ethernet PCI Express"
  Vendor: pci 0x14e4 "Broadcom"
  Device: pci 0x1600 "NetXtreme BCM5752 Gigabit Ethernet PCI Express"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x01c2 
  Revision: 0x02
  Driver: "tg3"
  Driver Modules: "tg3"
  Device File: eth0
  Memory Range: 0xefcf0000-0xefcfffff (rw,non-prefetchable)
  IRQ: 44 (3 events)
  HW Address: 00:18:8b:c1:24:e5
  Link detected: no
  Module Alias: "pci:v000014E4d00001600sv00001028sd000001C2bc02sc00i00"
  Driver Info #0:
    Driver Status: tg3 is active
    Driver Activation Cmd: "modprobe tg3"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #14 (PCI bridge)

```See the wireless stuff  
Sorry but I am out of ideas ... for now 
Got to get

---

### Post by rafsyanrodzi on 2011-05-04
referring to solution1,
mine shows no files found.
referring to solution 2,
mine shows no files found.
hellpppppppppp

---

### Post by madvinegar on 2011-05-04
> **westie457 said:**
> I also had this problem of wireless not working with the Broadcom STA Wireless driver after up-grading to 'Natty Narwhal' on my Acer laptop with a Broadcom 4311 wifi module. A big thank you to all who posted before me even though the suggestions put forward did not work. However I found a work around this problem and I hope others may find it useful.
The solution in my case worked using a network cable and 'Synaptic Package Manager'. This is what I did:-
1) In Additional drivers I de-activated the STA driver
2) In 'Synaptic' I then removed them completely.
3) Went back into Synaptic and found 'b43-fwcutter' and 'firmware-b43-installer'. I installed both packages because I was not sure which one was needed.
4) After a reboot wireless signed in to the router and the cable removed



Super thank you my friend. It worked for me!:D

---

### Post by TombstoneX on 2011-05-04
No wireless networking. Was working properly prior to 11.04. 

Here are my outputs:



sudo lshw -C network
```

  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:ae:84:fa
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.167 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:ef9fe000-ef9fffff

```
sudo hwinfo --netcard

```
> hal.1: read hal dataprocess 1728: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
24: PCI c00.0: 0280 Network controller                          
  [Created at pci.318]
  Unique ID: zb5c.AUabv0M9SM3
  Parent ID: qTvu.KxZ2I+vnJeF
  SysFS ID: /devices/pci0000:00/0000:00:1c.1/0000:0c:00.0
  SysFS BusID: 0000:0c:00.0
  Hardware Class: network
  Model: "Dell Wireless 1390 WLAN Mini-Card"
  Vendor: pci 0x14e4 "Broadcom"
  Device: pci 0x4311 "BCM4311 802.11b/g WLAN"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x0007 "Wireless 1390 WLAN Mini-Card"
  Revision: 0x01
  Driver: "b43-pci-bridge"
  Driver Modules: "ssb"
  Memory Range: 0xefdfc000-0xefdfffff (rw,non-prefetchable)
  IRQ: 17 (6110 events)
  Module Alias: "pci:v000014E4d00004311sv00001028sd00000007bc02sc80i00"
  Driver Info #0:
    Driver Status: ssb is active
    Driver Activation Cmd: "modprobe ssb"
  Driver Info #1:
    Driver Status: wl is active
    Driver Activation Cmd: "modprobe wl"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #13 (PCI bridge)

25: PCI 300.0: 0200 Ethernet controller
  [Created at pci.318]
  Unique ID: rBUF.fjPIa6PWQp7
  Parent ID: 6NW+.mbQGvmFGPp7
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:03:00.0
  SysFS BusID: 0000:03:00.0
  Hardware Class: network
  Model: "Dell Inspiron 9400 Laptop"
  Vendor: pci 0x14e4 "Broadcom"
  Device: pci 0x170c "BCM4401-B0 100Base-TX"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x01cd "Inspiron 9400 Laptop"
  Revision: 0x02
  Driver: "b44"
  Driver Modules: "ssb", "b44"
  Device File: eth0
  Memory Range: 0xef9fe000-0xef9fffff (rw,non-prefetchable)
  IRQ: 17 (6110 events)
  HW Address: 00:18:8b:ae:84:fa
  Link detected: yes
  Module Alias: "pci:v000014E4d0000170Csv00001028sd000001CDbc02sc00i00"
  Driver Info #0:
    Driver Status: b44 is active
    Driver Activation Cmd: "modprobe b44"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #20 (PCI bridge)

```

---

### Post by zilmar on 2011-05-05
I've tried the solutions in the first post but I couldn't get my wireless to work.

I found another solution to this.
I installed the package bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb and my problem was gone.

---

### Post by skwon on 2011-05-05
> **vsh3r said:**
> Hi,

Is anyone else seeing some connectivity issues with the Broadcom BCM43224?  Is seems to connect just rather slowly compared to when I start the system with OSX.

V$H.


I have exact same problem with the same bcm...
I cant seem to find the right solution for it... help???

---

### Post by skwon on 2011-05-05
> **vsh3r said:**
> Hi,

Is anyone else seeing some connectivity issues with the Broadcom BCM43224?  Is seems to connect just rather slowly compared to when I start the system with OSX.

V$H.

> **Sef said:**
> Problem in Natty Narwhal - 11.04 with the Broadband 43xx Wireless Card: Unable to download firmware for wireless. (Also works for 10.10 and 10.04)

From the 'Additional Drivers' section:

  

Error Message:

**Solution 1**: System > Administration > Synaptic Package Manager > Search: firmware-b43-lpphy-installer > Click Mark > Click install > Close

Kontza found the [solution]("https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/651010") (post #3), so thank him for it.

This solution fixed this problem on my Dell Inspiron 1545 with a Broadcom 4312 card. (Card Tech Specs: 0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01))

**Solution 2: **Another option is [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers").

Update: The Live USB of Natty Narwhal (11.04) automatically detected that I needed the STA driver.  After installing it and rebooting, the wireless worked. (No cable was needed for this.)

Update 2: After installing with the alternate cd, I needed a cable and after updating, I was able to download the STA driver through the 'Additional Drivers' section.

After following these instructions, I rebooted my netbook, and the wireless light finally lit on!
However, my wirless still wont search... help! 

my card is BCM 43225 with STA card

---

### Post by narmire on 2011-05-05
So I have a BCM4312 802.11b/g LP-PHY wireless card, and upgraded to Ubuntu 11.04 last week. Since then I have been having problems with my wireless card. Originally I had the STA drivers installed, but they stopped working after about 24 hours (the exact issue that everyone else seems to be having). So I installed the b43 drivers, and it seemed to work as I could get wireless on my home network. Unfortunately that seems to be the only network I can get my wireless to work with. Everywhere else I can usually see wireless networks, and try to connect, but the connection always times out. 

I've been working on this for almost a week now, so any help would be greatly appreciated :)

---

### Post by tw1199 on 2011-05-05
Also having a similar problem with my wireless.
Dell Inspiron 1501, with BCM4311.
It worked great with b43 and restricted drivers in 10.10, but after upgrading to 11.04 the wireless was dead.
Both drivers reported alive but disabled. Followed forum directions for diagnosis but without joy.

Followed westie457 / madvinegar's solution and now it is back alive.  Thanks for the directions - greatly appreciated!

Ubuntu team - Perhaps a wise, clever and knowledgeable contributor could figure out what changed/broke between versions and could diagnose?  It has the profile of a subtle but fatal little adjustment.
... As always, keep up the great work!

---

### Post by GvAU on 2011-05-06
I have a system with a Linksys WMP54GS wireless card which has a BCM4306 (rev 3) Broadcom chip in it.  My network uses WPA2 (personal) security. This setup was always a hassle to configure under Ubuntu 8.04LTS and earlier systems (and Fedora before that).

Last weekend I successfully upgraded to Ubuntu 10.04LTS and my Linksys card worked correctly without any special reconfiguration action by me.  

Emboldened by this success and a bit keen to try Unity I thought I would upgrade to 11.04 Natty Narwhal.  The result (after struggling thru some black screen problems on bootup) was no wifi!  

After many unsuccessful attempts to fix the problem using suggestions etc in this forum I have kind of followed the instructions here ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access)) to get it working.  

Please note that I had a working cable connection which helped.

The steps involved were:

1. I used Synaptic to remove b43-fwcutter and firmware-b43-installer (I had earlier tried firmware-b43-lpphy-installer but removed it when it was not helpful).

2. Then I did:
~$ sudo apt-get install b43-fwcutter firmware-b43-installer

3. Followed by these two commands:
~$ sudo modprobe -r b43 ssb
~$ sudo modprobe b43

4. Followed by a shutdown and then a reboot.  On reboot the card came up and recognised local wifi networks.  

5. I then clicked on the NetworkManager to create an entry for my wifi, select WPA2, add the password, etc. and connected to my network ok. Shutdown and reboot and it was still working ok! :)

Other points:

I suspect that my Linksys card needs to be configured correctly on system boot as attempts to reconfigure at other times are problematic.

I had earlier tried installing b43-fwcutter and then installing firmware-b43-installer but using this two step approach did not seem to work (or maybe it was that I had not run the two modprobes).

I don't know what ssb is or why it should be included in the first modprobe but it worked so I will leave well enough alone for now.

I hope this is helpful to others.

Cheers
Gerry

---

### Post by backflip on 2011-05-06
> **westie457 said:**
> I also had this problem of wireless not working with the Broadcom STA Wireless driver after up-grading to 'Natty Narwhal' on my Acer laptop with a Broadcom 4311 wifi module. A big thank you to all who posted before me even though the suggestions put forward did not work. However I found a work around this problem and I hope others may find it useful.
The solution in my case worked using a network cable and 'Synaptic Package Manager'. This is what I did:-
1) In Additional drivers I de-activated the STA driver
2) In 'Synaptic' I then removed them completely.
3) Went back into Synaptic and found 'b43-fwcutter' and 'firmware-b43-installer'. I installed both packages because I was not sure which one was needed.
4) After a reboot wireless signed in to the router and the cable removed

Thank you so much, after much hair tugging I tried your solution and it worked perfectly on my Inspiron 6400.

---

### Post by TombstoneX on 2011-05-06
OS: Ubuntu 11.04 
Notebook: Dell Inspiron 9400
Wireless Card: BCM4311 802.11b/g WLAN


This worked perfectly for me.


> **westie457 said:**
> 
The solution in my case worked using a network cable and 'Synaptic Package Manager'. This is what I did:-
**1)** In Additional drivers I de-activated the STA driver
**2)** In 'Synaptic' I then removed them completely. *(I never did this step)*
**3)** Went back into Synaptic and found 'b43-fwcutter' and 'firmware-b43-installer'. I installed both packages because I was not sure which one was needed.
**4)** After a reboot wireless signed in to the router and the cable removed

---

### Post by silvertwilight on 2011-05-06
Thanks for finding a solution.  Acer Aspire 3000 with the bcm4318
chip. Wired connection and followed suggestions.  Worked to get
wireless going.  I run both MS  WINXP and Ubuntu on the laptop.
If you think you have downloaded and installed the software/firmware
recommendations and nothing happens,  do a search on bcm in the
Synaptic Network manager to pull up related files. I had to check
the box and install one of the above files and wireless worked 
after that.

---

### Post by MZBKA on 2011-05-07
Would anybody be willing to help me follow the readme guide here:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

I have a BC 4313 and the guide seems to be what has helped everybody with this wireless card, but I am new to linux. I don't know how to install the .tar.gz file I've downloaded from Broadcom's website.  In particular, I don't know what <PATH> means in 

```
 tar xzf <path>/hybrid-portsrc_x86-32_v5.100.82.38.tar.gz
```

I'm on at HP Pavilon g4
BCM4313 802.11b/g/n

Thanks a lot in advance.

---

### Post by ArinSky on 2011-05-07
Guys, make sure you are removing blacklists.

In your /etc/modprobe.d folder there are sets of blacklists. Often the STA driver will install a blacklist on the 43xx and all other broadcom drivers to make sure there won't be a conflict. I tried for hours doing the correct steps as posted in this, but it wouldn't work until I looked through the blacklists and found that the 43xx I was trying to install was indeed blacklisted in about 4 spots.

This also helped me fix my video card, ironically, as this update also forced me to downgrade to the nvidia 173 driver and it was having the same issue because of blacklists xD

---

### Post by theiron on 2011-05-07
A little late to the party, I had issues upgrading to 11.04 from 10.10 using the ISO from a USB stick while offline completely.  I ended up downgrading to 10.10 and got that working again without the STA, just the B43 Firmware updated.

That said, I've been timid of upgrading again until I hear from on high that all is solved, but I stumbled onto the following:

On another laptop, I had both wired and wireless connected during the upgrade, and the upgrade didn't change that.  So, may I suggest that them's thinking about upgrading do so with the network connections hooked up like you would normally, and it should retain the changes that were made to the previous rev.

I will be performing the upgrade again tonight, with the wireless connected, which was not the case when I tried prior.

---

### Post by MrD_scifi on 2011-05-09
Dell Inspiron 1520, Broadcom 4311

on fresh install of 11.04:

1) attach ethernet lead
2) in "additional drivers", turn off STA driver that was auto installed after vanilla 11.04 install
3) in synaptic package manager, remove bcmwl-kernel-source, every  b43/broadcom entry, finding them by using the "search" button on those  two terms and not the "quick filter"
4) restart computer
5) open terminal,"sudo apt-get install bcmwl-kernel-source"
6) restart computer and enjoy the wifi.

---

### Post by marty331 on 2011-05-09
> **MrD_scifi said:**
> Dell Inspiron 1520, Broadcom 4311

on fresh install of 11.04:

1) attach ethernet lead
2) in "additional drivers", turn off STA driver that was auto installed after vanilla 11.04 install
3) in synaptic package manager, remove bcmwl-kernel-source, every  b43/broadcom entry, finding them by using the "search" button on those  two terms and not the "quick filter"
4) restart computer
5) open terminal,"sudo apt-get install bcmwl-kernel-source"
6) restart computer and enjoy the wifi.


I have a Dell Inspiron 1525 with the Broadcom 4312.  Do you have any idea if this will work with my setup?  I installed Natty and was thoroughly disappointed that I could not get wifi to work, so I did a clean install of 10.10.  Also, I could not get Virtual Box to work, I use a windoz box on there for logging into one of my clients that has made it difficult for Linux.

Thanks,
marty

---

### Post by GuitarzanHV on 2011-05-09
I haven't had any luck with my own thread, so I'll try posting on here.

Upgraded from 10.10 to 11.04 on a Dell Inspiron 4010 with a Broadcom 4313 card.
For me, the wifi only works if I start the computer with ethernet plugged in. Sometimes if I go to another building on campus, the wifi will come back on, but on reboot its gone again. Tried using the b43 driver, no avail. Output of lshw, nm-tool, and rfkill list for working and non-working connections are below.

My own thread is here: [http://ubuntuforums.org/showthread.php?t=1753493](http://ubuntuforums.org/showthread.php?t=1753493)

---

### Post by marty331 on 2011-05-09
> **GuitarzanHV said:**
> I haven't had any luck with my own thread, so I'll try posting on here.

Upgraded from 10.10 to 11.04 on a Dell Inspiron 4010 with a Broadcom 4313 card.
For me, the wifi only works if I start the computer with ethernet plugged in. Sometimes if I go to another building on campus, the wifi will come back on, but on reboot its gone again. Tried using the b43 driver, no avail. Output of lshw, nm-tool, and rfkill list for working and non-working connections are below.

My own thread is here: [http://ubuntuforums.org/showthread.php?t=1753493](http://ubuntuforums.org/showthread.php?t=1753493)


Have you tried [MrD_scifi]("http://ubuntuforums.org/member.php?u=975266")'s recommendation above?  I am going to try doing an upgrade tonight and will see if it works on my Dell 1525 with Broadcom 4213.

---

### Post by GuitarzanHV on 2011-05-09
> **marty331 said:**
> Have you tried [MrD_scifi]("http://ubuntuforums.org/member.php?u=975266")'s recommendation above?  I am going to try doing an upgrade tonight and will see if it works on my Dell 1525 with Broadcom 4213.

Tried it. No go. What I found interesting though, was that I could use the internet without either the b43 or STA driver installed. It said in the lshw that the driver was "brcm80211" or something like that, I will check. Of course, still didn't work after restart. Going to try to load it after boot.

---

### Post by MrD_scifi on 2011-05-09
okay, Linux Mint 11 RC is out, and both 32 and 64bit versions require you to install the B43 driver in Package Manager to get the 4311 wifi card working.  On installing the OS, the STA driver is not activated as with Ubuntu 11.04.  I just had a right mess about, finally figuring to just install the B43 driver and reset to get wifi.  This is not going to help any new adopters of Ubuntu with these broadcom wifi cards.

STA driver does not appear to work for 4311 cards in Mint 11 RC.  B43 driver does not work in vanilla Ubuntu 11.04 with my 14e4:4311 card

---

### Post by daz23 on 2011-05-10
Here's the fix for a dell d830 laptop with a Broadcom BCM4311, done quickly from command line. 

> 
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer b43-fwcutter


reboot

---

### Post by westie457 on 2011-05-10
Have now got the STA driver working for BCM4311 Wireless. The answer for me was found here :- 


//help.ubuntu.com/community/WifiDocs/Driver/bcm43xx


So far it is working without a reboot.

However if your card is not supported by the STA driver the previous work around **should **work.

Again many thanks to all who helped me even though they were helping others. All I did was read the threads for ideas and did trial and error to get wireless working.

---

### Post by Josh123 on 2011-05-10
> **narmire said:**
> So I have a BCM4312 802.11b/g LP-PHY wireless card, and upgraded to Ubuntu 11.04 last week. Since then I have been having problems with my wireless card. Originally I had the STA drivers installed, but they stopped working after about 24 hours (the exact issue that everyone else seems to be having). So I installed the b43 drivers, and it seemed to work as I could get wireless on my home network. Unfortunately that seems to be the only network I can get my wireless to work with. Everywhere else I can usually see wireless networks, and try to connect, but the connection always times out. 

I've been working on this for almost a week now, so any help would be greatly appreciated :)

I have the same lpphy (aka low power) card and I went through all the hardships that you stated above. 
b43 driver- 
Install firmware-b43-lpphy-installer and b43-fwcutter. However this driver gives DMA error in some machines like mine. You can see that in dmesg.That prevents it from connecting to some routers.  I had to put the wireless in PIO mode by creating b43.conf file in /etc/modprobe.d with following line- 
options b43 pio=1 qos=0 
My wireless started working. However b43 does not work seemlessly with this card. It showed network connected at lower speeds -- 1Mb/s to 18 Mb/s in the same room where my router is. In my case , connection dropped suddenly after couple of hours and would not re-connect. (I had to reboot or sudo modprobe -r b43 and sudo modprobe b43). This was very irritating. 

sta driver- I found the solution by jedi-penguin given here- 

[http://ubuntuforums.org/showthread.php?t=1700897&page=2](http://ubuntuforums.org/showthread.php?t=1700897&page=2)

the driver is here-
[http://packages.ubuntu.com/maverick/bcmwl-kernel-source](http://packages.ubuntu.com/maverick/bcmwl-kernel-source)
Ultimately, I installed the Broadcom-STA driver of Ubuntu10.10 maverick.

My card is working at full speed now (54 Mb/s). Though I have to check whether connection drops after couple of hours, I feel that will not happen.

---

### Post by westie457 on 2011-05-11
> **westie457 said:**
> Have now got the STA driver working for BCM4311 Wireless. The answer for me was found here :- 


//help.ubuntu.com/community/WifiDocs/Driver/bcm43xx


So far it is working without a reboot.

However if your card is not supported by the STA driver the previous work around **should **work.

Again many thanks to all who helped me even though they were helping others. All I did was read the threads for ideas and did trial and error to get wireless working.
OOPS it broke after a reboot.

Have now reverted to my original solution and given up using the STA driver.

Many thanks to 'josephmills' on this thread here 

[http://ubuntuforums.org/showthread.php?t=1748245&page=5](http://ubuntuforums.org/showthread.php?t=1748245&page=5)

It explained very clearly how to find what equipment you have and what drivers you need and how to install them

---

### Post by marty331 on 2011-05-11
I'm on a Dell 1525 with a Broadcom 4312.

This is what worked for me:
I followed MrD's suggestions and had to tweak it a little:
1) attach ethernet lead
2) in "additional drivers", turn off STA driver that was auto installed after vanilla 11.04 install
3) in synaptic package manager, remove bcmwl-kernel-source, every   b43/broadcom entry, finding them by using the "search" button on those   two terms and not the "quick filter"
4) restart computer
5) open terminal,"sudo apt-get install bcmwl-kernel-source"
6) restart computer and enjoy the wifi.
(at this point I did not have wifi going so then I continued on)
7)  in synaptic package manager I searched (again search, not quick filter) for broadcom and installed the following: b43-fwcutter, broadcom-sta-common, broadcom-sta-source.  Already installed was bcmwl-kernal-source, so I left that alone.
8)  restart, yes again.  I was still connected to ethernet but I hovered over my ethernet and opened the list of availalble networks and could see my wfie, so I disconnected the ethernet and connected to wifi.

I hope this helps someone!

---

### Post by Josh123 on 2011-05-11
> **Josh123 said:**
> 
[http://ubuntuforums.org/showthread.php?t=1700897&page=2](http://ubuntuforums.org/showthread.php?t=1700897&page=2)

Ultimately, I installed the Broadcom-STA driver of Ubuntu10.10 maverick.
the driver is here-
[http://packages.ubuntu.com/maverick/bcmwl-kernel-source](http://packages.ubuntu.com/maverick/bcmwl-kernel-source)


My card is working at full speed now (54 Mb/s). Though I have to check whether connection drops after couple of hours, I feel that will not happen.

My wireless is working well for ten hours. Cheers :)

---

### Post by MrD_scifi on 2011-05-11
There seems to be a number of different fixes to this issue doesn't there?  This might make fixing the issue globally for a number of Broadcom wifi card owners on different systems a lot harder to manage.

The fact my card operated with both STA and B43 drivers in the previous release is interesting.

---

### Post by josephmills on 2011-05-11
hi there guys and girls:D I would just like to clear up a couple of things. If you think that you need the b43 or the b43sta, these are two different mods/drivers the first thing that you want to do is type in  
```
lspci -vnn | grep 14e4 
```
this is what this code will do  
**ls** stands for list 
**pci** stands for pci cards in the computer 
**-vnn ** stands for find the model number 
**grep** grep is a filter so it filters out the 14e4 thats why it is in a different color 
**14e4** is what grep (the filter)is looking for 
so ls-->+<--pci=list pci cards 
lspci -vnn= list pci cards with model number 
lspci -vnn | = listpci cards with model number and stop 
lspci -vnn | grep = list all pci cards with a model number and filter with grep 
lspci -vnn | grep 14e4 = list all pci cards with model number and a filter with grep using 14e4 for the filter.


So what does this all mean well the** b43fwcutter only**works for the model numbers [b]
14e4:4307
14e4:4311
14e4:4312 IMPORTANT if you have this card you need the firmwareb43-lpphy-installer for your firmware 
14e4:4318
14e4:4319
14e4:4320
14e4:5354
[/b]


If you have model number[b]
14e4:0576
14e4:4313
14e4:4315 
14e4:4328
14e4:4329
14e4:432a
14e4:432b
14e4:432c
14e4:432d       
14e4:4353
14e4:4357
14e4:4358
14e4:4359
14e4:435a
14e4:4727
14e4:a99d
[/b]
then you are going to need the **broadcom-sta-source + broadcom-sta-common** 

both the b43fwcutter and the b43sta use the firmware-b43-installer
unless noted 

If you have the model number 
[b]
14e4:4301
14e4:4306
14e4:4320 
14e4:4324
[/b]
Then you are going to need the **b43-fwcutter with the firmware-b43legacy-installer **

**IMPORTANT** all of these card also need the bcmwl-kerrnel-source

Ok now that we have found our card and its model number and we know what mod/driver and firmware we need. Its time to install all of it. 
**Important** for these next steps you will need a internet connection using a cat5 cable(ethernet) or whatever as long as you are on line. If are dealing only with wireless see section installing b43fwcutter with out internet connection. 

First before installing we need to remove anything that is there right now so open up synaptic package manager and type in bcm into the search bar then click on the green box's and mark for removal then press the apply button now reboot the computer 
after rebooting start to install the things that you need by opening up synaptic package manger and type in bcm follow the chart above to install the correct mods/driver and firmware then reboot again is your wireless working. 


If not lets do some diagnostics please open your terminal and type in 
```
rfkill list 
``` where **rf**stands for Radio frequency kill stands for umm... and list is to list all the Radio frequency
if there is a soft block or a hard block please do a ```
rfkill unblock all 
``` if that wont work try ```
rfkill unblock wifi or rfkill unblock wlan
```

Now that we know that nothing is blocked lets look at your mods/drivers 
 ```
lsmod | grep b43
``` this will **ls=list-->+<--mod=mods/driver** so ls+mod=list all mods | means stop and grep is the filter and b43 is what grep is looking for 
do you see you mods listed it would be nice if some of the people with working wireless could post there lsmod + there model number of there card 

If lsmod looks good lets move on to the firmware 
```
dmesg | grep b43 
``` so dmesg looks up what the linux kernel sees and grep is the filter **IMPORTANT if you are useing the b43sta then you need top type in wl instead of b43 **

Are you geting any errors go re-install the firmware again this is the part that seems to be "the bug in the gar" 

**Installing b43fwcutter with out the internet connection** 

Ok so you have no internet connection on your Ubuntu box for what ever reason. but you need it. Well here is how to get it. These are the things that you are going to need.  

1) a blank cd/dvd or a penn drive or external hard drive or some way to transfer files (phone?) whatever. 

2) you are going to need another computer of some sorts to download your mods/firmware 


Ok, now that you have thous two things lets move on.

download this file  [http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)

Then transfer it over to your Ubuntu box 

Now in  your Ubuntu Box [computer]  please make your way to your **Home folder ** 

Once you are at your home folder right click on your home folder and ** make a new folder and call it wireless**

Now that you have made a new folder called wireless in your home directory. It is time to **move the downloaded file into the new folder called wireless** 

Next we need to move that folder to the firmware directory to do this open your terminal and type in 
```
sudo cp -r ~/wireless/* /lib/firmware/
``` 

Now lets double check to make sure the download made it to the firmware directory. Too do this type this into the terminal 
```
ls /lib/firmware
```
Do you see it there ? Good if not it did not moved. Go back to the last step and try again. But if you do see it lets move on to the next step

Ok so now that the download is in the firmware dir we are going to have to go there. To go there open your terminal and type in. 
```
cd /lib/firmware 
```
Now that you have moved lets double check to make sure this next code tells us where we are in the computer file dir. This next code stands for "print working directory" ```
pwd
``` are you at /lib/firmware if so good if not go back one step 

Now that we are in the firmware directory. We have to extract the download to do this type in 
```
sudo -s
``` then enter your password then 
```
tar -xzf b43-all-fw.tar_.gz
```
then 
```
exit
```

Now it is time to reboot 
```
sudo reboot 
```

Do you have wireless now ? If not you did some thing wrong. 
If you have some troubles please post here and some one will help you out 


Well I hope that this clears some stuff up about the b43fwcutter and the b43sta and also the b43-legacy have fun with your wire less! Please don't forget if you have one of these cards and they are working please post your lsmod and dmesg with model number of the card thanks again also I would like to say that I am working on a how to install with out the internet for the b43sta but do not have the hardware for it yet I am working on it. give me a couple of days thanks again and happy wireless :D
Joseph

---

### Post by MZBKA on 2011-05-11
> **MrD_scifi said:**
> Dell Inspiron 1520, Broadcom 4311

on fresh install of 11.04:

1) attach ethernet lead
2) in "additional drivers", turn off STA driver that was auto installed after vanilla 11.04 install
3) in synaptic package manager, remove bcmwl-kernel-source, every  b43/broadcom entry, finding them by using the "search" button on those  two terms and not the "quick filter"
4) restart computer
5) open terminal,"sudo apt-get install bcmwl-kernel-source"
6) restart computer and enjoy the wifi.

This doesn't work with the 4313 wireless card.  After the restart, the wireless stops working again. . .

Has anybody found a solution to the 4313 card?  Or can anybody help me install the driver found on broadcom's website?  The readme, which is not made for new linux users like me, is found here [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

---

### Post by coffeecat on 2011-05-11
> **MZBKA said:**
> 
BCM4313 802.11b/g/n


Your card *should* work in Natty out-of-the-box with the new open source  brcm80211 kernel driver. At least it did for me with a different model HP machine, but with the same BCM4313 card.

I've not searched the whole of this thread, but I see that the brcm80211 driver hasn't been mentioned in recent posts. People, please be aware that there is a new FOSS driver that comes in the box and which  supports [a handful of Broadcom N chipsets]("http://wlanbook.com/broadcom-wifi-driver-for-linux-11n-chips-now-open-source/"). It's working fine with my WPA2-PSK home network.

---

### Post by MZBKA on 2011-05-11
> **coffeecat said:**
> Your card *should* work in Natty out-of-the-box with the new open source  brcm80211 kernel driver. At least it did for me with a different model HP machine, but with the same BCM4313 card.

I've not searched the whole of this thread, but I see that the brcm80211 driver hasn't been mentioned in recent posts. People, please be aware that there is a new FOSS driver that comes in the box and which  supports [a handful of Broadcom N chipsets]("http://wlanbook.com/broadcom-wifi-driver-for-linux-11n-chips-now-open-source/"). It's working fine with my WPA2-PSK home network.

Hi there.  Thanks for your reply.  The card did not work out of box. That's why I tried using the STA driver.

Edit: I'd be willing to try the brcm80211 kernel driver again though.  How should I do this?

according to this [http://linuxwireless.org/en/users/Drivers/brcm80211#Firmware_installation](http://linuxwireless.org/en/users/Drivers/brcm80211#Firmware_installation)
the brcm80211 is untested on 64 bit linux.  Maybe that's my problem?

---

### Post by coffeecat on 2011-05-11
> **MZBKA said:**
> Edit: I'd be willing to try the brcm80211 kernel driver again though.  How should I do this?

Simply run the live CD or live USB and see if you can connect wirelessly without installing anything. If it connects, then it's worth investigating why your permanent installation is not. If it doesn't connect, then clearly the brcm80211 driver is not going to work for you.

> **MZBKA said:**
> according to this [http://linuxwireless.org/en/users/Drivers/brcm80211#Firmware_installation](http://linuxwireless.org/en/users/Drivers/brcm80211#Firmware_installation)
the brcm80211 is untested on 64 bit linux.  Maybe that's my problem?

That's a very good point. I used the 32-bit version for the HP netbook I tried. It is possible that this driver may not work as well, or not work at all, with 64-bit, although I'd be surprised if that were the case. Unfortunately, I can't test this because the HP netbook has an Intel Atom processor and I wouldn't get very far with a 64-bit live USB on it.

However, that might be something you might like to try if you're running 64-bit and wireless still doesn’t work in the live session. Try downloading the 32-bit ISO and running that and see if it makes a difference. It would be useful information.

---

### Post by MrD_scifi on 2011-05-11
> **josephmills said:**
> 
```
lspci -vnn | grep 14e4 
```this is what this code will do  



So what does this all mean well the** b43fwcutter only**works for the model numbers [B]
14e4:4307
14e4:4311
14e4:4312 IMPORTANT if you have this card you need the firmwareb43-lpphy-installer for your firmware 
14e4:4318
14e4:4319
14e4:4320
14e4:5354
[/B]


If you have model number[B]
14e4:0576
14e4:4313
14e4:4315 
14e4:4328
14e4:4329
14e4:432a
14e4:432b
14e4:432c
14e4:432d       
14e4:4353
14e4:4357
14e4:4358
14e4:4359
14e4:435a
14e4:4727
14e4:a99d
[/B]
then you are going to need the **broadcom-sta-source + broadcom-sta-common** 

both the b43fwcutter and the b43sta use the firmware-b43-installer
unless noted 



My card comes up as **14e4:4311** and it's the other way round for Ubuntu 11.04.  B43 must be removed.  STA must be installed after flushing everything.  However, with Linux Mint 11RC your advice works for me.  Unless I'm getting confused.  I'm currently using Mint 11RC and I've checked package manager and I've got b43 installed and wifi working and I remember it was opposite for Ubuntu 11.04.

---

### Post by GuitarzanHV on 2011-05-11
MZBKA,

I sense that we have the same problem, as I have the 4313 card on a Dell Inspiron and can't get wireless on reboot. I use the 64-bit, so I can confirm that the open-source driver brcm80211 will work, if the ethernet cable is plugged in at boot. Doesn't fix the problem for me, though.

Could this be a NetworkManager issue? How would one check that? After all, NM won't pick up an ethernet cable on my machine unless I restart.

---

### Post by apocripha on 2011-05-12
Hello gentlemen,

I run a Zv6000, lucid lynx, with a bm 43xx card.
I upgraded to the fwcutter ages ago and all worked fine for nearly 2 years.

I accidentally put my computer into hibernation and now the wifi card won't power back on.
I had that exact same problem back in November, and I was able to find a solution, which boiled down to one command line. Sadly I did not write it down, and cannot find it again in the great ocean that is the internet.

Could a kind soul tell me how to turn on my wifi card?

Cheers.
EDIT: post n°47 in this thread might be onto something. I combined key fn with most of my F keys and somehow the card has turned back on.

---

### Post by MasterNetra on 2011-05-12
This is the fix to the 43xx problem for 11.04, install maverick's version of bcmwl-kernel-source as 11.04's version is apparently broke.

Driver:[http://packages.ubuntu.com/maverick/bcmwl-kernel-source](http://packages.ubuntu.com/maverick/bcmwl-kernel-source)

Also recommend locking it using synaptic to prevent accidental upgrade.

---

### Post by fox-mulder on 2011-05-13
hi

i am so close to smash my laptop into peaces because of this BS, after installing Ubuntu 11.04 nothing works by all the freaking guides out there. 

my laptop is a HP MINI 210 and i want to see the b43 right under STA name in additional drivers but no,,
why isnt there any logic in this issue, ??

everything worked in 10.10 what is the logic here? why so much hassle with the NEW Ubuntu? no logic..
did they change everything from 10.10 to 11.04??

lspci -vvnn | grep 14e4

02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

i did sudo aptitude purge firmware-b43-installer, okey so what next?
hmm sudo aptitude install b43-fwcutter... then I see a picture of a "configuring b43-cutter wtf? how did he get that window in terminal? wtf I am ripping my hair out as we speak im so tired of my self not managing this apperntly easy task,, !@#$% me..

please help me](*,)](*,)](*,)

and ofc,,,, the issue is that I want to use b43 driver but it isnt there.

---

### Post by marty331 on 2011-05-13
> **fox-mulder said:**
> hi

i am so close to smash my laptop into peaces because of this BS, after installing Ubuntu 11.04 nothing works by all the freaking guides out there. 

my laptop is a HP MINI 210 and i want to see the b43 right under STA name in additional drivers but no,,
why isnt there any logic in this issue, ??

everything worked in 10.10 what is the logic here? why so much hassle with the NEW Ubuntu? no logic..
did they change everything from 10.10 to 11.04??

lspci -vvnn | grep 14e4

02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

i did sudo aptitude purge firmware-b43-installer, okey so what next?
hmm sudo aptitude install b43-fwcutter... then I see a picture of a "configuring b43-cutter wtf? how did he get that window in terminal? wtf I am ripping my hair out as we speak im so tired of my self not managing this apperntly easy task,, !@#$% me..

please help me](*,)](*,)](*,)

and ofc,,,, the issue is that I want to use b43 driver but it isnt there.


Totally understand, but try this before you pull all your hair out!
This is what worked for me:
I followed MrD's suggestions and had to tweak it a little:
1) attach ethernet lead
2) in "additional drivers", turn off STA driver that was auto installed after vanilla 11.04 install
3) in synaptic package manager, remove bcmwl-kernel-source, every    b43/broadcom entry, finding them by using the "search" button on those    two terms and not the "quick filter"
4) restart computer
5) open terminal,"sudo apt-get install bcmwl-kernel-source"
6) restart computer and enjoy the wifi.
(at this point I did not have wifi going so then I continued on)
7)  in synaptic package manager I searched (again search, not quick  filter) for broadcom and installed the following: b43-fwcutter,  broadcom-sta-common, broadcom-sta-source.  Already installed was  bcmwl-kernal-source, so I left that alone.
:cool:   restart, yes again.  I was still connected to ethernet but I hovered  over my ethernet and opened the list of availalble networks and could  see my wfie, so I disconnected the ethernet and connected to wifi.

---

### Post by nm_geo on 2011-05-13
> **fox-mulder said:**
> hi

i am so close to smash my laptop into peaces because of this BS, after installing Ubuntu 11.04 nothing works by all the freaking guides out there. 

my laptop is a HP MINI 210 and i want to see the b43 right under STA name in additional drivers but no,,
why isnt there any logic in this issue, ??

everything worked in 10.10 what is the logic here? why so much hassle with the NEW Ubuntu? no logic..
did they change everything from 10.10 to 11.04??

lspci -vvnn | grep 14e4

02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

i did sudo aptitude purge firmware-b43-installer, okey so what next?
hmm sudo aptitude install b43-fwcutter... then I see a picture of a "configuring b43-cutter wtf? how did he get that window in terminal? wtf I am ripping my hair out as we speak im so tired of my self not managing this apperntly easy task,, !@#$% me..

please help me](*,)](*,)](*,)

and ofc,,,, the issue is that I want to use b43 driver but it isnt there.
Fox-
You see the LP-PHY in the description of your chipset?  That mean low power chip.. Recheck synaptic for the correct firmware.. I hope all you will need to do is remove the present firmware-b43-installer and get the low power firmware installed.  Run this as well to make sure your wifi switch is working.

In fact since your wifi is not working remove all bcm related drivers and firmware.  Reboot with ethernet cable attached.
Then I would reinstall the b43-fwcutter and the low power firmware module.
Then
```
rfkill list
```You might need to reboot to get wifi working.

If that does not get it going then move to the maverick version of the STA driver, but I would not do that before trying the B43 and proper firmware. (firmware-b43-lpphy-installer) read the description it is for your chip.

---

### Post by fox-mulder on 2011-05-14
my wifi is working, but not the b43 driver.
on my last ubuntu 10.10 install i used b43 with no problems at all.

thanks for the input though, i will try the steps you guys gave me thanks again.

---

### Post by nm_geo on 2011-05-14
> **fox-mulder said:**
> my wifi is working, but not the b43 driver.
on my last ubuntu 10.10 install i used b43 with no problems at all.

thanks for the input though, i will try the steps you guys gave me thanks again.
my laptop is a HP MINI 210 and i want to see the b43 right under STA name in additional drivers but no,, 

Okay, I think I understand you can not see the B43 diver listed in Additional Drivers correct?   Well I can't see it either but I can still use it on my laptop.  In fact I am using the b43 driver on Development testing Oneric, Natty, Xubuntu 11.04, and Lucid 10.04.  To make it a little more complicated I also have the STA driver working on the same laptop with the same chipset on Maverick.
 
If your wifi is working be Happy..:)

---

### Post by fox-mulder on 2011-05-14
yes true I can't see it additional drivers, I want to use it without screwing my kernel or whatever.
damn this issue is a REAL PAIN :(

---

### Post by NormanFLinux on 2011-05-15
The solution to the wireless freeze is to upgrade to the latest kernel 2.6.39.0.

It brings a lot of new features and Natty is no longer a crippled beast tethered to an Ethernet cable.

The 2.6.38.8 kernel Natty ships with was buggy and connecting to a wireless network would freeze up the desktop, necessitating a hard reset.

Sometimes a kernel upgrade is definitely needed. The difference is remarkable, particularly with Unity! ;-)


> **fox-mulder said:**
> yes true I can't see it additional drivers, I want to use it without screwing my kernel or whatever.
damn this issue is a REAL PAIN :(

---

### Post by thonuz on 2011-05-15
I upgraded to 2.6.39 RC 5 a few days ago and on BCM4321 I still get the following:

Wireless working great as with the older kernels then as usual,
system freeze after a some minutes, cannot log out or move mouse or anything. I can also see the kernel panic in logs.
Yes it always worked before and now affects all the new distros based on latest ubuntu (mint and so forth).

---

### Post by deepclutch on 2011-05-15
Dell Inspiron 1720 duo with broadcom 4312 . Wireless works fine with hidden ssd&wpa+wpa2 enabled in network-manager. Only gripe is, when screen saver gets activated, wireless gets disconnected. any workaround for this? :-|

---

### Post by NormanFLinux on 2011-05-15
The new kernel has not worked with all variants of Broadcom cards.

Its worked on my HP Mini 2133. The gripe is the wireless button still gets disabled on reboot but when I turn it on to connect to the network, there is no longer a kernel panic and a sudden freeze.

---

### Post by NormanFLinux on 2011-05-15
I upgraded to 2.6.39.0, which may account for the problems you are having. If it works, I leave well enough alone. I mean I didn't install candidate 5. Have seen no need to yet.

Upgrade instructions are here:


You will have to install a PPA to get the update to install the new kernel.

 sudo add-apt-repository ppa:kernel-ppa/ppa

 sudo apt-get update

 apt-cache showpkg linux-headers

 sudo apt-get install linux-headers-2.6.39-0 linux-headers-2.6.39-0-generic linux-image-2.6.39-0-generic --fix-missing

 Run the above commands in terminal and once the upgrade is finished, reboot.

---

### Post by thonuz on 2011-05-15
> **NormanFLinux said:**
> I upgraded to 2.6.39.0, which may account for the problems you are having. If it works, I leave well enough alone. I mean I didn't install candidate 5. Have seen no need to yet.

Upgrade instructions are here:


You will have to install a PPA to get the update to install the new kernel.

 sudo add-apt-repository ppa:kernel-ppa/ppa

 sudo apt-get update

 apt-cache showpkg linux-headers

 sudo apt-get install linux-headers-2.6.39-0 linux-headers-2.6.39-0-generic linux-image-2.6.39-0-generic --fix-missing

 Run the above commands in terminal and once the upgrade is finished, reboot.

Hey Thanks I am going to try this kernel and instructions to see what happens. I imagine eventually a new kernel will work. I suppose I should check the change files in these builds. It would be interesting to see what happened to **.38 and so on.

---

### Post by thonuz on 2011-05-15
New kernel with broadcom ata enabled freezes even faster (some 30 seconds or so). I am just going back to a 2.6.35 distro for now and will check bug reports.

---

### Post by ptolemy7 on 2011-05-15
Hey! I am having a similar problem with my wireless card.  
I am completely new to linux in any way, shape or form, and hardly have any idea what i am doing.
For some reason, i am not being able to connect wirelessly. When i was installing the OS from the CD, i was able to to connect wirelessly, but after rebooting and finally opening Ubuntu for the first time in my life, i can not connect without an ethernet cable. 
My computer is a Dell 1458, and I think the wireless card is a dell 1515 though i am not sure. I really dont know what to do. 
I hope someone can help me.

Thanks
Ptolemy

---

### Post by NormanFLinux on 2011-05-15
You probably have a Broadcom card. To enable wireless networking again, you will have to install a new kernel from the PPA. Follow the instructions below and you should be good to go:

You will have to install a PPA to get the update to install the new kernel.

 sudo add-apt-repository ppa:kernel-ppa/ppa

 sudo apt-get update

 apt-cache showpkg linux-headers

 sudo apt-get install linux-headers-2.6.39-0 linux-headers-2.6.39-0-generic linux-image-2.6.39-0-generic --fix-missing

 Run the above commands in terminal and once the upgrade is finished, reboot.

---

### Post by deepclutch on 2011-05-16
Wireless interface is detected as eth1 instead of wlan0 with 2.6.38 kernel. though it works fine.  any workaround?

---

### Post by NormanFLinux on 2011-05-16
Are you connected online when you don't have an Ethernet cable plugged in? Then I wouldn't worry about it.

> **deepclutch said:**
> Wireless interface is detected as eth1 instead of wlan0 with 2.6.38 kernel. though it works fine.  any workaround?

---

### Post by daoki82 on 2011-05-16
> **NormanFLinux said:**
> You probably have a Broadcom card. To enable wireless networking again, you will have to install a new kernel from the PPA. Follow the instructions below and you should be good to go:

You will have to install a PPA to get the update to install the new kernel.

 sudo add-apt-repository ppa:kernel-ppa/ppa

 sudo apt-get update

 apt-cache showpkg linux-headers

 sudo apt-get install linux-headers-2.6.39-0 linux-headers-2.6.39-0-generic linux-image-2.6.39-0-generic --fix-missing

 Run the above commands in terminal and once the upgrade is finished, reboot.

Hey Norman, I'm having the same problem with the wireless card.. I input the first line you had there, and it then asked for my password. But when I entered it, the next line was:
< url open error [ Errno -2 ] Name or service not know  >

From there, when I input the same first line, it simply gives the < url open error [ Errno -2 ] Name or service not know  > line again. Any idea what might be wrong?

Thanks

---

### Post by NormanFLinux on 2011-05-16
I take it you're on Ethernet?

[http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0]("http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0")

This is where I got the instructions. I had to repeat a few times to get it all downloaded for installation.

It shouldn't be returning an error unless you mistyped something. I don't really get it.

Its best to copy and paste the text in the terminal to prevent errors from happening.

---

### Post by deepclutch on 2011-05-16
> **NormanFLinux said:**
> Are you connected online when you don't have an Ethernet cable plugged in? Then I wouldn't worry about it.
yes I can connect without ethernet enabled. b44 module is needed for onboard ethernet which is detected as eth0 . I've not tried both wireless and wired simultaneously.

---

### Post by NormanFLinux on 2011-05-16
If you want to update, plug in Eternet for best results.

---

### Post by HarryG321 on 2011-05-16
Dell Inspiron 1501
4311 chipset
11.04

Can't get it to work at all. Ethernet works fine, able to update with it, but wireless won't work at all.
Fn+F2 is meant to enable the wireless card, but nothing happens. 

ifconfig returns eth0 and lo, but no wlan interface.

Tried b43-fwcutter, wicd, upgrading to 2.6.39-0-generic.
Nothing working yet :/

---

### Post by irv on 2011-05-16
> **HarryG321 said:**
> Dell Inspiron 1501
4311 chipset
11.04

Can't get it to work at all. Ethernet works fine, able to update with it, but wireless won't work at all.
Fn+F2 is meant to enable the wireless card, but nothing happens. 

ifconfig returns eth0 and lo, but no wlan interface.

Tried b43-fwcutter, wicd, upgrading to 2.6.39-0-generic.
Nothing working yet :/
I have the same card in my Inspiron 1521 and this worked for me;
[http://ubuntuforums.org/showthread.php?t=1742147&page=4]("http://ubuntuforums.org/showthread.php?t=1742147&page=4")

---

### Post by HarryG321 on 2011-05-16
> **irv said:**
> I have the same card in my Inspiron 1521 and this worked for me;
[http://ubuntuforums.org/showthread.php?t=1742147&page=4](http://ubuntuforums.org/showthread.php?t=1742147&page=4)

Thank you so much! Worked like a charm :D


In summary;

[LIST]
[*]Disable Broadcom STA Driver.
[/LIST]

[LIST]
[*]Follow the steps in this post:
[/LIST]
[INDENT][INDENT][http://ubuntuforums.org/showpost.php?p=10758325&postcount=25](http://ubuntuforums.org/showpost.php?p=10758325&postcount=25)
[/INDENT][/INDENT]

---

### Post by NormanFLinux on 2011-05-16
You have to install the firmware package in addition to B43-fwcutter for wireless to work.

Or revert to bcmwl-source kernel. Ubuntu 11.04 requires either the B43 and firmware or bcmwl-source kernel for the wireless card to connect to the router.

---

### Post by edwin.donaldson on 2011-05-16
> **Sef said:**
> Problem in Natty Narwhal - 11.04 with the Broadband 43xx Wireless Card: Unable to download firmware for wireless. (Also works for 10.10 and 10.04)

From the 'Additional Drivers' section:

  

Error Message:

**Solution 1**: System > Administration > Synaptic Package Manager > Search: firmware-b43-lpphy-installer > Click Mark > Click install > Close



I have no access to the internet so installing firmware-b43 isn't possible via internet, copied .deb file to USB, but don't know how to install it.

---

### Post by NormanFLinux on 2011-05-17
Copy the deb. package to your Ubuntu desktop and run the Gdebi installer.

---

### Post by Aarontex40k on 2011-05-18
> **josephmills said:**
> hi there guys and girls:D I would just like to clear up a couple of things. If you think that you need the b43 or the b43sta, these are two different mods/drivers the first thing that you want to do is type in  
```
lspci -vnn | grep 14e4 
```this is what this code will do  
**ls** stands for list 
**pci** stands for pci cards in the computer 
**-vnn ** stands for find the model number 
**grep** grep is a filter so it filters out the 14e4 thats why it is in a different color 
**14e4** is what grep (the filter)is looking for 
so ls-->+<--pci=list pci cards 
lspci -vnn= list pci cards with model number 
lspci -vnn | = listpci cards with model number and stop 
lspci -vnn | grep = list all pci cards with a model number and filter with grep 
lspci -vnn | grep 14e4 = list all pci cards with model number and a filter with grep using 14e4 for the filter.


So what does this all mean well the** b43fwcutter only**works for the model numbers [B]
14e4:4307
14e4:4311
14e4:4312 IMPORTANT if you have this card you need the firmwareb43-lpphy-installer for your firmware 
14e4:4318
14e4:4319
14e4:4320
14e4:5354
[/B]


If you have model number[B]
14e4:0576
14e4:4313
14e4:4315 
14e4:4328
14e4:4329
14e4:432a
14e4:432b
14e4:432c
14e4:432d       
14e4:4353
14e4:4357
14e4:4358
14e4:4359
14e4:435a
14e4:4727
14e4:a99d
[/B]
then you are going to need the **broadcom-sta-source + broadcom-sta-common** 

both the b43fwcutter and the b43sta use the firmware-b43-installer
unless noted 

If you have the model number 
[B]
14e4:4301
14e4:4306
14e4:4320 
14e4:4324
[/B]
Then you are going to need the **b43-fwcutter with the firmware-b43legacy-installer **

**IMPORTANT** all of these card also need the bcmwl-kerrnel-source

Ok now that we have found our card and its model number and we know what mod/driver and firmware we need. Its time to install all of it. 
**Important** for these next steps you will need a internet connection using a cat5 cable(ethernet) or whatever as long as you are on line. If are dealing only with wireless see section installing b43fwcutter with out internet connection. 

First before installing we need to remove anything that is there right now so open up synaptic package manager and type in bcm into the search bar then click on the green box's and mark for removal then press the apply button now reboot the computer 
after rebooting start to install the things that you need by opening up synaptic package manger and type in bcm follow the chart above to install the correct mods/driver and firmware then reboot again is your wireless working. 


If not lets do some diagnostics please open your terminal and type in 
```
rfkill list 
``` where **rf**stands for Radio frequency kill stands for umm... and list is to list all the Radio frequency
if there is a soft block or a hard block please do a ```
rfkill unblock all 
``` if that wont work try ```
rfkill unblock wifi or rfkill unblock wlan
```Now that we know that nothing is blocked lets look at your mods/drivers 
 ```
lsmod | grep b43
``` this will **ls=list-->+<--mod=mods/driver** so ls+mod=list all mods | means stop and grep is the filter and b43 is what grep is looking for 
do you see you mods listed it would be nice if some of the people with working wireless could post there lsmod + there model number of there card 

If lsmod looks good lets move on to the firmware 
```
dmesg | grep b43 
``` so dmesg looks up what the linux kernel sees and grep is the filter **IMPORTANT if you are useing the b43sta then you need top type in wl instead of b43 **

Are you geting any errors go re-install the firmware again this is the part that seems to be "the bug in the gar" 

**Installing b43fwcutter with out the internet connection** 

Ok so you have no internet connection on your Ubuntu box for what ever reason. but you need it. Well here is how to get it. These are the things that you are going to need.  

1) a blank cd/dvd or a penn drive or external hard drive or some way to transfer files (phone?) whatever. 

2) you are going to need another computer of some sorts to download your mods/firmware 


Ok, now that you have thous two things lets move on.

download this file  [http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)

Then transfer it over to your Ubuntu box 

Now in  your Ubuntu Box [computer]  please make your way to your **Home folder ** 

Once you are at your home folder right click on your home folder and ** make a new folder and call it wireless**

Now that you have made a new folder called wireless in your home directory. It is time to **move the downloaded file into the new folder called wireless** 

Next we need to move that folder to the firmware directory to do this open your terminal and type in 
```
sudo cp -r ~/wireless/* /lib/firmware/
```Now lets double check to make sure the download made it to the firmware directory. Too do this type this into the terminal 
```
ls /lib/firmware
```Do you see it there ? Good if not it did not moved. Go back to the last step and try again. But if you do see it lets move on to the next step

Ok so now that the download is in the firmware dir we are going to have to go there. To go there open your terminal and type in. 
```
cd /lib/firmware 
```Now that you have moved lets double check to make sure this next code tells us where we are in the computer file dir. This next code stands for "print working directory" ```
pwd
``` are you at /lib/firmware if so good if not go back one step 

Now that we are in the firmware directory. We have to extract the download to do this type in 
```
sudo -s
``` then enter your password then 
```
tar -xzf b43-all-fw.tar_.gz
```then 
```
exit
```Now it is time to reboot 
```
sudo reboot 
```Do you have wireless now ? If not you did some thing wrong. 
If you have some troubles please post here and some one will help you out 


Well I hope that this clears some stuff up about the b43fwcutter and the b43sta and also the b43-legacy have fun with your wire less! Please don't forget if you have one of these cards and they are working please post your lsmod and dmesg with model number of the card thanks again also I would like to say that I am working on a how to install with out the internet for the b43sta but do not have the hardware for it yet I am working on it. give me a couple of days thanks again and happy wireless :D
Joseph
Synaptic wont let me remove "bcmwl-kernel-source". what should I do?

---

### Post by irv on 2011-05-18
> **Aarontex40k said:**
> Synaptic wont let me remove "bcmwl-kernel-source". what should I do?

Try this in a terminal:
```
sudo apt-get purge bcmwl-kernel-source
```
I think thats the command.

---

### Post by estomagordo on 2011-05-20
Hi everyone!

My first venture ever into Linux territory isn't going as planned :)
During the install of Ubuntu 11.04 my wireless was working correctly, but upon it's finish, I find myself having this problem, that seems to be shared by many.

I have tried to follow every guide I've come across, getting more apt at Linux navigation all the time, but still nothing seems to work!

It seems my Broadcom card is a model 4313:

> 44:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

When I try to install the driver, or rather activate it, I get the error message pointing to a file called jockey.log - so this isn't working.

Now, I have tried to install various drivers manually through the ubuntu software central. When I search "broadcom" I find five items: broadcom-sta-common, broadcom-sta-source, bcmwl-kernel-source, bcm5700-source and b43-fwcutter. Four out of these five, all but the bcm5700-source, have a green check mark next to them. So I guess I have those four drivers installed? Do I need to install some of them?

Or is there some other course of action I can take?

I have already tried the solution via synaptic package control mentioned in the OP. I get an error message (and this is my translation, as I run a localized version of Ubuntu)

"An error has ocurred
E: firmware-b43-lpphy-installer: subprocess installed post-installation-script gave error code 1."

---

### Post by coffeecat on 2011-05-20
> **estomagordo said:**
> It seems my Broadcom card is a model 4313:

@estomagordo, that card works perfectly with the default open source brcm80211 driver in Natty - or at least it does for me in a 32-bit system. There would be no need to install any of the other drivers. You said it was working perfectly at first. My guess is that you succumbed to Jockey pestering you to install the proprietary driver. My advice: ignore Jockey!

Please would you clarify one point. Two other members reported difficulty with the BCM4313 card, but there was a possibility they were running 64-bit systems. However, they never confirmed this even when asked. It would be useful to know if 64-bit makes a difference. Which version did you install: 64 or 32-bit.

If you are running a 32-bit system, or even a 64-bit, try uninstalling all the drivers and packages you installed related to Broadcom. Also check /etc/modprobe.d/blacklist.conf to make sure one of the proprietary drivers hasn't blacklisted brcm80211 for you. If you need help with that, post back.

---

### Post by irv on 2011-05-20
> **estomagordo said:**
> Hi everyone!

My first venture ever into Linux territory isn't going as planned :)
During the install of Ubuntu 11.04 my wireless was working correctly, but upon it's finish, I find myself having this problem, that seems to be shared by many.

I have tried to follow every guide I've come across, getting more apt at Linux navigation all the time, but still nothing seems to work!

It seems my Broadcom card is a model 4313:



When I try to install the driver, or rather activate it, I get the error message pointing to a file called jockey.log - so this isn't working.

Now, I have tried to install various drivers manually through the ubuntu software central. When I search "broadcom" I find five items: broadcom-sta-common, broadcom-sta-source, bcmwl-kernel-source, bcm5700-source and b43-fwcutter. Four out of these five, all but the bcm5700-source, have a green check mark next to them. So I guess I have those four drivers installed? Do I need to install some of them?

Or is there some other course of action I can take?

I have already tried the solution via synaptic package control mentioned in the OP. I get an error message (and this is my translation, as I run a localized version of Ubuntu)

"An error has ocurred
E: firmware-b43-lpphy-installer: subprocess installed post-installation-script gave error code 1."

Try this in a terminal:
First get rid of the bcmwl-kernel-source

```
sudo apt-get purge bcmwl-kernel-source
```



A fix for the Broadcom BCM43xx driver in 11.04.

1. I uninstalled “bcm-kernel-source” package,

```
sudo apt-get remove bcm-kernel-source
```


2. I installed “firmware-b43-installer” package

```
sudo apt-get install firmware-b43-installer
```

3. I installed “b43-fwcutter” packager

```
sudo apt-get install b43-fwcutter
```

4. I typed into the terminal:


```
 cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl| lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3 |rt6|rt7|witch|wl'
```

You can just copy and paste all these commands into a terminal, and afterwards if it doesn't work, try rebooting. But mine just worked after doing this.

---

### Post by estomagordo on 2011-05-20
coffeecat:

The wireless has never worked inside Ubuntu, just during the installation process. So something's definitely wrong. Also, this is most embarassing, but I'm not sure whether I have 32 bit or 64 bit. Realistically, I should have downloaded the 64 bit version when I decided to give Ubuntu a shot, but from what I've found online, it seems I actually am running 32 bit.

Is there a surefire way of knowing?

I will try a mass uninstall now, like you suggested. But regarding the blacklist.conf I can't figure out how to open it.

Like I said, very very new at this.

Thanks for your quick reply!

---

### Post by estomagordo on 2011-05-20
irv:

Thanks! I entered those exact commands, but nothing happened. Not even after a reboot. I was just supposed to enter the commands, not to also go into drivers and activate the driver, right?

Also, that first command, the uninstall one, gave me some sort of error message.

---

### Post by estomagordo on 2011-05-20
I tried to uninstall the kernel source again, and got the same (I think, and assume) message:

> Error! There are no instances of module bcmwl
[address]+bdcom located in the DKMS tree.
dpkg: [my translation from now on] error when handling bcmwl-kernel-source (-remove):
sub process installed pre-removal-script gave error code 3
dpkg: dkms: dependency problem, but removes nd according to nskeml:
bcmwl-kernel-source r dependent on dkms.
Removing dkms...
Handling utlsare fr man-db...
Error upon handling:
bcmwl-kernel-source

The process goes to 100% at first, and then this happens after it says "Removing all DKMS Modules"

---

### Post by coffeecat on 2011-05-20
> **estomagordo said:**
> coffeecat:

The wireless has never worked inside Ubuntu, just during the installation process.

I don't understand that. If you mean it worked when you ran the live CD, then it should work once you've installed it. My guess is that sometime between running the live CD and booting up your permanent installation the latter has been contaminated with stuff that Jockey wanted to install.

> **estomagordo said:**
> it seems I actually am running 32 bit.

Is there a surefire way of knowing?

Open a terminal. Run:

```
uname -p
```If you get "x86_64" you are running 64-bit. If "i686" you are running 32-bit.

> **estomagordo said:**
> I will try a mass uninstall now, like you suggested. But regarding the blacklist.conf I can't figure out how to open it.

Like I said, very very new at this.

Since you're new, it's going to be difficult to get rid of whatever is interfering with the brcm80211 driver. Try this. Boot up the live CD and choose "try Ubuntu". See if you can connect wirelessly without installing anything. If yes, then consider a re-install, only this time do not let the installer install any updates and, above all, if you get a prompt telling you that additional drivers are available, tell it to "GO AWAY!" :wink: Once you've installed, see if wireless is working. If it is and something pops up telling you additional drivers are available, tell it to "GO AWAY!". :) Above all, don't be tempted to install anything Broadcom related.

To others trying to help, be aware. **The new open source  brcm80211 driver that comes in Natty works just fine with the  BCM4313 card that estomagordo has. There should be no need for any of the other drivers.**

---

### Post by estomagordo on 2011-05-20
I tried re-installing and now everything works like a charm! I just unticked (or never ticked, can't remember) the boxes for check for updates and install third party updates.

Now, hopefully I can avoid intalling the wrong drivers by mistake in the future...

Thank you so much!

---

### Post by P235 on 2011-05-20
I would have saved myself plenty of frustration if I skipped to the end of this thread to read the solution to this problem:  re-install.  I will do just that, work out, and pretend that this was all a bad dream.  But, since this is a problem that goes back to 10.10, shame on the people responsible for resolving this.  There's a whole cluster of solutions that no longer work, and waves of people like me jumping on to the 11.04 bandwagon.  Waste, waste, waste.

---

### Post by coffeecat on 2011-05-20
> **P235 said:**
> I would have saved myself plenty of frustration if I skipped to the end of this thread to read the solution to this problem:  re-install.

Re-installing was only a solution for estomagordo's specific situation where they had one of the few Broadcom cards that works with the new open source brcm80211 driver and where the proprietary driver was interfering with this. I wouldn't want to give the impression to people with other Broadcom wireless chipsets that a simple re-install is all that is necessary, or is necessary at all. What wireless device do you have?

---

### Post by theiron on 2011-05-20
In my case, I couldn't get the wireless working in "Natty Narwhal" from a bare install.  My solution was to downgrade to 10.10, get the wireless working with the fwcutter installation (as noted in the DMESG output), and then did a wired upgrade to 11.04.  Wireless worked straightaway after the upgrade, so no worries!

I have attempted the upgrade thru wireless, and the install gets hung up in places, requiring the system to be restarting the hard way, by cutting power and facing the FSCK, which will ensue.

So, that's my experience and I'm stickin' to it.

---

### Post by _murphy_ on 2011-05-21
I have Lenovo Ideapad s10-3s with Broadcom BCM4313 wifi controller. I followed every single thread on 11.04 wifi problems and none worked for me.

rfkill list reports

ideapad_wlan: Wireless LAN
Soft Blocked: no
Hard Blocked: no

brcmwl-0: Wireless LAN
Soft Blocked: no
Hard Blocked: yes

The only way I did not try (and I wont) to unblock the driver is to install windows. 

hardware switch is on, Fn+F5 for soft blocking works, rfkill unblock all is good just for soft blocking. There are none of acer_wmi nor dell modules loaded. Just STA drivers. But wireless is still not working. 

Please [-o<

---

### Post by LU.Scot on 2011-05-22
Recently I installed Ubuntu. But I can't use internet. that doesn't find my Wireless LAN Card Connection, though Windows in my Comp does work well with no connection problem. What I should do? I have installed ndiswrapper on ubuntu and tried to do the same with live Youtube vedio. Everything was complete well except for My computuer couldn't unzip '.exe file' (I don't know why), though the person who listed up the video did the same and had his job done well. I can not connect to internet with Ubuntu as you know. I should read words and get what to do and reboot to linux again. It takes a long. I am Linux Biggnner, so It's difficult to understand what people talk to me. please take it easy to explain. 
 
when I typed lspci on terminal, it says 'broadcom device 4727'
when I see the detail about the WLAN CARD on WINDOW, It says Broadcom 802.11n NetWork Adapter.
 
I got known some of ubuntu orders such as 'mkdir, mv, cd'. as you see, I don't know 
Linux almost at all. I know I should study linux on my own. But to do so, I need 
internet connection. I can hardly find myself studying Ubuntu with no internet 
connection though. Please, Help me.

---

### Post by Ameet on 2011-05-22
I've tried several fixes posted here and can't seem to get it right.  I am an intelligent noob when it comes to networking so I'll do my best to describe the problem.

Installed 11.04 last week.  PC is a  Dell Inspiron 1525, with a Broadcom BCM4312 card.

```
~$ **lspci | grep 802.11**
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
```I believe I have installed ndiswrapper, and blacklisted the Ubuntu drivers:

```
~$ **tail /etc/modprobe.d/blacklist.conf **
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

# added 2011.05.22 aar 
# based on https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
~$ **ndiswrapper -l**
bcmwl6 : driver installed
    device (14E4:4315) present (alternate driver: ssb)

```I copied the driver by downloading this file: [http://ftp.us.dell.com/network/Dell_multi-device_A17_R174292.exe](http://ftp.us.dell.com/network/Dell_multi-device_A17_R174292.exe), uncompressing it into a ~/drivers directory, and by then running:

```
~$ **sudo ndisgtk**
```... and pointing it to ~/drivers/DRIVER_US/bcmwl6.inf

Wireless still doesn't work.  I get wired internet fine.  What am I missing here???

---

### Post by Joren on 2011-05-22
Hi All,

Upon freshly installed 11.04 the wireless did not work for my HP laptop, but thanks to the last couple of pages of this thread I finally got it to work.

laptop type:     HP-dv6318ea
wireless device: BCM4311 rev01

I installed the updates recommended by the update manager. Then I installed the Broadcom STA driver that was recommended in the System --> Administration --> Additional Drivers. That did not work and I started searching for a solution (using wired internet :)).

Firstly I found out that my wireless device was not claimed by any driver somehow since this was the output of ```
lshw -C Network
```
```
  *-network UNCLAIMED    
       description: Network controller
       product: BCM4311 802.11b/g WLAN  
       ...

```
So I wanted to assign a driver to it. I thought that perhaps the driver was blacklsited. The blacklisted drivers in /etc/modprobe.d/blacklist.conf did not state the sta driver anywhere. Also, many forums report about problems with STA. So I decided to try the installation of the b43 driver.

In Synaptics Package Manager I deinstalled the STA drivers and installed the following b43 drivers:
```

b43-fwcutter
firmware-b43-installer

```

After a restart this took care of the UNCLAIMEDness of the wireless device.
```

  *-network               
       description: Network controller

```
I unplugged the wire to test the network, but it still did not work. So just as in:[HTML]http://ubuntuforums.org/showpost.php?p=10758325&postcount=25[/HTML] I looked for blacklisted drivers in any file in the modprobe folder by typing. 
```

cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl| lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3 |rt6|rt7|witch|wl'

```

I found that there was an additional file created by the Broadcom installation, called ```

broadcom-sta-common.conf

``` and in here the b43 driver was blacklisted:
```
cat /etc/modprobe.d/broadcom-sta-common.conf 

# wl module from Broadcom conflicts with ssb
# We must blacklist the following modules:
 blacklist b44
 blacklist b43legacy
 blacklist b43
 blacklist ssb
 install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS

```

This made my wireless not to work, so I disabled everything in this file by changing it to:
```
cat /etc/modprobe.d/broadcom-sta-common.conf 
# wl module from Broadcom conflicts with ssb
# We must blacklist the following modules:
# blacklist b44
# blacklist b43legacy
# blacklist b43
# blacklist ssb
# install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS

```

Just to be certain I re-installed network manager and I think I also installed, just to be sure to have everything.
```

network-manager-pptp
network-manager-pptp-gnome

```

After again I restarted my laptop, the wireless configuration works! Finally my *lshw -C Network* looks like this:

 ```
 *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:d8000000-d8003fff

```

For the people who have it not working yet: Keep on trying, eventually you will succeed. :D It took me almost one entire day before I found a proper solution for the 11.04 (and I too wasted a lot of time on 10.04 solutions). I did not use Ndiswrapper for this wireless device, since the driver that was given by HP.com was not able to be unzipped to get the .sys and .inf files.

---

### Post by nm_geo on 2011-05-22
Good info Joren..   +1 to most of it also..

Ameet will have two issues that I see in blacklist.conf 

blacklist B43
blacklist ssb

Placing # in front will solve that.

Then  

Network controller: Broadcom Corporation BCM4312 802.11b/g [COLOR=Red]**LP-PHY **[/COLOR](rev 01)
LP-PHY is low power chip and needs 

firmware-b43-lpphy-installer

If Ameet decides to  try the b43 driver.

Try this link 
[http://ubuntuforums.org/showthread.php?t=1700897](http://ubuntuforums.org/showthread.php?t=1700897)
messages 5 & 6 should help

---

### Post by Ameet on 2011-05-22
Hey, NM_Geo,

I am trying all of these things and not getting any wifi access at all.

Again, I just did a fresh install of 11.04.  My PC is a Dell Inspiron 1525, with Broadcom 4312 card, LP-PHY [14e4:4315] (rev 01).

From Synaptic, I UN-installed:[INDENT][COLOR=Red]firmware-b43-installer
bcmwl-kernel-source[/COLOR]
[/INDENT]... and installed:[INDENT][COLOR=Blue]firmware-b43-lpphy-installer
b43-fwcutter[/COLOR]
[/INDENT]I commented out all blacklist entries for b43 and ssb in blacklist.conf, so it now looks like this:
```
$ **tail blacklist.conf**
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

# added 2011.05.22 aar 
# based on https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper
blacklist bcm43xx
#blacklist b43
blacklist b43legacy
#blacklist ssb

```However, I still get this response:

```
$ **sudo lshw -C Network**
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:e0:06:00
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.1.27 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:fe8fc000-fe8fffff ioport:de00(size=256)
  *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fe7fc000-fe7fffff

```So there is no driver attempting to control the wireless card at this time.  I feel like I'm missing a step.  And please realize, I am just a smart monkey typing stuff in - I don't have any deep knowledge of these networking commands and driver issues.  Please feel free to walk me through what may seem to be "obvious" to others. :-(.

Thanks

---

### Post by P235 on 2011-05-22
I apologize for my earlier outburst.  My card is the following:

04:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

Any suggestions are welcome.

---

### Post by josephmills on 2011-05-22
> **P235 said:**
> I apologize for my earlier outburst.  My card is the following:

04:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

Any suggestions are welcome.

hi there could we see a ```
lspci -vnn | grep 14e4
``` thanks

---

### Post by P235 on 2011-05-23
04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

---

### Post by josephmills on 2011-05-23
please see post number 44 you need the b43sta thanks post back if you get hung up thanks joseph [http://ubuntuforums.org/showthread.php?t=1748245&page=5](http://ubuntuforums.org/showthread.php?t=1748245&page=5)

---

### Post by P235 on 2011-05-23
Hi joseph, I followed part of the instructions from your post.  I uninstalled everything I found under bcm.  But, when I restarted I could connect to my wireless.  I didn't need to install broadcom-sta-common or broadcom-sta-source.  If there's no need to install these things then I will go on like this.  

Thanks!

---

### Post by josephmills on 2011-05-23
> **P235 said:**
> Hi joseph, I followed part of the instructions from your post.  I uninstalled everything I found under bcm.  But, when I restarted I could connect to my wireless.  I didn't need to install broadcom-sta-common or broadcom-sta-source.  If there's no need to install these things then I will go on like this.  

Thanks!

after you un-install everything then reinstall the things that are needed for you card (broadcom-sta-common or broadcom-sta-source firmware-b43-installer and the bcmwl-kernel-source) and you should be up and running

---

### Post by P235 on 2011-05-23
Right, I uninstalled everything and I'm up and runnning without broadcom-sta-common or source.  I wanted to check if it's okay to go on without any of it.

---

### Post by josephmills on 2011-05-23
> **P235 said:**
> Right, I uninstalled everything and I'm up and runnning without broadcom-sta-common or source.  I wanted to check if it's okay to go on without any of it.

so you have wireless then?

---

### Post by P235 on 2011-05-23
Yup.  I'm very thankful for the help.

---

### Post by coffeecat on 2011-05-23
> **P235 said:**
>   My card is the following:

04:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

> **P235 said:**
> Right, I uninstalled everything and I'm up and runnning without broadcom-sta-common or source.  I wanted to check if it's okay to go on without any of it.

You have one of the cards that works with the default (in the box) open source brcm80211 driver. If your card is working without installing the STA driver, then don't install anything, and good luck! :)

I don't think I can emphasise this enough, and as I said before:  **The new open source  brcm80211 driver that comes in Natty works just  fine with the  BCM4313 card. There is no  need for any of the other drivers.**

There are many knowledgeable and experienced Broadcom users in this thread, but experienced with the b43 and STA drivers. Perhaps they are not aware that there is a new open source driver. From what I can find by googling, it supports only a handful of Broadcom chipsets so far, including 4313, 43224 and 43225.

---

### Post by DAB4970 on 2011-05-23
Hello.  I just installed Natty on my HP Pavilion dv6835nr (laptop) in place of Lucid and I can't get either connection to work.

eth0 - realtek 8101E/8102E
eth1 - BCM 4312

Could someone please lead the way to getting eth0 working and then I can download the STA driver for BCM 4312.

Thanks.

addition:  I downloaded RTL8101E from realtek's site and the STA from Broadcom's site using my desktop.  The files have been uncompressed.  Not sure what to do at this point.

update:  I was able to get additional drivers installed during the reinstall process.  Don't understand how it was able to get a connection when the network manager said eth0 was disconnected.

---

### Post by erezson on 2011-05-23
Hey, I tried few manuals to fix the wireless.

I have Lenovo s12. At the beginning I couldn't enable the wireless at all, so I played with the driver and now I can enable but Ubuntu doesn't look for available connections at all.

Please, help me!:(

---

### Post by monasubramaniama on 2011-05-25
> **Sef said:**
> Problem in Natty Narwhal - 11.04 with the Broadband 43xx Wireless Card: Unable to download firmware for wireless. (Also works for 10.10 and 10.04)

From the 'Additional Drivers' section:

  

Error Message:

**Solution 1**: System > Administration > Synaptic Package Manager > Search: firmware-b43-lpphy-installer > Click Mark > Click install > Close

Kontza found the [solution]("https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/651010") (post #3), so thank him for it.

This solution fixed this problem on my Dell Inspiron 1545 with a Broadcom 4312 card. (Card Tech Specs: 0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01))

**Solution 2: **Another option is [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers").

Update: The Live USB of Natty Narwhal (11.04) automatically detected that I needed the STA driver.  After installing it and rebooting, the wireless worked. (No cable was needed for this.)

Update 2: After installing with the alternate cd, I needed a cable and after updating, I was able to download the STA driver through the 'Additional Drivers' section.
Finally my first post for the ubuntu community.
 

 To install the restricted drivers(broadcom wireless drivers) in the ubuntu 11.04 Natty Narwhal without  a wired Internet connection.
 

 
[LIST=1]
[*]Insert the Ubuntu 11.04 (Desktop) 	live CD into the CD-ROM drive.
[*]First goto the folder 	“pool\main\d\dkms” in the CD-ROM and double click on the 	“dkms_2.1.1.2-5ubuntu1_all.deb”. It will take you to the 	synapatic packet manager, click on install button here.
[*]Next goto the 	“pool\main\b\b43-fwcutter” in the CD-ROM  and double click on 	“b43-fwcutter_013-3_i386.deb”. It will take you to the synapatic 	packet manager, click on install button here.
[*]Next goto the folder 	“pool\restricted\b\bcmwl” in the CD-ROM  and double click on the 	“bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu3_i386.deb”. It 	will take you to the synapatic packet manager, click on install 	button here.
[*]Once this is done, restart the 	system and the wireless will work just fine ( click on the wireless 	tab on the top  right hand side of the screen and select the network 	to connect to.  If it is a secured connection then enter keyring 	token when prompted.)  	
[*]Using this method other restricted 	drivers present in the CD-ROM can be installed provided the 	dependencies are taken care of (the dependencies programs are 	present in “pool\main” folder)
[/LIST]

---

### Post by Ameet on 2011-05-25
I solved my problem (see below).  I am still using NDISwrapper, but instead of the latest bcmwl driver (v. 6), I switched to using the one I had under Ubuntu 10.04 (bcmwl5.inf).  Pulled out the ethernet cable, and *presto* wireless was on.

:popcorn:

> **Ameet said:**
> Hey, NM_Geo,

I am trying all of these things and not getting any wifi access at all.

Again, I just did a fresh install of 11.04.  My PC is a Dell Inspiron 1525, with Broadcom 4312 card, LP-PHY [14e4:4315] (rev 01).

From Synaptic, I UN-installed:[INDENT][COLOR=Red]firmware-b43-installer
bcmwl-kernel-source[/COLOR]
[/INDENT]... and installed:[INDENT][COLOR=Blue]firmware-b43-lpphy-installer
b43-fwcutter[/COLOR]
[/INDENT]I commented out all blacklist entries for b43 and ssb in blacklist.conf, so it now looks like this:
```
$ **tail blacklist.conf**
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

# added 2011.05.22 aar 
# based on https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper
blacklist bcm43xx
#blacklist b43
blacklist b43legacy
#blacklist ssb

```However, I still get this response:

```
$ **sudo lshw -C Network**
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:e0:06:00
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.1.27 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:fe8fc000-fe8fffff ioport:de00(size=256)
  *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fe7fc000-fe7fffff

```So there is no driver attempting to control the wireless card at this time.  I feel like I'm missing a step.  And please realize, I am just a smart monkey typing stuff in - I don't have any deep knowledge of these networking commands and driver issues.  Please feel free to walk me through what may seem to be "obvious" to others. :-(.

Thanks

---

### Post by nm_geo on 2011-05-25
Excellent Ameet.. There are typically more ways than one to skin a cat.. Did you read that coffeecat?:)

---

### Post by coffeecat on 2011-05-25
> **nm_geo said:**
> Did you read that coffeecat?:)

Indeed! :) But Ameet is using the BCM 4312 card, whereas I was banging on about the 4313, which is quite a different thing. :wink: Apart from being supported by the new open source driver, it's N capable.

---

### Post by nm_geo on 2011-05-25
> **coffeecat said:**
> Indeed! :) But Ameet is using the BCM 4312 card, whereas I was banging on about the 4313, which is quite a different thing. :wink: Apart from being supported by the new open source driver, it's N capable.

I was not referring to the discussion... I was teasing you about being a cat.. In fact i thought your info was great about the new driver..

---

### Post by lbaquerizo on 2011-05-26
> **Sef said:**
> Problem in Natty Narwhal - 11.04 with the Broadband 43xx Wireless Card: Unable to download firmware for wireless. (Also works for 10.10 and 10.04)

From the 'Additional Drivers' section:

  

Error Message:

**Solution 1**: System > Administration > Synaptic Package Manager > Search: firmware-b43-lpphy-installer > Click Mark > Click install > Close

Kontza found the [solution]("https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/651010") (post #3), so thank him for it.

This solution fixed this problem on my Dell Inspiron 1545 with a Broadcom 4312 card. (Card Tech Specs: 0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01))

**Solution 2: **Another option is [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers").

Update: The Live USB of Natty Narwhal (11.04) automatically detected that I needed the STA driver.  After installing it and rebooting, the wireless worked. (No cable was needed for this.)

Update 2: After installing with the alternate cd, I needed a cable and after updating, I was able to download the STA driver through the 'Additional Drivers' section.


i need help i have the intel

Network controller        : Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection 

so is the same problem but with different controlers i am stuck with mint 9 that works fine but i want to upgrade please help

---

### Post by irv on 2011-05-27
This tread is getting long and confusing. I think what we need here is a few howtos for each card. Because I am seeing that the fix is different for each one. we need a Howto for Broadcom 4311, 4312, 4313 etc, and the PRO/Wireless 4965, and any others out there. Or maybe the developers could just make them work right out of the box.

Going back to some older versions of Ubuntu, my wireless just plain worked. The question is what got broken in the code?

It has gotten to the point that many people who install Ubuntu need to jump through hoops to get their wireless working. This is turning people off on using Ubuntu.

Thanks for hearing me out this morning. Maybe I am just getting old and grumpy.

---

### Post by fox-mulder on 2011-05-30
yes, a separate howto for each driver would been great, im close to uninstall 11.04 and go back to 10.10 :*(

hopefully someone can stop me and help me with 4312 / b43 issue.

---

### Post by marty331 on 2011-05-30
> **fox-mulder said:**
> yes, a separate howto for each driver would been great, im close to uninstall 11.04 and go back to 10.10 :*(

hopefully someone can stop me and help me with 4312 / b43 issue.


I just reinstalled (due to a completely different issue) and I followed my own instructions.  I believe they are on page 25 or 24 of this post.  I have the 4312 as well and  my instructions worked.  No need to go back to 10.10, 11.04 is AWESOME!

---

### Post by _murphy_ on 2011-05-30
not that true for 4313 . . .

---

### Post by sarath kolli on 2011-06-02
please guide me regarding how to install essential linux-headers-generic and dep linux

in ubuntu 11.04...please note that i dont have internet in ubuntu as i depend on wlan for it...i can access internet in windows.

---

### Post by irv on 2011-06-02
> **sarath kolli said:**
> please guide me regarding how to install essential linux-headers-generic and dep linux

in ubuntu 11.04...please note that i dont have internet in ubuntu as i depend on wlan for it...i can access internet in windows.
In your case you should start a new thread and give as much information you can about what kind of an install you did and what you installed it on. But I can tell you this if you are trying to get a wifi card working you will need to plug into the Internet to get the right drivers. I know in my case I needed too.

---

### Post by fox-mulder on 2011-06-02
> **marty331 said:**
> I just reinstalled (due to a completely different issue) and I followed my own instructions.  I believe they are on page 25 or 24 of this post.  I have the 4312 as well and  my instructions worked.  No need to go back to 10.10, 11.04 is AWESOME!

I should mention that STA works but I wanna use the b43 driver not the STA driver, and in 10.10 b43 & STA worked fine they both showed up on the list "additional drivers" but not in 11.04 :(

and i use hp mini 210-1000

---

### Post by michael9559 on 2011-06-02
I found this website, it is easy to follow and totally fixed the problem for me: [http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/]("http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/")

I used '**Alternative Solution 2**', basically it says this:
1) Open the '*Synaptic Package Manager*' and search for '*bcm*'
2) Uninstall the '*bcmwl-kernel-source*' package
3) Make sure that the '*firmware-b43-installer*' and the '*b43-fwcutter*' packages are installed
4) Type into terminal (copy and paste is best): 
*cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl'*
5) See if the term '*blacklist bcm43xx*' is there
6) If it is type into the terminal '*cd /etc/modprobe.d/*' and then '*sudo gedit blacklist.conf*'
7) Find the line containing '*blacklist bcm43xx*' and put a # at the start of the line
8 ) Save the file *(apparently some get an error message that it cannot save, ignore this if it happens)*
9) Reboot

---

### Post by irv on 2011-06-02
> **fox-mulder said:**
> I should mention that STA works but I wanna use the b43 driver not the STA driver, and in 10.10 b43 & STA worked fine they both showed up on the list "additional drivers" but not in 11.04 :(

and i use hp mini 210-1000

Just for the record they both show up in 10.10 on my Dell Inspiron 1521 but not 11.04, and that includes Xubuntu 11.04.

---

### Post by irv on 2011-06-02
> **michael9559 said:**
> I found this website, it is easy to follow and totally fixed the problem for me: [http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/]("http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/")

I used '**Alternative Solution 2**', basically it says this:
1) Open the '*Synaptic Package Manager*' and search for '*bcm*'
2) Uninstall the '*bcmwl-kernel-source*' package
3) Make sure that the '*firmware-b43-installer*' and the '*b43-fwcutter*' packages are installed
4) Type into terminal (copy and paste is best): 
*cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl'*
5) See if the term '*blacklist bcm43xx*' is there
6) If it is type into the terminal '*cd /etc/modprobe.d/*' and then '*sudo gedit blacklist.conf*'
7) Find the line containing '*blacklist bcm43xx*' and put a # at the start of the line
8 ) Save the file *(apparently some get an error message that it cannot save, ignore this if it happens)*
9) Reboot

In my case I didn't have to do steps 5,6,7, and 8. I just jump from 4 to 9 and Rebooted. bcm43xx was in the list but I didn't have to rem it out (#). If you look at this file it said bcm43xx was replace by b43 which was just installed.

The question I have is why is this file not installed during the install of 11.04? If you are going to black list some driver and then replace it by another why not include it in the install process? It doesn't make any sense to me!

---

### Post by fox-mulder on 2011-06-02
11.04 doesn't make any sense regard of the driver BS ISSUE,
heres a question, ( if there is a Linux/Ubuntu/developer expert ) reading this, why the !@#$%^ did you developer **** this up, what was the reason? did the B43 driver mock the other drivers>?

freaking lame..

---

### Post by josephmills on 2011-06-02
> **fox-mulder said:**
> 11.04 doesn't make any sense regard of the driver BS ISSUE,
heres a question, ( if there is a Linux/Ubuntu/developer expert ) reading this, why the !@#$%^ did you developer **** this up, what was the reason? did the B43 driver mock the other drivers>?

freaking lame..

Hi there another x files fan yah. try this post number 44  [http://ubuntuforums.org/showthread.php?t=1748245&page=5](http://ubuntuforums.org/showthread.php?t=1748245&page=5)
if you get stuck just say something and we will jump in to help on a side note whats you fav episode I like humbug

---

### Post by raphytaffy on 2011-06-02
Not sure if I should be posting in this thread, but since my wireless card is BMC4309, I thought I'd give it a shot. Just installed 11.04 on my Inspiron 600M and wireless doesn't seem to be working. I'm a linux noob, but I browsed another thread and tried typing **sudo lshw -C network **in terminal. It returned this:

```
 *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:11:43:47:0c:22
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=5705-v3.16 ip=192.168.1.25 latency=32 link=yes mingnt=64 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:11 memory:faff0000-faffffff
  *-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:5 memory:fafee000-fafeffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:11:f5:33:2d:cb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

```

Since it returned information on my card, does this mean that drivers for it are already installed? Or should I follow the guide in OP? No idea how to interpret the results, all I notice is the DISABLED.

---

### Post by jakerock on 2011-06-03
Has anyone been able to fix the frequent disconnects problem with the broadcom wifi? I am using the broadcom 4312 card on a ubuntu natty 2.6.38-8-generic-pae, with the b43-lpphy installed. Although it doesnt look like its dependent on the kernel or the STA/b43 or the card model, or the wicd/nm-applet. :(

---

### Post by ihadanny on 2011-06-03
wanted to share a success story due to Joren's post (and others in this thread). 
Lenovo S12, with BCM4312 LP-PHY [14e4:4315], Dual boot mode with Windows7. 
STA Broadcom driver aka "wl", kept ruining firmware for both natty AND windows7, making the wireless unusable or extremely slow..
I finally gave up on it, un-installed and installed b43, exactly as Joren told it (except I used the LP-PHY variant), and wireless hums happily!
Thanks, that was a saver.

---

### Post by raphytaffy on 2011-06-03
Can anyone offer help/advice on my previous post? Not ashamed to say that I have absolutely no idea what I'm doing here haha.

---

### Post by nm_geo on 2011-06-03
> **raphytaffy said:**
> Can anyone offer help/advice on my previous post? Not ashamed to say that I have absolutely no idea what I'm doing here haha.

raphy,

Give us the result of these.

```
lspci -nn
``````
rfkill list
```

firmware=N/A  that could be a problem too

---

### Post by raphytaffy on 2011-06-03
```
:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] [1002:4c66] (rev 02)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
02:01.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller [1217:7113] (rev 20)
02:01.1 CardBus bridge [0607]: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller [1217:7113] (rev 20)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11a/b/g [14e4:4324] (rev 03)
:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by nm_geo on 2011-06-03
14e4:4324  yes (b43legacy) 



Ok we have a little information.  I got that from a search on "B43 linux"


I am not on my Natty distro so I can not see the driver choices in synaptic.  Open synaptic and search for b43 then look for "legacy" keyword.  Install the b43 legacy and the firmware if it shows up.  I will reboot into Natty and look too.

Okay in Natty now too.. I opened synaptic and you need to make sure you have 

firmware-b43legacy-installer and b43-fwcutter   installed.
Let's see what that does.

---

### Post by raphytaffy on 2011-06-03
> **nm_geo said:**
> Okay in Natty now too.. I opened synaptic and you need to make sure you have 

firmware-b43legacy-installer and b43-fwcutter   installed.
Let's see what that does.

Does it matter what order I install these in?

---

### Post by nm_geo on 2011-06-03
> **raphytaffy said:**
> Does it matter what order I install these in?

No it should not matter

---

### Post by raphytaffy on 2011-06-03
Got this error upon installation:

```
E:firmware-b43legacy-installer: subprocess installed post-installation script returned error exit status 1
```

---

### Post by nm_geo on 2011-06-03
> **raphytaffy said:**
> Got this error upon installation:

```
E:firmware-b43legacy-installer: subprocess installed post-installation script returned error exit status 1
```

Do you have the b43-fwcutter installed?  Are there any other b43 firmwares installed?

---

### Post by raphytaffy on 2011-06-03
> **nm_geo said:**
> Do you have the b43-fwcutter installed?  Are there any other b43 firmwares installed?

I just closed the error and Synaptic shows b43-fwcutter 1:013-3 and firmware-b43legacy-installer 4.178.10.4-5 installed. Now what do I do? lol

---

### Post by nm_geo on 2011-06-03
> **raphytaffy said:**
> I just closed the error and Synaptic shows b43-fwcutter 1:013-3 and firmware-b43legacy-installer 4.178.10.4-5 installed. Now what do I do? lol

Verify you have no other " b43 firmware" installed i believe there are two others.  Then do the 

```
sudo lshw -C network 
``` and paste results

---

### Post by raphytaffy on 2011-06-03
The option to remove **firmware-b43-installer** and **firmware-b43-lpphy-installer** is greyed out, so I'm assuming they are not installed.

```
:~$ sudo lshw -C network 
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:11:43:47:0c:22
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=5705-v3.16 ip=192.168.1.25 latency=32 link=yes mingnt=64 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:11 memory:faff0000-faffffff
  *-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:5 memory:fafee000-fafeffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:11:f5:33:2d:cb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
```

---

### Post by nm_geo on 2011-06-03
Still no firmware..
Ok play like broadcom don't know their own chipsets.
Remove the b43legacy firmware and install the firmware-b43-installer in synaptic.  Reboot and do the lshw command again.

---

### Post by raphytaffy on 2011-06-03
> **nm_geo said:**
> Still no firmware..
Ok play like broadcom don't know their own chipsets.
Remove the b43legacy firmware and install the firmware-b43-installer in synaptic.  Reboot and do the lshw command again.

Should I remove the b43-fwcutter as well or just the legacy?

---

### Post by nm_geo on 2011-06-03
> **raphytaffy said:**
> Should I remove the b43-fwcutter as well or just the legacy?

We will need the b43-fwcutter but you could remove all of them and re-install the b43-fwcutter and the firmware-b43-installer.

Then reboot and run
```
sudo lshw -C network
```and 
```
dmesg | grep firm
```Both results please

---

### Post by raphytaffy on 2011-06-03
No post-installation error this time around:

```
:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:11:43:47:0c:22
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=5705-v3.16 ip=192.168.1.25 latency=32 link=yes mingnt=64 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:11 memory:faff0000-faffffff
  *-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:5 memory:fafee000-fafeffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:11:f5:33:2d:cb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=410.2160 link=no multicast=yes wireless=IEEE 802.11bg
:~$ dmesg | grep firm
[   21.836049] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
```

---

### Post by nm_geo on 2011-06-03
Sure looks like you are about there to me.

Do you see a wireless light on?  The firmware installed.. So next boot up take the cable out and connect to your wireless.

First
```
sudo iwlist scanning; cat /etc/network/interfaces
```

Let do two at once before you Reboot

---

### Post by raphytaffy on 2011-06-03
Woot! Wireless is working! Thanks for all of your help :D

---

### Post by nm_geo on 2011-06-03
> **raphytaffy said:**
> Woot! Wireless is working! Thanks for all of your help :D

Excellent You are more than welcome we could have got it sooner but Broadcom gave us bad info to start with.

Any questions I might can answer?

---

### Post by raphytaffy on 2011-06-03
This is my first time really giving Ubuntu a try, so feel free to suggest any helpful links to a user making the transition from Windows. Thanks again!

---

### Post by nm_geo on 2011-06-03
> **raphytaffy said:**
> This is my first time really giving Ubuntu a try, so feel free to suggest any helpful links to a user making the transition from Windows. Thanks again!

You know the forums are good for that too... There are lots of info about ubuntu on the web.. Try Ubuntu manual or something like that and jump in with both feet you have already done the two hardest parts. Installing and wireless ...

---

### Post by sirius_2 on 2011-06-07
Hello, everybody! Excuse me for my bad English.
Today I've got problem with my Lenovo Ideapad S10 (Ubuntu 11.04 32bit).
I've installed today's updates, whereupon the wireless driver (wireless controller - BCM4312)was found broken. I suppose it cannot be updated properly.
I cannot activate it with driver utility, it shows "SystemError: installArchives() failed", also I can't do it with Synaptic ("E: bcmwl-kernel-source: subprocess installed post-installation script returned error exit status 2"
```
Unpacking replacement broadcom-sta-common ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu3.1) ...
/var/lib/dpkg/info/bcmwl-kernel-source.postinst: 53: Syntax error: "fi" unexpected (expecting ";;")
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up broadcom-sta-common (5.60.48.36-3) ...
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu3.1) ...
/var/lib/dpkg/info/bcmwl-kernel-source.postinst: 53: Syntax error: "fi" unexpected (expecting ";;")
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 bcmwl-kernel-source

```
I need your help. Thanks!:D

---

### Post by Alcoori on 2011-06-07
Hi everyone,

Ubuntu upgraded some files yesterday and asked for a reboot in order to complete it. When the laptop rebooted, my wireless drivers seemed to have disappeared.

when i do a 
```
lshw -C network
```

I get the following results

```
 *-network               
       description: Ethernet interface
       product: NetXtreme BCM5753M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 21
       serial: 00:17:08:33:fc:df
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=5753m-v3.56 ip=192.168.1.21 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:47 memory:f4100000-f410ffff
  *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f4000000-f4003fff

```

I've tried installing drivers for the wireless card but get errors like the ones for the poster above me.

What can I do?

(btw, noob here)

---

### Post by sirius_2 on 2011-06-08
Hm-m-m... Linux guru, where are you? Your help would be very useful for us.
The netbook without wireless connection is nothing, I think.

---

### Post by sirius_2 on 2011-06-08
To Alcoori.
Hello! If you've found yourself under the conditions like me, I can advise you to install older version of bcmwl-kernel-source with Synaptic. I've just done it and got wireless driver working. Unfortunately there is something wrong with the new version of this package.
Good luck!

---

### Post by Chazzer on 2011-06-08
thanks to **johnnytm**, your solution is the only one that worked for me!

---

### Post by abpriest on 2011-06-10
Output of:
```
lspci -vvnn | grep 14e4
```is:

```
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

```I ran ```
sudo apt-get install  firmware-b43-installer
```

And everything began working perfectly just as it had been under 10.10. 

Thanks!

---

### Post by abpriest on 2011-06-10
Well, it works partially....

Immediately after installing firmware-b43-installer the wireless worked. But after a restart, I couldn't get it to work with out doing this:
```

~$modprobe -r b43 ssb
~$modprobe b43 

```

Then, it worked again. But I assume that I will need to do this every time I restart. What am I missing?

---

### Post by bkratz on 2011-06-10
> **abpriest said:**
> Well, it works partially....

Immediately after installing firmware-b43-installer the wireless worked. But after a restart, I couldn't get it to work with out doing this:
```

~$modprobe -r b43 ssb
~$modprobe b43 

```Then, it worked again. But I assume that I will need to do this every time I restart. What am I missing?


post 2 of this thread has what you are looking for

[http://ubuntuforums.org/showthread.php?t=1773152](http://ubuntuforums.org/showthread.php?t=1773152)

---

### Post by amautotech on 2011-06-10
I am using Lenovo V460 , facing the same problem even after installing the drivers in Additional drivers panel , kindly guide me to solve it...

---

### Post by jakerock on 2011-06-13
> **jakerock said:**
> Has anyone been able to fix the frequent disconnects problem with the broadcom wifi? I am using the broadcom 4312 card on a ubuntu natty 2.6.38-8-generic-pae, with the b43-lpphy installed. Although it doesnt look like its dependent on the kernel or the STA/b43 or the card model, or the wicd/nm-applet. :(

Finally managed to fix this by getting rid of the b43-lpphy and installing the broadcom drivers from their website. :D

---

### Post by cicgo on 2011-06-13
I have a headache for an all week! I just can not make my wifi works!
**0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)**
is my card and I am running **Ubuntu 10.10 Maverick kernel Linux 2.6.35-30 on Dell Vostro1015.**
I tried everything I have found on forums. Especially I followed the instructions from *@josephmills* in this forum and nothing.
I installed Ubuntu year ago and after first update wireless was gone!! After several reinstalls OS and after spending many hours, somehow I managed to force wireless to work on. After that I had locked driver and everything was working perfectly until few days ago, after some updates was installed!!! Now I am running without wireless!
I know that can be big pain in the a.. but I must to fix wifi! 
Now I got install:

[LIST]
[*]firmware-b43-lpphy-instaler
[*]firmware-b43-legacy-installer (I've installed this because without that I see on NetworkManager that wireless is enabled but it show that I miss firmware?!! But when I try to install, message appears: E: firmware-b43legacy-installer: subprocess installed post-installation script returned error exit status 1.The same message appears when I tried to install firmware-b43-installer.)
[*]b43-fwcutter
[/LIST]
follow drivers aren't installed now:

[LIST]
[*]bcmwl-kernel-source
[*]bcmwl-modaliases
[/LIST]
In additional drivers I have only b43 (which was working perfectly before last update)
I've tried to remove everything and to install one by one, tried everything that found on forums but nothing. Now in NM there was no wireless, just wired connection. 
Just to mention that nothing is blocked:
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

Can anybody help? Can anybody give me advice please?

---

### Post by irv on 2011-06-13
cicgo if you are using version 10.10, the driver that installs with "Additional Driver" should work.
First uninstall all the drivers you have installed.
Next open the "Additional Drivers" under your Administration menu. It should find the STA driver. Select it and Activate. (make sure you are plugged in with the network cable so you can download the driver from the repo).
That should work.

I used 10.10 and 10.04 and I have the Broadcom 4311 card and it worked fine. I am using Xubuntu 11.04 now and I need to install the b43 driver. There was a change made somewhere between 10.10 and 11.04. I am not sure if it's in the kernel or what.

---

### Post by cicgo on 2011-06-13
thanx @irv     but I can not even activate the driver. Shows me a massage: "SystemError: Install Archive() faild" when I am trying to activate STA driver and "Sorry, the installation of this driver faild. Please have a look at the log file of details.:/var/log/jockey.log" when I'm trying to activate the b43 driver.
I'm living in agony! :sad:

---

### Post by irv on 2011-06-13
> **cicgo said:**
> thanx @irv     but I can not even activate the driver. Shows me a massage: "SystemError: Install Archive() faild" when I am trying to activate STA driver and "Sorry, the installation of this driver faild. Please have a look at the log file of details.:/var/log/jockey.log" when I'm trying to activate the b43 driver.
I'm living in agony! :sad:
When you try to activate the driver do you have your wire Internet plugged in and are you able to connect to the Internet. If you are not you can't activate the driver.

---

### Post by cicgo on 2011-06-14
Yes I am connected on internet all the time (with wire). 
I'm very confused!?! Some times when I log on my laptop NM shows me that wireless is enabled but firmware is missing, sometimes (as now) NM doesn't see wireless card!?? #@!~
Just to add: when I tried "sudo aptitude install b43-fwcutter firmware-b43-lpphy-installer" I got massage "**Errors were encountered while processing: firmware-b43legacy-installer**".
Does anybody know how to fix this problem?

---

### Post by irv on 2011-06-14
> **cicgo said:**
> Yes I am connected on internet all the time (with wire). 
I'm very confused!?! Some times when I log on my laptop NM shows me that wireless is enabled but firmware is missing, sometimes (as now) NM doesn't see wireless card!?? #@!~
Just to add: when I tried "sudo aptitude install b43-fwcutter firmware-b43-lpphy-installer" I got massage "**Errors were encountered while processing: firmware-b43legacy-installer**".
Does anybody know how to fix this problem?

I know you have the 4312 from another post of your. I have the 4311 which works with the b43 and not the STA driver. I read some of the posts at the beginning of this thread and while some got there 4312 working others with the same card did not by doing the same things. There are some real problems with this release of Ubuntu. I know it took me two days to get mine going and then just out of the blue it started to work and it has been working ever since. All I can say is start reading from the beginning of this thread and keep trying and who knows it may start working. I don't know what else to tell you.

---

### Post by haithurmiranda on 2011-06-15
i am absolutely brand new to ubuntu and linux in general, and just installed this on my HP laptop.

i have the 4311 wireless card and i'm having the same problem that everyone else seems to be having... i've been trying to follow the instructions in these posts to the best of my ability but honestly i have no idea what anyone is saying.

can anyone explain this in really, really simple terms for me?

---

### Post by marty331 on 2011-06-15
> **haithurmiranda said:**
> i am absolutely brand new to ubuntu and linux in general, and just installed this on my HP laptop.

i have the 4311 wireless card and i'm having the same problem that everyone else seems to be having... i've been trying to follow the instructions in these posts to the best of my ability but honestly i have no idea what anyone is saying.

can anyone explain this in really, really simple terms for me?


Please follow these instructions, I wrote these and I've used them on both of my computers running Natty.  If you have any questions just reply back, good luck!

1) attach ethernet lead
2) in "additional drivers", turn off STA driver that was auto installed after vanilla 11.04 install
3) in synaptic package manager, remove bcmwl-kernel-source, every     b43/broadcom entry, finding them by using the "search" button on those     two terms and not the "quick filter"
4) restart computer
5) open terminal,"sudo apt-get install bcmwl-kernel-source"
6) restart computer and enjoy the wifi.
(at this point I did not have wifi going so then I continued on)
7)  in synaptic package manager I searched (again search, not quick   filter) for broadcom and installed the following: b43-fwcutter,   broadcom-sta-common, broadcom-sta-source.  Already installed was   bcmwl-kernal-source, so I left that alone.
:cool:    restart, yes again.  I was still connected to ethernet but I hovered   over my ethernet and opened the list of availalble networks and could   see my wfie, so I disconnected the ethernet and connected to wifi.

---

### Post by westie457 on 2011-06-15
> **haithurmiranda said:**
> i am absolutely brand new to ubuntu and linux in general, and just installed this on my HP laptop.

i have the 4311 wireless card and i'm having the same problem that everyone else seems to be having... i've been trying to follow the instructions in these posts to the best of my ability but honestly i have no idea what anyone is saying.

can anyone explain this in really, really simple terms for me?

Hi the really simple way is here. Look at post #188


[http://ubuntuforums.org/showthread.php?t=1604868&page=19]("http://ubuntuforums.org/showthread.php?t=1604868&page=19")

---

### Post by westie457 on 2011-06-15
[QUOTE=cicgo;10934417]I have a headache for an all week! I just can not make my wifi works!
**0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)**
is my card and I am running **Ubuntu 10.10 Maverick kernel Linux 2.6.35-30 on Dell Vostro1015.**
I tried everything I have found on forums. Especially I followed the instructions from *@josephmills* in this forum and nothing.
I installed Ubuntu year ago and after first update wireless was gone!! After several reinstalls OS and after spending many hours, somehow I managed to force wireless to work on. After that I had locked driver and everything was working perfectly until few days ago, after some updates was installed!!! Now I am running without wireless!
I know that can be big pain in the a.. but I must to fix wifi! 
Now I got install:

[LIST]
[*]firmware-b43-lpphy-instaler
[*]firmware-b43-legacy-installer (I've installed this because without that I see on NetworkManager that wireless is enabled but it show that I miss firmware?!! But when I try to install, message appears: E: firmware-b43legacy-installer: subprocess installed post-installation script returned error exit status 1.The same message appears when I tried to install firmware-b43-installer.)
[*]b43-fwcutter
[/LIST]
follow drivers aren't installed now:

[LIST]
[*]bcmwl-kernel-source
[*]bcmwl-modaliases
[/LIST]
In additional drivers I have only b43 (which was working perfectly before last update)
I've tried to remove everything and to install one by one, tried everything that found on forums but nothing. Now in NM there was no wireless, just wired connection. 
Just to mention that nothing is blocked:
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

Can anybody help? Can anybody give me advice please?[/QUOTE

@cicgo


Have just got wireless working on a Maverick LiveUSB with a persistence so changes will be saved.

Everything was done in Synaptic.

1, Enable  Software Restricted by copyright.   Settings > Repositories >  enable software restricted by copyright (multiverse). Click 'Close'  a warning came about reloading click okay. Click 'Reload'

2, Search for 'bcm' .  NOT a 'Quick-search. The one in the top right corner.

3. Mark 'b43-fwcutter'

4. Leave 'bcmwl-modaliases' as it is

5. Mark 'firmware-b43-installer'. Click 'Apply'. 

6. Wait for everything to settle down and close 'Synaptic'.

7. Now click on 'network-manager' applet you should now see wireless networks around you.


If you cannot see any then repeat the above changing Line 5 to whatever works. You might need the 'firmware-b43-lpphy-installer' package.'

---

### Post by haithurmiranda on 2011-06-15
> **marty331 said:**
> Please follow these instructions, I wrote these and I've used them on both of my computers running Natty.  If you have any questions just reply back, good luck!

1) attach ethernet lead
2) in "additional drivers", turn off STA driver that was auto installed after vanilla 11.04 install
3) in synaptic package manager, remove bcmwl-kernel-source, every     b43/broadcom entry, finding them by using the "search" button on those     two terms and not the "quick filter"
4) restart computer
5) open terminal,"sudo apt-get install bcmwl-kernel-source"
6) restart computer and enjoy the wifi.
(at this point I did not have wifi going so then I continued on)
7)  in synaptic package manager I searched (again search, not quick   filter) for broadcom and installed the following: b43-fwcutter,   broadcom-sta-common, broadcom-sta-source.  Already installed was   bcmwl-kernal-source, so I left that alone.
:cool:    restart, yes again.  I was still connected to ethernet but I hovered   over my ethernet and opened the list of availalble networks and could   see my wfie, so I disconnected the ethernet and connected to wifi.

i can't seem to be able to delete any of the b43/broadcom entries in synaptic package manager... i can mark them but only for installation? does that mean they're not there?

---

### Post by cicgo on 2011-06-15
> **westie457 said:**
> 

@cicgo


Have just got wireless working on a Maverick LiveUSB with a persistence so changes will be saved.

Everything was done in Synaptic.

1, Enable  Software Restricted by copyright.   Settings > Repositories >  enable software restricted by copyright (multiverse). Click 'Close'  a warning came about reloading click okay. Click 'Reload'

2, Search for 'bcm' .  NOT a 'Quick-search. The one in the top right corner.

3. Mark 'b43-fwcutter'

4. Leave 'bcmwl-modaliases' as it is

5. Mark 'firmware-b43-installer'. Click 'Apply'. 

6. Wait for everything to settle down and close 'Synaptic'.

7. Now click on 'network-manager' applet you should now see wireless networks around you.


If you cannot see any then repeat the above changing Line 5 to whatever works. You might need the 'firmware-b43-lpphy-installer' package.'

@westie257 I done exactly you had specifies but something is wrong with my ubuntu. When I reloaded synaptic, a massage appeared:

[LIST]
[*]Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)/dists/maverick/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognised by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)/dists/maverick/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognised by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
[/LIST]
Also, when I tried to install firmware-b43-installer (firmware-b43-lpphy-installer, as well) another massage appeared:

[LIST]
[*]E: firmware-b43legacy-installer: subprocess installed post-installation script returned error exit status 1
E: firmware-b43-installer: subprocess installed post-installation script returned error exit status 1
[/LIST]
Apparently I have a problem with repository or with synaptic!?? This issue crosses my knowledge  of Ubuntu! I feel like I'm on dead end.  
Does anybody have a suggestion what next?

---

### Post by cicgo on 2011-06-15
At last I have succed! I ran recovery at startup and when I logged on, wireless appeared! Just to mention, I was mistaken. I thought that I was using b43 driver, but now I see that my card using sda.
I don't now if my wireless will continue to work without problems but now it working just well. 
Thanx to everyone who was trying to help me, you guys are doing a great job!
Salute

---

### Post by westie457 on 2011-06-15
> **cicgo said:**
> At last I have succed! I ran recovery at startup and when I logged on, wireless appeared! Just to mention, I was mistaken. I thought that I was using b43 driver, but now I see that my card using sda.
I don't now if my wireless will continue to work without problems but now it working just well. 
Thanx to everyone who was trying to help me, you guys are doing a great job!
Salute

Well done and Happy Ubuntu-ing. Believe it or not everybody here enjoys helping to find solutions and we also enjoy when those we help find their own solutions as you have done.

These Forums are a win-win situation.

---

### Post by linuxafficionade on 2011-06-16
According to HP I have:
Broadcom 802.11 a/b/g Broadcom 802.11 b/g Broadcom 4321AG 802.11a/b/g/draft-n Wi-Fi Adapter Broadcom 54g MaxPerformance 802.11g 



I am connecting via the STA driver but it is unstable - I get disconnected and I need to reboot in order for it to reconnect.

Any suggestions?

I am on Ubuntu Studio 11

---

### Post by westie457 on 2011-06-17
> **linuxafficionade said:**
> According to HP I have:
Broadcom 802.11 a/b/g Broadcom 802.11 b/g Broadcom 4321AG 802.11a/b/g/draft-n Wi-Fi Adapter Broadcom 54g MaxPerformance 802.11g 



I am connecting via the STA driver but it is unstable - I get disconnected and I need to reboot in order for it to reconnect.

Any suggestions?

I am on Ubuntu Studio 11

Hello did some 'Googling' and found this

[http://ubuntuforums.org/showthread.php?t=548624]("http://ubuntuforums.org/showthread.php?t=548624")

Which pointed to this

[http://ubuntuforums.org/showthread.php?t=575750&highlight=broadcom+4321]("http://ubuntuforums.org/showthread.php?t=575750&highlight=broadcom+4321")

This one pointed me to this one

[URL="http://ubuntuforums.org/showthread.php?
t=870575"]http://ubuntuforums.org/showthread.php?t=870575[/URL]

Other than these links I have no idea what to suggest.

Maybe someone who knows more than me will step in to help if those links do not provide the solution.

---

### Post by zander1013 on 2011-06-19
> **blindfury37 said:**
> I just recently installed 10.10 and new to ubuntu.
I have a Dell Inspiron 600m with a broadcom 4306.

I was able to use another guide I found on here to get the wifi card working and it connects to open networks and WEP networks fine but I can't get it to connect to any WPA/WPA2 networks. Does anyone know any fixes for this?

Thanks in advance.

your card was manufactured before WPA/WPA2 and subsequently does not support them.

the only fix for this is to get a newer card (hardware) that does support said protocols.

---

### Post by ryth on 2011-06-19
Excellent, solution one worked for me perfectly.  Thank you for your post.

---

### Post by SeePU on 2011-06-20
As far as I'm concerned there is NO solution for BCM4813 cards.

After mucking around and countless googling, no 'solutions' have worked for the bcm4318 card in the laptop I was using.  

Broadcom is the worst co. as far as Linux support. 

I don't want to mess with ndiswrapper.  Not an option for me.  I'd rather just leave it as a Windoze machine if that's the only option.

---

### Post by johnabdl on 2011-06-20
I'm sorry folks, I've been struggling with the Broadcom card problem since March, with a 4322 in a Dell Latitude e6500. 

I started with 10.01 and upgraded to 11.04, which improved things for a while. But although I've had days of good connection, I've also had days where it continually drops after a few minutes, requiring restarting the browser, the wireless connection or even the whole machine. 

I've tried most suggestions here and I've had enough, so I'm going to buy a new card, the Intel Ultimate N 6300. If you look around it seems it can be had for less than $40 including shipping. 

I'll post if it has any problems or if it has no problems.

---

### Post by zander1013 on 2011-06-20
hi,

none of the previous suggestions in this thread worked for me.



however, i found a solution that worked for me here...
[http://computerandu.wordpress.com/20...-ubuntu-11-04/](http://computerandu.wordpress.com/20...-ubuntu-11-04/) (this link is now dead i gave a similar one below).

EDIT: here is the correct link..
[http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/](http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/)

i removed the sta driver and then deployed Alternate Solution 2 given in the link. i do hope it works for you.

EDIT:if the old solutions are not working and your new one does not remove b43 from the blacklist it probably won't work.

---

### Post by SeePU on 2011-06-20
Thanks, Zander!  That page looks interesting and the latest discussion is also intriguing.  However, I have an update that is puzzling and peculiar. ;)

I'll try to be brief as I want to update my thread based on a specific Broadcom chipset - BCM4318.

I am curious whether the 'possible solution' in this thread and that web page is applicable to a majority of Broadcom cards or only certain ones.   I mention that because there are a lot of broadcom drivers surprisingly enough.  Or a lot of chipsets so a few drivers.  

Anyway, I am not sure what happened but I discovered wireless working shockingly enough but no good explanation.  I was going to try Fedora 15 on my live usb stick but didn't insert into the usb port in time.  The reboot went to the grub screen so on a whim I booted up XP Pro.  The wireless connected immediately.  Confirming that the laptop's Broadcom wifi card works, I restarted and back at the grub screen, I left it at default to boot up Lubuntu.

Not really knowing what I was going to try, lo and behold, the wireless was enabled and I was able to look at the available networks (as it scanned automatically?)!  So, I chose mine and entered the info to connect.  Wireless was then working.

Does that make any sense?  I only could think of maybe some bug with the Broadcom driver connected with the kernel (newer kernel versions?) or somehow Windows 'turned on' the wireless capability or something?

I didn't undo or blacklist anything so if a reboot into windows (and initiating wireless) could possibly do anything?  If that makes no sense whatsoever, please mention so I can disregard this theory (I don't want to waste time if this theory is no good).  

I would have tried the blacklisting and the instructions from you and that page if it wasn't working.

I still don't consider it 'fixed' or solved since I am not trusting it to last for any amount of time.  But, at least, I have a few more things to try.   I have rebooted the machine before when I tested other distros live (usb stick) so the 'reboot' alone doesn't account for the wifi success.

Way too much typing from me on this...sorry...

---

### Post by Yeshining on 2011-06-21
> **johnnytm said:**
> I also have an Inspiron 1545, with the same bcm4312 wireless card. I have never used the b43 driver, nor have I ever used fwcutter. All I have ver done is connect the wired connection right after install and enabled the sta driver. Any other time, even in prior releases, The b43 driver has caused me nothing but trouble and complication. I am really confused as to why so many people have had problems using the STA driver when it has always been such a straightforward simple solution.

Hello,I', a green hand to ubuntu, and my wireless doesn't work.
and my dell's type is inspiron n4020.
I think you can help me!
Jesus is with you and my contact is:msn: [email]mashangtiankai@hotmail.com[/email]

---

### Post by SeePU on 2011-06-21
I have an 'unrelated' (?) issue now which I am not suprised... is there a thread for sleep/hiberate issues? :)   

At least, my wireless still works...

But, I have to reboot the entire machine.  If I close the lid, the machine doesn't wake up at all... crap!   

I think this situation is common, though.... Seem to read about this situation on most linux forums.   I hope there's a decent solution, though.

---

### Post by irv on 2011-06-21
> **SeePU said:**
> I have an 'unrelated' (?) issue now which I am not suprised... is there a thread for sleep/hiberate issues? :)   

At least, my wireless still works...

But, I have to reboot the entire machine.  If I close the lid, the machine doesn't wake up at all... crap!   

I think this situation is common, though.... Seem to read about this situation on most linux forums.   I hope there's a decent solution, though.
Under your power setting there should be an option to set "when lid is closed" do nothing. This will save you from rebooting all the time when the lid is closed.

---

### Post by ceoccarter on 2011-06-22
I have this problem using a Dell 1525 Inspiron 32bit Vista and 11.4  dual boot.

I have no access to ethernet so need to install via terminal, could someone give me the instructions in the most simple form, I am learning how to operate within the terminal - sudo apt-get install etc. etc. (noob..just switching from windows..)

Additionally, I have tried to follow some instructions in this thread and identified my broadcom as the 4213, but nothing is working for me yet.

*I have tried to reinstall  bcmwl-kernel-source, I have tried the firmware-bc43-lpphy-installer -- I am trying but may not have got everything correct. Also the synaptics does not show what I expect it to from peoples posts either..*

Please help, really eager to get into Linux:guitar:

---

### Post by ceoccarter on 2011-06-22
So my problem has been fixed - anyone with a Dell Inspiron 32bit Vista dual boot unable to connect to the internets .. here is my message -- find an ethernet cable, with all your power. Syncaptics Manager will really help you.

I did a lot of things so I am not sure exactly what worked -- however, eventually _when my computer was finding wi-fi signal, but not connecting_, I ...

[LIST=1]
[*]clicked ''connect to new wireless network'
[*]entered the name of connection and password
[*]boom, i had internet access.'
[/LIST]
(I had not tried this in the beginning, or throughout each step of the process, so I am not sure how important it is, equally how long-term the solution will be)

I also installed 
-- ndiswrapper-common
-- firmware-b43 lphhy-installler (4312 only)
-- dcmwl-kernel-source ) reinstalled after synaptics installation via terminal >sudo modprobe ndiswrapper
-- sudo rmmod wl (and blacklisted b43 and ssb)

I followed a lot of the instructions from here, check out [this link]("http://ubuntuforums.org/showthread.php?t=885847") it is the first post -very very helpful 

and finally [here ]("http://polach.cc/broadcom-wifi-adapter-wpa-access-fix-on-ubuntu-ii")

**Good Luck** :popcorn:

---

### Post by Ufonautas on 2011-06-23
Hey!

I have a problem with my Broadcom WiFi Drivers (?). WiFi is terribly slow, download speed is 500b/s (not kb/s), and it keeps disconnecting after 10-15mins. I have tried to install Windows to check my WiFi speed there, and guess what? In M$ Windows my download speed is 1,5mb/s So, i think it's broadcom drivers problem. 

(I have tried both STA and B43 drivers) 

[http://imageshack.us/photo/my-images/97/screenshotwzx.png/](http://imageshack.us/photo/my-images/97/screenshotwzx.png/)

( My iwconfig and apt-get install vim (see how slow it is?)) 

Any ideas how to fix it? 

Becouse i hate Windows, but i'm forced by slow wifi to use them...

---

### Post by josephmills on 2011-06-23
> **Ufonautas said:**
> Hey!

I have a problem with my Broadcom WiFi Drivers (?). WiFi is terribly slow, download speed is 500b/s (not kb/s), and it keeps disconnecting after 10-15mins. I have tried to install Windows to check my WiFi speed there, and guess what? In M$ Windows my download speed is 1,5mb/s So, i think it's broadcom drivers problem. 

(I have tried both STA and B43 drivers) 

[http://imageshack.us/photo/my-images/97/screenshotwzx.png/](http://imageshack.us/photo/my-images/97/screenshotwzx.png/)

( My iwconfig and apt-get install vim (see how slow it is?)) 

Any ideas how to fix it? 

Becouse i hate Windows, but i'm forced by slow wifi to use them...

are you downloading from the internet(p2p) or from ubuntu software center apt and synaptic if this is the case look at where you are downloading from Ubuntu Software Center-->Edit-->Software Sources then make sure you are downloading from the right place

---

### Post by Ufonautas on 2011-06-24
> **josephmills said:**
> are you downloading from the internet(p2p) or from ubuntu software center apt and synaptic if this is the case look at where you are downloading from Ubuntu Software Center-->Edit-->Software Sources then make sure you are downloading from the right place


Thanks for reply, josephmills!

It's not the download Source problem, everywhere problem is the same, for example, ubuntuforums.org loads for about 30seconds, but on Windows OS (same computer)it loads for a 1sec. So, i think it's driver or iwconfig settings problem.


(And sorry, for my poor english grammar :) )

---

### Post by josephmills on 2011-06-25
> **Ufonautas said:**
> Thanks for reply, josephmills!

It's not the download Source problem, everywhere problem is the same, for example, ubuntuforums.org loads for about 30seconds, but on Windows OS (same computer)it loads for a 1sec. So, i think it's driver or iwconfig settings problem.


(And sorry, for my poor english grammar :) )
are you behind a proxy or tor ? also are you running proxychains. lets look at the card ```
iwconfig 
``` and ```
sudo lshw -C network 
```

---

### Post by fox-mulder on 2011-06-25
Okey I came to the part **lsmod | grep b43** and **dmesg | grep b43** in page 5 post 44 guide,
so what now? 

nothing changed as I can see, the b43 driver didn't show under STA driver :(

```
sudo lsmod | grep b43
``````

b43                   296610  0 
ssb                    45942  1 b43
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211

``````
sudo dmesg | grep b43
``````

[  667.324346] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  667.324379] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
[  667.413037] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[  667.487728] Registered led device: b43-phy0::tx
[  667.487889] Registered led device: b43-phy0::rx
[  667.488412] Registered led device: b43-phy0::radio
[  667.764134] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)

```"yah the Humbug episode was funny ;)

---

### Post by josephmills on 2011-06-25
> **fox-mulder said:**
> Okey I came to the part **lsmod | grep b43** and **dmesg | grep b43** in page 5 post 44 guide,
so what now? 

nothing changed as I can see, the b43 driver didn't show under STA driver :(

```
sudo lsmod | grep b43
``````

b43                   296610  0 
ssb                    45942  1 b43
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211

``````
sudo dmesg | grep b43
``````

[  667.324346] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  667.324379] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
[  667.413037] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[  667.487728] Registered led device: b43-phy0::tx
[  667.487889] Registered led device: b43-phy0::rx
[  667.488412] Registered led device: b43-phy0::radio
[  667.764134] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)

```"yah the Humbug episode was funny ;)

could we see a ```
lspci -nn
``` thanks

---

### Post by fox-mulder on 2011-06-26
sure

```

00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```

---

### Post by SeePU on 2011-06-26
I think some of you guys are going to extra trouble and don't need ndiswrapper.

Owners of laptops/computers with the Broadcom BCM4312 chips, you just need the -wl drivers.

See this page:

[http://wiki.debian.org/wl](http://wiki.debian.org/wl)

Additional info:

[http://linuxwireless.org/en/users/Drivers/b43#Ubuntu.2BAC8-Debian](http://linuxwireless.org/en/users/Drivers/b43#Ubuntu.2BAC8-Debian)

There's an Ubuntu page someplace but the page in the Debian wiki I posted first gives specific info about the install of the firmware for your wifi card/chipset.  It should apply to your Ubuntu install.

---

### Post by SeePU on 2011-06-26
> **irv said:**
> Under your power setting there should be an option to set "when lid is closed" do nothing. This will save you from rebooting all the time when the lid is closed.Just wanted to answer this.  

I installed Lubuntu on my laptop so the 'power settings' is set up differently than Ubuntu/Gnome.  I couldn't find anything except in 'Screensaver.'  There's a section for standby/suspend after a certain period of inactivity.  Nothing about the lid (being closed), though.  :-(

---

### Post by josephmills on 2011-06-26
> **fox-mulder said:**
> sure

```

00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```

ok lets try this ```
sudo apt-get remove --purge bcmwl-kernel-source && sudo apt-get remove --purge firmware-b43-installer && sud oreboot 
```after reboot do a ```
 sudo apt-get install firmware-b43-lpphy-installer && sudo apt-get install bcmwl-kernel-source && sudo reboot 
``` after reboot do you have wireless now ? if not do a ```
sudo modprobe b43 
``` now do you have wireless ?

---

### Post by bkratz on 2011-06-26
> **josephmills said:**
> ok lets try this ```
sudo apt-get remove --purge bcmwl-kernel-source && sudo apt-get remove --purge firmware-b43-installer && [COLOR="Red"]sud oreboot[/COLOR] 
```after reboot do a ```
 sudo apt-get install firmware-b43-lpphy-installer && sudo apt-get install bcmwl-kernel-source && sudo reboot 
``` after reboot do you have wireless now ? if not do a ```
sudo modprobe b43 
``` now do you have wireless ?

@Joseph

I am sure you meant "sudo reboot" at that location in the first area

---

### Post by josephmills on 2011-06-26
> **bkratz said:**
> @Joseph

I am sure you meant "sudo reboot" at that location in the first area

yes I did thanks for catching that ):P

---

### Post by fox-mulder on 2011-06-26
No b43 driver/wireless visible under STA driver

and when I tried 

```
sudo modprobe b43
```
this error came up 

```

WARNING: All config files need .conf: /etc/modprobe.d/psmouse.modprobe, it will be ignored in a future release.

```

xD wth 

thanks

---

### Post by josephmills on 2011-06-26
> **fox-mulder said:**
> No b43 driver/wireless visible under STA driver

and when I tried 

```
sudo modprobe b43
```
this error came up 

```

WARNING: All config files need .conf: /etc/modprobe.d/psmouse.modprobe, it will be ignored in a future release.

```

xD wth 

thanks

could we see a ```
lsmod
```

---

### Post by fox-mulder on 2011-06-26
lsmod

```

Module                  Size  Used by
b43                   296610  0 
ssb                    45942  1 b43
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211
michael_mic            12540  8 
arc4                   12473  4 
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
rfcomm                 38125  8 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
sco                    17779  2 
i915                  450944  3 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
snd_seq_midi_event     14475  1 snd_seq_midi
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip    17203  0 
btusb                  18160  2 
uvcvideo               66851  0 
wl                   2642531  0 
bluetooth              65565  9 rfcomm,sco,bnep,l2cap,btusb
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73312  0 
videodev               75143  1 uvcvideo
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
drm_kms_helper         40745  1 i915
lib80211               14570  2 lib80211_crypt_tkip,wl
soundcore              12600  1 snd
drm                   180037  4 i915,drm_kms_helper
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
r8169                  42534  0 
ahci                   21591  2 
libahci                25548  1 ahci

```

---

### Post by josephmills on 2011-06-26
> **fox-mulder said:**
> lsmod

```

Module                  Size  Used by
b43                   296610  0 
ssb                    45942  1 b43
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211
michael_mic            12540  8 
arc4                   12473  4 
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
rfcomm                 38125  8 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
sco                    17779  2 
i915                  450944  3 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
snd_seq_midi_event     14475  1 snd_seq_midi
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip    17203  0 
btusb                  18160  2 
uvcvideo               66851  0 
[COLOR="Red"] wl                   2642531  0 [/COLOR]
bluetooth              65565  9 rfcomm,sco,bnep,l2cap,btusb
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73312  0 
videodev               75143  1 uvcvideo
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
drm_kms_helper         40745  1 i915
lib80211               14570  2 lib80211_crypt_tkip,wl
soundcore              12600  1 snd
drm                   180037  4 i915,drm_kms_helper
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
r8169                  42534  0 
ahci                   21591  2 
libahci                25548  1 ahci

```

```
 sudo su 
echo blacklist wl >> /etc/modprobe.d/blacklist.conf
```

then reboot then 
```
modprobe b43 
``` then a ```
sudo su 
echo >> b43 /ect/modules
exit 
```
  
then reboot with the ethernet cable not connected
got wireless ?  If not let us see a ```
rfkill list all 
``` thanks

---

### Post by fox-mulder on 2011-06-26
I got wireless, I am using the the **sta** driver and its working but not the b43 hope I told that I want the b43 driver so we don't go the wrong way with this. ;)

thanks

---

### Post by bkratz on 2011-06-26
@Joseph,

sudo su 
echo >> b43 /[COLOR="Red"]ect[/COLOR]/modules
exit


[COLOR="red"]etc?[/COLOR]
also, STA sometimes puts b43 and ssb in the blacklist which should be removed.

---

### Post by josephmills on 2011-06-26
> **fox-mulder said:**
> I got wireless, I am using the the **sta** driver and its working but not the b43 hope I told that I want the b43 driver so we don't go the wrong way with this. ;)

thanks


mulder you are saying that the sta also called the wl is working for you is you wireless working ? if the wl or sta as you call it is working then blacklist the b43 and there you go. if not please tell me what is going on in this anomaly. thanks

---

### Post by josephmills on 2011-06-26
> **bkratz said:**
> @Joseph,

sudo su 
echo >> b43 /[COLOR="Red"]ect[/COLOR]/modules
exit


[COLOR="red"]etc?[/COLOR]
also, STA sometimes puts b43 and ssb in the blacklist which should be removed.

ohh fat fingers today

---

### Post by fox-mulder on 2011-06-26
okey, first of all now the **sta** is deactivated and it gives me an error when I try to activate it

```

Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

``` And I am connected with cable now, my wireless is also connected with a different ip wow even when the **sta** driver is deactivated.

**jockey.log**

```

2011-06-26 20:56:18,228 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c>
2011-06-26 20:56:23,995 DEBUG: reading modalias file /lib/modules/2.6.38-8-generic/modules.alias
2011-06-26 20:56:24,449 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-06-26 20:56:24,450 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-06-26 20:56:24,599 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-06-26 20:56:24,639 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-06-26 20:56:24,650 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-06-26 20:56:24,651 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-06-26 20:56:24,703 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-06-26 20:56:24,704 DEBUG: loading custom handler /usr/share/jockey/handlers/nouveau3d.py
2011-06-26 20:56:24,767 DEBUG: Instantiated Handler subclass __builtin__.Nouveau3DHandler from name Nouveau3DHandler
2011-06-26 20:56:24,768 DEBUG: Experimental 3D support for NVIDIA cards not available
2011-06-26 20:56:24,769 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-06-26 20:56:24,827 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-06-26 20:56:24,828 DEBUG: Firmware for DVB cards not available
2011-06-26 20:56:24,828 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-06-26 20:56:24,879 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-06-26 20:56:24,914 DEBUG: Software modem not available
2011-06-26 20:56:24,915 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-06-26 20:56:24,934 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-06-26 20:56:24,935 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-06-26 20:56:24,936 DEBUG: nvidia.available: falling back to default
2011-06-26 20:56:25,124 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-8 does not match X.org video ABI xorg-video-abi-10
2011-06-26 20:56:25,124 DEBUG: NVIDIA accelerated graphics driver not available
2011-06-26 20:56:25,132 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-06-26 20:56:25,134 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-06-26 20:56:25,135 DEBUG: nvidia.available: falling back to default
2011-06-26 20:56:25,230 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-06-26 20:56:25,231 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 947, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-06-26 20:56:25,240 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-06-26 20:56:25,241 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-06-26 20:56:25,241 DEBUG: nvidia.available: falling back to default
2011-06-26 20:56:25,339 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-06-26 20:56:25,340 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-06-26 20:56:25,352 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-06-26 20:56:25,353 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-06-26 20:56:25,354 DEBUG: fglrx.available: falling back to default
2011-06-26 20:56:25,448 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-06-26 20:56:25,448 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-06-26 20:56:25,506 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-06-26 20:56:25,506 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-06-26 20:56:25,507 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-06-26 20:56:25,517 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-06-26 20:56:25,518 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-06-26 20:56:25,518 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-06-26 20:56:25,519 DEBUG: all custom handlers loaded
2011-06-26 20:56:25,519 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'pci:v00008086d000027D8sv0000103Csd00003660bc04sc03i00')
2011-06-26 20:56:26,732 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 20:56:26,733 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-06-26 20:56:26,751 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 20:56:26,751 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-06-26 20:56:26,752 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-06-26 20:56:26,752 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00003660bc02sc00i00')
2011-06-26 20:56:26,787 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 20:56:26,787 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-06-26 20:56:26,788 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 20:56:26,788 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'platform:eisa')
2011-06-26 20:56:26,790 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-06-26 20:56:26,877 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-06-26 20:56:26,877 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 20:56:26,878 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-06-26 20:56:26,878 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'platform:pcspkr')
2011-06-26 20:56:26,880 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 20:56:26,880 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 20:56:26,881 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'pci:v00008086d00002448sv0000103Csd00003660bc06sc04i01')
2011-06-26 20:56:26,893 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'platform:hp-wmi')
2011-06-26 20:56:26,895 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-06-26 20:56:26,896 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'pci:v00008086d0000A011sv0000103Csd00003660bc03sc00i00')
2011-06-26 20:56:26,907 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 20:56:26,908 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2011-06-26 20:56:26,908 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'pci:v00008086d000027C8sv0000103Csd00003660bc0Csc03i00')
2011-06-26 20:56:26,920 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-06-26 20:56:26,920 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'pci:v00008086d0000A012sv0000103Csd00003660bc03sc80i00')
2011-06-26 20:56:26,932 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-06-26 20:56:26,932 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'pci:v00008086d000027C9sv0000103Csd00003660bc0Csc03i00')
2011-06-26 20:56:26,943 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-06-26 20:56:26,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'acpi:SYN1E18:PNP0F13:')
2011-06-26 20:56:26,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-06-26 20:56:26,946 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'option', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 20:56:26,946 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'pci:v00008086d000027CBsv0000103Csd00003660bc0Csc03i00')
2011-06-26 20:56:26,958 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2011-06-26 20:56:26,958 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 20:56:26,959 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'input:b0003v0408p0FF1e0104-e0,1,kD4,ramlsfw')
2011-06-26 20:56:26,959 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 20:56:26,960 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'usb:v0408p0FF1d0104dcEFdsc02dp01ic0Eisc02ip00')
2011-06-26 20:56:26,969 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2011-06-26 20:56:26,970 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 20:56:26,970 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'pci:v00008086d000027CAsv0000103Csd00003660bc0Csc03i00')
2011-06-26 20:56:26,982 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.11:bd03/19/2010:svnHewlett-Packard:pnHPMini210-1000:pvr04A3100000202100000300000:rvnHewlett-Packard:rn3660:rvr48.24:cvnHewlett-Packard:ct10:cvrN/A:')
2011-06-26 20:56:27,037 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'acpi:INT0800:')
2011-06-26 20:56:27,038 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-06-26 20:56:27,038 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 20:56:27,039 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'usb:v03F0p2A1Dd0349dcE0dsc01dp01icE0isc01ip01')
2011-06-26 20:56:27,092 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 20:56:27,093 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'usb:v03F0p2A1Dd0349dcE0dsc01dp01icFFiscFFipFF')
2011-06-26 20:56:27,095 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 20:56:27,095 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000103Csd0000365Ebc02sc80i00')
2011-06-26 20:56:27,525 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 20:56:27,262 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2011-06-26 20:56:27,526 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 20:56:27,784 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 20:56:27,527 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2011-06-26 20:56:27,785 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'b43', 'jockey_handler': 'KernelModuleHandler', 'package': 'firmware-b43-lpphy-installer'}
2011-06-26 20:56:27,786 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-06-26 20:56:27,786 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'pci:v00008086d000027DAsv0000103Csd00003660bc0Csc05i00')
2011-06-26 20:56:27,800 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 20:56:27,800 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'usb:v0408p0FF1d0104dcEFdsc02dp01ic0Eisc01ip00')
2011-06-26 20:56:27,802 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 20:56:27,802 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2011-06-26 20:56:27,803 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 20:56:27,803 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'pci:v00008086d000027C1sv0000103Csd00003660bc01sc06i01')
2011-06-26 20:56:27,816 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 20:56:27,817 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 20:56:27,817 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'pci:v00008086d000027CCsv0000103Csd00003660bc0Csc03i20')
2011-06-26 20:56:27,831 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'platform:reg-dummy')
2011-06-26 20:56:27,833 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2011-06-26 20:56:27,834 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 20:56:27,834 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-06-26 20:56:27,835 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'usb:v03F0p2A1Dd0349dcE0dsc01dp01icFEisc01ip01')
2011-06-26 20:56:27,838 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 20:56:27,838 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2011-06-26 20:56:27,839 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-06-26 20:56:27,841 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-06-26 20:56:27,872 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 20:56:27,873 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 20:56:27,873 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'pci:v00008086d000027BCsv0000103Csd00003660bc06sc01i00')
2011-06-26 20:56:27,885 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 20:56:27,885 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-06-26 20:56:27,886 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 20:56:27,886 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9405b0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-06-26 20:56:27,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'pci:v00008086d000027D8sv0000103Csd00003660bc04sc03i00')
2011-06-26 20:56:27,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-06-26 20:56:27,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-06-26 20:56:27,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-06-26 20:56:27,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00003660bc02sc00i00')
2011-06-26 20:56:27,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-06-26 20:56:27,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'platform:eisa')
2011-06-26 20:56:27,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-06-26 20:56:27,889 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-06-26 20:56:27,889 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-06-26 20:56:27,889 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'platform:pcspkr')
2011-06-26 20:56:27,890 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'pci:v00008086d00002448sv0000103Csd00003660bc06sc04i01')
2011-06-26 20:56:27,890 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'platform:hp-wmi')
2011-06-26 20:56:27,890 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-06-26 20:56:27,890 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'pci:v00008086d0000A011sv0000103Csd00003660bc03sc00i00')
2011-06-26 20:56:27,891 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2011-06-26 20:56:27,891 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'pci:v00008086d000027C8sv0000103Csd00003660bc0Csc03i00')
2011-06-26 20:56:27,891 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-06-26 20:56:27,891 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'pci:v00008086d0000A012sv0000103Csd00003660bc03sc80i00')
2011-06-26 20:56:27,892 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-06-26 20:56:27,892 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'pci:v00008086d000027C9sv0000103Csd00003660bc0Csc03i00')
2011-06-26 20:56:27,892 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-06-26 20:56:27,893 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'acpi:SYN1E18:PNP0F13:')
2011-06-26 20:56:27,893 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-06-26 20:56:27,893 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'pci:v00008086d000027CBsv0000103Csd00003660bc0Csc03i00')
2011-06-26 20:56:27,893 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2011-06-26 20:56:27,894 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'input:b0003v0408p0FF1e0104-e0,1,kD4,ramlsfw')
2011-06-26 20:56:27,894 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'usb:v0408p0FF1d0104dcEFdsc02dp01ic0Eisc02ip00')
2011-06-26 20:56:27,894 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2011-06-26 20:56:27,895 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'pci:v00008086d000027CAsv0000103Csd00003660bc0Csc03i00')
2011-06-26 20:56:27,895 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.11:bd03/19/2010:svnHewlett-Packard:pnHPMini210-1000:pvr04A3100000202100000300000:rvnHewlett-Packard:rn3660:rvr48.24:cvnHewlett-Packard:ct10:cvrN/A:')
2011-06-26 20:56:27,895 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'acpi:INT0800:')
2011-06-26 20:56:27,895 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-06-26 20:56:27,896 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'usb:v03F0p2A1Dd0349dcE0dsc01dp01icE0isc01ip01')
2011-06-26 20:56:27,896 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'usb:v03F0p2A1Dd0349dcE0dsc01dp01icFFiscFFipFF')
2011-06-26 20:56:27,896 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000103Csd0000365Ebc02sc80i00')
2011-06-26 20:56:27,896 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-06-26 20:56:27,897 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'pci:v00008086d000027DAsv0000103Csd00003660bc0Csc05i00')
2011-06-26 20:56:27,897 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'usb:v0408p0FF1d0104dcEFdsc02dp01ic0Eisc01ip00')
2011-06-26 20:56:27,897 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2011-06-26 20:56:27,898 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'pci:v00008086d000027C1sv0000103Csd00003660bc01sc06i01')
2011-06-26 20:56:27,898 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'pci:v00008086d000027CCsv0000103Csd00003660bc0Csc03i20')
2011-06-26 20:56:27,898 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'platform:reg-dummy')
2011-06-26 20:56:27,898 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2011-06-26 20:56:27,899 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-06-26 20:56:27,899 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'usb:v03F0p2A1Dd0349dcE0dsc01dp01icFEisc01ip01')
2011-06-26 20:56:27,899 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2011-06-26 20:56:27,899 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-06-26 20:56:27,900 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-06-26 20:56:27,900 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'pci:v00008086d000027BCsv0000103Csd00003660bc06sc01i00')
2011-06-26 20:56:27,900 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-06-26 20:56:27,901 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x941030c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-06-26 20:56:28,296 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 20:56:28,802 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 20:56:29,309 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 20:56:29,813 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 20:56:30,132 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 20:56:30,636 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 20:56:37,982 DEBUG: Shutting down
2011-06-26 21:52:31,998 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c>
2011-06-26 21:52:37,648 DEBUG: reading modalias file /lib/modules/2.6.38-8-generic/modules.alias
2011-06-26 21:52:38,103 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-06-26 21:52:38,104 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-06-26 21:52:38,242 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-06-26 21:52:38,289 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-06-26 21:52:38,301 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-06-26 21:52:38,301 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-06-26 21:52:38,352 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-06-26 21:52:38,352 DEBUG: loading custom handler /usr/share/jockey/handlers/nouveau3d.py
2011-06-26 21:52:38,416 DEBUG: Instantiated Handler subclass __builtin__.Nouveau3DHandler from name Nouveau3DHandler
2011-06-26 21:52:38,418 DEBUG: Experimental 3D support for NVIDIA cards not available
2011-06-26 21:52:38,418 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-06-26 21:52:38,492 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-06-26 21:52:38,494 DEBUG: Firmware for DVB cards not available
2011-06-26 21:52:38,494 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-06-26 21:52:38,546 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-06-26 21:52:38,582 DEBUG: Software modem not available
2011-06-26 21:52:38,583 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-06-26 21:52:38,600 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-06-26 21:52:38,601 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-06-26 21:52:38,602 DEBUG: nvidia.available: falling back to default
2011-06-26 21:52:38,787 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-8 does not match X.org video ABI xorg-video-abi-10
2011-06-26 21:52:38,788 DEBUG: NVIDIA accelerated graphics driver not available
2011-06-26 21:52:38,795 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-06-26 21:52:38,796 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-06-26 21:52:38,797 DEBUG: nvidia.available: falling back to default
2011-06-26 21:52:38,893 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-06-26 21:52:38,894 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 947, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-06-26 21:52:38,905 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-06-26 21:52:38,906 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-06-26 21:52:38,906 DEBUG: nvidia.available: falling back to default
2011-06-26 21:52:39,010 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-06-26 21:52:39,010 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-06-26 21:52:39,022 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-06-26 21:52:39,023 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-06-26 21:52:39,023 DEBUG: fglrx.available: falling back to default
2011-06-26 21:52:39,123 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-06-26 21:52:39,124 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-06-26 21:52:39,184 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-06-26 21:52:39,185 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-06-26 21:52:39,185 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-06-26 21:52:39,195 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-06-26 21:52:39,197 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-06-26 21:52:39,197 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-06-26 21:52:39,197 DEBUG: all custom handlers loaded
2011-06-26 21:52:39,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'pci:v00008086d000027D8sv0000103Csd00003660bc04sc03i00')
2011-06-26 21:52:40,408 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 21:52:40,408 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-06-26 21:52:40,427 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 21:52:40,427 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-06-26 21:52:40,427 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-06-26 21:52:40,428 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00003660bc02sc00i00')
2011-06-26 21:52:40,459 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 21:52:40,460 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-06-26 21:52:40,460 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 21:52:40,461 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'platform:eisa')
2011-06-26 21:52:40,463 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-06-26 21:52:40,551 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-06-26 21:52:40,551 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 21:52:40,552 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-06-26 21:52:40,552 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'platform:pcspkr')
2011-06-26 21:52:40,554 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 21:52:40,554 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 21:52:40,555 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'pci:v00008086d00002448sv0000103Csd00003660bc06sc04i01')
2011-06-26 21:52:40,569 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'platform:hp-wmi')
2011-06-26 21:52:40,571 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-06-26 21:52:40,571 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'pci:v00008086d0000A011sv0000103Csd00003660bc03sc00i00')
2011-06-26 21:52:40,584 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 21:52:40,584 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2011-06-26 21:52:40,585 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'pci:v00008086d000027C8sv0000103Csd00003660bc0Csc03i00')
2011-06-26 21:52:40,596 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-06-26 21:52:40,597 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'pci:v00008086d0000A012sv0000103Csd00003660bc03sc80i00')
2011-06-26 21:52:40,608 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-06-26 21:52:40,609 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'pci:v00008086d000027C9sv0000103Csd00003660bc0Csc03i00')
2011-06-26 21:52:40,620 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-06-26 21:52:40,621 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'acpi:SYN1E18:PNP0F13:')
2011-06-26 21:52:40,621 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-06-26 21:52:40,623 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'option', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 21:52:40,623 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'pci:v00008086d000027CBsv0000103Csd00003660bc0Csc03i00')
2011-06-26 21:52:40,635 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2011-06-26 21:52:40,635 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 21:52:40,636 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'input:b0003v0408p0FF1e0104-e0,1,kD4,ramlsfw')
2011-06-26 21:52:40,636 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 21:52:40,637 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'usb:v0408p0FF1d0104dcEFdsc02dp01ic0Eisc02ip00')
2011-06-26 21:52:40,646 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2011-06-26 21:52:40,647 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 21:52:40,647 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'pci:v00008086d000027CAsv0000103Csd00003660bc0Csc03i00')
2011-06-26 21:52:40,659 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.11:bd03/19/2010:svnHewlett-Packard:pnHPMini210-1000:pvr04A3100000202100000300000:rvnHewlett-Packard:rn3660:rvr48.24:cvnHewlett-Packard:ct10:cvrN/A:')
2011-06-26 21:52:40,709 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'acpi:INT0800:')
2011-06-26 21:52:40,709 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-06-26 21:52:40,710 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 21:52:40,710 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'usb:v03F0p2A1Dd0349dcE0dsc01dp01icE0isc01ip01')
2011-06-26 21:52:40,768 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 21:52:40,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'usb:v03F0p2A1Dd0349dcE0dsc01dp01icFFiscFFipFF')
2011-06-26 21:52:40,771 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 21:52:40,771 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000103Csd0000365Ebc02sc80i00')
2011-06-26 21:52:41,200 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 21:52:40,933 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2011-06-26 21:52:41,201 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 21:52:41,460 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 21:52:41,202 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2011-06-26 21:52:41,461 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'b43', 'jockey_handler': 'KernelModuleHandler', 'package': 'firmware-b43-lpphy-installer'}
2011-06-26 21:52:41,461 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-06-26 21:52:41,462 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'pci:v00008086d000027DAsv0000103Csd00003660bc0Csc05i00')
2011-06-26 21:52:41,475 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 21:52:41,476 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'usb:v0408p0FF1d0104dcEFdsc02dp01ic0Eisc01ip00')
2011-06-26 21:52:41,478 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 21:52:41,478 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2011-06-26 21:52:41,479 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 21:52:41,479 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'pci:v00008086d000027C1sv0000103Csd00003660bc01sc06i01')
2011-06-26 21:52:41,491 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 21:52:41,491 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 21:52:41,491 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'pci:v00008086d000027CCsv0000103Csd00003660bc0Csc03i20')
2011-06-26 21:52:41,503 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'platform:reg-dummy')
2011-06-26 21:52:41,505 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2011-06-26 21:52:41,506 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 21:52:41,506 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-06-26 21:52:41,507 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'usb:v03F0p2A1Dd0349dcE0dsc01dp01icFEisc01ip01')
2011-06-26 21:52:41,509 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 21:52:41,509 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2011-06-26 21:52:41,510 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-06-26 21:52:41,511 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-06-26 21:52:41,543 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 21:52:41,543 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 21:52:41,544 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'pci:v00008086d000027BCsv0000103Csd00003660bc06sc01i00')
2011-06-26 21:52:41,555 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 21:52:41,556 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-06-26 21:52:41,556 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 21:52:41,557 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x86bcb0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-06-26 21:52:41,557 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'pci:v00008086d000027D8sv0000103Csd00003660bc04sc03i00')
2011-06-26 21:52:41,557 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-06-26 21:52:41,558 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-06-26 21:52:41,558 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-06-26 21:52:41,558 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00003660bc02sc00i00')
2011-06-26 21:52:41,558 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-06-26 21:52:41,559 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'platform:eisa')
2011-06-26 21:52:41,559 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-06-26 21:52:41,559 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-06-26 21:52:41,560 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-06-26 21:52:41,560 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'platform:pcspkr')
2011-06-26 21:52:41,560 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'pci:v00008086d00002448sv0000103Csd00003660bc06sc04i01')
2011-06-26 21:52:41,560 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'platform:hp-wmi')
2011-06-26 21:52:41,561 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-06-26 21:52:41,561 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'pci:v00008086d0000A011sv0000103Csd00003660bc03sc00i00')
2011-06-26 21:52:41,561 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2011-06-26 21:52:41,562 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'pci:v00008086d000027C8sv0000103Csd00003660bc0Csc03i00')
2011-06-26 21:52:41,562 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-06-26 21:52:41,562 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'pci:v00008086d0000A012sv0000103Csd00003660bc03sc80i00')
2011-06-26 21:52:41,562 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-06-26 21:52:41,563 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'pci:v00008086d000027C9sv0000103Csd00003660bc0Csc03i00')
2011-06-26 21:52:41,563 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-06-26 21:52:41,563 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'acpi:SYN1E18:PNP0F13:')
2011-06-26 21:52:41,563 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-06-26 21:52:41,564 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'pci:v00008086d000027CBsv0000103Csd00003660bc0Csc03i00')
2011-06-26 21:52:41,564 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2011-06-26 21:52:41,564 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'input:b0003v0408p0FF1e0104-e0,1,kD4,ramlsfw')
2011-06-26 21:52:41,565 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'usb:v0408p0FF1d0104dcEFdsc02dp01ic0Eisc02ip00')
2011-06-26 21:52:41,565 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2011-06-26 21:52:41,565 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'pci:v00008086d000027CAsv0000103Csd00003660bc0Csc03i00')
2011-06-26 21:52:41,565 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.11:bd03/19/2010:svnHewlett-Packard:pnHPMini210-1000:pvr04A3100000202100000300000:rvnHewlett-Packard:rn3660:rvr48.24:cvnHewlett-Packard:ct10:cvrN/A:')
2011-06-26 21:52:41,566 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'acpi:INT0800:')
2011-06-26 21:52:41,566 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-06-26 21:52:41,566 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'usb:v03F0p2A1Dd0349dcE0dsc01dp01icE0isc01ip01')
2011-06-26 21:52:41,567 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'usb:v03F0p2A1Dd0349dcE0dsc01dp01icFFiscFFipFF')
2011-06-26 21:52:41,567 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000103Csd0000365Ebc02sc80i00')
2011-06-26 21:52:41,567 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-06-26 21:52:41,567 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'pci:v00008086d000027DAsv0000103Csd00003660bc0Csc05i00')
2011-06-26 21:52:41,568 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'usb:v0408p0FF1d0104dcEFdsc02dp01ic0Eisc01ip00')
2011-06-26 21:52:41,568 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2011-06-26 21:52:41,568 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'pci:v00008086d000027C1sv0000103Csd00003660bc01sc06i01')
2011-06-26 21:52:41,568 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'pci:v00008086d000027CCsv0000103Csd00003660bc0Csc03i20')
2011-06-26 21:52:41,569 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'platform:reg-dummy')
2011-06-26 21:52:41,569 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2011-06-26 21:52:41,569 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-06-26 21:52:41,570 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'usb:v03F0p2A1Dd0349dcE0dsc01dp01icFEisc01ip01')
2011-06-26 21:52:41,570 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2011-06-26 21:52:41,570 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-06-26 21:52:41,570 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-06-26 21:52:41,571 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'pci:v00008086d000027BCsv0000103Csd00003660bc06sc01i00')
2011-06-26 21:52:41,571 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-06-26 21:52:41,571 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x86c730c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-06-26 21:52:41,938 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 21:52:42,448 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 21:52:42,956 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 21:52:43,460 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 21:52:43,777 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 21:52:44,280 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 21:52:47,177 DEBUG: Shutting down
2011-06-26 22:43:39,759 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c>
2011-06-26 22:43:45,465 DEBUG: reading modalias file /lib/modules/2.6.38-8-generic/modules.alias
2011-06-26 22:43:45,917 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-06-26 22:43:45,918 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-06-26 22:43:46,062 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-06-26 22:43:46,103 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-06-26 22:43:46,114 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-06-26 22:43:46,115 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-06-26 22:43:46,168 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-06-26 22:43:46,169 DEBUG: loading custom handler /usr/share/jockey/handlers/nouveau3d.py
2011-06-26 22:43:46,230 DEBUG: Instantiated Handler subclass __builtin__.Nouveau3DHandler from name Nouveau3DHandler
2011-06-26 22:43:46,231 DEBUG: Experimental 3D support for NVIDIA cards not available
2011-06-26 22:43:46,232 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-06-26 22:43:46,303 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-06-26 22:43:46,305 DEBUG: Firmware for DVB cards not available
2011-06-26 22:43:46,305 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-06-26 22:43:46,356 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-06-26 22:43:46,388 DEBUG: Software modem not available
2011-06-26 22:43:46,389 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-06-26 22:43:46,406 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-06-26 22:43:46,407 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-06-26 22:43:46,408 DEBUG: nvidia.available: falling back to default
2011-06-26 22:43:46,593 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-8 does not match X.org video ABI xorg-video-abi-10
2011-06-26 22:43:46,593 DEBUG: NVIDIA accelerated graphics driver not available
2011-06-26 22:43:46,602 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-06-26 22:43:46,603 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-06-26 22:43:46,604 DEBUG: nvidia.available: falling back to default
2011-06-26 22:43:46,715 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-06-26 22:43:46,716 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 947, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-06-26 22:43:46,725 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-06-26 22:43:46,726 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-06-26 22:43:46,727 DEBUG: nvidia.available: falling back to default
2011-06-26 22:43:46,829 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-06-26 22:43:46,830 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-06-26 22:43:46,843 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-06-26 22:43:46,844 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-06-26 22:43:46,844 DEBUG: fglrx.available: falling back to default
2011-06-26 22:43:46,954 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-06-26 22:43:46,955 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-06-26 22:43:47,013 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-06-26 22:43:47,014 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-06-26 22:43:47,014 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-06-26 22:43:47,024 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-06-26 22:43:47,026 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-06-26 22:43:47,026 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-06-26 22:43:47,027 DEBUG: all custom handlers loaded
2011-06-26 22:43:47,027 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'pci:v00008086d000027D8sv0000103Csd00003660bc04sc03i00')
2011-06-26 22:43:48,245 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 22:43:48,245 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-06-26 22:43:48,264 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 22:43:48,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-06-26 22:43:48,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-06-26 22:43:48,265 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00003660bc02sc00i00')
2011-06-26 22:43:48,296 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 22:43:48,297 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-06-26 22:43:48,297 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 22:43:48,298 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'platform:eisa')
2011-06-26 22:43:48,300 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-06-26 22:43:48,390 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-06-26 22:43:48,391 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 22:43:48,391 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-06-26 22:43:48,391 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'platform:pcspkr')
2011-06-26 22:43:48,393 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 22:43:48,394 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 22:43:48,394 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'pci:v00008086d00002448sv0000103Csd00003660bc06sc04i01')
2011-06-26 22:43:48,407 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'platform:hp-wmi')
2011-06-26 22:43:48,409 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-06-26 22:43:48,409 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'pci:v00008086d0000A011sv0000103Csd00003660bc03sc00i00')
2011-06-26 22:43:48,421 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 22:43:48,421 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2011-06-26 22:43:48,422 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'pci:v00008086d000027C8sv0000103Csd00003660bc0Csc03i00')
2011-06-26 22:43:48,433 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-06-26 22:43:48,434 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'pci:v00008086d0000A012sv0000103Csd00003660bc03sc80i00')
2011-06-26 22:43:48,445 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-06-26 22:43:48,446 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'pci:v00008086d000027C9sv0000103Csd00003660bc0Csc03i00')
2011-06-26 22:43:48,457 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-06-26 22:43:48,457 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'acpi:SYN1E18:PNP0F13:')
2011-06-26 22:43:48,458 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-06-26 22:43:48,460 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'option', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 22:43:48,460 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'pci:v00008086d000027CBsv0000103Csd00003660bc0Csc03i00')
2011-06-26 22:43:48,471 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2011-06-26 22:43:48,472 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 22:43:48,473 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'input:b0003v0408p0FF1e0104-e0,1,kD4,ramlsfw')
2011-06-26 22:43:48,473 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 22:43:48,473 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'usb:v0408p0FF1d0104dcEFdsc02dp01ic0Eisc02ip00')
2011-06-26 22:43:48,483 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2011-06-26 22:43:48,484 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 22:43:48,484 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'pci:v00008086d000027CAsv0000103Csd00003660bc0Csc03i00')
2011-06-26 22:43:48,495 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.11:bd03/19/2010:svnHewlett-Packard:pnHPMini210-1000:pvr04A3100000202100000300000:rvnHewlett-Packard:rn3660:rvr48.24:cvnHewlett-Packard:ct10:cvrN/A:')
2011-06-26 22:43:48,547 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'acpi:INT0800:')
2011-06-26 22:43:48,547 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-06-26 22:43:48,549 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 22:43:48,549 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'usb:v03F0p2A1Dd0349dcE0dsc01dp01icE0isc01ip01')
2011-06-26 22:43:48,607 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 22:43:48,607 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'usb:v03F0p2A1Dd0349dcE0dsc01dp01icFFiscFFipFF')
2011-06-26 22:43:48,610 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 22:43:48,610 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000103Csd0000365Ebc02sc80i00')
2011-06-26 22:43:48,778 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 22:43:48,777 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2011-06-26 22:43:48,779 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 22:43:48,780 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 22:43:48,780 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2011-06-26 22:43:48,781 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'b43', 'jockey_handler': 'KernelModuleHandler', 'package': 'firmware-b43-lpphy-installer'}
2011-06-26 22:43:48,781 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-06-26 22:43:48,781 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'pci:v00008086d000027DAsv0000103Csd00003660bc0Csc05i00')
2011-06-26 22:43:48,794 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 22:43:48,794 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'usb:v0408p0FF1d0104dcEFdsc02dp01ic0Eisc01ip00')
2011-06-26 22:43:48,796 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 22:43:48,796 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2011-06-26 22:43:48,797 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 22:43:48,797 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'pci:v00008086d000027C1sv0000103Csd00003660bc01sc06i01')
2011-06-26 22:43:48,809 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 22:43:48,809 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 22:43:48,810 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'pci:v00008086d000027CCsv0000103Csd00003660bc0Csc03i20')
2011-06-26 22:43:48,821 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'platform:reg-dummy')
2011-06-26 22:43:48,823 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2011-06-26 22:43:48,824 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 22:43:48,824 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-06-26 22:43:48,824 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'usb:v03F0p2A1Dd0349dcE0dsc01dp01icFEisc01ip01')
2011-06-26 22:43:48,826 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 22:43:48,827 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2011-06-26 22:43:48,827 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-06-26 22:43:48,829 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-06-26 22:43:48,860 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 22:43:48,860 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 22:43:48,860 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'pci:v00008086d000027BCsv0000103Csd00003660bc06sc01i00')
2011-06-26 22:43:48,872 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 22:43:48,873 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-06-26 22:43:48,873 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-06-26 22:43:48,873 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a35b0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-06-26 22:43:48,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'pci:v00008086d000027D8sv0000103Csd00003660bc04sc03i00')
2011-06-26 22:43:48,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-06-26 22:43:48,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-06-26 22:43:48,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-06-26 22:43:48,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00003660bc02sc00i00')
2011-06-26 22:43:48,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-06-26 22:43:48,876 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'platform:eisa')
2011-06-26 22:43:48,876 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-06-26 22:43:48,876 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-06-26 22:43:48,876 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-06-26 22:43:48,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'platform:pcspkr')
2011-06-26 22:43:48,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'pci:v00008086d00002448sv0000103Csd00003660bc06sc04i01')
2011-06-26 22:43:48,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'platform:hp-wmi')
2011-06-26 22:43:48,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-06-26 22:43:48,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'pci:v00008086d0000A011sv0000103Csd00003660bc03sc00i00')
2011-06-26 22:43:48,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2011-06-26 22:43:48,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'pci:v00008086d000027C8sv0000103Csd00003660bc0Csc03i00')
2011-06-26 22:43:48,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-06-26 22:43:48,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'pci:v00008086d0000A012sv0000103Csd00003660bc03sc80i00')
2011-06-26 22:43:48,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-06-26 22:43:48,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'pci:v00008086d000027C9sv0000103Csd00003660bc0Csc03i00')
2011-06-26 22:43:48,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-06-26 22:43:48,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'acpi:SYN1E18:PNP0F13:')
2011-06-26 22:43:48,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-06-26 22:43:48,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'pci:v00008086d000027CBsv0000103Csd00003660bc0Csc03i00')
2011-06-26 22:43:48,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2011-06-26 22:43:48,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'input:b0003v0408p0FF1e0104-e0,1,kD4,ramlsfw')
2011-06-26 22:43:48,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'usb:v0408p0FF1d0104dcEFdsc02dp01ic0Eisc02ip00')
2011-06-26 22:43:48,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2011-06-26 22:43:48,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'pci:v00008086d000027CAsv0000103Csd00003660bc0Csc03i00')
2011-06-26 22:43:48,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.11:bd03/19/2010:svnHewlett-Packard:pnHPMini210-1000:pvr04A3100000202100000300000:rvnHewlett-Packard:rn3660:rvr48.24:cvnHewlett-Packard:ct10:cvrN/A:')
2011-06-26 22:43:48,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'acpi:INT0800:')
2011-06-26 22:43:48,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-06-26 22:43:48,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'usb:v03F0p2A1Dd0349dcE0dsc01dp01icE0isc01ip01')
2011-06-26 22:43:48,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'usb:v03F0p2A1Dd0349dcE0dsc01dp01icFFiscFFipFF')
2011-06-26 22:43:48,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000103Csd0000365Ebc02sc80i00')
2011-06-26 22:43:48,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-06-26 22:43:48,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'pci:v00008086d000027DAsv0000103Csd00003660bc0Csc05i00')
2011-06-26 22:43:48,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'usb:v0408p0FF1d0104dcEFdsc02dp01ic0Eisc01ip00')
2011-06-26 22:43:48,885 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2011-06-26 22:43:48,885 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'pci:v00008086d000027C1sv0000103Csd00003660bc01sc06i01')
2011-06-26 22:43:48,885 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'pci:v00008086d000027CCsv0000103Csd00003660bc0Csc03i20')
2011-06-26 22:43:48,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'platform:reg-dummy')
2011-06-26 22:43:48,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2011-06-26 22:43:48,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-06-26 22:43:48,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'usb:v03F0p2A1Dd0349dcE0dsc01dp01icFEisc01ip01')
2011-06-26 22:43:48,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2011-06-26 22:43:48,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-06-26 22:43:48,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-06-26 22:43:48,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'pci:v00008086d000027BCsv0000103Csd00003660bc06sc01i00')
2011-06-26 22:43:48,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-06-26 22:43:48,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8a4024c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-06-26 22:43:49,001 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 22:43:49,324 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 22:43:49,422 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 22:44:00,724 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 22:44:05,315 DEBUG: unbind/rebind on driver /sys/module/wl/drivers/pci:wl: device 0000:02:00.0
2011-06-26 22:44:06,025 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 22:44:06,425 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 22:44:18,088 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 22:44:18,376 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 22:44:18,436 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 22:44:18,729 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 22:44:18,800 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 22:44:19,058 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 22:49:52,927 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 22:49:53,182 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 22:49:57,086 DEBUG: unbind/rebind on driver /sys/module/wl/drivers/pci:wl: device 0000:02:00.0
2011-06-26 22:49:57,660 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 22:49:58,005 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 22:50:06,074 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 22:50:06,340 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 22:50:06,379 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 22:50:06,633 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 22:50:06,733 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-06-26 22:50:06,996 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

```

I was saying some many pages back that I want to use the **b43** driver under **sta** driver in additional drivers.

Thanks

---

### Post by fox-mulder on 2011-06-26
some time back i edited the /etc/modprobe.d/blacklist.conf file

```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
# blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist wl

```

I edited 
```

blacklist bcm43xx

```

 to 

```

# blacklist bcm43xx

```

maybe I should undo it?

thanks

---

### Post by nm_geo on 2011-06-26
Fox the file you seek is blacklist-bcm43.conf.. It is still under etc/modprobe.d/  and it is the one created by the STA (wl) driver.

---

### Post by auftable on 2011-06-27
Joren, thanks, you are my hero! I think the defining factor was commenting the blacklists in [FONT=monospace]/etc/modprobe.d/broadcom-sta-common.conf .[/FONT][FONT=Verdana]I just needed to use firmware-b43-lpphy-installer instead of firmware-b43-installer, because I have the BCM4312 low power chip, (which does not sound very cool) and what I found out when I tried to install your package. It explicitly said "won't install, you have got the ... low power...".
Now it recognizes some wlan networks, need to test it tomorrow.[/FONT]

---

### Post by poltr1 on 2011-06-27
I have a Dell Latitude D620 laptop running natty.  I tried nearly everything in this and other related threads, and I still can't get wireless networking to work on this laptop.  I removed everything b43-related and bcmwl-related from synaptic, and used Additional Drivers to download the Broadcom STA wireless driver.  (Had to log in as root to activate it; recevied a "SystemError: installActive()f failed" message otherwise.) Even after rebooting, I don't see an "Enable Wireless" item in the Network menu.  

Oh yes, I checked the little wi-fi switch on the side.  It's on.

Here's output from lspci, lshw, and lsmod:
```

dvadmin@dvlt003:~$ lspci | grep work
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
dvadmin@dvlt003:~$ sudo lshw -C network
[sudo] password for dvadmin: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:43:63:f8
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=5752-v3.19 ip=192.168.2.100 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:efcf0000-efcfffff
dvadmin@dvlt003:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
joydev                 17322  0 
pcmcia                 39671  0 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
i915                  450944  3 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
yenta_socket           27230  0 
dell_laptop            13515  0 
pcmcia_rsrc            18292  1 yenta_socket
dell_wmi               12601  0 
drm_kms_helper         40745  1 i915
drm                   180037  4 i915,drm_kms_helper
snd_timer              28659  2 snd_pcm,snd_seq
wl                   2642531  0 
sparse_keymap          13666  1 dell_wmi
dcdbas                 14054  1 dell_laptop
psmouse                73312  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_algo_bit           13184  1 i915
serio_raw              12990  0 
lib80211               14570  1 wl
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
tg3                   131476  0 

```

---

### Post by nm_geo on 2011-06-27
> **poltr1 said:**
> I have a Dell Latitude D620 laptop running natty.  I tried nearly everything in this and other related threads, and I still can't get wireless networking to work on this laptop.  I removed everything b43-related and bcmwl-related from synaptic, and used Additional Drivers to download the Broadcom STA wireless driver.  (Had to log in as root to activate it; recevied a "SystemError: installActive()f failed" message otherwise.) Even after rebooting, I don't see an "Enable Wireless" item in the Network menu.  

Oh yes, I checked the little wi-fi switch on the side.  It's on.

Here's output from lspci, lshw, and lsmod:
```

dvadmin@dvlt003:~$ lspci | grep work
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
dvadmin@dvlt003:~$ sudo lshw -C network
[sudo] password for dvadmin: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:43:63:f8
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=5752-v3.19 ip=192.168.2.100 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:efcf0000-efcfffff
dvadmin@dvlt003:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
joydev                 17322  0 
pcmcia                 39671  0 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
i915                  450944  3 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
yenta_socket           27230  0 
dell_laptop            13515  0 
pcmcia_rsrc            18292  1 yenta_socket
dell_wmi               12601  0 
drm_kms_helper         40745  1 i915
drm                   180037  4 i915,drm_kms_helper
snd_timer              28659  2 snd_pcm,snd_seq
wl                   2642531  0 
sparse_keymap          13666  1 dell_wmi
dcdbas                 14054  1 dell_laptop
psmouse                73312  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_algo_bit           13184  1 i915
serio_raw              12990  0 
lib80211               14570  1 wl
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
tg3                   131476  0 

```

You may be in luck today poltr1..  I have the same laptop with the same wireless card and I have it running Luci, Maverick, Natty and testing Oneiric.  

Guess what I use the b43-fwcutter and the firmware-b43-installer.  That is all nothing else.

Now I see you have wl in the lsmod.  Let's go to Synaptic search on bcm remove all installed STA files and bcmwl-kernel-source.

Now I just did this earlier as an experiment so let's see what you get when you 

```
cd /etc/modprobe.d
ls

```paste the result here 

We are looking for two files possibly that we are going to remove (rm).. 
blacklist-bcm43.conf and maybe [FONT=monospace]broadcom-sta-common.conf[/FONT]

Then we will re-install the b43-fwcutter and the firmware-b43-installer.
Reboot and all is well

---

### Post by auftable on 2011-06-28
I can not connect to my university, user-authenticated networks with b43, BCM12-LP. Normal ones work (WPA2). The settings of the problematic network are "WPA & WPA2 Enterprise", Protected EAP (PEAP), MSCHAPv2, with a certificate.
Do you know any additional module that has to be installed or un-blacklisted for these networks?

---

### Post by poltr1 on 2011-06-28
> **nm_geo said:**
> Guess what I use the b43-fwcutter and the firmware-b43-installer.  That is all nothing else.

Now I see you have wl in the lsmod.  Let's go to Synaptic search on bcm remove all installed STA files and bcmwl-kernel-source.

Now I just did this earlier as an experiment so let's see what you get when you 

```
cd /etc/modprobe.d
ls

```paste the result here 

We are looking for two files possibly that we are going to remove (rm).. 
blacklist-bcm43.conf and maybe [FONT=monospace]broadcom-sta-common.conf[/FONT]

Then we will re-install the b43-fwcutter and the firmware-b43-installer.
Reboot and all is well

Per your suggestion, I installed b43-fwcutter and firmware-b43-installer, and removed bcmwl-kernel-source.

I didn't have any of those blacklist files you mentioned, but there was a "blacklist bcm43xx" line in blacklist.conf.  This has since been commented out.

Rebooted the laptop and I now have wireless connectivity.

Thank you, nm_geo!  This just made my day. :guitar:

---

### Post by Dillinger86 on 2011-06-30
Im new to Ubuntu and just installed 11.04 on this Acer Aspire 3000 and the wireless doesn't work is there a fix for this? or can I use whats been posted in these threads? I did a search and i found this thread. thank you.

Edit: man i have spent hours trying to figure this out. I installed bcml-kernal-source thing but my wireless card still will not start i have the Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller. this is way harder than I thought it would be.

---

### Post by westie457 on 2011-07-01
> **Dillinger86 said:**
> Im new to Ubuntu and just installed 11.04 on this Acer Aspire 3000 and the wireless doesn't work is there a fix for this? or can I use whats been posted in these threads? I did a search and i found this thread. thank you.

Edit: man i have spent hours trying to figure this out. I installed bcml-kernal-source thing but my wireless card still will not start i have the Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller. this is way harder than I thought it would be.

Hi and welcome to the Forum.

Use the guide n this Thread. The link is _[here]("http://ubuntuforums.org/showpost.php?p=10801185&postcount=240")_

You will need to install 'b43-fwcutter' and 'firmware-b43-installer'.

Enjoy

---

### Post by Dillinger86 on 2011-07-01
> **westie457 said:**
> Hi and welcome to the Forum.

Use the guide n this Thread. The link is _[here]("http://ubuntuforums.org/showpost.php?p=10801185&postcount=240")_

You will need to install 'b43-fwcutter' and 'firmware-b43-installer'.

Enjoy
thanks westie i appreciate the help

---

### Post by Dillinger86 on 2011-07-01
> Processing triggers for man-db ...
Setting up b43-fwcutter (1:013-3) ...
Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ...
Not supported card here (PCI id 14e4:4318)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ...
Not supported card here (PCI id 14e4:4318)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-lpphy-installer

 I have this error..I will do this until I get It right

---

### Post by Dillinger86 on 2011-07-02
EDIT!!! 
i did it i finally got my wireless to work.. by some help from the posters and my dumb luck but mostly from reading all these post....thanks to the community

---

### Post by franzmaximilian on 2011-07-02
I am new to the Broadcom 43xx cards problem and can't honestly go through 417 messages in this thread!

My case: 
brand new laptop equipped with a Broadcom Corporation BCM43225 802.11b/g/n (rev 01).
Kubuntu 11.04 Natty Live from CD connects flawlessly to wifi. Just give your password and the connection is strong and stable (tested on a WEP protected network).
Kubuntu 11.04 Natty installed on HD and updated (from official repositories only): the network card is not even seen by KNetwork Manager.
Followed instructions of post #1: Solution 1) gave no benefits.
Solution 2) fails to install the STA driver and suggests to look into /var/log/jockey.log 
I will try... but if anyone has already faced and solved the same problem please help me! 
Franz

---

### Post by westie457 on 2011-07-02
> **franzmaximilian said:**
> I am new to the Broadcom 43xx cards problem and can't honestly go through 417 messages in this thread!

My case: 
brand new laptop equipped with a Broadcom Corporation BCM43225 802.11b/g/n (rev 01).
Kubuntu 11.04 Natty Live from CD connects flawlessly to wifi. Just give your password and the connection is strong and stable (tested on a WEP protected network).
Kubuntu 11.04 Natty installed on HD and updated (from official repositories only): the network card is not even seen by KNetwork Manager.
Followed instructions of post #1: Solution 1) gave no benefits.
Solution 2) fails to install the STA driver and suggests to look into /var/log/jockey.log 
I will try... but if anyone has already faced and solved the same problem please help me! 
Franz

Hi take a look at _[this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")_

I am not 100% sure that the drivers for Ubuntu and Kubuntu are the same. If they are everything will be okay. In Synaptic do a search (not a quick-search) for bcm. In the resulting list will be 'broadcom-sta-common' and 'broadcom-sta-source'. Try one and if that does not work try the other remembering to reboot after installing. Also check the 'Additional Drivers' for any installed drivers that are activated. If there are any WIfi drivers listed de-activate them before trying the above.

---

### Post by Christie_k22 on 2011-07-02
I hate to be doing this but I am still having problems after countless hours spent trying to get my wireless running over the past 3 weeks. I have tried everything I have been able to find and still not working properly. I have reinstalled Ubuntu over 20 times . . . The best I can get is to get it to recognise the card and connect to my wireless network however once I try downloading something it gets to about 2% or so and all stops. Same thing happens if I continue browsing. I can browse for a few minutes without a problem but then it acts as if (though still connected) there is no net or even local. Again everything stops. I am no expert at this as I have only been using Ubuntu for about a year and a half and have had some issues but nothing ever this bad. I was able to sort it all out without too much trouble. I will include as much info as I can.

Desktop Computer - Dell Inspiron 530
Wireless Card - Linksys WMP300n
Wireless Router - WTR160n
OS - Ubuntu 11.04 64 Bit


```
lspci -


00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
02:00.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
02:00.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
02:01.0 Network controller: Broadcom Corporation BCM4321 802.11b/g/n (rev 01)

lshw -


WARNING: you should run this program as super-user.
parallelwanderings        
    description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3960MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     E7300  @ 2.66GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm cpufreq
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:c000(size=4096) memory:fdd00000-fddfffff ioport:d8000000(size=134217728)
           *-display:0
                description: VGA compatible controller
                product: RV370 5B60 [Radeon X300 (PCIE)]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:42 memory:d8000000-dfffffff ioport:ce00(size=256) memory:fddf0000-fddfffff memory:fdd00000-fdd1ffff
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV370 [Radeon X300SE]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: memory:fdde0000-fddeffff
        *-network
             description: Ethernet interface
             product: 82562V-2 10/100 Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 02
             serial: 00:21:9b:11:50:ca
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 firmware=1.1-2 latency=0 multicast=yes port=twisted pair
             resources: irq:41 memory:fdfc0000-fdfdffff memory:fdfff000-fdffffff ioport:ff00(size=32)
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:fe00(size=32)
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:fd00(size=32)
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:fc00(size=32)
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:fdffe000-fdffe3ff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:43 memory:fdff4000-fdff7fff
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:fb00(size=32)
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:fa00(size=32)
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:f900(size=32)
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fdffd000-fdffd3ff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 92
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:d000(size=4096) memory:fdc00000-fdcfffff ioport:fde00000(size=1048576)
           *-multimedia
                description: Multimedia audio controller
                product: SB Audigy
                vendor: Creative Labs
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2
                resources: irq:21 ioport:df00(size=64)
           *-firewire
                description: FireWire (IEEE 1394)
                product: SB Audigy FireWire Port
                vendor: Creative Labs
                physical id: 0.2
                bus info: pci@0000:02:00.2
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:22 memory:fdcff000-fdcff7ff memory:fdcf8000-fdcfbfff
           *-network
                description: Wireless interface
                product: BCM4321 802.11b/g/n
                vendor: Broadcom Corporation
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: wlan0
                version: 01
                serial: 00:22:6b:a0:a7:41
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.56+Linksys, A Division of Cisc ip=192.168.1.105 latency=64 multicast=yes wireless=IEEE 802.11g
                resources: irq:16 memory:fdcf4000-fdcf7fff
        *-isa
             description: ISA bridge
             product: 82801IR (ICH9R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f800(size=8) ioport:f700(size=4) ioport:f600(size=8) ioport:f500(size=4) ioport:f400(size=16) ioport:f300(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fdffc000-fdffc0ff ioport:500(size=32)
        *-ide:1
             description: IDE interface
             product: 82801I (ICH9 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f100(size=8) ioport:f000(size=4) ioport:ef00(size=8) ioport:ee00(size=4) ioport:ed00(size=16) ioport:ec00(size=16)
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

lsmod - 


Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
binfmt_misc            17565  1 
snd_hda_codec_realtek   336693  1 
snd_emu10k1_synth      17244  0 
snd_emux_synth         42834  1 snd_emu10k1_synth
snd_seq_virmidi        13525  1 snd_emux_synth
snd_seq_midi_emul      13706  1 snd_emux_synth
snd_emu10k1           156895  3 snd_emu10k1_synth
snd_ac97_codec        134270  1 snd_emu10k1
ac97_bus               12730  1 snd_ac97_codec
snd_hda_intel          33211  2 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_pcm                96625  4 snd_emu10k1,snd_ac97_codec,snd_hda_intel,snd_hda_codec
snd_util_mem           14074  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13604  3 snd_emux_synth,snd_emu10k1,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event     14899  2 snd_seq_virmidi,snd_seq_midi
radeon                982197  3 
snd_seq                61621  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
snd_timer              29602  3 snd_emu10k1,snd_pcm,snd_seq
ndiswrapper           249811  0 
snd_seq_device         14462  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    76664  1 radeon
joydev                 17606  0 
snd                    67382  21 snd_hda_codec_realtek,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_pcm,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                 14438  0 
drm_kms_helper         42136  1 radeon
psmouse                73535  0 
drm                   227495  5 radeon,ttm,drm_kms_helper
serio_raw              13166  0 
i2c_algo_bit           13400  1 radeon
soundcore              12680  1 snd
snd_page_alloc         18529  3 snd_emu10k1,snd_hda_intel,snd_pcm
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
hid_logitech           17693  0 
ff_memless             13097  1 hid_logitech
usbhid                 46956  1 hid_logitech
hid                    91020  2 hid_logitech,usbhid
firewire_ohci          40370  0 
usb_storage            53538  0 
firewire_core          62646  1 firewire_ohci
uas                    17996  0 
crc_itu_t              12707  1 firewire_core
floppy                 74120  0 
e1000e                159096  0 


```

---

### Post by westie457 on 2011-07-02
Hi refer to the post above yours. The answer is there with just a little bit of work from you. Different chip numbers with the same solution.

---

### Post by Christie_k22 on 2011-07-02
Ahhh thanks! last I checked was probably an hour or 2 b4 that post was up and when I posted I had been working for hours already and was trying to hurry to get out the door and didn't notice that one. I am home now and am going to get back to work on this hopefully that will work. I will let you all know!

---

### Post by Christie_k22 on 2011-07-02
So I tried it and the same thing ends up happening . . . net works for a few min then stops suddenly. However it seems to be going faster at least. Before I was only downloading at around 500kbs (or less) now it has peaked at 2.5mbs.

---

### Post by Dillinger86 on 2011-07-02
i wish I could help but i was just installing and uninstalling firmware and drivers until it worked. at one point i messed up Ubuntu and had to re-install it.

---

### Post by nm_geo on 2011-07-02
> **Christie_k22 said:**
> So I tried it and the same thing ends up happening . . . net works for a few min then stops suddenly. However it seems to be going faster at least. Before I was only downloading at around 500kbs (or less) now it has peaked at 2.5mbs.

Drop a ```
lsmod
``` from terminal for review Christie

---

### Post by Christie_k22 on 2011-07-02
Seems whatever it was I did before trying this then doing this what was on the post b4 my original one was half working I just reinstalled and the same thing again and Im getting nothing 
```
Module                  Size  Used by
wl                   2568244  0 
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
radeon                982197  3 
snd_hda_codec_realtek   336693  1 
ttm                    76664  1 radeon
drm_kms_helper         42136  1 radeon
snd_hda_intel          33211  2 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
psmouse                73535  0 
snd_emu10k1_synth      17244  0 
snd_emux_synth         42834  1 snd_emu10k1_synth
snd_seq_virmidi        13525  1 snd_emux_synth
snd_seq_midi_emul      13706  1 snd_emux_synth
snd_emu10k1           156895  3 snd_emu10k1_synth
drm                   227495  5 radeon,ttm,drm_kms_helper
snd_ac97_codec        134270  1 snd_emu10k1
i2c_algo_bit           13400  1 radeon
ac97_bus               12730  1 snd_ac97_codec
snd_util_mem           14074  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13604  3 snd_hda_codec,snd_emux_synth,snd_emu10k1
lib80211_crypt_tkip    17387  0 
dcdbas                 14438  0 
snd_seq_midi           13324  0 
snd_rawmidi            30486  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
lib80211               14991  2 wl,lib80211_crypt_tkip
snd_pcm                96625  4 snd_hda_intel,snd_hda_codec,snd_emu10k1,snd_ac97_codec
snd_seq_midi_event     14899  2 snd_seq_virmidi,snd_seq_midi
snd_page_alloc         18529  3 snd_hda_intel,snd_emu10k1,snd_pcm
snd_seq                61621  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
snd_timer              29602  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         14462  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  21 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
serio_raw              13166  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
joydev                 17606  0 
hid_logitech           17693  0 
ff_memless             13097  1 hid_logitech
usbhid                 46956  1 hid_logitech
hid                    91020  2 hid_logitech,usbhid
usb_storage            53538  0 
floppy                 74120  0 
uas                    17996  0 
e1000e                159096  0 
firewire_ohci          40370  0 
firewire_core          62646  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
```

---

### Post by Christie_k22 on 2011-07-03
I just recently talked to a fellow college student who has little knowledge of linux. He is primarily a mac user but knows some about windows as well. As we were talking he offered up an odd suggestion "well if it was working in the previous version why not go back to that" he said to me. So I tried it . . . Oddly enough it is working. I have been online for about an hour and a half w/o any problems what so ever. I simply installed the STA driver from the additional drivers (hardware drivers on this version) then restarted and it works. I tested with the same download I have been testing with for the past few weeks and it downloaded in about 6 min like it is supposed to. I guess for now I am going to stay with this version since a working computer is better than a non working one (being a college student). My little netbook just wasn't cutting it. Now if only I can get flash/java working right on this . . . But thats another issue for another time in another part of the forums. Thank you everyone for your help.

---

### Post by fknyeah on 2011-07-03
Updated to 11.04, now I have no wireless.  I have no access to a hardline connection.  Just wireless on a separate computer.

I'm getting an error when I attempt to fix it.  Error is as follows:

E: firmware-b43-lpphy-installer: subprocess installed post-installation script returned error exit status 1

---

### Post by fknyeah on 2011-07-03
> **fknyeah said:**
> Updated to 11.04, now I have no wireless.  I have no access to a hardline connection.  Just wireless on a separate computer.

I'm getting an error when I attempt to fix it.  Error is as follows:

E: firmware-b43-lpphy-installer: subprocess installed post-installation script returned error exit status 1

EDIT: Also this:

Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ... 
Not supported card here (PCI id 14e4:170 
14e4:4311)! 
Use proper b43 or b43legacy firmware. 
Aborting. 
dpkg: error processing firmware-b43-lpphy-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Errors were encountered while processing: 
 firmware-b43-lpphy-installer 
E: Sub-process /usr/bin/dpkg returned an error code (1) 
A package failed to install.  Trying to recover: 
Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ... 
Not supported card here (PCI id 14e4:170 
14e4:4311)! 
Use proper b43 or b43legacy firmware. 
Aborting. 
dpkg: error processing firmware-b43-lpphy-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Errors were encountered while processing: 
 firmware-b43-lpphy-installer

---

### Post by westie457 on 2011-07-03
> **fknyeah said:**
> EDIT: Also this:

Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ... 
Not supported card here (PCI id 14e4:170 
14e4:4311)! 
Use proper b43 or b43legacy firmware. 
Aborting. 
dpkg: error processing firmware-b43-lpphy-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Errors were encountered while processing: 
 firmware-b43-lpphy-installer 
E: Sub-process /usr/bin/dpkg returned an error code (1) 
A package failed to install.  Trying to recover: 
Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ... 
Not supported card here (PCI id 14e4:170 
14e4:4311)! 
Use proper b43 or b43legacy firmware. 
Aborting. 
dpkg: error processing firmware-b43-lpphy-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Errors were encountered while processing: 
 firmware-b43-lpphy-installer

Hi you need to remove the 'firmware-b43-lpphy-installer' and then install the 'firmware-b43-installer' package, this will automatically install the b43-fwcutter package if not already installed and then reboot.

---

### Post by fknyeah on 2011-07-03
I was able to do this, however I still cannot connect to any networks.

[SOLVED] through [http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/](http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/)

---

### Post by calmeilles on 2011-07-10
Okay, so thank you for the solution; installing bcmwl-kernel-source was the answer for 10.04 LTS and Broadcom BCM4311.

But it's very disappointing that any of this frustration was necessary.  The Fedora 15 Live CD just worked, no proprietary software nonsense. :confused: and :(

---

### Post by westie457 on 2011-07-10
Hi calmeilles just to let you know that if you upgrade from 10.04 to 10.10 or 11.04 your wifi will not work with your current drivers. You will have to install the following 2 packages either through Synaptic or in the terminal with 'sudo apt-get install' - b43-fwcutter and firmware-b43-installer are the right ones.
Who knows what will be needed for 11.10. Your guess will be as good as mine for that one.

have fun.

---

### Post by Knowledge-is-power on 2011-07-21
[SIZE=2]Hi,
  
I have a serious problem with my wireless...
my laptop has this realtek rtl8191sevb[/SIZE] NIC installed.
I've tryed everything to update it or... find any solutions available that solve my problems...
i keep coming across broadcom drivers and packages in the software center but these wont work for me will they?

 Please can someone help me find a solution for my realtek network card,  it keeps getting worse. now I cant even search for wireless networks as  they are blacked out... I'm really lost as I've only just started using  linux for the first time... I'm technically savvy in windows but I've dived into the  deep end with linux straight a way...

never in my life did i expect more problems then i get with windows...
i guess it's just the compatibility issues to be fair... 


Before i could connect to the router, but without INTERNET access... which to be frank is useless to me.
im writing this hooked up via Ethernet witch is a pain as it's down stairs in a hallway.


as my name suggests, Knowledge is power... and right now I am powerless.
Please, enlighten me!

I would be very greatful!

---

### Post by nm_geo on 2011-07-21
Knowledge 

Start a new thread below.. 

Provide results from these terminal commands; just copy and paste these in terminal  then do the same for results.

```
lspci -nn | greg 0280

```
```
sudo lshw -C network

```
```
lsmod
```

few helpers review these stickies

---

### Post by Mcjohnnson on 2011-07-22
Solved my WLAN issue with [this]("http://dickmcjohnnson.blogspot.com/2011/07/wifi-wlan-on-acer-travelmate-timeline-x.html").

options acer_wmi wireless=1 and blacklist brcm80211

---

### Post by jaway on 2011-07-23
After months of frustrations that wireless no longer worked after having upgraded my Lenovo S12 netbook to Natty, I finally managed to get it working.

Why the below procedure works no one knows. My theory, though, is that the very first restart after having activated the Broadcom STA driver sets some bits on the 43xx adapter, which are later misinterpreted by the rfkill utility. Thus, the driver believes that the adapter has been hardware blocked although this is not the case.

The procedure worked for me (Broadcom 4312 adapter in a Lenovo S12) but there's no guarantee it will work for others.

ja/

---------------------------------------------------

Make Broadcom 4312 wireless adapter work in Ubuntu 11.04, Natty, on Lenovo S12 netbook.
Don't bother with blacklisting in /etc/modprobe.d - it is done automatically and correctly.

1) Activate the STA driver through 'Additional Drivers'.
2) In a terminal window run 'rfkill list' (without the quotes) which probably shows:
   0: hci0: Bluetooth
          Soft blocked: no
          Hard blocked: no
   1: ideapad_wlan: Wireless LAN
          Soft blocked: no
          Hard blocked: no
   2: ideapad_bluetooth: Bluetooth
          Soft blocked: no
          Hard blocked: no
   3: brcmwl-0: Wireless LAN
          Soft blocked: no
          Hard blocked: yes  <<<=== !!!
   (If any soft blocking is shown, press the proper key combination - on the S12 it is <Fn-F5> - and rerun 'rfkill list'.)

3) Shutdown the laptop.
4) Remove any network cable.
5) Remove laptop battery.
6) Connect laptop to wall power outlet.

7) Find your Ubuntu live CD or USB stick.
8) Boot the live CD.
9) Select 'Try Ubuntu'.
10) In a terminal window run 'rfkill list' as outlined in 2) above until only hard blocking is shown. If no blocking at all is shown continue with 15).
11) Through 'Additional Drivers' remove the STA driver.
12) Still in 'Additional Drivers' activate the STA driver.
13) Close the 'Additional Drivers' window.
14) With 'rfkill list' check that no hard blocking is present.
15) Now, PULL THE POWER PLUG. Remember you removed the battery, so your laptop is powerwise now totally dead.

16) Remove the live CD device.
17) Put the battery back into the laptop and/or reconnect to wall outlet.
18) Boot the laptop as you usually do.

You should now have a working wireless connection through the STA driver. However, you may have to enable wireless through the Network Manager, and maybe reboot the laptop.

---------------------------------------------------

---

### Post by johnabdl on 2011-07-23
I banged my head against the wall with a Broadcom 4322 in a Dell Latitude e6500 for many weeks, trying almost everything on these forums. 

The driver for the Intel Ultimate N 633ANHMW is in the kernel from 2.6 up. 
I installed an Intel Ultimate N 633ANHMW a month ago and have had no problems with any wireless network, any wireless router, and the wireless connection is up as soon as you log on. 

You can find a new one for less than $40 easily, and for around $30 if you look around.

---

### Post by bayouoldguy on 2011-07-24
( Running a Dell D620 w/Windows Vista Business , works fine thru Windows/Linksys E2000 & can "hardwire" to the internet on a USB/Ubuntu stick load).

i tried to access & set up Ubuntu 11.04 & my wireless net. was not able to "enter" any terminal commands changing the wireless setups. If I re-booted, I lost the settings in the USB stick.
Saw all the problems of others trying to get Wireless up & came to this conclusion:
     I stopped trying to use the USB/Ubuntu 11.04 stick & went back and reloaded Ubuntu 10.04LTS. Was able to get up & running on Wireless after uninstalling "bcmwl-kerne--source" & "bcmwl-modaliases", then installing "b43-fwcutter", re-booting, configuring my Wireless SSID, Security as: WPA & WPA2 Personal & putting in the passcode. A re-boot started up the Wireless & showing ALL neighborhood nets !.
Therefore: I installed Ubuntu 10.04LTS on my Dell D620 until
the Ubuntu Team/users correct the Driver situation !..."G":)

---

### Post by homeuser1 on 2011-07-24
I put off upgrading to 11.04 until this weekend because I feared this problem.  Well, Ubuntu didn't let me down.  I upgraded this weekend to 11.04 and as soon as I restarted my Dell 600 laptop, I lost my wireless connection and can't get it back.

There are no drivers showing up in the Additional Drivers and both the b43-fwcutter and firmware-b43-installer are installed in the synaptic package manager.  

:(

---

### Post by garvinrick4 on 2011-07-28
[LEFT] Is your Dell SSID off: (via chilli555)

```
sudo rmmod -f dell-laptop
```
If works make permanent:
add to / etc /rc.local or [COLOR=#3465a4]/etc/modprobe.d/blacklist.conf[/COLOR]

```
rmmod -f dell-laptop
```[/LEFT]

---

### Post by jplyons on 2011-07-29
Re: Ubuntu 11.04 install wireless detect problem

Hi,
I am working with my broadcom bcm4311 802.11b/g wlan driver because it
is losing its detection of my wireless router.

I have success when I do the following:

Remove these (below) using synaptic package manager.
b43-fwcutter
bcmwl-kernal-source
firmware-b43-installer

I then reboot.
I then re-install...
b43-fwcutter
bcmwl-kernal-source
firmware-b43-installer

Now all nearby wireless networks are detected. I just connect to mine
and it works!

Then I shut down. When I reboot wireless networks are gone!
If I do the above steps all over again, wireless comes back.

I lose it every time I re-boot after a successful install.
What is happening? Is there a login script I need to modify?

Where is the 11.04 login script.

Thank you for any help.
Joe

jplyons is online now Report Post   	Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message
Re: Ubuntu 11.04 install wireless detect problem

---

### Post by bkratz on 2011-07-29
> **jplyons said:**
> Re: Ubuntu 11.04 install wireless detect problem

Hi,
I am working with my broadcom bcm4311 802.11b/g wlan driver because it
is losing its detection of my wireless router.

I have success when I do the following:

Remove these (below) using synaptic package manager.
b43-fwcutter
bcmwl-kernal-source
firmware-b43-installer

I then reboot.
I then re-install...
b43-fwcutter
bcmwl-kernal-source
firmware-b43-installer

Now all nearby wireless networks are detected. I just connect to mine
and it works!

Then I shut down. When I reboot wireless networks are gone!
If I do the above steps all over again, wireless comes back.

I lose it every time I re-boot after a successful install.
What is happening? Is there a login script I need to modify?

Where is the 11.04 login script.

Thank you for any help.
Joe

jplyons is online now Report Post   	Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message
Re: Ubuntu 11.04 install wireless detect problem

when you first reboot do a

```
lsmod
``` 

and see if b43 is there or not, if not you should be able to force it to start at boot with

```
sudo su
echo b43 >> /etc/modules
exit
```

Which will add it to start up.

then reboot and recheck lsmod

it should be there and you should have wireless

---

### Post by westie457 on 2011-07-29
> **jplyons said:**
> Re: Ubuntu 11.04 install wireless detect problem

Hi,
I am working with my broadcom bcm4311 802.11b/g wlan driver because it
is losing its detection of my wireless router.

I have success when I do the following:

Remove these (below) using synaptic package manager.
b43-fwcutter
bcmwl-kernal-source
firmware-b43-installer

I then reboot.
I then re-install...
b43-fwcutter
bcmwl-kernal-source
firmware-b43-installer

Now all nearby wireless networks are detected. I just connect to mine
and it works!

Then I shut down. When I reboot wireless networks are gone!
If I do the above steps all over again, wireless comes back.

I lose it every time I re-boot after a successful install.
What is happening? Is there a login script I need to modify?

Where is the 11.04 login script.

Thank you for any help.
Joe

jplyons is online now Report Post   	Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message
Re: Ubuntu 11.04 install wireless detect problem

Hi you are so very close to the solution.
The problem in your case is 'bcmwl-kernel-source'. Remove that and reboot. Your wireless will work straight away.

---

### Post by jplyons on 2011-07-29
Hello Westie457 and thank you. Removing bcmwl-kernel-source worked.
Joe

---

### Post by NinoRode on 2011-07-30
Hello, my first post...

I have a similar problem as [jplyons]("http://ubuntuforums.org/member.php?u=488336"), however I have connection only on fresh install of 11.04 and never egain (yes, Iinstalled it 3 times, wireless works every time until I shut down or reboot...)

Alittle bit of history:

I have Acer Extensa 5220 with bcm4311 (rev1) chip. It worked fine under 10.10 with b43 driver. With 11.04 it stopped.

I'm not a newbie really, but a simple user. Nevertheless in last months I learned quite a bit about the kernel modules and stuff.

I've tried EVERYTHING I found on the forums with no real sucess.

So:

STA driver doesn't work for me.
b43 works good once per instalation. After reboot it still installs, the wireless card is recognised, ifconfig turns it on, iwconfig finds it, iwlist scannes my wireless network... However there was no way to persuade the card to connect.

Can anyone make sense of this?

I'm desperate.

---

### Post by westie457 on 2011-07-30
> **NinoRode said:**
> Hello, my first post...

I have a similar problem as [jplyons]("http://ubuntuforums.org/member.php?u=488336"), however I have connection only on fresh install of 11.04 and never egain (yes, Iinstalled it 3 times, wireless works every time until I shut down or reboot...)

Alittle bit of history:

I have Acer Extensa 5220 with bcm4311 (rev1) chip. It worked fine under 10.10 with b43 driver. With 11.04 it stopped.

I'm not a newbie really, but a simple user. Nevertheless in last months I learned quite a bit about the kernel modules and stuff.

I've tried EVERYTHING I found on the forums with no real sucess.

So:

STA driver doesn't work for me.
b43 works good once per instalation. After reboot it still installs, the wireless card is recognised, ifconfig turns it on, iwconfig finds it, iwlist scannes my wireless network... However there was no way to persuade the card to connect.

Can anyone make sense of this?

I'm desperate.

Follow this link [http://ubuntuforums.org/showpost.php?p=10798351&postcount=234](http://ubuntuforums.org/showpost.php?p=10798351&postcount=234)

---

### Post by NinoRode on 2011-07-31
Followed the link, didn't find anything new.

Then I decided to systematically install and test every driver available.

[LEFT]The newest one: bcmwl-kernel-source 5.100.82.38+bdcom-0ubuntu3 didn't even recognise the card:
[/LEFT]

       [LEFT]root@nino-Extensa-5220:/home/nino# modprobe -r b43 ssb wl[/LEFT]
    [LEFT]root@nino-Extensa-5220:/home/nino# modprobe wl[/LEFT]
    [LEFT]root@nino-Extensa-5220:/home/nino# iwconfig[/LEFT]
    [LEFT]lo        no wireless extensions.[/LEFT]
        [LEFT]eth0      no wireless extensions.[/LEFT]
        [LEFT]irda0     no wireless extensions.[/LEFT]
        [LEFT]ppp0      no wireless extensions.


Previous broadcom-sta-common 5.60.48.36-3 saw the card, but I couldn't wake it up:
[LEFT] 
nino@nino-Extensa-5220:~$ sudo su[/LEFT]
    [LEFT][sudo] password for nino: [/LEFT]
    [LEFT]root@nino-Extensa-5220:/home/nino# iwconfig[/LEFT]
    [LEFT]lo        no wireless extensions.[/LEFT]
        [LEFT]eth0      no wireless extensions.[/LEFT]
        [LEFT]irda0     no wireless extensions.[/LEFT]
        [LEFT]wlan0     IEEE 802.11bg  ESSID: off/any  [/LEFT]
    [LEFT]          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   [/LEFT]
    [LEFT]          Retry  long limit:7   RTS thr: off   Fragment thr: off[/LEFT]
    [LEFT]          Encryption key: off[/LEFT]
    [LEFT]          Power Management: off[/LEFT]
        [LEFT]ppp0      no wireless extensions.[/LEFT]
        [LEFT]root@nino-Extensa-5220:/home/nino# iwlist scan[/LEFT]
    [LEFT]lo        Interface doesn't support scanning.[/LEFT]
        [LEFT]eth0      Interface doesn't support scanning.[/LEFT]
        [LEFT]irda0     Interface doesn't support scanning.[/LEFT]
        [LEFT]wlan0     Interface doesn't support scanning : Network is down[/LEFT]
        [LEFT]ppp0      Interface doesn't support scanning.[/LEFT]
    root@nino-Extensa-5220:/home/nino# ifconfig wlan0 up    [LEFT]SIOCSIFFLAGS: No such file or directory[/LEFT]
    [LEFT]root@nino-Extensa-5220:/home/nino# man ifconfig[/LEFT]

[/LEFT]

The only driver working was the b43 (firmware- b43-installler)

root@nino-Extensa-5220:/home/nino# iwconfig

 lo        no wireless extensions. 
     
    eth0      no wireless extensions. 
     
    wlan0     IEEE 802.11bg  ESSID: off/any   
              Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm    
              Retry  long limit:7   RTS thr: off   Fragment thr: off 
              Encryption key: off 
              Power Management: off 
               
    irda0     no wireless extensions. 
     
    root@nino-Extensa-5220:/home/nino# ifconfig wlan0 up 
    root@nino-Extensa-5220:/home/nino# iwconfig 
    lo        no wireless extensions. 
     
    eth0      no wireless extensions. 
     
    wlan0     IEEE 802.11bg  ESSID: off/any   
              Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm    
              Retry  long limit:7   RTS thr: off   Fragment thr: off 
              Encryption key: off 
              Power Management: off 
               
    irda0     no wireless extensions. 
     
    root@nino-Extensa-5220:/home/nino# iwlist scan 
    lo        Interface doesn't support scanning. 
     
    eth0      Interface doesn't support scanning. 
     
    wlan0     Scan completed : 
              Cell 01 - Address: 02:30:B4:65:F7:80 
                        Channel:6 
                        Frequency:2.437 GHz (Channel 6) 
                        Quality=67/70  Signal level=-43 dBm   
                        Encryption key: on 
                        ESSID:"HomeWire" 
                        Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s 
                        Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s 
                                  36 Mb/s; 48 Mb/s; 54 Mb/s 
                        Mode:Master 
                        Extra:tsf=0000013f903a41f2 
                        Extra: Last beacon: 452ms ago 
                        IE: Unknown: 0008486F6D6557697265 
                        IE: Unknown: 010482848B96 
                        IE: Unknown: 030106 
                        IE: Unknown: 070A555320010B1E010B1E00 
                        IE: Unknown: 2A0100 
                        IE: Unknown: 32080C1218243048606C 
                        IE: IEEE 802.11i/WPA2 Version 1 
                            Group Cipher : TKIP 
                            Pairwise Ciphers (1) : TKIP 
                            Authentication Suites (1) : PSK 
                           Preauthentication Supported 
                        IE: Unknown: DD050010910400 
     
    irda0     Interface doesn't support scanning. 



However Network manager didn't recognise it (I don't know how and why it recognises it on fresh install). I then installed wicd which did the trick. Now things work.

I'm sorry, it really did look like a wirelles driver problem.

Do you happen to know if there is a Network manager thread or forum so I can discuss the issue with them?


Thanks for everything.

---

### Post by westie457 on 2011-07-31
> **NinoRode said:**
> Followed the link, didn't find anything new.

Then I decided to systematically install and test every driver available.

[LEFT]The newest one: bcmwl-kernel-source 5.100.82.38+bdcom-0ubuntu3 didn't even recognise the card:
[/LEFT]

       [LEFT]root@nino-Extensa-5220:/home/nino# modprobe -r b43 ssb wl[/LEFT]
    [LEFT]root@nino-Extensa-5220:/home/nino# modprobe wl[/LEFT]
    [LEFT]root@nino-Extensa-5220:/home/nino# iwconfig[/LEFT]
    [LEFT]lo        no wireless extensions.[/LEFT]
        [LEFT]eth0      no wireless extensions.[/LEFT]
        [LEFT]irda0     no wireless extensions.[/LEFT]
        [LEFT]ppp0      no wireless extensions.


Previous broadcom-sta-common 5.60.48.36-3 saw the card, but I couldn't wake it up:
[LEFT] 
nino@nino-Extensa-5220:~$ sudo su[/LEFT]
    [LEFT][sudo] password for nino: [/LEFT]
    [LEFT]root@nino-Extensa-5220:/home/nino# iwconfig[/LEFT]
    [LEFT]lo        no wireless extensions.[/LEFT]
        [LEFT]eth0      no wireless extensions.[/LEFT]
        [LEFT]irda0     no wireless extensions.[/LEFT]
        [LEFT]wlan0     IEEE 802.11bg  ESSID: off/any  [/LEFT]
    [LEFT]          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   [/LEFT]
    [LEFT]          Retry  long limit:7   RTS thr: off   Fragment thr: off[/LEFT]
    [LEFT]          Encryption key: off[/LEFT]
    [LEFT]          Power Management: off[/LEFT]
        [LEFT]ppp0      no wireless extensions.[/LEFT]
        [LEFT]root@nino-Extensa-5220:/home/nino# iwlist scan[/LEFT]
    [LEFT]lo        Interface doesn't support scanning.[/LEFT]
        [LEFT]eth0      Interface doesn't support scanning.[/LEFT]
        [LEFT]irda0     Interface doesn't support scanning.[/LEFT]
        [LEFT]wlan0     Interface doesn't support scanning : Network is down[/LEFT]
        [LEFT]ppp0      Interface doesn't support scanning.[/LEFT]
    root@nino-Extensa-5220:/home/nino# ifconfig wlan0 up    [LEFT]SIOCSIFFLAGS: No such file or directory[/LEFT]
    [LEFT]root@nino-Extensa-5220:/home/nino# man ifconfig[/LEFT]

[/LEFT]

The only driver working was the b43 (firmware- b43-installler)

root@nino-Extensa-5220:/home/nino# iwconfig

 lo        no wireless extensions. 
     
    eth0      no wireless extensions. 
     
    wlan0     IEEE 802.11bg  ESSID: off/any   
              Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm    
              Retry  long limit:7   RTS thr: off   Fragment thr: off 
              Encryption key: off 
              Power Management: off 
               
    irda0     no wireless extensions. 
     
    root@nino-Extensa-5220:/home/nino# ifconfig wlan0 up 
    root@nino-Extensa-5220:/home/nino# iwconfig 
    lo        no wireless extensions. 
     
    eth0      no wireless extensions. 
     
    wlan0     IEEE 802.11bg  ESSID: off/any   
              Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm    
              Retry  long limit:7   RTS thr: off   Fragment thr: off 
              Encryption key: off 
              Power Management: off 
               
    irda0     no wireless extensions. 
     
    root@nino-Extensa-5220:/home/nino# iwlist scan 
    lo        Interface doesn't support scanning. 
     
    eth0      Interface doesn't support scanning. 
     
    wlan0     Scan completed : 
              Cell 01 - Address: 02:30:B4:65:F7:80 
                        Channel:6 
                        Frequency:2.437 GHz (Channel 6) 
                        Quality=67/70  Signal level=-43 dBm   
                        Encryption key: on 
                        ESSID:"HomeWire" 
                        Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s 
                        Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s 
                                  36 Mb/s; 48 Mb/s; 54 Mb/s 
                        Mode:Master 
                        Extra:tsf=0000013f903a41f2 
                        Extra: Last beacon: 452ms ago 
                        IE: Unknown: 0008486F6D6557697265 
                        IE: Unknown: 010482848B96 
                        IE: Unknown: 030106 
                        IE: Unknown: 070A555320010B1E010B1E00 
                        IE: Unknown: 2A0100 
                        IE: Unknown: 32080C1218243048606C 
                        IE: IEEE 802.11i/WPA2 Version 1 
                            Group Cipher : TKIP 
                            Pairwise Ciphers (1) : TKIP 
                            Authentication Suites (1) : PSK 
                           Preauthentication Supported 
                        IE: Unknown: DD050010910400 
     
    irda0     Interface doesn't support scanning. 



However Network manager didn't recognise it (I don't know how and why it recognises it on fresh install). I then installed wicd which did the trick. Now things work.

I'm sorry, it really did look like a wirelles driver problem.

Do you happen to know if there is a Network manager thread or forum so I can discuss the issue with them?


Thanks for everything.
Only one point to make here.

STOP RUNNING YOUR SYSTEM AS ROOT.

It is not recommended at all

Everything you have done was on the wrong account. It should have been done in your user account. When things are installed with the user account they get installed with the right settings and stay set. Running your system as root is very dangerous to your computer.

---

### Post by blfang on 2011-08-04
After trying various solutions in this thread and others, I still cannot connect to my wireless network. I can see the available networks, but just cannot connect.

MacBook Pro
Broadcom: BCM43224
driver: brcm80211

installed:
firmware-b43-installer
b43-fwcutter
bcmwl-kernel-source (removing this did not solve the problem)

```
~$ lsmod
Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
vesafb                 13761  1 
arc4                   12529  2 
brcm80211             748941  0 
snd_hda_codec_hdmi     28167  4 
rfcomm                 47694  8 
sco                    18187  2 
bnep                   18308  2 
l2cap                  53570  16 rfcomm,bnep
binfmt_misc            17565  1 
mac80211              294370  1 brcm80211
snd_hda_codec_cirrus    18774  1 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
uvcvideo               72195  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17606  0 
nvidia              10709116  43 
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
applesmc               19604  0 
input_polldev          14007  1 applesmc
btusb                  18600  2 
bluetooth              72320  9 rfcomm,sco,bnep,l2cap,btusb
bcm5974                17396  0 
cfg80211              178528  2 brcm80211,mac80211
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_ips              18097  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19438  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
hid_apple              13324  0 
usb_storage            53538  0 
uas                    17996  0 
usbhid                 46956  0 
hid                    91020  2 hid_apple,usbhid
firewire_ohci          40370  0 
firewire_core          62646  1 firewire_ohci
tg3                   141750  0 
crc_itu_t              12707  1 firewire_core


``````
*-network
       description: Wireless interface
       product: BCM43224 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 60:33:4b:21:3a:7a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcm80211 driverversion=2.6.38-10-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:c1b00000-c1b03fff
```Thanks in advance!

---

### Post by f.constantino on 2011-08-05
Hello guys, 

first of all I apologize if I'm posting this in the wrong place, but I've made a topic and nobody answered and I'm really getting desperate.

Can someone tell me if Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01) is capable of working as an access point ? 

I haven't been able to find out if the card doesn't support it at all, or if I need some kind of new drivers, but I've tried a lot of different solutions and still can't get this working...

Any help would be greatly appreciated!

---

### Post by bayouoldguy on 2011-08-08
Re: Dell Latitude D600 Problem
Look what I found !....

[url]https://launchpad.net/ubuntu/maverick/i386/firmware-b43-installer
 & listed file:

firmware-b43-installer_4.150.10.5-4_all.deb (5.1 KiB)

I downloaded the file to the "Downloads" folder, & commanded to "extract".
It installed.....found my Wireless & is up & running from the USB stick !!.
I installed the b43-fwcutter package from the Synaptic Package manager first. The wireless apt always showed me "no firmware", & the "apt-get install firmware-b43-installer" command would not execute.

Now I guess I can upgrade to the 11.04 version !......"G"

All you guys having Dell D6XX series laptops with the Broadcom BCM4311
802.11 b/g Wlan wireless card may want to try this......
__________________

---

### Post by KemKev on 2011-08-10
OK...over the past two days I have read through every post in this thread and tried just about everything, but no luck.  I hope someone can point me in the right direction.

Started thread [http://ubuntuforums.org/showthread.php?p=11142113#post11142113]("http://ubuntuforums.org/showthread.php?p=11142113#post11142113")

---

### Post by wiz-oz on 2011-08-11
I own a hp6710b laptop that has a wireless card bios check. This means for wireless-n I am forced to use either an intel wag4965 (currently in the laptop) or a broadcom bcm94321MC. Getting that to run with wireless n is a nightmare, and I seriously doubt if the drivers for the intel ever will work.

So I am kind of looking into buying a broadcom BCM94321MC wireless card to see if this would work. Reading all this thread kind of makes me wonder if I could connect to a wireless N network reliably and with decent speed when the laptop runs lucid?

Anyone using mentioned card in a laptop that can confirm it works great? It would spare me from buying a card and then find out it will not work either.

Thanks for any help on this.

cheers,

wiz

---

### Post by battery_burner on 2011-08-12
Sorry if this is very basic but it might help someone. I noticed that when building a new hdd in a D400 (which had a working wireless connection with the old hdd 8.04) that for some reason the wireless function was turned off, to make it work on 11.04 all I had to do was press Function+F2 (there was no real clue to this being the cause of no wireless connection or why a new install should deactivate the WIFI on the laptop).

---

### Post by brantpadams on 2011-08-13
> **bkratz said:**
> when you first reboot do a

```
lsmod
``` 

and see if b43 is there or not, if not you should be able to force it to start at boot with

```
sudo su
echo b43 >> /etc/modules
exit
```

Which will add it to start up.

then reboot and recheck lsmod

it should be there and you should have wireless

This fixed my wireless problem. I almost feel embarrassed that it was so simple. Thanks a ton!

---

### Post by brantpadams on 2011-08-14
Regretfully, I have to retract my last statement. The script worked fine for a whole day until just recently my wireless card stopped scanning networks and now won't connect. I'm really frustrated that I can't figure out what the problem is. Currently, when I click on the wireless applet it reads that the driver is missing to activate. It doesn't make sense because I've installed every driver I can think of and I'm still not getting a fix. Here's the results of my last attempt:

> brant@brant-Inspiron-1525:~$ lspci -vvnn | grep 14e4
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
brant@brant-Inspiron-1525:~$ sudo apt-get install firmware-b43-installer
[sudo] password for brant: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  b43-fwcutter
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer
0 upgraded, 2 newly installed, 0 to remove and 68 not upgraded.
Need to get 0 B/18.2 kB of archives.
After this operation, 131 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package b43-fwcutter.
(Reading database ... 188270 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a013-3_i386.deb) ...
Selecting previously deselected package firmware-b43-installer.
Unpacking firmware-b43-installer (from .../firmware-b43-installer_4.150.10.5-5_all.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:013-3) ...
Setting up firmware-b43-installer (4.150.10.5-5) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
[B]dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-installer[/B]
E: Sub-process /usr/bin/dpkg returned an error code (1)
This happens every time I attempt the installation. Why then would my wireless work *some* of the time if the drivers aren't installed properly? 

I'm on a Dell Inspiron 1525 with a Broadcom BCM4312. If anyone can enlighten me as to what I should do I would be most grateful. 

Just to expand, after I had freshly installed 11.04, my wireless was working better than ever and I'd really like to keep that going. I'm currently running over ethernet.

EDIT:
The wireless applet reads "device not ready (firmware missing)" when clicked on.

---

### Post by westie457 on 2011-08-14
> **brantpadams said:**
> Regretfully, I have to retract my last statement. The script worked fine for a whole day until just recently my wireless card stopped scanning networks and now won't connect. I'm really frustrated that I can't figure out what the problem is. Currently, when I click on the wireless applet it reads that the driver is missing to activate. It doesn't make sense because I've installed every driver I can think of and I'm still not getting a fix. Here's the results of my last attempt:


This happens every time I attempt the installation. Why then would my wireless work *some* of the time if the drivers aren't installed properly? 

I'm on a Dell Inspiron 1525 with a Broadcom BCM4312. If anyone can enlighten me as to what I should do I would be most grateful. 

Just to expand, after I had freshly installed 11.04, my wireless was working better than ever and I'd really like to keep that going. I'm currently running over ethernet.

EDIT:
The wireless applet reads "device not ready (firmware missing)" when clicked on.

You were so close to the solution. Use firmware-b43-lpphy-installer instead of firmware-b43-installer. Then a quick reboot, click on network manager to see available networks. Choose yours enter some details as needed and away you go.

---

### Post by brantpadams on 2011-08-14
> **westie457 said:**
> You were so close to the solution. Use firmware-b43-lpphy-installer instead of firmware-b43-installer. Then a quick reboot, click on network manager to see available networks. Choose yours enter some details as needed and away you go.
Again, embarrassed by how easy that was. #-o
Thank you very much for your help. Although I could have sworn I already did that before...

---

### Post by wilfredt on 2011-08-21
I hate to ask the whole question again , but I have tried several time and followed all the steps , but still I am not able to use wireless on my 11.04 , The card is bcm 4312 and I have installed latest bcm kernel source .it seems to work for most of the people but I cant still find it working .
I can see the driver is active in additona hardware drivers .
It has been months I tried diffrent things with no help , I had some scripts in earlier version which did the job 
but those seem not to be working in 11.04 .

Please help me out :(

---

### Post by westie457 on 2011-08-21
> **wilfredt said:**
> I hate to ask the whole question again , but I have tried several time and followed all the steps , but still I am not able to use wireless on my 11.04 , The card is bcm 4312 and I have installed latest bcm kernel source .it seems to work for most of the people but I cant still find it working .
I can see the driver is active in additona hardware drivers .
It has been months I tried diffrent things with no help , I had some scripts in earlier version which did the job 
but those seem not to be working in 11.04 .

Please help me out :(

Hi the following will sort your wireless.


I also had this problem of wireless not working with the Broadcom STA Wireless driver after up-grading to 'Natty Narwhal' on my Acer laptop with a Broadcom 4311 wifi module. A big thank you to all who posted before me even though the suggestions put forward did not work. However I found a work around this problem and I hope others may find it useful.
The solution in my case worked using a network cable and 'Synaptic Package Manager'. This is what I did:-
1) In Additional drivers I de-activated the STA driver
2) In 'Synaptic' I then removed them completely.
3) Went back into Synaptic and found 'b43-fwcutter' and 'firmware-b43-installer'. I installed both packages because I was not sure which one was needed.
4) After a reboot wireless signed in to the router and the cable removed

Change the firmware-b43-installer to firmware-b43-lpphy-installer.

---

### Post by wilfredt on 2011-08-21
Thanks westie ,
 I tried the steps , found out a new issue that wireless is disabled by hardware switch 
 Then I tried to remove all the hardware and software blocks .

lsmod | grep dell If *dell-laptop* is loaded, remove it: 	Code:
 	sudo rmmod -f dell-laptop sudo rfkill unblock all 
But still the network manager shows wireless is disabled by hardware switch
and no sign of wireless being detected

---

### Post by westie457 on 2011-08-21
> **wilfredt said:**
> Thanks westie ,
 I tried the steps , found out a new issue that wireless is disabled by hardware switch 
 Then I tried to remove all the hardware and software blocks .

lsmod | grep dell If *dell-laptop* is loaded, remove it: 	Code:
 	sudo rmmod -f dell-laptop sudo rfkill unblock all 
But still the network manager shows wireless is disabled by hardware switch
and no sign of wireless being detected

Try turning it on via the hardware switch or a combination of keys (the Fn key+F2)usually works for Dell laptops. Or there might be a setting in the BIOS.

---

### Post by Tshann on 2011-08-29
Hi,
  I went through a great deal to try to get this puppy to work in Kubuntu 11.04. The final solution - for my rig (HP DV6233se) was to uninstall the bcmwl-kernel-source. I did confirm that the bcm43xx was blacklisted and removed the blacklist - didn't work. No fix on the broadcom sta driver ever worked. But after installing firmware-b43-installer (which automatically brought in cutter) I could get it to work, but I had to log into a terminal every time @ boot up and type in sudo modprobe b43. It was only after removing the above source file and rebooting that my rig came up with a working wireless for Kubuntu 11.04. Hope this is useful for someone else.

Peace

---

### Post by northd_tech on 2011-08-30
For those with Broadcom wireless troubles, I have posted a Broadcom troubleshooting chart and some VERY helpful links at posts #9 & 10 on this thread:

**THE beginners solution for fixing up Broadcom BCM43xx and Wireless Cards**
[http://ubuntuforums.org/showthread.php?p=11203404#post11203404](http://ubuntuforums.org/showthread.php?p=11203404#post11203404)

---

### Post by nm_geo on 2011-08-30
> **Tshann said:**
> Hi,
  I went through a great deal to try to get this puppy to work in Kubuntu 11.04. The final solution - for my rig (HP DV6233se) was to uninstall the bcmwl-kernel-source. I did confirm that the bcm43xx was blacklisted and removed the blacklist - didn't work. No fix on the broadcom sta driver ever worked. But after installing firmware-b43-installer (which automatically brought in cutter) I could get it to work, but I had to log into a terminal every time @ boot up and type in sudo modprobe b43. It was only after removing the above source file and rebooting that my rig came up with a working wireless for Kubuntu 11.04. Hope this is useful for someone else.

Peace

Perhaps I am missing something here.. and believe me I often do..
Do you still have to do the modprobe b43 each time or not?  If you do then b43 is in the blacklist files.. not just the blacklist.conf file but one that is created by the installation of the STA (wl) driver..

```
grep b43 /etc/modprobe.d/*
```

That code will tell us if you have the b43 blacklisted and the file name also.

---

### Post by ieee488 on 2011-09-02
> **westie457 said:**
> Hi the following will sort your wireless.


I also had this problem of wireless not working with the Broadcom STA Wireless driver after up-grading to 'Natty Narwhal' on my Acer laptop with a Broadcom 4311 wifi module. A big thank you to all who posted before me even though the suggestions put forward did not work. However I found a work around this problem and I hope others may find it useful.
The solution in my case worked using a network cable and 'Synaptic Package Manager'. This is what I did:-
1) In Additional drivers I de-activated the STA driver
2) In 'Synaptic' I then removed them completely.
3) Went back into Synaptic and found 'b43-fwcutter' and 'firmware-b43-installer'. I installed both packages because I was not sure which one was needed.
4) After a reboot wireless signed in to the router and the cable removed

Change the firmware-b43-installer to firmware-b43-lpphy-installer.



The above steps worked for the Broadcom 4311 in my Dell Latitude D620 though I didn't do step #5 about the firmware installer.

I don't normally use wifi, but it bugged me that I couldn't see any of the wireless networks around me.

Thank you.

---

### Post by staib on 2011-09-23
> **westie457 said:**
> 
The solution in my case worked using a network cable and 'Synaptic Package Manager'. This is what I did:-
1) In Additional drivers I de-activated the STA driver
2) In 'Synaptic' I then removed them completely.
3) Went back into Synaptic and found 'b43-fwcutter' and 'firmware-b43-installer'. I installed both packages because I was not sure which one was needed.
4) After a reboot wireless signed in to the router and the cable removed

):P This just worked for me on an HP Pavilion dv6000 with BCM4311 wifi.
**Many thanks.** I just Ubuntu'd by son's laptop and when the wi-fi stopped working I was starting to panic! 
Cheers,
Nick

---

### Post by dcunited on 2011-09-25
The complete removal of bcmwl-kernel-source can not be stressed enough.  I fought with this for two days on a Dell 1525 with a BCM4311.  Installing firmware, reboot, uninstall firmware and install b43-installer and then reboot.  It was not until I completely removed that package and THEN installed firmware-b43-installer that it worked.  This is on Ubuntu 11.10 Oneiric Ocelot Beta 2.

---

### Post by kinggo on 2011-09-30
I have DELL vostro 3500 with broadcom 4313 card. And wifi works, but after a recent update from broadcom (that fixed not working LED) I can't see signal levels in percentage with screenlets. It always says that it's not connected.

---

### Post by alco75 on 2011-10-17
I've searched the thread for **bcm43224** and not found the solution I'm about to post.

In Natty, my Thinkpad Edge 11" wifi worked fine out-of-the-box.
In Oneiric, it didn't.

The solution that worked for me that I found was to blacklist exactly two drivers by adding a couple of lines to the end of **/etc/modprobe.d/blacklist.conf**

```

blacklist bcma
blacklist brcmsmac

```

---

### Post by ajzz on 2011-10-17
Confirming that alco75's solution for works the BCM 43224 chips in Dell's XPS 1340s. (Ubuntu 11.10 Oneiric Ocelot).

A bug report for this issue already exists on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/873117](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/873117)

> **alco75 said:**
> 
The solution that worked for me that I found was to blacklist exactly two drivers by adding a couple of lines to the end of **/etc/modprobe.d/blacklist.conf**

```

blacklist bcma
blacklist brcmsmac

```

---

### Post by realruntime on 2011-10-18
> **alco75 said:**
> I've searched the thread for **bcm43224** and not found the solution I'm about to post.

In Natty, my Thinkpad Edge 11" wifi worked fine out-of-the-box.
In Oneiric, it didn't.

The solution that worked for me that I found was to blacklist exactly two drivers by adding a couple of lines to the end of **/etc/modprobe.d/blacklist.conf**

```

blacklist bcma
blacklist brcmsmac

```
Thanks! This also solved the problem on my Acer Travelmate TM8372TG with a BCM43225 device.

---

### Post by lovinglinux on 2011-10-19
I am not sure if this has been posted already, because the thread is pretty big.

After installing the driver through "Additional Drivers", the wireless was not detected anymore.

I was able to solve the problem using the instructions on the following thread:

[http://ubuntuforums.org/showthread.php?t=1745437](http://ubuntuforums.org/showthread.php?t=1745437)

---

### Post by garvinrick4 on 2011-10-19
[http://www.broadcom.com/docs/linux_sta/bcma.txt](http://www.broadcom.com/docs/linux_sta/bcma.txt)

---

### Post by sindhughanti on 2011-10-20
Please Help me here!
[http://ubuntuforums.org/showthread.php?p=11369857#post11369857](http://ubuntuforums.org/showthread.php?p=11369857#post11369857)

Thanks

---

### Post by merry_meerkat on 2011-10-21
> **garvinrick4 said:**
> [http://www.broadcom.com/docs/linux_sta/bcma.txt](http://www.broadcom.com/docs/linux_sta/bcma.txt)

I tried to follow the instructions there, but got this after
```
insmod wl.ko
```

**insmod: can't read 'wl.ko': No such file or directory**

Any help?

---

### Post by westie457 on 2011-10-21
@ merry_meerkat

Just noticed you have had an ongoing problem with your wireless, We shall try to get it working for you.

Can you post the output of these commands please. ```
uname -r

lspci -vnn

lsmod

rfkill list all
```
There might be some others however these will be enough to make a start.

Thank you

---

### Post by paridoth on 2011-10-21
I am having problems with my wireless after installing 11.10. i attempted installing "firmware-b43-lpphy-installer" from synaptic and no change. here are some outputs. I have a linksys usb wireless device in right now that works but I am trying to get my built in broadcom chip to work. please let me know if I can give you more info.

```
jamie@Ubuntu-Laptop:~$ uname -r
3.0.0-12-generic
jamie@Ubuntu-Laptop:~$ lspci -vnn
00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] 760/M760 Host [1039:0760] (rev 03)
	Flags: bus master, medium devsel, latency 64
	Memory at e0000000 (32-bit, non-prefetchable) [size=32M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-amd64

00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] SG86C202 [1039:0002] (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 99
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: e2100000-e21fffff
	Prefetchable memory behind bridge: e8000000-efffffff
	Kernel modules: shpchp

00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] [1039:0963] (rev 25)
	Flags: bus master, medium devsel, latency 0

00:02.1 SMBus [0c05]: Silicon Integrated Systems [SiS] SiS961/2/3 SMBus controller [1039:0016]
	Flags: medium devsel
	I/O ports at 8100 [size=32]
	Kernel driver in use: sis96x_smbus
	Kernel modules: i2c-sis96x

00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513] (prog-if 80 [Master])
	Subsystem: Acer Incorporated [ALI] Device [1025:0083]
	Flags: bus master, medium devsel, latency 128, IRQ 16
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at 2000 [size=16]
	Kernel driver in use: pata_sis

00:02.6 Modem [0703]: Silicon Integrated Systems [SiS] AC'97 Modem Controller [1039:7013] (rev a0) (prog-if 00 [Generic])
	Subsystem: Acer Incorporated [ALI] Device [1025:0083]
	Flags: medium devsel, IRQ 18
	I/O ports at 1000 [size=256]
	I/O ports at 1c00 [size=128]
	Capabilities: <access denied>
	Kernel modules: snd-intel8x0m

00:02.7 Multimedia audio controller [0401]: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller [1039:7012] (rev a0)
	Subsystem: Acer Incorporated [ALI] Device [1025:0083]
	Flags: bus master, medium devsel, latency 173, IRQ 18
	I/O ports at 1400 [size=256]
	I/O ports at 1c80 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:03.0 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f) (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:0083]
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at e2002000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:03.1 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f) (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:0083]
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at e2003000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:03.2 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002] (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:0083]
	Flags: bus master, medium devsel, latency 64, IRQ 23
	Memory at e2004000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet [1039:0900] (rev 91)
	Subsystem: Acer Incorporated [ALI] Device [1025:0083]
	Flags: bus master, medium devsel, latency 173, IRQ 19
	I/O ports at 1800 [size=256]
	Memory at e2005000 (32-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at 28000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: sis900
	Kernel modules: sis900

00:06.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:0083]
	Flags: bus master, medium devsel, latency 168, IRQ 19
	Memory at 28020000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
	Memory window 0: 20000000-23fff000 (prefetchable)
	Memory window 1: 24000000-27fff000
	I/O window 0: 00002400-000024ff
	I/O window 1: 00002800-000028ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

00:0b.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: AMBIT Microsystem Corp. TravelMate 2410 [1468:0312]
	Flags: bus master, fast devsel, latency 64, IRQ 17
	Memory at e2000000 (32-bit, non-prefetchable) [size=8K]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
	Flags: fast devsel

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
	Flags: fast devsel

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
	Flags: fast devsel
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter [1039:6330] (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Device [1025:0083]
	Flags: 66MHz, medium devsel, IRQ 7
	BIST result: 00
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Memory at e2100000 (32-bit, non-prefetchable) [size=128K]
	I/O ports at a000 [size=128]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel modules: sisfb

jamie@Ubuntu-Laptop:~$ lsmod
Module                  Size  Used by
rt2800usb              22300  0 
rt2800lib              48717  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              20092  1 rt2800usb
rt2x00lib              48114  3 rt2800usb,rt2800lib,rt2x00usb
bnep                   17923  2 
bluetooth             148839  7 bnep
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
joydev                 17393  0 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
arc4                   12473  4 
pcmcia                 39822  0 
b43                   318816  0 
snd_seq_midi           13132  0 
mac80211              272785  4 rt2800lib,rt2x00usb,rt2x00lib,b43
snd_rawmidi            25241  1 snd_seq_midi
cfg80211              172392  3 rt2x00lib,b43,mac80211
psmouse                73673  0 
snd_seq_midi_event     14475  1 snd_seq_midi
serio_raw              12990  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
k8temp                 12905  0 
binfmt_misc            17292  1 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
shpchp                 32356  0 
i2c_sis96x             12743  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sis900                 22729  0 
ssb                    50682  1 b43
jamie@Ubuntu-Laptop:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by merry_meerkat on 2011-10-21
[SIZE="3"]**@ westie 457**[/SIZE]
Thank you very much for offering to have a look. Yes, my broadcom wifi has a history of creating headaches, however this is a new problem.

[COLOR="DarkRed"](1 - Background)[/COLOR]
A bit of background: I'm on a Dell Studio 1747 ([specs here]("http://www.notebookreview.com/default.asp?newsID=5419")), which has a Broadcom wireless adapter (BCM43224 14e4:4353). According to the [Broadcom website]("www.broadcom.com/support/802.11/linux_sta.php"), it is compatible with the STA driver (the one that can be enabled through system settings). Up until upgrading to 11.10 Oneiric all was well. Now, however, the computer seems to [COLOR="Navy"]connect just fine to the router, but no traffic[/COLOR] happens at all. Trying with Windows or a different computer with Oneiric has no such problems.

[COLOR="DarkRed"](2 - Things tried or considered)[/COLOR]
I noticed that the [Broadcom website]("www.broadcom.com/support/802.11/linux_sta.php") released a new driver today, 21 Oct. Beforehand, there was a note on that site suggesting that there's an incompatibility with kernels from version 3. With the new release that note has been taken down. I tried to follow the instructions there to use the new driver, but nothing changed (perhaps I made a mistake, though).

One interesting twist is that I [COLOR="Navy"]can actually get wireless working[/COLOR] by adding to */etc/modprobe.d/blacklist.conf*
```
blacklist bcma
blacklist brcmsmac
``` However, it seems to make the connection quite slow.

Other options that I have considered are to try the b43-fwcutter drivers instead. However, most sites list my broadcom card as more compatible with the STA driver.
Finally, there seems to be a bug in oneiric concerning wireless connections using the N channel/standard. I haven't investigated that further.

[COLOR="DarkRed"](3 - output from commands)[/COLOR]
Anyway, so much for background information. Without further ado, the output from the commands you asked for - and some more.

uname -r
```
3.0.0-12-generic
```

uname -m
```
x86_64
```

lspci -vv -nn -s 08:00.0
```
08:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)
Subsystem: Dell Device [1028:000e]
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 17
Region 0: Memory at f8000000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: brcmsmac
Kernel modules: wl, bcma, brcmsmac
```

lsmod
```
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
dm_crypt               23199  0 
wl                   2568210  0 
lib80211               14991  1 wl
bcma                   20219  0 
arc4                   12529  2 
snd_hda_codec_hdmi     32040  1 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
snd_hda_codec_idt      70553  1 
dell_laptop            13831  0 
dcdbas                 14490  1 dell_laptop
snd_hda_intel          33390  3 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_seq_midi           13324  0 
snd_hwdep              13668  1 snd_hda_codec
snd_rawmidi            30547  1 snd_seq_midi
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
v4l2_compat_ioctl32    17083  1 videodev
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
psmouse                73882  0 
serio_raw              13166  0 
brcmsmac              631693  0 
brcmutil               17837  1 brcmsmac
mac80211              310872  1 brcmsmac
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              199587  2 brcmsmac,mac80211
i7core_edac            27942  0 
edac_core              53746  3 i7core_edac
crc_ccitt              12667  1 brcmsmac
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
intel_ips              18089  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
radeon               1015995  3 
ahci                   26002  4 
libahci                26861  1 ahci
ttm                    76805  1 radeon
r8169                  52788  0 
drm_kms_helper         42558  1 radeon
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
drm                   236330  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  1 radeon
wmi                    19256  1 dell_wmi
video                  19412  0 
```

rfkill list all
```
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

modinfo brcmsmac
```
filename:       /lib/modules/3.0.0-12-generic/kernel/drivers/staging/brcm80211/brcmsmac/brcmsmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     ACA36E033D8AEE7A67AA0AC
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
depends:        mac80211,brcmutil,cfg80211,crc-ccitt
staging:        Y
vermagic:       3.0.0-12-generic SMP mod_unload modversions
```

lshw -C network
```
*-network               
       description: Wireless interface
       product: BCM43224 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan1
       version: 01
       serial: c4:17:fe:03:71:cd
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.0.0-12-generic firmware=N/A ip=192.168.1.37 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:f8000000-f8003fff
```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11abgn  ESSID:"tty-29039"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:24:C9:67:21:90   
          Bit Rate=58.5 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:19   Missed beacon:0
```

Right, that's quite a bit more than requested. **Thank you very much** for having a peek at it! Any suggestions are welcome.

---

### Post by westie457 on 2011-10-22
@ merry_meerkat

Well you certainly know more about your card - and provided enough information too.

Before trying any b43 drivers have you tried configuring your router to NOT use 'n-band' speeds. Unless you have a super-duper high speed connection from your ISP or you have a high volume home network you do not need the bandwidth.
If blocking the 'n' band makes no difference then we will try the b43 drivers.

---

### Post by merry_meerkat on 2011-10-22
**[COLOR="Blue"]Thanks, westie457![/COLOR] This has solved the problem for me** - although it is really a workaround rather than a full solution.

It would appear that it is the [bug in Oneiric with 802.11N (bug 836250)]("https://bugs.launchpad.net/ubuntu/oneiric/+source/linux/+bug/836250"). As you suggested, I have changed my router to use 802.11G instead of N and now all is well. Thanks again! I would have probably instead tried first the b43 drivers and then tried to disable N on the computer rather than the router. This is a much cleaner solution!

[COLOR="DarkSlateGray"]Here's a recap of the situation as I understand it to be. Perhaps this helps others with this problem or setup:
Computer setup: [Dell Studio 1747]("http://www.notebookreview.com/default.asp?newsID=5419") with [Broadcom]("http://www.broadcom.com/support/802.11/linux_sta.php") BCM43224 14e4:4353 wireless running Ubuntu 11.10 x64. Ubuntu suggests the proprietary STA driver for that under [FONT="Courier New"]> System settings > Additional drivers[/FONT] and generally speaking that is correct. However, at this time there is a bug in Oneiric with connecting to 802.11N wireless standard. So, changing the router to use the (older and slower) 802.11G standard solves this problem. Hopefully the bug will get solved and we can switch the N back on at some point. I'll try it whenever there's an update to [bcmwl-kernel-source]("http://packages.ubuntu.com/oneiric/bcmwl-kernel-source").

Changing router configuration: usually done by going to [FONT="Courier New"]http://192.168.1.1[/FONT] In my case it's a Swisscom Centro Grande (go to [FONT="Courier New"]> Settings > WLAN > Transmission[/FONT]).[/COLOR]

Cheers.

---

### Post by westie457 on 2011-10-22
@ paridoth

Open Software Centre and search for 'bcm' then remove everything except b43-fwcutter and reboot.

Once the system has restarted open SC and repeat the search. Now install firmware-b43-installer and reboot again. This time disconnect the USB device. When the system is running click on the Network Manager icon and click on your wireless network to connect entering any details as necessary.

Any problems post back here.

Thank you.

---

### Post by yo_bhan on 2011-10-24
I Have BCM4312, after install 11.10 working perfectly :D

---

### Post by bremaya on 2011-10-24
Use the old kernel.. 2.6.39 for oneiric >>> [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39.4-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.39.4-oneiric/"), have a bug in kernel 3.*[URL="http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.39.4-oneiric/"]
[/URL]
Good for ad-hoc connections that do not work with kernel 3 .*[ ]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.39.4-oneiric/")

---

### Post by davidbowie on 2011-10-25
nm

---

### Post by FokkerCharlie on 2011-10-27
Hi Bremaya

Is there a bug filed about this?  I was struggling to get ad-hoc networking to work, and have ended up breaking my wireless entirely...

Charlie

---

### Post by nuisant on 2011-10-30
My Compaq laptop's wireless card was working fine in Natty. Recently upgraded to Oneiric (Ubuntu Studio) and have not been able to solve the driver issue yet. 

I have a Broadcom 4306 802.11b/g internal card.  Running a Clawhammer AMD64 with 64bit installation. 

It seems that it may be possible with b43 driver  - 
4320 version 3  - somehow found that out.

HOWEVER, I'm confused as to which of the many solutions there are that I should try (again), and be successful.  

ANY suggestions / leads would be greatly appreciated !   

cheers.

---

### Post by abdallah1993 on 2011-10-30
**[COLOR=Blue]Thanks, westie457![/COLOR] This has solved the problem for me**

---

### Post by nuisant on 2011-10-31
Whoa... nice - Thank you Westie457 .   OK  - it didn't work at first, so I re-installed 11.10 WITHOUT updating/upgrading. THEN I installed the b43fwcutter from synaptic and rebooted. After that I installed the firmware-b43-installer and rebooted. IT STILL DIDN'T WORK, my wireless card was still in an inactive state. THEN I did the upgrades and updates to 11.10 and somehow noticed that firmware-b43-installer was NOT installed after this(?), so I reinstalled it and without even rebooting, the network manager showed that my wireless card was active and I could connect. NICE WORK ! THANK YOU !

---

### Post by casvrijsbergen on 2011-11-01
Hey, I'm new to this forum and to Ubuntu at all, first installation and I love it! But I couldn't get the wireless to work. Tried different solutions on the net, I want to say that the solution alca75 posted above is also working on my lenovo thinkpad with bcm43224 chip. Thanks!

---

### Post by TBABill on 2011-11-01
Here is an easy method of getting Internet access on a BCM4312 (only version of the Broadcom I have) on 11.10. VERY simple and much easier than the madness of some other methods.
 
1. Insert live CD, USB, DVD
2. Boot into live session
3. Navigate to Additional Drivers
4. Select the STA driver and activate
5. When it says restart to take effect, DO NOT RESTART!! You're in a live session...it'll just start it over from scratch. INSTEAD, just ```
sudo modprobe wl
``` in a terminal.
6. Wait a few moments, enter security passcodes if required, then connect.
 
NOW do the install and you will NEVER have to connect via wire and you will have a fully operational wireless device as soon as the install is over. PLUS you can use the net while installing if you choose. 
 
This method is so much easier than any of the others I have seen posted and it eliminates the need to be tied to the router. Just install the driver, modprobe it and enjoy. Simple. Whether this works for the b43, I do not know. I never choose the b43 with a BCM4312 because the STA simply works better on it for me. 
 
Note: for some reason this does NOT work in Kubuntu or Xubuntu or Lubuntu (unfortunately). Would be great to have consistency in this regard, but at least Ubuntu works with it.

---

### Post by greybeard62 on 2011-11-02
A different machine, same issue.  Lenovo U160 running 11.10.  Connecting by BT only, no eth, can't get wireless to work.  Broadcom BCM4313 14e4:4727(rev01) Subsystem Broadcom (14e4:0510).  At this point I have the most current STA driver installed and active.  Wireless will not enable.

Interesting little machine, rfkill list all shows:
0:  ideapad_wlan: Wireless LAN
         Soft blocked: no
         Hard blocked: no
1:  ideapad_bluetooth: Bluetooth
         Soft blocked: no
         Hard blocked: no
2:  hcio: Bluetooth
         Soft blocked: no
         Hard blocked: no
3:  phy0: Wireless LAN
         Soft blocked: no
         Hard blocked: no
4:  acer-wireless: Wireless LAN
         Soft blocked: yes
         Hard blocked: no

Ideas are welcome, tried a bunch.

---

### Post by greybeard62 on 2011-11-02
In case someone wants to jump on the issue, I have done the following things found on this forum topic.  Uninstalled the STA driver, tried to install the b43 drivers, firmware installer etc but install failed, no hardware found - aborted.  Same for the legacy set except legacy set said use the other set.  Where is Synaptic package manager in 11.10?  All I find is the Ubuntu Software Center in 11.10.  So, blacklisted b43 or not doesn't seem to matter in my case.  The U160 was indeed working fine with Win7 wireless.  Unless there is a hint I'll try setting the MiFi to "g" and see if that helps using the STA driver.

---

### Post by westie457 on 2011-11-03
> **greybeard62 said:**
> In case someone wants to jump on the issue, I have done the following things found on this forum topic.  Uninstalled the STA driver, tried to install the b43 drivers, firmware installer etc but install failed, no hardware found - aborted.  Same for the legacy set except legacy set said use the other set.  Where is Synaptic package manager in 11.10?  All I find is the Ubuntu Software Center in 11.10.  So, blacklisted b43 or not doesn't seem to matter in my case.  The U160 was indeed working fine with Win7 wireless.  Unless there is a hint I'll try setting the MiFi to "g" and see if that helps using the STA driver.

Hi here is a hint for you. Post the output of ```
lsmod
``` please. 

There probably will be a clue to help.

Thank you

---

### Post by SpindizZzy on 2011-11-03
[COLOR=SeaGreen]_**** SOLVED !! ****_[/COLOR]


Ok, I've been wrestling with this issue for over 2 days now, and I just decided to give up and put my fate in the skilled hands of the Forum-Wizzards here... :)

I try to get online on a WPA2-encrypted network (from a university), but i always get errors.

The Univ makes us use the 'XpressConnect'-application (from Cloudpath Networks, Inc.) to obtain a certificate to go online, but it always fails on me. I get the error 'eth1 no authentication information' (in the terminal) and it halts on 'loading configuration information', stating 'A configuration was not found for this device'.

I **freshly installed 11.10** on an old netbook (**HP Mini 1000**), with a **Broadcom BCM4312 802.11b/g LP-PHY**, and try to get it to hook up with the University network.

I already discovered that i didn't have the right drivers with a fresh 11.10 install, and went through [this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers") post, installing both the STA and b43- drivers. None worked... :(:(

Are there specific drivers for the LP-PHY-version of this wireless card that i have to install ? Why is my card not sharing authentication info with that Xpressconnect application ?

Obviously the netbook has no access to internet, but my Macbook has, so i can 'sneakernet' files between the two...

[I]I have my uname -r, lspci -vnn, lsmod and rfkill list in attachment.

[/I][COLOR=Red]_**UPDATE:**_[/COLOR][I]
I found [this bug-thread]("https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/651010")[/I]   and realise now that there is a separate driver for the low-power version of this Wireless card. I copied it to a USB-stick and tried to install it on the Netbook. Off course, the package wants to go online when i run the sudo dpkg command...
Is there a version that has all the needed resources in it, so i can install without going online ? Or -if no such version is available- what steps do i take to install it without using an internet connection ?

[COLOR=SeaGreen]_**** SOLVED !! ****_[/COLOR]
I was finally able to install the necessary LP-PHY driver and followed this:

[LIST]
[*] Select the University network from the Wireless Networks list
[LIST]
[*] a dialog called "Wireless Network Authentication Required" will pop up
[/LIST]
 
[*] Change "Inner authentication" to PAP
[*] In the **Username** field, enter your actual University username.
[*] In the **Password** field, enter your actual University Password.
[*] Click **Connect** to connect to the University network.
[*] Click Ignore to the CA dialog box that pops up
[*] Turn network card off and then on
[/LIST]

---

### Post by Romu on 2011-11-04
Hi all,
I run Ubuntu on my HP Envy 14. This computer has a Broadcom 43224 wireless adapter. Wifi was perfect with 11.04 and is just a nightmare with 11.10 !

My wifi link can stay connected and running for hours or can just cut off every 2 mn. In that case, I have to switch off wireless in Network-Manager and switch on again, and wifi is back for...I don't know, surprise!

I read a bit around the wifi issue on Oneiric but without real solution has only the STA driver supports the 43224 chipset.

So I'm here, asking for a fix, thanks.

---

### Post by sky5564 on 2011-11-04
I posted this problem back in july and never got a single response.

[http://ubuntuforums.org/showthread.php?t=1797927](http://ubuntuforums.org/showthread.php?t=1797927)

---

### Post by greybeard62 on 2011-11-05
[QUOTE=we
stie457;11420621]Hi here is a hint for you. Post the output of ```
lsmod
``` please. 

There probably will be a clue to help.

Thank you

Here it is, Lenovo U160
vice
drm_kms_helper         42558  1 i915
brcmsmac              631693  0 
drm                   236330  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
psmouse                73882  0 
video                  19412  1 i915
btusb                  18600  4 
serio_raw              13166  0 
intel_ips              18089  0 
bluetooth             166112  25 bnep,rfcomm,btusb
brcmutil               17837  1 brcmsmac
mac80211              310872  1 brcmsmac
soundcore              12680  1 snd
cfg80211              199587  2 brcmsmac,mac80211
mei                    41480  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
crc_ccitt              12667  1 brcmsmac
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ahci                   26002  2 
libahci                26861  1 ahci
atl1c                  41643  0 

bill@bill-LENOVO-Ideapad-U160:~$ lspci -nn | grep Broadcom
04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

bill@bill-LENOVO-Ideapad-U160:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
bnep0     no wireless extensions.

bill@bill-LENOVO-Ideapad-U160:~$ dmesg | grep brc
[   13.443500] brcmutil: module is from the staging directory, the quality is unknown, you have been warned.
[   13.444900] brcmsmac: module is from the staging directory, the quality is unknown, you have been warned.
[   13.462779] brcmsmac 0000:04:00.0: bus 4 slot 0 func 0 irq 10
[   13.462837] brcmsmac 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.462849] brcmsmac 0000:04:00.0: setting latency timer to 64


bill@bill-LENOVO-Ideapad-U160:~$ sudo lshw -C network
 *-network               
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: f0:de:f1:11:f0:a0
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:f0400000-f043ffff ioport:2000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:82:99:14:4e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.0.0-12-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0500000-f0503fff
  *-network
       description: Ethernet interface
       physical id: 4
       logical name: bnep0
       serial: f0:7b:cb:e9:ca:a4
       capabilities: ethernet physical
       configuration: broadcast=yes ip=192.168.0.86 multicast=yes
bill@bill-LENOVO-Ideapad-U160:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

bnep0     Interface doesn't support scanning.

bill@bill-LENOVO-Ideapad-U160:~$ lsb_release -d
Description:	Ubuntu 11.10

bill@bill-LENOVO-Ideapad-U160:~$ uname -mr
3.0.0-12-generic x86_64

Wireless will not "enable".  Connected to net via BT/Droid, no eth here.

---

### Post by greybeard62 on 2011-11-05
Output of last requested command:
bill@bill-LENOVO-Ideapad-U160:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                 [ OK ] 
bill@bill-LENOVO-Ideapad-U160:~$ 


Thanks for looking.

---

### Post by anarchybob6 on 2011-11-05
i have a similar problem additional drivers does not detect any of the restricted drivers that i need to use my wifi card. mine is broadcom bcm4318 i have tried all of the different help ttorials on the internet and none of them helped. i have installed the b43fwcutter installed the broadcom source code and i installed every app that showed up when i serched broadcom and it didnt help a thing. i have no idea why my wifi card will not work on these newer versions of ubuntu but i had it working perfectly on 10.10 untill i did an upgrade to 11.04 and it no longer worked. now i have updated to 11.10 and still no wifi. i would really really really apreciate anyhelp i could get on this awful situation

---

### Post by SpindizZzy on 2011-11-05
Kinda glad that I'm not the only one wrestling with this...

Hope one of the more experienced users will pick this up :D

Thx in advance, guys !!

---

### Post by raghavsetu on 2011-11-05
I upgraded to 11.10 from 11.04 and my wireless stopped working.  
STA drivers were installed and were activated (By default ) 
I have Dell Inspiron 640m and network card is Broadcom 4311.  
I did following and it worked for me. 

From Ubuntu software center

1. Remove bcmwl-kernel-source. 
2. Check if firmware b43-installer and b43-fwcutter are installed. Install it if not installed.
3. Restart the computer. 

Same thing happened when I upgraded to 11.04 and everytime during package upgrades if I upgrade wireless drivers it  would stop working. 

Hope this helps.

---

### Post by Rayaz on 2011-11-06
Tried every thing I could find all over the net, but my wifi problem on an Acer 4820T with Oneiric Ocelot just would not resolve. It would work on a whim and often not work at all. 

Easy solution in the end was to ins re-install Linux Mint 11 Katya. Now my wireless works flawlessly!

---

### Post by Romu on 2011-11-07
Hi all,
I happily fixed my Broadcom 43224 wifi issue, I just removed the proprietary STA driver to keep only the brcmmac free driver, and it's far better.

---

### Post by bog_alt on 2011-11-08
Hi, i have installed Kubuntu on my Asus F5R and my wifi doesnt work. (i also tryed with ubuntu and xubuntu but no way to use my wifi). I followed several threads, posts and whatever i find in internet but i haven't solved my problem. My notebook has the wifi light on but ... it seams not working anyway.
*(I tryed with my old usb wifi netgear adapter in order to chek if the wifi signal was ok and it worked...*)

I'm posting you some datas and hope you can help me with this:

```
bog@bog-F5R:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
**02:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)**
06:00.0 Ethernet controller: Atheros Communications L2 Fast Ethernet (rev a0)

``````
bog@bog-F5R:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:fc:c1:e8:a6  
          indirizzo inet:192.168.1.106  Bcast:192.168.1.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::21b:fcff:fec1:e8a6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3294 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3095 errors:0 dropped:0 overruns:0 carrier:1
          collisioni:0 txqueuelen:1000 
          Byte RX:3249808 (3.2 MB)  Byte TX:577607 (577.6 KB)
          Memoria:feac0000-feb00000 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:400 (400.0 B)  Byte TX:400 (400.0 B)

``````
bog@bog-F5R:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

``````
bog@bog-F5R:~$ lsmod
Module                  Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17393  0 
snd                    55902  14 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
sp5100_tco             13495  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_piix4              13093  0 
psmouse                73673  0 
serio_raw              12990  0 
shpchp                 32356  0 
asus_laptop            19050  0 
sparse_keymap          13658  1 asus_laptop
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
usb_storage            44173  0 
uas                    17699  0 
pata_atiixp            12967  0 
radeon                925020  3 
atl2                   27979  0 
ttm                    65224  1 radeon
ahci                   21634  2 
libahci                25727  1 ahci
drm_kms_helper         32889  1 radeon
drm                   192226  5 radeon,ttm,drm_kms_helper
video                  18908  0 
i2c_algo_bit           13199  1 radeon
ati_agp                13242  0 

``````
bog@bog-F5R:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:fc:c1:e8:a6  
          indirizzo inet:192.168.1.106  Bcast:192.168.1.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::21b:fcff:fec1:e8a6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3294 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3095 errors:0 dropped:0 overruns:0 carrier:1
          collisioni:0 txqueuelen:1000 
          Byte RX:3249808 (3.2 MB)  Byte TX:577607 (577.6 KB)
          Memoria:feac0000-feb00000 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:400 (400.0 B)  Byte TX:400 (400.0 B)

bog@bog-F5R:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

bog@bog-F5R:~$ lsmod
Module                  Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17393  0 
snd                    55902  14 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
sp5100_tco             13495  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_piix4              13093  0 
psmouse                73673  0 
serio_raw              12990  0 
shpchp                 32356  0 
asus_laptop            19050  0 
sparse_keymap          13658  1 asus_laptop
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
usb_storage            44173  0 
uas                    17699  0 
pata_atiixp            12967  0 
radeon                925020  3 
atl2                   27979  0 
ttm                    65224  1 radeon
ahci                   21634  2 
libahci                25727  1 ahci
drm_kms_helper         32889  1 radeon
drm                   192226  5 radeon,ttm,drm_kms_helper
video                  18908  0 
i2c_algo_bit           13199  1 radeon
ati_agp                13242  0 

bog@bog-F5R:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fa9fc000-fa9fffff
  *-network
       description: Ethernet interface
       product: L2 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: a0
       serial: 00:1b:fc:c1:e8:a6
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.2.3 duplex=full firmware=L2 ip=192.168.1.106 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:40 memory:feac0000-feafffff memory:feaa0000-feabffff

``````
bog@bog-F5R:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

bog@bog-F5R:~$ dmesg | grep -e Broad
bog@bog-F5R:~$ lsb_release -d
Description:    Ubuntu 11.10
bog@bog-F5R:~$ uname -mr
3.0.0-12-generic i686

bog@bog-F5R:~$ sudo rmmod bc43
ERROR: Module bc43 does not exist in /proc/modules

bog@bog-F5R:~$ sudo modprobe -r b43 ssb wl
FATAL: Module wl not found.
bog@bog-F5R:~$ sudo modprobe  wl
FATAL: Module wl not found.
FATAL: Error running install command for wl


```when i try t reinstal the kernel:
```
bog@bog-F5R:~$ sudo apt-get --reinstall install bcmwl-kernel-source
**[ITALIAN LANG., says allways the same things :)] **
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
I seguenti pacchetti sono stati installati automaticamente e non sono più richiesti:
  diffstat module-assistant quilt
Usare "apt-get autoremove" per rimuoverli.
I seguenti pacchetti NUOVI saranno installati:
  bcmwl-kernel-source
0 aggiornati, 1 installati, 0 da rimuovere e 0 non aggiornati.
È necessario scaricare 0 B/1202 kB di archivi.
Dopo quest'operazione, verranno occupati 3367 kB di spazio su disco.
Selezionato il pacchetto bcmwl-kernel-source.
(Lettura del database... 105066 file e directory attualmente installati.)
Estrazione di bcmwl-kernel-source (da .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu4_i386.deb)...
Configurazione di bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu4)...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
Building only for 3.0.0-12-generic
Building for architecture i686
Building initial module for 3.0.0-12-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-12-generic/updates/dkms/

depmod........

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Elaborazione dei trigger per initramfs-tools...
update-initramfs: Generating /boot/initrd.img-3.0.0-12-generic
bog@bog-F5R:~$ sudo modprobe -r b43 ssb wl
bog@bog-F5R:~$ sudo modprobe -r b43 wl
bog@bog-F5R:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

bog@bog-F5R:~$ sudo modprobe -r b ***[i tryed to press TAB button to autofill the command but b43 does not exist]***
bluetooth  bnep     
```I tryed yo chek the blacklist file: 
```
bog@bog-F5R:~$ sudo cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
#blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
# blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```anyway, in the same dir i have several files:

```
bog@bog-F5R:~$ sudo kate /etc/modprobe.d/ **[pressed TAB button]**
alsa-base.conf               blacklist-framebuffer.conf
blacklist-ath_pci.conf       blacklist-modem.conf
**blacklist-bcm43.conf**         blacklist-oss.conf
blacklist.conf               blacklist-rare-network.conf
blacklist.conf~              blacklist-watchdog.conf
blacklist-cups-usblp.conf    broadcom-sta-common.conf
blacklist-firewire.conf      
bog@bog-F5R:~$ sudo kate /etc/modprobe.d/

```should i try to edit **blacklist-bcm43.conf **as well? 
```
bog@bog-F5R:~$ sudo cat /etc/modprobe.d/blacklist-bcm43.conf 
# Warning: This file is autogenerated by bcmwl. All changes to this file will be lost.
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211

```what does it mean? is **bcmwl** putting my drivers in blacklist by default?

Thank you very much

UPDATE:
**I removed all packeges with tags: bcm, broadcom and then typed in the terminal: **
```
sudo apt-get install firmware-b43-installer
sudo modprobe b43

```
wifi started working. i can't understand why this method has worked now and not yesterday ? i did the same at least twice yesterday...

---

### Post by greybeard62 on 2011-11-08
There were no hints to my problem with the Lenovo U160 and Broadcom 4313 given here.  In case anyone has the same issue here is the fix.  First use the kernel supplied driver, don't install the STA.  Then edit the blacklist file, /etc/modprobe.d/blacklist.conf and blacklist the acer_wmi module.  Hint, open file as administrator with gedit, save after changes.  Then rmmod acer_wmi.  If rfkill list all shows anything blocked issue unblock all.  Your Lenovo U160 will have great wi-fi working.  Cheeers! BTW, it worked in Mint 11 as well, same deal. My original posts are on page 50.

---

### Post by westie457 on 2011-11-08
@ bog_alt

You need to remove the bcmwl driver you are trying to use. It will not work with your wireless card.

open 'Additional Drivers' if it is listed there click on de-activate. Do not reboot when prompted. Instead open a terminal type in and run ```
sudo apt-get install b43-fwcutter
sudo apt-get install firmware-b43-installer
```

if any errors eg- cannot be found - then edit the sources list in Software Centre make sure the first 4 boxes under the Ubuntu Software Tab have a check mark in them. Then run the commands again.

When that has finished, reboot, unplug the USB dongle and your wireless should be working.


Good luck.


--------------------------------------------------------------------------

Have typed the above then noticed you got it working. Oh well.

---

### Post by auftable on 2011-11-09
If network-manager shows "device not managed" (German: "Gerät ... nicht verwaltet"), do this: [http://ubuntuforums.org/showpost.php?p=7040998&postcount=6](http://ubuntuforums.org/showpost.php?p=7040998&postcount=6) , but the config file ist now: 
/etc/NetworkManager/NetworkManager.conf 
And after that > sudo service network-manager restart, and wait 2 minutes, because directly after restarting the service, it still showed that the device is not managed. 

Finally solved my missing wlan functionality from just a distribution upgrade (I think it was up to 11.04)! I am happy :)

---

### Post by Cbviewer on 2011-11-12
Here's some code that might help someone to help me...please!

home@home-OEM:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
vesafb                 13489  1 
binfmt_misc            17292  1 
nvidia              10390874  44 
arc4                   12473  2 
snd_hda_codec_realtek   254125  1 
rt2800usb              22300  0 
rt2800lib              48717  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              20092  1 rt2800usb
rt2x00lib              48114  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              272785  3 rt2800lib,rt2x00usb,rt2x00lib
ppdev                  12849  0 
cfg80211              172392  2 rt2x00lib,mac80211
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             32114  1 
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73673  0 
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
r8169                  43104  0

---

### Post by auftable on 2011-11-12
@Cbviewer
Yes, you have posted the list of loaded modules, but neither b43 nor wl are loaded. What driver do you want to use? And check that only the other module, that you don't what to use, is blocked within the config files in /etc/modprobe.d/ , please.

---

### Post by Cbviewer on 2011-11-12
@auftable Thanks, that's really useful.  I am VERY new to this and do not actually know what I _want _to load and was hoping for advice as a lot of what I've read here and elsewhere is contradictory.  I'm happy to take advice and sort of need leading through it.

Thanks again.

---

### Post by auftable on 2011-11-12
@Cbviewer
Ok, what kind of wlan will you use? If you use it only at home or other private networks, try b43/44 first. Only if that fails or if you also want to have access to a wlan with user accounts, for example at a university, try the STA driver.
Only for b43/44:
Find out your wlan chipset: [http://linuxwireless.org/en/users/Drivers/b43#Supported_devices](http://linuxwireless.org/en/users/Drivers/b43#Supported_devices) .
Install, for example b43-fwcutter and firmware-b43(-lpphy if low power version)-installer with synaptic. Before, deinstall packages beginning with "broadcom-sta-", if installed. Reboot, try "sudo modprobe b43". If only then something works in the network manager, write a "#" in front of every line in /etc/modprobe.d/broadcom-sta-common.conf (edit with sudo gedit).

Btw., what's you current status at all? Error messages you get? What is network messenger showing?

---

### Post by sid1950 on 2011-11-13
Thanks for all the help. I tried a number before getting my WiFi back. The best help came from this link [http://linuxwireless.org/en/users/Drivers/b43#Supported_devices](http://linuxwireless.org/en/users/Drivers/b43#Supported_devices) which identified which driver would work, and has some useful instructions.

My hardware is a Dell Inspiron 1521 AMD Turion x64 Dual core 1.6Ghz, 4Gb RAM, 120Gb hdd. The wireless adapter is Broadcom BCM 4311.

I had Ubuntu 10.04 installed, along with VBox 4.1.4. I had tried 11.04 in a VM, and decided to take the plunge and upgrade. Upgrade went fine using an ethernet cable, but the wifi disappeared as soon as I had activated the STA driver. I tried several fixes from this thread and ended up with no networking at all! That was with the b43 LP-PHY driver. In every case I found that with the driver removed, the card was visible, but showing as disabled,  to the network manager utility on the task bar, which also showed Wireless Networking Enabled. With the driver activated the card was not visible and the Wireless Networking Enabled/disabled function had gone.

After trying various solutions over 3 days, I gave up and did a clean install from a CD using the x86_64 version. This time when I activated the STA driver it all worked fine. The bug seems to be in the download for the upgrade. My 64bit CD image is dated 5 Oct 2011. I'm going to do tests with my old Inspiron 1300 to see if I can replicate this, as it has the same 4211 card.

Again thanks to all those who took the time to post fixes. :)

---

### Post by auftable on 2011-11-14
I think there was a dialog when upgrading wanting me to chose either to keep the old version or chose the new version of a configuration file, and it was something with "network-manager" in it. Maybe that's why STA was deactivated when upgrading but works from a fresh 11.10 system. This could also explain sid1950's problems and solution.

---

### Post by poltr1 on 2011-11-19
Summarizing my install experience on a Dell Latitude D630 running Oneiric and the built-in Broadcom 4311 wireless device:

0) Connect to a network via a wired connection.  :)
1) Installed firmware-b43-lpphy-installer via sudo apt-get install.  Got some type of "installation failed; device not found" error message.
2) Ran update-manager, which populated the software center. 
3) Removed firmware-b43-lpphy-installer and installed firmware-b43-installer via the software center.
4) Commented out the blacklist b43xx line in /etc/modprobe.d/blacklist.conf.
5) Executed "sudo modprobe b43".  (Yeah, I could have rebooted.)

Clicked on my network status icon and I can see -- and connect to -- my wireless network.  Success!

[Updated at 13:01 to add: But upon reboot, I have to type in "sudo modprobe b43" to enable my wireless adapter, every time I start an Ubuntu session.  I think there's something else I need to do so that it would come up automatically.  But I don't know what that is.]

---

### Post by manco1911 on 2011-11-20
I have an Acer Extensa 4420 with a Brodacom BCM4311 integrated. 
After a couple of hours searching around.. i decided to ask the forum/search the forums (dont know why this was not my first choise, it usually is.. ). 

I did exactly what poltr1 said and worked flawlessly. I dont know if ill have to "modprobe" my card on reboot, since i havent rebooted yet. 

i will update on that. 

BTW @poltr1, you could make a small script and run it on system startup.. its not perfect, but it would solve the issue for now.. 

Thaks for the mini tutorial !!
i love this forum

---

### Post by bkratz on 2011-11-20
> **poltr1 said:**
> Summarizing my install experience on a Dell Latitude D630 running Oneiric and the built-in Broadcom 4311 wireless device:

0) Connect to a network via a wired connection.  :)
1) Installed firmware-b43-lpphy-installer via sudo apt-get install.  Got some type of "installation failed; device not found" error message.
2) Ran update-manager, which populated the software center. 
3) Removed firmware-b43-lpphy-installer and installed firmware-b43-installer via the software center.
4) Commented out the blacklist b43xx line in /etc/modprobe.d/blacklist.conf.
5) Executed "sudo modprobe b43".  (Yeah, I could have rebooted.)

Clicked on my network status icon and I can see -- and connect to -- my wireless network.  Success!

[Updated at 13:01 to add:[COLOR="Red"] But upon reboot, I have to type in "sudo modprobe b43" to enable my wireless adapter[/COLOR], every time I start an Ubuntu session.  I think there's something else I need to do so that it would come up automatically.  But I don't know what that is.]


You should be able to automagically load the b43 module at boot by adding it to the modules loaded at boot time. You could add it manually to /etc/modules or in the terminal do (one time):

```
sudo su 
echo b43 >> /etc/modules 
exit

```


This will require your password which will not be echoed to the screen, just press enter when done then try a reboot.

---

### Post by bkratz on 2011-11-20
> **manco1911 said:**
> I have an Acer Extensa 4420 with a Brodacom BCM4311 integrated. 
After a couple of hours searching around.. i decided to ask the forum/search the forums (dont know why this was not my first choise, it usually is.. ). 

[COLOR="Red"]I did exactly what poltr1 said and worked flawlessly. I dont know if ill have to "modprobe" my card on reboot, since i havent rebooted yet. 
[/COLOR]
i will update on that. 

BTW @poltr1, you could make a small script and run it on system startup.. its not perfect, but it would solve the issue for now.. 

Thaks for the mini tutorial !!
i love this forum



If you are using Ubuntu 11.10 you may have one additional file (folder) that is "blacklisting" the b43 driver. See this page for details.

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

See the last two lines.

---

### Post by manco1911 on 2011-11-20
@bkratz
Thanks for the tip, but for i didn't had to "modprobe" again upon reboot. 

maybe this is because i have an integrated card and not a usb-boundle ?

anyway, thanks. 

This kind of things can be hard for a new user, this was a laptop i just made a fresh install for a friend.. but happily it didnt discourage her.. :D 

i guess this is the kind of thigs everyone says: first step, search the forums  lol

---

### Post by sky5564 on 2011-11-20
My problem with this driver was that it was extremely slow, It did actually work but just terribly slow.

I think im going to black list all the linux broadcom drivers for my card and try to install the windows driver via ndis wrapper.

i will post my success or failure here in this thread just in case anyone else is having the same problem i did.

---

### Post by poltr1 on 2011-11-21
> **bkratz said:**
> If you are using Ubuntu 11.10 you may have one additional file (folder) that is "blacklisting" the b43 driver. See this page for details.

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

See the last two lines.

Running "sudo apt-get remove --purge bcmwl-kernel-source" fixed it.  I also added b43 to /etc/modules for good measure.  Thank you bkratz!

---

### Post by bkratz on 2011-11-21
> **poltr1 said:**
> Running "sudo apt-get remove --purge bcmwl-kernel-source" fixed it.  I also added b43 to /etc/modules for good measure.  Thank you bkratz!



Glad you got it going, enjoy!

---

### Post by m.foster on 2011-11-24
hello i am proud to say that i am a noob. But i will also say that i  will not be a noob for long. As i learn fast but i do need help with  some wireless issues. i recently installed a linksys wireless adapter  inconveniently i am working with aircrack-ng and this wireless adapter  does not support monitor mode because i had to use ndiswrapper. just  wondering if there was another way to get it to work or modify it. the  device in question is a linksys AE2500 if anyone has an idea please let  me know.

---

### Post by m.foster on 2011-11-24
hello i am proud to say that i am a noob. But i will also say that i  will not be a noob for long. As i learn fast but i do need help with  some wireless issues. i recently installed a linksys wireless adapter  inconveniently i am working with aircrack-ng and this wireless adapter  does not support monitor mode because i had to use ndiswrapper. just  wondering if there was another way to get it to work or modify it. the  device in question is a linksys AE2500 if anyone has an idea please let  me know.

---

### Post by sky5564 on 2011-11-25
This is kinda of weird.

I ran sudo lshw -C network 

```
*-network
       description: Wireless interface
       product: BCM43225 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 90:00:xx:xx:xx:XX
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.0.0-13-generic firmware=N/A ip=192.168.2.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:d0100000-d0103fff

```

Wich shows that the brcmsmac driver is currently in use on my system for my broadcom 43225 internal card, However in the driver install gui it says that a propritary broadcom "sta" driver is installed by default and in use.

[IMG]http://www.postimg.com/54000/photo-53021.jpg[/IMG]

The brcmsmac driver is an open source driver wich is NOT PROPRITARY in any way shape or form, It was released by broadcom sometime last year as an open source linux driver as you can read here - [http://linuxwireless.org/en/users/Drivers/brcm80211]("http://linuxwireless.org/en/users/Drivers/brcm80211")

[http://lwn.net/Articles/404248/]("http://lwn.net/Articles/404248/")

So why is ubuntu 11.10 saying i have a propritary driver installed when i dont?

---

### Post by Cbviewer on 2011-11-25
Thanks for all the help on here but I'm afraid to say that none of it actually solved the problem.  It has meant that the learning curve was steep and very useful.  

The most excellent news is that I have managed to solve the problem...new hard wear.

After a few searches I came across [https://www.thinkpenguin.com/](https://www.thinkpenguin.com/) on there they have a whole load of useful stuff, including their 802.11G USB Wireless Network Adapter.  I ordered on which was still very reasonable even with postage to the UK.  Under £40 and no more problems.  It's a lot cheaper than buying a new PC or a copy of Windows.

---

### Post by Sef on 2011-11-25
> So why is ubuntu 11.10 saying i have a propritary driver installed when i dont?

Because you do. What Broadcom has released is not ready for Canonical to put in Ubuntu yet.

---

### Post by sky5564 on 2011-11-25
> **Sef said:**
> Because you do. What Broadcom has released is not ready for Canonical to put in Ubuntu yet.

But its open source so obviously it has no proprietary license so why does the additional driver gui label it as something its not?

I dont understand, All that does is confuse the end user.

---

### Post by matt2053 on 2011-12-03
I hope someone sees this and can help me out. I will try here before starting a new thread. I'm fairly new to Ubuntu.

I installed 11.10 on my laptop, a Samsung Series 3. Broadcom WiFi drivers install ok, I can turn on WiFi, see AP's, etc. BUT, I simply cannot connect. I've spent hours trying to troubleshoot this and no luck. I hope someone can help me. I have the STA driver installed.

Edit: It works now. Magically. WTF.

---

### Post by H_J_C on 2011-12-04
> **matt2053 said:**
> I hope someone sees this and can help me out. I will try here before starting a new thread. I'm fairly new to Ubuntu.

I installed 11.10 on my laptop, a Samsung Series 3. Broadcom WiFi drivers install ok, I can turn on WiFi, see AP's, etc. BUT, I simply cannot connect. I've spent hours trying to troubleshoot this and no luck. I hope someone can help me. I have the STA driver installed.

Edit: It works now. Magically. WTF.

This happening to me 2, same sta drivet

---

### Post by dalesomers on 2011-12-05
> **poltr1 said:**
> 


[Updated at 13:01 to add: But upon reboot, I have to type in "sudo modprobe b43" to enable my wireless adapter, every time I start an Ubuntu session.  I think there's something else I need to do so that it would come up automatically.  But I don't know what that is.]

gksudo gedit /etc/modules
then add b43 and save

done!

---

### Post by poltr1 on 2011-12-11
Just finished installing Oneiric on a Gateway MA3 laptop with a Broadcom 4318 wireless LAN controller.  Used the instructions I posted uptopic, and I was able to connect via wireless.  Success.

---

### Post by saxmax on 2011-12-15
Hi to all,
i am pretty new to linux, i installed xubuntu 11.10 on my old acer travelmate 2600 who has b4306 wireless card.
I can not seem to make linux use the wireless adaptor. I have installed the firmware using b43 legacy firmware installer  (wichi readed was the correct firmware) but the additional driverstab in settings does not show me the firmware to activate.. I tryed to unistall and reinstall many times but i can not make it work. 
I followed this guide:

[http://linuxwireless.org/en/users/Drivers/b43#b43_and_b43legacy](http://linuxwireless.org/en/users/Drivers/b43#b43_and_b43legacy)

and expecially this part:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access)

but to no avail..

Could someone help me please?

my lspci -vnn | grep 14e4 is here:

02:05.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

---

### Post by bkratz on 2011-12-15
> **saxmax said:**
> Hi to all,
i am pretty new to linux, i installed xubuntu 11.10 on my old acer travelmate 2600 who has b4306 wireless card.
I can not seem to make linux use the wireless adaptor. I have installed the firmware using b43 legacy firmware installer  (wichi readed was the correct firmware) but the additional driverstab in settings does not show me the firmware to activate.. I tryed to unistall and reinstall many times but i can not make it work. 
I followed this guide:

[http://linuxwireless.org/en/users/Drivers/b43#b43_and_b43legacy](http://linuxwireless.org/en/users/Drivers/b43#b43_and_b43legacy)

and expecially this part:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access)

but to no avail..

Could someone help me please?



my lspci -vnn | grep 14e4 is here:

02:05.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)



The b43 legacy software was just for version 2 of your card. You have version 3 so the standard b43 is the correct version to use.

---

### Post by saxmax on 2011-12-15
Thanks a lot friend.. I have been struggling for all day hitting my head on the walls.. :-D
SOLVED!!
Sure is a complicated world this linux thing, but i like it! Expecially because you always find someone like you to help!
Thanks again!

---

### Post by bkratz on 2011-12-15
> **saxmax said:**
> Thanks a lot friend.. I have been struggling for all day hitting my head on the walls.. :-D
SOLVED!!
Sure is a complicated world this linux thing, but i like it! Expecially because you always find someone like you to help!
Thanks again!



Congratulations on getting it!

---

### Post by postscarcity on 2011-12-18
hi, having lots of trouble with setting up my wireless card. I converted an old windows box to ubuntu, but I haven't been able to get the wireless card recognized. I feel that I've tried everything mentioned in the forums, but I haven't had any luck. fairly noob here, so please bear with me.

here's my lspci -vnn | grep 14e4 

00:0a.0 Network controller [0280]: Broadcom Corporation BCM43xG 802.11b/g [14e4:4325] (rev 02)


Any help would be greatly appreciated. Thank you!

---

### Post by postscarcity on 2011-12-18
to add to the last post -- I've had no luck with the b43, b43 legacy, or b43-fwcutter packages. Somewhere it was suggested to try wl, but I'm not having any luck there either. Also, the suggestions made by wildmanne39 which seemed to work for everyone else, didn't have any effect when I tried them. I'm ready to try anything. Thanks in advance

---

### Post by cmrune on 2011-12-19
ok, so i installed ubuntu through windows just fine, but i cannot get my STA driver to work. 

I went and got the tar to build the driver myself since its not easy for me to get to our houses ethernet connection (personal reasons of course.)

So i started to try and build the driver, but it said i was missing some build packages, so i went back to windows and searched and found that i could get the packages from a livecd. 

I dont have a live cd,but i do have a live usb. tried booting up with the usb but could not find a place that said install packages to my current install. 

So how do i get the packages from my usb onto my current install so that i can build the  driver? Or, am i just doing this totally wrong (as in does the windows install come with the driver and im just overlooking it).

please and thank you for your responses.

---

### Post by westie457 on 2011-12-20
> **cmrune said:**
> ok, so i installed ubuntu through windows just fine, but i cannot get my STA driver to work. 

I went and got the tar to build the driver myself since its not easy for me to get to our houses ethernet connection (personal reasons of course.)

So i started to try and build the driver, but it said i was missing some build packages, so i went back to windows and searched and found that i could get the packages from a livecd. 

I dont have a live cd,but i do have a live usb. tried booting up with the usb but could not find a place that said install packages to my current install. 

So how do i get the packages from my usb onto my current install so that i can build the  driver? Or, am i just doing this totally wrong (as in does the windows install come with the driver and im just overlooking it).

please and thank you for your responses.

To get the drivers from a LiveUSB you boot into the normal Desktop then plug the USB in. Open the file browser and look for the Usb stick in the left panel.

From there navigate to pool/main/b for the b43-fwcutter and build essential packages, double-click on the .deb files to install.

For the STA driver navigate to pool/restricted/b and install similar to the above.

Now assuming you have a b4311 chip the STA driver will not work on 11.04 and 11.10.

The first packages might be enough to get some funtionality for the wireless however the part that gives full wireless is not available on the CD or USB. The needed package is 'firmware-b43-installer. So to get that you will either have to plug a cable in or go to a different computer and download the attached file.

I am looking for the install instructions for the file and will post them later.

Found them here. [http://ubuntuforums.org/showthread.php?t=1859446&page=4](http://ubuntuforums.org/showthread.php?t=1859446&page=4) post #34 has the instructions and post #40 has further instructions.

---

### Post by Flugan on 2011-12-23
I have a problem, I've installed the STA- drivers but for some reason it still refuses to work

My lspci -vnn | grep 14e4: 
03:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:0576] (rev 01)

If anyone can help me, well thanks alot :)

---

### Post by lbrown4283 on 2011-12-24
Alright, i have a bcm4318 on a gateway mx6425 laptop, fresh install 11.10 wired to modem, cant get a connection and i have tried downloading the broadcom-wl-4.150.10.5 and wl_apsta-3.130.20.0o  I have tried all the terminal commands, can some help me out please. what am i not doing.

---

### Post by cmrune on 2011-12-24
ok, so i went ahead and just took my computer to an ethernet connection and got the driver i needed, i took out the ethernet and my wireless connected, but only after i entered the password for my SSID 10 times. But, it worked, so i took the computer back to my room.

Well, now it will recognize the wireless if i enter through hidden networks, but it doesnt show the available networks, and the wireless wont connect (it keeps saying i am putting in the wrong password.)

What should i try to get this going right?

---

### Post by WhtTiger on 2011-12-26
Heya All Just Thought I'd Let Ya Know How I Fixed My Wireless On Sony Laptop ](*,)
1.Download WICD wireless manager
2.Follow These Instructions
 
The issue occured after some suggested updates from the Ubuntu graphical update tool.
The wireless network to which it was connected was a WPA-PSK (WPA2) Passphrase authentication.
The network key was properly typed in and was working well on another system so the error * Connection Failed: Bad Password * made no sense.
 There was nothing unusual in ** /var/log/wicd/wicd.log **, that  made me even more curious about what might be causing the error.After a  lot of try outs and a lot of readings and tests I finally got the cause  of the **weird Bad Password errors produced by wicd**
 Weirdly enought, somehow the Ubuntu package update tool has installed the default gnome ** network-manager ** package.
The installed ** network-manager ** package has mismatched somehow the way wicd connects to wireless networks and as a cause the ** wpa_supplicant ** binary was not properly invoked.
 As a consequence of the network-manager being present on the system  the wpa_supplicant process which made the exact connection to the  wireless network was not launching in, the exact wpa_supplicant  invocation missing was:
 wpa_supplicant -B -i wlan0 -c /var/lib/wicd/configurations/0022b0aa424a -D wext

 Luckily the solution to the notebook wireless device unable to connect to the Wireless network was simple.
 All I had to do is completely remove all occurance of ** network-manager ** packages installed on the Ubuntu system, by issuing the commands:
 sudo apt-get remove --yes network-manager
sudo dpkg --purge network-manager-pptp-gnome network-manager-pptp network-manager

 The reason for issuing the a ** dpkg &#8211;purge ** command was my desire to completely get rid of all kind of *network-manager* related configurations.
 

Now Just Go To WICD Put In Password For Wireless And Connect
Now after re-connecting with wicd wireless manager, it worked fine \\:D/
OMG Its Fixed 
I Bet This Way Will Fix Problems With Other Linux Distro's Too And Other Wireless Cards
Seems There is a problem with network manager
Happy Holidays All:KS

---

### Post by alreadytaken4536 on 2011-12-28
I am running Kubuntu Natty on a Dell Latitude D610 laptop. My wireless card is the BCM4318. Using that information and [this guide]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers") I decided that I should install the b43 drivers.

I ran both of these commands:

```

~$ sudo apt-get install b43-fwcutter

~$ sudo apt-get install b43-fwcutter firmware-b43-installer
```Nothing is showing up in my Additional Drivers window, and I have tried restarting a few times hoping the new drivers would appear.

I tried installing firmware-b43-lpphy-installer through the KPackageKit, but it gives me this error message after installing about 80%.

```
One of the selected packages failed to install corectly.More information is available in the detailed report.

subprocess installed post-installation script returned error exit status 1
```I'm not sure what else to do. I have followed all of the guides.

edit: I tried looking on the Kubuntu forums to see if they might have something more relevant. All I found was [this guide]("http://www.computerandyou.net/2011/05/how-to-solve-no-wireless-networks-in-ubuntu-11-04/"). I followed "Alternate Solution 2" and did the whole blacklist thing, but that didn't work either.

edit2: Well, my network manager seems to recognize that the driver is b43, so why can't I activate it?

edit3: If this is any help, I wasn't able to get wireless working during my live session of Kubuntu 11.04 either, so I don't think any of the solutions involving a live CD will work.

---

### Post by westie457 on 2011-12-29
@ alreadytaken4536

Could you post the output of ```
lsmod
``` please

---

### Post by alreadytaken4536 on 2011-12-29
> **westie457 said:**
> @ alreadytaken4536

Could you post the output of ```
lsmod
``` please

Certainly.

```
Module                  Size  Used by
dm_crypt               22463  0 
joydev                 17322  0 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
pcmcia                 39671  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
dell_laptop            13515  0 
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
dcdbas                 14054  1 dell_laptop
parport_pc             32111  1 
psmouse                73312  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
i915                  451053  2 
drm_kms_helper         40971  1 i915
drm                   184164  3 i915,drm_kms_helper
tg3                   131476  0 
ssb                    45942  0 
i2c_algo_bit           13184  1 i915
video                  18951  1 i915

```

---

### Post by sai-salamander on 2011-12-29
Hello! I hope someone can help me with this, because it's being very frustrating.

I bought a new netbook two days ago; a HP Pavilion dm1, and got my dual-boot all set up with Windows 7 on one side and Oneiric on the other. I had a lot of problems with Unity, so I reverted back to using the Classic Desktop - but that's not really the problem.

Ever since the fresh install (I installed and partitioned from a USB, since I have no disc drive), update manager has been popping up with 298 (or thereabouts) updates that need installing. Every attempt leads to a failure, with the message: failed to download package files, check your internet connection.

Now, my wireless indicator is telling me that I have signal, but it keeps dropping out on the internet too; I can access at times after restarting, then after a while it just drops out completely, but the indicator insists that I'm still connected. I am currently wired in but typing this on a different laptop, and it has the same issue with the updates, and now the internet has just dropped out as well.

I've been googling around for solutions, but none of them have worked. I tried changing the proxy settings and the connection settings, checking the updates before attempting an install (as in [this]("http://ubuntuforums.org/showthread.php?t=1772264") thread), and a few things with the drivers on terminal but to no avail.

I'm sort of at a loose end now, so I'd appreciate it if anyone could point me in the right direction?

---

### Post by westie457 on 2011-12-29
> **sai-salamander said:**
> Hello! I hope someone can help me with this, because it's being very frustrating.

I bought a new netbook two days ago; a HP Pavilion dm1, and got my dual-boot all set up with Windows 7 on one side and Oneiric on the other. I had a lot of problems with Unity, so I reverted back to using the Classic Desktop - but that's not really the problem.

Ever since the fresh install (I installed and partitioned from a USB, since I have no disc drive), update manager has been popping up with 298 (or thereabouts) updates that need installing. Every attempt leads to a failure, with the message: failed to download package files, check your internet connection.

Now, my wireless indicator is telling me that I have signal, but it keeps dropping out on the internet too; I can access at times after restarting, then after a while it just drops out completely, but the indicator insists that I'm still connected. I am currently wired in but typing this on a different laptop, and it has the same issue with the updates, and now the internet has just dropped out as well.

I've been googling around for solutions, but none of them have worked. I tried changing the proxy settings and the connection settings, checking the updates before attempting an install (as in [this]("http://ubuntuforums.org/showthread.php?t=1772264") thread), and a few things with the drivers on terminal but to no avail.

I'm sort of at a loose end now, so I'd appreciate it if anyone could point me in the right direction?

Hello and welcome to the Forum.

You would definitely be better off starting a new thread with your issues. Not very many people look at this thread these days as it is so large.

There are some very clever users here and they are more likely to see a new thread.

---

### Post by sai-salamander on 2011-12-29
> **westie457 said:**
> Hello and welcome to the Forum.

You would definitely be better off starting a new thread with your issues. Not very many people look at this thread these days as it is so large.

There are some very clever users here and they are more likely to see a new thread.

Ah, thank you for that! I wasn't sure whether everything to do with this issue was meant to go in this thread or not.

I shall go make a new one directly! :D

---

### Post by pellefantus on 2011-12-30
why is this problem not resolved with patches? Why does thousands of people need to get to this forums and troubleshoot for hours ( for me it has probably taken days ). Why cant the ubuntu developers release a ******* working patch to fix this issue!!!

---

### Post by joker99 on 2011-12-31
I had such problem with 11.04. But with XUbuntu 11.10, b43 drivers were installed properly by default.

---

### Post by westie457 on 2012-01-01
@ alreadytaken4536

Thanks for the reminder.

Have looked at your lsmod and there are no drivers installed, so rechecked your earlier post about what you installed and found what might be the problem.

Run this in a terminal ```
sudo apt-get install firmware-b43-installer
```

Reboot and it should be working. If not repost a new ```
lsmod
```

Thank you.

---

### Post by fipeto on 2012-01-03
Hi I have Dell inspiron n3010, BCM4313. I have tried [http://ubuntuforums.org/showthread.php?p=11446022](http://ubuntuforums.org/showthread.php?p=11446022) and many of the comments on [http://ubuntuforums.org/showthread.php?t=1753072&highlight=wireless+disabled+hardware+switch+dell](http://ubuntuforums.org/showthread.php?t=1753072&highlight=wireless+disabled+hardware+switch+dell) , but still have message "Wireless network is disabled by hardware switch". Please help! Thanks in advance!

---

### Post by alreadytaken4536 on 2012-01-05
> **westie457 said:**
> @ alreadytaken4536

Thanks for the reminder.

Have looked at your lsmod and there are no drivers installed, so rechecked your earlier post about what you installed and found what might be the problem.

Run this in a terminal ```
sudo apt-get install firmware-b43-installer
```Reboot and it should be working. If not repost a new ```
lsmod
```Thank you.
```

Module                  Size  Used by
bnep                   17923  2 
bluetooth             148839  7 bnep
dm_crypt               22565  0 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80435  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17393  0 
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73673  0 
pcmcia                 39822  0 
soundcore              12600  1 snd
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
dell_laptop            13519  0 
serio_raw              12990  0 
dcdbas                 14098  1 dell_laptop
ppdev                  12849  0 
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
parport_pc             32114  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
i915                  505159  2 
drm_kms_helper         32889  1 i915
drm                   192194  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
tg3                   132972  0 
video                  18908  1 i915

```

---

### Post by canerb on 2012-01-06
Hi all,

I'm using Dell Inspiron 1545 with Ubuntu 11.10 and my wireless card is:

c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

I have no problem with installing and activating STA drivers; however, the signal level is always too weak in Ubuntu. Sometimes Ubuntu doesn't even detect the networks that I can connect in Windows 7 without any problem at all. Is there any way to increase the signal level, or is it just because the STA drivers are not as good as Windows drivers in Linux? If that's the case, is it possible to use ndiswrapper tool to install wireless drivers instead of STA?

Thanks.

---

### Post by Rayaz on 2012-01-06
> **pellefantus said:**
> why is this problem not resolved with patches? Why does thousands of people need to get to this forums and troubleshoot for hours ( for me it has probably taken days ). Why cant the ubuntu developers release a ******* working patch to fix this issue!!!

Second that!

---

### Post by redeemer on 2012-01-11
I am having issues with 11.10, Broadcom BCM4312. I have posted a separate thread detailing my issues: [http://ubuntuforums.org/showthread.php?p=11603449](http://ubuntuforums.org/showthread.php?p=11603449).

Would appreciate it if somebody could take a look. Thanks!

---

### Post by ursus262 on 2012-02-05
This solution worked for me:

[http://ubuntuforums.org/showpost.php?p=11354063&postcount=4](http://ubuntuforums.org/showpost.php?p=11354063&postcount=4)

For some reason, the STA drivers didn't work, but the old B43 did.

I'm using an old Dell Inspiron 6400 (E1505) by the way.

---

### Post by avip04 on 2012-02-06
Hello there,
Am a newbie and am using 
**[SIZE=1][COLOR=Black]*Ubuntu* [COLOR=DeepSkyBlue]11.10 (*Oneiric Ocelot*) [/COLOR][Installed using wubi][/COLOR][/SIZE]**

on an [COLOR=RoyalBlue]_**Asus 1015PN**_[/COLOR] netbook with 2Gigs memory.
Got a **[COLOR=RoyalBlue]Broadcom 4313 chipset [14e4:4727][/COLOR]**


And now am in a real mess:confused:

[B][COLOR=RoyalBlue]
[/COLOR][/B]
I wanted to connect my netbook to my mobile using Joikuspot premium

and  i was able to scan and find the wireless ap but not able to receive an ip so i set a static ip and disabled ipv6 , still no go. . . 



Then after reading a post i installed the broadcom wireless source , common and the firmware [brcmwl-kernel-source] using synaptic, after uninstalling the previous brcm sta driver 

[which was downloaded form [http://www.broadcom.com/support/802.11/linux_sta.php]](http://www.broadcom.com/support/802.11/linux_sta.php]) 



After rebooting the system i did a iwconfig and was **not able to find the wlan0 interface **which was there before, so i removed the drivers that i installed and reinstalled the old broadcom sta from their site, am still not able to find the interface [but ubuntu recognizes my wlan card when i do a lspci]. ](*,)



Someone please help me. . . :sad:

update: guess its conflicting drivers , searching for the conflict now

Update: Solved it bcma was conflicting with wl driver, so blacklisted it. and even the wifi tethering problem was solved. now goanna setup a hotspot [like connectify] and a webdav server.

---

### Post by mahawksid on 2012-02-20
> **canerb said:**
> Hi all,

I'm using Dell Inspiron 1545 with Ubuntu 11.10 and my wireless card is:

c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

I have no problem with installing and activating STA drivers; however, the signal level is always too weak in Ubuntu. Sometimes Ubuntu doesn't even detect the networks that I can connect in Windows 7 without any problem at all. Is there any way to increase the signal level, or is it just because the STA drivers are not as good as Windows drivers in Linux? If that's the case, is it possible to use ndiswrapper tool to install wireless drivers instead of STA?

Thanks.
Check to see if ssb, bcma, wl or b43 is loaded:
  # lsmod | grep "ssb\|wl\|b43\|bcma"

  If any of these are installed, remove them:
  # rmmod ssb
  # rmmod bcma
  # rmmod wl
After this you try to re install your STA driver. Check if it helps. The problem you might be having is the problem of conflicting drivers.
Tell me the result

---

### Post by HeyLynx on 2012-02-29
Hello,

I have added a broadcom wireless but am having issues with its install and working. Firstly I searched and came up with a few solutions but none have worked.

When I type lspci -vnn | grep 14e4 I get this:
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

Installing the card in the network icon, the card needed a firmware upgrade. I having tried to downloaded the b43 and b43 legacy drivers at the command prompt but kept asking me to use the installer CD. Then I decided that this was a good time to upgrade to 11.10 of ubuntu. Then on the restart the wireless card is no longer seen in the network icon.

Have tried installing and re-installing both the b43 and b43 legacy drivers, each one at a time and then removing the drivers. This has been with the package manager. Now its still not seen so don't know what to do next.

Hope someone can help.

Have tried the things that mentioned in the 7 posts that mention this card i'm still at a loss.

---

### Post by brianbotkiller on 2012-03-03
thank you guys, this was very useful!

---

### Post by geoffmurph on 2012-03-05
Hi Folks

Your advice would be much appreciated as I am failing miserably to get a Broadcom bcw4306 PCI card to activate under Lubuntu 11.10. The system is recognizing the card as present but 'firmware not installed'.  I have tried apt-get fwcutter and firmware-b43legacy-installer, but resolutely no activity (not sure if/how I need to activate these modules, as I'm a bit of a noob)

Many thanks

Geoff

---

### Post by mauleshjani on 2012-03-17
dear do this,
 
give this command 1st 

```
sudo lspci -v
```then... give all these commands... u ll succeed...

```
sudo apt-get update
``````
sudo apt-get install firmware-b43-installer
``````
sudo apt-get remove bcmwl-kernel-source
``````
sudo reboot
```==================================================  =============================
bye  thx

---

### Post by geoffmurph on 2012-03-19
Many thanks for your help.  It was a driver issue.  I needed to use the legacy B43 driver!

Geoff:p

---

### Post by seriesoftubes on 2012-04-08
I seem to be having this problem with BCM4313 card. It's working fine whenever I'm right next to the router but when I want to use the computer elsewhere, in my room say, the connection gradually slows down and then grinds to a halt. I have to reload the connection and try to load the webpage as fast as possible. Sometimes the connection stays good for about two minutes before stopping again. I've tried most of the solutions given in this thread but they didn't help much. What else could I do with the driver in order to increase the range that it can actually use my network on?

---

### Post by 23senick on 2012-04-09
Try this thread for the 4313 - there are a couple of posts which list the steps

[http://ubuntuforums.org/showthread.php?t=1889170](http://ubuntuforums.org/showthread.php?t=1889170) 

Good luck!

---

### Post by soslug on 2012-04-09
I have a Broadcom 4311 on an old Dell 1521 Inspiron Laptop 

lspci displays the following

0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

I have not been able to successfully run the STA driver provided with any Ubuntu distribution since 10.04 Desktop LTS which if you are in any doubt it did work. I obtained a pre-release version of 12.04 due for release later this month and was not disappointed when again the Wireless STA driver failed to work.

The solution I came up with involved the editing of modules blacklist in etc and removing and installing some different drivers it is by no means ideal and I hope a resolution can be found for the Wireless STA driver can be incorporated as soon as possible.

First grep to locate the files with the entry Broadcom listed in the files

cat /etc/modprobe.d/* | grep 'bcm' 

the problem with this grep is that it does not tell you the file to locate where the driver is listed so instead use this.

grep 'bcm' /etc/modprobe.d/*

Check your system and modify the above command to find the appropriate blacklist used by your system
 
Edit any files that show bcm43xx with a "#" in front of it and remove the hash so it looks like this:-

bcm43xx

All other modules variants listed can be left alone.

Then open a console and run the following commands

sudo apt-get remove bcmwl-kernel-source
sudo apt-get install firmware-b43-installer

As I say its not pretty but at least you can finally use the wireless on the laptop again from Desktop 10.10 to 12.04.

---

### Post by bohemian9485 on 2012-04-09
I have a Lenovo S10-3 Ideapad netbook, it comes with Broadcom BCM4313 wireless PCI card. After replacing the original Windows 7 Starter operating system with Ubuntu 10.04 Lucid (updated to kernel 2.6.32-40-generic), I lost all the wireless functionality. From Hardware Drivers I was able to install Broadcom STA wireless driver, but obviously it was not the right one:
 
> These package contains Broadcom 802.11 Linux STA wireless driver for use with Broadcom's BCM4311-, BCM4312-, BCM4321-, and BCM4322-based hardware.Issuing lspci -vvnn | grep 14e4 command gave me this:

```

09:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0510]

```While iwconfig command showed this:

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:169
          Rx invalid nwid:0  invalid crypt:2  invalid misc:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

```Now my wireless works somehow but it was listed as eth1 device and performance is not satisfactory.

The weird thing is, when I boot up my netbook using Ubuntu 10.10 Oneiric from a USB stick, the installer could correctly identify my Broadcom card model and install the corresponding drivers. Even the BackTrack 5r2 USB installer can do the same thing and I was able to put my wireless card into monitoring mode using airmon-ng.

Now my question is: can I use the drivers from 11.10 version on my 10.04 OS? If so, how?

My conclusion is this is really a kernel problem and the only solution for me is do an OS upgrade. With Ubuntu 12.04 LTS just around the corner, I would rather wait for a little longer before I make this decision.

---

### Post by kwoby on 2012-04-10
I have an Acer aspire one 722 with BCM4313 and had a lot of problems; i tried various distributions without success. The only one which works without any tweaking is ubuntu 12.04 beta

I have no problems so far with the 12.04 beta; everything works (did not test the mike.) However I do regularly :

sudo apt-get update
sudo apt-get dist-upgrade

So get all the improvments until the final versions

greetings
Kwoby

---

### Post by bayouoldguy on 2012-05-01
> **mauleshjani said:**
> dear do this,
 
give this command 1st 

```
sudo lspci -v
```then... give all these commands... u ll succeed...

```
sudo apt-get update
``````
sudo apt-get install firmware-b43-installer
``````
sudo apt-get remove bcmwl-kernel-source
``````
sudo reboot
```==================================================  =============================
bye  thx

Thanks mauleshjani for the reminder...I tried Ubuntu 12.04 LTS on a USB stick. Installed the recommended wireless driver update,using a hardwire & found no connection to my router. I checked my subscribed threads & located your B43xx fix, the same fix that I had to run to get my Dell D620, w/Broadcom B4311 wireless to connect using Ubuntu 10.04 LTS over a year ago. We need to alert the current 12.04 LTS installers that the 12.04 LTS furnished wireless Broadcom STA driver install still does not solve the Broadcom B43xx problems.   "G"

---

### Post by soulg77 on 2012-05-02
> **mauleshjani said:**
> dear do this,
 
give this command 1st 

```
sudo lspci -v
```then... give all these commands... u ll succeed...

```
sudo apt-get update
``````
sudo apt-get install firmware-b43-installer
``````
sudo apt-get remove bcmwl-kernel-source
``````
sudo reboot
```==================================================  =============================
bye  thx

Hey all, I'm also trying to get a Broadcom BCM4311 wireless card working. I've just tried this and it has worked for me unfortunately. I'm on a Dell Latitude D630 if that makes a difference. Any help is greatly appreciated.

edit: looking at my wireless card through terminal it says "BCM4311 802.11a/b/g [14e4:4312] (rev 01)" hopefully that helps.

edit 2: Just got the wireless working. I ended not using bcmwl-kernel-source and instead used firmware-b43-installer along with b43-fwcutter. Btw, this is all on a fresh install of Kubuntu 12.04 LTS.

---

### Post by bayouoldguy on 2012-05-03
Yep, does work as you indicated....the command "sudo apt-get remove bcmwl-kernel-source" keeps wl  out of the activity....I set up my Canon MP500 printer in the
USB stick run tonight, to make sure the 12.04LTS version is working before I install.  "G"
Probably will wait for the 12.04.1 cleanup before final install.
(Dell D620 laptop & Compaq Presario as noted; Dell w/Windows Vista Business Dual Boot & the Compaq w/stats as shown below....old box still have other stuff on in Windows ME !)

---

### Post by linuxmatt7 on 2012-05-06
I have tried all the solutions in this thread on my HP Laptop running Ubuntu 12.04 LTS. They never worked on me. My card is the 4318 Wireless card. I install the drivers now it shows their is no wireless card at all.

---

### Post by bayouoldguy on 2012-05-06
linuxmatt7; have you looked at this site, be aware that two (2) drivers cannot exist at the same time.     [http://www.linuxwireless.org/en/users/Drivers/b43#Supported_devices](http://www.linuxwireless.org/en/users/Drivers/b43#Supported_devices) ........."G'

---

### Post by Do0d on 2012-05-06
Hello,

I've just put a fresh install of 12.04 32bit on my friends acer 4620Z and cannot for the life of me get the wireless card to show up. 

I've tried multiple walk throughs and guides from many sites, but none of them outline the process to install the drivers for 12.04. I just attempted soulG77's solution for 12.04, and that didnt work for me either.

Also, I am unable to use NDISwrapper, I'm able to download it in the software center, but when I attempt to install the .inf file, I get an error saying the NDISwrapper module is not found?

I did an entire reinstall and attempted just to install synaptic and ndiswrapper to use windows drivers, but I got the same error again. I'd appreciate any assitance any of you could provide. My friend needs her laptop as she is leaving for China in a week and wants to use it as a video phone to call back home. It would be awesome if any of you could help me figure this out!

Here is my sudo lspci -v

04:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
	Subsystem: AMBIT Microsystem Corp. Device 0422
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f8000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 2
	Capabilities: [58] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [13c] Virtual Channel
	Kernel modules: ssb

*******************SOLVED********************

After mucking around a bit more I figured out the fix for this on a fresh install of 12.04 is pretty simple.

If the additional drivers auto loaded the STA wireless driver, you can remove them in terminal with 

sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source

then run:

sudo apt-get install firmware-b43-installer b43-fwcutter

You should see your wireless access points when you reboot.

---

### Post by bohemian9485 on 2012-05-08
I did a fresh install of 12.04 Precise on my Lenovo S10-3 Ideapad netbook, even without using the Additional Drivers, it correctly detected my Broadcom BCM 4313 wireless NIC. The weird thing is, after installing Broadcom STA wireless driver, my wireless interface was changed to eth1 instead of the original wlan0. I can change the wireless NIC settings using nm-applet when it is eth0. But if I unstalled the STA driver, the wireless NIC will revert back to wlan0, although it could connect to various APs, I could not change its settings whatsoever. Any idea?

---

### Post by DemonSharkKisame on 2012-05-09
I have a Broadcom B4318 wireless card, and while I can get Ubuntu to boot from live media by blacklisting the wireless card, I'm wondering if it's possible to install the proper drivers (manually, I don't feel like dragging my desktop into my living room to get to an Ethernet connection) after blacklisting the card in GRUB, and whether or not (if the drivers can indeed install while the card required is blacklisted) simply deblacklisting my card after install would let it work. This issue is literally the one major roadblock keeping me from wiping Windows 7 from my computer. ;)

---

### Post by Jarks on 2012-05-11
This helped to me after upgrade from Kubuntu 11.10 to 12.04:

```

sudo apt-get update
sudo apt-get install firmware-b43-installer
sudo apt-get remove bcmwl-kernel-source
```then reboot. LED on the keyboard is still orange, but the controller works fine.

HP ProBook 4525s, Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

Thanks a lot!

---

### Post by BenTev28 on 2012-05-11
Hello - 

I have followed these instructions and many others for dealing with Broadcom 43xx issues, but I am still having trouble.  Since going from 11.10 to 12.04 I have been unable to get wireless working.  At the point I am right now the wireless card shows up in my network connections and detects networks but will not connect - it hangs on "configuring interface" for quite a while and then gives up.  Further information:

from lspci (currently using the STA driver, have tried both others listed as well):

03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
        Subsystem: Dell Inspiron M5010 / XPS 8300
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at e6d00000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [58] Vendor Specific Information: Len=78 <?>
        Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [d0] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [13c] Virtual Channel
        Capabilities: [160] Device Serial Number 00-00-0d-ff-ff-4a-9c-b7
        Capabilities: [16c] Power Budgeting <?>
        Kernel driver in use: wl
        Kernel modules: wl, bcma, brcmsmac

On connection attempt (channel -1 seems like a problem to me):
 p, li { white-space: pre-wrap; }     [RIGHT][SIZE=1]Type:[/SIZE][/RIGHT]
  [SIZE=1] Wireless 802.11[/SIZE]
   [RIGHT][SIZE=1]Connection State:[/SIZE][/RIGHT]
  [SIZE=1] Configuring interface[/SIZE]
   [RIGHT][SIZE=1]IP Address:[/SIZE][/RIGHT]
  [SIZE=1] No IP address.[/SIZE]
   [RIGHT][SIZE=1]Connection Speed:[/SIZE][/RIGHT]
  [SIZE=1] Unknown[/SIZE]
   [RIGHT][SIZE=1]System Name:[/SIZE][/RIGHT]
  [SIZE=1] eth1[/SIZE]
   [RIGHT][SIZE=1]MAC Address:[/SIZE][/RIGHT]
  [SIZE=1] 9C:B7:0D:4A:2B:FF[/SIZE]
   [RIGHT][SIZE=1]Driver:[/SIZE][/RIGHT]
  [SIZE=1] wl[/SIZE]
   [RIGHT][SIZE=1]Access Point (SSID):[/SIZE][/RIGHT]
  [SIZE=1] Network O Death 2.4G[/SIZE]
   [RIGHT][SIZE=1]Access Point (MAC):[/SIZE][/RIGHT]
  [SIZE=1] 00:00:00:00:00:00[/SIZE]
   [RIGHT][SIZE=1]Band:[/SIZE][/RIGHT]
  [SIZE=1] b/g[/SIZE]
   [RIGHT][SIZE=1]Channel:[/SIZE][/RIGHT]
  [SIZE=1] -1 (0 MHz)[/SIZE]


Any help would be appreciated!  Happy to post more information as needed.  Also, fairly new to these forums... if I'm failing etiquette please let me know.

---

### Post by Sef on 2012-05-27
> Since going from 11.10 to 12.04 I have been unable to get wireless working.

Did you upgrade or do a clean install?

---

### Post by DouglasDaniel on 2012-05-27
> **Jarks said:**
> This helped to me after upgrade from Kubuntu 11.10 to 12.04:

```

sudo apt-get update
sudo apt-get install firmware-b43-installer
sudo apt-get remove bcmwl-kernel-source
```then reboot. LED on the keyboard is still orange, but the controller works fine.

HP ProBook 4525s, Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

Thanks a lot!

Just want to say that, having lost Wireless when updating to 12.04 today, this method worked for me. Much simpler than some of the other methods I had tried earlier on too!

---

### Post by bohemian9485 on 2012-05-28
Found a [**Archlinux wiki guide on Broadcom wireless**]("https://wiki.archlinux.org/index.php/Broadcom_wireless") courtesy of Blackwolf of Ultimate Edition Oz forums, hope this guide can help you guys somehow.

---

### Post by gtuxljb on 2012-06-08
> **Jarks said:**
> This helped to me after upgrade from Kubuntu 11.10 to 12.04:

```

sudo apt-get update
sudo apt-get install firmware-b43-installer
sudo apt-get remove bcmwl-kernel-source
```then reboot. LED on the keyboard is still orange, but the controller works fine.

Thanks a lot!

This worked for me as well.  Broadcom 4312.  However, I had to install the firmware-b43-lpinstaller instead, as I am running it on a lower powered netbook.  

Also had to run updates twice, as it needed the latest kernel.

---

### Post by poltr1 on 2012-06-13
Did a full reinstall of Precise on my Compaq Presario M2000, which has a Broadcom 4318 wireless device, and used the alternate distro as the regular distro was hanging on me.

Referring to post #514 in this thread, which I posted last fall, I performed steps 0, 3, and 4.  And it is working again.

> **poltr1 said:**
> Summarizing my install experience on a Dell Latitude D630 running Oneiric and the built-in Broadcom 4311 wireless device:

0) Connect to a network via a wired connection.  :)
1) Installed firmware-b43-lpphy-installer via sudo apt-get install.  Got some type of "installation failed; device not found" error message.
2) Ran update-manager, which populated the software center. 
3) Removed firmware-b43-lpphy-installer and installed firmware-b43-installer via the software center.
4) Commented out the blacklist b43xx line in /etc/modprobe.d/blacklist.conf.


---

### Post by dougshell on 2012-06-15
Ok, i have tried just about every guide i can find to getting wireless working on my DELL 1525...but im about ready to give up and by a USB dongle.

I have tried reinstalling ubuntu, b43 drivers, sta drivers...and any thing else i have read. 

I am not a TOTAL linux noob, but i do struggle with even some of the simplest tasks as it has been about 5 years since my first (positive) experience with linux

I am willing to run any command and post outputs, but i need the commands pretty much spoon fed.  i can google stuff like how to untar and other thigns like that if necessary, but the simpler the better.

lspci returns:  Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

Any help would be great. Thank you.

---

### Post by matoxxx on 2012-06-17
Hello folks,

after many trial and error with wl and b43 drivers, randomly loosing connection on BCM4312 I found wireless drivers are conflicting with Intel's ethernet driver e1000e. Simple rmmod e1000e resolves the connection issue. What is intriguing I am unable to successfully blacklist this module co I have to manually remove it after boot. Does anyone have suggestions how to make permanent fix of forward this bug upstream to dev teams ?

---

### Post by HeroKing on 2012-06-27
mine just went dead on me after the latest update today. no matter what package i install, my wireless driver refuses to activate. if i try to use the additional drivers program, it tells me that it failed to install and to check "/var/log/jockey.log", which reads as this

```
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 firmware-b43-lpphy-installer
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)

2012-06-26 23:05:24,596 DEBUG: unbind/rebind on driver /sys/module/b43/drivers/ssb:b43: device ssb0:0
2012-06-26 23:05:27,246 DEBUG: writing back check cache /var/cache/jockey/check
2012-06-26 23:05:27,307 DEBUG: writing back check cache /var/cache/jockey/check
2012-06-26 23:05:27,748 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2012-06-26 23:05:28,485 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
```

---

### Post by Ham1337 on 2012-06-28
> **Jarks said:**
> This helped to me after upgrade from Kubuntu 11.10 to 12.04:

```

sudo apt-get update
sudo apt-get install firmware-b43-installer
sudo apt-get remove bcmwl-kernel-source
```then reboot. LED on the keyboard is still orange, but the controller works fine.

HP ProBook 4525s, Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

Thanks a lot!

This worked for me. Dell Vostro 1500, NIC: Broadcom BCM4311 802.11a/b/g
Thanks, Jark!

---

### Post by madvinegar on 2012-06-29
> **matoxxx said:**
> Hello folks,

after many trial and error with wl and b43 drivers, randomly loosing connection on BCM4312 I found wireless drivers are conflicting with Intel's ethernet driver e1000e. Simple rmmod e1000e resolves the connection issue. What is intriguing I am unable to successfully blacklist this module co I have to manually remove it after boot. Does anyone have suggestions how to make permanent fix of forward this bug upstream to dev teams ?


Have you tried manually adding the line "rmmod e1000e" inside /etc/modules?

```
sudo gedit /etc/modules
```

and in the end of the file add the line
> rmmod e1000e

Save, exit and reboot to test.

---

### Post by garver21 on 2012-07-12
i need help getting my wireless workin i have read throught the post an nothing works not sure if its a ubuntu issue or  a setting being wrong i have a wna3100 v1  broadcom bcm43231....  my router shows up on networks an i can connect to it but when i try to access the internet it says website not found .. anyone got any 
ideas

---

### Post by Salpiche on 2012-07-14
Clean 12.04 install on a Dell Mini 1210, it does not see wireless card at all tried everything here and still no dice, any ideas? thanks

---

### Post by loaderjr on 2012-07-17
I'm a total noob...just built a system running **Mythbuntu 12.04** with an old **Buffalo WLI2-PCI-G54S** wireless card. Its the Broadcomm 4306 rev 3 chipset. I tried to use the b43 firmware and didn't get it working, so then I tried the ndiswrapper method. I learned that ndiswrapper won't work on my 64-bit architecture, because Buffalo's Windows 98/XP/2000 drivers are 32-bit. I was unsuccessful in my attempt to use some Vista 64-bit drivers. 
 
To undo my ndiswrapper attempt, I removed the ndiswrapper packages I'd installed, and removed b43, b43legacy, and ssb from blacklist.conf. 
 
I then installed b43-fwcutter and firmware-b43-installer. My wireless card showed UNCLAIMED using lshw -C network. Using "sudo modprobe b43", my wireless card was recognized, and the GUI network settings allowed me to find and connect to my network with WPA2/AES and a hidden SSID. An additional driver was NOT loaded. I made the fix permanent by adding b43 to /etc/modules.
 
CONCLUSION: I *think* the following (from a clean install) would have made everything work without the 10 hours of pain I invested:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
If it works at this point, then type
```
echo "b43" >> /etc/modules
```
This forum was instrumental in my education...hopefully this helps someone else.

---

### Post by jimhenry on 2012-07-18
I had wireless working fine on a clean install of 11.10.   When I upgraded to 12.04, wireless stopped working.  This is my wireless card:

```

lspci -vvnn | grep 14
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```I've tried several of the solutions proposed on this thread and none of them have worked yet, including installing firmware-b43-installer and b43-fwcutter, commenting out the "blacklist bcm43xx" line in /etc/modprobe.d/blacklist.conf, and adding a "b43" line to /etc/modules.  Several times when I tried to activate the driver from the "Additional Drivers" panel, I got error messages in jockey.log about the device being blacklisted.  The last time I tried it it appeared to work; it said I just needed to reboot to finish activating it.  But... even after reboot, I can't get a wireless connection.  Clicking on the networking icon shows: "Wireless networks / device not ready (firmware missing)".  When I go back to the "Additional Drivers" panel it says of the Broadcom STA driver that "This driver is activated but not currently in use".

Any ideas?

---

### Post by jimhenry on 2012-07-19
> **jimhenry said:**
> When I go back to the "Additional Drivers" panel it says of the Broadcom STA driver that "This driver is activated but not currently in use".

When I search for "driver is activated but not currently in use", I find a lot of threads relating to a problem with the Nvidia graphics card driver, but nothing relating to a wireless card driver.  Most of the advice about testing and fixing the problem with the graphics card driver seems very graphics-specific, but one site recommended doing "lsmod | grep nvidia".  I did this instead:

```

jim@waylock:~/tmp/q2$ lsmod | grep b43
b43                   342643  0 
mac80211              436455  1 b43
cfg80211              178679  2 b43,mac80211
bcma                   25651  1 b43
ssb                    50691  1 b43

```It looks like b43 is running, but not being used by any other processes.  b43 is in turn using several other modules.

---

### Post by jimhenry on 2012-07-19
This finally fixed the problem:

```

sudo apt-get remove --purge firmware-b43-installer
sudo apt-get install firmware-b43-lpphy-installer

```

Immediately after the second command above finished, I got my wireless connection back -- I didn't have to tinker with the config files any more or the Additional Drivers panel.

---

### Post by waltkerr on 2012-07-20
After stuggling for years trying to find and install Linux drivers for my Broadcom B43-based WiFi card (branded as Microsoft MN720), I spend less than ten bucks and bought an Edimax WiFi dongle for my laptop. It installed in a snap and works great. My connection speeds are usually 8 to 10 times faster than I ever got with the Broadcom. If you are still battling with the Broadcom, take my advice: buy one of these thumbnail sized WiFi dongles (available in various brands for less than $10 and plugs into USB port), and put the Broadcom where it belongs: in the trash.

---

### Post by Na3iL on 2012-07-27
[CENTER][SIZE=4][COLOR=Blue]thx bro :)
[/COLOR][/SIZE][/CENTER]

---

### Post by IHeequ5i on 2012-07-30
I installed Pangolin on my wife's laptop last night after her Windows install bit the dust. Couldn't get the wireless working; it gave a "firmware not installed" message.

I put the laptop on the hardline, and came here looking for help. Installing the STA driver as noted in this thread fixed it.

Just wanted to say thanks for a useful and helpful thread.

---

### Post by linuxfan247 on 2012-07-31
> **Sef said:**
> Problem in Precise Pangolin 12.04 with the Broadband 43xx Wireless Card: Unable to download firmware for wireless. (Also works for 11.10, 11.04, 10.10 and 10.04)

From the 'Additional Drivers' section:

Possible Solutions:

**Solution 1:** After installing with the alternate cd, I needed a cable and after updating, I was able to download the STA driver through the 'Additional Drivers' section.

**Solution 2: **Another option is [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers").

**Solution 3**: System > Administration > Synaptic Package Manager > Search: firmware-b43-lpphy-installer > Click Mark > Click install > Close (This has been removed starting with 11.10 - Oneiric Ocelot. It may be installed with the Ubuntu Software Manager.)

Kontza found the [solution]("https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/651010") (post #3), so thank him for it.

This solution fixed this problem on my Dell Inspiron 1545 with a Broadcom 4312 card. (Card Tech Specs: 0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01))
I have one of those antennas on the back of my emachine pc but don't use it, read about the driver and where to download it. My location gets bad reception so wifi might be issue for me, I might go usb modem or wifi hotspot which is brodcast in the house it will pick it up cuase it is close.

---

### Post by linuxfan247 on 2012-07-31
> **garver21 said:**
> i need help getting my wireless workin i have read throught the post an nothing works not sure if its a ubuntu issue or  a setting being wrong i have a wna3100 v1  broadcom bcm43231....  my router shows up on networks an i can connect to it but when i try to access the internet it says website not found .. anyone got any 
ideas
Thanks for the tip!! I went to the site that sells them it supports linux alsoso cool!!! dual thumbs up!!

---

### Post by p548fg on 2012-08-18
Please help.

I have Dell Dimension E521 with USRobotics5417 card (BCM4218 chipset) for networking.  In the past (up to Ubuntu 11.X) I was able to install proprietary USR driver with ndiswrapper, and it worked.  Just spent about 3 hours trying to get it to work on 12.04, and no luck.  If you do not have suggestions on how to get this to work,  which network card would you recommend to replace USR.  I have N-Class Linksys E3200 router.  The card should preferably have external antenna.

---

### Post by Hey Gary on 2012-08-25
I have a Dell D800, loaded Xubuntu 12.4, and all looked good except no wireless.  I struggled several weeks.  Today I happened upon this page in the forum.  I downloaded the zip, followed the instructions and I am looking at the laptop with wifi working!

The wifi chipset on my D800 is BCM4309.

The forum page with my solution is:
[http://ubuntuforums.org/showthread.php?p=11413327](http://ubuntuforums.org/showthread.php?p=11413327)

You want to look at post #11 from Wild Man.

I hope this solves your problems, it was driving me batty too!!!

---

### Post by nate33 on 2012-09-03
I've just reinstalled 12.04 from a CD. Have no luck getting wireless to work. I did activate the broadcom STA driver under 'additional drivers' and it's activated/in use. Here's the info:

lspci: 
04:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

lshw -c network:
  *-network DISABLED      
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 1c:65:9d:cc:9a:35
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:fe900000-fe903fff



ifconfig -a:
eth0      Link encap:Ethernet  HWaddr f0:4d:a2:b3:93:ec  
          inet addr:192.168.9.4  Bcast:192.168.9.255  Mask:255.255.255.0
          inet6 addr: fe80::f24d:a2ff:feb3:93ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2412 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1863 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3009862 (3.0 MB)  TX bytes:215266 (215.2 KB)
          Interrupt:43 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 1c:65:9d:cc:9a:35  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

rfkill list: (after I ded rfill unblock all)
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

/etc/NetworkManager/NetworkManager.conf :
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


iwconfig:
lo        no wireless extensions.

eth1      IEEE 802.11  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:72 Mb/s   Tx-Power:off   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.


lsmod:
Module                  Size  Used by
joydev                 17693  0 
bnep                   18281  2 
rfcomm                 47604  0 
parport_pc             32866  0 
bluetooth             180104  10 bnep,rfcomm
ppdev                  17113  0 
vesafb                 13844  1 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
lib80211_crypt_tkip    17390  0 
dell_laptop            18119  0 
dcdbas                 14490  1 dell_laptop
snd_hda_codec_hdmi     32474  1 
psmouse                87692  0 
wl                   2568210  0 
snd_hda_codec_idt      70795  1 
snd_seq_midi_event     14899  1 snd_seq_midi
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
serio_raw              13211  0 
wmi                    19256  1 dell_wmi
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
edac_core              53746  0 
snd_timer              29990  2 snd_pcm,snd_seq
video                  19596  0 
edac_mce_amd           23709  0 
k10temp                13166  0 
fglrx                3263886  155 
snd                    78855  20 snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_seq_device,snd_timer
lib80211               14381  2 lib80211_crypt_tkip,wl
sp5100_tco             13791  0 
soundcore              15091  1 snd
i2c_piix4              13301  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
pata_atiixp            13204  0 
r8169                  62099  0 
usbhid                 47199  0 
hid                    99559  1 usbhid


Tried rmmod -f dell-laptop, didn't work either.
Also reset BIOS to default: didn't work.
Tried b43, didnt' work.
I don't know what else to do!

---

### Post by marty331 on 2012-09-03
Nate33, give this a try....


This is what worked for me:
I followed MrD's suggestions and had to tweak it a little:
1) attach ethernet lead
2) in "additional drivers", turn off STA driver that was auto installed after vanilla 11.04 install
3) in synaptic package manager, remove bcmwl-kernel-source, every b43/broadcom entry, finding them by using the "search" button on those two terms and not the "quick filter"
4) restart computer
5) open terminal,"sudo apt-get install bcmwl-kernel-source"
6) restart computer and enjoy the wifi.
(at this point I did not have wifi going so then I continued on)
7) in synaptic package manager I searched (again search, not quick filter) for broadcom and installed the following: b43-fwcutter, broadcom-sta-common, broadcom-sta-source. Already installed was bcmwl-kernal-source, so I left that alone.
 restart, yes again. I was still connected to ethernet but I hovered over my ethernet and opened the list of availalble networks and could see my wifi, so I disconnected the ethernet and connected to wifi.

---

### Post by nate33 on 2012-09-04
Marty331,
Thank you for your reply.
I followed your instructions and all the wireless stuff under the network icon are gone. 
I tried almost everything and checked on rfkill list, it said hard blocked=yes.

Any other suggestions, please let me know.
Thank you

---

### Post by lethalfang on 2012-09-16
> **jimhenry said:**
> This finally fixed the problem:

```

sudo apt-get remove --purge firmware-b43-installer
sudo apt-get install firmware-b43-lpphy-installer

```

Immediately after the second command above finished, I got my wireless connection back -- I didn't have to tinker with the config files any more or the Additional Drivers panel.

Thanks for this. 
This b43 wifi is the most annoying thing I've ever run across........ this finally fixed it in 12.04 (upgraded from 11.04).

---

### Post by Sevk on 2012-10-10
```
$rfkill list
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes


$lspci -C network
  *-network DISABLED      
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: ac:81:12:58:3b:b2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.2.0-29-generic-pae firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:f4500000-f4503fff



$sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill

3.2.0-29-generic-pae

$lsmod
Module                  Size  Used by
joydev                 17393  0 
bnep                   17830  2 
rfcomm                 38139  0 
parport_pc             32114  0 
ppdev                  12849  0 
bluetooth             158438  10 bnep,rfcomm
snd_hda_codec_idt      60251  1 
wl                   2646601  0 
bcma                   25651  0 
arc4                   12473  2 
psmouse                72919  0 
serio_raw              13027  0 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
ideapad_laptop         17890  0 
snd_seq_midi_event     14475  1 snd_seq_midi
sparse_keymap          13658  1 ideapad_laptop
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  414739  3 
wmi                    18744  0 
brcmsmac              540875  0 
soundcore              14635  1 snd
brcmutil               14675  1 brcmsmac
crc8                   12781  1 brcmsmac
cordic                 12487  1 brcmsmac
drm_kms_helper         45466  1 i915
mac_hid                13077  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
drm                   197692  4 i915,drm_kms_helper
mac80211              436455  1 brcmsmac
cfg80211              178679  2 brcmsmac,mac80211
i2c_algo_bit           13199  1 i915
lib80211_crypt_tkip    17275  0 
video                  19068  1 i915
lib80211               14040  2 wl,lib80211_crypt_tkip
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141369  0
```


b43-lpphy:

[PHP]Unpacking firmware-b43-lpphy-installer (from .../firmware-b43-lpphy-installer_4.174.64.19-4_all.deb) ...
Setting up firmware-b43-lpphy-installer (4.174.64.19-4) ...
Not supported card here (PCI id 14e4:4727
14e4:1692)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--install):
 subprocess installed post-installation script returned error exit status 1
[/PHP]

---

### Post by rossmurray on 2012-10-10
I have to agree about this annoying wifi card. I freaking Linux now but each time I have a problem with Ubuntu it is always surround my wifi.

I just last night did a sizeable update of over 200 files on 12.04 and again I've lost the wifi. Unfortunately enough of a gap passes that I can't recall what I did that fixed it last time.

I may have to do my own thread but hopefully within this 61 pages (sigh) there contains the bounty of an answer to my particular problem.

When I run ```
lspci -nn | grep 0280
lsmod | grep -e b43 -e wl

``` I get the following:

```
05:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
```
So NOTHING on the wl module at all.

I then tried blacklisting all the 80211 and wl module in blacklist.conf and then loading the wl module and it's dependencies with ```
sudo modprobe lib80211
sudo modprobe lib80211_crypt_tkip 
sudo modprobe wl
``` which then gave the following error

```
FATAL: Module not found
```

The search it doth continue..


EDIT: Success with STEP 2 from the original post. All I did was removed the Broadcom bcmwl-kernel-source package (using the Ubuntu Software Centre and the restricted repository), rebooted then installed it again (couldn't find even broadcom in the package search so I just pasted in bcmwl-kernel-source again and I was good to go).

BOOM!! Result. Get in!!

---

### Post by appier on 2012-10-13
> Solution: System > Administration > Synaptic Package Manager > Search: firmware-b43-lpphy-installer > Click Mark > Click install > Close 

The solution still works on Ubuntu 12.04 on an HP dv6000 laptop.  Thank you!

---

### Post by younesysf on 2012-10-14
hi to every body
i have problem with my acer aspire 5750g wireless. i am using kubunto 12.04 LTS.
 i gave this warning when  i want to install aditional derivers

Sorry, installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log
i have tested many ways but not solved.
here is my information:

for lspci -nn | grep -i BCM
```

03:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]


```

for lspci
```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0de9 (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe (rev 10)
02:00.1 SD Host controller: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader (rev 10)
02:00.2 System peripheral: Broadcom Corporation Device 16be (rev 10)
02:00.3 System peripheral: Broadcom Corporation Device 16bf (rev 10)
03:00.0 Network controller: Broadcom Corporation BCM43227 802.11b/g/n


```

for ifconfig
```

eth0      Link encap:Ethernet  HWaddr dc:0e:a1:18:cf:50  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::de0e:a1ff:fe18:cf50/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9067 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9613 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9717561 (9.7 MB)  TX bytes:1070580 (1.0 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:718 errors:0 dropped:0 overruns:0 frame:0
          TX packets:718 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:66141 (66.1 KB)  TX bytes:66141 (66.1 KB)


```

for iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by westie457 on 2012-10-15
Hi you need the Broadcom STA Driver. Plug in a cable please and in a terminal run ```
ksudo apt-get install bcmwl-kernel-source
``` wait a few seconds for networks to be found.

If none found also run ```
ksudo modprobe wl
``` and wait again. If after this still no networks found reboot the system.

All should now be working for you.

---

### Post by younesysf on 2012-10-15
> **westie457 said:**
> Hi you need the Broadcom STA Driver. Plug in a cable please and in a terminal run ```
ksudo apt-get install bcmwl-kernel-source
``` wait a few seconds for networks to be found.

If none found also run ```
ksudo modprobe wl
``` and wait again. If after this still no networks found reboot the system.

All should now be working for you.

i did it and got response:
```

younes@Younes-LPTP:~$ sudo modprobe wl
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module wl not found.
FATAL: Error running install command for wl

```

finally woooorked
by the help of[ this page]("http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Installation-mittels-DKMS")

---

### Post by ja4 on 2012-10-27
> **raghavsetu said:**
> I upgraded to 11.10 from 11.04 and my wireless stopped working.  
STA drivers were installed and were activated (By default ) 
I have Dell Inspiron 640m and network card is Broadcom 4311.  
I did following and it worked for me. 

From Ubuntu software center

1. Remove bcmwl-kernel-source. 
2. Check if firmware b43-installer and b43-fwcutter are installed. Install it if not installed.
3. Restart the computer. 

Same thing happened when I upgraded to 11.04 and everytime during package upgrades if I upgrade wireless drivers it  would stop working. 

Hope this helps.

raghavsetu you are DA MAN!  

I fought with slow wireless in Ubuntu 12.04 with a BCM4322 for months! I tried everything; disabled ipv6, iwlwifi 11ndisable=1, rfkill unblock all, iwconfig eth2 power off, and every other hack that can be found by googling 'ubuntu wireless slow'. Your suggestion finally fixed this problem after I wasted more than 10 hours.

Not only that, my download speed went from ~1 Mbps to over 16 Mbps!  Now my Ubuntu machine is finally as fast as my Windows machines!

---

### Post by cocoa117 on 2012-11-10
anyone have issue see their 5Ghz network? I have bcm4322 on HP TochSmart tx2, and I successfully installed the STA driver. And with iwlist I can see it support 5Ghz channels. But I can't see my 5Ghz network from router using network-manager.

Does anyone have same issue? or solution? It was working fine in ubuntu 10.10 to work with 5Ghz.

---

### Post by cocoa117 on 2012-11-10
> **cocoa117 said:**
> anyone have issue see their 5Ghz network? I have bcm4322 on HP TochSmart tx2, and I successfully installed the STA driver. And with iwlist I can see it support 5Ghz channels. But I can't see my 5Ghz network from router using network-manager.

Does anyone have same issue? or solution? It was working fine in ubuntu 10.10 to work with 5Ghz.

My bad, just realised my router's wifi channel was set to something not listed in the supported range. Now changed it to 44, the 5Ghz network showing in my network list. Yes!!!

---

### Post by dm_research on 2012-11-18
Hi,

I recently updated my 11 year old daughter's laptop (a hand-me-down Dell Inspiron 1501 she uses to help with her schoolwork) from lubuntu 12.04 to lubuntu 12.10.

Everything seemed to go OK except wifi no longer works.

Previously, I believe I needed to blacklist the ssb and b44 drivers and to enable the b43 driver, to match her wifi-only usage pattern. I recall seeing a post somewhere that said there was some sort of incompatibility between the b43 and (ssb+b44) combination - they should not be loaded in the same session. In any case, it worked in lubuntu 12.04 :)

After the lubuntu upgrade, there seems to be a link now between b43 and ssb. See example session below, where you can see that there is a new ssb_hcd driver that seems to be needed for b43, but it also brings the full ssb along too :(

```
$ lsmod | grep ssb
ssb_hcd                12749  0 
ssb                    50087  1 ssb_hcd

$ sudo modprobe -r ssb_hcd

$ lsmod | grep ssb

$ sudo modprobe b43

$ lsmod | grep ssb
ssb_hcd                12749  0 
ssb                    50087  2 ssb_hcd,b43

$ sudo modprobe -r b43
$ lsmod | grep ssb
ssb_hcd                12749  0 
ssb                    50087  1 ssb_hcd

$ sudo modprobe -r ssb_hcd
$ sudo modprobe -r ssb
$ sudo modprobe b43

$ lsmod | grep ssb
ssb_hcd                12749  0 
ssb                    50087  2 ssb_hcd,b43
```


Here is the output of sudo lsh -C network (with b43 and b44 enabled)

```
$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:d0200000-d0203fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64
       resources: memory:d0300000-d0301fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7d:35:be:19
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.5.0-18-generic firmware=666.2 link=no multicast=yes wireless=IEEE 802.11bg
```

Note that the last > DISABLED block disappears if b43 is not enabled. The first block mentions b43-pci-bridge which is not recognised by modprobe. Interestingly, the last block has a serial that looks like a MAC address (of the Broadcom BCM4311 card?), the first one does not. Perhaps some combination of these blocks would be enough to get it working, but I've had no success so far with this.

I have noticed the wifi indicator light on the laptop case flash on briefly (< 1 second) when the laptop boots up.

I should mention the laptop has an F2 hotkey, which in its past Windows XP life, caused wifi to toggle on/off, but lubuntu does not seem to recognise it.

If I could get it to boot with wifi enabled, that would be great. As administrator, I am happy to enable a wired connection if necessary, but for obvious reasons I would prefer not to give extra privileges (e.g., to run modprobe) to my daughter.

I would be very grateful for any advice on how to resolve the issue- I have spent several fruitless hours trying various 'fixes' suggested in this and other forums :confused:

---

### Post by HunkirDowne on 2012-11-18
Before either of us get too excited, I have not yet upgraded from Precise and have a different network card.  That said, here is a bit of (somewhat) useful information that I've found so far today.

Impatient Executive version:
Try installing the Broadcom-STA driver (wl) via these instructions:
[HTML]<a href="http://wiki.debian.org/wl"> Debian Wiki on WiFi using Broadcom driver </a>[/HTML]

OK, let's hope you're not too impatient just in case I'm wrong about the above.

More Detailed version:

Reference 1: [HTML]<a href="https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers"> Reference 1 </a>[/HTML]
Reference 2: [HTML]<a href="https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/651010"> Reference 2 </a>[/HTML]

According to the Ubuntu Docs (Reference 1) you (BCM4311) and I (BCM4312) should be using the 'wl' driver which *does* instruct the blacklisting of ssb and others, as I recall.  I say this because I'm currently using a different driver but I've used the 'wl' (broadcom-sta) driver in the past with great success.  But somewhere I got steered away from it on this card because it is one of the 'low power' cards.

Care to share your lspci information?  Here's mine:

```
$ lspci -vvnn|grep 14e4
```
yields:
```
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```

For me, the "LP-PHY" means (from some source) that I should use the following (from dpkg):
b43-fwcutter					install
firmware-b43-lpphy-installer			install

This is in agreement with what I found earlier in the thread (actually, the original post):
"Had the same problem, then I noticed that instead of firmware-b43-installer I had to install (manually, via synaptic) firmware-b43-lpphy-installer."  --Kontza in LaunchPad.
[HTML]<a href="https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/651010" Ref 2 </a>[/HTML] (Reference 2)

But also see (again, from the original post):
[HTML]<a href="https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers" Ref 1 </a>[/HTML] (Reference 1)

I think our situations are sufficiently different that what I'm currently using is not your solution despite Mr. Konza's expert advice (which applies to me).  I am much more familiar with the Debian advice as that is what I've used in the past for some really old hardware using a PCMCIA wifi card (Linksys, I think, but a Broadcom chipset nonetheless).

Care to share what you've tried that hasn't worked?

General comment: This thread started over two years ago.  62 pages is quite a lot and I won't read all of them unless I'm stuck on an elevator and the rest of the Internet is down.  :^)


> **dm_research said:**
> Hi,

I recently updated my 11 year old daughter's laptop (a hand-me-down Dell Inspiron 1501 she uses to help with her schoolwork) from lubuntu 12.04 to lubuntu 12.10.

Everything seemed to go OK except wifi no longer works.

Previously, I believe I needed to blacklist the ssb and b44 drivers and to enable the b43 driver, to match her wifi-only usage pattern. I recall seeing a post somewhere that said there was some sort of incompatibility between the b43 and (ssb+b44) combination - they should not be loaded in the same session. In any case, it worked in lubuntu 12.04 :)

After the lubuntu upgrade, there seems to be a link now between b43 and ssb. See example session below, where you can see that there is a new ssb_hcd driver that seems to be needed for b43, but it also brings the full ssb along too :(

```
$ lsmod | grep ssb
ssb_hcd                12749  0 
ssb                    50087  1 ssb_hcd

$ sudo modprobe -r ssb_hcd

$ lsmod | grep ssb

$ sudo modprobe b43

$ lsmod | grep ssb
ssb_hcd                12749  0 
ssb                    50087  2 ssb_hcd,b43

$ sudo modprobe -r b43
$ lsmod | grep ssb
ssb_hcd                12749  0 
ssb                    50087  1 ssb_hcd

$ sudo modprobe -r ssb_hcd
$ sudo modprobe -r ssb
$ sudo modprobe b43

$ lsmod | grep ssb
ssb_hcd                12749  0 
ssb                    50087  2 ssb_hcd,b43
```


Here is the output of sudo lsh -C network (with b43 and b44 enabled)

```
$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:d0200000-d0203fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64
       resources: memory:d0300000-d0301fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7d:35:be:19
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.5.0-18-generic firmware=666.2 link=no multicast=yes wireless=IEEE 802.11bg
```

Note that the last  block disappears if b43 is not enabled. The first block mentions b43-pci-bridge which is not recognised by modprobe. Interestingly, the last block has a serial that looks like a MAC address (of the Broadcom BCM4311 card?), the first one does not. Perhaps some combination of these blocks would be enough to get it working, but I've had no success so far with this.

I have noticed the wifi indicator light on the laptop case flash on briefly (< 1 second) when the laptop boots up.

I should mention the laptop has an F2 hotkey, which in its past Windows XP life, caused wifi to toggle on/off, but lubuntu does not seem to recognise it.

If I could get it to boot with wifi enabled, that would be great. As administrator, I am happy to enable a wired connection if necessary, but for obvious reasons I would prefer not to give extra privileges (e.g., to run modprobe) to my daughter.

I would be very grateful for any advice on how to resolve the issue- I have spent several fruitless hours trying various 'fixes' suggested in this and other forums :confused:

---

### Post by dm_research on 2012-11-19
Thanks @HunkirDowne!

I will take a look again at those references and will report back.

I did look at them before (when I installed 12.04) but I think I reverted to the b43 driver at the time (can't remember the reason why...).

However, it is possible that the Broadcom wl driver would work with 12.10 - definitely worth a try :)

Thank you.

---

### Post by dm_research on 2012-11-22
Unfortunately, the problem is still there...

Firstly, here is the output of lspci, as requested by @HunkirDowne:

```
$ sudo lspci -vvnn | grep 14e4
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)

```

As you can see, there is no reference to LPPHY (so I did not follow the rest of @HunkirDowne's suggestions). 

I followed the advice in one of the suggested references
> [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers)
in particular the "STA - Internet Access" > "11.10 (Oneiric Ocelot) - 12.10 (Quantal Quetzal)".

Because b44 depends on ssb, I needed to add that to the modprobe -r line.

When wl is enabled, it seems to bring in ssb and b44 :(

```
$ sudo modprobe -r b43 b44 ssb wl
$ sudo lsmod | grep ssb
$ sudo modprobe wl
$ sudo lsmod | grep ssb
ssb                    50087  1 b44

```

I found the webpage that suggested that the ssb driver is not compatible with wl:

> [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

On that page, there is a section "Remove any other drivers for the Broadcom wireless device." which mentions b43, ssb, etc. The recommended approach is to rmmod the incompatible drivers. I tried this, ran modprobe wl again and, you guessed it, they were back in the list of modules returned by lsmod!

The other thing I tried was to add the problematic drivers (b43 b44 ssb, etc) to /etc/modprobe.d/blacklist.conf and rebooted. Again, the b44, ssb and wl modules were loaded.

Then I thought that maybe there is an explicit reload of these modules that happens after processing the blacklist file. I checked /etc/modules and the only uncommented line was
> lp

which I assume enables printing, but seems to be "safe".

At the moment, I am beginning to suspect there is a bug somewhere in the wifi setup in 12.10 - it probably does not help that both cards are Broadcom and may share driver features. I would have given up long ago if I did not know that wifi *was working* in 12.04 and I am reasonably certain that the "fix" involved 'disabling' b44 and ssb.

Lastly, if it helps understanding, to access the internet when both Broadcom cards are inoperable, I use a tethered 3G connection (to check advice pages), but that's not a practical solution in the long term given the intended use of the laptop.

> **dm_research said:**
> Thanks @HunkirDowne!

I will take a look again at those references and will report back.

I did look at them before (when I installed 12.04) but I think I reverted to the b43 driver at the time (can't remember the reason why...).

However, it is possible that the Broadcom wl driver would work with 12.10 - definitely worth a try :)

Thank you.

---

### Post by Simm2 on 2012-11-29
I have got the same problem with 12.10.
To note : during installation of 12.10, and for some time after installation, Wifi worked nicely. It seems to me that it stopped working after a kernel update (3.5.0-18, a second update 3.5.0-19 did not improve anything wrt this problem).

---

### Post by rsavage on 2012-11-30
> **dm_research said:**
>  When wl is enabled, it seems to bring in ssb and b44 :(
 
```
$ sudo modprobe -r b43 b44 ssb wl
$ sudo lsmod | grep ssb
$ sudo modprobe wl
$ sudo lsmod | grep ssb
ssb                    50087  1 b44

```
 
..... 
 
At the moment, I am beginning to suspect there is a bug somewhere in the wifi setup in 12.10 - it probably does not help that both cards are Broadcom and may share driver features. I would have given up long ago if I did not know that wifi *was working* in 12.04 and I am reasonably certain that the "fix" involved 'disabling' b44 and ssb.

 
If you have a b44 ethernet card then you have these lines in /etc/modprobe.d/blacklist-bcm43.conf
 
```

blacklist b44
install wl modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install wl $CMDLINE_OPTS; modprobe --ignore-install b44

```
 
So when you modprobe wl, it automatically modprobes b44 too. Play around with this line and see if removing the "modprobe --ignore-install b44" fixes the problem. If it does then you need to raise a bug.
 
P.S. It is easy to miss new posts in sticky threads and this is why they sometimes don't get replies. It is much better to create a new thread with your problem. Then people with the same problem can easily find it, rather than wading through a 63 page thread (and if you want to be super helpful, update the community wiki page!).

---

### Post by Simm2 on 2012-11-30
> **rsavage said:**
> P.S. It is easy to miss new posts in sticky threads and this is why they sometimes don't get replies. It is much better to create a new thread with your problem. Then people with the same problem can easily find it, rather than wading through a 63 page thread (and if you want to be super helpful, update the community wiki page!).

It would be a good thing for a moderator to create a new thread starting with message 617 of this thread and some new title such as *Broadcom 43xx Card Problem (12.10 Quantal Qetzal)*.
Don't you think so ?

---

### Post by Sef on 2012-12-01
> Simm2: It would be a good thing for a moderator to create a new thread starting with message 617 of this thread and some new title such as Broadcom 43xx Card Problem (12.10 Quantal Qetzal).
Don't you think so ?

Have thought about starting a new one when the next distro comes out, but had not thought about cutting it and starting with a new one. That is a good idea. Thank you for the suggestion, Simm2. Done.

---

