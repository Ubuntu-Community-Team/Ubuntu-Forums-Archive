---
title: "Multimedia Network Setup Recommendations"
date: 2010-04-17
forum: Multimedia Software
---

### Post by ncwilde43 on 2010-04-17
This thread may be a little more generic, but I was wondering if I can get some recommendations on which equipment and setup I should use for my future home multimedia network.

I've listed what I think I want/need, the requirements for each.

[SIZE="4"]Please comment on the following:[/SIZE]
[LIST]
[*]Which type of equipment do you prefer for each task
[*]Which software do you prefer for task
[*]Would have a different piece of equipment do the job
[*]Would you combine some of the equipment
[*]My first step is to purchase storage to centralize and organize all media content.  Which equipment/software would you recommend?
[/LIST]
[SIZE="4"]Functional Requirements:[/SIZE]
[LIST][SIZE="3"]Multimedia[/SIZE]
[INDENT][*]Hot swappable drives
[*]Stream movies/music/pictures to all machines/consoles
[*]Store all media on network storage rather than local machines.
[*]Support for both Windows & Linux
[*]Rip/Backup all digital content (CDs/DVD's/Blu-Ray)[/INDENT]
[*][SIZE="3"]Home Theater[/SIZE]
[INDENT][*]Play Netflix/Hulu/Backed up content
[*]DVR support for at least 2 tuners
[*]All TV's can play all DVR content.
[*]Blu-Ray playback
[*]Music stereo
[*]Gaming[/INDENT]
[*][SIZE="3"]Server[/SIZE]
[INDENT][*]FTP/SFTP support 
[*]VPN
[*]Webserver
[*]Virtual Machine Host
[*]BOINC[/INDENT]
[/LIST]

[SIZE="4"]Equipment I currently have:[/SIZE]
[LIST]
[*]Toshiba Qosmio Multimedia Laptop with Ubuntu Lucid (mine)
[*]Dell Inspiron 1420 with Windows Vista (wife's)
[*]Old P4 Dell with Ubuntu Server Karmic
[*]Linksys WRT54GS (b/g) with DD-WRT
[*]Standard definition telivision
[/LIST]

[SIZE="4"]Equipment I think I need:[/SIZE]
[LIST]
[*][SIZE="3"]HTPC set top box for TV front end[/SIZE]
[INDENT][*][Boxee]("http://www.boxee.tv/")/[XBMC]("http://xbmc.org/")
[*]OS: [Mythbuntu]("http://www.mythbuntu.org/")/[Ubuntu Netbook Remix]("http://www.canonical.com/projects/ubuntu/unr")
[*]Blu-Ray Drive
[*]HDMI Support
[*]DVR control and playback
[*]Music playback
[*]PC Gaming
[/INDENT]
[SIZE="3"]Server box with Ubuntu Server Karmic[/SIZE]
[INDENT][*]Webhosting with [Apache]("http://www.apache.org/")
[*]SSH & SFTP with [OpenSSH]("http://www.openssh.com/")
[*]VPN with [OpenVPN]("http://openvpn.net/")
[*]Admin with [Webmin]("http://www.webmin.com/")
[*]iTunes streaming (for wife's PC) with [Firefly]("http://www.fireflymediaserver.org/")
[*]Content streaming via NFS/SAMBA/UPnP
[*]Ripping and encoding digital media (CDs/Blu-Ray/DVD)
[*]Recording and encoding TV shows[/INDENT]
[SIZE="3"]NAS/Media Storage[/SIZE]
[INDENT][*]Hot swappable
[*]Expandable
[*]eSATA
[*]2TB storage[/INDENT]
[*][SIZE="3"]Laptop with Windows 7 (wife's future computer][/SIZE]

[*][SIZE="3"]Netbook with ChromeOS || Arch Linux || UNR || Jolicloud (my future computer)[/SIZE]
[INDENT][*]Internet browsing
[*]Network administration
[*]Media browsing[/INDENT]
[*][SIZE="3"]n-Gigabit Router with [DD-WRT]("http://www.dd-wrt.com/")(future router)[/SIZE]
[/LIST]

[SIZE="4"]My questions to you all:[/SIZE]
[LIST]
[*]Should I use an NAS for SAMBA/NFS/UPnP attached to the network rather than a hot-swappable storage attached to the server?
[*]Should I combine both the NAS and server together?
[*]Should I combine the server, NAS and HTPC?
[*]Should I have the server or the HTPC do the TV/Blu-Ray recording/encoding?
[*]Should I use any ready made equipment/software ([Popcorn Hour]("www.popcornhour.com/"), [Slingbox]("http://www.slingbox.com/"), [Drobo]("www.drobo.com/"), [WHS]("http://www.microsoft.com/windows/products/winfamily/windowshomeserver/default.mspx"),[ Apple TV]("http://www.apple.com/appletv/"), [HP MediaSmart]("http://www.hp.com/united-states/campaigns/mediasmart-server/"), etc.)
[*]Should I strictly use custom made equipment?
[*]Should I use the receiver to collect all HD content (from the HTPC, gaming consoles, other media players) and then route the content to the TV via HDMI?
[/LIST]

[SIZE="4"]Notes:[/SIZE]
[LIST]
[*]I'd rather stick with Linux (because it's free and awesome!)
[*]My wife and I really like DishNetwork's DVR layout
[*]I'd like to have a seamless transition between live TV, DVR content, Hulu, Netflix, etc.
[/LIST]

Any comments and/or recommendations would be greatly appreciated!

[CENTER][IMG]http://docs.google.com/drawings/pub?id=1OHUqoz4WtZmrnAMN_vL1FiDEHTdHNCE5tPxwH9MxfUo&w=480&h=360[/IMG][/CENTER]
*Image made with [Google Docs Drawings]("http://googledocs.blogspot.com/2009/03/drawing-on-your-creativity-in-docs.html")

---

### Post by perspectoff on 2010-06-04
Yes, use some sort of NAS. I've used the Buffalo LinkStation for a few years, but Maxtor, Seagate, and IoMega now make similar network hard drives as well. A 500Gb drive is about $130.

Of course, if you're serious, a true NAS with hot-pluggable hard drives is a great investment. Synology, Netgear, and others have nice ones. (That will run you about $500-600 including hard drives, though.) It's amazing how fast you can fill up a hard drive (even 1 Tb) with videos, so having the expandability options of a true NAS is valuable in the long run. Also, if you want to use RAID, it's pretty important.

The network storage can be left on all the time and anyone on your LAN can access it (no matter what type of computer or OS they are using). If you use the HTPC box for the storage, you would have to leave it on all the time, and that's not so great (because it generates heat that will be transmitted to all your other multimedia components, especially if they are all stored in a cabinet). A separate network-attached storage unit can be placed anywhere on the LAN.

The network storage is the most important part of any multimedia system.

---

### Post by perspectoff on 2010-06-04
I have Vista and Windows 7 Media Edition and I never use them. Likewise, I've tried XBMC, Mythbuntu, Boxee, and LinuxMCE over the past 2-3 years and they are all wastes of time, in my opinion.

I used Myth TV as a standalone, but the only thing I really liked about it was the built in Torrent downloader. Unfortunately, using it while  watching content clogged up my network.

Now I merely download torrents at night (using KTorrent, utorrent, or other standard torrent client) onto my NAS and then watch them directly from the NAS the next day.

I watch almost all content (in both Linux and Windows) using VLC, including commercial videos (after installing libdvdcss2). It plays Flash and just about every conceivable codec. I access all online content (such as Hulu) through Firefox, playing it with Firefox plugins or externally with VLC (after setting file associations).

By placing a Firefox shortcut to Hulu on the desktop, I have instant access. Why get a standalone media center to watch Hulu or any other content when it is already playable through Firefox and VLC? Heck, I watched the Olympics (using the Moonlight 2.99 plugin for Firefox) this way.

Netflix hasn't released their DRM modules on CD for Linux, yet, so I still watch Netflix through the Wii (or through a Windows virtual appliance when traveling).

My equipment is an inexpensive slim-line standard PC (why bother with an underpowered netbook?) with an HDMI output. This is connected directly to my HDMI TV and amplifier (which powers my 12 channel whole-house audio). I play my commercial DVDs using the DVD drive of the PC (can't do that with a netbook unless you add on a separate DVD drive). I have a wireless mouse /pointer and keyboard (although I mostly only use the mouse /pointer).

(My kids love the Wii controller, so I also tweaked the system to use the Wii controller, but this took a little fiddling.)

To access video on the network storage, I merely use the Dolphin file manager (I use Kubuntu), or Nautilus in Ubuntu.

That's it. 

No need for fancy Media-Center editions with distracting bells and whistles. Keep it simple. You have to decide if the content is more important to you or whether playing around with the interface is your idea of enjoyment.

---

### Post by garfonzo on 2010-06-07
I would agree 100% with perspectoff. I have a server in my garage with 2.4TB of storage. It is full of music, movies, and pictures. I have 5 computers - Vista, 3 XP, and a Mac - all of which access the shared network storage. Now, it isn't a NAS, but Ubuntu Server has Samaba sharing the data to everyone simultaneously. 

I also tried using XBMC with the computer that is attached to my HD movie projector. That was a waste of time (in my opinion). After about 2 or 3 movies, I went back to the old way - watching *everything* via VLC player. Every movie or TV show on the server is played via VLC. All computers have MediaMonkey installed and they all share the same database. Thus, I create a playist on my main Vista computer, walk over to the computer hooked up to my stereo, and it's there too. 

The fanciness of XBMC or similar systems is beautiful. However, it requires more juice from each computer and is, in my eyes, not worth the hastle. Some people love those types of setups and all the power to them. But for me, it seems a little inefficient. 

Just my thoughts.

---

### Post by ncwilde43 on 2010-06-07
> **garfonzo said:**
>  Now, it isn't a NAS, but Ubuntu Server has Samaba sharing the data to everyone simultaneously.
I was thinking about setting up my own NAS or RAID Ubuntu Server of my own instead of buying one off the shelf (wife didn't like the price), but I'm afraid of spending some $ and not having it work like I want.  Is your Server setup in RAID, and if so, are the drives hot-swappable?

> **garfonzo said:**
> I also tried using XBMC with the computer that is attached to my HD movie projector. That was a waste of time (in my opinion). After about 2 or 3 movies, I went back to the old way - watching *everything* via VLC player.
May I ask, what was bad about XBMC that made you go back?  I want the interface to be as streamline as possible as to not confuse the wife (and others).  I want it more like a DVR setup using a remote, instead of a keyboard and mouse.  I also like the fact that XBMC hides TV episodes that have already been watched! ;-)

---

### Post by ncwilde43 on 2010-06-07
> **perspectoff said:**
>  If you use the HTPC box for the storage, you would have to leave it on all the time, and that's not so great (because it generates heat that will be transmitted to all your other multimedia components, especially if they are all stored in a cabinet).
Good point.

---

### Post by garfonzo on 2010-06-07
> **ncwilde43 said:**
> I was thinking about setting up my own NAS or RAID Ubuntu Server of my own instead of buying one off the shelf (wife didn't like the price), but I'm afraid of spending some $ and not having it work like I want.  Is your Server setup in RAID, and if so, are the drives hot-swappable?


I contemplated a RAID setup, but shyed away from it for two reasons. 1) I wasn't comfortable enough with how RAIDs work to really dive into that setup. I figured that if, in the future, something went awry (which will happen) I wanted a setup that was easy to fix based on my knowledge to date. I didn't want to learn a whole new system.
2) I had some people tell me it wasn't a great setup. See, I was looking for a backup system and was looking into RAID for that reason. People kept saying "RAID is not a backup solution". This is true. RAID is good for increasing your read speeds. However, I am not concerned with hard drive read speeds as that is not the bottle-neck of my network. 

My setup includes three hard drive inside the server tower connected via SATA or IDE. I then have three external drives of identical size which are mirrors of the three internals. Now, I'm not sure your goals and why you want hot swappable, but I have it so that every wednesday, a cron job executes a script that calls rsync to mirror the three data discs to the three external drives. So, if an internal drive fails, I can move the mirrored external to be internal with very little down time. There is no worry about uncompressing backup copies because it is a true mirror. 


> **ncwilde43 said:**
> May I ask, what was bad about XBMC that made you go back?  I want the interface to be as streamline as possible as to not confuse the wife (and others).  I want it more like a DVR setup using a remote, instead of a keyboard and mouse.  I also like the fact that XBMC hides TV episodes that have already been watched! ;-)

It's funny, because the reasons for why you want it as streamlined as possible is the same reason I left XMBC. I found that the interface of XBMC was something that I could (and would) learn, but for others in my house it was too foreign. It was far simpler for them to open Explorer, navigate to the mounted network drive (the server's hard drives) go to the "Movie" or "TV Shows" folder and double click on what they want to watch. 

The trick for me is to make the recording of TV Shows automated so that the end users (my wife) can find the files easily. When all the TV shows (which, by the way, are recorded on my Vista media center, converted, and sent to the server automatically) reside on the server, on a specific drive, in a folder called "TV Shows". My wife knows that that is where she can go to find her shows. Easy as pie. 

I loved the 'slickness' of XBMC. You can have Movie posters flash on the screen as you scroll through, have IMDB info instantly shown, movie ratings, cast listings, and a whole host of other stuff shown. It really is amazing. However, at the end of the day (literally) my wife and I just want to watch a movie together and the quickest way to do that is through VLC.

---

### Post by garfonzo on 2010-06-07
> **ncwilde43 said:**
> Good point.

For the computer that is hooked up to my projecter (Win XP) I put it to sleep when not in use. Thus, save power, is silent, and doesn't generate heat. With the hit of the mouse button it is instantly on. The server in the garage, however, is on 24/7. It is loud and generates heat (I have lots of fans blowing air all over the place). But who cares? It's in the garage.

---

### Post by ncwilde43 on 2010-06-07
garfonzo, thank you for the prompt reply.  I love the Ubuntu community!

---

### Post by garfonzo on 2010-06-07
> **ncwilde43 said:**
> garfonzo, thank you for the prompt reply.  I love the Ubuntu community!

:-)

You're quite welcome! This community is the main reason I chose Ubuntu over some other distribution. 

Let me know how things work out with your setup. I'm always playing/tweaking with my home multimedia setup so if you need help, don't hesitate to PM me. 

Cheers!

---

### Post by charcaroth on 2010-08-27
I'd like to add a +1 to what others have said here:  a simpler setup works best.  I have an old 2 ghz Athlon XP desktop with 2 gb PC3200 that I use as an HTPC controlled remotely with a Logitech diNovo Mini bluetooth keyboard/mouse combo or the Android Boxee remote app.  I've got a QNAP NAS with a RAID 1 array with my media connected through a wired network.  I find that I generally either browse a Samba share through VLC to play video and music files directly from the NAS, or I use Boxee to play the files, stream from Hulu and Pandora, etc.  After looking into several set-top boxes and finding that Popcorn Hour seemed to be the best available solution, when I set up the solution in mid-2009.  Due to cost considerations, I tried out MythTV, Linux MCE, and XMBC.  Eventually I figured I could use an Ubuntu desktop (originally at 9.04, now at 10.04) to do more or less the same thing easier and for free.  With the addition of the Boxee application and the Logitech diNovo mini keyboard/mouse, it's every bit as functional as a set-top box.

---

### Post by ncwilde43 on 2010-08-27
@[charcaroth]("http://ubuntuforums.org/member.php?u=303473"), thanks for you reply.  It's nice to get some feedback from those who've already gone through the process.  

Do you have a spouse/children who regularly use the setup?  And if so, do they complain about having to navigate?

---

### Post by charcaroth on 2010-08-30
>>
>>Do you have a spouse/children who regularly use the setup? And if so, do they complain about having to navigate?
>>

My wife generally uses her all-in-one Asus EeeTop PC (running XP and Ubuntu netbook edition) in the kitchen when she's cooking or checking email and Facebook.  She uses VLC (and occasionally Boxee) to play music from the NAS and has a good rudimentary knowledge of how to navigate.  She doesn't complain about that, but I find that she'll use Pandora more often than our own music due to the fact that it's quicker to get music playing and its ability to randomize from channel to channel.  I've showed her how to make playlists in VLC (and even drag shortcuts to them out to the desktop) but she tends to either browse around to find what she wants (if she takes the time) or just to start up Pandora.  

In the living room at the HTPC, I generally play files due to her impatience with using the touchpad on the DiNovo Mini.  The sensitivity has to be cut up pretty high to navigate on the HDTV and she doesn't like touchpads very much in any case.  I haven't known her to use the HTPC when I'm not home to navigate it for her.  She'll watch something off the DVR instead.  I tried transitioning from the DVR with a TV tuner to get cable working through MythTV, but got I increasingly impatient setting it up with my Plextor ConvertX (and didn't want to spend the money for a Silicon Dust unit that I wasn't sure I'd use) and so gave up on it.

---

