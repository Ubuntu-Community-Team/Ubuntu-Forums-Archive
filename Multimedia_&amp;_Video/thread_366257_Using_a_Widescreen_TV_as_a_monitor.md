---
title: "Using a Widescreen TV as a monitor"
date: 2007-02-20
forum: Multimedia &amp; Video
---

### Post by idheath on 2007-02-20
Hi,

I have Ubuntu 6.10 running on a Mini-ITX system that's connected to my TV (via an XGA PC connection on the TV, not a 'crappy' video connection).

This works fine with Ubuntu set to a  resolution of 1024x768 resolution (only using the 4:3 part of the screen), but my TV is widescreen and has a physical resolution of 1366x768.

How can I reconfigure my system so that I can have a resolution of 1366x768 to match my TV?

Cheers Ian

---

### Post by crispy_420 on 2007-02-21
Would be possible to mod your xorg and add that resolution?

---

### Post by idheath on 2007-02-22
Hi,

I tried that, but unfortunatley it didn't work.

The 'new' resolution doesn't even appear as an option in the Screen Resolution app.

Cheers Ian

---

### Post by jethro10 on 2007-02-22
> **idheath said:**
> Hi,

I have Ubuntu 6.10 running on a Mini-ITX system that's connected to my TV (via an XGA PC connection on the TV, not a 'crappy' video connection).

This works fine with Ubuntu set to a  resolution of 1024x768 resolution (only using the 4:3 part of the screen), but my TV is widescreen and has a physical resolution of 1366x768.

How can I reconfigure my system so that I can have a resolution of 1366x768 to match my TV?

Cheers Ian

I've just come here to ask the exact same question, for a MythTV setup !! Scary.
1. I dont know if all graphics cards go widescreen.
2. I'm happy to buy a new card, but none list 1366x768 (mines a 32" LCD")
3. It seems some cards may have resolutions that the hardware can do but are not listed as the Windows drivers dont do this.

I'm not able to help you today, but tonight i'm gonna be trying this so perhaps we can get somewhere.
Please Please update this thread if you solve it, including what your graphics card and and what version of Ubuntu you used.
It seems to me as if "Widescreen" is not covered much really.
H

---

### Post by rasbach on 2007-02-22
Unfortunately, 1024x768 is the maximum resolution on most of these televisions that have a PC mode.  I have a 61" Samsung DLP, and I too was a little discouraged to learn that 1024x768 was as high as I was able to go.

---

### Post by grim_d on 2007-02-22
i am wanting to connect my pc through my tv also, i have the cable coming tomorrow. Im pretty confident that the pc mode in my tv can support widescreen as i can put my x360 through vga into it happily enough as 1300x768.

I'm just wondering if ubuntu will auto detect the new resolution or will i have to add something to xorg.conf?

---

### Post by 351W on 2007-02-22
I'm running my 26" LCD TV at 1280x768. It looks good and its pretty close to 16:9

---

### Post by tgalati4 on 2007-02-22
Search the forums for setting up dual displays.  It's generally a pain in the *** but once set up it works well.  That way you can have your local display setup with native resolution and your shiny new plasma at its native resolution.

Samsung plasmas send VGA signals for native resolution to powerbooks, so I know that the 42 through 63 inch professional plasmas can address 1366 by 768.  They will scale other resolutions.

You should be able to reconfigure xorg to take the higher resolution--most modern video cards can drive that resolution.  60 Hz is a typical refresh.  46" Samsung pro LCD's I believe are only 1024 by 768, so you get some stretching.

Post your xorg settings and other procedures that work.  We all want to know!

---

### Post by smcnally on 2007-02-22
I can't tell you how to set it up in ubuntu, but having set many HTPCs up I can tell you that you are better off getting a VGA to Component video converter and setting your PC resolution to 1280x720.  This puts out a 720p image to the TV and it looks incredible.  I run my HTPC at that resolution and movies on it look great.  Trying to get a standard PC resolution to work on a NTSC display usually looks bad when compared to this.

---

### Post by grim_d on 2007-02-23
well ive discovered today that my tv CAN accept the widescreen reolution, but i cannot for the life of me get ubuntu to output anything anywhere near 1366x768, can anyone help me out.

through windows i managed something like 1280x720, but it was all stretched in odd ways :(

---

### Post by tgalati4 on 2007-02-23
With only the TV plugged in, not the main computer display:
sudo dpkg-reconfiger xserver-org

Choose wisely.

Make a backup of xorg.conf (reconfigure will also make a backup)

---

### Post by idheath on 2007-02-26
Hi,

I tried 'sudo dpkg-reconfiger xserver-org' but that gave an error.

I assume you meant 'sudo dpkg-reconfigure xserver-org' but this just said that the package 'xserver-org' is not installed.

BTW with reference to the earlier post about TV's resuolutions I've checked and my TV does support WXGA (1366x768).

Cheers Ian

---

### Post by Titus A Duxass on 2007-02-26
> sudo dpkg-reconfigure xserver-org' but this just said that the package 'xserver-org'  - Try "sudo dpkg-reconfigure xserver-xorg" not xserver-org.

---

### Post by tgalati4 on 2007-02-26
Linux is particular about spelling.  Humans a little less so.

---

### Post by grim_d on 2007-03-06
hmm but i would like to swap between my tv and my monitor with a physical cable change, so i want to be able to select 1366x768 (or similar) from the screen resolution menu

---

### Post by tgm4883 on 2007-03-06
I have a vizio vx37l and its resolution I use is 1366x768.  How I did this was adding that resolution to my xorg.conf.  That however didn't put that in my list of resolutions, however, when selecting 1280x768, my tv reports that the resolution that it is using is 1366x768, so you may, if you can, check what your tv is reporting.

---

### Post by cdean on 2007-06-09
There's some information and an xorg.conf in this thread:

[http://ubuntuforums.org/showthread.php?t=463622](http://ubuntuforums.org/showthread.php?t=463622)

---

### Post by Hugolp on 2007-08-09
The solution as someone said before is to add the resolution of 1280x768 to xorg.conf. Its not 1336x768 but it works on my 26" LCD screen. Looks very good. Someone said before that his 32" tv sees the ubuntu 1280x768 as 1336x768.

In conclusion, to get 720p you have to add 1280x768 to xorg.conf.

Hugo

---

### Post by kneedalz on 2007-12-07
I have a 50" Vizio plasma, and on my computer a eVGA GF8800 GTS 320MB PCIe VGA Card.  when I install the gutsy gibon to my computer, everything is ok till I reboot and all I get is a green screen.  tried it with fiesty fawn and got a grey screen. any suggestions?

---

