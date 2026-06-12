---
title: "ubuntu natty upgrade (possibly) doesnt have unity"
date: 2011-04-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kingbirdy on 2011-04-02
I just upgraded to natty, and I still have Gnome as best as I can tell, however, things like compiz aren't working, so I'm not entirely sure. and there appears to be no visual difference, though that doesn't necessarily mean much. And in the System menu, it still has "about GNOME" there. So did unity not install, or do I need to change something to use it, or is it there and I'm just crazy?

---

### Post by SuperDrive on 2011-04-02
You need to have a 3D driver installed, otherwise ubuntu will load under default gnome

---

### Post by kingbirdy on 2011-04-02
> **SuperDrive said:**
> You need to have a 3D driver installed, otherwise ubuntu will load under default gnome
the driver manager thing says I have my required driver, and the description for it says it is 3D accelerated. so I believe I already have it.

---

### Post by SuperDrive on 2011-04-02
if you already have the restricted 3d driver installed, then make sure u use the right desktop at login. Here is a c/p

There are now three session types available in GDM:
Ubuntu: it runs Unity. It requires 3D driver support. 
Ubuntu Classic: it runs GNOME with gnome-panel. It supports all video hardware and video drivers. 
Ubuntu Classic (No Effects): it runs GNOME with gnome-panel. It is in 2D mode only.

Usually unity loads by default after installing the 3d driver and restarting the PC

---

### Post by kingbirdy on 2011-04-02
I know that. I installed the whole thing in the install manager, then restarted, and I've since shutdown and gotten back on a few times. are there any differences you could tell me to help me figure out whether or not it is running?

---

### Post by Quackers on 2011-04-02
Open a terminal and run
```
compiz --replace
``` and see if any error messages are reported - not to mention see if Unity runs :-)

---

### Post by kingbirdy on 2011-04-02
well almost everything is the same, but now I dont have any top bar to firefox (page titles, close, etc.) when it is maximised, and my workspace indicator went from a line of workspaces to a little box or them. also bits and pieces of my screen keep going dark, like whatever line of text is above the one I'm typing, and the control bar (is that what its called? the bar at the very top of ubuntu), the favicon for my webpage, if I highlight something, or really anytime I do anything. In terminal, its not finished, however. its working on the fullscreen visual bell.

EDIT: and in the terminal, it said several things failed, so I guess that might count as errors.

---

### Post by kingbirdy on 2011-04-02
Oh, and sorry about double post, but now my screen blacks out if I scroll and only reappears every 6th scroll or so. same if I use arrow keys. I cant see the screen enough to edit, so I had to post again. please help with this. its horribly frustrating.

EDIT: okay, it got to the point where I couldnt do anything, so I rebooted. its doesnt do the black screens anymore.

---

### Post by Dutch70 on 2011-04-02
I don't know about the 3D thing with unity, but you can install Unity 2D from software center. Have a look at this thread, toward the end.
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1679321[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1679321")

---

### Post by kingbirdy on 2011-04-02
I tried that. It doesnt work.

---

### Post by Dutch70 on 2011-04-02
> **kingbirdy said:**
> I tried that. It doesnt work.

:confused: What doesn't work? As you can see in the thumbnail on page-2, it's in software center. I just added it about the time I added that thumbnail.

Are you saying software center isn't working???

---

### Post by ranch hand on 2011-04-02
> **kingbirdy said:**
> I tried that. It doesnt work.
For what it is worth and from what I read Unity 3D seems to be working as it is supposed to (a lot of effort for a worthless result) on my box.  Unity 2D still does not work.

I can, for instance, get the dash to come up (I assume this is a reference to a "dash board" a device originally used in buggies to keep mud and horse manuar from hitting you in the face) but at that point everything freezes to the extent that only unplugiing my box will get me out.

And no, I am not wasting my time and energy  filing bugs on a package that has been stated to be great.

---

### Post by cor2y on 2011-04-02
Heres what i have discovered, upgrading or doing a clean install where you have your /home partition intact borks natty unity 3D.

I have verified this on three pcs all using supported nvidia gpu for both nouveau and the closed binary, one desktop and a notebook with 10.10 already installed where i did 1 distro upgrade and one install via cd keeping the /home partition untouched, whatever hidden settings in /home borked the unity 3D even with the 3D drivers installed i was able to get both ubuntu classic and unity 2D to run but unity 3D required always launcher shortcut on the desktop and any changes made to compiz crashed unity, every login to the regular default ubuntu session i have to use that launcher to invoke unity, putting it in startup programs didnt seem to work.

The other desktop that got a truly clean install aka no previous version of linux on it Unity 3D worked flawlessly (this time i used the experimental nouveau 3D drivers), so i expect if this problem is still around when 11.04 final is released expect a lot of help questions on irc and on the forums.

---

### Post by PaulW2U on 2011-04-03
> **cor2y said:**
> Heres what i have discovered, upgrading or doing a clean install where you have your /home partition intact borks natty unity 3D.
Yes, I found that too. Unity's general stability was being reported here to be far better than I was finding it to be at the time. I used ccsm and toggled most of the settings on and off for several minutes. Unity soon started working properly so I assume any bad settings that were causing crashes and various features not to work were being over-written and corrected.

A later complete re-installation onto a newly formatted and re-partitioned drive has given me a very stable Unity especially after the last update.

---

### Post by sygin on 2011-04-03
Hi,

Just had the same problem. 

Solution:

1. Install compizconfig-settings-manager
sudo apt-get install compizconfig-settings-manager

2. Launch compizconfig-settings-manager
ccsm

3. Select Preferences from the left pane.

4. Select the "Default" profile and wait a while (desktop will freeze for a minute or so).

5. Select the "Unity" profile and wait a while (desktop will freeze for a minute or so).

6. Logout and log back in.

Cheers,
Sygin

---

### Post by kingbirdy on 2011-04-03
> **PaulW2U said:**
> A later complete re-installation onto a newly formatted and re-partitioned drive has given me a very stable Unity especially after the last update.
thats what I'd like to do, but I also have windows 7 installed, and I'd like to keep it. anyway to just remove ubuntu?

---

### Post by sdowney717 on 2011-04-03
sure, reinstall natty and tell it to wipe the ubuntu partition only.

OR just boot win 7, goto win 7 disk tools and delete the unrecognized healthy ubuntu partition
then reinstall ubuntu on the new empty partition

---

### Post by kingbirdy on 2011-04-03
> **sdowney717 said:**
> sure, reinstall natty and tell it to wipe the ubuntu partition only.

OR just boot win 7, goto win 7 disk tools and delete the unrecognized healthy ubuntu partition
then reinstall ubuntu on the new empty partition
okay, I'll probably do a reinstall when I get home to a good internet connection and can download the image. and as a sidenote, doesnt doing the disktools thing remove grub and screw you over unless you have the windows disk?

---

### Post by ranch hand on 2011-04-03
> **kingbirdy said:**
> okay, I'll probably do a reinstall when I get home to a good internet connection and can download the image. and as a sidenote, doesnt doing the disktools thing remove grub and screw you over unless you have the windows disk?
If you are booting with grub and remove the OS that supplies the grub files you will be screwed.

---

### Post by sdowney717 on 2011-04-05
perhaps yes BUT
you said your going to REINSTALL ubuntu and that will restore grub and then windows will boot again.

So if you delete ubuntu partition
then boot ubuntu CDROM and install your good again with a fresh ubuntu install and windows 7 will boot because grub is installed during ubuntu install.

---

