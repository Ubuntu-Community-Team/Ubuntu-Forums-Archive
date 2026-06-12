---
title: "more Intel HD audio problems"
date: 2006-08-05
forum: Multimedia &amp; Video
---

### Post by Akkrone on 2006-08-05
Just recently installed 6.06 and have tried many, many things I've found the in the forums here and around the net to try and get the audio working in my Ubuntu install. 

Alienware Area-51 M7700 (Clevo D900t), Intel HD Audio (ALC880) 

I currently have ALSA 1.0.12r2 installed, but I've tried what came with Ubuntu and the latest stable release of ALSA (1.0.11) with no luck. I've also tried Realtek's linux drivers with no luck. It appears that the modules snd-hda-intel and snd-hda-codec are installing with no errors. I have two mixers available in Gnome HDA Intel (ALSA mixer) and Realtek ALC880 (oss mixer) - nothing muted, all volumes up, no sound at all. if I do aplay -l i get:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

if I do aplay by itslef, it comes back with errors:

ALSA lib pcm_direct.c:867:(snd_pcm_direct_initialize_slave) snd_pcm_hw_params_any failed
ALSA lib pcm_dmix.c:876:(snd_pcm_dmix_open) unable to initialize slave
aplay: main:550: audio open error: Invalid argument

Any help would be greatly appriciated, I'm dying without my music. :)

---

### Post by Akkrone on 2006-08-08
No ideas at all?

---

### Post by sddfdds on 2006-11-30
I am having this problem as well.  Please does anyone have any idea how to fix it?

---

### Post by pillu on 2006-11-30
I don't know if this is of any help, but the sound was not working on my new lenovo laptop with the intel HD card. To get it working I needed to add the line

options snd-hda-intel model=laptop-eapd

to my /etc/modprobe.d/options file. It might be worth a try if you haven't done so already.

---

### Post by ndori on 2006-12-02
> **pillu said:**
> I don't know if this is of any help, but the sound was not working on my new lenovo laptop with the intel HD card. To get it working I needed to add the line

options snd-hda-intel model=laptop-eapd

to my /etc/modprobe.d/options file. It might be worth a try if you haven't done so already.

Hi pillu,
I just bought a new Lenovo 3000 C200 and my sound doesn't work, did the step you took fixed the problam?
Thanx.

---

### Post by sddfdds on 2006-12-02
I don't think I can attempt this unfortunately.  I am running the LiveCD (so that I didn't run into a problem just like this if I installed).

I tried rmmod snd_hda_intel (so I could then edit the file and modprobe again) but I get the error ERROR: Module snd_hda_intel is in use.

My laptop might just not be destined for a linux install :/

---

### Post by DougieFresh4U on 2006-12-02
I have been dealing with this Intel sound issue for days.!! Actually I am begining to be a pain in the ^ss about it as NO ONE seems to even come close to solving it. My thread gets no response and **Moderater** even **Locked** one of my threads as I was being impatiant as it was called

---

### Post by xp_newbie on 2006-12-07
Here is what I did to enable sound on my Lenovo 3000 N100:

> At the command prompt typed: **alsamixer**
 > received a cursors-like GUI with sliders as follows:
   Playback: Headphone, PCM, Front, Surround*, Center*, LFE*, Line*, CD, 
             Mic*, IEC958**, PC Speaker*, Aux*, Mono*, Stereo Downmix**
   Capture:  Line, CD, Mic, Phone, Aux, Mono, Capture!, Mix
   (card: HDA Intel, chip: AD1986A)

*  = Off, but sliders responding to up/down arrow keys,
** = Off, no full slider
!  = The only "Capture" control that has slider

Unmuting various combination (including *nothing* muted) did not help. 
Then:
  > sudo gedit /etc/modprobe.d/options
  > Add the line:
     options snd-hda-intel model=laptop-eapd
  > Reboot.


HTH,
Alex

P.S. When you plug your headphones to the headphones jack, it wouldn't disconnect the speakers. It was a known problem 5 months ago, but I have no idea whether any fix to it has been found. I will post a separate request for help about this.

---

### Post by biovore on 2006-12-09
Yeah, I have a dell e1705 and I have the same problem when you come out of a low power state, (hibernation, or suppend) the sound card dosn't get setup correctly. I think its due to something with ACPI.  Basicly I wouldn't expect this to get fixed any time soon.  So the work around for now is,  don't put your computer into hibernation or suppend modes.  (The if it hurts, don't do it approach)  Not the best news, but I guess this what we will have to do until someone figures it out..  Oh and by the way.. FreeBSD and OpenBSD also do the same thing..  So it isn't just linux :-P  Must be something to do with the documentation intel provides for the sound card might not be right.

---

