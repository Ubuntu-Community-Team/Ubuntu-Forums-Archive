---
title: "Realtek ALC861-VD no headphone sound"
date: 2007-07-14
forum: Multimedia &amp; Video
---

### Post by Anessen on 2007-07-14
Hey
I have been having problems getting my laptops audio to work properly. The laptop is a toshiba L30-10Y, with a Realtek ALC861-VD sound system.

I have recently reinstalled ubuntu (New hard disk). On my old install (7.04 still), I could not get the sound to work at all unless I installed a new Kernel from a link I found here (can't find it now). Using this new Kernel, I could get sound from each of Headphones and Speakers, without problems (some people saying they get both at once?)

But, since I was installing again, I tried to do a full update and see what happens (I like to have the most up to date software for security reasons). 

Now, the sound plays fine from the speakers, but I get nothing from the headphones.

My alsamixer does not work:
```
anessen@Attlee:~$ alsamixer

alsamixer: function snd_mixer_load failed: Invalid argument
```
ALSA used to work (sort of) before the updates. Even though I had no sound, the mixer would at least start.

My GNOME volume control lists my card as OSS (0: Realtek ALC861-VD OSS).

The volume control seems to work for the speakers, but I still get nothing from the headphones. It is strange that my ALSA stopped working after the updates. The sound tests in the Sounds control panel all seem to work, even when set to ALSA from Autodetect - but only from the speakers.

Any help would be greatly appreciated, I use this laptop for listening to music as well as general internet browsing.

---

### Post by Jadd on 2007-12-21
Same card, speakers are working, but headphones aren't. OSS 4 gave me a glimmer of hope (I ran oss-test).

---

### Post by stedevil on 2008-03-06
I have the same chip and all sound fully working. Check out this thread.

[http://ubuntuforums.org/showthread.php?p=4462175#post4462175](http://ubuntuforums.org/showthread.php?p=4462175#post4462175)

---

