---
title: "Can I share recorded tv files with a Windows machine and a media MVP?"
date: 2008-01-28
forum: Mythbuntu
---

### Post by Proost on 2008-01-28
Hello all-

First off, I would liekto apologize for my complete newbie status on Linux. I am planning my first MythTV box and I plan on using Mythbuntu. What I would like to do is record SDTV on my MythTV box and access/watch these recordings on my Windows machine and my Hauppaugge Media MVP. 

Is this possible? If so, how do I set that up during the install of Mythbuntu?

Thanks in advance!

---

### Post by ubnewbie2 on 2008-01-28
You can stream any recorded myth program, using the mythweb interface.  You could also use samba to share the hard drive and play the files under Windows.  To do this

[http://dsmyth.sourceforge.net/](http://dsmyth.sourceforge.net/)

might be useful

---

### Post by Proost on 2008-01-28
Thanks ubnewbie- That would work on my Windows PC.

What I was hoping to do was simply share the drive that MythTV records. Hoping that the Hauppaugge MediaMVP and the windowspc could simply play the files that the Haupaugge PVR150's have created. 

Is this possible?

---

### Post by ubnewbie2 on 2008-01-28
> **Proost said:**
> Thanks ubnewbie- That would work on my Windows PC.

What I was hoping to do was simply share the drive that MythTV records. Hoping that the Hauppaugge MediaMVP and the windowspc could simply play the files that the Haupaugge PVR150's have created. 

Is this possible?


Yes, as I said, you can share the drive using Samba.  It will then look like a Window's shared drive, and any device that can access a Window's share can use it.

One downside, is that the filenames are "coded" with the channel number and time/date.  They are not named with the program title.

I remember there was a utility called myth-pretty or something, that created a directory of symlinks to these files, using human preferred names.  Haven't looked into it for a while.  Knopmyth used to have it running by default, maybe mythbuntu does too?

---

### Post by superm1 on 2008-01-29
I'll chime in with this:
[http://www.mythtv.org/wiki/index.php/Windows_Watching_Recordings_in_Windows_with_MythTv_Player](http://www.mythtv.org/wiki/index.php/Windows_Watching_Recordings_in_Windows_with_MythTv_Player)
My roomate used it and had great luck

---

### Post by stdPikachu on 2008-01-29
> **ubnewbie2 said:**
> Yes, as I said, you can share the drive using Samba.  It will then look like a Window's shared drive, and any device that can access a Window's share can use it.

One downside, is that the filenames are "coded" with the channel number and time/date.  They are not named with the program title.

I'd also go the Samba route.

As for getting the files the right name, there's a FUSE project called MythTVFS which gives a "Program Name - Subtitle" view of your tvstore directory. If you shared this one out via samba it'd be much easier to navigate. You'd have to install the MythTVFS FUSE module yourself mind.

Whoops, no. Looks like there's already a package for Gutsy [http://packages.ubuntu.com/gutsy/utils/mythtvfs](http://packages.ubuntu.com/gutsy/utils/mythtvfs) - w00ts?

---

### Post by newlinux on 2008-01-29
There is a program in the contrib directory called mythrename.pl that will rename recordings to a more human readable format.

[http://www.mythtv.org/wiki/index.php/Mythrename.pl](http://www.mythtv.org/wiki/index.php/Mythrename.pl)

You'd probably want to run it as a cron job or a user job after recordings.

---

### Post by newlinux on 2008-01-29
> **stdPikachu said:**
> I'd also go the Samba route.

As for getting the files the right name, there's a FUSE project called MythTVFS which gives a "Program Name - Subtitle" view of your tvstore directory. If you shared this one out via samba it'd be much easier to navigate. You'd have to install the MythTVFS FUSE module yourself mind.

Whoops, no. Looks like there's already a package for Gutsy [http://packages.ubuntu.com/gutsy/utils/mythtvfs](http://packages.ubuntu.com/gutsy/utils/mythtvfs) - w00ts?

Oooh, I hadn't seen this before. Kind of cool and seemingly more elegant than mythrenam.pl. Maybe this is similar to how the UPnP server that mythtv uses exports its program info. Speaking of which, does the mediaMVP support UPnP? If so it could also play the recordings that way.

---

### Post by Nikas on 2008-01-29
> **newlinux said:**
> There is a program in the contrib directory called mythrename.pl that will rename recordings to a more human readable format.

[http://www.mythtv.org/wiki/index.php/Mythrename.pl](http://www.mythtv.org/wiki/index.php/Mythrename.pl)

You'd probably want to run it as a cron job or a user job after recordings.

I don't have the contrib directory. Where can i find the script?
Can i do something to install all the scripts that should exist in the directory?
(weekly builds)

---

### Post by newlinux on 2008-01-29
I'm pretty sure the mythtv contrib directory is installed by default in gutsy... It is in Feisty. Should be at:

/usr/share/doc/mythtv-backend/contrib/
You'll need to gunzip it and make it executable.

If it isn't there you can still get from svn I believe. I'll look it up if needed...

---

### Post by Nikas on 2008-01-29
> **newlinux said:**
> I'm pretty sure the mythtv contrib directory is installed by default in gutsy... It is in Feisty. Should be at:

/usr/share/doc/mythtv-backend/contrib/
You'll need to gunzip it and make it executable.

If it isn't there you can still get from svn I believe. I'll look it up if needed...

Yes! I do have it. ;-) Thanks.

---

### Post by Proost on 2008-01-29
Thanks everyone! I am going to try a couple of your suggestions and let youy know how it goes for a complete linux noob.

---

