---
title: "Making DVD for Sony dvd player"
date: 2012-02-25
forum: Multimedia Software
---

### Post by meduser on 2012-02-25
Hi, I am running Kubuntu 11.10. I am trying to make some DVD's for my kids, and I am having a hell of a time.

I started out like this:

```
Well, I don't know what I am doing wrong. I am trying to burn a copy of a movie. The file is in AVI format. 
I have tried K3B, get instant error. I have tried Brasesro, same issue. 
I have tried NeroLinux, and get same issue. As soon as I click burn, I get an error, and the DVD ejects.
I am trying to put family movies over to DVD. They play just fine in VLC as an AVI, but as soon as
I try to burn..get an error. 
I am sure I am missing something that needs to be installed. any help is appreciated.
Nero says burn process failed. It doesn't even start to burn the file
```

Then I tried this:

```
I would like to make a video dvd. 

I try K3b, and it runs for all of 2 seconds, and I get an error. 
I also have tried Brasero. Same thing. I add the image which I created using ffmpegx. 
It plays just fine in VLC..sound and video is awesome. 
I have tried both AVI and ISO and get the same reaction each time.

My burner is a brand new..ok not brand new..I have used it twice since I bought it 2 weeks ago. 
It is a LG MODISC, supermulti. It can right DVD's just fine. It is a SATA drive also. 
Fully detected in Kubuntu...I have installed the "restricted " stuff after a clean install of Kubuntu 11.10.
 and still have the same issue. I have also tried Devede with the same result. 
It is like I don't have the right setting for it. 
I am a newbie with Linux, and have only been using it for 4 weeks.

```

My DVD is present, and does work:

```
/dev/dvd:

ATAPI CD-ROM, with removable media
        Model Number:       HL-DT-ST DVDRAM GH22NS90                
        Serial Number:      KFGB9G85408         
        Firmware Revision:  HN00S300
        Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
Standards:
        Likely used CD-ROM ATAPI-1
Configuration:
        DRQ response: 50us.                                                                                            
        Packet size: 12 bytes                                                                                          
        cache/buffer size  = unknown                                                                                   
Capabilities:                                                                                                          
        LBA, IORDY(can be disabled)                                                                                    
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    PACKET command feature set
           *    Look-ahead
           *    DEVICE_RESET command
           *    NOP cmd
                Removable Media Status Notification feature set
           *    64-bit World wide name
           *    Gen1 signaling speed (1.5Gb/s)
           *    Phy event counters
                Asynchronous notification (eg. media change)
           *    Software settings preservation
```

I have tried to run:

```
growisofs -Z /dev/sr0 -dvd-video /path/video1 /path/video2 /path/video3
```

which gives me :

```
 it returned errors saying that it could not find the audio or video file. 
I checked the path location, and copied it over, and I tried an ISO of a movie, and got the same thing.
```

I downloaded devede, and tried to make an iso. that does create, but when I burn it to DVD and place in my player, it registers as a DVD-r, but says it cannot play it.

My DVD player is actually a Sony s360 bluray, and can play burnt movies, as I have done that before in Windows with no issues.

I tried to make the audio and video files in DEVEDE for K3B to make a video DVD, and it only seems to create the video files, and no sound, and if I burn that, it says DVD-r in Sony, and will not play. I am sure I am just not setting things up right, as others have great success at making DVD's. Please help me. I am going bonkers.

---

### Post by inobe on 2012-02-25
before you get into any of that, have you been here.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

and of course it's important to understand the steps.

[http://www.dedoimedo.com/computers/devede.html](http://www.dedoimedo.com/computers/devede.html)

note: PAL format is for countries outside the u.s.

---

### Post by meduser on 2012-02-25
> **inobe said:**
> before you get into any of that, have you been here.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)


Yes and it is installed. I installed Kubuntu fresh install, then sudo apt-get update, sudo apt-get upgrade, then sudo apt-get install ubuntu-restricted-extras

shows this :

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```

and of course it's important to understand the steps.

[http://www.dedoimedo.com/computers/devede.html](http://www.dedoimedo.com/computers/devede.html)

note: PAL format is for countries outside the u.s.

I have it set to NTSC.
checking out the steps now..thank you

---

### Post by meduser on 2012-03-02
Still can't get this to work.
Anyone with any ideas?

I have tried to use ffmpeg to make a mpeg file. I have the file made. It is 2.3gbs in size. I have tried to burn that to my dvd, but it still doesn't play in my dvd player. Any help is appreciated.
Thanks
Med

---

### Post by inobe on 2012-03-02
maybe your missing a step in the .iso creation process!

that said

1) what is the file format you are starting with, is it a .mp4.... .mkv..?

2) what steps settings did you use to create the .iso?

maybe the dvd becomes corrupted somehow!

try this method instead [http://www.ghacks.net/2009/03/20/create-dvds-in-linux-with-devede-mkisofs-and-k3b/](http://www.ghacks.net/2009/03/20/create-dvds-in-linux-with-devede-mkisofs-and-k3b/)

---

### Post by BicyclerBoy on 2012-03-02
Just to clarify..
The OP is trying to make a **DVD data** disc containing video in some format that his/her BD player will directly read/play.

The OP could make a **DVD-Video** disc but this has very specific requirements for format/bitrate/menu structure etc & likely results in loss of picture quality & run-time.

One way to work out the supported video codec /container formats for the S%&# player, on a data disc, is to check out the published specs or find it on the AV HT forums..

Some of the better players support h264 in mkv & play mpeg2-ts (dvb recordings) & m2ts (BD & AVCHD).

---

### Post by meduser on 2012-03-02
My bluray player does play burnt discs as I can play discs made in Windows with no issues.

I am starting with a variety of files. I have tried MKV, AVI, and ISO.

I have tried to use K3B to burn. It burns fine, but the dvd just registers as a DVD-r in the bluray player.

I have tried Devede, and have made both ISO's and audio and video folders. Same result as above.

I have tried ffmpeg through the terminal, and it created a 2.4gb mpeg file, and when I burn that image, same result...the Bluray player just says dvd-r.

I am sure I am missing a step, or doing something wrong, as many others have had success doing this exact thing. I am going to read over the link you posted and see what I am doing wrong. I have been to the IRC boards for Kubuntu, and spent hours with Bluekaj trying to get this to work, and it won't at this point.

---

### Post by meduser on 2012-03-02
Ok, trying this again. One thing I have not done previously is click the Advanced options drop down to reveal a few more options. In this section you want to select the option “Create Disk Structure”. Hopefully this works...I'll post back when it is done. Thanks for the help..it is much appreciated.;P

---

### Post by meduser on 2012-03-02
Alright..that worked. The difference seemed to be the select the option “Create Disk Structure”.

Thanks for the help, and the link. That was a good read.Thanks you.

---

### Post by inobe on 2012-03-02
your welcome, thanks for marking thread solved.

---

