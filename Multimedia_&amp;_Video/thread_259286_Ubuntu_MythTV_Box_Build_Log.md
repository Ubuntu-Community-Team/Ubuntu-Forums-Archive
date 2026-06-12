---
title: "Ubuntu MythTV Box Build Log"
date: 2006-09-17
forum: Multimedia &amp; Video
---

### Post by drews_blunted on 2006-09-17
I am going to be building a Ubuntu Media/Home Theatre Computer.
The computer will run mythtv as well as various games in mythgames/rip + encode / burn cds/dvd, browse the internet, check weather, read news, listen to music, browse my collection of divx movies on my computer. wireless keyboards as well as game pads & many other things that work with mythtv. 

So far i have ordered the following hardware:
(i already have a SATA + Ram)

BIOSTAR TForce6100 Socket 754 NVIDIA GeForce 6100 Micro ATX AMD Motherboard 
AMD Sempron 64 2800+ Palermo 1.6GHz Socket 754 Processor Model SDA2800BXBOX
Hauppauge WinTV-PVR-150 MCE PCI Interface 1042 Tuner Card
SILVERSTONE LASCALA SST-LC11B-M Black Aluminum front panel, 0.8mm SECC body HTPC case Computer Case TFX 240W PFC Power Supply
Western Digital Caviar SE WD800JD 80GB 7200 RPM SATA 3.0Gb/s Hard Drive
LITE-ON 16X DVD±R DVD Burner W/LightScribe and 5X DVD-RAM Write Black ATAPI/E-IDE Model SHM-165H6S

I have had have average success with installing and setting up mythtv beore but may run into a couple problems on the way. 

I will be uploading some pictures as soon as i have the thing built.

:D 

Please feel free to leave any comments and or sudgestions or tips for building a linux based PVR/Home theatre system.

---

### Post by drews_blunted on 2006-09-17
[img]http://images10.newegg.com/NeweggImage/productimage/11-163-046-01.JPG[/img]

[img]http://images10.newegg.com/NeweggImage/productimage/11-163-046-08.JPG[/img]

---

### Post by drews_blunted on 2006-09-25
Ok, so my project has had some ups and downs and i have gotten alot of good help from reading posts on the ubuntu forum and elsewhere on the internet. I have found the mythtv website to have alot of good info including directions on how to setup mythtv 0.20 on ubuntu dapper, as well as practicaly every plugin available.

Ive run into a couple last problems. 

The first one is Lircd. I have the program installed i just dont think i have configured it correctly the program starts and works fine, i have just never gotten it to work. i am using the ir device that came with my case as well as the tv changer/controller that came with the case below:
[http://www.silverstonetek.com/products-lc11m.htm](http://www.silverstonetek.com/products-lc11m.htm)

Im not sure if installing irblaster would help? is this needed and would this be my solution?

The webpage has a link to this tutorial witch is suposed to help me out but i have not gotten it to work and irw has yet to give me any output.
[http://venky.ws/projects/imon/](http://venky.ws/projects/imon/)

My second problem is getting the small lcd screen on my computer to do something, i know its plugged in cause i can see the lights are on, but i am yet to figure out how to fully get this feature working in ubuntu dapper. 

The Third issue is a small problem i am having with mythtv and my tv card.

here is the output ivtv drivers
[4294694.316000] ivtv:  ==================== START INIT IVTV =================== =
[4294694.316000] ivtv:  version 0.4.6 (tagged release) loading
[4294694.316000] ivtv:  Linux version: 2.6.15-23-386 preempt 486 gcc-4.0
[4294694.316000] ivtv:  In case of problems please include the debug info betwee n
[4294694.316000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[4294694.316000] ivtv:  any module options, when mailing the ivtv-users mailingl ist.
[4294694.489000] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[4294694.489000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[4294694.536000] tveeprom: ivtv version
[4294694.536000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4294694.552000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver # 0
[4294694.552000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[4294694.730000] cx25840 0-0044: ivtv driver
[4294694.730000] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[4294697.890000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[4294697.920000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[4294697.928000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[4294697.944000] tda9887 0-0043: (ivtv) chip found @ 0x86 (ivtv i2c driver #0)
[4294697.944000] ivtv0: i2c attach to card #0 ok [client=tda9887, addr=43]
[4294698.615000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[4294698.835000] ivtv0: Encoder revision: 0x02050032
[4294698.835000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4 096KB total)
[4294698.835000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (20 48KB total)
[4294698.835000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (20 48KB total)
[4294698.835000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffer s (2048KB total)
[4294698.836000] ivtv0: Create encoder radio stream
[4294698.836000] tuner: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F) ) by ivtv i2c driver #0
[4294698.931000] ivtv0: Initialized WinTV PVR 150, card #0
[4294698.931000] ivtv:  ====================  END INIT IVTV  =================== 

So im assuming this is a problem with mythtv because it looks like my tv cards working perfectly.

My problem is im not alowed to access the tv card and i get the error in myth tv of:

mythtv is already using all available inputs for the channel you selected, if you want to watch an in-progress recording select one from the playback menu. If you want to watch livetv cancel one of the in-progress recordings from the delete menu.

Im not sure what that means, i have no recordings going and have yet to even dig into the recording tv shows side of mythtv. 

I might add that, my tv card did work but now i am getting this error. Mostlikely because i have done something to messup the configuration.

---

### Post by drews_blunted on 2006-09-26
I have managed to fix my tv card. seems i forgot i set mythbackend to start at boot and was running it twice. 

I still cannot seem to get my remote control to work?

Has anyone ever gotten a controller to work in ubuntu?

Will amyone even respond to my thread? so far no responses?

---

### Post by munzli on 2006-09-29
well the imon stuff works quite well...

maybe this will help: [http://www.jonobacon.org/?p=579](http://www.jonobacon.org/?p=579)

---

### Post by GG_HTPC on 2007-07-06
Thank you for your post. I am trying to setup a MythTV system as well on Ubuntu 7.04. (New to Ubuntu). 

I have a Silverstone LC20 case with built-in iMon/VFD. I followed (I hope) all the instructions on your post and was able to test the driver in Mode2. I could see the remote hex output. But after that no luck, may be I missed doing a step or copying the files somewhere.

Any pointers?

Thank you in advance.

---

### Post by spinlock99 on 2007-11-20
Hi There,

> **drews_blunted said:**
> 

My problem is im not alowed to access the tv card and i get the error in myth tv of:

mythtv is already using all available inputs for the channel you selected, if you want to watch an in-progress recording select one from the playback menu. If you want to watch livetv cancel one of the in-progress recordings from the delete menu.

Im not sure what that means, i have no recordings going and have yet to even dig into the recording tv shows side of mythtv. 

I might add that, my tv card did work but now i am getting this error. Mostlikely because i have done something to messup the configuration.

I'm having the exact same problem.  How did you fix this?

Thanks,
Andrew

---

### Post by skerdoba on 2007-11-21
I have the same problem also.  I googled "mythtv is already using all available inputs" and found one other usable post on a MythDora forum at g-ding.tv which suggested to delete your video sources and set them up again. I tried that and it seems to work the first time, but the problem returns after every reboot.  I wonder if the problem has anything to do with the fact that I'm using an HDHomeRun, which is an external capture device that feeds an MPEG2 stream to MythTv over ethernet, rather than using a PCI card.  However if you're using a PCI capture card then that would blow my theory out of the water.  We at least know the problem is not restricted to Mythbuntu builds; I'm surprised there aren't more reports of this problem from others.

---

