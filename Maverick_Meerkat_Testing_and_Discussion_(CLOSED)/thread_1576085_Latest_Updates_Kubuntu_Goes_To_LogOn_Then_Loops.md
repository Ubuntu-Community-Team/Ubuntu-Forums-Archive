---
title: "Latest Updates Kubuntu Goes To LogOn Then Loops"
date: 2010-09-16
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by zenarcher on 2010-09-16
I just installed the latest updates, which included a kernel update and xserver update on Kubuntu 10.10 Beta (64 bit).  I'm using Nvidia graphics.

Following the update, after rebooting, I get to the Logon screen (although I have everything set to autologon).  I enter the username and password, the splash screen starts to come up, then takes me back to the logon screen again.

I uninstalled the proprietary Nvidia driver, after starting with the previous kernel, then rebooted and now cannot start with either the new or the old kernel.

I'm getting an error message something to the effect that the xorg server is already running.

This is the second time I've had this problem recently.  Last time I did a fresh reinstall, but there must be an easier way to fix the problem.  I have tried the recovery mode, opting for low graphics, however that does not work either.

Could anyone explain to me exactly how I might be able to get my system back?  I've read some posts on a similar problem, but nothing which has worked for me, or that I understand.

Any help would be appreciated.

Regards,
zenarcher

---

### Post by xebian on 2010-09-16
Just reinstalled nvidia drivers fixed it for me.

---

### Post by zenarcher on 2010-09-16
That's good to know, but I'm not sure how to reinstall the Nvidia driver, since I can only get to a terminal.  Could you help me with that?

Thanks,
zenarcher

---

### Post by xebian on 2010-09-16
> **zenarcher said:**
> That's good to know, but I'm not sure how to reinstall the Nvidia driver, since I can only get to a terminal.  Could you help me with that?

Thanks,
zenarcher

I only use the drivers from Nvidia.  So if you use the same, go to the directory where it's located.  Then sudo sh NVIDIA-lin...nnn.nn.nn.run and just answer/follow the prompts.

If you use the one from the repo, just sudo aptitude reinstall <pkg-name>

---

### Post by zenarcher on 2010-09-16
I use the one from the repo....thanks, I'll give that a try and post back.

Cheers,
zenarcher

---

### Post by zenarcher on 2010-09-16
Reinstalled nvidia-current but no luck.  I'm still in the same situation.  Recently, it seems, since the free Nvidia driver became the default, this has become a fairly common occurrence when I get an Nvidia and xorg update.

Not sure what to try next, or if to do a fresh install again.

Cheers,
zenarcher

---

### Post by cariboo on 2010-09-16
If all you did was install the drivers, try:

```
sudo nvidia-xconfig
```

at the prompt, then type:

```
startx
```

---

### Post by cwraig on 2010-09-16
I also have the same problem but i cannot find out which driver i was using because i cannot find my xorg.conf file anymore.

Any advice would be greatly appreciated. 

Has anyone filed a launchpad bug for this? I had a bit of a look around but couldn't find much.

---

### Post by zenarcher on 2010-09-16
Well, it's something beyond just the update, I'm guessing.  I went ahead and did a fresh install of Beta.  Everything was fine.  I then installed all the available updates, but did not install the Nvidia driver from the repo and rebooted.  When I rebooted, I had the same endless loop, before I even installed the Nvidia driver.  

Then, I rebooted again and from the command line, installed the Nvidia driver from the repo....nvidia-current....and rebooted again.  This time, I ended up with the Nvidia driver working so I could get my desktop back up, but I everything was huge...640x480....something like that, on my 21 inch widescreen.  I then uninstalled the Nvidia driver from Additional Drivers and reinstalled it from the same place without rebooting after doing the uninstall.  Then, finally rebooting one more time and have everything as it should be.

Not sure what it is, but it sure makes a mess.

Cheers,
zenarcher

---

### Post by cwraig on 2010-09-16
I just...

Plugged in my laptop into wired network
Booted into recovery mode and selected netroot
Ran "apt-get install nvidia-current"
After that finished i ran "init 6" to reboot.

KDE now logs in but with a very low resolution (800x600) and when i open the nvidia control panel it tells me that i'm not running the nvidia driver. 

I opened a terminal and ran "sudo nvidia-xconfig" 
and rebooted. 

Everything now seems to be back to normal. 

Note; I have an Nvidia 8600m (256)
      From the apt-get of the nvidia-current package I was not running the binary blob nvidia driver prior to the crash loop. 

Hope this can help someone else.

---

### Post by zenarcher on 2010-09-17
> **cwraig said:**
> I just...

Plugged in my laptop into wired network
Booted into recovery mode and selected netroot
Ran "apt-get install nvidia-current"
After that finished i ran "init 6" to reboot.

KDE now logs in but with a very low resolution (800x600) and when i open the nvidia control panel it tells me that i'm not running the nvidia driver. 

I opened a terminal and ran "sudo nvidia-xconfig" 
and rebooted. 

Everything now seems to be back to normal. 

Note; I have an Nvidia 8600m (256)
      From the apt-get of the nvidia-current package I was not running the binary blob nvidia driver prior to the crash loop. 

Hope this can help someone else.

That is pretty much the same thing that happened to me, even after doing a clean new install.  It appears some Ubuntu users have been getting the same situation, according to a couple of other posts.  Thanks for explaining what you did.  I have three more machines to update and I don't want to have to do fresh installs on each of them.  Really appreciated!

Cheers,
zenarcher

---

### Post by zenarcher on 2010-09-19
Well, I saw a bug for kdm fixed this morning, which appeared to be what I've been experiencing.  Did the updates and my other machines rebooted just fine.  No looping to the logon screen, so I'd say it's fixed.

Cheers,
zenarcher

---

