---
title: "flash causes system crash"
date: 2011-07-30
forum: Multimedia Software
---

### Post by panandrzej on 2011-07-30
Hi,

I have a problem with Adobe Flash Player. When I watch YouTube or Blip.tv or other video streaming sites, my computer crashes randomly during the video. It stops responding, I can't use keyboard and mouse. The only way to recover is a hard reset.
It happens in FF, Opera, Chromium and Chrome. I had this problem on Flash Player 10 and on 11-beta I have it too.

I running Ubuntu 11.04 Natty 64-bit. Kernel: 2.6.38-11-generic. GNOME 2.32.1. with Unity.

short config of my PC:
cpu: AMD Athlon X2 64bit DualCore
mobo: ASUS M2N68 (+newset BIOS there is)
gpu: Nvidia Geforce 8800GT
hdd: WDC 500Gb
ram: (some generic) 4gb

Help me please.

Your Sincerly,
Andrzej

---

### Post by .... on 2011-07-30
It's probably overheating. Monitor your temps. Also, check out the Flash-aid Firefox extension.

---

### Post by panandrzej on 2011-07-30
Hmmm... I've put new paste on the GPU core lately and PC works good under heavy gaming (like Civilization 5 or L4D2). Moreover flash works good under Windows. So I think it's rather software issue.
Any other suggestions?

---

### Post by ajgreeny on 2011-07-30
How did you install flash?

If using Firefox I strongly recommend **flash-aid** add-on.  This will search out the most appropriate version of flash for your system, download and install it, and automatically remove any conflicting packages you already have.

---

### Post by panandrzej on 2011-07-30
I've installed it from the package on Adobe's site.

I've tried flash-aid but it did't helped. :(

---

### Post by .... on 2011-07-30
Are you monitoring your CPU and GPU temps?
The next thing I would suggest is memtest.

---

### Post by craig100 on 2011-07-30
I have the situation where just Flash itself crashes every 5 minutes to an hour. Can't keep it on for long. It's worse if I have more than one Flash item going, like chat and radio streaming via a Flash interface.  When the Flash adverts changeover it goes then.

Running 10.10x64 12GB RAM NVidia Accelerated graphics driver (the recommended one)

---

### Post by .... on 2011-07-30
> **craig100 said:**
> I have the situation where just Flash itself crashes every 5 minutes to an hour. Can't keep it on for long. It's worse if I have more than one Flash item going, like chat and radio streaming via a Flash interface.  When the Flash adverts changeover it goes then.

Running 10.10x64 12GB RAM NVidia Accelerated graphics driver (the recommended one)
Are you monitoring your temps?

---

### Post by panandrzej on 2011-07-31
Temperature is fine. I did run memtest like 2 weaks ago - RAM was fine. As You can see craig100 has the same problem.

---

### Post by panandrzej on 2011-07-31
> **craig100 said:**
> I have the situation where just Flash itself crashes every 5 minutes to an hour. Can't keep it on for long. 

I have the same problem.

---

### Post by lovinglinux on 2011-07-31
Please click Flash-Aid menu, select "Help >> Generate report" and post the contents of the *firefox-report.txt* file created on your desktop, so I can analyse why Flash-Aid didn't help.

You might want to try another extension I develop, called [FlashVideoReplacer]("http://www.webgapps.org/add-ons/flashvideoreplacer"), that allows to watch YouTube and a few other sites with a better plugin (less CPU usage) or external player. Make sure to get version 2.1.14, which has the latest YouTube compatibility.

Also check [http://www.webgapps.org/tutorials/firefox/optimization/flash-optimization](http://www.webgapps.org/tutorials/firefox/optimization/flash-optimization)

---

### Post by panandrzej on 2011-07-31
Ubuntu Architecture

Linux Battlestation 2.6.38-11-generic #47-Ubuntu SMP Fri Jul 15 19:27:09 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

Firefox Packages

firefox						install
firefox-globalmenu				install
firefox-gnome-support				install
firefox-locale-en				install
firefox-locale-pl				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-5.0/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

am-monkeyd-nautilus-elementary-ppa-natty.list
am-monkeyd-nautilus-elementary-ppa-natty.list.save
ferramroberto-java-natty.list
ferramroberto-java-natty.list.save
ferramroberto-nvidia-natty.list
ferramroberto-nvidia-natty.list.save
google-chrome.list
google-chrome.list.save
opera.list
opera.list.save
playonlinux.list
playonlinux.list.save
sevenmachines-flash-natty.list
sevenmachines-flash-natty.list.save
team-xbmc-ppa-natty.list
team-xbmc-ppa-natty.list.save
tiheum-equinox-natty.list
tiheum-equinox-natty.list.save
tldm217-tahutek.net-natty.list
tldm217-tahutek_net-natty.list.save
tualatrix-ppa-natty.list
ubuntugnometeam-gnome3-natty.list
ubuntugnometeam-gnome3-natty.list.save

Flash packages

flashplugin64-installer				deinstall
Plugin locations

/home/panandrzej/.local/share/Trash/files/boxee/opt/boxee/system/players/flashplayer/xulrunner-x86_64-linux/bin/plugins/libflashplayer.so
/home/panandrzej/.local/share/Trash/files/boxee-0.9.22.13692.x86_64.modfied/opt/boxee/system/players/flashplayer/xulrunner-x86_64-linux/bin/plugins/libflashplayer.so
/home/panandrzej/.local/share/Trash/files/boxee.2/opt/boxee/system/players/flashplayer/xulrunner-x86_64-linux/bin/plugins/libflashplayer.so
/home/panandrzej/.local/share/Trash/files/boxee.3/opt/boxee/system/players/flashplayer/xulrunner-x86_64-linux/bin/plugins/libflashplayer.so
/home/panandrzej/Pobrane/libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so

/usr/lib/chromium-browser/plugins/flashplugin-alternative.so
/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks


/usr/lib/mozilla/plugins/libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped
/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory)
/etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory)
/usr/lib/flashplugin-installer/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-installer/libflashplayer.so' (No such file or directory)
/usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory)
/usr/lib/adobe-flashplugin/libflashplayer.so: ERROR: cannot open `/usr/lib/adobe-flashplugin/libflashplayer.so' (No such file or directory)
/usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory)
/usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory)
/usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)

pluginreg.dat

Generated File. Do not edit.

[HEADER]
Version:0.15:$
Arch:x86_64-gcc3:$

[PLUGINS]
IcedTeaPlugin.so:$
/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so:$
:$
1311152095000:1:5:$
The <a href="http://icedtea.classpath.org/wiki/IcedTea-Web">IcedTea-Web Plugin</a> executes Java applets.:$
IcedTea-Web Plugin (using IcedTea-Web 1.1.1 (1.1.1-0ubuntu1~11.04.1)):$
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
libtotem-narrowspace-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$
:$
1300218622000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.32.0 plugin handles video and audio streams.:$
QuickTime Plug-in 7.6.6:$
5
0:video/quicktime:Plik wideo QuickTime:mov:$
1:video/mp4:Plik wideo MPEG-4:mp4:$
2:image/x-macpaint:Obraz bitmapowy MacPaint:pntg:$
3:image/x-quicktime:Rysunek Quickdraw/PICT Macintosh:pict, pict1, pict2:$
4:video/x-m4v:Plik wideo MPEG-4:m4v:$
libtotem-mully-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$
:$
1300218622000:1:5:$
DivX Web Player version 1.4.0.233:$
DivXÂŽ Web Player:$
1
0:video/divx:Plik wideo AVI:divx:$
libtotem-gmp-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$
:$
1300218622000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.32.0 plugin handles video and audio streams.:$
Windows Media Player Plug-in 10 (compatible; Totem):$
13
0:application/x-mplayer2:Plik wideo AVI:avi, wma, wmv:$
1:video/x-ms-asf-plugin:Plik wideo ASF:asf, wmv:$
2:video/x-msvideo:Plik wideo AVI:asf, wmv:$
3:video/x-ms-asf:Plik wideo ASF:asf:$
4:video/x-ms-wmv:Plik wideo Windows Media:wmv:$
5:video/x-wmv:Plik wideo Windows Media:wmv:$
6:video/x-ms-wvx:Plik wideo Windows Media:wmv:$
7:video/x-ms-wm:Plik wideo Windows Media:wmv:$
8:video/x-ms-wmp:Plik wideo Windows Media:wmv:$
9:application/x-ms-wms:Plik wideo Windows Media:wms:$
10:application/x-ms-wmp:Plik wideo Windows Media:wmp:$
11:application/asx:Lista odtwarzania Microsoft ASX:asx:$
12:audio/x-ms-wma:Plik d&#313;&#351;wiÄ™kowy Windows Media:wma:$
libtotem-cone-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-cone-plugin.so:$
:$
1300218622000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.32.0 plugin handles video and audio streams.:$
VLC Multimedia Plugin (compatible Totem 2.32.0):$
20
0:application/x-vlc-plugin:VLC Multimedia Plugin::$
1:application/vlc:VLC Multimedia Plugin::$
2:video/x-google-vlc-plugin:VLC Multimedia Plugin::$
3:application/x-ogg:Plik multimedialny Ogg:ogg:$
4:application/ogg:Plik multimedialny Ogg:ogg:$
5:audio/ogg:Plik d&#313;&#351;wiÄ™kowy Ogg:oga:$
6:audio/x-ogg:Plik d&#313;&#351;wiÄ™kowy Ogg:ogg:$
7:video/ogg:Plik wideo Ogg:ogv:$
8:video/x-ogg:Plik wideo Ogg:ogg:$
9:application/annodex:Format wymiany Annodex:anx:$
10:audio/annodex:Plik d&#313;&#351;wiÄ™kowy Annodex:axa:$
11:video/annodex:Plik wideo Annodex:axv:$
12:video/mpeg:Plik wideo MPEG:mpg, mpeg, mpe:$
13:audio/wav:Plik d&#313;&#351;wiÄ™kowy WAV:wav:$
14:audio/x-wav:Plik d&#313;&#351;wiÄ™kowy WAV:wav:$
15:audio/mpeg:Plik d&#313;&#351;wiÄ™kowy MP3:mp3:$
16:application/x-nsv-vp3-mp3:Plik wideo NullSoft:nsv:$
17:video/flv:Plik wideo Flash:flv:$
18:video/webm:Plik wideo WebM:webm:$
19:application/x-totem-plugin:Totem Multimedia plugin::$
libflashplayer.so:$
/usr/lib/mozilla/plugins/libflashplayer.so:$
:$
1309501243000:1:5:$
Shockwave Flash 11.0 d1:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$
libflashplayer.so:$
/usr/lib/flashplugin-installer/libflashplayer.so:$
:$
1311773416000:1:13:$
Shockwave Flash 11.0 d1:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$

[INVALID]

---

### Post by lovinglinux on 2011-07-31
I can't see anything wrong with your report. Firefox is detecting the correct plugin version.

When it crashes, how many tabs with flash content do you have open?

Try installing Flashblock and enable only one flash instance at a time.

---

### Post by panandrzej on 2011-07-31
I have Ad-block installed - most of flash content is blocked. Usually I have 1 tab with video and some other non-flash pages in other tabs.

Wierd stuff.

---

### Post by lovinglinux on 2011-07-31
> **panandrzej said:**
> I have Ad-block installed - most of flash content is blocked. Usually I have 1 tab with video and some other non-flash pages in other tabs.

Wierd stuff.

Have you tried a clean profile, to see if the problem persists?

---

### Post by panandrzej on 2011-07-31
Nothing seems to help. I'll just add, that it happens since clean installation of Natty.

---

### Post by lovinglinux on 2011-07-31
> **panandrzej said:**
> Nothing seems to help. I'll just add, that it happens since clean installation of Natty.

Do you have the latest driver for your graphics card?

---

### Post by panandrzej on 2011-08-01
I have Nvidia Drivers ver. 173.14.30 (I can't upgrade it cause of my broken monitor - that is a totaaly different story :D )

I've been heavy-testing my PC for last 2 days.
Some results:

#1 Memtest show no errors after 2,5h test.
#2 This same kind of system crash occures, when I use Clementine (music player). <-- I'm not sure is it even related to the flash problem but symptoms are identical.

Meaby it is a sound card problem. I have no idea.

As you can see my PC is a mess. Sorry, if you wasted time on me. I'll prabobly need to buy new gear. Frak that!

---

### Post by lovinglinux on 2011-08-01
> **panandrzej said:**
> I have Nvidia Drivers ver. 173.14.30 (I can't upgrade it cause of my broken monitor - that is a totaaly different story :D )

I've been heavy-testing my PC for last 2 days.
Some results:

#1 Memtest show no errors after 2,5h test.
#2 This same kind of system crash occures, when I use Clementine (music player). <-- I'm not sure is it even related to the flash problem but symptoms are identical.

Meaby it is a sound card problem. I have no idea.

As you can see my PC is a mess. Sorry, if you wasted time on me. I'll prabobly need to buy new gear. Frak that!

I think the problem might be related to the video driver.

You could try to disable hardware acceleration in flash. You can do that by right-clicking on a video and selecting the Settings option.

---

### Post by PeteAsdf on 2011-08-18
Hi, 

I have the same problem. Mine happens when I watch live Flash TV streams (on TennisTV). Sometimes it only crashes the browser but more often it freezes the whole system (mouse & keyboard not responding).
I noticed that the vid uses quite a bit of my CPU: about 80% total usage. Is that normal? Not sure about the temperatures- I will check it the next time I'm on my system. What is the normal temperature for the graphics card? (Sorry for the the stupid questions btw).

My setup: Kubuntu 11.04 64 
Nvidia GEFORCE 8800GTS

Thanks!

---

### Post by Derek Karpinski on 2011-08-19
Same exact problem here too. Started after new 64bit flash update via flash-aid, and adding medibuntu codecs.

Help please.

---

### Post by Derek Karpinski on 2011-08-19
For whatever reason, today flash-aid doesn't show up, and if I go to 'about:addons' in firefox, it says flash-aid is incompatible with FF6.............

Regardless, I've solved it on my system by rerunning flash-aid, and disabling HW acceleration.

I've been watching youtube vids for hours now, no crashes. :o

---

### Post by lovinglinux on 2011-08-20
> **Derek Karpinski said:**
> For whatever reason, today flash-aid doesn't show up, and if I go to 'about:addons' in firefox, it says flash-aid is incompatible with FF6.............

It is a known issue with Flash-Aid 2.1.1 and Firefox 6. Get version 2.2.0 from [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/versions/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/versions/)

---

### Post by LinuxGF on 2011-08-25
> **craig100 said:**
> I have the situation where just Flash itself crashes every 5 minutes to an hour. Can't keep it on for long. It's worse if I have more than one Flash item going, like [flash chat]("http://www.flashcoms.com") and radio streaming via a Flash interface.  When the Flash adverts changeover it goes then.

Running 10.10x64 12GB RAM NVidia Accelerated graphics driver (the recommended one)
I have the same problem. I'll never know what to do.

---

### Post by thewolfman on 2011-08-25
Hi chaps,

do this in a terminal, it worked for me:

For 64 bit:

sudo apt-get purge --yes adobe-flashplugin
sudo apt-get purge --yes flashplugin-installer
sudo apt-get purge --yes flashplugin-nonfree
sudo apt-get purge --yes mozilla-plugin-gnash
sudo apt-get purge --yes swfdec-mozilla
sudo apt-get purge --yes browser-plugin-lightspark
sudo apt-get purge --yes mozilla-plugin-gnash
sudo apt-get purge --yes konqueror-plugin-gnash
sudo add-apt-repository ppa:sevenmachines/flash
sudo apt-get update
sudo apt-get install flashplugin64-installer

Regards thewolfman:P

---

### Post by Zeikcied on 2011-09-13
I've had the same issue with the Flash Player 11 beta.

When watching streams (like JustinTV or Ustream) or something on BlipTV, my system will freeze.  Well, sort of.  If I keep moving the mouse, after a few minutes the system will unfreeze for maybe 30 seconds, but even if I close Firefox the system will remain in this semi-frozen state until I force it to shut down.

When using FlashAid, how exactly do I disable hardware acceleration (assuming that's the problem)?  Do I just uncheck the "Enable Linux HWVideo Decode" box on the Advanced menu?   And is it still an issue with RC1 that just came out a couple days ago?

(For the record I have an NVIDIA GeForce 240 GT and the official driver version 270.41.06 from the Ubuntu repos.)

---

