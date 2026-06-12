---
title: "No Sound after standby"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by Beliar on 2007-04-28
Hello,
Standby works for me, but when the system wakes up again, I have no sound.
I tried to manually restart the service alsa-utils and I double checked the sound channels, none muted. I put them to maximum sound and muted and unmuted them, no sound.
Restarting X and logging in again wouldnt help either.
Only restarting helps.

Anyone else experiencing this, is there any solution??

FYI, I have an Asus A6va Notebook with some Realtek (880) sound codec (Intel HDA). Sound works neither with headphones nor with laptop speakers after waking up. Works perfect normally, I'm hearing music right ATM. :guitar: 

TIA,
greets, Beliar

---

### Post by mpgarate on 2008-03-13
same problem on vostro 1400

---

### Post by Anthony M on 2008-04-11
Same problem with Realtek ALC888

---

### Post by rocketman768 on 2008-04-11
> **Beliar said:**
> Hello,
Standby works for me, but when the system wakes up again, I have no sound.
I tried to manually restart the service alsa-utils and I double checked the sound channels, none muted. I put them to maximum sound and muted and unmuted them, no sound.
Restarting X and logging in again wouldnt help either.
Only restarting helps.

Anyone else experiencing this, is there any solution??

FYI, I have an Asus A6va Notebook with some Realtek (880) sound codec (Intel HDA). Sound works neither with headphones nor with laptop speakers after waking up. Works perfect normally, I'm hearing music right ATM. :guitar: 

TIA,
greets, Beliar

It's probably a buggy audio driver that doesn't like to be suspended. What you usually do in this case is "sudo gedit /etc/default/acpi-support" and look for the line that says

```

MODULES=""

```

and stick your audio driver between the quotes. For mine, the driver is emu10k2. If you don't know what yours is, try "lsmod | grep snd" and look through the output. What the MODULES thing does is removes those drivers before suspend, and reloads them afterwards.

---

### Post by Anthony M on 2008-04-11
Here is the output of ```
lsmod | grep snd
```

```
anthony@anthony-desktop:~$ lsmod|grep snd
snd_hda_intel         344088  4 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd

```

Which driver do I use to put in the modules line?

---

### Post by rocketman768 on 2008-04-13
You probably want to use snd_hda_intel.

---

### Post by Anthony M on 2008-04-13
> **rocketman768 said:**
> You probably want to use snd_hda_intel.

Even though by computer has Nvidia components?

---

### Post by rocketman768 on 2008-04-13
> **Anthony M said:**
> Even though by computer has Nvidia components?

Your lsmod didn't show any Nvidia sound stuff. Just put it in there and try it. It's not going to hurt anything.

I mean, you can try "lspci | grep -i audio" and you should see something like "Audio Device: Intel Corporation..." if you need verification.

---

### Post by hhpeter on 2008-05-03
> **rocketman768 said:**
> It's probably a buggy audio driver that doesn't like to be suspended. What you usually do in this case is "sudo gedit /etc/default/acpi-support" and look for the line that says

```

MODULES=""

```

and stick your audio driver between the quotes. For mine, the driver is emu10k2. If you don't know what yours is, try "lsmod | grep snd" and look through the output. What the MODULES thing does is removes those drivers before suspend, and reloads them afterwards.

That did not work for me:(:(:(
here is what I get with 

```
lsmod | grep snd
```

```
peter@asus-s96s:~$ lsmod | grep snd
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
```

I put snd_hda_intel in MODULES inside acpi-support file but sound is not working after suspend....any other suggestions?

---

### Post by bmdavis on 2008-05-15
Putting snd_hda_intel  in the MODULES=""  worked for me!  

Thanks so much.

Brian
Dell Inspiron 6400
Hardy Heron

---

