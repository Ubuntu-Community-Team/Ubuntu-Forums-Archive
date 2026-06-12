---
title: "genius mousepen tablet i608 pen does not draw"
date: 2011-12-23
forum: Multimedia Software
---

### Post by SmithWillSuffice on 2011-12-23
PROBLEM:
The Genius i608X tablet is found and the pen functions as a cursor mover, but neither pressure nor the button on the pen (which I believe should simulate a left mouse click) work.  So in Inkscape, gimp, Krita, Xournal, none of these allow me to draw with the pen.  I can draw by holding down my left mouse button or touchpad left button and then move the tablet pen, but needless to say this is painful and requires great coordination between left and right hands to draw anything half artistic!

Previous help threads like [http://ubuntuforums.org/showthread.php?t=1582286&highlight=i608]("http://ubuntuforums.org/showthread.php?t=1582286&highlight=i608") indicate the Genus mousepen graphic tablet should work in prior ubuntu releases.

Trouble is I've updated to ubuntut 11.10 oneuiric and the xorg configuraiton is all new.  For a start there is no longer any /etx/X11/xorg.conf file, all X settings seem to be distributed.  So installing the wizardpen driver package gives me a config file 

/usr/share/X11/xorg.conf.d/70-wizardpen.conf

which looks like this:
```
Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event*"
   MatchTag "WALTOP|Tablet"
   Driver "wizardpen"
   Option               "TopX"          "1506"
   Option               "TopY"          "2705"
   Option               "BottomX"       "31225"
   Option               "BottomY"       "30892"
EndSection
```

I have tried other confs like 
```
 MatchTag "wizardpen"
```
and
```
MatchDevicePath "/dev/input/by-id/usb-Genius_MousePen_i608X-event-mouse"
```

but none of these permutations would work to yield a functioning drawing penmouse.


Can any xorg configuraiton guru's help, or is this a case of waiting for a new wizardpen driver for the 11.10 release?

---

### Post by Favux on 2011-12-23
Hi SmithWillSuffice,

Welcome to Ubunut forums!

Please post the outputs of *lsusb* and *xinput list* in a terminal.

Did you find a WizardPen driver to install in Oneiric?  I don't think there is a xserver-xorg-input-wizardpen in the Oneiric repositories.  Where did you find it and how did you do it?

---

### Post by SmithWillSuffice on 2011-12-24
Thansk for replying Favux.

lsusb:
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:09a2 Logitech, Inc. QuickCam Communicate Deluxe/S7500
Bus 001 Device 004: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 001 Device 006: ID 15a9:0004 Gemtek WUBR177G
Bus 002 Device 002: ID 1241:1177 Belkin F8E842-DL Mouse
Bus 002 Device 003: ID 0458:5011 KYE Systems Corp. (Mouse Systems) 

```
seems a bit weird huh?  Where's the tablet?

So, `xinput --list`:
```

&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; HID 1241:1177                             id=8    [slave  pointer  (2)]
&#9116;   &#8627; Genius MousePen i608X                     id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard ...etc
```
seems ok right?

You're right, oneiric (11.10) has no "xserver-xorg-input-wizardpen" deb package.  I added the natty repo to my /etc/apt/sources.list (deb [http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu](http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu) natty main ).  I horrible thing to do I know, but what other option do I have?

For this reason I am not surprised the Genius graphic tablet does not function.  But I enjoy trying to find a solution, so willing to persist.  At worst I don't mind waiting for an oneiric package to appear.

I also tried using alien to install the rpm package: x11-input-wizardpen-0.8.1-6.1.x86_64.rpm
But this had no advantage, the tablet pen still worked to move the cursor around but would not draw, i.e., would not emulate left mouse button stuff correctly.

PS. Tested on WinXP VM worked fine.

I am open to some hacking.  I've written python wrappers using C classes for ieee-488 to USB devices before, but I'm not an expert programmer, just a scientist with motive :-)

---

### Post by Favux on 2011-12-24
Alright.  This is your tablet:
```
Bus 002 Device 003: ID 0458:5011 KYE Systems Corp. (Mouse Systems)
```
And the X server sees it as:
```
&#9116;   &#8627; Genius MousePen i608X                     id=9    [slave  pointer  (2)]

```
> I added the natty repo to my /etc/apt/sources.list (deb [http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu](http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu) natty main ). I horrible thing to do I know, but what other option do I have?
You're right, it is a long shot that will work, but maybe.  So what we need to do is find out if the problem is the match in the 70-wizardpen.conf.  So look in /usr/share/X11/xorg.conf.d and see if you have a wizardpen.conf and post the contents.  If not we need to add one.  Probably right now the tablet is on the evdev driver.  To find out enter:
```
xinput list-props "Genius MousePen i608X"
```
and post the results.

For a UC-LOGIC i608 I think we had to change from MatchVendor to MatchProduct to get a match:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
#    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
# remove comment below if you have Genius MousePen i608
    MatchProduct "UC-LOGIC"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
#    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
# remove comment below if you have Genius MousePen i608
    MatchProduct "UC-LOGIC"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```
So in your case it would be:
```
    MatchProduct "UC-LOGIC|KYE Systems"
```
I didn't add the coordinates because I don't know where you got them and if they are specific for your tablet.

I think from some remarks Peter Hutterer made that what is going on is that tablets like the WizardPens and Aipteks are now expected to work on the evdev driver.  They just forgot to tell us that.  :)  In which case we need to create a new .conf to do that.  Here are a couple of threads where we start making the attempt to do that:
[http://ubuntuforums.org/showthread.php?t=1889294](http://ubuntuforums.org/showthread.php?t=1889294)
[http://ubuntuforums.org/showthread.php?t=1886167](http://ubuntuforums.org/showthread.php?t=1886167)
There are some commands in those threads on diagnosing the situation; finding what driver is being used etc.  As you can see user modified .conf files are technically suppose to go in /etc/X11/xorg.conf.d because /usr/share/X11/xorg.conf.d is for the Distributions.

---

### Post by Favux on 2011-12-24
Oh, and I should put more emphasis on the fact that there is a bit of a discordance between lsusb and xinput.  From *xinput list* we're seeing the keywords as:
```
Genius, MousePen, i608X
```
So maybe instead of using KYE or whatever for the match perhaps i608X etc., is a better choice.

---

### Post by SmithWillSuffice on 2011-12-25
`xinput list-props "Genius MousePen i608X"`
```
Device 'Genius MousePen i608X':
        Device Enabled (117):   1
        Coordinate Transformation Matrix (119): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (235):     0
        Device Accel Constant Deceleration (236):       1.000000
        Device Accel Adaptive Deceleration (237):       1.000000
        Device Accel Velocity Scaling (238):    10.000000
        Evdev Axis Inversion (239):     0, 0
        Evdev Axis Calibration (240):   <no items>
        Evdev Axes Swap (241):  0
        Axis Labels (242):      "Abs X" (258), "Abs Y" (259), "Abs Z" (260), "Abs Rotary X" (261), "Abs Rotary Y" (262), "Abs Rotary Z" (263), "Abs Pressure" (264), "None" (0)
        Button Labels (243):    "Button Left" (120), "Button Middle" (121), "Button Right" (122), "Button Wheel Up" (123), "Button Wheel Down" (124), "Button Horiz Wheel Left" (125), "Button Horiz Wheel Right" (126), "Button Side" (255), "Button Extra" (256), "Button Forward" (257), "Button Unknown" (234), "Button Unknown" (234), "Button Unknown" (234), "Button Unknown" (234)
        Evdev Middle Button Emulation (244):    0
        Evdev Middle Button Timeout (245):      50
        Evdev Wheel Emulation (246):    0
        Evdev Wheel Emulation Axes (247):       0, 0, 4, 5
        Evdev Wheel Emulation Inertia (248):    10
        Evdev Wheel Emulation Timeout (249):    200
        Evdev Wheel Emulation Button (250):     4
        Evdev Drag Lock Buttons (251):  0

```
It'll take me a while to figure this out and start using those threads you gave, but thanks heaps for this start.

It looks like the evdev driver is the one being used.  I'm not sure how to force a switch to the wizardpen, but I'll try going with the solution using "/etc/X11/xorg.conf.d/52-wizardpen-on-evdev.conf"

PS. I'm dealing with Christmas and family interruptions, so please bear with me.  Hopefully if I can get this Tablet working it should benefit others.

---

### Post by SmithWillSuffice on 2011-12-25
So with the recommended vanilla,
"/etc/X11/xorg.conf.d/52-wizardpen-on-evdev.conf"
```
Section "InputClass"
        Identifier "wizardpen-on-evdev class"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "TopZ" "10"
        Option "BottomZ" "1023"
EndSection
```
I now get,
`xinput list-props 9`
```
Device 'Genius MousePen i608X':
        Device Enabled (117):   1
        Coordinate Transformation Matrix (119): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (235):     0
        Device Accel Constant Deceleration (236):       1.000000
        Device Accel Adaptive Deceleration (237):       1.000000
        Device Accel Velocity Scaling (238):    10.000000

```
and for,
`xinput query-state 9`
```
2 classes :
ButtonClass
        button[1]=up
        button[2]=up
        button[3]=up
        button[4]=up
        button[5]=up
        button[6]=up
ValuatorClass Mode=Absolute Proximity=In
        valuator[0]=8715
        valuator[1]=5459
        valuator[2]=0
```
the "valuator[2]=0" doesn't look good to me, but I'm not clear on interpreting this info or how to adjust settings to get z positioning working.  Indeed with `xinput test 9` in effect I see the a[0] and a[1] values change as I wander the pen around the tablet corresponding to x, y movements, but a[2]=0 is stuck on zero.

One thing improves, the tablet pen button works as a middle and right mouse click.  But there is still no pressure, and no left mouse click functionality, hence no actual drawing ability yet!  What do you recommend I adjust?

---

### Post by Djibouti on 2011-12-25
I bought this for my daughter for Christmas. :)
 I look forward to the final solution.
 Hungary

---

### Post by viktoria.s on 2011-12-25
Hi!

I have a genious mousepen i608x too. I have problems with it too. (I have never used a tablet pen before so if I say something stupid please excuse me. ) There is a wireless mouse comes with the pen which is does not work. And I cannot use the pen as a mouse completely. On the pen there are 2 buttons I assume that one can be used as a left mouse button and the other is the right mouse button, but it is not on that way. The cursor moves around the screen, but nothing happens if I press the any of the buttons. I tried to draw with it in gimp nothing happened. I tried also my paint. With this software I could switch tools with clicking with one of the pen buttons, but I was not really capable of drawing anything.
I tried the xinput list comand the result:
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Genius MousePen i608X                       id=11    [slave  pointer  (2)]
&#9116;   &#8627; HID 04f3:0103                               id=13    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; 1.3M WebCam                                 id=10    [slave  keyboard (3)]
    &#8627; HID 04f3:0103                               id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                            id=16    [slave  keyboard (3)]
```and the xinput list-props "Genius MousePen i608X" command gives me this:
```

Device 'Genius MousePen i608X':
    Device Enabled (144):    1
    Coordinate Transformation Matrix (146):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (277):    0
    Device Accel Constant Deceleration (278):    1.000000
    Device Accel Adaptive Deceleration (279):    1.000000
    Device Accel Velocity Scaling (280):    10.000000
    Evdev Axis Inversion (281):    0, 0
    Evdev Axis Calibration (282):    <no items>
    Evdev Axes Swap (283):    0
    Axis Labels (284):    "Abs X" (270), "Abs Y" (271), "Abs Z" (272), "Abs Rotary X" (273), "Abs Rotary Y" (274), "Abs Rotary Z" (275), "Abs Pressure" (276), "None" (0)
    Button Labels (285):    "Button Left" (147), "Button Middle" (148), "Button Right" (149), "Button Wheel Up" (150), "Button Wheel Down" (151), "Button Horiz Wheel Left" (152), "Button Horiz Wheel Right" (153), "Button Side" (267), "Button Extra" (268), "Button Forward" (269), "Button Unknown" (263), "Button Unknown" (263), "Button Unknown" (263), "Button Unknown" (263)
    Evdev Middle Button Emulation (286):    0
    Evdev Middle Button Timeout (287):    50
    Evdev Wheel Emulation (288):    0
    Evdev Wheel Emulation Axes (289):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (290):    10
    Evdev Wheel Emulation Timeout (291):    200
    Evdev Wheel Emulation Button (292):    4
    Evdev Drag Lock Buttons (293):    0

```and I do not know if the mentioned /etc/X11/xorg.conf.d/52-wizardpen-on-evdev.conf file should be created manually? (I have not found it on my system) I am using 64bit ubuntu 11.10.
Thank you in advance for any help.

---

### Post by Favux on 2011-12-25
Hi SmithWillSuffice,

We're seeing the z-axis in the original list-props:
```
        Axis Labels (242):      "Abs X" (258), "Abs Y" (259), "Abs Z" (260), "Abs Rotary X" (261), "Abs Rotary Y" (262), "Abs Rotary Z" (263), "Abs Pressure" (264), "None" (0)

```
Since it seems to be using absolute Mode it apparently recognizes it is working with a tablet and not a mouse.  But then you lose it with your new .conf.  In fact:
```
Device 'Genius MousePen i608X':
        Device Enabled (117):   1
        Coordinate Transformation Matrix (119): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (235):     0
        Device Accel Constant Deceleration (236):       1.000000
        Device Accel Adaptive Deceleration (237):       1.000000
        Device Accel Velocity Scaling (238):    10.000000
```
Looks like the list-props you get with the WizardPen driver.  It doesn't announce itself like the evdev or Wacom driver does and is truncated like that.  You could check in Xorg.0.log in /var/log and see if the match is currently to evdev or the WizardPen driver.

And sorry if I'm stating the obvious but do you know about configuring the extended input devices (in this case the stylus) in Gimp and Inkscape to get pressure?

Anyway I'm wondering if we need a MatchVendor or MatchProduct like:
```
    MatchIsTablet "on"
#    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
# remove comment below if you have Genius MousePen i608
    MatchProduct "i608X"
    MatchDevicePath "/dev/input/event*"

```
inserted in the matches.

Again looking at *man evdev* in a terminal I don't really see anything about Z.  But since it is in xinput list-props maybe we could use *man xinput* to figure something out.


Hi viktoria.s,

Yes you need to manually create the 52-wizardpen-on-evdev.conf since there isn't a package installing it.  Use:
```
gksudo gedit /etc/X11/xorg.conf.d/52-wizardpen-on-evdev.conf
```
The WizardPen driver never supported the tablet mouse.  In fact that caused the stylus not to work which is why there is a mouse snippet with the "Ignore" option turned on.  But since the evdev driver does handle mice maybe it'll handle the tablet mouse too.  So we'd want to try changing the mouse snippet.  Maybe something on the order of?:
```
Section "InputClass"
    Identifier "wizardpen-on-evdev class"
    MatchIsTablet "on"
#    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
# remove comment below if you have Genius MousePen i608
    MatchProduct "i608X"
    MatchDevicePath "/dev/input/event*"
    Driver "evdev"
EndSection

Section "InputClass"
    Identifier "wizardpen-on-evdev mouse class"
    MatchIsTablet "on"
#    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
# remove comment below if you have Genius MousePen i608
    MatchProduct "i608X"
    MatchDevicePath "/dev/input/mouse*"
    Driver "evdev"
EndSection
```

---

### Post by viktoria.s on 2011-12-26
Hi!
I tried what you have wrote. This
> **Favux said:**
> 
Hi viktoria.s,

Yes you need to manually create the 52-wizardpen-on-evdev.conf since there isn't a package installing it.  Use:
```
gksudo gedit /etc/X11/xorg.conf.d/52-wizardpen-on-evdev.conf
```The   Maybe something on the order of?:
```
Section "InputClass"
    Identifier "wizardpen-on-evdev class"
    MatchIsTablet "on"
#    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
# remove comment below if you have Genius MousePen i608
    MatchProduct "i608X"
    MatchDevicePath "/dev/input/event*"
    Driver "evdev"
EndSection

```
Did not make the mousepen work properly.
I have got the following error message from MyPaint:
Ignoring "Genius MousePen i608X" (probably a mouse, but it reports extra axes) [3 times]
No pressure sensitive devices found.

> **Favux said:**
> 
Section "InputClass"
    Identifier "wizardpen-on-evdev mouse class"
    MatchIsTablet "on"
#    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
# remove comment below if you have Genius MousePen i608
    MatchProduct "i608X"
    MatchDevicePath "/dev/input/mouse*"
    Driver "evdev"
EndSection

And this part gave me errors in the Xorg.0.log. I forget to note what was the precise message, but it was something like it could not open the device /dev/input/mouse1 invalid ioctl was given or something like that.

Can I ask where have you find the we should use Identifier "wizardpen-on-evdev mouse class" and can you give me some ideas what kind of other Identifiers can we use? Because I have a feeling that the tablet is treated like a mouse not a pen, and therefore no pressure sensitivity coming through.

Thanks.

---

### Post by Favux on 2011-12-26
**[SIZE="3"]Everyone[/SIZE]**,

It just occurred to me that the Aiptek driver is in Oneiric.  And if I recall correctly at least some WizardPen tablets have been able to use the Aiptek driver before.  I might have that backward but I don't think so.  So in the snippet, after you install the Aiptek driver, you'd change:
```
    Driver "evdev"

```
to
```
    Driver "aiptek"

```
Maybe worth a shot.


Hi viktoria.s,

Actually the Xorg.0.logs would be very helpful to figuring out what is going on.  The xinput list-props is useful too, but the Xorg.0.log in /var/log can be handy.  You can compress it by right clicking on it and choosing Create Archive and then attach it to your post with Manage Attachments.

The *invalid ioctl* (input output control) on the mouse event /dev/input/mouse1 suggests that the evdev driver did a grab on the stylus event (makes sense since that snippet was first) and won't release for the mouse.  That might suggest the problem in using the mouse on these tablets is a kernel driver issue, not a X driver issue.  If true it is possible Nikolai Kondrashov could help us:  [http://digimend.sourceforge.net/](http://digimend.sourceforge.net/)  But we should probably concentrate on getting the stylus working before trying the mouse.  And we should probably check if in the mouse snippet instead of matching to the mouse and reselecting the driver we should assume the driver match and then go to the mouse.

The *xinput list* output should give us the keywords we need for the match.  So it is not so much the keywords but whether is is MatchVendor or MatchProduct or whatever.  Also at some point should we lose the MatchIsTablet to make in more generic?  That match could screen out some tablets depending on the udev rules.  For some more information on constructing xorg.conf.d snippets see:
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d)
[http://manpages.ubuntu.com/manpages/lucid/man5/xorg.conf.5.html#contenttoc8](http://manpages.ubuntu.com/manpages/lucid/man5/xorg.conf.5.html#contenttoc8)
[http://cgit.freedesktop.org/xorg/xserver/commit/?id=66b21b2f455a1dfbc92f7caa571dcff3f3765808](http://cgit.freedesktop.org/xorg/xserver/commit/?id=66b21b2f455a1dfbc92f7caa571dcff3f3765808)


**[SIZE="3"]OKAY[/SIZE]**,
So our two questions are:
1)  How do we enable pressure for "simple" tablets on the evdev driver?  This is linear pressure usually with either 512 or 1024 levels.  In other words are there Z axis coordinate commands we should be using and what are they?
2)  Does the evdev driver support a tablet mouse in addition to the stylus for these "simple" tablets?  Or if there is a problem is it due to the kernel driver?

If you want to modify or clean up those questions let me know.  I'd like to get them as clear and concise as possible.  I'm thinking of cheating because I know someone who could answer our questions.  In fact he could probably get pressure working in evdev if it doesn't work already.  However he is incredibly busy and I really don't want to bother him unless I have to.  Plus even if there is a response it may take quite a while.

---

### Post by viktoria.s on 2011-12-27
Hi Favux!

Thank you for your reply! The links you have sent were interesting. This page [http://digimend.sourceforge.net/](http://digimend.sourceforge.net/) contained some interesting informations. In the compatibility list I have found:
 ```

5543:0005   UC-Logic Tablet WP8060U     Genius MousePen 8x6 **Genius MousePen i608** DigiPro WP8060**   Manhattan 8"x6"**  Iball Pen Tablet 8060U**
OK              OK              OK
```I guess the i608X version not different from the i608 version so it might be supported.

The page itself said:
> Patches are accepted into the kernel and will appear in the             2.6.37 release.I am using 3.0.0-14-generic kernel so that might be right.
The page also said:
> Work has began on adding support for these tablets to             xf86-input-wacom driver.So I tried the tablet with the wacom driver, so far with no luck. The pressure sensitivity does not work.

I have attached a zip file containing the conf file and the x log.

I also installed evtest package and run some test. In the zip file you can find the test results. I run it on a console terminal (after hitting ctrl+alt+F1), but the stange thing that there weren't any pressure information on there. I tried just holding the pen in one position and change the pressure, but there was no Event type 3 / Event code 24 event. 
And I think that's not good.

Regards:
viktoria.s

---

### Post by Favux on 2011-12-28
I think what he meant by:
> Work has began on adding support for these tablets to xf86-input-wacom driver. 
was the Waltop tablets.  Because those are now supported by the Wacom X driver again after his patches to the Waltop kernel driver were accepted.  There was a period where they wouldn't work on the Wacom X driver anymore and Waltop tablets had to go to using the WizardPen driver.

Peter Hutterer mentioned maybe enabling the Wacom X driver (xf86-input-wacom) for the "simple tablets" when he was talking about using them on the evdev X driver, but he said there hadn't been a user demand for it.  So I'm not surprised it didn't work.

Well not only did your match in the 52-wacom.conf work surprisingly it appears that the Wacom driver went ahead and accepted the tablet since I don't see it rejected and the Wacom module unloaded in your Xorg.0.log.  So to me that indicates the Wacom X driver just doesn't support the WizardPen tablets.   But at least we now know that:
```
	MatchProduct "i608X"
	MatchDevicePath "/dev/input/event*"
```
gives us a match so that is progress!  Have you tried the Aiptek driver with that match?

But interestingly in the evtest output it seems to be saying there is a Z-axis (pressure) available since it reports:
```
    Event code 24 (Pressure)
      Value      0
      Min        0
      Max     1023
```
You're just seeing only X and Y axis coordinates on the raw data.  Now why?  Since you are in the console the X server isn't running and so it doesn't matter whether the tablet is on the Wacom or the evdev driver, correct?  But if the kernel driver wasn't reporting the Z-axis why does evtest and Xorg.0.log show it as available?  By the way is yours a KYE or a UC_LOGIC i608X?

---

### Post by Favux on 2011-12-28
So our current 52-wizardpen-on-evdev.conf for the i608X is:
```
Section "InputClass"
    Identifier "wizardpen-on-evdev class"
#    MatchIsTablet "on"
#    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
# remove comment below if you have Genius MousePen i608
    MatchProduct "i608X"
    MatchDevicePath "/dev/input/event*"
    Driver "evdev"
#    Option "TopZ" "10"
#    Option "BottomZ" "1023"
EndSection

Section "InputClass"
    Identifier "wizardpen-on-evdev mouse class"
#    MatchIsTablet "on"
#    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
# remove comment below if you have Genius MousePen i608
    MatchProduct "i608X"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```
We could use the entire "device name" of "Genius MousePen i608X" but unlike with xinput you see we can use any of the 3 keywords in xorg.conf.d.


@ viktoria.s,

What do you see in your Xorg.0.log with the above?  Does it change with the Z lines uncommented, i.e. active?  If so what is the difference?

**[SIZE="3"]Important[/SIZE]**:  I need your lsusb output for your tablet so I can verify the Vendor and ProductID.  Because the other i608X says:
```
Bus 002 Device 003: ID 0458:5011 KYE Systems Corp. (Mouse Systems)

```
which doesn't match the compatibility table's:
```
5543:0005   UC-Logic Tablet WP8060U     Genius MousePen 8x6 Genius MousePen i608 DigiPro WP8060**   Manhattan 8"x6"**  Iball Pen Tablet 8060U**

```
or other entry that I see.

---

### Post by viktoria.s on 2011-12-29
Hi Favux!

I have ```
sudo lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0402:9665 ALi Corp. 
Bus 002 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 004: ID 04f3:0103 Elan Microelectronics Corp. 
Bus 002 Device 005: ID 0458:5011 KYE Systems Corp. (Mouse Systems)

```and yes the KYE Systems Corp is the mousepen.
(For some strange reason the normal lsusb command does not lists the mousepen for me.)
If I create the 52-wizardpen-on-evdev.conf like in the #15 post.
I got the following in xorg.0.log according to the mousepen (if you need the full log please let me know and i attache it.)
```
[   705.552] (II) config/udev: Adding input device Genius MousePen i608X (/dev/input/event15)
[   705.552] (**) Genius MousePen i608X: Applying InputClass "evdev pointer catchall"
[   705.552] (**) Genius MousePen i608X: Applying InputClass "evdev keyboard catchall"
[   705.552] (**) Genius MousePen i608X: Applying InputClass "evdev tablet catchall"
[   705.552] (**) Genius MousePen i608X: Applying InputClass "wizardpen-on-evdev class"
[   705.552] (II) Using input driver 'evdev' for 'Genius MousePen i608X'
[   705.552] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   705.552] (**) Genius MousePen i608X: always reports core events
[   705.552] (**) Genius MousePen i608X: Device: "/dev/input/event15"
[   705.552] (--) Genius MousePen i608X: Found 10 mouse buttons
[   705.552] (--) Genius MousePen i608X: Found scroll wheel(s)
[   705.552] (--) Genius MousePen i608X: Found relative axes
[   705.552] (--) Genius MousePen i608X: Found x and y relative axes
[   705.552] (--) Genius MousePen i608X: Found absolute axes
[   705.552] (II) evdev-grail: failed to open grail, no gesture support
[   705.552] (--) Genius MousePen i608X: Found x and y absolute axes
[   705.552] (--) Genius MousePen i608X: Found absolute tablet.
[   705.552] (--) Genius MousePen i608X: Found keys
[   705.552] (II) Genius MousePen i608X: Configuring as tablet
[   705.552] (II) Genius MousePen i608X: Configuring as keyboard
[   705.552] (II) Genius MousePen i608X: Adding scrollwheel support
[   705.552] (**) Genius MousePen i608X: YAxisMapping: buttons 4 and 5
[   705.552] (**) Genius MousePen i608X: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   705.552] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input15/event15"
[   705.552] (II) XINPUT: Adding extended input device "Genius MousePen i608X" (type: KEYBOARD)
[   705.552] (**) Option "xkb_rules" "evdev"
[   705.552] (**) Option "xkb_model" "pc105"
[   705.552] (**) Option "xkb_layout" "hu"
[   705.552] (WW) Genius MousePen i608X: touchpads, tablets and touchscreens ignore relative axes.
[   705.552] (II) Genius MousePen i608X: initialized for absolute axes.
[   705.553] (**) Genius MousePen i608X: (accel) keeping acceleration scheme 1
[   705.553] (**) Genius MousePen i608X: (accel) acceleration profile 0
[   705.553] (**) Genius MousePen i608X: (accel) acceleration factor: 2.000
[   705.553] (**) Genius MousePen i608X: (accel) acceleration threshold: 4
[   705.553] (II) config/udev: Adding input device Genius MousePen i608X (/dev/input/mouse2)
[   705.553] (**) Genius MousePen i608X: Ignoring device from InputClass "wizardpen-on-evdev mouse class"
```There is no difference with the mousepen if I uncomment the #    Option "TopZ" "10"
#    Option "BottomZ" "1023" lines still no pressure sensitivity and the xorg.0.log messages are identical the one above.

Thank you for all your help, and if you need any other informations please let me know.

---

### Post by Favux on 2011-12-29
Alright, from what I am being told the evdev driver has indeed replaced the WizardPen driver.  Nick (Nikolai Kondrashov) says:
> It should just work for the models supported by the kernel.

See compatibility table [1]. The latest git of the patchset has untested support for one more model, see latest compatibility table [2]. If you need other models supported, I would be happy to add support for them to the kernel, provided there is anyone having the device and willing to help with diagnostics and testing.
In other words there is no need for a xorg.conf.d .conf file.  The problem being if you look in the 3.0 or later kernel the /drivers/hid/hid-kye.c is empty, no tablet entries at all.  And there isn't a hid-acecad.c at all.  Only the hid-uclogic.c has tablets entered.  It isn't clear to me whether some of the UC-LOGIC tablets and KYE tablets might be the same tablet, just with a different Vendor and Product ID.  In which case there might be something we could do.

Peter Hutterer further confirms there is no need for a .conf file because:
> evdev doesn't really treat any axes as a special one, it just forwards them. pressure is supposed to come from ABS_PRESSURE from the kernel and should just be forwarded as-is. Might be worth just running evtest against it to get the details. ABS_Z is for d devices that have a true z-axis.

there are no options specific to other axes than x and y though.
So no way to change Z axis settings.  This is a problem since it means evdev is feature incomplete for the tablets.  You should be able to change at least the pressure threshold (something like *Option "TopZ" "?"*).

@ viktoria.s,

It apparently doesn't matter that you are seeing the name *Genius MousePen* in the compatibility table.  What counts is that your:
Vendor ID = 0458 = KYE Systems
Product ID = 5011
And there is no Vendor ID 0458 in Nick's compatibility table that I see much less a 5011 product model.  I only see UC-LOGIC (5543) and Waltop (172f) tablets in the table.  This appears to explain why the following tablets are not exhibiting pressure:
```
lsusb:
Bus 001 Device 004: ID 0458:5010 KYE Systems Corp. (Mouse Systems)
xinput list:
&#9116;   &#8627; Genius EasyPen i405X                      id=11   [slave  pointer  (2)]
```
```
lsusb:
Bus 002 Device 003: ID 0458:5011 KYE Systems Corp. (Mouse Systems)
xinput list:
&#9116;   &#8627; Genius MousePen i608X                     id=9    [slave  pointer  (2)]
```
There're probably more but I'd have to go back and look for them.

So to get your tablet working you have to do what Nick requests above and on his site:  [http://digimend.sourceforge.net/](http://digimend.sourceforge.net/)  Send in the  usbhid-dump output he requests and then help him test kernel patches so he can submit them to the kernel.

---

### Post by viktoria.s on 2011-12-30
Hi Favux!

I just sent an email to Nick the usbhid-dump output. ;) If you want me to attach that to this forum too please let me know.

And thank you again for all your help.

---

### Post by Favux on 2011-12-30
Sure viktoria.s, please attach the output here too.  That way we can look and see if it is one of the models already in the hid-uclogic.c.

And thank you for sending that into Nick.

---

### Post by Djibouti on 2011-12-30
There is a permanent solution? If it's there, writing down in one?

---

### Post by Favux on 2011-12-31
Hi Djibouti,

What we have discovered is the problem is not with evdev, which is the X driver for the tablet.

The problem is with hid kernel driver for your model tablet.  Your model is not yet in the hid driver.  The only way to fix that is to patch the kernel.  Viktoria.s has sent Nick the usbhid-dump information he needs to patch/add the i608X to the kernel hid driver.  Once viktoria.s tests Nick's proposed changes Nick will submit them to the kernel for inclusion.  I don't know if that will be the 3.3 kernel; probably the 3.4 kernel.  Likely he'll also then supply backports of the patches for older kernels (like Oneiric's 3.0) as he already does on his site.

For Ubuntu I guess it would be nice if someone made an Oneiric PPA of the patches, probably using a dkms implementation.

---

### Post by viktoria.s on 2012-01-02
Hi!

Happy new year to all of you!

@ Favux
I have attached the data I have sent to Nick plus the output of sudo lsusb -v -d 0458:5011 (which was also requested by Nick).

Nick wrote me the following:
> The Genius MousePen i608X is very much different from i608. The latter is an
old and simple UC-Logic model, which I have myself, in fact. The former is a
new device, seemingly developed inside Genius (KYE Systems) and very much
similar to Genius MousePen i405X.

There are other, easily solvable problems with them, but the main problem is
that these two only work as a mouse (i.e. no pressure data), unless told by
the driver to switch to tablet mode. It is not apparent how to do that.

We would need to either contact Genius and ask them or try to capture the
Windows driver USB traffic. It is possible to do that either with a proper
Windows machine or with a Windows machine inside a virtual machine under
Linux. There are several ways to do that and I could try to provide you with
instructions for at least some of them.

Once and if it is done, I could make a Linux kernel driver and build a
kernel package for you to try. If and when it works, I would submit the
driver to the upstream and in time it will appear in stock Ubuntu. Until
then you will need to compile the kernel whenever you need it updated.
Unless, of course, someone volunteers to make a DKMS package for the driver.
I am not quite sure if I can run the test on a windows machine, since I am not using windows at all at the moment. I may try to set up a virtual machine on my computer but it may take a lot of time for me. It would be great if someone who uses windows could capture the windows driver trafic.

---

### Post by Favux on 2012-01-02
Happy New Year!

Thank you for the information.
> the main problem is
that these two only work as a mouse (i.e. no pressure data), unless told by
the driver to switch to tablet mode. It is not apparent how to do that.
This reminds me of the bluetooth Wacom tablets.  The kernel's Bluez stack needs to be told to switch to high speed mode, not the default low speed mode, in order for the tablet to report correctly.

So Nick doesn't think it is as easy as adding to the hid-quirks.c's (in the kernel's /drivers/hid/usbhid directory) hid_blacklist the Vendor and Product IDs along with HID_QUIRK_MULTI_INPUT as in?:
```
	{ USB_VENDOR_ID_UCLOGIC, USB_DEVICE_ID_UCLOGIC_TABLET_PF1209, HID_QUIRK_MULTI_INPUT },
	{ USB_VENDOR_ID_UCLOGIC, USB_DEVICE_ID_UCLOGIC_TABLET_WP4030U, HID_QUIRK_MULTI_INPUT },
	{ USB_VENDOR_ID_UCLOGIC, USB_DEVICE_ID_UCLOGIC_TABLET_KNA5, HID_QUIRK_MULTI_INPUT },
	{ USB_VENDOR_ID_UCLOGIC, USB_DEVICE_ID_UCLOGIC_TABLET_TWA60, HID_QUIRK_MULTI_INPUT },
	{ USB_VENDOR_ID_UCLOGIC, USB_DEVICE_ID_UCLOGIC_TABLET_WP5540U, HID_QUIRK_MULTI_INPUT },
	{ USB_VENDOR_ID_UCLOGIC, USB_DEVICE_ID_UCLOGIC_TABLET_WP8060U, HID_QUIRK_MULTI_INPUT },
	{ USB_VENDOR_ID_WALTOP, USB_DEVICE_ID_WALTOP_MEDIA_TABLET_10_6_INCH, HID_QUIRK_MULTI_INPUT },
	{ USB_VENDOR_ID_WALTOP, USB_DEVICE_ID_WALTOP_MEDIA_TABLET_14_1_INCH, HID_QUIRK_MULTI_INPUT },
```
Of course not, why make it easy?

Hope someone has Windows to test with and will help.

---

### Post by Favux on 2012-01-27
[SIZE="3"]**FYI Update**[/SIZE]:

Nikolai Kondrashov with the help of viktoria.s has "discovered the way to make the KYE tablets report all the data, including pressure. This was tested with EasyPen i405X, EasyPen M610X and MousePen i608X in userspace with modified usbhid-dump."

Nick is now working on the kernel driver for the KYE tablets.  He's gone to the extent of ordering an EasyPen i405X from Amazon UK to be delivered to him in Finland!  So with a little luck support should be available shortly.  :)

---

### Post by gjrodher on 2012-02-13
hello all!
I'm new to ubuntu forums.
I am following this issue of i608X genius because I bought one and I can not use it on ubuntu!
unfortunately I haven't the knowledge they needed to help on this issue but am just like at your disposal to help reach the solution of the problem!

Greetings!

---

### Post by Favux on 2012-02-13
Hi gjrodher,

Welcome to Ubuntu forums!

What release of Ubuntu do you have?  I don't think Nick has come out yet with kernel patches to get your Genius i608X working yet, so there is nothing to test.  Hopefully not too much longer for them.  He may be a little overdue and I suppose I'll contact him in a little bit if he doesn't post them.

---

### Post by gjrodher on 2012-02-13
Thank you very much for your quick response Favux!
I have Ubuntu 11.10 x86_64 with 3.0.0-15 kernel.
I appreciate the efforts made by you to help novices like me!
Sorry for any errors in the writing, I do not speak English as a native language but I make my effort to make me understand!

A hug!

---

### Post by viktoria.s on 2012-02-15
Hi everybody!

I have got great news! Nick has completed the kernel patch.:):):). A big thank you for him! See the attachment.
Nick wrote about it:
> 
Please find attached the supposedly working KYE tablet kernel patch. This is
for those of you who would like to built their own kernel. This is also to
have it published in some form for now.

It should support EasyPen i405X, EasyPen M610X and MousePen i608X.

The EasyPen M610X should have "eraser" button mapped to "redo", because
neither the HID standard nor the Linux evdev interface have "eraser" key
code and I didn't want it to send any application-specific key code.

The MousePen i608X should have mouse in absolute mode for now. I'll see
what could be done about it later.
Nick has also built the latest version of 64-bit Ubuntu kernel (I have used with Ubuntu 11.10) which you can download from here:
[http://ponomarevs.no-ip.org:40404/pub/linux-headers-3.0.0-16_3.0.0-16.28_all.deb](http://ponomarevs.no-ip.org:40404/pub/linux-headers-3.0.0-16_3.0.0-16.28_all.deb)
[http://ponomarevs.no-ip.org:40404/pub/linux-headers-3.0.0-16-kye_3.0.0-16.28_amd64.deb](http://ponomarevs.no-ip.org:40404/pub/linux-headers-3.0.0-16-kye_3.0.0-16.28_amd64.deb)
[http://ponomarevs.no-ip.org:40404/pub/linux-image-3.0.0-16-kye_3.0.0-16.28_amd64.deb](http://ponomarevs.no-ip.org:40404/pub/linux-image-3.0.0-16-kye_3.0.0-16.28_amd64.deb)

Nick wrote about these:
> 
Please install them to try the driver. It should work with xf86-input-evdev
without any configuration. Please remove any WizardPen configuration you had
done.

Please report success or failure.
There is also a request from Nick: he is still waiting for feedback on EasyPen M610X - if there is any owners of this tablet he would like to ask for testing to speed it up.

Regards:
Viktoria.s

---

### Post by viktoria.s on 2012-02-15
Hi!

I have posted the new kernel patch/build in post #28. 
Now I would like to inform you how to make the tablet work in mypaint. 
(I have Ubuntu 11.10+Genius MousePen i608X and this has worked for me.)

The current version in ubuntu 11.10 is 0.9.1-1, but unfortunately with this version you can draw with the pen but unfortunately there are no pressure sensitivity. 

So my solution is:
Visit this website [https://launchpad.net/~achadwick/+archive/mypaint-testing]("https://launchpad.net/%7Eachadwick/+archive/mypaint-testing") and follow the instructions on this page to upgrade mypaint to 1.0.0.
Start mypaint and choose from the menu MyPaint>Help>Debug>GTK Input device dialog
On that dialog in the Device: list choose the first Genius MousePen i608X item. (This is the pen. The second is the mouse.)
Set Mode: to screen. (See the image bellow.)
[IMG]http://img163.imageshack.us/img163/442/mypaint10inpusdev.png[/IMG]

And after that you will get pressure sensitivity in mypaint.:)

If you have any problem with this please let me know.

Regards:
viktoria.s

---

### Post by viktoria.s on 2012-02-15
Hi!

I have posted the new kernel patch/build in post #28. 
Now I would like to inform you how to make the tablet work in gimp. 
(I have Ubuntu 11.10+Genius MousePen i608X and this has worked for me.)

The current version in ubuntu 11.10 is 2.6.11. 
You can setup the tablet in this version by selecting Edit>Preferences and on that dialog Input devices and then selecting Configure extended input devices. That dialog is the same dialog as in mypaint 1.0.0, so you should set it up the tablet as I mentioned in the previous post.
But unfortunately with this version you can draw, but occasionaly there are weird horizontal and vertical lines appear on the drawing.

So my solution for that problem is:
Visit this website: [http://alcides-mp.com/software/gimp-2-7-4-binaries-for-ubuntu/](http://alcides-mp.com/software/gimp-2-7-4-binaries-for-ubuntu/) and download and extract gimp 2.7.4 to /opt/gimp-2.7.4 directory.
After I have extracted the file there were some problems with the symbolic links in the lib directory and gimp did not started. I did the following to solve that problem:
I have deleted the following files from the /opt/gimp-2.7.4/lib directory:
```

libpangoxft-1.0.so.0
libpangox-1.0.so.0
libpangoft2-1.0.so.0
libpangocairo-1.0.so.0
libpango-1.0.so.0
libgthread-2.0.so.0
libgobject-2.0.so.0
libgmodule-2.0.so.0
libglib-2.0.so.0
libgio-2.0.so.0
libgimpui-2.0.so.0
libgimpmodule-2.0.so.0
libgimpbase-2.0.so.0
libgimp-2.0.so.0
libgegl-0.1.so.0
libbabl-0.1.so.0
libgimpcolor-2.0.so.0
libgimpthumb-2.0.so.0
libgimpmath-2.0.so.0
libgimpconfig-2.0.so.0
libgdk-x11-2.0.so.0
libgtk-x11-2.0.so.0
libgimpwidgets-2.0.so.0

```After that I have created the following sympolic links in the /opt/gimp-2.7.4/lib directory:
```

libpangoxft-1.0.so.0 -> /opt/gimp-2.7.4/lib/libpangoxft-1.0.so.0.2905.0
libpangox-1.0.so.0 -> /opt/gimp-2.7.4/lib/libpangox-1.0.so.0.2905.0
libpangoft2-1.0.so.0 -> /opt/gimp-2.7.4/lib/libpangoft2-1.0.so.0.2905.0
libpangocairo-1.0.so.0 -> /opt/gimp-2.7.4/lib/libpangocairo-1.0.so.0.2905.0
libpango-1.0.so.0 -> /opt/gimp-2.7.4/lib/libpango-1.0.so.0.2905.0
libgthread-2.0.so.0 -> /opt/gimp-2.7.4/lib/libgthread-2.0.so.0.3106.0
libgobject-2.0.so.0 -> /opt/gimp-2.7.4/lib/libgobject-2.0.so.0.3106.0
libgmodule-2.0.so.0 -> /opt/gimp-2.7.4/lib/libgmodule-2.0.so.0.3106.0
libglib-2.0.so.0 -> /opt/gimp-2.7.4/lib/libglib-2.0.so.0.3106.0
libgio-2.0.so.0 -> /opt/gimp-2.7.4/lib/libgio-2.0.so.0.3106.0
libgimpui-2.0.so.0 -> /opt/gimp-2.7.4/lib/libgimpui-2.0.so.0.704.0
libgimpmodule-2.0.so.0 -> /opt/gimp-2.7.4/lib/libgimpmodule-2.0.so.0.704.0
libgimpbase-2.0.so.0 -> /opt/gimp-2.7.4/lib/libgimpbase-2.0.so.0.704.0
libgimp-2.0.so.0 -> /opt/gimp-2.7.4/lib/libgimp-2.0.so.0.704.0
libgegl-0.1.so.0 -> /opt/gimp-2.7.4/lib/libgegl-0.1.so.0.107.1
libbabl-0.1.so.0 -> /opt/gimp-2.7.4/lib/libbabl-0.1.so.0.106.1
libgimpcolor-2.0.so.0 -> /opt/gimp-2.7.4/lib/libgimpcolor-2.0.so.0.704.0
libgimpthumb-2.0.so.0 -> /opt/gimp-2.7.4/lib/libgimpthumb-2.0.so.0.704.0
libgimpmath-2.0.so.0 -> /opt/gimp-2.7.4/lib/libgimpmath-2.0.so.0.704.0
libgimpconfig-2.0.so.0 -> /opt/gimp-2.7.4/lib/libgimpconfig-2.0.so.0.704.0
libgdk-x11-2.0.so.0 -> /opt/gimp-2.7.4/lib/libgdk-x11-2.0.so.0.2400.8
libgtk-x11-2.0.so.0 -> /opt/gimp-2.7.4/lib/libgtk-x11-2.0.so.0.2400.8
libgimpwidgets-2.0.so.0 -> /opt/gimp-2.7.4/lib/libgimpwidgets-2.0.so.0.704.0

```And in this way gimp has started.
In order to configure gimp you should choose Edit>Input devices, on the dialog select Genius MousePen i608X form the list on the left (in this version of gimp there is only one item for this tablet) and set Mode to screen. (See the image bellow.)
[IMG]http://img7.imageshack.us/img7/6940/gimp247conf.png[/IMG]

And in this version of gimp those weird horizontal/vertical line did not appeared.:D

If you have any problem with this please let me know.

Regards:
viktoria.s

---

### Post by viktoria.s on 2012-02-15
Hi!

I have posted the new kernel patch/build in post #28. 
Now I would like to inform you how to make the tablet work in Alchemy. 
(If you do not know this software you can get more informations about it here: [http://al.chemy.org/](http://al.chemy.org/))
(I have Ubuntu 11.10+Genius MousePen i608X and this has worked for me.)
I have got the BETA 008 version of this sowftware and OpenJDK 1.6.0_23.

If you launch the software there might be a problem with the libjpen library. 
(Based on this page [http://al.chemy.org/forum/bugs/topic638.html](http://al.chemy.org/forum/bugs/topic638.html) I did the following.)
I have rename the Alchemy's lib directory to libold. 
I have downloaded the jpen library (jpen-2-100101-lib.zip) from here [http://sourceforge.net/projects/jpen/files/jpen/2-100101/](http://sourceforge.net/projects/jpen/files/jpen/2-100101/)
I have created a new lib directory under the Alchemy directory and copied there libjpen-2-2-ia64.so, libjpen-2-2.so, libjpen-2-2-x86_64.so, libjpen-2-3.jnilib from the zip file. I have copied into the Alchemy directory the jpen-2.jar from the zip.

I have started the Alchemy (from the Alchemy directory) in a terminal window with the following command:
java -Djava.library.path=lib -jar Alchemy.jar

If you have successfully set up everything the following message should appear in the terminal:
INFO: jpen-2-2-x86_64 loaded
and if you choose Pressure Shapes in the Create menu you can see how the pressure is affecting the shape of what you are drawing.
(As far as I know the pressure affect only this tool.)

If you have any problem with this please let me know.

Regards:
viktoria.s

---

### Post by Favux on 2012-02-15
Hi viktoria,

Thank you (and Nick!) for posting the new Kye Systems kernel patch for the EasyPen i405X, EasyPen M610X, MousePen i608X.  :)

The Gimp ghost line problem is due to a bug in Oneiric (and Natty) which is made obvious by Gimp's history buffer.  Unlike Oneiric's default 2.6 Gimp the 2.7 version has the history buffer disabled (removed?) because it caused too many problems/bugs.  Alexia Death (Gimp developer) provided a patch to turn off the history buffer on this Launchpad bug report:  [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154/](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154/)  Aapo Rantalainen made a PPA for the patch applied to the default version of Gimp in Oneiric:  [https://launchpad.net/~aapo-rantalainen/+archive/gimp26-noghostline](https://launchpad.net/~aapo-rantalainen/+archive/gimp26-noghostline)  Once the patched Gimp is installed from the PPA it should work fine.  Using the PPA may be simpler for folks.

---

### Post by viktoria.s on 2012-02-15
Hi Favux!

Thank you for your tip:
> **Favux said:**
> 
Alexia Death (Gimp developer) provided a patch to turn off the history buffer on this Launchpad bug report:  [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154/](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154/)  Aapo Rantalainen made a PPA for the patch applied to the default version of Gimp in Oneiric:  [https://launchpad.net/~aapo-rantalainen/+archive/gimp26-noghostline]("https://launchpad.net/%7Eaapo-rantalainen/+archive/gimp26-noghostline")  Once the patched Gimp is installed from the PPA it should work fine.  Using the PPA may be simpler for folks.

I just tested this version of gimp and it worked well (no ghost lines) with this kernel too :).

---

### Post by janailson on 2012-02-16
I apologize for the ignorance, but how do I install this patch? 
I am using 3.0.0-14-generic kernel / Ubuntu 11.10

---

### Post by viktoria.s on 2012-02-17
Hi janailson!

If you're using Ubuntu 11.10 64-bit then I suggest you to download the 3 prebuilt packages. You can find the links for those packages in post #28 (previous page). 
Just download them and install them by running sudo dpkg -i *16.28*.deb from the directory you have downloaded the packages. For me that worked perfectly.
If you want to use the kernel patches you have to build the kernel yourself and unfortunately I cannot help with that, because I have never built a kernel before.

---

### Post by janailson on 2012-02-17
> **viktoria.s said:**
> Hi janailson!

If you're using Ubuntu 11.10 64-bit then I suggest you to download the 3 prebuilt packages. You can find the links for those packages in post #28 (previous page). 
Just download them and install them by running sudo dpkg -i *16.28*.deb from the directory you have downloaded the packages. For me that worked perfectly.
If you want to use the kernel patches you have to build the kernel yourself and unfortunately I cannot help with that, because I have never built a kernel before.

:( Too bad ...... use Ubuntu 32 bit and also do not know compile the kernel ....: (
Use the Genius i405x.

---

### Post by viktoria.s on 2012-02-19
Hi janailson!
> **janailson said:**
> :( Too bad ...... use Ubuntu 32 bit and also do not know compile the kernel ....: (
Use the Genius i405x.

As far as I know Nick has started to work on a DKMS package, and that may help you out.
(But I guess that is going to take a little bit of time to complete, so please be patient.)

---

### Post by janailson on 2012-02-19
> **viktoria.s said:**
> Hi janailson!


As far as I know Nick has started to work on a DKMS package, and that may help you out.
(But I guess that is going to take a little bit of time to complete, so please be patient.)

Wow!
OK!
Thanks for the valuable information!! : D
(Will it work nicely on Ubuntu 11.04?)

---

### Post by viktoria.s on 2012-02-20
Hi everybody!

I got great news for you :)! Nick wrote me the following (on Sun, 19 Feb 2012):
> 
Yesterday I have decided to resurrect my old development blog and post small
news there. You can subscribe to it or just visit it from time to time to
see what progress I make in refining support for your tablets and when I
finally submit the patches to the kernel.

The blog URL is [https://sourceforge.net/apps/wordpress/digimend/](https://sourceforge.net/apps/wordpress/digimend/)
The RSS URL is [https://sourceforge.net/apps/wordpress/digimend/feed/](https://sourceforge.net/apps/wordpress/digimend/feed/)


---

### Post by viktoria.s on 2012-03-10
Hi!

I just have a question. Nick wrote on his blog ([http://sourceforge.net/apps/wordpress/digimend/](http://sourceforge.net/apps/wordpress/digimend/)) that this patch probably will appear only in the 3.4 kernel. I am just wondering is there any way to put it into the ubuntu kernel sooner than that? (For example if this patch could go at least to the kernel of the 12.04 release that would be great.)
(At this moment I have 2 choices I use Nick's packages and not updating my kernel or somehow learn patch and compile the latest ubuntu kernel (which sounds not easy))

Thanks in advance.

---

### Post by Favux on 2012-03-10
Hi viktoria.s,

Well the ideal way would be to put in a Launchpad bug report on the KYE tablets for Precise.  And on that report post Nick's patch, so they know there is a fix available.  Then hope the kernel team backports the KYE support into Precise's 3.3 (?) kernel.  That's much more likely if the patch has been accepted upstream by the kernel into 3.4.

But even if the kernel team decided to do that it might be months before you actually see the backport.

Doing it yourself isn't that hard.  See appendix 1 at the bottom of the [Wacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949").  The command to download the Ubuntu kernel source code is there.  Also the magic command to compile modules.  Nick's patch will tell you which modules are changed and that will tell you which ones to copy into place.  You could end up with a little HOW TO to post for KYE tablets.

---

### Post by Favux on 2012-03-11
Hi,

I've got the patch in a patch form that I can attach to a post and you can download.  And I've got preliminary instructions roughed out.

Did you want to try this?

---

### Post by viktoria.s on 2012-03-13
Hi Favux,

thank you for your advices.

> **Favux said:**
> Hi,

I've got the patch in a patch form that I can attach to a post and you can download.  And I've got preliminary instructions roughed out.

Did you want to try this?

Yes, sure :). Thanks.

---

### Post by Favux on 2012-03-13
I forgot to ask.  What kernel (uname -r) are you using?  I've forgotten which Ubuntu release you have.

---

### Post by Favux on 2012-03-13
Alright, here goes.

If the kernel source code doesn't download then you may need to check in Software Sources in the Ubuntu Software tab if you have the box in front of Source code checked.

We'll do  everything on the Desktop.

First download on your Desktop HID-kye-Add-support-for-3-tablets.patch and extract it.  Then open a terminal and download your Ubuntu kernel's source code onto your Desktop with the following commands.
```
cd Desktop

sudo apt-get build-dep --no-install-recommends linux-image-$(uname -r)

apt-get source linux-image-$(uname -r)
```
The dependencies can take a while to download.  The kernel is about 94 MB and takes a few minutes to download depending on your connection. You'll see something like  linux_3.0.0.orig.tar.gz, linux_3.0.0-16.29.dsc, linux_3.0.0-16.29.diff.gz, and linux-3.0.0 if your release is Oneiric.

To see the files you want to patch and then compile you can use Nautilus (Places) to go into the kernel's folder (linux-3.0.0) now on your Desktop and navigate to drivers/input/hid.

You'll apply the patch in the terminal using the following commands:
```
cd linux-3.0.0

patch -p1 < ~/Desktop/HID-kye-Add-support-for-3-tablets.patch
```
I tested and this 3.4 kernel patch did apply succesfully to the 3.0 kernel, albeit some hunks requiring an offset.  After the files are patched change directory to the downloaded kernel's source code /drivers/hid directory:
```
cd drivers/hid
```
Now you are ready to compile the HID modules. Use the following command:
```
make -C/lib/modules/`uname -r`/build M=`pwd` modules
```
This compiles all the HID modules, which you don't need, but the compile goes fast even so.

I think we want 3 of the compiled modules:  hid.ko, hid-kye.ko, and usbhid.ko.  First make a backup of your current versions using some extension.  You want to be able to restore them from the Recovery Mode command line if you have to.  I don't think the changes to hid.ko or usbhid.ko will break anything else, but to be safe.
```
sudo cp /lib/modules/$(uname -r)/kernel/drivers/hid/hid.ko /lib/modules/$(uname -r)/kernel/drivers/hid/hid.ko.orig

sudo cp /lib/modules/$(uname -r)/kernel/drivers/hid/hid-kye.ko /lib/modules/$(uname -r)/kernel/drivers/hid/hid-kye.ko.orig

sudo cp /lib/modules/$(uname -r)/kernel/drivers/hid/usbhid/usbhid.ko /lib/modules/$(uname -r)/kernel/drivers/hid/usbhid/usbhid.ko.orig

sudo cp /lib/modules/$(uname -r)/kernel/drivers/hid/usbhid/usbmouse.ko /lib/modules/$(uname -r)/kernel/drivers/hid/usbhid/usbmouse.ko.orig

```
Now you copy the appropriate newly compiled modules into your system kernel's modules directory with:
```
sudo cp hid.ko /lib/modules/$(uname -r)/kernel/drivers/hid/hid.ko

sudo cp hid-kye.ko /lib/modules/$(uname -r)/kernel/drivers/hid/hid-kye.ko

sudo cp usbhid/usbhid.ko /lib/modules/$(uname -r)/kernel/drivers/hid/usbhid/usbhid.ko

sudo cp usbhid/usbmouse.ko /lib/modules/$(uname -r)/kernel/drivers/hid/usbhid/usbmouse.ko

```
* need for usbmouse.ko from viktoria.s

Rebuild all of the module dependencies:
```
sudo depmod -a
```
A reboot and with luck the KYE tablet should be working.

---

### Post by viktoria.s on 2012-03-19
Hi Favux!

Thank you for the instructions. I have installed XUbuntu 12.04 onto a virtual machine and tried you method on that one. (To me testing if I can do it on precise is more important than to test it in oneiric, since there is a package in oneiric, but there will not be a package for precise (Unless of course the 3.4 linux kernel comes out and there will be a package in the mainline kernel ppa ;)))
So I could make the modules and it is seems working on the VM at least. I have only a few comments to make.
When you do the backup and copy the correct directory is /lib/modules/kernel/drivers/hid
```
sudo cp /lib/modules/$(uname -r)/kernel/drivers/hid/hid.ko /lib/modules/$(uname -r)/kernel/drivers/hid/hid.ko.orig
```I guess you have missed the /drivers/ in the path. And in the /lib/modules/kernel/drivers/hid/usbhid directory I had to replace all the files: usbhid.ko, usbkbd.ko, usbmouse.ko too (not just the one you have mentioned), otherwise there was errors on the startup of X. (The X started but with errors.)(Probably because the MousePen i608X has a mouse so it seems logical that at the least minimum the usbmouse.ko is required as well, but I have replaced the usbkbd.ko too just to make sure everything will be OK.)

---

### Post by Favux on 2012-03-19
Hi viktoria.s,

> I have installed XUbuntu 12.04 onto a virtual machine...I could make the modules and it is seems working on the VM
Great!  :)  Thank you for testing.
> I guess you have missed the /drivers/ in the path.
Sorry.  :redface:  Thanks for catching that.

Could you test with the original usbkbd.ko, not the newly compiled usbkbd.ko?  And see if that still gives you X startup errors.  Since we're using the patched vanilla kernel HID I'm trying to make the minimum changes needed to get the KYE tablet working.  On the hope that will minimize the risk of breakage.  So that's important to get a definite answer on.

> And in the /lib/modules/kernel/drivers/hid/usbhid directory I had to replace all the files: usbhid.ko, usbkbd.ko, usbmouse.ko too (not just the one you have mentioned), otherwise there was errors on the startup of X.
My fault because prior to Oneiric (or maybe Natty?) in the usbhid directory there was only usbhid.ko.  Presumably because the Ubuntu Makefiles combine usbhid.ko, usbkbd.ko, and usbmouse.ko into usbhid.ko in earlier kernels, I'll have to check.  I noticed that Oneiric no longer did that but then I went ahead and acted like it was an earlier kernel.  Oops! :)

---

### Post by viktoria.s on 2012-03-24
Hi Favux,

> Could you test with the original usbkbd.ko, not the newly compiled usbkbd.ko?  And see if that still gives you X startup errors.I have tested and it seems working OK with the original usbkbd.ko file.

---

### Post by Favux on 2012-03-24
Great.  :)  Thanks for narrowing it down.  I think we now have a working HOW TO.

I'm hoping it will generalize to Nick's other kernel patches for the earlier Ubuntu kernels for Lucid, Maverick, and Natty.


**[SIZE="3"]FYI everyone[/SIZE]**:  I've created a new [**HOW TO Add Support for KYE, UC-logic, and Waltop Tablets in Ubuntu**]("http://ubuntuforums.org/showthread.php?t=1946486") which includes the above KYE tablet support instructions.

---

### Post by janailson on 2012-03-25
:-)

---

### Post by fahren on 2012-07-21
Hi Favux

If i follow your HOW TO i can give support to my tablet genius mousepen i608x ?

If it's that true then i'll try to do it. Hope you make this how to for dummys as well :P

i have to say that i use ubuntu 12.04 for amd 64 with gnome-shell :)

kind regards from chile :D

---

### Post by Favux on 2012-07-21
Hi fahren from Chile,  :)

Welcome to Ubuntu forums!


It looks like yours is one of the models that the HOW TO will help get working.  To confirm run **lsusb** in a terminal.  In the tablet line you should see 0458:5011.  Also see:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)

You could also use the kernel Nick has compiled with the patch in it.  See the **Kernel packages** link here:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend)  It'll be an older version of the Precise kernel you are using now, most likely.

We are trying to come up with a way to make this simpler.

---

### Post by fahren on 2012-07-24
> **Favux said:**
> Hi fahren from Chile,  :)

Welcome to Ubuntu forums!


It looks like yours is one of the models that the HOW TO will help get working.  To confirm run **lsusb** in a terminal.  In the tablet line you should see 0458:5011.  Also see:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)

You could also use the kernel Nick has compiled with the patch in it.  See the **Kernel packages** link here:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend)  It'll be an older version of the Precise kernel you are using now, most likely.

We are trying to come up with a way to make this simpler.
you know? i have doubts about the tutorial and all the comments...

fist of all i'm not a english native speaker so excuse me if i'm not so clear with what i say...

- i have to download linux-headers-3.0.0-16-kye_3.0.0-16.28_amd64.deb and 
linux-image-3.0.0-16-kye_3.0.0-16.28_amd64.deb ? but my kernel is 3.
xx.

- it's necesary Nick's kernel?

- i have to use the Attached Files?

---

### Post by Favux on 2012-07-24
You have two choices.

1)  Use Nick's pre-compiled kernel.  He has compiled a whole kernel with the patch applied.  Yes it will probably be older than the kernel you have.

To find your kernel version enter in a terminal:
```
uname -r
```

2)  Use the attached patch and patch the kernel source that you download yourself.  You don't compile the whole kernel.  Just the kernel modules you need.


And yes if you are having trouble reading and understanding the instructions, go slow.  Or rethink trying.

I understand it is hard to follow, especially in another language.

---

### Post by fahren on 2012-07-25
> **Favux said:**
> You have two choices.

To find your kernel version enter in a terminal:
```
uname -r
```

2)  Use the attached patch and patch the kernel source that you download yourself.  You don't compile the whole kernel.  Just the kernel modules you need.

I understand it is hard to follow, especially in another language.

Hi, my kernel is: 3.2.0-26-generic

I have to download this kernel version? And the attached patches?...

Have to do all that in the desktop? I'll try this weekend cause i use my laptop in a production environment :P and i don't want to take unnecesary risks...

Or better: i'll try it on a virtual machine to test how it works :D

I'll keep you inform about that :)

Kind regards :P

---

### Post by fahren on 2012-07-26
Hi, it's me again :)

I cancompile the kernel modules associated with the tablet in a virtual machine and it is a easy thing to do but... it doesn't work because i have to install other stuf to make it work...

So, now i'm gonna test it on my laptop :O

please prey for me xD

---

### Post by Favux on 2012-07-26
My fingers are crossed.  Good luck!

---

### Post by fahren on 2012-07-26
Favux it work!! now i can sketch or draw in my ubuntu linux! i love it! thanks by the support man :)

a big hug from chile :KS

---

### Post by Favux on 2012-07-26
Great!  You are welcome.

I'll take a hug from Chile.  :)

---

### Post by Mediqiam on 2012-07-28
Greetings from Venezuela,

I've just registered yesterday, and I found this post very useful. I've got a new Genius i608 mousepen, and this info can prevent the Ubuntu user from a big headache. Thanks a lot for your time and efforts. The tablet works Ok.

I'd like, if you agree, to translate this info to my native language (Spanish), due to little differences in the naming of some folders.

---

### Post by Favux on 2012-07-28
Hi Mediqiam,

Welcome to Ubuntu forums!


Sure, feel free to translate the information to Spanish.  I hope it helps many Spanish speaking KYE Systems tablet users on linux.  :)

---

### Post by Mediqiam on 2012-08-17
Thank you!, I will, but now I find that perhaps because of an update of Ubuntu, the table no longer works properly. That is, it works as a pointer, but not the buttons or the tip of the pen work well. I've found the pen tip causes the Internet browser go previous page, and the main button leads to next page; the secondary button has no effect. I repeated the procedure with the kernel, and the problem continues. It was good while it lasted :)

I'll keep searching a solution, but I think you all are in the right way, thanks.

---

### Post by Favux on 2012-08-17
Hi Mediqiam,

If the update contained a kernel update that's what broke your tablet.  The tablet modules need to be recompiled against the new kernel for you to get a working tablet.

That's the drawback of compiling the modules.  You can't allow a kernel update unless you are prepared to recompile them.  That is why I talk about dkms (dymnamic kernel module support).  That would automatically recompile the modules for you with a new kernel.  But the HID part of the kernel doesn't allow that yet.  I think Nick said they've (Jiri and Nick) enabled it in the 3.5 kernel.

You could use one of Nick's pre-made kernels.  He's added a few more:  [http://sourceforge.net/projects/digimend/files/kernel-packages/kernel-patches-5/](http://sourceforge.net/projects/digimend/files/kernel-packages/kernel-patches-5/)  But then you have to use that kernel until he adds an updated kernel.

My guess is something went wrong with your recompile.  Perhaps you did not copy the newly compiled modules into the correct locations?

---

### Post by Mediqiam on 2012-08-17
Hi Favux.

You may be right. Tonite I'll repeat the patch & recompile process, step by step in order to verify. If it doesn't work, I'll download the precompiled kernels. Anyway, I'll be posting the results for reference.

Thanks again :).

---

### Post by Mediqiam on 2012-08-25
Hi everybody.

Well, after a week, I had the time to solve my tablet issue. I followed the suggestion from **Favux**, and installed the pre-compiled kernel with tablet support. And, as expected, it is working now; thanks.

It's important to remember: the automatic Ubuntu kernel updates may cause loss of tablet support. I learned it the hard way :)

Thanks, and greetings.

---

### Post by isul on 2013-04-23
Hello iam newbe in ubuntu. I have the Same problem. I cannot draw with my Genius i608X. I have compiled Wizardpen ([http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_WizardPen](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_WizardPen)). But it is still not working.

I am using kernel 3.2.0-40-generic-pae. do i should up grade my kernel to 3.5 generic-lts-quantal and Change xorg tobe xserver-xorg-lts-quantal? ([http://askubuntu.com/questions/257617/how-can-i-upgrade-the-ubuntu-12-04-2-kernel-to-3-5-0-23](http://askubuntu.com/questions/257617/how-can-i-upgrade-the-ubuntu-12-04-2-kernel-to-3-5-0-23)). Please help me. Sorry my english is so bad :).

---

