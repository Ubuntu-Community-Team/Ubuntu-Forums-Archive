---
title: "Yet another ATI problem"
date: 2006-06-08
forum: Multimedia &amp; Video
---

### Post by Dillius on 2006-06-08
My computer contains an ATI Radeon X800 GTO. My Xorg.conf is showing as finding this video card as far as I can tell, and it is trying to load with the "ati" driver, but whenever it does this Xserver fails to start entirely because of a "No Screens Found" error. I'm betting it's a configuration problem, as a few times it has said more along the lines that no screen may be configured properly, but I haven't got a clue where to start.

Edit: For the most part, I'd be happy to get it running at all. That way I'd have a bit easier of an environment to work on it's functionality such as getting the network working so I can upgrade some packages.

---

### Post by ltmon on 2006-06-08
From a console try:

```

sudo dpkg-reconfigure xserver-xorg

```

If all else fails use "vesa" as your driver rather than "ati" when you do this.  It should at least get you a desktop showing up.

Once you've got that you could try the installation instructions for the fglrx driver (the closed source ATI produced one).  The instructions for this are in various places, but a good clear source is: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

L.

---

### Post by flipkick on 2006-06-08
I really think of dappers (xorg 7) conf file as a weird mixture of settings.

Somehow I managed to install fglrx and fglrxinfo seems to output what i need.

But after 30 minutes of working and especially with firefox, my system refuses work.

Only one specific page, ein klick and my monitor gets black, not possible to change to console or restarting....

why is that F*** that comlicated still ?

---

### Post by flipkick on 2006-06-08
I really think of dappers (xorg 7) conf file as a weird mixture of settings.

Somehow I managed to install fglrx and fglrxinfo seems to output what i need.

But after 30 minutes of working and especially with firefox, my system refuses work.

Only one specific page, one click on that page and my monitor gets black, not possible to change to console or restarting....

why is that F*** that comlicated still ?

---

### Post by Dillius on 2006-06-08
Wow... I have never had so much trouble with Ubuntu before.

I go back to try to just boot the Desktop CD in safe graphics mode. But if I try to use that, i get NO video output at ALL. DVI or VGA.

When I tried to edit my current install to use the Vesa driver instead of ATI, it gave me another screen error about the screens not being configured properly for the Vesa driver.

---

### Post by Dillius on 2006-06-08
[QUOTE=ltmon]From a console try:

```

sudo dpkg-reconfigure xserver-xorg

```

If all else fails use "vesa" as your driver rather than "ati" when you do this.  It should at least get you a desktop showing up.

Once you've got that you could try the installation instructions for the fglrx driver (the closed source ATI produced one).  The instructions for this are in various places, but a good clear source is: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

L.[/QUOTE]

I also tried this technique. Same problem, no output to my monitor AT ALL. I can hear the sound GDM makes when it loads though.

---

### Post by dbarron on 2006-06-08
I have to agree with Dillius (symptom-wise).  I spent 3 hours last night dinking with the xorg.conf and other ideas.  One thing I haven't tried (I assume it will work) is to try running VESA vs an ATI driver/fglrx, nor have I tried an older ATI driver.
Has anyone done either of these two things, (esp if successfully) ?

---

### Post by Dillius on 2006-06-08
Been playing with it a bit more, and at one point my monitor flashed me an "Out of Range" error before going blank. Gonna look up what I can, but I'm using an NEC Multisync LCD 1970GX

EDIT: What I'm trying to figure out is:
Why in the world wouldn't VESA work?

If i'm using the DVI connector instead of the VGA connector, do I need to put it as a different PCI device? like instead of 1:00:0 as 1:00:1?

---

### Post by Dillius on 2006-06-08
Tried using VESA and VGA and ATI drivers, none of them will give me any display whatsoever. Still wondering if anyone knows a magic trick to this.

---

