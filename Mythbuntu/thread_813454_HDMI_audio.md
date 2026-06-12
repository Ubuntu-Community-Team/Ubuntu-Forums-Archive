---
title: "HDMI audio"
date: 2008-05-30
forum: Mythbuntu
---

### Post by dsbw on 2008-05-30
So, I have two 8.04 boxes (one with an Nvidia-based K9NGM3 mobo and one with an ATI-based MA69GM mobo) that I'm trying to get HDMI audio working on. By upgrading the ALSA and ATI drivers on the ATI machine, I was able to see the iec958 switch, but toggling it produced no audio output.

The Nvidia machined showed the audio card but the switch didn't show in alsamixer until I added to my options file the line:

```
options snd-hda-intel index=0 model=6stack-dell
```

This based on advice from someone using the same mobo (I've tried with and without the index). 

So, now the iec958 shows up on the NVidia machine, *too*, but doesn't actually make any sound on the TV speakers *too*.

I've tried different settings for "model", and so far all have either been worse (not showing the iec958) or the same (no sound).

At this point, I'm looking at:

*) Compiling the latest RealTek drivers. They're from the 15th.
*) Switching to OSS. Dunno what the implications of that are.

Any other possibilities that anyone can see?

---

### Post by Trollslayer on 2008-05-31
Silly question - is the output muted? I found on my Abit I-F90HD it was muted by default.

---

### Post by superm1 on 2008-05-31
> **dsbw said:**
> So, I have two 8.04 boxes (one with an Nvidia-based K9NGM3 mobo and one with an ATI-based MA69GM mobo) that I'm trying to get HDMI audio working on. By upgrading the ALSA and ATI drivers on the ATI machine, I was able to see the iec958 switch, but toggling it produced no audio output.

The Nvidia machined showed the audio card but the switch didn't show in alsamixer until I added to my options file the line:

```
options snd-hda-intel index=0 model=6stack-dell
```This based on advice from someone using the same mobo (I've tried with and without the index). 

So, now the iec958 shows up on the NVidia machine, *too*, but doesn't actually make any sound on the TV speakers *too*.

I've tried different settings for "model", and so far all have either been worse (not showing the iec958) or the same (no sound).

At this point, I'm looking at:

*) Compiling the latest RealTek drivers. They're from the 15th.
*) Switching to OSS. Dunno what the implications of that are.

Any other possibilities that anyone can see?
You may need to switch to NVIDIA 173.14 or later.  They don't necessarily allow pass through HDMI audio from an iec958 pipe on earlier drivers.

---

### Post by dsbw on 2008-05-31
> **superm1 said:**
> You may need to switch to NVIDIA 173.14 or later.  They don't necessarily allow pass through HDMI audio from an iec958 pipe on earlier drivers.

Huh. I used EnvyNG, would that not get me the latest?

---

### Post by superm1 on 2008-05-31
> **dsbw said:**
> Huh. I used EnvyNG, would that not get me the latest?
Just check the version number.  Make sure that 173.14 or later is included with it.  If not, bug the Envy author to include the newer one :)

---

### Post by Dewey_Oxberger on 2008-05-31
If you get it working please post back what you had to do.  I have a similar NVidia based board and I've never been able to get it to go.

Alsa 1.0.16 was supposed to get it going.

I thought EnvyNG downloaded the latest driver...

---

### Post by dsbw on 2008-05-31
> **superm1 said:**
> Just check the version number.  Make sure that 173.14 or later is included with it.  If not, bug the Envy author to include the newer one :)

Huh. Looking at it, I see you have an option:

169.12
95.43.05
71.86.04

And 173.14 is the one at the site. Huh. That may have just answered my problem big time. Maybe that's the same problem with my ATI board.

I'm going to try to install these without Envy...

---

### Post by superm1 on 2008-06-01
> **dsbw said:**
> Huh. Looking at it, I see you have an option:

169.12
95.43.05
71.86.04

And 173.14 is the one at the site. Huh. That may have just answered my problem big time. Maybe that's the same problem with my ATI board.

I'm going to try to install these without Envy...
err i'd be careful doing that.  Installing them manually can end up being some trouble.  I say file a bug against envy to include the latest driver.  I"m not sure why there is the delay in getting it included, maybe testing or what not.

---

### Post by dsbw on 2008-06-01
> **superm1 said:**
> err i'd be careful doing that.  Installing them manually can end up being some trouble.  I say file a bug against envy to include the latest driver.  I"m not sure why there is the delay in getting it included, maybe testing or what not.

This is from the Envy wiki:

> Envy does not automatically update itself when new upstream drivers are released; but all that's required is to update the version of the driver in envy and set the new md5 of the installer.

Does that mean that it can easily take new Nvidia drivers? It's not as informative as it thinks it is.:)

---

### Post by dsbw on 2008-06-02
All right, I updated the NVidia driver. 

Then, on a clean install, I installed the newest NVidia driver using their instructions (worked fine) then ran the Alsa Update script. This trashed the video.

Huh.

So I tried again and did the Alsa update first *then* installed the new NVidia driver. I also made the changes to the options file to include the "options snd-hda-intel model=6stack" line.

Now I have the latest NVidia, the latest ALSA, and the iec958 un-muted.

And no HDMI audio. ](*,)

---

### Post by superm1 on 2008-06-02
> **dsbw said:**
> All right, I updated the NVidia driver. 

Then, on a clean install, I installed the newest NVidia driver using their instructions (worked fine) then ran the Alsa Update script. This trashed the video.

Huh.

So I tried again and did the Alsa update first *then* installed the new NVidia driver. I also made the changes to the options file to include the "options snd-hda-intel model=6stack" line.

Now I have the latest NVidia, the latest ALSA, and the iec958 un-muted.

And no HDMI audio. ](*,)
Be careful about passing particular model's to snd-hda-intel.  That information is read from the BIOS.  Only pass a model in the event that it is inaccurate what gets read from the BIOS.

---

### Post by dsbw on 2008-06-03
> **superm1 said:**
> Be careful about passing particular model's to snd-hda-intel.  That information is read from the BIOS.  Only pass a model in the event that it is inaccurate what gets read from the BIOS.

Auto didn't work; I got that setting from someone else using the same board successfully. Though only the S/PDIF out, not HDMI audio.

So...I'm stuck, it seems. I mean, I'm going to try updating the BIOS and, over time, doing some other stuff, but right now I don't know of anyone who actually has HDMI audio working at all on MythTV. (I think I've got the boxes going with S/PDIF but that's about it.)

The only other thing I can think of is: How do I encourage this to get working? Whom do I bribe or where do I contribute code do update MythTV?

---

