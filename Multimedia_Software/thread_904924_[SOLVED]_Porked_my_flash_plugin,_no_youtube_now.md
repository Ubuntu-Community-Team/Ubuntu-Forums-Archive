---
title: "[SOLVED] Porked my flash plugin, no youtube now"
date: 2008-08-29
forum: Multimedia Software
---

### Post by Morty007 on 2008-08-29
I accidentally messed up my flash plugin while trying to figure out why a particular page on ebay was causing high cpu usage. 


What I've tried to do to fix:

Uninstall and install the adobe flash plugin- tried to copy the libflashplayer.so into the usr/lib mozilla plugins folder, but it says that permission is denied. 

I've followed this [http://ubuntuforums.org/showthread.php?t=904753&highlight=adobe+flash+player](http://ubuntuforums.org/showthread.php?t=904753&highlight=adobe+flash+player) thread but on the 3rd step it said it was going to remove 100mbs of stuff, so I got scared and stopped it. 

In terminal under java --version I get :
Unrecognized option: --version
Could not create the Java virtual machine.

Java is enabled in Firefox 3. So I'm just plain lost!  

Using gnome in Linux Mint 5.

[[img]http://xs130.xs.to/xs130/08355/screenshot--_-_file_browser786.png[/img]](http://xs.to)


[[img]http://xs130.xs.to/xs130/08355/screenshot467.png[/img]](http://xs.to)

---

### Post by srt4play on 2008-08-29
I would uninstall the flashplugin in synaptic and download the version 10 release candidate from labs.adobe.com. Copy libflashplayer.so into the directory by doing Alt-F2, type the command 'gksudo nautilus'. You are getting permission denied because only the root user can write to the filesystem outside of your home directory.

---

### Post by wolfen69 on 2008-08-29
see my reply (#7) on [this]("http://ubuntuforums.org/showthread.php?t=904753") thread.

---

### Post by Morty007 on 2008-08-29
TY srt4play for the quick response. I did what you said and the plugin folder is now opened as root, but it won't let me drap and drop the .so file in there and it won't let me copy and paste.

---

### Post by Morty007 on 2008-08-29
> **wolfen69 said:**
> see my reply (#7) on [this]("http://ubuntuforums.org/showthread.php?t=904753") thread.

Wolfen, before I posted I did what you suggested, but when I did 
sudo apt-get autoremove, it said it was going to remove about 100 mb's worth of stuff,see below. I'm holding off until you reply. thanks. 

[[img]http://xs230.xs.to/xs230/08355/screenshot-terminal827.png[/img]](http://xs.to)

---

### Post by Morty007 on 2008-08-29
Ok, all went well until the last step when I get:

Downloading...
--21:02:50--  [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.tar.gz)
           => `./flashplayer10_install_linux_051508.tar.gz'
Resolving download.macromedia.com... 72.246.91.191
Connecting to download.macromedia.com|72.246.91.191|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
21:02:51 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.

---

### Post by Morty007 on 2008-08-30
marc@marc-desktop ~ $ sudo apt-get update
[sudo] password for marc: 
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/main Translation-en_US                
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/upstream Translation-en_US            
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/import Translation-en_US              
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US                     
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Get:1 [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa Release [7813B]                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US         
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                            
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/main Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages                          
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/upstream Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages                
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/import Packages                       
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/main Packages          
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/upstream Packages      
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/import Packages                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Fetched 7813B in 6s (1297B/s)                                                  
Reading package lists... Done
marc@marc-desktop ~ $ sudo apt-get upgrade
[sudo] password for marc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  linux-headers-2.6.24-19 linux-headers-2.6.24-19-generic
  linux-image-2.6.24-19-generic linux-libc-dev
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 27.8MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main linux-image-2.6.24-19-generic 2.6.24-19.41 [18.4MB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main linux-headers-2.6.24-19 2.6.24-19.41 [8131kB]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main linux-headers-2.6.24-19-generic 2.6.24-19.41 [644kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main linux-libc-dev 2.6.24-19.41 [696kB]
Fetched 27.8MB in 47s (582kB/s)                                                
(Reading database ... 116315 files and directories currently installed.)
Preparing to replace linux-image-2.6.24-19-generic 2.6.24-19.36 (using .../linux-image-2.6.24-19-generic_2.6.24-19.41_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.24-19-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Preparing to replace linux-headers-2.6.24-19 2.6.24-19.36 (using .../linux-headers-2.6.24-19_2.6.24-19.41_all.deb) ...
Unpacking replacement linux-headers-2.6.24-19 ...
Preparing to replace linux-headers-2.6.24-19-generic 2.6.24-19.36 (using .../linux-headers-2.6.24-19-generic_2.6.24-19.41_i386.deb) ...
Unpacking replacement linux-headers-2.6.24-19-generic ...
Preparing to replace linux-libc-dev 2.6.24-19.36 (using .../linux-libc-dev_2.6.24-19.41_i386.deb) ...
Unpacking replacement linux-libc-dev ...
Setting up linux-image-2.6.24-19-generic (2.6.24-19.41) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.24-19.36 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.24-19.36 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


Setting up linux-headers-2.6.24-19 (2.6.24-19.41) ...
Setting up linux-headers-2.6.24-19-generic (2.6.24-19.41) ...

Setting up linux-libc-dev (2.6.24-19.41) ...
marc@marc-desktop ~ $ sudo apt-get purge flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  flashplugin-nonfree*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 168kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 116314 files and directories currently installed.)
Removing flashplugin-nonfree ...
Purging configuration files for flashplugin-nonfree ...
marc@marc-desktop ~ $ sudo apt-get clean
marc@marc-desktop ~ $ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
marc@marc-desktop ~ $ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 18.8kB of archives.
After this operation, 168kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  flashplugin-nonfree
Install these packages without verification [y/N]? y
Get:1 [http://packages.linuxmint.com](http://packages.linuxmint.com) elyssa/upstream flashplugin-nonfree 10.0.b218-0ubuntu3 [18.8kB]
Fetched 18.8kB in 0s (26.1kB/s)          
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 116308 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.0.b218-0ubuntu3_i386.deb) ...
Setting up flashplugin-nonfree (10.0.b218-0ubuntu3) ...
Downloading...
--16:28:07--  [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.tar.gz)
           => `./flashplayer10_install_linux_051508.tar.gz'
Resolving download.macromedia.com... 72.246.91.191
Connecting to download.macromedia.com|72.246.91.191|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
16:28:07 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.

marc@marc-desktop ~ $ 





Same thing, can anyone help?

---

### Post by benerivo on 2008-08-30
> **Morty007 said:**
> tried to copy the libflashplayer.so into the usr/lib mozilla plugins folder, but it says that permission is denied

Try ```
gksudo nautilus
```then you can copy the file where you want.

Your problem may be related to the system trying to download the beta version of flash (version 10)?

EDIT - The version your system tries to download (051508.tar.gz) is now superceded with [this]("http://labs.adobe.com/downloads/flashplayer10.html") (081108.tar.gz).

---

### Post by Morty007 on 2008-08-30
Benerivo, I did that and it let me copy the .so file, but when I right click in the mozilla plugins folder the paste command is greyed out.

I tried to drag and drop and that wouldn't work either.

---

### Post by benerivo on 2008-08-30
Make sure that this begins with no windows open at all. Then open a console and run gksudo nautilus. Using only that instance of nautilus, navigate to the .so file and right click > copy it. The navigate to the plugins folder and paste it. This should work.

---

### Post by Morty007 on 2008-08-30
Still a no go, can't paste or drag. Below is the only windows I had open. 

[[img]http://xs330.xs.to/xs330/08356/screenshot658.png[/img]](http://xs.to)

---

### Post by Morty007 on 2008-08-30
Ok, managed to copy it both in usr/lib/mozilla/plugins and to usr/lib flashplugin/non-free and then restarted the browser, nothing. :confused:

[[img]http://xs230.xs.to/xs230/08356/screenshot702.png[/img]](http://xs.to)

---

### Post by Morty007 on 2008-08-30
Solved, I followed what ubuntufreak did here

[http://ubuntuforums.org/showthread.php?t=795019&page=10](http://ubuntuforums.org/showthread.php?t=795019&page=10)

---

### Post by ubuntu-freak on 2008-08-30
> **Morty007 said:**
> Solved, I followed what ubuntufreak did here

[http://ubuntuforums.org/showthread.php?t=795019&page=10](http://ubuntuforums.org/showthread.php?t=795019&page=10)

 
Glad you got it working. :)
 
However, I recommend that anyone else having problems with Flash playback should follow the instructions in the troubleshooting section of my [howto](ubuntuforums.org/showthread.php?t=766683), as the above link contains fairly outdated instructions.

---

### Post by Morty007 on 2008-08-30
Thanks UF. Unfortunately, Cnn.com crashes firefox when I try to view a video. 

Also this ebay links makes my cpu usage go sky high...but only when I scroll down to where the green is. [http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&ssPageName=STRK:MEWAX:IT&item=140260895919](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&ssPageName=STRK:MEWAX:IT&item=140260895919)

Any hints on how to fix this? Thanks a million!!!!

---

### Post by ubuntu-freak on 2008-08-31
Perhaps you could report the bugs to Adobe and use the v10 beta 1 plugin from my howto, or v9.

---

