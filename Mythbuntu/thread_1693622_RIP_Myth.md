---
title: "RIP Myth"
date: 2011-02-23
forum: Mythbuntu
---

### Post by winewood on 2011-02-23
Let me start by saying, I know just enough Linux to be dangerous...  
I attempted to update my 10.4 to 10.10.
 
what a mistake!
 
I had previously only run security updates.   In preparation to my big update, I ran all software updates and made a backup via tar.
 
I then ran my "sudo update-manager -d", and proceeded to "update"
 
This ran for an hour, then I ended up on a black screen that wanted my 
mythtv login: 
 
wierd.. autologin usually put that in.
 
when it booted, it said it was running kernel 2.6.32-21-generic.  I was confused.  I understood the latest kernel sources were 35 somthing...
when I attempted to compile my Nvidia drivers manually, it said it couldnt find the kernel source.  I looked and although a uname -r stated = 2.6.32-21-generic , the src was gone??
The newer kernel was there, but wasnt running.  (my first install had a grub menu when booting, but now I do not see it, and do not understand how to run newer kernels)  
 
SO!.. being 3:30 AM, I went to my tar backup and proceeded to un-tar it back into place to fix it!...
 
OMG..    that broke more things.
 
Question is..  whats the next step?    I have my old shows, and my database backup.   anyone??
 
Sad Panda  <---

---

### Post by newlinux on 2011-02-23
Clean reinstall, restore backup and setup storage group with your old shows. That's my suggestion.

---

### Post by rhpot1991 on 2011-02-23
I'd grab your DB backup and shows, then reinstall everything.

---

### Post by tgm4883 on 2011-02-23
> **winewood said:**
> Let me start by saying, I know just enough Linux to be dangerous...  


That's not usually a good start.

> **winewood said:**
> 
I attempted to update my 10.4 to 10.10.


Great! Although I usually don't try to fix something that isn't broke.

> **winewood said:**
> 
what a mistake!


Oh noes, what happened?

> **winewood said:**
> 
I had previously only run security updates.   In preparation to my big update, I ran all software updates and made a backup via tar.


That's a good idea to make sure everything is up to date before upgrading the distro.

> **winewood said:**
> 
I then ran my "sudo update-manager -d", and proceeded to "update"


That's a good wa....... Wait wait wait, you ran that command to update to 10.10!?! You weren't kidding when you said "I know just enough Linux to be dangerous... ". No doubt you found that command in some forum right? I urge you to verify what the commands do before you run them. Let me explain exactly where you went wrong.

```
thomas@earth:~$ update-manager --help
Usage: update-manager [options]

Options:
  -h, --help            show this help message and exit
  -V, --version         Show version and exit
  --data-dir=DATA_DIR   Directory that contains the data files
  -c, --check-dist-upgrades
                        Check if a new Ubuntu release is available
[B]  -d, --devel-release   Check if upgrading to the latest devel release is
                        possible[/B]
  -p, --proposed        Upgrade using the latest proposed version of the
                        release upgrader
  --no-focus-on-map     Do not focus on map when starting
  --dist-upgrade        Try to run a dist-upgrade
  -s, --sandbox         Test upgrade with a sandbox aufs overlay
thomas@earth:~$ 

```

You upgraded to the latest development release, which is 11.04 and currently an alpha.

---

### Post by winewood on 2011-02-23
thanks for your suggestions guys!
 
I think I will indeed do a re-install, then copy my old shows and DB back.
>  
You upgraded to the latest development release, which is 11.04 and currently an alpha. 

Actually I was mistaken, it was C and not D. The button stated via the gui that it was 10.10, so I am sure it was not the alpha. I was going off memory at 4AM in the morning :D
 
I do find it wierd that a re-install would break things so bad. Why would the auto login break after an upgrade? Why would my kernel be "upgraded" but uname -r show an older one... then when trying to recompile drivers with kernel, say the info was removed... crazy stuff!
 
HAHA! I take it back. I knew this would break it in my gut, but in the end it always gets fixed, and I enjoy the ride. If it never broke, I wouldn't learn.
 
As for why I did it? I was getting random and buggy errors, that were just annoying enough to install the latest. I had asked about the random errors, and they had not been reported by anyone else. In a way.. "I was trying to fix it".

---

### Post by rhpot1991 on 2011-02-23
The old Kernels are always left around, so that makes sense that you could have somehow booted into the old one.  Perhaps you have Grub installed on more than one hard drive and the wrong one got updated?

In the end it doesn't really matter, you untaring the backup over the current system most likely broke a lot of things, so you should just do a fresh install at this point.

---

### Post by winewood on 2011-02-23
I found out that a backup drive I had was in the system.  Although it wasnt the primary boot, it was prob the recipient of a new kernel :/

---

### Post by winewood on 2011-02-23
There is hope!
When I boot it asks me for a user on a black screen.
 
I figured.. if its loading the wrong kernel, then just install grub and update it.
 
I did so, and now I am booting with the latest kernel 2.6.35.-25-generic and I was able to compile my nvidia driver against it and get into "gdm start".
 
This should be totally recoverable!  I see my front end, and my backend, but wierd thing is, my network driver is not loaded.  In fact none of the services are starting.  
 
Is there a command to start the normal run-level that seems to be stuck on the lowest?  Why is it not?   I may need some real help... anyone?
 
I am FINE with re-installing, but I remember it asking me about partitions.. and I am not wanting to loose my 2TB of shows and all the apache2 modifications and permissions that I spent months on.   
 
Im sure I am missing something simple.  Anyone?

---

### Post by winewood on 2011-02-23
well.. for some strange reason.. after getting into the GDM desktop and opening up all the auto-startup options and closing them, the install process for myth begins.
 
I am not about to guess why or what. Just saving someone some typing if your responding. thanks!
 
update:  I now can get in.
However the configure new install starts.. im assuming 10.10.. but it cannot connect to the database using the old password.  I have no idea why??  Should i re-install mysql and try to rebuild the db?   The db isnt starting. :/ 
 
It looks like I will have to remove mythtv and whatever it was doing, and manually reinstall.  I would do a livecd install, but I do not want it re-partitioning junk and loosing my 2TB of TV shows.

---

### Post by winewood on 2011-02-24
Its almost back!
 
I had to remove mysql 5.1 and reinstall (2 commands and poof!)
 
[COLOR=#000000][FONT=Verdana]apt-get --purge remove mysql-server-5.1 [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]apt-get --reinstall install mysql-server-5.1[/FONT][/COLOR]
 
I was able to reset my root password which was nice.
 
Then the backend and front end were able to talk to each other and my database information was intact and happy!
 
Apache2 is broke now, but im sure that is just a simple fix away as I have the tar backups to pull from.

---

### Post by winewood on 2011-02-25
A re-install of apache, then a restore of the files from tar and I am off to the races.  I had 3 different sites running off my apache, so I feared a total redo.  My wife was gonna be TICKED if I lost her shows.  
 
All good!  While I was at it, I put in a new video card, and replaced my power supply fan with a silent one.  A bearing went out on the old one, and it was a freight train!
 
The failure that started this really wasn't forseable, but I think the best was made of it.

---

### Post by winewood on 2011-02-25
DOH!
 
After reboot, mysql isnt running.  Sadly.. (im ashamed to say this), the only way I know to get it running is to re-install...
 
Any ideas on how to get it auto starting? I see it in /etc/init.d/mysql and it "should" be starting, but im not seing why its not starting.
 
Suggestions?

---

