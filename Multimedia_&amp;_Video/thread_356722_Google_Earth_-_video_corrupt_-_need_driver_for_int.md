---
title: "Google Earth - video corrupt - need driver for intel 82865g?"
date: 2007-02-08
forum: Multimedia &amp; Video
---

### Post by tripecac on 2007-02-08
I recently built a nice Ubuntu PC for my girlfriend.  It's a Pentium D 2.8GHz, 1 GB ram, running Dapper (6.0.6).  It's been running fine for basic stuff (firefox, openoffice, mp3 players), but **Google Earth** has horrible redrawing problems:

- failure to erase portions of the map (e.g., yellow country lines)
- updates occur in small rectangular portions of the screen (rather than whole screen)
- the "compass" in the upper right is completely blurred/corrupt

This PC is still using onboard video (intel 82865g).  I haven't manually installed any video drivers yet, mostly because I haven't found an "idiot proof" binary yet.

So I'm wondering if the problem is:

a) google earth (bad coding)
b) [lack of] video driver
c) intel video hw/sw - not as well supported as nvidia and ati
d) onboard video - not as well supported as video card
e) ubuntu/linux - not as smooth at video as XP

After reading a lot about google earth + ubuntu, I see that many other people are [apparently] having similar graphics problems.  "install a new driver" seems to be the default action item for them.

I'm not sure how to do this for the intel 82865g on Ubuntu, though.  I'm wary of messing with compilers and the kernel, and would much rather click on a couple buttons in Synaptic, or at least run a binary from the command line, as long as I feel I can safely roll back.

Suggestions?

Thanks!

Travis

---

### Post by tripecac on 2007-02-09
I installed Google Earth on another Ubuntu 6.06 desktop.  This second machine is much older and weaker (1.7 GHz Pentium 4, Geforce2 MX 400 graphics card).  It runs google earth very slowly (which can be expected) but with **no graphical glitches**.

This rules out Ubuntu (and linux) as being the sole cause of the graphical glitches.

This leaves:

b) [lack of] video driver
c) intel video hw/sw - not as well supported as nvidia and ati
d) onboard video - not as well supported as video card

Any suggestions on how I can get Google Earth running smoothly on the fast PC?

---

### Post by CoMRaDe_X on 2007-02-10
my ati mobile card does not even get to the program
it hangs on the splash screen
and i believe this is the same with everyone else using flgrx/ati
btw im using edgy

---

### Post by thejart on 2007-02-12
intel has a linux driver on their website for the 82865g.

[http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1044&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1044&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

i haven't installed it yet (i'm a little nervous to do so, i just got everything working like i want it).  i'm in the same boat as you, though...i just installed google earth and the image refresh is awful.

let me know your results if you decide to install.  i've got a few other projects going on right now and i can't really afford to have my entire system down if the driver effs everything up (ie. i'm not savy enough yet to just revert back to the default drivers).

---

### Post by tripecac on 2007-02-13
Ah, my thoughts exactly...  Wait until someone else tries it. :)  Kinda of like that recent auto-update where the proactive "early adopters" had their systems messed up, and the rest of us "wait-and-seers" were all okay. :)

I have no idea how to revert drivers either.  I'm also wondering if maybe our onboard intel cards (not really cards, but you know what I mean) will always be problematic compared to a "real" video card like a cheap nvidia. 

Out of curiosity, when did you get into linux/ubuntu?

---

### Post by thejart on 2007-02-13
i installed kubuntu in december.  i've been messing around with linux/unix off and on for about 10 years, but this is the first time i've really immersed myself in it.  there's a lot of system admin stuff that i had never even touched.  i decided that with the release of vista, though, i'd give m$ the finger :) how 'bout you?

you're right, our intel "cards" are going to be significantly inferior no matter what drivers we install.  it leaves me little incentive to even try it...plus i've got an old 3d accelerator card somewhere, i just need to figure out if it's compatible/up-to-spec.

---

### Post by tripecac on 2007-02-13
Same here.  I have an old Geforce Ti 4200 which I'm thinking about installing.  I have no idea how that measures up to the (modern but onboard) Intel graphics but it seems easier to rollback from a hardware install than a driver install.  I guess.  Linux drivers (and windows drivers for that matter) are a bit of a mystery to me.

Ditto in terms of linux/unix background - been using it off and on for a decade or so but never got around to using a linux desktop on a daily basis until last year.  Ubuntu is far more "idiot proof" than slackware (which I tried before) but I wish it were even easier.  Heck, I wish we never even had to think about drivers.  They should "just work".  Hopefully someday, drivers will go the way of autoexec.bat and config.sys and low-level TCP/IP settings (which are are still there, but we never have to think about them).

Which old video card are you contemplating trying?

---

### Post by thejart on 2007-02-15
sorry it took me so long to get back to you...i've been tacklin' a cron issue for the past couple of days.

i'm not exactly sure what the video card is.  it's in another machine that i'm not using right now.  i think it's an old ati rage or radeon something.  i also have an old voodoo3 somewhere too...hell, it's probably a pci card :)

i did a little research on our intel cards, though, and they're supposed to be sufficient.  in addition to getting google earth to run i would like to run a 3d desktop.  it looks like intel is most compatible with the aiglx server.

anyway, on to do a little more research and job-hunting.

---

### Post by thejart on 2007-02-15
i have a status update for you.  i got the direct rendering working!  i had to make some changes to my /etc/X11/xorg.conf file.  frankly, i've made so many changes that i'm not exactly sure what fixed it, but b/c i didn't install anything new it was easy to revert when things didn't work.  anyway, i basically followed the steps laid out on the [composite manager page]("https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy").  but i did it like this:

(section "module")
```
Load "dri"
#Load "dbe"
Load "glx"  # although this was already in mine
```

(section "device" your video card)
```
Option  "XAANoOffscreenPixmaps" "true"
```

(at the very bottom)
```
Section "DRI"
        Mode 0666
EndSection
        
#Section "Extensions"
#       Option "Composite" "Enable"
#EndSection

#Section "ServerLayout"
#        Option         "AIGLX" "true"
#EndSection
```

and google earth works!  now i'm trying to install compiz.

---

### Post by tripecac on 2007-02-15
Interesting...

The only only line that you mentioned which is different from my xorg.conf is this one:

**Option  "XAANoOffscreenPixmaps" "true"**

I added it to my video card's section, then rebooted.

Google Earth is still weird; it still redraws portions of its screen rather than the entire screen.

What else did you change?  What was the behavior you were getting before?

---

### Post by thejart on 2007-02-16
okay, update to the update.  i actually got all of the edits from [the guide]("https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy") to work.  one important thing that it doesn't tell you, though is that **you need to comment out the Load "GLcore" in the Module section**.  in my last post i said that i was going to install compiz, well i changed that to beryl and the GLcore was conflicting with the card (i guess).  anyway, here's my xorg.conf (just the relevant section for your perusal:

```
...

Section "Module"
  Load "i2c"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "type1"
  Load "vbe"
  #  Load "GLcore"
  load "glx"
  load "GLcore"
  load "v4l"
EndSection

...

Section "Device"
  identifier "Intel Corporation 82865G Integrated Graphics Controller"
  boardname "i810"
  busid "PCI:0:2:0"
  driver "i810"
  screen 0
EndSection

...

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "Default Screen" 0 0
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
  option "AIGLX" "true"
EndSection

Section "ServerFlags"
EndSection

Section "DRI"
  Mode 0666
EndSection

Section "Extensions"
  option "Composite" "Enable"
EndSection

```

i just realized after pasting it, that you're right, i don't have **Option  "XAANoOffscreenPixmaps" "true"**.  the weird thing is that everything works, and that i know i added it at some point, but i must've deleted it.  hmmm...

---

### Post by tripecac on 2007-02-17
I installed my old Geforce 4200 Ti, and now google earth works nicely!  

I had to reconfigure xorg.conf and install nvidia drivers, but that only took about 10 minutes.

NOTE: Without nvidia drivers, google earth was running in software emulation mode.  It looked okay, but was slow.  The nvidia drivers pepped things up.

So, I'm guessing it's the onboard Intel video card that is causing problems w/ google earth.

Try scrounging up an old nvidia card.  I've seen 'em for as low as $30.  IMO that's a much "cheaper" solution than spending hours trying to get the onboard video card to work.

---

### Post by petersen_t1 on 2007-02-17
Hey guys, glad you got your copy of Google Earth running. I've been having the same problems and I have a bone stock Dell Dimension B110. It has an intel card in it. Fortunately (or rather, unfortunately), I still have windows on this computer (the hard drive is split right in two) so I can run Google Earth in windows when I need to.

I'm running dapper and everything (other then Google Earth) is working very nicely, so I'm going to leave things alone as they are. I'm a little nervous about updating to Edgy, from what others have said, so I think I'm going to skip Edgy for now and just wait for the next version of ubuntu (and see what people have to say about it before upgrading!).

It seems like that link you posted about configuring AIGLX is for Edgy only, but I guess I could backup my xorg.conf file and give it a shot. Worth a shot and if anything goes wrong I can just backup to the old xorg.conf (which I know works)!

Thanks for the comments, they have been enlightening. I love ubuntu and once I get Google Earth running on it, I'll get rid of windows!! :)

---

### Post by tripecac on 2007-02-19
thejart - it looks like you have GLCore uncommented:

```
Section "Module"
  Load "i2c"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "type1"
  Load "vbe"
  #  Load "GLcore"
  load "glx"
  load "GLcore"   <-- this one is uncommented
  load "v4l"
EndSection
```

---

### Post by thejart on 2007-02-19
the last few days have been interesting :) i got everything working, which is where i was in my last post, including running beryl.  then i rebooted on saturday morning and got the white cube of death.  for some reason, after i configured my xorg.conf file to turn on aiglx, and get my intel decoder working, it got reconfigured somehow.  this is what my xorg.conf looks like now:

<CODE>Section "Module"
  Load "i2c"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "type1"
  Load "vbe"
  load "glx"
#  load "GLcore"
  load "v4l"
  load "dri"
  load "dbe"
EndSection

...

Section "Device"
  identifier "Intel Corporation 82865G Integrated Graphics Controller"
  boardname "i810"
  busid "PCI:0:2:0"
  driver "i810"
  screen 0
  Option "XAANoOffscreenPixmaps"
EndSection

...

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "Default Screen" 0 0
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
  option "AIGLX" "true"
EndSection

Section "ServerFlags"
EndSection

Section "DRI"
  Mode 0666
EndSection

Section "Extensions"
  option "Composite" "Enable"
EndSection
</CODE>

it seems like the Load "GLcore" statement enables the software emulation, or at least conflicts with my card in some way.  regardless, things are back to normal now and google earth works well, too.  

i would like to get a better video card, though, so thanks for the suggestion.  it's nice to know what already works.

---

