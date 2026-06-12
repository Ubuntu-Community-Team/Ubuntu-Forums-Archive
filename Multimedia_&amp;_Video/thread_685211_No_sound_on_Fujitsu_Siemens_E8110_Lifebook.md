---
title: "No sound on Fujitsu Siemens E8110 Lifebook"
date: 2008-02-01
forum: Multimedia &amp; Video
---

### Post by MadMason on 2008-02-01
Hi all,

I am a newbie trying to learn Linux. Therefore i installed Ubuntu as this was the one recommended by my friends. The problem is that i get no sound. As i am a newbie i cannot even do more than checking if nothing is muted or etc. 

Since days i am surfing the net trying to find out solutions but none seem to work for me :( I will really be very glad if anyone of you can help me out. I post here the things which i saw were generally asked by people during troubleshooting

> 
lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)


> 
lsmod | grep -i snd
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm


> 
 cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0640000 irq 23


> 
cat /etc/modules 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
snd-hda-intel


> 
uname -r
2.6.22-14-generic


The IEC stuff is also muted. What can i do more? I have Ubuntu Gutsy 7.10

Please help

---

### Post by MadMason on 2008-02-02
Does nobody have any idea about it? :( I like Ubuntu and wanna keep using it. Please help.

---

### Post by MadMason on 2008-02-02
An interesting find. I just plugged in my earphones in the Laptop and i have sound in the earphones. But why i cannot hear any sound on the normal speakers?

---

