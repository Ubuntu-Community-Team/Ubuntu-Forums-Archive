---
title: "A Problem with Vector Graphics Applications?"
date: 2008-12-27
forum: Multimedia Software
---

### Post by Roger Allott on 2008-12-27
I'd appreciate some help with resolving a matter that's very irritating. The answer might be that my laptop (details in my signature) isn't powerful or sophisticated enough to run the apps that are causing me the problems. That would be fine, if it turns out that that's my problem, but it's a fairly new machine and I'd find it very odd that it's not competent to handle modern bits of software.

The most likely cause is that I've erroneously installed a driver for something I don't have, or I've installed some package(s) that doesn't like being installed with some package(s) that was/were installed beforehand.

There are four apps that cause somewhat similar problems. I'm making a semi-educated stab in the dark that something they all have in common is that they deal with vector graphics to some extent, and that might (or might not) be a clue to what my problem is. The four apps are:
[LIST=1][*]Googleearth 4.2.205.5730-0medibuntu4
[*]Worldwind 0.5.0-1
[*]Celestia (gnome variant) 1.5.1+dfsg1-1ubuntu1
[*]Blender 2.46+dfsg-4[/LIST]

The first two of these give me real grief as regards the images rendered on screen. I've attached screenshots of them to show what I mean. They are completely unusable.

The image rendered in Celestia is at least viewable and recognisable, but the problem is that the display is continually flickering so that I can't use the toolbar to actually do any floating around the universe, which I think is what the app is all about.

Blender has installed OK and I can run it fine (I think), but even when I run the "Blender (windowed)" version, I get it running in full screen mode. That makes it flippin' difficult to follow any tutorials!

There is however a problem that all of these apps give me, and that comes when I close or exit them. None of them seem to shut down properly, as all of them leave me with a residual white screen covering my desktop wallpaper. I have to reboot my machine to get my proper wallpaper back.

So, has anyone got any ideas as to what might be causing a conflict such that these apps don't function correctly?

BTW, I'm running Ubuntu 8.10 and as far as I know my machine does not have a dedicated graphics card.

---

### Post by Roger Allott on 2008-12-30
No responses at all????

Has no one got any idea what might be wrong with my system? Have I omitted an important piece of information that would assist diagnosis?

---

### Post by Roger Allott on 2009-01-07
Well, I'm going to persevere with this thread in the (blind?) faith that someone will respond one day!

I've just done a system update and one package that got updated was nvidia-177-modaliases, which I thought was odd as I'm pretty sure that I don't have an nvidia card or any other type of video or sound card (other than on-board).

Can anyone think of why that package might be useful to me and/or why I shouldn't remove/uninstall it?

Furthermore, I've just searched in Synaptic for any other packages referencing nvidia and it tells me that the following are installed:
[LIST][*]nvidia-common
[*]nvidia-71-modaliases
[*]nvidia-96-modaliases
[*]nvidia-173-modaliases
[*]nvidia-177-modaliases
[*]xserver-xorg-video-nv
[*]smartdimmer
[*]jockey-gtk
[*]jockey-common[/LIST]

Should I remove/uninstall all of those packages?

What search terms should I put into Synaptic to find any other drivers that I may have installed erroneously?

---

### Post by mc4man on 2009-01-08
Can't help you to any real extent
Your graphics is more than likely Intel x3100 (965GM)

The stock response might be to turn off compiz completely. 

As far as the nv stuff installed I don't believe that's an issue, I have nvidia cards and xserver-xorg-video-'everything' is installed, obviously I'm only using the nvidia driver.

There are occasional posts about x3100 and google earth, not overly positive but people rarely post in lieu of an issue.

you could try some <keywords> site:ubuntuforums.org  searches in google

[http://www.googleguide.com/advanced_operators.html](http://www.googleguide.com/advanced_operators.html)

---

### Post by Roger Allott on 2009-01-08
Thanks for that. A bit of googling on "intel x3100 googleearth" yielded a page telling me that to launch the app in 7.10 one must start it by entering:
```
LIBGL_ALWAYS_INDIRECT=1 googleearth
```

So, in for a penny in for a pound, I did that. Googleearth started up as has become familiar now, with a screen similar to the attachment I added to post #1. I closed the screen and was about to close the terminal window when I noticed that it had given me an error message and some sort of crash log.

```
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
Google Earth has caught signal 11.

Stacktrace from glibc:
  /usr/lib/googleearth/googleearth-bin(__gxx_personality_v0+0x1e8) [0x8057fb4]
  /usr/lib/googleearth/googleearth-bin [0x8058399]
  [0xb80ba400]
  ./libbase.so(_ZN5earth8SpinLock4lockEj+0x22) [0xb805a3fc]
  ./libbase.so(_ZN5earth9LockGuardC1ERNS_8SpinLockE+0x1f) [0xb804027f]
  ./libnet.so(_ZN5earth3net18CurlHttpConnection13removeRequestEPNS0_15CurlHttpRequestE+0x25) [0xb7bdd45b]
  ./libnet.so(_ZN5earth3net15CurlHttpRequest4stopEv+0x20) [0xb7bdd4aa]
  ./libnet.so(_ZN5earth3net15CurlHttpRequestD0Ev+0x25) [0xb7bdd4d7]
  ./libnet.so(_ZN5earth3net11HttpRequest5unrefEv+0x35) [0xb7bd5701]
  ./libnet.so(_ZN5earth6RefPtrINS_3net11HttpRequestEED1Ev+0x1e) [0xb7bcc9c2]
  ./libnet.so(_ZN5earth3net14NetworkRequestD0Ev+0x28) [0xb7bcda70]
  ./libbase.so(_ZN5earth8Referent8orphanedEv+0x10) [0xb80354fe]
  ./libbase.so(_ZN5earth8Referent5unrefEv+0x17) [0xb805c1d5]
  ./libnet.so(_ZN5earth3net7FetcherD0Ev+0x42) [0xb7bd1332]
  ./libbase.so(_ZN5earth8Referent8orphanedEv+0x10) [0xb80354fe]
  ./libbase.so(_ZN5earth8Referent5unrefEv+0x17) [0xb805c1d5]
  ./libwmsbase.so(_ZN5earth6RefPtrINS_3net7FetcherEED1Ev+0x1e) [0xb7c2f0ba]
  ./libcommon.so(_ZN5earth6common10HtmlRenderD0Ev+0x52) [0xb649fc46]
  ./libgoogleearth.so(_ZN10scoped_ptrIN5earth6common10HtmlRenderEED1Ev+0x12) [0xb77d4b56]
  ./libgoogleearth.so(_ZN16StartupTipWidgetD0Ev+0x73) [0xb77d3ca1]
  ./libgoogleearth.so(_ZN10scoped_ptrI16StartupTipWidgetE5resetEPS0_+0x1b) [0xb77ddea5]
  ./libgoogleearth.so(_ZN5earth6client11ApplicationD1Ev+0x60) [0xb77d8a48]
  /usr/lib/googleearth/googleearth-bin(main+0x155) [0x805884d]
  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb615d685]
  /usr/lib/googleearth/googleearth-bin(__gxx_personality_v0+0x75) [0x8057e41]




We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/stuart/.googleearth/crashlogs/crashlog-0F901964.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.
```

I've absolutely no idea what all that means, but perhaps someone here might know what went on?

The content of the crashlog text file is:
```
CRASHLOGVER 1
CRASHLOGID 0x0F901964
APPVERMAJOR 4
APPVERMINOR 2
APPVERBUILD 205
APPBUILDDATE Nov 13 2007
APPBUILDTIME 17:52:07
OSTYPE 11
OSVERMAJOR 2
OSVERMINOR 6
OSVERBUILD 27
OSVERPATCH 0
PID 18195
CRASHSIGNAL 11
CRASHTIME 1231395774
PROGRAMUPTIME 47

STACK 0x8057fb4
STACK 0x8058399
STACK 0xb80ba400
STACK 0xb805a3fc
STACK 0xb804027f
STACK 0xb7bdd45b
STACK 0xb7bdd4aa
STACK 0xb7bdd4d7
STACK 0xb7bd5701
STACK 0xb7bcc9c2
STACK 0xb7bcda70
STACK 0xb80354fe
STACK 0xb805c1d5
STACK 0xb7bd1332
STACK 0xb80354fe
STACK 0xb805c1d5
STACK 0xb7c2f0ba
STACK 0xb649fc46
STACK 0xb77d4b56
STACK 0xb77d3ca1
STACK 0xb77ddea5
STACK 0xb77d8a48
STACK 0x805884d
STACK 0xb615d685
STACK 0x8057e41

DSO googleearth-bin/0x8048000/111416
DSO googleearth-bin/0xb80ba000/1076
DSO libbase.so/0xb7ff3000/669696
DSO libcomponent.so/0xb7fdc000/86805
DSO libfusion.so/0xb7fd6000/13124
DSO libgeobase.so/0xb7c70000/3443270
DSO libmath.so/0xb7c55000/103833
DSO libwmsbase.so/0xb7bf0000/395459
DSO libnet.so/0xb7ba6000/287819
DSO libalchemyext.so/0xb7ba0000/15216
DSO libcollada.so/0xb7847000/3388384
DSO libgoogleearth.so/0xb76da000/1439454
DSO libGLU.so.1/0xb765c000/507779
DSO libcrypto.so.0.9.8/0xb7536000/1103016
DSO libcurl.so.3/0xb750c000/159800
DSO libfreeimage.so.3/0xb7449000/770245
DSO libgcc_s.so.1/0xb743e000/39096
DSO libjpeg.so.62/0xb741a000/139688
DSO libmng.so.1/0xb73bd000/364312
DSO libpng12.so.0/0xb7394000/156964
DSO libqt-mt.so.3/0xb6c5e000/7313347
DSO libqui.so.1/0xb6bc2000/621811
DSO libssl.so.0.9.8/0xb6b87000/221460
DSO libstdc++.so.6/0xb6aad000/849472
DSO libtiff.so.3/0xb6a50000/364328
DSO libz.so.1/0xb6a39000/86972
DSO libIGCore.so/0xb6942000/952308
DSO libIGGfx.so/0xb688a000/704928
DSO libIGAttrs.so/0xb6828000/365780
DSO libIGDisplay.so/0xb6813000/70352
DSO libIGGui.so/0xb67d1000/246068
DSO libIGSg.so/0xb66c3000/1036804
DSO libIGCollision.so/0xb66b4000/55044
DSO libIGMath.so/0xb666b000/277228
DSO libIGUtils.so/0xb6643000/146568
DSO libIGOpt.so/0xb6568000/841480
DSO libIGExportCommon.so/0xb64e0000/517352
DSO libcommon.so/0xb63e3000/997730
DSO librender.so/0xb6389000/349174
DSO libauth.so/0xb62fd000/548318
DSO libframework.so/0xb62e6000/86398
DSO libm.so.6/0xb62a5000/145796
DSO libc.so.6/0xb6147000/1406664
DSO libpthread.so.0/0xb612e000/82132
DSO libdl.so.2/0xb6129000/7340
DSO libXrender.so.1/0xb611f000/29100
DSO libXcursor.so.1/0xb6116000/31268
DSO libXft.so.2/0xb6102000/71736
DSO libfreetype.so.6/0xb608c000/459460
DSO libfontconfig.so.1/0xb605e000/173420
DSO libXext.so.6/0xb604f000/52036
DSO libX11.so.6/0xb5f60000/958688
DSO libSM.so.6/0xb5f57000/27140
DSO libICE.so.6/0xb5f3f000/83208
DSO libGL.so.1/0xb5edd000/350728
DSO libGL.so.1/0xb5f33f20/39616
DSO ld-linux.so.2/0xb80a0000/105916
DSO libXfixes.so.3/0xb5ed8000/12628
DSO libexpat.so.1/0xb5eb1000/144352
DSO libXau.so.6/0xb5ead000/5848
DSO libxcb-xlib.so.0/0xb5eaa000/2752
DSO libxcb.so.1/0xb5e91000/92820
DSO libXxf86vm.so.1/0xb5e8b000/14588
DSO libXdamage.so.1/0xb5e88000/4704
DSO libdrm.so.2/0xb5e7e000/25336
DSO libXdmcp.so.6/0xb5e79000/15108
DSO libnss_compat.so.2/0xb5457000/26284
DSO libnsl.so.1/0xb543e000/82720
DSO libnss_nis.so.2/0xb5433000/32904
DSO libnss_files.so.2/0xb5427000/38356
DSO libnss_mdns4_minimal.so.2/0xb62ce000/5908
DSO libnss_dns.so.2/0xb3c1e000/15228
DSO libresolv.so.2/0xb3c0a000/62764
DSO libevll.so/0xb20f5000/6108992
DSO libnavigate.so/0xaf762000/1336238
DSO liblayer.so/0xaf511000/2359150
DSO libmeasure.so/0xaf461000/696250
DSO libbasicIngest.so/0xaf376000/915434
DSO libgooglesearch.so/0xaf2bb000/741326
DSO libinput_plugin.so/0xaf280000/232214
DSO libflightsim.so/0xaf17b000/1022678
```

Would I be correct in thinking that the crashlog is unfathomable to anyone other than a googleearth programmer or support technician?

---

### Post by ender4 on 2009-01-17
> 

Would I be correct in thinking that the crashlog is unfathomable to anyone other than a googleearth programmer or support technician?

i would say that's a fair assumption

---

