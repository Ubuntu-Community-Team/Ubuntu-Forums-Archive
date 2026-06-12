---
title: "Need to run TV card in Windows before it starts in Ubuntu 12.04"
date: 2014-01-30
forum: Multimedia Software
---

### Post by Maxamil58 on 2014-01-30
Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
tveeprom               17009  1 saa7134
Using Kaffeine

This card has to be run in Windows first otherwise it will only show the program text and then after awhile pop up a window title 'Sorry-Kaffeine' and body 'Read error from'

If I use my Avermedia in Windows to run the card first then reboot to Ubuntu and immediately launch Kaffeine everything works fine.

Especially annoying when I want a break from something else to watch some TV

I would like to learn how I could restart the process if anyone could help?  Maybe the auto start is interrupted or failing due to power demands of other hardware?

---

### Post by TheFu on 2014-01-31
Is the video card supported by Linux?
Are there any error/warning messages?
What do the log files say?
Is a power reset really what is needed or does some bios code need to be loaded before the card can be used and only Windows does this?

Or is this just a question on how to restart any process and not specific to video equipment at all? If so, use start/stop/status/restart commands with 12.04 services - **sudo restart apache2** .  For generic programs use the **kill -HUP {pid}** method.

---

### Post by Maxamil58 on 2014-02-07
Thank you for your reply and sorry for the delay in responding. The card is supported by Linux and ran fine for sometime before this misbehaviour. Only warning is as stated in my first post though at an earlier time it would read 'Sorry the server has timed out' or 'failed to receive a response from the server' or something along those lines.

On checking I found that I do not need to launch AverMedia program in Windoze the TV card is made active (and Warmed up?) simply by logging on to Windoze then rebooting to Ubuntu.

Here is a print of queries and syslog.

yyyyyy@xxxxxxxxx:~$ lsmod | grep saa7134   (NOT WORKING)
saa7134_dvb            33449  0 
saa7134_alsa           18172  1 
videobuf_dvb           13867  1 saa7134_dvb
snd_pcm                80916  3 saa7134_alsa,snd_hda_intel,snd_hda_codec
saa7134               153846  2 saa7134_dvb,saa7134_alsa
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,saa7134,ir_nec_decoder
videobuf_dma_sg        18786  3 saa7134_dvb,saa7134_alsa,saa7134
videobuf_core          25409  3 videobuf_dvb,saa7134,videobuf_dma_sg
v4l2_common            15793  2 tuner,saa7134
videodev               86588  3 tuner,saa7134,v4l2_common
tveeprom               17009  1 saa7134
snd                    62218  18 saa7134_alsa,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

yyyyyy@xxxxxxxx:~$ lsmod | grep saa7134     (AFTER RESTART WITH WINDOWS LOGON)
saa7134_dvb            33449  6              NB CHANGE IN THIS LINE
videobuf_dvb           13867  1 saa7134_dvb
saa7134_alsa           18172  1 
snd_pcm                80916  4 saa7134_alsa,snd_hda_intel,snd_hda_codec
saa7134               153846  2 saa7134_dvb,saa7134_alsa
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,saa7134,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder
videobuf_dma_sg        18786  3 saa7134_dvb,saa7134_alsa,saa7134
videobuf_core          25409  3 videobuf_dvb,saa7134,videobuf_dma_sg
v4l2_common            15793  2 tuner,saa7134
videodev               86588  3 tuner,saa7134,v4l2_common
tveeprom               17009  1 saa7134
snd                    62218  21 saa7134_alsa,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

/var/log/syslog reads after a fail

Feb  4 16:25:14 xxxxxxxxxxxx kernel: [336287.592010] tda1004x: setting up plls for 48MHz sampling clock
Feb  4 16:25:15 xxxxxxxxxxxx kernel: [336287.876010] tda1004x: found firmware revision 29 -- ok
Feb  4 16:25:17 xxxxxxxxxxxx kernel: [336290.404011] tda827xa_set_params: could not write to tuner at addr: 0xc0
Feb  4 16:26:01 xxxxxxxxxxxx kernel: [336334.332012] tda827xa_set_params: could not write to tuner at addr: 0xc0
Feb  4 16:26:11 xxxxxxxxxxxx kernel: [336343.792012] tda827xa_set_params: could not write to tuner at addr: 0xc0
Feb  4 16:26:21 xxxxxxxxxxxx kernel: [336354.024023] tda827xa_set_params: could not write to tuner at addr: 0xc0
Feb  4 16:26:25 xxxxxxxxxxxx kernel: [336357.816013] tda827xa_set_params: could not write to tuner at addr: 0xc0
Feb  4 16:26:44 xxxxxxxxxxxx kernel: [336376.636022] tda827xa_set_params: could not write to tuner at addr: 0xc0
Feb  4 16:26:56 xxxxxxxxxxxx kernel: [336388.820010] tda827xa_set_params: could not write to tuner at addr: 0xc0
Feb  4 16:27:01 xxxxxxxxxxxx kernel: [336394.448011] tda827xa_set_params: could not write to tuner at addr: 0xc0

Guessing

In my Ubuntu 12.04 some process/driver is not succeeding in initiating the TV card hardware unless the said hardware has been warmed.  This could be indicative of failing power supply of the computer.
I'd like to learn what process is starting the TV card at start up so I can try re-running it to see if I can 'wake' the card.

---

