---
title: "First post - new to mythtv"
date: 2009-09-01
forum: Mythbuntu
---

### Post by getafix35 on 2009-09-01
Hi everyone
 
Well, where do I start?
 
This is my first attempt to install mythtv as I am up for a challange and have dabbled with the various Windows home theater options. You know which ones I am talking about - might be a swear word here. :P
 
Anyway my setup is as follows:
 
GA-MA78GM-S2H mobo.
Phenom 9750 quad core
2 x PVR-500 analogue cards
2 x PVR-150 analogue cards
onboard graphics (HD3200) via HDMi
onboard sound
1 x 160gb seagate HDD
1 x 500gb seagate HDD
1 x LG BluRay/HD DVD drive (playback only)
1 x LG DVD/CD Writer.
1 x 580watt Gigabyte PSU
1 x 47" LCD 1920x1080 native resolution.
Output to a Yamaha Z9 amp via optical.
TV is via a satelite STB connected to 1 x PVR-500
 
I installed Mythbuntu 9.04 as a front/backend.
 
After going through the setup process and reading through the install manual, I have various questions.
 
1. How do I set my output resolution to 1920x1080
2. The quality of the picture on screen (live tv) was not good at all. There seemed to a lot of tearing and pixelation (if there is such a word) 
3. I could not get any audio out.
4. The quality of DVD playback was sub standard. Similar to the live TV quality.
5. I have the Microsoft infrared receiver seen [here]("http://gbpvr.com/pmwiki/uploads/Main/MS-MCE_Remote_2005_w_Beanbag.jpg"). Which option do I select in the setup to get this to work. Is there any other tweaking needed.
6. I also have a harmony 880 remote. Once again do I need tweaking. I selected Harmony in the setup, but I am not convinced that the IR receiver is working so I don't know if the remote is either.
 
I will continue to search the forums for answers but I would appreciate some help if possible.
 
Cheers

---

### Post by LowSky on 2009-09-01
you need ATI drivers to be installed, especially catalyst to get the correct resolution.


on board graphic will not be so good an dthe problem with DVd and TV playback on a giant screen. Sorry but even the newer stuff still suffers in this department. Yuo can pick up a nice HD4550 for about $35, but then again everyone is going to tell you ATI graphics stink, and you should choose a Nvidia chiset, like a 9600GT.

also analog TV looks horrible on HDTV's If you want crisp picture you will need digital tuners.

[ATI Drivers WEBSITE]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by the_pod on 2009-09-01
> **getafix35 said:**
> 
1. How do I set my output resolution to 1920x1080
2. The quality of the picture on screen (live tv) was not good at all. There seemed to a lot of tearing and pixelation (if there is such a word).
4. The quality of DVD playback was sub standard. Similar to the live TV quality.

I have the same onboard video you do (using [http://www.newegg.com/Product/Product.aspx?Item=N82E16813128382](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128382) as MB) and my video works perfect.  That said, if you don't have the ATI drivers installed you don't get the 1080 from what I found.  This should fix #1 & #4, and perhaps #2. If not #2, then you need to do some digging on your specific capture card as I've found many different tweeks, settings, and secret black-magic voodoo for the ones I have.

> 
3. I could not get any audio out.

You'll find a bunch of settings for sounds, some in the Myth setup, others in the more basic menus, others still in the OS. I don't have sound running via the HDMI so I can't confirm or deny that is the problem.  Mine runs via a dongler that converts to a double RCA adapter and that works fine.  I'd encourage you to play with the system sounds in the OS and get familiar w/ the different options. You really need to crank the sound WAY up in the OS, have it save (surprisingly not intuitive), and also have the sound cranked up in the Myth Setup - roughly 100%. (You'll see 2 volume meters - one is system sound which, I believe, is based on how the OS sets it - see note above about figuring out how to save this setting - the other is for the relative sound volume to the TV - mine is typically set at 90%+, so just be aware it needs to be LOUD.

> 
5. I have the Microsoft infrared receiver seen [here]("http://gbpvr.com/pmwiki/uploads/Main/MS-MCE_Remote_2005_w_Beanbag.jpg"). Which option do I select in the setup to get this to work. Is there any other tweaking needed.

6. I also have a harmony 880 remote. Once again do I need tweaking. I selected Harmony in the setup, but I am not convinced that the IR receiver is working so I don't know if the remote is either.
 

FWIW, I was where you are about 2 months ago.  Now I'm up, running, getting all my channels, have things setup, watching HD (all my channels are QAM).  It was a bear the first 2-3 weeks to figure out what was going on and to find resources.  My take on the forums is that you can get some really good feedback if your post title is extremely specific and you've done a good bit of searching before.  If you're patient and get to know all the different setup menus very well at some point things just click and then you're mostly functional.  

As a side, I've found the DVD player/ripper to be subpar (primarily b/c its hit or miss on what it will burn and/or rip), and that seems to be a common complaint so I don't use it.  You may have better luck than me.

Good luck, have fun, and be prepared to learn a lot of stuff you'll never use again!

---

### Post by getafix35 on 2009-09-02
Fisrtly thank you for the replies. I am glad it wasn't a go and RTFM response like I have seen before when a newbie asks what would be seen as stupid questions.

> you need ATI drivers to be installed, especially catalyst to get the correct resolution.

I figured this out. It is amazing how intalling Linux has thrown me. I am so used to Windoze that I was like a deer caught in the headlights when I used Mythbuntu for the first time.

So I have downloaded [this]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English") chipset and mobo driver from ATI. I will read up how to install it.

> but then again everyone is going to tell you ATI graphics stink, and you should choose a Nvidia chiset, like a 9600GT.

I also have a nVidia 9800GT but the fan is pretty noisy so I have avoided it. I will give it a bash if i need to.

> If not #2, then you need to do some digging on your specific capture card as I've found many different tweeks, settings, and secret black-magic voodoo for the ones I have.

I am using the Hauppauge PVR-500 analogue. Here in RSA we only have HDTV via a STB and not over FTA (coax). At this stage we are not able to capture an HD signal as there are not cards that have HDMi inputs that can be used in an HTPC enviroment. I know that there is one on the market, but the encryption might be a problem.
So for now I am stuck with an analogue signal.

I figure that once I have installed the mobo driver, the onboard audio should also work. I will be connecting audio via an optical cable from the mobo (onboard) to my amp. 

What I basically want to achieve is to be able to record live tv (pvr functionality) rip my dvd's to the HDD, as well as my music and any pictures I may have.

I would then like to be able to view this in various other rooms in the house via a mythbuntu frontend. For now, I need to get the backend up and running smoothly.

Thanks for the pointers so far and I am continuously reading as I go along.

Cheers
GAreth

---

