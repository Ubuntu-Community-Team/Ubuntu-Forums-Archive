---
title: "Microphone Recording always muted"
date: 2008-11-16
forum: Multimedia Software
---

### Post by Dr.Suave on 2008-11-16
Hi - just upgraded from Gutsy to Ibex. However, after the upgrade I found that microphone capture is ALWAYS muted in the ALSA mixer. I click unmute, close the mixer, then open it again to find that the microphone is still muted. The mic does work in playback, however. It's really important that I get the microphone working, as I use Skype as my main means of communication...

I've tried switching from pulseaudio to ALSA, but I get the same problem...

Can anyone help? I'm happy to do a full reinstall if that's what it will take.

Wilf

---

### Post by Melindrea on 2008-11-16
I will be watching this thread, since that problem was one of the reasons that I downgraded back to Hardy on the laptop.

---

### Post by Dr.Suave on 2008-11-17
anyone have even the vaguest of ideas?

---

### Post by robertyou on 2008-11-17
Can you try to double-click on the volume icon in your system tray and go to "Preference". Check "Front Mic", "Front Mic Boost", "Microphone", and "Mic Boost".

Then you'll see those options you just checked on the panel.
After some tuning I got my mic working.

---

### Post by Dr.Suave on 2008-11-18
Thanks for the reply.

Funnily enough I can't find "Front Mic" or "Front Mic boost" anywhere... maybe because I've disabled pulse audio... (I used this method, because of the non-destructiveness... not that I know how to reverse it: [http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/](http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/))  

I'm including a screenshot of my eternally muted capture mixer and the mixer options.

Maybe I should try a clean install, then look for the front mic options.

The strange thing is that I never had any trouble with this in Gutsy.

---

### Post by Dr.Suave on 2008-11-18
Something very strange just happened - I decided I'd give up and see if a clean reinstall would help. And with my system about to be wiped, I was free to mess around with Ubuntu without fear of any real consequences. So I installed the latest KDE. And I opened up Kmix, and set microphone to capture.

And the microphone works in KDE! It seems to be a GNOME only thing - never actually submitted a bug to launchpad, but I'll funk on over there and put this in. If if you can submit bugs for Gnome to launchpad - not sure how the whole thing works.

Anyway, if anyone has any ideas on how to fix this bug in Gnome, please let me know - having to change platforms is a bit of a pain, I quite like gnome, even though I know KDE is supposed to have more functionality, it reminds me of Windows too much!

Thanks, 

Wilf

---

### Post by heisters on 2008-12-04
This sounds a lot like my problem on a Thinkpad T61. On a lark, I installed kmix. Using it, I was able to enable the "Capture" channel, which got the mic working. I wasn't able to do this with either gnome-volume-settings or alsamixer. Looking at the settings now, alsamixer -V all looks just the same as before. So it seems like kmix has access to some setting that the others don't, but that is nonetheless crucial. Recording seems to still be working even though I've quit kmix now.

There's a bug here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/299642](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/299642)

---

