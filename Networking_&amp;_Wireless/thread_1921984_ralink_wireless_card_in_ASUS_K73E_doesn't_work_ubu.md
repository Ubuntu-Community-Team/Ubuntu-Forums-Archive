---
title: "ralink wireless card in ASUS K73E doesn't work ubuntu 10.04"
date: 2012-02-07
forum: Networking &amp; Wireless
---

### Post by gringo loco on 2012-02-07
I just installed 10.04 in my new Asus K73E and everything seems to be working great except my Internet connection (wireless). Can anyone tell me where I might find a driver for the installed Ralink 820.11n wireless LAN card. I asked Asus for more information on the card and available drivers and all they could tell me was "We do not support Linux."

any ideas would be helpful because I really hate windows 7 and as soon as I can get connected through ubuntu I can get rid of it entirely.

---

### Post by barong234 on 2012-02-08
maybe this link can help you out [http://ubuntuforums.org/showthread.php?t=960642](http://ubuntuforums.org/showthread.php?t=960642)

---

### Post by gringo loco on 2012-02-14
No luck on that one, thanks.
I'm thinking I might just sell this machine to someone who likes Windough$ (do you know anyone in Central America who wants a brand new ASUS cheap) and buy another brand that works with Linux, but until then I suppose I'll just use Windows for Internet and Ubuntu for everything else. At least my "everything else" won't get infected that way.

---

### Post by josephmills on 2012-02-14
Hello there could you please open your terminal (ctrl+alt+t) then enter in 
```
lspci -nn && lsusb && lsmod && rfkill list all 
``` 
then paste here (just need some more info)thanks

---

### Post by gringo loco on 2012-02-14
di,snd_seq

snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

uvcvideo               57374  0 

videodev               34361  1 uvcvideo

v4l1_compat            13251  2 uvcvideo,videodev

soundcore               6620  1 snd

snd_page_alloc          7076  2 snd_hda_intel,snd_pcm

psmouse                63677  0 

serio_raw               3978  0 

lp                      7028  0 

parport                32635  2 ppdev,lp

fbcon                  35102  71 

tileblit                1999  1 fbcon

font                    7557  1 fbcon

bitblit                 4707  1 fbcon

softcursor              1189  1 bitblit

video                  17375  0 

output                  1871  1 video

vga16fb                11385  1 

vgastate                8961  1 vga16fb

ahci                   32360  2 

ben@Benasus:~$

---

### Post by UltimateCat on 2012-02-14
There website is:

[www.ralinktech.com](www.ralinktech.com)

I found the driver I need there

Best regards

---

### Post by gringo loco on 2012-02-15
> **UltimateCat said:**
> There website is:

[www.ralinktech.com](www.ralinktech.com)

I found the driver I need there

Best regards
Yes, I found the driver page there but I have no idea which one I need and they have not replied to my inquiry. ASUS can't tell me what the Ralink product model number is and all the drivers are listed by product model number.

---

### Post by gringo loco on 2012-02-17
Thank You all for your help and suggestions. I have now found a driver at Ralink that I think is the right one. I believe the wireless card is a RT5390 and ralink have a Linux driver for that. I have downloaded it (using my connection via Windows 7 and then moving it into Ubuntu's files) it is a tar.bz2 and so far I have not been able to figure out what to do to get it installed. Does anyone have a "how to for dummies" that I can follow to get this driver installed????

---

### Post by gringo loco on 2012-02-18
OK I think I have all the information I need. It is probably going to take me a little while to implement it all. The basics are well laid out in the following post. Thanks to all the people who helped, both here and at Ask Ubuntu. 

[http://ubuntuforums.org/showthread.php?t=1645716](http://ubuntuforums.org/showthread.php?t=1645716)

---

### Post by pcorazao on 2012-02-21
i have that same laptop, download this(RT2860) driver:

IS_AP_STA_RT2860_D-3.2.7.0_VA-3.2.7.0_W7-3.2.7.0_RU-4.1.4.0_AU-4.1.2.0_112311_1.5.16.0WP_Free.exe

you can follow along with this to get it working.

[http://www.howtogeek.com/howto/43752/how-to-install-a-wireless-card-in-linux-using-windows-drivers/](http://www.howtogeek.com/howto/43752/how-to-install-a-wireless-card-in-linux-using-windows-drivers/)

note this is the windows 7 version of the driver, once extracted look for the win 32 INF driver.

---

### Post by pcorazao on 2012-04-03
BTW i tried out the 12.04 beta and it found the wireless card right off the bat, and it works great.

---

