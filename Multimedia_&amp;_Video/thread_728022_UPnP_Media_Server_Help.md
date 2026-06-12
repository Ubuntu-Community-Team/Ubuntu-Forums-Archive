---
title: "UPnP Media Server Help"
date: 2008-03-18
forum: Multimedia &amp; Video
---

### Post by burns863 on 2008-03-18
Some help needed along the lines of UPnP and Mediatomb...

I have installed the Mediatomb UI, Daemon and Common packages through synaptic after enabling the APT repository, and its here that I am confused.

The /var/lib/mediatomb directory is empty, where as all the documentation I have been reading suggests this is the location of the config file.  Is this right?

When I start the mediatomb UI through the applications menu Firefox says it cant find the file (as the directory is empty, as said above).  So... through terminal I binded mediatomb to "wlan0", and started the mediatomb server.  In a second terminal window I ran the comand "mediatomb -d" to run the server in the background.  This worked, but I still didnt seem to have any files in the directories where I expected.

So.. I reinstalled, but to no avail.  And now, whenever I start the server, run the daemon command ,then close the terminal windows, Mediatomb becomes in accessible through firefox (or at least the page is, but the filesystem & database produce an error of failed connection).

Have I gone wrong somewhere?  Completely confused now! I would really appreciate any help :)  Gona post this up on the Mediatomb forums too but they dont seem as active as the Ubuntu Community :guitar:

Thanks!

Dan

---

### Post by Tomosaur on 2008-03-18
> **burns863 said:**
> Some help needed along the lines of UPnP and Mediatomb...

I have installed the Mediatomb UI, Daemon and Common packages through synaptic after enabling the APT repository, and its here that I am confused.

The /var/lib/mediatomb directory is empty, where as all the documentation I have been reading suggests this is the location of the config file.  Is this right?

When I start the mediatomb UI through the applications menu Firefox says it cant find the file (as the directory is empty, as said above).  So... through terminal I binded mediatomb to "wlan0", and started the mediatomb server.  In a second terminal window I ran the comand "mediatomb -d" to run the server in the background.  This worked, but I still didnt seem to have any files in the directories where I expected.

So.. I reinstalled, but to no avail.  And now, whenever I start the server, run the daemon command ,then close the terminal windows, Mediatomb becomes in accessible through firefox (or at least the page is, but the filesystem & database produce an error of failed connection).

Have I gone wrong somewhere?  Completely confused now! I would really appreciate any help :)  Gona post this up on the Mediatomb forums too but they dont seem as active as the Ubuntu Community :guitar:

Thanks!

Dan

Try looking in ~/.mediatomb, that's where my config file is :)

---

### Post by burns863 on 2008-03-18
From the mediatomb forum I have found out that the config file wont be generated until the server is booted for the first time as a system daemon.  The config file at ~/.mediatomb is used until then.

So... I thought I was along the right lines using 'mediatomb -d' to run as a system daemon although it doesn't appear to be working.

Is there anyway I can check that mediatomb starts on boot up other than just trying to use the server?

---

