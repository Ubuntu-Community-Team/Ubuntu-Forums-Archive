---
title: "Lost audio in Feisty"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by hnick on 2007-06-28
I installed Feisty on a new machine. 
Asus P5NSLI motherboard (uses ADI AD1986A SoundMAX 6-channel CODEC for audio)
Intel Dual core processor
4 1Gb sticks of Ram (system sees 3 of them)
NVidia eGeForce 7300 GT express PCI video card 

Initially the system had sound and I could play MP3s without any problems. The system crashed coming out of hibernate mode and I haven't had sound since. It is a software problem as the dual-boot XP sound works and the live Feisty CD still produces sound. 

I have compared the output of the lsmod for both the live CD and my current setup. The only difference between entries having a "snd" characteristic is:
diff lsmod.txt.sorted live.lsmod.txt.sorted 
1,2c1,2
< snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
< snd_hda_codec         205056  1 snd_hda_intel
---
> snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
> snd_hda_codec         205440  1 snd_hda_intel
 
The only differences I can see are that "snd_pcm_oss" and "snd_pcm,snd_mixer_oss" are reversed and that snd_hda_codec has different numbers. I don't know what the numbers represent being something of a noob at this.

I also compared dmesg of both live CD and current and saw nothing that looked like audio setup. All the interrupt assignments were the same. 

Does anybody have any suggestions?
Thanks.

---

### Post by jjborcha on 2007-06-30
I also have a Asus P5NSLI with AD1986A sound chip.  Also having problems with audio for 7.04 version.  (Sound worked fine with 6.04 Ubuntu).  Strange -- I can hear the login and logout sounds fine, but when I want to play a CD or an Ogg all I get is garbled digital audio.  Any suggestions appreciated.

---

### Post by hnick on 2007-07-18
It was indeed a software problem... It turns out that various programs can turn off sound even if they're not on. I was experimenting with different programs and discovered that sound was muted in a movie player that I don't normally use. I turned it up and the sound came back for all my other players.

Very interesting.... but shtupid...

---

