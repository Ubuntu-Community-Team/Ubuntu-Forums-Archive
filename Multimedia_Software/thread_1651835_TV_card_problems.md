---
title: "TV card problems"
date: 2010-12-23
forum: Multimedia Software
---

### Post by huggies15 on 2010-12-23
Hello all,

Im trying to install a tv card in my ubuntu pc, its a videomate T100. now i know theres not much help out there (its all for the t200 +), but im trying to coble together a way of getting this to work. Ive followed this guide [http://ubuntuforums.org/archive/index.php/t-1050253.html](http://ubuntuforums.org/archive/index.php/t-1050253.html)
and when i do sudo modprobe saa7134-dvb i keep coming up with fatal error messages:

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Error inserting saa7134 (/lib/modules/2.6.31-22-generic-pae/kernel/drivers/media/video/saa7134/saa7134.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for saa7134
FATAL: Error inserting saa7134_dvb (/lib/modules/2.6.31-22-generic-pae/kernel/drivers/media/video/saa7134/saa7134-dvb.ko): Unknown symbol in module, or unknown parameter (see dmesg)

the dmesg read out is:

[  147.343293] saa7134: Unknown symbol ir_codes_pinnacle_color
[  147.343735] saa7134: Unknown symbol ir_codes_avermedia
[  147.344327] saa7134: Unknown symbol ir_codes_flydvb
[  147.344825] saa7134: Unknown symbol ir_codes_genius_tvgo_a11mce
[  147.344953] saa7134: Unknown symbol ir_codes_gotview7135
[  147.345074] saa7134: Unknown symbol ir_codes_encore_enltv
[  147.345291] saa7134: Unknown symbol ir_codes_behold
[  147.345573] saa7134: Unknown symbol ir_codes_behold_columbus
[  147.345735] saa7134: Unknown symbol ir_codes_proteus_2309
[  147.346016] saa7134: Unknown symbol ir_codes_flyvideo
[  147.346247] saa7134: Unknown symbol ir_codes_eztv
[  147.346527] saa7134: Unknown symbol ir_codes_encore_enltv_fm53
[  147.346648] saa7134: Unknown symbol ir_codes_pixelview
[  147.346839] saa7134: Unknown symbol ir_codes_avermedia_a16d
[  147.347258] saa7134: Unknown symbol ir_rc5_timer_keyup
[  147.347703] saa7134: Unknown symbol ir_codes_real_audio_220_32_keys
[  147.347824] saa7134: Unknown symbol ir_codes_asus_pc39
[  147.348094] saa7134: Unknown symbol ir_extract_bits
[  147.348217] saa7134: Unknown symbol ir_rc5_timer_end
[  147.348372] saa7134: Unknown symbol ir_codes_msi_tvanywhere_plus
[  147.349125] saa7134: Unknown symbol ir_input_init
[  147.350201] saa7134: Unknown symbol ir_codes_cinergy
[  147.350321] saa7134: Unknown symbol ir_input_nokey
[  147.350496] saa7134: Unknown symbol ir_codes_videomate_tv_pvr
[  147.350895] saa7134: Unknown symbol ir_codes_hauppauge_new
[  147.351472] saa7134: Unknown symbol ir_codes_pinnacle_grey
[  147.351751] saa7134: Unknown symbol ir_codes_purpletv
[  147.361284] saa7134: Unknown symbol ir_codes_pctv_sedna
[  147.361415] saa7134: Unknown symbol ir_codes_avermedia_m135a
[  147.361548] saa7134: Unknown symbol ir_input_keydown
[  147.361680] saa7134: Unknown symbol ir_codes_kworld_plus_tv_analog
[  147.361909] saa7134: Unknown symbol ir_codes_manli
[  147.363502] saa7134_dvb: Unknown symbol saa7134_tuner_callback
[  147.363638] saa7134_dvb: Unknown symbol saa7134_ts_register
[  147.364183] saa7134_dvb: Unknown symbol saa7134_set_gpio
[  147.364313] saa7134_dvb: Unknown symbol saa7134_ts_qops
[  147.364875] saa7134_dvb: Unknown symbol saa7134_ts_unregister

the problem is it is recognised in the lspci (i think):

00:0b.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
00:0d.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

i have also downloaded and installed the v4l-dvb and dvb-apps from linuxtv.
but no program is recognising it.
Any help would be appreciated, or i may have to go back to xp - bad times :(

Cheers,
Steve Hughes

---

### Post by laceration on 2010-12-23
Different continents have different cards, I am in the USA, but I have successfully used a card w/ that decoder chip.  As in the page you refereed to, I remember using a perl program to extract the firmware file + copying it. Using modprobe is probably not necc. as newer kernels(2.6+) pretty much have support built in and recognize the hardware when its there.

I think you just need to find some good instructions on how to set this up and to confirm that this card is supported.  You best do that by going here:

[http://linuxtv.org/wiki/index.php/Hardware_Device_Information](http://linuxtv.org/wiki/index.php/Hardware_Device_Information)

---

### Post by no2498 on 2010-12-24
i am not a coder in any way
but i see you have v4l
i see a lot of v4l2 with all the webcams
think they did away kind of just v4l

things like convert, compat

LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so firefox

most all the cams i see use v4l2

just trying to help or point you in the right way

---

