---
title: "[solved] My Samba Problem"
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by Indras on 2006-06-19
I'm making this post as some searchable help for someone who is having the same problem.  I spent nearly three hours figuring this one out (much of the time searching the forums), so I thought the best thing to do was to post the solution to my problem.

I have two computers, both ran Windows XP with no security.  One belongs to my wife, the other to me.  We share an internet connection through a Linksys 4-port router/firewall, and the 2Wire Home Gateway/DSL Modem has an additional firewall built in.  I'm constantly having to poke holes in both of them when I want to try a new P2P program.

But anyway, my first time installing Ubuntu, I installed in a little bit of hard drive space I had left in my primary master drive.  My partitions looked sorta like this (from memory):
/dev/hda1  ( /win98 ) FAT32 Windows 98 SE drive, 2Gb
/dev/hda5  ( /winxp ) NTFS Windows XP drive, 65Gb
/dev/hda6  ( /)  ext3 root partition, 10Gb
/dev/hda7  Linux-Swap, 1Gb
/dev/hdb1  ( /storage ) FAT32 Storage space, 80Gb

My 80Gb of storage space is shared between me and my wife.  It contains about 10Gb of digital photos, 5Gb of MP3s, installation files for abandonware games (one of my hobbies), and basically is just the "throw into" drive.  In order to make the switch completely from WinXP to Linux, I needed to make the /storage drive shareable via samba to my wife's computer, who was going to stay with Windows, for gaming purposes.

It always keep a copy of linux installed on my machine, ever since Redhat 7.  Last time it was Fedora Core 2.  I've never seriously stuck with it for more than a few hours out of frustration, or desire to play some DOS or Windows game.

After cruising around the forums, I found a good tutorial on getting samba up and running and get my drive shared so that my wife could access it without a password, which was a beautiful thing.

After a while, I noticed that my root partition was more than half full.  I knew I didn't need that much space in my NTFS partition anymore, so I popped in my Partition Magic 8.0 disk in my drive.  I tried shrinking the partition, but it contained errors that would've taken too long to correct, so I just deleted it and put a new 10Gb NTFS partition in its place.  Then I tried to stretch my ext3 partition to fill up the freed space, about 55Gb.

Partition Magic crashed about halfway through the move for some unknown reason (which I have seen other stories about this on the forums).  So be forewarned: do not try to use this software to move Ubuntu partitions.

I didn't bother trying to recover it, I just deleted it and made a new ext3 partition in its place and reinstalled Ubuntu.

However, this time, using the exact same guide, I could not get the /storage drive to share to the Windows box.  Her computer would enter into network neighborhood, my computer (scrappy), and could see the share.  However, when she tried to open it, it gave her a warning about not having permission to access this device.

Hours of head-banging and frustration later, I followed the guide at [www.ubuntuguide.org](www.ubuntuguide.org) on how to make a /home/public share that anyone could write to without authentication.  It worked like a charm.  Network neighborhood now showed two entries: Storage and Public.  Public, she could enter, and put files into and take them out.  Storage still gave the same error.  So I knew it was a permissions problem.  Sure enough, doing a ls -l in my root drive showed /storage mounted as 770, not 777 like it needed to be.  Another few minutes of searching for guides showed me why.  In my /etc/fstab, /storage was being mounted with "umask=007".  Changing this to "umask=0" and remounting the partition fixed it.

This is one of those types of problems that I probably could not have gotten solved by asking for help here in the forums, since it was VERY situation-specific.  However, I wouldn't feel right without sharing my solution with anyone else who may be searching for the answer.

However, I still have some questions.  Why would my first installtion have no problems with this, but the second installation, with the same disc and nearly the exact same partition setup, have this problem?  I have no way of knowing what my /etc/fstab looked like on my old installtion, since it is gone, but I can only assume that line was not in there since my share did work.  How does the Ubuntu installer determine this?  Is there a chance that some software I had installed the first time had corrected this?  Is there a way to force a partition to read as 777, even though it was mounted as 770?

---

