---
title: "nvidia driver questions (so I don't screw things up)"
date: 2010-08-08
forum: Multimedia Software
---

### Post by ed-koala on 2010-08-08
I'm thinking of updating my nvidia graphics driver from the nvidia website, but checking into this I have a couple of questions that came up.

1.  nvidia lists the current driver as 256.44.  Checking my hardware drivers only shows "current version," no version number is listed.  Synaptic lists the driver as 195.36.24.  That driver doesn't even appear on nvidia's web site under current or archived drivers.  What gives and is 256.44 actually different and newer than 195.36.24?

2. Assuming I stop gdm and install from nvidia's run file, will this overwrite my current xorg.conf?  I have to make slight modifications to the file for my dual video cards and sli to work properly so I want to know if I need to worry about this.

3.  How buggy is the new driver?  General idea is all I need how likely I may be to hit a problem.

Thanks!

---

### Post by Quackers on 2010-08-08
I'm in a similar situation. I'm not absolutely sure whether or not it's the same driver as the "current recommended" driver already installed. I decided that as everything is working as it should do I'd leave well alone :-)

---

### Post by ed-koala on 2010-08-08
That's the way I'm leaning myself.  My current driver is working fine, and I'm not sure if updating will help anything (mainly World of Warcraft).

Still, 195 to 256 seems like quite a jump....

---

### Post by Quackers on 2010-08-08
As my current driver isn't numbered I can't tell which one it is. Personally I have decided not to install new video drivers unless they come through System > Admin > Hardware Drivers. TBH as I'm not a gamer it wouldn't really affect me.

---

### Post by Frogs Hair on 2010-08-08
The latest Nvidia driver can be installed via the ppa . If the current driver is working for you there is no reason to change it , read the recent changes at Nvidia and see if it will improve performance with your current hardware or games.

---

### Post by Ginsu543 on 2010-08-08
Which PPA please?

---

### Post by Soul-Sing on 2010-08-10
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by VH-BIL on 2010-08-10
I agree with "Frogs Hair":
If it ain't broke, don't fix it!

---

### Post by ed-koala on 2010-08-10
I went ahead and upgraded anyway ... I'm just a fool for having the latest version I guess.

All went well though I did have to re-do my xorg configuration file so my dual video cards would work properly.  I also had to reboot - logging out wasn't enough, but no biggie there.

Thanks for the help!  (Still wondering why the 195 drivers don't appear on nvidia's website, but I'm not going to worry about it.)

---

### Post by cascade9 on 2010-08-10
> **VH-BIL said:**
> I agree with "Frogs Hair":
If it ain't broke, don't fix it!

+1. 

If there is some major improvements in performance and there is some game (or similar) thats giving problems, maybe its worth thinking about then...but upgrading just because there is a newer version can have issues. Remember the 195.xx.xx drivers that were cooking cards?

> **ed-koala said:**
> (Still wondering why the 195 drivers don't appear on nvidia's website, but I'm not going to worry about it.)

They do. If you seach using the 'download drivers' button, you will only find the 256.xx drivers, but there is a way of seeing the older versions- just under 'download drivers' there is 'beta and archived drivers', and searchign there should bring up at latest 'archived' drivers. 

The 195.xx drivers are pretty new anyway. 

Edit- that was a right mess, sorry, fixed now.  

I'd link to that page, but the nvidia site wont allow that....

---

### Post by ed-koala on 2010-08-10
Yeah, I probably shouldn't have upgraded as everything was running fine, but since it worked I won't cry over it.

I went to the archive page ... the first listing is for the 185 series driver.  No 195 version is there. At least not for the AMD64 driver list. No big deal, it's in the repositories, but it ain't where it should be, at the top of the archive page list.

---

### Post by cascade9 on 2010-08-10
Thats just weird....if I search for archived drivers for 6XXX-9XXX in the archive section, I get the all the drivers that can (in theory) work with those cards, ranked in order of release. 

top of the list is 173.14.27 (August 4, 2010), then 256.44 (August 2, 2010) then 256.35 (June 22, 2010) then 195.36.31 (June 11, 2010) and so forth. 

That was seaching for linux 64bit drivers are well.

---

