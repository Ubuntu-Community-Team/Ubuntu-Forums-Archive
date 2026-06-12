---
title: "Intel 915GM problem running projector and LCD display at same time"
date: 2006-10-19
forum: Multimedia &amp; Video
---

### Post by RobertKMoniot on 2006-10-19
I have a Dell Inspiron B130 with Intel 915GM/GMS/910GML
Express Graphics Controller.  Running Ubuntu 6.06 Dapper
with the 2.6.15.7 i686 kernel.  Xorg-x11 is up to date.
The Xorg.0.log is attached.

The problem occurs when I display video on a projector
while also displaying on the laptop's LCD screen at the
same time.  Getting a picture is OK: I have to set the
screen resolution to 1024x780 first, then use Fn+CRT/LCD
to activate the video output.  The projector image is
fine if I run in the mode that displays only on the
projector, but if I try to display on both at once, the
image from the projector has wavy lines (dynamically
moving) that make for very uncomfortable viewing.

This does not seem to be the projector's fault since
exactly the same behavior occurs with either an
NEC MT1065 or a Mitsubishi XD10U.  It is also not
intrinsically a problem with the Intel chip since
when I boot to Windows it runs both displays at
once just fine.

Anyone know how to tweak the driver so it will use a
video mode that the projector is happier with?

Bob

---

### Post by wieman01 on 2006-10-19
"xinerama" did the job for me...

[http://ubuntuforums.org/showthread.php?t=221908]("http://ubuntuforums.org/showthread.php?t=221908")

---

### Post by DarkN00b on 2006-10-19
You might check out i810switch in Synaptic. Here's the description:

[quote="synaptic"]Enables/disables video output to CRT/LCD on i810 video hardware
i810switch enables/disables the output to the CRT display and LCD,
depending on the i810 graphics controller hardware. Such hardware is found
on some laptops (eg, Sony Vaios, some Dell models, etc). Chipsets also
supported include i855, i830, i845.

This package includes the i810rotate script, which toggles the output
between three states: LCD only, LCD + CRT, and CRT only.[/quote]

It should work with your i915 also.

---

### Post by RobertKMoniot on 2006-10-19
Thanks for the suggestions, and the Xinerama works really neat, but
dual-head operation is not what I am looking for.

My need is to show what is on the laptop display (e.g. slides) to a roomful
of people, using a projector.  So I need to have the projector showing
the same thing that is on the laptop.  The problem is that when I do
this, the projector's image is not steady, but fine detail wiggles
around.  If I use the mode in which the laptop's display is dark while
the projector is displaying, the image is steady.  But then I have to
look at the projection screen while typing or using the mouse, which
is awkward.

---

### Post by RobertKMoniot on 2006-10-19
I did not try i810switch since it seems by the description to
do what the Fn+CRT/LCD key combo does.  Please correct me if
I am wrong.

---

### Post by wieman01 on 2006-10-19
> **RobertKMoniot said:**
> Thanks for the suggestions, and the Xinerama works really neat, but
dual-head operation is not what I am looking for.

"xinerama" can do both actually. You can configure it in such a way that you have the same screen both on laptop & projector. I think that's what you want to get around the "image not being steady" problem.

---

### Post by eitan on 2006-10-20
Is the solution presented here (of configuring xorg with xinerama and two screens) applicable in this situation:

 [a] laptop connected to running projector, booting
  laptop:  nothing detected by projector
 [b] fn+monitor key combination does nothing
 [c] sudo dpkg-reconfigure xserver-xorg while connected
  to projector does nothing

Does having beryl installed/running conflict with anything?

I'm running edgy eft on an hp laptop.

thanks, / eitan

---

### Post by wieman01 on 2006-10-20
> **eitan said:**
> Is the solution presented here (of configuring xorg with xinerama and two screens) applicable in this situation:

 [a] laptop connected to running projector, booting
  laptop:  nothing detected by projector
 [b] fn+monitor key combination does nothing
 [c] sudo dpkg-reconfigure xserver-xorg while connected
  to projector does nothing

Ok, I don't understand your question 100% but here are my answers:

a. Connecting a projector while both projector & PC are running, does not constitute a problem. You may have to restart X though.
b. "xinerama" does nothing about "fn + monitor key". Won't work.
c. You won't need "dpkg-reconfigure" at all.

---

### Post by DarkN00b on 2006-10-20
> **RobertKMoniot said:**
> I did not try i810switch since it seems by the description to
do what the Fn+CRT/LCD key combo does.  Please correct me if
I am wrong.

You are correct. I was under the impression that the Fn+CRT/LCD keys on your keyboard were not working properly. i810switch just enables them if they are not working.

---

### Post by eitan on 2006-10-20
> **wieman01 said:**
> Ok, I don't understand your question 100% but here are my answers:...



..oops sorry;  i inadvertantly replied to the wrong thread.  
i meant to reply to this one:
[http://ubuntuforums.org/showthread.php?t=221908](http://ubuntuforums.org/showthread.php?t=221908)

where you present a xorg configuration for mirroring.

i'm working on a fairly new laptop..one that i tested with a projector for the first time earlier today.  i couldn't get the projector to even detect a signal.  i tried all kinds of things, from rebooting my laptop to see if the signal would get picked up on bootup, to restarting X (ctrl+alt+backspace) to trying dpkg-reconfigure'ing xsever-xorg.

anyhow, i hope to try a new xorg.conf file, based on the one you present in the thread and am hoping to get this to work..wish me luck.  :-)

---

### Post by wieman01 on 2006-10-20
> **eitan said:**
> anyhow, i hope to try a new xorg.conf file, based on the one you present in the thread and am hoping to get this to work..wish me luck.  :-)
Yes, all the best. But post a message if you need assistance. This should not be much of a problem.

---

### Post by eitan on 2006-10-20
> **wieman01 said:**
> Yes, all the best. But post a message if you need assistance. This should not be much of a problem.

glad to hear it!  in the event i get stuck, you'll probably find another post on this thread.  thanks!

---

### Post by eitan on 2006-10-20
i've been doing a little more reading..stumbled across the i810 xorg man page .. [http://www.xfree86.org/current/i810.4.html#sect0](http://www.xfree86.org/current/i810.4.html#sect0)

i am curious, instead of defining two devices and two screens, and two monitors, and then defining one to be adjacent to the other, as you show.. it would seem 
that the following configuration might work as well?

 define a single device with these options:
   "MonitorLayout" "CRT,LFP"
   "Clone" "true"
   "DevicePresence" "true"

...

---

### Post by wieman01 on 2006-10-20
I think that would work as well. The drawback is - as far as I know - that both displays need to have the same resolution. So that's certainly no option in my case.

---

### Post by eitan on 2006-10-20
ok.  i finally got to spend some time with a projector.

i got a simple x.org config file to work with one screen definition, by using the Clone option.

i had to fall back to 1024x768, which is fine.  the main thing that bothers me is that i have a laptop that by default likes things wider (1280x800) and so my local display is stretched, which makes it look not so great.  but the projection is nice.

i tried the dual head setup, and got that to work too.  my problem with that is that it's not really designed for mirroring.  i can't see what i place on the workspace that the projector displays on my screen.

in a previous message you mentioned that xinerama can be configured to behave more like a mirroring solution.  i guess what i really need is a pointer to a good xinerama reference..

thanks for your help.

/ eitan

---

### Post by eitan on 2006-10-20
the other thing that bothers me a little with this setup is that i'd have to switch out two different xorg.conf's:  one for when i'm using a projector, and one when i'm not (so as to get the higher resolution)..

---

### Post by RobertKMoniot on 2006-10-20
OK, thanks for the further hints.

I first used the xinerama solution with the ServerLayout
Option Screen "External Screen" Relative "Internal Screen" 0 0

This cured the problem of the unsteady projected display.  However, the mouse cursor only appears on one of the two
displays.  This is actually a plus when projecting slides,
where the cursor is just a nuisance.  But I also use this
computer for classroom work where the class needs to see
the mouse cursor to see how things are done.

So I then tried eitan's suggestion of the "Clone" "true" option
in the Device section of a standard version of xorg.conf.
This achieves just what I want: a steady projected display
that is the same, including mouse cursor, as the laptop display.
I do not mind having to use the same resolution for both.  When
I am not using the projector I can swap config files to get
back to 1280x800.

Thanks to all for your help.

---

### Post by wieman01 on 2006-10-20
> **eitan said:**
> the other thing that bothers me a little with this setup is that i'd have to switch out two different xorg.conf's:  one for when i'm using a projector, and one when i'm not (so as to get the higher resolution)..
Not much you can do about that I am afraid...

---

### Post by wieman01 on 2006-10-20
> **eitan said:**
> i had to fall back to 1024x768, which is fine.  the main thing that bothers me is that i have a laptop that by default likes things wider (1280x800) and so my local display is stretched, which makes it look not so great.  but the projection is nice.
Yes, widescreen is a problem. Same here.
> **eitan said:**
> i tried the dual head setup, and got that to work too.  my problem with that is that it's not really designed for mirroring.  i can't see what i place on the workspace that the projector displays on my screen.
Yes, my fault. Without knowing your config your setup should be something like this:
> Screen 0 "Default Screen"
Screen 1 "External Screen" Relative "Default Screen" 0 1
_**OR:**_
> Screen "Default Screen"
Screen "External Screen" Relative "Default Screen"
Replace "Default Screen" with your Laptop screen & "External Screen" with your projector's.

---

### Post by wieman01 on 2006-10-20
> **RobertKMoniot said:**
> OK, thanks for the further hints.

I first used the xinerama solution with the ServerLayout
Option Screen "External Screen" Relative "Internal Screen" 0 0

This cured the problem of the unsteady projected display.  However, the mouse cursor only appears on one of the two
displays.  This is actually a plus when projecting slides,
where the cursor is just a nuisance.  But I also use this
computer for classroom work where the class needs to see
the mouse cursor to see how things are done.

So I then tried eitan's suggestion of the "Clone" "true" option
in the Device section of a standard version of xorg.conf.
This achieves just what I want: a steady projected display
that is the same, including mouse cursor, as the laptop display.
I do not mind having to use the same resolution for both.  When
I am not using the projector I can swap config files to get
back to 1280x800.

Thanks to all for your help.
"Clone" is the nicest solution in my opinion with the given restrictions.

---

### Post by nekr0z on 2007-02-20
I have the same problem on a laptop with 855GM. And I still think that this "clone" solution is not that good idea: you need to restart xorg after you plug the projector. This sucks. Just imagine: I'm at the conference ready to read a report using some slides. Another person is reading a report before me, and I don't have time to configure all after he goes off the stage, I need to get on the stage, plug in a projector and start on. So I need the slides prepared to start, and restarting xorg just makes me spend time on this AFTER I plug in the projector... No deal!

---

