---
title: "Desperate for help..."
date: 2010-10-07
forum: Multimedia Software
---

### Post by ubunwhat on 2010-10-07
I have asked this question in different forums without getting help, and now I am at my wit's end.  I will state up front that I know precious little about hardware and drivers, so if you can help please make your response as simplistic as possible.  Likewise, if I am asking in the wrong place please let me know.  Here is the situation.

I installed Ubuntu on a Toshiba Satellite about a month ago.  It worked for about three hours.  I installed Wine, and it still worked but the display would sometimes go black for a few seconds.  Later that day I rebooted and that was it, no more Ubuntu.  It goes through all of the process of booting but then the screen just goes black before I even get to the purple Ubuntu screen.  I'm running this on a drive in an enclosure so I simply plugged the drive into another machine ( actually two other machines ), and it works perfectly.  I have an old Vista drive that I put in the Toshiba and that works just fine, so it's not a pure hardware issue.  Just to be sure I wiped the Ubuntu drive and re-installed, this time without installing wine.  No Toshiba love.  Just the black screen.  I even made a flash drive with the loader and iso from the Ubuntu site.  Same deal.  It starts to boot from the flash and then just goes black where you would normally expect the purple Ubuntu screen.  This thing is driving me nuts and I am at a point where I really need this machine working and will be faced with simply wiping the Ubuntu drive and installing Windows.  Any help at all would be greatly appreciated.

---

### Post by CharlesA on 2010-10-07
It sounds like it's having a problem with the resolution.

Try this:

Reboot the machine and hold down shift to get the GRUB menu, then select recovery mode.

It should prompt you to fix X or something similar.

Can't recall what it says off the top of my head, but try that and see if it'll load up.

---

### Post by P4man on 2010-10-07
Try the ubuntu stick/cd again, but hold down the shift key early in the boot process ( right after the bios) to get a menu. Bottom right (I think F6 ?) there are some additional options to play with. Try the "nomodeset" option.

If that solves it, then you probably have to add that option to your installed ubuntu bootloader, if you need help with that, Ill talk you through it IF indeed nomodeset is the cure.

---

### Post by ubunwhat on 2010-10-07
@Charles:  Nope.  I did get into GRUB and recovery mode.  It sailed through without a hitch and then went black when the purple Ubuntu screen was supposed to load.

@P4man:  I tried nomodeset ages ago.  No love at all.

---

### Post by Hakunka-Matata on 2010-10-08
@ubunwhat,  Your user handle is correct then, ubunwhat.  I'd be saying the same thing.  Just for giggles maybe try an earlier/different version?

Good Luck

---

### Post by lidex on 2010-10-08
What model is it? You may find help here:
[http://www.linlap.com/](http://www.linlap.com/)

---

### Post by CharlesA on 2010-10-08
> **ubunwhat said:**
> @Charles:  Nope.  I did get into GRUB and recovery mode.  It sailed through without a hitch and then went black when the purple Ubuntu screen was supposed to load.

@P4man:  I tried nomodeset ages ago.  No love at all.

Ugh. Does it help if you hook up an external monitor? That would try to rule out a resolution problem.

---

### Post by P4man on 2010-10-08
It used to work, then you got flickering issues and now even a livecd (stick) that previously worked doesnt work anymore? That does smell like a hardware problem. 

Now I read you booted vista fine, but did you try any hardware acceleration under windows? 

Using an external monitor as suggested above might shed some light on it too, but if its a resolution problem, you should be able to access a TTY by pressing control + alt +F1

---

### Post by CharlesA on 2010-10-08
> **P4man said:**
> 
Using an external monitor as suggested above might shed some light on it too, but if its a resolution problem, you should be able to access a TTY by pressing control + alt +F1

Indeed.

Now that you mention it, it does kinda sound like a hardware problem, but I don't know what sort of hardware problem would cause it to work in Windows, but not in Linux.

---

### Post by P4man on 2010-10-08
> **CharlesA said:**
> Indeed.

Now that you mention it, it does kinda sound like a hardware problem, but I don't know what sort of hardware problem would cause it to work in Windows, but not in Linux.

Its weird for sure, but Im guessing windows is running without aero or any 3d acceleration, whereas ubuntu will by default enable GPU acceleration on most videocards. On both ati and nvidia (not sure about intel, but probably too) it now enables desktop compositing even on the opensource drivers and in a live session. That requires the GPU to work properly.

Anyway, Im not betting any money on this being a GPU that has died, but it seems possible.

---

### Post by Rubi1200 on 2010-10-08
What graphics card is installed on the machine?

Here are some more options:
[https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

### Post by CharlesA on 2010-10-08
> **P4man said:**
> Its weird for sure, but Im guessing windows is running without aero or any 3d acceleration, whereas ubuntu will by default enable GPU acceleration on most videocards. On both ati and nvidia (not sure about intel, but probably too) it now enables desktop compositing even on the opensource drivers and in a live session. That requires the GPU to work properly.

Anyway, Im not betting any money on this being a GPU that has died, but it seems possible.

That does make sense. I've had machines choke when I've enabled desktop effects.

---

### Post by P4man on 2010-10-08
To throw in just one more idea: is this a laptop with 2 videocards ? One intergrated (usually intel) and one discrete (ATI or nvidia) ?

---

### Post by ubunwhat on 2010-10-08
It is a Toshiba Satellite P205.  The video card is an integrated Intel 945 (950) Chipset.  The card does have some issues but nothing that has prevented from working just fine in Windows doing everything from basic computing to playing videos etc.  As I said I am woefully ignorant in terms of hardware and sadly most of this has gone over my head.  TTY?  I don't have an external monitor to hook up to it aside from my television via S-Video, but that would require being inside Windows to set up.  Wouldn't the display just reset back to the LCD when I booted?  I mean, I use this all the time to watch movies etc but I have never actually tried booting while connected to my television.  

While I'm on the subject of the card itself, and restating for effect that I am not a hardware guy, I will throw this out there re: the video card.  And please understand that I am throwing this out there mainly because I think that the repair shop I took it to a while back was scamming me.  There has been on consistent issue with the display, even in Windows, for the better part of a year.  It is odd, but I will try to explain it.  Please bear with me.

In Windows, when I first turn the machine on the display is wonky if the lid is open beyond about a 50 degree angle.  By wonky I mean that all text or images have red and green lines through them.  After about five minutes of being on the display is fine, but it goes wonky again if I open the lid further.  Say I open it to 90 degrees.  That's another three or four minutes of lines and then it sorts itself out and the display is fine.  If I open it beyond that it's another few minutes.  So if I open the screen beyond 90 degrees at startup it's about fifteen minutes before the display is right.  The text and everything is still readable, it's just annoying.  I took this in expecting to be told that the data cable to the LCD needed to be replaced.  Instead I was told that the cable was fine but the chip was bad and could not be replaced, but could be repaired for $249.  This seemed a bit ridiculous to me so I didn't bother.  After all, the display issue is not that big of a deal.  HOWEVER.... I did notice that when I had Ubuntu running on it after the first install that this problem disappeared.  I could start Ubuntu cold and the colors were fine.

I have tried to research this as much as I can but there is precious little out there.  One thing that did catch my attention was an article on Fedora where the writer spoke about how installing third party video drivers could screw up displays in Fedora even if the driver was not being used.  That simply having the driver on the machine could jack up Fedora, but out of the box Fedora supported the Intel 950 chipset.  This, of course, made me curious as to whether Fedora would work on the Toshiba.  I made not one, not two, but three different Fedora sticks using the iso and creator from Fedora's site.  None of them would even boot.  I just kept getting a message saying that there was no OS on the drive I was trying to boot.  I don't really want to go the Fedora route even if it could work because all of the tarballs and everything are such a headache, as opposed to the ease of installing and configuring software in Ubuntu.  

So, having said all of that, what do you think?  Try booting while connected to the tv?  Or is this a situation where I need an old priest, a young priest, and a few gallons of holy water?

---

### Post by ubunwhat on 2010-10-08
> **CharlesA said:**
> That does make sense. I've had machines choke when I've enabled desktop effects.

During the time that Ubuntu was running on that machine I had enable desktop effects and they were working fine.  It didn't choke on the desktop effects.

---

### Post by ubunwhat on 2010-10-08
> **P4man said:**
> To throw in just one more idea: is this a laptop with 2 videocards ? One intergrated (usually intel) and one discrete (ATI or nvidia) ?

Oh, if only there were some way to bypass the integrated card.  I am told, however, that this is not possible.

---

### Post by lidex on 2010-10-08
Have you made an attempt to access your log files? I'm thinking ```
/var/log/Xorg.0.log
```would be informative, as well as dmesg

---

### Post by P4man on 2010-10-09
> **ubunwhat said:**
> 
In Windows, when I first turn the machine on the display is wonky if the lid is open beyond about a 50 degree angle.  By wonky I mean that all text or images have red and green lines through them.  After about five minutes of being on the display is fine, but it goes wonky again if I open the lid further.  Say I open it to 90 degrees.  That's another three or four minutes of lines and then it sorts itself out and the display is fine.  If I open it beyond that it's another few minutes.  So if I open the screen beyond 90 degrees at startup it's about fifteen minutes before the display is right.  The text and everything is still readable, it's just annoying.  I took this in expecting to be told that the data cable to the LCD needed to be replaced.  Instead I was told that the cable was fine but the chip was bad and could not be replaced, but could be repaired for $249.  This seemed a bit ridiculous to me so I didn't bother.  After all, the display issue is not that big of a deal.  HOWEVER.... I did notice that when I had Ubuntu running on it after the first install that this problem disappeared.  I could start Ubuntu cold and the colors were fine.

Thats bizare. I dont see much relation between the lid angle and "temperature" but for sure you are having a serious hardware issue. Maybe its the display controller, maybe the video controller, maybe the cable, but something isnt working right and it looks like heat will cause something to expand and make it work again. Sometimes, if you are lucky.

If you connect an external monitor (possibly a TV), then it would help to see if the problem is either the LCD monitor, cable, display controller... or the GPU. But whatever it is:

> Or is this a situation where I need an old priest, a young priest, and a few gallons of holy water?

Something like that. Ritually slaughtering a chicken and offering coca cola works too, at least they told me in Guatemala. In Mexico they assured me it had be pepsi cola.

---

### Post by CharlesA on 2010-10-09
I've seen cases where the "cable" that is connecting the LCD to the mobo gets frayed or loose and if you tilt the screen too far in one direction, it doesn't make a good connection.

I'd really suggest getting it looked at if it's under warranty.

---

