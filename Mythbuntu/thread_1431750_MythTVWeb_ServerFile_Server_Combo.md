---
title: "MythTV/Web Server/File Server Combo"
date: 2010-03-17
forum: Mythbuntu
---

### Post by Iceman692 on 2010-03-17
I'd really appreciate any help you can offer with this project I am working on. I am doing a lot of research myself, but I have a few questions that I haven't found the answer to. I am a first time Linux user and I don't have access to the machine I want to use yet.
[LIST=1]
[*]I am planning to use a 3 year old Dell XPS laptop for this. **Should a laptop like that be able to handle running MythTV, a web server, and a file server? Given the nature of laptops, would it cause a crash to leave it on all the time? **All of these services will be used in lightly (mostly personal use and some hosted sites), and will hardly ever be functioning at the same time.
[*]I would like to have the file server act as a network drive on my Windows 7 PC when I am on the LAN and outside of the LAN. **Is this possible? If so, could you please direct me to some thread/page about it?** I have not been able to find anything on this.
[*]Since Mythbuntu comes with MythWeb, I know Apache is included. **Is a full LAMP package included (Linux, Apache, MySQL, PHP)? Or do I need to install some of these services seperately for my webserver?**
[*]Since all of this will be avaiable to the web, how do you recommend that I secure my machine?
[/LIST]Again, thanks in advance for the help. Like I said, I'm a new user, but I'm fairly advanced with Windows. Also, I don't plan on taking advantage of this community by simply taking the help and leaving. Once I get this all up and running, I will post a detailed how to, because it seems like a lot of people would be interested in putting together a full featured server like this. I also plan to build a web interface that would integrate all of the features of the server, including a type of online FTP client.

---

### Post by SiHa on 2010-03-17
Purely from a hardware point of view; as you suggest, laptops are just not designed for this. You will, I can almost guarantee, have a hardware failure (fan / PSU) that will be costly to repair before too long @ 24/7 operation.
Why not just pick up an old tower off eBay for next to nothing? These, at least, are designed to cope with continuous operation. If any components fail they are cheap to replace.

---

### Post by timconradinc on 2010-03-17
This could probably work. One thing you don't mention is if you're planning on recording Television or using MythTV for it's other capabilities (movies, music, etc).

Here's my responses, point by point.

1) I use mythtv on a similar-vintage laptop. I'm not sure how high end the XPS laptop is, though, mine was towards the higher end. I just use it as a front end, however. Your laptop likely does not have the horsepower required to run HD video, however. My laptop tries, but just can't play it.

Two things to consider - laptops generally have pretty poor bus speeds and only have one disk. If you are, indeed recording something, you may run into issues where there's just not enough i/o to play it back at the same time without jitters in the video. The same could be said if you were watching a movie and copying a large file to the disk through the file share, as well.

2) You can configure Samba on your laptop to be a share for Windows boxes. I have this set up at home and it seems to work fine with Windows 7 for me. [Here's a guide]("https://help.ubuntu.com/community/SettingUpSamba#Samba%20Server%20Configuration%20-%20Manual"). If you search for 'linux samba' or 'karmic samba', you'll likely find dozens, if not hundreds of guides.

However, this is largely designed around sharing these files from a local LAN. Sharing them remotely requires more set-up to do. You could look at something like OpenVPN to provide remote access to your home LAN to do what you want.

3) LAMP is installed with the web front end, since it's php based, and mythtv uses mysql as a database. There can be some weirdness though, depending on how you set up mythweb. At least in the past, I've had issues where servername/anything got redirected to servername/mythweb. I believe in the configuration center there's an option to change this configuration setting now.

4) I wouldn't recommend putting much of anything directly connected to the internet. Buy an inexpensive wireless router or router. They're about $50 USD, and will stop inbound traffic to the mythtv box at least unless you explicitly configured it to happen.

If you're new to Linux, this is a good place to start. It's difficult to learn anything simply for the sake of learning it. If you have a specific goal, this makes it a lot easier. There's a lot of documentation and guides available on configuring various aspects of Ubuntu to make this easier overall.

Good luck!

---

### Post by Iceman692 on 2010-03-18
Thank's for both of your suggestions. I decided to build a desktop for longevity and performance. I'll detail that later in the post.
 
> **timconradinc said:**
> This could probably work. One thing you don't mention is if you're planning on recording Television or using MythTV for it's other capabilities (movies, music, etc).
 
Here's my responses, point by point.
 
1) I use mythtv on a similar-vintage laptop. I'm not sure how high end the XPS laptop is, though, mine was towards the higher end. I just use it as a front end, however. Your laptop likely does not have the horsepower required to run HD video, however. My laptop tries, but just can't play it.
 
Two things to consider - laptops generally have pretty poor bus speeds and only have one disk. If you are, indeed recording something, you may run into issues where there's just not enough i/o to play it back at the same time without jitters in the video. The same could be said if you were watching a movie and copying a large file to the disk through the file share, as well.
 
2) You can configure Samba on your laptop to be a share for Windows boxes. I have this set up at home and it seems to work fine with Windows 7 for me. [Here's a guide]("https://help.ubuntu.com/community/SettingUpSamba#Samba%20Server%20Configuration%20-%20Manual"). If you search for 'linux samba' or 'karmic samba', you'll likely find dozens, if not hundreds of guides.
 
However, this is largely designed around sharing these files from a local LAN. Sharing them remotely requires more set-up to do. You could look at something like OpenVPN to provide remote access to your home LAN to do what you want.
 
3) LAMP is installed with the web front end, since it's php based, and mythtv uses mysql as a database. There can be some weirdness though, depending on how you set up mythweb. At least in the past, I've had issues where servername/anything got redirected to servername/mythweb. I believe in the configuration center there's an option to change this configuration setting now.
 
4) I wouldn't recommend putting much of anything directly connected to the internet. Buy an inexpensive wireless router or router. They're about $50 USD, and will stop inbound traffic to the mythtv box at least unless you explicitly configured it to happen.
 
If you're new to Linux, this is a good place to start. It's difficult to learn anything simply for the sake of learning it. If you have a specific goal, this makes it a lot easier. There's a lot of documentation and guides available on configuring various aspects of Ubuntu to make this easier overall.
 
Good luck!
 
I do plan on using this system to record TV as well as utilizing the many other features.
 
I appreciate all the help and that has cleared up a lot for me.
 
Now I guess I'm moving on to more specific hardware questions as I start to go through this. **Please let me know what you think of this hardware configuration for what I plan to do with this.**
 
Right now I have:
 
- An empty custom PC case with a couple exhaust fans.
- A PCI WinTV-PVR-150 Analog TV Tuner and Radio Tuner (with onboard encoder to prevent bogging down my processor)
- Pentium Dual-Core Processor (2.48 GHz)
 
I am planning to buy:
 
- Foxconn P41A-G LGA 775 Intel G41 ATX INtel Motherboard (Do I need an additional graphics card or sound card? The spec sheet says that they are onboard, but do I need an additional one for this since its going to be playing video HD and SD?)
- Sony Optiarc 24x DVD+RW Drive
- Rosewill RCX-Z300 92 mm Ball CPU Cooler
- WD10EALS 1TB 7200 RPM 32 MB Cache SATA 3.0Gb/s HD
- Rosewill RV350 350W ATX 1.3 Power Supply
- Crucial 1GB (2 x 512 MB) DDR2 SDRAM
 
This is also my first custom PC. Thanks for any advice you can give on how well this will work with MythTV! Overall, this project is only looking to cost me $250. Not bad. :D

---

### Post by SiHa on 2010-03-18
My own experience of integrated Intel graphics & Mythbuntu was not a good one, but to be fair it was quite an old board, things may have improved. The general favourite for Linux, especially for HD playback is an nVidia chipset capable of [[COLOR="Blue"]_VDPAU_[/COLOR]](http://www.mythtv.org/wiki/VDPAU) HW decoding.
As you're buying new, maybe look for an LGA775 board with integrated nVidia? Something like [[COLOR="Blue"]_this_[/COLOR]](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128363&nm_mc=AFC-C8Junction&cm_mmc=AFC-C8Junction&AID=10446076&PID=3488348&SID=GA-E7AUM-DS2H), it's not full-size ATX, but still has two PCI and a PCI-E slot. (Note, I am not recommending this board in particular, but I have two Gigabyte boards on my Myth machines and they both play nice.) 

Also, IMHO you would be better off with 2GB RAM, the price difference I would have thought would be minimal.

My two pence worth.

---

### Post by timconradinc on 2010-03-18
I'd tend to agree with the 2GB of RAM, it's just nice to have.

According to the release notes [here]("http://www.mythbuntu.org/9.10/release") the IR blaster on the PVR-150 doesn't work, so if you're recording from a cable box, you might have issues. This was the hardware I recently upgraded from, but I didn't spend any time figuring out if it worked before. I know on older releases, I had to follow [these instructions]("http://http://www.blushingpenguin.com/mark/blog/?p=24") and that was for a 2.6.27 kernel, and 9.10 ships with a 2.6.31 kernel.

Plus, I don't think the PVR-150 is going to record HD video, if that's your intention.

I'm old-school unix, but I prefer to spread out i/o as much as possible. I'd recommend buying an inexpensive disk just for the OS & mythtv to be installed, and then keep your 1TB drive *just* for video. 

Even if your plan isn't to do HD video right now, I'd still recommend getting a VDPAU-capable card, so it's there if you decide to use it in a year or two.

---

### Post by SiHa on 2010-03-18
> **timconradinc said:**
> 

I'm old-school unix, but I prefer to spread out i/o as much as possible. I'd recommend buying an inexpensive disk just for the OS & mythtv to be installed, and then keep your 1TB drive *just* for video. 


+1

Also makes for a much easier upgrade / re-install.

---

### Post by Iceman692 on 2010-03-18
I love open source. You can always find the most helpful people around it. lol ;)
 
> **SiHa said:**
> My own experience of integrated Intel graphics & Mythbuntu was not a good one, but to be fair it was quite an old board, things may have improved. The general favourite for Linux, especially for HD playback is an nVidia chipset capable of [[COLOR=blue]_VDPAU_[/COLOR]]("http://www.mythtv.org/wiki/VDPAU") HW decoding.
As you're buying new, maybe look for an LGA775 board with integrated nVidia? Something like [[COLOR=blue]_this_[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128363&nm_mc=AFC-C8Junction&cm_mmc=AFC-C8Junction&AID=10446076&PID=3488348&SID=GA-E7AUM-DS2H"), it's not full-size ATX, but still has two PCI and a PCI-E slot. (Note, I am not recommending this board in particular, but I have two Gigabyte boards on my Myth machines and they both play nice.) 
 
Also, IMHO you would be better off with 2GB RAM, the price difference I would have thought would be minimal.
 
My two pence worth.
 
Thanks for the tip on the Intel. I'd be hapy to go with nVidia because of their performance in general, but I want something full size, and I'm having trouble finding it. I will be using a pretty big case ([http://www.newegg.com/Product/Product.aspx?Item=N82E16811144026](http://www.newegg.com/Product/Product.aspx?Item=N82E16811144026)) and I'd hate for all those extra PCI ports to go to waste! Afterall, with the way common people will simply throw/give away a PC with plenty of useful parts left in it, I may be able to expand my tuner collection to several tuners.
 
I agree that more RAM would be useful. I may be able to find 4 x 512 MB sticks for free...would a decent board and linux play nice with 4 seperate sticks or should I just spring for 2 x 1 GB sticks? I'm seeing varying opinions across the web.
 
> **timconradinc said:**
> I'd tend to agree with the 2GB of RAM, it's just nice to have.
 
According to the release notes [here]("http://www.mythbuntu.org/9.10/release") the IR blaster on the PVR-150 doesn't work, so if you're recording from a cable box, you might have issues. This was the hardware I recently upgraded from, but I didn't spend any time figuring out if it worked before. I know on older releases, I had to follow [these instructions]("http://http//www.blushingpenguin.com/mark/blog/?p=24") and that was for a 2.6.27 kernel, and 9.10 ships with a 2.6.31 kernel.
 
Plus, I don't think the PVR-150 is going to record HD video, if that's your intention.
 
I'm old-school unix, but I prefer to spread out i/o as much as possible. I'd recommend buying an inexpensive disk just for the OS & mythtv to be installed, and then keep your 1TB drive *just* for video. 
 
Even if your plan isn't to do HD video right now, I'd still recommend getting a VDPAU-capable card, so it's there if you decide to use it in a year or two.
 
Speaking of IR, I'm not worried about the blaster since I will be using straight coax; however, I do need a way to rig up an IR reciever. I haven't found anything on IR recievers on NewEgg. Is there a solution that can be integrated into the box? I have a USB IR reciever from my old Dell Media Center Laptop and I plan to use the same remote, but an integrated solution sure would be nice...
 
I do plan to build up to HD eventually, but at the moment, my goal is an average box first and upgrade to the fancy things once that's done. After all, adding a tuner is a simple matter of plugging it into a PCI and adding the settings. I will still leave my analog in as a secondary tuner.
 
> **SiHa said:**
> +1
 
Also makes for a much easier upgrade / re-install.
 
UPGRADING...this has been a subject on my mind for most of the day. As I'm sure you read, this will be a combo server. I'm wondering what would be the easiest way to go about this in relation to upgradability. I suppose if leave the web files on the 1 TB drive, upgrading to the latest version of MythUbuntu would keep everything functional except a few settings I may have to tweak due to a problem someone mentioned earlier with MythTV taking complete control of the webserver as default. Then I'd probably have to reconfigure my file server things all together. Is there an easier way to configure this to where updating would require very minimal side effects on the services I have already functional? When upgrading, does MythUbuntu keep the settings from the previous version?
 
[COLOR=red]**Once again, you are the best!**[/COLOR]

---

### Post by Iceman692 on 2010-03-18
After more searching, I did find an internal IR receiver.
 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16811999191](http://www.newegg.com/Product/Product.aspx?Item=N82E16811999191)
 
There are some reviews that people got it to work for this exact purpose...although they also mention the hell they had to go through to get it working. Anyway, this looks like the solution. Hopefully I can get my WMC remote working with it. It's a decent price and will fill up those silly 3.5 in floppy drives. lol

---

### Post by timconradinc on 2010-03-19
I haven't done a dist upgrade of mythbuntu, but I did with my desktop at work, which has regular ubuntu. I went from 9.04 to 9.10, and it worked okay, except the upgrade did all sorts of weird things with firefox. I ended up working through those things, though.

My main mythtv system has 2 HDD's in it. I found it useful to just install to one or the other when doing an upgrade, that way everything that was there is still there and i can easily just reboot to that old install.

If you're mucking with apache or pretty much anything on Ubuntu anymore, key is to not edit the actual config files, but drop a file in the daemon.d directory. As an example, there's /etc/apache2/conf.d directory. Create a new file in there for your changes, and upgrades become a lot easier because you just have to copy those files.

Finding a working remote can be a pain. I just use a wireless keyboard to control my mythtv. I find it a lot easier to deal with (And likely less expensive). It's not exactly ideal, though.

---

### Post by Iceman692 on 2010-03-19
I think I found a better motherboard. What do you think of this one? Overkill? Not enough?
 
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4245907&CatId=4543](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4245907&CatId=4543)
 
This PC will be used as both a front end and a backend. Will the integrated graphics be sufficient?

---

### Post by SiHa on 2010-03-20
Looks pretty good to me.

Speaking of upgrading, I was speaking metaphorically. I prefer to do a re-install of the latest version, rather than an upgrade. As has been previously mentioned, upgrades seem to cause problems - this forum is littered with the corpses of failed upgrades. 

MythTV stores everyting in the MySQL database, so you can generally backup the database and restore to a new install.
Occasionally there are database schema differences between Myth versions (such as 0.21 - 0.22), but most tables can still be copied across manually.

---

### Post by pootle42 on 2010-03-20
If you are running other apps I would recommend that you put these in Virtual Machines on top of your mythtv box.  This makes it really easy to back them up, and to upgrade the main box, as well as making it possible to move them onto another host if you should want to at any time.

I run an aptcache proxy VM and a web server in 2 separate VMs on my back end.

I agree with timconradinc, add a an extra big disc (and if its on a laptop, don't use USB, get a sata plug in card, USB eats CPU and cripples disc performance)

I built my backend server as a straight mythtv backend (although I did this by building a straight ubuntu server, adding in myth afterwards), with KVM virtualisation.  It takes very little time to then add new VMs.  Note that you need to be VERY careful about which intel processor you buy though to make sure that it supports KVM.  Intel seem to include (or not) support for virtualisation almost at random - even to the level where what looks like 2 CPUs from the same range with only different clock speeds will have 1 with and 1 without support.

I have a laptop with a 9300m GS nvidia chipset and it will happily play broadcast HD (as in UK freesat).  It can't really manage blu-ray level HD though.

If you're considering an desktop card, I've used nVidia GT220 recently which work well, and use relatively little power (they don't need any extra power leads plugged in) which can be a problem with older power supplies.

---

### Post by Iceman692 on 2010-03-20
> **SiHa said:**
> Looks pretty good to me.

Speaking of upgrading, I was speaking metaphorically. I prefer to do a re-install of the latest version, rather than an upgrade. As has been previously mentioned, upgrades seem to cause problems - this forum is littered with the corpses of failed upgrades. 

MythTV stores everyting in the MySQL database, so you can generally backup the database and restore to a new install.
Occasionally there are database schema differences between Myth versions (such as 0.21 - 0.22), but most tables can still be copied across manually.

Great. That's better than I was anticipating. So do you would install the entire latest MythUbuntu OS in order to upgrade, correct?

> **pootle42 said:**
> If you are running other apps I would recommend that you put these in Virtual Machines on top of your mythtv box. This makes it really easy to back them up, and to upgrade the main box, as well as making it possible to move them onto another host if you should want to at any time.

I run an aptcache proxy VM and a web server in 2 separate VMs on my back end.

I agree with timconradinc, add a an extra big disc (and if its on a laptop, don't use USB, get a sata plug in card, USB eats CPU and cripples disc performance)

I built my backend server as a straight mythtv backend (although I did this by building a straight ubuntu server, adding in myth afterwards), with KVM virtualisation. It takes very little time to then add new VMs. Note that you need to be VERY careful about which intel processor you buy though to make sure that it supports KVM. Intel seem to include (or not) support for virtualisation almost at random - even to the level where what looks like 2 CPUs from the same range with only different clock speeds will have 1 with and 1 without support.


That sounds like a great idea! Of course the processor that was given to me ([SIZE=1]Intel® Pentium® Processor E2220 (1M Cache, 2.40 GHz, 800 MHz FSB)[/SIZE]) list this in the specs:

Intel® Virtualization Technology (VT-x): NO

I guess that means I can't run VMs on it? I thought programs like VMware for windows ran on any CPU?

---

### Post by SiHa on 2010-03-20
> **Iceman692 said:**
> Great. That's better than I was anticipating. So do you would install the entire latest MythUbuntu OS in order to upgrade, correct?


That's what I do. With the database backup and media storage on the second drive, it's fairly painless.

---

### Post by frego on 2010-03-21
> **Iceman692 said:**
> 
Intel® Virtualization Technology (VT-x): NO

I guess that means I can't run VMs on it? I thought programs like VMware for windows ran on any CPU?

You *can* run VM's on that chip, you will just have sub par performance.  Any AMD AM2 or better has VT, Intel is sort of hit and miss on whether any given chip has VT.  KVM and VirtualBox both definitely run better with the VT chips.

---

### Post by Iceman692 on 2010-04-02
The advice that I have gotten so far has definitely steered me in the right direction.

My rig is basically complete. All I need to so is wrap the cords in the case for aesthetics.

I am thinking of using Mythbuntu for my base software package, but I'm unsure. Which distro do you think is most powerful, bug-free, and capable of pulling those server duties on the side?

If you're curious, the specs of my completed rig are as follows:

Case: Apevia X-Dreamer II
Motherboard: EVGA nForce 730i w/ Nvidia GeForce 9300
Power Supply: Sunbeam 680W ATX12V Modular Power Supply
RAM: Wintec Ampo 2 GB (2 x 1 GB) DDR2
Optical: Sony Optiarc DVD Burner w/ LightScribe
CPU: Intel Pentium Processor E2220 (1M Cache, 2.40 GHz, 800 MHz)
CPU Fan: Rosewill RXZ-Z300 92 mm Ball CPU Cooler
Hard Drives: Hitachi Deskstar (1 TB, 7200 RPM, 32 MB Cache) and planning to buy a 60 GB, 7200 RPM Hard Drive for my OS
Tuner Card: WinTV-PVR-150 (Analog)
Wireless Card: Netgear Wifi G
IR reciever: Antec Veris Basic Internal IR Reciever and Remote
Other: Floppy Drive w/ Built-in Memory Card Reader
:P

---

