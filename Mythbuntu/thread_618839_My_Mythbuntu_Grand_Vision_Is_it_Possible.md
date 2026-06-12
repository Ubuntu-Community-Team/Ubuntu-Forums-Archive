---
title: "My Mythbuntu Grand Vision: Is it Possible?"
date: 2007-11-20
forum: Mythbuntu
---

### Post by clove on 2007-11-20
I would like to put together an always-on machine to handle various multimedia and file server tasks for my house.  Mythbuntu's looking like a good candidate (other Linux-based alternative suggestions welcome).

I've read quite a bit about what Mythbuntu can do and I realize that some items on my list may be answered elsewhere, but part of what I'm looking for here is how these things perform in real life.  I have an existing Vista-based network/media center which looked good on paper but turned out to be a complete catastrophe in real life, so I just want to dismantle it and get things right this time.

Any feedback on suggestions/ impossibilities/ real-world-experience is appreciated.  Here's what I would like to accomplish:

1) Feed 2 HDTV TV signals (cable and/or on air) into a pair of tuner cards and have complete PVR capabilities on several diskless frontend machines (this should be straightforward enough).

2) Store a library of video files of different types/codecs on the backend server and be able to browse through them and watch them on the frontend machines.

3) Store my entire music collection on the backend and be able to come home and easily select an album to play on a frontend machine without spending 10 minutes to get it going.

4) Stuff the backend server full of hard drives and be able to access all my files remotely from other Linux and Windows machines in the house.  This includes working on documents, editing photos, etc directly over the network so all files are kept in one place.

5) Keep all my documents encrypted on the server, probably by designating one hard drive as a Truecrypt (or equivalent) encrypted volume, so I'll be safe if the machine is ever stolen.  Any files I'm working on from a different machine would be decrypted on the fly.

6) Run an always-on bittorrent client on the backend that can be remotely controlled by other (Ubuntu) machines on the network so I can keep all my bittorrent activity in one place.

7) Remotely access the server from a pocket pc device or other remote computer to schedule tv recordings, view connected webcams, etc.

So there's my wish list.  I got most of this functionality set up on Vista-based machines early this year, but like I said, what looked good on paper turned out to be a complete train wreck in reality and is just making life miserable.  Thanks in advance for any feedback.

---

### Post by ubnewbie2 on 2007-11-20
1,2,3 are in Mythtv

4 is easy via NFS and Samba shares

5 I have no knowledge of, sorry

6 seems possible, just install bit torrent client on the server,  "remote-control" might be via VNC

7  -remote scheduling is part of myth - via mythweb - (don't know about webcams though)

---

### Post by newlinux on 2007-11-20
5 don't know either, 6 is possible a number of ways, vnc, nxclient, or just setup a torrent client that also has a web interface (I do this with ktorrent).

7. Mythweb is good for this as mentioned, and you can stream a webcam video through many different streaming protocols.

This will not start off seemless, and probably will take a lot of configuration. Aside from 5 and webcams, I do all of these things (I've got 7 tuners though - they serve the whole house and we record a lot). What were the problems with Vista? Maybe we can help you  avoid those problems with myth.

Since myth has a UPnP server I even added in some non myth "frontends" to stream to.

---

### Post by tonyr1988 on 2007-11-20
Just to throw a little in, for #6, several torrent clients have built-in web interfaces. Azureus and Deluge do, and I believe KTorrent does as well.

Or, you can set up a remote desktop. A web interface will probably be easiest, though.

---

### Post by shad0w_walker on 2007-11-20
Number 6 would probably best be done with torrentflux.

---

### Post by clove on 2007-11-20
Thanks to everyone for all the quick responses.

> This will not start off seemless, and probably will take a lot of configuration....What were the problems with Vista? Maybe we can help you avoid those problems with myth.

Ok, I'll try my best to be brief:

I don't expect a seamless setup with Mythbuntu, but Vista was a really rough road.  Ater 6 solid weeks of troubleshooting using various forums (for the Media Center portion) some of the remaining issues/annoyances that I just can't solve include:

1) Sleep issues.  The system is supposed to go into S3 sleep mode and resume to record programs.  There are really too many issues with this to list, but with Mythbuntu I know I need to leave the system on 24/7 so I won't worry about this.

2) Media extender issues: I bought Xbox 360s to use as extenders (the only option).  Aside from $$$, they don't play any video codecs except wmv files without server-side transcoding which puts a huge load on the server's processor and is not a smooth process (choppy video).  I had to get in the habit of converting all videos to wmv format which takes a ton of time.  There are plenty of other issues with the extenders including that they fail to wake the server like they're supposed to, they can be very sluggish at times, they constantly disconnect from the server, and they often crash the server which requires a server reboot.  BTW my whole house is cat 5 wired so this is a software issue.

3) Sluggish performance--even with 2G of RAM in the server, the TV often stutters and the hard drive light is lit solid for minutes sometimes with constant swapfile and disk maintenance activities--just a bloated OS I guess.

4) Plug-in crashes--I use two plugins--one to watch online media and the 2nd to load/manage dvd content which has been loaded onto the server.  Both crash the system constantly.

5) Approx 1 in 5 recorded programs plays back with completely distorted audio.

6) General sluggishness/usability issues.  I'm using fast machines here, but everything is just slow.  It's embarrassing to have people over who have to witness me struggle through the laborious task of just turning on a football game.

7) The rest of Vista.  The above are just Media Center-related.  I would have to write a book to cover the problems I've had with Vista in general as an OS--it's just not ready for prime time.  It's really the reason that drove me to discover Ubuntu in the first place.

---

### Post by uopjohnson on 2007-11-21
You can solve the encrypted documents issues with ubuntu as well.  Just look around the ubuntu wiki and search the other forums.  All you need to do is create an encrypted volume that is mounted with a password.  You can have it mounted all the time and you will just need the password when you reboot.  You can't do anything more automatic because that takes away the security of encryption.  You can then share that mount over smb or nfs as you would any normal file sytem.  The best part it you can do this all easily with ubuntu and the standard repos.

---

### Post by dougsnell on 2007-11-21
> **clove said:**
> 
3) Sluggish performance--even with 2G of RAM in the server, the TV often stutters and the hard drive light is lit solid for minutes sometimes with constant swapfile and disk maintenance activities--just a bloated OS I guess.

...

6) General sluggishness/usability issues.  I'm using fast machines here, but everything is just slow.  It's embarrassing to have people over who have to witness me struggle through the laborious task of just turning on a football game.

7) The rest of Vista.  The above are just Media Center-related.  I would have to write a book to cover the problems I've had with Vista in general as an OS--it's just not ready for prime time.  It's really the reason that drove me to discover Ubuntu in the first place.

Vista has a lot of those problems, and you can overcome some of them to some extent if you *really* know what you're doing (turn off indexing service, turn off UAC, turn off most of the graphical stuff, hard-coding your paging file, and so forth).  In all, it's still going to be slower than XP.  XPMCE would probably be better than Vista.

At the same time, you could be bumping into a bus/device limitation.  With everything you have going on, I'm not surprised in the least your drives were on solid for mintues at a time.  If that's the case, changing the OS will only help at a minimal amount.  If you don't have one, look into a hardware RAID controller (I'm hoping you have SATA drives ... if not, I'd be foolish not to recommend them).  RAID 5 would be cheaper, but RAID 0+1 would be better (striped for performance, mirrored for reliability).

I'd also suggest off-loading the BitTorrent stuff onto another machine entirely.  Store the finished files on your myth back-ends if you want (particularly for security/consistency), but unless you've fine-tuned that control, it's also hammering your subsystems unneccessarily.  Lots of small disk writes create a lot of chatter.

---

### Post by clove on 2007-11-21
Thanks everyone for all the great feedback and advice so far.  Just to test things out, I installed Mythbuntu on an old Pentium 4 box I had laying around.  In only one hour, I had it up and running and got to play with a lot of the features.  I'm very impressed.  I fired up my Ubuntu laptop, the Mythbuntu share folders showed up under the network, and I copied some music over.  So simple!! And the speed that I can browse through and play music blows the doors off Vista.  Everything's lightning fast so far (and this is on a 6 year-old machine).

No TV yet--I will have to go buy a new tuner card this weekend because my Hauppauge 1600 cards aren't (yet) supported.

I have a feeling this new setup will work out very nicely.

---

### Post by pasta514 on 2007-11-25
LinuxMCE perhaps?  Seems like a bit of parallel thinking...

---

### Post by kameleon25 on 2007-11-26
For your #6 I would reccomend rtorrent. I use it on my server and it is awesome. Small footprint, has all the capabilities of the big GUI ones like throttle up/down, seed for certain time or to a certain ratio, automatic download, etc. I just have a directory nfs mounted to my other machines and when I see something I like I will download the torrent and save it to that directory. rtorrent sees it and starts downloading. I just run it with screen. so it would be like:

#screen rtorrent

Then just resume from wherever you want to check. 

Also may I suggest hellanzb for your newsgroup needs. Awesome also. Basically the rtorrent equivalent for newsgroups.

---

