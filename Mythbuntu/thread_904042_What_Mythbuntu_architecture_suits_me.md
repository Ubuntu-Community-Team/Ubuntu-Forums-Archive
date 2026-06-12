---
title: "What Mythbuntu architecture suits me?"
date: 2008-08-28
forum: Mythbuntu
---

### Post by Cuban_Eight on 2008-08-28
I've been scratching my head for the last couple of days, after searching the web for Media Center software I've come across Mythbuntu and decided to have a shot at using it in my home.  I'd be interested to get some ideas of what would be the best implementation for me.  I'll start with a rundown of what I have to work with at the moment....

I've installed Cat5 cabling in my home that all runs back to a central point where my adsl modem/switch will sit.  My modem also doubles as a wireless access point.
I have an xbox in our main TV room that we use for watching .avi's, gaming and music.  (our current media center, such as it is)
I have a 'retired' Intel server (S875WP1 mobo, P4 2.8GHz, 512Mb Ram, two 320GB SATA and one 320GB PATA HDD) that I have a mind to use as a backend machine.
I have a couple of other older desktop PC's (P4's) that I can also use as front ends around the house for the kids rumpus room, kitchen etc.
I have no video capture card, or remote control yet.  They are on the buying list for now.
I am in Australia too, if that means anything other that PAL!

What I want to do, is primarily have a single repository of our media (video, pics and music) that can be accessed throughout the house.  Other features, like recording TV etc would be a bonus.  Currently our media files are spread between the Xbox, desktop PC's and USB drives.  So I'm obviously looking at a backend/multiple frontend type architecture.  My main concerns are redundancy and compatibility I suppose.
Can I use our xbox as a front end with a Mythbuntu backend?
My server motherboard has hardware RAID, can I use this with Mythbuntu, or can I install an OS that will support RAID and then put MythTV on top?
If RAID is out of the question what other options are there to save my files in case of a disk failure?
I have no TV aerial outlet where I plan to place the backend, can a frontend PC with video capture card record to the backend server?
Any suggestions for which capture card and remote I should be looking for?

Thanks in advance for any tips folks.

---

### Post by jlp_engineer on 2008-08-29
> **Cuban_Eight said:**
> I've been scratching my head for the last couple of days, after searching the web for Media Center software I've come across Mythbuntu and decided to have a shot at using it in my home.  I'd be interested to get some ideas of what would be the best implementation for me.  I'll start with a rundown of what I have to work with at the moment....

I've installed Cat5 cabling in my home that all runs back to a central point where my adsl modem/switch will sit.  My modem also doubles as a wireless access point.
I have an xbox in our main TV room that we use for watching .avi's, gaming and music.  (our current media center, such as it is)
I have a 'retired' Intel server (S875WP1 mobo, P4 2.8GHz, 512Mb Ram, two 320GB SATA and one 320GB PATA HDD) that I have a mind to use as a backend machine.
I have a couple of other older desktop PC's (P4's) that I can also use as front ends around the house for the kids rumpus room, kitchen etc.
I have no video capture card, or remote control yet.  They are on the buying list for now.
I am in Australia too, if that means anything other that PAL!

What I want to do, is primarily have a single repository of our media (video, pics and music) that can be accessed throughout the house.  Other features, like recording TV etc would be a bonus.  Currently our media files are spread between the Xbox, desktop PC's and USB drives.  So I'm obviously looking at a backend/multiple frontend type architecture.  My main concerns are redundancy and compatibility I suppose.
Can I use our xbox as a front end with a Mythbuntu backend?
My server motherboard has hardware RAID, can I use this with Mythbuntu, or can I install an OS that will support RAID and then put MythTV on top?
If RAID is out of the question what other options are there to save my files in case of a disk failure?
I have no TV aerial outlet where I plan to place the backend, can a frontend PC with video capture card record to the backend server?
Any suggestions for which capture card and remote I should be looking for?

Thanks in advance for any tips folks.

I can't help you with the Xbox, but any of your systems, since they are a few years old, should be fine with the latest version of Mythbuntu.  Also, I believe that your RAID arrangement, as long as it is NOT a RAID function built into the MB chipset, should also work fine, as the latest Linux kernels support most RAID controllers made over the last several years.  

Lastly, your back-end is where all your tuners will be, so I would recommend that you route your antenna cable to this location, or relocate your back-end server to another location.

Good luck :)

---

### Post by tgm4883 on 2008-08-29
To clarify

Install a backend/frontend combo where your computer with the TV card will be.  If your desire is to record to the other computer, then mount an NFS share and record over the network.

And your xbox can be used as a frontend, XBMC has built in MythTV support

---

### Post by ian dobson on 2008-08-29
Hi,

1) I woud recommend running linux sotware RAID rather than the motherboard fake raid. You just need to setup the BIOS for "normal" harddrives then under linux use mdadm to create a RAID array. I'm currently running a 3Tb (3x1Tb samsung) RAID5 array and am very happy with the performance/stability.
Using mdadm has the advantage of not being motherboard specific,if your motherboard dies you can just replace it with any board that has enough connectors.

2) Findout what your cable company supplies as a signal, it could be DVB-c,Analoge or maybe ATSC as that you can then decide what tuner cards you'll need. I'm running 2 DVB-C and 2 Analog cards in my server as my cable company supplies most of the channels I want over DVB-c but not all. I've run a 30-35meter long cable from the cable inlet to my server and the picture quality is perfect.

3) If possible run an antenna cable to the server, you could use a combined frontend/backend with the tuners installed in the frontend but I wouldn't recommend it. I ran the system like that and everytime mythTV decided it wanted to record something it started the frontend PC through WOL and my wife got a shock (why does this thing keep on switching itself on/off).

4) Make sure you have enough tuners in the server to cover all the possible combinations of programs that you want to record. If you have DVB (c,s,t) you can record multiple programs at the same time from one tuner if they're on the same multiplex. With analoge you can only record one program at a time. I have configured my DVB-c tuners so that they can record 2 programs at the same time, so that if I have 2 back to back recordings I never miss the beginning/end of a program (I record 5 minutes extra at the beginning/end of every program).

The most important advice I have is take your time, think about what you want to achieve and involve the rest of the family in deciding how the system should work. I installed my mythtv system in december of last year and it took me about a month of working on/off on the system until it worked as I wanted.

Regards
Ian Dobson

---

### Post by Cuban_Eight on 2008-08-29
Thanks for the replies guys, its certainly given be something to think about...

I might have a fiddle with the software RAID, the box I have is certainly big enough to stuff some more drives into.  They would be a combo of SATA and IDE though. I've spent the day messing around with formatting and mounting drives as it is.  This is all new to me, I've been sys admin in a Windows Domain for several years now and finally trying my hand at this black art they call 'open source'!  Its taken me 8 hours to sort out how to format in ext3 and xfs, mount / , a swap and three storage drives, and then create some directories that I can write to!!
I have an older box at home here that I will put Mythbuntu on to fiddle with over the weekend for some testing (and much learning) and get a better idea of how it works.  I don't have a tuner card yet so will do some googling on them.  Cable is not a worry as I live in country South Australia and its not available out here in the sticks.  We do have free to air digital though and sattelite tv is available although I'm not a subscriber.

I think I will be taking my time!  Mainly because I'm a slow learner!!:)

---

### Post by ian dobson on 2008-08-29
Hi,

This might be a good source of info for you:- [http://www.overclockers.com.au/wiki/MythTV](http://www.overclockers.com.au/wiki/MythTV)

Regards
Ian Dobson

---

### Post by Cuban_Eight on 2008-08-29
Thanks Ian,  

thats a great link!  The info on what tuner cards will work here is excellent, just what I was after.

---

### Post by anonymousdog on 2008-08-29
I'd go for hardware RAID if your RAID card actually offloads to RAID logic from the driver (i.e., only if it's a real RAID card where the RAID functionality isn't built into the Windows driver [which so many SATA "RAID" controllers are :-( ]).  If it's a real RAID controller, that will always be faster and more easily recoverable than Linux RAID.

---

### Post by Lindsay.Mathieson on 2008-08-30
Hi Cuban, quite a few Aussie users here, I'm from Brisbane myself so you should be able to get lots of help for Aussie specific stuff.

Experimenting with a older box is an excellent way to start, ubuntu/myth is a complex beast, but logical and tweaking/breaking it is a good way to learn how it works. Don't be afraid to reinstall from scratch many times :) I probably spent a good year fiddling with myth and other systems before setting up our combined front/back end but its gone really smoothly.

Digital is definitely the way to go if you can receive it. Eventually you're going to need a online EPG for your mythbox, I throughly recommend   [shepherd]("http://svn.whuffy.com/wiki") as a guide data source, its comprehensive and makes setting channel logos easy.

---

### Post by ronferds on 2008-08-30
buddy am new here, how do i post a new thread?

---

### Post by Lindsay.Mathieson on 2008-08-30
"New Thread" button from the main forum.

---

### Post by Cuban_Eight on 2008-09-10
Okay, I've setup my server with mdadm software raid using four 320GB drives (2 PATA and 2 SATA) and a fifth 40GB drive in the machine is running MythTV as a backend.

I've bought a Leadtek DTV-2000H tuner card, which also comes with a remote control.  The only catch is the remote control will have to be in the loungeroom for me to use it, which puts the tuner card in the same place. (the aerial socket is there too of course!) So this is all very convenient apart from the fact I don't want this hideously large server box with the raid drives in my loungeroom too.  So I'm thinking of using the server as a second backend, for storing music and video's, and another PC in the lounge as a front/backend that will record TV locally but rip music and video files to the bigarse backend.
Is this doable easily?

Can I use Wake on LAN for the raid backend so I'ts not acting as central heating in my spare room fulltime?

Is it possible to put another frontend in the kids room, which can then access TV from the loungeroom PC as well as the stored music and video's?

---

