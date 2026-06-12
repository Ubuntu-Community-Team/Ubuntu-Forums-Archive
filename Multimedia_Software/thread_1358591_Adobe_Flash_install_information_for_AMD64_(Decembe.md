---
title: "Adobe Flash install information for AMD64 (December 2009 update)"
date: 2009-12-18
forum: Multimedia Software
---

### Post by michael37 on 2009-12-18
To moderators: please make this post sticky.  [thread="1259102"]It's predecessor[/thread] was sticky on the x86-64 forum, but that forum is now closed.  Thank you.

[size="5"]**NEWS! Adobe Flash 11 for 64-bit is finally released!**[/size]

Designed for **64-bit** versions of Ubuntu starting with Hardy 8.04.
Do NOT use this script on any 32-bit version of Ubuntu.

[SIZE="3"]Why use these instructions?[/size]
Instructions on Adobe website in "download flash player" are actually inaccurate for Linux 64-bit and will make you install Flash version 10. You do not want that.
Instructions on a popular sevenmachines ppa give a beta version with **known security holes**. You don't want that either.

[SIZE="3"]Which browser is supported?[/size]
The only supported browsers are **64-bit Firefox 3.6 and 64-bit Firefox 10 provided by Ubuntu team**.  Lucid 10.04 and Maverick 10.10 supply functional version of FF 3.6 browser; otherwise you **must** obtain updated one from **firefox-stable PPA**.  Detailed instructions here: [FirefoxNewVersion from ubuntu community wiki]("https://help.ubuntu.com/community/FirefoxNewVersion").
Binary 32-bit version from Mozilla site is **NOT supported** and will not work. You can tell a difference by observing your User Agent from [http://whatsmyuseragent.com/](http://whatsmyuseragent.com/).  Important differences are highlighted below.

[INDENT]*[COLOR="Lime"]RIGHT 64-bit browser:[/COLOR]* Mozilla/5.0 (X11; **Linux x86_64**; rv:7.0.1) Gecko/20100101 Firefox/7.0.1
*[COLOR="Red"]WRONG 32-bit browser:[/COLOR]* Mozilla/5.0 (X11; U; **Linux i686 (x86_64)**; en-US; rv:1.9.1.6) Gecko/20091201 Firefox/3.5.6
[/INDENT]
[SIZE="3"]
Installation[/SIZE]
[LIST=1]
[*]Uninstall previous scripts by running 
```

sudo rm /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm /usr/lib/mozilla/plugins/libflashplayer.so 
```
[*]Enable partner repository:
Select System->Administration->Software Sources
Go to "Other Sources" tab
Check "partner" line 
Close window
[*]Install Adobe script from partner's repository:
```
sudo apt-get update
sudo apt-get install adobe-flashplugin
```
[*]Close all browsers.
[*]Restart your browser.
[*]Test by going to [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/).  Version 11,1,102,62 should show up in "Version" box.
[/LIST]



[SIZE="3"]
Troubleshooting[/SIZE]
[LIST]

[*] **Uninstall instructions**
```

sudo rm /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm /usr/lib/mozilla/plugins/libflashplayer.so 
```
If you get errors during uninstall, you probably didn't install it correctly.
If you still have flash plugin in Firefox after uninstall, post the information related to the flash plugin provided by shown in about:****plugins.


[*]**Complete cleanup instructions.**  
brainspank contributed a script in comment 72, [direct link]("http://ubuntuforums.org/showpost.php?p=8666948&postcount=72"), which wipes all versions of Flash from your computer.  Try running this script and then re-running Get64bitFlash.


[*]**No sound?**
Sound on a clean installation of Karmic 9.10 or Lucid 10.04 should work out of box.  However, if you upgraded your machine from older versions of Ubuntu, or if you customized your audio, you sound may not work.  In this case, try following instructions in [thread="1455816"]this thread.[/thread]


[*]**Compiz/Desktop Effects**
If you are experiencing stability issues or problems with full screen, temporarily disable desktop effects.  Best strategy is to run command:
```

metacity --replace &

```
If flash suddenly starts working, consider turning off desktop effects permanently, or consult **Compiz** forums.  The bug is not in flash.


[*]**Instability and Crashing** due to Adobe Air.
By themselves, AIR and the Flash plugin in Firefox both work great. Though sometimes when I navigate to a page in Firefox with Flash on it while AIR is running, Firefox exits due to a segmentation fault.  Examples of AIR apps are **Pandora** and **tweetdeck**.  This bug is reported only for 64-bit Ubuntu.  [thread="1080781"]More info.[/thread]

[*]If you are having problems with stability, go to System / Administration / Software Sources, click on Updates tab and select Backports and Proposed.  Update and upgrade.


[*]**Screensaver**
If you have issues with full screen mode popping back to actual size (like on Hulu), check your screensaver and power management settings (uncheck "Activate screensaver when computer is idle" and put sliders to the right). 

[*]**Firefox 3.5 on Jaunty**
If Flash works in Firefox 3.0.X but doesn't work in Firefox 3.5.X that you downloaded from Mozilla site or using Ubuntuzilla, then you are running 64-bit Firefox 3.0.X and 32-bit Firefox 3.5.X.  This plugin is 64-bit and will not work in a 32-bit browser.  Remove 32-bit browser and install supported 64-bit browser by following instructions at [FirefoxNewVersion from ubuntu community wiki]("https://help.ubuntu.com/community/FirefoxNewVersion").


[*]**Intel graphics driver bug**
If you have an Intel video card, you may experience a bug in Intrepid and Jaunty.  
  Source: [thread="1130582"]Performance optimizations[/thread], based on [bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/314928").
> 
  2. Download Bartec's fixmtrr.sh script and make it executable:
```

$ sudo wget http://launchpadlibrarian.net/26193373/fixmtrr.sh -O /usr/local/bin/fixmtrr.sh
$ sudo chmod +x /usr/local/bin/fixmtrr.sh

```
  3. Create a symbolic link to ensure the fixmtrr.sh script is executed upon each login via GDM:
```

$ sudo ln -s /usr/local/bin/fixmtrr.sh /etc/gdm/PostLogin/Default

```
  N.B. This works only if you are using the GNOME Display Manager (GDM). KDE/other users need to execute this script manually - see the Important Note section. 



[*]**Flash crashes on older 64-bit CPUs**
If firefox crashes with "Illegal instruction", possibly on all sites except youtube:
```

$ firefox
Illegal instruction

```
then read the [thread="1263905"]following thread[/thread] about CPUs lacking lahf_lm instruction.  Users report this problem with old Xeons and old Athlon64 chips.


[*]**How to install for 32-bit Adobe Flash installation on 64-bit systems**
Use this method IF AND ONLY IF you can't get 64-bit Adobe Flash working. You cannot run 32-bit and 64-bit simultaneously. 
[LIST=5]
[*]Complete cleanup instructions.
brainspank contributed a script in comment 72, [direct link]("http://ubuntuforums.org/showpost.php?p=8666948&postcount=72"), which wipes all versions of Flash from your computer.  Run this script.
[*]Run command ```
sudo apt-get install flashplugin-installer
```
[*]Close all browsers.
[*]Test by going to [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/).  Version 10,1,82,76 should show up in "Version" box.
[*]Youtube and some other sites will work.  Many sites will not.  Complaints here: [http://www.adobe.com/support/flash/](http://www.adobe.com/support/flash/)
[/LIST]

[/LIST]

[SIZE="3"]
Changelog[/SIZE]
Version 1.0
Flash 11 RELEASE for 64-bit. FINALLY! Version 11,0,1,152.
Version 0.4.0b
Flash 11 Beta for 64-bit
Version 0.3.3
"Square" Preview 3 version 10,3,162,29.
Version 0.3.1
[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)
September 27, 2010 &#8212; Flash Player "Square" has been updated to include the security enhancements described in Security Bulletin APSB10-22. In addition, 32-bit content debuggers are now available in this preview.
Updated version to 10,2,161,23
Version 0.3.0
Updated version to 10,2,161,22
Versions 0.2 and 0.3. 
[Adobe has murdered Flash for 64-bit Linux. At least for the moment.]("http://www.theregister.co.uk/2010/06/11/64_bit_flash_for_linux_dead/")
Version 0.2.3
Updated version to 10.0.45.2
Added cleanup for ~/.mozilla/plugins
Version 0.2.2
Updated version to 10.0.42.34 alpha prerelease of Adobe Flash
Version 0.2.1
Adds a symlink to /usr/lib/firefox-addons/plugins
Version 0.2
Updates for the version 10.0.32.18 of Adobe Flash

---

### Post by neilius on 2009-12-19
Many thanks for this, works perfectly upgrading Flash on my system, having previously used an earlier version of this script. Rock on! :guitar: Works in Epiphany and Google Chrome (but not sure if Chrome is using its own plugin, although it reports the same version number).

---

### Post by michael37 on 2009-12-19
> **neilius said:**
> Many thanks for this, works perfectly upgrading Flash on my system, having previously used an earlier version of this script. Rock on! :guitar: Works in Epiphany and Google Chrome (but not sure if Chrome is using its own plugin, although it reports the same version number).

Google Chrome uses Firefox plugins.

---

### Post by nanotube on 2009-12-20
suggest you also link to the instructions for running 32bit flash with 32bit firefox (for those that want to use the latest mozilla release, which is not available in the repos for any but the very latest ubuntu release).

there are instructions on the ubuntuzilla project faq, but essentially boils down to doing what you're doing, but using the 32bit flash library.

---

### Post by michael37 on 2009-12-20
> **nanotube said:**
> suggest you also link to the instructions for running 32bit flash with 32bit firefox (for those that want to use the latest mozilla release, which is not available in the repos for any but the very latest ubuntu release).

there are instructions on the ubuntuzilla project faq, but essentially boils down to doing what you're doing, but using the 32bit flash library.

Nanotube, thanks for the suggestion.  I will abstain from adding these instructions for two reasons.  One, I don't run 32-bit Firefox so I can't really advise wisely on this point.  Second, I think there are plenty of websites addressing 32-bit flash so I am not sure how much value I'll add.
If you want to write a set instructions for 32-bit Firefox users on 64-bit Ubuntu, I'll be glad to include it in this guide.

---

### Post by Treeh on 2009-12-20
Is there any advantage to do doing this over downloading the x64 Flash plug-in from Adobe Labs?

---

### Post by michael37 on 2009-12-20
> **Treeh said:**
> Is there any advantage to do doing this over downloading the x64 Flash plug-in from Adobe Labs?

Ease of use.  Adobe Flash is only available in binary form and only from Adobe site.  This script downloads and installs 64-bit version of Flash, while the flashplugin-installer package simply downloads and installs 32-bit version of Flash.

---

### Post by neilius on 2009-12-20
I wonder if Ubuntu will include the 64bit binary by default soon, as it's been quite stable, much MUCH more so than nspluginwrapper with the 32bit version!

---

### Post by michael37 on 2009-12-20
> **neilius said:**
> I wonder if Ubuntu will include the 64bit binary by default soon, as it's been quite stable, much MUCH more so than nspluginwrapper with the 32bit version!

Ubuntu won't include it until Adobe releases the product. I hope everyone here understands that they are running an alpha prerelease version.

---

### Post by neilius on 2009-12-20
Interesting that it's still in alpha after all this time.

---

### Post by nanotube on 2009-12-20
> **michael37 said:**
> Nanotube, thanks for the suggestion.  I will abstain from adding these instructions for two reasons.  One, I don't run 32-bit Firefox so I can't really advise wisely on this point.  Second, I think there are plenty of websites addressing 32-bit flash so I am not sure how much value I'll add.
If you want to write a set instructions for 32-bit Firefox users on 64-bit Ubuntu, I'll be glad to include it in this guide.

i have the info on this on the ubuntuzilla faq page, here specifically:
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#Flash](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#Flash)

Feel free to use/link to if you want. :)

---

### Post by Yellow Pasque on 2009-12-20
> suggest you also link to the instructions for running 32bit flash with 32bit firefox
Get the 32-bit version of libflashplayer.so and put it in /usr/lib32. Double-check that it's actually the 32-bit version, i.e.:
```
file /usr/lib32/libflashplayer.so
```
I guess you may need some other lib32 packages too.

---

### Post by michael37 on 2009-12-20
> **nanotube said:**
> i have the info on this on the ubuntuzilla faq page, here specifically:
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#Flash](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#Flash)

Feel free to use/link to if you want. :)

This will break 64-bit plugin.  I don't feel comfortable with these instructions.  Is there a way to separate the plugins?

---

### Post by michael37 on 2009-12-20
> **Temüjin said:**
> Get the 32-bit version of libflashplayer.so and put it in /usr/lib32. Double-check that it's actually the 32-bit version, i.e.:
```
file /usr/lib32/libflashplayer.so
```
I guess you may need some other lib32 packages too.

I have not found code that looks for Firefox plugins in /usr/lib32.  Is this Ubuntuzilla specific?

---

### Post by efflandt on 2009-12-20
I have an early Athlon64 3200+ from 2004 (without lahf_lm instruction) and flashplugin v 10.0.42.34 still requires the flashplugin-lahf-fix.so detailed in Illegal Instruction link.

If anyone has issues with full screen mode popping back to actual size (like on Hulu), check your screensaver and power management settings (uncheck "Activate screensaver when computer is idle" and put sliders to the right).  My Visual Effects are set to none.

---

### Post by michael37 on 2009-12-20
> **efflandt said:**
> I have an early Athlon64 3200+ from 2004 (without lahf_lm instruction) and flashplugin v 10.0.42.34 still requires the flashplugin-lahf-fix.so detailed in Illegal Instruction link.

If anyone has issues with full screen mode popping back to actual size (like on Hulu), check your screensaver and power management settings (uncheck "Activate screensaver when computer is idle" and put sliders to the right).  My Visual Effects are set to none.

Thanks for the hints, I will include them.

---

### Post by nanotube on 2009-12-20
> **michael37 said:**
> This will break 64-bit plugin.  I don't feel comfortable with these instructions.  Is there a way to separate the plugins?

i don't have any 64bit machines to look at... if /usr/lib32 exists, as temujin says, then that may be it. otherwise, no. if the latter is the case, then the user just has to decide whether he wants to run the mozilla build with flash, or the ubuntu repos build with flash.

---

### Post by Hybird on 2009-12-21
I have 3.5.6 firefox install which I believe is the 64bit version and when I go to "About" in the help tab I get this:

```
Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-US; rv:1.9.1.6) Gecko/20091201 Firefox/3.5.6
```I used Ubuntuzilla to get newest 64 bit version.

When I downloaded and execute the script to install the flash player it executes in terminal and closes, but when I restarted Firefox and check "about : plugins" I have none? And obviously flash doesn't work.. any ideas?

---

### Post by michael37 on 2009-12-21
> **Hybird said:**
> I have 3.5.6 firefox install which I believe is the 64bit version and when I go to "About" in the help tab I get this:
...
I used Ubuntuzilla to get newest 64 bit version.


Ubuntuzilla provides only 32-bit version.  Use 32-bit flash with this version of Firefox. [Instructions from Ubuntuzilla.]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#Flash")

If you want 64-bit version of Firefox, see [here]("https://help.ubuntu.com/community/FirefoxNewVersion").

---

### Post by Hybird on 2009-12-21
Ok, thanks. I thought I had the 64 bit version of firefox... I think that originally I had 64 bit flash on 32 bit firefox which caused my flash videos to freeze and go gray. I guess I'll just install 32 bit flash and hope for the best.

---

### Post by Yellow Pasque on 2009-12-21
> I have 3.5.6 firefox install which I believe is the 64bit version
It's not; it says 'i686' (32-bit) on an x86_64 system

---

### Post by Mrsongs on 2009-12-21
Thanks! I've been struggling with this for a while, and the new version of libflashplayer.so does the trick. BTW, the addons tab in Firefox now shows both Shockwave Flash 10.0 r32 and Shockwave Flash 10.0 r42 despite my making sure that r32 was gone from the relevant directories. I first tried using the disable button on r32 and flash did not work; both versions must indicate that they are enabled for flash to work.

---

### Post by watchpocket on 2009-12-21
No Flash installed after following the steps exactly.  No Flash in "about: plugins".  Very Frustrating.  

Do I have "libflashplayer.so"  installed as user "rj"  (that's me)?  (See below.)

Would that be my problem? 

 It *was* installed as "rj    rj" (instead of "root   rj") right after running the script, so I did a

sudo chown root /usr/lib/mozilla/plugins/libflashplayer.so

which made it "root  rj".   Does it need to be "root  root" (as per the other plugins)? If so, I'm not sure how to create that.  (And, are permission what they should be?)

[rj-desktop:~]  [v4.3.10]  zsh  551 --> lf /usr/lib/mozilla/plugins                                                     
total 11848
   4 drwxr-xr-x 2 root root    4096 2009-12-21 21:47 ./
   4 drwxr-xr-x 4 root root    4096 2009-10-27 14:06 ../
  92 -rw-r--r-- 1 root root   90008 2009-09-24 08:19 gecko-mediaplayer-dvx.so
  96 -rw-r--r-- 1 root root   94104 2009-09-24 08:19 gecko-mediaplayer-qt.so
  96 -rw-r--r-- 1 root root   94104 2009-09-24 08:19 gecko-mediaplayer-rm.so
  96 -rw-r--r-- 1 root root   94104 2009-09-24 08:19 gecko-mediaplayer.so
  96 -rw-r--r-- 1 root root   94104 2009-09-24 08:19 gecko-mediaplayer-wmp.so

---->   9364 -rwxr-xr-x 1 root rj   9570952 2009-10-28 00:04 libflashplayer.so*   <-----
                              
   8 -rw-r--r-- 1 root root    6120 2009-11-03 05:58 librhythmbox-itms-detection-plugin.so
 104 -rw-r--r-- 1 root root  101536 2009-11-11 04:15 libtotem-cone-plugin.so
 108 -rw-r--r-- 1 root root  106240 2009-11-11 04:15 libtotem-gmp-plugin.so
  76 -rw-r--r-- 1 root root   72816 2009-11-11 04:15 libtotem-mully-plugin.so
  84 -rw-r--r-- 1 root root   81336 2009-11-11 04:15 libtotem-narrowspace-plugin.so
 100 -rw-r--r-- 1 root root   94912 2009-10-19 16:58 libvlcplugin.so
 300 -rw-r--r-- 1 root root  299872 2009-06-14 15:34 mplayerplug-in-dvx.so
   4 -rw-r--r-- 1 root root    1067 2009-06-14 15:33 mplayerplug-in-dvx.xpt
 300 -rw-r--r-- 1 root root  299872 2009-06-14 15:34 mplayerplug-in-qt.so
   4 -rw-r--r-- 1 root root    1067 2009-06-14 15:33 mplayerplug-in-qt.xpt
 300 -rw-r--r-- 1 root root  299872 2009-06-14 15:34 mplayerplug-in-rm.so
   4 -rw-r--r-- 1 root root    1067 2009-06-14 15:33 mplayerplug-in-rm.xpt
 300 -rw-r--r-- 1 root root  299864 2009-06-14 15:34 mplayerplug-in.so
 300 -rw-r--r-- 1 root root  299872 2009-06-14 15:34 mplayerplug-in-wmp.so
   4 -rw-r--r-- 1 root root    1067 2009-06-14 15:33 mplayerplug-in-wmp.xpt
   4 -rw-r--r-- 1 root root    1067 2009-06-14 15:33 mplayerplug-in.xpt
   0 lrwxrwxrwx 1 root root      31 2009-12-20 23:30 xineplugin.so -> ../../xine-plugin/xineplugin.so
[rj-desktop:~]  [v4.3.10]  zsh  552 -->


Running Karmic on a 64-bit System76 Wild Dog Performance desktop unit (model wilp6), 3 GHz quad core intel processor Q9650, 1 GB nVidia GeForce GTS 250 video card, Firefox 3.5.6.  Thanks for any suggestions.

---

### Post by michael37 on 2009-12-21
> **watchpocket said:**
> No Flash installed after following the steps exactly.  No Flash in "about: plugins".  Very Frustrating.  

Are you sure your Firefox is 64-bit?

---

### Post by watchpocket on 2009-12-21
Just now have read the whole thread & determined that I'm running 32-bit Firefox. Will follow link re FirefoxNewVersion at community wiki to get the 64-bit version.

Thank you for posting the script, which will probably work for me once I get 64-bit FF up.

---

### Post by watchpocket on 2009-12-21
"Jaunty and Karmic[install the following package]("https://help.ubuntu.com/community/InstallingSoftware#installing-a-package"): ***[firefox-3.5]("apt:firefox-3.5")***.  Firefox 3.5 will be installed alongside Firefox 3.0." 
"Alert: Firefox doesn't know how to open this address, because the protocol (apt) isn't associated with any program."   

 So, how do I get 64-bit FF 3.5.6?

---

### Post by michael37 on 2009-12-21
> **watchpocket said:**
> "Jaunty and Karmic[install the following package]("https://help.ubuntu.com/community/InstallingSoftware#installing-a-package"): ***[firefox-3.5]("apt:firefox-3.5")***.  Firefox 3.5 will be installed alongside Firefox 3.0." 
"Alert: Firefox doesn't know how to open this address, because the protocol (apt) isn't associated with any program."   

 So, how do I get 64-bit FF 3.5.6?

Three issues here.  

The link didn't open since your 32-bit Firefox from Mozilla binary build didn't know how to handle (apt) type link.  Ubuntized firefox knows how to work it.

firefox-3.5 package is really the latest of firefox-3.5.x family. So, all you got to do is select Applications -> Ubuntu Software Center, and search for Firefox there.  Firefox 3.5.6 is simply named "Firefox Web Browser".  Once you install it, Ubuntu will automatically and seamlessly keep Firefox at the latest security update.  

**BUT** you may need to uninstall the 32-bit version before installing 64-bit version.  Since I don't know how you installed it, I can't help you do the uninstall.  I also suspect that you may also need to sort through your plugins and get rid of non-functioning 32-bit ones.  I saw a couple in them in the listing of /usr/lib/mozilla/plugins/ directory.
Run file <name> to see if it's 32-bit or 64-bit. 
64-bit plugin: 
```
mike@home: /usr/lib/mozilla/plugins$ file libflashplayer.so 
libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped

```
32-bit plugin:
```
mike@home: /usr/lib/mozilla/plugins$ file nphelix.so 
nphelix.so: symbolic link to `/usr/local/RealPlayer/mozilla/nphelix.so'

(ugh, some complexity here, this is a link)

mike@home: /usr/lib/mozilla/plugins$ file /usr/local/RealPlayer/mozilla/nphelix.so
/usr/local/RealPlayer/mozilla/nphelix.so: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, not stripped

```

---

### Post by michael37 on 2009-12-22
> **Mrsongs said:**
> Thanks! I've been struggling with this for a while, and the new version of libflashplayer.so does the trick. BTW, the addons tab in Firefox now shows both Shockwave Flash 10.0 r32 and Shockwave Flash 10.0 r42 despite my making sure that r32 was gone from the relevant directories. I first tried using the disable button on r32 and flash did not work; both versions must indicate that they are enabled for flash to work.

I tried to reproduce it, but I am having very hard time figuring out how you have r32 and r42 installed at the same time.  Could you please run command:
```
locate libflashplayer
```

If command locate is not found, [install mlocate]("apt:mlocate"), and run the command in ~24 hours.  That's how long it will take mlocate to index your hard drive.

---

### Post by MirceaD on 2009-12-22
Thank you very much! It worked like a charm.

---

### Post by watchpocket on 2009-12-22
> **michael37 said:**
> firefox-3.5 package is really the latest of firefox-3.5.x family. So, all you got to do is select Applications -> Ubuntu Software Center, and search for Firefox there.  Firefox 3.5.6 is simply named "Firefox Web Browser".  Once you install it, Ubuntu will automatically and seamlessly keep Firefox at the latest security update.  

**BUT** you may need to uninstall the 32-bit version before installing 64-bit version. 




(1) I first deleted five non-64-bit plugins from /usr/lib/mozilla/plugins.

--> file mplayerplug-in-wmp.xpt                             
mplayerplug-in-wmp.xpt: XPConnect Typelib version 1.2

(That's what "file" reported, not

 "ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, not stripped.")

(The ones I deleted were all *.xpt files (instead of *.so files).

(2) I uninstalled my 32-bit Firefox and its associated files.

(3) I then installed "Firefox Web Brower" from Applications --> Ubuntu Software Center, but apparently got just the 32-bit Firefox again: 

"Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-US; rv:1.9.1.6) Gecko/20091201 Firefox/3.5.6."

I then came to a complete standstill at <https://help.ubuntu.com/community/AptURL>

at this point:  "Clic on this link [apt://mplayer](apt://mplayer) , and in the "Application launch" windows, clic on the "Choose" button [& so on] . . . and validate."

because after adding the necessary strings and values in about:config, I still couldn't go anywhere upon clicking on apt://mplayer.  

So I still have 32-bit Firefox and cannot yet seem to install 64-bit FF.  Really strange, but maybe something obvious to a fresh eye.  Thanks for any/all suggestions.

---

### Post by michael37 on 2009-12-22
> **watchpocket said:**
> 
(2) I uninstalled my 32-bit Firefox and its associated files.

(3) I then installed "Firefox Web Brower" from Applications --> Ubuntu Software Center, but apparently got just the 32-bit Firefox again: 

"Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-US; rv:1.9.1.6) Gecko/20091201 Firefox/3.5.6."

Well, the thing is that you apparently have not uninstalled 32-bit Firefox.   The help/about above is from the 32-bit version. I edited the OP so you can check the outputs of help/about for 32-bit and 64-bit FF 3.5.6.  Another tell-tale sign is lack of word Ubuntu in this line.  If you were running Firefox installed from the software center, you would see Ubuntu there. Looks like you still have two Firefoxes on your computer.

---

### Post by watchpocket on 2009-12-22
> **michael37 said:**
> Well, the thing is that you apparently have not uninstalled 32-bit Firefox.   The help/about above is from the 32-bit version. I edited the OP so you can check the outputs of help/about for 32-bit and 64-bit FF 3.5.6.  Another tell-tale sign is lack of word Ubuntu in this line.  If you were running Firefox installed from the software center, you would see Ubuntu there. Looks like you still have two Firefoxes on your computer.


In trying to delete all previous firefoxes, I think I deleted too much.  I re-installed from Synaptic Package Manager and have a firefox icon in my panel, but when I click on it, I get this: "Error  Could not launch application.  Falied to execute child process 'firefox' (No such file or directory).  Typing this from text-browser lynx.

---

### Post by michael37 on 2009-12-22
> **watchpocket said:**
> In trying to delete all previous firefoxes, I think I deleted too much.  I re-installed from Synaptic Package Manager and have a firefox icon in my panel, but when I click on it, I get this: "Error  Could not launch application.  Falied to execute child process 'firefox' (No such file or directory).  Typing this from text-browser lynx.

run command

sudo apt-get install --reinstall firefox-3.5

---

### Post by watchpocket on 2009-12-22
> **michael37 said:**
> run command

sudo apt-get install --reinstall firefox-3.5

I did this in the <alt>+<F2> "Run Application" box, re-booted and got the same error message.

Then I did it in the terminal (to no avail):

[rj-desktop:~]  [v4.3.10]  zsh  661 --> sudo apt-get install --reinstall firefox-3.5                                      
[sudo] password for rj: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/960kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 189462 files and directories currently installed.)
Preparing to replace firefox-3.5 3.5.6+nobinonly-0ubuntu0.9.10.1 (using .../firefox-3.5_3.5.6+nobinonly-0ubuntu0.9.10.1_amd64.deb) ...
Unpacking replacement firefox-3.5 ...
Setting up firefox-3.5 (3.5.6+nobinonly-0ubuntu0.9.10.1) ...
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox-3.5
Please restart all running instances of firefox-3.5, or you will experience problems.

[rj-desktop:~]  [v4.3.10]  zsh  662 -->


Still getting same error message box whether I click on the Firefox icon in the panel or the Applications --> Internet --> Firefox Web Browser icon.

I've royally screwed up something (i.e. deleted something essential) but have no idea what, and no idea where to go from here. Ugh.

(Meanwhile I downloaded the arora browser and am using it to post.)

---

### Post by Yellow Pasque on 2009-12-22
<snip>

---

### Post by watchpocket on 2009-12-22
[quote=Temüjin;8545728]<snip>/quote]

  <snip>

---

### Post by michael37 on 2009-12-22
> **watchpocket said:**
> I did this in the <alt>+<F2> "Run Application" box, re-booted and got the same error message.

Then I did it in the terminal (to no avail):

Preparing to replace firefox-3.5 3.5.6+nobinonly-0ubuntu0.9.10.1 (using .../firefox-3.5_3.5.6+nobinonly-0ubuntu0.9.10.1_amd64.deb) ...
Unpacking replacement firefox-3.5 ...
Setting up firefox-3.5 (3.5.6+nobinonly-0ubuntu0.9.10.1) ...
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox-3.5
Please restart all running instances of firefox-3.5, or you will experience problems.

[rj-desktop:~]  [v4.3.10]  zsh  662 -->


Still getting same error message box whether I click on the Firefox icon in the panel or the Applications --> Internet --> Firefox Web Browser icon.

I've royally screwed up something (i.e. deleted something essential) but have no idea what, and no idea where to go from here. Ugh.

(Meanwhile I downloaded the arora browser and am using it to post.)

Hard to help fix stuff that you don't know is missing.

Try to reinstall xulrunner-1.9.1, xulrunner-1.9.1-gnome-support, firefox-3.5-gnome-support and firefox-3.5-branding.  

Speaking of trolling, this particular subthread is totally off-topic to Flash.  If above suggestion doesn't fix it, please start a new topic.  Feel free to private message me with the link to that topic.

---

### Post by Meekle on 2009-12-23
Yay for this. I've been banging my head on Flash installer from package manager.  Thank you!

---

### Post by cwgpress on 2009-12-27
A big thank you! I was in dependency hell trying to do this from synaptic. I haven't had usable flash since Karmic came out and I missed being able to see youtube without downloading or using a different browser. This was like a Christmas present to me, albeit a couple days after.

---

### Post by Hilko on 2009-12-27
Many thanks !!! I've always had difficulty installing flash. Now youtube works.

However, i cannot play the media on this page [http://news.bbc.co.uk/2/hi/entertainment/8423340.stm](http://news.bbc.co.uk/2/hi/entertainment/8423340.stm)

Has anyone been able to play the media on this page after using the script from the first post ?
Can anyone please help me to get it work ?

---

### Post by palenekim on 2009-12-28
Thanks a lot everyone. It was a lot of help. I am brand new to linux yet open to the experience. After following the instructions to download the link that was first posted by  'michael37' everything worked out perfectly. Hopefully Adobe will have a true release of flash player (64-bit) that will be a standard update for ubuntu.

---

### Post by rtunstall on 2009-12-28
Help please. When i right click on the attachment and save it, it saves as attachment.php. What am I doing wrong??

---

### Post by michael37 on 2009-12-28
> **rtunstall said:**
> Help please. When i right click on the attachment and save it, it saves as attachment.php. What am I doing wrong??

You are probably not using a modern Firefox browser.  Check in Help/About.

In any case, it's safe to manually rename the file from attachment.php to the correct file name.

---

### Post by stryderjzw on 2009-12-28
This is frustrating. My flash plugin now keeps crashing and I'm not sure how to debug it. I think it's the new 64-bit version that came out a little while ago.

Strangely, the 32-bit Flash with nswrapper is more stable, but the Compiz bug keeps me from clicking on flash buttons (like the pause button in Youtube). 

Ugh.

---

### Post by michael37 on 2009-12-28
> **stryderjzw said:**
> This is frustrating. My flash plugin now keeps crashing and I'm not sure how to debug it. I think it's the new 64-bit version that came out a little while ago.

Strangely, the 32-bit Flash with nswrapper is more stable, but the Compiz bug keeps me from clicking on flash buttons (like the pause button in Youtube). 

Ugh.

1. Read the OP.  Lots of troubleshooting there, esp for Nvidia and Intel graphic card owners.  
2. If that doesn't help, post what's under Shockwave Flash in about:****plugins (open new tab, type about:****plugins in a navigation toolbar)

---

### Post by stryderjzw on 2009-12-28
I purged the files again and redownloaded the 64-bit libflashplayer.so file from Adobe manually. Restarted and it seems to be working again. :D

---

### Post by metaplecticGroup on 2009-12-30
Hi, I installed the 64 bit flash player as instructed by
the sticky.  I went to the Adobe web page at the end
and indeed I have version 10,0,42,34 installed. But 
I still can't make the videos on Hulu or You Tube 
to go full screen. These are my system specs
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.16) 
Gecko/2009121602 Ubuntu/8.04 (hardy) Firefox/3.0.16
Any advice?

---

### Post by emzed on 2010-01-02
Thanks a million!! Using this script I finally was able to use flash on my Asrock 330 HT / Ubuntu 9.10

---

### Post by AgentZ86 on 2010-01-02
How do I tell if I'm running 64 bit Firefox or not ? was my initial question

But I've answered this myself in that 64 bit firefox won't run on 32 bit install unless you have the 32 bit libraries etc.

So Most should assume they have 64 bit firefox on 64 bit install

To conclude this GetFlash64 works perfectly

Thanks for the work, I really need to learn how to write scripts

Nice Job

---

### Post by marn on 2010-01-02
I'm trying to find out if my FF is 64 Bit. I use the german "version". When I click on Help (Hilfe) --> About (über Mozilla) all it tells me is this: 

Firefox Version 3.5.6 Mozilla Firefox for Ubuntu canonical  - 1.0 (then some legal stuff in german)

As I have been having problems with flash, I would like to follow the instructions above, would like to make sure that I am really using the 64 Bit version though (don't like doing things on a hunch)

System: 9.10 AMD 64 bit on Dell Vostro 1510

Am I missing something?

Marn

Edit: solved my own problem by typing "about:" into the adress bar. Result: 
Build identifier: Mozilla/5.0 (X11; U; Linux x86_64; de; rv:1.9.1.6) Gecko/20091215 Ubuntu/9.10 (karmic) Firefox/3.5.6

---

### Post by sigurnjak on 2010-01-02
I am running 64 bit flash from sevenmachine ppa and love it so far . Websites that would never render properly render great , full screen video works great .
But not all is well in 64bit flash .
1 Facebook Yoville for my wife is not working , i strongly believe it is game and not flash . For her i have Seamonkey2 with flash 9 32 bit and it does job fine .

2 When i play music and browse and come across flash video it kicks out my music player (audcious or rhythmbox ) . In 32bit linux there is libflashsupport.so or something similar to fix it , but so far i have not been able to find one for 64 bit Karmic .

If anyone have any trick up their sleeve please share !

---

### Post by Podex on 2010-01-03
Hi,
Your script works fine but there are two spelling mistakes: 

> 
 This script is used to setup the Flash 10 Alpha. 
 By entering yes below you acknowlage that you 
 are installing development software and you 
 will file bug reports with Adobe for every 
 problem you incounter.


acknowlage=acknowledge and incounter=encounter

---

### Post by a2z on 2010-01-04
> **efflandt said:**
> I have an early Athlon64 3200+ from 2004 (without lahf_lm instruction) and flashplugin v 10.0.42.34 still requires the flashplugin-lahf-fix.so detailed in Illegal Instruction link.

If anyone has issues with full screen mode popping back to actual size (like on Hulu), check your screensaver and power management settings (uncheck "Activate screensaver when computer is idle" and put sliders to the right).  My Visual Effects are set to none.

I've gotten around this by holding ctrl while clicking "full screen" and then release mouse then ctrl. But that was with jaunty at times. 

I'm having similar problems of this thread with karmic. Some videos all buttons work, some no buttons work. And When full screen does work, the progress bar is half way down the screen. And I don't think the video window is any bigger. Even though everything else is not visable.

---

### Post by JackRock on 2010-01-04
I've followed the original post, and it worked beautifully.

---

### Post by Dx11 on 2010-01-05
I get the following error when running the script 
Errors were encountered while processing: flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
However video and sound in youtupe are working, so thanks for the script

---

### Post by Moozillaaa on 2010-01-05
> **rtunstall said:**
> Help please. When i right click on the attachment and save it, it saves as attachment.php. What am I doing wrong??

> **michael37 said:**
> You are probably not using a modern Firefox browser.  Check in Help/About.

In any case, it's safe to manually rename the file from attachment.php to the correct file name.

And perhaps he IS using the correct browser version, as I am, and got the same rt click options...




[IMG]http://ubuntuforums.org/attachment.php?attachmentid=142579&d=1262712552[/IMG]

Edit post #1:

[SIZE=3]Installation[/SIZE]
[LIST=1]
[*]Download Get64bitFlash-0.2.2.tar.gz script at the end of this post [COLOR=Red]**(use "Right Click, Save Link As...)**[/COLOR]
[/LIST]

This step gives the user an 'attachment.php', on their desktop.

Change to: Left click, Save file. It will by default save to desktop. 

Then proceed to #2.


Edit:
I just got to post #41, and see I might have browser problems.
This should be in post #1: If the following rt click option appears, you might then have the wrong browser installed. Do this check:
(Insert proper browser check sequence)

Having read first 41 posts so far, I see that having the proper browser version is ALL-important...

I believe also that user Watchpocket's problem should not be moved to a separate thread; rather followed through, for others who WILL do the same thing wrong. JMO.

---

### Post by Moozillaaa on 2010-01-05
deleted; still at step described in previous post...

---

### Post by AgentZ86 on 2010-01-05
> **Moozillaaa said:**
> Item #3 says to close all browsers.

Directions must then be resumed from another machine??? (or from a printout)

No you run the script/file from the folder in which you downloaded to, then once the install completes as described you then can use your browser and new plugin

read #4,5,6,7 please

Just download the file to your home directory, or if it defaults to your download file then move to home, then right click and extract here.
Then you will see the files
then continue to follow #4,5,6,7

---

### Post by Moozillaaa on 2010-01-05
> **AgentZ86 said:**
> No you run the script/file from the folder in which you downloaded to, then once the install completes as described you then can use your browser and new plugin

read #4,5,6,7 please

Just download the file to your home directory, or if it defaults to your download file then move to home, then right click and extract here.
Then you will see the files
then continue to follow #4,5,6,7

My first question is about supported browsers, and a discrepancy that I've detailed already:

Post 1 says my FF version is supported.

But OP told user rtunstall post 41, who got the same result that I did, that he probably was NOT using a 'modern' version of FF. I do NOT want to run down the same rabbit hole that user watchpocket ran into, ending at post 35, with no solution. I don't have the computer savvy as some others here, BUT, I DO know NOT to proceed if there's still a question...

---

### Post by HappyFeet on 2010-01-06
Try this:

First, uninstall the flash you have. Then do:
```
sudo apt-get clean && sudo apt-get autoremove
```
Then get the [64bit flash]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz") file.

Right click it and **extract here**. You will be left with **libflashplayer.so** file. Put the libflashplayer.so file in your home folder.

Then do:```
sudo cp /home/your_user_name/libflashplayer.so /usr/lib64/mozilla/plugins
```

Make sure to put *your name* where I wrote your_user_name.

Restart firefox if open.

I don't mean to step on anyone's toes, but why the need for a script? Once libflashplayer.so is in your home folder, just copy it to the right place. Btw, it does not have to be in your home folder. It's just 1 way to do it.

---

### Post by Moozillaaa on 2010-01-06
My first question is about supported browsers, and a discrepancy that I've detailed already:

Post 1 says my FF version is supported.

But OP told user rtunstall post 41, who got the same result that I did, that he probably was NOT using a 'modern' version of FF. I do NOT want to run down the same rabbit hole that user watchpocket ran into, ending at post 35, with no solution. I don't have the computer savvy as some others here, BUT, I DO know NOT to proceed if there's still a question...

---

### Post by michael37 on 2010-01-06
> **Moozillaaa said:**
> My first question is about supported browsers, and a discrepancy that I've detailed already:

Post 1 says my FF version is supported.

But OP told user rtunstall post 41, who got the same result that I did, that he probably was NOT using a 'modern' version of FF. I do NOT want to run down the same rabbit hole that user watchpocket ran into, ending at post 35, with no solution. I don't have the computer savvy as some others here, BUT, I DO know NOT to proceed if there's still a question...

In your picture, you didn't show the bottom of the About Firefox window which actually says if your browser is supported or not.  Please copy/paste that text output, it should start with *Mozilla/5.0*.

---

### Post by LazyEyeFIME on 2010-01-06
Hi everyone, I am new around here, I installed Flash for 64 bit from the official site, but sometimes when I am watching videos on YouTube the video dissapers or when I click on the play button it did not respond.

---

### Post by Moozillaaa on 2010-01-06
> **michael37 said:**
> In your picture, you didn't show the bottom of the About Firefox window which actually says if your browser is supported or not.  Please copy/paste that text output, it should start with *Mozilla/5.0*.

Good call! Thanks for replyin' here... I didn't know there was more version info.

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.6) Gecko/20091215 Ubuntu/9.10 (karmic) Firefox/3.5.6

It came with the canonical-burned CD, if that tells more...

OK - I just triple checked - totally identical version as what post 1 says is supported, but this doesn't explain that rt click discrepancy ???

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=142723&d=1262829856[/IMG]

---

### Post by jewels. on 2010-01-07
I am having trouble with the download link above?  When I download the file, and attempt to extract it, I get the following error message:

SOFTWARE: Archive Manager

POPUP WINDOW:
An error occurred while loading the archive.
Command Line Output:
gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Exiting with failure status due to previous errors

Could anyone offer a suggestion?  Am I doing something incorrectly?  Thank you in advance!

~jewels

---

### Post by rememberthemer on 2010-01-08
Don't want to tread on anyones toes her but surely the safest way to get flash player for amd64 is to backport it from Debian Squeeze/Sid. This works for Karmic, is completely reversible, and won't clobber anything else.

First make sure that any existing installs of flashplayer etc are purged. Note that nspluginwrapper does not always deregister flashplayer so you should check.

```
nspluginwrapper -l
```
and if 'libflash...' etc is there, then remove them 
```
sudo nspluginwrapper -r <the flash bits you still have> 
```

All removed? Ok you need some of the Ubuntu/Debian packaging tools
```
sudo apt-get install debhelper cdbs
```

Then download the debian source into a new directory somewhere
```
wget http://ftp.de.debian.org/debian/pool/contrib/f/flashplugin-nonfree/flashplugin-nonfree_2.8.tar.gz http://ftp.de.debian.org/debian/pool/contrib/f/flashplugin-nonfree/flashplugin-nonfree_2.8.dsc

```
Now use the following steps to extract and build the package:
```
dpkg-source -x flashplugin-nonfree_2.8.dsc
cd flashplugin-nonfree-2.8
dpkg-buildpackage -rfakeroot
cd ..

```
Admire your new package *flashplugin-nonfree_2.8_amd64.deb*
Install it with either dpkg or gdebi, e.g.
```
sudo dpkg -i flashplugin-nonfree_2.8_amd64.deb
```

---

### Post by Deeday on 2010-01-09
Same problem here as Hilko and LazyEyeFIME: Flash videos like [_this one_]("http://news.bbc.co.uk/1/hi/england/8450052.stm") do not respond to clicks, so they cannot be played, unless they start automatically when the page loads. Can anyone shed any light on this issue? That would be much appreciated.

I'm running:
Intel Core2
Karmic 9.10, 64 bit
Firefox 64 bit
Flash plug-in 10,0,42,34

---

### Post by Kamen-rider on 2010-01-10
I'm using shiretoko 3.5.7

sorry, very unstable, always automatically close itself.

i'm trying to uninstall 64bit firefox and install 32bit.

---

### Post by projectbronco on 2010-01-10
Thanks for the write up, I've had to use this a few times when doing a fresh install.
I've got to have youtube working! lol
Thanks again.

---

### Post by rememberthemer on 2010-01-11
Deeday

I can view this flash flawlessly under both chrome and firefox and from the looks of things have a very similar system to you.

I use the flashplugin package from Debian Squeeze/Sid installed as per my instructions above. At install time, the package downloads and installs the flashplugin for the correct arch. It is the way ubuntu used to install flash.

There is no need to worry about using packages from Debian. Almost every Ubuntu package was born as a Debian package - in fact the majority are completely unchanged and simply require a rebuild to function perfectly. E.g. the google chrome packages installs under both Debian and Ubuntu and works well in each.

---

### Post by wil3y on 2010-01-14
Thanks OP, i was havin issues installing flash (newb) problem solved  :D

---

### Post by tripart on 2010-01-14
rememberthemer, 

Thanks for those instructions above. It took me two tries, but that was because I still had flash showing up in Firefox add-ons from trying the previous method (with downloader script) from this thread.

Once I removed libflashplayer.so from ~/.mozilla/plugins/ I installed the package generated from your commands and successfully got the confirmation of 10,0,42,34 installed at [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

Hooray!:popcorn:

---

### Post by tripart on 2010-01-14
I should mention that the originally posted (page 1 of this thread) method did work at first for me, but after a restart Firefox wasn't displaying flash at all (verified at Adobe version test page).

Did a restart just now and still get flash version confirmation. All 64bit flash and firefox now. Double hooray. :popcorn::popcorn:

---

### Post by brainspank on 2010-01-14
In case anybody else wanted it/finds it useful.  I fought with flash for quite a while (the guide didn't work because I had some old cruft lying around).  This is just a script I built up over time to make sure that I cleaned everything out when I retried it.  Some of it I copied, some I added for my situation.

If you want to use it, I suggest running it before the Get64bitFlash script as:
```
$ sudo ./flash_remove.sh
```

flash_remove.sh
```

#!/bin/bash
apt-get remove --purge flashplugin-installer
apt-get remove --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash 
apt-get remove --purge iceweasel-flashplugin mozilla-flashplugin firefox-flashplugin 
apt-get remove --purge swfdec-mozilla libflashsupport nspluginwrapper iceape-flashplugin 
apt-get remove --purge xulrunner-flashplugin midbrowser-flashplugin xulrunner-addons-flashplugin
rm -f ~/.mozilla/plugins/*flash*
rm -f /usr/lib/firefox-addons/plugins/*flash*
rm -f /usr/lib/firefox/plugins/*flash*
rm -f /usr/lib/iceape/plugins/flashplugin-alternative.so
rm -f /usr/lib/iceweasel/plugins/flashplugin-alternative.so
rm -f /usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
rm -f /usr/lib/midbrowser/plugins/flashplugin-alternative.so
rm -f /usr/lib/mozilla/plugins/*flash*
rm -f /usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so
rm -f /usr/lib/xulrunner/plugins/flashplugin-alternative.so
rm -f /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so

```

---

### Post by mikeize on 2010-01-15
Thank you so much for this thread (and the flash/cruft remove script above).  Flash has been such a hassle, with some sites working, and others not.  Haven't tested all my favorite sites yet, but youtube and archive.org are working again!

---

### Post by D3mon_Spawn on 2010-01-16
Anyone else having problems viewing hulu videos with the latest version of this flash script? Or is it just me? Ive trying watching hulu vids on firefox and chrome but both don't seem to work. Every time I click a video it says: "Sorry we were unable to stream this video, please check your internet connection." I know its defiantly not my internet connection since hulu works on my mac computer.

---

### Post by adempewolff on 2010-01-16
Anyone else have problems in Karmic with the 64 bit flash plugin capturing the sound card/not playing nicely with pulseaudio.  There are lots of threads about earlier releases, and the 32 bit plugin having troubles, along with how to fix them, but I have found nothing for users of the 64 bit plugin.

Furthermore this problem is only on my OS which I recently upgraded from 9.04 to 9.10.  I have another partition with a clean install of 9.10 that I have been using since the beta which did not have this problem.  However when I switched back, there were all sorts of problems with flash.

First off, both the 32b and 64b plugin were installed and enabled in firefox:shock:  I tried deleting the *.so file and purging all the flash installer packages, but somehow that didn't remove it from firefox.  Finally I deleted all of mozilla's folders in /usr/, uninstalled both firefox-3.5 and ubufox packages, then reinstalled them.  At this point I discovered that ubufox automatically installs the 32b flash plugin :mad: but deleting it's .so file actually worked at removing it this time around.

So then I installed the 64b plugin.  For some reason the script in this (and previous) threads has never worked for me, but I have always just copied the file manually.  So now I finally got my system to only have one flash plugin installed--the more stable 64b one.

Problem is that it still does not seem to be playing nice with the pulseaudio server.  Sometimes when I am playing a media file with rhythmbox, pause the file, then use a flash control with sound in firefox, I am unable to resume playback of the file in Rhythmbox without first restarting firefox.

In the distant past this problem seems to have been caused for many people because firefox was bypassing pulseaudio with flash's sound output.  Unfortunately all the fixes do not seem to apply to Karmic or the 64b plugin.  Furthermore, even I am not having the problem on my clean install!  Is anyone else having this problem with Karmic and the 64b plugin, or does anyone have suggestions on what to do?

Thanks,
Austin

---

### Post by lelantus on 2010-01-18
**_D3mon_Spawn_ : Anyone else having problems viewing hulu videos with the latest version of this flash script? Or is it just me? Ive trying watching hulu vids on firefox and chrome but both don't seem to work. Every time I click a video it says: "Sorry we were unable to stream this video, please check your internet connection." I know its defiantly not my internet connection since hulu works on my mac computer."**

Yes! I even went through the trouble of installing the latest versions of both Chrome, Shiretoko, and Firefox. Hulu doesn't like any of them. Again, I *know* it's not my internet connection either, because I can stream Hulu videos just fine on the Windows PC. It may also be worthy to note that other videos that utilize Flash work just fine; Hulu is the only site I'm having any problems with. This is a new development that's got me quite peeved. Anybody have anything? I'm pretty confused about the whole thing... I'm a relatively seasoned Ubuntu user, and I really don't know why this is happening. Anybody?
~_Lelantus_

---

### Post by MadEgg on 2010-01-18
I tried the steps described by rememberthemer above, after purging all current Flash installation attempts from a 9.04 installation.

It installed and sort-of works. Youtube for example works. But sometimes it crashes. For example, loading Farmville on Facebook immediately crashes the browser without any error reported. Pretty annoying. Why isn't there any decent Ubuntu package for Flash on AMD64 available from the repo?

---

### Post by blpearl on 2010-01-19
[http://www.professormesser.com/2008/07/23/bios-and-cmos-overview/](http://www.professormesser.com/2008/07/23/bios-and-cmos-overview/)

I am having issues watching videos at the above site...  I am a bit of al Linux newB and would appreciate any help that would be given in my direction...  These are essential for my schooling right now as a study aid.  This is the beginning of my journey into the world of computing!

Once again, any help would be appreciated!!

~/Blpearl

**EDIT** 
Both Hulu and Youtube are working fine.  One other area of issue...  In all Flash videos, when I right click and select "Settings", the Settings popup does not go away.  Any ideas???  I tried clicking "Close" and pressing ESC key...  Thanks!

---

### Post by andycastille on 2010-01-19
> **michael37 said:**
> To moderators: please make this post sticky.  [thread="1259102"]It's predecessor[/thread] was sticky on the x86-64 forum, but that forum is now closed.  Thank you.

***** This is an updated version of the script since the original maintainer has not updated it in a while.  Provides December 2009's version of 64-bit Adobe Flash *****

Designed for **64-bit** Hardy 8.04, Jaunty 9.04 and Karmic 9.10 only.
Do NOT use this script on any 32-bit version of Ubuntu.
Status in Intrepid is unknown: I had so much problems with 64-bit Intrepid that I don't recommend it.

Supported 64-bit browsers **provided by Ubuntu team**: 
[LIST]
[*] Firefox 3.0.14 and later, and 3.5.5 and later for Jaunty 9.04 and Karmic 9.10.
[*] Firefox 3.0.14 and later (but NOT 3.5) in Hardy.
[/LIST]
Binary 32-bit version from Mozilla site is **NOT supported** and will not work. Select Help -> About Mozilla Firefox.  Differences are highlighted below.[INDENT]*[COLOR=Lime]64-bit browser:[/COLOR]* Mozilla/5.0 (X11; U; **Linux x86_64**; en-US; rv:1.9.1.6) Gecko/20091215 **Ubuntu**/9.10 (karmic) Firefox/3.5.6
*[COLOR=Red]32-bit browser:[/COLOR]* Mozilla/5.0 (X11; U; **Linux i686 (x86_64)**; en-US; rv:1.9.1.6) Gecko/20091201 Firefox/3.5.6
[/INDENT]For more information, see [FirefoxNewVersion from ubuntu community wiki]("https://help.ubuntu.com/community/FirefoxNewVersion").
[SIZE=3]
Installation[/SIZE]
[LIST=1]
[*]Download Get64bitFlash-0.2.2.tar.gz script at the end of this post (use "Right Click, Save Link As...)
[*]Right click on the tar.gz and select "Extract Here"
[*]Close all browsers.
[*]Inside the folder that extracts is a "Get64bitFlash" file, double click on it.
[*]Select "Run in Terminal"
[*]When the terminal closes, restart your browser.
[*]Test by going to [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/).  Version 10.0.42.34 should show up in "Version" box.
[/LIST]


[SIZE=3]
Troubleshooting[/SIZE]
[LIST]
[*] **Uninstall instructions**
```

sudo rm /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm /usr/lib/mozilla/plugins/libflashplayer.so 
```If you get errors during uninstall, you probably didn't install it correctly.
If you still have flash plugin in Firefox after uninstall, post the information related to the flash plugin provided by shown in about:plugins.
[*]If you are experiencing stability issues or problems with full screen, temporarily disable desktop effects.  Best strategy is to run command:
```

metacity --replace &

```If flash suddenly starts working, consider turning off desktop effects permanently, or consult **Compiz** forums.  The bug is not in flash.
[*]If you are having problems with stability, go to System / Administration / Software Sources, click on Updates tab and select Backports and Proposed.  Update and upgrade.
[*]Some users report Hulu crashing.  The other flash sites work fine.  Given the alpha and closed source nature of the plugin, it may be a problem related to Hulu specifically.  Or it may be due to desktop effects.
[*]If you have issues with full screen mode popping back to actual size (like on Hulu), check your screensaver and power management settings (uncheck "Activate screensaver when computer is idle" and put sliders to the right).
[*](Jaunty) If Flash works in Firefox 3.0.X but doesn't work in Firefox 3.5.X that you downloaded from Mozilla site or using Ubuntuzilla, then you are running 64-bit Firefox 3.0.X and 32-bit Firefox 3.5.X.  This plugin is 64-bit and will not work in a 32-bit browser.  Remove 32-bit browser and install supported 64-bit browser by following instructions at [FirefoxNewVersion from ubuntu community wiki]("https://help.ubuntu.com/community/FirefoxNewVersion").
[*]If you have an Intel video card, you may experience a bug in Intrepid and Jaunty.  
  Source: [thread="1130582"]Performance optimizations[/thread], based on [bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/314928").
[*]If firefox crashes with "Illegal instruction", possibly on all sites except youtube:
```

$ firefox
Illegal instruction

```then read the [thread="1263905"]following thread[/thread] about CPUs lacking lahf_lm instruction.  Users report this problem with old Xeons and old Athlon64 chips.
[/LIST]

[SIZE=3]
Changlog[/SIZE]
Version 0.2.2
Updated version to 10.0.42.34 alpha prerelease of Adobe Flash
Version 0.2.1
Adds a symlink to /usr/lib/firefox-addons/plugins
Version 0.2
Updates for the version 10.0.32.18 of Adobe Flash

Thanks! I have been on Google for an hour looking for an answer, then I found this. It is the correct answer! Thanks again, michael37!! You rock!

---

### Post by arekjan on 2010-01-20
I too am receiving the generic message on Hulu "Sorry we were unable to stream this video, please check your internet connection." when using the 64 bit flash plugin. I was able to find this may be caused by the fact that the 64bit Linux plugin may not be yet fully compatible with their streaming server as mentioned here under "Known Issues":

[http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html](http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html)

---

### Post by iwgunter on 2010-01-20
Yay, finally got Flash working. Ta :)

---

### Post by cosmicbuff on 2010-01-22
thankyou saved so much time,

btw,will it update when the new verions are released,or i will have to do it the same way for every version.

---

### Post by hazypictures on 2010-01-22
Amazing. This solved all my browser issues! As a n00b, never thought about the 64 bit thing. Thank you.

---

### Post by michael37 on 2010-01-22
> **cosmicbuff said:**
> thankyou saved so much time,

btw,will it update when the new verions are released,or i will have to do it the same way for every version.

Yes, until Adobe fully releases the software and it will be rolled into Ubuntu regular upgrade procedure.  Ubuntu intentionally will not provide unreleased third-party product, even though I think it works better than alternatives.

---

### Post by Deeday on 2010-01-23
**Many THANKS** _brainspank_ (and _michael37_). The clean-up script flash_remove.sh seems to have done the trick, since the following attempt to install Flash with Get64bitFlash this time was successful (i.e. Flash videos now always respond to clicks)   =D>

---

### Post by momist on 2010-01-24
> **Deeday said:**
> **Many THANKS** _brainspank_ (and _michael37_). The clean-up script flash_remove.sh seems to have done the trick, since the following attempt to install Flash with Get64bitFlash this time was successful (i.e. Flash videos now always respond to clicks)   =D>

Seconded by me.  I upgraded my pc recently to 64 bit and was a bit flummoxed by this breaking Flash, and the apparent fix not permanently fixing it.  Thanks ):P _brainspank_ for the flash_remove script - that's fixed it!

):P

---

### Post by Mander on 2010-01-25
I can't get this working for some reason.  I've tried the flash_remover script as well as uninstalling all the other flash stuff, and when I try the Get64bitFlash script I get the following error message, and then the terminal window hangs:

Get64bitFlash: 8: function: not found

about: gives me the following:

Build identifier: Mozilla/5.0 (X11; U; Linux x86_64; en-GB; rv:1.9.0.17) Gecko/2010010604 Ubuntu/9.04 (jaunty) Firefox/3.0.17

Do I need to force Jaunty to switch to 3.5 or something?  I don't even really know how to do that, but perhaps that is somehow related?

ETA:  I also tried HappyFeet's suggestion of just downloading and installing, but now flash doesn't have any sound.  Sigh.

---

### Post by GraceDivine on 2010-01-25
Thanks for the tutorial!
I dislike using proprietary, closed-source programs, but sometimes I just have to.

---

### Post by arnab_das on 2010-01-28
thanks for this article. i have installed flash now. but previously i had previously installed flash as directed here: [http://kb2.adobe.com/cps/408/kb408084.html](http://kb2.adobe.com/cps/408/kb408084.html)

all i did then followed ur instructions and installed flash. but i dont know if i'm currently using the 64 bit version. any way of verifying that?

---

### Post by michael37 on 2010-01-28
> **arnab_das said:**
> thanks for this article. i have installed flash now. but previously i had previously installed flash as directed here: [http://kb2.adobe.com/cps/408/kb408084.html](http://kb2.adobe.com/cps/408/kb408084.html)

all i did then followed ur instructions and installed flash. but i dont know if i'm currently using the 64 bit version. any way of verifying that?

Run command
$ locate libflashplayer
you should see

/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so

If there are more of 'em, that's not good.

$ file /usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so: ELF [COLOR="Red"]64-bit[/COLOR] LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped

---

### Post by michael37 on 2010-01-28
Bad news to all: confirmed that Hulu DOES NOT WORK with 10.0.42 version of the player.  [http://www.hulu.com/discussions/9/111251/501809](http://www.hulu.com/discussions/9/111251/501809)

It worked with older version.  How did you folks resolve this problem?

---

### Post by michael37 on 2010-01-28
> **Mander said:**
> I can't get this working for some reason.  I've tried the flash_remover script as well as uninstalling all the other flash stuff, and when I try the Get64bitFlash script I get the following error message, and then the terminal window hangs:

Get64bitFlash: 8: function: not found

about: gives me the following:

Build identifier: Mozilla/5.0 (X11; U; Linux x86_64; en-GB; rv:1.9.0.17) Gecko/2010010604 Ubuntu/9.04 (jaunty) Firefox/3.0.17

Do I need to force Jaunty to switch to 3.5 or something?  I don't even really know how to do that, but perhaps that is somehow related?

ETA:  I also tried HappyFeet's suggestion of just downloading and installing, but now flash doesn't have any sound.  Sigh.


Try running it from a terminal.

$ bash
$ Get64bitFlash

---

### Post by michael37 on 2010-01-28
I tested FF 3.6 and it works.

Rejoice!

See instructions for the  Firefox-stable channel at [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by arnab_das on 2010-01-28
this is the output i get after i enter the command:

> /opt/Adobe AIR/Versions/1.0/Resources/libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/npwrapper.libflashplayer.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so

---

### Post by michael37 on 2010-01-28
> **arnab_das said:**
> this is the output i get after i enter the command:

Run brainspank's complete cleaner (see OP). You have lotsa junk on your system.

---

### Post by arnab_das on 2010-01-28
thanks a ton! i have now followed ur and brainspank's instructions and have installed the 64 bit version. i know that for sure coz i had completely removed flash prior to install, so much so that you tube videos would show 'get the latest flash' messages.

again, thanks a ton.

now my output is something like this: 

> $ locate libflashplayer
/opt/Adobe AIR/Versions/1.0/Resources/libflashplayer.so
/usr/share/ubufox/plugins/npwrapper.libflashplayer.so


(off topic: this thread should be made sticky. since loads of users actually use the 64 bit versions of the OS)

---

### Post by Mayimbero on 2010-01-28
Worked great thanks.

---

### Post by Aurum Beats on 2010-01-29
thnk verymuch!!! it's working;)

---

### Post by DavePlummer on 2010-01-29
As mentioned by michael37, the 64-bit Flash plugin, version 10.0.42.34, does not work for the Hulu site in Firefox. However, it works for me with Hulu Desktop ([http://www.hulu.com/labs/hulu-desktop](http://www.hulu.com/labs/hulu-desktop)).

---

### Post by michael37 on 2010-01-29
> **DavePlummer said:**
> As mentioned by michael37, the 64-bit Flash plugin, version 10.0.42.34, does not work for the Hulu site in Firefox. However, it works for me with Hulu Desktop ([http://www.hulu.com/labs/hulu-desktop](http://www.hulu.com/labs/hulu-desktop)).

Another alternative is to use the older version of flash, 10.0.32.18.  How is hulu desktop working for you?  Which option would you prefer?

---

### Post by DavePlummer on 2010-01-29
Hulu Desktop has been solid for me. I think I prefer to use the latest Flash plugin and Hulu desktop rather than use the older version of Flash.

---

### Post by lordazuzu on 2010-01-31
Actually working on Ubuntu 9.10 x86_64 on my Dell laptop.
Installing the 64bit alpha plugin solved a segmentation fault I had trying to switch to fullscreen in any flash-carried streaming site.
Gratz :)

---

### Post by lotharjade on 2010-02-11
It seems that 10.0.45.2 is out now.  Time for an update? :biggrin:

---

### Post by 65 mustang on 2010-02-11
> **lotharjade said:**
> It seems that 10.0.45.2 is out now.  Time for an update? :biggrin:

Ya, i had a bunch of white squares on about every website but youtube.  I hand edited the shell script to have th 45.2 in it and reinstalled and now everything works again.

Note to maintainer.  Make the filename a variable so you dont have to update the version on 2 lines.

---

### Post by foresthill on 2010-02-11
I installed the 10.0.45.2 version that came out today. I can watch embedded YouTube videos OK, but if I try to watch them on the YouTube site, it crashes Firefox.

I'm running 9.10 64 bit on a Pentium M processor. IIRC, this version causes no problems on my Core 2 Duo machine. So it's pretty hit and miss with 64 bit. I'm seriously considering going back to 32 bit after all these problems with getting Flash to work.

---

### Post by michael37 on 2010-02-11
Script updated.  @mustang, thank you for suggestion.

My Pentium M doesn't support 64-bit, so I can't test.  

New Flash version works pretty much the same as previous version on my Core 2 Duo:  Youtube (had site problems earlier in the day, works just fine now), several Flash games, several Flash-heavy web site.  Hulu still doesn't work, but Hulu Desktop does.

I will also test on Atom 330.

---

### Post by Digikid on 2010-02-13
Fresh install.....did this tut to a T and still not working.

Please advise.

---

### Post by lekksi on 2010-02-15
This worked for me, thanks!
Karmic 64 bit.

---

### Post by Detonate on 2010-02-15
Works great!! Solved some problems I was having.  Youtube plays fine.

---

### Post by Mrmental on 2010-02-16
Worked for me! (Ubuntu 9.10, AMD 64, Phenom X3, Namoroka).
Thank OP!

---

### Post by lotharjade on 2010-02-16
I installed 10.0.45.2 and it seems to work.  As always though it stutters a bit.  Any idea if that is a Flash or connection issue?  (700 Kbps connection)

---

### Post by HappyFeet on 2010-02-16
> **lotharjade said:**
> I installed 10.0.45.2 and it seems to work.  As always though it stutters a bit.  Any idea if that is a Flash or connection issue?  (700 Kbps connection)

If you are using an older video card, that will happen.

---

### Post by lotharjade on 2010-02-17
> **HappyFeet said:**
> If you are using an older video card, that will happen.

I believe I have an Nvidia 8200 on board video card.  I know that isn't a top end card, but I thought it would be new enough to work pretty well.

Oddly enough Hulu Desktop works stutter free, but it has issues in the various browsers I use.

---

### Post by orawax on 2010-02-19
Flash broke with the latest Firefox update ( 3.5.8 ), and I can't get it to work anymore. Tried uninstalling and removing everything flash plugin related before reinstalling, but still no luck...

---

### Post by michael37 on 2010-02-19
> **orawax said:**
> Flash broke with the latest Firefox update ( 3.5.8 ), and I can't get it to work anymore. Tried uninstalling and removing everything flash plugin related before reinstalling, but still no luck...

I switched to FF 3.6 and I am not testing my script on FF 3.0 or 3.5 anyway.  If Mozilla doesn't recommend older versions, why should I?

Any objections -- please voice them here.

---

### Post by wgold on 2010-02-20
Newbie here.  AMD 64bit user that just upgraded to Firefox 3.6, and lost the ability to play video in Firefox.  In addition, now I no longer see a link to Plugins under Help...

I've tried following the instructions provided here, but to no avail.

---

### Post by michael37 on 2010-02-20
> **wgold said:**
> Newbie here.  AMD 64bit user that just upgraded to Firefox 3.6, and lost the ability to play video in Firefox.  In addition, now I no longer see a link to Plugins under Help...

I've tried following the instructions provided here, but to no avail.

Read the "which browser is supported" section.

---

### Post by wgold on 2010-02-20
I have the correct, supported browser.

---

### Post by michael37 on 2010-02-20
Please post info in Help/About, then run through "complete uninstall" in the Troubleshooting section and execute the script again.

---

### Post by Ceiber Boy on 2010-02-21
Thank you..

---

### Post by HotShotDJ on 2010-02-22
Excellent!  The new version supports my web cam.  I tested at [Paltalk Express]("http://express.paltalk.com/") and it works perfectly.

---

### Post by Bob535 on 2010-02-23
I was having crashing issues with 3.5.8 and the second latest version of flash. So I came and upgraded to 3.6 with 10.45.2. The adobe site shows my version fine, but certain sites still crash firefox. 

There is no error in the terminal when it crashes, and I have confirmed it's not the missing instruction bug for my CPU.

Armorgames flash files load fine, 
Youtube main page crashes me. CollegeHumor also crashes me. 

Any ideas?

---

### Post by sunbird on 2010-02-24
Everything works for me, **except** I can't click on embedded videos, but have to open them in a separate window, as reported [here]("http://ubuntuforums.org/showthread.php?t=1345228").

Not a huge deal, but any idea how to fix?

---

### Post by abahsain on 2010-02-24
Thanks for the info I had a problems with the flash since I installed the ubuntu but with this I have at all sorted out I advice everyone who has lots problem to completely remove FF and then install it again and then install the plugin

THANKS:popcorn:

---

### Post by michael37 on 2010-02-25
> **Bob535 said:**
> I was having crashing issues with 3.5.8 and the second latest version of flash. So I came and upgraded to 3.6 with 10.45.2. The adobe site shows my version fine, but certain sites still crash firefox. 

There is no error in the terminal when it crashes, and I have confirmed it's not the missing instruction bug for my CPU.

Armorgames flash files load fine, 
Youtube main page crashes me. CollegeHumor also crashes me. 

Any ideas?

Read @abahsain post above.  Also, try disabling all your extensions.

---

### Post by Enav on 2010-02-25
Thanks... works like a charm
BTW  i want learn to programm scrips like that   any suggestion???

---

### Post by sandyd on 2010-02-25
ive created a gui program to install/remove flash 32 bit & 64 bit. see sig.

---

### Post by michael37 on 2010-02-26
> **Enav said:**
> Thanks... works like a charm
BTW  i want learn to programm scrips like that   any suggestion???

[Advanced Bash Scripting guide]("http://tldp.org/LDP/abs/html/")

---

### Post by mcarrera on 2010-02-26
Thanks, it works like a charm, or it sounds good like a violin - it's a say we have here.

---

### Post by adentrh on 2010-02-26
Worked for me. Used brainspanks' script, then michael37s' get flash script. Now Flash works.  Thanks Michael37 for making this your mission and producing amazing results!

---

### Post by Madmoose on 2010-02-27
Hey,

This lessened the annoying flicker I was getting with the flash from the Ubuntu Software Center. Thanks for this.

---

### Post by bashphoenux on 2010-02-28
Thanks ! :)

---

### Post by Bob535 on 2010-03-01
This is an addon to my previous post on page 13. 

Okay, so I tried using the remove GUI, reinstall, still crashes.
Tried the complete removal script (front post) reinstall, still crashes.

It's still intermittent. Sometimes sites will work, and sometimes they will crash the browser. Restart needed in between, but does not consistently fix the problem. Sometimes it takes 2-3.

Any other ideas?

---

### Post by AldenIsZen on 2010-03-02
> **mikeize said:**
> Thank you so much for this thread (and the flash/cruft remove script above).  Flash has been such a hassle, with some sites working, and others not.  Haven't tested all my favorite sites yet, but youtube and archive.org are working again!

 Seconded, thanks man! Also used the flash/cruft remover.

---

### Post by green.jon on 2010-03-06
Worked great for me. Thank you, michael37! :D

---

### Post by oaksterdam on 2010-03-08
Well, this went pretty well, I guess, but I've lost audio.

Ubuntu 8.04 64-bit server edition; Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2) Gecko/20100301 Ubuntu/8.04 (hardy) Firefox/3.6 

Did the full firefox uninstall and then used the flash_remove script, then the firefox install (via synaptic) and michael37's instructions.

Flash was working for me in Firefox 3.0, but I wasn't able to use MLB Audio's streams (not the TV, the radio broadcasts).  The flash player seems to work, but no audio.  Also, hangs after a minute.

Have tested the audio with youtube, armorgames & nothing.  Any suggestions?

---

### Post by AldenIsZen on 2010-03-08
Yes, try restarting Firefox, and if that doesn't work, Ubuntu. I didn't have audio this morning, but that cleared it up. Of course I hibernate a lot and that could of been where that stemmed from.

---

### Post by oaksterdam on 2010-03-08
@AldenIsZen
Thanks for the suggestion; will try restarting Ubuntu, as restarting firefox didn't work.  I'm wondering of the server edition makes a difference.

Also wondering if upgrading to 8.10 or 9.04 would make a difference.  FWIW, I'm on the server edition for the RAID support.

Crud.  Reboot didn't help either.  I'll keep searching for an answer.

---

### Post by AldenIsZen on 2010-03-08
It could very well be the version of Ubuntu you are using. I am no expert, but I do know PulseAudio was implemented a few "upgrades" ago. It was rocky at first, but seems to work much better, especially in Karmic. I am not sure if it is the default, but I think it was included as an option with 8.04. It could be that the older system doesn't have the same support with newer Flash packages. But again this is conjecture since I am simply a less than power user who just reads a lot. 

  But if you have sound everywhere else... and you have followed this guide... 

 One more thing, have you tried looking for info. in [this]("http://ubuntuforums.org/showthread.php?t=766683") thread? It has older versions of Ubuntu listed. You may want to look for the trouble shoting section, after reading the normal applicable section, of course. Completely getting rid of all traces of Flash (which may not work with the script and your version of Ubuntu and could be complicating your issue) before re-installation may be key to success.

---

### Post by michael37 on 2010-03-08
> **oaksterdam said:**
> @AldenIsZen
Thanks for the suggestion; will try restarting Ubuntu, as restarting firefox didn't work.  I'm wondering of the server edition makes a difference.

Also wondering if upgrading to 8.10 or 9.04 would make a difference.  FWIW, I'm on the server edition for the RAID support.

Crud.  Reboot didn't help either.  I'll keep searching for an answer.

My guess that an update to 9.10 would make the most difference as audio was badly broken and then only partially fixed in Hardy.  (google for hardy alsa pulse and you'll see for yourself).

I have never tested under Hardy server, so I have no idea.  I still think that you may be able to get it working since I suspect this may be just a missing library.

Could you please run command:
ldd /usr/lib/firefox/plugins/libflashplayer.so

---

### Post by oaksterdam on 2010-03-09
@michael37:
$ ldd /usr/lib/firefox/plugins/libflashplayer.soldd: /usr/lib/firefox/plugins/libflashplayer.so: No such file or directory

$ locate libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
/usr/lib/xulrunner-addons/plugins/libflashplayer.so

$ ldd /usr/lib/mozilla/plugins/libflashplayer.so 
	linux-vdso.so.1 =>  (0x00007ffff08dd000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00007f88ed17c000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00007f88ecf60000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x00007f88ecc5c000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0x00007f88eca4b000)
	libXt.so.6 => /usr/lib/libXt.so.6 (0x00007f88ec7e7000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x00007f88ec569000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x00007f88ec338000)
	libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0x00007f88ebd69000)
	libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0x00007f88ebace000)
	libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0x00007f88eb8ae000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0x00007f88eb694000)
	libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0x00007f88eb488000)
	libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0x00007f88eb244000)
	libcairo.so.2 => /usr/lib/libcairo.so.2 (0x00007f88eafd9000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0x00007f88ead93000)
	libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0x00007f88eab90000)
	libdl.so.2 => /lib/libdl.so.2 (0x00007f88ea98c000)
	libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0x00007f88ea6cb000)
	libnss3.so => /usr/lib/libnss3.so (0x00007f88ea399000)
	libsmime3.so => /usr/lib/libsmime3.so (0x00007f88ea16e000)
	libssl3.so => /usr/lib/libssl3.so (0x00007f88e9f3b000)
	libplds4.so => /usr/lib/libplds4.so (0x00007f88e9d38000)
	libplc4.so => /usr/lib/libplc4.so (0x00007f88e9b34000)
	libnspr4.so => /usr/lib/libnspr4.so (0x00007f88e98f7000)
	libm.so.6 => /lib/libm.so.6 (0x00007f88e9676000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00007f88e9468000)
	libc.so.6 => /lib/libc.so.6 (0x00007f88e9105000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f88f20a8000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0x00007f88e8f04000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00007f88e8ce9000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x00007f88e8ae6000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0x00007f88e88de000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0x00007f88e86c3000)
	libz.so.1 => /usr/lib/libz.so.1 (0x00007f88e84ab000)
	libexpat.so.1 => /usr/lib/libexpat.so.1 (0x00007f88e8287000)
	libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0x00007f88e8085000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0x00007f88e7e82000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x00007f88e7c7d000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0x00007f88e7a74000)
	libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0x00007f88e7871000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0x00007f88e7668000)
	libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0x00007f88e7461000)
	libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0x00007f88e7256000)
	libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0x00007f88e702a000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0x00007f88e6e04000)
	libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0x00007f88e6bd6000)
	libpcre.so.3 => /usr/lib/libpcre.so.3 (0x00007f88e69b0000)
	libnssutil3.so.1d => /usr/lib/libnssutil3.so.1d (0x00007f88e6791000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00007f88e658c000)

---

### Post by oaksterdam on 2010-03-09
Eureka!

@AldenIsZen
The link to the Multimedia howto did it!  I started working through the instructions and the first step was to enable the Medibuntu repository.  After doing so, a bunch of packages were updated/installed and after a restart voila I had working flash and working sound with flash.  I didn't go any further in the instructions as that did it.

Many thanks to you and Michael37 for your assistance.

---

### Post by uid313 on 2010-03-11
I get bad performance when in fullscreen mode. It is slow.

Add this code, to ensure the script only runs on 64-bit systems
```

#!/bin/bash

if [ `arch` != "x86_64" ]
then
 echo "Your system is not 64-bit. Only run this script on 64-bit."
fi

```

---

### Post by michael37 on 2010-03-11
> **uid313 said:**
> I get bad performance when in fullscreen mode. It is slow.


If you are referring to playback of high def videos in full screen, that's a common problem.  A few things helps:
1. Switching to metacity from compiz windows manager (aka disabling "effects").
2. Raising speed of your CPU via Gnome CPU applet (by default, CPU speed changes, and running flash occasionally "forgets" to raise CPU speed).
3. Reducing resolution.

Google for hardware-accelerated Flash 10.1, and also why Adobe is not planning to support hardware-accelerated Linux Flash.  Complains and bug reports to Adobe please...

---

### Post by jimbop99 on 2010-03-12
Thanks michael37. I am new to world of linux and have been messing around with Ubuntu 9.10 64bit. Your instruction worked great!

---

### Post by gundogar on 2010-03-12
you are a star. Works like charm 
:popcorn:

---

### Post by Bob535 on 2010-03-12
Okay, so here is the cause of my flash crashing issues.

Segmentation fault in Firefox (flash 10) while AIR 1.5 is running 

You can find a post with that title in the old 86_64 forums, if you are running an AIR 1.5 App (Such as tweetdeck) it will cause firefox to crash when you try to play a flash file.

Took me weeks to figure this out. Hope it helps someone.

---

### Post by michael37 on 2010-03-13
> **Bob535 said:**
> Okay, so here is the cause of my flash crashing issues.

Segmentation fault in Firefox (flash 10) while AIR 1.5 is running 

You can find a post with that title in the old 86_64 forums, if you are running an AIR 1.5 App (Such as tweetdeck) it will cause firefox to crash when you try to play a flash file.

Took me weeks to figure this out. Hope it helps someone.

This is awesome, thank you.  Do you have a link for that post please?  I will add that to the FAQ.

---

### Post by Bob535 on 2010-03-14
[http://ubuntuforums.org/showthread.php?t=1080781](http://ubuntuforums.org/showthread.php?t=1080781)

---

### Post by xumuk37 on 2010-03-21
or just do it (c) in Synaptic...   it's allready possible

type flashp in find field and mark :
flashplugin-nonfree & flashplugin-installer

The easiest way ;)

---

### Post by ulriksvensson on 2010-03-21
Thanks for this, it worked perfectly for me. Strange though that this bug was only a problem for me the last few days.

---

### Post by michael37 on 2010-03-21
> **xumuk37 said:**
> or just do it (c) in Synaptic...   it's allready possible

type flashp in find field and mark :
flashplugin-nonfree & flashplugin-installer

The easiest way ;)

Horrible advice, please do not do this.

Read the thread why.

---

### Post by rifter on 2010-03-24
> **michael37 said:**
> To moderators: please make this post sticky.  [thread="1259102"]It's predecessor[/thread] was sticky on the x86-64 forum, but that forum is now closed.  Thank you.

***** This is an updated version of the script since the original maintainer has not updated it in a while.  Provides February 2010's version of 64-bit Adobe Flash *****

Designed for **64-bit** Hardy 8.04, Jaunty 9.04, Karmic 9.10 and Lucid 10.04 only.
Do NOT use this script on any 32-bit version of Ubuntu.
Status in Intrepid is unknown: I had so much problems with 64-bit Intrepid that I don't recommend it.
[SIZE="3"]
Which browser is supported?[/SIZE]
The only supported browser is **64-bit Firefox 3.6 provided by Ubuntu team**.  You must obtain it from **firefox-stable PPA**.  Detailed instructions here: [FirefoxNewVersion from ubuntu community wiki]("https://help.ubuntu.com/community/FirefoxNewVersion").
Binary 32-bit version from Mozilla site is **NOT supported** and will not work. Select Help -> About Mozilla Firefox.  Differences are highlighted below.

[INDENT]*[COLOR="Lime"]RIGHT 64-bit browser:[/COLOR]* Mozilla/5.0 (X11; U; **Linux x86_64**; en-US; rv:1.9.2) Gecko/20100123 **Ubuntu**/9.10 (karmic) Firefox/3.6
*[COLOR="Red"]WRONG 32-bit browser:[/COLOR]* Mozilla/5.0 (X11; U; **Linux i686 (x86_64)**; en-US; rv:1.9.1.6) Gecko/20091201 Firefox/3.5.6
[/INDENT]
[SIZE="3"]
Installation[/SIZE]
[LIST=1]
[*]Download Get64bitFlash-0.2.3.tar.gz script at the end of this post (use "Right Click, Save Link As...)
[*]Right click on the tar.gz and select "Extract Here"
[*]Close all browsers.
[*]Inside the folder that extracts is a "Get64bitFlash" file, double click on it.
[*]Select "Run in Terminal"
[*]When the terminal closes, restart your browser.
[*]Test by going to [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/).  Version 10.0.45.2 should show up in "Version" box.
[/LIST]


[SIZE="3"]
Troubleshooting[/SIZE]
[LIST]
[*] **Uninstall instructions**
```

sudo rm /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm /usr/lib/mozilla/plugins/libflashplayer.so 
```
If you get errors during uninstall, you probably didn't install it correctly.
If you still have flash plugin in Firefox after uninstall, post the information related to the flash plugin provided by shown in about:****plugins.


[*]**Complete cleanup instructions.**  
brainspank contributed a script in comment 72, [direct link]("http://ubuntuforums.org/showpost.php?p=8666948&postcount=72"), which wipes all versions of Flash from your computer.  Try running this script and then re-running Get64bitFlash.


[*]**Compiz/Desktop Effects**
If you are experiencing stability issues or problems with full screen, temporarily disable desktop effects.  Best strategy is to run command:
```

metacity --replace &

```
If flash suddenly starts working, consider turning off desktop effects permanently, or consult **Compiz** forums.  The bug is not in flash.


[*]**Instability and Crashing** due to Adobe Air.
By themselves, AIR and the Flash plugin in Firefox both work great. Though sometimes when I navigate to a page in Firefox with Flash on it while AIR is running, Firefox exits due to a segmentation fault.  Examples of AIR apps are **Pandora** and **tweetdeck**.  This bug is reported only for 64-bit Ubuntu.  [thread="1080781"]More info.[/thread]


[*]**Hulu** unable to play videos.
If you are having problems with Hulu not playing content, it's a **known bug** with the current release of Adobe Flashplayer.  Given the alpha and closed source nature of the plugin, the bug is not known, but it seems to be related to Hulu specifically.  A recommended workaround is "Hulu Desktop".  [http://www.hulu.com/discussions/9/111251/501809](http://www.hulu.com/discussions/9/111251/501809)


[*]If you are having problems with stability, go to System / Administration / Software Sources, click on Updates tab and select Backports and Proposed.  Update and upgrade.


[*]**Screensaver**
If you have issues with full screen mode popping back to actual size (like on Hulu), check your screensaver and power management settings (uncheck "Activate screensaver when computer is idle" and put sliders to the right). 

[*]**Firefox 3.5 on Jaunty**
If Flash works in Firefox 3.0.X but doesn't work in Firefox 3.5.X that you downloaded from Mozilla site or using Ubuntuzilla, then you are running 64-bit Firefox 3.0.X and 32-bit Firefox 3.5.X.  This plugin is 64-bit and will not work in a 32-bit browser.  Remove 32-bit browser and install supported 64-bit browser by following instructions at [FirefoxNewVersion from ubuntu community wiki]("https://help.ubuntu.com/community/FirefoxNewVersion").


[*]**Intel graphics driver bug**
If you have an Intel video card, you may experience a bug in Intrepid and Jaunty.  
  Source: [thread="1130582"]Performance optimizations[/thread], based on [bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/314928").



[*]**Flash crashes on older 64-bit CPUs**
If firefox crashes with "Illegal instruction", possibly on all sites except youtube:
```

$ firefox
Illegal instruction

```
then read the [thread="1263905"]following thread[/thread] about CPUs lacking lahf_lm instruction.  Users report this problem with old Xeons and old Athlon64 chips.

[/LIST]

[SIZE="3"]
Changlog[/SIZE]
Version 0.2.3
Updated version to 10.0.45.2
Added cleanup for ~/.mozilla/plugins
Version 0.2.2
Updated version to 10.0.42.34 alpha prerelease of Adobe Flash
Version 0.2.1
Adds a symlink to /usr/lib/firefox-addons/plugins
Version 0.2
Updates for the version 10.0.32.18 of Adobe Flash

This is awesome.  I'm not sure how my flash got broken (it was working, then I followed some multimedia howtos and the buttons in youtube stopped working), but installing the 64 bit flash using your script worked perfectly.

Incidentally, regarding the Hulu bugs; there is a good howto _[color=blue][thread=1286425]here[/thread][/color]_ that explains how to install hulu-desktop.

---

### Post by michael37 on 2010-04-13
> **rifter said:**
> Incidentally, regarding the Hulu bugs; there is a good howto _[color=blue][thread=1286425]here[/thread][/color]_ that explains how to install hulu-desktop.

Thanks, added the link to the OP.

---

### Post by meskes on 2010-04-13
From what I was able to glean from an strace, this issue seems to be a result of a parsing conflict with Javascript, which would explain why it does not work with gmail, the pandora site it's self or any other site which runs java script. I confirmed this by **disabling javascript** in Firefox then going to sites without it active. Both worked fine. I was gonna check out adobe's site to see if this had already been made mention of however, you need a login to merely view their buglist and quite honestly I don't have the time to be bothered.


Matt

---

### Post by kamatschka on 2010-04-15
Thank you very much for this tutorial. I was p**ed of because some flash Vids didnt work ... 

This tutorial helped me to get a 64bit Firefox with full Flash support running.

I have no problems anymore. 

Greetings from germany...

---

### Post by FredDie3785 on 2010-04-20
OK now flash videos play flawlessly but there's a few other bugs that came out.
For example, Quick Reply wont work on this and other forums.
Another bug is with some Facebook apps that are based on flash. There's a great game called Bejeweled Blitz (one of the best imho). Simply my scores aren't saved. It's always "Submiting Scores" but they are not saved.
Before using the script it worked without a problem.

---

### Post by michael37 on 2010-04-22
> **FredDie3785 said:**
> OK now flash videos play flawlessly but there's a few other bugs that came out.
For example, Quick Reply wont work on this and other forums.
Another bug is with some Facebook apps that are based on flash. There's a great game called Bejeweled Blitz (one of the best imho). Simply my scores aren't saved. It's always "Submiting Scores" but they are not saved.
Before using the script it worked without a problem.

Submit a bug to develop of a given game.  I found some facebook games that don't work at all when using 64-bit flash.  (some other games work just fine).

---

### Post by bkadoctaj on 2010-04-23
Thanks for a great thread.  I've used it a number of times already.  :)

---

### Post by kjano on 2010-04-24
[sorry for cross-posting]

I installed Get64bitFlash but this does not seem to work for my 10.04RC problem :(. 

see [http://ubuntuforums.org/showpost.php?p=9165950&postcount=7](http://ubuntuforums.org/showpost.php?p=9165950&postcount=7)

---

### Post by linh.plt on 2010-04-27
This works wonderfully with my HP dv4, running Lucidx64, and FF 3.6
Before, I had to choose either to watch Tudou/youtube or Megavideo. If I can watch Megavideo (using gnash), then my tudou wont load. If  I watch Tudou (uninstall gnash), then Megavideo wont work. :confused:
So anyway, I followed the instruction on page 1 and restart my laptop, now I can watch all of those site without any problems.:popcorn:
Thank you so much!

---

### Post by gozo311 on 2010-04-30
Quick and easy, man.  MUCH MUCH MUCH appreciated.

---

### Post by Lightstar on 2010-04-30
Awesome!  Thank you very much!

I had flash only half-working on 10.04 64bit.
Videos would load, but I couldn't click anything in the flash, couldn't adjust volumes etc etc

This fixed it all, yay! you are my hero

---

### Post by spartan_87 on 2010-04-30
I just did a fresh install of Ubuntu 10.04 64-bit. Flash is working, I can see video on youtube and everything, but I have no sound. 

The sound on my system works fine, but I have no sound in flash on Firefox. 

I have been trying to get this working all day, I have purged all other versions of flash, and ran the script you provided and still does the same thing, no sound.

Any ideas?

---

### Post by BF79 on 2010-04-30
works grat and thanks for the help   making my transition  sweet

---

### Post by chowder on 2010-04-30
Easy, perfect in 10.04 64-bit.
Thanks!!

---

### Post by _0R10N on 2010-04-30
It works perfectly on Lucid!!! Awesome contribution!!!:popcorn:

---

### Post by 74.niro on 2010-05-01
thank you very much. I had a very tough time playing flash files till I read this post. The downloaded script worked like a charm. I'm using Ubuntu 10.04 -64 bit version.

---

### Post by michael37 on 2010-05-01
> **spartan_87 said:**
> I just did a fresh install of Ubuntu 10.04 64-bit. Flash is working, I can see video on youtube and everything, but I have no sound. 

The sound on my system works fine, but I have no sound in flash on Firefox. 

I have been trying to get this working all day, I have purged all other versions of flash, and ran the script you provided and still does the same thing, no sound.

Any ideas?

As you can see, most of people are running fine on Lucid.

I haven't upgraded to Lucid yet so I don't really know.  Anyone else who runs Lucid -- any ideas?

---

### Post by Yellow Pasque on 2010-05-01
> **michael37 said:**
> As you can see, most of people are running fine on Lucid.

I haven't upgraded to Lucid yet so I don't really know.  Anyone else who runs Lucid -- any ideas?
Configure ALSA apps (like Flash) to use Pulseaudio so they mix properly with other apps: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

---

### Post by spartan_87 on 2010-05-01
I finally got the sound to work in flash. 

I am using a soundblaster audigy card and I switched the sound settings to my onboard sound, then back to my audigy sound card and all of a sudden I have sound in flash now. Guess the sound settings just needed to be refreshed.

Thanks!

---

### Post by heatpumpcontrol on 2010-05-01
> **brainspank said:**
> In case anybody else wanted it/finds it useful.  I fought with flash for quite a while (the guide didn't work because I had some old cruft lying around).  This is just a script I built up over time to make sure that I cleaned everything out when I retried it.  Some of it I copied, some I added for my situation.

If you want to use it, I suggest running it before the Get64bitFlash script as:
```
$ sudo ./flash_remove.sh
```

flash_remove.sh
```

#!/bin/bash
apt-get remove --purge flashplugin-installer
apt-get remove --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash 
apt-get remove --purge iceweasel-flashplugin mozilla-flashplugin firefox-flashplugin 
apt-get remove --purge swfdec-mozilla libflashsupport nspluginwrapper iceape-flashplugin 
apt-get remove --purge xulrunner-flashplugin midbrowser-flashplugin xulrunner-addons-flashplugin
rm -f ~/.mozilla/plugins/*flash*
rm -f /usr/lib/firefox-addons/plugins/*flash*
rm -f /usr/lib/firefox/plugins/*flash*
rm -f /usr/lib/iceape/plugins/flashplugin-alternative.so
rm -f /usr/lib/iceweasel/plugins/flashplugin-alternative.so
rm -f /usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
rm -f /usr/lib/midbrowser/plugins/flashplugin-alternative.so
rm -f /usr/lib/mozilla/plugins/*flash*
rm -f /usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so
rm -f /usr/lib/xulrunner/plugins/flashplugin-alternative.so
rm -f /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so

```

First make the install script executable and then run it. (replace /path/to/file.sh with the path to the shell script.)
Code:

sudo chmod +x /path/to/file.sh
sudo /path/to/file.sh

---

### Post by DiabolusItalicus on 2010-05-02
Michael37,
just one word: T-H-A-N-K-S-!-!-! :D

On my just-installed Lucid Linx your script worked flawlessly and Flash runs perfectly.

> **michael37 said:**
> To moderators: please make this post sticky.  [thread="1259102"]It's predecessor[/thread] was sticky on the x86-64 forum, but that forum is now closed.  Thank you. [...] 

To moderators: P-L-E-A-S-E, make this post sticky **A-B-S-O-L-U-T-E-L-Y-!**

Regards from Italy.

---

### Post by D3mon_Spawn on 2010-05-03
works great in 10.04!! :D

---

### Post by Jwilliamhunt on 2010-05-03
Remind me again why something like flash is never compatible with x64 bit systems? When are we (open source) going to replace Flash with something more flexible and light weight and x64 bit compatible?! Or is that never going to happen? I think I hate Adobe. I love Ubuntu but I'm tired of this "make things work" after I install a new version. I think I'm going to give up on it. I'm beat..Red Hat 6.0 was my first, I think Ubuntu 10.04 will be my last. 

[IMG]http://lh5.ggpht.com/_gAimwjDi7hg/S99reJPtCoI/AAAAAAAAAcA/-CArw-x11Ag/s800/Screenshot-1.png[/IMG]

---

### Post by michael37 on 2010-05-05
> **Jwilliamhunt said:**
> Remind me again why something like flash is never compatible with x64 bit systems? When are we (open source) going to replace Flash with something more flexible and light weight and x64 bit compatible?! Or is that never going to happen? I think I hate Adobe. I love Ubuntu but I'm tired of this "make things work" after I install a new version. I think I'm going to give up on it. I'm beat..Red Hat 6.0 was my first, I think Ubuntu 10.04 will be my last. 


Hulu?  Try re-reading the OP, section Troubleshooting and instructions how to get Hulu desktop running. Sorry, this topic has been covered previously.

---

### Post by ourladyoflinux on 2010-05-09
Thanks so much! After an hour of frustration, your fix worked perfectly!

---

### Post by brayden551 on 2010-05-09
Thank you so much :D I thought I was the only one with this problem - Turns out I wasen't! Again thanks, Now i can Pause and play you tube without having to use the TAB key ](*,)

IT works on the new ubuntu too, :D

---

### Post by guikubivan on 2010-05-10
First of all, I have a basic installation of Debian AMD64 Squeeze. I am using the package flashplugin-nonfree, which basically does the same thing as the script in this thread (downloads the prerelease, version 10.0.45.2, and installs it). Youtube and most things are working great (I installed Hulu desktop to be able to use Hulu).

HOWEVER, The only thing that I can't find an easy solution for (other than using Windows) is getting the sound to work for the online sheet music editor, noteflight.com. I can look at scores and edit them, but I can't playback. This is really frustrating!!! Does anybody have hints or suggestions? :confused:

---

### Post by dBuster on 2010-05-10
> **guikubivan said:**
> First of all, I have a basic installation of Debian AMD64 Squeeze. I am using the package flashplugin-nonfree, which basically does the same thing as the script in this thread (downloads the prerelease, version 10.0.45.2, and installs it). Youtube and most things are working great (I installed Hulu desktop to be able to use Hulu).

HOWEVER, The only thing that I can't find an easy solution for (other than using Windows) is getting the sound to work for the online sheet music editor, noteflight.com. I can look at scores and edit them, but I can't playback. This is really frustrating!!! Does anybody have hints or suggestions? :confused:

I do not believe that you using the flashplugin-nonfree is the same thing.  looking at a 32 bit plugin on a 64 bit platform.  Whereas the script here actually installs a 64 bit plugin on a 64 bit platform.  

Might be the sheetmusic software and not wanting to play well with the mix you have.

The script here will remove any instance of 32 bit flash then install the proper 64 bit flash.  Sure each and everyone of us may have a quirk or two but this thread is amazing with all the quirks being brought out and worked on collectively.

As far as everything working, for me everything I do, hulu, to include hulu desktop, and so forth is working!

---

### Post by fri666 on 2010-05-11
great post! thanks a lot! worked perfectly in 10.04! at last everything related to flash is working flawlessly (in my case for the first time, i must say) :)

---

### Post by playcat on 2010-05-12
Ubuntu 10.04 likes this solution ... 

Not sure if I'm doing things right, but simply starting the program provided, typing 'yes' and waiting a little bit did the job for me.

Anyway, thanks for this.
Dan

---

### Post by kilroy0097 on 2010-05-13
michael37 I have to say thank you very much for this walk through. With a little bit of time and effort I was able to not only install Mozilla/Firefox 3.6.3 finally but was also able to reinstall Flash again and also fix my Hulu Desktop which was suddenly not working.

However there was some issue after adding the PPA needed for 8.04 Hardy. The traditional commands were not working at all.

I found this at this source: [http://forums.dropbox.com/topic.php?id=10123](http://forums.dropbox.com/topic.php?id=10123)

This is an excerpt
> 
1. grab the key from the key server as described on the installation page

gpg --keyserver pgp.mit.edu --recv-keys 3565780E

2. export that key to a file

gpg --export -a 3565780E > dropbox.key

3. go to "System" -> "Software Sources" -> "Authentication" and import that key-file.


Once I was able to download the correct signing key then I was able to update software lists and install the new firefox.

Thought I might add this bit of knowledge to this thread in case someone down the line needed it.

Thanks again for your hard work. :)

---

### Post by deanjm1963 on 2010-05-13
I've had no problems with flash since using the PPA for the 64bit version (which is at the same version number as the current 386 release).

Simple ...

```
sudo add-apt-repository ppa:sevenmachines/flash
```

update synaptic and install Flash 64 bit

---

### Post by Lilonius on 2010-05-13
@deanjm1963 - Thanks a lot. SO far so good. need to test it more. If there is some problem i will post it here.

Running: Lucid Lynx 64bit

---

### Post by mushroomwilly on 2010-05-13
Hi folks ,
My Sytem is an Intel Dual Core 2.6Ghz , on board sound card which uses under win7 OS Realtek AC'97 driver ver. 2.41 . 4 Gbyte Ram , 2 Tbyte
harddisk .

I'm a total newcomer , which installed parallel to Win 7 OS the Ubuntu Studio which i really like ! But because I'm jet to stupid , I got about 3 or 4 major problems ! So please help if possible !

1.I want to use AC'97 driver for my sound card , if possible as ALSA  
  driver . How to do it ?
2.If I want to answer or check my email account , which is by Microsoft 
  Live Messenger [email]Reinthal@hotmail.de[/email] , I have to shut down Ubuntu to 
  start win 7 ! Stupid , but i don't know how to access it from Ubuntu 
  Studio .
3.Mozilla Firefox 3.6.3 surfs very slow , approx 1-2 min. for each site .
  Thats why I use Opera 10 , which is really fast , but I can't get the 
  flash player running or better - installed ! 
  So anybody knows how to get Opera 10 working on a 64 bit Intel dual 
  core !?[http://ubuntuforums.org/images/icons/icon9.gifhttp://ubuntuforums.org/images/icons/icon7.gif](http://ubuntuforums.org/images/icons/icon9.gifhttp://ubuntuforums.org/images/icons/icon7.gif)

            Thanks for your afford , keep on rocking [http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

                     mushroomwilly

---

### Post by squiddy on 2010-05-15
so, after i install flash from this installer, if there any version updates, will it be updated automatically from synaptic/update manager? or should i get the latest installer from here and repeat all the steps all over again?

thanks.

---

### Post by michael37 on 2010-05-15
> **squiddy said:**
> so, after i install flash from this installer, if there any version updates, will it be updated automatically from synaptic/update manager? or should i get the latest installer from here and repeat all the steps all over again?

thanks.

The latter.  Process described in this thread is not using the synaptic/update manager.  Why not? 'Cause Ubuntu standard update process does not support alpha/beta-quality closed source software that is Adobe's 64-bit flash.

---

### Post by michael37 on 2010-05-15
> **deanjm1963 said:**
> I've had no problems with flash since using the PPA for the 64bit version (which is at the same version number as the current 386 release).

Simple ...

```
sudo add-apt-repository ppa:sevenmachines/flash
```

update synaptic and install Flash 64 bit

I haven't been contacted by the author so I can't guarantee that the author will keep the PPA updated and this method will continue to work with the future versions.  Thanks for bringing it to the attention.

---

### Post by pirateboy on 2010-05-17
AWESOME! thanks for this post. it worked great for me.

---

### Post by sdibaja on 2010-05-18
I went thru this great tutorial a couple of weeks ago and all was fine! Thanks!

BUT... now when I check the version number all is correct but I no longer can get flash to run.
I went thru the same paces as before, but still no flash.

wazzup? :confused:

---

### Post by 1proton on 2010-05-20
THX
worked great

---

### Post by ActionParsnip on 2010-05-20
[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

States:

sudo add-apt-repository ppa:sevenmachines/flash && sudo apt-get update && sudo apt-get install flashplugin64-installer

Which will give native 64bit flash. WAAAAAY easier than all that faffing around.:KS:KS:KS:KS:KS

---

### Post by sdibaja on 2010-05-20
got it!  and now it works again!!! 
... much thanks for helping the reading challenged.
Peter

---

### Post by kaotik2003 on 2010-05-21
Thanks, you solved my issue with non responsive buttons in Youtube.

---

### Post by stephenlamb on 2010-05-23
Many thanks.  This worked perfectly for me - and it is fully automatic and so very easy!

---

### Post by X-Windows on 2010-05-27
Props! Worked perfectly for me. Very easy to install. :)

---

### Post by Pav3 on 2010-05-30
When a flash video is on fullscreen, the video gets choppy and it eventually freezes.  I'm on AMD64, anyone else having this issue?  I'm using 10.04 and I tried disabling and enabling the visual effects.

---

### Post by michael37 on 2010-05-30
> **Pav3 said:**
> When a flash video is on fullscreen, the video gets choppy and it eventually freezes.  I'm on AMD64, anyone else having this issue?  I'm using 10.04 and I tried disabling and enabling the visual effects.

In general, full screen usually performs worse due to more computational power required and because Linux version still lacks proper hardware acceleration (it does not matter if you select enable/disable in Flash plug-in settings).

In your case, the best course of action is to go to [http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html), click on "Report issues and feature requests" and report an issue to Adobe.  Flash is closed source.  We can't fix the problem.

---

### Post by Pav3 on 2010-05-31
> **michael37 said:**
> In general, full screen usually performs worse due to more computational power required and because Linux version still lacks proper hardware acceleration (it does not matter if you select enable/disable in Flash plug-in settings).

In your case, the best course of action is to go to [http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html), click on "Report issues and feature requests" and report an issue to Adobe.  Flash is closed source.  We can't fix the problem.

My hardware is up to date (AMD64 with the latest fglrx driver) to play full HD but I wasn't sure whether the fullscreen freeze is an issue on my end.

The only set of instructions that I haven't tried was the "$ sudo ./flash_remove.sh" script since I don't know how to execute it yet (I'm new to linux). Perhaps if I do a complete reinstallation with the script, it may solve the issue?

Thanks for the info michael37,
After installing the 64bit flash player, I can use a fully functional youtube player (minus the fullscreen) on firefox and the Hulu desktop player seems to be working fine.  The fullscreen problem as well as slow playback from some players other than youtube is something that I'll report over to adobe.

---

### Post by shepla on 2010-05-31
Thank-you Michael37 for your fixit process - it worked a treat!:P

---

### Post by rude balloon on 2010-06-01
Thanks a bunch. I got the ubuntu 10.04 version but the download that you supplied worked. 
 
I tried many things from other sites and none fixed the problem at all. Lots of codes and downloads that I went through. Man was I getting frustrated but then came across your forum and your document worked.

---

### Post by christophe.vernin on 2010-06-01
I had the same problem (Firefox 3.6.3 and AMD 64 bits with Ubuntu 10.04).
To copy the last version of libflashplayer.so (10.0.45.2) in the directory .mozilla/plugins didn't succeed. But an earlier version (10.0.22) succeeded.

---

### Post by abdusamed on 2010-06-01
will this lower flash resources .. more importantly.. why wasn't this already pre installed in ubuntu 10.04 so that we don't have to do this!

---

### Post by michael37 on 2010-06-01
> **abdusamed said:**
> will this lower flash resources .. more importantly.. why wasn't this already pre installed in ubuntu 10.04 so that we don't have to do this!

This version, a 64-bit native flash, is beta software from Adobe.   Ubuntu has policy against distributing beta closed-source software, that's why you had to install it separately.  Ubuntu does provide flashplugin-installer (DO NOT USE) package which is a VASTLY inferior solution of 32-bit flash hacked into a 64-bit Firefox plug-in.

---

### Post by PanosOzzy on 2010-06-03
tnx man . works great !!!!

---

### Post by XSAlliN on 2010-06-04
Instaled 64 bit version for 64 Lucid - and works but in Full-screen lags horribly if I try to move the volume slider or the progress bar. Even with Compiz effects disable works just the same...

---

### Post by drumenigma on 2010-06-05
> **XSAlliN said:**
> Instaled 64 bit version for 64 Lucid - and works but in Full-screen lags horribly if I try to move the volume slider or the progress bar. Even with Compiz effects disable works just the same...

I just installed it myself and am having the same thing happen. Watching the videos in regular small screen mode seems to work fine but when I enlarged it to full screen it was very choppy.

---

### Post by iShurtugal on 2010-06-05
thank you SOOOO much, I was seriously getting ticked at flash, but this fixed it, and all i had to do way type my password and yes!

---

### Post by michael37 on 2010-06-11
64-bit Adobe Flash plugin is RIP.  See OP.

---

### Post by BiZARRe_T on 2010-06-20
I didn't try this method reviewed gere for installing adobe flash player on 10.04 64bit.

I had the same problem as we all have, supporting 64bit from adobe.

So as i searched allot i found this blog and finaly i was able to see flash not only in youtube but other sites. :p

[http://blog.mattrudge.net/2010/05/03/installing-flash-player-on-ubuntu-10-04-64-bit/]("http://blog.mattrudge.net/2010/05/03/installing-flash-player-on-ubuntu-10-04-64-bit/")

i hope to help somebody.:p

---

### Post by michael37 on 2010-06-20
> **BiZARRe_T said:**
> I didn't try this method reviewed gere for installing adobe flash player on 10.04 64bit.

I had the same problem as we all have, supporting 64bit from adobe.

So as i searched allot i found this blog and finaly i was able to see flash not only in youtube but other sites. :p

[http://blog.mattrudge.net/2010/05/03/installing-flash-player-on-ubuntu-10-04-64-bit/]("http://blog.mattrudge.net/2010/05/03/installing-flash-player-on-ubuntu-10-04-64-bit/")

i hope to help somebody.:p

Not helpful.  Please read the OP -- the script referenced here will not work because Adobe removed 64-bit flash.

---

### Post by -LynX- on 2010-06-20
It looks like Adobe want to stay on x86. Oh well.. :frown:

Never mind, here's how to install Adobe Flash Player on x64 Ubuntu (AMD64) :

1. Download libflashplayer from [*_**here**_*]("http://www.enterupload.com/udviwxng50qk/libflashplayer-10.0.d20.7.linux-x86_64.7z.html") (Enterupload).
2. Open your terminal
3. Type sudo nautilus, then press enter
4. Go to your download directory, Extract ibflashplayer-10.0.d20.7.linux-x86_64.7z
5. Go to libflashplayer-10.0.d20.7.linux-x86_64 directory, and copy libflashplayer.so
6. Go to /usr/lib64/firefox/plugins/
7. Paste
8. Restart Firefox

:lolflag:

---

### Post by Goldenlight on 2010-06-21
link is dead :confused:
Looks like I will be running 2 OS now.. Old 32 bit WindowsXp and New Ubuntu 64 10.04

I refuse to buy another copy of windows to get 64 bit support. I'll stick with Linux...

---

### Post by Yellow Pasque on 2010-06-21
> **Goldenlight said:**
> link is dead :confused:
Looks like I will be running 2 OS now.. Old 32 bit WindowsXp and New Ubuntu 64 10.04

I refuse to buy another copy of windows to get 64 bit support. I'll stick with Linux...
You can also run a 32-bit browser in your existing install, set up a 32-bit schroot, or try virtualbox.

---

### Post by michael37 on 2010-06-21
The correct solution at this time is to run a cleaner script (see [comment 72]("http://ubuntuforums.org/showpost.php?p=8666948&postcount=72") in this thread) and then run command
```
sudo apt-get install flashplugin-installer
```

This sequence installs 32-bit flash and nspluginviewer which allows using 32-bit flash in a 64-bit browser. 

THIS IS THE ONLY SUPPORTED AND FULLY FUNCTIONAL SOLUTION.

Wrong things to do:
[LIST=1]
[*]Continue using 10.0.X.X 64-bit Adobe Flash player due to serious security issues
[*]Downloading third-party 64-bit flash which may be harmful
[*]Installing 32-bit browser (not recommended by Ubuntu Mozilla team)
[*]Hijacking this thread
[/LIST]

Thank you for your attention.

---

### Post by DoritosBR on 2010-06-22
The 32 bit npwrapper plugin on lucid doesn't work on a lot of cases.
One of them is not advancing, retroceding on a youtube video (the videos that shows the old interface)
Or even playing an embeded youtube video.

Right click on almost any flash (including the adobe.com) freezes your browser.

I'll be using the 64 bit one for now.

---

### Post by techunit on 2010-06-22
Hey Guys I Some how got flash working from the plug-in installer in firefox but I have no interation control? Um Opera Works Well And I Think That It has 64bit version with flash!

---

### Post by Detonate on 2010-06-24
Although the 64bit flash is not currently available, I already had it installed before all the hoopla broke out.  I have not yet seen a lot of traffic on the net about the security issues actually being exploited.  I intend to keep running it until I do see such traffic.  Neither the 32bit or gnash alternatives are attractive to me.

---

### Post by Detonate on 2010-06-24
Here is an alternate download site for 64bit flash.  It was still working a few minutes ago.

[http://linux.softpedia.com/get/Internet/HTTP-WWW-/Adobe-Flash-Player-for-64-bit-Linux-42958.shtml](http://linux.softpedia.com/get/Internet/HTTP-WWW-/Adobe-Flash-Player-for-64-bit-Linux-42958.shtml)

---

### Post by michael37 on 2010-06-24
> **Detonate said:**
> Although the 64bit flash is not currently available, I already had it installed before all the hoopla broke out.  I have not yet seen a lot of traffic on the net about the security issues actually being exploited.  I intend to keep running it until I do see such traffic.  Neither the 32bit or gnash alternatives are attractive to me.

The security advisory for 10.0.45.2 looks extremely ugly :frown:   

[http://www.adobe.com/support/security/bulletins/apsb10-14.html](http://www.adobe.com/support/security/bulletins/apsb10-14.html)

Considering that Flash vulnerabilities are the easiest to exploit (e.g. hijacking website that you visit or redirecting you to a cracked website), I would not recommend using version 10.0.45.2.

---

### Post by Yellow Pasque on 2010-06-24
> I would not recommend using version 10.0.45.2.
And if you must use it, use flashblock plugin to block all flash except sites you trust.

---

### Post by lotharjade on 2010-06-25
Have a lot of you switched over to 32 bit now? :confused:

:mad: Am I the only one who feels this whole situation is a 32 bit flash hell?  Life was so good a few days ago.  Hulu worked.  All my browsers worked.  :cry:  Now they will all start sucking.

I am slowly starting to hope that Apple and Google kick Adobe right in the teeth on the flash issue, and win a replacement solution for all us Linux folk.  :twisted:

](*,)

---

### Post by jdunn on 2010-06-25
There are still a few (trustworthy?) sites out there that have the 10.0.45.2 64-bit plugin.  I tried the latest 32-bit flash plugin with unsatisfactory results so I'm sticking with the older 64-bit version for Firefox and Google-Chrome.  At the same time, I'm automatically deleting flash cookies on browser exit and trying to learn how to get app-armor configured.  Once, I get app-armor profiles right, I should have little worries *fingers crossed*

One problem with Chrome is it currently can't do true ad-blocking (only ad-hiding) and it can't do script-blocking with the granularity of NoScript for FF.  Two options for concerned Chrome users are special bash scripts or Privoxy.  I found Privoxy to be overkill for one computer, plus it slowed down web browsing considerably...Maybe it would be faster in tandem with Squid?  Another option is to dump Chrome and use SWare Iron with its built-in ad-blocking but the linux version of Iron is several versions behind Chrome.

---

### Post by lotharjade on 2010-06-26
I wish I was a programmer (specifically a good one), so I could help make the Gnash a reality to replace Adobe Flash.  Or so we could rewrite things like Hulu to run in HTML5 or something like that.

---

### Post by Yellow Pasque on 2010-06-26
> **lotharjade said:**
> I wish I was a programmer (specifically a good one), so I could help make the Gnash a reality to replace Adobe Flash.  Or so we could rewrite things like Hulu to run in HTML5 or something like that.
It doesn't help to be a code wizard when something needs to be done a certain way and you don't have the proper documentation..

---

### Post by Linuxforall on 2010-06-26
Gnash is running quite good with occasional CPU spikes on Youtube here. I installed from the ppa at [www.getgnash.org/packages](www.getgnash.org/packages) Even though some sites don't play, I can live with it.

---

### Post by bcschmerker on 2010-06-27
> **lotharjade said:**
> Have a lot of you switched over to 32 bit now? :confused:

:mad: Am I the only one who feels this whole situation is a 32 bit flash hell?  Life was so good a few days ago.  Hulu worked.  All my browsers worked.  :cry:  Now they will all start sucking....
](*,)I ran head-on into a functionality issue with Adobe® Flash&#8482; 10.1.53.64 (32-bit) in Mozilla® Firefox&#8482; 3.6.3 for AMD64 (64-bit):  Function and procedure buttons in Flash&#8482; IFrames from some Websites do not work as they did under 10.0.45.2.  (This issue does not affect an eMachines®/Acer® EL1210-09 that I have for video streaming, which is all-32 bit under Microsoft® Windows&#8482; 6.0.6002; I have yet to see if functionality is an issue for an all-Intel®-chipped Gateway®/Acer® rig under an i64-based Windows&#8482; 7.0.8001.)

Update:  The functionality issues are apparently confined to the AMD64 Version, as all systems are go for the i386 Version on my all-AMD rig.  Now, if only Adobe Labs would put AMD64 and EM64T support back into Flash Player 10.1.55-up, as SWF-Dec doesn't feed back properly for specific websites....

---

### Post by proteusmoteus on 2010-06-29
If you are satisfied w/ only youtube, vimeo, blip.tv, video.google, megavideo, and various games then you can dump adobe's flash and use the firefox extension [FlashVideoReplacer]("https://addons.mozilla.org/en-US/firefox/addon/161869/"). Made by the same guy that did [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/"), it embeds a native video player (totem/mplayer/vlc) in youtube, vimeo and blip.tv (more expected in the future and swfdec currently handles video.google, megavideo and games). Here is his [ubuntuforums thread]("http://art.ubuntuforums.org/showthread.php?t=1487327") on the extension.

The extension for some reason does require a flash plugin, but gnash or swfdec works as well as adobe's flash for this purpose. I recommend swfdec (swfdec-mozilla in synaptic) as my testing today indicated it still works better than gnash despite being unmaintained. The one game I tested w/ swfdec worked fine  ([desktop  tower defense]("http://www.handdrawngames.com/DesktopTD/Game.asp")).

While installing swfdec-mozilla also install gecko-mediaplayer (plugin for mplayer) and remove the package totem-mozilla. gecko-mediaplayer offers better functionality in the form of: buffer progress info, seeking (jumping to different times in the video), replay, and can be configured to buffer less before starting playback.

swfdec-mozilla configuration: right click on flash object (not on the 3 listed video sites as the flash object is replaced by gecko-mediaplayer) go to "Autoplay" option and select "Never".

gecko-mediaplayer configuration: in Gnome MPlayer (now under Sound & Video in Gnome menu) select Edit > Preferences; or edit preferences via right clicking the embedded object. Lower the time spent buffering before starting playback via first the "Plugin" tab and changing the "Cache Size" to 544.  You have to use the arrows (doesnt allow input from typing) to go down to 32 and then up to 544. Due to a bug the 32 value doesnt work as well as 544, and the numbers reached before going all the way down to 32 are invalid. Of course raise this value if you want video to buffer longer (slow connection), but don't modify cache values on other tabs as those relate to max memory allowed for mplayer (disabled by default) rather than amount of video data to download before playing.

Pretty quick and easy, but dont expect any other video sites to work with swfdec. Of course the whole point of using this extension, rather than letting swfdec, gnash, or even adobe play the videos, is that the CPU utilization is much less.

---

### Post by proteusmoteus on 2010-06-30
[bcschmerker]("http://ubuntuforums.org/member.php?u=609186"), your issue sounds like "[Adobe Flash  Player does not respond to mouse clicks]("https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/410407")". It is an issue with the emulation of flash due to lack of a native 64-bit plugin. There are a couple of work arounds, described at the beginning of the bug report, that sometimes work.

Workaround 3, which solved the problem for me, is to open a terminal and enter:
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
Before the last line of text enter the following:
export GDK_NATIVE_WINDOWS=1

---

### Post by bcschmerker on 2010-07-01
> **proteusmoteus said:**
> [bcschmerker]("http://ubuntuforums.org/member.php?u=609186"), your issue sounds like "[Adobe Flash  Player does not respond to mouse clicks]("https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/410407")"....There are a couple of work arounds, described at the beginning of the bug report, that sometimes work.

Workaround 3, which solved the problem for me, is to open a terminal and enter:
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
Before the last line of text enter the following:
export GDK_NATIVE_WINDOWS=1In fact Flash Player 10.1.53.64 *does* respond to mouse clicks, with exceptions limited to certain Websites.  I already posted to a specific Discussion at the [SingSnap® Message Boards](http://www.singsnap.com/snap/forum/categories) to recommend a bug fix on three affected Procedures that require Adobe Flash.  I *will* see what effect the Gdk_Native_Windows setting has on my system, leaving it at whatever setting gets the most consistent results.  Thanks for the tip.

---

### Post by speedy55555 on 2010-07-22
Is there any version that works with 64-bit Slackware? There's no apt-get on slack, it seems.

---

### Post by mattlach on 2010-07-28
> **michael37 said:**
> 
[URL="http://www.theregister.co.uk/2010/06/11/64_bit_flash_for_linux_dead/"]**[COLOR="Red"][SIZE="7"]Adobe has murdered Flash for 64-bit Linux.[/SIZE][/COLOR]**
At least for the moment.[/URL]


I just manually copied the old 64bit .so library from /usr/lib/mozilla/plugins/libflashplayer.so on one of my boxes that had it installed, and now I manually copy it to my new 64bit installs...

---

### Post by merry_meerkat on 2010-07-29
Hello,
I'm on 64-bit Ubuntu Lucid and I am trying to make sense of this all. From the different posts I understand that there is currently no 64-bit flash for Linux - or at least none that can be recommended.

I understand that the best interim solution for me is to install 32-bit flash.

Here's my question, though:
1 - Can I only install flash 32-bit if my browser (Firefox) is 32-bit?
2 - How do I find out whether my browser is 32- or 64-bit? (> Help > About says: "Mozilla Firefox for Ubuntu canonical - 1.0")
3 - If necessary, how to I install Firefox 32-bit on my Ubuntu 64-bit machine?

Thanks - I'm a bit confused...

---

### Post by Yellow Pasque on 2010-07-29
^^^^ To answer this
1 - No, that's what nspluginwrapper is for. Make sure you've removed any old Flash by running the script in comment#72 in this thread. Then run:
```
sudo apt-get install flashplugin-installer
```
Also, see: [http://ubuntuforums.org/showpost.php?p=9529549&postcount=230](http://ubuntuforums.org/showpost.php?p=9529549&postcount=230)
2 - Make the About window bigger and look for 'i686' in the version string. If you see it, that means it's a 32-bit build.
3 - No, don't (unless you're still having issues after trying the instructions in 1).

---

### Post by michael37 on 2010-07-29
> **mattlach said:**
> I just manually copied the old 64bit .so library from /usr/lib/mozilla/plugins/libflashplayer.so on one of my boxes that had it installed, and now I manually copy it to my new 64bit installs...

You are exposing yourself to very serious published security vulnerability.  By directing you to a specially crafted website, an attacker can take over your computer.  Would you like that?  In case you didn't know, compromized Linux computers are worth nearly 10 times more than compromized Windows computers due to their vastly superior abilities and toolset.

---

### Post by merry_meerkat on 2010-07-30
> **Temüjin said:**
> ^^^^ To answer this
1 - No, that's what nspluginwrapper is for. Make sure you've removed any old Flash by running the script in comment#72 in this thread. Then run:
```
sudo apt-get install flashplugin-installer
```
Also, see: [http://ubuntuforums.org/showpost.php?p=9529549&postcount=230](http://ubuntuforums.org/showpost.php?p=9529549&postcount=230)
2 - Make the About window bigger and look for 'i686' in the version string. If you see it, that means it's a 32-bit build.
3 - No, don't (unless you're still having issues after trying the instructions in 1).

Thanks! Did that and everything's fine here.
Re 2: the did hide that very well...

---

### Post by cprofitt on 2010-08-02
It appears my answer is to not use Flash... or use a different OS if I need flash...

I choose no flash.

---

### Post by mattlach on 2010-08-03
> **michael37 said:**
> You are exposing yourself to very serious published security vulnerability.  By directing you to a specially crafted website, an attacker can take over your computer.  Would you like that?  In case you didn't know, compromized Linux computers are worth nearly 10 times more than compromized Windows computers due to their vastly superior abilities and toolset.

Interesting.

I knew that I would have to be careful about new vulnerabilities in flash, if I was going this route, as there would be no more patches, but I wasn't aware that there were any already.

Thanks for the heads up.

---

### Post by rifter on 2010-08-03
> **michael37 said:**
> You are exposing yourself to very serious published security vulnerability.  By directing you to a specially crafted website, an attacker can take over your computer.  Would you like that?  In case you didn't know, compromized Linux computers are worth nearly 10 times more than compromized Windows computers due to their vastly superior abilities and toolset.

Okay, so what versions are vulnerable?
I just checked my flash version and it is pretty old.  I followed these instructions several months ago but ended up with a 10.0 era flash; people are talking about 10.1 here, which I think I downloaded at some point but apparently don't have installed.

It adds insult to injury that adobe doesn't even allow downloads of the last versions of 64 bit linux flash they produced.  Is there anyone who is willing to put up a copy so people can use it?  I realize we'd need to be careful about being given a trojan version, but that is easily remedied by having md5sums from a trusted source.

I haven't read adobe's distribution rules in awhile, but I do recall back in the bad old days they had some restrictions even though the player was free as in beer.  However there were even then conditions under which it was allowed.  That is something to think about as well.

---

### Post by rifter on 2010-08-03
> **rifter said:**
> Okay, so what versions are vulnerable?
I just checked my flash version and it is pretty old.  I followed these instructions several months ago but ended up with a 10.0 era flash; people are talking about 10.1 here, which I think I downloaded at some point but apparently don't have installed.

It adds insult to injury that adobe doesn't even allow downloads of the last versions of 64 bit linux flash they produced.  Is there anyone who is willing to put up a copy so people can use it?  I realize we'd need to be careful about being given a trojan version, but that is easily remedied by having md5sums from a trusted source.

I haven't read adobe's distribution rules in awhile, but I do recall back in the bad old days they had some restrictions even though the player was free as in beer.  However there were even then conditions under which it was allowed.  That is something to think about as well.

Well... There went that idea. :cry:
[http://www.adobe.com/products/players/fpsh_distribution1.html](http://www.adobe.com/products/players/fpsh_distribution1.html)
> 
You may post Adobe Flash Player on company intranet sites or local networks. You may also distribute the Players on a CD, DVD, or any other physical media within the terms and conditions of the electronic Player Distribution License Agreement.


[http://www.adobe.com/products/players/fpsh_faq.html#section-1-5](http://www.adobe.com/products/players/fpsh_faq.html#section-1-5)
> 

Can I make the Adobe Players available directly from my website?
    No. The Adobe free Player distribution agreement does not allow you to distribute the Players from your website. You must direct visitors to the Adobe Web Players area of our Downloads site. To easily link to our website, we provide Adobe Web Player buttons that you can display on your site. You can download the buttons and view the guidelines here: [http://www.adobe.com/macromedia/style_guide/buttons/](http://www.adobe.com/macromedia/style_guide/buttons/) 


So I guess they are still going to be jerks about distribution.  I guess it was too much to hope for.  I am sure that no one wants to be spanked by adobe just for giving people a flash plugin that may or may not be vulnerable anyway.

---

### Post by michael37 on 2010-08-03
> **rifter said:**
> Okay, so what versions are vulnerable?
I just checked my flash version and it is pretty old.  I followed these instructions several months ago but ended up with a 10.0 era flash; people are talking about 10.1 here, which I think I downloaded at some point but apparently don't have installed.

[http://www.adobe.com/support/security/advisories/apsa10-01.html]("http://www.adobe.com/support/security/advisories/apsa10-01.html")

A critical  vulnerability exists in Adobe Flash Player 10.0.45.2 and earlier versions for Windows, Macintosh, Linux and Solaris operating systems

> **rifter said:**
> It adds insult to injury that adobe doesn't even allow downloads of the last versions of 64 bit linux flash they produced.  Is there anyone who is willing to put up a copy so people can use it?  I realize we'd need to be careful about being given a trojan version, but that is easily remedied by having md5sums from a trusted source.

At this point, *all* versions of 64-bit Linux flash, including the latest, are vulnerable.  That's why you can't (and shouldn't) download it from Adobe site or anywhere else.  

Please re-read the advisory -- you can't protect yourself from that vulnerability.

---

### Post by Yellow Pasque on 2010-08-03
> Please re-read the advisory -- you can't protect yourself from that vulnerability.
Flash abstinence is the only safe way, but for people who are going to try Flash fornication anyway, I would strongly recommend a "Flashblock" add-on that blocks all Flash by default, (replacing Flash objects with a button that the user must click, and only autoloading Flash that is trusted/whitelisted).

---

### Post by rifter on 2010-08-04
> **Temüjin said:**
> Flash abstinence is the only safe way, but for people who are going to try Flash fornication anyway, I would strongly recommend a "Flashblock" add-on that blocks all Flash by default, (replacing Flash objects with a button that the user must click, and only autoloading Flash that is trusted/whitelisted).

Actually [color=blue]_[NoScript](http://noscript.net/)_[/color]  is an even better choice.  Not only does it block flash, but it preemptively blocks all scripts and code.  As we know any of that can be potentially harmful.  You can whitelist sites, but what is even better it divides the scripts by domains so that, for instance, if you go to a site and it has scripts from different sources, you can differentiate between them.  You can even give temporary permissions for a specific case, and revoke them, and it is pretty easy to revoke any permissions you want right from the browser window, or even block with prejudice certain domains so you will preemptively put a stop to their problems.

Unfortunately for a good while Chrome and Chromium had no extensions possible at all, and it still has nothing like NoScript, which is a Firefox extension.  _[color=blue][This article](http://techie-buzz.com/browsers/disable-javascript-images-cookies-in-google-chrome.html)[/color]_  promises that Google will give us something like that in Chrome/Chromium real soon now.  Which is good because Chrome is using the same Flash extension FireFox has on your system.

---

### Post by rifter on 2010-08-04
> **michael37 said:**
> [http://www.adobe.com/support/security/advisories/apsa10-01.html]("http://www.adobe.com/support/security/advisories/apsa10-01.html")

A critical  vulnerability exists in Adobe Flash Player 10.0.45.2 and earlier versions for Windows, Macintosh, Linux and Solaris operating systems



At this point, *all* versions of 64-bit Linux flash, including the latest, are vulnerable.  That's why you can't (and shouldn't) download it from Adobe site or anywhere else.  

Please re-read the advisory -- you can't protect yourself from that vulnerability.

Well, doesn't that mean that the 10.1.x versions of Flash are not affected?  Because that had been available up till now, I thought.  I know I downloaded it awhile back...

---

### Post by michael37 on 2010-08-04
> **rifter said:**
> Well, doesn't that mean that the 10.1.x versions of Flash are not affected?  Because that had been available up till now, I thought.  I know I downloaded it awhile back...

Actually, 10.1.X versions are not affected, they've been checked.  You can use 10.1.53.64, but it's available only for 32-bit.  You can feel free to install "sudo apt-get install flashplugin-installer" which will deploy nspluginwrapper and wrap 32-bit in your 64-bit browser.  Note that many bugs will appear such as non-working buttons, etc -- they've been all documented in this thread.  

So, I have to agree that flashblock and noscript are better solutions at this time.

---

### Post by crjackson on 2010-08-07
The current state of 64 bitness is really sad.  I wanted to put 64 bit on everything I have, but because my wife, kids, and sometimes myself watch various flash content it's not going to happen.

12 64bit systems ALL running 32bit Ubuntu.  Sad...:(

Some day 64bit Ubuntu will be on all my systems, but now when flash isn't working fully.

---

### Post by Linuxforall on 2010-08-08
64bit from day one of its introduction, intially flash was the issue but the latest adobe flash works flawlessly on Opera, Chrome and FF with the nsplugin, wrapper, I have not faced a single issue with any other software in x64, even Skype and Google Earth which are x32 programs with x64 wrapper never ever gave me issue here on not one but severeal different PCs and laptops.

---

### Post by Yellow Pasque on 2010-08-08
> **crjackson said:**
> The current state of 64 bitness is really sad.

64-bit is better than it's ever been. Flash video is still a buggy, resource-hogging pain for many. Hurry up, HTML5! :D

---

### Post by mc4man on 2010-08-08
Having needed a 64 bit iso this morning went to the ubuntu dl page - found it odd how they 'describe' the 64 bit install
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by crjackson on 2010-08-08
> **Linuxforall said:**
> 64bit from day one of its introduction, intially flash was the issue but the latest adobe flash works flawlessly on Opera, Chrome and FF with the nsplugin, wrapper, I have not faced a single issue with any other software in x64, even Skype and Google Earth which are x32 programs with x64 wrapper never ever gave me issue here on not one but severeal different PCs and laptops.

Well, I'll give it another chance.  I ran 64 for about a year and flash was not flawless for me.  I seem to remember that installing FF32 bit and flash 32 bit worked.  I'll have to look into that again.  That was my only complaint.

---

### Post by crjackson on 2010-08-08
> **mc4man said:**
> Having needed a 64 bit iso this morning went to the ubuntu dl page - found it odd how they 'describe' the 64 bit install
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Very suspicious indeed!

---

### Post by mas_sergio on 2010-08-09
i don't understand the instructions becuase everything has lines through it (crossed out) and where to get the script to install x64 flash? maybe I should just leave my buggy flash alone... i don't want to break something :s

---

### Post by bcschmerker on 2010-08-10
> **michael37 said:**
> [http://www.adobe.com/support/security/advisories/apsa10-01.html]("http://www.adobe.com/support/security/advisories/apsa10-01.html")

A critical  vulnerability exists in Adobe Flash Player 10.0.45.2 and earlier versions for Windows, Macintosh, Linux and Solaris operating systems



At this point, *all* versions of 64-bit Linux flash, including the latest, are vulnerable.  That's why you can't (and shouldn't) download it from Adobe site or anywhere else.  

Please re-read the advisory -- you can't protect yourself from that vulnerability.
The actual [Security Bulletin for Flash Platform](http://www.adobe.com/support/security/bulletins/apsb10-14.html) identifies multiple critical bugs.  At this point, I have to go on the assumption that Adobe Systems has pushed 64-bit support to the in-development (as of August 2010) Flash Platform 11; testing 64-bit fixes is a relatively new art in the commercial-software business.  Adobe *did* patch Flash Player 9, as Version 9.0.277.0.

---

### Post by Mark76 on 2010-08-12
Is anyone else having problems with embedded videos (not iplayer) on the BBC website and the MySpace musicplayer?

Neither of which seem to be working properly for me.

---

### Post by PsYcHoTiC_MaDmAn on 2010-08-15
> **Mark76 said:**
> Is anyone else having problems with embedded videos (not iplayer) on the BBC website and the MySpace musicplayer?

Neither of which seem to be working properly for me.

Yes, flash works elsewhere > miniclip or youtube for example

but every time I try iplayer I get "flash plugin crashed" using the 64bit flash

however chromium allows me to watch it

---

### Post by LenW on 2010-08-19
Many thanks for this procedure - flash now works very well for me.
( I used the copy at 
   [https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins#flash](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins#flash) )
BUT this procedure as it stands is NOT compatible with the very 
important package ubuntu-restricted-extras 
- a problem which seems easy to fix:

The "extras" package uses the alternative name "mozilla-flashplugin"
for the generic name /usr/lib/mozilla/plugins/flashplugin-alternative.so .
I believe that if this procedure (and script) did likewise, 
all would be fine.  Is there anything else that requires using 
"xulrunner-addons-flashplugin" ?

As it stands, every time I ran apt-get after the "extras" package failed,
it kept trying to finish and returned a code of 2 and error message:
 > update-alternatives: error: alternative link 
 > /usr/lib/mozilla/plugins/flashplugin-alternative.so 
 > is already managed by xulrunner-addons-flashplugin.

To fix this, I did:```

  sudo update-alternatives --remove xulrunner-addons-flashplugin \
     /usr/lib/flashplugin-installer/libflashplayer64.so
  sudo apt-get   (something)  
  sudo update-alternatives --install  \
     /usr/lib/mozilla/plugins/flashplugin-alternative.so  \
     mozilla-flashplugin  \
     /usr/lib/flashplugin-installer/libflashplayer64.so 60
  
```
This automatically activated the right plugin since it has a higher
priority (60 vs 50) than the one installed in "extras" .

But if the "mozilla-flashplugin" name was used by this procedure,
all would work fine no matter which order the installations were done.

One silver lining of all of this is that I think I now understand
update-alternatives.  :-)

Thanks for helping me to install this great plugin.
Cheers,
-Len

---

### Post by Mark76 on 2010-08-24
I ran Seamonkey from a terminal. Navigated to a BBC webpage with embedded video and got this

> *** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()


---

### Post by michael37 on 2010-08-24
> **Mark76 said:**
> I ran Seamonkey from a terminal. Navigated to a BBC webpage with embedded video and got this

Wrong thread, we don't use npviewer using this method.

---

### Post by michael37 on 2010-08-24
> **LenW said:**
> Many thanks for this procedure - flash now works very well for me.
<snip>
Thanks for helping me to install this great plugin.
Cheers,
-Len

Ouch, that procedure still works.  Not good at all.  

Please read the OP in this thread about the current status of this plugin.

---

### Post by Yellow Pasque on 2010-08-24
> **michael37 said:**
> Wrong thread, we don't use npviewer using this method.
Uhh, npviewer is a part of nspluginwrapper...

---

### Post by michael37 on 2010-08-24
> **Temüjin said:**
> Uhh, npviewer is a part of nspluginwrapper...

Yeah, we don't use it in this thread.  This thread is about native 64-bit flash.

Please open another thread about your environment with nspluginviewer emulator.

---

### Post by hotstepperk on 2010-08-25
> **michael37 said:**
> 

[SIZE="3"]
Installation for 32-bit Adobe Flash installation on 64-bit systems[/SIZE]
[LIST=1]
[*]**Complete cleanup instructions.**  
brainspank contributed a script in comment 72, [direct link]("http://ubuntuforums.org/showpost.php?p=8666948&postcount=72"), which wipes all versions of Flash from your computer.  Run this script.
[*]Run command ```
sudo apt-get install flashplugin-installer
```
[*]Close all browsers.
[*]Test by going to [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/).  Version 10,1,82,76 should show up in "Version" box.
[*]Youtube and some other sites will work.  Many sites will not.  Complaints here: [http://www.adobe.com/support/flash/](http://www.adobe.com/support/flash/)
[/LIST]




Thanks man. I was having problems with my flash, this works fine. Kindly tell me which sites dont work though? Thanks again.

---

### Post by lotharjade on 2010-08-29
It sounds like Gnash (a replacement for Flash) has just made another release, and has been making great improvements (AND WORKS FOR 64-BIT!).  Does anyone know how this compares to the 32-bit Flash?  Does it work with Hulu, Iplayer, etc?  Are there any good reviews of the new Gnash vs. Flash?  I would be tempted to switch.  (I suspect we all would like to kick Adobe to the curb if possible)

[http://lwn.net/Articles/401443/]("http://lwn.net/Articles/401443/")

---

### Post by Yellow Pasque on 2010-08-29
> **michael37 said:**
> Yeah, we don't use it in this thread.  This thread is about native 64-bit flash.

Please open another thread about your environment with nspluginviewer emulator.
but 64-bit Flash is dead.. so what are you advocating (i.e what is this thread about)?

---

### Post by Linuxforall on 2010-08-29
From the tests done on the latest Gnash and Lightspark, things look promising but still a long way to go, some sites work, youtube mostly work but the issue of CPU consumption even with promised hardware acceleration via Open GL support has not been fulfilled it seems, CPU usage on average is way higher in both Gnash and Lightspark compared to Adobe Flash.

---

### Post by makoto149 on 2010-09-12
Just installed Ubuntu 10.04 on my new HP Pavilion S5360F Desktop, on which Windows was pre-installed (of course, gag) and lasted all of 10 minutes before I laid down a sweet dual boot setup.

Everything works great, except Flash. But thanks to the instructions in this post, it works like a dream. Can't live without youtube, man. Can't do it.

Thanks to the author of this post. You rock.

---

### Post by Detonate on 2010-09-12
Just for information, YouTube no longer requires flash.  You can view videos on YouTube with the new HTML5 viewer.  Go here and opt in to the viewer.

[http://www.youtube.com/html5](http://www.youtube.com/html5)

---

### Post by diosak on 2010-09-13
i used Google's Chrome browser on a 64-bit Ubuntu 10.10 system.
neither the stable nor the beta version of the browser worked with flash.
i just installed the dev one and it seems to be ok!
try it out!

---

### Post by CadetD on 2010-09-15
Try the new Adobe Flash Square 64bit plugin at: 
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
It is still alpha or beta, but works well so far.

---

### Post by m1001879 on 2010-09-15
> **CadetD said:**
> Try the new Adobe Flash Square 64bit plugin at: 
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
It is still alpha or beta, but works well so far.

Perfect timing, I've been trying to solve this problem all night!

I'm a total ubuntu/linux newbie so forgive my computer illiteracy, but what do I do with the file when it opens? It opens in archive manager as a tar.gz file. Now what?

---

### Post by crjackson on 2010-09-15
> **m1001879 said:**
> Perfect timing, I've been trying to solve this problem all night!

I'm a total ubuntu/linux newbie so forgive my computer illiteracy, but what do I do with the file when it opens? It opens in archive manager as a tar.gz file. Now what?

Extract the file and place it in the browser's plugin folder.

---

### Post by m1001879 on 2010-09-15
> **crjackson said:**
> Extract the file and place it in the browser's plugin folder.

And how do I do that? Bear in mind I've never used linux before so it's all a little new to me, this is all rather more automatic on windoze.

This is what I see on the screen in front of me (obviously I can see the 'extract' button, how do I extract into the firefox plugin folder?)...

[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]http://i55.tinypic.com/ohk3p.png[/IMG]

---

### Post by Mark76 on 2010-09-16
Bah. The BBC site doesn't work properly even with the new plugin.

I'm beginning to suspect that they've secretly switched to html5 without telling anyone.

---

### Post by Linuxforall on 2010-09-16
Not only does this version run better and smoother in full screen or regular, it also uses way less CPU than x32 via nsplugin.

---

### Post by formaldehyde_spoon on 2010-09-16
> **m1001879 said:**
> And how do I do that? Bear in mind I've never used linux before so it's all a little new to me, this is all rather more automatic on windoze.

This is what I see on the screen in front of me (obviously I can see the 'extract' button, how do I extract into the firefox plugin folder?)...



Right click on the .tar.gz file, select 'extract here'.
You'll see a .so file.
Go to your Home folder, click View > Show Hidden Files
From your Home folder go into .mozilla/plugins
Put the .so file there, restart Firefox

---

### Post by jdunn on 2010-09-16
> **CadetD said:**
> Try the new Adobe Flash Square 64bit plugin at: 
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
It is still alpha or beta, but works well so far.

Works well for me.

---

### Post by kitchens on 2010-09-16
What do I have to do to get this to work with Chrome? Extract it to /usr/lib/flashplugin-installer/ ?

---

### Post by akai_kenshi on 2010-09-16
Chrome should pull the plugin from the /.mozilla folder, you shouldn't have to do anything special.

Open up Chrome and type "chrome://plugins" in the URL bar. If you see "Shockwave Flash 10.2 d161" then you're good to go.

---

### Post by kitchens on 2010-09-16
Does it matter that I don't have Firefox installed at all?

---

### Post by madeinfamous on 2010-09-16
hello all,

find this script a little while ago in the forum here, (only for amd64)

i've modified it for your convenience,

[https://sites.google.com/site/nueusx/Get64bitFlash_codename_square.tar.gz]("https://sites.google.com/site/nueusx/Get64bitFlash_codename_square.tar.gz")


it will remove old flash and install the new one,

extract, double click it, choose launch in terminal, type "yes" when prompt,

[http://www.adobe.com/software/flash/about/]("http://www.adobe.com/software/flash/about/")  here you can verified you have the new version "10,02,161,22"

have a nice week

note: i haven't created this script, so thx to whoever made it :)

---

### Post by piemonkey on 2010-09-16
A very nice person called SevenMachines has a ppa that now contains the latest 64bit flash player, and presumably will be updated if and when Adobe update their version (although I wouldn't put it past them dumping it again).

Just add ppa:sevenmachines/flash to your software sources, or see here [https://launchpad.net/~sevenmachines/+archive/flash](https://launchpad.net/~sevenmachines/+archive/flash) for more details.

---

### Post by vgrisham on 2010-09-16
Now that Adobe has made good on it's pledge to resuscitate 64 bit flash for Linux, perhaps we could remove the big red MURDER heading at the beginning of this thread. :D

---

### Post by michael37 on 2010-09-16
> **vgrisham said:**
> Now that Adobe has made good on it's pledge to resuscitate 64 bit flash for Linux, perhaps we could remove the big red MURDER heading at the beginning of this thread. :D

Tough customer, you got to give me a few hours to update and test the script :)

New instructions will be posted very shortly!

---

### Post by michael37 on 2010-09-16
Hulu works great for me now, with the new version.

Please report non-working sites in this thread.

---

### Post by michael37 on 2010-09-16
> **piemonkey said:**
> A very nice person called SevenMachines has a ppa that now contains the latest 64bit flash player, and presumably will be updated if and when Adobe update their version (although I wouldn't put it past them dumping it again).

Just add ppa:sevenmachines/flash to your software sources, or see here [https://launchpad.net/~sevenmachines/+archive/flash](https://launchpad.net/~sevenmachines/+archive/flash) for more details.

Unless sevenmachines has permissions to redistribute software (which I doubt), then his package is **illegal** and he and any user of his ppa is in violation of Adobe EULA.

If you prefer not to be suited by Adobe, please follow instructions in this thread.

---

### Post by formaldehyde_spoon on 2010-09-17
> **michael37 said:**
> Unless sevenmachines has permissions to redistribute software (which I doubt), then his package is **illegal** and he and any user of his ppa is in violation of Adobe EULA.

If you prefer not to be suited by Adobe, please follow instructions in this thread.
Even if sevenmachines has violated Adobe's EULA (which seems likely), it hasn't done anything illegal - ie. no laws have been broken.
Sevenmachines may (and I stress 'may') be vulnerable to civil action by Adobe, but have not commited any crime.  
It's unlikely Adobe would take serious action against Sevenmachines, and absolutely unthinkable to imagine they might sue someone who has used Sevenmachines (even if there was a case to answer by the user, which I seriously doubt)

Off on a slight tangent: don't forget anyone can put ANYTHING in a EULA.  I could specify what colour clothes you should wear while using my software if I wanted, and then (try) to sue you for beach of contract if you didn't! ;)

---

### Post by Linuxforall on 2010-09-17
If EULA were to be followed, all Linux users are violating M$ patents one way or another,even when you type SUDO :)

---

### Post by formaldehyde_spoon on 2010-09-17
> **Linuxforall said:**
> If EULA were to be followed, all Linux users are violating M$ patents one way or another,even when you type SUDO :)
Not really. EULA is intended to be a sort of contract you abide by while using and/or installing someone's software.  If you aren't using MS software their EULAs are irrelevant. (and EULAs are completely unrelated to patents)

---

### Post by Linuxforall on 2010-09-17
> **formaldehyde_spoon said:**
> Not really. EULA is intended to be a sort of contract you abide by while using and/or installing someone's software.  If you aren't using MS software their EULAs are irrelevant. (and EULAs aer absolutely unrelated to patents)

Not really, MS owns various patents ranging from JPEG, sudo and more, its just that they don't have the interest to enforce it now as desktop linux is not yet a threat to their livelihood, wait till linux captures 30% of desktop market, M$ will come with fire and brimstone and thats a guarantee.

---

### Post by formaldehyde_spoon on 2010-09-17
> **Linuxforall said:**
> Not really, MS owns various patents ranging from JPEG, sudo and more, its just that they don't have the interest to enforce it now as desktop linux is not yet a threat to their livelihood, wait till linux captures 30% of desktop market, M$ will come with fire and brimstone and thats a guarantee.
You are talking about something different.  If you want to talk about patents I'b be happy to discuss them, in a seperate thread.

I say again, patents are NOT related to EULAs.  EULAs was already a bit off topic, please don't derail the existing (slight) derailment. ;)

---

### Post by Linuxforall on 2010-09-17
> **formaldehyde_spoon said:**
> You are talking about something different.  If you want to talk about patents I'b be happy to discuss them, in a seperate thread.

I say again, patents are NOT related to EULAs.  EULAs was already a bit off topic, please don't derail the existing (slight) derailment. ;)

No one is derailing anything here, the very mention of the ppa bought up this topic, EULA and patents are inter related period, now don't go derailing that please :)

---

### Post by formaldehyde_spoon on 2010-09-17
> **Linuxforall said:**
> No one is derailing anything here, the very mention of the ppa bought up this topic, **EULA and patents are inter related period,** now don't go derailing that please :)
They are not.  Not in any way or fashion, not by any stretch of the imagination.  I suggest you look them up.

I for one am not going to discuss patents again in this thread.

---

### Post by Linuxforall on 2010-09-17
> **formaldehyde_spoon said:**
> They are not.  Not in any way or fashion, not by any stretch of the imagination.  I suggest you look them up.

I for one am not going to discuss patents again in this thread.

I did, you are wrongly interpreting the meaning, anyways moot point here, ppa for sevenseas is fine and I am sure Adobe won't have any issues with it. PPA method is not only convenient for those who are not savvy with cli, also the fact it will auto update itself is a boon.

---

### Post by Yellow Pasque on 2010-09-17
Yeah, I'm pretty sure that SevenMachines lives somewhere in Europe, where they don't have tyrannical laws and the fscking DEA. GOD BLESS AMERICA, because corporations >  people.

---

### Post by makoto149 on 2010-09-17
This worked amazingly well on Ubuntu 10.04. My undying gratitude to the author(s) of the original post.

---

### Post by formaldehyde_spoon on 2010-09-18
> **Linuxforall said:**
> **I did, you are wrongly interpreting the meaning,** anyways moot point here, ppa for sevenseas is fine and I am sure Adobe won't have any issues with it. PPA method is not only convenient for those who are not savvy with cli, also the fact it will auto update itself is a boon.

O rly? Links please.

---

### Post by proculation on 2010-09-19
OH
MY
GOD !!!!

AT LAST !!!  :guitar:

I've so HATED nspluginwrapper... HATED !

For months I'm waiting for an alternative. Surfing the web was almost non-possible. The CPU went 100%. IOwait too. The mouse and keyboard stuck.

I had to kill firefox/chrome and npviewer a lot of times a day and sometimes the computer was so frozen I had to just reboot manually.

Thanks !!!

---

### Post by xain72 on 2010-09-19
Thanks!! :razz:
I really hate the nspluginwrapper... cpu over 60%-70% only to view a video on youtube....

---

### Post by mc4man on 2010-09-19
As far as the ppa it should be noted it's only an installer with a couple of scripts.
Overall in these matters (patents, codecs, ect.), what's so called 'legal or illegal' is really 'is there money to be had or not'

As far as the end users of anything for their own personal use there isn't, so nobody cares - might as well call that 'legal'

---

### Post by SnowflakeRV7 on 2010-09-20
So leaving aside patent and EULA issues and getting back to Flash and making it work properly under 64-bit Ubuntu, I now have the latest Flash version installed and running, but with *no audio*.  Has anyone found a fix for that?  I'm running an nVidia chipset, btw, which I think matters.

---

### Post by formaldehyde_spoon on 2010-09-20
> **SnowflakeRV7 said:**
> So leaving aside patent and EULA issues and getting back to Flash and making it work properly under 64-bit Ubuntu, I now have the latest Flash version installed and running, but with *no audio*.  Has anyone found a fix for that?  I'm running an nVidia chipset, btw, which I think matters.

I'm having no Flash trouble with my nvidia gear...

---

### Post by efflandt on 2010-09-20
The most recent revived 64-bit flash plugin from [http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/) is flashplayer_square_p1_64bit_linux_091510.tar.gz

Firefox shows the extracted plugin as Shockwave Flash 10.2 d161

Wasn't sure where to put it, so I put it in /usr/lib/mozilla/plugins/

The only thing that did not find it automatically was Hulu Desktop, so I had to point ~/.huludesktop to /usr/lib/mozilla/plugins/libflashplayer.so instead of the previous uninstalled nswrapper 32-bit version.

Seems to work fine for everything so far on i5 650 3.2 GHz, GT220 with nVidia v195.36.24.  It seems to use an average of 25% of each of my 4 real or simulated cpus according to System Monitor, but I don't know if that is % of current or max cpu speed because often 2 or 3 are idling at 1200 MHz and rarely do any go to 3.2 GHz.

---

### Post by Yellow Pasque on 2010-09-20
> **SnowflakeRV7 said:**
> So leaving aside patent and EULA issues and getting back to Flash and making it work properly under 64-bit Ubuntu, I now have the latest Flash version installed and running, but with *no audio*.  Has anyone found a fix for that?  I'm running an nVidia chipset, btw, which I think matters.
If Flash is not showing in the sound control panel, you might have to do this: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

If the above fix is not the issue, try starting FF from the terminal.

---

### Post by captain_rob on 2010-09-21
Thank you for thr solution of installing shockwave 10.2 d161 :)

But today a update of 10.04 installed brought me 10.1 r85 back, so I have now two plugins installed. How can I get rid of the last one??

---

### Post by michael37 on 2010-09-22
> **captain_rob said:**
> Thank you for thr solution of installing shockwave 10.2 d161 :)

But today a update of 10.04 installed brought me 10.1 r85 back, so I have now two plugins installed. How can I get rid of the last one??

Run the complete cleanup script mentioned in the troubleshooting section of the original post, that will uninstall all other flashes (so that update doesn't try to reinstall it)

You may need to rerun Get64bitFlash script afterwards.

---

### Post by michael37 on 2010-09-22
> **efflandt said:**
> The most recent revived 64-bit flash plugin from ...
Firefox shows the extracted plugin as Shockwave Flash 10.2 d161

Wasn't sure where to put it, so I put it in /usr/lib/mozilla/plugins/


That's why there are instructions and a script in the original post.

---

### Post by michael37 on 2010-09-22
> **makoto149 said:**
> This worked amazingly well on Ubuntu 10.04. My undying gratitude to the author(s) of the original post.

Thank you, it's my pleasure.  I do want to give credit to the original author whose name I unfortunately do not recall due to passage of time.

---

### Post by michael37 on 2010-09-22
> **mc4man said:**
> As far as the ppa it should be noted it's only an installer with a couple of scripts.
Overall in these matters (patents, codecs, ect.), what's so called 'legal or illegal' is really 'is there money to be had or not'

As far as the end users of anything for their own personal use there isn't, so nobody cares - might as well call that 'legal'

Adobe EULA mentions absolutely nothing about commercial vs non-commercial use.  It says that redistribution is illegal.  Sevenmachines redistributes Adobe software, thus, what he is doing is illegal.

Look, I would MUCH prefer if Adobe Flash was open source software and I was able to redistribute it under GPL.  But I can't, and I have to respect rights of software authors that a large number of end users on this board is apparently enjoying.

---

### Post by michael37 on 2010-09-22
> **Temüjin said:**
> If Flash is not showing in the sound control panel, you might have to do this: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

If the above fix is not the issue, try starting FF from the terminal.

Thank you, I added this link to the troubleshooting section.  On my computer, flash uses alsa by default.

According to the Adobe page, 
[http://www.adobe.com/products/flashplayer/systemreqs/](http://www.adobe.com/products/flashplayer/systemreqs/)
sound will not work if computer is configured to use OSS or ESD.

---

### Post by mc4man on 2010-09-22
> Sevenmachines redistributes Adobe software, thus, what he is doing is illegal.
I fail to see what software he/she is redistributing - there is no adobe software in the ppa, only some install scripts

(possibly you should ck.something out before making comments on...

---

### Post by formaldehyde_spoon on 2010-09-22
> **michael37 said:**
> Adobe EULA mentions absolutely nothing about commercial vs non-commercial use.  It says that redistribution is illegal.  Sevenmachines redistributes Adobe software, thus, what he is doing is illegal.

...


Now I'm just repeating myself.
It is not illegal(ie no laws have been broken).
The EULA does not say that. - and since when could people make new laws in EULAS!?
At worst, sevenmachines could be sued for breach of contract (whether that would be successful or not is another story).
The reason Adobe mentions redistribution is so they can't be held liable for any trouble caused by their redistributed software - so BECAUSE that clause is in their EULA, they aren't going to care if sevenmachines redistributes their free software for the sake of helping others install it. 

EDIT:
> **mc4man said:**
> I fail to see what software he/she is redistributing - there is no adobe software in the ppa, only some install scripts

(possibly you should ck.something out before making comments on...

:-\
In that case this is a total non-issue.  I can't believe it's even been brought up! ;)

---

### Post by rifter on 2010-09-22
So, now that there is a 64 bit linux flash I am wanting to go back again, following your excellent instructions, but I seem to have a bit of a problemwith this bit:
> 
Binary 32-bit version from Mozilla site is NOT supported and will not work. Select Help -> About Mozilla Firefox. Differences are highlighted below.
RIGHT 64-bit browser: Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2) Gecko/20100123 Ubuntu/9.10 (karmic) Firefox/3.6
WRONG 32-bit browser: Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-US; rv:1.9.1.6) Gecko/20091201 Firefox/3.5.6


When adobe pulled the 64 bit linux flash and the instructions changed to undoing the 64 bit flash and reinstalling the 32 bit flash, I followed those directions but I do not recall whether I went back to a 32 bit firefox or not.

I do have the ppa listed [color=blue]_[here](https://help.ubuntu.com/community/FirefoxNewVersion)_[/color], as instructed ( ppa:mozillateam/firefox-stable ) I am not sure whether apt-cache policy is saying my firefox is from but I think it looks like it may not be from there:
> 
$ apt-cache policy firefox
firefox:
  Installed: 3.6.10+build1+nobinonly-0ubuntu0.9.10.1
  Candidate: 3.6.10+build1+nobinonly-0ubuntu0.9.10.1
  Version table:
 *** 3.6.10+build1+nobinonly-0ubuntu0.9.10.1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
        500 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
        100 /var/lib/dpkg/status
     3.6.7+build2+nobinonly-0ubuntu0.9.10.1 0
        500 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
     3.5.3+build1+nobinonly-0ubuntu6 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
$ 


The thing is that the string you are talking about no longer seems to appear in the firefox about box so I have no basis for comparison.  Instead it says (in an unselectable image no less so I have  to type it out by hand :P  )
> 
Firefox
version 3.6.10
Mozilla Firefox for Ubuntu canonical - 1.0


and then the copyright notice.  Is there anywhere else I can check?  I'm kind of annoyed if the setup I have led to a 32 bit firefox, even if it is because the 64 bit one is a lower version for some reason, since apt should not be switching architectures on me and I thought before that it would favor 64 bit versions of things if they were available in a given repository.

Can you shed some light on this?

---

### Post by Yellow Pasque on 2010-09-22
@rifter: Make the "about" window bigger ;)

---

### Post by LenW on 2010-09-23
The Ubuntu Update Manager is offering this update for flashplugin-installer:
> 
 Changes for the versions:
 10.1.82.76ubuntu0.10.04.2
 10.1.85.3ubuntu0.10.04.1
 
 Version 10.1.85.3ubuntu0.10.04.1: 
 
   * SECURITY UPDATE: New upstream release 10.1.85.3 (LP: #643811)
  <https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/643811>
     - debian/config, debian/postinst: Updated sha256sums and path
     - CVE-2010-2884 <http://cve.mitre.org/cgi-bin/cvename.cgi?name=2010-2884>


It certainly would be nice if we could now get where we want to go
by swimming downstream for a change.  
Is this a update a Good Thing?
  If not, could someone please review briefly why not,
  and perhaps some hint as to why Ubuntu keeps getting it wrong?

Thx,
-LenW

---

### Post by rifter on 2010-09-23
> **Temüjin said:**
> @rifter: Make the "about" window bigger ;)

D'oh! :oops: .. although it seems like cheating when an about box has no scrollbars but is smaller than it's content.

In any case my joy and rapture at your post, not to mention how flash seems to be working and claims the right version number, were instantly dispelled when I beheld this there:

```

Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.2.3) Gecko/20100401 Firefox/3.6.3

```

(Dr. Strangelove voice): "Mein fuhrer, I can copy and paste that part now!"

Now as listed above apt-cache policy et al seem to indicate the linux package is installed.  I actually recently purged wine so the windows firefox isn't anywhere that Ubuntu would want to look .. for all intents and purposes it is not installed (I wanted to redo some stuff that was installed in wine because I found I seem to have accidentally done something naughty to my prefix).  And of course the link I clicked on was the one at the top of the screen, which says it is just using the command firefox, like normal.  Further:

```

$ firefox -V
Mozilla Firefox 3.6.10, Copyright (c) 1998 - 2010 mozilla.org
$ which firefox
/usr/bin/firefox
$ 

```

Okay.. so to double check I kill firefox and start it manually from the command line (explicitly /usr/bin/firefox).  Predictably, it is the same result.
I have no clue why my firefox is saying that.  I guess I can purge it and start over but it will definitely be awhile getting my plugins, extensions, and settings and all back.

By the way, I do like your sig.  You are doing a good deed in spreading that.

---

### Post by rifter on 2010-09-23
An ominous sign, too, is that [color=blue]_[hulu](http://www.hulu.com)_[/color] is working now.  Either I do have the wrong flash somehow or they fixed their problems.

Why oh why didn't adobe include telling you the architecture when checking the version! :cry: :P

---

### Post by LenW on 2010-09-23
> **michael37 said:**
> Ouch, that procedure still works.  Not good at all.  


(Sorry, it's been a while since you wrote this, but I didn't see it
until yesterday....)
Could you please say a bit more?
What does "ouch" refer to?
What is "not good at all"?

Also, no one has commented on the substance of my post #257,
which had to do with update-alternatives.
In fact, the Get64bitFlash procedure doesn't use that facility.
Wouldn't that be a good idea?

Thx,
-LenW

---

### Post by michael37 on 2010-09-23
> **LenW said:**
> 
Also, no one has commented on the substance of my post #257,
which had to do with update-alternatives.
In fact, the Get64bitFlash procedure doesn't use that facility.
Wouldn't that be a good idea?

Thx,
-LenW

No.  This is a test version, and the intention is to use only this version and to remove others to prevent confusion and to simplify testing and troubleshooting.

In general, using system-wide alternatives for flash is quite meaningless.

---

### Post by michael37 on 2010-09-23
> **rifter said:**
> An ominous sign, too, is that [color=blue]_[hulu](http://www.hulu.com)_[/color] is working now.  Either I do have the wrong flash somehow or they fixed their problems.

Why oh why didn't adobe include telling you the architecture when checking the version! :cry: :P

Hulu is fixed indeed.  I asked people to test (since hulu worked for me), but this thread is too spammy so people didn't notice my question ;)

---

### Post by michael37 on 2010-09-23
> **rifter said:**
> I guess I can purge it and start over but it will definitely be awhile getting my plugins, extensions, and settings and all back.

Sound like a good plan to me.

---

### Post by LenW on 2010-09-23
OK, I have done the complete clean-up, installed the new version,
  and gotten the message "You have version 10,2,161,22 installed"
Works so far.

Is it known to be safe to go into the water with this one, in light of
this posting from Aug 3, 2010 :

> **michael37 said:**
> [http://www.adobe.com/support/security/advisories/apsa10-01.html]("http://www.adobe.com/support/security/advisories/apsa10-01.html")

A critical  vulnerability exists in Adobe Flash Player 10.0.45.2 and earlier versions for Windows, Macintosh, Linux and Solaris operating systems

At this point, *all* versions of 64-bit Linux flash, including the latest, are vulnerable.  That's why you can't (and shouldn't) download it from Adobe site or anywhere else.  

Please re-read the advisory -- you can't protect yourself from that vulnerability.

---

### Post by formaldehyde_spoon on 2010-09-23
> **LenW said:**
> OK, I have done the complete clean-up, installed the new version,
  and gotten the message &quot;You have version 10,2,161,22 installed&quot;
Works so far.

Is it known to be safe to go into the water with this one, in light of
this posting from Aug 3, 2010 :

Yes, note the version number (well actually, no-one ever knows software IS safe, they just don't know it ISN'T safe).  
There was a security hole in 10.0: Adobe fixed 32 bit with 10.1 within a week of that discovery, but just pulled 64 bit completely (until last week).

---

### Post by akernan on 2010-09-26
I have no problem with amd64 flashplugin for firefox except I can not upload pictures in Facebook.  It says I do not have flash installed.  I go to the [Adobe link]("http://www.adobe.com/software/flash/about/") verify my install, I have 10,2,161,22 installed.

Any ideas or help would be appreciated.

Thanks,
Tony

---

### Post by Linuxforall on 2010-09-26
For pic upload, Sun Java is needed, install it by enabling partner repo in synaptic.

---

### Post by akernan on 2010-09-27
I have Java installed, using the Icedtea plugin.  Why does it say I need to install Flash?

---

### Post by akernan on 2010-09-27
I just removed Icedtea and installed sun-java6 plugin, no change.  Here's a screen capture..

---

### Post by proteusmoteus on 2010-09-28
new flash player square version. preview 2 released yesterday available at
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by akernan on 2010-09-28
I installed the new 64 bit Flash, but I still get an upgrade msg when I try to upload photod on Facebook.  I installed gnash and it somewhat works. I can use the java uploader.

---

### Post by michael37 on 2010-09-28
> **proteusmoteus said:**
> new flash player square version. preview 2 released yesterday available at
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

updated.

---

### Post by michael37 on 2010-09-28
> **akernan said:**
> I just removed Icedtea and installed sun-java6 plugin, no change.  Here's a screen capture..

Looks like facebook bug.  Since both facebook and adobe flash is closed source, feel free to file bug reports with both.

---

### Post by Brad wilkinson on 2010-09-30
Hello,

Just installed per the script on the front page, the flash page reported the correct version and all. 

So youtube works again, but [http://www.abc.net.au/iview/#](http://www.abc.net.au/iview/#) tells me that flash has encountered a problem. 

*sigh*

Thanks for putting up the script though. all we need now is for the ABC to get their page up to date with the latest version of flash....

---

### Post by tech7 on 2010-09-30
hey this is awesome, thanks...  does anybody know if 10.10 will have a 64-bit binary??

---

### Post by michael37 on 2010-09-30
> **tech7 said:**
> hey this is awesome, thanks...  does anybody know if 10.10 will have a 64-bit binary??

The issue at hand is that 64-bit binaries are in preview mode.  Ubuntu does not ship software that is not released, so it's really out of Ubuntu's control (i.e. nothing that this forum can do).  Since Adobe controls flash destiny, feedback goes here: [http://bugs.adobe.com/flashplayer/](http://bugs.adobe.com/flashplayer/)

---

### Post by michael37 on 2010-09-30
> **Brad wilkinson said:**
> Hello,

Just installed per the script on the front page, the flash page reported the correct version and all. 

So youtube works again, but [http://www.abc.net.au/iview/#](http://www.abc.net.au/iview/#) tells me that flash has encountered a problem. 

*sigh*

Thanks for putting up the script though. all we need now is for the ABC to get their page up to date with the latest version of flash....

The interface works perfectly for me, incl. a bandwidth test.  I can't watch movies since I am not in Australia, but I am not seeing any problems.

Try full wipe (see OP) and reinstall script again?

---

### Post by mas_sergio on 2010-10-01
[SIZE="4"]I was having serious problems with flash in google chrome blocking out youtube videos. It was a very selective pattern I noticed some video's worked after the upgrade while others turned grey and flash would not load the video. The fix for me was a plugin conflict between FLASH and AdThwart... AdThwart (wich never gave me this problem before) somehow was conflicting with the newest version of FLASH when ad's were present in the videos in google Chrome's browser. The solution was to click on the adthwart icon and de-select  "Enabled for this page" box. That solved my problems.[/SIZE]

Check to see if any of your flash problems are plugin related to your browsers. That solved my problem anyways. =]

---

### Post by rifter on 2010-10-08
> **rifter said:**
> An ominous sign, too, is that [color=blue]_[hulu](http://www.hulu.com)_[/color] is working now.  Either I do have the wrong flash somehow or they fixed their problems.

Why oh why didn't adobe include telling you the architecture when checking the version! :cry: :P

Okay, I don't know why but a set of my responses are gone from the thread, or I don't see them, as are the responses to my responses.

Anyway I found out sometime back that the string that these instructions tell you to look at in the about box is actually the user agent string, which can change.  I was seeing windows version, and that is why.  I couldn't figure out how to go back, but either way that makes the about box not as reliable a place to get the version as far as architecture.

However, if you do

about:buildconfig

you get the real build information.  On my firefox, which I was sure is 64 bit and now know is, I get

```

about:buildconfig

Build platform
target
x86_64-unknown-linux-gnu

Build tools
Compiler 	Version 	Compiler flags
gcc 	gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) 	-Wall -W -Wno-unused -Wpointer-arith -Wcast-align -W -Wno-long-long -pedantic -g -fno-strict-aliasing -pthread -pipe -DNDEBUG -DTRIMMED -Os -freorder-blocks -fno-reorder-functions
c++ 	gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) 	-fno-rtti -fno-exceptions -Wall -Wpointer-arith -Woverloaded-virtual -Wsynth -Wno-ctor-dtor-privacy -Wno-non-virtual-dtor -Wcast-align -Wno-invalid-offsetof -Wno-long-long -pedantic -g -fno-strict-aliasing -fshort-wchar -pthread -pipe -DNDEBUG -DTRIMMED -Os -freorder-blocks -fno-reorder-functions

Configure arguments
--build=x86_64-linux-gnu --prefix=/usr '--includedir=/usr/include' '--mandir=/usr/share/man' '--infodir=/usr/share/info' --sysconfdir=/etc --localstatedir=/var '--libexecdir=/usr/lib/firefox-3.5' --disable-maintainer-mode --disable-dependency-tracking --srcdir=. --enable-optimize --enable-ipc --enable-tests --enable-mochitest --disable-system-cairo --disable-system-sqlite --without-system-nspr --without-system-nss --disable-debug --with-user-appdir=.mozilla --without-system-jpeg --without-system-zlib --enable-system-myspell --disable-crashreporter --disable-composer --disable-elf-dynstr-gc --disable-gtktest --disable-install-strip --disable-installer --disable-ldap --disable-mailnews --disable-profilesharing --disable-strip --disable-strip-libs --disable-tests --disable-mochitest --disable-updater --disable-xprint --enable-application=browser --enable-canvas --enable-default-toolkit=cairo-gtk2 --enable-gnomevfs --enable-pango --enable-postscript --enable-svg --enable-mathml --enable-xft --enable-xinerama --enable-extensions=default,-reporter --enable-safe-browsing --enable-single-profile --with-distribution-id=com.ubuntu --enable-startup-notification --enable-official-branding 

```

That is the real and authoritative build information but if it is gobledegook to you no worries, just look for the build target, which is on top.  Notice it says x86_64 which is a 64 bit architecture.  Maybe we should change the instructions?  People change user agent strings all the time.  I had done so at some point for the usual reason of seeing if I got a better response from some site that did not work with linux firefox.  Often this is from silly user agent checking rather than an actual breakage and the ie version works fine.

---

### Post by rifter on 2010-10-09
> **efflandt said:**
> The most recent revived 64-bit flash plugin from [http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/) is flashplayer_square_p1_64bit_linux_091510.tar.gz

Firefox shows the extracted plugin as Shockwave Flash 10.2 d161

Wasn't sure where to put it, so I put it in /usr/lib/mozilla/plugins/

The only thing that did not find it automatically was Hulu Desktop, so I had to point ~/.huludesktop to /usr/lib/mozilla/plugins/libflashplayer.so instead of the previous uninstalled nswrapper 32-bit version.

Seems to work fine for everything so far on i5 650 3.2 GHz, GT220 with nVidia v195.36.24.  It seems to use an average of 25% of each of my 4 real or simulated cpus according to System Monitor, but I don't know if that is % of current or max cpu speed because often 2 or 3 are idling at 1200 MHz and rarely do any go to 3.2 GHz.

Thanks for the tip re: hulu desktop.  I had wondered why it quit working.  I guess it hardcodes that line or something because I was sure I purged the package.  Anyway that change fixed it.  Hooray!

---

### Post by DimensionaL on 2010-10-10
You are awesome!Thanks a lot my friend for your post this flash "thing" was my problem for days!!:P:P

---

### Post by formaldehyde_spoon on 2010-10-10
> **Brad wilkinson said:**
> Hello,

Just installed per the script on the front page, the flash page reported the correct version and all. 

So youtube works again, but [http://www.abc.net.au/iview/#](http://www.abc.net.au/iview/#) tells me that flash has encountered a problem. 

*sigh*

Thanks for putting up the script though. all we need now is for the ABC to get their page up to date with the latest version of flash....
Hey Brad, ABC iview is working fine for me.

Watching Astro Boy now! :D

---

### Post by jonathan22 on 2010-10-10
Smooth installation on 10.10.  Thanks Michael!

---

### Post by Guyllfyre on 2010-10-13
The script ran without a hitch, Adobe site says it's installed, eBay picture uploader does not recognize Flash as being installed.

Any ideas?

I'm running Ubuntu Studio 10.04 x64.

---

### Post by Linuxforall on 2010-10-13
Why not use sevenmachines ppa for x64 flash?

---

### Post by Guyllfyre on 2010-10-14
> **Linuxforall said:**
> Why not use sevenmachines ppa for x64 flash?

Didn't know it existed.

Added it to my repositories, figured out the name of it, apt-get installed it, and now flash works.

---

### Post by simplio on 2010-10-30
I'm trying more than 6 months to install the 64bit flash player on my ubuntu.  Thank you veeeeeeeeeeeeeery much........
You 've made it so easy for a beginner like me

---

### Post by mad_max0204 on 2010-10-31
Finally. Flash works like it should. No freezes no bad performance in fullscreen and no other glitches that existed in previous versions. Looks like adobe finally did it like they should have done it years back.
And yeah thanks for the install script.

PS. No need for reboot :)

---

### Post by nobane on 2010-11-05
this solved my problems thank you

---

### Post by ThatLucidGuy12 on 2010-11-07
Oh, thank you! Just to let you know that going to YouTube and allowing Firefox to install plugins worked for me in said OS. Rock on! :guitar:

---

### Post by michael37 on 2010-11-07
> **ThatLucidGuy12 said:**
> Oh, thank you! Just to let you know that going to YouTube and allowing Firefox to install plugins worked for me in said OS. Rock on! :guitar:

That probably means you are not running 64-bit Firefox, or smth else is broken in your setup.

---

### Post by MickM on 2010-11-07
I am having no end of problems with my flash player. I cannot view youtube, I can view abc.com.au news but the sound is garbled. 
When I first installed ubuntu 5 weeks ago I was able to view youtube but about 4weeks ago everything went wrong. I have been trying to follow these t6hreads but my problems seem to be getting worse.
I am using an EeePC netbook.

---

### Post by Detonate on 2010-11-07
You know that most videos on YouTube, more everyday are being converted, can now be viewed with the embedded viewer in html5 in supported browsers.
Does not require flash.  Works great.
[http://www.youtube.com/html5](http://www.youtube.com/html5)

---

### Post by santosh83 on 2010-11-17
Thank you very much! Your script worked flawlessly here; just installed Maverick Meerkat. Tested with a few videos on Youtube... Seems to work as well as the 32-bit one did:-)

---

### Post by LenW on 2010-11-17
Is the script still needed, given the 
sevenmachines ppa ?

---

### Post by dBuster on 2010-11-21
Here is one for everyone.  NFL.com videos will not play.  I can get the commercials, ahem, I had commercials prior to the latest upgrade and now I have nothing.

[NFL test video]("http://www.nfl.com/videos/nfl-game-highlights/09000d5d81c47c03/Favre-OC-exchange-words-after-pick?module=HP_cp2")

Not sure why when everything else including hulu desktop is working for me.

---

### Post by Detonate on 2010-11-21
I'm using 10.10, 64bit flash, chromium-browser, GEForce 9500 GT video, i5 CPU,and it played for me.  At first, the picture quality was poor but after a few seconds it cleared up.

---

### Post by Yellow Pasque on 2010-11-22
> **LenW said:**
> Is the script still needed, given the 
sevenmachines ppa ?
Unfortunately, the script is needed, because lots of Ubuntu users don't know/care about the Debian policy where you shouldn't put files directly into /usr/... unless they're in a .deb package.

---

### Post by dBuster on 2010-11-22
> **Detonate said:**
> I'm using 10.10, 64bit flash, chromium-browser, GEForce 9500 GT video, i5 CPU,and it played for me.  At first, the picture quality was poor but after a few seconds it cleared up.

Could be due to my not using a current release?!  Who knows...  Saw the video today at work where I am forced to use windows...

---

### Post by Detonate on 2010-11-22
My flash version is 10.0 r45.

---

### Post by stber321 on 2010-11-23
not true 1st of all... because a lot [COLOR=black]of Firefox sour[/COLOR][U][COLOR=black]ce code is the same[/COLOR] as seamonky it will also run in seamonky
2nd... the easist way to install is though the repositories
[/U]

---

### Post by AldenIsZen on 2010-11-30
> **dBuster said:**
> Here is one for everyone. NFL.com videos will not play. I can get the commercials, ahem, I had commercials prior to the latest upgrade and now I have nothing.
 
[NFL test video]("http://www.nfl.com/videos/nfl-game-highlights/09000d5d81c47c03/Favre-OC-exchange-words-after-pick?module=HP_cp2")
 
Not sure why when everything else including hulu desktop is working for me.
 
 In windows 7 the video was jerky and yet I have dual core 3ghz PC with the latest flash installed. But I am using I.E. I will test it out with Ubuntu later, and I have the Flash Squared beta installed.

---

### Post by Harry33 on 2010-12-03
Great news.
Adobe has published 64-bit Flash Plugin 10.2 preview3 beta1 for Linux.
That one is capable of GPU acceleration (VDPAU, VA-API).

Just go and download the flashpalyer_10_2_p3_64bit_linux_111710.tar.gz file,
extract it (libflashplayer.so) and put it into plugins folder of your browser.
In Natty with Chromium: /usr/lib/chromium-browser/plugins/
In Natty with Firefox: /usr/lib/mozilla/plugins/

Here:
[http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)

---

### Post by Yellow Pasque on 2010-12-03
> **Harry33 said:**
> Great news.
Adobe has published 64-bit Flash Plugin 10.2 preview3 beta1 for Linux.
That one is capable of GPU acceleration (VDPAU, VA-API).
The 64-bit beta does not contain Adobe's new Stage Video acceleration; only the 32-bit beta does. Also, there is no VA-API support, just VDPAU and CrystalHD. Basically, only nvidia card owners who use the binary driver and 32-bit (or 32-bit Flash) will get GPU acceleration.

> In Natty with Chromium: /usr/lib/chromium-browser/plugins/
In Natty with Firefox: /usr/lib/mozilla/plugins/[/code]
You really shouldn't install random files into /usr and its subdirectories (per Debian policy). Make a plugin directory in ~/.mozilla and put flash there.

---

### Post by akwala on 2010-12-03
> **Harry33 said:**
> Great news.
Adobe has published 64-bit Flash Plugin 10.2 preview3 beta1 for Linux.
That one is capable of GPU acceleration (VDPAU, VA-API).

Just go and download the flashpalyer_10_2_p3_64bit_linux_111710.tar.gz file,
extract it (libflashplayer.so) and put it into plugins folder of your browser.
In Natty with Chromium: /usr/lib/chromium-browser/plugins/
In Natty with Firefox: /usr/lib/mozilla/plugins/

Here:
[http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)

For Maverick/Lucid/Karmic, add this repository to your software sources and install the flashpligin64 installer: [https://launchpad.net/~sevenmachines/+archive/flash](https://launchpad.net/~sevenmachines/+archive/flash)

This will download the plugin from adobe.com and put it where it needs to be -- you may need to manually remove/replace the older libflashplayer.so if you added it manually before.

---

### Post by akwala on 2010-12-04
> **Temüjin said:**
> TYou really shouldn't install random files into /usr and its subdirectories (per Debian policy). Make a plugin directory in ~/.mozilla and put flash there.
If you use **ppa:sevenmachines/flash** to install the 64-bit plugin, it will end up in /usr/lib/flashplugin-installer, which is specific to the installer; other /usr subdirs remain untouched, as far as I can tell. Links like the following in /etc/alternatives cause the respective browsers to use this plugin:
```
chromium-browser-flashplugin -> /usr/lib/flashplugin-installer/libflashplayer.so
firefox-flashplugin -> /usr/lib/flashplugin-installer/libflashplayer.so
mozilla-flashplugin -> /usr/lib/flashplugin-installer/libflashplayer.so
xulrunner-addons-flashplugin -> /usr/lib/flashplugin-installer/libflashplayer.so
xulrunner-flashplugin -> /usr/lib/flashplugin-installer/libflashplayer.so
```

---

### Post by francois.e on 2010-12-07
I work with ubuntu 10.10 64 bit on a hp pavilion 2713ca laptop.

Trying to use [https://launchpad.net/~sevenmachines/+archive/flash]("https://launchpad.net/%7Esevenmachines/+archive/flash") in the software sources of synaptic package manager.

What would be the missings fields;

ex: Source [https://launchpad.net/~sevenmachines/+archive/flash]("https://launchpad.net/%7Esevenmachines/+archive/flash") maverick main??

Help will certainly be appreciated. Thanks.

---

### Post by Yellow Pasque on 2010-12-07
> **francois.e said:**
> I work with ubuntu 10.10 64 bit on a hp pavilion 2713ca laptop.

Trying to use [https://launchpad.net/~sevenmachines/+archive/flash]("https://launchpad.net/%7Esevenmachines/+archive/flash") in the software sources of synaptic package manager.

What would be the missings fieldsù;

ex: Source [https://launchpad.net/~sevenmachines/+archive/flash]("https://launchpad.net/%7Esevenmachines/+archive/flash") maverick main??

Help will certainly be appreciated. Thanks.
In terminal:
```
sudo apt-add-repository ppa:sevenmachines/flash
```

---

### Post by francois.e on 2010-12-08
Thanks a lot for the solution. but finally it was not needed. 

Firefox proposed to install a few plugins including Shockwave flash. After rebooting the box, everything worked fine.

---

### Post by pafufta503 on 2010-12-24
thank you so much.  i was about to start smashing vegetables with a mallett in frustration.  whenever i tried to watch a flash video, it worked fine.  if i tried to right click the browser would freeze, while the audio still streamed.  if i tried to fullscreen my video would turn all glitchy and i'd have to restart.

the script fixed almost everything.  i can right click on the video now without freezing.  the fullscreen is still slightly buggy, doesn't respond to mouse click, but i can work around that.

---

### Post by Robins Airman on 2010-12-26
Thank you Michael37...this worked perfectly!

---

### Post by michael37 on 2010-12-26
Apologies for the long delay, and happy upcoming New Year to everyone!

Please re-run the script version 0.3.3 to update your Flash to the latest secure version which fixes **[COLOR="Red"]CRITICAL[/COLOR]** vulnerability.

> 
The Flash Player "Square" refresh from November 30th includes the fixes associated with this bulletin:

[http://www.adobe.com/support/security/bulletins/apsb10-26.html](http://www.adobe.com/support/security/bulletins/apsb10-26.html)

From [http://forums.adobe.com/message/3314389#3314389](http://forums.adobe.com/message/3314389#3314389)

---

### Post by nik_nah on 2011-01-11
I've tried various things, flash-aid, etc.  none of them worked, but this one is good!  Thank you!

---

### Post by roguebuck on 2011-01-13
this works in both opera 11 and the latest icecat.

---

### Post by DocToff on 2011-01-21
This works for me. Another score for Ubuntu, and I have one less reason to use my Windows partition.

Thank you.

---

### Post by FSPIC on 2011-01-24
I will look at the update but I just got two laptops with win 7 and AMD dual 2.2 CPU's. I easily put 10.10 on a vista machine w/ intel cpu (to best recollection) on a partition. Both halves work well. I am unable to install 10.10 or any variant or even earlier 64 bit ubuntu on my two Win 7 laptops w/ AMD duals.

Part of the problem may be the type of installation procedure which may require a boot, image, etc, disk, which I never did before. If I can get Ubuntu working in partitions of whole drives of my two desktop HP 3705 machines I will consider going totally Ubuntu on a laptop Win7 unit.

However on the win 7 machines I never got to the point of being asked if I wanted to do a total install, to best recollection. I will review my paperwork and identify my graphics and CPU fully and re-check this site as the last posting date may not cover my relatively (I guess) new stuff.

---

### Post by AldenIsZen on 2011-01-25
> **FSPIC said:**
> ...

Part of the problem may be the type of installation procedure which may require a boot, image, etc, disk, which I never did before. If I can get Ubuntu working in partitions of whole drives of my two desktop HP 3705 machines I will consider going totally Ubuntu on a laptop Win7 unit.
...

Please elaborate, I am not sure what you are trying to say here.

---

### Post by dBuster on 2011-01-26
> **AldenIsZen said:**
> Please elaborate, I am not sure what you are trying to say here.

I agree please elaborate more!  I do not think it is the CPU that is causing the issues for you.  There must be something else.

---

### Post by LenW on 2011-01-26
Is there a more appropriate place for a discussion
about Ubuntu installation problems?

---

### Post by BaldyLocks1972 on 2011-02-07
Works perfectly on my 64bit Ubuntu 10.10 installation.  Thanks.

---

### Post by zzzcreepyzzz on 2011-02-08
omg omg omg... you're the best!!!! I was stuck for soooooo long. it was driving me crazy... thank you thank you .... yayyyyy!!!!... flash works perfectly!

---

### Post by WinRiddance on 2011-02-08
DOES NOT WORK FOR ME with 64bit dual-core AMD laptop and Ubuntu 10.10 which was freshly installed a few weeks ago. But then again, part of the reason is the script itself perhaps since the "run in terminal" mode is not even available to me.

I do a lot of web design and when I double-click on the script, it opens up in my code editor. However, if I open my root terminal, followed by copying and pasting the entire script into the terminal, it still won't work. According to the adobe link I have the latest flash player installed, the numbers match. Personally, I think the majority of the crashes have more to do with ATI drivers (now owned by AMD) then anything else. The ATI drivers have been an issue for me since I switched to Ubuntu, during version 9.04 Jaunty. Since then "umpteen zillion" driver updates have been released during the past couple of years but the crashing problems, primarily with flash applications, have never been 100% resolved.

My laptop is only a couple of years old, has 4 GB of ram, and worked pretty much flawlessly with Windows Vista (ugh). But firefox crashing has been so bad that I can actually replicate this at will now ... all I have to do is visit a couple of flash intensive sites or view a few videos, and baaam, total freeze of the system ... hard reset required. Coincidentally my system ran a lot better with Ubuntu 9.10 which was widely hailed to be a memory hog ....
Go figure ....

---

### Post by Yellow Pasque on 2011-02-08
@WinRiddance: If you write code, you should really know how to execute a script. Don't open it in a text editor. Download it, open terminal:
```
cd <wherever you downloaded it>
tar xzf Get64bitFlash-0.3.3.tar.gz
chmod +x Get64bitFlash
./Get64bitFlash
```

---

### Post by WinRiddance on 2011-02-08
Well now, there's dozens of different types of code ... perhaps I'm just not writing what you're writing and as an ex windows user I'm still learning a lot about Ubuntu too. My (Komodo) code editor just opens by default, didn't have it set up to do that for this particular type of file, but it did.

I guess it's irrelevant though because I still went and checked with the adobe site and according to that adobe page my numbers are the same in their verification check as in the posted current linux version. I'm still convinced that my problems have more to do with the fact that it's a laptop with lousy ATI drivers. Thanks anyway.

---

### Post by Thonixx on 2011-02-09
I don't know if it is known, but there is a PPA available for installing the flashplugin64-installer deb package.

It's very useful and it serves the Flash player 10.2.

With the following commands you add the PPA and install the plugin (64bit) for every browser.

```
sudo add-apt-repository ppa:sevenmachines/flash && sudo apt-get update && sudo apt-get install flashplugin64-installer
```

---

### Post by Astronaut11 on 2011-03-17
Is there any particularly strong reason to force me to sign up, just so I can download Get64bitFlash-0.3.3.tar.gz rather than list the script in a forum message just like this:

```
#!/bin/bash

## First we make the working directory
sudo mkdir -p /tmp/pluginstall &> /dev/null

#choose version of ubuntu
#Input code browser
function strinput {
 unset refstr
 echo -n "$1"
 read refstr
}

## Ask if they agree to file bug reports, sort of a reminder
echo
echo "This script is used to setup 64-bit Adobe Flash 10 Square."
echo ""
echo "By downloading the software listed below, I acknowledge that I have read and agreed to the terms of the Flash Player 'Square' License, the Adobe.com Terms of Use and the Adobe Online Privacy Policy."
echo "See http://labs.adobe.com/technologies/eula/flashplayer10.html"
echo ""
echo " Do you agree? yes or no : "


if [ "$installtype" = "" ]
then
 echo -n "(please type the whole word in lower case letters)"
 strinput
else
 refstr=$installtype
fi

if [ "$refstr" = "yes" ]
then
 echo "Flash installing."


## First we uninstall and remove all the existing flash packages

# No longer trying to reply nspluginwrapper since Acrobat Reader 9 requires it
#sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo apt-get -y purge flashplugin-nonfree
#sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
sudo rm -f /usr/lib/mozilla/plugins/npwrapper*flash*so
rm -f ~/.mozilla/plugins/*flash*so

## What is current version?
export version="2_p3_64bit_linux_111710"
## Then we make a temp folder and download the new plugin
cd /tmp/pluginstall
sudo wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_$version.tar.gz

## Next we extract and place the plugin
sudo tar xvf flashplayer10_$version.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -s /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/

echo "Please restart Firefox to enable Flash"

elif [ "$refstr" = "no" ]
then
 echo "I am sorry but you have to agree. "

else
 echo  " I am sorry but you have to agree. "
 echo
fi

```

It works well by the way.  Thanks.

---

### Post by Yellow Pasque on 2011-03-18
> Is there any particularly strong reason to force me to sign up, just so I can download Get64bitFlash-0.3.3.tar.gz rather than list the script in a forum message just like this

It's generally faster/easier to direct n00bs with a clickable link and commands than it is with copy/paste, open text editor, etc. It also takes less screen space..

At any rate, welcome to ubuntuforums, anonymous leech (don't take it personally as I leech sites too). Don't lose your password because you just may want to ask a question someday... ;)

---

### Post by Jenga-kun on 2011-04-13
I installed flash via the command prompts in the Comprehensive Multimedia and Video Howto thread. My questions are is the version of flash provided in this thread better than the one in the other thread, and if so should I uninstall or purge my previously installed version of flash before I install this one?

---

### Post by Yellow Pasque on 2011-04-13
> **Jenga-kun said:**
> is the version of flash provided in this thread better than the one in the other thread, and if so should I uninstall or purge my previously installed version of flash before I install this one?

Yes, it's better if you're running 64-bit OS/browser, and you should definitely uninstall the old one.

---

### Post by LenW on 2011-04-13
Does this procedure also apply to Firefox 4 ?
How about the sevenmachines PPA ?

---

### Post by michael37 on 2011-04-13
> **LenW said:**
> Does this procedure also apply to Firefox 4 ?
How about the sevenmachines PPA ?

Works with Firefox 4.

Sevenmachines PPA provides essentially the same functionality as this script. Choose either -- you don't need both.

---

### Post by LenW on 2011-06-30
I'm having trouble with Firefox 5:
 - Flash setup from this thread works fine on 
    FF 3.6.18  (Ubuntu Lucid - 10.04)
 - Testing new FF versions 4.0.1 and 5.0 with the 
    Foxtester add-on.
 - For both , <install-dir>/plugins is symlinked to 
    /usr/lib/mozilla/plugins/ 
 - testing Flash with  
    [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)
 - Works fine with 3.6.18 and 4.0.1  
    (flash player 10,3,162,29)
 - Under FF 5.0, I get "Click here to download   
    plugin".
Any suggestions?
-LenW

---

### Post by Gotisch on 2011-07-02
Rere(probably rerere)requested my many times forgotten password just to say thanks to Astronaut11
(and thread maintainer of course :P)
I hate those "register to download only single small text file you want" sites.

---

### Post by LenW on 2011-07-15
To update [my report on FF 5]("http://ubuntuforums.org/showthread.php?t=1358591&page=13#postcount10997264"),
  (in case anyone is interested):

I just got an automatic update from sevenmachines: 
    11.0.1.60-0ubuntu0~sevenmachines4

I tested this against 3 versions of Firefox 
   and got the same results as before:
The Flash test works for FF 3.6.18  and 4.0.1 
    but not 5.0 .
I then noticed and installed a new FF: 5.0.1 
    and now the Flash test works.

---------------------------
Are there any reasons to be cautious of this new
Flash plugin, ver 11,0,1,60 ?

-LenW

---

### Post by michael37 on 2011-07-18
> **LenW said:**
> 
Are there any reasons to be cautious of this new
Flash plugin, ver 11,0,1,60 ?

-LenW

Not much, it's a new beta version. 

Updated instructions to point to the new version.

---

### Post by joelgsf on 2011-09-04
Very good script. It did worked for me, but installed flash version 9.0 r999, not version 10. I don't know if it is due to the version installed, but it is not working with Youtube. Any hints?
TIA,

  Joel Guilherme

---

### Post by Darktl on 2011-09-09
Hi! Today i have installed flash, but the script in the first post is outdated, so here is the one that works:


#!/bin/bash

## First we make the working directory
sudo mkdir -p /tmp/pluginstall &> /dev/null

#choose version of ubuntu
#Input code browser
function strinput {
 unset refstr
 echo -n "$1"
 read refstr
}

## Ask if they agree to file bug reports, sort of a reminder
echo
echo "This script is used to setup 64-bit Adobe Flash 10 Square."
echo ""
echo "By downloading the software listed below, I acknowledge that I have read and agreed to the terms of the Flash Player 'Square' License, the Adobe.com Terms of Use and the Adobe Online Privacy Policy."
echo "See http://labs.adobe.com/technologies/eula/flashplayer10.html"
echo ""
echo " Do you agree? yes or no : "


if [ "$installtype" = "" ]
then
 echo -n "(please type the whole word in lower case letters)"
 strinput
else
 refstr=$installtype
fi

if [ "$refstr" = "yes" ]
then
 echo "Flash installing."


## First we uninstall and remove all the existing flash packages

# No longer trying to reply nspluginwrapper since Acrobat Reader 9 requires it
#sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo apt-get -y purge flashplugin-nonfree
#sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
sudo rm -f /usr/lib/mozilla/plugins/npwrapper*flash*so
rm -f ~/.mozilla/plugins/*flash*so

## What is current version?
[http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11/flashplayer11_rc1_install_lin_64_090611.tar.gz](http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11/flashplayer11_rc1_install_lin_64_090611.tar.gz)

export version="11_rc1_install_lin_64_090611"
## Then we make a temp folder and download the new plugin
cd /tmp/pluginstall
sudo wget http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11/flashplayer$version.tar.gz

## Next we extract and place the plugin
sudo tar xvf flashplayer$version.tar.gz libflashplayer.so
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -s /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/

echo "Please restart Firefox to enable Flash"

elif [ "$refstr" = "no" ]
then
 echo "I am sorry but you have to agree. "

else
 echo  " I am sorry but you have to agree. "
 echo
fi

---

### Post by michael37 on 2011-10-06
True, my post was running stale as there were many other instructions on the web. Many of them are completely wrong now, since Flash 11 was released. I found working instructions and just updated my post with LATEST AND GREATEST Adobe Flash version 11 release. 

Make sure you update as this version fixes a number of issues.

:guitar:

---

### Post by LenW on 2011-10-06
For the first time since I have been following this, the official Adobe page,
[http://www.adobe.com/software/flash/about](http://www.adobe.com/software/flash/about)
shows the same version as the one discussed in this thread.
In fact, it lists the latest version for ALL platforms as 11.0.1.152 .

Any significance to this development?

(BTW, this module is dated 2011-09-23, but sevenmachines is still
  at  11.0.1.129-0ubuntu0~sevenmachines1  , dated 2011-09-09 )

---

### Post by casperfelix on 2011-10-12
Just ran the original script described as 'experimental' on my Lucid/AMD64 which has had flash problems every now and again - and plenty of fixes used on it over the last year or so - and it worked a treat, and I'm being told "You have version 11,0,1,152 installed". 
Until the next time!

---

### Post by mockingbird on 2011-10-24
I have Firefox 8 B4 installed, and I'm getting repeated crashes with .0.152 flash 64...

Would switching to trunk 10.0 help me?

---

### Post by mockingbird on 2011-10-24
Nope...  Installed 10.0 trunk and I'm still having the crashes.

Using **K**ubuntu 11.10...  Video card is nVidia 6600 with 290.03 drivers from PPA.

Can someone confirm please?  This combination works fine with FF 8.0 in Windows.

---

### Post by mockingbird on 2011-10-31
Latest 11.2 64-Bit beta fixed the crashing.

---

### Post by LenW on 2011-11-10
My Update Manager failed to fetch the 'lucid' Packages.gz file for flash,
[http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)
Furthermore all the listings for flashplugin64-nonfree at
[https://launchpad.net/~sevenmachines/+ppa-packages](https://launchpad.net/~sevenmachines/+ppa-packages) 
are marked (DEPRECATED) and seem to be unavailable.

Is the sevenmachines PPA out of the Flash business?
Is there another way 64-bit Flash can be maintained with APT?

---

### Post by michael37 on 2011-11-12
> **LenW said:**
> My Update Manager failed to fetch the 'lucid' Packages.gz file for flash,
[http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)
Furthermore all the listings for flashplugin64-nonfree at
[https://launchpad.net/~sevenmachines/+ppa-packages](https://launchpad.net/~sevenmachines/+ppa-packages) 
are marked (DEPRECATED) and seem to be unavailable.

Is the sevenmachines PPA out of the Flash business?
Is there another way 64-bit Flash can be maintained with APT?

That is absolutely correct. Adobe Flash now provides *OFFICIAL* flash with no funky scripting required.

Simply uninstall flash that you installed from sevenmachines, type 
```
sudo rm /usr/lib/mozilla/plugins/libflashplayer.so
```
and then

```
sudo apt-get update && sudo apt-get install adobe-flashplugin
```

---

### Post by Kubunu on 2011-11-12
> **michael37 said:**
> 
```
sudo rm /usr/lib/mozilla/plugins/libflashplayer.so
```and then

```
sudo apt-get update && sudo apt-get install adobe-flashplugin
```


I tried the above but I get the message :

package adobe-flashplugin is not available,but is refered to by another package.

---

### Post by michael37 on 2011-11-12
> **Kubunu said:**
> I tried the above but I get the message :

package adobe-flashplugin is not available,but is refered to by another package.

You can try clicking on this link:
[apt:adobe-flashplugin?channel=$distro-partner]("apt:adobe-flashplugin?channel=$distro-partner")

If that doesn't work, enable Canonical partner repository in System->Administration->Software Sources manually.

---

### Post by jtbo on 2011-11-29
> **michael37 said:**
> You can try clicking on this link:
[apt:adobe-flashplugin?channel=$distro-partner]("apt:adobe-flashplugin?channel=$distro-partner")

If that doesn't work, enable Canonical partner repository in System->Administration->Software Sources manually.

There is no hope if using 9.10 Karmic, everything official is 404, rest say error or failed, only hope is to get that package downloaded from some other place and install it manually. However instrucionts for that require copying flashplugin.so (or whatever it was called) to ~/.mozilla/plugins folder which does not exists, so no chanche there either.

Script was nice as with that it was possible to get flash to older distros too. 

It is quite frustrating how distros are killed after few years use, there should be some smarter way for this, change to p2p distribution or something else, looking going back to windows soon as constant several months of rebuilding to get everything running again because of forced upgrade is really not my cup of tea.

---

### Post by michael37 on 2011-11-30
> **jtbo said:**
> There is no hope if using 9.10 Karmic, everything official is 404, rest say error or failed, only hope is to get that package downloaded from some other place and install it manually. However instrucionts for that require copying flashplugin.so (or whatever it was called) to ~/.mozilla/plugins folder which does not exists, so no chanche there either.

Script was nice as with that it was possible to get flash to older distros too. 

It is quite frustrating how distros are killed after few years use, there should be some smarter way for this, change to p2p distribution or something else, looking going back to windows soon as constant several months of rebuilding to get everything running again because of forced upgrade is really not my cup of tea.

Not sure why you are complaining about 9.10. Ubuntu release schedule is published nearly 5 years in advance.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

If you don't want to upgrade for long time, run LTS version: either 10.04 LTS through April 2013 or wait till 12.04 LTS which will probably run through 2017.

---

### Post by LenW on 2012-01-04
Is there a trick to running PBS videos, such as 
   [http://www.pbs.org/programs/live-from-lincoln-center/](http://www.pbs.org/programs/live-from-lincoln-center/)
or [http://www.pbs.org/wgbh/nova/physics/fabric-of-cosmos.html](http://www.pbs.org/wgbh/nova/physics/fabric-of-cosmos.html)  ?

All I get is a black rectangle where the video should be.
Note that this simple Flash item works (as does YouTube): 
       [http://www.pbs.org/wgbh/nova/body/map-human-heart.html](http://www.pbs.org/wgbh/nova/body/map-human-heart.html)
    
I am running Ubuntu 10.04 (64-bit), Firefox  7.0.1,  flash 11.1.102.55
(Same results with FF 9.0.1 under FirefoxTester)

---

### Post by michael37 on 2012-01-04
> **LenW said:**
> Is there a trick to running PBS videos, such as 
   [http://www.pbs.org/programs/live-from-lincoln-center/](http://www.pbs.org/programs/live-from-lincoln-center/)
or [http://www.pbs.org/wgbh/nova/physics/fabric-of-cosmos.html](http://www.pbs.org/wgbh/nova/physics/fabric-of-cosmos.html)  ?

All I get is a black rectangle where the video should be.
Note that this simple Flash item works (as does YouTube): 
       [http://www.pbs.org/wgbh/nova/body/map-human-heart.html](http://www.pbs.org/wgbh/nova/body/map-human-heart.html)
    
I am running Ubuntu 10.04 (64-bit), Firefox  7.0.1,  flash 11.1.102.55
(Same results with FF 9.0.1 under FirefoxTester)

That's exactly the config I have, and it works for me fine. Try disabling add-ons etc.

---

### Post by LenW on 2012-01-05
> **michael37 said:**
> That's exactly the config I have, and it works for me fine. Try disabling add-ons etc.

- I have a test FF profile with NO add-ons enabled.
- I have tried to follow the new simplified installation instructions (just apt-get),
- and even used the clean-up script.
No change in any results.

I extracted this URL from the PBS source:
 [http://video.pbs.org/widget/partnerplayer/2182002440/?w=512&h=288&chapterbar=False&autoplay=False](http://video.pbs.org/widget/partnerplayer/2182002440/?w=512&h=288&chapterbar=False&autoplay=False)
Does it work for you?

Any other ideas on what to try?

---

### Post by michael37 on 2012-02-22
11.2 will be the last 64-bit Firefox Flash version, although security updates will be available for 5 years.

New versions of Flash will be available only in Google Chrome browser.

[http://www.h-online.com/open/news/item/Chrome-only-future-for-Flash-on-Linux-1440104.html](http://www.h-online.com/open/news/item/Chrome-only-future-for-Flash-on-Linux-1440104.html)

---

### Post by LenW on 2012-03-16
Regarding my problem with PBS videos - see reply #408 -
I have never figured out what caused this problem.  But now, moving to
Firefox 11.0, it finally works.  I am now running Flash 11,1,102,63 .

---

### Post by azrobinr on 2012-04-18
> **michael37 said:**
> Adobe EULA mentions absolutely nothing about commercial vs non-commercial use.  It says that redistribution is illegal.  Sevenmachines redistributes Adobe software, thus, what he is doing is illegal.

Look, I would MUCH prefer if Adobe Flash was open source software and I was able to redistribute it under GPL.  But I can't, and I have to respect rights of software authors that a large number of end users on this board is apparently enjoying.

Just read the Adobe Flash EULA today, and the section that defines restrictions on the encoding make it look like things have changed...

4.1.2 H.264/AVC Software Encoding. The H.264/AVC software encoding functionality available in the 
Adobe Runtimes is licensed solely for personal, non-commercial use. For more information on 
obtaining the right to use the H.264/AVC software encoding functionality for commercial purposes, 
please refer to [http://www.adobe.com/go/licensing](http://www.adobe.com/go/licensing).

---

