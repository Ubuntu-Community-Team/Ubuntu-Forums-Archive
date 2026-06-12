---
title: "Networking with XP"
date: 2009-08-20
forum: Networking &amp; Wireless
---

### Post by motorcity909 on 2009-08-20
[SIZE=1]Hi, my Ubuntu machine is part of my home network with 3 XP machines.  I've got shared folders on all the machines and Ubuntu can successfully access the XP shares but I can only access the Ubuntu (samba) shares on an XP machine by turning off the firewell (via Firestarter).  Otherwise the XP machines simply say I don't have the rights to view these files.

I've got Firestarter set up to allow connections from the other machines by IP adress but that doesn't work.  I got it to work briefly but after a reboot of the XP machine the share was lost again.

Interestingly, if I do de-activate the firewall, the XP machine can see the Ubuntu share but only half the folder!  The share is my Music folder and I can see letters A to L but not M to Z!![/SIZE]
[SIZE=1]
I've also been unable to share my printers which are installed on the Ubuntu machine - hopefully if I can sort the shared folders, I can get the printers shared too.

Many thanks in advance for any help[/SIZE].

---

### Post by Iowan on 2009-08-20
[Problem 4]("http://ubuntuforums.org/showthread.php?t=1169149") might provide some answers.

---

### Post by motorcity909 on 2009-08-24
Thanks for that Iowna.  I followed the instructions in Problem 4 -


[LIST]
[*]uninstalled Firestarter (ironically, before I did this, I tried to access the Ubuntu share on an XP machine and it worked!  Although it was only Music letters A to L, M to Z still denied access)
[*]installed GUFW and activated the firewall
[*]inserted the code, changing it to my network IP range
[*]still no access on the XP machine
[/LIST]
I even de-activated the firewall via GUFW and the share was still inaccessible.

To be honest, sharing folders isn't 'mission-critical' (the main thing is that I can access my son's XP machine and backup his Documents) but now this is more of a challenge I'd like to beat!  :)

---

### Post by motorcity909 on 2009-08-24
I really need to learn to be patient.  In the time it took me to type my last posting and send it, my network had obviously sorted itself out and the Music folder was accessible on the XP machine.  That said, it was only letters A to L, still no M to Z.

XP shares are still happily accessible on the Ubuntu machine.

I'm going to reboot both the XP and Ubuntu machines to see if the share survives.  Will post results soon.

---

### Post by motorcity909 on 2009-08-24
Okay, here is the current state of play.


[LIST]
[*]I can access the Ubuntu share on an XP machine, but only Music letters A to L, not M to Z.
[/LIST]

[LIST]
[*]I can no longer access XP shares on the Ubuntu machine as per 'windows share' screengrab.
[/LIST]

Regarding the fact that XP can only access A to L of the shared Music folder, the strange thing is the XP machine shows all folders M to Z as being empty.  The two screengrabs (music_share1 and music_share2) show the Properties of the last L folder and then the Properties of the first M folder.  As you can see, the first correctly shows over 1gb of Lucinda Williams, the second shows 0kb of Machine Head, even though there is definitely an album in that folder.

Folder A to L totals 33.9gb, while M to Z is 25.8gb.  Is there a maximum size to a shared folder?

To be honest, I'm getting a bit frustrated with this whole sharing question - maybe I'll just copy files from one to another with a memory stick! :)

---

### Post by dmizer on 2009-08-24
"Failed to retrieve sharelist from server" is almost always related to a firewall problem.

Please try all suggested fixes for all problems shown in the 6th link in my sig. It will likely fix both XP and Ubuntu.

---

### Post by dmizer on 2009-08-24
Also, if you just want to share music with computers on your network, try [gnump3d]("http://www.gnu.org/software/gnump3d/").

You can install it through synaptic package manager.

After installing it, just edit /etc/gnump3d/gnump3d.conf and change the "root = " option so that it points to your music directory.

Then you can browse to [noparse]http://ubuntu-ip-address:8888[/noparse] in your Windows computer and stream music. It'll be much faster and more convenient for your Windows users that way.

---

### Post by motorcity909 on 2009-08-24
Thanks for that Dmizer.  

I've figured out a workaround in order that I can see the XP shares on Ubuntu.  I de-activate the firewall via GUFW and access the XP shares so they are mounted on my desktop.  I then re-activate the firewall and those XP shares remain accessible.  I can then copy the files I need.  Once the shares are unmounted, they are inaccessible again unless I de-activate the firewall again.

For the small amount of XP to Ubuntu filesharing I need to do, this is an acceptable solution.  It only means the firewall is down for about 30 seconds when I need it.

You're right to say the main thing I'm trying to do here is share my Music folder, mainly to my son's XP machine, so I will definitely give gnump3d a try.

Thanks again! 

:guitar:

---

### Post by motorcity909 on 2009-08-25
Hi again Dmizer, I'm pleased to say the Music folder share to the XP machines is still good, not been lost overnight with machines switched off.  My workaround for accessing the XP shares is also fine, so I'm sticking with that.

The last problem now is getting the entire Music folder to share to the XP machines - as I said before you can access letters A to L, but not M to Z.  Hence, I'd like to try gnump3d as you recommended.

But it doesn't appear in a search on synaptic package manager.  Is there a terminal code I can enter to install it?  Thanks in advance for any help!

---

### Post by dmizer on 2009-08-25
Apparently it's not in the repositories anymore, which is a shame. But you can get it here: [http://ftp.uk.debian.org/debian/pool/main/g/gnump3d/gnump3d_2.9.9.9-2_all.deb](http://ftp.uk.debian.org/debian/pool/main/g/gnump3d/gnump3d_2.9.9.9-2_all.deb)

Here's the MD5 checksum: a4d072a0d356896dab41975d0c6aa63a

Once you download it, you can just double click on it to install.

---

