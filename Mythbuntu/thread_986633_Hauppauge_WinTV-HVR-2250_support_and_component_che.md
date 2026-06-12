---
title: "Hauppauge WinTV-HVR-2250 support and component check"
date: 2008-11-18
forum: Mythbuntu
---

### Post by reldruH on 2008-11-18
Hello. I'm in the process of picking out components for a mythtv setup. I've installed mythtv before and feel relatively comfortable with it, but this will be the first computer I've ever built and I was hoping to get some feedback on whether all the parts I've chosen will work nicely both with each other and with mythtv.

Parts:
Motherboard: [Asus P5Q-EM LGA 775 Intel G45 HDMI Micro ATX]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131336")
Processor: [Intel Core 2 Duo E8400 3.0 GHz]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819115037")
Case: [Antec Veris Fusion Black 430 Micro ATX]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811129030")

Those are the components I'm really worried about working together (ie, will the ports on the motherboard fit nicely into slots already in the case? Is the processor definitely supported?)

Besides that, I'm assuming any standard SATA hard drive will work and I can get ram at the right size and speed. I'd like to use a slim, slot-loading CD drive but don't think that will fit in the slot on the case? If anybody knows either way, I'd appreciate it.

And lastly, the thing I'm really worried about: in my first mythtv box I have a Hauppuage PVR-500 and it's wonderful. That's been discontinued unfortunately (and doesn't support digital signals, anyway), so I'm looking at the WinTV-HVR-2250 but everything I've seen seems to imply it's not supported yet. I'd love to get somebodys personal experience with it, or just a website I can check for reliable updates (perhaps somebody to donate some money to?) Failing that, recommendations on a nice, pci-e (preferably dual, hybrid) tuner card would be wonderful.

Thanks for your time,
Aaron

---

### Post by korb on 2008-11-30
Support in progress:

[[COLOR="Blue"]http://www.mythtv.org/wiki/index.php?title=Hauppauge_HVR-2250&printable=yes[/COLOR]]("http://www.mythtv.org/wiki/index.php?title=Hauppauge_HVR-2250&printable=yes")

I can recommend the [[COLOR="Blue"]pcHDTV-5500[/COLOR]]("http://www.mythtv.org/wiki/index.php/PcHDTV_HD-5500") having just purchased one. It's only a single tuner (one each analog and digital) but it seems to work pretty well right out of the box (and the drivers are included in all recent kernels).

On the other hand, according to the above link, support for the card you want is expected "by the end of the year", so if you're not in a hurry, it looks like you could get what you want (and after reading the specs, I want one, too!). :)

Good luck!

Bill

---

### Post by reldruH on 2008-11-30
It's funny you should mention that link here; I'm the one who got the email from Hauppauge support about it being working in linux by the end of the year. I'll take a look at the pcHDTV tuner, but I'd really like the 2250; there are enough people where I live that I'd like to have 4 tuners total (in a miniATX box, no less) so my number of expansion ports is pretty small. What I ended up deciding to do is stick with a dual analog-only tuner from Hauppauge until the 2250 is supported. Thanks for your help.

---

### Post by zachtib on 2008-12-05
> **reldruH said:**
> What I ended up deciding to do is stick with a dual analog-only tuner from Hauppauge until the 2250 is supported. Thanks for your help.

I've got a Hauppauge 2250 right now, and it's a nice card.  I'm also waiting for Linux support, but in the meantime, I've got it in my Windows box running Media Center.

I hadn't seen that link about it working in Myth by the end of the year, that's great!

---

### Post by LowSky on 2009-05-27
I got it working using the beta driver and made a crued tutorial, hope this helps the community

[http://ubuntuforums.org/showthread.php?p=7344302#post7344302](http://ubuntuforums.org/showthread.php?p=7344302#post7344302)

---

### Post by azich on 2011-01-26
I was able to get an HVR-2250 working on Ubuntu 11.04 2.6.35-24-generic by substituting the basic hg clone / make / make install with something a bit more complicated but ultimately successful for me:

```

0. `sudo apt-get install v4l-conf`
1. `hg clone http://kernellabs.com/hg/~stoth/saa7164-v4l`
2. Use this as v4l/.config: [http://pastebin.com/4GPrszBV](http://pastebin.com/4GPrszBV)
4. `make`

5. For all files with implicit declaration of function 'usb_buffer_free', add the following to the top after the #includes.

#define usb_buffer_alloc(a, b, c, d) usb_alloc_coherent(a, b, c, d)
#define usb_buffer_free(a, b, c, d) usb_free_coherent(a, b, c, d)

6. Repeat steps 4 and 5 until you no longer encounter the 'usb_buffer_free' errors.

7. You should now encounter the 'struct net_device' errors. Download the full linux-source-2.6.35, decompress it, and copy the following to the v4l directory.

linux-source-2.6.35/drivers/media/dvb/dvb-core/*.h
linux-source-2.6.35/drivers/media/dvb/dvb-core/*.c

8. `make`
9. You may encounter more 'usb_buffer_free' errors, if so, repeat steps 4 and 5 again until it goes away.
10. `sudo make install`
11. `sudo modprobe -r saa7164; sudo modprobe saa7164` or `reboot`

```

Here is the relevant section of the kernel log after the modprobe: [http://pastebin.com/rWB6WBhB](http://pastebin.com/rWB6WBhB)



Hope this helps!

---

### Post by RedHead904 on 2011-04-29
I just installed 11.04 2.6.38-8-generic and tried to follow the instructions given above. I have, at this point, a few questions.
 
1. I ran terminal and entered the first two commands (steps 0 and 1). I ran those commands at my home folder since that is where terminal opens. Is that the proper place to do this?
 
2. At step 2, using "ls", I found that my home folder now contained a sub-folder "saa7146-v4l" and another sub-folder "v4l" within that. That is where I created the ".command" file. Again, was that the right thing to do?
 
3. I didn't let the fact that the insturctions omitted a step 3 worry me. Should I have been?
 
4. When I did the "make" command in step 4, I got the response "No targets specified and no makefile found". I was still in my home folder since there are no instructions to cd to any other location. What should I do to make the "make" command work?
 
Any help on these points will be appreciated and I'll gladly forge on into the next steps.

---

### Post by BrandonXavier on 2011-05-01
I didn't need to go thru any of that process to get my HVR2250's working in 11.04 (64 bit).  The only thing missing was the firmware file "NXP7164-2010-03-10.1.fw". The relevant instructions from [http://ubuntuforums.org/showthread.php?t=1567490](http://ubuntuforums.org/showthread.php?t=1567490) are:

> wget [http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw](http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw)
sudo cp *fw /lib/firmware

Note:  I have no idea if the remotes work - my HVRs are in basically a dedicated backend (all my viewing is done from frontends)

---

### Post by joel.wietelmann on 2011-07-20
> **BrandonXavier said:**
> I didn't need to go thru any of that process to get my HVR2250's working in 11.04 (64 bit).  The only thing missing was the firmware file "NXP7164-2010-03-10.1.fw". The relevant instructions from [http://ubuntuforums.org/showthread.php?t=1567490](http://ubuntuforums.org/showthread.php?t=1567490) are:



Note:  I have no idea if the remotes work - my HVRs are in basically a dedicated backend (all my viewing is done from frontends)

THANK YOU!!!!  I went through all the complicated steps I read online (compiling latest v4l, etc) and this did the trick like magic on a fresh install with no other hackery.  This should be posted all over the internet.

Edit: Spoke too soon - Channel scan is finding nothing.  I'm on analog cable with maybe 5 digital channels thrown in there.

---

