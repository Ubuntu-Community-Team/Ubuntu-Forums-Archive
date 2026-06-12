---
title: "Mythbuntu 12.04LTS 64-bit - Mythtv GUI not autostarting"
date: 2013-10-26
forum: Mythbuntu
---

### Post by neutron68 on 2013-10-26
The system has been through a few issues with no GUI, and GRUB problems.
An apt-get update, apt-get upgrade was done on Oct.20 by the user.
The GUI problems were caused by not having the extra power cable plugged into the new video card.
The GRUB problems were fixed by the Boot Repair Live CD.
see: [http://ubuntuforums.org/showthread.php?t=2183434](http://ubuntuforums.org/showthread.php?t=2183434)

Now, the machine boots to a grey Mythbuntu GUI login (rather than autostarting the Mythtv GUI) and the user can't successfully login to "Mythbuntu Session" using the known-correct user password.
I am able to SSH into the machine using the known-correct user password, so we know it's correct.

Any ideas why the Mythbuntu login is popping up and not auto-launching the Mythtv GUI?
Any ideas how to fix?

---

### Post by neutron68 on 2013-10-26
Is this related to the .Xauthority file ownership problem?  It sounds very similar, if not the exact same thing.

[http://askubuntu.com/questions/146137/login-screen-loops-unless-you-login-as-guest](http://askubuntu.com/questions/146137/login-screen-loops-unless-you-login-as-guest)

[http://ubuntuforums.org/showthread.php?t=2167759&highlight=mythbuntu+password](http://ubuntuforums.org/showthread.php?t=2167759&highlight=mythbuntu+password)

[http://ubuntuforums.org/showthread.php?t=1890457](http://ubuntuforums.org/showthread.php?t=1890457)

[http://ubuntuforums.org/showthread.php?t=2167760](http://ubuntuforums.org/showthread.php?t=2167760)

---

### Post by neutron68 on 2013-10-26
I just tried giving ownership back to the user, via an SSH session.

> cd /home/username
chown username:username .Xauthority 

After a reboot, all was well.

see
[http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop/265858#265858](http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop/265858#265858)

I would think you could also bring up a TTY window by doing CTRL-ALT-F1 and log in.

---

### Post by neutron68 on 2013-10-26
I did some seaching in launchpad and see that this issue is caused by a bug in lightdm, first reported in 2011.
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/871667](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/871667)

The version of lightdm running on my friend's machine is lightdm 1.2.3.
The .deb file in the apt archive on the hard drive is dated July 19, 2013.
/var/cache/apt/archives/liblightdm-gobject-1-0_1.2.3-0ubuntu2.3_amd64.deb
/var/cache/apt/archives/lightdm_1.2.3-0ubuntu2.3_amd64.deb

It appears the bug still exists in version 1.2.3

---

