---
title: "Digital sound dies / comes back irregularly with Creative SB Live 5.1 SPDIF/IEC958"
date: 2007-12-03
forum: Mythbuntu
---

### Post by kruel on 2007-12-03
For reference, I am running Mythbuntu 7.10 (All the most recent updates)

This weekend I decided to finally try and get SPDIF/IEC958 output working on my HTPC.

I am using a Creative Labs SB Live! 5.1 card with a 3mm Coaxial SPDIF out.

I hooked it up to my receiver via a 3mm Mono to Digital Coax cable. So far so good.

I tested it by playing a DTS encoded video using : 

```
 mplayer -ao alsa:device=spdif -ac hwdts file.vob
```

And it worked, DTS light came on, sound was great.  I was amazed that it worked, and happy.  Walked away, came back 15 mins later.  Tried the same file... No sound, but the DTS light came on??

So the receiver is detecting a DTS signal, just nothing is being transmitted on it.  I checked all the mixer settings I could find.  Restarted the machine, and it worked - then died - then worked (this time, without a reboot).

I read a little info about the SB Live! Digital output voltage being 5.0v and receivers using 0.5v , so I passed the Coax to a Coax/Optical converter.  Sound worked fine, then died - again.  Same problem, so that rules out the receiver.

**EDIT**  I should note, that I plugged a DVD player into the same audio input on the receiver and it worked repeatedly with no problems over the course of a day. So I am confident that it is not a receiver issue.

Is there maybe some muting option I missed?  I checked alsamixer, xfce4-mixer and amixer, none of the settings appear different.  I am going to check the output of ```
/var/lib/alsa/asound.state
``` when I get home to see if there is a difference when it is working vs. not working.

In the mean time, does anyone have any ideas?

Thank you!

---

### Post by superm1 on 2007-12-03
I'm not going to say this solution will necessarily work for you, but it works for me.

~$ cat .asoundrc
Here is the ~/.asoundrc i'm using
```
pcm.!default {
        type plug
        slave {
                rate 48000
                pcm "spdif"
        }
}
```

It forces all audio out spdif all the time.  Seems to work consistently and in all apps i've tried.

---

### Post by mvoorberg on 2009-01-15
This solution worked for me to get digital audio working under Live TV, but I still haven't seen any DTS from DVD's etc...

I'm thrilled to have gotten this far but as everything, I'll keep tinkering with it.  ;)

---

