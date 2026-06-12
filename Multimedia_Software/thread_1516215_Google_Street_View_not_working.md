---
title: "Google Street View not working"
date: 2010-06-23
forum: Multimedia Software
---

### Post by mo1956 on 2010-06-23
I can't use the Google "Street view" feature.  I get a message saying I need Adobe flash player version 10.

I am running Ubuntu 8.04 (hardy) and have Firefox 3.0.19.  I installed Adobe - Flash Player version 10 and confirmed the installed version in the package manager, but when I go to the following site [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/) it tells me I have version 9,0,277,0 installed.

Any suggestions?

---

### Post by lovinglinux on 2010-06-23
Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by mo1956 on 2010-06-23
I have the Flash-Aid installed and followed the thread you suggested.

---

### Post by lovinglinux on 2010-06-23
> **mo1956 said:**
> I have the Flash-Aid installed and followed the thread you suggested.

Does it work?

Check the flash version again, you should have version 10.1 r53 now.

---

### Post by mo1956 on 2010-06-24
When I installed the Flash Player from Adobe web site the version is 10.1.53.64-1. according to "Synaptic Package Manager".  Is that the same as version 10.1 r53?

---

### Post by SoFl W on 2010-06-24
I am not sure, I had trouble accessing Google Street view earlier today.  I haven't used google maps /street view in a long time, but I had a problem.

---

### Post by Frantic_Earthling on 2010-06-25
Did you install Google Earth from the Ubuntu repos or from the Google download page?

---

### Post by lovinglinux on 2010-06-25
> **mo1956 said:**
> When I installed the Flash Player from Adobe web site the version is 10.1.53.64-1. according to "Synaptic Package Manager".  Is that the same as version 10.1 r53?

Is the same version, but looking at Synaptic won't help much. You need to look which version is being detected by the browser.

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

---

### Post by mo1956 on 2010-06-25
When I execute the statements "**about:config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about:plugins"**.  The screen is blank.

---

### Post by lovinglinux on 2010-06-25
> **mo1956 said:**
> When I execute the statements "**about:config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about:plugins"**.  The screen is blank.

Please post a screenshot.

---

### Post by mo1956 on 2010-06-25
> **lovinglinux said:**
> Please post a screenshot.


I forgot to enter the command about:plugins in the address bar.  The shockwave information is below.
File name:  /usr/lib/flashplugin-nonfree/libflashplayer.so Shockwave Flash 9.0 r277.  The Adope Flash Player is not listed.

---

### Post by lovinglinux on 2010-06-25
> **mo1956 said:**
> I forgot to enter the command about:plugins in the address bar.  The shockwave information is below.
File name:  /usr/lib/flashplugin-nonfree/libflashplayer.so Shockwave Flash 9.0 r277.  The Adope Flash Player is not listed.

To fix that, see my post [#2]("http://ubuntuforums.org/showpost.php?p=9500841&postcount=2"). You need to run FLASH-AID after installation to replace the flash plugin with the correct version. If you already installed it, then run the install option from FLASH-AID menu in Firefox statusbar.

---

### Post by mo1956 on 2010-06-25
> **lovinglinux said:**
> To fix that, see my post [#2]("http://ubuntuforums.org/showpost.php?p=9500841&postcount=2"). You need to run FLASH-AID after installation to replace the flash plugin with the correct version. If you already installed it, then run the install option from FLASH-AID menu in Firefox statusbar.

I ran the Flash-Aid and got the following.  Looks like the Adobe flash plugin is not getting installed.

  	 	 	 	 	 	  Please wait...DON'T CLOSE THIS TERMINAL! 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 Package swfdec-mozilla is not installed, so not removed 
 The following packages were automatically installed and are no longer required: 
   linux-headers-2.6.24-16-generic linux-headers-2.6.24-16 
 Use 'apt-get autoremove' to remove them. 
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 Package mozilla-plugin-gnash is not installed, so not removed 
 The following packages were automatically installed and are no longer required: 
   linux-headers-2.6.24-16-generic linux-headers-2.6.24-16 
 Use 'apt-get autoremove' to remove them. 
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 Package adobe-flashplugin is not installed, so not removed 
 The following packages were automatically installed and are no longer required: 
   linux-headers-2.6.24-16-generic linux-headers-2.6.24-16 
 Use 'apt-get autoremove' to remove them. 
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 Package flashplugin-nonfree is not installed, so not removed 
 The following packages were automatically installed and are no longer required: 
   linux-headers-2.6.24-16-generic linux-headers-2.6.24-16 
 Use 'apt-get autoremove' to remove them. 
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 E: Couldn't find package flashplugin-installer 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 The following packages were automatically installed and are no longer required: 
   linux-headers-2.6.24-16-generic linux-headers-2.6.24-16 
 Use 'apt-get autoremove' to remove them. 
 Suggested packages: 
   konqueror-nsplugins libflashsupport msttcorefonts ttf-xfree86-nonfree xfs 
 The following NEW packages will be installed: 
   flashplugin-nonfree 
 0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded. 
 Need to get 0B/19.3kB of archives. 
 After this operation, 168kB of additional disk space will be used. 
 Preconfiguring packages ... 
 Selecting previously deselected package flashplugin-nonfree. 
 (Reading database ... 134136 files and directories currently installed.) 
 Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.0.1.218+really9.0.277.0ubuntu1_i386.deb) ... 
 Setting up flashplugin-nonfree (10.0.1.218+really9.0.277.0ubuntu1) ... 
 Downloading... 
 --11:54:24--  [http://download.macromedia.com/pub/flashplayer/installers/current/9/install_flash_player_9.tar.gz](http://download.macromedia.com/pub/flashplayer/installers/current/9/install_flash_player_9.tar.gz) 
            => `./install_flash_player_9.tar.gz' 
 Resolving download.macromedia.com... 96.7.19.191 
 Connecting to download.macromedia.com|96.7.19.191|:80... connected. 
 HTTP request sent, awaiting response... 200 OK 
 Length: 3,064,514 (2.9M) [application/x-gzip] 
  
     0K .......... .......... .......... .......... ..........  1%  157.52 KB/s 
    50K .......... .......... .......... .......... ..........  3%  157.14 KB/s 
   100K .......... .......... .......... .......... ..........  5%  161.69 KB/s 
   150K .......... .......... .......... .......... ..........  6%  157.13 KB/s 
   200K .......... .......... .......... .......... ..........  8%  161.73 KB/s 
   250K .......... .......... .......... .......... .......... 10%  157.22 KB/s 
   300K .......... .......... .......... .......... .......... 11%  149.40 KB/s 
   350K .......... .......... .......... .......... .......... 13%  161.90 KB/s 
   400K .......... .......... .......... .......... .......... 15%  156.85 KB/s 
   450K .......... .......... .......... .......... .......... 16%  162.10 KB/s 
   500K .......... .......... .......... .......... .......... 18%  156.37 KB/s 
   550K .......... .......... .......... .......... .......... 20%  162.56 KB/s 
   600K .......... .......... .......... .......... .......... 21%  157.32 KB/s 
   650K .......... .......... .......... .......... .......... 23%  161.44 KB/s 
   700K .......... .......... .......... .......... .......... 25%  149.38 KB/s 
   750K .......... .......... .......... .......... .......... 26%  157.22 KB/s 
   800K .......... .......... .......... .......... .......... 28%  161.68 KB/s 
   850K .......... .......... .......... .......... .......... 30%  157.21 KB/s 
   900K .......... .......... .......... .......... .......... 31%  160.14 KB/s 
   950K .......... .......... .......... .......... .......... 33%  158.71 KB/s 
  1000K .......... .......... .......... .......... .......... 35%  161.79 KB/s 
  1050K .......... .......... .......... .......... .......... 36%  157.22 KB/s 
  1100K .......... .......... .......... .......... .......... 38%  161.64 KB/s 
  1150K .......... .......... .......... .......... .......... 40%  157.06 KB/s 
  1200K .......... .......... .......... .......... .......... 41%  157.23 KB/s 
  1250K .......... .......... .......... .......... .......... 43%  161.66 KB/s 
  1300K .......... .......... .......... .......... .......... 45%  157.14 KB/s 
  1350K .......... .......... .......... .......... .......... 46%  161.89 KB/s 
  1400K .......... .......... .......... .......... .......... 48%  147.89 KB/s 
  1450K .......... .......... .......... .......... .......... 50%  172.18 KB/s 
  1500K .......... .......... .......... .......... .......... 51%  157.73 KB/s 
  1550K .......... .......... .......... .......... .......... 53%  161.67 KB/s 
  1600K .......... .......... .......... .......... .......... 55%  157.23 KB/s 
  1650K .......... .......... .......... .......... .......... 56%  157.00 KB/s 
  1700K .......... .......... .......... .......... .......... 58%  154.01 KB/s 
  1750K .......... .......... .......... .......... .......... 60%  157.30 KB/s 
  1800K .......... .......... .......... .......... .......... 61%  161.72 KB/s 
  1850K .......... .......... .......... .......... .......... 63%  157.16 KB/s 
  1900K .......... .......... .......... .......... .......... 65%  161.70 KB/s 
  1950K .......... .......... .......... .......... .......... 66%  157.21 KB/s 
  2000K .......... .......... .......... .......... .......... 68%  161.83 KB/s 
  2050K .......... .......... .......... .......... .......... 70%  157.19 KB/s 
  2100K .......... .......... .......... .......... .......... 71%  156.69 KB/s 
  2150K .......... .......... .......... .......... .......... 73%   89.62 KB/s 
  2200K .......... .......... .......... .......... .......... 75%  189.55 KB/s 
  2250K .......... .......... .......... .......... .......... 76%  244.49 KB/s 
  2300K .......... .......... .......... .......... .......... 78%  158.05 KB/s 
  2350K .......... .......... .......... .......... .......... 80%  161.61 KB/s 
  2400K .......... .......... .......... .......... .......... 81%  157.14 KB/s 
  2450K .......... .......... .......... .......... .......... 83%  160.83 KB/s 
  2500K .......... .......... .......... .......... .......... 85%  158.15 KB/s 
  2550K .......... .......... .......... .......... .......... 86%  156.98 KB/s 
  2600K .......... .......... .......... .......... .......... 88%  161.77 KB/s 
  2650K .......... .......... .......... .......... .......... 90%  157.23 KB/s 
  2700K .......... .......... .......... .......... .......... 91%  161.71 KB/s 
  2750K .......... .......... .......... .......... .......... 93%  157.03 KB/s 
  2800K .......... .......... .......... .......... .......... 95%  161.81 KB/s 
  2850K .......... .......... .......... .......... .......... 96%  156.94 KB/s 
  2900K .......... .......... .......... .......... .......... 98%  152.09 KB/s 
  2950K .......... .......... .......... .......... ..        100%  163.67 KB/s 
  
 11:54:43 (157.89 KB/s) - `./install_flash_player_9.tar.gz' saved [3064514/3064514] 
  
 Download done. 
 Flash Plugin installed. 
  
 Finished! You can close this terminal. You must restart Firefox now.

---

### Post by lovinglinux on 2010-06-25
> **mo1956 said:**
> I ran the Flash-Aid and got the following.  Looks like the Adobe flash plugin is not getting installed.

It ran correctly. The problem is that the current version available for Ubuntu 8.04 is 10.0.1.218+really9.0.277.0ubuntu1. So the only available version from the repositories for your Ubuntu version is 9.0 r277. So you need to remove it, then install the deb file from Adobe site.

```
sudo apt-get purge flashplugin-nonfree
sudo apt-get purge flashplugin-installer
```

Then [get adobe-flashplugin from here]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb"). Download it and double click the deb file to install. 

Test if it works and if the version detected by Firefox is now 10.1 rc53.

You can remove FLASH-AID, since it will only install the version from the repositories.

---

### Post by mo1956 on 2010-06-25
That fixed the problem.  Thanks for the help.

---

### Post by lovinglinux on 2010-06-25
> **mo1956 said:**
> That fixed the problem.  Thanks for the help.

You are welcome.

---

