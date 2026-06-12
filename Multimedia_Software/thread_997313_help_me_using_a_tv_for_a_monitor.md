---
title: "help me using a tv for a monitor"
date: 2008-11-29
forum: Multimedia Software
---

### Post by facewithnoname54 on 2008-11-29
ok i have a small problem i just pick up a 42 inch plasma that im using and i hooked my pc into it but when i boot up the screen is off and i can get to anything to resize it i end up missing about a inch of the top the bottom is but its like someone has pulled the screen to the left because i cant see at least three inches on the left and a huge black bar on the right i did manage to get it to work so that i can type this out but when i restart it goes back to the way it was but like right now everything is way to big i just want to shink it a little is there anything i can do 
 thank you for your help

---

### Post by facewithnoname54 on 2008-11-29
or can someone tell me how to get more options as far as resolution goes i only have two at the moment that i can use 800 x 600 (4:3) and 600 x 480 (4:3) there is one more but it moves the screen like i described before

---

### Post by scorp123 on 2008-11-29
> **facewithnoname54 said:**
>  800 x 600 (4:3) and 600 x 480 (4:3) there is one more but it moves the screen like i described before How did you connect to your TV?

Modern TV's should have a DVI-port so you could connect it directly to your graphics card and use it as if it were a screen. I have a cheapo ACER LCD-TV ("HD ready ... " yeah, riiiight) which can do 1366 x 768 Pixels max. and it works tip top as "PC screen" when connected via DVI to any of my computers.

If you connected using some "TV Out" port which your graphics card may have then matters are a bit more complicated. Classic TV signals are divided into three camps as far as their standard goes:
[LIST]
[*]SECAM ... which is only used by France, some former French colonies in Africa and most former Soviet-Republics incl. Russia.
[*]PAL ... which is what most of the world uses. 720x576 pixels, 50 Hz.
[*]NTSC ... which is what you'd use in the Americas, the Caribbean, Thailand, the Philippines and Japan. 640x480 pixels, 60 Hz.
[/LIST]

So depending on which TV standard your TV operates under you'd have to adjust your screen resolution (PAL: 720x576) to either 640x480 or 800x600 and you'd have to set the refresh rate right (PAL: 50 Hz), or else there is a high likeliness that the picture will be shaking and/or not correctly positioned on the screen.

If you use classic TV signals then you most likely won't be able to go beyond 800x600 as this is the max. resolution the old classic TV standards can handle.

If you need higher resolutions you'd have to go with the VGA/DVI port of your TV set.

---

### Post by facewithnoname54 on 2008-11-30
well im running it into a the pc port on the back of the tv directly into the video card and i had a ton of resolution to choose from at first but i was trying to fix the problem i was haveing and ended up losing alot of the resolution settings i had before i am using it right now but when the icons are the size of a golf ball its kinda annoying i just want to go to a higher res to shink them down

---

### Post by Forlong on 2008-12-01
Your description lacks two major infos needed: what graphics card and what driver are you using?

Also: what exactly did you do to end "up losing alot of the resolution settings"?


P.S. [http://en.wikipedia.org/wiki/Punctuation](http://en.wikipedia.org/wiki/Punctuation)

---

### Post by facewithnoname54 on 2008-12-02
> **Forlong said:**
> Your description lacks two major infos needed: what graphics card and what driver are you using?

Also: what exactly did you do to end "up losing alot of the resolution settings"?


P.S. [http://en.wikipedia.org/wiki/Punctuation](http://en.wikipedia.org/wiki/Punctuation)

Well I'm not so sure about the drivers. And what I did i couldn't tell you to save my life.... I put some command in the terminal that I read on another forum page they said it solved there problem like I was having so I tried it. Ended up losing more the what I started with. Anyway I'm running a Power Spec computer that was bought from Microcenter in 05-06 the graphics card is Via UniChrome. It came with Xp on it and it used the s3 video drivers. I don't know what Ubuntu is running it with or how to look that up.

O and I hope the punctuation is better its from all those years texting and instant messaging.... Pretty clever tho I like that

---

### Post by Forlong on 2008-12-02
You can run [Compiz-Check]("http://forlong.blogage.de/entries/pages/Compiz-Check") to find out what graphics chip and driver you are using.

A general note regarding VIA: their support for Linux has been disappointing in the past but they are working on it now. I'm not sure how well Intrepid supports VIA chips, maybe you'll have to install a driver directly from their site.

In any case: once you know exactly what type of chip you have, you will be able to find support (at least) by those using the same.

---

### Post by facewithnoname54 on 2008-12-02
Ok so I ran compiz-check and it skipped it because openchrome driver is in effect I am getting ready to research it but thats the only driver it gives me

---

### Post by Forlong on 2008-12-02
Please post the full output here.

---

### Post by facewithnoname54 on 2008-12-02
stephen@stephen-desktop:~$ compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         VIA Technologies, Inc. CN400/PM800/PM880/PN800/PN880 [S3 UniChrome Pro] (rev 02)
 Driver in use:         openchrome
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Your current resolution is too high to run Compiz. 

Would you like to know more? (Y/n) y

 Your resolution is 1280x720 but the maximum 3D texture size that your
 graphics card is capable of is 512x512. Thus Compiz won't be able to run
 on this setup. You have to decrease the resolution first (in case you are
 using a dual-head setup, try disabling one monitor and run the script again). 

stephen@stephen-desktop:~$

---

### Post by Forlong on 2008-12-02
OK... first of all, I need to get this off my chest: how come you have a 42" plasma but such a crappy graphics chip? :)

Anyway... how does your **/etc/X11/xorg.conf** look like?
You can post it like this:
```
grep -v ^# /etc/X11/xorg.conf
```
and use the forum's [noparse][CODE][/noparse] tag please (# button)

---

### Post by philetus on 2008-12-02
I may be wrong, but I think your graphics driver is malfunctioning.

---

### Post by facewithnoname54 on 2008-12-02
So according to that I can't run compiz. And i would like to but that resolution is to big and I don't have a selection for it. Would it just be better to upgrade my vid card? The one I have now is built on the board. Can I upgrade it and not have any issues I may have to go with agp and suggestions on a card that would work? Thats only if you think is worth it though I also would like to have the hdmi input for the tv.

---

### Post by facewithnoname54 on 2008-12-02
Well in my defense I just got the tv its was a deal that I couldn't pass 500$ bran new... Anyway here is what you said to type in ```
stephen@stephen-desktop:~$ grep -v ^# /etc/X11/xorg.conf

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
stephen@stephen-desktop:~$ 


``` 
Thats all that came up when I did that.

---

### Post by Forlong on 2008-12-02
> **facewithnoname54 said:**
> So according to that I can't run compiz.
I doubt that it would be possible anyway.
> **facewithnoname54 said:**
> Would it just be better to upgrade my vid card?
If you can afford it: yes, definitely!
> **facewithnoname54 said:**
> The one I have now is built on the board. Can I upgrade it and not have any issues
I think so. If there's any problems with the onboard graphics and the new card. you could disable it in the BIOS, but I doubt it will be necessary.
> **facewithnoname54 said:**
> I may have to go with agp and suggestions on a card that would work? Thats only if you think is worth it though I also would like to have the hdmi input for the tv.
I am by no means an expert when it comes to the best choice of hardware.
All I can tell you is this: Nvidia has decent support for Linux and Compiz works very well with it.
The downside is: their drivers are closed source, so you depend on them if they feel the need to fix bugs or not.

I for myself have an (older) ATI card which also works well with Compiz because ATI is slowly keeping up in terms of proper Linux support. I also hear good things about their support for newer HD cards (which was poor in the past).
Their drivers are also closed, though.

I guess it depends on what you want to do with your hardware. Like I said, Nvidia seems to be the best choice for Compiz but newer ATI cards may be better in other use cases, I don't know.

(I for myself swore to never buy an ATI card again, because some years ago, when I started using Linux, their support was *very* poor :p)

---

### Post by facewithnoname54 on 2008-12-02
Well thank you for your help. I guess that I will just upgraded the card then witch means you might just see me with another post close to this one. But I my just go to ATI because, I have also heard so pretty good things about them latly

---

