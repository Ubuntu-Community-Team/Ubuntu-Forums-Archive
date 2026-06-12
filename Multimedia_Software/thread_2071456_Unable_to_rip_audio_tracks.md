---
title: "Unable to rip audio tracks"
date: 2012-10-15
forum: Multimedia Software
---

### Post by oxf on 2012-10-15
**Unable to rip audio tracks all of a sudden!**             
                                                                Please can  someone help me with this problem. I'm trying to rip some audio tracks.  Previously I have ripped without problem so I don't know why I have the problem  now all of a sudden!

I have two CD ripping applications installed, Asunder and Ruby Ripper.
Neither will work.

In Asunder it scans disk for a while and then stops and says "Unable to create directory "name of album" permission denied"

In Ruby Ripper it does a similar thing trying over and over to scan the disk and then says
" No disk found in drive /dev/sr0"

I've tried repeatedly and rebooted but no luck..

Any ideas whats wrong?

Thanks

---

### Post by evilsoup on 2012-10-15
It could be a hardware problem... can you play the music on the disc, when it's in the drive? And can you see the files in your file manager?

---

### Post by Yellow Pasque on 2012-10-16
For rubyripper, does /dev/sr0 exist?

Asunder stores settings in ~/.asunder
The second line of that file is where it creates files. Make sure your permissions on that directory aren't screwed up.

---

### Post by oxf on 2012-10-16
Yes it plays CD's just fine!

Where exactly is the Asunder directory located? I can't find it!

Thanks

Veronica

---

### Post by rajeevisonline on 2012-10-16
it says permissions...can logging in as root fix the issue, please check your permissions.

btw...why dont u try rhythmbox?

---

### Post by Yellow Pasque on 2012-10-16
> Where exactly is the Asunder directory located? I can't find it!

It's not a directory. It's a hidden file (named .asunder) in your home directory.

---

### Post by Amon_Re on 2012-10-17
> **oxf said:**
> **Unable to rip audio tracks all of a sudden!**             
                                                                Please can  someone help me with this problem. I'm trying to rip some audio tracks.  Previously I have ripped without problem so I don't know why I have the problem  now all of a sudden!

I have two CD ripping applications installed, Asunder and Ruby Ripper.
Neither will work.

In Asunder it scans disk for a while and then stops and says "Unable to create directory "name of album" permission denied"

In Ruby Ripper it does a similar thing trying over and over to scan the disk and then says
" No disk found in drive /dev/sr0"

I've tried repeatedly and rebooted but no luck..

Any ideas whats wrong?

Thanks

I don't think it's a hardware problem, I have the exact same problem with 2 drives and AUDEX. I was ripping CD's fine on Sunday, today I get 'drive error'.

I'm thinking an update broke something but no luck yet in tracking down which update and what.

---

### Post by Amon_Re on 2012-10-17
Never mind, for some reason my Android phone is identifying as a CD player and was messing up Audex.

---

### Post by harrii on 2012-10-20
Hi,

there is a bug in audex: if you have 2 optical drives, only one will work (asumably the one which is first in alphabetical order).

However, this workaround does for me:
Edit ~/.kde4/share/config/audexrc and change cdDevice=1 to cdDevice=/dev/sr0 (or sr1)

---

