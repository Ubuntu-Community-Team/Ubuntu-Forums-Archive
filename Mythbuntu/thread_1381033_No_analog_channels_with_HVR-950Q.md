---
title: "No analog channels with HVR-950Q"
date: 2010-01-14
forum: Mythbuntu
---

### Post by bcg30506 on 2010-01-14
I'm using this Hauppauge USB tuner to bring in the clear QAM channels from our Charter cable service.  I note on the product page for the device it is also supposed to tune in NTSC analog channels.  Mine does not, at least with the scan in Mythtv-setup.  Is it possible to get both?  If so, what is the process in mythtv-setup to have it scan for both NTSC and QAM stations?

---

### Post by Colonelguf on 2010-01-16
According to [http://www.kernellabs.com/blog/?p=899](http://www.kernellabs.com/blog/?p=899), 950Q is supposed to be working with analog. I am a newby myself and don't know how to get the latest software updates. Everytime I try to access the analog the frontend locks up. I am running Mythbuntu 9.10. I have been using Ubuntu for several years off and on, but this is my first try with Myth and I have a lot to learn.

---

### Post by newbuntu81 on 2011-03-05
I have an HVR 950q in one Mythbuntu 10.10 box, and also an HVR 2250 in another box running the same distribution and kernel, etc.

I can't get either to work with NTSC analog cable in mythtv, but I can get both to record in ATSC over the air digital in mythtv.  I can run mplayer and manually set the frequency and show NTSC analog cable...which means the drivers are working with linux, just not Mythtv 0.24.

Any ideas?

_**Here is my log output:**_

michael@michael-OptiPlex-GX270:~/v4l-dvb$ [COLOR=Blue]**dmesg | grep tve**[/COLOR]
[   13.674604] tveeprom 1-0050: Hauppauge model 72001, rev B3F0, serial# 3439372
[   13.674611] tveeprom 1-0050: MAC address is 00:0d:fe:34:7b:0c
[   13.674615] tveeprom 1-0050: tuner model is Xceive XC5000 (idx 150, type 76)
[   13.674619] tveeprom 1-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   13.674623] tveeprom 1-0050: audio processor is AU8522 (idx 44)
[   13.674626] tveeprom 1-0050: decoder processor is AU8522 (idx 42)
[   13.674630] tveeprom 1-0050: has no radio, has IR receiver, has no IR transmitter

michael@michael-OptiPlex-GX270:~/v4l-dvb$ [COLOR=Blue]**dmesg | grep 72001**[/COLOR]
[   13.674604] tveeprom 1-0050: Hauppauge model 72001, rev B3F0, serial# 3439372
[   13.674633] hauppauge_eeprom: hauppauge eeprom: model=72001

michael@michael-OptiPlex-GX270:~/v4l-dvb$ **[COLOR=Blue]dmesg | grep xc5000[/COLOR]**
[   15.021641] xc5000: xc5000_attach(1-0061)
[   15.021647] xc5000 1-0061: creating new instance
[   15.026960] xc5000: Successfully identified at address 0x61
[   15.026964] xc5000: Firmware has not been loaded previously
[   15.035332] xc5000: xc5000_attach(1-0061)
[   15.035336] xc5000 1-0061: attaching existing instance
[   15.040082] xc5000: Successfully identified at address 0x61
[   15.040085] xc5000: Firmware has not been loaded previously
[   15.369775] xc5000: xc5000_sleep()
[   44.988797] xc5000: xc5000_is_firmware_loaded() [COLOR=Red]returns False id = 0x2000[/COLOR]
[   44.999791] xc5000: xc5000_is_firmware_loaded() [COLOR=Red]returns False id = 0x2000[/COLOR]
[   44.999797] xc5000: [COLOR=SeaGreen]waiting for firmware upload (**[COLOR=Blue]dvb-fe-xc5000-1.6.114.fw[/COLOR]**)...
[   45.780801] xc5000: firmware read 12401 bytes.
[   45.780806] xc5000: firmware uploading...
[   45.780810] xc5000: xc5000_TunerReset()
[   53.968037] xc5000: firmware upload complete...[/COLOR]
[   53.968055] xc5000: xc_initialize()
[   57.380023] xc5000: xc5000_set_tv_freq() frequency=6400 (in units of 62.5khz)
[   57.380030] xc5000: xc_SetSignalSource(1) Source = CABLE
[   58.984020] xc5000: xc_SetTVStandard(0x8020,0x0400)
[   58.984026] xc5000: xc_SetTVStandard() Standard = M/N-NTSC/PAL-BTSC
[   62.204018] xc5000: xc_tune_channel(400000000)
[   62.204028] xc5000: xc_set_RF_frequency(400000000)
[   63.932719] xc5000: *** ADC envelope (0-1023) = 65535
[   63.937838] xc5000: *** Frequency error = 1023984 Hz
[   63.942583] xc5000: *** Lock status (0-Wait, 1-Locked, 2-No-signal) = 65535
[   63.952204] xc5000: *** HW: V0f.0f, FW: V0f.0f.ffff
[   63.956949] xc5000: *** Horizontal sync frequency = 31244 Hz
[   63.961821] xc5000: *** Frame lines = 65535
[   63.966693] xc5000: *** Quality (0:<8dB, 7:>56dB) = 65535
[   64.380816] xc5000: [COLOR=SeaGreen]xc5000_is_firmware_loaded() returns True id = 0xffff[/COLOR]
[   64.380823] xc5000: xc5000_set_tv_freq() frequency=6400 (in units of 62.5khz)
[   64.380827] xc5000: xc_SetSignalSource(1) Source = CABLE
[   65.988019] xc5000: xc_SetTVStandard(0x8020,0x0400)
[   65.988025] xc5000: xc_SetTVStandard() Standard = M/N-NTSC/PAL-BTSC
[   69.204020] xc5000: xc_tune_channel(400000000)
[   69.204026] xc5000: xc_set_RF_frequency(400000000)
[   70.932770] xc5000: *** ADC envelope (0-1023) = 65535
[   70.937762] xc5000: *** Frequency error = 1023984 Hz
[   70.942634] xc5000: *** Lock status (0-Wait, 1-Locked, 2-No-signal) = 65535
[   70.952253] xc5000: *** HW: V0f.0f, FW: V0f.0f.ffff
[   70.957000] xc5000: *** Horizontal sync frequency = 31244 Hz
[   70.961872] xc5000: *** Frame lines = 65535
[   70.966619] xc5000: *** Quality (0:<8dB, 7:>56dB) = 65535
[   71.073184] xc5000: xc5000_sleep()
[ 3194.249314] xc5000: [COLOR=SeaGreen]xc5000_is_firmware_loaded() returns True id = 0xffff[/COLOR]
[ 3194.249321] xc5000: xc5000_set_tv_freq() frequency=6400 (in units of 62.5khz)
[ 3194.249325] xc5000: xc_SetSignalSource(1) Source = CABLE
[ 3195.916041] xc5000: xc_SetTVStandard(0x8020,0x0400)
[ 3195.916047] xc5000: xc_SetTVStandard() Standard = M/N-NTSC/PAL-BTSC
[ 3199.244557] xc5000: xc_tune_channel(400000000)
[ 3199.244565] xc5000: xc_set_RF_frequency(400000000)
[ 3201.041181] xc5000: *** ADC envelope (0-1023) = 65535
[ 3201.046174] xc5000: *** Frequency error = 1023984 Hz
[ 3201.051174] xc5000: *** Lock status (0-Wait, 1-Locked, 2-No-signal) = 65535
[ 3201.069051] xc5000: *** HW: V0f.0f, FW: V0f.0f.ffff
[ 3201.074044] xc5000: *** Horizontal sync frequency = 31244 Hz
[ 3201.086438] xc5000: *** Frame lines = 65535
[ 3201.091417] xc5000: *** Quality (0:<8dB, 7:>56dB) = 65535
[ 3201.555516] xc5000: xc5000_sleep()
[ 3763.874542] xc5000: [COLOR=SeaGreen]xc5000_is_firmware_loaded() returns True id = 0xffff[/COLOR]
[ 3763.874549] xc5000: xc5000_set_tv_freq() frequency=6400 (in units of 62.5khz)
[ 3763.874553] xc5000: xc_SetSignalSource(1) Source = CABLE
[ 3765.536036] xc5000: xc_SetTVStandard(0x8020,0x0400)
[ 3765.536042] xc5000: xc_SetTVStandard() Standard = M/N-NTSC/PAL-BTSC
[ 3768.816042] xc5000: xc_tune_channel(400000000)
[ 3768.816047] xc5000: xc_set_RF_frequency(400000000)
[ 3770.574621] xc5000: *** ADC envelope (0-1023) = 65535
[ 3770.579740] xc5000: *** Frequency error = 1023984 Hz
[ 3770.584742] xc5000: *** Lock status (0-Wait, 1-Locked, 2-No-signal) = 65535
[ 3770.595622] xc5000: *** HW: V0f.0f, FW: V0f.0f.ffff
[ 3770.601495] xc5000: *** Horizontal sync frequency = 31244 Hz
[ 3770.607113] xc5000: *** Frame lines = 65535
[ 3770.612115] xc5000: *** Quality (0:<8dB, 7:>56dB) = 65535
[ 3771.206396] xc5000: xc5000_is_firmware_loaded() returns True id = 0xffff
[ 3771.206404] xc5000: xc5000_set_tv_freq() frequency=6400 (in units of 62.5khz)
[ 3771.206408] xc5000: xc_SetSignalSource(1) Source = CABLE
[ 3772.840028] xc5000: xc_SetTVStandard(0x8020,0x0400)
[ 3772.840033] xc5000: xc_SetTVStandard() Standard = M/N-NTSC/PAL-BTSC
[ 3776.124477] xc5000: xc_tune_channel(400000000)
[ 3776.124484] xc5000: xc_set_RF_frequency(400000000)
[ 3777.872988] xc5000: *** ADC envelope (0-1023) = 65535
[ 3777.878233] xc5000: *** Frequency error = 1023984 Hz
[ 3777.883225] xc5000: *** Lock status (0-Wait, 1-Locked, 2-No-signal) = 65535
[ 3777.894110] xc5000: *** HW: V0f.0f, FW: V0f.0f.ffff
[ 3777.902354] xc5000: *** Horizontal sync frequency = 31244 Hz
[ 3777.907346] xc5000: *** Frame lines = 65535
[ 3777.913607] xc5000: *** Quality (0:<8dB, 7:>56dB) = 65535
[ 3778.033681] xc5000: xc5000_sleep()
[ 3780.564074] xc5000: [COLOR=SeaGreen]xc5000_is_firmware_loaded() returns True id = 0xffff[/COLOR]
[ 3780.564081] xc5000: xc5000_set_tv_freq() frequency=6400 (in units of 62.5khz)
[ 3780.564085] xc5000: xc_SetSignalSource(1) Source = CABLE
[ 3782.208040] xc5000: xc_SetTVStandard(0x8020,0x0400)
[ 3782.208046] xc5000: xc_SetTVStandard() Standard = M/N-NTSC/PAL-BTSC
[ 3785.440043] xc5000: xc_tune_channel(400000000)
[ 3785.440057] xc5000: xc_set_RF_frequency(400000000)
[ 3787.176920] xc5000: *** ADC envelope (0-1023) = 65535
[ 3787.184918] xc5000: *** Frequency error = 1023984 Hz
[ 3787.190160] xc5000: *** Lock status (0-Wait, 1-Locked, 2-No-signal) = 65535
[ 3787.201793] xc5000: *** HW: V0f.0f, FW: V0f.0f.ffff
[ 3787.210037] xc5000: *** Horizontal sync frequency = 31244 Hz
[ 3787.215155] xc5000: *** Frame lines = 65535
[ 3787.220788] xc5000: *** Quality (0:<8dB, 7:>56dB) = 65535
[ 3787.590938] xc5000: xc5000_sleep()
[ 4113.037100] xc5000: [COLOR=SeaGreen]xc5000_is_firmware_loaded() returns True id = 0xffff[/COLOR]
[ 4113.037107] xc5000: xc5000_set_tv_freq() frequency=6400 (in units of 62.5khz)
[ 4113.037111] xc5000: xc_SetSignalSource(1) Source = CABLE
[ 4114.708053] xc5000: xc_SetTVStandard(0x8020,0x0400)
[ 4114.708059] xc5000: xc_SetTVStandard() Standard = M/N-NTSC/PAL-BTSC
[ 4118.012049] xc5000: xc_tune_channel(400000000)
[ 4118.012054] xc5000: xc_set_RF_frequency(400000000)
[ 4119.769654] xc5000: *** ADC envelope (0-1023) = 65535
[ 4119.777407] xc5000: *** Frequency error = 1023984 Hz
[ 4119.783050] xc5000: *** Lock status (0-Wait, 1-Locked, 2-No-signal) = 65535
[ 4119.795040] xc5000: *** HW: V0f.0f, FW: V0f.0f.ffff
[ 4119.800918] xc5000: *** Horizontal sync frequency = 31244 Hz
[ 4119.806161] xc5000: *** Frame lines = 65535
[ 4119.811030] xc5000: *** Quality (0:<8dB, 7:>56dB) = 65535
[ 4120.425826] xc5000: [COLOR=SeaGreen]xc5000_is_firmware_loaded() returns True id = 0xffff[/COLOR]
[ 4120.425833] xc5000: xc5000_set_tv_freq() frequency=6400 (in units of 62.5khz)
[ 4120.425836] xc5000: xc_SetSignalSource(1) Source = CABLE
[ 4122.104122] xc5000: xc_SetTVStandard(0x8020,0x0400)
[ 4122.104128] xc5000: xc_SetTVStandard() Standard = M/N-NTSC/PAL-BTSC
[ 4125.408435] xc5000: xc_tune_channel(400000000)
[ 4125.408442] xc5000: xc_set_RF_frequency(400000000)
[ 4127.163058] xc5000: *** ADC envelope (0-1023) = 65535
[ 4127.168403] xc5000: [COLOR=Red]*** Frequency error = 1023984 Hz[/COLOR]
[ 4127.176279] xc5000: *** Lock status (0-Wait, 1-Locked, 2-No-signal) = 65535
[ 4127.188778] xc5000: *** HW: V0f.0f, FW: V0f.0f.ffff
[ 4127.194862] xc5000: *** Horizontal sync frequency = 31244 Hz
[ 4127.202654] xc5000: *** Frame lines = 65535
[ 4127.207269] xc5000: *** Quality (0:<8dB, 7:>56dB) = 65535
[ 4127.362628] xc5000: xc5000_sleep()
[ 4130.141748] xc5000: [COLOR=SeaGreen]xc5000_is_firmware_loaded()[/COLOR] returns True id = 0xffff
[ 4130.141756] xc5000: xc5000_set_tv_freq() frequency=6400 (in units of 62.5khz)
[ 4130.141759] xc5000: [COLOR=SeaGreen]xc_SetSignalSource(1) Source = CABLE[/COLOR]
[ 4131.804053] xc5000: xc_SetTVStandard(0x8020,0x0400)
[ 4131.804059] xc5000: [COLOR=SeaGreen]xc_SetTVStandard() Standard = M/N-NTSC/PAL-BTSC[/COLOR]
[ 4135.124038] xc5000: xc_tune_channel(400000000)
[ 4135.124044] xc5000: xc_set_RF_frequency(400000000)
[ 4136.916944] xc5000: *** ADC envelope (0-1023) = 65535
[ 4136.921816] xc5000: [COLOR=Red]*** Frequency error = 1023984 Hz[/COLOR]
[ 4136.929569] xc5000: *** Lock status (0-Wait, 1-Locked, 2-No-signal) = 65535
[ 4136.941317] xc5000: *** HW: V0f.0f, FW: V0f.0f.ffff
[ 4136.947064] xc5000: *** Horizontal sync frequency = 31244 Hz
[ 4136.953189] xc5000: *** Frame lines = 65535
[ 4136.958561] xc5000: *** Quality (0:<8dB, 7:>56dB) = 65535
[ 4137.298894] xc5000: xc5000_sleep()

---

### Post by newbuntu81 on 2011-03-05
> **newbuntu81 said:**
> I have an HVR 950q in one Mythbuntu 10.10 box, and also an HVR 2250 in another box running the same distribution and kernel, etc.



I ran across this article from Mark Ackerman at [http://www.kernellabs.com/blog/?p=1388:](http://www.kernellabs.com/blog/?p=1388:)

As a final update for anyone who is struggling with this card, as I  did. Here is my summary of notes, and thanks to all who helped.
1/ add the line:    “options xc5000 no_poweroff=1 debug=1&#8243; no quotes   , to:
  &#8728; # sudo gedit /etc/modprobe.d/local.conf    and
  &#8728; # sudo gedit /etc/modprobe.d/xc5000.conf

2/ The digital side is easy to set up — if your 950Q is your only tuner,  then it will show up (digital) as the only DVB device. The only trick  here, is to create a custom recorder group (instead of the default of  “generic”) for it.

3/  Then tackle the analog side. If it is your only tuner device, then  this will be /dev/video0, and probably /dev/dsp1 for the audio — yes you  need this field.

4/ Then put it in the same recorder group as the digital side.

5/ After doing mythfilldatabase and setting up the channels for  everything, fire up mythfrontend. Go into the Setup -> … ->  Recording Profiles, and set the resolution for the analog to be 720×480  for everything (default, live-tv, etc..). Change the audio sampling rate  to 48000.

5b/ You need to make sure your capture resolution for LiveTV mode and  the various capture modes is set to 720×480 (the default in MythTV is  480×480)

6/  you’ll need to create an “input source” for digital, and a second  “input source” for analog. Yes, they can both point at exactly the same  schedulesdirect.org channel lineup, but they do need to be separate  otherwise.

7/  Then use the “input connections” menu in mythtv-setup to point the  digital side of the 950Q at the digital “source”, and the analog side at  the analog “source”.


 • sound with tvtime using :
   &#8728; tvtime | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay 
 • change the MythTV sound device for the analog  side of the HVR-1500-950Q to be /dev/dsp1 again. MythTV now has working  sound in analog mode and I have been able to change between analog and  digital modes (and vice versa) without any of the problems seen in the  past

---

