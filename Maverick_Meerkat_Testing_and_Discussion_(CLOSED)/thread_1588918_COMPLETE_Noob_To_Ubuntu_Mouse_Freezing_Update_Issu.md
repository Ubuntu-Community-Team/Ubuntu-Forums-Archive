---
title: "COMPLETE Noob To Ubuntu/ Mouse Freezing/ Update Issues"
date: 2010-10-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by AmbrociousXP on 2010-10-05
OK, as I stated in my description, Im a complete noob to Ubuntu and I just downloaded and dual booted my Ubuntu with my Windows 7. I downloaded the Ubuntu 10.10 and decided to use it since this time I successfully was able to connect into my wireless network. 

I noticed when I play any kind of sound, my mouse freezes up eventually after a few seconds of playing any sound (either mp3 or Ubuntu built in system sounds, even sound test sounds froze me up) or when I am doing to much at the same time. I assumed it was an issue and some things needed to be updated but when I tried to update the software, it tells me this:


> 
Requires installation of untrusted packages


The action would require the installation of packages from not authenticated sources.

Details:

apport apport-gtk apt apt-transport-https apt-utils aptdaemon brasero brasero-cdrkit brasero-common busybox-initramfs busybox-static capplets-data consolekit cups cups-bsd cups-client cups-common desktopcouch empathy empathy-common evolution evolution-common evolution-plugins foomatic-db-compressed-ppds gnome-accessibility-themes gnome-applets gnome-applets-data gnome-bluetooth gnome-control-center gnome-keyring gnome-settings-daemon gnome-themes-selected gvfs gvfs-backends gvfs-fuse gwibber gwibber-service indicator-session initramfs-tools initramfs-tools-bin jockey-common jockey-gtk kerneloops-daemon language-pack-en language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base language-selector language-selector-common libbrasero-media1 libcairo2 libck-connector0 libcryptui0 libcups2 libcupscgi1 libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libevolution libgcr0 libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa libgnome-bluetooth8 libgnome-window-settings1 libgp11-0 libgtk-vnc-1.0-0 libgtksourceview2.0-0 libgtksourceview2.0-common libgvfscommon0 libpam-ck-connector libpam-gnome-keyring libsyncdaemon-1.0-1 libtelepathy-glib0 libvala-0.10-0 light-themes ltrace module-init-tools nautilus-sendto nautilus-sendto-empathy nvidia-173-modaliases nvidia-current-modaliases openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-math openoffice.org-style-human openoffice.org-writer openprinting-ppds pitivi python-apport python-aptdaemon python-aptdaemon-gtk python-cupshelpers python-desktopcouch-records python-problem-report python-pygoocanvas python-ubuntuone-client python-uno seahorse shotwell software-center system-config-printer-common system-config-printer-gnome system-config-printer-udev telepathy-gabble tomboy ttf-opensymbol ttf-symbol-replacement ttf-ubuntu-font-family ubuntu-artwork ubuntu-keyring ubuntu-sso-client ubuntuone-client ubuntuone-client-gnome uno-libs3 update-manager update-manager-core ure xserver-xorg-video-geode zenity


Im new to Ubuntu sort of and I'm deciding to learn more about it since my wireless usb works with this version. Some detailed help on "how to" would be really wonderful. How do I install the updates of untrusted packages and would that be a good thing or a bad thing? I'm sure the mouse issue is a small thing and will be worked out over time but the updates are important here. Thanks in advance.

---

### Post by cariboo on 2010-10-05
Update your sources list, using either the Applications->Accessories->Terminal:

```
sudo apt-get update
```

Update Manager:

Click the Check button

Or System->Administration->Synaptic Package Manger:

Click Reload

Then try to do the updates again.

Check System->Administration->System Monitor->Processes to see what is using all your resources.

---

### Post by AmbrociousXP on 2010-10-05
OK I did what you said and during the run of the Synaptic Package Manager it told me this:


W: > A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

Also my mouse is starting to freeze even when I'm doing nothing at all, yet my keyboard still works. As Far as I can see, nothing is taking up a lot of my system resources. Firefox sometimes gets in the 40's under the CPU usage and the gnome was up to 11 once but nothing really bad.

---

### Post by davrosuk on 2010-10-05
To fix that GPG error:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
```

---

### Post by AmbrociousXP on 2010-10-07
Where do I type that at?

---

### Post by JackNocturne on 2010-10-07
also type at **terminal**

---

### Post by AmbrociousXP on 2010-10-07
OK it went threw the terminal just fine then I moved onto the next step in the Synaptic Package Manager. I clicked on the reload button and this is the message I get after it almost completed downloading the packages:


> 
[B]Could not download all repository indexes
[/B]
The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct. 


[I]Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.[/I]



As far as I can tell, my network is working just fine. I am using Ubuntu right now and it surfs the net just fine. The freeze ups still happen though. Anything Im missing or maybe haven't tried and also, thanks for helping me out I appreciate it a lot. I also tried to update again in the Update Manager...it keeps telling me that "The action would require the installation of packages from not authenticated sources." 

Question: If this is the update manager and I assume it connects into the main Ubuntu update server for the updates, how could it be that It would be requiring unauthentic programs to b installed? I assume those are third party drivers and such but still, how I can I bypass this temporarily and just allow it to install?

---

### Post by AmbrociousXP on 2010-10-07
Any extra help would be greatly appreciated.

---

### Post by 23dornot23d on 2010-10-08
How do you connect your mouse and the belkin .... are they both plugged into a extension
USB by any chance ..... (or maybe the sound related issue is to do with it setting sound on the modem somehow)

A few other small questions ..... I looked through your previous problems .... but no mention of what computer
or what type of mouse etc .... 

I presume its a USB mouse ... type in a terminal the following

**lspci**

gives a list of the devices ....... and adds a bit more info for people to work on ........ (ls is for List)
also ... for usb devices .. and how they are connected .... cut and paste the results please ....

[B]lsusb

With the Belkin unplugged does the mouse run ok ........ (just a test)

[/B]Wonder why you have so many untrusted sources ..... its not usually a problem - but its a personal choice.
only you will know what ppa's you have added ... as far as I know the standard ones do not ask the question
as its all to do with keeping your system as secure as possible.

---

### Post by AmbrociousXP on 2010-10-09
[B][COLOR=DarkRed]Mouse is HP USB with a SN: 0910006706
Wireless N Belkin USB Model Number: F6D4050 v2[/COLOR]


OK here is the result of my lspci from the Terminal:[/B]


> 00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 PCI bridge: nVidia Corporation NF200 PCIe 2.0 switch for Quadro Plex S4 / Tesla S870 / Tesla S1070 / Tesla S2050 (rev a2)
02:00.0 PCI bridge: nVidia Corporation NF200 PCIe 2.0 switch for Quadro Plex S4 / Tesla S870 / Tesla S1070 / Tesla S2050 (rev a2)
02:02.0 PCI bridge: nVidia Corporation NF200 PCIe 2.0 switch for Quadro Plex S4 / Tesla S870 / Tesla S1070 / Tesla S2050 (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 8800 GTS 512] (rev a2)
04:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GX2] (rev a2)
I'll unplug the USB Belkin wireless device in a bit to test it out.


EDIT: OK I unplugged it and the mouse works just fine. I noticed that a lot of things trigger my mouse to just freeze up. Too many things running that have to do with the Ubuntu OS, sound that continues, video from my external HD, trying to update causes my mouse to freeze too. I'm currently back on my Windows 7 and simply being on Firefox froze me up, nothing else was running at the time. I'm sure I'll be able to overcome this problem eventually but I'm gonna need some help. [COLOR=Red][B]How exactly to I allow those programs to install? The ones that say the source is unverified?


NOTE: [COLOR=Black]I have installed previous version of Ubuntu before and everything else worked MINUS the wireless Belken USB device. There were no freezes of any kind on the previous Ubuntu's so I assume it's not exactly my fault completely but I could be wrong.[/COLOR]
[/B][/COLOR]

---

### Post by ronacc on 2010-10-09
post your /etc/apt/sources.list .

---

### Post by AmbrociousXP on 2010-10-10
> **ronacc said:**
> post your /etc/apt/sources.list .

My what? Not sure what your asking for...

---

### Post by LiquidMeson on 2010-10-10
> **ronacc said:**
> post your /etc/apt/sources.list .

He's referring to the sources.list file.
in the terminal type: cat /etc/apt/sources.list

I find [http://pastebin.com/](http://pastebin.com/) is a good location to share long text with.

---

### Post by MishaAct on 2010-10-10
> **AmbrociousXP said:**
> My what? Not sure what your asking for...
you look like a troll )

---

