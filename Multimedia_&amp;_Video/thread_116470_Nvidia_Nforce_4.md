---
title: "Nvidia Nforce 4"
date: 2006-01-12
forum: Multimedia &amp; Video
---

### Post by Virogenesis on 2006-01-12
I''ve just got my new motherboard through today its a nforce and uses the ac97 codec.
Anyway I'm looking for a bit of help setting this up as I've always had great experience with linux where it would just pick up my sound card out of the box and was hoping that would be the case aswell due to nvidia drivers.

Hiopefully someone will be able to help me out of this tricky mess

Thanks

---

### Post by tim15856 on 2006-01-12
Try the Live-CD and see if everything works. If not, download the driver. [http://www.nvidia.com/object/linux_nforce_amd64_1.0-0310.html](http://www.nvidia.com/object/linux_nforce_amd64_1.0-0310.html)

Edit: It looks like that may be for the older nForce. I don't see any Linux drivers on nVidia's website for the nForce4.

---

### Post by Virogenesis on 2006-01-13
After researching I've found out that nvidia only support oss for now and my mobo manual tells me i've got a ac97 chip so i'm wondering how i'll go about using alsa.
Live disc also failed to play sounds

Sample lspci 
```

vir@TheFamousTuX:~/Desktop$ lspci 0000:00:00.0 Memory controller: nVidia Corporation: Unknown device 005e (rev a2)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 0050 (rev a2)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 0052 (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 005a (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 005b (rev a2)
0000:00:04.0 Multimedia audio controller: nVidia Corporation: Unknown device 005 9 (rev a2)
0000:00:06.0 IDE interface: nVidia Corporation: Unknown device 0053 (rev a2)
0000:00:07.0 IDE interface: nVidia Corporation: Unknown device 0054 (rev a2)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 0055 (rev a2)
0000:00:09.0 PCI bridge: nVidia Corporation: Unknown device 005c (rev a2)
0000:00:0a.0 Bridge: nVidia Corporation: Unknown device 0057 (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a2)
0000:00:0c.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a2)
0000:00:0d.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:08.0 SCSI storage controller: Adaptec AIC-7892A U160/m (rev 02)
0000:05:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0140 (rev a2)

```

```

vir@TheFamousTuX:~/Desktop$ lsmod | grep snd
snd_intel8x0           30144  1
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm

```

```

vir@TheFamousTuX:~/Desktop$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.9 (Sun May 29 07:31:02 2005 UTC).
vir@TheFamousTuX:~/Desktop$ cat /proc/asound/pcm
00-00: Intel ICH : NVidia CK804 : playback 1 : capture 1
00-01: Intel ICH - MIC ADC : NVidia CK804 - MIC ADC : capture 1
00-02: Intel ICH - IEC958 : NVidia CK804 - IEC958 : playback 1
vir@TheFamousTuX:~/Desktop$ cat /proc/asound/cards
0 [CK804          ]: NFORCE - NVidia CK804
                     NVidia CK804 with ALC655 at 0xfebfd000, irq 22

```

Thanks hope you can help

---

### Post by nilly on 2006-01-13
Sound works thru alsa on my asus nforce4 mboard.. np

---

### Post by Virogenesis on 2006-01-13
seem i do have sound but i need to turn my speakers up to max when playing a cd seems i might have to turn up the volume and change setting but where? :(
I've ran alsamixer aswell.

Please help

---

### Post by vvlaw on 2006-01-15
[QUOTE=Virogenesis]seem i do have sound but i need to turn my speakers up to max when playing a cd seems i might have to turn up the volume and change setting but where? :(
I've ran alsamixer aswell.

Please help[/QUOTE]

i was found this same error just now,but it looks like i had already install the alsa drivers.
~~~
vvlaw@ubuntu:~$ cat /proc/asound/cards
0 [CK804          ]: NFORCE - NVidia CK804
                     NVidia CK804 with ALC655 at 0xfe02d000, irq 22
vvlaw@ubuntu:~$ cat /proc/asound/pcm
00-00: Intel ICH : NVidia CK804 : playback 1 : capture 1
00-01: Intel ICH - MIC ADC : NVidia CK804 - MIC ADC : capture 1
00-02: Intel ICH - IEC958 : NVidia CK804 - IEC958 : playback 1
vvlaw@ubuntu:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.9rc4a.
Compiled on Jan 15 2006 for kernel 2.6.12-9-386.
vvlaw@ubuntu:~$
~~~

but why i can't still use the mic ???where is the problem?:(

---

### Post by handy on 2006-01-15
Alsa worked on my nForce 3, under Breezy 5.10 64bit, untill I turned off onboard sound in the BIOS.  I'd rather run the SBlive PCI card.

---

### Post by mo_x on 2006-01-15
Sounds is fine with the alsa snd_intel8x0 driver for me.

cat /proc/asound/cards
0 [CK804          ]: NFORCE - NVidia CK804
                     NVidia CK804 with ALC850 at 0xe3205000, irq 22

Mine is a Realtek ALC850 yours a ALC655. You could try installing a newer version of alsa.
What motherboard do you have?

---

### Post by Virogenesis on 2006-01-15
well i've fixed it basicaly I brought this mobo back in Nov and I replaced the existing one straight away as I thought my cpu wouldn't take long and well I ended up buying a Mobile chip from the states off of ebay so anyway it never turnt up and  finaly I managed to get my money back off of paypal.
Having taken so long I tried a old AMD k62 board I had laying around I took off didn't work so just screwed back in my new board.

Now Thurday I get my new graphics card install that don't to bed as I'm trying to decide to use ubuntu 64 or not.
Comes Friday I get my new cpu head run to my bros can't remember what for and basicaly had a smoke and yeah cut a long story short....

All down to human error.... was working straight out of the box and only reason why I remebered is because I saw a jumper on the side... 
Whats amusing is I was expecting for it to work out of the box as I researched before buying but yeah I'm happy now.

---

### Post by vvlaw on 2006-01-16
[QUOTE=mo_x]Sounds is fine with the alsa snd_intel8x0 driver for me.

cat /proc/asound/cards
0 [CK804          ]: NFORCE - NVidia CK804
                     NVidia CK804 with ALC850 at 0xe3205000, irq 22

Mine is a Realtek ALC850 yours a ALC655. You could try installing a newer version of alsa.
What motherboard do you have?[/QUOTE]

it looks like that i had already installed the snd_intel8x0?

vvlaw@ubuntu:~$ lsmod | grep snd
snd_intel8x0           30144  3
snd_ac97_codec         71420  1 snd_intel8x0
snd_pcm_oss            46240  0
snd_mixer_oss          16256  2 snd_pcm_oss
snd_pcm                78344  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_pcm
snd                    49412  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  2 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
vvlaw@ubuntu:~$

but when i want to use the wengophone,there show some error messages :( 

Entering ph_media_start
ph_media DTX/VAD 0
ph_media clock rate 8000
ph_media_start - opening AUDIO device
error opening opening AUDIO device &#35774;&#22791;&#25110;&#36164;&#28304;&#24537;

Entering ph_media_start
ph_media DTX/VAD 0
ph_media clock rate 8000
ph_media_start - opening AUDIO device
error opening opening AUDIO device (

---

