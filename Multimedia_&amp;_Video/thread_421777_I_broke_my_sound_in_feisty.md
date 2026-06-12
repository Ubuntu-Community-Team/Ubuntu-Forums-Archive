---
title: "I broke my sound in feisty"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by kking on 2007-04-24
I installed Ubuntu Feisty on my new computer the other day, and for the most part things have gone pretty well.  Today I decided to try to fix one of the odd little things that needed to be taken care of.

Sound worked for me out of the install, but for some reason the volume control applet never worked.  It *appears* to work, but never changes the volume.

So I went into the volume control preferences, and here you choose the device and track to control.  The default was "CA0106 (Alsa mixer)" for the device and "IEC958 Center/LFE" for the track.  I didn't know what any of this meant, but figured I couldn't do any harm just trying the other options (after all, it's just volume control, right?).

I was playing some music so I could hear any changes.

None of the other tracks on this device did anything, so I tried the other device, "mixer00 (OSS Mixer)."  When I clicked on one of the tracks (can't recall which one), the audio stopped (though the music was still playing).

THAT sure wasn't the right option, so I switched back to one that still allowed sound to play...but it didn't.

I tried all the settings, including the default, and I now  have no sound at all.  I tried rebooting, that didn't change anything.

In the past my next step would be to reinstall the OS, but I want to figure out how to track this down and fix it without redoing everything.  I just don't know enough about how sound works in linux to know where to start.  It always has just worked for me.

Here's my setup:
Ubuntu Feisty (x86)
AMD Athlon X2 5200+
Asus M2N-SLI Deluxe mobo (nforce 570) (onboard audio is disabled)
SB Audigy SE

I'm figuring that my other hardware probably doesn't matter much, but if it does, let me know what info would help.

I'm not sure where to start.

---

### Post by El Viejo Lobo on 2007-04-24
Here is a link to the Wiki where you can learn to use sound control in Ubuntu: [http://alsa.opensrc.org/Alsamixer#NAME](http://alsa.opensrc.org/Alsamixer#NAME)
Ubuntu have a Terminal Audio Aontrol that more then likely is not configured
correctly. It drove mi crazy with my laptop's  microphone.
Go to the terminal and write the comand: "alsamixer" and you will see it in graphics.
I attached a screenshot of it.

---

### Post by kking on 2007-04-25
I ran that program, and raised the volume for every setting to 100% and I still have no sound.

My media player still shows that it's playing, but no sound is coming out anymore.  It's not just my media player, but it's a good constant source of sound for testing.

Thanks for the suggestion though!

Any other ideas? (anyone?)

---

### Post by El Viejo Lobo on 2007-04-25
kking, you can see how I resolved my my microphone problem. Things look like a bit loco with linux maybe we are too newbee yet.
[http://ubuntuforums.org/showthread.php?p=2510974#post2510974](http://ubuntuforums.org/showthread.php?p=2510974#post2510974)
[http://ubuntuforums.org/showthread.php?p=2527562#post2527562](http://ubuntuforums.org/showthread.php?p=2527562#post2527562)

I hope that you will find the way out of the problem soon.

---

### Post by kking on 2007-04-25
I'll take a look at those, but I don't believe that this has anything to do with a microphone.  I don't/haven't had one hooked up at all.

I'm stuck here and I am really hoping to avoid a complete reinstall of the OS.

Please help!

UPDATE:
So I played around in alsamixer some more and this time discovered something had become muted somehow.  As soon as I unmuted it, music started playing.

I was then able to figure out which setting I need the volume control applet to be on to control my volume, but it still acts funny.  As I turn the volume down, it really lowers quick!  The sound is completely turned down before I get down to 50% volume in the applet.

Anyone have any ideas on how to adjust this?

---

### Post by BrokenBrick on 2007-04-25
I have this same problem.  My sound was working just fine and then it suddenly stopped.  I think it might have been caused by my watching a movie in gxine on my TV with sound, while watching something else with no sound in VLC on my monitor.  I dunno why that would have killed it though.  I played around with the device setting as well, and still had no luck

---

### Post by kking on 2007-04-25
Well, if it's the same problem as mine, go into alsamixer, raise all the volumes, and press 'm' to make sure it's not muted.

Now it's just the sensitivity of the volume control that gets me.

---

