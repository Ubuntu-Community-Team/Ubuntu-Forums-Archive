---
title: "PulseAudio Confusion ..."
date: 2008-07-10
forum: Mythbuntu
---

### Post by Lindsay.Mathieson on 2008-07-10
I'm confused as to the status of PulseAudio and Myth in Mythbuntu 8.04 :(

My understanding is that PulseAudio is the default sound server on mythbuntu 8.04? is this correct? ALSA is setup with a pulse plugin that routes it through the pulseaudio server?

How about MythTV? at the moment I have it using ALSA:surround51, should I be using ALSA:pulse?

Thanks - Lindsay

---

### Post by superm1 on 2008-07-10
> **Lindsay.Mathieson said:**
> I'm confused as to the status of PulseAudio and Myth in Mythbuntu 8.04 :(

My understanding is that PulseAudio is the default sound server on mythbuntu 8.04? is this correct? ALSA is setup with a pulse plugin that routes it through the pulseaudio server?

How about MythTV? at the moment I have it using ALSA:surround51, should I be using ALSA:pulse?

Thanks - Lindsay
Hi Lindsay:
Mythbuntu (installed from CD proper) doesn't include Pulseaudio.  If you "add" onto Ubuntu you will be using pulseaudio, and might consider setting ALSA:pulse

---

### Post by Lindsay.Mathieson on 2008-07-10
> **superm1 said:**
> Hi Lindsay:
Mythbuntu (installed from CD proper) doesn't include Pulseaudio.  If you "add" onto Ubuntu you will be using pulseaudio, and might consider setting ALSA:pulse

Thanks, Interesting. I have a desktop kubuntu where IO've done exactly that, I might test out myth and PulseAudio with that.

I have a DVD with AC3 6 channel that crashes Myth in 5.1 mode, I'm hoping pulse will fix that.

---

### Post by pnauta on 2008-08-23
> **Lindsay.Mathieson said:**
> Thanks, Interesting. I have a desktop kubuntu where IO've done exactly that, I might test out myth and PulseAudio with that.

I have a DVD with AC3 6 channel that crashes Myth in 5.1 mode, I'm hoping pulse will fix that.

Did you ever get it working with Pulseaudio?

---

### Post by Lindsay.Mathieson on 2008-08-23
> **pnauta said:**
> Did you ever get it working with Pulseaudio?

yes and no, I got PulseAudo working under KDE 4.1 quite well and various apps using it -mplayer, Amarok and MythTV.

However 6 Channel audio from the "I Am Legend" dvd still killed mythfrontend.

---

### Post by pnauta on 2008-08-23
Thanks.  I got everything working EXCEPT mythmusic which is still not working at all, by changing the settings to ALSA:pulse and changing the ~/.asound.rc to

> pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

---

### Post by Lindsay.Mathieson on 2008-08-23
did MythMusic ever work?

Also, do you run mythfrontend as the user associated with ~/.asound.rc

If you want to make the alsa pulse settings global edit /etc/asound.conf. Mine has the following:

```
pcm.pulse
{
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

```

---

### Post by pnauta on 2008-08-24
Oh yes, everything worked just fine until I started adding other pachages to connect our new Yamaha keyboard to it :(

I will try the global edit and see if that helps.

So , the current state of affairs is that only MythMusic doesn't work, even when using ALSA:pulse.

---

### Post by pnauta on 2008-08-25
Just to let you know that my MythMusic is working again.  I have entered ALSA:hw:0,0 into MythMusic and it now plays again.  I'm not happy about this setup (is hardware dependent) but it has to do for now.

---

### Post by Lindsay.Mathieson on 2008-08-25
> **pnauta said:**
> Just to let you know that my MythMusic is working again.  I have entered ALSA:hw:0,0 into MythMusic and it now plays again.  I'm not happy about this setup (is hardware dependent) but it has to do for now.

Good to know I suppose :)

I was going to suggest you test ALSA:pulse with MythMusic (which would presumably fail) and post the mythfrontend.log here.

---

### Post by pnauta on 2008-08-25
Yes, that failed (already tried that on saturday):
> 2008-08-23 11:03:17.748 Opening audio device 'pulse'. ch 2(2) sr 48000
2008-08-23 11:03:17.748 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL pulse
2008-08-23 11:03:17.768 AudioOutput Warning: Mixer attach error -2: No such file
 or directory


---

### Post by Lindsay.Mathieson on 2008-08-25
Are you using S/PDIF output?

---

### Post by pnauta on 2008-08-25
Yes,

I constructed an optical SPDIF bracket and connected it to the SPDIF header on the motherboard.  Works like a charm, I use only that connection to my receiver.

---

### Post by Lindsay.Mathieson on 2008-08-25
Ah, that might be part of the problem. I presume you have Myth pass through to SPDIF activated, not sure how well works with pulse or whether you should be doing it differently. Might be a good idea to take it to the mythtv list.

---

### Post by pnauta on 2008-08-25
The problem is: only MythMusic didn't work before I entered ALSA:hw:0,0 into MythMusic.  Before that, it was ALSA:pulse and before PulseAudio entered the equation, it was sufficient to set it to ALSA:default.

---

