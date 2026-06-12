---
title: "How I fixed my audio problem"
date: 2006-06-09
forum: Multimedia &amp; Video
---

### Post by dcroxton on 2006-06-09
I was very disappointed when I upgraded to Dapper this week, because I lost all sound -- basically, it didn't recognize that I had any audio device.  I was about to post to this forum when I decided to give it one last try.  There was a promising post about user permissions, which actually was a problem I had with Breezy, but it didn't help this time.  I found a post that directed me to [this page]("https://wiki.ubuntu.com/HowToSetupSoundCards").  It turns out that it hadn't loaded the proper driver for my sound.

Finding out exactly what I was using was a little tricky, because the sound is built in to the motherboard, and all I could find in the manual was that it was AC'97.  I couldn't identify the sound chip by looking at the motherboard, so I googled a bit and found something that looked like it was right, but it didn't work.  To be honest, I don't recall how I figured out what the soundcard was, except that I knew the motherboard was using an Intel chipset and it turned out to be an intel sound chip.  The page [here]("http://www.icewalkers.com/Linux/Howto/BootPrompt-HOWTO-8.html") at least gave me the reference I needed to try my experiments.

The first link told me the rest of what I needed to know:  modprobe snd-intel8x0, then add the appropriate line to /etc/modules so that it would load each time.  I did have to play around with the mixer quite a bit to get things working.  I found it with all sorts of unusual default settings, and of course it's not a simple volume meter, but about 10 different volume meters, most of whose names meant nothing to me, so I just had to play around.

I hope this might help some of those having audio problems.  I've still got one lingering issue, which is that I can't adjust the volume using software -- the only thing that works is using the speaker knob.  The only setting I've found that affects output is "PCM," which has to be on for anything to work.  I've played around in three different mixers and adjusted every volume control I could find, but nothing changed the output sound in the slightest.

---

### Post by Sarisar on 2006-06-21
I was looking for solutions to my own audio problems and on another thread they mention that you may not be in the audio group (/etc/group)

[http://ubuntuforums.org/showthread.php?t=186788&highlight=soundcard+problems]("http://ubuntuforums.org/showthread.php?t=186788&highlight=soundcard+problems")

See if that helps :)

---

