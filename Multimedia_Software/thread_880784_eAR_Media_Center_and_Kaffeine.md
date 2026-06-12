---
title: "eAR Media Center and Kaffeine"
date: 2008-08-05
forum: Multimedia Software
---

### Post by calibre97 on 2008-08-05
I installed the eAR Media Center last night and for the most part it's really slick. If nothing else, I like the desktop presentation. My problem is with the "Play DVD" part of the Media Center. I put in a DVD and select it but then I get an error that the DVD is encrypted so I'd need to install libdvdcss and run a script (more on that in a sec).

I downloaded Xine and it can play the DVD fine. I have libdvdcss installed. I have the restricted stuff installed. I have mediabuntu in the repositories. I've done a full update. The problem is Kaffeine. And that script I'm directed to use: /usr/share/doc/kaffeine/install-css.sh. It doesn't exist. In fact, I can't find an "install-css.sh" file anywhere.

Anyone else been playing with eAR OS? I have it on my laptop so I'm not really planning on using it as a typical 'media center' so maybe that's part of the problem. I know the guys behind it are in Greece right now, rightfully enjoying a bit of R&R before spinning up a Live CD update, but I'm hoping someone here can maybe help. As I said, I can watch DVDs with Xine so I'm not completely high and dry, and I'll have to look into streaming and embedded stuff later...oh, while I'm on multimedia...anyone get streaming/embedded Quicktime to work? Last I read, and it was a few weeks ago, Apple had changed something in their check so that the libraries that had been working no longer were. Is that true?

---

### Post by xc3RnbFO8P on 2008-08-05
This **install-css.sh** should be in your computer.
I got it in 
/usr/share/doc/kaffeine/ and
/usr/share/doc/libdvdread3/
Maybe missing from a upgrade?

---

### Post by calibre97 on 2008-08-05
I did a straight install to the empty partition from the Live CD that I downloaded just about a week ago so it's pretty current (should be the 1.10b mentioned on the eAR site but I haven't figured out where to see a distro version number!) and then I did an update from Update Manager after I got onto my wireless network at home. No 'upgrade' per se. I just don't have a /usr/share/doc/kaffeine directory. I have a TON of stuff in .../doc but no kaffeine. Kaffeine is installed and launches from the Dock but no de-CSSing capability yet even though Synaptic says I have libdvdcss installed. I'll check that other location when I get home and may try removing libdvdcss and then reinstalling it.

OK, I don't have /usr/share/doc/libdvdread3 or /usr/share/doc/kaffeine even though I have everything installed!
-kaffeine
-libdvdcss2
-ubuntu-restricted

What am I missing? gxine runs and plays DVDs, but kaffeine won't. I got everything to work in Kubuntu.

---

