---
title: "Recommend Mythtv Frontend Hardware"
date: 2016-05-15
forum: Mythbuntu
---

### Post by lmclaren on 2016-05-15
Hi,

I have looked through the supported hardware and searched on the web but can not find any clear options.

I am looking for a silent, front end only option.

Must have the following:
[LIST]
[*]Mythtv Front end, not Kodi etc.
[*]Silent (no fan)
[*]Ethernet cable
[*]HDMI video and audio
[/LIST]


Nice to have:
[LIST]
[*]Nvidia graphics
[*]Small
[/LIST]

 
From what I can tell, Nvidia still has the edge over the Intel graphics, is this correct?

I have read about a RP3 as a full front end but can not find anywhere that mentions performance.
This will be the main lounge room machine, it must be snappy.

I have a very old acer revo that I use in the bedroom and it is still ok, just find it hard to believe that there is nothing better now.
I am in Australia if anyone want to point me to a seller.

thank you.

---

### Post by Bucky Ball on 2016-05-15
So, you are actually asking for recommendations for suitable hardware for a media server, to put it in other words? If so, you might want to change your thread title to 'Recommend MythTV frontend hardware', or something similar, to improve your chances of support. 

I use Kodi on a Raspberry Pi, before that an Odroid, previous to that a Raspberry Pi. Don't underestimate these little beasts. You can hang as many hard drives as you like off one and handles 1080 HD without a murmur. It can stream from any other computer in the house (or to it). I will be plugging one of my TV dongles into it for recording when the old media recorder/player dies. 

They also have absolutely everything on your wish list. A separate graphics is not really necessary as ARM processors handle all this on the chip.

Not sure whether others are using RPis for MythTV, never used it, but don't doubt it as I see no reason. Although, that's not saying much. :)

---

### Post by lmclaren on 2016-05-15
Thanks Bucky Ball, I have clarified my post.
I have found lots of posts using Kodi etc but I am looking for a full front end.

---

### Post by hollywoodpete on 2016-05-15
What do you mean by a full front end? MythTV makes a great backend but IMHO the frontend isn't quite on the same level as Kodi. I'm not trying to sell you on Kodi or the Raspberry Pi but the combination makes a great frontend with Openelec or Libreelec. The only limitation is sound quality. MythTV frontend on a Pi3 is currently not a good option. It may happen at some point if you really know what you are doing. If you are looking for a high quality frontend, the options are endless. I have Kodi/Pis on most of my TVs but in my surround sound HDTV media room I have a multi-core AMD PC with a high quality fanless video card and a sound card. I run Kodi on it, but MythTV will work fine

---

### Post by lmclaren on 2016-05-16
Thanks Hollywoodpete, I have tried kodi again and it is not for me. I will look at the hardware.

---

### Post by philip7 on 2016-05-16
I know you probably don't want to hear this but I can only second using Kodi on a Raspberry Pi with the Mythtv Add-On. With HDMI-CEC I've been able to ditch the keyboard and use my existing tv remote.

Initially I was hesitant using Kodi, I preferred the Mythtv interface, but decided to stick with it and found it very intuitive.

I have heard there is a Mythtv build on Raspberry Pi, I might look into this at some point but I'd need to check the support for HDMI-CEC. I guess the great thing about a Raspberry Pi is that you'd only need to invest in a new memory card.

---

### Post by Bucky Ball on 2016-05-16
> **philip7 said:**
> I guess the great thing about a Raspberry Pi is that you'd only need to invest in a new memory card.

And it will cost a fraction of the price of many other alternatives.

---

### Post by hollywoodpete on 2016-05-16
> **philip7 said:**
> I know you probably don't want to hear this but I can only second using Kodi on a Raspberry Pi with the Mythtv Add-On. With HDMI-CEC I've been able to ditch the keyboard and use my existing tv remote.

Initially I was hesitant using Kodi, I preferred the Mythtv interface, but decided to stick with it and found it very intuitive.

I have heard there is a Mythtv build on Raspberry Pi, I might look into this at some point but I'd need to check the support for HDMI-CEC. I guess the great thing about a Raspberry Pi is that you'd only need to invest in a new memory card.

But the sound quality is still a compromise.

---

### Post by philip7 on 2016-05-17
> **hollywoodpete said:**
> But the sound quality is still a compromise.

I really couldn't notice a difference between my Raspberry Pi and my previous solution, but I'm not an Audiophile.

Why would this be a compromise?

---

### Post by Bucky Ball on 2016-05-17
> **hollywoodpete said:**
> But the sound quality is still a compromise.

Audio through a HDMI cable is a compromise? In comparison to? I guess the compromise is if you wanted to use 5.1 sound or beyond. Not sure the RPi has the capability of plugging into a system like that via HDMI. Others might have a better idea.

The HDMI audio is going with the video signal to the television then out through the television, so if you are getting bad sound doing that, maybe the television or sound system is low-end. I am an audiophile, though not as zealous as I once was, and have great stereo sound system. RPi> TV via HDMI then sound out the TV to the stereo. Sounds great. :)

---

### Post by hollywoodpete on 2016-05-18
> **Bucky Ball said:**
> Audio through a HDMI cable is a compromise? In comparison to? I guess the compromise is if you wanted to use 5.1 sound or beyond. Not sure the RPi has the capability of plugging into a system like that via HDMI. Others might have a better idea.

The HDMI audio is going with the video signal to the television then out through the television, so if you are getting bad sound doing that, maybe the television or sound system is low-end. I am an audiophile, though not as zealous as I once was, and have great stereo sound system. RPi> TV via HDMI then sound out the TV to the stereo. Sounds great. :)


The sound quality is a compromise to a high end sound card with digital outputs fed though a surround sound system. The Pi handles video fine but I'm just not ready to put it in my media room. The flat screen TVs we use today have terrible built in speakers. I am not knocking the PIs (I have 5 actively being used) but I still have a HTPC in the media room simply because of the better sound. I did buy a digital add-on sound card last week from NewEgg and am waiting for it to arrive. I am hoping this will solve the sound compromise

---

### Post by lmclaren on 2016-06-04
Ok, based on research over the last month these look like viable alternatives.


Has anybody tested these or same chip sets?
[http://www.geekbuying.com/item/Tronsmart-Ara-X5-Windows-10-TV-Box-Cherry-Trail-Z8300-Quad-Core-1-8G-Gen-8-Graphics-2G-32G-2-4Ghz-5Ghz-351938.html](http://www.geekbuying.com/item/Tronsmart-Ara-X5-Windows-10-TV-Box-Cherry-Trail-Z8300-Quad-Core-1-8G-Gen-8-Graphics-2G-32G-2-4Ghz-5Ghz-351938.html)
with this processor
[http://ark.intel.com/products/87383/Intel-Atom-x5-Z8300-Processor-2M-Cache-up-to-1_84-GHz](http://ark.intel.com/products/87383/Intel-Atom-x5-Z8300-Processor-2M-Cache-up-to-1_84-GHz)


[http://www.geekbuying.com/item/Vorke-V1-Intel-Celeron-J3160-4G-64G-MINI-PC-802-11b-g-n-Gigabit-LAN-Bluetooth4-0-HDMI---Black-367582.html?source=ShareAsale](http://www.geekbuying.com/item/Vorke-V1-Intel-Celeron-J3160-4G-64G-MINI-PC-802-11b-g-n-Gigabit-LAN-Bluetooth4-0-HDMI---Black-367582.html?source=ShareAsale)
with this processor
[http://ark.intel.com/products/91533/Intel-Celeron-Processor-J3160-2M-Cache-up-to-2_24-GHz](http://ark.intel.com/products/91533/Intel-Celeron-Processor-J3160-2M-Cache-up-to-2_24-GHz)


Apart from the price difference, the main points are that the Tronsmart with Cherry Trail does not have  a fan at all, the Vorke does. Maybe the Vorke does not use the fan much?
Graphics seem similar. Memory higher on the Vorke.

If the Tronsmart is going to do it "easy" eg no lag in the UI etc then I would lean that way.

thanks

Lee

---

### Post by hollywoodpete on 2016-06-05
> **hollywoodpete said:**
> The sound quality is a compromise to a high end sound card with digital outputs fed though a surround sound system. The Pi handles video fine but I'm just not ready to put it in my media room. The flat screen TVs we use today have terrible built in speakers. I am not knocking the PIs (I have 5 actively being used) but I still have a HTPC in the media room simply because of the better sound. I did buy a digital add-on sound card last week from NewEgg and am waiting for it to arrive. I am hoping this will solve the sound compromise

Just a quick update, I installed the HiFi Berry on my Pi and use passthrough with optical. The sound is amazing. There is no compromise on my front end anymore and my Pi is now in my theater room. I am getting an acrylic case to show it off but the sound is amazing.

To the OP since I derailed and hijacked his thread, there is no way I would get hardware with Windows 10 pre-installed with the intent of using Mythbuntu. The snappyness of a minimal Linux OS running a media player on low-power hardware will be lost.

---

### Post by lmclaren on 2016-06-05
I am not going to use Windows os, just the hardware.

---

### Post by hollywoodpete on 2016-06-05
> **lmclaren said:**
> I am not going to use Windows os, just the hardware.

Then why pay ~$100 for a Windows license you don't plan on using? Not to mention you will be chasing down hacks, kernels and fixes to make it work

---

### Post by gedakc on 2016-06-06
For anyone considering using Raspberry Pi 2 or 3 for mythfrontend, this is indeed possible.  There are some compromises over using a full blown x86-64 system with NVidia graphics, but the cost savings can be significant.

I wrote a tutorial on this.  See [Setting Up an Inexpensive Raspberry Pi 2 as a Cheap Frontend to MythTV with MythFrontend]("http://gedakc.users.sourceforge.net/display-doc.php?name=pvr-rpi-mythtv-frontend")

Overall I have been very content using the RPi2 with mythfrontend.

There are a few different native mythfrontend builds for the Raspberry Pi to choose from.  See [Mythtv.org - Native MythTV Frontend]("https://www.mythtv.org/wiki/Raspberry_Pi#Native_Mythtv_Frontend").

---

### Post by lmclaren on 2016-06-07
@gedakc,  I have had a look, very nice write up, thank you. 
Would you call the menu navigation "snappy"? 
Is RP3 any better than the 2? 

thank  you again.

@hollywoodpete, at least one of the computers is supported for Ubuntu and the Windows licences are free for some devices depending on cpu etc. So no money to MS. Only paying for the computer.

---

### Post by gedakc on 2016-06-07
> **lmclaren said:**
> 
Would you call the menu navigation "snappy"? 
Is RP3 any better than the 2? 


I find the menu navigation on par with my combined MythTV FE/BE running on my Intel i5-2500k processor.  No noticeable lag.

The RPi3 is has a faster processor and both the CPU and GPU are clocked at higher speeds.  If you have a choice of either at the same price then I'd recommend getting the RPi3 (it also has built-in WiFi and bluetooth which the RPi2 does not).

---

### Post by lmclaren on 2016-06-08
thanks gedakc, rp3 on its way.

---

### Post by lmclaren on 2016-06-09
Hi gedakc,

Will the built  "mythtv-v0.27.6-69-g41a2a8d-RPI2-jessie.tar.bz2" you link on your guide work with a rpi3?

thanks

---

### Post by gedakc on 2016-06-09
> **lmclaren said:**
> Will the built  "mythtv-v0.27.6-69-g41a2a8d-RPI2-jessie.tar.bz2" you link on your guide work with a rpi3?


Yes.  Even though the RPi3 is a newer processor and supports 64 bits, it is binary compatible with the earlier Raspberry Pi computers including the RPi2.

---

### Post by lmclaren on 2016-06-11
thank you gedakc,

Up and running, working through the final tweaks.

---

### Post by wpcprez on 2016-07-13
> **gedakc said:**
> For anyone considering using Raspberry Pi 2 or 3 for mythfrontend, this is indeed possible.  There are some compromises over using a full blown x86-64 system with NVidia graphics, but the cost savings can be significant.

I wrote a tutorial on this.  See [Setting Up an Inexpensive Raspberry Pi 2 as a Cheap Frontend to MythTV with MythFrontend]("http://gedakc.users.sourceforge.net/display-doc.php?name=pvr-rpi-mythtv-frontend")

Overall I have been very content using the RPi2 with mythfrontend.

There are a few different native mythfrontend builds for the Raspberry Pi to choose from.  See [Mythtv.org - Native MythTV Frontend]("https://www.mythtv.org/wiki/Raspberry_Pi#Native_Mythtv_Frontend").
how is the deinterlacing? I am running all nvidia frontends with most everything decoded via the cards since they support H.265 on chip. How does the RPI3 handle the deinterlacing?

---

### Post by JimLS on 2016-10-09
I know this has been discussed various places but I am still unclear on some tradeoffs.  I am only using USA OTA broadcasts.  Wanting to set up a front end for a TV in another room.  I can easily run network cable for it.  I have a RP2 but may pick up a RP3 as they are cheap enough.  

Using the Myth software would probably result in better WAF but I am wondering about responsiveness.  I don't demand it be super quick.  What's the tradeoffs between Kodi and Myth software (or others)?

Do I need to buy the decoder key?  I have seen some places say they got ok performance without it but it seems to be for other than USA OTA signals.  Again, it's cheap enough I am not sure why I am even asking...

Planning to wire a IR receiver to a GPIO pin for control as I can't find any info on CEC for this small TV (vizio E22VA) so I don't think it has it.

---

### Post by philip7 on 2016-10-12
I initially bought my Raspberry Pi as a bit of fun, I signed up to the HDHomeRun DVR and needed a Raspberry Pi to run the app, as I had Kodi running it made sense to see how well the integration with Mythtv worked.

For Mythtv I think the Mythtv Frontend looks much better, but from a user experience perspective I prefer using Kodi, HDMI-CEC means I can ditch the wireless keyboard and use my existing remote control. If I need another frontend in another room its only £50 which is much cheaper than any other option.

I only had to buy the decoder key when I started recording in HD, for SD it wasn't required. There hasn't been any lag using a Pi either, but the Pi and backend are both wired directly to the hub so probably the best option.

---

