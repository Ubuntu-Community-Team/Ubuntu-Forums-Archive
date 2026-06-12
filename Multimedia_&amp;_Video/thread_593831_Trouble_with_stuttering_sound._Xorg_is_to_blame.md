---
title: "Trouble with stuttering sound. Xorg is to blame?"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by dxlr8r on 2007-10-27
This is probably the strangest thing ever. I have stuttering in my sound. I tried it all to make it not stutter, since it worked in Windows. By luck I tried the old Ubuntu 6.06.1 and there it worked! 

So... I thought it's kernel 2.6.15 was the magic thing, so I copied that one (and it's modules and so on, updated grub...) and hoped for the best. But NOO. It booted alright and everything was nice, but still the same. 

I've tried it all as I said. Mixing alot i alsamixer, installed OSS (so it's not alsa), tried a seperate audiocard (still stuttering). The only thing that seperated this install and the 6.06.1 in term that has anything to say is Xorg 7.2.0 vs 7.0.0. 

I thought that was insane to, Xorg is screen not sound. But... I installed mplayer and played that from tty. Then everything worked! Both direct to alsa, to oss and to esd. I even had some "cat /dev/urandom > test" and some complex commands to stress it, and it worked. Now the question is, how do I fix it? How do I revert back to X.org 7.0.0, or is it possible to fix 7.2.0? I've taken 7.0.0 xorg.conf file and tried with that one to, but still the same high pitch noise there. I have also tried other distroes. The same thing there. But they all used xorg 7.2.0. And the sound stutters when I move windows, use the mouse, page-up and down, stress in X (like restoring Firefox with 20 tabs), so actually it doesn't seem that insane.

I've also tried XOrg with vga, vesa and nvidia, without that making any difference.

```
simen@dxlr8r:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 02)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
00:0d.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 0c)
01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3 Ti 200] (rev a3)
```

```
simen@dxlr8r:~$ lsmod | grep ^snd
snd_usb_audio          79744  1 
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  2 snd_usb_audio,snd_pcm_oss
snd_page_alloc         10888  1 snd_pcm
snd_usb_lib            17280  1 snd_usb_audio
snd_hwdep               9988  1 snd_usb_audio
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
```

I've been on this for over a week now! Please help me out. I really don't wanna install Windows. Haven't done that in many many years.

---

### Post by Caffeine_Junky on 2007-10-28
This one (see OP ) has been sitting for a few hrs = 10 , I will give it a bump and see if there is someone else about with a possible fix

Maybe one solution is to go back to 7.04, and submit a "bug report" for your issue?

Bump :)

sorry I could not be of more use!
good luck

---

### Post by dxlr8r on 2007-11-15
It turns out the whole motherboard series have this problem. Not related to Linux. Same in Windows actually. But they released some kinda patch to fix the faulty hardware, so it's much better there with the patch. My solution was to send the sound to my old server with esound (I'll look into PulseAudio), and now EVERYTHING is good again.

Thank you for your interest.

:guitar: on :P

---

