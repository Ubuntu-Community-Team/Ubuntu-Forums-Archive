---
title: "Lucid Lynx Flash update today not working. Version 11.2.202"
date: 2012-03-28
forum: Multimedia Software
---

### Post by ajgreeny on 2012-03-28
I have tried to update my flash plugin today, using both the repository version and the flash-aid version, both of which seem to be v11.2.202.228

The appropriate libflashplayer.so plugin file appears in my filesystem, but it does not work in any manner at all.  Luckily I noticed that the version available in the repos is the same as the beta version that flash-aid has made available for some time, and which I knew does not work on my system using 10.04.  I therefore kept a copy of the older 11.1r102 that does work so could copy that back in place of the 11.2.202, otherwise I would now be without a working flash player.

Has anyone else had the same problem?
I can not believe that I'm the only one that has seen this.  Could it be due to my graphic card, an ATI 9200SE using the OS radeon/ati driver?
Any clues as to how I can overcome this and use the latest plugin?

---

### Post by Peter Donaldson on 2012-03-29
Same with me

---

### Post by cuyo01 on 2012-03-29
I had problems with the last update of flashplayer but for me it worked but the colors of videos were incorrect, also im using opera browser and in some pages with embbeded videos from youtube y can see a "trailing white tail" when srooling the page around the embedded videos, i was used to it before but with the last update the trail becomes longer and the page in general become more sluggish to scroll.

the only solution for me was install the 11.1.102.63 version, looks like the latest flash plugin is broken.

I have a nvidia gt240 card with propietary drivers updated

---

### Post by Skoki on 2012-03-29
It doesn´t work at all (OS ati driver)!

---

### Post by Trockendeck on 2012-03-29
I have the same problem with the new flash plugin. All the colors are screwed up and some videos don't work at all.

Can somebody give an advice on howto install the previous version? I can't even find the previous plugin on the Adobe web site.

---

### Post by Grapevine on 2012-03-29
Everybody looks blue on my vids from now.

I found something on the Adobe bugbase:
[https://bugbase.adobe.com/index.cfm?event=bug&id=3109467]("https://bugbase.adobe.com/index.cfm?event=bug&id=3109467")

---

### Post by shantiq on 2012-03-29
colors quite funked up!     why do they have to release stuff that does not work    Goshhhh     so annoying:KS    [[green filter or blue and changing from one vid to the next all but freezes everything or at least stutters



how to take flashplayer back anyone?   does not let you do it through package/force version in synaptic   [says dependencies etc etc....]



**see . lovely..**   [ATTACH]215105[/ATTACH]


also worse on Opera than on Chrome

---

### Post by mojo risin on 2012-03-29
Same with me. Look two threads below- I used the there suggested flash aid, but it only works with either gnash or the other open source flash.
As usual the service of them is bad, very slow and laggy. I tried getting adobe to work with it but to no avail. must be something wrong with the updated path or whatever.
Also tried rolling back, forcing an earlier version but didnt work.

---

### Post by shantiq on 2012-03-29
**a fix ?**   [has worked on my oneiric setup] if it looks the same on your synaptic try it
i do not know why the second one works and not the first but it simply does


[[IMG]http://img689.imageshack.us/img689/6061/adobeb.th.png[/IMG]](http://img689.imageshack.us/img689/6061/adobeb.png)

---

### Post by alexcckll on 2012-03-29
LAtest update gives me accelerated rendering again on my Lenovo Ideapad S12, but it doesn't allow me to search back in the clip I'm playing without crashing Flash.

Another step forward, though...

---

### Post by Peter Donaldson on 2012-03-29
Bandaid solution-

Extract libflashplayer.so (11.1.102.55) from file downloaded at [http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml]("http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml")[LIST]
[/LIST]



Move libflashplayer.so to folder usr/lib/flashplugin-installer

Worked on the chromium, firefox, seamonkey, midori

---

### Post by cuyo01 on 2012-03-29
you can download older flash versions from here:

[http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html)

in my case downloaded flash player 11.1.102.63 (174MB) its a zip that contains all plugins for all 32 and 64 bit systems with windows, mac, linux, solaris OS's

the README file lists wich file/archive is for what plattaform, in my case /fp_11.1.102.63_archive/11_1r102_63_32bit/flashplayer11_1r102_63_linux.i386.tar.gz wich contains libflashplayer.so.

located all files libflashplayer.so in my hard disk and replaced them with the downloaded one, requires administrator privileges to replace (sudo nautilus)

---

### Post by r.stiltskin on 2012-03-29
> **Peter Donaldson said:**
> Bandaid solution-

Extract libflashplayer.so (11.1.102.55) from file downloaded at [http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml]("http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml")[LIST]
[/LIST]



Move libflashplayer.so to folder usr/lib/flashplugin-installer

Worked on the chromium, firefox, seamonkey, midori
Brilliant.  This worked for chromium and firefox on my 10.05 LTS/old Nvidia system.

---

### Post by Trockendeck on 2012-03-29
> **cuyo01 said:**
> you can download older flash versions from here:

[http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html)

Thank you, works like a charm. 

I just copied the plugin to the "$HOME/.mozilla/plugins" directory. Surprisingly this works for chromium too not just firefox.

---

### Post by garyhehn on 2012-03-29
> **cuyo01 said:**
> you can download older flash versions from here:

[http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html)

in my case downloaded flash player 11.1.102.63 (174MB) its a zip that contains all plugins for all 32 and 64 bit systems with windows, mac, linux, solaris OS's

the README file lists wich file/archive is for what plattaform, in my case /fp_11.1.102.63_archive/11_1r102_63_32bit/flashplayer11_1r102_63_linux.i386.tar.gz wich contains libflashplayer.so.

located all files libflashplayer.so in my hard disk and replaced them with the downloaded one, requires administrator privileges to replace (sudo nautilus)
Thanks cuyo01, your advice worked for me. I simply replaced libflashplayer.so located in /usr/lib/flashplugin-installer/ with the libflashplayer.so from the archive, flashplayer11_1r102_63_linux.i386.tar.gz, that you described. Flash is now working again for me on both Firefox and Chromium.

---

### Post by efflandt on 2012-03-29
Same issues as others.  Most videos from other sources and even ads that precede YouTube videos were fine, but YouTube videos themselves had smurf people and other totally wrong colors.  Flash settings would freeze the settings dialog box and all flash controls, so I could not uncheck hardware acceleration or do anything else with the video other than close the browser.

Not sure if 64-bit 11.10 still uses 32-bit flash with wrapper, but whatever it is from ubuntu-restricted-extras had just updated itself today along with some transitional package.

I used Synaptic to totally remove flashplugin-installer and something else related to flash and manually installed newest same version 64-bit flash using the four-square tar.gz file from Adobe.  Still had smurfs after unchecking hardware acceleration until I closed Firefox and opened it again.  Then YouTube videos looked fine.

PC is in my sig with nvidia DVI to HDMI connected 32" HDTV.

---

### Post by Guinioul on 2012-03-30
> **Peter Donaldson said:**
> Bandaid solution-

Extract libflashplayer.so (11.1.102.55) from file downloaded at [http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml](http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml)


Move libflashplayer.so to folder usr/lib/flashplugin-installer

Worked on the chromium, firefox, seamonkey, midori

It works for me too !
a BIG BIG tanks !!!

---

### Post by BobSongs on 2012-03-30
I'm getting the same "Smurf effect" as everyone else.

What's interesting is the small preview in Youtube. Move the cursor along the bottom of the video's play line and a small courtesy preview appears with the correct colours.

I can't wait... I really cannot wait for Flash to die and finally be replaced by something that's properly optimized. It's lack of optimization is what kept it off the iPod and iPhone.

If you're doing it from the command line, use THIS address:

```
/usr/lib/flashplugin-installer
```

If you're replacing the file using Nautilus, the correct command is:

```
gksudo nautilus
```
and enter your password.

---

### Post by chiron80 on 2012-03-30
> **cuyo01 said:**
> you can download older flash versions from here:

[http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html)

in my case downloaded flash player 11.1.102.63 (174MB) its a zip that contains all plugins for all 32 and 64 bit systems with windows, mac, linux, solaris OS's

the README file lists wich file/archive is for what plattaform, in my case /fp_11.1.102.63_archive/11_1r102_63_32bit/flashplayer11_1r102_63_linux.i386.tar.gz wich contains libflashplayer.so.

located all files libflashplayer.so in my hard disk and replaced them with the downloaded one, requires administrator privileges to replace (sudo nautilus)

Thank cuyo01, your solution worked for me as well.

I also want to add, for anyone out there who may be searching for a solution, this caused HuluDesktop to stop working for me. If I ran it on the command line, it would report "Illegal Instruction"

It is set up on my MythTV FrontEnd, so I was surprised when Hulu Desktop was working just fine one day and then stopped the next (due to an automatic update).

Has anyone filed a bug report about this? Is it limited to older releases, or certain graphics cards?

For the record, I'm running Mythbuntu 10.10 (Maverick). I have an older graphics card: nVidia Corporation NV34 [GeForce FX 5200], with the closed-source NVIDIA driver (version 173). Probably time I upgraded Ubuntu (if not the entire computer).

- Ben

---

### Post by Crazy K on 2012-03-30
> **Peter Donaldson said:**
> Bandaid solution-

Extract libflashplayer.so (11.1.102.55) from file downloaded at [http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml]("http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml")[LIST]
[/LIST]



Move libflashplayer.so to folder usr/lib/flashplugin-installer

Worked on the chromium, firefox, seamonkey, midori

I can't seem to find that folder anywhere on my system. 

By the way, I use Chromium, should that make a difference?

---

### Post by souravc83 on 2012-03-30
Its happening for me only in Youtube. Other flash sites seems to be working fine.
Also, if you go to the fullscreen, this goes away. Also, going fullscreen does not work seamlessly now. Dunno why.

---

### Post by #1 fisherman on 2012-03-30
I just ran update manager and am now having the same problem tried to Move libflashplayer.so to folder usr/lib/flashplugin-installer but an error occured access denied could some one help For I am somewhat new to ubuntu what do i have to do to for permission 
thanks

---

### Post by #1 fisherman on 2012-03-31
guess I figured it out on my own (sudo nautilus) from the other replies,Thanks for the fix worked for me as well instantly

---

### Post by BobSongs on 2012-03-31
> **Crazy K said:**
> I can't seem to find that folder anywhere on my system. 

By the way, I use Chromium, should that make a difference?

Yeah, a slight correction on the location. Put a leading forward slash / before usr like:

```
/usr/lib/flashplugin-installer
```

That should work.

---

### Post by souravc83 on 2012-03-31
For me, the fix worked for firefox, but chrome still shows the blue color on all videos. Do I need to replace the libflashplayer.so in some folder which contains chrome plugins as well?

---

### Post by lovinglinux on 2012-03-31
> **souravc83 said:**
> For me, the fix worked for firefox, but chrome still shows the blue color on all videos. Do I need to replace the libflashplayer.so in some folder which contains chrome plugins as well?

About the blue color issue: [http://ubuntuforums.org/showpost.php?p=11766379&postcount=274](http://ubuntuforums.org/showpost.php?p=11766379&postcount=274)

---

### Post by andrewsjp on 2012-03-31
Same here on two versions of Ubuntu; 10.04 and Xubuntu 11.10.  No flash at all where expected.  This happed when updating to the latest flash security update.

---

### Post by Deevad on 2012-03-31
> **Peter Donaldson said:**
> Bandaid solution-
Extract libflashplayer.so (11.1.102.55) from file downloaded at [http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml]("http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml")[LIST]
[/LIST]
Move libflashplayer.so to folder usr/lib/flashplugin-installer
Worked on the chromium, firefox, seamonkey, midori

Perfect and thanks for the solution Peter. :guitar:
Here all PCs in my family got 10.04 and they reported me the problem today after updates done this week.

( note I tested without success via 'flash aid' extension for firefox : Flash beta / flash stable / Gnash + I tested also everything in Synaptic : force version back / install other package

---

### Post by souravc83 on 2012-03-31
Thanks, LovingLinux. Shutting off the hardware acceleration solved the problem in chrome. Perfect!

---

### Post by ZeroFossilFuel on 2012-03-31
> **BobSongs said:**
> I can't wait... I really cannot wait for Flash to die and finally be replaced by something that's properly optimized. 

I second that motion. :mad:

---

### Post by Crazy K on 2012-03-31
> **BobSongs said:**
> Yeah, a slight correction on the location. Put a leading forward slash / before usr like:

```
/usr/lib/flashplugin-installer
```

That should work.

Seems to be working now. For some people is might show up in this area: 

```
/usr/lib/adobe-flashplugin
```

For me that's where I had to put the file. 

But yeah, I also have Flash control as an extension which might or might not be helping.

---

### Post by tyler.durden on 2012-04-01
I have solved the problem by downgrading to adobe-flashplugin_11.1.102.63. Thanks for idea))

---

### Post by jonbjoseph on 2012-04-01
> **cuyo01 said:**
> you can download older flash versions from here:

[http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html)

in my case downloaded flash player 11.1.102.63 (174MB) its a zip that contains all plugins for all 32 and 64 bit systems with windows, mac, linux, solaris OS's

the README file lists wich file/archive is for what plattaform, in my case /fp_11.1.102.63_archive/11_1r102_63_32bit/flashplayer11_1r102_63_linux.i386.tar.gz wich contains libflashplayer.so.

located all files libflashplayer.so in my hard disk and replaced them with the downloaded one, requires administrator privileges to replace (sudo nautilus)


Video is now working for me on Firefox and Chrome. Thanks for this information.

---

### Post by wb8nbs on 2012-04-01
Problems here also.

Ubuntu 10.04 did a flash upgrade last night and this morning flash would not work for  a streaming radio station. Also noticed some (but not all) youtube videos would not play. Solved with the [cuyo01]("http://ubuntuforums.org/member.php?u=207088") solution, downgraded the libflashplayer.so file to 11.1.R102 from the adobe site.  My system is 32 bit, Athlon XP.

---

### Post by pickarooney on 2012-04-01
I managed to fix this problem with the solution in post 11 (thanks!). Next morning I came in to the living room and my son was watching Antz. I couldn't believe the problem had now shifted to mplayer and I spent five minutes fiddling with various settings before I realised it was actually A Bug's Life.

---

### Post by DavidSwan20 on 2012-04-03
> **Peter Donaldson said:**
> Bandaid solution-

Extract libflashplayer.so (11.1.102.55) from file downloaded at [http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml](http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml)


Move libflashplayer.so to folder usr/lib/flashplugin-installer

Worked on the chromium, firefox, seamonkey, midori

Many thanks. After hours of searching and failed attempts, I found this and it works brilliantly in Chromium.
However, for Firefox I had to also copy libflashplayer.so to /usr/lib/mozilla/plugins.
I don't know if this is because as part of my attempts to fix the problem I had previously used the Firefox Flash-Aid.

---

### Post by lovinglinux on 2012-04-03
> **DavidSwan20 said:**
> Many thanks. After hours of searching and failed attempts, I found this and it works brilliantly in Chromium.
However, for Firefox I had to also copy libflashplayer.so to /usr/lib/mozilla/plugins.
I don't know if this is because as part of my attempts to fix the problem I had previously used the Firefox Flash-Aid.

That's because /usr/lib/mozilla/plugins is in fact the correct location, which is what Flash-Aid uses.

Firefox will first look into /usr/lib/mozilla/plugins and will be redirected to /usr/lib/flashplugin-installer/libflashplayer.so by a series of symbolic links, if it finds a flashplugin-alternative.so instead of libflashplayer.so, which happens if flashplugin-installer is installed.

However, keep in mind you don't need flashplugin-installer. In fact I don't even recommend keeping it when installing flash downloaded manually from Adobe, because in the next update it will be replaced. Just remove flashplugin-installer and extract the libflashplayer.so downloaded from Adobe into /usr/lib/mozilla/plugins.

[Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") can do all that for you as well. Get the flash player version you need from [Adobe](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html). Extract the archive, find the tar.gz file corresponding to your architecture and copy it (don't extract it). Open Flash-Aid Advanced mode, select "Custom" in the installation option, paste the tar.gz path in the field. Click the Script tab, then Execute. Flash-Aid will remove all installed flash versions and install the  one from the tar.gz file in the proper location.

---

### Post by twp on 2012-04-03
Using LovingLinux's method, with flashaid.  It works.  RELIEF!  Now how long do we have to wait for a fix in the update?  Ubuntu 11.10.
Pray for acceptance of the HTML5 video/audio standard. Down with Adobe Flash...

---

### Post by lovinglinux on 2012-04-03
> **twp said:**
> Using LovingLinux's method, with flashaid.  It works.  RELIEF!  Now how long do we have to wait for a fix in the update?  Ubuntu 11.10.
Pray for acceptance of the HTML5 video/audio standard. Down with Adobe Flash...

I would get a comfortable chair to wait for that fix. In fact, I think it won't be fixed. Adobe said they will provide only security patches, so I doubt they will try to fix this. Specially considering their current replies to bug reports: "we don't support Linux anymore".

Anyway, I guess the problem might disappear with Ubuntu updates, since this is an old issue that comes and go.

If the problem continues indefinitely, then the only viable alternative would be to Switch to Chrome when Flash Pepper comes out.

---

### Post by FrankenCub on 2012-04-03
> **Peter Donaldson said:**
> Bandaid solution-

Extract libflashplayer.so (11.1.102.55) from file downloaded at [http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml](http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml)


Move libflashplayer.so to folder usr/lib/flashplugin-installer

Worked on the chromium, firefox, seamonkey, midori

Awesome, I quite watching the Smurfs when I was a child and certainly didn't expect them back. Hmmm, maybe they were Na'vi :lolflag:

---

### Post by nemesisgus on 2012-04-03
I just downgraded to the previous version by uninstalling the updated problematic packages 'adobe-flashplugin' and 'adobe-flash-properties-gtk' (11.2.202.228) and installing the last working version (11.1.102.63). You can download them here: [http://ubuntu.wbac.ac.th/archive-canonical/ubuntu/pool/partner/a/adobe-flashplugin/?C=M;O=D](http://ubuntu.wbac.ac.th/archive-canonical/ubuntu/pool/partner/a/adobe-flashplugin/?C=M;O=D)

Let's see if next updates fix the issue.

@Ubuntu 11.04

---

### Post by robert shearer on 2012-04-03
Big thanks to Lovinglinux..!!  post#37
> Flash-Aid can do all that for you as well. Get the flash player version you need from Adobe. Extract the archive, find the tar.gz file corresponding to your architecture and copy it (don't extract it). Open Flash-Aid Advanced mode, select "Custom" in the installation option, paste the tar.gz path in the field. Click the Script tab, then Execute. Flash-Aid will remove all installed flash versions and install the one from the tar.gz file in the proper location.

I have been struggling for days to restore flash and had almost given up hope but the above method worked superbly..

---

### Post by lovinglinux on 2012-04-03
> **robert shearer said:**
> Big thanks to Lovinglinux..!!  post#37


I have been struggling for days to restore flash and had almost given up hope but the above method worked superbly..

You are welcome.

---

### Post by jjpdijkstra on 2012-04-04
To unsmurf my web-flash I disabled hardware acceleration. I didn't like to do that, though I assume that it will be fixed soon. 

Another (maybe subsequently) odd thing is that there is something off with the buffer/rendering of flash since today. 

You guys probably know why (hardware acceleration right) but flash lags and stutters/ audio sync is off when reaching the end of its buffer. 

I have tried all combinations of adobeflashplugins possible. What do you suggest I should have installed?

flashplugin-installer 11.2.202.228ubuntu1

or 

gnash/lightspark

or 

adobe-flashplugin

or/and

nonfree-extra sound?

---

### Post by Uncertified Welder on 2012-04-04
> **Peter Donaldson said:**
> Bandaid solution-

Extract libflashplayer.so (11.1.102.55) from file downloaded at [http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml](http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml)


Move libflashplayer.so to folder usr/lib/flashplugin-installer

Worked on the chromium, firefox, seamonkey, midori

I have done this and it works for me... as long as I'm logged in as root.  If I use another account it no longer works.  What have I missed?

---

### Post by Johan_D on 2012-04-04
[SIZE=2]A tiny detail from my “adobe flash” travails that might perhaps be of use to someone...[/SIZE]
 

 [SIZE=2]I followed yesterday's clear instruction of NEMESISGUS, installing the last working version 11.1.102.63 of both adobe-flashplugin and adobe-flash-properties-gtk.  When to my surprise this at first did not work, causing the same black video screen on YouTube as before - indicating presence of a certain “sfwdec” player instead of the expected adobe flash - it finally occurred to me to uninstall the package swfdec-mozilla … and voilà - everything now worked!  [/SIZE] 
 

 [SIZE=2](Before realising that the adobe “update” was to blame, over few days I had been installing a lot of unnecessary stuff - including the “toxic” swfdec-mozilla - lest it somehow made up what had been lacking... :-))[/SIZE]
 

 [SIZE=2]The great help from this forum is one of the reasons I stick with Ubuntu.[/SIZE]

---

### Post by lovinglinux on 2012-04-05
> **Johan_D said:**
> [SIZE=2]A tiny detail from my &#8220;adobe flash&#8221; travails that might perhaps be of use to someone...[/SIZE]
 

 [SIZE=2]I followed yesterday's clear instruction of NEMESISGUS, installing the last working version 11.1.102.63 of both adobe-flashplugin and adobe-flash-properties-gtk.  When to my surprise this at first did not work, causing the same black video screen on YouTube as before - indicating presence of a certain &#8220;sfwdec&#8221; player instead of the expected adobe flash - it finally occurred to me to uninstall the package swfdec-mozilla &#8230; and voilà - everything now worked!  [/SIZE] 
 

 [SIZE=2](Before realising that the adobe &#8220;update&#8221; was to blame, over few days I had been installing a lot of unnecessary stuff - including the &#8220;toxic&#8221; swfdec-mozilla - lest it somehow made up what had been lacking... :-))[/SIZE]
 

 [SIZE=2]The great help from this forum is one of the reasons I stick with Ubuntu.[/SIZE]

That is one of the reasons I develop Flash-Aid. It removes, swfdec, gnash, lightspark, adobe flashplugin installed manually and even flash for Windows installed by Wine, so that kind of conflict doesn't happen when you use it. If the user has some weird flash installed somewhere else, the add-on can detect it when generating the report provided by the Help menu, so it makes easier to troubleshoot.

BTW, Adobe has purged the last beta from the server, so Flash-Aid is delivering the nasty 11.2.202.228 version as well. If you are using it and it fails to download flash, click the "Check Upate" button, in the extension menu and wait a few seconds to get a confirmation.

> **Uncertified Welder said:**
> I have done this and it works for me... as long as I'm logged in as root.  If I use another account it no longer works.  What have I missed?

Downgrade flash using [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/"). After installing the extension, get the flash player version you need from [Adobe](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html). Extract the archive, find the tar.gz file corresponding to your architecture and copy it (don't extract it). Open Flash-Aid Advanced mode, select "Custom" in the installation option, paste the tar.gz path in the field. Click the Script tab, then Execute. Flash-Aid will remove all installed flash versions and install the  one from the tar.gz file in the proper location.

---

### Post by ortermagic on 2012-04-05
Hi, I have been without a flash player for a week or more....It first happened after I downloaded a flash update that came up in my update manager  for the 11.10 installation that I had been running successfully for quite some time.
 After the update thingy was installed flash would not work at all. I tried all sots of different ways to get it going again, using the software centre, by downloading the tar gz from the adobe download site etc...
 I tried Flash-aid. again and again. Searched forums...

   Nothing worked. So I decided to do a complete reinstall and revert to Maverick, thinking it had to be yet another buggy issue with Onereic. I tried everything I know,
 (not a lot, I'm a 60's relic nearly 70 years of age)
 I found I still could not get Flash to work within that freshly installed distro (10.10 which used to work okay), still no luck.
Can't understand why it does not go, I have 2 other machines in my household running on 10.04 natty they are both a-okay. 
HTML5 vids work alright, can anyone tell me what is happening to flash player?   ](*,)

---

### Post by ortermagic on 2012-04-05
I meant to include this attachment which consists of the actual report generated at my last install and use of Flash-aid...Hope someone will be able to figure out what is happening here!

---

### Post by ortermagic on 2012-04-05
At he risk of completely exposing the inner workings of my browser I think I had better attatch another file which goes into some detail. I hope It helps one of you brainy people to unpick my problem :p

---

### Post by Awareness on 2012-04-05
Thanks! it worked!!

its a shame it broke that bad in ubuntu in the first place... :(

....but you saved the day... :)

kudos to you

---

### Post by Johan_D on 2012-04-05
P.S.  After downgrading to the latest working version ([SIZE=2]11.1.102.63) of packages adobe-flashplugin and adobe-flash-properties-gtk (.deb files), one ought to “pin” these packages, in order to prevent automatic “updating” to the new bad version of adobe flash.[/SIZE]
 
 [SIZE=2]As described in an earlier thread:  [/SIZE] 
 [SIZE=2]First install package dselect. [/SIZE] 
 [SIZE=2]Then type command “dselect” as root [/SIZE] 
 [SIZE=2]select option “Select” in the menu [/SIZE] 
 [SIZE=2]hit space bar to exit help[/SIZE]
 [SIZE=2]hit /[/SIZE]
 [SIZE=2]type in adobe-flashplugin, and hit return[/SIZE]
 [SIZE=2]then hit shift+h (which will pin the highlighted package adobe-flashplugin), then exit;[/SIZE]
 [SIZE=2]repeat the above for adobe-flash-properties-gtk.[/SIZE]
 
 [SIZE=2]When you now run Update Manager you will see these two packages automatically unchecked.[/SIZE]

---

### Post by ortermagic on 2012-04-05
Sorry to be so slow on the uptake but I am having a bit of trouble installing the " fp_11.1.102.63_archive " file I just downloaded. Its unpacked on my desktop atm please could somebody possibly put the necessary  terminal commands on here for me to enable the transfer of said file into the usr registry I have not worked out how to unpack tarballs and so far I haven't found a tutorial that makes sense to me

---

### Post by lovinglinux on 2012-04-05
> **ortermagic said:**
> At he risk of completely exposing the inner workings of my browser I think I had better attatch another file which goes into some detail. I hope It helps one of you brainy people to unpick my problem :p

There is something weird in your report.

As you can see, your system thinks the libflashplayer.so doesn't exist:

```
/usr/lib/flashplugin-installer/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-installer/libflashplayer.so' (No such file or directory)
```

However, Firefox detects it:

```
[PLUGINS]
libflashplayer.so:$
/usr/lib/flashplugin-installer/libflashplayer.so:$

```

Did you copy the file manually for some reason? 

Type [noparse]about:plugins[/noparse] in the address bar and make sure flash is being detected. Also make sure your browser and the flash player have the same architecture, otherwise it won't work.

BTW, Adobe purged the last Flash beta from their server. To use Flash-Aid properly, I recommend selecting the stable flash version from the repos in the installation options or clicking "Check Update" in the extension menu before running the Wizard. Either way, it will install version 11.2.202.228, which is the problematic one.

---

### Post by lovinglinux on 2012-04-05
> **ortermagic said:**
> Sorry to be so slow on the uptake but I am having a bit of trouble installing the " fp_11.1.102.63_archive " file I just downloaded. Its unpacked on my desktop atm please could somebody possibly put the necessary  terminal commands on here for me to enable the transfer of said file into the usr registry I have not worked out how to unpack tarballs and so far I haven't found a tutorial that makes sense to me

You can install it via Flash-Aid. You have downloaded a big tar.gz file from Adobe and unpacked it. Inside there were several other  flash packages. Select the one according to your architecture, but don't unpack it. Just copy it, then open Flash-Aid Advanced Mode, select "Custom" in the installation options and paste the file in the field. Click the Script tab, then execute.

---

### Post by ortermagic on 2012-04-05
Thank you for helping me, I have been struggling with this on my own for far too long,
I have tried both methods you offered but neither seem to work..Please see the attached
hope it will become a little clearer...I do not think I manually moved anything, consciously !

---

### Post by lovinglinux on 2012-04-05
> **ortermagic said:**
> Thank you for helping me, I have been struggling with this on my own for far too long,
I have tried both methods you offered but neither seem to work..Please see the attached
hope it will become a little clearer...I do not think I manually moved anything, consciously !

Now, post the report from the Help menu.

---

### Post by ortermagic on 2012-04-06
Hi lovinglinux here's the help report,

---

### Post by ortermagic on 2012-04-06
I have just been made aware of this post ... Interesting!

[http://www.tuxgarage.com/2012/02/adobe-drops-support-of-flash-for.html](http://www.tuxgarage.com/2012/02/adobe-drops-support-of-flash-for.html)

---

### Post by r.stiltskin on 2012-04-06
There seems to be some confusion between
/usr/lib/adobe-flashplugin
 vs.
/usr/lib/flashplugin-installer

Apparently some packages install the .so file in the former and others install it in the latter.

If you still don't have this working, it might be helpful to see exactly which flash packages you have installed.  Please open a terminal window and type this command
```
dpkg -l | grep flash
```
and post the output.  That will list all the packages that you have installed (or removed) that contain "flash" in their names.

---

### Post by ortermagic on 2012-04-06
Hi thanks for jumping in I have just done what you asked and I get this response from the terminal

fairy@fairy-K7S41GX:~$ dpkg -l | grep flash
fairy@fairy-K7S41GX:~$ dpkg -l grep flash
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  grep           2.6.3-3        GNU grep, egrep and fgrep
No packages found matching flash.
fairy@fairy-K7S41GX:~$ 


I know it seems peculiar, especially as I used flash-aid to install only 10 minutes ago (custom install referencing a tar gz from my desktop) Seems odd that there are no flash packages recognised.

---

### Post by philinux on 2012-04-06
> **nemesisgus said:**
> I just downgraded to the previous version by uninstalling the updated problematic packages 'adobe-flashplugin' and 'adobe-flash-properties-gtk' (11.2.202.228) and installing the last working version (11.1.102.63). You can download them here: [http://ubuntu.wbac.ac.th/archive-canonical/ubuntu/pool/partner/a/adobe-flashplugin/?C=M;O=D](http://ubuntu.wbac.ac.th/archive-canonical/ubuntu/pool/partner/a/adobe-flashplugin/?C=M;O=D)

Let's see if next updates fix the issue.

@Ubuntu 11.04

Yessssss. My GF's pc is 10.04 And I got this [http://ubuntu.wbac.ac.th/archive-canonical/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.1.102.63-0lucid1_i386.deb](http://ubuntu.wbac.ac.th/archive-canonical/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.1.102.63-0lucid1_i386.deb)

Since the tar was 170meg. I uninstalled flash then gdebi the above file. Now version locked in synaptic.

Has anyone raised a bug for this. I couldn't find one on launchpad.

---

### Post by r.stiltskin on 2012-04-06
> **ortermagic said:**
> 
I know it seems peculiar, especially as I used flash-aid to install only 10 minutes ago (custom install referencing a tar gz from my desktop) Seems odd that there are no flash packages recognised.

I think maybe you didn't run the command correctly.  You seem to have 2 command lines showing in the output you posted.

Notice the vertical bar | that I place before grep.  That's usually on the same key as the 'backslash', so press shift-\ to get it. 

```
dpkg -l | grep flash
```

---

### Post by r.stiltskin on 2012-04-06
> **philinux said:**
> 
Since the tar was 170meg. I uninstalled flash then gdebi the above file. Now version locked in synaptic.


I'm still using 10.04 LTS.

I took the easy road.  This one: [http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml]("http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml") was only a 6.4 MB download. I extracted the libflashplayer.so from that & copied it to my /usr/lib/adobe-flashplugin directory & I haven't had any problems with it.

---

### Post by philinux on 2012-04-06
> **r.stiltskin said:**
> I'm still using 10.04 LTS.

I took the easy road.  This one: [http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml]("http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml") was only a 6.4 MB download. I extracted the libflashplayer.so from that & copied it to my /usr/lib/adobe-flashplugin directory & I haven't had any problems with it.

That link has now been updated to the latest flash that dosnt work 11.2. The deb file I linked to is 6 meg too. And is version 11.1 which plays nice with 10.04

---

### Post by r.stiltskin on 2012-04-06
> **philinux said:**
> That link has now been updated to the latest flash that dosnt work 11.2.
Bummer.


> The deb file I linked to is 6 meg too. And is version 11.1 which plays nice with 10.04OK, I misunderstood your previous post.  
I'll download a copy from your link.

---

### Post by philinux on 2012-04-06
> **r.stiltskin said:**
> Bummer.


OK, I misunderstood your previous post.  
I'll download a copy from your link.

Yeah anyone following this just purge all flash first with synaptic. Then once installed lock the version.

---

### Post by ortermagic on 2012-04-06
Thanks rumple, 
Sorry, I didn't know where to get that line(I'm learning all kinds of new things)
After my last visit here I went and installed the only flash thing in my synaptic package manager, 
I returned to the terminal, (after having a little nap, I get tired these days) inputted the revised correct command and got this...

fairy@fairy-K7S41GX:~$ dpkg -l | grep flash
ii  flashplugin-installer                11.2.202.228ubuntu0.10.10.1                       Adobe Flash Player plugin installer
fairy@fairy-K7S41GX:~$ 


what I really want and need to do, I think,  is to put the working flash that I lack and everyone seems to have into my synaptic.
I'm sure it shouldn't be this obscure.

---

### Post by ortermagic on 2012-04-06
I looked into usr/lib and don't appear to have .../adobe-flashplugin directory?
Is it hidden?

---

### Post by ajgreeny on 2012-04-06
> **ortermagic said:**
> I looked into usr/lib and don't appear to have .../adobe-flashplugin directory?
Is it hidden?
Just run ```
locate libflashplayer.so
``` to find where the plugin is, or more importantly, if you have installed it at all.

---

### Post by ortermagic on 2012-04-06
AJ
I have a funny feeling that I have completely removed the file at some point over the last week...[I]To blindly go...
[/I]Any way this is theresult of running ...
locate libflashplayer.so

fairy@fairy-K7S41GX:~$ locate libflashplayer.so
/home/fairy/libflashplayer.so
/home/fairy/Downloads/install_flash_player_10_linux/libflashplayer.so
/home/fairy/flash problem/install_flash_player_10_linux/libflashplayer.so
/home/fairy/usr/lib/kde4/libflashplayer.so
fairy@fairy-K7S41GX:~$

I appear to have several instances of /libflashplayer.so onboard...I think thats because I set up a folder inhome to hold all the bits and peices of flashas I collect them...Sorry to be making such a stroganov of this ...It's a bit embarrassing tbh

---

### Post by r.stiltskin on 2012-04-06
@ortermagic:
Looking back over your posts, it seems that you are working on a Maverick system.  I mistakenly thought you were asking about Lucid, so I'm not sure that this will work for you.  It seems that Ubuntu support for Maverick has expired, so you should probably upgrade the entire system, or you might want to wait till the end of the month when 12.04 LTS (Precise Pangolin) is released.

For what it's worth, Flash 11.2.202.228 works fine on my 64-bit Oneiric system.

I'll leave this here for any 10.04 LTS (Lucid) users who lost *all* Flash functionality after the update.

You don't seem to have any copies of flash anyplace in your /usr directory, so it seems that for some reason none of your attempts have resulted in a proper installation.  I don't think any of those copies scattered around in your /home directory are a problem.   My only concern is that I don't know anything about _flash-aid_ and it seems to have tried to install flash in /usr/lib/kde4 which is a non-standard location for it, in ubuntu 10.04 at least.  And yet that somehow ended up in your home directory too, so I'm wondering if there's a link somewhere that we haven't detected that may be pointing to that ...

Anyway here's my advice.  I can't guarantee that it will work because some of your other attempts may have left behind some garbage that this won't clean up.  But this won't break your system.  At worst, you'll end up still without flash -- but that's no worse than where you are now.  It won't hurt anything else.  I can tell you that this worked perfectly on my 10.04 LTS machine.

First maybe you should remove, or at least disable, _flash-aid_.  I don't know what it does, it's not a standard Ubuntu thing and I don't see why you need it.  After this process is finished (assuming it's successful) you don't want to be making any further changes to the flash plugin anyway.  So (in Firefox) go to Tools/Add-ons/Plugins, find _flash-aid_ and click disable.  Then quit and restart Firefox.

(Apologies to the flash-aid developers.  I just don't like turning my baby over to a "wizard"; I'd rather run a few simple commands and know exactly what's being done to my system.)

Then:
1.
go to this link (that's the same link that philinux posted earlier) [http://ubuntu.wbac.ac.th/archive-canonical/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.1.102.63-0lucid1_i386.deb]("http://ubuntu.wbac.ac.th/archive-canonical/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.1.102.63-0lucid1_i386.deb") and save that file to your Desktop.

2.
Open a terminal window.  The remaining steps will all be done at the command line.

3.
Run this command
```
sudo apt-get purge flashplugin-installer
```
That should get rid of anything remaining from the non-working flashplugin version 11.2...

4.
Run this command
```
sudo apt-get purge adobe-flashplugin
```
That will probably do nothing because I don't think you've ever installed that package, but run it just in case.  It can't hurt anything.

5.
Next command:
```

sudo cp ~/Desktop/adobe-flashplugin_11.1.102.63* /var/cache/apt/archives/
```
That will save a copy of the .deb file that you just downloaded in your apt archives.

6.
Now we install it:
```

sudo gdebi /var/cache/apt/archives/adobe-flashplugin_11.1.102.63*
```At this point, you should have a working flash plugin.  I'm not sure, you might have to restart Firefox again to get it to use the new plugin.

7.
Now, we "lock" this version, so your package manager doesn't come along next week and "helpfully" replace it with another non-working update.
```

echo "adobe-flashplugin hold" | sudo dpkg --set-selections

```Note there's that vertical bar again in the middle of the command line.

8.
Finally, now that flash is working again (hopefully), you can delete all the various copies of it that are scattered around in your home directory -- all the ones listed in post #71, and the new one we just downloaded to your Desktop.  Leave the one that we copied to /var/cache/apt/archive.  That's all you need.

Good luck.

---

### Post by lovinglinux on 2012-04-06
> **r.stiltskin said:**
> My only concern is that I don't know anything about _flash-aid_ and it seems to have tried to install flash in /usr/lib/kde4 which is a non-standard location for it, in ubuntu 10.04 at least.  And yet that somehow ended up in your home directory too, so I'm wondering if there's a link somewhere that we haven't detected that may be pointing to that ...

I know about Flash-Aid, because I am the developer. It is a script generator that helps to remove conflicting plugins, install flash from various sources and apply some performance tweaks. It has been developed for 2 years, has 33.000 daily users and [a 5 star review on AMO](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/reviews/). It is not a standard Ubuntu application, but it does help a lot of people solve their flash problems.

Flash-Aid certainly didn't put any files on /usr/lib/kde4 or the home directory.

> **r.stiltskin said:**
> Anyway here's my advice.  I can't guarantee that it will work because some of your other attempts may have left behind some garbage that this won't clean up.  But this won't break your system.  At worst, you'll end up still without flash -- but that's no worse than where you are now.  It won't hurt anything else.  I can tell you that this worked perfectly on my 10.04 LTS machine.

Flash-Aid does cleanup "garbage" plugins installed on several locations, to avoid conflicts.

> **r.stiltskin said:**
> First maybe you should remove, or at least disable, _flash-aid_.  I don't know what it does, it's not a standard Ubuntu thing and I don't see why you need it.  After this process is finished (assuming it's successful) you don't want to be making any further changes to the flash plugin anyway.  So (in Firefox) go to Tools/Add-ons/Plugins, find _flash-aid_ and click disable.  Then quit and restart Firefox.

Flash-Aid doesn't do anything until you interact with it, by running the Wizard or the other installation modes, so removing it or disabling it won't make any difference.

You don't know what Flash-Aid does, but it is exactly what you need to fix a mess like this.

---

### Post by lovinglinux on 2012-04-06
> **ortermagic said:**
> Hi lovinglinux here's the help report,

Your report shows me that you have properly installed flashpliun-installer form the repos, but that won't solve the SMURF effect.

HEre are the instructions on how to remove the installed plugin and install version 11.1.102.63 using Flash-Aid.

Get the [flash player 11.1.102.63 pack from Adobe](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip). Extract the archive, find the tar.gz file corresponding to your architecture and copy it (**don't extract it**). Open Flash-Aid Advanced mode, select "Custom" in the installation option, paste the tar.gz path in the field. Click the Script tab, then Execute. Flash-Aid will remove all installed flash versions and install the  one from the tar.gz file in the proper location.

In addition to the instructions above, I recommend removing the remaining downloaded flash files from your home. Flash-Aid won't detect that location, so you need to do it manually, with these commands:

```
rm /home/fairy/libflashplayer.so
rm /home/fairy/Downloads/install_flash_player_10_linux/libflashplayer.so
rm /home/fairy/flash problem/install_flash_player_10_linux/libflashplayer.so
rm /home/fairy/usr/lib/kde4/libflashplayer.so
```

Keep in  mind that is probably not safe to use version 11.1.102.63, so at least make sure to block flash with NoScript extension and only allow trusted sites.

---

### Post by BobSongs on 2012-04-07
My report on Flash-Aid and the Flash player in general:

I followed the instructions given and removed all installed copies of Adobe-*. Tested the result by opening Youtube in Firefox: no videos would run. Done.

Installed Flash-Aid on 11.10 Ubuntu 32-bit using the default desktop. Used:

- Tools > Flash-Aid > Quick Mode > Install stable Flash

Followed through with password and restart.

Results:
**Pros:** Youtube videos played correctly (no more blue human skin).
**Cons:** When scrolling the Youtube page up and down with my mouse wheel, the Flashplayer crashed displaying sad-looking Lego-type block. Pausing the video and restarting resulted in another crash. Clicking the video ahead or behind the play point caused yet another crash. At other times the player simply crashed without provocation.

Next Step
Opened Synaptic Package Manager to remove all Adobe references (adobe-flashplugin, adobe-flash-properties-gtk) and tried various other methods from the Flash-Aid menu. All other methods failed claiming a 404 error. Removed Flash-Aid from my plug-ins.

Read through this thread. Found the link to
[http://ubuntu.wbac.ac.th/archive-canonical/ubuntu/pool/partner/a/adobe-flashplugin/?C=M;O=D](http://ubuntu.wbac.ac.th/archive-canonical/ubuntu/pool/partner/a/adobe-flashplugin/?C=M;O=D)
Downloaded adobe-flashplugin_11.1.102.63-0oneiric1_i386.deb & adobe-flash-properties-gtk_11.1.102.63-0oneiric1_i386.deb and installed these two files using dpkg.

Results:
**Pros:** The Flash player at the Youtube site no longer crashed when scrolling the page.
**Cons:** The player's image would freeze (sound worked though) if the video was forced to play at different points in the time line when already playing.

SUCCESSFUL SOLUTION:
Followed the advice listed as a bandaid solution [**here**]("http://ubuntuforums.org/showpost.php?p=11802933&postcount=11"). Placed a copy of libflashplayer.so in /usr/lib/flashplugin-installer

Results:
**Pros:** The Flash player at the Youtube site no longer crashes, no longer has difficulties when jumping through the video's time line.
**Cons:** Wasted too much time trying other solutions.

---

### Post by ortermagic on 2012-04-07
@r.stiltskin
Thank you for posting that solution, or possible solution to my problem. I have followed your instructions.
The unfortunate result I get is as follows...

 fairy@fairy-K7S41GX:~$ sudo apt-get purge flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-installer is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
fairy@fairy-K7S41GX:~$ sudo apt-get purge adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
fairy@fairy-K7S41GX:~$ sudo cp ~/Desktop/adobe-flashplugin_11.1.102.63* /var/cache/apt/archives/
fairy@fairy-K7S41GX:~$ sudo gdebi /var/cache/apt/archives/adobe-flashplugin_11.1.102.63*
sudo: gdebi: command not found
fairy@fairy-K7S41GX:~$ 

There is something amiss with the sudo: gdebi command ... do you know why it stalls at this point?

---

### Post by ortermagic on 2012-04-07
Dear r.stiltskin
this is a happy post...thank you for leading me to a solution to a problem that has been bugging me for two weeks.
How did I do it? after trying to install using the terminal unsuccessfully and posting the above query re- "sudo: gdebi: command not found" I right clicked on the desktop file you pointed me towards and noticed that I had an option to open it using the software centre, so I tried it ...and it worked! Yippee! 

I will now have to study using terminal commands to hopefully clear out the fog in my brain.
I guess I will have to discover how to pin the thing in, so that any future upgrades will leave it alone.

I'm sorry lovinglinux but your app did not work for me? don't know why, I tried every which way to to get it going, but failed every time.
Nevertheless thank you so much for all your help, I really appreciate it.
I don't know if I am allowed to do this but I feel the need to add a little musical link here.
[http://www.youtube.com/watch?v=W-zgBalOefY&feature=related](http://www.youtube.com/watch?v=W-zgBalOefY&feature=related)
Thanks everyone! Any relevant advice will always be appreciated 
Roger

---

### Post by Trapper on 2012-04-07
I had this flash problem after updating to 228 on one of my machines but not another. I took the hard drive from the computer it worked on and put it in the other machine and booted up. Flash would not work on that box. I moved it back to the original box and it did work again. So, this almost has to be hardware specific. Totally different hardware on my 2 machines.

My fix was as others have done and copied over my 228 libflashplayer.so with the 11.1.102.55 libflashplayer.so

_ALSO_ !!!! .... do a full search of your home .mozilla folder for libflashplayer.so and delete any you find.

I found  11.1.102.55 .tar.gz to extract libflashplayer.so from here: [http://www.techspot.com/downloads/5104-adobe-flash-player-for-linux.html](http://www.techspot.com/downloads/5104-adobe-flash-player-for-linux.html)

---

### Post by Trapper on 2012-04-07
Another thought on why some are experiencing problems with 228 and others are not. My problems all seem to be on machines with 32 bit processors. It would be interesting to know if it's 32 bit specific. For me, personally, it is only affecting my older 32 bit machines. Even 64 bit machines running 32 bit don't seem to be affected.

This also does not seem to be a 10.04 specific problem. I have the same problem on the plagued 32 bit machines with 11.10 and 12.04.

---

### Post by lovinglinux on 2012-04-07
Solutions:

[http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by lovinglinux on 2012-04-07
> **BobSongs said:**
> Results:
**Pros:** Youtube videos played correctly (no more blue human skin).
**Cons:** When scrolling the Youtube page up and down with my mouse wheel, the Flashplayer crashed displaying sad-looking Lego-type block. Pausing the video and restarting resulted in another crash. Clicking the video ahead or behind the play point caused yet another crash. At other times the player simply crashed without provocation.

Untick the option HWDecode in Flash-Aid tweaks to avoid instability. But then you need to disable hardare acceleration in Flash Settings.

> **BobSongs said:**
> Next Step
Opened Synaptic Package Manager to remove all Adobe references (adobe-flashplugin, adobe-flash-properties-gtk) and tried various other methods from the Flash-Aid menu. All other methods failed claiming a 404 error. Removed Flash-Aid from my plug-ins.

That's because Adobe removed the last beta from their site. You need to click "Check Update" in Flash-Aid menu, so it can rfetreive the new ulr. However, since there is no more Beta, the downloaded file will be the same as the stable version from  the repos.

> **BobSongs said:**
> SUCCESSFUL SOLUTION:
Followed the advice listed as a bandaid solution [**here**]("http://ubuntuforums.org/showpost.php?p=11802933&postcount=11"). Placed a copy of libflashplayer.so in /usr/lib/flashplugin-installer

Results:
**Pros:** The Flash player at the Youtube site no longer crashes, no longer has difficulties when jumping through the video's time line.
**Cons:** Wasted too much time trying other solutions.

Keep in mind this is the unsafe solution. Besides, you could simply puth the file inside ~/.mozilla/plugins. 

See [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by daviddixit on 2012-04-18
> **Peter Donaldson said:**
> Bandaid solution-

Extract libflashplayer.so (11.1.102.55) from file downloaded at [http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml]("http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml")[LIST]
[/LIST]



Move libflashplayer.so to folder usr/lib/flashplugin-installer

Worked on the chromium, firefox, seamonkey, midori
Help please!
I tried this, but there was no    	 	 	 	 	flashplugin-installer folder...

---

### Post by r.stiltskin on 2012-04-18
It depends on how you installed flash.  You may have /usr/lib/adobe-flashplugin instead.  If so, libflashplayer.so goes in that folder.

However, that linux.softpedia.com link won't help anymore -- it's been updated and now contains the same 
11.2.202.228 version that's causing the problem.  Instead of that one, you can download this file: 
[http://ubuntu.wbac.ac.th/archive-canonical/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.1.102.63-0lucid1_i386.deb]("http://ubuntu.wbac.ac.th/archive-canonical/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.1.102.63-0lucid1_i386.deb"), extract it and use the libflashplayer.so contained there.

---

### Post by lovinglinux on 2012-04-19
> **daviddixit said:**
> Help please!
I tried this, but there was no    	 	 	 	 	flashplugin-installer folder...

See [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by Bloodyraw on 2012-04-20
I had problems with this too. First of all, there is a difference between "flashinstaller" and "adobe flash".

I am using chrome, and for some reason Chrome came with 2 different outcomes when I had either one of them.
When I had flashinstaller i would just go black when playing flash movies, and when having adobe flash, it wouldnt even recognize that I had flash installed...

So I deledted everything and installed adobe flash from adobe.com.
Went to a terminal and entered; sudo nautilus.
Went to /usr/lib/adobe-flashplugin and copied libflashplayer.so to /usr/lib/chromium-browser/plugins
Restarted chrome... Bang, worked like a charm

---

### Post by tstduke on 2012-04-30
Had same problem with flash not working. 
With adobe no longer supporting flash for linux I went to youtube site that tests html5:
[http://www.youtube.com/html5](http://www.youtube.com/html5)
I clicked on the link at the bottom which says "Join the html5 trial"
then refreshed by browser (Firefox). 
Lo and behold Youtube videos would play again!
Apparently Flash is dying on the web due to Html5 replacing it. Many websites now use html5 instead of flash. However not all websites use html5 yet so this "workaround" won't work for all sites. Most major sites do however use html5 though. 
Hope this helps someone. 
Its a lot easier than constantly fiddling with system files.

---

### Post by lovinglinux on 2012-04-30
> **tstduke said:**
> Had same problem with flash not working. 
With adobe no longer supporting flash for linux I went to youtube site that tests html5:
[http://www.youtube.com/html5](http://www.youtube.com/html5)
I clicked on the link at the bottom which says "Join the html5 trial"
then refreshed by browser (Firefox). 
Lo and behold Youtube videos would play again!
Apparently Flash is dying on the web due to Html5 replacing it. Many websites now use html5 instead of flash. However not all websites use html5 yet so this "workaround" won't work for all sites. Most major sites do however use html5 though. 
Hope this helps someone. 
Its a lot easier than constantly fiddling with system files.

No they don't. Most major sites still use flash.

---

### Post by seancyril on 2012-05-04
> **lovinglinux said:**
> You can install it via Flash-Aid. You have downloaded a big tar.gz file from Adobe and unpacked it. Inside there were several other  flash packages. Select the one according to your architecture, but don't unpack it. Just copy it, then open Flash-Aid Advanced Mode, select "Custom" in the installation options and paste the file in the field. Click the Script tab, then execute.



Thanks for the advice. It has put an end to a week of hair pulling and teeth gnashing. I now have flash working on Ubuntu 11.10

Sean:p

---

### Post by cliffordsnow on 2012-06-12
For those that are still having problems and can not find a copy of an old version, you can get it directly from Adobe 

[https://fpdownload.macromedia.com/get/flashplayer/pdc/11.1.102.63/install_flash_player_11_linux.x86_64.tar.gz](https://fpdownload.macromedia.com/get/flashplayer/pdc/11.1.102.63/install_flash_player_11_linux.x86_64.tar.gz)

Apparently if you want a different version just replace the version number in the link above.

good luck

---

### Post by Laysan_A on 2012-06-14
Just want to say a couple things for folks still searching flash installation problems. First, I've been using flash aid for a while now, and I think it's really great. I still have trouble remembering where everything gets stored, so it's really nice that I can just trust flash aid to remove any potentially conflicting copies of flash before installation. It's reliable and pretty easy to learn all its ins and outs.

The other thing I wanted to say, I recall someone mentioned that flash was recognized in their browser as being installed, but still seemed to be uninstalled and not working. I had the same issue with my laptop's lubuntu installation. I had manually copied the zip file from adobe to my /user/local/src directory as root, unpacked it, chose the correct version and deleted the rest, then installed it. It showed up in "about plugins", and in the plugin menu in firefox, but there was only a blank screen - basically a hole in the page where the video should've been. I discovered it was a permissions problem. For some reason lubuntu assigns read and write status to the owner (root), but gives no rights at all to either "group" or "others". By right-clicking the flash plugin file (where I had put it in /usr/local/src - which is owned by root) and selecting properties (as root), I changed the permissions for both group and others to "read", and it was fixed.

---

### Post by Linker101 on 2012-06-17
**tl;dr, The last line of my post is the real solution.**

I fixed this problem. It took forever.

I tried following this: [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

What they tell you to do is essentially the following:

[LIST]
[*]create a file /etc/adobe/mms.cfg (or just edit it if its already there)
[*]Add the following two lines
[/LIST]
```
EnableLinuxHWVideoDecode=1
OverrideGPUValidation=true

```
This fixes the problem, but when I watch videos on any other website the flash player constantly crashes.


This isn't really a problem to do with adobe, because I have the same flash player installed on my laptop and it works fine. The problem is the nvidia package that uses hardware acceleration  for playing flash videos.



The packages that governs the hardware acceleration for playing flash videos is called nvidia-current. Open Synaptic and remove it. Alternatively:






Open terminal and type the following:

```
sudo apt-get remove nvidia-current
```

---

### Post by aaronLund on 2012-07-18
> **Peter Donaldson said:**
> Bandaid solution-

Extract libflashplayer.so (11.1.102.55) from file downloaded at [http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml]("http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml")[LIST]
[/LIST]



Move libflashplayer.so to folder usr/lib/flashplugin-installer

Worked on the chromium, firefox, seamonkey, midori

I got flashplayer11_1r102_63_linux.i386.tar.gz from here:
[https://github.com/webgapps/flashaid/downloads](https://github.com/webgapps/flashaid/downloads)

Extraxted libflashplayer.so to /usr/lib/flashplugin-installer as well.

Worked like a charm.  This flash problem has been plaguing the 11.04 box in the garage.  I never wanted to spend the time troubleshooting but just got fed up.  

Thanks!

NOTE:  I have Flash-Aid 2.2.3 and that didn't seem to help at all.  Not too sure if I'm sold on Flash Aid all that well because of it.

Whatever.  I'm stoked to be able to listen to tunes again.

---

### Post by r.stiltskin on 2012-07-25
> **Linker101 said:**
> **tl;dr, The last line of my post is the real solution.**

I fixed this problem. It took forever.

I tried following this: [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

What they tell you to do is essentially the following:

[LIST]
[*]create a file /etc/adobe/mms.cfg (or just edit it if its already there)
[*]Add the following two lines
[/LIST]
```
EnableLinuxHWVideoDecode=1
OverrideGPUValidation=true

```
...

Open terminal and type the following:

```
sudo apt-get remove nvidia-current
```

Sorry to report that neither of these worked on my old desktop (Asus A7N8X-E motherboard with Nvidia nForce2 chipset, AthlonXP cpu, and Nvidia GeForce4-based video card) running Kubuntu 12.04 32 bit.  With Flash 11.2.202 I still get "missing plugin" or Flash simply doesn't work.  No "smurf-effect" -- it just acts as if Flash is not installed.  (In fact, nvidia-current was never installed.)

Also, makes no difference whether Flash is installed with apt-get, or Synaptic, or FlashAid, or whether libflashplayer.so is located in /usr/lib/mozilla/plugins or in usr/lib/flashplugin-installer.

The only solution I've found that works is to locate libflashplayer.so (the actual file, not a link) and replace it with an older version -- I'm using 11.1.102.55 -- and hope that I'm lucky regarding whatever security problems it contains.

---

### Post by SonnyE on 2012-07-26
Flash disappeared on YouTube in Firefox and Chromium today, and was crashing every time on the Adobe Flash test page. That was using version 11.2.202, so I changed to version 11.1.102.63 and it works now.

Details: I downloaded fp_11.1.102.63_archive.zip from Adobe, extracted flashplayer11_1r102_63_linux.i386.tar.gz to a folder. Then from that folder, I followed the instructions that were in the readme.txt for the newer fp_11.2.202.228_archive.zip (a version that didn't work) resulting in these manual installation commands:

$ sudo cp libflashplayer.so /usr/lib/flashplugin-installer/
$ sudo cp -r usr/* /usr

System: Lubuntu 12.04 - 442 MB RAM (a bit low) - AMD (original brand name ATI) IGP320M graphics (the OSS driver can do graphic acceleration using it, but it tends not to be well-supported)

---

### Post by aaronLund on 2012-08-31
Jeez.

Just had to do it again.

A bit off-topic:  Why does FlashAid remove /usr/lib/flashplugin-installer ?

What is it trying to do?  Does it auto-update?

I'm fully aware I could look.....just busy at the moment (and thinking out loud).

---

### Post by yensean on 2012-08-31
hey can you help me to install flash 
i am new ubuntu user 
i have no idea what to do?

---

### Post by yensean on 2012-08-31
hey can you help me to install flash 
i am new ubuntu user 
i have no idea what to do?

---

### Post by lovinglinux on 2012-09-02
> **aaronLund said:**
> Jeez.

Just had to do it again.

A bit off-topic:  Why does FlashAid remove /usr/lib/flashplugin-installer ?

What is it trying to do?  Does it auto-update?

I'm fully aware I could look.....just busy at the moment (and thinking out loud).

Flash-Aid tries to make sure all flash versions are removed before installing the selected version.

---

### Post by lovinglinux on 2012-09-02
> **yensean said:**
> hey can you help me to install flash 
i am new ubuntu user 
i have no idea what to do?

Open the Software Center, type *flash* in the search field and hit *Enter*. Select the *Adobe Flash Plugi*n from the results and click the *Install* button. Restart the browser.

---

### Post by Energizor on 2012-10-05
My flash also got all messed up when I installed Flash 11.2 32 bit.
I could not get it to work at all I am running Lucid.

I did sudo nautilus and added a 11.1.102 version I found from another package.

All seemed to be working fine. Youtube and all. Until I tried PCH.com.
Had numerous crashes with Firefox 15 and Google Chrome. I then tried Opera and it found Flash but would not use it.Firefox even had an overlapping of music on the slots game from the home page link. Google Chrome did not.

I even checked all dependencies for Flash and Firefox 15. There were a few missing and adding them made the pages load smoother.

I then tried Seamonkey 2.0.11 with the 11.1.102 Flash and all is working great now with zero problems. So does anyone have any idea why this is?:p

---

### Post by pyutaros on 2012-11-19
I didn't read the entire thread, so I apologize if someone already posted something like this.  I got tired of manually downgrading flash on every computer I use, so i wrote this script.  Save it to a your computer and remove the ".txt".  Make sure it's sent to run as an executable and then you can run it from a terminal by typing ./Adobe_fix.  Here is the code below:

```
wget http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip
unzip fp_11.1.102.63_archive.zip
tar -xzvf fp_11.1.102.63_archive/11_1r102_63_32bit/flashplayer11_1r102_63_linux.i386.tar.gz -C fp_11.1.102.63_archive/
sudo cp -f fp_11.1.102.63_archive/libflashplayer.so /usr/lib/flashplugin-installer
```

---

### Post by rockhen on 2013-01-05
I saved 11.1 to my documents folder, comes in handy when I attempt to install 11.2 and it still crashes and I don't mind installing manually. The only minor problem is some websites or Flash games ask you to upgrade Flash. Nice of Adobe to leave out the growing number of Linux users. Any one want a copy? Am I allowed to share it?

---

