---
title: "Testing a new OS"
date: 2010-08-31
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Scunnered on 2010-08-31
When browsing the forums or Linux magazines I see the warning that we should not test new OS on a production system.  As a home user my needs are low but although ensuring that my data is regularly backed up I am reluctant to for example load Ubuntu 10.10 on to my system.

I would like to see how Meerkat looks and works but seek guidance on the best approach to ensure  the safety of my current data.  Currently I have my data on a separate /home partition and wonder whether it is safe enough to work with another partition or is there a better way.

Up till now I have tended only to look at the next Ubuntu offering when at release candidate stage and have fortunately not had problems.  I feel that as I am now more comfortable with Ubuntu that I may be able by testing offer something back and it is this that prompts this question.

Your kind assistance will be appreciated

---

### Post by philinux on 2010-08-31
Moved to Maverick testing forum. Please read the forum stickies.

---

### Post by howefield on 2010-08-31
> **Scunnered said:**
> I would like to see how Meerkat looks and works but seek guidance on the best approach to ensure  the safety of my current data.

Many different approaches that you could take. The three I favour just now are as follows.

1. Make an image of my disk with Clonezilla. Safety first, so that if anything goes wrong, I'm back in business in a few minutes - (and all valuable data backed up in multiple locations). 5 partitions on my disk, / /home /swap, then an extended with 2 partitions, one for loading eg, 10.10 and one data/storage partition.

2. Install onto a pen drive with persistence, so nothing touches the hard disk.

3. Virtual machine, it isn't exactly like the "real" thing, but close enough to get to know whether I want to bother with options 1/2.

---

### Post by go7Ul1ai on 2010-08-31
Aye, I would just make a liveCD or liveUSB and boot it up from there, that way your data is safe :)

---

### Post by VMC on 2010-08-31
> **Scunnered said:**
> When browsing the forums or Linux magazines I see the warning that we should not test new OS on a production system.  As a home user my needs are low but although ensuring that my data is regularly backed up I am reluctant to for example load Ubuntu 10.10 on to my system.

I would like to see how Meerkat looks and works but seek guidance on the best approach to ensure  the safety of my current data.  Currently I have my data on a separate /home partition and wonder whether it is safe enough to work with another partition or is there a better way.

Up till now I have tended only to look at the next Ubuntu offering when at release candidate stage and have fortunately not had problems.  I feel that as I am now more comfortable with Ubuntu that I may be able by testing offer something back and it is this that prompts this question.

Your kind assistance will be appreciated
Its very easy to create a lone partition to test with. What is the output of ```
sudo fdisk -l
```

---

### Post by ktp on 2010-08-31
> **lee.jarratt said:**
> Aye, I would just make a liveCD or liveUSB and boot it up from there, that way your data is safe :)

best way to go if you just want to test driver it...if you like it then there is always create new/test partition and install.

---

### Post by andrewabc on 2010-08-31
As other have stated liveusb should work best to test. Much faster than livecd. It should tell you the if all the basics work (audio/video/drivers/apps).

---

### Post by Scunnered on 2010-09-02
My thanks to everyone for their guidance. 

I have sufficient space on my HD to have an additional partition but was reluctant to use that as I was scared of problems.  I like the idea of the USB so I will see what I need to do for this method.

I see that the beta is not available to download so this looks like a good time to take matters forward.

Again my thanks

---

### Post by scokem on 2010-09-02
If you are merely interested in seeing what it looks like and checking out new features etc then virtual machines are ideal for this. Get VirtualBox and away you go. If anything gets really screwed up you can just trash the virtual machine and re-install again (or roll back if you've been taking snapshots). I've always got several virtual machines that run the latest builds of Ubuntu and Ubuntu NBE and a couple of other distros so I can see how they're evolving and every new release cycle I just install the newest build.

---

### Post by Scunnered on 2010-09-02
I had a look at VirtualBox and got into a fankle.  Whether it was my inexperience or not I am not sure.

I run only Ubuntu and from memory was informed that VirtualBox only supported 9.10. This resulted in me walking away from that option.

From what you say I obviously got things wrong.  Will have another look at things later on.

Have installed on HD on a separate partition and so far so good.

---

### Post by Scunnered on 2010-09-02
Initial reaction favourable. 

When loading config network with DHCP, network auto configuration failed but when the install completed I was able to access my wireless connection without problem.

Had slight difficulty in loading Restricted Extras and have reported that on Launchpad.  One strange thing is that as my partner uses my system at times and she has visual problems I have attached a 21 inch screen to the laptop.  If I set the page to the maximum it will display OK on the screen but the laptop does not.  I have about a half inch either side of the page and nothing so far will fully populate the screen.

Will keep looking at things and see what develops.

---

