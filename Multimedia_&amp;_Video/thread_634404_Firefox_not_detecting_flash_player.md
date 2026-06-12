---
title: "Firefox not detecting flash player"
date: 2007-12-07
forum: Multimedia &amp; Video
---

### Post by Schalken on 2007-12-07
I've installed the package "flashplugin-nonfree" and restarted my computer, however when Firefox detects flash media on a page it still says "Additional plugins are required to display all media on this page."

So I proceed to install the plugin via Firefox's built in method, selecting Ubuntu's nonfree flash player, and it says "The package flashplugin-nonfree is already installed." If it's already installed then how come it can't use it?

---

### Post by Dynaflow on 2007-12-07
I got the same thing last night.  I believe Ubuntu downloads the plugin directly from Adobe, via Synaptic.  Based on my attempts to work around it last night, this seems to be a problem on Adobe's end, and hopefully they'll get it sorted out soon.  Until then, find an older version of Flash or just wait it out.

---

### Post by mouseboyx on 2007-12-07
you have to get this from adobe
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&ogn=EN_US-gntray_dl_getflashplayer](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&ogn=EN_US-gntray_dl_getflashplayer)

and put the .so file here

/usr/lib/firefox/plugins/

---

### Post by ameba on 2007-12-07
how

---

### Post by melojo on 2007-12-07
this link worked for me [http://ubuntuforums.org/showthread.php?t=632107](http://ubuntuforums.org/showthread.php?t=632107)
I had to create the plugins directory because one was not there. 

If you don't have permission to some directories and you are using nautilis to move files
try sudo nautilus.

---

### Post by Schalken on 2007-12-08
> **Dynaflow said:**
> I got the same thing last night.  I believe Ubuntu downloads the plugin directly from Adobe, via Synaptic.  Based on my attempts to work around it last night, this seems to be a problem on Adobe's end, and hopefully they'll get it sorted out soon.  Until then, find an older version of Flash or just wait it out.

You appear to be right. This is the output I get when trying to install flashplugin-nonfree via either Firefox, or a package manager (note the last two lines):
```
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 108702 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb) ...
Setting up flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) ...
Downloading...
--18:25:23--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 122.252.42.70
Connecting to fpdownload.macromedia.com|122.252.42.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,036,127 (2.9M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%   52.73 KB/s
   50K .......... .......... .......... .......... ..........  3%   52.70 KB/s
  100K .......... .......... .......... .......... ..........  5%   52.67 KB/s
  150K .......... .......... .......... .......... ..........  6%   52.71 KB/s
  200K .......... .......... .......... .......... ..........  8%   53.72 KB/s
  250K .......... .......... .......... .......... .......... 10%   51.97 KB/s
  300K .......... .......... .......... .......... .......... 11%   52.25 KB/s
  350K .......... .......... .......... .......... .......... 13%   53.40 KB/s
  400K .......... .......... .......... .......... .......... 15%   52.18 KB/s
  450K .......... .......... .......... .......... .......... 16%   52.06 KB/s
  500K .......... .......... .......... .......... .......... 18%   52.24 KB/s
  550K .......... .......... .......... .......... .......... 20%   53.49 KB/s
  600K .......... .......... .......... .......... .......... 21%   52.23 KB/s
  650K .......... .......... .......... .......... .......... 23%   51.92 KB/s
  700K .......... .......... .......... .......... .......... 25%   52.25 KB/s
  750K .......... .......... .......... .......... .......... 26%   53.40 KB/s
  800K .......... .......... .......... .......... .......... 28%   52.24 KB/s
  850K .......... .......... .......... .......... .......... 30%   52.01 KB/s
  900K .......... .......... .......... .......... .......... 32%   53.63 KB/s
  950K .......... .......... .......... .......... .......... 33%   51.99 KB/s
 1000K .......... .......... .......... .......... .......... 35%   52.25 KB/s
 1050K .......... .......... .......... .......... .......... 37%   52.02 KB/s
 1100K .......... .......... .......... .......... .......... 38%   53.63 KB/s
 1150K .......... .......... .......... .......... .......... 40%   52.01 KB/s
 1200K .......... .......... .......... .......... .......... 42%   52.24 KB/s
 1250K .......... .......... .......... .......... .......... 43%   53.39 KB/s
 1300K .......... .......... .......... .......... .......... 45%   52.24 KB/s
 1350K .......... .......... .......... .......... .......... 47%   51.99 KB/s
 1400K .......... .......... .......... .......... .......... 48%   52.04 KB/s
 1450K .......... .......... .......... .......... .......... 50%   53.64 KB/s
 1500K .......... .......... .......... .......... .......... 52%   52.01 KB/s
 1550K .......... .......... .......... .......... .......... 53%   52.22 KB/s
 1600K .......... .......... .......... .......... .......... 55%   53.39 KB/s
 1650K .......... .......... .......... .......... .......... 57%   52.24 KB/s
 1700K .......... .......... .......... .......... .......... 59%   51.93 KB/s
 1750K .......... .......... .......... .......... .......... 60%   52.24 KB/s
 1800K .......... .......... .......... .......... .......... 62%   53.39 KB/s
 1850K .......... .......... .......... .......... .......... 64%   52.25 KB/s
 1900K .......... .......... .......... .......... .......... 65%   52.01 KB/s
 1950K .......... .......... .......... .......... .......... 67%   52.24 KB/s
 2000K .......... .......... .......... .......... .......... 69%   53.40 KB/s
 2050K .......... .......... .......... .......... .......... 70%   52.24 KB/s
 2100K .......... .......... .......... .......... .......... 72%   52.01 KB/s
 2150K .......... .......... .......... .......... .......... 74%   53.58 KB/s
 2200K .......... .......... .......... .......... .......... 75%   52.06 KB/s
 2250K .......... .......... .......... .......... .......... 77%   52.22 KB/s
 2300K .......... .......... .......... .......... .......... 79%   52.02 KB/s
 2350K .......... .......... .......... .......... .......... 80%   53.63 KB/s
 2400K .......... .......... .......... .......... .......... 82%   52.01 KB/s
 2450K .......... .......... .......... .......... .......... 84%   52.25 KB/s
 2500K .......... .......... .......... .......... .......... 86%   53.38 KB/s
 2550K .......... .......... .......... .......... .......... 87%   52.17 KB/s
 2600K .......... .......... .......... .......... .......... 89%   51.99 KB/s
 2650K .......... .......... .......... .......... .......... 91%   52.23 KB/s
 2700K .......... .......... .......... .......... .......... 92%   53.39 KB/s
 2750K .......... .......... .......... .......... .......... 94%   52.09 KB/s
 2800K .......... .......... .......... .......... .......... 96%   52.07 KB/s
 2850K .......... .......... .......... .......... .......... 97%   52.23 KB/s
 2900K .......... .......... .......... .......... .......... 99%   53.40 KB/s
 2950K .......... ....                                       100%   52.65 KB/s

18:26:20 (52.53 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.



```

Why would the MD5sum be wrong? Is the package comparing it to the MD5sum of a previous version? What's wrong with the version downloaded from Adobe?

I'm using the version that the package tried to download, [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz) , and it works fine! Does the package need to be updated to use a new MD5sum?

---

### Post by Beernut on 2007-12-08
> **mouseboyx said:**
> you have to get this from adobe
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&ogn=EN_US-gntray_dl_getflashplayer](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&ogn=EN_US-gntray_dl_getflashplayer)

and put the .so file here

/usr/lib/firefox/plugins/

This worked for me.  I ran the installer and used /usr/lib/firefox/ as the install directory.

---

### Post by henriquemaia on 2007-12-08
I had this too. I normally use a userspace firefox installation, but now I was just trying to keep things as default as possible. However, I had to install the flash plugin by hand. Is there any report on lanchpad about this issue?

---

### Post by daradib on 2007-12-08
This is a very recent bug, caused by Adobe's update of Flash 9.0 update 3 (9.0.115.0) codename "Moviestar" on December 4th.

[http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html](http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html)

This causes Ubuntu to not install the flash plugin, detecting a change in the flash plugin installer file (via MD5 checksums). See [bug 173890]("http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890"). This bug has been fixed in the next release of Ubuntu (Hardy 8.04) and it should soon come as an update to Ubuntu 7.10.

If you want an immediate fix, do the following.

Using Synaptic Package Manager, remove the package flashplugin-nonfree.

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree

Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

If you have 64-bit Ubuntu, you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)

---

### Post by Dynaflow on 2007-12-08
> **daradib said:**
> ...

If you have 64-bit Ubuntu, you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)

64-bit users now have a .deb of their own: [http://launchpadlibrarian.net/10804892/flashplugin-nonfree_9.0.115.0ubuntu2_amd64.deb]("http://launchpadlibrarian.net/10804892/flashplugin-nonfree_9.0.115.0ubuntu2_amd64.deb")

---

### Post by daradib on 2007-12-08
> **Dynaflow said:**
> 64-bit users now have a .deb of their own: [http://launchpadlibrarian.net/10804892/flashplugin-nonfree_9.0.115.0ubuntu2_amd64.deb]("http://launchpadlibrarian.net/10804892/flashplugin-nonfree_9.0.115.0ubuntu2_amd64.deb")

May I ask where that package came from. It does not appear anywhere in official Ubuntu repositories. Oh wow. I'm a fool. That was the package I put up (I'm Cyrus Jones). I recommend that you build the packages yourself, however, because you should exercise caution when downloading a random package (the source package is trusted as it is from an included Hardy source package) since that lets anything be executed that the creator of the package made (and possibly malicious).

---

### Post by bazanime on 2007-12-08
> **Dynaflow said:**
> 64-bit users now have a .deb of their own: [http://launchpadlibrarian.net/10804892/flashplugin-nonfree_9.0.115.0ubuntu2_amd64.deb]("http://launchpadlibrarian.net/10804892/flashplugin-nonfree_9.0.115.0ubuntu2_amd64.deb")

Awesome. I can confirm that this works wonders and so far i haven't seen anything malicious.   Just make sure you uninstall Gnash through Synaptic Package Manager ((SPM)..... just search for gnash in SPM search and then select the three instances of gnash for removal.

---

### Post by Schalken on 2007-12-09
That 64bit ubuntu package worked a treat, thanks **daradib**! :D

It looks like we have to get our flash packages from hardy until the feisty ones are updated.

---

### Post by jimmj43 on 2007-12-09
Rats! It's late and I'm rushing and I forgot the nic of the poster who provided links for 32-bit and 64-bit flash gizmos.

As you might have guessed, I'm a retarded noob, so would someone mind telling me HOW to install that 32-bit flash gizmo I downloaded?  <--In click-by-click steps rather than code if possible. I've already removed the resident installer to make room for it.

Sidenote questions: Based on what I've read, the resident gizmo is nothing more than an INSTALLER - that once installed you still have to go "out there" and D/L the actual flash player. The question here is whether that's still the case - the 32-bit gizmo is simply a repaired version of the resident one that's not up to the task? In the event that IS the case, can someone provide lead-the-pathetic-noob-by-his-nose instricktions on HOW to poperly introduce the installer package to the player package so they'll play nice together and let me watch Youtube? Both packages are resting as icons on my desktop.

Thanks!

---

### Post by Dynaflow on 2007-12-09
> **jimmj43 said:**
> Rats! It's late and I'm rushing and I forgot the nic of the poster who provided links for 32-bit and 64-bit flash gizmos.

As you might have guessed, I'm a retarded noob, so would someone mind telling me HOW to install that 32-bit flash gizmo I downloaded?  <--In click-by-click steps rather than code if possible. I've already removed the resident installer to make room for it.

Sidenote questions: Based on what I've read, the resident gizmo is nothing more than an INSTALLER - that once installed you still have to go "out there" and D/L the actual flash player. The question here is whether that's still the case - the 32-bit gizmo is simply a repaired version of the resident one that's not up to the task? In the event that IS the case, can someone provide lead-the-pathetic-noob-by-his-nose instricktions on HOW to poperly introduce the installer package to the player package so they'll play nice together and let me watch Youtube? Both packages are resting as icons on my desktop.

Thanks!

Okay, so if you've [downloaded the .deb]("http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb") file for 32-bit (aka i386) systems and it's sitting on your desktop, you're ever so close to having the wonders of YouTube at your fingertips again.

Though I cringe at the association, .deb files are a lot like .exe files in that other, slightly more popular operating system.  Double-click the thing, follow the instructions, and it'll do its thing.  Before doing so with this particular .deb file, go into System -> Administration -> Synaptic Package Manager and search for flashplugin-nonfree.  If its checkbox is green, right-click it, select "Remove completely," and hit Apply.  Then double-click your desktop .deb and away you go.

If you're still not seeing Flash, your problem may be that you've chosen Gnash as your default Flash player, even though it can only play stuff from Flash 7 on down, I believe.  The simplest way to solve this problem is to look for it in Synaptic the same way you looked for flashplugin-nonfree and get rid of it, at least temporarily.  Though the open-source Gnash is much more honorable and saintly than the non-free Flash plugin, it currently has a terrible time playing the newest, and even new'ish, Flash-based content, so if it's your default player, you will have a terrible time trying to view that kind of content too.  See [this thread]("http://ubuntuforums.org/showthread.php?t=634574").

---

### Post by daradib on 2007-12-09
> **Dynaflow said:**
> Okay, so if you've [downloaded the .deb]("http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb") file for 32-bit (aka i386) systems and it's sitting on your desktop, you're ever so close to having the wonders of YouTube at your fingertips again.

Though I cringe at the association, .deb files are a lot like .exe files in that other, slightly more popular operating system.  Double-click the thing, follow the instructions, and it'll do its thing.  Before doing so with this particular .deb file, go into System -> Administration -> Synaptic Package Manager and search for flashplugin-nonfree.  If its checkbox is green, right-click it, select "Remove completely," and hit Apply.  Then double-click your desktop .deb and away you go.

If you're still not seeing Flash, your problem may be that you've chosen Gnash as your default Flash player, even though it can only play stuff from Flash 7 on down, I believe.  The simplest way to solve this problem is to look for it in Synaptic the same way you looked for flashplugin-nonfree and get rid of it, at least temporarily.  Though the open-source Gnash is much more honorable and saintly than the non-free Flash plugin, it currently has a terrible time playing the newest, and even new'ish, Flash-based content, so if it's your default player, you will have a terrible time trying to view that kind of content too.  See [this thread]("http://ubuntuforums.org/showthread.php?t=634574").

Well said. :guitar:

---

### Post by jimmj43 on 2007-12-09
WOO-HOO! I got YouTube!!

Thanks, guys. :)


Assuming the "video" tag is still on-topic, I need to change horses: I have VLC installed but it won't play mpeg vids. In days gone past I learned to use MediaPlayerClassic for nearly everything vid in Windoze. If I need a codec, I just went out and got it. Does VLC work similarly?  How can I make VLC play mpegs - and for that matter, pretty much any other vid format I might encounter, such as AVI and REAL, and DivX, and.....?

---

### Post by daradib on 2007-12-09
> **jimmj43 said:**
> Assuming the "video" tag is still on-topic, I need to change horses: I have VLC installed but it won't play mpeg vids. In days gone past I learned to use MediaPlayerClassic for nearly everything vid in Windoze. If I need a codec, I just went out and got it. Does VLC work similarly?  How can I make VLC play mpegs - and for that matter, pretty much any other vid format I might encounter, such as AVI and REAL, and DivX, and.....?

Well I am not to experienced with VLC. However, I do recommend using Totem to play multimedia content. It does not have MPEG support out of the box. See the Ubuntu Community Documentation article [RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats") and [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") for more information to add extra codec support to Totem.

---

### Post by daradib on 2007-12-09
VLC should already have MPEG support, nothing must be done except for installing VLC itself via the vlc package in Synaptic.

---

### Post by robert114 on 2007-12-09
daradib's thanks you solved the problem!

---

### Post by jimmj43 on 2007-12-09
> **daradib said:**
> VLC should already have MPEG support, nothing must be done except for installing VLC itself via the vlc package in Synaptic.

Why am I reminded of the "Dilbert" cartoon strip? ^That^ is exactly the kind of answers I used to get from the chief engineer at the company I worked for. [I]"It SHOULD work["/I] fails to address the problem: It DOESN'T work.

Just for drill I'll uninstall VLC, then reinstall it, then test it. If it still fails, I'll try the alternate approach offered.

Thanks guys! :)

---

### Post by daradib on 2007-12-09
I actually recommend the "alternate" way. VLC has not had a perfect reputation with Ubuntu. Yes, it was funny- "should work".

---

### Post by jimmj43 on 2007-12-10
Item: I HATE being a dunderhead!

Item: Uninstall & reinstall of VLC failed to achieve the desired result.

Item: If/when one is installing a buncha stuff via 'Add/Remove'. one SHOULD pay attention!! 

It was the first or 2 java gizmos where I goofed in the installation process. I missed checking the "agree" box on the terms of agreement, and clicked on "forward". 

Tsk, tsk, tsk... An error message promptly popped up. I closed out the error message and clicked on the "back" button. *sigh*...... Now disabled. Can't go back and click the "agree" box and try again.

Hit the "forward button to continue and was presented with the notification that I'd cleverly managed to break the installer, and.yada, yada... Bottom line: The "add/remove function is now broken and some sites won't load text and...... *sigh*...... There's ANOTHER clean Gutsy install in my immediate future.

---

### Post by xxzeenoxx on 2007-12-10
> **daradib said:**
> This is a very recent bug, caused by Adobe's update of Flash 9.0 update 3 (9.0.115.0) codename "Moviestar" on December 4th.

[http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html](http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html)

This causes Ubuntu to not install the flash plugin, detecting a change in the flash plugin installer file (via MD5 checksums). See [bug 173890]("http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890"). This bug has been fixed in the next release of Ubuntu (Hardy 8.04) and it should soon come as an update to Ubuntu 7.10.

If you want an immediate fix, do the following.

Using Synaptic Package Manager, remove the package flashplugin-nonfree.

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree

Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

If you have 64-bit Ubuntu, you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)

Thanks for the link to the deb package.  worked great...

---

### Post by jimmj43 on 2007-12-10
> **daradib said:**
> Well I am not to experienced with VLC. However, I do recommend using Totem to play multimedia content. It does not have MPEG support out of the box. See the Ubuntu Community Documentation article [RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats") and [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") for more information to add extra codec support to Totem.

Recently, I have been experiencing an unpleasant trend: Routine upgrades that cripple the OS, and add/remove packages that wreck the entire add/remove function!

I'm currently running my 4th clean install of Gutsy is just the past two days. The first two 'do-overs' were prompted when downloading/installing routine updates crasher the add/remove function and caused a variety of seemingly unrelated glitches, It may be notable that months of using Feisty saw only a single such incident - routine upgrades broke the OS, which is what provoked me to go to Gutsy. The first two Gutsy installs crashed (to varying degrees) only upon attempting to D/L & install routine upgrades. #3 crash resulted after totally avoiding routine upgrades after the install, then grappling with video issues. Now on the 4th install, and still without updates, and still grappling with video issues... I'm STILL grappling with video issues. I'm sensing the presence of a black hole / "Catch-22 " - video player(s) aren't gonna work unless the upgrades are installed, and the upgrades break the OS. :confused:

I went looking for Totem after a failed attempt to use VLC as a video player. Couldn't find it. After expanding to 'All available applications', I looked in"All",  "sound & video", "other", and "Accessories" to no avail. So then I thought to myself, "Well, maybe it's in the "restricted formats" package", so set about to install it.

ERROR!

An error occured
The following details are provided

E: /var/cache/apt/archives/libmp4v2-0_2.0.0+cvs20040908+mp4v2bmp-Obuntu5_i386.deb: unable to fsync updated status of 'libmp4v2-0'

Closed that one and was met with another listing a double:

E:Error: could not create log directory /root/synaptic/log/-mkdir (read-only file system)

E: Failed to write commit log

*sigh*

I wonder f MediaPlayerClassic has a version that'll run in Linux...  Am I doomed to hobble around on the 'wine' crutch? :confused:

---

### Post by misfitpierce on 2007-12-10
If you have 64 bit you put .so file anywhere your going to KEEP it and do this in terminal

nspluginwrapper -i /PATH/TO/.SO

---

### Post by daradib on 2007-12-10
> **jimmj43 said:**
> Recently, I have been experiencing an unpleasant trend: Routine upgrades that cripple the OS, and add/remove packages that wreck the entire add/remove function!

I'm currently running my 4th clean install of Gutsy is just the past two days. The first two 'do-overs' were prompted when downloading/installing routine updates crasher the add/remove function and caused a variety of seemingly unrelated glitches, It may be notable that months of using Feisty saw only a single such incident - routine upgrades broke the OS, which is what provoked me to go to Gutsy. The first two Gutsy installs crashed (to varying degrees) only upon attempting to D/L & install routine upgrades. #3 crash resulted after totally avoiding routine upgrades after the install, then grappling with video issues. Now on the 4th install, and still without updates, and still grappling with video issues... I'm STILL grappling with video issues. I'm sensing the presence of a black hole / "Catch-22 " - video player(s) aren't gonna work unless the upgrades are installed, and the upgrades break the OS. :confused:

I went looking for Totem after a failed attempt to use VLC as a video player. Couldn't find it. After expanding to 'All available applications', I looked in"All",  "sound & video", "other", and "Accessories" to no avail. So then I thought to myself, "Well, maybe it's in the "restricted formats" package", so set about to install it.

ERROR!

An error occured
The following details are provided

E: /var/cache/apt/archives/libmp4v2-0_2.0.0+cvs20040908+mp4v2bmp-Obuntu5_i386.deb: unable to fsync updated status of 'libmp4v2-0'

Closed that one and was met with another listing a double:

E:Error: could not create log directory /root/synaptic/log/-mkdir (read-only file system)

E: Failed to write commit log

*sigh*

I wonder f MediaPlayerClassic has a version that'll run in Linux...  Am I doomed to hobble around on the 'wine' crutch? :confused:

First try loading Synaptic (System -> Administration -> Synaptic)

Search for libmp4v2-0. Right-click it and Mark for Complete Removal. Then search for sun java. Do the same thing for the packages sun-java6-bin and sun-java6-jre, as well as for any other packages on the list that start with sun-java.

In Synaptic, go to Edit -> Fix Broken Packages

Go to Custom Filters -> Marked Changes and highlight all those packages, right-click, mark them for Reinstallation.


Try running these commands:
```

sudo apt-get install -f
sudo dpkg --configure -a
```

---

### Post by daradib on 2007-12-10
Please try using Synaptic now instead of Add/Remove Applications. It gives you a lot more software and is more powerful. Hopefully, you can fix your problems without a reinstallation.

---

### Post by daradib on 2007-12-10
For more information on the flashplugin-nonfree bug, see [http://ubuntuforums.org/showthread.php?p=3929669](http://ubuntuforums.org/showthread.php?p=3929669)

---

### Post by secular on 2008-01-19
> **mouseboyx said:**
> you have to get this from adobe
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&ogn=EN_US-gntray_dl_getflashplayer](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&ogn=EN_US-gntray_dl_getflashplayer)

and put the .so file here

/usr/lib/firefox/plugins/


Thanks! Worked for Xubuntu.

---

### Post by jnewm on 2008-01-21
Thanks Daradib (and everyone else who contributed to this post), your fix worked perfectly for me.

---

### Post by 3rdcoast on 2008-01-22
Glad this thread exists,Thanks for .deb link....

---

### Post by daradib on 2008-01-22
No problem. Cheers!

---

