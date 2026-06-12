---
title: "Black screen of death"
date: 2007-01-15
forum: Multimedia &amp; Video
---

### Post by kristjans on 2007-01-15
I installed Intel graphics drivers & everything was okay, except the screen flickered on a low refresh rate (the widescreen resolution was working without any extra resolution hacks). 

So, I tried editing xorg.conf, but I believe I totally messed it up & the screen is now completely black. It would be nice for someone to help me configure xorg.conf for my laptop (Gateway 6510 GZ)... :) 
One time it actually even worked... I was in terminal (safe mode), exited and went to another room. I came back and my desktop was there in all beauty... Soon I pressed CTRL+ALT+BACKSPACE and the screen turned black again. :mrgreen: 

I attached the logs and xorg.conf, so you can see, how much of a n00b I am:D

---

### Post by peabody on 2007-01-15
I'd try running a "sudo dpkg-reconfigure xserver-xorg" at the terminal and walking through it to get your xorg.conf back to something sane.  I sounds like you may have to manually enter the refresh rate settings of your laptop's LCD.  Those you'll have to look up I'm afraid.

---

### Post by kristjans on 2007-01-15
And what about if I can't find the refresh rate?

---

### Post by peabody on 2007-01-15
The only thing you'll be able to do is make a best guess at a generic monitor profile from the wizard in "sudo dpkg-reconfigure xserver-org".

---

### Post by kristjans on 2007-01-15
kristjans@kristjans-laptop:/etc$ sudo dpkg-reconfigure xserver-org
Package `xserver-org' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-org is not installed

As soon as I did that, I typed in reboot.

Then I was away again (not physically, mentally for this time :)), and before I noticed, I had the log in screen. Now I'm back in my beatiful desktop. Which flickers like hell and kills my eyes.

---

### Post by peabody on 2007-01-15
Sorry about that, made a typo.  That should have been xserver-xorg.

---

### Post by kristjans on 2007-01-15
Now it doesn't work again. I asked the Gateway technical support for details, but they talked about correcting the screen resolution in Windows XP and everything else unrelated. :rolleyes:

---

### Post by kristjans on 2007-01-16
It's getting worse

[quote=Gateway Tech Support]
Thank you for your e-mail.  To address your issue on your Gateway 6510GZ
notebook that has a horizontal lines on its LCD, I would like to inform 
you that this behavior occurs when the video driver of your computer 
becomes corrupted or has been altered.

[...]

Russel
Badge GWEL5120
[/quote]

](*,)

All the information on their website:

[quote=Gateway Specifications]
    * 15.4-inch active matrix (TFT) LCD color display
    * Maximum panel resolution: 1280 × 800
    * Maximum color depth: 32-bit (16.7 million colors) at 1024 × 768 and 262,144 colors at 1280 × 800
[/quote]

Would it be any help to set up the screen, so it won't give the black screen when not in the safe mode AND not flicker in any mode?

---

### Post by peabody on 2007-01-16
I wish I knew what to tell you.  The only thing I can recommend is that you keep trying the "sudo dpkg-reconfigure xserver-xorg" thing and play with it until you manage to find something that works.

---

### Post by kristjans on 2007-01-16
What I was thinking was that if there could be some failsafe value to put there, I could expand the frequency ranges in xorg.conf until it stops working... and then find the maximum that works... Does it make sense and what do you think would it work? And any recommendations what to start with, if it is possible? :D

And:
[http://forum.notebookreview.com/showthread.php?p=1752669#post1752669](http://forum.notebookreview.com/showthread.php?p=1752669#post1752669)

Any comments on that (first) reply there?

---

### Post by peabody on 2007-01-16
That could work although you need to be very careful about what a valid range is, too little could be invalid as well as too much.  I really thought there was something like "generic laptop lcd" or some such in the choos a monitor profile section of that wizard I told you about.  Does nothing seem to work?

---

### Post by kristjans on 2007-01-16
The "sudo dpkg-reconfigure xserver-org" doesn't even automatically detect 1280x800 resolution. Anyways, I was thinking it might be also something caused by the Intel driver - because if I remember right, the black screen first appeared on ctrl+alt+backspace... And then ever since, with a few exceptions.

Anyways, out of interest :rolleyes: I opened my laptops LCD monitor... it didn't open up all the way, but with a bit effort I managed to read the sign that said "Model No B154EW01". :mrgreen: 

Well, I Googled around a bit and found someones configuration files -- which, of course didn't work. And then I saw an eBay offer for 6510GZ display panels and sure enough, there was a model B154EW01-V5 listed.

Here's a link to B154EW01-V1 specifications:
[http://www.auo.com/auoDEV/products.php?sec=notebook&func=info&product_id=89&items_id=2](http://www.auo.com/auoDEV/products.php?sec=notebook&func=info&product_id=89&items_id=2)

And then I found this:
> 
Näyttö AU Optronics B154EW01
Tunnus AUO1974
Valmistaja B154EW01 V9
Näytön tyyppi 15"" LCD
Valmistuspäiväys viikko 1 / 2005
Sarjanumero ei ole
Näytön enimmäiskoko 33 cm x 21 cm (15.4"")
Kuvasuhde 5:3
Vaakataajuus 30 - 83 kHz
Pystytaajuus 56 - 75 Hz
Erotuskyky enimmillään 1280 x 800
Gamma 2.20
DPMS-tilan tuki ei ole 


I happened to be born in Estonia, and this text is in Finnish. Well, due to some coincidence Finnish happens to be the closest related language to Estonian, so I can pretty much understand what it says:

Horizontal frequency:
Vaakataajuus 30 - 83 kHz

Vertical frequency:
Pystytaajuus 56 - 75 Hz

DPMS-tilan tuki ei ole 
No DPMS support... :D

I'll be right back, going to try this out. :mrgreen:

---

### Post by kristjans on 2007-01-16
Okay, at least there's no black screen this time... but the screen is still flickery... 

1) Should I try to reinstall Intel's drivers?
2) Could it have to do something with running in 16-bit mode? My screen supports up to 18-bit, but I don't know how to get it working in 18-bit mode.

---

### Post by scientus on 2007-01-24
i had a similar problem with my toshiba running kubuntu after a failed attempt to run dual screens (intel 945 card)...
I had to run sudo dpkg-reconfigure xserver-xorg force it into 1024x768 keep whatever it refresh rate it gave me, go into desktop (KDE).
Then  Control Center>Monitor&Display>Hardware.  Configure... button and the detect display. Restarted and problem was fixed...Hope you work it out and I dont know if this will help any

---

