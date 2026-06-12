---
title: "New Mythbuntu build"
date: 2014-10-02
forum: Mythbuntu
---

### Post by Mike_Brown on 2014-10-02
New to this forum -- first post --

I am building a MythTV box from components I have left over from past computers. The computer is to be used as an OTA PVR and be set up with MythBuntu using a MythTV backend and Frontend --connected to Home Theater System via HDMI for the Video and analog audio off the motherboard for sound. I only will us the components I already have – not going to put any new money into it. I plan to install XBMC – KODI – on my Windows 8.1 box as a Frontend accessing this box via Cat5 set up with Static IP addresses on my home network. I have used Ubuntu 8.4 and 10.2 so I have experience with setting up Ubuntu.
The components:
·         Dell Optiplex 755 with Core2 Duo 7500 (2.93gHz)
·         Either 1 - 160Gb + 1 - 250Gb hard drives or 1 – 1Tb Hard Drive
·         2 Hauppauge HVR 1600s
·         Video card with 1Gb ram (I have 2 laying around – both are GigaByte brand)
·         Sony VIAO USB IR receiver (not sure what Model #)
 
My questions are:
·         Should I expect this to give good results as a PVR?
·         Any known conflicts with any of the components?
·         Should I set up the computer with Ubuntu then add MythTV or just install MythBuntu from the beginning?

Thanks in advance for any pointers, information, or critiques.

---

### Post by khPWXxF on 2014-10-20
Welcome to the forum.
 
That processor should be fine for recording – just a slight question of whether it will support post-processing of the recordings to (say) eliminate commercial breaks.  I choose not to do this anyway as it’s so easy to simply skip them on playback, apart from which playback whilst still recording is so frequent in my household.
 
RAM – aim for at least 2GB.  I have heard of 1GB setups; indeed my first “what’s this mythtv all about” stab was with a Pentium with 1GB (and an 8GB disk!!) before I acquired a proper setup.
 
Disk:  I’d suggest you use the 160GB for everything in your initial testing phase with 3 partitions - for root, swap and /var/lib/mythtv (media).  Then migrate by moving the media to your 1TB.  That will split operating system, swap and database on the 160 from the recordings.
 
Tuners:  You don’t say where you are or what you hope to receive, but I guess from your tuner choice it’s North America.  I understand that those tuners are well supported but provide more details and hope for a ‘local’ response.
 
Graphics.  I understand you to say that you want a combined frontend/backend plus a frontend running on windows.
 
For the combined FE/BE the choice of graphics cards is very important because of availability of drivers and the offloading of work from the cpu.  Nvidia has been card of choice for years, Intel second choice and AMD not well supported, but I can see a change of opinion with Intel climbing in popularity in recent months.  Which cards do you have?  That could result in either eternal happiness or grief.
 
I cannot comment on myth on windows.
 
As for Ubuntu + mythtv or Mythbuntu question, you will get many views.  I started with Mythbuntu (back in 2009) as a Linux novice and would make that choice again, but others will advise otherwise.
 
Hope this helps.
Phil

---

### Post by dannyboy79 on 2014-10-20
**Should I expect this to give good results as a PVR?**
that tuner is well supported within mythbuntu, if you're in NA check schedules direct to see if they have a listing for OTA lineup for your local area. i would partition the 160GB hard drive as
20GB /
Same GB size as physical RAM /swap
Remaining space for /var/lib/mythtv
For the 1 TB drive I would mount it where ever you want and make it a secondary storage location for recordings.
**· Any known conflicts with any of the components?**
you don't mention what graphics card you'll have in the backend/frontend, if you want to be able to playback video files pick a decent gpu with good hdmi output support in whatever linux driver you go with whether propritary or open source
**· Should I set up the computer with Ubuntu then add MythTV or just install MythBuntu from the beginning**
it's really a preference thing but mythbuntu is very very awesome and convenient!

---

### Post by anoldguy on 2014-10-20
The BackEnd is where your TV tuners are.  You can use the BackEnd computer to also playback via its Front End.  You can also have another Front End to playback over the network.  The TV recording does not take much processing and bandwidth.  Playback over your network does take bandwidth.  I can playback on my iPad, but the WiFi bandwidth limits to watching non-High Definition.  I had occasional drop outs with 100 MBS Ethernet LAN (my router has 16 ports and I see 3 dark right now) but switching to 1000 MBS gives me no problems. 

I have been using MythTV on my Back End computer and Mythbuntu on a separate Front End in the living room.  Mythbuntu strips out a lot of Ubuntu to make it small.  

If you are in North America, you will want to subscribe to Schedules Direct(.org).  It is a listing service that gives you two weeks of listings.  It is a very nice thing to have and makes recording programs easy.  SD has had to go to another listing provider, so the recommended version in Oct/2014 is MythTV 0.27.4 

MythTV can be a challenge to set up, but I would not be without it.  Imagine the best features from all other DVRs, and more.  I don't like to use Windows Media Center anymore; it seems too constricted to me.  The over-the-air quality is terrific.  Be sure to periodically back-up your database.  See the wiki at mythtv.org

---

### Post by Mike_Brown on 2014-10-21
Thanks for the replies.

This MythTV DVR build is a project to build a DVR from spare components and parts I already have and to attempt to have only ‘sweat equity’ in it – ie: no money investment. (I actually converted the Dell ‘slim’ desktop case by inserting spacers in the 4 sides to make the case tall enough for the Hauppauge full height cards.)

I have built the box with these components:
·          Dell Optiplex 755 with Core2 Duo 7500 (2.93gHz)
·          4GB DDR2 RAM
·          1 - 250Gb Hard Drive + 1 – 1Tb Hard Drive
·          2 Hauppauge HVR 1600s
·          Video card = GigaByte GV-R435OC-512I -- Radeon HD 4350 with 512Mb ram (HDMI out)
·          Sony VIAO USB IR receiver (not sure what Model #)
·          Connection to network via Linksys WRT120n router (hard wired)
 
I am in Florida and I will be using this as an OTA DVR. I hope to be able to set recordings by time/channel instead of using a scheduling service. I already have a store-bought DVR (an older Phillips – same as some Magnavox units) which I use this way – the problem with the current DVR is it has one tuner so only one channel at a time can be recorded. Since the Phillips is getting old, I plan to use the MythTV box as a replacement and upgrade – the Phillips only plays back in DVD quality 16 X 9 format, not true HD. This box will be full HD.
 
I installed MythBuntu on the 250MB hard drive last weekend and have had a few set-up problems. I am setting up this box to run as a BackEnd and also as a FrontEnd. Since I have not decided whether to connect directly to my Home Theater or to locate in a different room, I am also going to install XBMC –KODI on my Windows HTPC as a separate FrontEnd to be able to access the recordings on this box.
 
The main issue I am having is setting the IP address for the Back End. I have set my other hard-wired computers to static IP addresses and have tried to do the same for the Back End in the MythBuntu Back End setup screen. Each time, the only options the address cell lists are the default address – 127.***.0.1 -- and whatever dynamic address the router has chosen. I haven’t had time to research and sort this out. The WIKI I have read and also the message at the bottom of the screen says that the address can be set, but the address cell will not take any input. I have tried to change the IP address in the Ubuntu ‘Network’ tab under ‘Settings’, but that hasn’t seemed to work either.
 
Another issue is that the BackEnd seems to only see one of my Hauppauge cards. The computer sees both of them in the BIOS settings page at startup so I know they are both connected properly.
 
I think I will re-install MythBuntu and partition the 250MB as suggested and then have the 1TB for recordings.
 
Thanks again for any pointers, information, or critiques.

---

### Post by Mike_Brown on 2014-10-27
I have come across one issue during the set up -- It does not appear that myth is going to use my 1TB drive. I partitioned my 200GB drive with root + swap + /var/lib/mythtv. Every time I boot, I have to mount the 1TB drive.

Is this something to be concerned about? Will Myth access this drive with recordings? If not, how can I make Myth aware of this drive for recordings?

Thanks for any advise.

---

### Post by TheMiz on 2014-12-05
This is kind of reviving an old post (which I hate doing), but I was looking for advice on drive partitioning, and saw a question I could answer:
 > [COLOR=#000000] have come across one issue during the set up -- It does not appear that [/COLOR][COLOR=#417394]myth[/COLOR][COLOR=#000000] is going to use my 1TB drive. I partitioned my 200GB drive with root + swap + /var/lib/mythtv. Every time I boot, I have to mount the 1TB drive.[/COLOR]

[COLOR=#000000]Is this something to be concerned about? Will [/COLOR][COLOR=#417394]Myth[/COLOR][COLOR=#000000] access this drive with recordings? If not, how can I make [/COLOR][COLOR=#417394]Myth[/COLOR][COLOR=#000000] aware of this drive for recordings?[/COLOR]

You need to edit /etc/fstab to make that extra disk auto mount on boot.

---

### Post by Mike_Brown on 2014-12-11
> **TheMiz said:**
> This is kind of reviving an old post (which I hate doing), but I was looking for advice on drive partitioning, and saw a question I could answer:
 

You need to edit /etc/fstab to make that extra disk auto mount on boot.

Thanks for the reply. At the time I wrote that, I had 250Gb & 1Tb hard drives in the computer. The 250Gb was old and gave me other troubles, so I just took it out which resolved the problem by only having 1 drive and letting Mythbuntu make all adjustments.

---

