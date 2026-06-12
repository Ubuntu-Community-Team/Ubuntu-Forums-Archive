---
title: "do I need to be root?"
date: 2009-06-10
forum: Mythbuntu
---

### Post by zapstrap on 2009-06-10
I tried posting this on the MythTV forums, but haven't got far:



I have an older mobo - ASUS P4P800VM, 2.8GHz P4, 1GB ram, 2 discs - 40GB ATA, 1.5TB SATA, LG DVD drive (new, but not bluray), Hauppauge PVR-150, eVGA e-GeForce N6200 256MB video.
 
I just wanted to give MythTV a test drive. I got the mobo/processor/case for $0, added the rest new. If I can get it working at least sort of, I'll swap out the mobo/cpu/ram for something a little faster, add another tuner card (one with ATSC/QAM) and carry on.
 
I installed downloaded, verified, burned onto a CD and installed mythbuntu from scratch, no multi-boot or anything fancy. The install went fairly smoothly. I put the OS on the 40GB drive, with plans to upgrade that later too. I put the 1.5TB drive on /home, thinking I'd keep media in a subdirectory off of that. After that, it seems to have all gone pear shaped.
 
I've read and read and read some more about how to make this work. So far, I can't even get MythTv backend to configure properly. I walk through all the menus, but when I try to leave by hitting escape from the main menu, I get:
 
Cannot create a file /home/media/dbbackups//.test - directory is not writable?
Cannot create a file /home/media/livetv//.test - directory is not writable?
 
Do you want to fix these problems?
 
If I choose yes, I end up back at the same menu screen. If I choose "No, I know what I am doing", it exits, but nothing works properly.
 
I tried running the Mythbuntu log grabber, and reviewing the output. I guessed that starting with the MythTV backend would be best. I get the following message:
 
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
 
Well that's a big help, thanks!
 
So, in frustration, I tried just dropping a regular DVD to see if I could at least have a little success with that. No, VLC player, Mplayer and MythTV all refuse to even play it. I Tried a different DVD, same results. This is the same drive I used to install Mythbuntu, so my guess is that it's installed and hooked up correctly.
 
Now that I've been stuck here for several days, and am beginning to think if I had just bought MCE I'd be done by now, does anybody have any suggestions?



Since posting the above, I've verified all the restricted codecs are installed, but I still can't get past the first screen on MythTV.  DVD playback does not work at all in MythTV, or VLC player, and plays as a scrambled mess in Mplayer. 

When I boot, the first place I end up is a configuration screen called Database Configuratin 1/2.  It asks for much stuff, but I don't have a database, haven't a clue how to create one, and can't get past this screen.

I tried changing the resolution on my desktop monitor from 1024x768 to 1280x1024.  That works, but when I try to save the X11 configuration file, I get an error message:

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'

I've noticed that this distribution locks the root account, so anything that must by run as root must be preceded by sudo, and usually my password must be entered.  Are all of these problems related to this?  It seems there's no reason that the nvidia xserver settings app. shouldn't be able to write to file, unless it's a permissions issue.  Do I have to be root to do any configuration or setup?  Shouldn't the nvidia tool run as root?

Is there some installation guide that covers these issues?  It seems like this is an awful lot of trouble to get nowhere.

---

### Post by yaroto98 on 2009-06-10
> Cannot create a file /home/media/dbbackups//.test - directory is not writable?
Cannot create a file /home/media/livetv//.test - directory is not writable?

sounds like your mounted media isn't mounted as read/write, just read. You may have to change your /etc/fstab

---

### Post by tgm4883 on 2009-06-10
It's a permissions problem.  Don't put your recording in your home directory, and the recording directory should be owned by mythtv:mythtv and have permissions of 774.

Putting it in the home directory is just asking for trouble. Either use the default at ```
/var/lib/mythtv/recordings
``` or what I use ```
/srv/mythtv/*hard drive name*/recordings
```

---

### Post by klc5555 on 2009-06-10
The problem is just what the error message says it is: mythtv can't write to the new directory you created "/home/media/"

When you created the directory structure and mount point "/home/media", its permissions were likely set to "root" (or possibly your username).  Mythtv expects the user "mythtv" to own the directory structure it writes to, which is how the default mythbuntu storage directory /var/lib/mythtv/recordings is set up, had you used it. So, in reassigning mythtv's storage directory as /home/media/, you can make it writable for "mythtv" by: 

sudo chown mythtv /home/media 
sudo chgrp mythtv /home/media
sudo chmod 775 /home/media

and you should be OK. 

Alternatively you can just make /home/media universally writable by changing its permissions to 777, but this is less to be recommended.

Having fixed the permissions in your default storage directory, you can go back into the backend setup and begin configuring your tuner card.

---

### Post by SiHa on 2009-06-10
First, if you're just dipping your toes in, so-to-speak, the best / safest thing is just to accept all the defaults (like storage directories!). When you've got it going, then you can start playing. You're going to install on fresh hardware anyway, so you can tweak when you do that.

> When I boot, the first place I end up is a configuration screen called Database Configuration 1/2
You will get this when the frontend can't find the backend server. I'm guessing it's because the IP address for the master backend server (in backend setup) is incorrect. As you have both FE & BE on the same machine, you can leave the IP as the default (127.0.0.1) for now. You will only need to change this if you intend to have a remote FE

One note, in the box where you can enter a PIN for the frontend (or something) you need to leave it at the default 0000 which confusingly is translated as 'no PIN' if you make it blank that'll cause problems.

As for the > Unable to create new X config backup file '/etc/X11/xorg.conf.backup'


I had this, and I'm fairly sure that:

1) If you run nvidia-settings from the menu, it should run with sufficient privileges to be able to write the X11.conf.
2) If you run from a terminal, you need to use sudo:```
sudo nvidia-settings
``` otherwise you will get the above error.

HTH

Simon

---

