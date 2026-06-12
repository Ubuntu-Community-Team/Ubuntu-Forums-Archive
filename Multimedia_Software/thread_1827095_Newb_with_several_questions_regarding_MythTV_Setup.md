---
title: "Newb with several questions regarding MythTV Setup"
date: 2011-08-17
forum: Multimedia Software
---

### Post by WiredDriver on 2011-08-17
Hi all,
I'm an absolute newb to linux and MythTV and I have some questions regarding hardware options and setup.  I have never built a computer or modified major components before, so some of this might be incorrect.
   
  I was given a Dell Optiplex gx280 that I plan on using as a frontend/backend combo.  Currently the system has:
  1gb (2 512mb sticks) DDR2 memory
  80gb SATA HD
  280w Power Supply
  1 PCI express 16 pin port
  3 PCI ports
  [Specs from Dell]("http://support.dell.com/support/edocs/systems/opgx280/en/ug/specs02.htm") (I have the desktop tower).

  I have already installed Mythbuntu 11.04, but that&#8217;s it.
   
   
  I plan on getting a TV Tuner and graphics card so I can output HDMI to my receiver (audio) and to the TV (video).  If I need I can also upgrade the memory and possibly the power supply (only if needed).  Later on I will plan on putting in a bigger HD, but for now my budget limits this.
   
  **General Questions:**
  Since I only have 1 PCI express slot, should I use it for the tuner or the graphics card?  I&#8217;m not sure which tuner or video card to look at since I&#8217;m not sure which one should use the PCI express slot and which should use just PCI.
   
  Also my bus type for the PCI Express is listed as 1.0a, but I haven&#8217;t seen anything for that specific version, do I need something that&#8217;s 1.0a or will anything work?
   
  Does the tuner card or the graphics card encode the video (or does it depend on my hardware?)?
   
   
  **Tuners:**
  For the tuner I would like to have a dual tuner, but this might not happen in the beginning (budget dependent).  I would be satisfied with capabilities provided by a single tuner for now.  I have been looking at the HDHomerun box to use a dual tuner, but my concern here is network congestion.  Will I notice a performance decrease on my network if this is used?
   
  Also, I work from home and VPN to my employer everyday.  I know when I&#8217;m connected to the VPN I cannot print to my home printer as it sits on my network, not my employers network.  Would this also be the case with the HDHomerun?  I&#8217;m wondering if I will not be able to record or watch tv via the HomeRun if my VPN is active.  If so, this is a major problem.
   
  I was also wondering if the HDHomerun could be plugged into a switch that&#8217;s plugged into my router instead of directly into the router.  I ask because I was going to run one wire from the router to the entertainment center where a switch would be located where the HTPC, Blu-ray player, and PS3 would be connected.  I would like to add the HDHomerun here as that is where my TV antenna is currently located.  Would this work?
   
  When looking at tuners I was looking at getting the [hauppauge hvr1600]("http://www.hauppauge.com/site/products/data_hvr1600.html").  I guess the downside to this one is if I need to use the PCI Express slot and it&#8217;s only a single tuner.  I think the benefit would be I would have room to add another one later on to have two tuners.  I was also interested in this one because it could control a cable/ satellite box later on if I add that back in.  Is it correct that I could then just use my Myth box as my DVR and not have to pay my provider the DVR subscriptions?  I believe so.
   
  I&#8217;ve also looked at the [hauppauge hvr2250]("http://www.hauppauge.com/site/products/data_hvr2250.html"), but my concern here is it looks like not all of the functions (s-video) work currently with this card.  I also don&#8217;t think my computer has the PCIe X1 slot.
   
  **Graphics card:**
  
  I&#8217;m looking to output video to a 47&#8221; 1080p TV via HDMI.  It looks like most video cards will handle this so that&#8217;s not an issue.
   
  Is 1gb DDR3 overkill for a dual tuner system?  What is the minimum amount of memory you feel is necessary.
   
  If the graphics card requires, it is possible for me to upgrade my power supply.
   
   
  **Conclusion:**
  If you could build a decent setup, what components would you use?  I&#8217;m not looking to store my entire media library on here.  I&#8217;m just looking at recording a show or two here and there while the wife and I are on vacation or something.  I was hoping to do this for around $250.
   
  I hope everything I&#8217;ve stated above is clear and correct.  If you have any questions, please ask.

---

### Post by WiredDriver on 2011-08-18
bump

---

### Post by BicyclerBoy on 2011-08-19
The graphics card is the most important component.
You must use the PCI express slot for this.
Don't assume any video card is okay, they're not.

If you want best performance go nVidia, there is no argument.
The best HTPC nVidia cards do not require lots of power, quite the opposite.
I rate them:
GT430, GT220 (GT240 over speced)
GT520  half height cheap/low power but too slow for best video PQ.
Video card needs 512MB.
A GT530 GT535 would be perfect but they do not exist in consumer cards only OEM.

PCIexpress is backwards compatible as long as the slot is the correct physical size/length.
Your machine has 1 PCIe (x16), thats good should be fine..

Hard to answer the tuner questions as your country /location changes the rules..
Tuners could be USB if your got no space.
Seems to be some new cable card options in US lately Ceton & Prime.
HD Homerun is good choice. An HD recording is 5GB/hr.
HD/digital recordings are just a datastream (compressed un-decoded) so not CPU intensive.
A wired home network can move that in 2-5 minutes.

I do not think the analogue part works on the HVR220

1GB ram okay, more is always better, 64bit is better if transcoding.
You need HDD space, get a 1TB SATA green drive US$50. 
 
Sources of info:
All tuner card support comes form LinuxTV V4L-DVB project
[http://linuxtv.org/wiki/index.php/Main_Page](http://linuxtv.org/wiki/index.php/Main_Page)

mythbuntu forum right here..

MythTV wiki pages..


By using SAT HDD & PCIe video you get components you can reuse later, the the weakest link (& noisest/power hungry) is the CPU.
Pentium is a dog compared to core2duo.

I don't know about your network issues.

---

### Post by WiredDriver on 2011-08-23
Thanks BicyclerBoy.

Here's what I'm currently looking at:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814121397](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121397)

Then  use the hauppague 1600 tuner.  I have a local shop here which will give  me 2 sticks of DDR2 memory for 2gb memory.  If needed, I'll step up to  this PSU [http://www.newegg.com/Product/Product.aspx?Item=N82E16817371033](http://www.newegg.com/Product/Product.aspx?Item=N82E16817371033)

---

### Post by BicyclerBoy on 2011-08-24
The video card looks fine.
That's a damn good PSU for the money.
Seasonic Gold X series are the best but cost a lot more.

If you are using 10.04, you will need to update the alsa user-space drivers to 1.0.24 for HDMI audio.

The GT520 video card needs a fairly recent nvidia driver 270 ..

Note the warning about the HVR-1600 versions.
[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600)

You can run later kernels with 10.04 to get the kernel support for the tuner card.

---

