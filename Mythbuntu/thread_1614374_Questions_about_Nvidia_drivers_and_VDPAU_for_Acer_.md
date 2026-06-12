---
title: "Questions about Nvidia drivers and VDPAU for Acer RevoAspire"
date: 2010-11-05
forum: Mythbuntu
---

### Post by Meph1st0 on 2010-11-05
Peers,

As already mentioned in the title, I have an Acer RevoAspire 1600.  It has the Nvidia ION LE graphics card.  I want to be certain that it's using VDPAU and the latest (I think?) Nvidia drivers.  I've read posts about people using the Avenard repository and that by using it it drastically improved performance.  I've also read that the Avenard repository is no long necessary if you're using auto-builds.

I believe I am using auto-builds (0.23.1 PPA with the Mythbuntu-testing PPA) with this installation but I don't know if I have the most current Nvidia drivers.  In my X Server Settings it shows that I have version 260.19.06 but the Nvidia drivers website shows 260.19.12 as their most current. [http://www.nvidia.com/object/linux-display-ia32-260.19.12-driver.html](http://www.nvidia.com/object/linux-display-ia32-260.19.12-driver.html)  Also, under the Hardware Drivers application it only shows one available Nvidia driver to select (And all it says is Current Version).  I've also read that I can enable the Nvidia repository (which I can't figure out how to do) and it'll show me more options for Nvdia drivers. I've read that I should be running the 195 version as opposed to the 185 version. But I don't even know which version I'm running except for what it shows in the X Server Settings which doesn't say 185 or 195.

So it appears I don't have the latest version.  So naturally you'd think I should update.  However, on that same Nvidia download page it talks about removing VDPAU support which is what I want most of all.

So now I'm confused; very confused.  How do I know if I'm using VDPAU for sure?  I have it enabled in myth frontend.  And HD content works fine in myth frontend.  But, I'm also running Boxee and HD content does not work fine there.  I've enabled VDPAU in Boxee too, but online content is very choppy.

It would be very helpful to receive a clear explanation on this.  This is one of those times when too much research has caused nothing but confusion.

Thanks everyone.

Jonathan

---

### Post by ian dobson on 2010-11-05
Hi,

YOu have the latest version of the NVidia drivers that ubuntu offers per repositry. Maybe you could manually download and install the latest driver direct from the NVidia web site. I wouldn't recommend it but if you really need the newest version that's the only way, or wait until ubuntu release an new package.

Your problem looks more like a problem with Boxee, if MythTV can playback everything OK, and Boxee can't then maybe have a look at the configuration options in Boxee.

Regards
Ian Dobson

---

### Post by Meph1st0 on 2010-11-05
okay, thank you Ian, I really needed that confirmation about my Nvidia drivers.  Here's some more information that I've come across.  I also have flash 10.1 installed based on what I can see in synaptic package manager.

If I run top and then start a recording (at 1080i) in mythtv frontend I only get about 17% cpu usage. But that's merely a recording and flash is not involved. If I open Firefox and go to Hulu and watch an episode there top shows something like 144% CPU usage. Which can't be right. And I wouldn't think that that would have anything to do with Boxee per se. I'm thinking it's got to be a Firefox / Flash / driver thing.

I've read that Flash does not use VDPAU. At least I think I read that somewhere. However, do you think that using the Avenard repository would fix these problems?

I'm asking that question based upon the information found in this thread: [http://forums.boxee.tv/showthread.php?t=14858&highlight=avenard](http://forums.boxee.tv/showthread.php?t=14858&highlight=avenard)

Though that thread is from January. I can't help but wonder if things have improved with the auto builds since then. Also, because I'm running Mythbuntu 10.10, I can't tell if there's an Avenard repository for that distribution yet.

I know that Firefox and Flash don't really have much to do with Mythtv or Mythbuntu but I'm really just fishing for any help I can get.

Thanks again for your help Ian.

Jonathan

---

### Post by LowSky on 2010-11-05
Flash for Linux doesn't support graphic card exceleration like VDPAU.
The 144% is because your Intel ATOM processor is Hyperthreaded (virtual cores) which means the workload can be split on the CPU making it look like more cores than it actually has.

Flash on Atom processors performs poorly. I know it seems odd that you can play HD recordings with little issue and flash becomes a problem, but its unfortunatly all about softare support. Blame Adobe for weeker than Window's Linux support.

---

### Post by slamhound on 2010-11-05
One thing that I found that dramatically helped my flash performance (at least using the Hulu Desktop Player) was the advice found in the last part of this [page]("http://www.mythtv.org/wiki/Hulu_Desktop_Integration").  Basically, if when opening Hulu Desktop, you switch the resolution to the something lower than you typically have (but which is still the maximum that Hulu is sending anyway), the performance of full-screen flash improves.  This makes Hulu very watchable, whereas before it stuttered too much for me to watch anything.  The resolution switching can be made automatic when you open the Hulu Desktop Player.  This worked for me even on my Ion system.

---

