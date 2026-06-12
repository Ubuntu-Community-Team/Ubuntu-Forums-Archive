---
title: "Setting up VPN using GUI interface?"
date: 2012-10-18
forum: Networking &amp; Wireless
---

### Post by Stephan H on 2012-10-18
Hello Forum,

I was thinking of having a constant connection to my (XP) machine at work using a VPN.
Apart from setting it up on the other side, I tried to find out how to do it on Kubuntu. Reading the FAQ/Wiki I could see it all works from the command line a lot. Hence my question as there was no advice found anywhere: is there a way of setting up a VPN using a GUI interface, no command line? I guess it would take me quite some time to learn and understand all required commands and their syntax. I rather learn it gradually.
So is there any way to just use a graphical interface to setup a VPN?

St

---

### Post by 1clue on 2012-10-18
I can't really help you with the gui because I know nothing about it.

However I've helped manage a Cisco Pix firewall at one of my offices in the past, and while there exists a GUI for Pix, when you hire an expert consultant to come in and handle the big stuff they hardly acknowledge its existence.  Every expert I've talked to ignores the GUI and uses the command line.  I asked about it, and they said the GUI doesn't really help.  You still need to know what the options are and how it all works, and the GUI doesn't save you much typing.

If that's the case with Cisco Pix, then I'm pretty certain it's true with Linux as well.  There is probably something simple for the most common options but I'm betting a VPN to your office isn't one of them.

I've managed my office firewall with Linux, but it was years ago and there have been several different schemes for firewalls in Linux since.

You might consider getting a VPN appliance.  Probably any higher-end wireless router for home use has a VPN function, and you can probably connect to whatever you have at your office if they use something common.

---

### Post by ahallubuntu on 2012-10-18
If you want to setup a VPN server at home, I highly recommend getting a cheap router that supports DD-WRT.  Some routers have enough RAM and flash memory to support the large version of DD-WRT that includes a built-in OpenVPN server.  This is how I have my home network setup.

Some example routers that support DD-WRT with OpenVPN:  Asus RT-N13U B1 (also wireless N router if you need wireless).  Or try an old Linksys WRT54G (Version 4 or older only) or WRT54GL, which can be had cheaply (G wireless only - disable wireless, use it as a gateway only and attach your N wireless router to it).

The newest versions of DD-WRT do have a Gui interface for setting up OpenVPN that's easier than the old methods.  Still, there is some command line work required to generate certificates, if you want a good secure VPN.  You can have a VPN that uses only a password but that puts your home network at risk of being compromised.

---

### Post by 1clue on 2012-10-18
-1 on that from my perspective.

DD-WRT has almost no testing.  Models are "verified" by somebody installing a new version on their router and getting it to work for their scenario.  They don't test anything comprehensively even on virtual hardware.

I ran it for awhile and discovered how unstable it was on my router, and after I crashed every 3 days I finally went back to the OEM firmware.

---

### Post by ahallubuntu on 2012-10-18
There are different builds of DD-WRT you can download and install, and DD-WRT builds are specific to individual routers (or chipsets).  Some of builds are just update builds by a developer who used newer source code and not recommended for the average user.  It's usually best to start with the default build given at [www.dd-wrt.com](www.dd-wrt.com) for that individual router (search the Router Database), because those builds have been used and tested by a number of people.  In addition, you can usually find a thread discussion individual hardware and suggestions for newer builds for different routers.

The WRT54G DD-WRT builds have been used by thousands of people, so that might be your best bet for finding a reliable router with DD-WRT.  I recommend also the Asus RT-N13U B1 as I noted.  It never crashes.  (If you obtain one, I can tell you the build I used.)
 
I manage five DD-WRT routers (that I can remember) on different hardware, and they are all rock solid reliable.  They never crash or need to be rebooted.  EVER.  The only time they go down is when power is lost or they are rebooted on purpose. Some of them are used by businesses  who could never afford to use a flaky router, because they need to be online all the time.

---

### Post by 1clue on 2012-10-18
Bless you then.

I did all that, only with a WRT610N.  Used the recommended build, the previously recommended build, the not-so-recommended builds, did the whole thing from 30-30-30 and fresh flash to the finish several times.

Maybe I was trying to get some functionality none of the other thousands of people were trying.

That's my whole point.  DD-WRT is probably fine if you're one of the herd.  If you use even one feature that isn't used by everyone else, then you're screwed because it's UNTESTED.

Can you tell me that every possible configuration option has bees completely exercised in that router build you use?  Not every permutation of course, that's not possible.  But has every feature been tested with a reasonably complete set of values?

The answer to that is "no" because there IS no test suite for the code.  None.  There is also no manual test process for the builds, for users of a specific router to follow to certify for the rest of the users of that router that this build in fact works, and where problems might be.

---

### Post by 1clue on 2012-10-18
And that's another thing.  I stopped using it almost a year ago.  I stopped using it because the recommended build for my router hadn't changed in the time I had been trying it.  What do you know?  It's still the same build.

---

