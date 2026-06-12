---
title: "Live CD trouble: Dell LX733R"
date: 2006-10-03
forum: Multimedia &amp; Video
---

### Post by William Dojinn on 2006-10-03
As the title suggests I'd burned a live CD of the latest version of x86 Ubuntu in hopes of testing it on my old Dell to get familliar with how thigns work before doing any actual hunting on new systems(as opposed to simply poking around randomly as was the case in a thread elsewhere here). 

Long and short, the install hangs on the normal installation, tried again with 'safe' graphics mode, it boots up, but reports x11 doesn't work.

Running a Dell LX733R an nvidia vanta/vantant card, and I have 256MB system ram.

Note I could very well be off on the exact modle, but its a 733mhhat was new in '99-2000.

Anything else I should list?

---

### Post by maniacmusician on 2006-10-03
it's kind of odd that it doesnt work. have you tried the alternate install cd, or is live cd a must for you?

does the live cd hang on the installation (ie, do you actually click "install" and then it hands, or does it never even boot up in a graphical environment?) if the latter, then i guess your card isnt supported out of the box. 

some more questions: are you sure you burned it right? at a really slow speed? did you check the md5 sum to make sure your disk wasnt corrupted? a tutorial on how to download and burn [here]("http://www.psychocats.net/ubuntu/iso"). theres some other really good tutorials on that site. ([http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)) pretty much everything about installation you need to know, and then some.

If it turns out your md5 is fine and not corrupted, then i would suggest the alternate CD. it will at least do an install and get you to a workable environment.

let me know if you need anything else (feel free to pm me, i dont frequent these parts of the forum often)

---

### Post by William Dojinn on 2006-10-03
Considering that the CD got through the entire startup process and only bricked on starting x11, along with the error messge to the effect that it couldn't recognize my video card I would find it fairly safe to assume that mine is a card that isn't immidiatly recognizable(why doesn't Ubuntu simply go to a generic configuration then like windows does?). 

Going to try a few thingsl isted in that install FAQ that you linked me to. If that doens't work....I'll be back, hopefully with a more detailed account of the problem at hand.

---

### Post by William Dojinn on 2006-10-03
Hm, after a bit of tinkering in the console i've come to the overriding conclusion that unless the nvidia legacy drivers are included on the CD yet not loaded by default I'm up a creek when it comes to the target system.

Other than the minor inconveniance of not knowing how to set Xorg up(uhm....what's the kilobyte equivilant of sixteen megabytes?) I'd say the CD itself works well, except i haven't been able to actually test any of it as I'm very unfamilliar with pure console work.

---

### Post by maniacmusician on 2006-10-04
so...it boots you to a live console? weird.

the "safe graphics mode" but is supposed to be a generic configuration, I think. 

just to see, in the live console, type:
```
sudo nano /etc/X11/xorg.conf
``` dont forget the capital X. if it tells you that theres no such command, do
```
sudo aptitude install nano
```

if it asks you for a password (i dont think it does on the live cd), i think the password is just ubuntu.
Once you have xorg.conf opened up in the text editor (nano), scroll down to where it says  something along the lines of 

```
Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon Xpress 200 (RC410)"
        Driver      "radeon"
        Option      "AccelMethod" "EXA"
        Option      "RenderAccel" "true"
        BusID       "PCI:1:5:0"
EndSection

```

obviously your identifier will be different, for your card. But where it says Driver, replace whatever option is there with "vesa". vesa is the generic driver. then press CTRL + X to exit, and when it asks  you to save, say yes, and hit enter again for the location. then press either press CTRL + Backspace to restart Xorg (dunno if that works from the console) or just type "startx" to start Xorg. hopefully, the generic driver will work for you.

---

### Post by William Dojinn on 2006-10-04
A few points of interest here. Firstly, and this is quite possibly where things get real headscratchy, unless I try reconfiguring xorg through "dpkg-reconfigure xserver-xorg" the xorg config file is completely blank, meaning the install isn't apparently even attempting at a cinfiguration.

Secondly I get the following error message(well there IS more, but this is all I could get written down).
```

Fatal Server Error:
X10: Fatal IO Error(connection reset by peer) on X server: 0:0

```

Thirdly I believe tht the default given for my graphics card location isn't accurate, however I don't quite know how to translate what lspci gives me into something that is recognized as a valid location
```
 0000:01:0A.0
```
followed by a group of hex code before going down to lsit the next driver down.

Finally in KB what does 16MB translate to? 16884?

---

### Post by William Dojinn on 2006-10-05
*bump*

Could really really use a hand on this one.

by the way, is midnight command or some simmiler app on the CD?

---

### Post by maniacmusician on 2006-10-05
so when you do "dpkg-reconfigure xserver-xorg", the xorg file fills with information? could you copy and paste the contents of your xorg.conf?

if you have a usb drive, the best thing to do is plug it in, and then type in the terminal

```

sudo cp /etc/X11/xorg.conf /media/sda1

```

make sure you capitalize the X in X11,

---

### Post by William Dojinn on 2006-10-05
Best I've got is a USB cd burner. 

About to just give up till I get a replacement system. I know the nature of the problem, I know it SHOULD be easy to fix, I just don't know that one piece of infromation that'll fix it, and without a network connection it makesi t that much harder for anyone ELSE to get that infromation.

Any way the configuration files could be saved to windows then retrieved after booting back there?

---

### Post by maniacmusician on 2006-10-05
not a safe way, no. If you're willing to peruse through the conf file it's still fixable. like i said in one of my posts above, there is a Device section (see above for exact details) that points out your card and which driver is currently loaded. so why dont you copy down the details of that and show them here? or replace whatever driver is there with the generic driver "vesa"

---

