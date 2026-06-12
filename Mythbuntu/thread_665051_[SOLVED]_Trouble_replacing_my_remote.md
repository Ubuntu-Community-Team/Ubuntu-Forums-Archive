---
title: "[SOLVED] Trouble replacing my remote"
date: 2008-01-11
forum: Mythbuntu
---

### Post by Meph1st0 on 2008-01-11
My wife the other day accidentally dropped our snapstream firefly remote in a cup of hot chocolate.  I've since purchased a new one.  Is there anything special I have to do with regards to lirc or drivers or anything?  I'm using the same RF receiver as the old one and that doesn't seem to cut it.  Anything else I need to do?  Should I reboot or restart the lirc deamon?

How do I restart the lirc deamon?

---

### Post by williammanda on 2008-01-11
> **Meph1st0 said:**
> My wife the other day accidentally dropped our snapstream firefly remote in a cup of hot chocolate.  I've since purchased a new one.  Is there anything special I have to do with regards to lirc or drivers or anything?  I'm using the same RF receiver as the old one and that doesn't seem to cut it.  Anything else I need to do?  Should I reboot or restart the lirc deamon?

How do I restart the lirc deamon?

What remote did you purchase?

You stop and start lirc with these commands:
Stop
sudo /etc/init.d/lirc stop
start
sudo /etc/init.d/lirc start

Also you can get additional info here:
[https://help.ubuntu.com/community/InstallLirc/Gutsy](https://help.ubuntu.com/community/InstallLirc/Gutsy)

---

### Post by Meph1st0 on 2008-01-11
I bought the same one, the snapstream firefly.  My wife likes that remote and doesn't want to have to get used to another one, even though I've got a harmony 680 collecting dust that we could use instead.

Stopping and starting the lirc deamon didn't seem to do it.  Also, I've gone back into mythbuntu control center and unchecked the remote box, applied it and then rechecked it and applied it as well.  That didn't seem to fix it.  Though I didn't have the "generate dynamic button mappings" box checked because I don't want it to overwrite the changes that I had made a long time ago to my .lircrc file.  Maybe I'm misinterpretting that checkbox but I assume that that's what that checkbox would do.

---

### Post by Meph1st0 on 2008-01-11
Do I need to do some sort of modprobe or something like that?  Is there some unique hardware ID that the computer is looking for?  Am I completely confused about what the modprobe command does?

---

### Post by Meph1st0 on 2008-01-11
Anybody?  Don't give up on me yet!

I'm replacing a broken piece of hardware with the exact same (new) piece of hardware.  I don't understand why this wouldn't work straight out of the box.

I am currently updating the machine through synaptic.  Just FYI.  It's gonna take a while.

---

### Post by Meph1st0 on 2008-01-12
It's working now.  I really don't know what I did to fix it.  I think all I really did is recreate my lircd.conf file and ~/.mythtv/lircrc files and then reboot.  I think everything else was superfluous.

We can mark this as solved if we want.

---

### Post by williammanda on 2008-01-12
I too had a strange problem getting the remote to work when i was changing from edgy to feisty. I saved my .lircrc and lircmd file as an attachment in email. When I finished changing to feisty and was ready to setup the remote, it didn't respond. I ended up have to re-make the .lircrc and lircmd files from scratch. For some reason the two files got corrupt and wouldn't work.

---

### Post by Meph1st0 on 2008-01-12
That is actually one thing that I had done but didn't think that it was the fix.  Maybe it was.

I ran mythbuntu-lircrc-generator and it seemed to recreate those files.

---

