---
title: "Mythbuntu newbie with q's on root access et al"
date: 2008-12-23
forum: Mythbuntu
---

### Post by bryantg on 2008-12-23
Hi - I'm an old time unix guy, but brand new to Mythbuntu, and have a few questions that I hope y'all can help with.

I just installed it to help a friend with a project on a raw machine, and I have no idea what the root password is, just the myth user that it created during the install.  Is there a default for this, or a way I can reinstall and set it, or do need to install plain Ubuntu first, then MythTV on top to get more control over the environment?

Does Mythbuntu install the entire OS?  I tried to do a udevmonitor, and it claimed it couldn't find it, don't know that's a permissions problem or an install thing.

Lastly, is there a way to get a video to show up automagically when it gets copied to the videos directory (var/lib/mythtv/videos)?  I noticed that I had to go to a setup screen to add it before it would show up in the list of videos to play.

Thanks,
Greg

---

### Post by volkswagner on 2008-12-24
I am not sure about the video question.

Mythbuntu installs a complete OS.  It is basically a trimmed version of Xubuntu, with the added goodies of Mythtv and mythbuntu-control-centre.

When you installed Mythbuntu, you should have created an admin type user.  Perhaps bryant for your case.  With this user can can easily achieve root privileges with sudo in front of your command.  You use brant's password when prompted. 

like

```
sudo thunar
```

would launch the file browser with root privileges, be very careful here!!!!

If you want to set the password for root run

```
sudo passwd root
```

You will then set and confirm the password.

If you want shell access as root run

```
su
```

then enter your new root password.

---

### Post by bryantg on 2008-12-24
I must have messed up the first install.  I had tried sudo earlier, but it claimed it didn't have setuid privilege.  I reinstalled, and it seems to work fine, now.

Thanks,
Greg

---

### Post by jaakan on 2008-12-25
I'd just like to add that following will let you become root if you use an admin user account ( the first user that gets created on mythbuntu ) without needing to enable direct access to the root account 

```
sudo -i
```

```
sudo su -
```

---

