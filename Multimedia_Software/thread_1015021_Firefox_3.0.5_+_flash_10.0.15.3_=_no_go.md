---
title: "Firefox 3.0.5 + flash 10.0.15.3 = no go"
date: 2008-12-18
forum: Multimedia Software
---

### Post by emuman on 2008-12-18
System: Intrepid, all updates. Flash works with Konqueror, but not in Firefox. About:plugins doesn't show the flash plugin. Link in /usr/lib/firefox/plugins/libflashplayer.so points to /etc/alternatives/firefox-flashplugin which points to /usr/lib/adobe-flashplugin/libflashplayer.so which exists. Any idea?

---

### Post by davescafe on 2008-12-18
I am experiencing this problem as well. Flash plugin does not work. Here are my specific details:

[LIST]
[*]I have completely and cleanly re-installed Ubuntu 8.10 32-bit Desktop 
[*]I have installed all available Ubuntu updates.
[*]I have installed OpenOffice.org 3.0 and VMware Server 2.0, but no other programs
[*]Firefox version: 3.0.5
[*]Flash plugin version (from repros) 10.0.12.36
[/LIST]

I welcome any help.

Dave

---

### Post by gandaran on 2008-12-18
> **davescafe said:**
> I am experiencing this problem as well. Flash plugin does not work. Here are my specific details:

[LIST]
[*]I have completely and cleanly re-installed Ubuntu 8.10 32-bit Desktop 
[*]I have installed all available Ubuntu updates.
[*]I have installed OpenOffice.org 3.0 and VMware Server 2.0, but no other programs
[*]Firefox version: 3.0.5
[*]Flash plugin version (from repros) 10.0.12.36
[/LIST]

I welcome any help.

Dave
do you have any other flash package like swfdec, gnash, libflash or flashblock installed or any firefox addblock or flasblock addon?
if you go to tools » addons » plugins, do you find there a shockwave flash plugin? is it enabled?
firefox » edit » preferences » applications tab » shockwave file, is it set to use shockwave flash on firefox? 
post the output of **locate libflash** (type in terminal)
also the full output of this code, type in firefox url bar
```
about:plugins
```

---

### Post by kuhnchris19 on 2008-12-18
gandaran. Im in the 64 bit intrepid. I'm having a huge flash problem as well in firefox3.0.5. from locate libflash i get>> /usr/lib/openoffice/program/libflash680lx.so
 And I don't have any flash or such thing in the firefox plugins. The about plugins in the url bar gives me>>  Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
Demo Print Plugin for unix/linux

    File name: libunixprintplugin.so
    The demo print plugin for unix.

MIME Type 	Description 	Suffixes 	Enabled
application/x-print-unix-nsplugin 	Demo Print Plugin for Unix/Linux 	.pnt 	Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.24.3 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	Windows Media video 	wmv 	Yes
video/x-wmv 	Windows Media video 	wmv 	Yes
video/x-ms-wvx 	Windows Media video 	wmv 	Yes
video/x-ms-wm 	Windows Media video 	wmv 	Yes
video/x-ms-wmp 	Windows Media video 	wmv 	Yes
application/x-ms-wms 	Windows Media video 	wms 	Yes
application/x-ms-wmp 	Windows Media video 	wmp 	Yes
application/asx 	Microsoft ASX playlist 	asx 	Yes
audio/x-ms-wma 	Windows Media audio 	wma 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.24.3 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes
IcedTea Web Browser Plugin

    File name: IcedTeaPlugin.so
    The IcedTea Web Browser Plugin executes Java applets.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	IcedTea 	class,jar 	Yes
application/x-java-applet 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-applet;jpi-version=1.6.0_00 	IcedTea 	class,jar 	Yes
application/x-java-bean 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-bean;jpi-version=1.6.0_00 	IcedTea 	class,jar 	Yes
VLC Multimedia Plug-in

    File name: libvlcplugin.so
    Version 0.9.4 Grishenko, copyright 1996-2007 The VideoLAN Team
    [http://www.videolan.org/](http://www.videolan.org/)

MIME Type 	Description 	Suffixes 	Enabled
audio/mpeg 	MPEG audio 	mp2,mp3,mpga,mpega 	Yes
audio/x-mpeg 	MPEG audio 	mp2,mp3,mpga,mpega 	Yes
video/mpeg 	MPEG video 	mpg,mpeg,mpe 	Yes
video/x-mpeg 	MPEG video 	mpg,mpeg,mpe 	Yes
video/mpeg-system 	MPEG video 	mpg,mpeg,mpe,vob 	Yes
video/x-mpeg-system 	MPEG video 	mpg,mpeg,mpe,vob 	Yes
video/mp4 	MPEG-4 video 	mp4,mpg4 	Yes
audio/mp4 	MPEG-4 audio 	mp4,mpg4 	Yes
application/mpeg4-iod 	MPEG-4 video 	mp4,mpg4 	Yes
application/mpeg4-muxcodetable 	MPEG-4 video 	mp4,mpg4 	Yes
video/x-msvideo 	AVI video 	avi 	Yes
video/quicktime 	QuickTime video 	mov,qt 	Yes
application/x-ogg 	Ogg stream 	ogg 	Yes
application/ogg 	Ogg stream 	ogg 	Yes
application/x-vlc-plugin 	VLC plug-in 	vlc 	Yes
video/x-ms-asf-plugin 	Windows Media Video 	asf,asx 	Yes
video/x-ms-asf 	Windows Media Video 	asf,asx 	Yes
application/x-mplayer2 	Windows Media 		Yes
video/x-ms-wmv 	Windows Media 	wmv 	Yes
video/x-ms-wvx 	Windows Media Video 	wvx 	Yes
application/x-google-vlc-plugin 	Google VLC plug-in 		Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/3gpp 	3GPP audio 	3gp,3gpp 	Yes
video/3gpp 	3GPP video 	3gp,3gpp 	Yes
audio/3gpp2 	3GPP2 audio 	3g2,3gpp2 	Yes
video/3gpp2 	3GPP2 video 	3g2,3gpp2 	Yes
video/divx 	DivX video 	divx 	Yes
video/flv 	FLV video 	flv 	Yes
video/x-flv 	FLV video 	flv 	Yes
video/x-matroska 	Matroska video 	mkv 	Yes
audio/x-matroska 	Matroska audio 	mka 	Yes

Any ideas?? Or am I just retarded and don't have something active?

---

### Post by gandaran on 2008-12-18
kuhnchris19 
did you install the flashplugin-nonfree (32-bits flash+ npwrapper) from the repos/synaptic?
if you did then remove both packages and get the 64-bits beta adobe flash, download the tar.gz package here [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
unpack and just drop the libflashplyer.so file in a browser plugins directory, usually /usr/lib/mozilla/plugins or any firefox plugins folder.

---

### Post by kuhnchris19 on 2008-12-18
Dam. Still didn't happen, I end up with a shared library file that I can't do anything with. tried forcing it in terminal, no go.

---

### Post by nikgare on 2008-12-18
my Flash plugin is tored in this directory:
~/.mozilla/plugins

and works fine from there, maybe yours should be there too?

---

### Post by gandaran on 2008-12-18
kuhnchris19
> Dam. Still didn't happen, I end up with a shared library file that I can't do anything with. tried forcing it in terminal, no go.
whats happening?

nikgare
> my Flash plugin is tored in this directory:
~/.mozilla/plugins
yes, the flash plugin works anywhere in a browser plugins directory

---

### Post by kuhnchris19 on 2008-12-18
Says i don't have the application for a .so file type?

---

### Post by davescafe on 2008-12-18
> **gandaran said:**
> do you have any other flash package like swfdec, gnash, libflash or flashblock installed or any firefox addblock or flasblock addon?
if you go to tools » addons » plugins, do you find there a shockwave flash plugin? is it enabled?
firefox » edit » preferences » applications tab » shockwave file, is it set to use shockwave flash on firefox? 
post the output of **locate libflash** (type in terminal)
also the full output of this code, type in firefox url bar
```
about:plugins
```

I have installed no Firefox plugins except flashplayer-nonfree from the Ubuntu repository.

When IU go to Tools >> Addons >> Plugins, the following plugins are listed:
[LIST=1]
[*]Default Plugin
[*]Demo Print Plugin for unix/linux
[*]DivX Web Player
[*]Totem Web Browser Plugin 2.24.3
[*]Windows Media Player Plug-in 10 (compatible; Totem)
[/LIST]
These were all installed with my default Ubuntu 8.10 install.

When I go to Synaptic, the package"flashplugin-nonfree" is marked as installed (as I intended), however, the following directory is empty:
~/.mozilla/<profile>/extensions
In addition, there is no "plugins" directory at this path: ~/.mozilla

The output of terminal$ "locate libflash" is:
/usr/lib/openoffice/program/libflash680li.so

The problem I am seeing is that the flashplugin-nonfree package in the repros (as well as flashplugin-nonfree-extrasound) is not working. However, I *am* able to get flash to work if I go out to the Adobe website, download the tar.gz file and install it that way.

---

### Post by gandaran on 2008-12-18
> **kuhnchris19 said:**
> Says i don't have the application for a .so file type?
what? you need an application for .so file?
if I'm reading correctly your problem just do the following, drag the libflashplayer.so with the mouse or copy/paste to a browser plugins directory

---

### Post by spsuaiken on 2008-12-18
I actually got this to work a couple of days ago on Ibex AMD64.
I'm not on that machine right now, but I remember it going something like this:

Explicitly download and install the latest flash install to ~/.mozilla/plugins

Then download the package nspluginwrapper and install it.

```
sudo apt-get install nspluginwrapper
nspluginwrapper -i ~./mozilla/plugins/libflashplayer.so
```

For some reason I had to type the full path name to get it to work.

This seems to make it profile dependent instead of looking for it in /usr/lib/plugins

There also seems to be a development plugin from Macromedia directly made for 64, but I haven't tried it yet.
[HTML]http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz[/HTML]

---

### Post by gandaran on 2008-12-18
> The problem I am seeing is that the flashplugin-nonfree package in the repros (as well as flashplugin-nonfree-extrasound) is not working. However, I *am* able to get flash to work if I go out to the Adobe website, download the tar.gz file and install it that way.
well, if installing flash from the tar.gz package works then just keep it, it's exactly the same flash if you use synaptic to install the flashplugin-nonfree (it's installed in /usr/lib/flashplugin-nonfree) maybe your firefox cannot detect flash instaled this way (broken system links) and don't install the flashplugin-nonfree-extrasound, you probably don't need it or if you really have flash sound problems there are others ways you can fix it.

---

### Post by trksh22 on 2008-12-18
This is all so confusing. Flash worked before I upgraded to Ibex. Boohoohoo. 

I donwloaded it from the adobe site, but I got the deb package.... no flash for me! I will have to read back to see if I missed what to do with the tar.gz file. 

Help, please :)

---

### Post by davescafe on 2008-12-18
> **trksh22 said:**
> This is all so confusing. Flash worked before I upgraded to Ibex. Boohoohoo. 

I donwloaded it from the adobe site, but I got the deb package.... no flash for me! I will have to read back to see if I missed what to do with the tar.gz file. 

Help, please :)

Using the tar.gz file is simple and it works. Here are the steps I followed.
[LIST=1]
[*]Download the tar.gz file from Adobe.com
[*]Extract the archive using the command: tar zxvf install_flash_player_10_linux.tar.gz
[*]In a terminal window, change directories into the folder you just extracted ("install_flash_player_10_linux)
[*]at the terminal, run, sudo ./flashplayer-installer
[*]Alternately, you can simply copy the "libflashplayer.so" into /usr/lib/mozilla/plugins
[/LIST]

That's all. It should work.

---

### Post by knightwolf8877 on 2008-12-19
hey I was having the same issue it wouldn't show flash. I had adobe flash installed.


go to synaptic package manager. search for flash. find flashplugin-nonfree adobe flash player plugin installer and uninstall it


I have installed


swfdec-mozilla
libswfdec-0.8-0
 
and it all works perfectly
hope this helps

---

### Post by gandaran on 2008-12-19
> **knightwolf8877 said:**
> hey I was having the same issue it wouldn't show flash. I had adobe flash installed.


go to synaptic package manager. search for flash. find flashplugin-nonfree adobe flash player plugin installer and uninstall it


I have installed


swfdec-mozilla
libswfdec-0.8-0
 
and it all works perfectly
hope this helps
good for you then, nobody  else seams to like swfdec flash! you get that big stupid play button for flash videos play and it won't work on every flash site

---

### Post by tpl on 2008-12-19
QUOTE=davescafe;6396184]Using the tar.gz file is simple and it works. Here are the steps I followed.
[LIST=1]
[*]Download the tar.gz file from Adobe.com
[*]Extract the archive using the command: tar zxvf install_flash_player_10_linux.tar.gz
[*]In a terminal window, change directories into the folder you just extracted ("install_flash_player_10_linux)
[*]at the terminal, run, sudo ./flashplayer-installer
[*]Alternately, you can simply copy the "libflashplayer.so" into /usr/lib/mozilla/plugins
[/LIST]

That's all. It should work.[/QUOTE]

I had the same problem with FF 3.05 and flash no longer working. Followed the above as downloading the .deb did not work for me  ( Error: later version is already installed)  I did have to cp the .so file as the installer seemed to "forget" my sudo when it asked for the destination folder.

---

### Post by t1010011 on 2008-12-19
What worked for me (I'm  using Ibex x64 with the latest automatic updates);

Went to:[URL="http://labs.adobe.com/downloads/flashplayer10.html"]
http://labs.adobe.com/downloads/flashplayer10.html[/URL]

Downloaded the  64-bit Plugin for Linux

extracted contents of the tar.gz
which gives you the file libflashplayer.so

now move it to the folder:
/usr/lib/mozilla/plugins

you can always do that in the archaic way by typing in the terminal:
sudo nautilus
then copy & pasting

---

### Post by tpl on 2008-12-19
I take my last post back.    It worked just once when I restarted FF and that was it.

With all due respect to FF and Ubuntu... IE and flash always keep in working for me on every update. Maybe running IE in Wine is the answer.

---

### Post by jsalcie on 2008-12-19
This Work for me.
 sudo apt-get install adobe-flashplugin
restart firefox
my 2cents.:popcorn:

---

### Post by albinootje on 2008-12-19
> **davescafe said:**
> 
[LIST]
[*]I have completely and cleanly re-installed Ubuntu 8.10 32-bit Desktop 
[*]I have installed all available Ubuntu updates.
[*]I have installed OpenOffice.org 3.0 and VMware Server 2.0, but no other programs
[*]Firefox version: 3.0.5
[*]Flash plugin version (from repros) 10.0.12.36
[/LIST]

I'm using Ubuntu 8.10 - 32-bit
with the Ubuntu repositories + Medibuntu repos.

```

ii  flashplugin-nonfree 10.0.15.3ubuntu1~intrepid1
ii  flashplugin-nonfree-extrasound 0.0.svn2431-3
ii  firefox 3.0.5+nobinonly-0ubuntu0.8.10.1
ii  firefox-3.0 3.0.5+nobinonly-0ubuntu0.8.10.1
ii  firefox-3.0-branding 3.0.5+nobinonly-0ubuntu0.8.10.1
ii  firefox-3.0-gnome-support 3.0.5+nobinonly-0ubuntu0.8.10.1
ii  firefox-gnome-support 3.0.5+nobinonly-0ubuntu0.8.10.1

```
Upgraded firefox and flash-plugin yesterday, tested succesfully with :
[http://www.youtube.com/watch?v=wvsboPUjrGc&feature=related](http://www.youtube.com/watch?v=wvsboPUjrGc&feature=related)

about:plugins shows :
```

    File name: libflashplayer.so
    Shockwave Flash 10.0 r15

```
I don't use the ~/.mozilla/firefox/profile-name-blabla/plugins/
```

ls -la /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root 46 2008-12-19 05:36 /etc/alternatives/mozilla-flashplugin -> /usr/lib/flashplugin-nonfree/libflashplayer.so

```

---

### Post by tpl on 2008-12-19
I solved my particular problem. I uninstalled Gnash.  The videos I needed to see were swf 8.5 and up, Gnash it appears only gets up to swf 7.x 
 Phew!

---

### Post by trksh22 on 2008-12-19
> **davescafe said:**
> Using the tar.gz file is simple and it works. Here are the steps I followed.
[LIST=1]
[*]Download the tar.gz file from Adobe.com
[*]Extract the archive using the command: tar zxvf install_flash_player_10_linux.tar.gz
[*]In a terminal window, change directories into the folder you just extracted ("install_flash_player_10_linux)
[*]at the terminal, run, sudo ./flashplayer-installer
[*]Alternately, you can simply copy the "libflashplayer.so" into /usr/lib/mozilla/plugins
[/LIST]

That's all. It should work.

Thanks for your help. :)
It worked on my last try. Not sure what I did differently from previous tries, but it worked :) 

Thanks all!

---

### Post by poopypants on 2008-12-21
Just wanted to mention that in order for apt-get install to work (jsalcie's method) the partner 3rd party software source needs to be listed and enabled/checked in your software sources. (This will also give you the updates as soon as possible, ie every time there is a check for software updates.)

source is:
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) <branch, eg intrepid> partner

more details here:
[http://ubuntulinuxtipstricks.blogspot.com/2008/12/adobe-flash-avoiding-md5-errors.html](http://ubuntulinuxtipstricks.blogspot.com/2008/12/adobe-flash-avoiding-md5-errors.html) edit: link

---

### Post by IainPurdie on 2008-12-22
I've been hammering at this for days. Finally got it to work today after repeating a load of the above steps. In case it helps anyone else, this may make a difference:

1) using package manager, uninstall the existing free flash player as well as any previous Adobe versions

2) Make sure you have Firefox closed while installing

3) Check the /usr/lib/mozilla/plugins folder. There should be nothing flash-related in here. No symolic links, no nothing.

4) Ensure the Tools / Addons / Plugins info in Firefox doesn't show a Shockwave Flash entry

5) I then used the .deb file from Adobe, opened with the packet manager. Again, once downloaded and before installing I made sure Firefox was closed down. Also ensure it's not "sleeping" or anything in System Monitor. Proper closed.

And it worked. At last. Now I can watch all the videos on TopGear.com :)

---

### Post by cb34 on 2008-12-22
[http://ubuntuforums.org/showthread.php?t=1011649](http://ubuntuforums.org/showthread.php?t=1011649) maybe all the spam in this thread will help you guyz out, i got everything super stable now. :D

or this little bit of blahblah. :D [http://ubuntuforums.org/showthread.php?t=1018373](http://ubuntuforums.org/showthread.php?t=1018373)

good luck all, flash, firefox issues suck. i lost sleep from all this bs. :p

---

### Post by sanjayak on 2008-12-22
I have to downgrade my flash plugin to version 9 to get over the problem. For me, problematic sites give the same problem in Firefox, Konqueror, and Opera. The problem could be some of the web sites having a bad logic to check the flash version.

---

### Post by cb34 on 2009-01-08
i hope this helps:

[http://ubuntuforums.org/showthread.php?t=1034369](http://ubuntuforums.org/showthread.php?t=1034369)

---

