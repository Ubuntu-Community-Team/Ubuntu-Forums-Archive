---
title: "cx 88xx not loading"
date: 2010-07-13
forum: Mythbuntu
---

### Post by creznedmick on 2010-07-13
Greetings
CARD Haupppauge HVR 1300
I am a bit lost. I have downloaded the latest version of mercurial and v4l-dvb. I have installed the the drivers  and tried to load modules:
 sudo modprobe cx8800
I have added the following lines to etc/modules:

 alias char-major-81     videodev
 alias char-major-81-0   cx8800
 options cx88xx card=56 tuner=63 radio=63
 alias /dev/radio0 cx8800
 alias /dev/video0 cx8800

and rebooted. This is the output of


$  dmesg | grep "cx88"| more
[   12.410009] cx88xx: Unknown symbol ir_codes_pixelview_table
[   12.410439] cx88xx: Unknown symbol ir_codes_norwood_table
[   12.410550] cx88xx: Unknown symbol ir_codes_hauppauge_new_table
[   12.410717] cx88xx: Unknown symbol ir_codes_winfast_table
[   12.410823] cx88xx: Unknown symbol ir_codes_pixelview_new_table
[   12.410895] cx88xx: Unknown symbol ir_codes_cinergy_1400_table
[   12.410965] cx88xx: Unknown symbol ir_codes_dntv_live_dvb_t_table
[   12.411074] cx88xx: Unknown symbol ir_extract_bits
[   12.411208] cx88xx: Unknown symbol ir_codes_msi_tvanywhere_table
[   12.411532] cx88xx: Unknown symbol ir_decode_biphase
[   12.411626] cx88xx: Unknown symbol ir_input_init
[   12.411767] cx88xx: Unknown symbol ir_codes_adstech_dvb_t_pci_table
[   12.411899] cx88xx: Unknown symbol ir_input_nokey
[   12.411968] cx88xx: Unknown symbol ir_codes_powercolor_real_angel_table
[   12.412167] cx88xx: Unknown symbol ir_codes_npgtech_table
[   12.412298] cx88xx: Unknown symbol ir_codes_avertv_303_table
[   12.412368] cx88xx: Unknown symbol ir_codes_dntv_live_dvbt_pro_table
[   12.412780] cx88xx: Unknown symbol ir_input_keydown
[   12.412854] cx88xx: Unknown symbol ir_decode_pulsedistance
[   12.412924] cx88xx: Unknown symbol ir_codes_iodata_bctv7e_table
[   12.412993] cx88xx: Unknown symbol ir_dump_samples
[   12.413140] cx88xx: Unknown symbol ir_codes_pinnacle_pctv_hd_table
[   12.570838] cx88xx: Unknown symbol ir_codes_pixelview_table
[   12.571272] cx88xx: Unknown symbol ir_codes_norwood_table
[   12.571384] cx88xx: Unknown symbol ir_codes_hauppauge_new_table
[   12.571552] cx88xx: Unknown symbol ir_codes_winfast_table
[   12.571658] cx88xx: Unknown symbol ir_codes_pixelview_new_table
[   12.571731] cx88xx: Unknown symbol ir_codes_cinergy_1400_table
[   12.571801] cx88xx: Unknown symbol ir_codes_dntv_live_dvb_t_table
[   12.571911] cx88xx: Unknown symbol ir_extract_bits
[   12.572047] cx88xx: Unknown symbol ir_codes_msi_tvanywhere_table
[   12.572375] cx88xx: Unknown symbol ir_decode_biphase
[   12.572470] cx88xx: Unknown symbol ir_input_init
[   12.572622] cx88xx: Unknown symbol ir_codes_adstech_dvb_t_pci_table
[   12.572756] cx88xx: Unknown symbol ir_input_nokey
[   12.572826] cx88xx: Unknown symbol ir_codes_powercolor_real_angel_table
[   12.573026] cx88xx: Unknown symbol ir_codes_npgtech_table
[   12.573159] cx88xx: Unknown symbol ir_codes_avertv_303_table

Can anyone please help
Michael

---

### Post by ian dobson on 2010-07-13
Hi,

I imagine you should ask about this over at the v4l-dvb forums.

It looks as if the cx88 module is trying to use another module (something to do with ir) and it's not loaded.

Do you see anything else in dmesg that could point towards what the problem is.

Regards
Ian Dobson

---

### Post by creznedmick on 2010-07-13
greetings Ian
I will post to v4l forum if you cannot help. 
I scanned dmesg output and the cx88 is the only reference to "ir" I can find

Michael

---

### Post by ian dobson on 2010-07-13
Hi,

So it's not bringing anything up about loading an ir* module, requiring some firmware or other?

OK, the it looks as if the compile or install screwed up badly. When do you see when you do a depmod -a? (see [http://linux.about.com/library/cmd/blcmdl8_depmod.htm](http://linux.about.com/library/cmd/blcmdl8_depmod.htm)) as root?

Digging through the internet I found a German site where they had the same problems and in the end it was with with a conflict between the cx88 driver and the DVB support included in the kernel.

Regards
Ian Dobson

---

