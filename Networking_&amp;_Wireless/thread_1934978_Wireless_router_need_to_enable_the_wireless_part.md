---
title: "Wireless router need to enable the wireless part"
date: 2012-03-03
forum: Networking &amp; Wireless
---

### Post by rapattack1 on 2012-03-03
Hi i just plugged in a Belkin N1 wireless router and the ethernet part works right away but the wireless part not. I have no clue how to enable wireless on anything. I looked at the Network Connections>wireless tab and saw that someones connection is there that hasn't been used for a year. I got this from someone that has no tech knowledge so no use asking him. So do i delete his connection and create a new one? If so what do i fill in? This is the manufacturers  page on this model [http://www.belkin.com/IWCatProductPage.process?Product_Id=299175](http://www.belkin.com/IWCatProductPage.process?Product_Id=299175)

---

### Post by praseodym on 2012-03-03
Hi,

what hardware is in use? Please show
```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by rapattack1 on 2012-03-03
```
carla@carla-desktop:~$ lspci -nnk | grep -iA2 net
00:07.0 Bridge [0680]: nVidia Corporation MCP61 Ethernet [10de:03ef] (rev a2)
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth
carla@carla-desktop:~$ lsusb
Bus 002 Device 005: ID 0e8f:0021 GreenAsia Inc. 
Bus 002 Device 004: ID 17a0:0001  
Bus 002 Device 002: ID 04f3:0230 Elan Microelectronics Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 012: ID 05e3:070e Genesys Logic, Inc. X-PRO CR20xA USB 2.0 Internal Card Reader
Bus 001 Device 011: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 010: ID 046d:08d7 Logitech, Inc. QuickCam Communicate STX
Bus 001 Device 009: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
carla@carla-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
dm_crypt               11331  0 
snd_usb_audio          75765  2 
snd_usb_lib            15801  1 snd_usb_audio
sbp2                   19448  0 
joydev                  8740  0 
ppdev                   5259  0 
parport_pc             25962  1 
snd_emu10k1_synth       5156  0 
snd_emux_synth         31695  1 snd_emu10k1_synth
snd_seq_virmidi         4213  1 snd_emux_synth
snd_seq_midi_emul       5492  1 snd_emux_synth
snd_emu10k1           131163  3 snd_emu10k1_synth
snd_ac97_codec        100646  1 snd_emu10k1
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  4 snd_usb_audio,snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          7076  2 snd_emu10k1,snd_pcm
snd_util_mem            3106  2 snd_emux_synth,snd_emu10k1
snd_hwdep               5412  3 snd_usb_audio,snd_emux_synth,snd_emu10k1
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  4 snd_usb_lib,snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      6003  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                47263  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          5700  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
gspca_zc3xx            45189  0 
gspca_main             21199  1 gspca_zc3xx
videodev               34425  1 gspca_main
v4l1_compat            13251  1 videodev
snd                    54244  22 snd_usb_audio,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia               9961216  32 
emu10k1_gp              1492  0 
lp                      7028  0 
psmouse                63677  0 
serio_raw               3978  0 
agpgart                31724  1 nvidia
soundcore               6620  1 snd
gameport                9089  2 emu10k1_gp
parport                32635  3 ppdev,parport_pc,lp
i2c_nforce2             5199  0 
usb_storage            40033  0 
ohci1394               26950  0 
usbhid                 36110  0 
hid                    67288  1 usbhid
ieee1394               81181  2 sbp2,ohci1394
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
forcedeth              49556  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
pata_amd                8766  0 
sata_nv                19376  6 
ramzswap                6362  1 
xvmalloc                4074  1 ramzswap
lzo_decompress          2189  1 ramzswap
lzo_compress            1853  1 ramzswap
carla@carla-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

carla@carla-desktop:~$ rfkill list

```

---

### Post by praseodym on 2012-03-03
I dont see a wireless device?! Neither a PCI- nor an USB-device?!

---

### Post by rapattack1 on 2012-03-03
I posted the model of the device above....i don't know as i have never used a wireless router before :0)

---

### Post by praseodym on 2012-03-03
Your comp obviously does not have a wireless device?! Do you have a WLAN-stick? Was it plugged for "lsusb"?

---

### Post by linux6994 on 2012-03-03
Since you are communicating to and through your N1 wireless router the next step is to log on to the N1 wireless router to enable and configure the wireless as you wish.

In firefox go to 192.168.1.1, you will see a logon screen for the N1 wireless router, leave password blank and hit submit. You can then configure the router as you wish.

[http://www.belkin.com/support/download/files/F5D8231-4v1_manual.pdf](http://www.belkin.com/support/download/files/F5D8231-4v1_manual.pdf)

---

### Post by rapattack1 on 2012-03-04
Hi thanks that sounds right....it says though problem loading page' so i can't log into the router. Maybe i have to take it back to the factory setting or something? I have logged into modems before but never knew how to enable the wireless part so always left it.

---

### Post by rapattack1 on 2012-03-12
OK sorry finally got round to logging into the router well after i looked at the manual. It was 192.168.2.1 btw! Anyway i am in but i did something wrong the first time because i thought i was enabling the wireless part and it seemed to but the lights on the modem indicated wifi only plus the net went down on my computers. I use ethernet for two computers and wanted the wifi for the smartphone only. Anyway so i had to reset or restore the router and that got me back on the net. Geez i didn't know what i was doing. Anyway there are so many parts to this router. Do you know if i can enable both ethernet and wifi?

---

### Post by praseodym on 2012-03-12
Check, if the MAC-address filter is turned on.

---

### Post by rapattack1 on 2012-03-13
O'ops sorry just after i posted i was able to enable both wifi and ethernet by doing a hard reset? I think thats what i did. Trouble is now there is no key/security so the internet is open to anyone. I gather that there are several ways to do the security but i have no clue what to choose as i don't know what is the most secure.

---

### Post by rapattack1 on 2012-03-16
My router is a Belkin N1 if anyone knows how to put a password on this model? I just don't understand it. I have logged into the router but nothing makes sense to me. I tried to do it before but then i couldn't get any internet at all until i did the reset thing again!

---

### Post by praseodym on 2012-03-17
Type in the router IP into your browser while connected via cable. In the interface you can change the encryption, turn on the firewall, etc.

---

### Post by rapattack1 on 2012-03-18
Sorry i need more info. As i said i can't understand it. I am logged in so i need more info. Can someone please read the manual for me as there are too many pages and i got it wrong before and wasn't able to get on the net

---

### Post by praseodym on 2012-03-18
I also have a Belkin-Router. Type in your browser

[http://IP.Address.of.Router](http://IP.Address.of.Router)
Check the IP address from the manual (here it is [http://192.168.2.1](http://192.168.2.1) )

---

### Post by rapattack1 on 2012-03-19
Sorry this is the third time i am saying i can log into the modem. Can i be more clear? I need info in order to turn security on or whatever the wording is. So if i want to access the wifi part i have to type in a password on the device i am using say my blackberry or iphone. Clear? :0)

---

### Post by kurt18947 on 2012-03-19
If I may intrude, You bought this from someone, correct?  If so, I'd press and hold for several seconds  the 'reset' button on the back first off.  Let it restart. Then unplug for at least 30 seconds.  Plug in, let the router start up then press and hold the 'reset' button again.  This may be overkill but should take less than 5 minutes total.  This should remove any custom settings by its previous owner.  I can open the linked manual but for some reason evince shows clear text but pictures and screen caps get blurry when zoomed enough to actually see.  Here is another reference page:

[http://en-us-support.belkin.com/app/answers/detail/a_id/7014/~/belkin-n1-wireless-router---user-guide]("http://en-us-support.belkin.com/app/answers/detail/a_id/7014/%7E/belkin-n1-wireless-router---user-guide").  Links to manuals for various versions are on the bottom.  To turn on/turn off wireless, log onto the router, [http://192.168.2.1](http://192.168.2.1).  After restoring factory settings, there will be no password unless you've entered one (you should), then wireless -> channel/SSID.  To enable/disable wireless, click the "wireless mode", one option should be "off".  Here is a screen shot from the v3 manual:
[ATTACH]214553[/ATTACH]

You can also set your own SSID which is a name for your wireless network.  Don't use anything personally identifiable like your name or address.  Of course if you're the only house within a kilometer it probably doesn't matter :).  The preferred encryption is WPA2 if all devices support it.

I just re read your post.  To select security, on the left side of the screen below my circled entry is "security". If you can click on it, a window should open where you can enter your preferred stuff.

---

### Post by rapattack1 on 2012-04-08
Hi oh this is odd. I wasn't notified of your email. Ok you might not have read the whole thing. I can access wifi! I need to set a password. I do not understand the settings so can't do it without someone helping me. I have read everything over and over and it did my head in. Sorry i know you are trying to help but i can't understand this stuff. I don't know the difference between ss whatever and whatever technologies that are used for wifi. I have tried for years to understand and its just not my field.

---

