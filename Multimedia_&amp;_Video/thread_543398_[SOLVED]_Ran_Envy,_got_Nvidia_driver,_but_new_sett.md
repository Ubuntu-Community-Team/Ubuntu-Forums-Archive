---
title: "[SOLVED] Ran Envy, got Nvidia driver, but new settings won't stay applied between boo"
date: 2007-09-05
forum: Multimedia &amp; Video
---

### Post by Phrawm48 on 2007-09-05
For Feisty Fawn / 7.04  (installed two days ago after about six months of experience with Dapper / 6.04...)

I successfully downloaded, installed, and ran the Envy 0.9.7 script described in multiple graphics adaptor related threads (including the two threads I cite in this post).  I then used "Applications > System Tools > Nvidia Settings" to set my Nvidia GeForce FX5500 to 1280x1024.

The result is beautiful when it's applied BUT -- the settings don't stay applied between boots.  I'm obliged to rerun the Nvidia Settings after each restart  to reapply the new screen resolution.

I've tried and failed to find the answer to my question in either of these two "primary" threads as well as a few others:

[http://ubuntuforums.org/showthread.php?t=432056](http://ubuntuforums.org/showthread.php?t=432056)

[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)

I'll add a couple of bits of supplementary info.

I first tried using the "sudo nvidia-glx-config enable" command.  It screwed up my xorg.conf file so bad that I was compelled to use terminal mode to revert to the backup xorg.conf and reboot.  So at least for me, "sudo nvidia-glx-config enable" seriously broke my computer; I uninstalled it and am now afraid of it.

The second problem I had was that I had to modify the Nvidia Settings' launcher by prefacing the command with "gksudo".  If I didn't do that I received the message 'Unable to create new X config backup file '/etc/X11/xorg.conf.backup'." when I tried to save my changes.

After using sudo when starting the Nvidia tool, I could use the tool to overwrite xorg.conf.  But the 1280x1024 setting doesn't stay applied between boots.   I've attached my current xorg.conf to this thread as a compressed archive, " [imperfect_xorg.conf.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=42613&stc=1&d=1188973270")".

Can someone please help me sort this out?  Ideally I'd really rather just have a simple screen resolution that always came up  1280x1024 and not even be bothered with the "rickety", version-dependent Nvidia driver.

Cheers & thanks much,
Ric
SFO

(P.S.  I wonder if Linux will ever get past the need to experimentally hand edit  xorg.conf to configure displays and pointing devices.  This forum has post after post after post by one reasonably intelligent person after another who is struggling with it...)

---

### Post by RomeReactor on 2007-09-05
Hi. Try this: let's make a backup of your xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
then, edit your current xorg.conf:
```
gksudo gedit /etc/X11/xorg.conf
```
scroll down to **Section "Screen"**, then just below, to the **SubSection     "Display"**, you have this line:
```
Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
```
try deleting the first resolution, so that it reads:
```
Modes      "1280x1024" "1024x768" "800x600" "640x480"
```
save the file, close gedit, and restart the X server by pressing CTRL+ALT+BACKSPACE. (or just reboot). See if you can now make the 1280x1024 resolution stick between reboots.

If this doesn't work, or you're dumped to the command line after rebooting, revert the backup xorg:
```
sudo cp /etc/X11/xor.conf.backup /etc/X11/xorg.conf
```
and
```
sudo reboot
```

---

### Post by Phrawm48 on 2007-09-05
Thanks much!

*try deleting the first resolution, so that it reads...* did indeed work, at least through one restart...

Cheers & thanks 'gain,
Ric
SFO

---

