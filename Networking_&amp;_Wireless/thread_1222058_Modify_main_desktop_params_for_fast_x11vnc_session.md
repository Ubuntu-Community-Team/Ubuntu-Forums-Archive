---
title: "Modify main desktop params for fast x11vnc session through CLI"
date: 2009-07-24
forum: Networking &amp; Wireless
---

### Post by sadohert on 2009-07-24
Up until now I've been running a separate vncserver on display :2 using icewm that I connect to through an ssh tunnel from work so I can use my home computer for stuff, and the network response is reasonably fast (smaller resolution, lower weight window management, etc.).  I'd really rather use my main gnome desktop.  The bundled vino setup was giving me issues where my mouse clicks were WAY delayed.  I've now discovered x11vnc, which has some cool features (desktop scaling for example).  But now the network response isn't great.  I'm hoping someone can point me to some CLI trickery I can use to cripple my main desktop for teh duration of the vnc session.  Things like:

-Lower resolution
-Use a solid coloured background
-Disable desktop effects
-other handy optimizations.

Can anyone point me at what kinds of commands I might run?  gconftool2 type stuff maybe?

Thanks a lot.  

I'm continuing to search and will be back if I find anything helpful.

Stu

---

### Post by krunge on 2009-07-24
For tuning x11vnc settings have a look here:
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-slow-link](http://www.karlrunge.com/x11vnc/faq.html#faq-slow-link)[/INDENT]
and also the surrounding FAQs.

You can use xrandr(1) to change the screen resolution via the cmdline.

Note that using x11vnc's -scale option typically reduces performance (more CPU overhead and less VNC compression.)

x11vnc has an option "-solid" to try to set a solid background when vncviewers are connected.  If it doesn't work, you can see it printing out the gconf cmds it is running to try to toggle the solid background, so you could try to fix it.

To speed up the rate at which x11vnc can read the pixels out of your framebuffer consider using nvidia proprietary drivers if your graphics card is nvidia.  Also changing the display depth from 32bpp to 16bpp can give a 2X speedup (but AFAIK display depth cannot be switched dynamically.)

I've heard "metacity --replace" will disable compiz animations and "compiz --replace" will restore them (personally I would simply disable compiz 100% of the time; it's useless.)

Try the x11vnc option "-ncache 10" described here:
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching](http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching)[/INDENT]
it will try to do client side caching of pixel data (be forewarned you may be able to **SEE** the cached data below your desktop.  SSVNC on unix/macosx is good at hiding this from your view.)

Experiment with different VNC encodings (ZRLE, Tight) and quality settings.

x11vnc has recently added TurboVNC support.
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-turbovnc](http://www.karlrunge.com/x11vnc/faq.html#faq-turbovnc)[/INDENT]
Depending on your circumstances that may give some speedup. You'd need a TurboVNC viewer (either TurboVNC or recent SSVNC)

---

### Post by sadohert on 2009-07-27
Thanks a lot, krunge!  I appreciate the new ideas to try out.

Notes on those things that I have tried so far:

1.  The solid colour background thing doesn't seem to work for me, but I'll have a look at the output from x11vnc and see if this gives me any clues on what else to try.
2.  I tried that ncache feature, and did in fact see the cached data (if I understand what you're saying correctly).  I basically saw a strip of my desktop repeated right below the regular desktop in my vnc viewer.
3.  I briefly played around with the metacity/compiz --replace commands.  They seemed to work in general, although I found after 2 switches back and forth a bunch of window manager stuff seemed to get screwed up.  Basically, all the border bits of my application windows disappeared (ie. that part along the top of a window you can click and drag the window around with).

Btw, I am using the Nvidia prop. drivers.

Anyway, I'll tinker some more and follow up if I get anywhere.  Being able to reduce the screen resolution through the command line will be handy.

Stu

---

### Post by krunge on 2009-07-27
> **sadohert said:**
> 2.  I tried that ncache feature, and did in fact see the cached data (if I understand what you're saying correctly).  I basically saw a strip of my desktop repeated right below the regular desktop in my vnc viewer.
Yes, if you can live with that you can often get a nice speedup; I use -ncache every day with remote desktops: with it I actually find -solid isn't needed and I use a full jpeg photo for my remote background (because the background is cached on the viewer-side.)

As I said, if you are viewing from unix or macosx the SSVNC viewer does a good job of hiding the cache region. On Windows it depends on how your viewer handles auto-scrolling, etc.

It is too bad after all of these years the VNC protocol doesn't support a client-side caching encoding, then we probably wouldn't need to use the -ncache hack...

---

