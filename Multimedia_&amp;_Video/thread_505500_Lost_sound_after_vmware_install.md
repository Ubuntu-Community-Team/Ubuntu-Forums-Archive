---
title: "Lost sound after vmware install"
date: 2007-07-20
forum: Multimedia &amp; Video
---

### Post by xeo_pt on 2007-07-20
I had sound, then I install vmware and it works with sound in both the client and the host.

After a reboot i lost the sound.

Any ideas?

---

### Post by dabl on 2007-07-20
Hmmm -- you mean you rebooted the host Linux system, right?  Well, open your VMWare virtual machine and see if it has sound.  Possibly it has somehow "adjusted" the sound system in the VMWare session.

---

### Post by xeo_pt on 2007-07-31
I don't think so.
Because sometimes I have sound in both the host and the client, and 
sometimes there is no sound in both systems.

Maybe is a problem with the nVidia driver.

I will do some search.

Thanks for your help.

---

### Post by NobleSavage on 2007-07-31
I had the same issue.  Don't have a clue how to fix it.

---

### Post by xeo_pt on 2007-08-02
My problem was nothing to do with vmware ( I think)
since I have 2 sound boards a nVidia and a e-mu, the main
board was e-mu,
with this article I change the main sound borad to the nVidia:
[http://ubuntuforums.org/showthread.php?t=480349&highlight=nvidia+sound](http://ubuntuforums.org/showthread.php?t=480349&highlight=nvidia+sound)

---

