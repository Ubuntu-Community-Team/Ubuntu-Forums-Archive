---
title: "Need Help Optimizing 7.04 for ATI Radeon"
date: 2007-09-24
forum: Multimedia &amp; Video
---

### Post by creon_of_thebes on 2007-09-24
After four days of work and plenty of hours googling and searching this forum, I finally got 7.04 running on my Toshiba Satellite a215-s4757.  There are a few guides and threads around, and after using the installation CD and trying a few things from each guide/thread, it's up.  Most notably, "Mike's" guide didn't work-- the GUI would crash and the caps lock would blink.

After installing via alternate disc, I edited /etc/X11/xorg.conf and added:

HorizSync 32-56
VertRefresh 32-60

This is all that needed to be done (at least w/ this particular installation).  However, GNOME doesn't look very pretty.  I'd like to make sure I have the ATI drivers installed, and I had it work once before, but my GUI crashed and I couldn't recover it (I'm new).

Assuming you (the reader) have more expertise w/ linux and Ubuntu than I do... why exactly does adding those two lines allow me to boot into the GUI?  How can I make use of my graphics card?  I'm updating right now, so the sound should work afterwards.  I'm not even going to begin worrying about the wireless card yet.

One last question: When in the hell will it become easier to install linux on machines using ATI graphics cards?  IIRC, the ATI drivers for 7.04 are buggy.  When can I expect an updated installer CD that fixes the bug?

Thanks.

---

### Post by creon_of_thebes on 2007-09-24
Also, please note:  any time I've had 7.04 running on this laptop and edited /etc/X11/xorg.conf the GUI crashes.  I was only able to salvage it five minutes ago (after adding the simple Option "MaxTapTime" "0" to disable tap clicks) because I had a xorg.conf.backup.  I rewrote .backup as .conf and it loaded the GUI fine.

Any thoughts on this?

---

### Post by creon_of_thebes on 2007-09-24
Alright, so, I restarted my system after the update and I get the blinking caps and black screen.  I don't know if anything can be done about it.  When will stable ATI drivers become available on an Ubuntu install cd?

---

### Post by Jouke74 on 2007-09-25
Hmm the infamous X1200 Raedon mobile card... That means trouble yes. Start with checking under system administration > restricted drivers if there are drivers available for your ATI card. (With any luck there also might be the wireless card drivers.) If so, install these first, the latest ATI drivers are not the most easy to configure nor really stable for many people. The ones coming in the Ubuntu repository should usually work, but to be honest I don't know whether the X1200 is supported. I assume you installed the Feisty AMD64 bit alternative iso. The name of the ATI drivers is FGLRX.

You might sometimes need to reboot twice to get it to work, after the initial black screen.
(But do keep your back file ready in case of trouble).

The two lines make sure that your monitor refresh rates stay within limits of the range that your monitor allows... But the real problem is that you need to configure your X server right. That is the program that arranges all screen output.

"and trying a few things from each guide/thread". You need to take **one** guide and finish it without errors from start to the begining. If it fails figure out why. See it like taking six recipes for different flavours of a cake. And now you take instructions from a few and simply mix them together. This won't work. (Searching for X1200 does not give much good guides though I can see, only problems.)

---

### Post by creon_of_thebes on 2007-09-25
Thanks for the response.  Think it'll be easier to install Ubuntu on my computer with the next stable release?

---

