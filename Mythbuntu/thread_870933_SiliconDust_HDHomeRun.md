---
title: "SiliconDust HDHomeRun"
date: 2008-07-26
forum: Mythbuntu
---

### Post by bglaze1 on 2008-07-26
I am thinking about purchasing the SiliconDust HDHomeRun.  It seems like the best option for capturing two digital signals at once.  I have seen in the Functional Hardware post that a few people are currently using this.  But I have a couple of follow-up questions:

Does the HDHomeRun work out of the box with the latest version of Myth and Ubuntu? Or does it require a fair amount of tweaking?

How is the video quality?  Do you have any problems with the video streaming over the network?

Has anyone used this to capture over the air HD?

Thanks for your help.

---

### Post by theacoustician on 2008-07-26
> **bglaze1 said:**
> I am thinking about purchasing the SiliconDust HDHomeRun.  It seems like the best option for capturing two digital signals at once.  I have seen in the Functional Hardware post that a few people are currently using this.  But I have a couple of follow-up questions:

Does the HDHomeRun work out of the box with the latest version of Myth and Ubuntu? Or does it require a fair amount of tweaking?

How is the video quality?  Do you have any problems with the video streaming over the network?

Has anyone used this to capture over the air HD?

Thanks for your help.

1. Should work out of the box fairly well.  If not, the command line app isn't hard.

2. The quality is as broadcast.  All this device does is demodulate 8VSB and packetize it into a TS stream.  Its never touches the video.  I've had zero problems using it over a wired network, but on wireless you get the occasion packet loss.  It usually acceptable for causal watching, but recording over wireless will not make you happy.

3. Yes, you just need at least 100b network connection between the HDHomeRun and your recording machine.  Wireless won't cut it.

---

### Post by CNLiberal on 2008-08-08
I purchased one of these about a year ago.  It's been WONDERFUL.  I was using an antenna mounted on a LARGE mast.  I was only able to get one channel reliably, and others only at night.  The only problems I had with OTA was that sometimes, Myth would stop recording for no apparent reason.  It would stop recording until I rebooted the backend, and then it picked up again no problem.  That was on the older .20.  I'm running .21 now and I have had issues with the other 2 PCI PVR-x50 cards I have and the HDHR.  Apparently, you need to have all your cards pointed to a Video Source and have them hooked up to cable/OTA in order for the backend not to go crazy.  I think I'm gonna pull them tonight.  But the HDHR is definitely a sweet device.  It's gonna record the Olympics in HD for me!  sweet.

---

### Post by bmwman on 2008-08-08
I'm using the SiliconDust HDHomeRun for like 3 months now. It's a great piece of hardware and definetly recommend it if you want to spend the money.

---

### Post by Dewey_Oxberger on 2008-08-11
I've been using one for 8 months.  It works great.  Mythbuntu config allows you to select it from a list and it just worked for me.  Zero config issues for me.

I had two problems setting it up:

1)  It arrived with some sort of internal configuration error and the error message said to email tech support.  I did and they had me working in about an hour (it was a Saturday).

2)  I screwed up and had a 10 MBit hub in my network.  HD really needs more than 10 MBits to work so I was getting all kinds of crazy problems.  Updated the hub to 100MBit and all has been well.

My only complaint about the HDHomeRun is its IR sensor seems very directional and doesn't seem to work well.  I've stopped using IR remotes as the family prefers the remote keyboard.

---

### Post by bglaze1 on 2008-08-16
What are you using as a source for your HDHomerun?  I was just going to be using OTA HD initially, but I have thoughts of going to either cable or satellite in the future, will the HDHomerun work with any of these inputs? Does the HDHomerun have limitations as to what input it can receive?

---

### Post by Nate B. on 2008-08-16
[HDHomerun product specs]("http://www.silicondust.com/products/hdhomerun")

---

