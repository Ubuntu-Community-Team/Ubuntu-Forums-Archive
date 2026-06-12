---
title: "Need help with wireless on Ubuntu 9.1"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by darbielove on 2009-10-29
I just installed ubuntu 9.1 and I can't get my wirless internet working. I had it working in the previouse version of ubuntu. The light does come on. I have a compaq presario c571nr. What should I do?

---

### Post by sickly on 2009-10-29
did you try right clicking the network connections icon and see if the enable networking and wireless is checked?

---

### Post by darbielove on 2009-10-29
I'll try that.

---

### Post by darbielove on 2009-10-29
It was checked

---

### Post by jtmedin on 2009-10-29
I have the same problem with wireless & wireless is not shown. wired is shown

---

### Post by tacantara on 2009-10-29
I experienced a loss of wireless connectivity also when I upgraded to 9.10.  I connected to my router via ethernet and that worked.  Apparently some wireless support was dropped in this new OS.  I reverted to 9.04 by installing it on a separate partition, hoping that I will find an answer to the 9.10 problem so I can return to it as my main OS.

I haven't been able to find anything useful on this forum or Google to fix the problem....yet.  The answers are out there (I hope).

---

### Post by sickly on 2009-10-30
are you seeing networks and cant connect? or you dont even see any?

---

### Post by blueb73 on 2009-10-30
I am having the same issue.

cant see any networks.  I can see plenty on my other laptop (running Hardy), and I used wubi to install 9.10, and the windows partition can see wireless networks, but the the ubuntu partition!
plug in a wire and i can connect fine.

argh!!!

---

### Post by darbielove on 2009-10-30
I can't see any networks. I can in Windows

---

### Post by insanecrazy4 on 2009-10-30
im having the same exact problem

---

### Post by tacantara on 2009-10-30
Ditto.  I can't see the wireless network in my home, but I can connect via CAT5 to the router.  In Jaunty, the wireless works flawlessly.

---

### Post by Vague Rant on 2009-10-30
Same or similar problem for me with an Acer Aspire One and an Atheros wireless card (do any of you know if you also use Atheros cards?). Couldn't get any networks to show, so I manually created a network and tried connecting that way. Network Manager claimed I was connected, but with a signal strength of 0%. Now I can get network access by unchecking wireless then checking it again, but it has to be done on each boot. Worth checking if this works for any of you; not the ideal, but a decent stopgap until things work properly.

---

### Post by markoloka on 2009-10-30
I see networks but can't connect. no matter what i write to wpa pass it's same result: no go. 
that network manager seems to be piece of s**t. it didn't work in previous ubuntu's either.

I'll do again what i did with previous versions: throw network manager to trash can and use WICD. 
For me it's best. [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
I have a-link wireless usb card, don't remember model.

---

### Post by zenlunatic on 2009-10-30
Same problem.  Worked fine in Jaunty.  My wireless device isn't even recognized.  All I have is eth0 (wired), lo.  Nothing in restricted drivers either (broadcomm card).

---

### Post by stevenjcarney on 2009-10-30
I'm having the same problem. 
I JUST did a clean install of 9.10. My wireless card isn't even being picked up when I do " **lshw -C network" **in the terminal. I'm sitting on cat5 right now.

---

### Post by zenlunatic on 2009-10-30
I installed bcmwl-kernel-source and it is working fine.  Kinda disappointing...

---

### Post by lexpenrose on 2009-10-30
Hi guys, 

Same problem here. For me it's my Broadcom STA Wireless Driver that doesn't work. You can install the broadcom driver from the CD ( or USB stick ) but then you can't even activate it using the restricted hardware. 

People have posted a few different solutions including fwcutter but none worked for me, 9.04 everything worked fine.

---

### Post by lexpenrose on 2009-10-30
> **zenlunatic said:**
> I installed bcmwl-kernel-source and it is working fine.  Kinda disappointing...

Yep, I installed that driver too, then it wouldn't let me activate it in the restricted hardware. 
It's a showstopper for me , I will revert back to Linux Mint until Ubuntu makes their installs work out of the box ( which includes broadcom wireless driver, codecs, etc )

---

### Post by vikas.sriv14 on 2009-10-30
Same problem occured woth me too. i have already installed bcmw-kernel package and that didn't help either. i hope there is a solution to this or i would have to go back to 9.04

---

### Post by sickly on 2009-10-30
darbialove, try to open a terminal and type 
 
iwlist scan
 
 
and see if any networks come up. if not post the output

---

### Post by alisdair on 2009-10-30
I have similar problem, i can connect by wireless/wired through ethernet/wired through usb but the internet doesn't work. I tried to reinstall a driver package and even donwgraded the kernel but nothing helped.

---

### Post by AlmaTlust on 2009-10-30
I had the same problem with 9.10 (64). Installing wicd instead of networkmanager solved the problem for me.

---

### Post by cphayes0914 on 2009-10-30
I installed the brdcm knl  as well as scrapping the junk network manager for wicd and now its working fine.   After I installed brdcm the proprietary driver started working, but every time I booted the comp I had to manually turn on wireless detection.  Now that I scrapped network manager, no need.

---

### Post by Kevbert on 2009-10-30
Same problem here. No Broadcom drivers were installed by default. To get wireless going, copied b43 and b43 legacy firmware directories from Jaunty 9.04 to 9.10 /lib/firmware directory and after a reboot everything was fine.

---

### Post by darbielove on 2009-10-30
[sickly]("http://ubuntuforums.org/member.php?u=919149") - I typed iwlist scan in a terminal and this is what printed:

lo                Interface doesn't support scanning.

eth0            Interface doesn't support scanning.

wmaster0     Interface doesn't support scanning.

wlan0          Failed to read scan data: Network is down.

---

### Post by sickly on 2009-10-30
darbielove, open a terminal and type,

sudo ifconfig wlan0 up

then try 

iwlist wlan0 scan

and see if the output shows any networks

---

### Post by ninjatiger422 on 2009-10-30
Go:

System > Administration > Hardware Drivers

Activate one.

I HAD to have a network cable plugged in because it had to download the drivers.

---

### Post by darbielove on 2009-10-30
sickly - i tried those things and I got the following:

SIOCSIFFLAGS: No such directory

---

### Post by sickly on 2009-10-30
in terminal type

lspci

and post the results

---

### Post by darbielove on 2009-10-30
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
  00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
  00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
  00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
  00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
  00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
  00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
  00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
  00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
  00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
  00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
  00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
  00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
  00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
  00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
  06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
  08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by Jagsjim on 2009-10-30
I have been following along with the instructions and have the same problem darbielove has.    Any help would be greatly appreciated.  Here is my log:

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by sickly on 2009-10-30
06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01) 

is what i was looking for. The answer to your problem was solved on this thread 

[http://ubuntuforums.org/showthread.php?t=1240500](http://ubuntuforums.org/showthread.php?t=1240500). 


Hope this helps.

---

### Post by darbielove on 2009-10-30
I tried the sudo in the terminal and it sayd "command not found"

---

### Post by Jagsjim on 2009-10-30
sudo apt-get install b43-fwcutter

The first command had a typo this is the correct command

---

### Post by sickly on 2009-10-30
sudo is not a command, it will give you root privleges for a command or to open something

---

### Post by darbielove on 2009-10-30
Just tried that. this is what I get.

   

  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done
  E: Couldn't find package b43-fwcutter

---

### Post by sickly on 2009-10-30
do this first:

sudo apt-get update

---

### Post by darbielove on 2009-10-30
When I try that I get this:

   Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
   
    Could not resolve 'security.ubuntu.com'
   
  Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
   
    Could not resolve 'security.ubuntu.com'
   
  Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
   
    Could not resolve 'security.ubuntu.com'
   
  Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
   
    Could not resolve 'security.ubuntu.com'
   
  Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
   
    Could not resolve 'security.ubuntu.com'
   
  Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
   
    Could not resolve 'us.archive.ubuntu.com'
   
  Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
   
    Could not resolve 'us.archive.ubuntu.com'
   
  Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
   
    Could not resolve 'us.archive.ubuntu.com'
   
  Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
   
    Could not resolve 'us.archive.ubuntu.com'
   
  Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
   
    Could not resolve 'us.archive.ubuntu.com'
   
  Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
   
    Could not resolve 'us.archive.ubuntu.com'
   
  Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
   
    Could not resolve 'us.archive.ubuntu.com'
   
  Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
   
    Could not resolve 'us.archive.ubuntu.com'
   
  Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
   
    Could not resolve 'us.archive.ubuntu.com'
   
  Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
   
    Could not resolve 'us.archive.ubuntu.com'
   
  Reading package lists... Done           
   
  W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'
   
   
   
  W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
   
   
   
  W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
   
   
   
  W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
   
   
   
  W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
   
   
   
  W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'
   
   
   
  W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
   
   
   
  W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
   
   
   
  W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
   
   
   
  W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
   
   
   
  W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  Could not resolve 'security.ubuntu.com'
   
   
   
  W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
   
   
   
  W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
   
   
   
  W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
   
   
   
  W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
   
   
   
  W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by darbielove on 2009-10-30
I am thinking that I need to have a connection to a direct ethernet cable, but I connect to a company server. ??

---

### Post by sickly on 2009-10-30
lol. i feel like a ***hole. I forgot your not conected to the internet. To do this your going to have to use a wired conection to conect to the internet. Your wired conection should work.

---

### Post by darbielove on 2009-10-30
ok I'll keep the scripting untill I can find a wired connection. Thank you for your help. I'm sure it will work.

---

### Post by teward on 2009-10-30
I'll bet you this is an issue with 9.10.  Recommendation:  Submit a bug report.

In the Dell support category here on this site, a similar issue arose, so I am drawn to the conclusion that this is a bug in 9.10.

---

### Post by bhishan on 2009-10-30
> **darbielove said:**
> I just installed ubuntu 9.1 and I can't get my wirless internet working. I had it working in the previouse version of ubuntu. The light does come on. I have a compaq presario c571nr. What should I do?

You will need a cable connection first. After connecting it to a cable network install the ubuntu-restricted-extras and go to system>administration>hardware drivers and activate the drivers that show up in the list and you will be good to go. I had this same problem. I can imagine how depressing it is for people who have access to only wireless internet.

---

### Post by darbielove on 2009-10-30
I guess I should have been a beta tester. Where should I go to submit the bug?

---

### Post by sickly on 2009-10-30
i guess its been a ongoing issue before 9.10  with these  cards.

---

### Post by tacantara on 2009-10-31
Well, I've tried everything here in this thread, and I still have to rely on an ethernet connection to my router to access the Internet.  Sadly, I keep getting error messages when I try to access the repos, something to the effect of "cannot connect to the server," thus I can't get any updates or download packages through Synaptic.  I'm sure it is not a connectivity problem, as the same ethernet connection is allowing me access to this Forum. Is it possible that something went awry during the upgrade that is preventing my computer from talking to the Ubuntu repos?

I hope everyone else experiencing wifi issues has better luck in resolving them.

---

### Post by jlhaslip on 2009-10-31
> **bhishan said:**
> You will need a cable connection first. After connecting it to a cable network install the ubuntu-restricted-extras and go to system>administration>hardware drivers and activate the drivers that show up in the list and you will be good to go. I had this same problem. I can imagine how depressing it is for people who have access to only wireless internet.

Trying to set up 9.10 as a dual boot with 9.04 and the wireless card is failing to get the right drivers.

Have a hard wire connection and tried that. No Drivers were found or required, but I know the Wireless is a Broadcom BCM4311 802.11b/g because it is working fine in a dualboot 9.04 install.

also tried the solution re: sudo apt-get upgrade followed by the sudo apt-get install bw43 as per the posting around #36, and that fails to find the Driver as well.

What to try next?

[SOLVED]

Not sure what happened. Started the machine the next day and it was all good.
Strange, but true.

try this first ==> [http://ubuntuforums.org/showpost.php?p=7788633&postcount=2](http://ubuntuforums.org/showpost.php?p=7788633&postcount=2)

---

### Post by darbielove on 2009-10-31
I am thinking with empathy for the ubuntu developers becase the theory of distributing genuine software is a good argument and a good idea.

---

### Post by gearond on 2009-11-11
Very similar, if not same problem.

Recognizes that there is a wireless usb dongle, asks for the password, goes through the usual (too long) connection timeout, then asks for the password again. 

Everything works fine on the windows vista side of this dual boot Gateway W350a with Airlink101 dongle. It also worked fine on 9.04 Ubuntu.

I will try the other network manager alternative and post the results (have to leave right now)

PS, 9.10 is great, faster, better looking, slightly more functional. But wireless and switching to postgres8.4 were a PITA!!!!!!!!!1 (Neither working yet)

---

### Post by byzantine on 2009-11-11
I followed this thread.......I CANT get a wired connection either.........

Because of that I can't copy and paste.....but the highlights

*I am a not 'tech savvy', so please bare with me.

SYSTEM>PREFERENCES>NETWORK CONNECTIONS

wirless, auto netgear

connect automatically is checked

mode:  infrastructure
ipv4 settings: method----> automatic (DHCP)   ipv6---->automatic


SYSTEM>PREFERENCES>NETWORK PROXY

Direct Internet connection is 'dotted'.
there are NO ignored hosts


SYSTEM>ADMIN>NETWORK TOOLS


Devices--->  network device:  loopback interface (lo)



I Installed:   sudo apt-get install linux-backports-modules-karmac......I got 'error messages' could not resolve 'us.archive.ubuntu.com'  things like that.


IWLIST SCAN

lo   interface doesn't support scanning
eth0   interface does not support scanning
wmaster0  interface doesn't support scanning
wlan0   no scan results


my NETWORK CONTROLLER is

Intel PRO/Wirelss 4965 AG or AGN [Kedron] Network Connection (rev 61)



The wireless works on the dual boot.


Thanks for any help

---

### Post by byzantine on 2009-11-11
bump...see page 5

---

### Post by kakyoism on 2009-11-14
INTEL 4965 AGN, can't obtain IP with encrypted WIFI. Tried network-manager and wicd to no avail.

---

### Post by xifer on 2009-11-17
Got similar problems.  All worked fine with 9.0

Tried kde/xfce/gnome networkmanagers.  Any chunky download loses the connection and it wont come back.  sometimes restart router fixes it.  Have also restarted xserver and rebooted computer all to no avail.  When i am connected i get 2MB in ubuntu - Windoze (sic) gets 54MB connection.  Have read this may be DHCP issues but i don't want to have to configure all the comps here with static IP.  There must be an answer?

---

### Post by YeeP on 2009-11-19
My "original" card I was using, I found that it is no longer supported by ubuntu 9.10. I guess I am OK with that. I just got my hands on a Cisco aironet card(I need to see the exact model). Do you pros think if I follow the described "update drivers" process when connected on a hardwire, this may take care of my problems?


Also, I know I have seen a list of supported cards for ubuntu on the web. I am thinking I will just go buy a new card if this doesnt work. I really like ubuntu and would rather just stay with the newest versions when they come out.  Anyone know the url of the said "list"

---

### Post by bkratz on 2009-11-19
> **YeeP said:**
> My "original" card I was using, I found that it is no longer supported by ubuntu 9.10. I guess I am OK with that. I just got my hands on a Cisco aironet card(I need to see the exact model). Do you pros think if I follow the described "update drivers" process when connected on a hardwire, this may take care of my problems?


Also, I know I have seen a list of supported cards for ubuntu on the web. I am thinking I will just go buy a new card if this doesnt work. I really like ubuntu and would rather just stay with the newest versions when they come out.  Anyone know the url of the said "list"







Is this the list you are looking for?

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by gearond on 2009-11-19
I'm still not hearing any choruses out there singing, "My 9.1 Ubuntu works GREAT with wireless now. I love Ubuntu, 9.1, and now both with wireless, la ti da ti daaaaaaaah!"

So I'm sticking with 9.04, thank you:P

---

### Post by philipccna on 2009-11-20
Same issue also found on my HP Mini 2140 notebook. Wifi works perfectly on the previous 9.04 version but now I cannot get it to work since I upgraded to the latest version...

---

### Post by kyle2595 on 2009-11-22
I have the same issue.  When I go to "Hardware Drivers"  the "Broadcom STA wireless driver" is listed, but I can't activate it.  I have even tried what was listed here:
[http://ubuntuforums.org/showthread.php?t=1240500](http://ubuntuforums.org/showthread.php?t=1240500)
and it still does not work. (And I was connected to a wired internet connection.)
If anyone has anything that could help, it would be much appreciated.  Thank you!

---

### Post by subckt on 2009-11-23
I had the exact same problem.  Found solution at

[http://www.linuxforums.org/forum/wireless-internet/155047-ubuntu-v9-1-wireless-problem.html](http://www.linuxforums.org/forum/wireless-internet/155047-ubuntu-v9-1-wireless-problem.html)

Basically you just do :

  sudo apt-get update
  sudo apt-get --reinstall install bcmwl-kernel-source

Then do 

  System-->Administration-->Hardware_Drivers

and then this time you should be able to activate the driver

-- subckt

---

### Post by kyle2595 on 2009-11-23
I had tried that as well, nothing seams to work.

---

### Post by batchelar on 2009-11-26
i am a relative newbie to ubantu and linix  have used it limited in the past
i have an acer one  that was running linpus  now ubantu 9.1
i have my wired connection going and working fine.
I have a wireless  connection set up with teh proper password but when i try to use my wireless it says it is disabled. I click teh button to enable wireless on teh body of teh computer and nothing happens. is there anything else i can do?

---

### Post by karthick ayyapillai on 2010-03-05
hi 
i have just upgraded to Ubuntu 9.1 from ubuntu 8 version using live DVD 
I faced the same wireless problem. My system already was not having wireless working i was using a netgear adapter for both windows and linux when i tried first without the adapter it was not working but it started to work when i restarted with netgear adapter connected to the system.I even
tried
sudo apt-get install wicd
its not in repository

when i tried to restart the system i got a message that both atheros and netgear adapter were disabled in the wireless config switch if any one knows the solution please help
I use a siemens amilo 1718 laptop . No windows partition entire linux partition.

---

### Post by niceguy123 on 2010-04-06
> **subckt said:**
> I had the exact same problem.  Found solution at

[http://www.linuxforums.org/forum/wireless-internet/155047-ubuntu-v9-1-wireless-problem.html](http://www.linuxforums.org/forum/wireless-internet/155047-ubuntu-v9-1-wireless-problem.html)

Basically you just do :

  sudo apt-get update
  sudo apt-get --reinstall install bcmwl-kernel-source

Then do 

  System-->Administration-->Hardware_Drivers

and then this time you should be able to activate the driver

-- subckt

I did this and >  System-->Administration-->Hardware_Drivers

and got an empty Hardware Drivers window with this headline:

```
No proprietary drivers are in use on this system
``` 

BTW - for the first few days after upgrading to 9.1 I had no problem connecting to the wifi. But for the past few hours I have had no luck.

---

### Post by K6MLE on 2010-04-07
Out of nothing more than frustration, I think it best to wait until 10.1 comes out and once again try wireless on this Acer Aspire 4520.  How can I roll this laptop back from 9.1 to 9.04?  Is there a way to do it that doesn't require wiping the hard drive and starting from scratch?

---

### Post by jjwheeler2 on 2010-04-09
To all of you having problems with 9.1 try downloading the program Wifi Radar off the software center. It fixed my Wifi problems with Ubuntu on a Dell 1521 with the Broadcom 4401 card.

---

### Post by manixdk on 2010-05-28
> **K6MLE said:**
> Out of nothing more than frustration, I think it best to wait until 10.1 comes out and once again try wireless on this Acer Aspire 4520.  How can I roll this laptop back from 9.1 to 9.04?  Is there a way to do it that doesn't require wiping the hard drive and starting from scratch?

There isn't, AFAIK. I've now had the same problem twice. I just don't have the time of patience to do it again. So I backed up all my files and am using my Win box, waiting for the next "downgrade":(:cool:

---

### Post by chrisknowles on 2010-08-02
Wow, and I thought it was just me.  Is there an easy way to fix this for xubuntu without reattaching to a wired network?

---

### Post by K6MLE on 2010-08-02
I finally went with Ubuntu 10.04 and all went pretty smoothly.  Wireless now works on my Acer Aspire.

---

