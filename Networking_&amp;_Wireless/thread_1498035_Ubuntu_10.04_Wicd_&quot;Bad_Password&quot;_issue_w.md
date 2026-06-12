---
title: "Ubuntu 10.04 Wicd &quot;Bad Password&quot; issue with DWA-125"
date: 2010-05-31
forum: Networking &amp; Wireless
---

### Post by betachild on 2010-05-31
I have followed everything according to the the post by:

[http://ubuntuforums.org/showthread.php?t=1289917](http://ubuntuforums.org/showthread.php?t=1289917)

I got through everything, was able to install wicd and scan the available networks, however when I connect to my own network with WPA2, it always gives me "Bad Password" when authenticates. I tried also using WPA and WEP, nothing worked. Even when I put the security to none, it connects, but for something reason wasn't connecting to any web sites when browsed using firefox; however the status shows connected and the router shows registered when logged into 192.168.0.1. 

I tried uninstall network manager and then restart with wicd, same problem. 

The wired network is managed without any problem. The adapter works under windows 7 and XP flawlessly.

And also wicd ask for password everytime the computer starts to gain control of the network cards. is there any way to cancel that?

Thanks in advance

---

### Post by betachild on 2010-05-31
bump

---

### Post by TheOneHidalgo on 2010-06-01
I had this same problem for a while, and I found a solution that seems to work.

Chances are, network manager is still installed, which very well may be the source of your problem. Open the terminal and try the following commands:

sudo apt-get remove network-manager
sudo /etc/init.d/wicd restart


I hope this helps.


Source: Post #18

[https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/540070](https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/540070)

Sorry, I didn't see where you said you've already tried uninstalliing network-manager and restarting wicd.

---

### Post by kat3c on 2010-06-01
I just had the very same problem.  Trying to uninstall network manager via the software center didn't seem to work.  Said it was not installed, but it obviously still was.  Uninstalling via the terminal really did work, however.  Wicd worked fine then and connected to my wireless (wrt54g) just fine.

---

### Post by iReboot on 2010-06-09
I have the same problem.  

Atheros AR5212 wireless card, 10.04 installed on a lenovo T61.

I'm using wicd, because network manager hasn't worked for me since Hardy Heron.

---

### Post by SaintDanBert on 2010-06-14
1.  There are several other threads with this same or very similar problem. Perhaps someone might merge them.

2.  How do I know if I'm fighting an incomplete removal of network-manager
vs. a new install of wicd?

3.  How do I sort all of this out from the terminal if the desktop tools are not doing the correct things to remove network-manager and add wicd?

4.  Do you need a running eth0 network while all of this is trying to happen?

5.  Is there some way to use the DVD iso contents for package add?

6.  How long is it til closing time?

---

### Post by ponyone on 2010-06-15
I am also having the same problem also with a wrt54g. Was fine before I updated to 10.04 now I can not connect to wireless through either my toshiba portege wireless built-in card or an asus usb-n13 i got.

Did a terminal remove for network manager and in installed wicd, rebooted and still getting problems.

Can connect with wired connection and can connect to wireless if I turn of any encryption. But with encryption it always comes back with "bad password".... and yes I tried all types wep, wpa, wpa2 with passphrase and keys.

To SaintDanBert : yes you need a wired connection to change from network manager to wicd (which i like better) ... and closing time is in 4 hours !

---

### Post by ponyone on 2010-06-17
As an update... tried several linux LiveCd's like Puppy Linux and Slax and the card is not even seen. Tried using Ubuntu 8.04.4 and had no problems at all connecting !! Will continue to try newer versions until it fails again. Somewhere along the way something changed in the distributions that causes a problem using encryption.

---

### Post by SaintDanBert on 2010-06-18
> **ponyone said:**
> 
...
To SaintDanBert : yes you need a wired connection to change from network manager to wicd (which i like better) ... and closing time is in 4 hours !

Access to the net has become so ubiquitous that we might step back and think about things in cold-iron or deep-recovery situations.  
[list]
[*]If all of our docs are online, how do we read the steps needed to tackle recovery tasks
[*]If the iron is cold, even local copies of docs are not available
[*]I don't remember seeing article using the distro CD or DVD media
to tinker systems during networking troubles. I don't remember ever seeing discussion of using the media -- does it work?
[*]cloud thinking is shifting more and more system details "out there" on our LAN or even WAN or public net. What does one do if the LAN is down? 
[/list]

Project effort anyone?
~~~ 0;-Dan

---

### Post by negativ on 2010-06-23
I have this same problem on a 10.04 box.  Two other machines running Arch Linux with wicd work fine.  network-manager is not installed.

---

### Post by PoseidonOSU on 2010-06-24
has this issue been resolved in any of the other threads?

---

### Post by SaintDanBert on 2010-06-25
> **ponyone said:**
> 
Did a terminal remove for network manager and in installed wicd, rebooted and still getting problems.


I found that I kept getting more than one copy of wpa_supplicant started on reboot. Never discovered why.

I disconnected from all networking, and used my hardware switch to turn off wifi.  After reboot, I removed network-manager and wicd both.

After another reboot, I turned on the wireless and installed wicd.
Happy happy joy joy.  No more troubles.

> **ponyone said:**
> 
To SaintDanBert : yes you need a wired connection to change from network manager to wicd (which i like better) ... and closing time is in 4 hours !

I'm partial to Black-and-Tan ... without the politics ... and Grants, in a snifter.

---

### Post by ajg0 on 2010-07-26
I have seen the same problem every time my kernel is updated. No amount of reboot/clean up has helped. I use wicd after removing network manager a while ago.

I was only able to resolve it after removing my wireless USB card and re-inserting. This also resolved my network problem when booting into Ubuntu after Windows Vista (I have dual boot). 

Could this be some residual config on the usb card that gets reset by removing and re-inserting the usb card?  It would be great to see this issue resolved.

---

### Post by elasticsoul on 2010-07-27
I can't connect wirelessly either. Wired, no problem. Wireless, as described by others, no matter what I do I keep getting "bad password."
 
Currently trying to connect to the work network, and more weirdness happens:
[LIST=1]
[*]I uninstalled Network Manager per the instructions above.
[*]Using WICD, viewed the available networks.
[*]Clicked Connect for my work network.
[*]Bad Password.
[/LIST]

---

### Post by elasticsoul on 2010-07-27
Just tried on the work network, still bad password. Trying Fedora now...

---

### Post by blamothe on 2010-08-30
brand new ubuntu user (just switched from gentoo). things have worked, great, but i've had the same "bad password" problems. i used to get the "bad password" error whenever i tried to connect, but after completely removing network manager as this thread suggests, i stopped getting the error on boot. however, when i put the machine to sleep and bring it back up, i get the "bad password" error again. i'm runing ubuntu 10.04 on a macbook pro 5,1 with the broadcom card using the broadcom-sta drivers.

---

### Post by Exurgency on 2010-09-18
Semi bump. 

Everything went to hell after the last update. network-manager started having this avahi-related 'cannot connect because of .local domain' spazzing, prompting me to switch to wicd, which has been getting 'Bad password' since. 

Running on a simple ralink RT2860.

Hopefully someone can fix this.

---

### Post by pwabrahams on 2010-10-17
I too was struggling with the Bad Password issue.  I uninstalled both Network Manager and wicd and then reinstalled Network Manager.  The Bad Password problem has gone away now, though I had to start the wireless connection explicitly (until I marked it for automatic startup).

I guess that at this point it's possible to bypass Bad Password using either wicd or networkmanager, but you have to get the sequence just right.  As long as I have a working arrangement I'm not inclined to disrupt it to experiment further.

---

### Post by swells5 on 2010-10-20
10.10 DWA-125 tried to remove network-manager from CLI and got postgresql errors. It says that network-manager is not installed then gives
---------------

Package network-manager is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 40 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up postgresql-common (111) ...
 * Starting PostgreSQL 8.4 database server                                       * The PostgreSQL server failed to start. Please check the log output:
2010-10-20 08:30:29 EDT FATAL:  could not create shared memory segment: Invalid argument
2010-10-20 08:30:29 EDT DETAIL:  Failed system call was shmget(key=5432001, size=36880384, 03600).
2010-10-20 08:30:29 EDT HINT:  This error usually means that PostgreSQL's request for a shared memory segment exceeded your kernel's SHMMAX parameter.  You can either reduce the request size or reconfigure the kernel with larger SHMMAX.  To reduce the request size (currently 36880384 bytes), reduce PostgreSQL's shared_buffers parameter (currently 4096) and/or its max_connections parameter (currently 103).
	If the request size is already small, it's possible that it is less than your kernel's SHMMIN parameter, in which case raising the request size or reconfiguring SHMMIN is called for.
	The PostgreSQL documentation contains more information about shared memory configuration.
                                                                         [fail]
invoke-rc.d: initscript postgresql, action "start" failed.
dpkg: error processing postgresql-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of postgresql-8.4:
 postgresql-8.4 depends on postgresql-common (>= 109~); however:
  Package postgresql-common is not configured yet.
dpkg: error processing postgresql-8.4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql:
 postgresql depends on postgresql-8.4; however:
  Package postgresql-8.4 is not configured yet.
dpkg: error processing postgresql (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 postgresql-common
 postgresql-8.4
 postgresql
E: Sub-process /usr/bin/dpkg returned an error code (1)
-------------
after that reboot  and wicd still gives 'bad password' error.
anyone have any thoughts?
I tried reinstalling postgresql, removing it competely and reinstalling it but no luck
Steve

---

### Post by Rgibbons on 2010-10-21
I have the exact same bad password using Ubuntu 10.04 on my Powerbook G4.

I noticed that my wireless security on my Airport Extreme is set for WPA Personal, but the only choices on WICD are WPA 1/2. Could this be the problem?

It is also asking for a "key" instead of the "password" that Airport Extreme uses. Are they the same thing?

---

### Post by Rgibbons on 2010-10-21
Just found the solution on another site. You must use a hexidecimal form of your password. When you enter a passphrase, WPA is meant to create a key by hashing that passphrase.

Now I have to change it on all my macs.

---

### Post by jimwg on 2010-10-25
Please please help me out with this issue that I've been struggling with since Sept. I've a G3 900mhZ iBook running Wicd on Ubuntu 10.04 and a eMac running 10.4.11. My iBook can only link with the eMac via an unsecured (no password) connection. I've done the WEP Key Maker route and it doesn't work for me but I think I just might be doing things wrong. On my eMac's Shared Airport panel I only have WEP encryption options to create WEP key lengths at 128 or 40 bits. WEP Key Maker states you you must insert a "$" at the beginning of its key to work in Airport, but if I do that the key becomes 13 digits long and Airport rejects that. So even if use that 13-digit length key in the WEP HEX panel on Wicd it doesn't work. Or is there a "trick" to this? Could it be that Wicd expects WPA instead of WEP but my iBook's Airport card only takes WEP? I know I sound confused and I guess I am! I REALLY don't want to use an unsecured connection in a densely populated city, so I'd me beholden to anyone who can help me step by step!

Thanks!

JimWG

---

### Post by moughan on 2010-11-06
I found a solution that's persistent last night on my Acer Aspire, running the Kubuntu netbook setup. 

Running both WICD and Network-manager. I went into Network-Manager and **deleted the wireless profile **that were setup when I upgraded to 10.04.  I then setup a new one with my password, and rebooted.  

Worked!

I've rebooted several times to check it, and no more "Bad Password" problems..

I'll try the same "solution" on my Dell laptop tonight.

---

### Post by cybertoon on 2010-12-05
> **TheOneHidalgo said:**
> I had this same problem for a while, and I found a solution that seems to work.

Chances are, network manager is still installed, which very well may be the source of your problem. Open the terminal and try the following commands:

sudo apt-get remove network-manager
sudo /etc/init.d/wicd restart


I hope this helps.


Source: Post #18

[https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/540070](https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/540070)

Sorry, I didn't see where you said you've already tried uninstalliing network-manager and restarting wicd.


worked for me ! :) thanks

---

### Post by diego73 on 2010-12-05
This is that work for me.
 
 After try network manager, wicd, change router configuration and wpa_supplicant without any positive results to connect to my house wireless, then I decide to update the kernel version of my notebook from 2.6.32.xx to 2.6.35.22 and congratulations that work.

Some Data:
   Distro: Ubuntu 10.04
 Notebook: Sony Vaio VGN-N320E
 Router: Linksys WRT160N V3

Steps to kernel update:
   ```

sudo apt-get update
 sudo apt-get dist-upgrade

```Now i enjoy my wifi :D!!!!!!

For more see:
[http://ubuntuforums.org/showthread.php?t=1560502](http://ubuntuforums.org/showthread.php?t=1560502)

---

### Post by Biohmmwv on 2011-02-02
> **TheOneHidalgo said:**
> I had this same problem for a while, and I found a solution that seems to work.

Chances are, network manager is still installed, which very well may be the source of your problem. Open the terminal and try the following commands:

sudo apt-get remove network-manager
sudo /etc/init.d/wicd restart


I hope this helps.


Source: Post #18

[https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/540070](https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/540070)

Sorry, I didn't see where you said you've already tried uninstalliing network-manager and restarting wicd.


Thanks! That worked for me.

---

### Post by this_costs_more_cell_bill on 2011-02-17
> **Rgibbons said:**
> Just found the solution on another site. You must use a hexidecimal form of your password. When you enter a passphrase, WPA is meant to create a key by hashing that passphrase.

Now I have to change it on all my macs.
really?! I know the hexadecimal for a decimal, but I can't figure out what hexadecimal conversion can be made on a string!

---

### Post by this_costs_more_cell_bill on 2011-02-17
> **Biohmmwv said:**
> Thanks! That worked for me.
me too

---

### Post by whatthefunk on 2011-02-25
I have similar problems.  I uninstalled the original network manager and put on Wicd.  It worked perfectly for a couple weeks, then I started getting the Bad Password message and couldnt connect at all.  I reinstalled the OS, ditched network manager again and put up Wicd.  It worked for two weeks and then gave out again.

Ive reinstalled Network Manager, but it isnt working now either.

Ive tried every "fix" in this thread and countless others but nothing works.

Does anybody have a fix for this?????  What good is a laptop if I cant connect to the internet?  Is there another distro that actually allows you to connect to the internet without three months of banging your head against the wall?

---

### Post by RagingOcelot on 2011-03-05
> **TheOneHidalgo said:**
> I had this same problem for a while, and I found a solution that seems to work.

Chances are, network manager is still installed, which very well may be the source of your problem. Open the terminal and try the following commands:

sudo apt-get remove network-manager
sudo /etc/init.d/wicd restart


I hope this helps.


Source: Post #18

[https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/540070](https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/540070)

Sorry, I didn't see where you said you've already tried uninstalliing network-manager and restarting wicd.

Thanks! It worked for me. Now it'll be interesting to see how well it holds up.

---

### Post by tafra on 2011-03-06
So, just one tip after few days not so well spent...

Bad password error was haunting me, and after a while i went to check router settings again. 

There it was, wrong mac num. in filter :(

Bad password is not about password at all here. Now wpa-psk2 is working flawless.

All i wanted to say check that first, i didnt! ;D

---

### Post by askrabal on 2011-05-23
> **TheOneHidalgo said:**
> I had this same problem for a while, and I found a solution that seems to work.

Chances are, network manager is still installed, which very well may be the source of your problem. Open the terminal and try the following commands:

sudo apt-get remove network-manager
sudo /etc/init.d/wicd restart


I hope this helps.


Source: Post #18

[https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/540070](https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/540070)

Sorry, I didn't see where you said you've already tried uninstalliing network-manager and restarting wicd.


I just had this problem and couldn't figure it out. I tried this and it worked perfectly. Thanks a bunch!!!!

---

### Post by countryranger on 2011-09-20
I am at my wits end.  I am having this exact same problem, but it appears each fix is for a slightly different problem that plagues this system.  OK here is my experience with "BAD PASSWORD"

Router: Belkin
Antennae: Netgear N300 USB WiFI Adapter (Just bought because I thought my old USB had died)

**Tried setting encryption on router to WPA and to WPA2 individually instead of WPA/WPA2 several times #NO RESULT**

I**nstalled NDISWRAPPPER to get the drivers installed and blacklisted any drivers I could find that appeared in any possible solution #Got Ubuntu to recognize the USB Device **

```

mark@mark-PE542A-A-A614N:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: /etc/modprobe.d/blacklist.conf line 56: ignoring bad line starting with 'Unknown'
WARNING: /etc/modprobe.d/blacklist.conf line 57: ignoring bad line starting with 'Run'
bcmwlhigh5 : driver installed
    device (0846:9020) present

mark@mark-PE542A-A-A614N:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0458:0007 KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0846:9020 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```Printout of /etc/modprobe.d/blacklist.conf
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
Unknown option -e
Run 'gedit --help' to see a full list of available command line options.
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb

```**Installed wicd and removed network-manager and network-manager-gnome** using command line #BAD PASSWORD

Ran gedit on every config file I could find for wicd #everything appears ok
here are the printouts anyway passkey is included as 54441344, 

```

**/etc/wicd/wireless-settings.conf**
[94:44:52:22:46:22]
afterscript
dhcphostname = mark-PE542A-A-A614N
bssid = 94:44:52:22:46:22
ip
use_dhcphostname = 0
dns_domain
gateway
use_global_dns = 0
encryption = True
postdisconnectscript
beforescript
hidden = False
channel = 6
mode = Managed
psk = a0bcf75bbbdb10f65b4b4b13b70415e644c93f01bc9cedd62e98e5d4f08da280
has_profile = True
netmask
key = 54441344
usedhcphostname = False
predisconnectscript
enctype = wpa-psk
dns3
dns2
dns1
use_settings_globally = 0
use_static_dns = 0
apsk = "54441344"
encryption_method = WPA2
essid = Belkin.3622
automatic = True
search_domain

**/var/lib/wicd/configurations/**944452224622

ap_scan=1
ctrl_interface=/var/run/wpa_supplicant
network={
       ssid="Belkin.3622"
       scan_ssid=0
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk="54441344"
}


```I have restarted wicd several times and rebooted more times than I can count.  Any further insight is welcome.

---

### Post by ponyone on 2011-09-21
I found that as soon as I upgraded to Ubuntu 11.02 everything worked just fine!
:KS

---

### Post by countryranger on 2011-09-21
I am using 11.04 with all updated kernels... still no luck

---

### Post by wgato on 2011-10-02
I am also having this problem and have tried everything.

i could use the internet fine until i ran some updates.
now i get 'bad password' every time i to get online. i am using wpa.
removing network-manager does not solve the problem.

i can connect to my friends network for about 10 minutes and then i am disconnected.  he is using wep.

if wicd is the problem, what other software can i use?

---

### Post by CurJam on 2011-10-12
> **TheOneHidalgo said:**
> I had this same problem for a while, and I found a solution that seems to work.

Chances are, network manager is still installed, which very well may be the source of your problem. Open the terminal and try the following commands:

sudo apt-get remove network-manager
sudo /etc/init.d/wicd restart


I hope this helps.




I confirm that this solution worked for me too.

---

### Post by berzerk_br on 2012-01-05
It has been several days reading countless forums in search for a solution for the "bad password" issue... None worked for me. Now that I found a solution on my own that I couldn't see anywhere else, I decided to share.

I have a Dell Vostro 1310 notebook with BT5 (2.6.39.4) and Windows Vista, and my network card is the RTL8169. The wired connection works, but no luck with wireless under RT5; in Vista it worked perfectly.

I tried many proposed fixes which did not work, such as (not in any particular order):
- uninstall wicd and reinstall
- removed network-manager (since I didn't have it, I installed and uninstalled it)
- change the wifi channel of my router
- changed my router's encryption type (TKIP/AES), mode (WPA/WPA2), SSID, etc 
- disabled the wake on lan under windows
- downloaded, compiled and installed the latest driver from Realtek under BT5
- downloaded the latest Realtek driver for Windows
- used wpa_supplicant manually to connect (this is when I was sure it isn't a wicd issue)
- tried all available drivers on wpa_supplicant (such as wext)
- reinstalled BT5
- added b43 to load up at boot
- downgraded kernel
- disabled the rx offload on my eth0

I did many other things that I can't even remember... Even opened up my laptop and cleaned the board! :)

Well... finally I found the solution. The problem in my case is with the RTL8169 architecture, it seems. 

Since my computer is a Dell and despite the fact that I had already installed the latest official Realtek driver on both Windows and RT5, I decided to try one last desperate attempt. I went on Dell's support site and downloaded their latest network driver package for my machine and installed it on WINDOWS. I rebooted and went into RT5 to test, and to my surprise, it worked on the first try and has been working since then.

The only possible explanation I can come up with is that the Dell update (which was over 50Mb) had also a firmware upgrade embedded, which fixed some issue with the NIC that was the cause of the problems in RT5. Crazy, but worked.

My advice to all those who have not been able to fix the "bad password" or any other wireless connectivity problem is to get the computer manufacturer's update for the network card instead or the card's manufacturer (Realtek in this case). Do it on Windows if you have dual boot, it is likely that they care more for those clients and work harder on the updates.

This may work for other brands and other distros, it may be worth a shot. 

I hope this helps anyone with the issue. Just as a reminder, my config was DELL + BT5 + VISTA + RTL8169.

Take care,
-Ricardo

---

### Post by james3760 on 2012-01-08
Got to Preferences, then advanced settings and under driver, change it from RALINK, ATMEL or whatever it is set at, to WEXT.

It almost always has to be set at WEXT.

---

### Post by wayover13 on 2012-04-18
Someone wake me up when this issue finally gets fixed/resolved. I suspect it has to do with all the auto-configuration the *buntus seem to think they need to do for everyone now (my own issues relate to Lubuntu, btw). I've given up on wicd for now--which, in my attempts, would allow me to connect maybe once in every 30 tries.

I need a wifi manager that's going to work with the evilwm minimalist window manager, which is why I turned to wicd. network-manager in its standard guise isn't going to work with any system that doesn't have a taskbar/tray arrangement. So I've now turned to the command line version, cnetworkmanager.

cnetworkmanager -d -a shows you the network interface names on your computer and the wifi networks it's detected. Then sudo cnetworkmanager -C detected-essid --wpa-pass=password (for wpa encrypted networks) will get you online. It'll work for now, until this wicd/network-manager incompatibility issue gets ironed out.

James

PS Connecting to a wifi network using cnetworkmanager requires superuser privileges.

---

