---
title: "No sound, please help!"
date: 2006-02-11
forum: Multimedia &amp; Video
---

### Post by garton on 2006-02-11
I've just installed Kubuntu 5.10 (Breezy) AMD64 edition on a machine with a Sempron CPU and a Asus K8U-X board. When KDE starts, there is no sound and I get this message:

```
Sound server informational message:
Error while initializing the sound driver:
device /dev/dsp can't be opened (No such file or directory)
The sound server will continue, using the null output device.

```

I've searched through the forums, and googled, but I can't seem to find anything that relates enough to my particular problem.

Here's a few... things. Clearly, the onboard audio chip is visible to the kernel. (This is a Asus K8U-X board.)

```
frepe@lovin:~$ lspci -v |grep audio
0000:00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)
```

It seems to autoload the snd_intel8x0 module, which is *correct* for this chip. I've verified that by some googling. 

```
frepe@lovin:~$ lsmod | grep snd
snd_intel8x0           34816  0
snd_ac97_codec         87000  1 snd_intel8x0
snd_pcm_oss            51232  0
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                91020  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24200  1 snd_pcm
snd                    55784  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10912  1 snd
snd_page_alloc         11408  2 snd_intel8x0,snd_pcm



```

This I don't like one bit...

```
frepe@lovin:~$ cat /proc/asound/cards
--- no soundcards ---

```

There is no /dev/dsp file present. Nor are there any /dev/dsp1 or anything like that.

```
frepe@lovin:~$ ls -la /dev |grep dsp
frepe@lovin:~$              

```

There a /dev/snd directory though, but it doesn't contain anything interesting.

```
frepe@lovin:~$ ls -la /dev/snd
total 0
drwxr-xr-x   2 root root        0 2006-02-11 12:41 .
drwxr-xr-x  12 root root        0 2006-02-11 12:42 ..
crw-rw----   1 root audio 116, 33 2006-02-11 12:41 timer

```

Also, there's this thing from dmesg that looks fishy...

```
frepe@lovin:~$ dmesg |grep AC\'97
[  163.521905] AC'97 0 does not respond - RESET

```

So... any suggestions? I've searched through a lot of forums and googling without finding anything really useful.

Thanks in advance!

---

### Post by garton on 2006-02-11
I just put an old SB Live! card in the box, and sound worked right away. This must be an issue with the onboard devices of the K8U-X mobo.

In fact, it's not just the onboard sound that doesn't work. The onboard NIC does nothing either. I don't like this mobo one bit.

---

### Post by brucetan on 2006-02-11
dear garton,

I am having problem with SB Live on ubuntu Breezy.  You seem to get it work!   What module did you use?  was it "snd-emu10k1" module?

---

### Post by garton on 2006-02-11
It seems so. Here's what modules got loaded when I inserted the SB Live card:

frepe@lovin:~$ lsmod|grep snd
snd_emu10k1_synth       7680  0
snd_emux_synth         35072  1 snd_emu10k1_synth
snd_seq_virmidi         7808  1 snd_emux_synth
snd_seq_midi_emul       7168  1 snd_emux_synth
snd_seq_dummy           4484  0
snd_seq_oss            32128  0
snd_seq_midi            9920  0
snd_seq_midi_event      8064  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                52032  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1           109476  2 snd_emu10k1_synth
snd_rawmidi            27040  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_seq_device          9488  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_util_mem            5376  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10784  2 snd_emux_synth,snd_emu10k1
snd_intel8x0           34816  0
snd_ac97_codec         87000  2 snd_emu10k1,snd_intel8x0
snd_pcm_oss            51232  0
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                91020  4 snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24200  3 snd_seq,snd_emu10k1,snd_pcm
snd                    55784  16 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_seq_device,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10912  1 snd
snd_page_alloc         11408  3 snd_emu10k1,snd_intel8x0,snd_pcm

---

### Post by garton on 2006-02-11
[QUOTE=garton]It seems so. Here's what modules got loaded when I inserted the SB Live card:

```
frepe@lovin:~$ lsmod|grep snd
snd_emu10k1_synth       7680  0
snd_emux_synth         35072  1 snd_emu10k1_synth
snd_seq_virmidi         7808  1 snd_emux_synth
snd_seq_midi_emul       7168  1 snd_emux_synth
snd_seq_dummy           4484  0
snd_seq_oss            32128  0
snd_seq_midi            9920  0
snd_seq_midi_event      8064  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                52032  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1           109476  2 snd_emu10k1_synth
snd_rawmidi            27040  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_seq_device          9488  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_util_mem            5376  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10784  2 snd_emux_synth,snd_emu10k1
snd_intel8x0           34816  0
snd_ac97_codec         87000  2 snd_emu10k1,snd_intel8x0
snd_pcm_oss            51232  0
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                91020  4 snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24200  3 snd_seq,snd_emu10k1,snd_pcm
snd                    55784  16 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_seq_device,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10912  1 snd
snd_page_alloc         11408  3 snd_emu10k1,snd_intel8x0,snd_pcm[/QUOTE]

```

---

### Post by brucetan on 2006-02-11
many thanks.  Is your SB Live card's model = CT4730?

---

### Post by garton on 2006-02-11
I don't know. Where does it say?

---

### Post by brucetan on 2006-02-12
i got my one on the back of the card.

---

### Post by FarEast on 2006-02-12
Hi brucetan,
I hope you will read my reply :).
[http://ubuntuforums.org/showpost.php?p=723341&postcount=22](http://ubuntuforums.org/showpost.php?p=723341&postcount=22)

---

### Post by brucetan on 2006-02-13
dear fareast, many thanks.

Garton, with fareast's help I got my SB Live working in full now. You may like to reference to [http://ubuntuforums.org/showthread.php?t=126975&page=5]("http://ubuntuforums.org/showthread.php?t=126975&page=5")

---

### Post by ekalin on 2006-03-12
See

[http://www.ubuntuforums.org/showthread.php?p=817147#post817147](http://www.ubuntuforums.org/showthread.php?p=817147#post817147)

for a solution to make the ALI 5455 card work with ALSA.

---

