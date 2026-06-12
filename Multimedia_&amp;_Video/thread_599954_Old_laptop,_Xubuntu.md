---
title: "Old laptop, Xubuntu"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by RealEmotionX on 2007-11-01
Well I dont really expect a resolution to this issue but I am running a old

NEC ready 340T laptop and there are NO Drivers at all

all I really want is to update the graphics driver so I can use the screen to its fullest.

Any suggestions? It does not have a net connection WHAT-SO-EVER.

---

### Post by hardyn on 2007-11-01
could you help those of us that do not want to google the specs of a NEC 340T?

w/o a network conx its going to be tricky... you could find the packages that you need, and download them from a different machine and disk them over to the notebook... BUT... if it does not have a network connection... it probably wont run any better than the VGA or VESA driver anyway, sooo... you probably have it as high as it will go, already.

---

### Post by RealEmotionX on 2007-11-02
Yeah I know the drill about specs but I have no idea what its hardware is either, google turns up little but Ill check


, , ,

all my quick search turned up

's a NEC Ready 340T Notebook with 300 MHz AMD-K6 MMX, 256K Level 2 Cache, 64 MB RAM, 4 GB hard drive, 24x CD, 56K modem, USB ports, external floppy (also swappable with CD), two PCMCIA card slots, 128 bit graphics with 2 MB memory, 16 bit stereo sound, trackpad interface, and 13.3 inch TFT Active Matrix Display. It's running Windows 98 and boasts a bundle including Microsoft Works and Word 97, the essential browser and online wares, etc., as well as other programs.

also when it was running win98 it went to 1024 x 768.

---

### Post by hardyn on 2007-11-02
well 64mb of system ram is slim for a graphical environment period!
a 2mb graphics will not leave you much, you should do some investigating to find what graphics chip is is actually using; you should be able to achieve 1024x768 though the vesa driver.  it would be helpful if you post the contents of your xorg.conf file.

if you have a PCMCIA slot... which you do... ebay up a PC card ethernet port, or better yet a wireless card!  then you can solve your networking problem; of course you will have to decide if throwing any money at a computer that old will be worth it.

cheers.

---

### Post by VCSkier on 2007-11-02
you might be better with an even lighter distro, maybe like [MEPIS antiX]("http://distrowatch.com/?newsid=04562")...  plus, from what i've read, MEPIS has top notch hardware detection and OOTB support, often considered better than Ubuntu's.  Thats just an uneducated suggestion though, I really don't have any experience with these things.

---

### Post by RealEmotionX on 2007-11-03
well my grandmother (this is her machine and she wanted to be able to use it to write a novel but had no copy of 98) wants it back, though she may not be able to read it. it places the 800 x 600 window in a fraction of the screen and has a FN key that streatches it to fit.

also I forgot how to display the xorg into. XD I am a fairly new linux user but I am smart enough to to figure things out quickly.

My grandmother's old computer was running Ubuntu, I dont know how it happened but she LOVED it. But that machine (that was 2 years old) fried, so Xubuntu was a nice alternative for her.

---

### Post by Melcar on 2007-11-03
I currently have Xubuntu 7.10 running on a similar spec. laptop.  333MHz PentiumII CPU, 256MB RAM, 2MB graphics chip (it's a neomagic 256AV).  I only get 2D on the graphics chip and can only display 800x600 (when the laptop was running Win2K it had 3D accel. and could go to 1024x768), but for what it's being used for (web browsing and e-mail) it's more than enough.  I just added an extra wireless card to it to make it more useful.  A bit slow at times (video playback is almost impossible).  I can even run the composite extension for the windows (odd since I don't have 3D accel.).

---

### Post by midir on 2008-03-21
I've been looking for help with exactly the same laptop and display, albeit with Windows 98 rather than Ubuntu. Couldn't find any info on the display chipset anywhere. I couldn't even find the chip when I tried taking the machine apart. But I finally came across this long archived page about running Linux on the NEC Ready 340T:

[http://web.archive.org/web/20020607031837/http://www.sroka.org/nec_ready_340t.html](http://web.archive.org/web/20020607031837/http://www.sroka.org/nec_ready_340t.html)

and this similar page about running Linux on the NEC Ready 330T:

[http://web.archive.org/web/20000815232108/http://sol.cs.binghamton.edu/~pmadden/linux_nec_ready_330t.html](http://web.archive.org/web/20000815232108/http://sol.cs.binghamton.edu/~pmadden/linux_nec_ready_330t.html)

The 330T page says its display chipset is a Neomagic 2160, and a quick search reveals this to be also known as a Neomagic MagicGraph 128XD.

So maybe, possibly, that info will help users of both operating systems. :)

---

