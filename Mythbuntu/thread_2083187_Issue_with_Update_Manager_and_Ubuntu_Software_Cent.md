---
title: "Issue with Update Manager and Ubuntu Software Center hanging on new 12.04.01 install"
date: 2012-11-11
forum: Mythbuntu
---

### Post by GaryP2 on 2012-11-11
I just did a clean install of Mythbuntu 12.04.1 64-bit on and am having some issues with Update Manager (UM) and Ubuntu Software Center (SC) hanging at times. Everything else seems to be working well. Has anyone else seen this issue?
 
Right after the install I ran UM to update security and recommended updates. That went good. Then after a reboot in Mythbuntu Control Centre I enabled the both MythTV Updates (0.25) and Mythunbu Updates repositories and reran UM. I saw update manager download many MythTV updates including a couple Mythbuntu updates, but it hung before it said everything was installed. I eventually terminated the UM and it looks like I’ve got 0.25.3 when I check both from a command line (mythbackend –version) and in the history of SC.
 
I reformatted the system and have the same results as above when I tried the install a second time.
 
Now I’m seeing issues when installing software from the SC. When I try to install phpmyadmin, the progress bar goes about 80% then the install hangs. After a reboot it shows phpmyadmin installed but it isn’t configured. When I try to remove it, it hangs at about 50% progress mark.
 
It almost seems like these utilities hang at the point where the text window should be opening to run the post install, config, or removal scripts. The history tab in SC suggests the app is either installed or removed as desired, but in the case of phpmyadmin, it was never completed set up correctly until I had to do some manual things. Whenever UM and SC hang, I wait several minutes and there is no hard drive activity.
 
I was able to load gedit from the SC with no issue.
 
I’ve tried several things to resolve the issue, including issuing sudo rm /var/lib/apt/lists/* –vf and sudo apt-get update that was suggested elsewhere. I tried a few other things others suggested when having problems with UM and SC to no avail.
 
Has anyone else had issues like this with UM or SC? I’ve restored my database and recordings and MythTV seems to be working great on this new install (including mythfilldatabase, etc.) – just having issues with UM and SC.

---

### Post by nickrout on 2012-11-12
Try running your update/upgrade from the commandline as some packages require user input.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ibjsb4 on 2012-11-12
Seems to be a lot of software center/update manager problems these days.  Try synaptic package manager to see if problems still exist.

sudo apt-get install synaptic

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by GaryP2 on 2012-11-12
Thanks for the suggestions. Removing and installing phpmyadmin through apt-get remove / install seems to work just fine, so I’ll probably just do my updates through the CLI. I suspected it might have something to do with a user input or running some post-install script, etc., but in the case of installing phpmyadmin, it installed right away without any prompts through the CLI. 
 
I did find [this post]("http://ubuntuforums.org/showthread.php?t=2006419") from June which describes someone else’s similar experience.
 
I used Update Manager on 10.04 all the time and never ran into issues, and am just surprised that this isn’t tripping more people up.
 
I’ve read others suggesting Synaptic as well. Thanks again for the suggestions.

---

