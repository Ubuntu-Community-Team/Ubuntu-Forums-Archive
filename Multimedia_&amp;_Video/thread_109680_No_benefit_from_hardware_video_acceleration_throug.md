---
title: "No benefit from hardware video acceleration throughout Gnome"
date: 2005-12-29
forum: Multimedia &amp; Video
---

### Post by reedlaw on 2005-12-29
I wasn't truly aware of this problem until I got a laptop.  Now, due to a slower processor, I can tell that most of the Gnome rendering of windows and video is likely done by the CPU.

How do I know?  I tried playing a 720p (HDTV) resolution movie trailer and on my fast desktop barely got a moving image and on my laptop almost nothing at all.  The notebook came with Windows which after failing to get a full refund for, I tried it out for a comparison.  What a surprise!  I got a full-screen, silky-smooth video playback.

So what is wrong?  I've followed several threads on Gnome's slowness and Linux responsiveness is general, but I think the problem is larger than that.  It seems that whatever software is responsible for redrawing windows or displaying video has no access to the full power of my video hardware.  This laptop has an Intel 915 chip in it and I can play Enemy Territory and other 3d accelerated games with no problem.  Why can't some of that power be applied to 2d displays?

Another possibly related problem is that on every laptop I have installed Ubuntu Breezy on the video playback is very light and washed out.  It looks like the contrast is turned up very high.  I saw no such problem in Windows.  

IMHO this is a serious problem that needs to be remedied ASAP to ensure the successful adoption of Linux on the desktop.  Please respond with your suggestions and/or deeper knowledge on this subject, which I admit, I am nearly clueless about.

---

### Post by anil_robo on 2005-12-29
I have problems with hardware acceleration only with wine. Everything else works great!

Regarding movies, VLC is playing all the movies very smoothly for me, even the high resolution ones, just as it was doing in windows. Totem gives bad video quality, especially with wmv files, even with appropriate codecs.

But yes, you're right to some extent. This issue needs some discussion, and a search in the forums would disclose that it is already being discussed in great details elsewhere.

---

### Post by Swab on 2005-12-29
Check out [this thread on composite managers]("http://www.ubuntuforums.org/showthread.php?t=75527")...  should speed things up for you.

Edit:  Actually from reading the thread myself, you need a decent nvidia or ati card.

---

### Post by reedlaw on 2005-12-30
I am aware of the poor video quality in Totem, but I also get the washed out look in VLC on every laptop I tested.  Aparently it has to do with the LCD.  I will test it on a desktop with an LCD screen and report back my results.  The issue is video appears very bright and high-contrast.  Desktop elements appear normal.  Games perform fine, it's only video that show this problem, regardless of codec or wrapper (AVI, MOV, MPEG, etc.).

Another serious issue that Ubuntu and Linux in general fails in is getting a proper browser-plugin for all types of media.  On my new Windows installation I bypassed both Quicktime and Real Player for Quicktime Alternative and Real Alternative.  Both codec work flawlessly.  Both have browser plugins that work, albeit only in IE, not in Firefox.  If the Windows camp can produce free codecs and plugins that work, why can't we do it too?  Actually the codecs are well taken care of in Linux, it is just the working browser plugins that are lacking.  I have tried mozplugger, mplayer plugin, VLC plugin, etc. but all of them fail in certain situations.  The totem plugin would even crash Firefox everytime I navigated away from a video!  The one area that most Firefox plugins fail is Apple's quicktime movie trailers.  I could only get this working in Windows with IE and Quicktime Alternative.

---

