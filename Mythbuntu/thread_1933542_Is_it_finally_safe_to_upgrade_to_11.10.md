---
title: "Is it finally safe to upgrade to 11.10?"
date: 2012-02-29
forum: Mythbuntu
---

### Post by JamesNorris on 2012-02-29
Around the time of 11.10, there were lots of posts about lirc breakage. 

lirc is one of the only things that I can't afford to break (WAF - apparently controlling Myth with a keyboard is unacceptable)

If I take the plunge now, rather than going straight to 12.04 next month, will I still see this breakage. 

I did a search, but aside from the workarounds, I can't find anything confirming a fix was ever published.

---

### Post by nickrout on 2012-02-29
What is wrong with your present system? If the answer is "nothing" then do not upgrade.

---

### Post by JamesNorris on 2012-02-29
> **nickrout said:**
> What is wrong with your present system? If the answer is "nothing" then do not upgrade.

It is mostly due to the unlikeliness of 0.25 being available on 11.04.

---

### Post by newlinux on 2012-02-29
Personally, if you can wait, I'd wait for a little while after 12.04 is out and then go with that. I tend to do LTS->LTS as long as my systems are stable or there's not something I just gotta have in a newer release. The mythbuntu repos will stay up to date for LTS releases. Then you can wait longer between upgrades and still have access to updates if you need them.

---

### Post by ijumpship on 2012-02-29
To Me this question is like "Do  I buy something new or stick to the Old?" Most time people tell you that if something is not broken in Linux do not change it.But Here are my recommendations

Assuming you have an existing system

[LIST=1]
[*]Make sure your OS is normally on a separate  drive from such things as MUSIC,VIDEOS,Picture-I learnt from using version 9.04 through to 10.10 that  plunge upgrades can be painful like sound do not work,front-end not connecting blah blah blah.
[*] Get a test drive (40g-80g cheap on EBay/some stores)  and load the New System.it just take a laptop and a spare machine to test.put the front-end on a CD on the laptop. and test.
[*]Please I hope you have turners that are network or USB type( I used the network types)
[*]**[COLOR=Red]Do not take down your system until you know no-one is at home.[/COLOR]**The wife/family will kill you.So maybe its time to send them on a day break.Just make sure you have time
[*]Then take the plunge if you like it.
[/LIST]
**Well for all the New  Persons your Option is to use the latest stable but if it do not work out almost guarantee the version before when properly upgrade and update will bring satisfaction  **


I am using 11.10 and I like the added features.I had to reconfigure my mythweb  for external use, as I am using  set-top boxes to connect to the front-end when I am away .


I like "Newness","Living on the Edge" so I ain't gonna stick to the old car cause it takes me to work but the wheels are dropping off and the repairs cost as much as buying a new car.


So just read on mounting drives,securities,etc. and take the plunge with me 11.10 is sweet with a little sweat.

---

### Post by tobiz on 2012-03-11
Is it safe to upgrade to 11.10? In my view after my experience, no. I did a clean install of 11.10 and initially had it working, including mounting a RAID 1 array on /var/lib/mythtv. I then applied all the existing updates and the troubles began. Most significantly the system would no longer power off, just went into some strange 'hung' mode displaying the 5 red dots. Eventually found that if you run upgrade-grub2 just before powering off (via shutdown) power off worked; not a nice fix! Then found that by setting "auto save session on logout" power off also work; better work around. Then tried to setup RTC wakeup (my 8.10 'production' system has this and has been running ok for years, ie I've done it before). Whilst the system will wake from RTC alarm it wouldn't shutdown when no user logged in. Eventually the system totally destroyed itself for no reason I could think of to do with what I had done, eg the windows could not be moved and other strange, weird behaviours. So I've started again, this time a clean install of 11.04; I hope this turns out better.

---

### Post by neutron68 on 2012-04-28
After the initial posting of a Mythbuntu "release" version, is a new version of the ISO ever released (to fix known problems, for example)?

I've not seen any "ALL CLEAR" messages given for 11.10, so it makes me think that new ISOs are NOT made after the initial release date.

I'm currently running 11.04.  
Could I upgrade straight to 12.04?  Or must I upgrade to 11.10 first and then upgrade to 12.04?

Thanks,
Eric

---

### Post by neutron68 on 2012-06-25
I'm currently running 11.04.
Could I upgrade straight to 12.04? Or must I upgrade to 11.10 first and then upgrade to 12.04?

Thanks,
Eric

---

### Post by Lester_Burnham on 2012-06-26
Hi,

How tweaked is your current system? No hacked fixes etc. Nvidia video hopefully.
Backup database.
I upgraded my 11.04 to 11.10 and it's fine. You can then add mythtv 0.25 ppa or upgrade to 12.04

I only use the MCE remote, so only a couple of button names to change in /.lirc/mythtv
If buttons don't work, find what they are using irw in a terminal.

Lester

---

### Post by neutron68 on 2012-06-26
The 11.04 system is not tweaked very much.  I added a script to the /etc/cron.hourly directory to call to the mythlink.pl script once an hour - which generates symlinks with "pretty" (human-readable) video file names.

Can I upgrade straight to 12.04? Or must I upgrade to 11.10 first and then upgrade to 12.04?

Thanks,
Eric

---

### Post by alien878 on 2012-06-26
Since 11.04 is not an LTS, you will have to first upgrade to 11.10.  When I did this, a lot of things were broken on 11.10, but I just upgraded to 12.04 immediately and (most) things started working again.

VERY IMPORTANT:  Make sure you have a backup of some type or do it on a test drive first.  I have my system on a separate partition from videos, music, etc. and always use clonezilla to clone the boot partition before any upgrade (even simple package upgrades).  These backups have saved me several times.

---

### Post by neutron68 on 2012-06-26
I've got an nvidia GeForce 8600 GT card so I am VDPAU compatible, etc.

My Mythbuntu 11.04 install is all on one 1TB hard drive.  
The Mythbuntu installer put my /var/lib directory in it's own xfs partition.
I'm not sure how to surgically back up only the OS and leave the /var/lib/ directory out of the backup?

I just did a backup with the Mythbuntu backup tool in the Mythbuntu Control Centre.
Is that good enough?  Am I ready to plow onto 11.10?

I'm reading about the horrors of 11.10 in this thread:
[http://ubuntuforums.org/showthread.php?t=1860270](http://ubuntuforums.org/showthread.php?t=1860270)

By now (6 months after 11.10 was first released), are there post-release fixes that get downloaded along with the distro upgrade, that fix all the problems noted (X not starting, black screen after upgrade, automatic login not working, myth backend not automatically starting)

Eric

---

### Post by Lester_Burnham on 2012-06-26
Hi,

If you had a spare 1tb drive. You could clonezilla the whole drive, but it's not the easiest to use. Or install 12.04 on new drive and import database etc.
I would backup the database and copy your recordings to another drive, as you can always reinstall the OS and re-import. I have not really used the MCC backup as yet. So not sure what it backs up.

What did the back-up give you?

Lester

---

### Post by neutron68 on 2012-06-26
> **Lester_Burnham said:**
> Hi,

If you had a spare 1tb drive. You could clonezilla the whole drive, but it's not the easiest to use. Or install 12.04 on new drive and import database etc.
I would backup the database and copy your recordings to another drive, as you can always reinstall the OS and re-import. I have not really used the MCC backup as yet. So not sure what it backs up.

What did the back-up give you?

Lester

It made a 2.2kb tar.gz file in the /home/username directory.  I think it backed up the myth database.  I'm not sure what else.

My Mythbuntu 11.04 install is all on one 1TB hard drive.
The Mythbuntu installer put my /var/lib directory in it's own xfs partition.
Do you know how to use clonezilla to surgically back up only the OS and leave the /var/lib/ directory out of the backup?

Eric

---

### Post by Lester_Burnham on 2012-06-27
Hi,

I normally use this page as a guide for backing up the database.
[http://www.mythpvr.com/mythtv/tips/migrate-recordings.html](http://www.mythpvr.com/mythtv/tips/migrate-recordings.html)

Not sure in clonezilla, as I've never just backed up directories before. Normally just image to another disk.

With the /var/lib/ being on its own partition and as long as your recordings in /var/lib you should be fine. 
Do the database backup using my link and see what size it turns out as an .sql file.

Lester

---

### Post by alien878 on 2012-06-27
> **neutron68 said:**
> My Mythbuntu 11.04 install is all on one 1TB hard drive.  
The Mythbuntu installer put my /var/lib directory in it's own xfs partition.
I'm not sure how to surgically back up only the OS and leave the /var/lib/ directory out of the backup?
I don't know why mythbuntu defaults to put all the videos/music/gallery in /var/lib as there is stuff in there that suspect needs to be restored with the OS.  It is a bit of work, but I would recommend you create a new partition by shrinking the OS one (with gparted) and mount it on /myth.  Then move the videos/music/gallery/etc. into this directly (mytharchive) and change the mythbackend settings to use them.  You can then use clonezilla to clone the smaller OS drive.  The Parted Magic CD has both gparted and clonezilla.  Alternatively, you could just cone the whole drive if you have a big enough backup disk.  That might take a while though.

CORRECTION:  I misread your post.  If /var/lib is already in a separate partition then you should be good to go with clonezilla because if you clone the root partition, /var/lib will be excluded.  You might want to tar up /var/lib excluding recordings etc. as I'm not sure if the upgrade will do anything in there that would hinder an OS restore.
> **neutron68 said:**
> I just did a backup with the Mythbuntu backup tool in the Mythbuntu Control Centre.
Is that good enough?  Am I ready to plow onto 11.10?
That will only back up mythtv.  If you have to go back, it will mean a re-install from scratch and you will lose any tweeks or customizations you have made to the rest of the system.

---

### Post by keepitsimpleengr on 2012-07-02
You are wise to be cautious…

I recently updated from 10.10 to 12.04; a client (drop-dead easy :D ), a client/audio-visual workstation (huge struggle :rolleyes: ), and the client/server (relatively easy :p ), all 64bit.

I journaled and notated as Q&A the client/audio-visual workstation upgrade in askubuntu ([here]("http://askubuntu.com/questions/151461/how-can-i-upgrade-from-ubuntu-10-10-to-12-04")).  To get around the many problems of 12.04 as a workstation, I switched to Xubuntu, but I upgraded to Ubuntu, then switched to Xubuntu. I also dropped Unity on the workstation but not the other client or client-server.

Fortunately, I use separate partitions in my systems.  Highly encouraged.

The final client-server pretty much went without a hitch, except for the driver for my tuners, but that was an easy fix, see the askubuntu Q&A [here]("http://askubuntu.com/questions/146136/hauppauge-wintv-hvr-2250-tuner-firmware-to-work-in-12-04-mythubuntu").  

There are some annoyances in 12.04, the new kernel handling of the remote doesn't work (hopefully fixed in kernel 3.5) and the Unity top panel remains visible but useless on mythfrontend (in line to be fixed).  There is some tearing on HD playback (as yet not looked at by me) and the occasional freeze of mythfrontend.

Hope my experiences can be helpful, good luck.

---

