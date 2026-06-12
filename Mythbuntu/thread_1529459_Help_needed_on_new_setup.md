---
title: "Help needed on new setup"
date: 2010-07-12
forum: Mythbuntu
---

### Post by gjsearle74 on 2010-07-12
Hi,
 
Currently running two windows HTPC's in conjunction with a WHS that I use to store and stream out all my music, recorded TV, etc.....
 
I'm going to make the switch to Mythbuntu using a Backend with all my tuners located out of the way and two small frontend units in the house (love the idea of all the recordings I make being made exactly where I want them stored! [unlike WMC]).
 
I do have a few questions for those more enlightened individuals:
[LIST]
[*]is there a tuner limit on Mythbuntu?
[*]can I use the dvr-ms files from my previous setup, or will I need to convert them?
[*]do I stick with my WHS for backup purposes, or is there a better route? (wouldn't be adverse to setting up a ubuntu server if required)
[/LIST]Cheers
 
Greg

---

### Post by newlinux on 2010-07-12
Welcome to mythtv and ubuntu.
1. No tuner limit that I know of (although I'm sure there is some phyiscal limit). How many are you looking to have?  Most I've had is 10.
2. You can use DVR-MS in mythvideo. I don't know if mythtv's Internal player supports them directly but mplayer and vlc do, and you can have mythvideo spawn mplayer or VLC when encountering dvr-ms files
3. Depends on how much time you want to spend, what your backend needs are, etc. Too many variables to answer properly. I use Linux machines for all my backups just fine. If you are happy with WHS and it works for you, sticking with it sounds dine.

---

### Post by gjsearle74 on 2010-07-12
Thanks for the welcome and the quick reply :p
 
Looking to re-use 3 nova-t-500 DVB-t cards (6 tuners) and a TBS 6890 DVB-s (2 tuners).
 
May look at add another dvb-s card in the future.

---

### Post by newlinux on 2010-07-12
> **gjsearle74 said:**
> Thanks for the welcome and the quick reply :p
 
Looking to re-use 3 nova-t-500 DVB-t cards (6 tuners) and a TBS 6890 DVB-s (2 tuners).
 
May look at add another dvb-s card in the future.

You are welcome.

Depending on how you setup your storage groups and how you distribute your tuners your tuner limit may come from disk speed and network bandwidth (depending on how many jobs are running simultaneously). Just something to think about,

---

### Post by gjsearle74 on 2010-07-12
Got a wired gigabit network running through the house, so hopefully that shouldn't hold me back(?).

Not thought about disk speed :o

If it started to struggle, could i set different tuners to record to different drives?

Anyway; waiting for a 'new' mobo to arrive off ebay, so I should be getting my hands dirty this coming weekend - wish me luck! :)

---

### Post by newlinux on 2010-07-12
> **gjsearle74 said:**
> Got a wired gigabit network running through the house, so hopefully that shouldn't hold me back(?).

Not thought about disk speed :o

If it started to struggle, could i set different tuners to record to different drives?

Anyway; waiting for a 'new' mobo to arrive off ebay, so I should be getting my hands dirty this coming weekend - wish me luck! :)

Yes you can spread the recording load across multiple drives using storage groups (or you could go to a RAID setup). I currently have the capability to write 10 recordings at once and I spread these across various storage groups. Gigabit has great bandwidtch in theory, but sometimes actually speed (especially between any two given nodes) is a lot lower than you'd think. Someone watching a stream from a remote computer while, that remote computer is recording a couple of streams and yet another remote computer is running commercial flagging to that recording machine - it all adds up. 

But most likely networking won't be your problem, or disk, unless things are all happening at the same time - I think you'll be fine.

I've got gigabit going through the house, but I've got my tuners spread across 3 different machines and various storage groups.

---

### Post by gjsearle74 on 2010-07-12
So many possibilities for an ex-windows user; think my brain could be hurting coming installation time! :shock:

With tuners on 3 different machines, is the recorded tv stored locally, or on the main backend?

Apologies if I'm asking all the noobie questions; some of the documentation can be confusing.....:oops:

---

### Post by newlinux on 2010-07-12
> **gjsearle74 said:**
> So many possibilities for an ex-windows user; think my brain could be hurting coming installation time! :shock:

With tuners on 3 different machines, is the recorded tv stored locally, or on the main backend?

Apologies if I'm asking all the noobie questions; some of the documentation can be confusing.....:oops:

My recordings are distributed across 5 different drives across 4 different computers. Most recording is local so not as to take up network bandwidth or be affected by the network. But I also have a central fileserver that has a lot of recordings as well.

---

### Post by laffinet on 2010-07-12
Ideally you want one master backend which has all your tuners connected to it. This would also hold all your recording files. Basically your central server.
All the other computers then become remote frontends.

But that might be too much of a change to your setup.

---

### Post by gjsearle74 on 2010-07-13
> **laffinet said:**
> Ideally you want one master backend which has all your tuners connected to it. 
 
Think thats the way I'll head; I'll let you know how I get on! :D

---

### Post by newlinux on 2010-07-13
> **laffinet said:**
> Ideally you want one master backend which has all your tuners connected to it. This would also hold all your recording files. Basically your central server.
All the other computers then become remote frontends.

But that might be too much of a change to your setup.

Whether or not that is ideal is debatable and depends on your needs. I have multiples backends because:

1. One couldn't hold all my tuners
2. I like to distribute job processing across backends. None of my machines are extremely powerful, so I need multiple to distribute the job processing load (especially commercial flagging).
3. Disk storage. Yes, I could just use storage groups and record across any networked computer's drive, but by mostly recording locally I greatly reduce my network traffic.
4. Redundancy. if one machine fails or is accidentally turned off or simply the backend stops functioning properly, etc. I most likely won't miss any recordings because I have tuners on other machines.

On master backend with all tuners not only isn't ideal for me, it  wouldn't work. I have too many other services and applications on my network to centralize all of them to just one server. All of my backends are also frontends.

---

### Post by laffinet on 2010-07-13
> **newlinux said:**
> Whether or not that is ideal is debatable and depends on your needs

I agree. I shouldn't have made it an absolute statement.

I was looking at it from a system simplicity POV. Handling and organising multiple backends can get rather complicated.

If your one system can handle it storage and processing wise I think it's easier and neater to use the one-backend-server solution.

> 3. Disk storage. Yes, I could just use storage groups and record across any networked computer's drive, but by mostly recording locally I greatly reduce my network traffic

If your backend can handle all the tuners you wouldn't have to deal with storage groups across the network and everything is still local.

But as I said, I agree that it depends on your needs and I don't want to turn this into a "what's best" discussion ;)

---

### Post by newlinux on 2010-07-14
> **laffinet said:**
> ...
If your backend can handle all the tuners you wouldn't have to deal with storage groups across the network and everything is still local.


True, but my point was that if I have storage on multiple machines that I want to utilize for recordings without recording over the network then multiple backends with tuners is the only way to achieve this.

> 
But as I said, I agree that it depends on your needs and I don't want to turn this into a "what's best" discussion ;)
I haven't mentioned any setup as being "best" so I don't think this is turning into a "what's best" discussion :) I simply wanted to inform others there are reasons for different setups. Mythtv is flexible in its setup for this reason.

---

### Post by laffinet on 2010-07-14
> **newlinux said:**
> 
I haven't mentioned any setup as being "best" 

No you didn't, but I sort of did :D

---

### Post by nickrout on 2010-07-16
you guys watch far too much TV!

---

### Post by chipppy on 2010-07-16
Good Evening

I dont have 10 tuners only 4.  I have a hardware RAID setup (gigabyte mobo spec -R) with 10TB of space in my FE/BE box and 2 FE thin clients elsewhere.  
With 3-8 kids when friend over and everyone watching different movies and recording across all 4 tuners not a problem with an intel E8500 CPU and gigabyte net.

I do recommend putting as much tuner and storage in BE as possible so to reduce network traffic.  

Cheers
Chipppy

---

### Post by gjsearle74 on 2010-07-19
Thanks for all the advice guys. Got my backend set up; currently running in parallel with my WMC system to iron out any issues ahead of going 'live' - WAF needs to remain at maximum!

2 dual tuners running, and two frontends configured.

Starting to get my head around storage groups etc...

My biggest sticking point is how I deal with backups/redundancy.....

Do I go with a RAID 5 setup on my backend, or configure a server (have spare hardware) to handle backing-up/archiving of recorded tv/dvd's etc?

Is the server route possible? ie something to replace my WHS for storing tv?

---

### Post by nickrout on 2010-07-19
> **gjsearle74 said:**
> Thanks for all the advice guys. Got my backend set up; currently running in parallel with my WMC system to iron out any issues ahead of going 'live' - WAF needs to remain at maximum!

2 dual tuners running, and two frontends configured.

Starting to get my head around storage groups etc...

My biggest sticking point is how I deal with backups/redundancy.....

Do I go with a RAID 5 setup on my backend, or configure a server (have spare hardware) to handle backing-up/archiving of recorded tv/dvd's etc?

Is the server route possible? ie something to replace my WHS for storing tv?

TV files are very space intensive. If you want to backup you obviously have to double your storage space. Many take the view "it's only TV, I won't bother backing it up."

---

### Post by newlinux on 2010-07-19
I do nightly backups of my important media content (videos, dvds, music, pictures, but not most TV recordings) to my file server, and some of it I even backup offsite (music and pictures). It requires a lot of space (my fileserver has 4.5TB). i don't need extra uptime or speed or real time mirroring, just mostly concerned with recent backups so I don't use. There are lots of backup solutions in Linux (I just use a couple of rsync scripts).

---

### Post by gjsearle74 on 2010-07-22
Ok guys, I think I'm finally getting there for a noob!

2 front ends, looking to add a 3rd. Primary backend and now looking to add an ubuntu server too.

Plan is to boot the frontends from the backend via the network, with no hard drives installed (will handle this at some point in the future).

BE no raid, just sufficient disks as required. Will then backup to the server (probably including recorded tv for now).

The server to have OS on a disk (mirrored in raid 1 - although after reading various posts not sure if this will boot or what problems I have if one drive fails?) and other drives for backup space for the BE.

Then weekly backup my music, ripped dvd's and photos to an external hard drive on the server for added security.

Overkill? Sound do-able? Wanna get this nailed before the full switchover and two fingers to M$ :D

---

### Post by newlinux on 2010-07-22
no such thing as overkill :). It's worth it from a learning experience. Sound doable - I do most of that except the network boots. We're here to help! Just make sure to build in usable steps so that if things don't work you can pinpoint what's not working.

---

### Post by gjsearle74 on 2010-07-22
Cheers mate, and thanks again for all your advice to date.

I'll see how I get on, just wanted to make sure I was headed in the right direction!

I will probably be back for some more advice if/when I start pulling my hair out! :D

---

### Post by nickrout on 2010-07-22
> **gjsearle74 said:**
> Ok guys, I think I'm finally getting there for a noob!

2 front ends, looking to add a 3rd. Primary backend and now looking to add an ubuntu server too.

Plan is to boot the frontends from the backend via the network, with no hard drives installed (will handle this at some point in the future).

BE no raid, just sufficient disks as required. Will then backup to the server (probably including recorded tv for now).

The server to have OS on a disk (mirrored in raid 1 - although after reading various posts not sure if this will boot or what problems I have if one drive fails?) and other drives for backup space for the BE.

Then weekly backup my music, ripped dvd's and photos to an external hard drive on the server for added security.

Overkill? Sound do-able? Wanna get this nailed before the full switchover and two fingers to M$ :D

I think the backup of media is OTT because, well, it's just TV.

You have a backup of the DVD's you have ripped anyway, it's called the original DVDs safe in a cupboard somewhere.

I would devote the doubled requirement for hard drive space to double the multimedia, but that's just me!

Everything there is doable of course. Make sure you do your network backups when you don't want to do too much other network stuff (like watching all that media :))

---

### Post by newlinux on 2010-07-22
I do backup my videos and other media, except recordings (some of it I even backup offsite). Storage is relatively cheap these days. It's more to save me pain of having to re-rip (or in my home video case, recapture in realtime). But I don't backup TV recordings. Some videos are things I transferred from videotape, which degrades.

---

