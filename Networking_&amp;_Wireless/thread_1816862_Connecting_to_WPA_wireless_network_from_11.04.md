---
title: "Connecting to WPA wireless network from 11.04"
date: 2011-08-02
forum: Networking &amp; Wireless
---

### Post by galtech on 2011-08-02
Hi there, 

I have recently upgraded my laptop to Ubuntu 11.04 from 10.10. 
I am having a problem connecting to wireless networks using WPA security (in work). At home, I can connect without any problem to my own wireless connection which uses WEP security. 

Has anyone got any ideas for what I could try so that I can connect to WPA wireless networks? 

Below is some information that may be of help. 
Also, the laptop can see the network in work, but it cannot connect. It continually asks for the key. I have entered the correct key on each occasion with no joy. Any help would be very much appreciated. 

```
peter@peter-laptop:~$ lspci -nn | grep 0280
peter@peter-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17335  0 
fat                    55505  1 vfat
cryptd                 19801  0 
aes_i586               16956  0 
aes_generic            38023  1 aes_i586
binfmt_misc            13213  1 
savage                 35490  2 
drm                   180037  3 savage
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
thinkpad_acpi          73750  0 
arc4                   12473  2 
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
rt73usb                26854  0 
crc_itu_t              12627  1 rt73usb
pcmcia                 39671  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
rt2500usb              22621  0 
snd_timer              28659  2 snd_pcm,snd_seq
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
rt2x00usb              19693  2 rt73usb,rt2500usb
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
rt2x00lib              39075  3 rt73usb,rt2500usb,rt2x00usb
mac80211              257001  2 rt2x00usb,rt2x00lib
nsc_ircc               23199  0 
video                  18951  0 
psmouse                73312  0 
irda                  185091  1 nsc_ircc
cfg80211              156212  2 rt2x00lib,mac80211
serio_raw              12990  0 
snd                    55295  12 snd_intel8x0,snd_ac97_codec,thinkpad_acpi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
shpchp                 32345  0 
soundcore              12600  1 snd
ppdev                  12849  0 
nvram                  14035  1 thinkpad_acpi
parport_pc             32111  1 
crc_ccitt              12595  1 irda
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usb_storage            43946  0 
e100                   40108  0 
uas                    17676  0 
floppy                 60032  0 
peter@peter-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
peter@peter-laptop:~$ rfkill list all
1: phy3: Wireless LAN
	Soft blocked: no
	Hard blocked: no
peter@peter-laptop:~$ ^C
peter@peter-laptop:~$ 

```

Update 03.08.2011: I noticed there was a build up of wireless connections of the same name in the list (might have been the failed attempts). I deleted all these connections of the same name and when I switched on the laptop in work this morning I was prompted with a message stating that there were wireless connections available. I selected the one I wanted and entered the key and success: I am connected.

---

