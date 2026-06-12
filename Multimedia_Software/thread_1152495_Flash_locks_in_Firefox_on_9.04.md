---
title: "Flash locks in Firefox on 9.04"
date: 2009-05-07
forum: Multimedia Software
---

### Post by ralphwroberts on 2009-05-07
Yep, I know lots has been posted already on this problem (tons of people seem to have it) ... and I have tried all that stuff! New drivers (I have Nvidia), reinstalling Firefox, deleting gnash and other Flash players, reinstalling Flash from Adobe... etc. etc.  Like many, updating from 8.10 to 9.04 broke video, especially in Firefox.

let's simplify ... try to run a Flash video from a website and it locks up ... check the error console in Firefox and you get:

Warning: Expected ':' but found 'undefined'.  Declaration dropped.

what does this mean and how do we fix it?

thanks!

--Ralph

---

### Post by ralphwroberts on 2009-05-08
anyone?

---

### Post by ralphwroberts on 2009-05-22
*kick*

I've tried everything I could find... Flash just locks in Firefox.

surely the message I posted above is a clue to a fix?

--Ralph

---

### Post by VeN0mizer on 2009-05-22
I've got the same crap going on and I am using the open source ATI drivers...but my system hangs with those all the time anyways...but yes...flash locks up firefox for me too and I have to whip out the trusty old terminal to kicks its teeth in :(

---

### Post by ralphwroberts on 2009-05-23
yes, quite a few of us seem to be having this problem with Flash.

Here's another clue, O Great Ubuntu Bug Stompers. This seems related to networking. When I try to watch a Flash clip in Firefox, it seems to lock not only Firefox but also the network, i.e. email does not go through, SSH connections drop, etc.

Now, just to throw in a bit of empirical testing, I fired up VLC. I could watch FLV files on the local machine (HP with AMD 64 chip) fine. But call one up over the network (both LAN and Internet) and the same lockup occurs as happens in Firefox.

In short, Flash and Jaunty are not on speaking terms if the Flash is coming from outside.

Can someone kill this durn bug, please?

--Ralph

---

### Post by gandaran on 2009-05-23
> **ralphwroberts said:**
> yes, quite a few of us seem to be having this problem with Flash.

Here's another clue, O Great Ubuntu Bug Stompers. This seems related to networking. When I try to watch a Flash clip in Firefox, it seems to lock not only Firefox but also the network, i.e. email does not go through, SSH connections drop, etc.

Now, just to throw in a bit of empirical testing, I fired up VLC. I could watch FLV files on the local machine (HP with AMD 64 chip) fine. But call one up over the network (both LAN and Internet) and the same lockup occurs as happens in Firefox.

In short, Flash and Jaunty are not on speaking terms if the Flash is coming from outside.

Can someone kill this durn bug, please?

--Ralph
vlc or any other player don't use adobe flash plugin only firefox uses it and your problem with adobe flash in jaunty could be related to pulseaudio.
now which jaunty do you have 32-bits or 64-bits, if 64-bits have you tried the 64-bits pre-release adobe flash? 
have a look at this [pulseaudio fix guide]("http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio+fixes"), maybe it'll help.

---

### Post by ralphwroberts on 2009-05-23
> **gandaran said:**
> vlc or any other player don't use adobe flash plugin only firefox uses it and your problem with adobe flash in jaunty could be related to pulseaudio.
now which jaunty do you have 32-bits or 64-bits, if 64-bits have you tried the 64-bits pre-release adobe flash? 
have a look at this [pulseaudio fix guide]("http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio+fixes"), maybe it'll help.

thanks for the response.

uname -a
Linux briley 2.6.28-12-generic #43-Ubuntu SMP Fri May 1 19:27:06 UTC 2009 i686 GNU/Linux

32 bit looks like (although this is a 64-bit machine and I thought 64-bit was installing).

I did the pulseaudiofix guide and it made no difference, alas. Flash videos start, play 1-2 seconds, then lockup.

---

### Post by gandaran on 2009-05-23
> **ralphwroberts said:**
> thanks for the response.

uname -a
Linux briley 2.6.28-12-generic #43-Ubuntu SMP Fri May 1 19:27:06 UTC 2009 i686 GNU/Linux

32 bit looks like (although this is a 64-bit machine and I thought 64-bit was installing).

I did the pulseaudiofix guide and it made no difference, alas. Flash videos start, play 1-2 seconds, then lockup.
can you confirm firefox is using adobe flash and not some open source flash like swfdec or gnash? when you right click the flash video window does it say adobe flash player 10 or something else?

---

### Post by ralphwroberts on 2009-05-23
> **gandaran said:**
> can you confirm firefox is using adobe flash and not some open source flash like swfdec or gnash? when you right click the flash video window does it say adobe flash player 10 or something else?

yep, definitely running latest version of Adobe Flash... I've checked all the stuff posted in the forums like swfdec and gnash (removed), upgraded video drivers, using the kernel from Proposed repo, ET AL.

that ain't it.

really frustrated... gotta get Flash working.

---

### Post by gandaran on 2009-05-24
> **ralphwroberts said:**
> yep, definitely running latest version of Adobe Flash... I've checked all the stuff posted in the forums like swfdec and gnash (removed), upgraded video drivers, using the kernel from Proposed repo, ET AL.

that ain't it.

really frustrated... gotta get Flash working.
have you tried disabling flash hardware acceleration? right click flash video window » settings » enable/disable hardware acceleration.

---

### Post by WubbleU on 2009-05-24
> **gandaran said:**
> have you tried disabling flash hardware acceleration? right click flash video window » settings » enable/disable hardware acceleration.
I also have this problem, and no, disabling hardware acceleration does not fix it.

---

### Post by ralphwroberts on 2009-05-24
> **gandaran said:**
> have you tried disabling flash hardware acceleration? right click flash video window » settings » enable/disable hardware acceleration.

thanks... I'll try ANYTHING at this point ... so I did click off hardware acceleration, exited and reentered Firefox. Still locks. ... also tried telling Flash it could use unlimited space for storage. Still locks.

Any other ideas, guys? I remember when I upgraded to 8.04, it was a pain getting Flash to work again and a slightly longer pain after going to 8.10. ... but 9.04 is turning into a BEAR!

---

### Post by gameover2008 on 2009-05-26
Hello. What does you pluginreg.dat say?

[located here]
  ~/.mozilla/firefox/<some chars>.default/pluginreg.dat

///g

---

### Post by WubbleU on 2009-05-31
My pluginreg.dat

```

Generated File. Do not edit.

[HEADER]
Version:0.09:$

[PLUGINS]
/usr/lib/jvm/java-6-sun-1.6.0.13/jre/lib/amd64/libnpjp2.so:$
:$
1236627719000:1:7:$
:$
libnpjp2.so:$
34
0:application/x-java-vm:Java::$
1:application/x-java-applet:Java::$
2:application/x-java-applet;version=1.1:Java::$
3:application/x-java-applet;version=1.1.1:Java::$
4:application/x-java-applet;version=1.1.2:Java::$
5:application/x-java-applet;version=1.1.3:Java::$
6:application/x-java-applet;version=1.2:Java::$
7:application/x-java-applet;version=1.2.1:Java::$
8:application/x-java-applet;version=1.2.2:Java::$
9:application/x-java-applet;version=1.3:Java::$
10:application/x-java-applet;version=1.3.1:Java::$
11:application/x-java-applet;version=1.4:Java::$
12:application/x-java-applet;version=1.4.1:Java::$
13:application/x-java-applet;version=1.4.2:Java::$
14:application/x-java-applet;version=1.5:Java::$
15:application/x-java-applet;version=1.6:Java::$
16:application/x-java-applet;jpi-version=1.6.0_13:Java::$
17:application/x-java-bean:Java::$
18:application/x-java-bean;version=1.1:Java::$
19:application/x-java-bean;version=1.1.1:Java::$
20:application/x-java-bean;version=1.1.2:Java::$
21:application/x-java-bean;version=1.1.3:Java::$
22:application/x-java-bean;version=1.2:Java::$
23:application/x-java-bean;version=1.2.1:Java::$
24:application/x-java-bean;version=1.2.2:Java::$
25:application/x-java-bean;version=1.3:Java::$
26:application/x-java-bean;version=1.3.1:Java::$
27:application/x-java-bean;version=1.4:Java::$
28:application/x-java-bean;version=1.4.1:Java::$
29:application/x-java-bean;version=1.4.2:Java::$
30:application/x-java-bean;version=1.5:Java::$
31:application/x-java-bean;version=1.6:Java::$
32:application/x-java-bean;jpi-version=1.6.0_13:Java::$
33:application/x-java-vm-npruntime:::$
/usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so:$
:$
1239706446000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.26.1 plugin handles video and audio streams.:$
QuickTime Plug-in 7.2.0:$
5
0:video/quicktime:QuickTime video:mov:$
1:video/mp4:MPEG-4 video:mp4:$
2:image/x-macpaint:MacPaint Bitmap image:pntg:$
3:image/x-quicktime:Macintosh Quickdraw/PICT drawing:pict, pict1, pict2:$
4:video/x-m4v:MPEG-4 video:m4v:$
/usr/lib/totem/gstreamer/libtotem-mully-plugin.so:$
:$
1239706446000:1:5:$
DivX Web Player version 1.4.0.233:$
DivX® Web Player:$
1
0:video/divx:AVI video:divx:$
/usr/lib/totem/gstreamer/libtotem-gmp-plugin.so:$
:$
1239706446000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.26.1 plugin handles video and audio streams.:$
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
/usr/lib/totem/gstreamer/libtotem-cone-plugin.so:$
:$
1239706446000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.26.1 plugin handles video and audio streams.:$
VLC Multimedia Plugin (compatible Totem 2.26.1):$
19
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
18:application/x-totem-plugin:Totem Multimedia plugin::$
/usr/lib/xulrunner-addons/plugins/libunixprintplugin.so:$
:$
1240705237000:1:5:$
The demo print plugin for unix.:$
Demo Print Plugin for unix/linux:$
1
0:application/x-print-unix-nsplugin:Demo Print Plugin for Unix/Linux:.pnt:$
/usr/lib/xulrunner-addons/plugins/libnullplugin.so:$
:$
1240705237000:1:5:$
The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.:$
Default Plugin:$
1
0:*:All types:.*:$
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so:$
:$
1243153234000:1:7:$
Shockwave Flash 10.0 r22:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$

```

---

### Post by The Funkbomb on 2009-06-02
I'm having the same issue.  Some flash works, others does not.  Youtube works, some miscellaneous videos do not.

I'm running 9.04 x64.  Everything is up to date...

Here is what happens.  I try to view a video and it doesn't load.  Then Firefox grays out.  If I go into system monitor, npviewer.bin is eating up all my CPU.  Usually I'm running around 3% with spikes to 10%.  npviewer.bin will spike it up to 100% and stay there.  If I kill npviewer.bin, firefox will unfreeze but no video love.

For jollies, I ran firefox through terminal and this is what I get...

```
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
*** NSPlugin Wrapper *** ERROR: NPP_Destroy() wait for reply: Connection closed
*** NSPlugin Wrapper *** ERROR: NPObject 0x2e09a90 is no longer valid!
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:1854):invoke_NPP_Destroy: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** ERROR: NPObject 0x480c420 is no longer valid!
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:1923):invoke_NPP_SetWindow: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2533):invoke_NPP_HandleEvent: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:1923):invoke_NPP_SetWindow: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2533):invoke_NPP_HandleEvent: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:1923):invoke_NPP_SetWindow: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2533):invoke_NPP_HandleEvent: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:1923):invoke_NPP_SetWindow: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2533):invoke_NPP_HandleEvent: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:1854):invoke_NPP_Destroy: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** ERROR: NPObject 0x37a8600 is no longer valid!

```

I went through synaptic and reinstalled both NSPlugin and the flash plugin with no luck.

---

### Post by linenoise on 2009-09-08
Another "me too" post.  Is anything moving on this?  Anyone have any ideas?  This is supremely frustrating.

---

