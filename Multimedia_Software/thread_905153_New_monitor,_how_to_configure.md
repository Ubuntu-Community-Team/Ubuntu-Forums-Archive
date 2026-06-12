---
title: "New monitor, how to configure?"
date: 2008-08-30
forum: Multimedia Software
---

### Post by drubdrub on 2008-08-30
This is embarassing(ly simple?)

I bought a new monitor.  Isn't there a utility to auto-sense the monitor model, etc, and generate the new parameters for the /etc/X11/xorg.conf?

Old: 21" Compaq CRT
New: 24" Sceptre LCD

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)

Attempting to configure 1900 x 1280

Many thanks!


<** I've been looking through "sticky"s, "howto"s, and performing searches for about 30 min.  Learned several new things, but not how to configure the new monitor.

Apologies.  I hate to miss the obvious and bet this has been covered more than once. 

Once I figure it out, I'll try to write the doc, if needed.**>

---

### Post by RequinB4 on 2008-08-30
What exactly is the issue with the moniter when you plug it into the box?

As of hardy, "xorg.conf" isn't *as* useful because x autodetects the moniter.

If you're just trying to configure a higher resolution --

1) Make sure your new moniter's native resolution isn't too low (a quick google can do this) for you to have very high res.

2) Make sure your video card drivers are up to date.  If you have a serious (800x600 etc) decline in resolution that might be a problem.

---

### Post by drubdrub on 2008-08-30
Thanks, RequinB4

Sorry.  Guess I wasn't very complete with the description ...

The problem is the system did not seem to autodetect the new monitor.  The /etc/X11/xorg.conf still shows the (old) Compaq monitor.  Fortunately, there was a compatible mode, so the new panel is functional, at 1600x1200.  Of course, I want to configure it at 1900x1280.

I could pretty easily add a "ModeLine" entry but would like to get the monitor properly configured on the system so all options and appropriate modes can be used.

BTW, I tried using nvidia-xconfig, which generated a new xorg.conf, but the same Compaq monitor remains.  Here's an abbreviated listing of the "Monitor" section of the xorg.conf.

Hope this better frames the problem.

Sure appreciate the attention and suggestions!  Cheers

-----------------------------------

The 
Section "Monitor"
    Identifier     "Compaq"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync

... stuff deleted ...

    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync

EndSection

---

### Post by RequinB4 on 2008-08-30
Are you using the old moniter to re-configure xorg?  since it autodetects you need to have the new one plugged in.

Failing that, Because of what I said earlier, this shouldn't be necessary, but it might be what you need for some reason:

First, plug in your new moniter and not the old one:

either do this or boot into recovery mode (text install):
```

/etc/init.d/gdm stop
[code]

and then (write this down and then execute)

[code]
dpkg-reconfigure xserver-xorg

```

It should give you a few prompts - if you don't know just press enter (even with it blank), but there are instructions.

Post back here whether that works or not :)

Edit; failing that, the surefire way of doing the moniter is manually as you say via Modeline, but let's leave that as a last resort :P

---

### Post by drubdrub on 2008-08-31
Grumble, grumble, grumble ....

<ctl> <alt> <fN> doesn't bring up console windows.  Now working from a putty session on an XP box.  Any thoughts on why the multi-console doesn't work?  I thought it was configured by default.  :confused:  Good thing I configured sshd.

```

dpkg-reconfigure xserver-xorg

```

Yields
```

Package `xserver-org' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-org is not installed

```

Thanks again

---

### Post by RequinB4 on 2008-08-31
> **drubdrub said:**
> 
```

Package `xserver-org' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-org is not installed

```


Don't you mean xserver-xorg? Maybe a typo?

edit: try:

```
sudo displayconfig-gtk
```

---

### Post by drubdrub on 2008-09-01
Just realized I didn't answer one of your questions.  The new monitor is in use, even as I type this.  It works at 1600 x 1200, which is one of the modeline entries under the Identifier "Compaq".  Images are a bit skewed, as you might expect, but perfectly usable.

Doh!  Yup, a typo.  Too close to the problem .... fat fingers ... whatever ...

When running 
```

dpkg-reconfigure xserver-xorg

```
the monitor was not autodetected and was not available to choose manually from the menu.  So, that wasn't very useful, unfortunately.

Since the reconfigure attempt bombed, I tried adding a modeline for 1920 x 1200.  Cloned the apparently functioning line for 1600 x 1200 and chaged the "1600" to "1920".  Restarted gdm.  Use System -> Preferences -> Screen Resolution. The new value, 1920 x 1200 is not listed in the menu.  xorg.conf now looks like:

```

<snip>
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1920x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  Gamma   1.0
EndSection
<snip>

```

I suspect I'm missing something.  The "Screen Resolution" utility shows the current screen configuration at 16000 x 1200 and at a 50 Hz Refresh Rate.  That combination is not listed in xorg.conf.  As can be seen, the entries at that resolution are configured for 65 and 60 Hz.  Confusing ...

RequinB4, sincere thanks for all the coaching!  Very, very helpful in working through the issues.

---

### Post by RequinB4 on 2008-09-01
> Just realized I didn't answer one of your questions. The new monitor is in use, even as I type this. It works at 1600 x 1200, which is one of the modeline entries under the Identifier "Compaq". Images are a bit skewed, as you might expect, but perfectly usable.

Ok, That helps xD From now on do everything with the new moniter

Can you post your entire xorg.conf at pastebin.ubuntu.com? and give me the link?  This might be as simple as you didn't recognize another moniter section for the new moniter...

Also, as i said in the first post, make sure you have the most up-to-date drivers for your card!!! - You could have the best moniter in the world but your card has to support the res and refresh rate...

This is taking longer than it should mostly because of a misunderstanding of what the problem was :(

---

### Post by drubdrub on 2008-09-01
Apologies for the mis-communication. :oops:  The Sceptre has been in use though our entire conversation.  The Compaq CRT failed completely, necessitating the purchase of the new monitor.

There is a "monitor1" section and I inferred that is intended for the Sceptre since the Sceptre name was not identified in the dpkg-reconfigure list.

Posted xorg.conf.  [http://pastebin.ubuntu.com/42459/](http://pastebin.ubuntu.com/42459/)
My edits include commenting out lines 193, 194, 197, and adding 198.

I have relied on the system's notification of new SW.  Assume Synaptic is responsible for those notifications.  Just ran "apt-get update".  That should be sufficient to assure the latest driver version?  Anything else required to assure the latest driver?

Perhaps 4 months ago the GeForce 7300 was added to the configuration.

Just realize my first post said > Attempting to configure 1900 x 1280.  Wrong.  Should have said "1920 x 1200".  [X24WG-1080p]("http://www.sceptre.com/Products/LCD/Specifications/spec_X24wg-1080p.htm")

---

### Post by RequinB4 on 2008-09-01
First thing to try, you need to add the new modeline name you put above into line 132

To restate, add "1900x1200@60" to the Modes line in this section:

> Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV44 [GeForce 6200 TurboCache]"
        Monitor         "Compaq"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1792    1344
                Modes           "1600x1200@60"  "1792x1344@60"  "1600x1200@65"  "1400x1050@75"  "1400x1050@60"  "1280x960@75"   "1280x1024@60"  "1280x960@60"   "1280x1024@75"  "1152x864@75"   "1024x768@43"   "1024x768@60"   "1024x768@70"   "1024x768@75"   "1024x768@85"   "832x624@75"    "800x600@60"    "800x600@85"    "800x600@75"    "800x600@72"    "800x600@56"    "640x480@85"    "640x480@75"    "640x480@72"    "640x480@60"
        EndSubSection
EndSection


Then reboot, try to increase your resolution, w/e (I'm not pretending I expect this to work, but why not check)

Now, go to line 127 and replace "Compaq" with "monitor1" in the section above.

Now reboot and try to increase your resolution and cross your fingers ;)

---

### Post by drubdrub on 2008-09-01
Hmmmm.  I thought about that possibility, but ruled it out since that Section associates the Compaq monitor to the GeForce 6400.  The GeForce 7300 should be associated with the Sceptre, me thinks, cuz that'w where it's physically attached!  8-)

Worth a try.  Back soon ....

---

### Post by drubdrub on 2008-09-01
1. Added the "1920x1200@60" and changed "Compaq" to "monitor1".  Restart
gdm.  Tried to change resolution.  The new option was not on the list.  Remove those changes.

2. Added the "1920x1200@60" to line 165.  Restart gdm. Tried to change resolution.  The new option was not on the list.  Removed those changes.
    
When I created the modeline entries on lines n and n, I simply copied the
"1600x1200@60" entries and only changed "1600" to "1920".  Are other
changes on those lines required?

The damned thing seems to pretty effectively ignore my efforts!  ;-)

Blech

To be sure we're still on the same page, reposting xorg.conf.  [http://pastebin.ubuntu.com/42552/](http://pastebin.ubuntu.com/42552/)

Thanks again

---

