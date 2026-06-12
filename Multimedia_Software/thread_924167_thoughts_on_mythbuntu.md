---
title: "thoughts on mythbuntu?"
date: 2008-09-19
forum: Multimedia Software
---

### Post by tone33 on 2008-09-19
So I'm looking to setup a media server.  My requirements are:

1) manage pictures
2) manage music (rip cds and playback)
3) manage movies (rip dvds and playback)
4) watch online movies (netflix)

5) Interface to it through
    a) TV - remote
    b) another computer - i.e. connect digikam or Fspot to the picture share, or amarok to the music share


No real need for a PVR right now as I don't have cable, and don't really have any desire to get it.  I'm thinking about using mythbuntu to do this or possibly a debian server install (or maybe another distro??) with MythTV on top for the dvd ripping and TV interface stuff.  Any thoughts?

---

### Post by paulg on 2008-09-19
MythTV, IMO, is not the most suitable application for picture and music management. It is however, one of only a couple applications that I know of that is fully operational by a remote for music management which makes it ideal for the livingroom.

The MythTV [wiki]("http://www.mythtv.org/wiki/index.php/Main_Page") has good descriptions for all supported plugins [here]("http://www.mythtv.org/wiki/index.php/Category:Plugins"). I really recommend looking it over. Most of the plugins require a little additional configuration but generally add a lot of functionality to MythTV.

If you can live with its constraints, MythMusic will allow you to configure your system to rip audio CDs inserted into the system and add them to your [MythMusic] library. It's not that I don't like the way it works, I just find it cumbersome for my largish collection. Actually, looking at the wiki, I think I need to take a second look at this.

It does have what looks like a good plugin for managing ripped DVDs but I haven't tried it. MythDVD Looks like it is intended to be used as a DVD ripper/transcoder but it looks like it might be able to keep menus too.

There's a NetFlix plugin for managing a NetFlix account but it says it will not allow "Watch Now/Instantly" feature. Is that what you're looking for?

As far as I know, and one of the major complaints I have seen about MythMusic is that it is incapable of sharing it's library with another program such as Amarok. There's a few developers who are looking at this. Personally I just use Amarok as my music player and VNC (I run x11vnc server side) to my system to queue up the playlist etc. I've just set up my media mounts as NFS shares to mount them on my other systems and haven't tried sharing an Amarok MySQL database yet but most of my music playing is through my 'server' using Amarok. A sore spot with Digikam is that it will not store the library database on a networked drive (specifically NFS, haven't seen any report of it working with Samba/CIFS either). There is a work around to have it store the pictures on a remote computer but that still won't allow you to share your tags etc which is probably what you'd really want to be able to do.

VNC does work ok for accessing a computer remotely, and most server management can be done through an SSH terminal on another system. The MythTV menus don't always respond when doing that but this is how I'm doing it for now (with a laptop) until I have working remote. Another work around in MythWeb which allows to setup recording schedules from a web interface (along with some other things). A requirement for my setup was no keyboard in the livingroom but somehow a laptop is OK ;) All computers in your home can be setup as a frontend.

PVR functionality doesn't require cable and works just as well with antenna signals. Schedules for antenna viewing are available in most regions around the world as far as I know.

On Mythbuntu vs. Debian I can only comment as a Ubuntu user and a Debian server user. My MythTV installation is on my Debian system. It is rock solid. I mean, when you install new software and configure it properly, it just works. Kernel updates tend to be limited mainly to security updates so you don't need to recompile your binary video drivers from NVidia/ATI often (I think I did it once in the last year?). That said, it lacks many of the things that make an Ubuntu desktop great. Ubuntu has extremely simple restricted driver installation, updates, and all the cutting edge free software you could ever want. In the Debian stable branch (currently Etch) you don't get the latest software, you get stability. So when I setup my server I chose to go with Debian as I need it as a fileserver/backup system first and a multimedia dispenser second. And in that respect it has been wonderful. I used Debian before I started with Ubuntu 5.04 so I'm familiar with it. But the MythTV setup has not been the most intuitive process I've had to follow. Had MythTV been my primary focus when I started, and had Mythbuntu been around at that time, I might have done things differently. I've been chipping away at MythTV for quite a while now and I still don't have everything working the way I'd like it to! But my server functions all work so I'm not about to reinstall when nothing else is broken!

---

### Post by wolfen69 on 2008-09-19
i use [Mythbuntu]("http://www.mythbuntu.org/") and love it. be sure to read the wiki first though.

---

### Post by tone33 on 2008-09-20
Paulg,

Thanks for all the info.  I may just start with Debian, and setup music with Amarok, although i had a hard time with my first stab at Amarok, maybe it's because I'm coming from windows media player, and itunes, and to me Amarok just was not as intuitive (or maybe it just wasn't working for me the way it was supposed to).

Not sure what I'll do about pictures yet - it is disappointing that in digikam tags and edits are local to the user.  I had this same problem with Picasa trying to edit pictures on different user accounts in windows.  I am hoping to find a solution that is flexible enough to do this as my wife may want to edit and tag pictures from her laptop, and I may to edit and tag them from my laptop and we should be able to see each others changes.

One other thing I am looking for is a way to manage home videos - my file/media server will also house these.  Any recommendations for software to manage/edit home videos?

I like the idea of installing mythtv separately because it will force me to learn it.  And your tips on stable distro are good as I am looking for the same thing - just a file/media server and not a desktop system.  I recently went through a Gentoo install, got most everything working, and learned quite a bit about linux for all the time and trouble it took.

---

