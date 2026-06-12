---
title: "Installing Mythbuntu"
date: 2010-02-04
forum: Mythbuntu
---

### Post by ijourneaux on 2010-02-04
I would like to configure a PVR system using MythTV and Ubuntu using an Adaptec dual analog tuner, an HDHomeRun dual tuner and an HD PVR. Although a proficient PC user, I onyl have limited exposure to Linux and Ubuntu.

How much am I biting off?

Currently my family is using a PVR based on BeyondTV but I am finding that BeyondTV support for the HD-PVR is not where it needs to be. With the HD-PVR BeyondTV is very fragile.

I have always wanted to look at MythTV but upto this point BeyondTV was rock solid. This is critical for me since the system is used by everyone in the family.

Take Care

---

### Post by laffinet on 2010-02-04
Mythbuntu is a very stable and capable system, but depending on your hardware and how much you want to customise things it might take a bit to setup. Don't be afraid though, lots of people around to help.

And once you got the system setup and running it's a breeze to use and very very stable.

First thing you should do is check your hardware for compatibility. Just pop each of your hardware components (well, the main ones as in graphics card, tuners, network components) into google with "mythtv" or "mythbuntu" or just "myth" and see what pops up.
There are also some lists and guides around for hardware. Again, google for things like "myth hardware compatibility" or so.

The less you read about problems with your specific hardware the easier it will be to set up.

Enjoy !

---

### Post by Calmor on 2010-02-05
I would say to keep the WAF ([http://en.wikipedia.org/wiki/Woman_acceptance_factor]("http://en.wikipedia.org/wiki/Woman_acceptance_factor")) high, you might want to dual-boot or practice on a spare machine before you attempt to switch over completely. 

Depending on your system, requirements, and any miscellaneous problems you may face, it can take a considerable amount of time to set up.  

Like you, I was a BeyondTV user, and made the jump to Mythbuntu.  Trying a firewire cable box tuner, it was probably more frustrating than it had to be.  I was already fairly familiar with Linux, so some of the learning curve was already dealt with.  I've heard the HDHR runs pretty smoothly too, so it should be a far easier ride.

laffinet's suggestions are good.  Personally, I'd also suggest an NVidia card.  My machine had hardware HDMI out of the motherboard on an ATI chipset, but I could never get a satisfactory picture.  I also tried another, much more robust ATI, and still couldn't get it to work.  This was over a year ago, so maybe things have changed, but I went to Best Buy, picked up a $150 NVidia card, dropped it in, and viola - HD output with no hassles.

You'll likely run into some snag along the way, but the folks here are good about helping you find the answers.

---

### Post by ijourneaux on 2010-02-05
Thanks for the comments. As for the "WAF" (I had not seen the wiki page) it is critical. I don't plan on (can't if I value my home life <grin>) surprising her with it!

The key tuner I need to have work is the HD PVR. If I don't ahve the HD PVR, I could stay with BeyondTV. The BeyondTV support for the HD PVR is abysmal and the configuration is extremely fragile.

If needed, I could swap out the Adaptec Dual Tuner for the Hauppauge PVR-500 as it is probably better supported.

I have installed Ubuntu in the past successfully (that part is easy) and used it at the user level without any problems. The issue here is the complexity of the hardware and drivers involved.

Here are the items that would need to be addressed

- support for the HD-PVR, Adaptec Dual Tuner, HDHomeRun
- IR blaster to control the cable box (currently on the HD-PVR)
- IR reciever to allow use of remote (currently on the HD-PVR)

Not too critical is the bluetooth wireless keyboard I use to control the PVR. The PVR is located in the basement so I have an IR reciever/transmitter to transfer the IR commands to the HD PVR.

I will do a search for the tuners. That part will probably be the easy part. The bigger issues (WAF) is how the end user interacts with the PVR.

Take Care all.

---

### Post by 4dognight on 2010-02-05
I can vouch for the HDHomerun as being very well supported, as well as a PVR-500 as I have both running  in 9.10.

Are you also saying you have a cable set top box? If so, it probably has a firewire port n the back. Depending on the model it is also probably well supported. I have 2 Motorola 3250 STB. There is a channel changer program used to control the channel changing, which is run over the firewire port also, You would not need a IR blaster then.

---

