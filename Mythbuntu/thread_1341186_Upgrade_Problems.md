---
title: "Upgrade Problems"
date: 2009-11-29
forum: Mythbuntu
---

### Post by ian dobson on 2009-11-29
Hi All,

OK I upgraded my dedicated backend and my Frontend to 9.10 this weekend and here's what I found/problems I've had and solutions:-

1) I had to manually edit the videosources table and delete the configpath field before the database upgrade would work.

2) On the frontend I was using the JYA packages for VDPAU support and the update killed mythfrontend. I had to manually reinstall it.

3) The device files /dev/nvidia0 and nvidiactl don't have the correct user rights. I had to manually change the rights using chmod on every boot in /etc/rc.local

4) Mythcontrolcenter totally destroyed my lirc configuration. I'm using a generic serial driver, which isn't supported and so it deleted the configuration.

5) My sound is muted every time on boot. I used alsactl restore in 9.04 to restore the configuration. But the upgrade removed the alsa-utils package.

The biggest problem I have now is "now do you delete recordings from the frontend"? I've always watched a program then pressed right on the remote then delete recording. There is a menu "manage recordings" and a menu option delete recordings but that just seems to go to the view recordings screen.

Regards
Ian Dobson

---

### Post by ian dobson on 2009-11-29
Hi,

And why is mythtv-backend dependant on nvidia-185-libvdpau? I need CUDA and I can't get it running with the standard ubuntu NVIDIA drivers.

Regards
Ian Dobson

---

### Post by ianhaycox on 2009-11-30
Press D to delete recordings. I only found it by stabbing at the keyboard in frustration.

Yes - this annoyed me as well.

---

### Post by SiHa on 2009-11-30
> **ian dobson said:**
> 

The biggest problem I have now is "now do you delete recordings from the frontend"? I've always watched a program then pressed right on the remote then delete recording. There is a menu "manage recordings" and a menu option delete recordings but that just seems to go to the view recordings screen.


Personally, I changed the 'Action on exiting a recording' to 'Save Position and Exit, Exit, Prompt for delete', so when I finish watching a recording, I just press 'back' to stop it then select the 'Delete' option.

---

### Post by ian dobson on 2009-11-30
> **ianhaycox said:**
> Press D to delete recordings. I only found it by stabbing at the keyboard in frustration.

Yes - this annoyed me as well.

That only works if you have a keyboard attached. My frontend is as living room frendly as possible and doesn't have a keyboard.

Regards
Ian Dobson

---

### Post by SiHa on 2009-11-30
> 4) Mythcontrolcenter totally destroyed my lirc configuration. I'm using a generic serial driver, which isn't supported and so it deleted the configuration.

Same here. I've filed a bug, but nothing much seems to have been done about it.

---

### Post by williammanda on 2009-11-30
Also to delete recordings you can select "i". This is the old menu that use to pop up when using the arrows in version .21.

---

### Post by larsolav on 2009-11-30
> **williammanda said:**
> Also to delete recordings you can select "i". This is the old menu that use to pop up when using the arrows in version .21.

I mapped the green button on my streamzap remote to "i" and the red button to "d". The green "i" button is very helpful when needing to download metadata in mythvideo...

---

### Post by ian dobson on 2009-11-30
> **SiHa said:**
> Same here. I've filed a bug, but nothing much seems to have been done about it.

Yep, it would be nice if they just had an option "Leave the LIRC configuration alone, I know what I'm doing"

Regards
Ian Dobson

---

### Post by ian dobson on 2009-11-30
> **larsolav said:**
> I mapped the green button on my streamzap remote to "i" and the red button to "d". The green "i" button is very helpful when needing to download metadata in mythvideo...

OK, i've just mapped the Red button to i and it appears to work. Not as nice as pressing forwards and jumping to a menu where you could play/delete etc.

Regards
Ian Dobson

---

### Post by SiHa on 2009-11-30
> **ian dobson said:**
> Yep, it would be nice if they just had an option "Leave the LIRC configuration alone, I know what I'm doing"

Regards
Ian Dobson

Particularly as I was especially careful not to stray anywhere near the LIRC configuration screens, 'just in case'. Good job I had all the files backed up.
> OK, i've just mapped the Red button to i and it appears to work. Not as nice as pressing forwards and jumping to a menu where you could play/delete etc.
Still prefer my way...;)

---

