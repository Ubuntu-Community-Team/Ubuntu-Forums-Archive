---
title: "HOWTO: Speed up the FGLRX drivers in Hardy..."
date: 2008-04-28
forum: Multimedia Software
---

### Post by Mazza558 on 2008-04-28
I think I've found a config which is the fastest possible combination for anyone using the fglrx drivers which are from the Restricted manager in Hardy. Some people have reported lackluster performance, and these options in the Xorg.conf file should speed things up considerably. This is actually an extension of the guide I wrote for the beta of Hardy, with some new things to try.

[B]HOWTO: Speed up your ATi Restricted drivers!

Step one - open your Xorg Configuration file[/B]

    * Enter your password

**Step two - start adding the options**

    * This is quite a mundane process, but should be worth it.
    * Scroll down the file to the "device section. This should look something like this provided you haven't already edited it:

```
Section "Device"
	Identifier	"ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
EndSection
```

    * Between the "busid" and "EndSection" (on a new line), paste these lines:

```
	Option 	     "AccelMethod" 		"EXA"
	Option 	     "MigrationHeuristic" 	"greedy"
        Option       "DRI" "true"
```

# Press "save" and close Gedit
# Next, save your work, open a new tab in Firefox and close it (choose to save your session, as then you can continue later)
# Finally, press CTRL + ALT + Backspace to log out. If you see the cursor and beige background (with no errors, these first settings worked. Log in again.
# If these didn't work, and you get an error, log in with a terminal by choosing "Options" from the login screen, then "sessions", then "failsafe terminal". Then, in the terminal, type:

```
sudo nano  /etc/X11/xorg.conf
```

Then remove these lines, press CTRL + X to save, press Y, then enter, then type "exit" to get back to your normal login. If these settings didn't work, stop here.

**Step three: More to try:**

    * These settings will gradually speed things up as you add them.
    * Add them ONE AT A TIME (except the first one) to test each one. Save the file and log out with CTRL + ALT + Backspace to test, then login and try the next one - repeat until all the options are added and work fine.
    * If one breaks your setup, just follow the steps mentioned above and try the next one.

```
        Option       "VideoOverlay" "on"
        Option       "OpenGLOverlay" "off"
```

(add these both at the same time, save the file, then CTRL + ALT + Backspace to test)

```
        Option       "TexturedVideo" "on"
```

(add just this one, save the file, then CTRL + ALT + Backspace to test)

```
        Option       "UseFastTLS" "0"
```

(add just this one, save the file, then CTRL + ALT + Backspace to test)

```
        Option       "BlockSignalsOnLock" "on"
```

(add just this one, save the file, then CTRL + ALT + Backspace to test)

```
        Option       "KernelModuleParm" "locked-userpages=0"
```

(add just this one, save the file, then CTRL + ALT + Backspace to test)

```
        Option       "ForceGenericCPU" "off"
```

(add just this one, save the file, then CTRL + ALT + Backspace to test)

```
Option "XAANoOffscreenPixmaps" "on"
```

(add just this one, save the file, then CTRL + ALT + Backspace to test)

```
Option "Textured2D" "on"
Option "TexturedXrender" "on
```

(add these ONLY if you have an ATi card newer than the mobility X1050 (so from the beginning of 2007 onwards roughly - they're experimental)

```
Option "BackingStore" "on
```

(Caches stuff which has already been rendered (e.g Firefox pages)



**Step four: Do they work?**

Try a twirl of the compiz cube, explore the interface, and decide whether these options improved things for you. Good luck!


Note: Source for some of these options are from 
[HERE (click)]("http://forum.compiz-fusion.org/showthread.php?t=6794")

---

### Post by Mazza558 on 2008-04-29
Anyone find this of any use?

---

### Post by thumper_e on 2008-04-29
Awesome 

Thanks alot for your time. 

I have Radeon 9600 and all seems a touch smoother.

Ian

---

### Post by Mr. Sunshine on 2008-04-29
Thank you! I was a bit frustrated with Hardy, but I'm happier now. Everything's much faster.

I have a Radeon HD 3650 and I'm running Hardy 64 bit with the fglrx driver from the Ubuntu repos (8-3).

I have included all of the above steps in my xorg.conf, except these two which made opening a window slower on my machine:
>         Option       "ForceGenericCPU" "off"
	Option "BackingStore" "on

I'm bookmarking this and saving the web page to my disk. If someone could sticky the thread would be great.

---

### Post by ephman on 2008-05-07
hi,

i have a dell inspiron 6000, with an ati m300 128mb video card.  i used the compiz benchmark to test after every addition.  i went from about 190 frames a second up to 239.  not that bad.  thanks a ton!  i was finding hardy very sluggish...

thanks for your bandwidth,

ephman

---

### Post by st0nedpenguin on 2008-05-07
It's worth checking out the amdpcsdb problem mentioned in the original guide too.

---

### Post by AaronMT on 2008-05-18
Thanks for the help. :)

---

### Post by Gus_T_Reer on 2008-05-21
Thanks a lot for this Mazza.

For the record I use totem-xine as opposed to totem-gstreamer (doesn't handle dvd menus) and using 
```
        Option       "VideoOverlay" "on"

```
stops the video from displaying (sound carries on tho').

Omitting this or setting it to "off" cures the problem.

Regards

GTR

---

### Post by MatthewPlanchard on 2008-08-05
Thanks for the suggestions, Mazza

Used compiz benchmark after every setting change and got about a one fps increase (note: things seem a little bit clearer and, I don't know, smoother, even though I did not note significant fps increase)

---

### Post by markbuntu on 2008-08-05
fps checks are bogus. I get 60fps when I sync to the refresh rate of my monitor but everything just screams along anyway.

Also, some of the tweaks that work with 8.3-8.6 drivers do not work with the 8.7 driver and may not work in future driver releases. The ati devs will include options in the aticonfig --help menu and eventually in Catalyst Control Center once they are stabilized. 
For example, the TexturedVideo option is now in aticonfig.

---

### Post by Melcar on 2008-08-05
A few things:

- The driver can't use EXA.  XAA is the only option available.

- VideoOverlay and TexturedVideo both do the same thing, in different ways; they basically let you use Xv for video playback acceleration.  The driver uses one or the other, so you can't force both on (the driver will just default to one of the options depending on the chip you have).  Generally, VideoOverlay is used on r4xx and earlier type cards, and TexturedVideo for r5xx and newer (usually the driver loads the options automatically).  You can force either option on or off, but depending on the card you have one may end up being slower than the other.

- You don't need to manually load DRI; it loads automatically.

---

