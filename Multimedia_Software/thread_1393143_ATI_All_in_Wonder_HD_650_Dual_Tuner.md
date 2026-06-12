---
title: "ATI All in Wonder HD 650 Dual Tuner"
date: 2010-01-29
forum: Multimedia Software
---

### Post by Alpha7 on 2010-01-29
Hi All, 

I recently picked up a HD 650 Tuner for my computer and have had problems with in under windows and figured I might have better luck here. It works under windows but only with a third party program I don't really want to pay for after the card and everything + ATI and WMC not working with it. 

Anyways lspci -vnn shows the card is recognized and from what I've read elsewhere it means its installed but the firmware is not there...

05:01.0 Multimedia controller [0480]: ATI Technologies Inc Device [1002:4d50]
	Subsystem: ATI Technologies Inc Device [1002:a698]
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at fdb00000 (32-bit, non-prefetchable) [size=1M]
	Memory at fa000000 (32-bit, prefetchable) [size=32M]
	Capabilities: <access denied>

I've looked and I can't find any additional info or anywhere to find 650 firmware and was hoping to find some help here.

Running 9.04 x64
With two ATI HD 3870 

Any help is appreciated.

---

### Post by sports.car.guy on 2010-01-29
> **Alpha7 said:**
> Hi All, 

I recently picked up a HD 650 Tuner for my computer and have had problems with in under windows and figured I might have better luck here. It works under windows but only with a third party program I don't really want to pay for after the card and everything + ATI and WMC not working with it. 

Anyways lspci -vnn shows the card is recognized and from what I've read elsewhere it means its installed but the firmware is not there...

05:01.0 Multimedia controller [0480]: ATI Technologies Inc Device [1002:4d50]
    Subsystem: ATI Technologies Inc Device [1002:a698]
    Flags: bus master, medium devsel, latency 64, IRQ 10
    Memory at fdb00000 (32-bit, non-prefetchable) [size=1M]
    Memory at fa000000 (32-bit, prefetchable) [size=32M]
    Capabilities: <access denied>

I've looked and I can't find any additional info or anywhere to find 650 firmware and was hoping to find some help here.

Running 9.04 x64
With two ATI HD 3870 

Any help is appreciated.


Google is a wonderful thing!

Installing the firmware, and getting your card up and running, as with most of the supported cards are well documented. Now it depends on what version of Ubuntu you are running as well.

As of 9.10 the firmware files for ATSC / DVB / Capture cards are available on the repositories, the v4l packages are up to date enough for most cards, and the kernel as well. Prior versions Ubuntu you will need to download the windows installer and extraction script for your card from linuxtv.org's wiki. Then you will probably need to update the v4l linux libraries manually. Last but not least you are maybe looking at a kernel recompile too.

I just installed the Hauppauge WinTV-HVR 950Q on my MythTV server on 9.10 and it was pretty straight forward. It took me all of 10 minutes of looking through google listings too to find out how to get it up and running.

I am not trying to be a jerk here. I am just sick of questions like this, like we're tech support and getting paid. 

'I installed it and it don't work, now help me please.' 

The please sometimes from people out here being optional. If you went to most of the other forums and asked for help like this they would flame you so bad you'd think you were the worlds worst for asking. I used to be a regular on one such forum some time ago. You want help, try to help yourself first by doing things like research it on google. When you get stuck, then lay out what you've done to get to the point you are at, including the research so that we can compare it to what we know and see if it conflicts.

---

### Post by Alpha7 on 2010-01-29
You are kinda being a jerk.. I did look.. LIKE I SAID and couldn't find anything which is why I searched these forums first for an answer and after not finding anything posted.

I need to know what firmware the card has, I've already looked a lot at the V4L stuff and it still doesn't recognize my card once I start up Mythtv.

---

### Post by sports.car.guy on 2010-01-29
> **Alpha7 said:**
> You are kinda being a jerk.. I did look.. LIKE I SAID and couldn't find anything which is why I searched these forums first for an answer and after not finding anything posted.

I need to know what firmware the card has, I've already looked a lot at the V4L stuff and it still doesn't recognize my card once I start up Mythtv.

If I was being harsh I appologoize. It is very straight forward to get it up and running. It is well documented. I swear. I am not trying to be a jerk. I did a google search even knowing where to look, and it brought up where I am sending you for future reference. I am not some search engine genius or sauvant, I swear.

Below is the v4l / tv tuner wiki main page. It is a great resource for finding a card's support and if it is how to get it up and running.

[http://linuxtv.org/wiki/index.php/Main_Page](http://linuxtv.org/wiki/index.php/Main_Page)

Here is the AMD section:

[http://linuxtv.org/wiki/index.php/ATI/AMD](http://linuxtv.org/wiki/index.php/ATI/AMD)

Currently both the PCI and PCIe versions of this model are not supported according the the v4l / tv tuner support wiki.

Again if I came across harsh I am sorry.

---

### Post by dellster on 2010-01-30
This is a very broad question but, since this particular flavor of ATI card is not supported, for someone who has some home grown kernel experience and years of programming experience, could you possibly point out some resources where I might find some information on writing a device driver for this?

I didn't find much on the sited mentioned above and I've already checked the AMD developer forums and nothing has come from there.  The book "Essential Linux Device Drivers" has a section on video drivers but I haven't found any good on-line resources for device drivers related to multimedia devices.  I've tried googling on this topic but I'm not finding a lot.  Any suggestions?

Thanks much.

---

### Post by sports.car.guy on 2010-01-30
> **dellster said:**
> This is a very broad question but, since this particular flavor of ATI card is not supported, for someone who has some home grown kernel experience and years of programming experience, could you possibly point out some resources where I might find some information on writing a device driver for this?

I didn't find much on the sited mentioned above and I've already checked the AMD developer forums and nothing has come from there.  The book "Essential Linux Device Drivers" has a section on video drivers but I haven't found any good on-line resources for device drivers related to multimedia devices.  I've tried googling on this topic but I'm not finding a lot.  Any suggestions?

Thanks much.

I would think the Video4Linux forums, their resource pages, and such would be a good place. If you can work rapport with the people involved with the project I am sure they would be more then willing to take you under their wings so to speak.

---

### Post by Loedie on 2010-02-07
Hello.
 I am a newbie to Linux and is currently running Ubuntu 9.10. I have a ATI WONDER HD 650 PCI as well and can't get it to work. Tried all the get_dvb_firmwate etc without success. I the suspected a faulty card and tried it on windows. It worked 100% in WindowsXP which led me to the conclusion that the card is not supported in Linux yet. I am not a software expert. I only have a bit of BASIC experience. I am obviously interested in obtaining a driver for this card and are more than willing to help in any way I can. Although I can't write the firmware I can help with testing, docs or anything else. Please feel free to contact me.

---

### Post by tjwreds on 2010-03-03
If you check out the links that the sports car guy put up, you'll see that ATI TV TUNER 650 is no worky, not supported.  I have the same card and feel your pain.  I would LOVE to be wrong about this.  Anyone?  Bueller?

tjwreds

---

### Post by Loedie on 2010-04-05
I have done some research and the card is definitely not supported. The problem is there is now firmware on the card. If you use window the driver loads the firmware on the card at startup. That makes it a bit more complicated by the sound of it. Any way, I bit the bullet and purchase a Hauppauge 1600 PCI card and it work perfectly. The only problem I had is that I could not auto-tune the card using MythTV. I ended up setting up all the channels manually. It is fortunately only a once of exercise. I am still keeping my eyes and ears open because I would still like to use the card if I can get it working.
   
  Cheers.

---

### Post by gdm40 on 2012-07-31
Yes definitely not supported I tried the firmware workaround "failed miserably" and am unfortunately relegated to using the evil empires media center.

A shame that after all this time  "NM why bother commenting further".

---

