---
title: "Help with new Mythbuntu setup"
date: 2011-01-27
forum: Mythbuntu
---

### Post by larry_bg on 2011-01-27
Hello, I have old Dell Optiflex GX220 Intel Pentium 4 CPU 2.80GHz with 2GB memory that I would like to use with Mythbuntu for my home setup with Comcast digital cable. I’m new to this and don’t know what kind of hardware I should additionally to buy to make it happen, and what the setup should be. Will this configuration enough to record and play HD movies, if no what is the preferred hardware would be? 



Can you help with this?


Thanks,
Larry

---

### Post by nhtrader on 2011-01-27
I just got mythtv up and running two days ago with the help of everyone here in this forum. I downloaded the latest version from their site a week ago mythbuntu 10.10 (32bit). It works great.

If you have a CD/DVD-ROM installed on your system, you should be ok. You can play standard DVDs which is no problem. HD movies, well that's a loaded question because, you really meand HDVD or Bluray? If you mean BluRay, then you need a Bluray player on you computer system. As for HDVD (toshiba format), Bluray players don't play HDVD and so you can't play HD movies. However, playing Bluray movies will be fine. Also, viewing HD Tv will be fine and so is recording HD TV.

I'm also a comcast customer and it looks like you just need a tuner card that can interpret the QAM signal (digital TV and HD TV over cable). BTW, ATSC means using an antenna or over the air (OTA). And NTSC is for the old TV broadcast signal which is no longer broadcast over the air. Comcast still sends NTSC for those who wish to use their old CRT based TVs. So in summary your mainly interested in recording QAM channels. Your new tuner card must be able to receive QAM channels. 

Lastly, this is important. I can only record unencrypted channels (2-34). I don't have a premium cable package so I don't know how it works with encrypted premium channels.

I'm using a Happauge HVR-1250 tuner card which is able to record 2 programs simultaneously even though it is a single tuner card. (It has to due with using a multiplexed signal.) This was completely unexpected and surprised me. It's an older model, but as you can see it does more than what is reported in the product spec sheet. 

However, your hardware may not support recording 2 programs simultaneously. But it should record 1 no problem.

I only record the new digital channels using the new broadcast standard ATSC. So can't speak for the old NTSC, or analog recording.

The beauty of mythtv is that it only costs you the time to set it up, which will take awhile. So give it a whirl. I'd suggest starting out with a new Hard Disk Drive, or use an empty one, or one that can be erased. Recording HD TV requires a lot of HDD space. Typically 6 Gb per hour.

---

### Post by larry_bg on 2011-01-27
Thanks for the info. Is there a list of suggested video cards and tuners? Will I be able to use my box for both front and backend? I cannot find any graphical schema how cables should be connected, is there any available?

Thanks.
Larry

---

### Post by nhtrader on 2011-01-27
Basically, MythTv uses the v4l-dvb device driver. So read this...
[http://www.linuxtv.org/wiki/index.php/Main_Page](http://www.linuxtv.org/wiki/index.php/Main_Page)

Yes, Your computer can server as both frontend and backend. That's my current configuration.

Comcast Cable <- (RG6) -> Tv tuner Card which can occupy an internal PCI or PCI express slot. There's also another option. You could get a TV  tuner USB stick. This plugs into a USB slot on your computer and the other end gets connected to the RG6 cable which is your comcast source.

---

### Post by nhtrader on 2011-01-27
It just occurred to me that maybe you mean how does your computer connect to you new LCD/plasma/flat panel HD TV?

In this case, your current hardware/computer system may be problematic.

1. Does your current system have an HDMI connector? ( I doubt it)
2. Does your current system have a DVI connector? ( I doubt it)
3. Does your current system have a VGA connector? (I'm guessing YES)
4. Is your current system connected to a home network? (I'm guessing YES)
5. Do you own another computer with an HDMI connector? (won't guess one)

6. What connections does you LCD HD TV have?
      HDMI / DVI / VGA / RGB / Composite 

 7. Also what audio inputs does it have? (RCA, mini headphonejack, Toslink(fiber optic))


If your LCD HD TV has a VGA or D-SUB connector, then you can connect your PC directly to the TV. Change the TV's input to VGA or D-SUB and you should see your computer screen on the TV. Plus, you will also need sound. So you need another cable to connect the PC to the TV    ( PC:headphone jack to TV:audio in.)

If your TV has HDMI and you have another computer that has an HDMI port/connector then using HDMI is the preferred method.

These two computers need to be on the same network and the MythTV PC (PC1) will act as a server to the other computer with the HDMI port (PCMAC2). And all you need to do is connect the TV to  PCMAC2(HDMI) using a HDMI cable. Again, change the TV's input to HDMI and you should see your computer's content. Then you use PCMAC2 as a client to PC1-MythTV. So you need to have 4 devices turned on: PC1, PCMAC2, TV, and network switch/router. 

The advantage to using HDMI is twofold. One, you only need one cable for both video and audio. Two, HDMI supports full HD (1920x1080).

The disadvantage to using the VGA connector is that it will limit you to your video card's or onboard video's maximum resolution, which is usually less than 1920x1080.

So if you don't have PCMAC2 and you were to upgrade your hardware so that you can utilize HDMI, then all you would need is a new motherboard that has an HDMI port. Probable a new CPU and Fan (dual core > 2.8 Ghz would be enough). Then of course some new RAM to match the new motherboard (2 Gb is min. but 4 would be better b/c the motherboard probably would take some for the onboard video card. typically 512Mb is shared video memory). You can use same HDD, probably the same case if the new motherboard matches the form factor of your current motherboard; you probably can keep the same power supply but you'll have to check your current power supply's connectors and check if they are adequate for the new motherboard and CPU plus you'll need some extra SATA connectors; keep same CD/DVD-ROM, etc.

---

### Post by joho500 on 2011-01-28
> **larry_bg said:**
> Hello, I have old Dell Optiflex GX220 Intel Pentium 4 CPU 2.80GHz with 2GB memory that I would like to use with Mythbuntu for my home setup with Comcast digital cable. I’m new to this and don’t know what kind of hardware I should additionally to buy to make it happen, and what the setup should be. Will this configuration enough to record and play HD movies, if no what is the preferred hardware would be? 



Can you help with this?


Thanks,
Larry

To play HD content you need hardware acceleration i.e. the graphics chip is used to play the content. You need a nvidia graphics card that supports VDPAU, see [http://www.mythtv.org/wiki/VDPAU#Supported_Cards]("http://www.mythtv.org/wiki/VDPAU#Supported_Cards")

Cheers,
Joost

---

