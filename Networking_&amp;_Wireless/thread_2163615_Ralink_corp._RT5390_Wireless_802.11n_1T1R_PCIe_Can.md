---
title: "Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe Can not connect to wifi"
date: 2013-07-19
forum: Networking &amp; Wireless
---

### Post by korn16ftl3 on 2013-07-19
i normally dual boo my laptops so in the process of setting up a newly obtained laptop i decided to use a different variant of ubuntu, lubuntu 13.04 desktop amd64  (i normally use backtrack or kubuntu) i partitioned every thing and began set up...upon completion of set up i immediately tried to connect to the internet via my wifi (Ralink corp. RT5390 Wireless) and i know i have input the WEP key correctly all i can see is the connecting symbol in the lower right and after about 3 minutes of it attempting to connect it says in the upper right disconnected...even tho i have never connected.

further more upon researching how to get some kind of analisis i found the following thread:
[http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385](http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385)

so i followed those directions and am now going to post the results the file here and hope some one will be able to make sense of the mess:

```


*************** info trace ***************


***** uname -a *****


Linux user-HP-2000-Notebook-PC 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring


***** lspci *****


06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:3577]
    Kernel driver in use: r8169
07:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Hewlett-Packard Company U98Z077.00 Half-size Mini PCIe Card [103c:1636]
    Kernel driver in use: rt2800pci


***** lsusb *****


Bus 001 Device 002: ID 0bc2:3008 Seagate RSS LLC 
Bus 002 Device 002: ID 058f:a001 Alcor Micro Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


***** iwconfig *****


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


***** rfkill *****


0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


***** lsmod *****


rt2800pci              18582  0 
rt2800lib              66507  1 rt2800pci
rt2x00pci              14519  1 rt2800pci
rt2x00lib              54869  3 rt2x00pci,rt2800lib,rt2800pci
mac80211              606457  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              510937  2 mac80211,rt2x00lib
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib


***** nm-tool *****


NetworkManager Tool


State: disconnected


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    belkin.fb8:      Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    11FX07010372:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WEP




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off






***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


***** iwlist *****


wlan0     No scan results




***** resolv.conf *****




***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


***** dmesg *****


[   18.686396] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.687162] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   77.227116] wlan0: authenticate with <MAC address removed>
[   77.242509] wlan0: direct probe to <MAC address removed> (try 1/3)
[   77.445447] wlan0: direct probe to <MAC address removed> (try 2/3)
[   77.649010] wlan0: direct probe to <MAC address removed> (try 3/3)
[   77.852851] wlan0: authentication with <MAC address removed> timed out
[   79.052206] wlan0: authenticate with <MAC address removed>
[   79.059866] wlan0: direct probe to <MAC address removed> (try 1/3)
[   79.262736] wlan0: direct probe to <MAC address removed> (try 2/3)
[   79.466426] wlan0: direct probe to <MAC address removed> (try 3/3)
[   79.670125] wlan0: authentication with <MAC address removed> timed out
[   93.060057] wlan0: authenticate with <MAC address removed>
[   93.066676] wlan0: direct probe to <MAC address removed> (try 1/3)
[   93.269823] wlan0: direct probe to <MAC address removed> (try 2/3)
[   93.473535] wlan0: direct probe to <MAC address removed> (try 3/3)
[   93.677209] wlan0: authentication with <MAC address removed> timed out


****************** done ******************



```

---

### Post by varunendra on 2013-07-19
Welcome to the forums korn16ftl3 !
> **korn16ftl3 said:**
> ....hope some one will be able to make sense of the mess:
Ohh.. please don't call my beloved piece of text a mess !! :P

Which one of these is your wireless access point? -
```

  Wireless Access Points 
    belkin.fb8:      Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    11FX07010372:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WEP

```
If it is the first one, try changing the encryption mode in your router to pure WPA2-PSK only, with AES instead of TKIP. Currently it is in WPA/WPA2 mixed mode.

If it is the second one, you may try WPA2 as it is more secure and works better with Linux. Not necessary though.

After changing the encryption type in the router (if you can), reboot the router.

In the laptop, please do the following -
```
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci nohwcrypt=Y
```
..then try to connect. If it helps connecting, we can make the 'nohwcrypt' parameter permanent (above will be temporary and will be lost at reboot).

However, if it doesn't help, you may try the proprietary driver from realtek, as mentioned in post #4 here : [http://ubuntuforums.org/showthread.php?t=2160399&p=12732190#post12732190](http://ubuntuforums.org/showthread.php?t=2160399&p=12732190#post12732190)

But try to make the native one work first, as the proprietary one will need to be rebuild-reinstalled each time you have a kernel upgrade.

Let us know how it goes.

---

### Post by korn16ftl3 on 2013-07-19
> **varunendra said:**
> Welcome to the forums korn16ftl3 !

Ohh.. please don't call my beloved piece of text a mess !! :P 

lol dont take the mess comment personally to me i have no idea what that is but to some one like u its a road map to what is wrong :-)

>  
Which one of these is your wireless access point? -
```

  Wireless Access Points 
    belkin.fb8:      Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    11FX07010372:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WEP

```
If it is the first one, try changing the encryption mode in your router to pure WPA2-PSK only, with AES instead of TKIP. Currently it is in WPA/WPA2 mixed mode.

If it is the second one, you may try WPA2 as it is more secure and works better with Linux. Not necessary though.

After changing the encryption type in the router (if you can), reboot the router. 

 11FX07010372 is my AP and i dont have any direct control over the router/ap its self sadly...how ever can verify it works fine on my windows 7 partition 

> 
In the laptop, please do the following -
```
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci nohwcrypt=Y
```
..then try to connect. If it helps connecting, we can make the 'nohwcrypt' parameter permanent (above will be temporary and will be lost at reboot).

However, if it doesn't help, you may try the proprietary driver from realtek, as mentioned in post #4 here : [http://ubuntuforums.org/showthread.php?t=2160399&p=12732190#post12732190](http://ubuntuforums.org/showthread.php?t=2160399&p=12732190#post12732190)

But try to make the native one work first, as the proprietary one will need to be rebuild-reinstalled each time you have a kernel upgrade.

Let us know how it goes.

i will attempt these as well, i have also decided to possibly try switching  my WiFi mini PCIe cards around as well as i have got various laptop parts lying around and thought perhaps Lubuntu might like diferant hardware better than others....how ever the computer i have found does not necessarily as the first card i tried putting in mad the laptop boot up with a [FONT=HPRegular][COLOR=#000000]**_*wlan module id (702) wireless module not supported error*_** so i will be trying various things i have around to try to resolve this ....when restoring the OS and checking the recommended driver updates online in windows 7 i seen a BIOS update i am now preparing to do that as well....perhaps this may change the outcome of something as well....i will be posting back shortly and list any thing i have changed and/or more logs for other WiFi cards as well (if i have any others that will work with this picky thing).

also thank you for the warm welcome :-)

ok so... UPDATE:

I did the following_ WITH OUT changing router encryption _because as i stated above i do not have direct control over the router/AP

[/COLOR][/FONT]> 
In the laptop, please do the following -
```
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci nohwcrypt=Y
```
..then try to connect. If it helps connecting, we can make the 'nohwcrypt' parameter permanent (above will be temporary and will be lost at reboot).


i completed the first part: sudo modprobe -rfv rt2800pc, and a few lines scrolled by saying rmod rt2800pci and several other things.....i then attempted to connect again...nothing.
i typed the second part of your instructions: sudo modprobe -v rt2800pci nohwcrypt=Y several longer lines appeared insmod /lib/modules/3.8.0-19-generic/kernal/lib/crc-ccitt.ko and several other various line came across...at this point in time it seemed as tho the computer decided to try to reconnect how ever failed and once again said disconnected in the upper right corner

> 
However, if it doesn't help, you may try the proprietary driver from realtek, as mentioned in post #4 here : [http://ubuntuforums.org/showthread.php?t=2160399&p=12732190#post12732190](http://ubuntuforums.org/showthread.php?t=2160399&p=12732190#post12732190)

But try to make the native one work first, as the proprietary one will need to be rebuild-reinstalled each time you have a kernel upgrade.

Let us know how it goes.

how can i do the proprietary driver instructions from the listed post from another computer that only runs windows 7?

/facepalm
[http://askubuntu.com/questions/303415/ubuntu-13-04-ralink-rt5390-wont-work-after-upgrade](http://askubuntu.com/questions/303415/ubuntu-13-04-ralink-rt5390-wont-work-after-upgrade)
its even an HP2000 LOLOL wow

---

### Post by varunendra on 2013-07-19
> **korn16ftl3 said:**
> /facepalm
[http://askubuntu.com/questions/303415/ubuntu-13-04-ralink-rt5390-wont-work-after-upgrade](http://askubuntu.com/questions/303415/ubuntu-13-04-ralink-rt5390-wont-work-after-upgrade)
its even an HP2000 LOLOL wow

No need to facepalm, I didn't notice that link in the referred post either (just realised after following both :P).

In case you are still having trouble, just download the packages on the other system which is connected to internet > copy the downloaded packages (the .bz2 and the patch) to your Home folder in Ubuntu, and do the rest as mentioned in the post (or the askubuntu page).

I'm sure it'll work as your os version/architecture is same as the op in that thread. But I'm keen to know about its performance. :)


**PS:**
Since you seem interested (or I assumed), the '-r' option in the first modprobe command removes the driver (so you can reload it with the new parameter), so it obviously disables the wireless for that moment. The next one loads it again with the 'nohwcrypt' parameter (which shifts the load of encryption from the card's hardware to the OS). The '-v' parameter makes the command verbose, so you could see what would have otherwise happened in the background.

---

### Post by korn16ftl3 on 2013-07-19
> **varunendra said:**
> 
In case you are still having trouble, just download the packages on the other system which is connected to internet > copy the downloaded packages (the .bz2 and the patch) to your Home folder in Ubuntu, and do the rest as mentioned in the post (or the askubuntu page).

I'm sure it'll work as your os version/architecture is same as the op in that thread. But I'm keen to know about its performance. :)

ok so download the link in that post we just figured out was about my computer and the rest is done via the xterm cmd prompt then?

because...well the directions look like spanish to me lol.

i was never a major linux user.....i have just dabbled in it before and like having a back-up OS so i can recover things if my windows OS gos completely FUBAR or un-bootable for reasons other than hardware failure

> 
**PS:**
Since you seem interested (or I assumed), the '-r' option in the first modprobe command removes the driver (so you can reload it with the new parameter), so it obviously disables the wireless for that moment. The next one loads it again with the 'nohwcrypt' parameter (which shifts the load of encryption from the card's hardware to the OS). The '-v' parameter makes the command verbose, so you could see what would have otherwise happened in the background.

so its like an ipconfig /release and ipconfig /renew but for driver is what it kinda sounds like u are explaining

---

### Post by varunendra on 2013-07-19
> **korn16ftl3 said:**
> ok so download the link in that post we just figured out was about my computer and the rest is done via the xterm cmd prompt then?

Make sure to copy those downloaded packages in your "Home" folder *(the one that opens by default when you open the "File browser")*. Then open the terminal from either the menu or by the shortcut key - Ctrl+Alt+T. Its working directory by default be your Home *(that's why we need the files to be there)*.

Once the files are in place, and the terminal is open, just enter the commands as mentioned in the post (one at a time > let it finish its job > enter next one). When asked for password, you will have to type your login password. You won't see anything in the terminal while typing the password, just type it correctly and press "Enter" key.

If you are confused about the 'Home' thing, forget it, it's not that important to do it the same way. Just copy the downloaded file to your desktop, and enter this command in the terminal -
```
cd ~/Desktop
```
This will change the working directory of the terminal to the Desktop. Follow the rest of instructions exactly as in the post thereafter.

Feel free to ask if you still have any problems or if you get any errors during the process.

---

### Post by korn16ftl3 on 2013-07-19
ok....step 4 it says download patch.......umm thats a link to [http://gridlox.net/diff/rt5592sta_fix_64bit_3.8.patch](http://gridlox.net/diff/rt5592sta_fix_64bit_3.8.patch) and its all txt.... ? what do i do with that?

copy paste it in notepad and make it a .patch file instead of a .txt?

---

### Post by varunendra on 2013-07-19
Yes, you can do that. Or-

Right click on the link and "Save link target as.." (or whatever similar option your browser gives).

Basically, itself is a file (with ".patch" being its extension name) that opens in the browser instead of downloading if you left click it.

It is nothing but a 'diff' file that is used by patch command to automatically change specific lines in the target file (mentioned in the .patch file itself). These changes are required to make it compatible with your OS. You can also make these changes manually if you know how to read the file (or determine what changes it is going to do and where). Patch command just automates it.

---

### Post by korn16ftl3 on 2013-07-19
OK...LOL i tried saving the txt as a .patch and it worked before u replied...i have a tenancey to underestimate myself some time i think...also worst case scenario what am i gonna do....screw something up and dump my fresh install and start again? LOL

any how on to the next bit im a little confused by that does not seem to make sense here:

.....if i type make and hit enter.....it says the program make is not currently installed. you can install it by typing: sudo apt-get install make...... well we all know i cant get that because were tying to achieve internet access to begin with....any ideas or help here?

---

### Post by varunendra on 2013-07-19
Hmm.. absence of make means you may not have other essentials as well that are required to successfully build a package. Let's install them first. Run the following command in terminal (you may copy paste) -
```
apt-get install --print-uris linux-headers-generic build-essential
```
If it asks to press Y or N to proceed, press Y. Instead of trying to download these packages to install, the command will return their download links at the bottom of the output. Copy these links to a text file. Then use these links to download the packages on another computer which is connected to internet.

Copy *ALL* of these downloaded packages to a blank folder on your Ubuntu **desktop**. Rename this folder to "**korn**" (to avoid confusion). Then open a terminal and do (mind the case of letters, as linux commands are case sensitive) -
```
cd ~/Desktop/korn
sudo dpkg -i *
```
Report back if there are any errors. It is very important that ALL the required packages are present in the "korn" folder while running 'dpkg -i'. So make sure to not miss any link.

Once these packages are installed, you may proceed from the 'make' command (make sure to be in the same directory in terminal where you have extracted the downloaded driver files).

---

### Post by varunendra on 2013-07-19
Hmm.. absence of make means you may not have other essentials as well that are required to successfully build a package. Let's install them first. Run the following command in terminal (you may copy paste) -
```
apt-get install --print-uris linux-headers-generic build-essential
```
If it asks to press Y or N to proceed, press Y. Instead of trying to download these packages to install, the command will return their download links at the bottom of the output. Copy these links to a text file. Then use these links to download the packages on another computer which is connected to internet.

Copy *ALL* of these downloaded packages to a blank folder on your Ubuntu **desktop**. Rename this folder to "**korn**" (to avoid confusion). Then open a terminal and do (mind the case of letters, as linux commands are case sensitive) -
```
cd ~/Desktop/korn
sudo dpkg -i *
```
Report back if there are any errors. It is very important that ALL the required packages are present in the "korn" folder while running 'dpkg -i'. So make sure to not miss any link.

Once these packages are installed, you may proceed from the 'make' command (make sure to be in the same directory in terminal where you have extracted the downloaded driver files).

---

### Post by korn16ftl3 on 2013-07-19
ok...now im beginning to get frustrated here.....

```
apt-get install --print-uris linux-headers-generic build-essential
```

results in the following which i did copy and paste directly from the terminal....and i did even try to add sudo once as well

```
user@user-HP-2000-Notebook-PC:~$ apt-get install --print-uris linux-headers-generic build-essentialReading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'build-essential' has no installation candidate
user@user-HP-2000-Notebook-PC:~$ sudo apt-get install --print-uris linux-headers-generic build-essential
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'build-essential' has no installation candidate
user@user-HP-2000-Notebook-PC:~$ 

```

seriously....what did i do wrong here?......is my install fubar some how?

im going to rest i have been screwing with this laptop for about 15hrs now its been quite the troubled piece of hardware between digging up a hard drive that i had to pass integrity tests and a few other things....ill be back in a few hours thanks for your help and bearing with me threw the situation its people like you that encourage me to not be so discouraged when it comes to something like Linux that im not extremely familiar with :-)

when i get up im going to see if i can not dig up a patch cord some place and try to bridge the conection from this computer to the whacked out Lubuntu computer.....this should help resolve something i would imagine....at least get some of the things i need so i can use the make cmd and such

EDIT:
ALL RIGHT LOL im bridged from one laptop to the other now.....now have u got a good way to solve this from here? LOL

---

### Post by varunendra on 2013-07-19
Yeah, open Synaptic Package Manager from menu, goto "Settings > Repositories" and make sure all software sources (except the CD/DVD in the box below) are enabled, then close the "Repository" box, "Reload" the list it and install the "linux-headers-generic" and "build-essential" packages from synaptic itself, or from the commands above (it seems the software source that provides build-essential is somehow disabled. The above is the easy way to enable all)

---

### Post by korn16ftl3 on 2013-07-19
> **varunendra said:**
> Yeah, open Synaptic Package Manager from menu, goto "Settings > Repositories" and make sure all software sources (except the CD/DVD in the box below) are enabled, then close the "Repository" box, "Reload" the list it and install the "linux-headers-generic" and "build-essential" packages from synaptic itself, or from the commands above (it seems the software source that provides build-essential is somehow disabled. The above is the easy way to enable all)

when marking linux-headers-generic 3.8.0.26.44 for REINSTALATION

```
E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Unable to lock the download directory

```

OR

```
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Unable to lock the download directory
```


im wondering if i shouldnt just dump this Lubuntu partition entirely with EASUSE in windows and re-install with this bridged and let it update as it installs....then see what kind of issues if any i run across.....even tho i already updated every thing....

i went back to this:

```
apt-get install --print-uris linux-headers-generic build-essential 
```

and the terminal read out:

```

user@user-HP-2000-Notebook-PC:~$ apt-get install --print-uris linux-headers-generic build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
linux-headers-generic set to manually installed.
The following extra packages will be installed:
  binutils dpkg-dev fakeroot g++ g++-4.7 gcc gcc-4.7 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libc-dev-bin libc6-dev
  libdpkg-perl libfile-fcntllock-perl libgcc-4.7-dev libgomp1 libitm1
  libstdc++6-4.7-dev linux-libc-dev make manpages-dev
Suggested packages:
  binutils-doc debian-keyring g++-multilib g++-4.7-multilib gcc-4.7-doc
  libstdc++6-4.7-dbg gcc-multilib autoconf automake1.9 libtool flex bison gdb
  gcc-doc gcc-4.7-multilib libmudflap0-4.7-dev gcc-4.7-locales libgcc1-dbg
  libgomp1-dbg libitm1-dbg libquadmath0-dbg libmudflap0-dbg binutils-gold
  glibc-doc libstdc++6-4.7-doc make-doc
The following NEW packages will be installed:
  binutils build-essential dpkg-dev fakeroot g++ g++-4.7 gcc gcc-4.7
  libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  libc-dev-bin libc6-dev libdpkg-perl libfile-fcntllock-perl libgcc-4.7-dev
  libgomp1 libitm1 libstdc++6-4.7-dev linux-libc-dev make manpages-dev
0 upgraded, 22 newly installed, 0 to remove and 0 not upgraded.
Need to get 27.7 MB of archives.
After this operation, 76.2 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
'http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.7/libgomp1_4.7.3-1ubuntu1_amd64.deb' libgomp1_4.7.3-1ubuntu1_amd64.deb 27276 MD5Sum:7285581224f08d9cb905b747e6890348
'http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.7/libitm1_4.7.3-1ubuntu1_amd64.deb' libitm1_4.7.3-1ubuntu1_amd64.deb 36234 MD5Sum:6e65e4e92f7ff96e2894b4b7cae7cf3d
'http://us.archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.23.2-2ubuntu1_amd64.deb' binutils_2.23.2-2ubuntu1_amd64.deb 2392896 MD5Sum:bf8a1a67d3f3004220dafa59a11fb6e7
'http://us.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc-dev-bin_2.17-0ubuntu5_amd64.deb' libc-dev-bin_2.17-0ubuntu5_amd64.deb 81378 MD5Sum:f713734128611f734d42e05b7f7976c0
'http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_3.8.0-26.38_amd64.deb' linux-libc-dev_3.8.0-26.38_amd64.deb 921322 MD5Sum:c444c3438e4f9572e4f0dcb300f750a5
'http://us.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-dev_2.17-0ubuntu5_amd64.deb' libc6-dev_2.17-0ubuntu5_amd64.deb 3088016 MD5Sum:7b8c3349ee019a814096536661388b60
'http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.7/libgcc-4.7-dev_4.7.3-1ubuntu1_amd64.deb' libgcc-4.7-dev_4.7.3-1ubuntu1_amd64.deb 2463686 MD5Sum:35245e386a0b3a6ba5e0122dbd2727a8
'http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.7/gcc-4.7_4.7.3-1ubuntu1_amd64.deb' gcc-4.7_4.7.3-1ubuntu1_amd64.deb 6088274 MD5Sum:cccb7b1b52e1fbcec5dd8fa4e0d0fa72
'http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/gcc_4.7.3-1ubuntu10_amd64.deb' gcc_4%3a4.7.3-1ubuntu10_amd64.deb 5120 MD5Sum:299396a922a032b2dc16c35d819a0a99
'http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.7/libstdc++6-4.7-dev_4.7.3-1ubuntu1_amd64.deb' libstdc++6-4.7-dev_4.7.3-1ubuntu1_amd64.deb 1704038 MD5Sum:a82b28b16a7c307c6f0d82220acaebd0
'http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.7/g++-4.7_4.7.3-1ubuntu1_amd64.deb' g++-4.7_4.7.3-1ubuntu1_amd64.deb 7993008 MD5Sum:10310c3b526c5a294b5a2f2d0b888832
'http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.7.3-1ubuntu10_amd64.deb' g++_4%3a4.7.3-1ubuntu10_amd64.deb 1448 MD5Sum:6d3fdc77e7d4fd4d2de706d70e107cff
'http://us.archive.ubuntu.com/ubuntu/pool/main/m/make-dfsg/make_3.81-8.2ubuntu2_amd64.deb' make_3.81-8.2ubuntu2_amd64.deb 119656 MD5Sum:e45c0678447ace15f908aacfce04d3e4
'http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/libdpkg-perl_1.16.10ubuntu1_all.deb' libdpkg-perl_1.16.10ubuntu1_all.deb 186276 MD5Sum:a5272a7a88d00f541882c65236734d21
'http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.16.10ubuntu1_all.deb' dpkg-dev_1.16.10ubuntu1_all.deb 712234 MD5Sum:f5d0c81b8490596c0b8909ac3326c74e
'http://us.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.6ubuntu4_amd64.deb' build-essential_11.6ubuntu4_amd64.deb 5672 MD5Sum:4cf112be35170f25981553874b2813e6
'http://us.archive.ubuntu.com/ubuntu/pool/main/f/fakeroot/fakeroot_1.18.4-2ubuntu1_amd64.deb' fakeroot_1.18.4-2ubuntu1_amd64.deb 89056 MD5Sum:5865cd6159dff6bcce9d41800cc9d0cc
'http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libalgorithm-diff-perl/libalgorithm-diff-perl_1.19.02-3_all.deb' libalgorithm-diff-perl_1.19.02-3_all.deb 49964 MD5Sum:7462f70e9e9b691ca4a4657371d6ba8e
'http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libalgorithm-diff-xs-perl/libalgorithm-diff-xs-perl_0.04-2build3_amd64.deb' libalgorithm-diff-xs-perl_0.04-2build3_amd64.deb 12542 MD5Sum:adb9ed1ba65220e8261f2a270359c488
'http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libalgorithm-merge-perl/libalgorithm-merge-perl_0.08-2_all.deb' libalgorithm-merge-perl_0.08-2_all.deb 12672 MD5Sum:bf1355aea7ab249fcd344cf0c692bc6c
'http://us.archive.ubuntu.com/ubuntu/pool/main/libf/libfile-fcntllock-perl/libfile-fcntllock-perl_0.14-2_amd64.deb' libfile-fcntllock-perl_0.14-2_amd64.deb 15774 MD5Sum:499fc3a13488e697932ac628b8d8c0ee
'http://us.archive.ubuntu.com/ubuntu/pool/main/m/manpages/manpages-dev_3.44-0ubuntu1_all.deb' manpages-dev_3.44-0ubuntu1_all.deb 1738270 MD5Sum:3f2e9ef5adcd8a40eff198b815f5d8ad
user@user-HP-2000-Notebook-PC:~$ 

```

---

### Post by varunendra on 2013-07-19
Sorry for the delay in response..

Those "held packages" problem can be solved, but reinstalling is a quicker solution (usually takes 15-20 minutes). You may go ahead with a fresh install if you haven't already.

However, if you got those links this time, it means you can also use the previous method of downloading the packages manually then installing with 'dpkg -i'.

Whatever suits you best.

---

### Post by korn16ftl3 on 2013-07-19
> **varunendra said:**
> Sorry for the delay in response..

Those "held packages" problem can be solved, but reinstalling is a quicker solution (usually takes 15-20 minutes). You may go ahead with a fresh install if you haven't already.

However, if you got those links this time, it means you can also use the previous method of downloading the packages manually then installing with 'dpkg -i'.

Whatever suits you best.

even tho reinstalling is not the best answer because i really dont learn much of any thing that way at all im going to try that, this is getting me on my last nerve lol

EDIT/UPDATE:

ok i went ahead and dumped my Lubuntu partition (and now i have something funky going on in GRUB but ill mess with that later).
first thing i did was open up the terminal and type make and hit eneter and it read out the following:
```
user@user-HP-2000-Notebook-PC:~$ makeThe program 'make' is currently not installed. You can install it by typing:
sudo apt-get install make

```

all right no major there im bridged to the internet until i can get this WiFi thing resolved so i did as directed and got as follows:
```

user@user-HP-2000-Notebook-PC:~$ sudo apt-get install make
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  make-doc
The following NEW packages will be installed:
  make
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 120 kB of archives.
After this operation, 324 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ raring/main make amd64 3.81-8.2ubuntu2 [120 kB]
Fetched 120 kB in 0s (194 kB/s)
Selecting previously unselected package make.
(Reading database ... 133110 files and directories currently installed.)
Unpacking make (from .../make_3.81-8.2ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Setting up make (3.81-8.2ubuntu2) ...

```

from here we are still thinking something is up with [COLOR=#000000]linux-headers-generic and b[/COLOR][COLOR=#000000]uild-essential because of the same make error we had to begin with so i used sudo apt-get and here are the read outs for that cmd on both of those packages:

[/COLOR]

```

user@user-HP-2000-Notebook-PC:~$ sudo apt-get install linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
linux-headers-generic set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
user@user-HP-2000-Notebook-PC:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  binutils dpkg-dev fakeroot g++ g++-4.7 gcc gcc-4.7 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libc-dev-bin libc6-dev
  libdpkg-perl libfile-fcntllock-perl libgcc-4.7-dev libitm1
  libstdc++6-4.7-dev linux-libc-dev manpages-dev
Suggested packages:
  binutils-doc debian-keyring g++-multilib g++-4.7-multilib gcc-4.7-doc
  libstdc++6-4.7-dbg gcc-multilib autoconf automake1.9 libtool flex bison gdb
  gcc-doc gcc-4.7-multilib libmudflap0-4.7-dev gcc-4.7-locales libgcc1-dbg
  libgomp1-dbg libitm1-dbg libquadmath0-dbg libmudflap0-dbg binutils-gold
  glibc-doc libstdc++6-4.7-doc
The following NEW packages will be installed:
  binutils build-essential dpkg-dev fakeroot g++ g++-4.7 gcc gcc-4.7
  libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  libc-dev-bin libc6-dev libdpkg-perl libfile-fcntllock-perl libgcc-4.7-dev
  libitm1 libstdc++6-4.7-dev linux-libc-dev manpages-dev
0 upgraded, 20 newly installed, 0 to remove and 0 not upgraded.
Need to get 27.6 MB of archives.
After this operation, 75.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ raring/main libitm1 amd64 4.7.3-1ubuntu1 [36.2 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ raring/main binutils amd64 2.23.2-2ubuntu1 [2,393 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ raring/main libc-dev-bin amd64 2.17-0ubuntu5 [81.4 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ raring-updates/main linux-libc-dev amd64 3.8.0-26.38 [921 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ raring/main libc6-dev amd64 2.17-0ubuntu5 [3,088 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ raring/main libgcc-4.7-dev amd64 4.7.3-1ubuntu1 [2,464 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ raring/main gcc-4.7 amd64 4.7.3-1ubuntu1 [6,088 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ raring/main gcc amd64 4:4.7.3-1ubuntu10 [5,120 B]
Get:9 http://us.archive.ubuntu.com/ubuntu/ raring/main libstdc++6-4.7-dev amd64 4.7.3-1ubuntu1 [1,704 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ raring/main g++-4.7 amd64 4.7.3-1ubuntu1 [7,993 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ raring/main g++ amd64 4:4.7.3-1ubuntu10 [1,448 B]
Get:12 http://us.archive.ubuntu.com/ubuntu/ raring/main libdpkg-perl all 1.16.10ubuntu1 [186 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ raring/main dpkg-dev all 1.16.10ubuntu1 [712 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ raring/main build-essential amd64 11.6ubuntu4 [5,672 B]
Get:15 http://us.archive.ubuntu.com/ubuntu/ raring/main fakeroot amd64 1.18.4-2ubuntu1 [89.1 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu/ raring/main libalgorithm-diff-perl all 1.19.02-3 [50.0 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu/ raring/main libalgorithm-diff-xs-perl amd64 0.04-2build3 [12.5 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu/ raring/main libalgorithm-merge-perl all 0.08-2 [12.7 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu/ raring/main libfile-fcntllock-perl amd64 0.14-2 [15.8 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu/ raring/main manpages-dev all 3.44-0ubuntu1 [1,738 kB]
Fetched 27.6 MB in 1min 30s (304 kB/s)                                         
Selecting previously unselected package libitm1:amd64.
(Reading database ... 133120 files and directories currently installed.)
Unpacking libitm1:amd64 (from .../libitm1_4.7.3-1ubuntu1_amd64.deb) ...
Selecting previously unselected package binutils.
Unpacking binutils (from .../binutils_2.23.2-2ubuntu1_amd64.deb) ...
Selecting previously unselected package libc-dev-bin.
Unpacking libc-dev-bin (from .../libc-dev-bin_2.17-0ubuntu5_amd64.deb) ...
Selecting previously unselected package linux-libc-dev:amd64.
Unpacking linux-libc-dev:amd64 (from .../linux-libc-dev_3.8.0-26.38_amd64.deb) ...
Selecting previously unselected package libc6-dev:amd64.
Unpacking libc6-dev:amd64 (from .../libc6-dev_2.17-0ubuntu5_amd64.deb) ...
Selecting previously unselected package libgcc-4.7-dev:amd64.
Unpacking libgcc-4.7-dev:amd64 (from .../libgcc-4.7-dev_4.7.3-1ubuntu1_amd64.deb) ...
Selecting previously unselected package gcc-4.7.
Unpacking gcc-4.7 (from .../gcc-4.7_4.7.3-1ubuntu1_amd64.deb) ...
Selecting previously unselected package gcc.
Unpacking gcc (from .../gcc_4%3a4.7.3-1ubuntu10_amd64.deb) ...
Selecting previously unselected package libstdc++6-4.7-dev:amd64.
Unpacking libstdc++6-4.7-dev:amd64 (from .../libstdc++6-4.7-dev_4.7.3-1ubuntu1_amd64.deb) ...
Selecting previously unselected package g++-4.7.
Unpacking g++-4.7 (from .../g++-4.7_4.7.3-1ubuntu1_amd64.deb) ...
Selecting previously unselected package g++.
Unpacking g++ (from .../g++_4%3a4.7.3-1ubuntu10_amd64.deb) ...
Selecting previously unselected package libdpkg-perl.
Unpacking libdpkg-perl (from .../libdpkg-perl_1.16.10ubuntu1_all.deb) ...
Selecting previously unselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.16.10ubuntu1_all.deb) ...
Selecting previously unselected package build-essential.
Unpacking build-essential (from .../build-essential_11.6ubuntu4_amd64.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.4-2ubuntu1_amd64.deb) ...
Selecting previously unselected package libalgorithm-diff-perl.
Unpacking libalgorithm-diff-perl (from .../libalgorithm-diff-perl_1.19.02-3_all.deb) ...
Selecting previously unselected package libalgorithm-diff-xs-perl.
Unpacking libalgorithm-diff-xs-perl (from .../libalgorithm-diff-xs-perl_0.04-2build3_amd64.deb) ...
Selecting previously unselected package libalgorithm-merge-perl.
Unpacking libalgorithm-merge-perl (from .../libalgorithm-merge-perl_0.08-2_all.deb) ...
Selecting previously unselected package libfile-fcntllock-perl.
Unpacking libfile-fcntllock-perl (from .../libfile-fcntllock-perl_0.14-2_amd64.deb) ...
Selecting previously unselected package manpages-dev.
Unpacking manpages-dev (from .../manpages-dev_3.44-0ubuntu1_all.deb) ...
Processing triggers for man-db ...
Setting up libitm1:amd64 (4.7.3-1ubuntu1) ...
Setting up binutils (2.23.2-2ubuntu1) ...
Setting up libc-dev-bin (2.17-0ubuntu5) ...
Setting up linux-libc-dev:amd64 (3.8.0-26.38) ...
Setting up libc6-dev:amd64 (2.17-0ubuntu5) ...
Setting up libgcc-4.7-dev:amd64 (4.7.3-1ubuntu1) ...
Setting up gcc-4.7 (4.7.3-1ubuntu1) ...
Setting up gcc (4:4.7.3-1ubuntu10) ...
Setting up libstdc++6-4.7-dev:amd64 (4.7.3-1ubuntu1) ...
Setting up g++-4.7 (4.7.3-1ubuntu1) ...
Setting up g++ (4:4.7.3-1ubuntu10) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode
Setting up libdpkg-perl (1.16.10ubuntu1) ...
Setting up dpkg-dev (1.16.10ubuntu1) ...
Setting up build-essential (11.6ubuntu4) ...
Setting up fakeroot (1.18.4-2ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Setting up libalgorithm-diff-perl (1.19.02-3) ...
Setting up libalgorithm-diff-xs-perl (0.04-2build3) ...
Setting up libalgorithm-merge-perl (0.08-2) ...
Setting up libfile-fcntllock-perl (0.14-2) ...
Setting up manpages-dev (3.44-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

soooo can any one tell me where i stand with these readouts from a **FRESH INSTALL**?

---

### Post by varunendra on 2013-07-19
> **korn16ftl3 said:**
> soooo can any one tell me where i stand with these readouts from a **FRESH INSTALL**?

You are all set to successfully build and install the driver. I hope you have kept those two packages safe (the .bz2 and the .patch). You may now follow the instructions to install the rt5390sta driver (skipping the two download parts if you have kept them, else all the steps).

---

### Post by korn16ftl3 on 2013-07-19
> **varunendra said:**
> You are all set to successfully build and install the driver. I hope you have kept those two packages safe (the .bz2 and the .patch). You may now follow the instructions to install the rt5390sta driver (skipping the two download parts if you have kept them, else all the steps).

got all the way to the make part of the instruction i have not proceeded to the sudo make install cmd yet but im going to share my make results so that you may review them as i did have an error

```
user@user-HP-2000-Notebook-PC:~/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO$ makemake -C tools
make[1]: Entering directory `/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools'
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/Makefile
make -C /lib/modules/3.8.0-26-generic/build SUBDIRS=/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-26-generic'
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/crypt_md5.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/crypt_aes.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/mlme.o
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/mlme.c: In function &#8216;MlmeResetRalinkCounters&#8217;:
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/mlme.c:824:3: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/mlme.c:824:3: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/drs_grp.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_wep.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/action.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_data.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_init.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_aes.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_sync.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/eeprom.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_info.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_radar.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/spectrum.o
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/spectrum.c: In function &#8216;PeerMeasureReportAction&#8217;:
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/spectrum.c:1951:3: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217; [-Wformat]
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_channel.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_profile.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.o
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c: In function &#8216;AsicGetAutoAgcOffsetForTemperatureSensor&#8217;:
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:1233:28: warning: assignment discards &#8216;const&#8217; qualifier from pointer target type [enabled by default]
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:1246:28: warning: assignment discards &#8216;const&#8217; qualifier from pointer target type [enabled by default]
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_profile.o
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_profile.c: In function &#8216;STA_MonPktSend&#8217;:
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_profile.c:408:9: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217; [-Wformat]
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rtmp_chip.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/assoc.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/auth.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sync.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sanity.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/connect.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/wpa.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/ags.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_os_util.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/sta_ioctl.o
In file included from /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/include/os/rt_linux.h:53:0,
                 from /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/include/rtmp_os.h:44,
                 from /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/include/rtmp_comm.h:69,
                 from /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/sta_ioctl.c:30:
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/sta_ioctl.c: In function &#8216;rt_ioctl_giwscan&#8217;:
include/net/iw_handler.h:554:9: warning: array subscript is below array bounds [-Warray-bounds]
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_linux.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/ba_action.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_led.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.o
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c: In function &#8216;DefaultATEAsicAdjustTxPower&#8217;:
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c:300:24: warning: assignment discards &#8216;const&#8217; qualifier from pointer target type [enabled by default]
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c: In function &#8216;DefaultATETxPwrHandler&#8217;:
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c:1402:25: warning: assignment discards &#8216;const&#8217; qualifier from pointer target type [enabled by default]
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c:1356:45: warning: unused variable &#8216;CfgOfTxPwrCtrlOverMAC&#8217; [-Wunused-variable]
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c: In function &#8216;ATESTART&#8217;:
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c:1892:4: warning: overflow in implicit constant conversion [-Woverflow]
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c: In function &#8216;ATESTOP&#8217;:
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c:2163:2: warning: overflow in implicit constant conversion [-Woverflow]
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c: In function &#8216;TXFRAME&#8217;:
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c:2752:2: warning: overflow in implicit constant conversion [-Woverflow]
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c: In function &#8216;RXFRAME&#8217;:
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c:2901:2: warning: overflow in implicit constant conversion [-Woverflow]
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c: In function &#8216;Default_Set_ATE_TX_FREQ_OFFSET_Proc&#8217;:
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c:3695:13: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c: In function &#8216;ATEPeriodicExec&#8217;:
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c:6495:3: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/rt_ate.c:6495:3: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_dfs.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_cs.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_mac_pci.o
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_mac_pci.c: In function &#8216;RT28xx_UpdateBeaconToAsic&#8217;:
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_mac_pci.c:1451:16: warning: unused variable &#8216;irqFlag&#8217; [-Wunused-variable]
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_data_pci.o
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_data_pci.c: In function &#8216;RTMPFreeTXDUponTxDmaDone&#8217;:
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_data_pci.c:540:8: warning: unused variable &#8216;TXWISize&#8217; [-Wunused-variable]
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_data_pci.c: In function &#8216;RTMPHandleMgmtRingDmaDoneInterrupt&#8217;:
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_data_pci.c:882:8: warning: unused variable &#8216;TXWISize&#8217; [-Wunused-variable]
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_rbus_pci_drv.o
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_rbus_pci_drv.c: In function &#8216;RTMPInitPCIeDevice&#8217;:
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_rbus_pci_drv.c:1386:23: warning: unused variable &#8216;Index&#8217; [-Wunused-variable]
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.o
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c: In function &#8216;RtmpAsicSendCommandToMcu&#8217;:
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:621:4: warning: passing argument 3 of &#8216;pci_read_config_word&#8217; from incompatible pointer type [enabled by default]
In file included from /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/include/os/rt_linux.h:41:0,
                 from /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/include/rtmp_os.h:44,
                 from /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/include/rtmp_comm.h:69,
                 from /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/include/rt_config.h:33,
                 from /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:28:
include/linux/pci.h:794:19: note: expected &#8216;u16 *&#8217; but argument is of type &#8216;ULONG *&#8217;
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:627:4: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 2 has type &#8216;ULONG&#8217; [-Wformat]
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:627:4: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 3 has type &#8216;ULONG&#8217; [-Wformat]
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:641:4: warning: passing argument 3 of &#8216;pci_read_config_word&#8217; from incompatible pointer type [enabled by default]
In file included from /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/include/os/rt_linux.h:41:0,
                 from /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/include/rtmp_os.h:44,
                 from /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/include/rtmp_comm.h:69,
                 from /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/include/rt_config.h:33,
                 from /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:28:
include/linux/pci.h:794:19: note: expected &#8216;u16 *&#8217; but argument is of type &#8216;ULONG *&#8217;
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:650:4: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 2 has type &#8216;ULONG&#8217; [-Wformat]
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rtmp_mcu.c:650:4: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 3 has type &#8216;ULONG&#8217; [-Wformat]
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/ee_prom.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/ee_efuse.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_rf.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt30xx.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt3090.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt33xx.o
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt33xx.c: In function &#8216;RT33xx_AsicTxAlcGetAutoAgcOffset&#8217;:
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt33xx.c:1199:24: warning: assignment discards &#8216;const&#8217; qualifier from pointer target type [enabled by default]
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt3390.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.o
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c: In function &#8216;RT5390_AsicTxAlcGetAutoAgcOffset&#8217;:
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../chips/rt5390.c:2756:25: warning: assignment discards &#8216;const&#8217; qualifier from pointer target type [enabled by default]
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/chips/rt5390_ate.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/chips/rt30xx_ate.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../ate/common/ate_pci.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_pci_rbus.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_rbus_pci_util.o
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/pci_main_dev.o
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/pci_main_dev.c: In function &#8216;rt2860_probe&#8217;:
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/pci_main_dev.c:346:13: warning: assignment discards &#8216;const&#8217; qualifier from pointer target type [enabled by default]
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/pci_main_dev.c: At top level:
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/pci_main_dev.c:493:13: warning: &#8216;rt2860_remove_one&#8217; defined but not used [-Wunused-function]
  CC [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.o
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c: In function &#8216;FrequencyCalibration&#8217;:
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:197:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:210:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:226:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:251:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:264:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/frq_cal.c:280:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]
  LD [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.o
see include/linux/module.h for more information
  CC      /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.mod.o
  LD [M]  /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-26-generic'
cp -f /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.ko /tftpboot
cp: cannot create regular file &#8216;/tftpboot&#8217;: Permission denied
make: *** [LINUX] Error 1

```

and the readout for the sudo make install is as follows:

```

user@user-HP-2000-Notebook-PC:~/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO$ sudo make install
[sudo] password for user: 
make -C /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux -f Makefile.6 install
make[1]: Entering directory `/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/3.8.0-26-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5390sta.ko /lib/modules/3.8.0-26-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 3.8.0-26-generic
make[1]: Leaving directory `/home/user/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux'

```

when i get to the modprobe part of the instruction i am getting an error the read out is as follows:
```

user@user-HP-2000-Notebook-PC:~/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO$ modprobe rt5390sta
ERROR: could not insert 'rt5390sta': Operation not permitted
user@user-HP-2000-Notebook-PC:~/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO$

```

[B]ok i got it working :-) a couple things that should be noted...Lubuntu does not have gedit and it needs to be installed same with the above make and [COLOR=#000000][FONT=Ubuntu Mono]linux-headers-generic but all in all.....what a pain in the ass LOL now...on to try to compile a Final Fantasy XI private server out of this thing lmfao


[/FONT][/COLOR][/B][COLOR=#000000][FONT=Ubuntu Mono]
EDIT:
hmmm seems the connection ceased to function...how ever i am on it right now replying with the same connection....ill do some more tinkering and see whats going on....it said it was connected so no idea what the deal is here[/FONT][/COLOR]

---

### Post by varunendra on 2013-07-20
Some explanation -
> **korn16ftl3 said:**
> 
```
[COLOR="#FF0000"]cp: cannot create regular file ‘/tftpboot’: Permission denied[/COLOR]
make: *** [LINUX] Error 1

```
Exactly that one error is normal (without sudo), it can be safely ignored.

> 
```

user@user-HP-2000-Notebook-PC:~/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO$ modprobe rt5390sta
ERROR: could not insert 'rt5390sta': [COLOR="#FF0000"]Operation not permitted[/COLOR]

```
The error line also tells you why the error. System wide things can not be done as normal user, you need to have root privileges to do them. In short, modprobe command needs to be run with 'sudo' (unless you have acquired root with 'sudo su' and are in root mode).

> [B]ok i got it working :-) a couple things that should be noted...Lubuntu does not have gedit and it needs to be installed same with the above make and [COLOR=#000000][FONT=Ubuntu Mono]linux-headers-generic
To be honest, I still haven't followed those instructions very closely, only roughly glanced at them because the important parts (regarding wpa supplicant and patching) seemed ok. Gedit is the part of the default Ubuntu D(esktop)E(nvironment). You can use whatever text editor your DE provides. In LXDE (DE in Lubuntu) the default text editor is "Leafpad" instead of "Gedit".

So you don't need to install gedit. Just replace it with whichever one you have. Also, "make" is part of "build-essential" package. There are certain libraries plus linux headers that are required to compile a package. The package build-essential, as its name suggests, contains all the essential libraries and components, and the headers 'sometimes' need to be installed separately (normally, they are supposed to be installed by default with every new kernel version). We include linux-headers along with build-essential just to be on safe side (if it is already installed, no harm in reinstalling).


> EDIT:
hmmm seems the connection ceased to function...how ever i am on it right now replying with the same connection....ill do some more tinkering and see whats going on....it said it was connected so no idea what the deal is here
Feel free to continue with questions if you have further issues with the wifi. After all, the thread is meant to properly 'Solve' your wireless problem.

You can run the same "wireless_script" (follow the link in my signature) again to get a detailed report on the current status of the wifi.

---

