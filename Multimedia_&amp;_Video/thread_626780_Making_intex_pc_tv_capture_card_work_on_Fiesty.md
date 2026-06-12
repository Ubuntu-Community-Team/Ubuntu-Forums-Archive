---
title: "Making intex pc tv capture card work on Fiesty"
date: 2007-11-29
forum: Multimedia &amp; Video
---

### Post by rsramkee on 2007-11-29
I wanted to share my experience of making an Intex PC TV Capture card work, since I did not find this info after searching a lot. I live in India.

I run P4 2.8Ghz, 1.2Gig RAM, Fiesty Fawn, kernel 2.6.20.16 (though i rebuilt the kernel). I got an Intex PC TV Capture card and was trying to make tvtime work. The card has the saa7130 or saa7134 chipset. 

Upon installation, the card was detected and /dev/video0 was created but dmesg indicated that the card is not among the ones listed as supported and since card did not have EEPROM, the card was not up and running right away,

A bit of searching took me to [http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134). This page states the following:
<quote>
[I]Intex PC TV Capture
    * 00:09.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01) 
modprobe saa7134 card=3 tuner=14
    * 01:0a.0 Multimedia controller: Philips Semiconductors SAA7134 Video Broadcast Decoder (rev 01) card=3 sold at roughly $18 nice value card 
[/I]</quote>

I tried modprobe with both "card=3 tuner=14" and "card=3" and neither worked. I modified /etc/modprobe.d/options by adding the line "option saa7134 card=x tuner=x" for both the options and still it did not work. tvtime would always say no signal and tvtime-scanner never picked up any channels. 

Also I noticed that dmesg listed the following line:
" saa7130[0]: found at 0000:01:09.0, rev: 1, irq: 19, latency: 64, mmio: 0xfe5ffc00"

The card was neither 00:09.0 or 01:0a.0, which also possibly indicated that I may have a newer version of the hardware with the same brand name, One interesting thing I noticed was that when I used just "card=3" I could hear the audio output alone when tvtime-scanner runs, though no channels were picked up by the scanner. If I stopped the scanner when I heard some channel's audio and then started tvtime on composite output 2, I could see video and hear the same audio as was playing when I stopped scanning. Of course, I could not do any channel flipping given the video was displaying on composite 2 input and also the television input on tvtime was still showing no signal. That I thought probably indicated that some parameters had interchanged between the tv input and the composite input in the driver. 

In saa7134-cards.c, I noticed that card 3 (4th array element) was SAA7134_BOARD_FLYVIDEO2000. The array entry was the following:
       [SAA7134_BOARD_FLYVIDEO2000] = {
                .name           = "LifeView/Typhoon FlyVIDEO2000",
                .audio_clock    = 0x00200000,
                .tuner_type     = TUNER_LG_PAL_NEW_TAPC,
                .radio_type     = UNSET,
                .tuner_addr     = ADDR_UNSET,
                .radio_addr     = ADDR_UNSET,

                .gpiomask       = 0xe000,
                .inputs         = {{
                        .name = name_tv,
                        .vmux = 1,
                        .amux = LINE2,
                        .gpio = 0x0000,
                        .tv   = 1,
                },{
                        .name = name_comp1,
                        .vmux = 0,
                        .amux = LINE2,
                        .gpio = 0x4000,
                },{
                        .name = name_comp2,
                        .vmux = 3,
                        .amux = LINE2,
                        .gpio = 0x4000,
                },{
                        .name = name_svideo,
                        .vmux = 8,
                        .amux = LINE2,
                        .gpio = 0x4000,
                }},
                .radio = {
                        .name = name_radio,
                        .amux = LINE2,
                        .gpio = 0x2000,
                },
                .mute = {
                        .name = name_mute,
                        .amux = LINE2,
                        .gpio = 0x8000,
                },

I interchanged the values of .vmux and .gpio values between comp2 and tv. The resultant array looked like this:

       [SAA7134_BOARD_FLYVIDEO2000] = {
                .name           = "LifeView/Typhoon FlyVIDEO2000",
                .audio_clock    = 0x00200000,
                .tuner_type     = TUNER_LG_PAL_NEW_TAPC,
                .radio_type     = UNSET,
                .tuner_addr     = ADDR_UNSET,
                .radio_addr     = ADDR_UNSET,

                .gpiomask       = 0xe000,
                .inputs         = {{
                        .name = name_tv,
                        .vmux = 3,
                        .amux = LINE2,
                        .gpio = 0x4000,
                        .tv   = 1,
                },{
                        .name = name_comp1,
                        .vmux = 0,
                        .amux = LINE2,
                        .gpio = 0x4000,
                },{
                        .name = name_comp2,
                        .vmux = 1,
                        .amux = LINE2,
                        .gpio = 0x0000,
                },{
                        .name = name_svideo,
                        .vmux = 8,
                        .amux = LINE2,
                        .gpio = 0x4000,
                }},
                .radio = {
                        .name = name_radio,
                        .amux = LINE2,
                        .gpio = 0x2000,
                },
                .mute = {
                        .name = name_mute,
                        .amux = LINE2,
                        .gpio = 0x8000,
                },

I recompiled the kernel (thanks to [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)) and when I rebooted with this changed code, everything worked fine. tvtime_scanner was able to find all the channels and tvtime could display video and play audio. I am now able to flip channels as well. I havent yet tried making radio or the remote work. 

I just thought I will write this up since these cards are popular as they are very inexpensive and I did not find much documentation or other user experiences in making this work. Also, if anyone thinks I could have done something better or there is an well known easier way to make these cards work, please do let me know.

Thanks

---

### Post by Zweisteine on 2008-02-09
Thank you very much! That worked for me as well.
The sound only works through a loopback cable, though. Have you managed to get it to work directly?

---

### Post by rsramkee on 2008-02-10
Not really. I think the only way the sound on this card works is through the loopback cable whether its windows or linux. The card does not process sound and just send the sound output to the audio out to be fed into the sound card.

---

### Post by handsomevj on 2008-02-20
Hi ramkee this is vijay here, hope you remember me. Thanks for continuing the support. But we are not able to open the required the file. We tried to open it using vi command, but not able to find required file, to be modified. A few more detailed steps would be helpful :)

---

### Post by handsomevj on 2008-03-23
Hi, we got it detected, but same problem no signal. Where is the required saaa7134 C file needed to be modified? Do we have to add any driver patch or the generic drivers detected will work?

---

