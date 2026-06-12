---
title: "Sharing media files on a NAS"
date: 2010-03-23
forum: Networking &amp; Wireless
---

### Post by SNR99 on 2010-03-23
I thought I would try and be clever but have become stuck!  I have bought a NEtgear ReadyNAS with a view of copying all sound files and photos to one place.  I have a wired home network and a Windows XP PC which I have mapped the NAS to as a network drive.

Then came the Linux bit.  I have a laptop which I want to do the same with.  I have set up the NAS so that it operates with both CIFS and NFS file systems.  I can see the CIFS file system in the Network part of Ubuntu 9.10 but am having trouble in getting programs to see it.  Ideally I want to use F Spot or Picasa to view the photos and then also use one of the audio packages to play music around the house.  When I ask F Spot or Picasa to search for files or folders, the network does not show up in the list.

Do I need to add the network drive similar to the XP machine?:D

---

### Post by Morbius1 on 2010-03-23
If you're using Nautilus to connect to the NAS it creates a mount point that your application can access - the problem is it's in a hidden directory ( Why? - no one knows ).

It's located at: **/home/your_user_name/.gvfs**

You have to enable Nautilus to "see" that directory by going to:
**Nautilus > Edit > Preferences > View > Show hidden and backup files.**

If your app can't see the hidden directory then make a symlink from there to a non-hidden directory. For example:

Open **Terminal**
Type **mkdir /home/your_user_name/NAS**
Type **ln -s /home/your_user_name/.gvfs /home/your_user_name/NAS**

---

### Post by SNR99 on 2010-03-23
Thanks, that worked. Picasa still cant see it but another graphics package can which is a bit weird.  Picasa gets as far as the NAS folder I created above but then sees nothing else.  Id really like to use Picasa but am stumped now - any ideas?

---

