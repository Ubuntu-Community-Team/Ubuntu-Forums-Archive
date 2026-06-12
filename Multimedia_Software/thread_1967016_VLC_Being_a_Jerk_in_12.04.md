---
title: "VLC Being a Jerk in 12.04"
date: 2012-04-27
forum: Multimedia Software
---

### Post by Katla on 2012-04-27
Just upgraded today, and found that my VLC didn't take the change too well. 

When I start a video, the sound is choppy and video takes a second or two to show up. After another couple of seconds the audio will fix itself. That is annoying, but I could live with it. However, if I pause the video, I cannot restart it. At all. No going back to the beginning, anything. It is just dead. Furthermore, when I close VLC, it disappears from view everywhere except for the taskbar, where it cannot be removed, no matter how many times I click "quit". I have to restart the system to clear it, and it takes a long time to shut down, with a distressingly long scroll or error messages that go by much too quick to read. 

I've looked around, and I've not seen anyone else reporting an issue like this, so I am assuming it is just me. I have no idea what to do. The only change I've made from when it was working was the upgrade to 12.04. I had to run a dpkg command during that as there was some issue with the installation, but everything seems to be working fine. Save for VLC.

I have no clue where to begin. Any assistance would be helpful. Thank you.

---

### Post by mc4man on 2012-04-27
You could try opening your home folder, view > show hidden files
Open  .config & delete the vlc folder & see if any change (will give you a fresh default vlcrc

Also maybe check in synaptic (if installed), search vlc, & see if  libvlccore4 is still installed, if so remove

---

### Post by Katla on 2012-04-27
libvlccore4 was not installed.

Deleting the VLC folder showed initial promise, as I was then able to pause and restart the video, but going to full screen it completely froze.

---

### Post by Curtis6767 on 2012-04-27
You might try this:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by garvinrick4 on 2012-04-27
```
sudo apt-get purge vlc
```
```
sudo apt-get install vlc
```

---

### Post by Katla on 2012-04-27
> **garvinrick4 said:**
> ```
sudo apt-get purge vlc
``````
sudo apt-get install vlc
```

That worked in that the icon is no longer stuck in the taskbar after I shut down the program, but all other issues remain. 

I also installed libdvdcss, to no effect.

---

### Post by mc4man on 2012-04-27
if it's just freezing in fullscreen you may want to post what video card/chip you have, what driver, ect.

You could try opening vlc from terminal with 
vlc -vv
Then cause the freeze & see if anything of interest in the terminal
Also right after freeze open ~/.xsession-errors, see if anything reported at the tail end or so.

---

### Post by garvinrick4 on 2012-04-27
Maybe clean cache so as to get a fresh vlc from repo's. One at a time below.
sudo apt-get clean
sudo apt-get purge vlc
sudo apt-get install vlc

Worked in 11.10 I gather so upgrade is problem? So fresh one from precise repos just might do it.

---

### Post by mobisallen on 2012-04-28
its a fact that some times when u upgrade any software due to human error or internet connection error such things happens . there is any file which is being disturbed or corrupted due to up gradation. so if u just uninstall the vlc and reinstall it and then at that time again upgrade it . it can b helpful, because if u will try to check the files any more it can create more problems

---

### Post by Katla on 2012-04-28
> if it's just freezing in fullscreen you may want to post what video card/chip you have, what driver, ect.

You could try opening vlc from terminal with 
vlc -vv
Then cause the freeze & see if anything of interest in the terminal
Also right after freeze open ~/.xsession-errors, see if anything reported at the tail end or so. 	

I'm using the onboard card of a Gigabyte S-series. Ubuntu tells me the graphics are "Gallium 0.4 on llvmpipe (LLVM 0x300)". 

I kept on eye on the terminal after I'd opened VLC. Nothing really jumped out at me. A lot of messages about how the video timing might be late, but that looked pretty normal. Even when it froze on me, I got no errors. The terminal just reported in earnest whatever was supposed to be happening but wasn't. I think he's in on it. 

Here's the relevant(?) part of the xsession log, with a little bit after for context. 

> 0x4600002 (The Simpso) without a timestamp!  This means some buggy (outdated) application is on the loose!
Window manager warning: Tried to ping a window with CurrentTime! Not allowed.
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1879036094") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1879036094") 


I'm now wondering how corrupted my install of the upgrade was. 

I'd brought up how it takes a while for the computer to shutdown on restart, and that just before it goes out I get a long, fast scroll of errors (may just be one repeating, as they all look alike - I dunno, goes by too quick to read). Then this morning I had to boot my system 3 times before Ubuntu took hold.

Since VLC was working fine prior to me upgrading to 12.04, and I've not seen anyone else reporting a similar issue, I've got to think that I've got a bad install of Pangolin. 

The question now becomes, how do I fix that?

---

### Post by Katla on 2012-05-02
As a bump, I've got an ATI RS690 card (Radeon x1200). In looking around, I don't think I want the Gallium 0.4 drivers for that, but have no idea how to change them. 

What clued me in was that I was unable to change brightness/contrast on the default Ubuntu movie player tonight. That might help with the VLC problem a bit, though I am still worried about the overall install and errors, as well as the nervous reboot.

---

### Post by Katla on 2012-05-02
I ran a "dmesg | grep drm" command in the terminal and got a long string of stuff back, including a repeating error. 

I've looked around at driver issues, but nothing is telling me what I need to know (or, if it is, it is too cryptic for me). To wit, I need to find out how to reload ATI drivers.

---

### Post by jmore9 on 2012-05-02
I had a problem with ver 2 of vlc that's in the repos upon upgrade.  I jsut went back 1 ver and evrything works fine now, maybe that helps some.

---

### Post by wolfen69 on 2012-05-02
Just back up and do a clean install.

---

### Post by Katla on 2012-05-03
I'm unclear on how to go about doing a clean install. I've got Natty 11.04 on a flash drive that I've been tempted to use again, or even just re-do 12.04, but I don't know where to find it. 

And by back-up, does that entail moving all of my files to another drive?

---

### Post by skeltonh on 2012-05-03
You could try:

sudo add-apt-repository ppa:n-muench/vlc
sudo apt-get update
sudo apt-get purge vlc
sudo apt-get install vlc

Another problem I found (with corrupted install) is that some instances of Ubuntu does not run a swap device. Usually when you encrypt your home directory at install.  Check to see if your swap drive is online. 

swapon -s

This should show you your swap device and other info.  If it is not there you will have to format your swap device then mount it manually.  Change your /etc/fstab to reflect the device so that it is mounted on reboot.

If you have a corrupted install, you may have to reinstall or perform a number of 'sudo apt-get upgrade' and 'sudo apt-get dist-upgrade' to fix your problem.

---

### Post by RJARRRPCGP on 2012-05-03
For me, it started refusing to enable the swap automatically after I deleted the swap partition and increased the swap partition size.

It's a known Debian-related issue where changing the swap partition size post-installation results in the OS refusing to enable the swap automatically.

I always had to do **swapon /dev/sda2** after any reboot!

Confirmed to occur with Squeeze.

---

### Post by Katla on 2012-05-04
> **skeltonh said:**
> You could try:

sudo add-apt-repository ppa:n-muench/vlc
sudo apt-get update
sudo apt-get purge vlc
sudo apt-get install vlc

Another problem I found (with corrupted install) is that some instances of Ubuntu does not run a swap device. Usually when you encrypt your home directory at install.  Check to see if your swap drive is online. 

swapon -s

This should show you your swap device and other info.  If it is not there you will have to format your swap device then mount it manually.  Change your /etc/fstab to reflect the device so that it is mounted on reboot.

If you have a corrupted install, you may have to reinstall or perform a number of 'sudo apt-get upgrade' and 'sudo apt-get dist-upgrade' to fix your problem.

My swap drive appears to be in order.

Tried the VLC commands. Problem persists. It seems to work fine now until I switch to fullscreen. 

Running the sudo apt-get upgrade did some stuff, but I'm too nervous to reboot to see if it fixed anything.

---

### Post by md2020 on 2012-10-31
I realize that this thread may be a bit dated but since I found it when trying to resolve my own issue I thought I would post what worked for me so that any others that may stumble upon this can possibly benefit.

I too was having trouble with VLC freezing when going fullscreen in Ubuntu 12.04. Audio was still working fine and I could move the mouse around but the screen was frozen and I couldn't do anything. 

For what it is worth my video card is a Nvidia GEForce 8300GS and I am using the most current restricted (nvidia) driver.

I tried a couple of settings for VLC that I had seen in other forums/posts but those did not work for me. Here is what worked for me:

Running Ubuntu 12.04 (Unity) in 2D mode instead of 3D mode.

Now VLC plays video files fullscreen without issue. I was not really concerned with losing the 3D features since playing video files was the main purpose for this machine.

You select 2D mode on the Ubuntu login screen by clicking on the icon in  the upper right corner of the password entry window/box.
In there you can select "Ubuntu 2D". Subsequent system boots will then use 2D mode until changed. (unless you have altered something to prevent this)

---

### Post by aheiba on 2013-05-23
I guess this helps.
Open vlc, go to Tools > Preferences > Video > Output, change the Default to X11, save and restart vlc.
Thanks to timendum
[http://askubuntu.com/questions/25745/vlc-will-sometimes-have-issues-displaying-video-in-fullscreen?rq=1](http://askubuntu.com/questions/25745/vlc-will-sometimes-have-issues-displaying-video-in-fullscreen?rq=1)

---

### Post by csushma24 on 2013-08-06
> **aheiba said:**
> I guess this helps.
Open vlc, go to Tools > Preferences > Video > Output, change the Default to X11, save and restart vlc.
Thanks to timendum
[http://askubuntu.com/questions/25745/vlc-will-sometimes-have-issues-displaying-video-in-fullscreen?rq=1](http://askubuntu.com/questions/25745/vlc-will-sometimes-have-issues-displaying-video-in-fullscreen?rq=1)

I had a similar problem as katla!
But this actually solved the problem, thanks!

---

