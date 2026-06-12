---
title: "sound problem [works in debian]"
date: 2006-10-11
forum: Multimedia &amp; Video
---

### Post by Quintin Riis on 2006-10-11
I'm having some trouble getting sound working properly in an Ubuntu install.

This is with a Compaq iPAQ applicance computer.  The sound is integrated Intel i810.  There is a small builtin speaker which is meant to function as both PC Speaker and also for regular audio.

This works as expected under Debian, playing music files, video, etc and the builtin speaker outputs sound.

However, under Ubuntu, the speaker is only functioning as PC Speaker.  

Any ideas as to how to correct this issue?  I can post any config files, etc that would help.

---

### Post by Kateikyoushi on 2006-10-11
I had the same problem, turning line jack sense off in alsamixer solved it.

---

### Post by Quintin Riis on 2006-10-11
> **Kateikyoushi said:**
> I had the same problem, turning line jack sense off in alsamixer solved it.
Was this with an iPAQ computer?  Or another one with builtin speaker?  

I have already tried this and it did not resolve the issue.

---

### Post by Kateikyoushi on 2006-10-11
Not an ipaq but it has a built in speaker.
Sorry to hear still not works. :-k

---

### Post by Quintin Riis on 2006-10-11
Really frustrated at this issue.  I have many of these machines, and am considering getting a nice ubuntu setup going on them, then imaging it to other machines and selling them to people who need a cheap computer.

amixer 'Line Jack Sense' off is what you are recommmending, ja?  Didn't do it...

Confirm sound works fine since the system bell will make the PC Speaker BEEP and I can get audio through the 1/8" audio on front of the device.

---

### Post by fuxx123 on 2006-12-17
I have one of those IPAQs too and i got the front  PC speaker to work by:

[LIST=1]
[*]Double-clicking on the volume icon
[*]Select Edit--->Preferences
[*]Select "Master Mono"
[*]Unmute the Master Mono column

[/LIST]

Hope this helps!!

---

