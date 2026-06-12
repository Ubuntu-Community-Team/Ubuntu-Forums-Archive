---
title: "ATI HDTV wonder - black screen on NTSC input"
date: 2008-09-18
forum: Mythbuntu
---

### Post by leeko on 2008-09-18
Hi,

I'm trying to set up an ati hdtv wonder on my mythbuntu 8.04 box. I have the digital (ATSC) part working, but I'm struggling to get the analogue input to work. 

I've set up the digital input according to the mythtv wiki page, using the nxt2004 firmware. It's recognised as an Air2PC card, and I can get a signal and watch TV. 

I then set up the analogue portion of the card using the default v4l settings in mythtv-setup (/dev/video0, probed info shows "ATI HDTV Wonder [cx8800]"). The default input is set to "television". I have a separate antenna attached to both RF inputs on the card.

I have defined 2 separate video sources, which both pull the same us-bcast schedule data from schedules direct (I think I read somewhere that it's not a good idea to use the same video source for more than one tuner). 

My input connections are as follows:
DVB:0 (DVBInput) -> SD
V4L: /dev/video0 (Television) -> SD-NTSC
V4L: /dev/video0 (Composite) -> none
V4L: /dev/video0 (S-video) -> none

When I watch digital TV, it works as expected (albeit with shaky signal, but a few channels work flawlessly).

But, when I try to switch to the analogue input, all I get is a black screen (no sound either). I'm able to use the guide and change channels, but always a black screen for the TV picture. 

The only thing I can find in dmesg is:

```
leeko@leeko-media:~$ sudo dmesg |grep saa
[   47.734379] saa7130/34: v4l2 driver version 0.2.14 loaded
[   47.752858] saa7134_alsa: disagrees about version of symbol saa7134_tvaudio_setmute
[   47.752867] saa7134_alsa: Unknown symbol saa7134_tvaudio_setmute
[   47.753017] saa7134_alsa: disagrees about version of symbol saa_dsp_writel
[   47.753020] saa7134_alsa: Unknown symbol saa_dsp_writel
[   47.753166] saa7134_alsa: disagrees about version of symbol videobuf_dma_free
[   47.753169] saa7134_alsa: Unknown symbol videobuf_dma_free
[   47.753316] saa7134_alsa: disagrees about version of symbol saa7134_pgtable_alloc
[   47.753318] saa7134_alsa: Unknown symbol saa7134_pgtable_alloc
[   47.753355] saa7134_alsa: disagrees about version of symbol saa7134_pgtable_build
[   47.753357] saa7134_alsa: Unknown symbol saa7134_pgtable_build
[   47.753388] saa7134_alsa: disagrees about version of symbol saa7134_pgtable_free
[   47.753390] saa7134_alsa: Unknown symbol saa7134_pgtable_free
[   47.753421] saa7134_alsa: disagrees about version of symbol saa7134_dmasound_init
[   47.753424] saa7134_alsa: Unknown symbol saa7134_dmasound_init
[   47.753531] saa7134_alsa: disagrees about version of symbol saa7134_dmasound_exit
[   47.753534] saa7134_alsa: Unknown symbol saa7134_dmasound_exit
[   47.753617] saa7134_alsa: disagrees about version of symbol videobuf_dma_init
[   47.753619] saa7134_alsa: Unknown symbol videobuf_dma_init
[   47.753742] saa7134_alsa: disagrees about version of symbol videobuf_dma_init_kernel
[   47.753744] saa7134_alsa: Unknown symbol videobuf_dma_init_kernel
[   47.753865] saa7134_alsa: Unknown symbol videobuf_pci_dma_unmap
[   47.753981] saa7134_alsa: Unknown symbol videobuf_pci_dma_map
[   47.754018] saa7134_alsa: disagrees about version of symbol saa7134_set_dmabits
[   47.754020] saa7134_alsa: Unknown symbol saa7134_set_dmabits

```

and:

```
leeko@leeko-media:~$ sudo dmesg |grep cx8
[   43.286646] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   43.286842] cx88[0]: subsystem: 1002:a101, board: ATI HDTV Wonder [card=34,autodetected]
[   43.286845] cx88[0]: TV tuner type 68, Radio tuner type -1
[   43.326862] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   43.683988] cx88[0]/0: found at 0000:00:0a.0, rev: 5, irq: 16, latency: 32, mmio: 0xe6000000
[   43.688105] cx88[0]/0: registered device video0 [v4l2]
[   43.688255] cx88[0]/0: registered device vbi0
[   43.722864] cx88_alsa: disagrees about version of symbol videobuf_dma_free
[   43.722874] cx88_alsa: Unknown symbol videobuf_dma_free
[   43.722922] cx88_alsa: disagrees about version of symbol cx88_core_put
[   43.722924] cx88_alsa: Unknown symbol cx88_core_put
[   43.723029] cx88_alsa: Unknown symbol videobuf_pci_alloc
[   43.723061] cx88_alsa: disagrees about version of symbol cx88_core_irq
[   43.723063] cx88_alsa: Unknown symbol cx88_core_irq
[   43.723107] cx88_alsa: disagrees about version of symbol cx88_core_get
[   43.723109] cx88_alsa: Unknown symbol cx88_core_get
[   43.723290] cx88_alsa: disagrees about version of symbol btcx_riscmem_free
[   43.723292] cx88_alsa: Unknown symbol btcx_riscmem_free
[   43.723398] cx88_alsa: disagrees about version of symbol videobuf_dma_init
[   43.723400] cx88_alsa: Unknown symbol videobuf_dma_init
[   43.723473] cx88_alsa: disagrees about version of symbol cx88_sram_channel_dump
[   43.723475] cx88_alsa: Unknown symbol cx88_sram_channel_dump
[   43.723519] cx88_alsa: disagrees about version of symbol cx88_sram_channel_setup
[   43.723521] cx88_alsa: Unknown symbol cx88_sram_channel_setup
[   43.723558] cx88_alsa: disagrees about version of symbol videobuf_dma_init_kernel
[   43.723561] cx88_alsa: Unknown symbol videobuf_dma_init_kernel
[   43.723620] cx88_alsa: Unknown symbol videobuf_pci_dma_unmap
[   43.723696] cx88_alsa: Unknown symbol videobuf_pci_dma_map
[   43.723739] cx88_alsa: disagrees about version of symbol cx88_risc_databuffer
[   43.723741] cx88_alsa: Unknown symbol cx88_risc_databuffer
[   43.723775] cx88_alsa: disagrees about version of symbol videobuf_to_dma
[   43.723777] cx88_alsa: Unknown symbol videobuf_to_dma
[   43.766346] cx88[0]/2: cx2388x 8802 Driver Manager
[   43.766390] cx88[0]/2: found at 0000:00:0a.2, rev: 5, irq: 16, latency: 32, mmio: 0xe8000000
[   44.765955] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   44.765964] cx88/2: registering cx8802 driver, type: dvb access: shared
[   44.765969] cx88[0]/2: subsystem: 1002:a101, board: ATI HDTV Wonder [card=34]
[   44.765973] cx88[0]/2: cx2388x based DVB/ATSC card
[   45.179139] DVB: registering new adapter (cx88[0])
[  310.996147] cx88[0]: irq mpeg  [0x100000] ts_err?*
[  310.996166] cx88[0]/2-mpeg: general errors: 0x00100000

```

If anyone can help me with this, I'd really appreciate it!

Thanks,

Lee

---

### Post by spamoften on 2008-09-18
Hi Lee,

I replied on your other thread regarding HDTV playback on AMD 2400+ (will not work).

I have an ATI HDTV Wonder and have only enabled the ATSC input.  The instructions to enable the analog and get it working were too involved, so I have not even tried.  Let me know via message if you get this working, I would appreciate it from a fellow HDTV wonder owner.

---

### Post by leeko on 2008-09-18
Hi Spamoften,

Thanks for the replies. I'll let you know if I get it working. 

you mentioned that the instructions for the analogue portion were too involved. May I ask which instructions you were referring to? I haven't found any specific instructions for the analogue part, which is probably why I'm having difficulty....

Thanks,

Lee

---

### Post by leeko on 2008-09-26
Hi, 

is anyone able to help with this? The wiki page on mythtv.org suggests that the card can be set up correctly, but does not specify how to set up the analog portion. 

I would really like to be able to use this part of the card!

Thanks,

Lee

---

### Post by jlp_engineer on 2008-10-02
Lee,

I am working on this card too.  So far no luck getting it to do anything but show up in Mythsetup.  I cannot tune anything in on the digital tuner.  Have not tried the analog tuner yet.

When and if I get it to work - I will post it here... in detail.

---

### Post by leeko on 2008-10-03
Hi, 

The digital portion works fine - have you downloaded the correct firmware?

Check out [www.mythtv.org/wiki/index.php/ATI_HDTV_Wonder](www.mythtv.org/wiki/index.php/ATI_HDTV_Wonder) for the full installation instructions. 

If you have any joy with the analogue portion, I'd love to hear it!

Thanks,

Lee

---

### Post by angryswede on 2008-10-12
Anyone have any luck yet with the analog tuner?

---

### Post by leeko on 2008-10-12
Nothing on my part - but watching closely (the thread, not the black screen... that would be daft). 

Lee

---

### Post by angryswede on 2008-10-12
ok good news.  i tried using tv time this morning instead of mythtv and behold the analog tuner worked.  however, audio is not working.  i suspect there might be some type of pulse audio issue.  also i am using the coax input, i am going to try with the composite input.

---

### Post by angryswede on 2008-10-12
I tried the composite input as well, but no sound on that either.  I found this link [http://ubuntuforums.org/showthread.php?t=723618;](http://ubuntuforums.org/showthread.php?t=723618;) however, when I run this:

padsp sox -r 48000 -w -c 2 -t ossdsp /dev/dsp -t ossdsp /dev/dsp 

I get this:
sox soxio: Failed reading `/dev/dsp': unknown file type `ossdsp'

---

### Post by leeko on 2008-10-12
I've been able to get a picture on the composite input, coming from my DTV set-top box. But, I've never been able to get audio from it. 

The analogue coax input was most important for me, though, and I never managed to get anything from it - video or audio - using myth, TVtime or Xawtv. It's a bit moot after February 2009, as the OTA analogue signals will be switched off in the USA. Still, it would be nice to get it working... 

Cheers,

Lee

---

### Post by pondo on 2008-11-18
Gents, Im fairly new to Ubuntu and even newer to Myth TV. I have an ATI HDTV card too. I have the same results. Digital works great analog... :-(.
Also have a hauppauge PVR250 in the box with the ATI. They work nicely together under 8.10. 
If I come up with anything on the ATI analog issue, I'll share here.
cheers.

---

### Post by leeko on 2008-11-19
Thanks Pondo,

I appreciate any info shared :)

Lee

---

### Post by swingboy3 on 2009-03-02
I have been using the digital side too for a while and have some things working on analog.

As far as composite or S-video, they work fine, but the audio has to be fed into the on-board audio-card not into the ATI.  My most recent discovery was that this went into the microphone port of that.  Kind of weird, but it works.  To set up the composite you just make a random channel number such as 1 or 99 and add it to an independent source and tie it to the composite or s-video input.  The only problem I have is that the color is washed out a bit and the top half of the screen fades to green sometimes.  
I would like to get the analog TV part working so that I can hopefully get a clearer picture.  Currently I can't even add channels by scanning.  I will work on it more and get back to you.

---

### Post by spamoften on 2010-04-06
It's been a while since I posted here.  I have re-installed Mythbuntu 9.10 and have the ATSC capture working perfectly for the ATI HDTV Wonder card.  I also have a 950Q USB ATSC tuner working in the same box.  The 950Q has far greater sensitivity, which allows tuning in remote TV stations from 100km away, whereas the ATI periodically can tune them in, but not as frequently or successfully.

Has anyone got the analog NTSC tuner working? I haven't and still have one analog NTSC OTA channel I would like to tune...

---

### Post by AKADAP on 2010-04-07
> **spamoften said:**
> It's been a while since I posted here.  I have re-installed Mythbuntu 9.10 and have the ATSC capture working perfectly for the ATI HDTV Wonder card.  I also have a 950Q USB ATSC tuner working in the same box.  The 950Q has far greater sensitivity, which allows tuning in remote TV stations from 100km away, whereas the ATI periodically can tune them in, but not as frequently or successfully.

Has anyone got the analog NTSC tuner working? I haven't and still have one analog NTSC OTA channel I would like to tune...

As far as I can tell, the NTSC functionality was broken a few years ago, and the developers don't think it is important enough to fix since everything is going digital. My cable connection still has about 30 NTSC signals I can't access, and there are still a couple of OTA stations running NTSC that I cant access because of this.

---

### Post by AKADAP on 2010-05-01
I made a bit of progress on this...

Per a suggestion on the mythtv-user mailing list:
I ran mythbackendsetup to stop the mythTV backend from running.
As super user, I ran the following script:
```
#!/bin/sh
#
# unload hdtv wonder modules
#
/sbin/modprobe -r cx8800
/sbin/modprobe -r cx88_dvb
/sbin/modprobe -r nxt200x
/usr/bin/pkill pulseaudio; /sbin/modprobe -r cx88_alsa
/sbin/modprobe -r tuner
/sbin/modprobe -r tuner_simple
/sbin/modprobe -r tuner_types
/sbin/modprobe -r tda9887
/sbin/modprobe -r tda8290
#
# reload hdtv wonder modules
#
/sbin/modprobe cx88_dvb
/sbin/modprobe cx8800 video_nr=1 vbi_nr=1
/sbin/modprobe cx88_alsa index=1

```
Then I ran:
```

mplayer tv://32 -tv device=/dev/video1:driver=v4l2:chanlist=us-cable:alsa:adevice=hw.1,0:amode=1:audiorate=48000:forceaudio:volume=100:immediatemode=0:norm=NTSC
```

up pops a window showing video with sound!
Unfortunately, when I exited mythbackendsetup, and tried to view live TV, the analog tuner was missing.
Worse, I have since updated to Ubuntu 10.04, and now mythfrontend segmentation faults when I try to run liveTV

---

