---
title: "Installing Intrepid through SSH"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by NetworkNewbie on 2009-02-11
Hello!

I'm currently attempting to install Intrepid Server Edition on a server I recently purchased in Denver, Colorado (I live in Toronto, Ontario), using this tutorial [http://blog.jeffduckett.com/articles/2008/08/04/install-ubuntu-hardy-8-04-remotely-via-ssh-32-or-64-bit/](http://blog.jeffduckett.com/articles/2008/08/04/install-ubuntu-hardy-8-04-remotely-via-ssh-32-or-64-bit/)

This is an excellent tutorial (and probably the only one available on this esoteric process, kudos to Jeff Duckett) with some awesome scripts that automate the process of installation, however I've run into a snag- I keep running out of disk space at the moment any kind of writing to disk takes place, as the server has RedHat installed already, which I suspect is taking up the entire partition...I have run df -k to reveal:

Filesystem         1k-blocks    Used Available Use% Mounted on
/dev/sda3           67357816 2014636  61866316   4%  /
/dev/sda1             101086  101069         0 100%  /boot
tmpfs                1037040       0   1037040   0%  /dev/shm
/dev/sda1             101086  101069         0 100%  /mnt/ubuntu

What's going on here? I'm not sure how to interpret the above information. Two sda1's? What's up with that?

Also, here's the instructions that I'm giving to the fstab portion of the script:

echo proc            /proc  proc            0    0    >    fstab
echo /dev/sda1       /ext3  defaults,errors=remount-ro  0  1  >  fstab
echo /dev/sda3       /swap  sw              0    0    >    fstab


I'm fairly certain that the problem lies in my fstab configuration. My question(s) are:
                Why does the installer keep telling me that-->

  mount: none already mounted or /mnt/ubuntu/proc busy       AND
  mount: according to mtab, none is already mounted on /mnt/ubuntu/proc

Is the way I've configured the fstab actually doing anything?

Is there a temporary way to free up some space on the current RedHat install to make way for the new Intrepid install?

Thanks if you've read this far, I only somewhat realize how all over the place this post is. I bow down to the gurus to enlighten me. 

Thank you.

---

