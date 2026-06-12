---
title: "Mythbuntu on AMD 780G or nV 8300"
date: 2009-01-01
forum: Mythbuntu
---

### Post by Gourmand on 2009-01-01
I'm thinking about HTPC using one of these chipsets. And I wanna make it with Linux (looks like Mythbuntu is good choice). But I'm not sure - can Mythbuntu itself ot with addon use hardware h.264/VC-1 decoding specifically on AMD 780G or nV 8300? I wanna get 1080p with HDMI output but use low power processor to make it noiseless and energy effective. There are different motherboards based on these chipsets. I don't wanna use dualcore AMD or Intel, but low level Sempron instead. 780G and nVidia 8300 both have h.264 and VC-1 hardware decoding. It works in PowerDVD 7.3 as well. But what about Mythbuntu? Can it use hardware decoding?

Or I have to look at another player? Can anybody suggest me one supporting hardware decoding on 780G or 8300?

---

### Post by mr_raider on 2009-01-01
Support for HD hardware acceleration on Myth and Mplayer is experimental on nvidia boards, and non-existent on ATI:

[http://www.phoronix.com/scan.php?page=article&item=xorg_vaapi_mplayer&num=1](http://www.phoronix.com/scan.php?page=article&item=xorg_vaapi_mplayer&num=1)

---

### Post by Entilzha on 2009-01-02
Dang, I was looking at creating a media center based on Mythbuntu and the Gigabyte GA-MA78GM-S2H which has the 780G. It seems to me that doesn't make a lot of sense if the HD acceleration isn't supported.

How do any of you guys handle the HD stuff if this doesn't work yet? You put in very powerful CPU's to compensate? It would be a pretty sad conclusion for me if a cheap 780G mobo plus a Windows license trumps a Mythbuntu system for cost.

---

### Post by Gourmand on 2009-01-02
not so good for me...

what is good - process goes on the road
what is bad - at least half of the year or more I have wait to get working solution :(

...I don't wanna Windows... I hate Vista, but XP I can use only non-licensed :confused:
I don't wanna waste money for operating system

the only way now - use dual core 3 GHz CPU - but this kills entire idea of cheap, noiseless and low energy consuming system

---

### Post by jape42 on 2009-01-02
The other thing you may need to investigate is support for multicore in the video players you plan on using.  In my original grandiose (but flawed) plan of building of a new mythfrontend  I came to realize that for 1080i files from my camcorder (.mts/avchd) mplayer/ffmpeg only supports a single core and is nowhere near being able to play these files on my AMD x2 5200. (ie 1  core is maxed out, the other is idle)


regards,

jp

---

### Post by Gourmand on 2009-01-02
I don't want use multicore

I want GPU acceleration on 780G or 8300 integrated video and nothing else

And all videos for me will have 720p or 1080p mostly h.264

---

### Post by newlinux on 2009-01-02
I have no problems playing 1080i content from my camcorder on my x2 3800. Both cores appear to be in use according to htop...

I can play pretty much all of my HD mpeg-2 (720p and 1080i) content on any of my non celeron processors in my signature and I don't use hardware acceleration on any. Pretty much any dual core can playback mpeg-2 HD content. h.264 is another story, but I routinely playback 720p h.264 on my X2 3800 and X2 4200, which are my primary mythfrontends, althought they are admittedly not the highest bitrate h.264 files around...

---

### Post by newlinux on 2009-01-02
> **Gourmand said:**
> I don't want use multicore

I want GPU acceleration on 780G or 8300 integrated video and nothing else

And all videos for me will have 720p or 1080p mostly h.264

Go with nvidia, VDPAU is coming along and offers acceleration for h.264. I don't know if the 8300 supports it or not.

---

### Post by Gourmand on 2009-01-02
found this:

> VDPAU is currently supported on the following NVIDIA GPUs:

Desktop GPUs:
GeForce 200 Series
GeForce 9 Series
GeForce 86xx Series
GeForce 85xx Series
GeForce 84xx Series
GeForce 8300 GS
GeForce 8800 GTS 512
GeForce 8800 GT
GeForce 8800 GS

Mobile GPUs:
GeForce 98xxM
GeForce 9700M
GeForce 96xxM
GeForce 9500M
GeForce 9300M
GeForce 9200M
GeForce 8800M
GeForce 8800M GTS
GeForce 8800M GTX
GeForce 8600M
GeForce 8400M

Motherboard GPUs:
GeForce 9400
GeForce 9300
GeForce 9100
[b]GeForce 8300
GeForce 8200[/b]


as I see it is just supported by only by mplayer and some patched libraries, but not by integrated media systems like MythTV

can MythTV use libavcodec, libavutil, ffmpeg patched for VDPAU?

I wanna use processor Sempron LE-1150 with 45W power consumption, 800 MHz bus and 128/256 Kbytes L1/L2 and 2.0 GHz clock with just only 2x512 DDR2 RAM (256 MB will be cut off by GPU) - is this enough for running Mythbuntu FE/BE? what about simultaneously bit-torrenting?

---

### Post by newlinux on 2009-01-02
You can configure mythtv to use standalone players for playing back video. I do this for some files where the internal player doesn't work so well. I know they are working on VDPAU support in the internal player for myth, but don't know when it will be available... I don't know what you can do about changing which libs the internal player uses without compiling it yourself...

You'd have to compile myth .22 on your own, VDPAU won't be available for .21...

[http://www.mythtv.org/wiki/index.php/VDPAU](http://www.mythtv.org/wiki/index.php/VDPAU)

VDPAU sounds good - unfortunately, none of my crusty old GPUs support it (I bought old cheap GPUs because hardware acceleration wasn't available in Linux at the time other than mpeg-2, which I didn't need cause my CPU could do it fine).

---

### Post by newlinux on 2009-01-02
The only thing that processor will struggle with is HD playback. If you get VDPAU working then it might playback h.264. I've seen good results with teh VDPAU acceleration, but I am by no means an expert :). without VDPAU, probably no shot a 1080i/p h.264 playback.

But for everything else (recording, SD playback, maybe even mpeg-2 720p playback, bit torrent, etc) that will probably be fine. with XvMC it could definitely playback mpeg-2 HD files.

---

### Post by Gourmand on 2009-01-02
sure I need hardware acceleration only for 1080 movies - but this is just about 10% of all HD movies around me, mostly they are 720p

even my old notebook with 1.7 GHz Celeron and Intel graphics plays 720p as well

but I never had a deal with MythTV and I don't know how much resources it needs for fast work

as I see - there could MythTV appear soon with native support of VDPAU - and what about Mythbuntu? When it could appear?

---

### Post by newlinux on 2009-01-02
BTW, what all do you want your media center to do? If you aren't interested in recording, you might want to look into XBMC. I use it back and forth with Mythtv and it looks great, and is much better and handling my video and music libraries. It can be configured to launch external players as well, so you could use it to launch a patched mplayer with VDPAU support. They too are still early on in implementing VDPAU in their native players...

---

### Post by newlinux on 2009-01-02
> **Gourmand said:**
> sure I need hardware acceleration only for 1080 movies

even my old notebook with 1.7 GHz Celeron and Intel graphics plays 720p as well

but I never had a deal with MythTV and I don't know how much resources it needs for fast work

as I see - there could MythTV appear soon with native support of VDPAU - and what about Mythbuntu? When it could appear?

Yeah but is that in windows or linux? Windows graphic drivers allow for much more of the CPU load to offput on the GPU, depending on the model and driver... 

I have a 1.6Ghz celeron laptop with intel graphics and it will not playback anything HD, even mpeg-2 recordings - running linux...

Mythbuntu is just ubuntu customized for mythtv with prebuilt mythtv packages. I don't have any idea when mythtv .22 will be officially released, but it is my guess that it won't be in mythbuntu until then, which is probably a ways off...

But you can always compile your own mythtv on ubuntu.

---

### Post by Gourmand on 2009-01-02
They say XBMC is quite far from hardware acceleration support... Idea use mplayer is not bad. But further I wanna install TV-tuner and get recording and timeshift options for SDTV.

> Mythbuntu is just ubuntu customized for mythtv with prebuilt mythtv packages

this is another issue for my interest of Mythbuntu - I don't wanna install and tune OS, then install and tune media system... I wanna install all by once

but I don't know yet - how hard it will be replace parts of installed Mythbuntu when hardware accelerated native player will be released

---

### Post by mr_raider on 2009-01-02
XBMC is even worse. They use an older ffmpeg codec for playback which supports dual core, but no GPU acceleration.

There are now patches available for VDPAU support on Myth Player, mplayer, xine and ffmpeg.

My suggestion is to get an AMD 5050e with 45W TDP (70$) and Geforce 8200 based mobo (90$). It will run anything up to and including 1080i/720p on CPU horsepower alone. It barely consumes more power than a Sempron. Once hardware acceleration for HD comes aorund you will be OK. 

The only caveat is getting HDMI to work this board is non trivial.

Don't be too enamored with hardware acceleration on windows. It's hit and miss, and not always trouble free. While DVXA functions are built into Windows Vista, on XP you need to buy proprietary software like PowerDVD 8 or Arcsoft to get PurevideoHD or AvivoHD acceleration. I think Media Player Classic Home Cinema has some acceleration abilities for h264.

---

### Post by newlinux on 2009-01-02
> **Gourmand said:**
> They say XBMC is quite far from hardware acceleration support... Idea use mplayer is not bad. But further I wanna install TV-tuner and get recording and timeshift options for SDTV.



this is another issue for my interest of Mythbuntu - I don't wanna install and tune OS, then install and tune media system... I wanna install all by once

but I don't know yet - how hard it will be replace parts of installed Mythbuntu when hardware accelerated native player will be released

If you want to record in the future, I'd definitely stick with myth. 

For me, installing ubuntu and then install mythtv using mythbuntu-control-centre wasn't any more difficult than installing mythbuntu (which will basically install those same packages). You'll pretty much have to tweak the same things. It's the same underlying OS just using XFCE instead of Gnome by default. The things that are tough to troubleshoot that involve configuring mythtv if you have a problem (video playback for one) will be the same either way.

But there are no issues with going with mythbuntu either. I was just pointing out what you could do if you wanted to run a later version of mythtv than ubuntu/mythbuntu has in their repository.

---

### Post by Gourmand on 2009-01-02
> **mr_raider said:**
> 
The only caveat is getting HDMI to work this board is non trivial.


what's a problem??
won't nVidia driver (180.16 or .18 ) just have an option which one output to use?

---

### Post by mr_raider on 2009-01-02
Actually 177.80 works fine. You need to upgrade Alsa and muck around with the settings.

---

### Post by Gourmand on 2009-01-03
Why not latest stable 180.16?

---

### Post by mr_raider on 2009-01-03
Feel free to try it. I'm just saying I got it to work with the default drivers.

---

### Post by Gourmand on 2009-01-03
currently I'm looking at MB ASUS M3N-H/HDMI (NVIDIA GeForce 8300 (MCP78U), LAN Atheros F1 10/100/1000, 1xATA133, 6xSATA II, 2x IEEE1394 LSI FW322, 8-channel HDA Realtek ALC1200, 1600-5200 bus) and processor AMD Athlon 64 LE-1600 Socket AM2 45W (Orleans, 2 GHz bus, 2.2 GHz clock, L1 128, L2 1024) and single 1024 DDR2 800 Mhz SDRAM Kingston 

calculation using extreme power calc gives me excellent result - power consumption with one SATA HDD and discrete video will be less than 120W on 70% system load (without optical drive, but with TV-tuner, low powered fan and 2 USB devices) - with integrated video it can be just about 110W (!) - looks like with just torrenting it can consume less than 100W! - this thing I could leave at home for 7x24 torrenting! 

looks good but I finally have decide - will this enough to play 720p/1080p and support all MythTV features in Linux or not...

---

### Post by mr_raider on 2009-01-03
My suggestion stands. Get a 4850e or 5050e. Until video acceleration on Linux is up to snuff, you will appreciate the power. Calculate the power consumption on those CPUs. It's not much worse than the Sempron.

---

### Post by Entilzha on 2009-01-03
Hmm, I did some research on this 780G thing.

If I understand correctly it uses UVD for hardware decoding of HD streams. Though catalyst 8.10 and higher support UVD in Linux, Mythbuntu doesn't know how to use it yet.

Though it looks like ppl are really working on it, there's no saying when it will be working. Thus I think that for my current HTPC build I'd better stick to nvidia, or even Windows, yuck...

---

### Post by Gourmand on 2009-01-03
> **mr_raider said:**
> My suggestion stands. Get a 4850e or 5050e. Until video acceleration on Linux is up to snuff, you will appreciate the power. Calculate the power consumption on those CPUs. It's not much worse than the Sempron.

I don't need 1080p decoding RIGHT NOW - I've got lot of movies in 720p or remuxed but just few of in 1080p

I need 1080p for future... Later I'll able change processor or run hardware acceleration on GPU.

But now Athlon 64 LE-1600 is twice cheaper than similar dualcore.

---

### Post by mr_raider on 2009-01-03
That's a reasonable approach. Make sure your board is AM3 compatible. Most 780g/8200s are though. Once the 45nm parts start trickling down, we may see some great HTPC CPUS. I wouldn't mind getting a Deneb (phenom II) variant of this sucker:

[http://www.newegg.ca/Product/Product.aspx?Item=N82E16819103300](http://www.newegg.ca/Product/Product.aspx?Item=N82E16819103300)

---

### Post by ZarathustraDK on 2009-02-10
> **Gourmand said:**
> I don't need 1080p decoding RIGHT NOW - I've got lot of movies in 720p or remuxed but just few of in 1080p

I need 1080p for future... Later I'll able change processor or run hardware acceleration on GPU.

But now Athlon 64 LE-1600 is twice cheaper than similar dualcore.

How about simply customizing Ubuntu with compiz? Something like utilizing the cube-effect for different functions (jukebox on one side, TV (with patched mplayer) on another, retro-gaming on a third, fileshares on a fourth etc. (I wouldn't know about TIVO-like abilities, never ventured that far)? The main-quip about Myth I've heard from some of my buddies who have ventured into customized HTPC-building is that it is kind of low on the eye-candy-side compared to Windows media-center.

Then have it all auto-startup in predefined positions (is that possible w/ compiz?).

I mean, Compiz-fusion is the biggest wow-factor Open Source has on the 'uninitiated'. What better place to put it than on a big-*** TV for all visitors to see?

---

### Post by Gourmand on 2009-02-11
> **ZarathustraDK said:**
> How about simply customizing Ubuntu with compiz? Something like utilizing the cube-effect for different functions (jukebox on one side, TV (with patched mplayer) on another, retro-gaming on a third, fileshares on a fourth etc. (I wouldn't know about TIVO-like abilities, never ventured that far)? The main-quip about Myth I've heard from some of my buddies who have ventured into customized HTPC-building is that it is kind of low on the eye-candy-side compared to Windows media-center.

Then have it all auto-startup in predefined positions (is that possible w/ compiz?).

I mean, Compiz-fusion is the biggest wow-factor Open Source has on the 'uninitiated'. What better place to put it than on a big-*** TV for all visitors to see?

nice idea... but it would be twice nice if it's possible use a kinda of "space mouse" - to rotate cube by moving hand or something in the air - like in Nintendo Wii 

I know such software to use with webcam on Windows ([it's here](http://www.camspace.com/)) - but not for Linux :(

anybody knows?

---

### Post by ZarathustraDK on 2009-02-20
> **Gourmand said:**
> nice idea... but it would be twice nice if it's possible use a kinda of "space mouse" - to rotate cube by moving hand or something in the air - like in Nintendo Wii 

I know such software to use with webcam on Windows ([it's here](http://www.camspace.com/)) - but not for Linux :(

anybody knows?

Something like this maybe? [http://www.logitech.com/index.cfm/mice_pointers/mice/devices/3443&cl=US,EN]("http://www.logitech.com/index.cfm/mice_pointers/mice/devices/3443&cl=US,EN"). It's a bit pricey, but magic wands like that should be ;)

---

### Post by PelleGris on 2009-02-20
A little side note:
I just purchased an nv-8300 based board, because I was unable to get an acceptable picture quality with an ATI-690G on my plasma. I also tried with an ATI-2600XT, but it seems to me that the nv-drivers are much better linux wise.

Regards

PelleGris

---

### Post by Gourmand on 2009-02-20
> **ZarathustraDK said:**
> Something like this maybe? [http://www.logitech.com/index.cfm/mice_pointers/mice/devices/3443&cl=US,EN]("http://www.logitech.com/index.cfm/mice_pointers/mice/devices/3443&cl=US,EN"). It's a bit pricey, but magic wands like that should be ;)

very nice but a little expensive...

[this](http://www.gyration.com/?l=uk#productDetail/office/goMouse) looks cheaper

but I talk about software using web-cam to recognize specific motion to control mouse

---

### Post by newlinux on 2009-02-20
> **Gourmand said:**
> nice idea... but it would be twice nice if it's possible use a kinda of "space mouse" - to rotate cube by moving hand or something in the air - like in Nintendo Wii 
...

I've got a gyro mouse that can do just that...

[http://reviews.cnet.com/mice/gyration-go-2-4/4505-3148_7-31428447.html](http://reviews.cnet.com/mice/gyration-go-2-4/4505-3148_7-31428447.html)

Got it off ebay...

EDIT: didn't see the previous post... Yeah, that's the same mouse I have...

---

### Post by sampaio on 2009-09-18
It is planned to support the series7?   Nvidia (7600GS)   I planned to use my old 7600 card in my HTPC with XBMC ...    Thanks

---

