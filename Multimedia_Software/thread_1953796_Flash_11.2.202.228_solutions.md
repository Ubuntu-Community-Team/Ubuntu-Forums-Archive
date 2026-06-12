---
title: "Flash 11.2.202.228 solutions"
date: 2012-04-06
forum: Multimedia Software
---

### Post by lovinglinux on 2012-04-06
The most recent versions of Flash, 11.2.202.228, is causing a lot of problems to nVidia users, like the SMURF effect. This thread intends to provide the possible solutions the easiest way possible.


**Possible Solutions**

**[COLOR="DarkRed"]1 - Disable hardware acceleration in Flash[/COLOR]**

You can do that by visiting a video on YouTube, right-clicking on it, selecting the *Settings* option then *Display* tab. Just untick the option *Enable hardware acceleration*

[IMG]http://i.imgur.com/35TMy.jpg[/IMG]

If the settings dialog doesn't respond to mouse clicks, then close it, enter the fullscreen video mode and try again.

If that doesn't help, you can try to add a special line to /etc/adobe/mms.cfg. To that, open a terminal and open the file in an editor with gksudo:

```
gksudo gedit /etc/adobe/mms.cfg
```

Add the following line:

```
EnableLinuxHWVideoDecode=0
```

Save it. Restart the browser and check if it works. If it doesn't work, you can try to use *EnableLinuxHWVideoDecode=1* instead, but that will probably cause flash instability.


**[COLOR="darkred"]2 - Downgrade Flash[/COLOR]**

There are several reports that Flash 11.1.102.63 works. 

> **[COLOR="Red"][SIZE="4"]IMPORTANT[/SIZE][/COLOR]**

[COLOR="Red"]**[SIZE="4"]Although this is a viable solution, you need to be aware that it will probably be a security risk. If you opt to use this method, make sure to at least block flash from running on untrusted sites.[/SIZE]**[/COLOR]

You can block flash on Firefox using [NoScript](https://addons.mozilla.org/en-US/firefox/addon/noscript/) extension. 

If you are using Chrome, type **chrome://settings/content** in the address bar and tick "Click to Play" in the plugin section.

If you are using Opera, then click Settings >> Preferences", select the *Advanced* tab, click *Content* in the sidebar, then tick the option "Enable plugins only on demand".

To downgrade flash, first download version 11.1.102.63. Adobe offer a package for download that is hugem because include builds for Windows, Mac and Linux. So I have uploaded the files to my server to make it easier:

> **32bit** [https://github.com/downloads/webgapps/flashaid/flashplayer11_1r102_63_linux.i386.tar.gz](https://github.com/downloads/webgapps/flashaid/flashplayer11_1r102_63_linux.i386.tar.gz)

md5sum edc3326dd25adee13a8109834d8c05ce

> **64bit** [https://github.com/downloads/webgapps/flashaid/flashplayer11_1r102_63_linux.x86_64.tar.gz](https://github.com/downloads/webgapps/flashaid/flashplayer11_1r102_63_linux.x86_64.tar.gz)

md5sum 144b9ab0fec08d589b5369b1417d8332

After downloading the file, extract it using the file manager, copy the file *libflashplayer.so* and paste into ~/.mozilla/plugins/. To see that directory under your home, you need to show hidden files. You can do that in Nautilus by hitting CTRL+H.

Restart Firefox and test it. 

If you are using Chrome 32bit, then you will have to disable the plugin that comes with Chrome. To do that, type **chrome://plugins/** in the address bar, then click the *Details* link in the top-right corner, then disable the Shockwave plugin located in the /opt/google/chrome folder.


> **[COLOR="Red"]IMPORTANT[/COLOR]**

If you use this method, keep in mind that the plugin located under ~/.mozilla/plugins/ will supersed the other pluguins, so even if you get an update from Ubuntu, Firefox will continue to use the old version until you remove the plugin from that location.


This method will work for the user applying it. If you need to downgrade flash to all users, then the easiest way is to use [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/"). After installing it, open Flash-Aid Advanced mode, select "Custom" in the installation option, paste the link to the flash 11.1.102.63 in the field. Click the Script tab, then Execute. Flash-Aid will remove all installed flash versions and install the  one from the tar.gz file in the proper location.

[IMG]http://i.imgur.com/vB7IW.jpg[/IMG]


**TROUBLLESHOOTING**

If you are using Chrome type **chrome://plugins/** in the address bar, then click the *Details* link in the top-rigfht corner, then check Shockwave plugin location and if there is more than one plugin detected.****

If you are suing Firefox, type **about:config** in the address bar, then type *plugin.expose_full_path* in the filter, double-click the resulting preference to make it true. 

[IMG]http://i.imgur.com/Ud6i9.jpg[/IMG]



Then type **[noparse]about:plugins[/noparse]** in the address bar and verify that the plugin is detected and is in the proper location:

[IMG]http://i.imgur.com/lASFS.jpg[/IMG]

If you are still experiencing problems, please attach the firefox-report.txt file generated in your desktop after running the commands below:

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'pluginreg.dat' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat ~/.mozilla/firefox/**/pluginreg.dat >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by ArchaicReality on 2012-04-07
But my question is... why does flash crash when using chrome only on certain videos on youtube? Its driving me nuts

---

### Post by pqwoerituytrueiwoq on 2012-04-07
> **ArchaicReality said:**
> But my question is... why does flash crash when using chrome only on certain videos on youtube? Its driving me nuts
if you are using a nvidia gpu with hardware decode on it tends to crash when the quality changes 
some videos are in 480p and when you switch to full screen they will switch to 720p not all videos have 720p or 1080p

---

### Post by ArchaicReality on 2012-04-07
I have AMD. I dont understand why it does this. It happens on firefox as well so thats why I thought that it was my comp

---

### Post by lovinglinux on 2012-04-07
> **ArchaicReality said:**
> I have AMD. I dont understand why it does this. It happens on firefox as well so thats why I thought that it was my comp

Since the main problem with the current version of flash is hardware acceleration, it might be affecting AMD as well, but not causing the SMURF effect.

---

### Post by winh8r on 2012-04-07
I am just jumping in here for a very simple reason:

to thank [COLOR="Red"]**lovinglinux**[/COLOR] for all his work, both in developing FlashAid and also 

his continued assistance to those experiencing difficulties in light of the 

recent Flash problems. 

Thank You.

---

### Post by QIII on 2012-04-07
+1 LL's good work
 
 LL --
 
 I noticed yesterday that flash content on my primary news website would  not work without the latest version (which I installed with FlashAid,  thank you.) It is possible that some content may not work with the  downgrade if the website admins are zealous.

In general, have you put any thought into what happens in a post-Linux-Flash-support world that might be of interest? You've put a lot of work into this for the last few years.

---

### Post by Trapper on 2012-04-07
So. Here's the big question. Why hasn't Adobe released a fix?

---

### Post by winh8r on 2012-04-07
> **Trapper said:**
> So. Here's the big question. Why hasn't Adobe released a fix?



This

[http://ubuntuforums.org/showpost.php?p=11806849&postcount=2]("http://ubuntuforums.org/showpost.php?p=11806849&postcount=2")

---

### Post by lovinglinux on 2012-04-07
> **Trapper said:**
> So. Here's the big question. Why hasn't Adobe released a fix?

Because Adobe is no longer supporting Flash on Linux. They gave this task to Google, which will release a new kind o plugin, using Chrome Pepper API. Neither Mozilla or Opera will adopt Pepper.

> **winh8r said:**
> I am just jumping in here for a very simple reason:

to thank [COLOR="Red"]**lovinglinux**[/COLOR] for all his work, both in developing FlashAid and also 

his continued assistance to those experiencing difficulties in light of the 

recent Flash problems. 

Thank You.

You are welcome and thanks a lot for your comments.

The SMURF effect is driving me crazy.

> **QIII said:**
> +1 LL's good work

Thanks.

> **QIII said:**
>  I noticed yesterday that flash content on my primary news website would  not work without the latest version (which I installed with FlashAid,  thank you.) It is possible that some content may not work with the  downgrade if the website admins are zealous.

Yes, it's possible, but I don't the extent of differences between both versions.

> **QIII said:**
> In general, have you put any thought into what happens in a post-Linux-Flash-support world that might be of interest? You've put a lot of work into this for the last few years.


I am scratching my head. Flash-Aid has lost on the most used feature, which is the Beta installation and I really don't want to use Chrome for Flash videos. I have already tried to do some dirty hacks, without success. 

There is a totem vega plugin that is coincidentally appearing in some support threads. It allows flash to be played by totem, but without controls. I haven't tested it yet, but I remember helping someone with flash troubles because of it.

There is a thread at [http://ubuntuforums.org/showthread.php?t=1954094](http://ubuntuforums.org/showthread.php?t=1954094)

---

### Post by QIII on 2012-04-07
If worse comes to worst while the community works on a solution to such a blatant "nose-thumbing" from Adobe, I may have to dig out an XP disk and run it in VBox for Flash content.  Sigh.

---

### Post by lovinglinux on 2012-04-07
> **QIII said:**
> If worse comes to worst while the community works on a solution to such a blatant "nose-thumbing" from Adobe, I may have to dig out an XP disk and run it in VBox for Flash content.  Sigh.

Well, I can't say I haven't thought about that too. But either doing that or using Chrome will brake my work-flow. At least using Chrome we can use the "Open With" feature of Opera or the Firefox extension.

---

### Post by Trapper on 2012-04-07
> **lovinglinux said:**
> Because Adobe is no longer supporting Flash on Linux. They gave this task to Google, which will release a new kind o plugin, using Chrome Pepper API. Neither Mozilla or Opera will adopt Pepper.


Okay. Another squeeze to eliminate competition and to get everyone to "buy" into specific new technologies and hardwares. Firefox is pretty much dead without flash support unless flash is going to be replaced. What's the roadmap here?

---

### Post by gradinaruvasile on 2012-04-07
> **QIII said:**
> If worse comes to worst while the community works on a solution to such a blatant "nose-thumbing" from Adobe, I may have to dig out an XP disk and run it in VBox for Flash content.  Sigh.

Nah, its not THAT bad. If you have a decent enough CPU, unticking that hardware option (first image) will remove the smurf effects and you can play 1080p with no issues.

About the future of Flash:

Pepper might be an open API, but the flash plugin itself (thats a proprietary piece of work) will be bundled with Chrome.

So, you are a developer of an open (or not so open) source browser on Linux. You implement the Pepper API. But you will lack the reason d'etre of it: the flash plugin itself. Adobe+Google surely signed some agreement over the IP that goes into the Flash Plugin so it will not be possible to publish it freely ONLY if Google or Adobe or both decides to do so.
So, until then you can have all the pepper API implementation and you would still require the installation of Chrome or at least the libpepflashplayer.so file from the installer.

PS: I have Google Chrome dev version installed. Once i verified th eplugins and saw that there is a /opt/google/chrome/PepperFlash/libpepflashplayer.so file instead of libgcflashplayer.so in the plugin list.
I disabled the locally installed flash plugin and this pepper thing worked (with smurfs and all).
Then i linked the pepper plugin to ~/.mozilla/plugins/, fired up Chromium, but the plugin, although it appeared in the plugin list, had nothing besides its name and it did not work. I use the latest buildbot builds of Chromium that is updated quite a few times every day so there is something fishy with the pepper flash support - it seems to be implemented only in Chrome.
The next day i wanted to do some more testing, but as Chrome was updated, the pepper plugin vanished and the old NPAPI one came back.

---

### Post by paulie-m on 2012-04-07
I installed flash 11.2.202.228 today and all my browseres stopped playing flash.I looked through various forums for advice but only one worked. Reinstall flash 11.1.102.63 (available from adobe archives). All was well after that. P.S. I have nVidia card, but had exactly the same trouble on my other PC which has Intel graphics chipset and same solution worked on this.

---

### Post by gradinaruvasile on 2012-04-07
> **paulie-m said:**
> I installed flash 11.2.202.228 today and all my browseres stopped playing flash.I looked through various forums for advice but only one worked. Reinstall flash 11.1.102.63 (available from adobe archives). All was well after that. P.S. I have nVidia card, but had exactly the same trouble on my other PC which has Intel graphics chipset and same solution worked on this.

That might be some other issue.

Flash player is in fact a single .so file (dll equivalent): libflashplayer.so or whatever the packagers rename it (flash-mozilla.so). The installed .debs put the .so file in /usr/lib/mozilla/plugins/ folder and create some symlinks.
But as user you can copy/link the plugin's .so file in the ~/.mozilla/plugins/ folder, it will be picked up by the browsers aswell.
You can have more than 1 instance of the flash player, typically this is the issue. You can check in any browser the "about:plugins" page to see how many instances you have. You can have more than one and have no issues if you disable all but one.

---

### Post by paulie-m on 2012-04-07
I did have to copy the .so file into /usr/lib..etc after downloading from adobe archives. Previously I had tried the same with with a .so file from version 11.2.202.228 and that did not worked.Before downgrading I installed gnash and used galternatives to select that as my default flash player.What a load of rubbish!! It's a terrible flash player. That's when I downloaded older 11.1.102.63 version,copied over the .so file and all my browsers are happy again (and me too).

---

### Post by bdlandry on 2012-04-07
FYI: If you are using Vuze, this problem also causes it to crash when you do a search, then click on a search result and open the search page to download.

The fix of downgrading libflashplayer.so fixes this problem as well.

in 11.10 I replaced the libflashplayer.so in /usr/lib/flashplugin-installer with the older version from: 

[http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip)

---

### Post by lovinglinux on 2012-04-07
> **gradinaruvasile said:**
> NPS: I have Google Chrome dev version installed. Once i verified th eplugins and saw that there is a /opt/google/chrome/PepperFlash/libpepflashplayer.so file instead of libgcflashplayer.so in the plugin list.
I disabled the locally installed flash plugin and this pepper thing worked (with smurfs and all).
Then i linked the pepper plugin to ~/.mozilla/plugins/, fired up Chromium, but the plugin, although it appeared in the plugin list, had nothing besides its name and it did not work. I use the latest buildbot builds of Chromium that is updated quite a few times every day so there is something fishy with the pepper flash support - it seems to be implemented only in Chrome.
The next day i wanted to do some more testing, but as Chrome was updated, the pepper plugin vanished and the old NPAPI one came back.

I have noticed a PepperFlash folder inside stable Chrome's profile directory as well. But it is empty. I guess they experimenting.

> **Trapper said:**
> Okay. Another squeeze to eliminate competition and to get everyone to "buy" into specific new technologies and hardwares. Firefox is pretty much dead without flash support unless flash is going to be replaced. What's the roadmap here?

Firefox is not dead because this only affects the Linux version, but I agree it looks like this was a moove by Google to force Pepper adoption.


> **gradinaruvasile said:**
> That might be some other issue.

Flash player is in fact a single .so file (dll equivalent): libflashplayer.so or whatever the packagers rename it (flash-mozilla.so). The installed .debs put the .so file in /usr/lib/mozilla/plugins/ folder and create some symlinks.
But as user you can copy/link the plugin's .so file in the ~/.mozilla/plugins/ folder, it will be picked up by the browsers aswell.
You can have more than 1 instance of the flash player, typically this is the issue. You can check in any browser the "about:plugins" page to see how many instances you have. You can have more than one and have no issues if you disable all but one.

I have Intel chipset and I am using 11.2.202.228 without issues. But a have seen reports from non-nVidia users that lost flash after the update to 11.2.202.228, even with AMD.


> **bdlandry said:**
> FYI: If you are using Vuze, this problem also causes it to crash when you do a search, then click on a search result and open the search page to download.

The fix of downgrading libflashplayer.so fixes this problem as well.

in 11.10 I replaced the libflashplayer.so in /usr/lib/flashplugin-installer with the older version from: 

Please read the first post. Instead of downloading the 170Mb you suggested,I have provided the Linux packages you find inside that file and also instructions where to put the file. If you are installing for yourself, the best location is ~/.mozilla/plugins.

---

### Post by EgoGratis on 2012-04-08
I used and recommend Flash-Aid since i can remember and the addon exist. Thanks.

But i must say i am against recommending downgrading Flash to previous versions of Flash and against mentioning this option. I do understand this solves some issues for some users BUT at the same time it opens known security holes for them?

This is just not an option and for users that have problems with Flash and won't use Chrome only two options exist:

1.) Adobe fixes Flash problems.
2.) There is no Flash anymore for Linux users that don't want to use Chrome and have problems with latest Flash.

I don't see other options right now for users that have problems with latest Flash and none of the "workarounds" work for them with latest Flash version. 

Running software that has "web access" and known security holes is just not an option and therefore downgrading Flash should not be mentioned at all as it's not the solution for the problem as it only creates way larger security problems!

---

### Post by lovinglinux on 2012-04-08
> **EgoGratis said:**
> I used and recommend Flash-Aid since i can remember and the addon exist. Thanks.

But i must say i am against recommending downgrading Flash to previous versions of Flash and against mentioning this option. I do understand this solves some issues for some users BUT at the same time it opens known security holes for them?

This is just not an option and for users that have problems with Flash and won't use Chrome only two options exist:

1.) Adobe fixes Flash problems.
2.) There is no Flash anymore for Linux users that don't want to use Chrome and have problems with latest Flash.

I don't see other options right now for users that have problems with latest Flash and none of the "workarounds" work for them with latest Flash version. 

Running software that has "web access" and known security holes is just not an option and therefore downgrading Flash should not be mentioned at all as it's not the solution for the problem as it only creates way larger security problems!

I don't like it either, but everyone is doing and this is spread all over the place. Noboy is warning other users, which was one of the reasons I created this thread, so I could include a red warning and offer explanation how to secure flash. If people will do it anyway, at least they will be informed about the consequences and possible security measures.

The fact is that Adobe won't fix it. Flash is dead on Linux, until Chorme releases the Pepper API.

Anyway, I will consult the other staff to know their opinion.

---

### Post by claracc on 2012-04-08
I havent'had any problem with new adobe flash plugin in my hp compaq 6720s laptop wwith VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) and lucid lynx.

But in my old laptop pentium III, CPU 1GHz, 512 Mb ram from which 64 MB go for old sis 630 video card, new adobe flash plugin causes epiphany browser 2.30.6 to crash, the other browser in this laptop, chromium, says It has lost the flash plugin. 

So, for me, to downgrade flash plugin is a solution to surf the web the way I did, of course I will have to use block ads in epiphany and also ads and flash block in chromium.

I prefer to use epiphany in this machine since chromium uses a lot of CPU in this old laptop. I have tried to use gnash plugin but newspaper pages with streaming flash videos don't recognizes the plugin, so for me it is useless. I also have seen linterna magica but I havent tried, someone?

As I see the problem, the linux solution has to go in the address marked by apps like flash videoreplacer developed by lovinglinux, but for all kinds of containers of streaming flash videos ( I mean for example brightcove platform used by some newspapers), I am not a developer and I don't know about the work it would suppose. It is clear video players as sm player play converted videos with far less cpu load and in very good quality.

In my old pentium III laptop all adobe flash players play streaming flash videos in low motion, except the ones in youtube since I have installed a greasymonkey script viewtube to avoid flash, but this is only a solution for youtube.

Sorry for the long post, but  adobe flash problem requires a lot of reflections.

---

### Post by Eromatic on 2012-04-08
I found a possible workaround by using Compiz to swap the red and blue channels, but you do need to keep the buggy flash and hardware acceleration enabled for the following to work:

Within the CompizConfig Settings Manager, you will need to enable the Color filter plugin. Go into the Color filter plugin settings and select New (Located below the Filters files list.) Add the swap-red-blue filter to the list.

You should be able to find the swap-red-blue filter at:
/usr/share/compiz/colorfilter/data/filters/swap-red-blue

To activate the filter for the current window that you wish to use the filter on, within the active playing window, press the hotkey for Toggle window filtering. Then press the hotkey multiple times for Switch filter until you get to the swap-red-blue filter. This should reverse the smurf effect within the flash video, but the filter will reverse the color channels for everything else within the window. 

Press the Toggle window filtering hotkey within the desired window whenever you want to enable or disable the color filter.

---

### Post by joris1977 on 2012-04-08
Hi Lovinglinux, I am loving your flash-aid plugin. It makes it a lot easier to solve stupid flash issues. Maybe you could consider to make downgrading to flash 11.1.102.63 an option with a small explanation why this will fix  problems for a lot of people.

I just spend a whole afternoon on fixing a friends computer where the flash plugin had broken all of a sudden. (old Radeon card) A lot of people advice to install your plugin when having flash trouble, and this is good advice, but it will not solve the troubles with the current version of the flash plugin.

And I hope HTML5 will be here soon, because I hate wasting my time on the mess flash and silverlight have created for linux users...

---

### Post by keithpeter on 2012-04-08
Hello All

Fresh install of 12.04 on an Asus EeePC 1000 just now: installed ubuntu-restricted-extras, some youtube videos not playing, showing the 'plugin' warning. Other videos did play (smaller ones). Right clicking revealed that YouTube had switched to HTML5 'trial'. The only codec missing was HS.xxx.

I used the 'downgrade' instructions (with the addition of NoScript) and now flash is working on all videos. I had to restart before Firefox about:plugins command saw the plugin.

One hopes for an all HTML5 solution to this one...

Thanks for putting the instructions (and security warning) out.

Oddly enough, the PC with nvidia GT520 card and proprietary drivers is working fine...

---

### Post by Deskjockey on 2012-04-08
Thanks lovingLinux, the first method worked for me.

---

### Post by elphaba on 2012-04-08
I just solved my adobe flash plugin problem on firefox by installing Opera.  Not sure if the problem I was having was like that of others but having a browser that works now is great.  (my problem showed when I couldn't use the "interactive" chart option on finance.yahoo.com - works great now with Opera)

Opera downloads at: [http://www.opera.com/download/](http://www.opera.com/download/)

I downloaded the file for "linux" which was a .deb file and which I accessed from a terminal session.  No errors during installation. 

I don't think it will automatically update when there are new versions. I will need to stay on top of it if I want to keep current.

---

### Post by lovinglinux on 2012-04-08
> **Eromatic said:**
> I found a possible workaround by using Compiz to swap the red and blue channels, but you do need to keep the buggy flash and hardware acceleration enabled for the following to work:

Within the CompizConfig Settings Manager, you will need to enable the Color filter plugin. Go into the Color filter plugin settings and select New (Located below the Filters files list.) Add the swap-red-blue filter to the list.

You should be able to find the swap-red-blue filter at:
/usr/share/compiz/colorfilter/data/filters/swap-red-blue

To activate the filter for the current window that you wish to use the filter on, within the active playing window, press the hotkey for Toggle window filtering. Then press the hotkey multiple times for Switch filter until you get to the swap-red-blue filter. This should reverse the smurf effect within the flash video, but the filter will reverse the color channels for everything else within the window. 

Press the Toggle window filtering hotkey within the desired window whenever you want to enable or disable the color filter.

Interesting. I will add thsi to the first post.

> **joris1977 said:**
> Hi Lovinglinux, I am loving your flash-aid plugin. It makes it a lot easier to solve stupid flash issues. Maybe you could consider to make downgrading to flash 11.1.102.63 an option with a small explanation why this will fix  problems for a lot of people.

I just spend a whole afternoon on fixing a friends computer where the flash plugin had broken all of a sudden. (old Radeon card) A lot of people advice to install your plugin when having flash trouble, and this is good advice, but it will not solve the troubles with the current version of the flash plugin.

And I hope HTML5 will be here soon, because I hate wasting my time on the mess flash and silverlight have created for linux users...


You can use Flash-Aid to easily install any version. The only drawback is that you need to download the package from Adobe. See istructions in the first post.

I have thought about the possibility of introducing a downgrade option in Flash-Aid. However, in addition to the security concerns, I am not allowed to distribute flash directly and Adobe only provides those huge files with builds for Windows, Mac and Linux. So it is simpler to just provide the custom installation option in the Advanced mode.

> **Deskjockey said:**
> Thanks lovingLinux, the first method worked for me.

You are welcome.

> **keithpeter said:**
> Hello All

Fresh install of 12.04 on an Asus EeePC 1000 just now: installed ubuntu-restricted-extras, some youtube videos not playing, showing the 'plugin' warning. Other videos did play (smaller ones). Right clicking revealed that YouTube had switched to HTML5 'trial'. The only codec missing was HS.xxx.

I used the 'downgrade' instructions (with the addition of NoScript) and now flash is working on all videos. I had to restart before Firefox about:plugins command saw the plugin.

One hopes for an all HTML5 solution to this one...

Thanks for putting the instructions (and security warning) out.

Oddly enough, the PC with nvidia GT520 card and proprietary drivers is working fine...

You are welcome. Don't forget to remove the old plugin when they release a new flash version, if the problem goes away.

> **elphaba said:**
> I just solved my adobe flash plugin problem on firefox by installing Opera.  Not sure if the problem I was having was like that of others but having a browser that works now is great.  (my problem showed when I couldn't use the "interactive" chart option on finance.yahoo.com - works great now with Opera)

Opera downloads at: [http://www.opera.com/download/](http://www.opera.com/download/)

I downloaded the file for "linux" which was a .deb file and which I accessed from a terminal session.  No errors during installation. 

I don't think it will automatically update when there are new versions. I will need to stay on top of it if I want to keep current.

I like Opera as well. It is not perfect, but flash is working better than Firefox in terms of stability and performance. I have issues on some sites, like justin.tv, which has a terrible delay when clicking flash controls, but it might be because of other stuff in the pages.

---

### Post by DMustaine on 2012-04-08
OK, fixed... but where? Here's the steps I took:

adding this line to  /etc/adobe/mms.cfg
EnableLinuxHWVideoDecode=1
File doesn't exist. Unable to implement.

I tried to downgrade from the other thread with no success...

Following this threads options I found in the /usr/lib/bin/mozilla/plugins a file names something like "flash alternative" and renamed it to .old

copied and pasted the file "*libflashplayer.so"* into said folder and still no go.

Added "flash-aid" to Firefox and upon installing saw flash-aid display the following error: "Remove conflicting flash installations and install the appropriate version according to Ubuntu system architecture." 
This is still showing for flash-aid

Went to software manager, searched installed, and removed the flash plugin.

now all works fine.

Don't know what to say. VERY frustrating, and confusing to a "casual" user. I'm going to remove the flash-aid add-on and see what happens. I'll reply with the results.

---

### Post by DMustaine on 2012-04-08
> **DMustaine said:**
> ...Don't know what to say. VERY frustrating, and confusing to a "casual" user. I'm going to remove the flash-aid add-on and see what happens. I'll reply with the results.


OK flash-aid removed, no conflict reported, and youtube, and a few other flash type video sites I tried all work properly.

Bizarre, I wish I documented which version of flash I removed from the software manager, but I do know it was 10.xxxxxx


THANK YOU for all the help and work lovinglinux.

I can't tell you how infuriated I was but this. I use Ubuntu to surf exclusively. I dual-boot but have found no reason to go to Windows for months on end (except remote work sessions). I was about to give up on Ubuntu completely tomorrow if I couldn't get this fixed. Sad isn't it? Unable to watch ONLY youtube.com videos brought me to that decision... ALL other tube sites, and flash videos I've tried worked fine. It was only youtube that smurfed (and I tried a LOT of older / probably disreputable sites trying to replicate the error).

Maybe it's something to discuss with Youtube instead of flash. I really tried probably 100 of the most common flash sites with no problem. 

Thank you again, and I hope my comments are helpful, and my reply with the output of the diag as well.

---

### Post by lovinglinux on 2012-04-08
> **DMustaine said:**
> OK, fixed... but where? Here's the steps I took:

adding this line to  /etc/adobe/mms.cfg
EnableLinuxHWVideoDecode=1
File doesn't exist. Unable to implement.

If you follow the tutorial, it will create the file for you. All you need is to run the command as suggested, add the line, then save it.

```
gksudo gedit /etc/adobe/mms.cfg
```

> **DMustaine said:**
> Following this threads options I found in the /usr/lib/bin/mozilla/plugins a file names something like "flash alternative" and renamed it to .old

copied and pasted the file "*libflashplayer.so"* into said folder and still no go.

Is not /usr/lib/bin/mozilla/plugin. Where did you get that information? The correct folder is ~/.mozilla/plugins, which is under your home directory. There is no need to mess with system files.  If you enter *[I].mozilla*[/I] folder in your home and there is no ***plugins*** folder inside it, just create it and place the *libflashplayer.so* there.

> **DMustaine said:**
> Added "flash-aid" to Firefox and upon installing saw flash-aid display the following error: "Remove conflicting flash installations and install the appropriate version according to Ubuntu system architecture." 
This is still showing for flash-aid

I don't understand where you get such "error" in Flash-Aid. That is the description of the add-on. Please post a screenshot so I can understand what you are trying to do.

> **DMustaine said:**
> Don't know what to say. VERY frustrating, and confusing to a "casual" user. I'm going to remove the flash-aid add-on and see what happens. I'll reply with the results.

When you are not using Flash-Aid, it doesn't do anything. So if you didn't executed the Flash-Aid Wizard or Advanced mode, it didn't do anything to your system. Removing it won't make any difference either.

---

### Post by QIII on 2012-04-09
> **gradinaruvasile said:**
> Nah, its not THAT bad. If you have a decent enough CPU, unticking that hardware option (first image) will remove the smurf effects and you can play 1080p with no issues.

I'm quite sure I don't say I was having any problem other than that a site I use requires the lastest update.  I've never encountered smurfing and 1080p works fine.  But thanks for asking.

---

### Post by wbosher on 2012-04-09
Hi guys,
 
I am also having trouble with Firefox (well my wife is), it is also happening with Chromium. She is finding Facebook games unresponsive. You Tube movies play fine other than cranking the CPU up to about 65%.
 
Is this likely to be caused by the same problem as everyone is experiencing here?
 
I am going to try to disable hardware acceleration as suggested when I get home from work, but I am just wondering if anyone else has had the same problem with Facebook.
 
I have a dual boot with Windows XP, but I am trying to gradually wean her off Windows and this Facebook Issue isn't helping my cause. :(
 
Cheers for all the advice guys, much appreciated.

---

### Post by gradinaruvasile on 2012-04-09
> **wbosher said:**
> Hi guys,
 
I am also having trouble with Firefox (well my wife is), it is also happening with Chromium. She is finding Facebook games unresponsive. You Tube movies play fine other than cranking the CPU up to about 65%.
 
Is this likely to be caused by the same problem as everyone is experiencing here?
 
I am going to try to disable hardware acceleration as suggested when I get home from work, but I am just wondering if anyone else has had the same problem with Facebook.
 
I have a dual boot with Windows XP, but I am trying to gradually wean her off Windows and this Facebook Issue isn't helping my cause. :(
 
Cheers for all the advice guys, much appreciated.

Facebook games typically have issues with Linux flash. But in my wife's experience Chrome/Chromium works best (even with the latest flash) with Facebook games. But it might depend on video cards, drivers etc. CPU usage is high, but thats expected of anything that uses Flash.

---

### Post by gradinaruvasile on 2012-04-09
> **lovinglinux said:**
> 

Is not /usr/lib/bin/mozilla/plugin. Where did you get that information? The correct folder is ~/.mozilla/plugins, which is under your home directory. There is no need to mess with system files.


There is a system folder: 

/usr/lib/mozilla/plugins/

is the correct folder where browsers look for plugins by default. And the flash deb installers might link stuff all over the place, but the only interesting places are ~/.mozilla/plugins (user-specific) or /usr/lib/mozilla/plugins/ (system-wide). The naming of the plugins .so file also might differ, browsers pick them up anyway.
The "about:plugins" url is present in all browsers i believe and it will show discovered plugins. I never had any issues with multiple plugins, i just verified the paths and disabled those i didnt want. Very easy to do in any browser.

---

### Post by lovinglinux on 2012-04-09
> **gradinaruvasile said:**
> There is a system folder: 

/usr/lib/mozilla/plugins/

is the correct folder where browsers look for plugins by default.

Yes, that is exactly the place where Flash-Aid puts the *libflashplayer.so* file if you need to install flash for all users, like described in the first post. However, the user I was replying to was talking about /usr/lib/bin/mozilla/plugin, which is not the same and not mentioned in my tutorial. In fact I don't even mention /usr/lib/mozilla/plugins/, because Flash-Aid takes care of putting it there and setting up the proper file ownership and permissions.

---

### Post by wbosher on 2012-04-10
I disabled hardware acceleration in Firefox and Facebook games are playing ok now, still a little bit slow but much better. Chromium doesn't work.
 
One more small step in converting my wife.  :p

---

### Post by bcschmerker on 2012-04-13
Thanks for the heads up on the backgrade option.  In my case, I have issues with the audio on the [Userplane® video chat](http://www.userplane.com/), in terms of choppy audio transmission; I haven't encountered audio problems elsewhere so far where Flash is needed.  A test run of the in-beta (as of 13 April 2012) Adobe® Flash 11.3.300 on an Asus® CM1630-06 (upgraded with audio and video hardware) under Microsoft® Windows® 7.0.8001 (MultiProcessor Kernel 6.1.7601) has not resulted in a complete remedy w/r/t the Userplane® video chat audio issue; I still have the same chop as with Flash 11.2.202.228.

Several Websites that require Adobe® Flash for basic audio functionality are monitoring this situation closely, as W3C Hypertext Markup Language 5 is not a one-for-one replacement for Flash in their respective cases.

---

### Post by pickarooney on 2012-04-13
I'm still stuck on this. With the latest version and hardware acceleration disabled the smurf problem is gone but every video freezes after a while (audio continues). 

I've tried unpacking an older version from another thread on here but that has the same freezing problem.

This didn't happen in whatever version I had last month. What's the best way to roll back?

---

### Post by lovinglinux on 2012-04-13
> **pickarooney said:**
> I'm still stuck on this. With the latest version and hardware acceleration disabled the smurf problem is gone but every video freezes after a while (audio continues). 

I've tried unpacking an older version from another thread on here but that has the same freezing problem.

This didn't happen in whatever version I had last month. What's the best way to roll back?

Delete any flash downloaded manually and install version 11.2.202.228 from the repositories. You can easily do that with Flash-Aid. Then enable hardware acceleration. The Smurf effect will be back. Then try this:

[http://www.wiredrevolution.com/ubuntu/fix-blue-tinted-video-in-ubuntu](http://www.wiredrevolution.com/ubuntu/fix-blue-tinted-video-in-ubuntu)

I am not sure if it works with Flash, but worth a try.

---

### Post by pickarooney on 2012-04-13
Cool, with your extension I was able to install that version of flash and so far, even with hardware acceleration the smurf effect is not there. I'll test it a bit more tomorrow as there are new nvidia drivers available for update. Thanks.

---

### Post by pickarooney on 2012-04-14
Now it's doing the same thing - video blocking, audio playing in HTML5 mode. Worse than ever really.

---

### Post by lovinglinux on 2012-04-14
> **pickarooney said:**
> Now it's doing the same thing - video blocking, audio playing in HTML5 mode. Worse than ever really.

nVidia has released a new driver. Although it doesn't cover the flash issues, it might worth a shot:

[http://www.unixmen.com/nvidia-295-40-is-available-install-in-ubuntu11-1012-04-linuxmint-via-ppa/](http://www.unixmen.com/nvidia-295-40-is-available-install-in-ubuntu11-1012-04-linuxmint-via-ppa/)

---

### Post by mc4man on 2012-04-14
I just put up a new 12.04 install (64bit) using the nvidia 295.40 & flash version in screen
So far no blue

---

### Post by ajgreeny on 2012-04-14
I have just downloaded the flash tar.gz  11.2.202.233 from adobe and extracted the libflashplayer.so from it.  I then copied this new version to replace the 11.1r102 which had been the last that worked on my machines, and much to my surprise it worked with no problems.

The 11.2.202.228 previously available had not worked at all in my systems.  This must also be worth a look-see by those who have the "smurf effect" from version 11.2.202.228.

Were Adobe shamed into doing something to overcome the problem after all?

---

### Post by lovinglinux on 2012-04-14
> **ajgreeny said:**
> I have just downloaded the flash tar.gz  11.2.202.233 from adobe and extracted the libflashplayer.so from it.  I then copied this new version to replace the 11.1r102 which had been the last that worked on my machines, and much to my surprise it worked with no problems.

The 11.2.202.228 previously available had not worked at all in my systems.  This must also be worth a look-see by those who have the "smurf effect" from version 11.2.202.228.

Were Adobe shamed into doing something to overcome the problem after all?

I don't think they did anything to fix the problem. I think is just a coincidence this problem went away with this update. It happened before.

Would be nice if anyone can test it on a nVidia machine and check if it still cause the SMURF effect.

---

### Post by Eromatic on 2012-04-14
The color channel swap issue (smurf effect) still remains on my computer. This is with hardware acceleration enabled within the Flash Player Display Settings, and while using the following:

Adobe Flash: 11,2,202,233
X Updates PPA: nvidia-graphics-drivers 	295.40-0ubuntu1~natty~xup1 
Firefox 11.0
nvidia 9500GT

---

### Post by lovinglinux on 2012-04-14
> **Eromatic said:**
> The color channel swap issue (smurf effect) still remains on my computer. This is with hardware acceleration enabled within the Flash Player Display Settings, and while using the following:

Adobe Flash: 11,2,202,233
X Updates PPA: nvidia-graphics-drivers 	295.40-0ubuntu1~natty~xup1 
Firefox 11.0
nvidia 9500GT

Thanks for the info. I suppose disabling hardware acceleration still works as solution with that version, right?

---

### Post by Eromatic on 2012-04-14
> **lovinglinux said:**
> Thanks for the info. I suppose disabling hardware acceleration still works as solution with that version, right?
Correct.

---

### Post by lovinglinux on 2012-04-14
I have updated Flash-Aid download url to get flash version 11.2.202.233. If you want that version (not recommended for nVidia users), click "Check Update" in the extension menu, wait for the warning that a new version is available and then run the Wizard again, selecting the BETA option.

---

### Post by mc4man on 2012-04-14
> **lovinglinux said:**
> I don't think they did anything to fix the problem. I think is just a coincidence this problem went away with this update. It happened before.

Correct - on a new install 'no blue' lasted for a  restart or 2, now back llke before

---

### Post by bcschmerker on 2012-04-14
Adobe Systems has Flash 10.3.183.18 available at [www.Adobe.com/Products/FlashPlayer/Distribution3.html]("http://www.adobe.com/products/flashplayer/distribution3.html").  In addition to the usual Executables and MSI's for Microsoft® Windows® 6-up and a DMG for Apple® MacOS X® on Intel-based systems, Adobe provides Red Hat® RPM's and GZip source packages for LinUX systems at the page cited (no Debian® DEB's as of 14 April 2012).

**Addendum:**  Be advised that, as of 15 April 2012, Adobe® Labs only has Flash Player 11.3.300.214 for Microsoft® Windows® 6-up (EXE's for ActiveX and Plug-in) and Apple® MacOS X® 10.5-up (DMG).

---

### Post by andrew.46 on 2012-04-15
Thanks, flash is now working here :).

---

### Post by ajgreeny on 2012-04-15
> **bcschmerker said:**
> Adobe Systems has Flash [COLOR=Red]11.3.183.18[/COLOR] available at [www.Adobe.com/Products/FlashPlayer/Distribution3.html]("http://www.adobe.com/products/flashplayer/distribution3.html").  In addition to the usual Executables and MSI's for Microsoft® Windows® 6-up and a DMG for Apple® MacOS X® on Intel-based systems, Adobe provides Red Hat® RPM's and GZip source packages for LinUX systems at the page cited (no Debian® DEB's as of 14 April 2012).
Don't get too excited!  It is [COLOR=Red]10[/COLOR].3.183.18, not [COLOR=Red]11[/COLOR].3.183.18

I have also found this morning that 11.2.202.233 only works on one of my machines, not all of them, so back to the drawing board, I'm afraid, and I'll have to stick with 11.1r102.

---

### Post by pickarooney on 2012-04-16
> **lovinglinux said:**
> nVidia has released a new driver. Although it doesn't cover the flash issues, it might worth a shot:

[http://www.unixmen.com/nvidia-295-40-is-available-install-in-ubuntu11-1012-04-linuxmint-via-ppa/](http://www.unixmen.com/nvidia-295-40-is-available-install-in-ubuntu11-1012-04-linuxmint-via-ppa/)

Strange... I added that PPA and tried to update but apt told me I had the latest version. nVidia settings tool tells me I have 295.33

---

### Post by terrykiwi83 on 2012-04-16
I was just curious to whether Adobe ever made a fix for the issue with Flash 11 x64 in regards to all people being blue on You-tube and flash videos in general?

Its not looking promising since they pulled support as far as am aware?

---

### Post by Frogs Hair on 2012-04-16
You may want to search for other threads because I remember seeing some reports of blue people . I have never had problems with flash.

---

### Post by lovinglinux on 2012-04-16
> **terrykiwi83 said:**
> I was just curious to whether Adobe ever made a fix for the issue with Flash 11 x64 in regards to all people being blue on You-tube and flash videos in general?

Its not looking promising since they pulled support as far as am aware?

They didn't and they won't.

The problem might be solved when when Google releases PepperFlash.

BTW, the development build of Chrome 64bit already has PepeprFlash.

---

### Post by Herpythebrony on 2012-04-16
On my Lubuntu machine. Flash works with flash aid and disabling hardware acceleration.

---

### Post by DMustaine on 2012-04-18
> **lovinglinux said:**
> If you follow the tutorial, it will create the file for you. All you need is to run the command as suggested, add the line, then save it.

It didn't create the file... don't know why.



> **lovinglinux said:**
> Is not /usr/lib/bin/mozilla/plugin. Where did you get that information? The correct folder is ~/.mozilla/plugins, which is under your home directory. There is no need to mess with system files.  If you enter *[I].mozilla*[/I] folder in your home and there is no ***plugins*** folder inside it, just create it and place the *libflashplayer.so* there.


Didn't know that, and it wasn't explained. There was no plugins folder. I did a search and the only libflashplayer.so I found in the entire system was in the  /usr/lib/bin/mozilla/plugin folder, so I assumed that was the one to replace.

It's fixed now like I said and I don't know which step did it. There still is no folder ~/.mozilla/plugins"

---

### Post by bcschmerker on 2012-04-25
> **lovinglinux said:**
> ...Is not /usr/lib/bin/mozilla/plugin. Where did you get that information? The correct folder is ~/.mozilla/plugins, which is under your home directory. There is no need to mess with system files.  If you enter *[I].mozilla*[/I] folder in your home and there is no ***plugins*** folder inside it, just create it and place the *libflashplayer.so* there....
On my own rig running 10.04.4-LTS, there is no /usr/lib/bin, but two different Subdirectories of /usr/lib that do exist are involved.  APT currently places the Adobe® Flash™ Player plugin, libflashplayer.so, in /usr/lib/adobe-flashplugin, and a symbolic link thereto in /usr/lib/mozilla/plugins.  The user subdirectory ~/.mozilla/plugins (a sub-subdirectory of /home) would be useful for experimental plug-ins lib*.so that need be kept to one User's Profiles in the Mozilla® applications.

---

### Post by lovinglinux on 2012-04-25
> **bcschmerker said:**
> On my own rig running 10.04.4-LTS, there is no /usr/lib/bin, but two different Subdirectories of /usr/lib that do exist are involved.  APT currently places the Adobe® Flash™ Player plugin, libflashplayer.so, in /usr/lib/adobe-flashplugin, and a symbolic link thereto in /usr/lib/mozilla/plugins.  The user subdirectory ~/.mozilla/plugins (a sub-subdirectory of /home) would be useful for experimental plug-ins lib*.so that need be kept to one User's Profiles in the Mozilla® applications.

The problem with /usr/lib/adobe-flashplugin and /usr/lib/flashplugin-installer is that once the package manager updates flash, the manually installed file will be replaced. That is why I suggest ~/.mozilla/plugins. Several users already complained about the updates, because they followed a tutorial the suggests placing the plugin in the /usr/lib/flashplugin-installer folder. However, if you remove *flashplugin-installer* and *adobe-flashplugin* packages before copying the .so, then it will not be affected by the updates. Flash-Aid removes both packages, plus gnash, lightspark and manually installed files and place the .so under /usr/lib/mozilla/plugins.

---

### Post by forrestcupp on 2012-04-25
Great work. With all of the Flash support requests, this really should be a sticky, maybe even in General Help, also.

---

### Post by oslub on 2012-04-29
Hello, I am having trouble with flash plugin as well. I run Lubuntu on an desktop with these configurations: 
Intel Pentium 4E, 2800 MHz (5.25 x 533), 1014 MB  (DDR SDRAM), Graphic  adapter Intel(R) 82865G Graphics Controller  (96 MB), motherboard  P4i65G.

Both on Chromium and Firefox, I have increasingly more and more trouble watching videos, even in low quality and also most of webpages I visit load slowly and freeze a lot, images take a long time to load, this gets worse at each new release of flash. It is not exclusively on linux, on windows XP I can no longer watch online streamings as well as I could before, I thought it was due to my desktop old configurations but apparently flash is a big responsible as well. 

However, on XP I can still visit most websites without any major trouble and only videos are running slowly. On Lubuntu, not only videos, but also webpages in general take a lot of time to load,  it's really annoying that scrolling a page, editing a doc in google  docs or loading a new tab takes forever... I can't work with more than 3/4 opened tabs.

Disabling hardware acceleration on youtube helped a little, although it still freezes a bit and some videos keep making chromium crash, even in normal mode (not fullscreen) and sometimes even before the video starts. On Firefox the crashes don't happen. I installed flashvideoreplacer on my firefox but for some  odd reason, in the menu, only the preferences and quality options are  working, the  copy url or download won't do any action, this seems some sort of bug,  If I don't disable the add-on, instead of the  video there is just a black square. I also tried to select external method and chose GNOME  player, but  nothing happens. I already removed and reinstalled the add-on again. So far I've been using flashgot add-on to download the video from youtube and watch it on GNOME (good thing I have a decent internet connection). I'm not really comfortable with security issues involved with downgrading flash, so other options would be welcome.

I would be already satisfied with playing the videos on GNOME or VLC without having to download. 
About the slow and freezing web browsing, accordingly with the rest of the posts here, I guess all we can do is to wait for the Chrome solution...  

It's frustrating because this is pretty much the only thing that keeps me from leaving XP on this machine, overall Lubuntu performance is much lighter and faster than XP in here and besides Microsoft is pratically dumping XP and forcing upgrade, while Lubuntu allows me to still make use of it for some time more.

---

### Post by lovinglinux on 2012-04-29
> **oslub said:**
> Hello, I am having trouble with flash plugin as well. I run Lubuntu on an desktop with these configurations: 
Intel Pentium 4E, 2800 MHz (5.25 x 533), 1014 MB  (DDR SDRAM), Graphic  adapter Intel(R) 82865G Graphics Controller  (96 MB), motherboard  P4i65G.

Both on Chromium and Firefox, I have increasingly more and more trouble watching videos, even in low quality and also most of webpages I visit load slowly and freeze a lot, images take a long time to load, this gets worse at each new release of flash. It is not exclusively on linux, on windows XP I can no longer watch online streamings as well as I could before, I thought it was due to my desktop old configurations but apparently flash is a big responsible as well. 

However, on XP I can still visit most websites without any major trouble and only videos are running slowly. On Lubuntu, not only videos, but also webpages in general take a lot of time to load,  it's really annoying that scrolling a page, editing a doc in google  docs or loading a new tab takes forever... I can't work with more than 3/4 opened tabs.

Disabling hardware acceleration on youtube helped a little, although it still freezes a bit and some videos keep making chromium crash, even in normal mode (not fullscreen) and sometimes even before the video starts. On Firefox the crashes don't happen. I installed flashvideoreplacer on my firefox but for some  odd reason, in the menu, only the preferences and quality options are  working, the  copy url or download won't do any action, this seems some sort of bug,  If I don't disable the add-on, instead of the  video there is just a black square. I also tried to select external method and chose GNOME  player, but  nothing happens. I already removed and reinstalled the add-on again. So far I've been using flashgot add-on to download the video from youtube and watch it on GNOME (good thing I have a decent internet connection). I'm not really comfortable with security issues involved with downgrading flash, so other options would be welcome.

I would be already satisfied with playing the videos on GNOME or VLC without having to download. 
About the slow and freezing web browsing, accordingly with the rest of the posts here, I guess all we can do is to wait for the Chrome solution...  

It's frustrating because this is pretty much the only thing that keeps me from leaving XP on this machine, overall Lubuntu performance is much lighter and faster than XP in here and besides Microsoft is pratically dumping XP and forcing upgrade, while Lubuntu allows me to still make use of it for some time more.

Flash has become a CPU hungry application on any OS, that's why Apple banned it from iPad. On Linux it has even more problems with hardware acceleration and performance. Because of that, machines with a configuration like yours will struggle to play flash videos, even on low resolutions. I recommend at least a Dual Core to get smooth flash playback. Unfortunately, there is much we can do. Perhaps now that Google will be developing PepperFlash things might get better, but being forced to use Chrome is not a good thing on on itself.

Anyway, your issues are not exactly related to the issues of this thread, since most affected users are those who own nvidia cards. I suggest you check these tutorials and threads:

For flash troubleshooting and optimization: [http://ubuntuforums.org/showthread.php?t=1517564](http://ubuntuforums.org/showthread.php?t=1517564)

For Flash-Aid support: [http://ubuntuforums.org/showthread.php?t=1491268](http://ubuntuforums.org/showthread.php?t=1491268)

For FlashVideoReplacer support: [http://ubuntuforums.org/showthread.php?t=1487327](http://ubuntuforums.org/showthread.php?t=1487327)

---

### Post by malcolmcdixon on 2012-05-01
Managed to get flash player going by down grading flash as suggested above, after trying everything else, although will not work on some sites or some youtube videos, maybe my video card is not liked by the new flash version? it was just a black empty box!
have attached a fire fox report as suggested above if its any help, cheers

---

### Post by jamesmika on 2012-05-04
Can Wine help us?

Firefox for Wine works well. The latest flash plugin installer doesn't run under wine. We do not need the flash plugin installer. We only need the flash plugin. Can we somehow extract the plugin, without using Windows?

Does the Windows flash plugin work with Windows Firefox under wine?

Tested with Firefox 32 bit. And Flash Plugin 32 bit. Those offline installers are working.
[http://fpdownload.macromedia.com/get/flashplayer/current/licensing/win/install_flash_player_11_plugin_32bit.exe](http://fpdownload.macromedia.com/get/flashplayer/current/licensing/win/install_flash_player_11_plugin_32bit.exe)
[http://fpdownload.macromedia.com/get/flashplayer/current/licensing/win/install_flash_player_11_plugin_64bit.exe](http://fpdownload.macromedia.com/get/flashplayer/current/licensing/win/install_flash_player_11_plugin_64bit.exe)

Fullscreen doesn't work. No complete solution.

---

### Post by Dlambert on 2012-05-04
Does this problem affect the Google Chrome built in flash? I though flash was dropped on Linux, and would only be released through chrome "pepper"? [http://blogs.adobe.com/flashplayer/2012/02/adobe-and-google-partnering-for-flash-player-on-linux.html](http://blogs.adobe.com/flashplayer/2012/02/adobe-and-google-partnering-for-flash-player-on-linux.html)

---

### Post by addicted_to_the_net on 2012-05-05
Thank you so much! This Flash problem has been driving me nuts! After following your instructions for downgrading using flash-aid, my Firefox is displaying flash again.

---

### Post by Throne777 on 2012-05-07
I'm getting the Smurf effect in BOTH Firefox & Chrome :s
Not consistently though. For instance, The Expendables 2 trailer was the Smurf Edition, yet the Dark Knight Rises trailer was Smurf free.

---

### Post by jamesmika on 2012-05-08
Still doesn't work for me. Neither Firefox nor Chrome. I downgraded to 11.1.102.63. (Checked with about:plugins)

Still lags heavily and I can't exit from full screen.

The problem occurred first on precise. I have a ATI graphics card. There was no lag and no other problems on oneirirc.

Please help.

---

### Post by bcschmerker on 2012-05-10
> **jamesmika said:**
> Still doesn't work for me. Neither Firefox nor Chrome. I downgraded to 11.1.102.63. (Checked with about:plugins)

Still lags heavily and I can't exit from full screen....Looks as though ye might need Flash&#8482; 10.3.183.18, which Adobe Systems maintains for operating systems that cannot use Flash 11.x.  I still need to check on the Chrome&#8482; OS and which company Google® contracted with for maintenance and updates thereof.

Several distros, including the now-extinct gOS® (a product of Good OS LLC), relied on Canonical® in the recent past, and I cannot rule out the possibility that Google® may have revived the GooglePC.com Website to maintain Chrome&#8482; OS.  Adobe Systems and Google Inc. are developing the Pepper&#8482; plug-in as a LinUX-ready parallel to Flash&#8482; Players 11.3-up in both Microsoft® Windows® 6.0.60xx, 6.1.76xx and 7.0.80xx; and Apple® Mac OS® X&#8482; 10.7-up.

---

### Post by lovinglinux on 2012-05-12
> **jamesmika said:**
> Can Wine help us?

Firefox for Wine works well. The latest flash plugin installer doesn't run under wine. We do not need the flash plugin installer. We only need the flash plugin. Can we somehow extract the plugin, without using Windows?

Does the Windows flash plugin work with Windows Firefox under wine?

Tested with Firefox 32 bit. And Flash Plugin 32 bit. Those offline installers are working.
[http://fpdownload.macromedia.com/get/flashplayer/current/licensing/win/install_flash_player_11_plugin_32bit.exe](http://fpdownload.macromedia.com/get/flashplayer/current/licensing/win/install_flash_player_11_plugin_32bit.exe)
[http://fpdownload.macromedia.com/get/flashplayer/current/licensing/win/install_flash_player_11_plugin_64bit.exe](http://fpdownload.macromedia.com/get/flashplayer/current/licensing/win/install_flash_player_11_plugin_64bit.exe)

Fullscreen doesn't work. No complete solution.

It works under Wine. I have used Playonlinux to install it. First install Firefox using Playonlinux "install a non-listed program" tool. To install Flash use the same tool, but select the option to "Edit or update an existing application".

> **Dlambert said:**
> Does this problem affect the Google Chrome built in flash? I though flash was dropped on Linux, and would only be released through chrome "pepper"? [http://blogs.adobe.com/flashplayer/2012/02/adobe-and-google-partnering-for-flash-player-on-linux.html](http://blogs.adobe.com/flashplayer/2012/02/adobe-and-google-partnering-for-flash-player-on-linux.html)

PepperFlash is not implemented yet. Chrome 64bit development build already has PepperFlash, but it is unusable.

> **Throne777 said:**
> I'm getting the Smurf effect in BOTH Firefox & Chrome :s
Not consistently though. For instance, The Expendables 2 trailer was the Smurf Edition, yet the Dark Knight Rises trailer was Smurf free.

Have you tried one of the methods suggested in the first post?

---

### Post by bcschmerker on 2012-05-13
> **bcschmerker said:**
> ...I still need to check on the Chrome™ OS and which company Google® contracted with for maintenance and updates thereof....Update:  Adobe Systems has upgraded Flash™ Player 10 to  10.3.183.19, as of 13 May 2012.  Turns out, Chrome™ OS is targeted at netbooks and smaller and won't pack many critical functions already handled by Ubuntu®.

---

### Post by ex_isp on 2012-05-15
Personally, glad to see flash go.  Adobe has sucked for a long time IMHO.  If html5 can replace it, we are all better off.

BTW, the html5 and a restart of firefox (V12) solved the annoying smurf issue here!

Many thanks to all that contributed to this thread!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!;)

---

### Post by mc4man on 2012-05-20
Another 'fix' that I've found to work here is to use a patched libvdpau, it only is 'applied' when needed

ppa (you only need the libvdpau package, for some also the -dev package
[https://launchpad.net/~tikhonov/+archive/misc](https://launchpad.net/~tikhonov/+archive/misc)

referring comments
[https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/967091/comments/104](https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/967091/comments/104)
[https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/967091/comments/116](https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/967091/comments/116)
As usual YMMV

---

### Post by arizonalarry2 on 2012-06-07
I've done everything in this thread and nothing worked. I've spent the last three months trying to get any video anywhere to play with no success.

Then I stumbled across reply # 6 in this thread telling me to install Hal -

[http://ubuntuforums.org/showthread.php?t=1968972](http://ubuntuforums.org/showthread.php?t=1968972)


IT WORKS


Hey you Ubuntu guys do yourselves a favor - hire Corvax and put him in charge LOL

---

### Post by malcolmcdixon on 2012-06-07
:p This problem with flash has been bugging me crazy, after enjoying trouble free computing on Ubuntu 10.10 flash stopped working after an up date, I decided to upgrade to 11.10 but still could only get flash player working partially after down grading flash following the instructions at the beginning of this thread. 11.10 had gone a bit wonky after I had tried to use the windows version of Firefox and Flash using 'play on Linux'. Since my whole family totally enjoy Gnome Desk Top and asked me to "put the computer back to how it was" I found an old 10.04 disk and installed it, then downloaded  Flash Player 10.3.183.19 which Adobe still maintain. I downloaded [http://fpdownload.macromedia.com/get/flashplayer/current/licensing/linux/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/licensing/linux/install_flash_player_10_linux.tar.gz)   then using flash aid 'advanced mode' 'custom path' to the location of the downloaded file then 'text' 'execute' flash was installed and working fine and we are back on our favorite DE  bonus!  thanks all, malc ;)
**[COLOR=black]Extra Info[/COLOR]**
[COLOR=black]I'm not sure if there are security issues with flash player 10.3.183.19 as it is still maintained, however I have installed a flash blocker extension in fire fox anyway. malc.[/COLOR]

---

### Post by hueyafrosamurai on 2012-06-09
> **malcolmcdixon said:**
> :p This problem with flash has been bugging me crazy, after enjoying trouble free computing on Ubuntu 10.10 flash stopped working after an up date, I decided to upgrade to 11.10 but still could only get flash player working partially after down grading flash following the instructions at the beginning of this thread. 11.10 had gone a bit wonky after I had tried to use the windows version of Firefox and Flash using 'play on Linux'. Since my whole family totally enjoy Gnome Desk Top and asked me to "put the computer back to how it was" I found an old 10.04 disk and installed it, then downloaded  Flash Player 10.3.183.19 which Adobe still maintain. I downloaded [http://fpdownload.macromedia.com/get/flashplayer/current/licensing/linux/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/licensing/linux/install_flash_player_10_linux.tar.gz)   then using flash aid 'advanced mode' 'custom path' to the location of the downloaded file then 'text' 'execute' flash was installed and working fine and we are back on our favorite DE  bonus!  thanks all, malc ;)


Thanks so much, this worked for me. After trying all the others, this is  the only one to work. Now I just have to be careful in using an old  version of flash...

---

### Post by Grandma_DOG on 2012-06-09
+1   Turning off Hardware Accel worked for me.  Xubuntu 11.10




------------------------------------------------------
Many Linux problems can be solved via [OSInt]("http://deep-web.org/osint/"), the trick is to know where to look.

---

### Post by bcschmerker on 2012-06-09
> **malcolmcdixon said:**
> :p This problem with flash has been bugging me crazy, after enjoying trouble free computing on Ubuntu 10.10 flash stopped working after an up date, I decided to upgrade to 11.10 but still could only get flash player working partially after down grading flash following the instructions at the beginning of this thread. 11.10 had gone a bit wonky after I had tried to use the windows version of Firefox and Flash using 'play on Linux'. Since my whole family totally enjoy Gnome Desk Top and asked me to "put the computer back to how it was" I found an old 10.04 disk and installed it, then downloaded  Flash Player 10.3.183.19 which Adobe still maintain. I downloaded [http://fpdownload.macromedia.com/get/flashplayer/current/licensing/linux/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/licensing/linux/install_flash_player_10_linux.tar.gz)   then using flash aid 'advanced mode' 'custom path' to the location of the downloaded file then 'text' 'execute' flash was installed and working fine and we are back on our favorite DE  bonus!  thanks all, malc ;)
[B]
[/B]Thanks for a confirmation of Flash-Aid™, which I use on my 10.04.5-LTS desktop install and will probably use with 12.04.1-LTS once I have all the hardware I've preplanned for upgrading my hybrid Everex®.  Adobe Systems having halted development of Flash™ Player for LinUX with 11.2.202.* (11.2.202.236 is available as of 9 June 2012), which is unsatisfactory for several Websites still needing the Macromedia® software architecture for multimedia functionality, I am likewise using 10.3.183.20 (as of 9 June 2012) from FPDownload.Macromedia.com, selecting via the "Custom (http url or local path)" option:
```
http://fpdownload.macromedia.com/get/flashplayer/current/licensing/linux/install_flash_player_10_linux.tar.gz
```
I am using Flash™ Player 11.3.300.257 on my current Windows box but still waiting for Google® Code to get 64-bit Pepper up and running, so I can keep the data coming in and going out properly with 12.04.1-LTS, AMD64 Edition (to which I am preparing to upgrade the Everex®).  (10.3.183.20 is 32-bit only.)

---

### Post by klugja on 2012-06-30
Flash player 10 is the best solution for me!

Tried 11.1, tried turning acceleration off, all to no avail.  Flash video is completely blank, and flash hasn't worked in any browser but chrome for a long time (not opera or firefox).

I tried downloading flash 10, and it worked great.

I had been using Chrome, but since my update a couple of days ago, Chrome has a sandbox zombie, and the gui window never comes up.

I am using Nvidia and an Athlon XP 1800+ 32 bit processor.

When I boot windows on the same system, I am using the 11.3 flash player, and everything just works.

I hadn't been able to watch flash for some time at Reuters web site, (video was blank), and now it just works.

---

### Post by lovinglinux on 2012-06-30
> **klugja said:**
> Flash player 10 is the best solution for me!

Tried 11.1, tried turning acceleration off, all to no avail.  Flash video is completely blank, and flash hasn't worked in any browser but chrome for a long time (not opera or firefox).

I tried downloading flash 10, and it worked great.

I had been using Chrome, but since my update a couple of days ago, Chrome has a sandbox zombie, and the gui window never comes up.

I am using Nvidia and an Athlon XP 1800+ 32 bit processor.

When I boot windows on the same system, I am using the 11.3 flash player, and everything just works.

I hadn't been able to watch flash for some time at Reuters web site, (video was blank), and now it just works.

About Chrome see this:

[http://ubuntuforums.org/showthread.php?t=2011882](http://ubuntuforums.org/showthread.php?t=2011882)

Apparently, some Chrome users are experiencing issues with the new PepperFlash plugin. I am not, but it might be because my plugins are set to play with click.

---

### Post by klugja on 2012-07-01
My guess is the trouble lies with Adobe:

[Updated Flash crashes on start]("https://bugbase.adobe.com/index.cfm?event=bug&id=3154276")

---

### Post by bcschmerker on 2012-07-01
> **lovinglinux said:**
> About Chrome see this:

[http://ubuntuforums.org/showthread.php?t=2011882](http://ubuntuforums.org/showthread.php?t=2011882)

Apparently, some Chrome users are experiencing issues with the new PepperFlash plugin. I am not, but it might be because my plugins are set to play with click.
Thanks for the heads up on a settings-related issue for Pepper™, as I anticipate needing Chromium™ due to Adobe Systems terminating development of Flash™ Player for LinUX (needed by Mozilla® Firefox® 13-up) at 11.2.202.*.  As of 30 June 2012 I have all the hardware that I planned on for upgrading my hybrid Everex® to 12.04.1-LTS, AMD64 Edition, and await the dot-one Install ISO for both the system cited and an eMachines®/Acer® EL1210-09 rebuild that had operability problems with Kubuntu 10.04.3-LTS (as the original 12.04-LTS Install ISO has a dependencies problem, the fix for which will be released in the dot-one ISO).

---

### Post by xchecker on 2012-07-01
Still having Flash problems on my desktop with Firefox, Ubuntu 12.04 and NVidia graphics.

I had the 'smurf' problem but was able to fix that.

I disabled hardware acceleration.
I used Flash-Aid.
I am now running Flash version 11.1.102.63
I overwrote with 'libvdpau1' as suggested [[COLOR="Blue"]here[/COLOR]]("http://askubuntu.com/questions/117127/flash-video-appears-blue").

Flash videos still crash my system.

Do I need to delete other versions of Flash perhaps?  Or go back to version 10?  I've tried so many things by this point that I'm getting confused and quite frustrated.  Thanks!

---

### Post by mc4man on 2012-07-01
> **xchecker said:**
> Still having Flash problems on my desktop with Firefox, Ubuntu 12.04 and NVidia graphics.
I had the 'smurf' problem but was able to fix that.

I disabled hardware acceleration.
I used Flash-Aid.
I am now running Flash version 11.1.102.63
I overwrote with 'libvdpau1' as suggested [[COLOR="Blue"]here[/COLOR]]("http://askubuntu.com/questions/117127/flash-video-appears-blue").

Flash videos still crash my system.

Do I need to delete other versions of Flash perhaps?  Or go back to version 10?  I've tried so many things by this point that I'm getting confused and quite frustrated.  Thanks!

The best solution to the blue video is to not overwrite anything ect, but to use [the ppa for 12.04 to provide a patched libvdpau ]("https://launchpad.net/~tikhonov/+archive/misc")
In 12.10 ubuntu has applied the patch to libvdpau
(you can also just use the 12.10 versions of libvdpau, libvdpau-dev in 12.04, do so here (0.4.1-6ubuntu1

Other methods may lead to crashes, also with the patched libvdpau there is no need to disable hardware acceleration

---

### Post by xchecker on 2012-07-01
Thanks.  Using Flash-Aid I reinstalled the recommended version and then reupdated the libvdpau1 file from tikhanov and that seems to be working now - no more crashes.  I really appreciate the help.  Thanks!

---

### Post by snuffy47 on 2012-07-03
Hello All

I have been struggling with flash on my Presario 2100 for a week now

Ubuntu 12.04

When I go to a flash webpage it tells me I am missing the plugin.  I  have tried a few posts including pasting .so file from version 63.  That  seemed to work last night but it stopped this morining again.

Firefox and chrome no work.  To not for a while chrome would not even run it would just crash.

I think I have version 63 of flash installed.  Have flash aid installed

Currently utube works but other flash pages do not :(
                          ```
trevor@Presario:~$ sudo apt-cache search flashplayer 
 [sudo] password for trevor:  
 flashplugin-nonfree-extrasound - Adobe Flash Player platform support library for Esound and OSS 

``````
trevor@Presario:~$ sudo apt-cache show flashplugin-nonfree-extrasound 
 Package: flashplugin-nonfree-extrasound 
 Priority: optional 
 Section: multiverse/sound 
 Installed-Size: 64 
 Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com> 
 Original-Maintainer: Petter Reinholdtsen <pere@debian.org> 
 Architecture: i386 
 Version: 0.0.svn2431-3ubuntu1 
 Replaces: libflashsupport 
 Depends: libc6 (>= 2.3.4) 
 Recommends: flashplugin-installer 
 Conflicts: flashplugin-nonfree-pulse, libflashsupport 
 Filename: pool/multiverse/f/flashplugin-nonfree-extrasound/flashplugin-nonfree-extrasound_0.0.svn2431-3ubuntu1_i386.deb 
 Size: 8562 
 MD5sum: 1150ee717da87aab891f421f201835d4 
 SHA1: 10254f19f74ca403848958f61f584d290cb1b413 
 SHA256: 09340fd08ff50ab787dcd10f329d8eda051d64d7f217cf362d0a345bc378c373 
 Description-en: Adobe Flash Player platform support library for Esound and OSS 
  This is an open Source extension library for the Adobe Flash Player 
  that enables support for otherwise unsupported sound systems.  It 
  provides the libflashsupport.so plugin.  The sound system to use is 
  automatically detected: 
  . 
   * It first tries to detect Esound, 
   * Next, it checks for OSS. 
  . 
  If all of the above failed, it falls back to the ALSA driver that's 
  built directly into FlashPlayer 9. 
  . 
  For PulseAudio support, see flashplugin-nonfree-pulse. 
 Description-md5: 74ec5439ce259e0c156f5f983af2c21f 
 Bugs: https://bugs.launchpad.net/ubuntu/+filebug 
 Origin: Ubuntu
  
```I really need some help here :sad:

---

### Post by lovinglinux on 2012-07-03
> **snuffy47 said:**
> Hello All

I have been struggling with flash on my Presario 2100 for a week now

Ubuntu 12.04

When I go to a flash webpage it tells me I am missing the plugin.  I  have tried a few posts including pasting .so file from version 63.  That  seemed to work last night but it stopped this morining again.

Firefox and chrome no work.  To not for a while chrome would not even run it would just crash.

I think I have version 63 of flash installed.  Have flash aid installed

Currently utube works but other flash pages do not :(
                          ```
trevor@Presario:~$ sudo apt-cache search flashplayer 
 [sudo] password for trevor:  
 flashplugin-nonfree-extrasound - Adobe Flash Player platform support library for Esound and OSS 

``````
trevor@Presario:~$ sudo apt-cache show flashplugin-nonfree-extrasound 
 Package: flashplugin-nonfree-extrasound 
 Priority: optional 
 Section: multiverse/sound 
 Installed-Size: 64 
 Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com> 
 Original-Maintainer: Petter Reinholdtsen <pere@debian.org> 
 Architecture: i386 
 Version: 0.0.svn2431-3ubuntu1 
 Replaces: libflashsupport 
 Depends: libc6 (>= 2.3.4) 
 Recommends: flashplugin-installer 
 Conflicts: flashplugin-nonfree-pulse, libflashsupport 
 Filename: pool/multiverse/f/flashplugin-nonfree-extrasound/flashplugin-nonfree-extrasound_0.0.svn2431-3ubuntu1_i386.deb 
 Size: 8562 
 MD5sum: 1150ee717da87aab891f421f201835d4 
 SHA1: 10254f19f74ca403848958f61f584d290cb1b413 
 SHA256: 09340fd08ff50ab787dcd10f329d8eda051d64d7f217cf362d0a345bc378c373 
 Description-en: Adobe Flash Player platform support library for Esound and OSS 
  This is an open Source extension library for the Adobe Flash Player 
  that enables support for otherwise unsupported sound systems.  It 
  provides the libflashsupport.so plugin.  The sound system to use is 
  automatically detected: 
  . 
   * It first tries to detect Esound, 
   * Next, it checks for OSS. 
  . 
  If all of the above failed, it falls back to the ALSA driver that's 
  built directly into FlashPlayer 9. 
  . 
  For PulseAudio support, see flashplugin-nonfree-pulse. 
 Description-md5: 74ec5439ce259e0c156f5f983af2c21f 
 Bugs: https://bugs.launchpad.net/ubuntu/+filebug 
 Origin: Ubuntu
  
```I really need some help here :sad:


See [http://ubuntuforums.org/showthread.php?t=2011882](http://ubuntuforums.org/showthread.php?t=2011882) for the Chrome  issue.

Do you really need flashplugin-nonfree-extrasound?

---

### Post by snuffy47 on 2012-07-03
I do not need the non free flash stuff to my knowledge

It has been a busy couple days and nights tring to get it to work

I did install Mint 12 and it worked out of the box but had slow internet problems

How do I start over again and make sure there are no flash stuff

---

### Post by Spydax on 2012-07-03
> **lovinglinux said:**
> The most recent versions of Flash, 11.2.202.228, is causing a lot of problems to nVidia users, like the SMURF effect...

If you are still experiencing problems, please attach the firefox-report.txt file generated in your desktop after running the commands below:

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt

```

I'm dying here.  Been working on this forever - still no luck fixing my skipping streaming audio - I've tried everything mentioned on Chrome/Chromium/Firefox, still can't watch a video without every other second clipping.  I Need this to work, let me know what other information you may need.


[PHP]Ubuntu Architecture

Linux USERNAME-PC 3.2.0-25-generic #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"

Firefox Packages

firefox						install
firefox-branding				install
firefox-globalmenu				install
firefox-gnome-support				install
firefox-locale-en				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

dropbox.list
dropbox.list.distUpgrade
dropbox.list.save
google-chrome.list
google-chrome.list.distUpgrade
google-chrome.list.save
google-talkplugin.list
google-talkplugin.list.distUpgrade
google-talkplugin.list.save
maverick-partner.list
maverick-partner.list.distUpgrade
maverick-partner.list.save
paullo612-unityshell-rotated-oneiric.list
paullo612-unityshell-rotated-oneiric.list.distUpgrade
tualatrix-ppa-natty.list
tualatrix-ppa-natty.list.distUpgrade
tualatrix-ppa-natty.list.save
ubuntu-wine-ppa-maverick.list.distUpgrade
ubuntu-wine-ppa-maverick.list.save
ubuntu-wine-ppa-natty.list
ubuntu-wine-ppa-natty.list.distUpgrade
ubuntu-wine-ppa-natty.list.save
ubuntu-wine-ppa-oneiric.list
ubuntu-wine-ppa-oneiric.list.distUpgrade
ubuntu-wine-ppa-oneiric.list.save

Flash packages

flashplugin-installer				install

Plugin locations

/home/USERNAME/data/com.adobe.flashplayer/lib/libflashplayer.so
/opt/google/chrome/plugins/libflashplayer.so
/usr/lib/chromium-browser/plugins/libflashplayer.so

/usr/lib/mozilla/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/firefox-addons/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/flashplugin-installer/libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)

pluginreg.dat

Generated File. Do not edit.

[HEADER]
Version:0.15:$
Arch:x86_64-gcc3:$

[PLUGINS]
libflashplayer.so:$
/usr/lib/flashplugin-installer/libflashplayer.so:$
:$
1341344034000:0:1:$
Shockwave Flash 11.2 r202:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$
libnpgtpo3dautoplugin.so:$
/opt/google/talkplugin/libnpgtpo3dautoplugin.so:$
:$
1337017443000:0:5:$
Google Talk Plugin Video Accelerator version:0.1.44.15:$
Google Talk Plugin Video Accelerator:$
1
0:application/vnd.gtpo3d.auto:O3D MIME::$
libnpgoogletalk.so:$
/opt/google/talkplugin/libnpgoogletalk.so:$
:$
1337017441000:0:5:$
Version: 2.9.10.0:$
Google Talk Plugin:$
1
0:application/googletalk:Google Talk Plugin:googletalk:$
IcedTeaPlugin.so:$
/usr/lib/jvm/java-6-openjdk-amd64/jre/lib/amd64/IcedTeaPlugin.so:$
:$
1334072412000:0:5:$
The <a href="http://icedtea.classpath.org/wiki/IcedTea-Web">IcedTea-Web Plugin</a> executes Java applets.:$
IcedTea-Web Plugin (using IcedTea-Web 1.2 (1.2-2ubuntu1)):$
34
0:application/x-java-vm:IcedTea:class,jar:$
1:application/x-java-applet:IcedTea:class,jar:$
2:application/x-java-applet;version=1.1:IcedTea:class,jar:$
3:application/x-java-applet;version=1.1.1:IcedTea:class,jar:$
4:application/x-java-applet;version=1.1.2:IcedTea:class,jar:$
5:application/x-java-applet;version=1.1.3:IcedTea:class,jar:$
6:application/x-java-applet;version=1.2:IcedTea:class,jar:$
7:application/x-java-applet;version=1.2.1:IcedTea:class,jar:$
8:application/x-java-applet;version=1.2.2:IcedTea:class,jar:$
9:application/x-java-applet;version=1.3:IcedTea:class,jar:$
10:application/x-java-applet;version=1.3.1:IcedTea:class,jar:$
11:application/x-java-applet;version=1.4:IcedTea:class,jar:$
12:application/x-java-applet;version=1.4.1:IcedTea:class,jar:$
13:application/x-java-applet;version=1.4.2:IcedTea:class,jar:$
14:application/x-java-applet;version=1.5:IcedTea:class,jar:$
15:application/x-java-applet;version=1.6:IcedTea:class,jar:$
16:application/x-java-applet;jpi-version=1.6.0_50:IcedTea:class,jar:$
17:application/x-java-bean:IcedTea:class,jar:$
18:application/x-java-bean;version=1.1:IcedTea:class,jar:$
19:application/x-java-bean;version=1.1.1:IcedTea:class,jar:$
20:application/x-java-bean;version=1.1.2:IcedTea:class,jar:$
21:application/x-java-bean;version=1.1.3:IcedTea:class,jar:$
22:application/x-java-bean;version=1.2:IcedTea:class,jar:$
23:application/x-java-bean;version=1.2.1:IcedTea:class,jar:$
24:application/x-java-bean;version=1.2.2:IcedTea:class,jar:$
25:application/x-java-bean;version=1.3:IcedTea:class,jar:$
26:application/x-java-bean;version=1.3.1:IcedTea:class,jar:$
27:application/x-java-bean;version=1.4:IcedTea:class,jar:$
28:application/x-java-bean;version=1.4.1:IcedTea:class,jar:$
29:application/x-java-bean;version=1.4.2:IcedTea:class,jar:$
30:application/x-java-bean;version=1.5:IcedTea:class,jar:$
31:application/x-java-bean;version=1.6:IcedTea:class,jar:$
32:application/x-java-bean;jpi-version=1.6.0_50:IcedTea:class,jar:$
33:application/x-java-vm-npruntime:::$
librhythmbox-itms-detection-plugin.so:$
/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so:$
:$
1333654548000:0:5:$
This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.:$
iTunes Application Detector:$
1
0:application/itunes-plugin:::$
libtotem-mully-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$
:$
1333401159000:0:5:$
DivX Web Player version 1.4.0.233:$
DivXÂ® Web Player:$
1
0:video/divx:AVI video:divx:$
libtotem-cone-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-cone-plugin.so:$
:$
1333401159000:0:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.0.1 plugin handles video and audio streams.:$
VLC Multimedia Plugin (compatible Totem 3.0.1):$
21
0:application/x-vlc-plugin:VLC Multimedia Plugin::$
1:application/vlc:VLC Multimedia Plugin::$
2:video/x-google-vlc-plugin:VLC Multimedia Plugin::$
3:application/x-ogg:Ogg multimedia file:ogg:$
4:application/ogg:Ogg multimedia file:ogg:$
5:audio/ogg:Ogg Audio:oga:$
6:audio/x-ogg:Ogg Audio:ogg:$
7:video/ogg:Ogg Video:ogv:$
8:video/x-ogg:Ogg Video:ogg:$
9:application/annodex:Annodex exchange format:anx:$
10:audio/annodex:Annodex Audio:axa:$
11:video/annodex:Annodex Video:axv:$
12:video/mpeg:MPEG video:mpg, mpeg, mpe:$
13:audio/wav:WAV audio:wav:$
14:audio/x-wav:WAV audio:wav:$
15:audio/mpeg:MP3 audio:mp3:$
16:application/x-nsv-vp3-mp3:NullSoft video:nsv:$
17:video/flv:Flash video:flv:$
18:video/webm:WebM video:webm:$
19:application/x-totem-plugin:Totem Multimedia plugin::$
20:audio/midi:MIDI audio:mid, midi:$
libtotem-gmp-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$
:$
1333401158000:0:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.0.1 plugin handles video and audio streams.:$
Windows Media Player Plug-in 10 (compatible; Totem):$
13
0:application/x-mplayer2:AVI video:avi, wma, wmv:$
1:video/x-ms-asf-plugin:ASF video:asf, wmv:$
2:video/x-msvideo:AVI video:asf, wmv:$
3:video/x-ms-asf:ASF video:asf:$
4:video/x-ms-wmv:Windows Media video:wmv:$
5:video/x-wmv:Windows Media video:wmv:$
6:video/x-ms-wvx:Windows Media video:wmv:$
7:video/x-ms-wm:Windows Media video:wmv:$
8:video/x-ms-wmp:Windows Media video:wmv:$
9:application/x-ms-wms:Windows Media video:wms:$
10:application/x-ms-wmp:Windows Media video:wmp:$
11:application/asx:Microsoft ASX playlist:asx:$
12:audio/x-ms-wma:Windows Media audio:wma:$
libtotem-narrowspace-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$
:$
1333401158000:0:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.0.1 plugin handles video and audio streams.:$
QuickTime Plug-in 7.6.6:$
5
0:video/quicktime:QuickTime video:mov:$
1:video/mp4:MPEG-4 video:mp4:$
2:image/x-macpaint:MacPaint Bitmap image:pntg:$
3:image/x-quicktime:Macintosh Quickdraw/PICT drawing:pict, pict1, pict2:$
4:video/x-m4v:MPEG-4 video:m4v:$[/PHP]

---

### Post by Spydax on 2012-07-03
In attempting to prove my little brother wrong (he said it was my NIC card), because I knew it wasn't the network card, I attempted to load up a HTML5 video (mostly to prove that the problem was primarily due to Flash) the HTML5 loads up and plays at 1.5x speed. Made no sense - flash was half speed, HTML5 was almost double speed. So dong a different search for the HTML5 problem I narrowed down the issue to the pulseaudio, killed that process, restarted it, and we are in business.

Got the idea from here
[http://superuser.com/questions/440372/html5-video-only-plays-back-at-fast-speed-on-ubuntu-linux](http://superuser.com/questions/440372/html5-video-only-plays-back-at-fast-speed-on-ubuntu-linux)

> Took me days to figure out the issue, but basically pulseaudio can get screwed up and somehow cause all html5 video to go wonky.

Easy fix:

Stop pulseaudio:

killall pulseaudio (or) pulseaudio -k

Restart pulseaudio

go to Run (Alt+F2) and type pulseaudio (or run pulseaudio in a terminal)

And this weird error will magically be fixed.

---

### Post by bcschmerker on 2012-07-18
> **Spydax said:**
> I'm dying here.  Been working on this forever - still no luck fixing my skipping streaming audio - I've tried everything mentioned on Chrome/Chromium/Firefox, still can't watch a video without every other second clipping.  I Need this to work, let me know what other information you may need....Looks as though ye need Adobe® Flash™ Player 10.3.183.20, which was originally patched for systems unable to run Versions 11-up.  The lovinglinux Extension [Flash-Aid™]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") will be needed to download and install LibFlashPlayer.so 10.3.183.20 from the GZip at Macromedia®/Adobe® FPDownload, using the "Custom (http URL or local path)" option:
```
http://fpdownload.macromedia.com/get/flashplayer/current/licensing/linux/install_flash_player_10_linux.tar.gz
```

---

### Post by September on 2012-08-16
Dunno if this is posted on any other part of the forums, but couldn't see in this thread. This SMURF effect on youtube videos bugged me good and I had to find a workaround. I'll share my solution just for the information.

I've noticed that on embedded youtube videos there was no smurf effect. Inspecting the html obj properties, I came up with the workaround that, if the embedded obj has the property "wmode" set to "transparent", then there is no smurf effect. This way, I don't need to disable the hw acceleration and I'm happy about it. So the bug with nvidia and such is probably related to the colorspace and probably triggered by the way the alpha channel is employed or something like that, because the red and blue channels are swapped.

I've written a tiny gmscript to fix the youtube videos. Well, it is for youtube only but it's 100% for me :)

```
// ==UserScript==
// @name        Youtube Color Correction
// @namespace   http*://www.youtube.com/*
// @description Overwrites obj props on youtube pages to fix the color screwup of flash+nvidia
// @include     http*://www.youtube.com/*
// @version     1
// ==/UserScript==

var vid = document.getElementById("watch-player");

if(vid)
{
    var inner = vid.innerHTML;
    var pos = inner.indexOf("embed type");
    
    if(pos >= 0)
    {
        var before = inner.substring(0, pos);
        var after = inner.substring(pos + 5);
        
        vid.innerHTML = before + "embed wmode='transparent' " + after;
    }
}
```

---

### Post by chincol on 2012-08-23
Thanks buddy, that worked like a charm.

---

### Post by chincol on 2012-08-23
Thanks buddy, that worked like a charm.

---

### Post by Eromatic on 2012-09-08
_[Nvidia](http://lists.x.org/archives/xorg-announce/2012-September/002066.html)_ had updated libvdpau to 0.5 a few days ago to work around the color channel & key color issues. It's very similar to the version provided at _[Tikhonov's PPA](https://launchpad.net/~tikhonov/+archive/misc)_, but also corrects a memory leak issue that "occurs when libvdpau is unloaded."

---

### Post by TenPlus1 on 2012-09-08
I am currently using Chromium and have managed to get the pepperflash plugin working from Google Chrome which allows me to use flash 11.3 with all of these problems fixed and HD video working fine...

---

### Post by daemoncycler on 2012-10-30
DUDE!!!  Thanks so much.  Been givin me trouble for weeks now.  Reinstalled Lubuntu 11.10 & couldn't figure out what happened.  Downloaded version 11.1.1.02.63 from your server, copied into /usr/lib/chromium-browser/plugins & /usr/lib/flashplugin-installer.

Problems with plugin shockwave crashing & missing plugin fixed.

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

### Post by Bazon on 2012-11-25
Sorry if this was mentioned before, haven't read the whole thread:

If your Flash-Fullscreen display** immediately returns to small size**, here is a workaround:
**DOUBLE-click the fullscreen icon.**
(So it seems to be a focus problem.)

---

### Post by grey1beard on 2013-03-31
Having read the thread, and deciding that I might try the 'downgrade' route as per the op, I find no mention of the need to remove earlier versions of the flashinstaller plugin nor copies of libflashplayer.so from the various locations.
I noted that in the op, the use of FlashAid will 'remove all copies of Flash', but having clicked on the link, now find that FlashAid has been removed by its author'.
Any thoughts or suggestions, anyone ?
John

---

### Post by arpanaut on 2013-04-02
The workaround of using the Flash version 11.1.102.63 and putting it's .so file in the .mozilla/firefox/plugins folder is not working anymore.
It seems that firefox is blocking the use of the old version. I have a couple of old rigs that don't support sse2 (bummer).

So, is there another workaround, or some modification possible to the .so file, or an option to turn off the blocking of the old plugin within firefox?

Using 12.04 fully updated on these boxes.

Edit: Okay so it seems that if you click through the prompt to upgrade window, not the link to upgrade "most" flash video will play. Still would like a more seamless way to get this to work.

---

### Post by grey1beard on 2013-05-11
I've given up trying to fix flash player on my wife's laptop running 11.04(or was it 11.10 ?!!) and decided to upgrade to 12.04LTS, the sae as mine.
All went well till I tried the BBC site to lookat a video clip - black rectangle, or white, if I try Youtube.

I checked that a video in her home folder plays OK, so at least she'll not hit me when she finds out later !

Can't try the 1st method on the 1st post of this thread, as nothing is visible if I right click.

Tried to run *apt-get install adobe-flashplugin* route and got

> Package adobe-flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'adobe-flashplugin' has no installation candidate

Does that last line mean I have not got Flash player installed ?

Getting in quite a muddle where Flash player is concerned, so I'd be grateful for some help.
John

---

### Post by grey1beard on 2013-05-12
Re my previous post, I've given up, backed up her home folder, installed a new 12.04 from a live disc.
However, video clips on the BBC site still don't run, nor do youtube clips.
Do I need to go back to an earlier version of libflashplayer.so to fix this ?
If so, which one is recomended , and do I only have to change it for the existing one in /usr/lib/flashplugin-installer ?
I've got shockwave flash 11.2 r202 in the Firefox Plugins, and I assume this is OK.

:( John

EDIT  I should point out that my elderly Toshiba laptop, running the same versions, has no problems at all with videos, which makes it doubly frustrating.

---

### Post by bobblex on 2013-05-12
Try  apt-get install flashplugin-installer as that seems to be how it's listed in Synaptic.

Ooops, never mind I see that you apparently already have flashplugin-installer installed.

---

### Post by grey1beard on 2013-05-13
You got me excited there for a moment, bobblex, but thanks anyway !

John

EDIT I've given up,( again) and managed to get flash videos playing by using the reversion method in #1, and putting up with the warning pop-up that comes with using it.
I needed to create a plugins folder in .mozilla, and to disable the current plugin via the firefox/tools/add-ons/plugins page.

---

### Post by grey1beard on 2013-05-16
It worked for a couple of days, then suddenly stopped this evening. A new Update Manager installed Flash 11.2.208.285 which seems to be the cause.
I disabled that in Tools/Add-ons/plugins, and allowed the old 11.1.102.63 to continue, which it does, albeit after clicking on "Activate", as before.

John

---

### Post by grey1beard on 2013-06-29
Hi pyutaros,
Having lost flash player function on my wife's laptop yet again, I've just tried running your script in Terminal as suggested, but with no noticable result.
I've looked in Tools/Add-ons, but only the 11.2.202 (disabled) is in evidence.
Is there some final action I need to take to get 11.1.102.63 to install, or checks I need to make ?
Regards
John

---

