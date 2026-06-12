---
title: "Samba server stops accepting mount requests, help!"
date: 2011-04-21
forum: Networking &amp; Wireless
---

### Post by travlemon on 2011-04-21
Hello!

I'm having an issue with a Samba server running on an Ubuntu "server".  Technically, it's not a server, it's just an old desktop with Ubuntu 10.04 running it..and I have a few server processes running (ProFTP, Samba, etc.)

The Ubuntu server is where I store all of my important files that get backed up to a separate hard drive.  I shared folders via Samba, and I use two computers to access the shares.  I access the shares with an .sh file I created that uses the mount cifs command to mount to those shares.

It has been working flawlessly for a long long time, up until recently.  For the past few days to a week, I will try to mount the shares with no result.  In the terminal, the commands just freeze, as if the command is trying to execute, but having network issues.

The only way I can get it to work is if I reboot the Ubuntu server, then it maps flawlessly.  But a day later, it's back to hanging up when trying to mount.


Sorry that's so long, does anyone have any idea what I can do to fix it?  I haven't changed a thing on the machine, so I don't know where the problem came from.  Also, I tried running updates making sure it's fully updated.  No go

Any help is much appreciated!

---

### Post by Harmless128 on 2011-04-21
Strictly speaking my problem is slightly different to yours but does involve the latest update and Samba. 2 days ago I applied the latest udate to one of my 10.04 machines. I had previously set up a shared folder folder so my Vista and xp machines could transfer files using a short cut or network neighbourhood.

Now the ubuntu machine appears in neighbouhood but it no longer has a share. I get the usual "you do not have permission to access" xp error box. When I try to create a new share using  Samba in Systems - Administrator it does run but the share doesn't appear. Even the printer folder which by default is shared on neighbourhood is no good.

The good news is that this has happened before and was fixed by a small update later on. I quess its a matter of bringing it to the attention of the authors of the latest update.

---

### Post by travlemon on 2011-04-22
> **Harmless128 said:**
> Strictly speaking my problem is slightly different to yours but does involve the latest update and Samba. 2 days ago I applied the latest udate to one of my 10.04 machines. I had previously set up a shared folder folder so my Vista and xp machines could transfer files using a short cut or network neighbourhood.

Now the ubuntu machine appears in neighbouhood but it no longer has a share. I get the usual "you do not have permission to access" xp error box. When I try to create a new share using  Samba in Systems - Administrator it does run but the share doesn't appear. Even the printer folder which by default is shared on neighbourhood is no good.

The good news is that this has happened before and was fixed by a small update later on. I quess its a matter of bringing it to the attention of the authors of the latest update.

Thanks for responding! I'm not quite sure that my issue was caused by one of the updates.  I hadn't updated this machine in a long time actually, and the problem occurred before I applied any updates.  However, I figured it was due for updates and maybe there would be something to fix it.  Unfortunately, it didn't work.  Some more updates came through tonight, and I'm going to see if they fix it.  I also shut down a couple networking programs I had running.  

If the problem goes away,  I'll try running the programs I eliminated, and see if the issue comes back.  One more funny thing about the problem, I can browse the network shares in Nautilus just fine.  Usually mounting works flawlessly and browsing is a pain...

I'll post my results back here.

---

### Post by headvampyre@hotmail.co.uk on 2011-04-22
Could you post your smb.conf?
This woud help greatly :) also , are all your machines Linux? You could use NFS if they are :)

---

### Post by travlemon on 2011-04-22
> **headvampyre@hotmail.co.uk said:**
> Could you post your smb.conf?
This woud help greatly :) also , are all your machines Linux? You could use NFS if they are :)

Hello, here is my entire smb.conf file in the code box below.  Unfortunately, I still have a good 3 or 4 Windows machines on the network, which need access to the shares as well.  

I confirmed that the problem is still present.  I rebooted the "server" yesterday and the shares mounted nice and quick, no issues.  But today, just a few minutes ago, they wouldn't mount.  I really don't understand, I never had this issue at all, and I haven't made any changes to the server.  

Another thing I will try is mounting the shares from a laptop I have that runs PCLinuxOS.  The computers, that are failing to mount, are running Mint 10.  Still, they mount perfectly when the server's been rebooted.  Oh man!

I hope you see something in smb.conf that I'm missing, I'm not too savvy on the file.  And thanks!



EDIT - SOLVED IT!!:  I've removed my smb.conf because I don't want it to be there if it doesn't have to be.  And, it is no longer needed, as I figured out what the problem was.

It's one of those things that was going to be inevitable that I notice it eventually.  Very simple problem, the drive that I store backups on is going bad, and causing the server to freeze when trying to access files.  I ran the PC without that drive plugged in, and I never had an issue mounting the shares.  So, that makes total sense, as the problem isn't even close to being Samba related!

On to my "fix" for the hard drive, if anyone is curious.  This is totally unrelated to Linux, but might as well share the info!  It's an external Maxtor 320gb USB hard drive, gray and very old looking.  It's from probably 2006.  The green power light stays solid, with no activity, and nothing appears to be spinning inside the drive.  No platters spinning, no clicking or crunching noises as if it were really messed up, nothing.  So I tried the freezer trick!  That's right, I shoved the drive into a sealed zip lock bag, and stuck it in the freezer.

First I tried 1 hour, then took it out and immediately plugged it into power.  Surprisingly, it actually heard SOMETHING moving, but not much activity.  I figured maybe it needs a little more time.  So I tried 5 hours, and had roughly the same experience as the 1 hour test.  Then, I wasn't messing around anymore, stuck that sucker in the freezer over night and well into the afternoon of today!  It still sounded like it wanted to move, but I wasn't getting the PC to recognize it.  I left it plugged into power and the PC while I left for a few hours.  I came back, and the PC still showed no sign of my junky Maxtor drive. Finally, I unplugged it from power, plugged it back in and....what do you know?  It started right up and I was browsing all of the files, with no issues reading the data whatsoever.

I don't think there was a disk/data problem with this thing, I think there's simply a power issue with starting the drive up or making it spin.  I don't think there's any issue with the actual data storage.  This thing will probably die on me again very soon, but at least I've removed the mystery to that annoying issue with my shares not mounting!

---

