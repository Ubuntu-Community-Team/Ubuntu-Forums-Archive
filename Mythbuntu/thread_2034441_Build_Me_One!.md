---
title: "Build Me One!"
date: 2012-07-28
forum: Mythbuntu
---

### Post by gizzardjr on 2012-07-28
[COLOR=black][FONT=Tahoma]I want to build a Mythbuntu box so badly.  Experienced users, if you were to build a brand new Mythbuntu box, would the following hardware specifications meet your requirement to record over the air local HD broadcasts.[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]CPU - Intel i3 2100[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Motherboard - [[COLOR=black]Intel BOXDH67CLB3 LGA 1155 Intel H67 HDMI [/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813121508")[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Capture Card / Tuner - [/FONT][/COLOR][[COLOR=black][FONT=Tahoma]Hauppauge WinTV-HVR-1600 [/FONT][/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815116075")[COLOR=black][FONT=Tahoma][/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Video (on board Intel HD Graphics)[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Sound - onboard - hdmi[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Memory - 4bg ddr3 1333[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Optical Drive - Blu-Ray Burner or DVD Burner (doesn't really matter)[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Power - 600w +[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Case - Generic Custom Case[/FONT][/COLOR]

---

### Post by mymythtv on 2012-07-28
Well - not bad, but it depends :-)

Personally, I would go for Nvidia graphics ( discrete ?! ) - supported by developers / vdpau.
Having a frontend ( Zotac HD11 ), only using 5-10% cpu on HD playback, CPU isn't the big issue - Graphic card is !

My backend is a BE/FE combined - Dual core, 4 GB memory, Nvidia graphics - no problem in playback or jobs.

If you do a lot of "user jobs", commercial skip, transcoding, then CPU might be a bottleneck, but..

Can't tell about HVR-1600 - try to look around for other posts, but guess is that it's ok - somebody will proberly argue for another ( not hauppauge ) card :-)

Please check [http://www.mythtv.org/wiki/High_Definition_Disk_Formats](http://www.mythtv.org/wiki/High_Definition_Disk_Formats) and [http://www.mythtv.org/wiki/Release_Notes_-_0.25#Disc_Playback_.28DVD.2C_Blu-Ray.2C_etc.29_and_Media_Detection](http://www.mythtv.org/wiki/Release_Notes_-_0.25#Disc_Playback_.28DVD.2C_Blu-Ray.2C_etc.29_and_Media_Detection) regarding blueray in myth / 0.25 - it's not a "walkover"

Just my 2 cent.
  Bjarne

---

### Post by faginbagin on 2012-07-29
I'm not sure that particular model, 1387, is supported under linux. It's not mentioned here:
[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600)
Also, it doesn't include a remote, so you'd need some sort of remote solution, which could be a wireless keyboard.

FWIW, I have two model 1199 HVR-1600s. I have found they need a stronger signal than my silicon dust HD homeruns. But that's on WOW cable. I know some folks have found the HD homeruns lacking when it comes to OTA. But maybe the current HDHR3s are better than the previous HDHR2s. For an extra $35 (using newegg prices), the HDHR3 will give you an extra tuner and is also capable of recording more than one program on the same multiplex at the same time, what mythtv calls virtual tuners. For OTA, that means if your PBS station has multiple channels, broadcasting different content at the same time, you could record each of those channels at the same time, because they should all be on the same multiplex. The HVR-1600 is not capable of tuning more than one channel per mux at the same time.

You can try to get it working with the onboard video, but don't be surprised if you need to get a discrete nvidia card.

A 600 watt PSU is way overkill. 300 is probably more than enough, even with 2 or 3 disks, and a discrete video card based on the nvidia GT 430 or GT 520 GPUs. Seasonic makes a couple of 80+ 300 watt PSUs.

---

