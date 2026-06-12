---
title: "Gah, muted (again)."
date: 2010-07-29
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by x-shaney-x on 2010-07-29
This was my main bugbear in my lucid install, in fact the main reason I am now using maverick as my main.

The sound being randomly muted or volume icon not matching the slider etc.
I have avoided it so far in maverick but from today it is now every boot up.

Yes I am aware it's alpha etc and yes I am aware there is a so-called fix but I am wondering if anyone knows what the deep down problem causing this is so I know what to keep an eye on?

---

### Post by Universal344 on 2010-07-29
This probably isn't the best solution, but when I had sound muting issues, I found removing pulse audio and falling back to alsa gave me sound back.

---

### Post by x-shaney-x on 2010-07-29
Not keen on doing that.
Sound works perfectly everywhere when it isn't muted.
This was a problem before lucid's release and was never fixed.  I just hope it's fixed by maverick's release.

---

### Post by cariboo on 2010-07-29
There is an easy fix [here]("http://ubuntuforums.org/showpost.php?p=9349048&postcount=10") that takes a lot less time than removing pulse.

---

### Post by x-shaney-x on 2010-07-29
Yes I'm aware of the fix (or should I say workaround) which is ok for my lucid install but I don't think applying workarounds in a dev release is such a good idea because I can't keep track of whether things are properly being fixed or not.
Or is this something that is one of those things that never gets fixed because it works for many?
I know people have been reporting muted sound on startup since before karmic.

---

### Post by VMC on 2010-07-29
> **x-shaney-x said:**
> Yes I'm aware of the fix (or should I say workaround) which is ok for my lucid install but I don't think applying workarounds in a dev release is such a good idea because I can't keep track of whether things are properly being fixed or not.
Or is this something that is one of those things that never gets fixed because it works for many?
I know people have been reporting muted sound on startup since before karmic.

For me that work around works best. I zsync my Maverick iso's and install fresh instead of updates. That way I can test ubiquity and the install process each time. I do updates from time to time just to test that as well. 

So the muted sound work around comes around each and every time I  re-install Maverick.

---

### Post by x-shaney-x on 2010-07-29
Hmm, just because I am getting fed up of sorting sound every boot I tried the fix and it isn't working in maverick for me

---

### Post by cariboo on 2010-07-29
The work around saves the sound state on shutdown, if the sound is muted on shutdown it will be muted on startup. Make sure the sound is unmuted when you shutdown.

---

### Post by x-shaney-x on 2010-07-29
Ahh yes of course.  Seems to be working again so far

---

### Post by x-shaney-x on 2010-07-29
Nope, not a fix at all on a multi-user system it seems.

Example:

User 1 has sound set to halfway then logs out.
User 2 logs in and decides to have sound muted, finishes session and reboots.
User 1 later decided to use comp again, boots up, logs in and sound is muted.

This was the problem in lucid and still in maverick.

---

### Post by thonuz on 2010-07-29
Also what works for me is to check in System: Preferences: Sound: 
Hardware tab and Output tab, I have 2 devices and have muting issues depending upon if I use external speakers or the laptops internal. Also my sound preferences applet is gone on every reboot.
I had to change devices and reboot to get any internal sound. At least that was the quick way. 
--Just an additional note. I can no longer keep the sound preferences in the task bar. All I get is crash Icon coming back......

---

### Post by mc4man on 2010-07-29
You should post up your setup - laptop, desktop, what output you're using, speaker setup (external volume control?

You should be able to fashion an additional workaround for your scenario without to much problem.

If you happen have external pc speakers then probably shouldn't even be using the gnome-volume-control applet anyway - it behaves incorrectly. (that would resolve your secondary issue

---

### Post by x-shaney-x on 2010-07-29
It's an HP G62-105SA Core i3 Laptop

According to lshw:
5 Series/3400 Series Chipset High Definition Audio using HDA-Intel
And according to the product info page it has Aztec Lansing speakers.

Everything in sound preferences is default - Analog Stereo Duplex for the hardware tab and Analog Speakers for the output.
As mentioned before I have exactly the same problems in Lucid.

This laptop is pretty new and I was also using a HP desktop computer just before which also gave me exactly the same problems on both lucid and maverick.

Finally, the missus has a Dell laptop which yet again has exactly the same muting problem.

---

### Post by thonuz on 2010-07-30
Did you under Preferences Sound: look for 2 devices
also under Output  is Internal or HDMI

Changing these always works for me. 
HDMI kills my internal sound on core i5.Try playing with these settings,
Maybe reboot even--happened to me

---

### Post by mc4man on 2010-07-30
> User 2 logs in and decides to have sound [COLOR="Blue"]muted[/COLOR], finishes session and reboots.

if 'user whoever' is actually muting (mute all) then offhand don't see any way to unmute at log in or boot up.

if they're turning the level down to 0 then you can restore the levels to whatever your normal is with a small start up script (pcm will be 0dB, master at  -X.XXdB

---

### Post by x-shaney-x on 2010-07-30
@ thonuz

There are several devices listed but if I select ANYTHING other than the default setting I get no sound on next boot (NOT muted, just no sound).

@ mc4man

I don't think a user should have to run a script or actually do anything to get their sound working just because of how another user wants their volume.
I think this is a serious problem.

There ARE existing bug reports for this but like I've said before, these have being going back to before karmic so I'm not holding out much hope of this getting fixed for maverick.

---

### Post by ronacc on 2010-07-30
I agree with x-shaney-x  , although i run a single user box and hence haven't run into this , it does seem stupid to have a multiuser system that does not honor each users personal settings . After all it doesn't use Bob's passwords for Jenny's browser logins  ( I hope) .

---

