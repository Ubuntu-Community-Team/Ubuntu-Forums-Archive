---
title: "Audio cuts in and out (Breezy)"
date: 2006-02-11
forum: Multimedia &amp; Video
---

### Post by GrantB on 2006-02-11
Hi all,

I have Breezy installed on my laptop, and it's not uncommon for sound to suddenly cut out.  If I fiddle with the volume controls, sometimes it will come back, sometimes it won't.  If I shut down the current player (say, mplayer) and open another (say, xmms), then sometimes the audio will come back.  Usually when it starts happening, I'm playing movie files (though maybe that's my impression because I don't often play audio-only files).

Some days I won't have this problem at all, sometimes it'll mess with me all day.  I tried Googling for an answer, but either my problem is unique or I'm not choosing the right search terms.

Does this sound like a software or driver issue?  Or perhaps a hardware problem?

According to the volume control tool, my sound device is "Intel 82801DB-ICH4".

Output of "cat /proc/asound/cards" is:
0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                     Intel 82801DB-ICH4 with VIA1612A at 0xffeff800, irq 9

Output of "aplay -l" is:
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Thanks for any help you can give
-Grant

---

### Post by FarEast on 2006-02-12
Hi,

Visit the link below(I am not sure if it helps, though).  
[https://bugzilla.ubuntu.com/show_bug.cgi?id=10376#c1](https://bugzilla.ubuntu.com/show_bug.cgi?id=10376#c1)

---

### Post by GrantB on 2006-02-12
No, that does not look applicable.

When I observe it, I'll be watching a video, and maybe 10 seconds into it the sound will just *stop*.  If I open Volume Control and play with sliders, it might suddenly come back after fiddling for a few seconds, but it also might not.

---

### Post by FarEast on 2006-02-13
> I'll be watching a video, and maybe 10 seconds into it the sound will
> just *stop*.

I am not sure if it has something to do with the problem with you...
Today I had a similar problem.  When I tried to listen to a sound file(ogg)
on a web by clicking it, 'totem plug-in' began to play it and the sound
stopped suddenly (maybe about 10 seconds from the beginning).
When I start totem and pass the URL of it, I do not have the problem.

I also found that the sound from totem is 'choppy' when esd is not running.

---

### Post by GrantB on 2006-02-13
I see it most often when using a web browser to view Google Video (I've observed it with both Opera and Mozilla), almost every time.  It doesn't happen as often using mplayer from the command-line, though it does happen.

Maybe it's file format/codec related?  I'm not even sure if that's possible.

---

### Post by wncben on 2006-02-13
It sounds like your buffer is not set up correctly.  Check out your /etc/esound/esd.conf  and your /etc/asound.conf files.  I had to change my esd.conf file, and make an asound.conf file from scratch (following a couple howto's and combining them.  My current setup is here[http://ubuntuforums.org/showthread.php?t=126975&page=6]("http://ubuntuforums.org/showthread.php?t=126975&page=6")
My current setup is in post 56, but the posts above it follow through some trouble shooting I went through, and also link to the original howtos' I used.
  Just a side note,  the howto's I used were from hoary, and it seemed that the folks thought breezy would fix the issue.  Obviously there is an improvement in breezy, which I hope will continue in dapper as the issue is not resolved yet.  I do not think that there will be an easy fix anytime soon, as there are so many different systems.  In the mean time I hope this helps.
Give it a try.  I have found, from what others have written, and my own observations through trial and error that having you buffer set wrong can make your sound cut in and out and sound choppy.

Hope it helps!
~Ol' Ben

---

