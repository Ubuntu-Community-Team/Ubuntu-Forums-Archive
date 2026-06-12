---
title: "unable to get to iomega home network hard drive"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by madmaxnj on 2009-01-03
Okay, here's what I've found/tried so far.

First, this drive suxs and in XP you need to run their utility every time to 'find' and mount the drive.

On my LAN (D-link wired/wireless router) I have an XP box, Ubuntu box, and occasional wired/wireless Windows laptops.  I'm running Intrepid and am relatively new to linux.

I can only see the network drive in Ubuntu if my XP box is On.  If the XP box is off, the network drive does not show up anywhere.  If I can see the drive in Places-Network (I see the two shared folders created on the drive), if I double click on one of the folders, it acts like its going to the shared folder, but its empty (though I can see all the files in XP).  This happens with the non-password shared folder and the password shared folder (no prompt for a password).  If I look at the properties the Type:  unknown type (application/octet-stream).  Contents: nothing.  Location: network:///.  Volume: unkown.  Free space:  unknown.

I've searched around and read a few other suggestions.  I tried in Terminal nautilus smb://username@server/share and get an error Failed to mount Windows share.  Please selelct another viewer and try again.

I think I need to set something somewhere so it knows that this is a folder.

I'v tried sudo mount.cifs //server/share /media/share but it locks up after I hit enter after it asks me for a password (there is no password).

If I go to a web browser and type smb://server/ I see the index and the two folders (looking like an FTP site).  But if I click on one of the folders it acts like it goes to the folder but doesn't change what it displays.  Likewise if I just type in the path with the folder name directly into the URL it acts like its going there but nothing happens.

If I try Place-Connect to Server, I always get Failed to mount Windows share.  I've tried server name only (name or IP), servername and share(folder name), with and without username (no password, though I get a prompt).

All roads seem to get to the same dead end at this point.  Please help me find my way.

Thanks

---

### Post by madmaxnj on 2009-01-05
bump

---

### Post by madmaxnj on 2009-01-11
Okay, I figured out a way to connect to the iomega home network hard drive.  Like others that have posted I had many problems trying to connect to it through traditional methods.  But I found a way. 

First, login to the admin utility of the drive.  Enable FTP.  On the FTP page create a user account, and then give the user read/write privileges.  I also created a password since all the attempts I've tried to connect ask for a password, even when on the smb settings I didn't set one.

Now, go to Places-Connect to Server.  Select:
-FTP (with login)
-Server: your shared drives IP address
-Port:  default on iomega is 21
-folder:  default is public
-user name:  whatever you setup in the first step
-add a bookmark so you don't have to do this every time.  The bookmark will show up in your Places drop down.

When you connect it will ask for the password you created in the first step.

Now, I get an keyring error, which I just x out of and then get an error that it didn't connect, even though it did and I have the folder icon on my desktop.  Its not elegant, but it works.  Now if I can fix the keyring and somehow make this try to autoconnect on bootup I'll be all set.

---

