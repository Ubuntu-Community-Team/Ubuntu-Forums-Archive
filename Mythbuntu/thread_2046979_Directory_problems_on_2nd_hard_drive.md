---
title: "Directory problems on 2nd hard drive"
date: 2012-08-24
forum: Mythbuntu
---

### Post by image_editor on 2012-08-24
I have recently installed a second hard drive in my mythbuntu 12.04 system. I have mounted it at point /media/montsalvat.
I have created two directorys within this being video and recordings.

Even though i have changed the "default", "Live TV", and "Videos" storage directory in the backend to the following respectively;
/media/montsalvat/recordings
/media/montsalvat/recordings
/media/montsalvat/video
Live TV wont record to the recordings directory and the content of the videos directory is not seen within the frontend gui (on the same machine).
I have checked permissions by looking at Thunar file manager and have found the following.
/media is owned by root read and write
/montsalvat is owned by root read and write
/media/montsalvat/recordings is owned by mythtv read and write
/media/montsalvat/video is owned by mythtv read and write.
I have noticed that when i change /media/montsalvat to owned by mythtv everything below this folder dissapears. At this point mythtv can then write a file to the recordings directory but the front end can never play it back saying that the recording is unavailable.
I have obviously stuffed up somwhere chronic, any help would be greatly appreciated.
My family loves this system and i just want to get it working.
Regards Damian ](*,)

---

### Post by klc5555 on 2012-08-24
In a Mythbuntu machine, the mythtv apps and utilities expect the entire path to the TV recordings directories to be owned by mythtv, group mythtv and permissions set to something like from 755 to maybe 775 to allow everybody who should to read and write. Your main user should be a part of the mythtv group. 

If the owner of part of the recording path is "root", you're generally busted: root accesses the hardware (recording hardware and lirc stuff), mythtv accesses the database and related stuff, and your main user runs the frontend. If the owner of part of the path is your main user, quirky mythtv problems are likely, because though your main user is (or should be) part of the "mythtv" group, that doesn't mean mythtv can read/write to directories owned by your main user.

For these reasons, mythbuntu tends to install the recordings, videos, and music directories under /var/lib/mythtv/... where the necessary permissions and ownership are easy. Whenever I add a new storage drive, I'll always mount it under /var/lib/mythtv/... unless I'm putting stuff on it I don't intend mythtv to be able to access.

I'd recommend mounting your new recordings drive under /var/lib/mythtv/... Then set all directories (and files) on this drive to owner mythtv, group mythtv, and permissions 775. Mythtv (and you) should have no access trouble there. Unless your main user is not part of the mythtv group. If it is not, this should be fixed.

There are other ways to get around the permissions headache, but most of them are not really to be recommended because they compromise the security of your machine.

---

### Post by tgm4883 on 2012-08-24
> **klc5555 said:**
> In a Mythbuntu machine, the mythtv apps and utilities expect the entire path to the TV recordings directories to be owned by mythtv, group mythtv and permissions set to something like from 755 to maybe 775 to allow everybody who should to read and write. Your main user should be a part of the mythtv group. 

This isn't entirely true, which you even back up later. The /var directory is owned by root. I myself put everything in sub directories in /srv/mythtv/ and /srv is owned by root.

> **klc5555 said:**
> 
If the owner of part of the recording path is "root", you're generally busted: root accesses the hardware (recording hardware and lirc stuff), mythtv accesses the database and related stuff, and your main user runs the frontend. If the owner of part of the path is your main user, quirky mythtv problems are likely, because though your main user is (or should be) part of the "mythtv" group, that doesn't mean mythtv can read/write to directories owned by your main user.

For these reasons, mythbuntu tends to install the recordings, videos, and music directories under /var/lib/mythtv/... where the necessary permissions and ownership are easy. Whenever I add a new storage drive, I'll always mount it under /var/lib/mythtv/... unless I'm putting stuff on it I don't intend mythtv to be able to access.

I'd recommend mounting your new recordings drive under /var/lib/mythtv/... Then set all directories (and files) on this drive to owner mythtv, group mythtv, and permissions 775. Mythtv (and you) should have no access trouble there. Unless your main user is not part of the mythtv group. If it is not, this should be fixed.

There are other ways to get around the permissions headache, but most of them are not really to be recommended because they compromise the security of your machine.

The OP mentions who owns those folder, but doesn't mention the full folder permissions (which I think is likely the issue). For instance, you can write recordings to a folder but not play them back? Both of those are done by the backend, so for some reason the backend (the mythtv user) can write to but not read from that directory.

---

### Post by klc5555 on 2012-08-24
> **tgm4883 said:**
> This isn't entirely true, which you even back up later. The /var directory is owned by root. I myself put everything in sub directories in /srv/mythtv/ and /srv is owned by root.

Oops. :oops:  Well, I guess that puts the root in "root directory"...

But my main intention was actually only to discourage what I've seen several do when they add recordings storage drives to mythtv machines  --they mount the new drives at the root directory level, then when they notice they have permissions problems, they just open up the whole drive top to bottom to 777 and let everyone and everything access it.  Hard to imagine a better way to get hacked than that.

---

### Post by tgm4883 on 2012-08-24
> **klc5555 said:**
> Oops. :oops:  Well, I guess that puts the root in "root directory"...

But my main intention was actually only to discourage what I've seen several do when they add recordings storage drives to mythtv machines  --they mount the new drives at the root directory level, then when they notice they have permissions problems, they just open up the whole drive top to bottom to 777 and let everyone and everything access it.  Hard to imagine a better way to get hacked than that.

Yea that would be bad.

FWIW, I've always seen people try to put the recording directory in their home directory, and for some reason, that causes problems. I've never investigated it though.

---

### Post by langner on 2012-09-11
Hi,

I don't know if you have solved this problem yet but I had a similar problem when I installed a new hard drive. I solved it by following the instructions in the link. 

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
(have a look from about 'mount the drive' section where it states **USERNAME**. This will give you the user rights for the folder(s). Before you do anything from the page, please read it all.)

Now just so you know, I was able to follow this and I'm a complete noob to this and all is working well.

Matt

---

