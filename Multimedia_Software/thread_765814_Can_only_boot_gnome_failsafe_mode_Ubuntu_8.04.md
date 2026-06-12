---
title: "Can only boot gnome failsafe mode Ubuntu 8.04"
date: 2008-04-24
forum: Multimedia Software
---

### Post by lyndaj70 on 2008-04-24
Hi!

I upgraded to Ubuntu 8.04 and when I went to login the screen would first go brown with the cursor still visible.  After some hard disk activity, the screen would go black and the login screen would reappear.

Thought it was something that went wrong with the upgrade from 7.10, so I wiped and ran a clean install.  Same problem.

I can access the live cd and my desktop if I choose failsafe gnome as my session, but cannot login to regular gnome.  I have checked my logs and I discovered this in /var/log/daemon.log:
```
Apr 24 19:52:01 monster gdm[5537]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
```

Failsafe gnome just starts gnome without running scripts.  I am wondering where I can access the scripts to turn them off one by one to troubleshoot the error.

I have this same distro on my laptop.  Both are running ATI video, but the laptop has an Intel chipset (celeron) and I have no problems despite numerous reboots to test.  My desktop is an AMD Sempron, a 64-bit processor and I receive the same error every time I reboot, even after wiping and installing the 64-bit version.  

Also, my video is reporting "out of range" while booting, which I had in Gutsy but fixed with startupmanager but I guess it hasn't been ported to Hardy yet.

Any ideas?

Thanks in advance, 
Lynda

---

### Post by cms2337 on 2008-04-24
*bump*

I'm having the same exact problem.

---

### Post by blueyll on 2008-04-25
me too!****

---

### Post by orre64 on 2008-04-25
Same here!

---

### Post by Canadaboy on 2008-04-25
same here...

---

### Post by brpaolo on 2008-04-26
> **lyndaj70 said:**
> 
Failsafe gnome just starts gnome without running scripts.  I am wondering where I can access the scripts to turn them off one by one to troubleshoot the error.


Hello, I have the same problem (on a Dell Inspiron laptop ATI Radeon X300 video), ... and the same question!

For the moment I am working using failsafe mode.

---

### Post by Onderstekop on 2008-04-26
I am also having this problem and I'm also trying to find the scripts.
I found this so far:

In ~/.gnome2/ there could be a file named .session. If not, gdm will load the default session from /etc/gdm/Init (and PostLogin and Presession). More information can be found here: [http://library.gnome.org/admin/gdm/stable/configuration.html.en](http://library.gnome.org/admin/gdm/stable/configuration.html.en) 

/etc/gdm also holds the failsafe scripts. 

If I use fglrxinfo in a non failsafe session it will output SGI and mesa drivers. In failsafe it will output ATI drivers. I'm not sure if this is the same for everybody here (please try), but it could be a clue for what to look for.

Hope this helps.

---

### Post by Onderstekop on 2008-04-26
Today I installed KDE to see if this would help, but it didn't and I think the problem lies in the new xorg. I got some xorg.conf hacking to do tonight.

---

### Post by lyndaj70 on 2008-04-26
> **Onderstekop said:**
> Today I installed KDE to see if this would help, but it didn't and I think the problem lies in the new xorg. I got some xorg.conf hacking to do tonight.


(possible dumb question) If the problem is in xorg, would it not effect all of the window managers?  I can log into failsafe gnome, and when I (eh-hem "oops") accidentally deleted the gnome desktop manager it booted me into x-windows without a problem.  From what I understand (and I am far from expert) if it was in xorg that would affect ALL of the video and we wouldn't be able to login to any of the window managers.  Am I off-track on the logic?

---

### Post by cor2y on 2008-04-26
If it is xorg try the failsafe/recovery kernel and reconfigure x and then do a normal boot.

---

### Post by lyndaj70 on 2008-04-26
> **cor2y said:**
> If it is xorg try the failsafe/recovery kernel and reconfigure x and then do a normal boot.


I reconfigured xorg without success.. Still have to use failsafe gnome.  Thanks, though.

---

### Post by Onderstekop on 2008-04-27
> **lyndaj70 said:**
> I reconfigured xorg without success.. Still have to use failsafe gnome.  Thanks, though.

It worked for me.

---

### Post by lyndaj70 on 2008-04-27
> **Onderstekop said:**
> It worked for me.
What settings did you use?  I'm willing to give it another shot....

---

### Post by abds on 2008-04-27
Try installing restricted drivers if there are any. I was having the same problem, but it went away installing the restricted ATI drivers.

---

### Post by lyndaj70 on 2008-04-27
Well, I have to mark this thread as solved... Apparently it was a driver issue...

I took your advice and reconfigured xorg, but the problem still remained.  I took it back down to 7.10 then ran an upgrade hoping that it would pick up on the settings in the previous install that worked.  Ended up making things worse and for a bit had 800X600 resolution, though I "could" boot into Gnome.

So in frustration I wiped again, and upon first boot as usual it said I could use restricted drivers.  As I had tried it both ways without success, I just clicked enable driver.  It downloaded a file, installed, and asked to reboot.  THIS TIME however, I was able to login successfully, and for the first time ever on this computer, I actually have desktop effects!  It also displayed a message that in order for my computer to run properly, it "had" to use restricted drivers....I'm not sure I actually did anything to fix it, but I believe somehow that it was the driver, and Ubuntu fixed it this time.

Thank you so much for your help!  I'm going to go play with these effects now....  :guitar:

---

### Post by brpaolo on 2008-04-28
For me
 sudo apt-get remove xserver-xgl
has done the trick (sort of). 

See 
[https://bugs.launchpad.net/ubuntu/+source/displayconfig-gtk/+bug/221764](https://bugs.launchpad.net/ubuntu/+source/displayconfig-gtk/+bug/221764)

---

### Post by etienne@Rofti on 2010-02-04
I'm having a very similar problem. I am using Karmic, and I cannot log into a Gnome, or an XTerm session, only Gnome-Failsafe.

I started a thread but no-one has replied yet:
[http://www.uluga.ubuntuforums.org/showthread.php?p=8689533](http://www.uluga.ubuntuforums.org/showthread.php?p=8689533)

Any help would be greatly appreciated!

---

