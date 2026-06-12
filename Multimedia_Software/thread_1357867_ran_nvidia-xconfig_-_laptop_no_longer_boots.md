---
title: "ran nvidia-xconfig - laptop no longer boots"
date: 2009-12-17
forum: Multimedia Software
---

### Post by ken.simon on 2009-12-17
Laptop is a Toshiba Satellite L300 with 3G ram and a dual core Pentium.

I have been running Ubuntu 9.10 since October.  For the most part it has been good, with the exception of some glitchy sound and video.  Since I mostly use this laptop for reading, I had ignored the glitches.  Today, I was attempting to clean up the issue, and ran, as was suggested in a post 'sudo nvidia-xconfig'. I rebooted the laptop and it will no longer boot correctly.  Symptoms are as follows:
1. I get the normal Toshiba splash screen.
2. Get the message 'GRUB loading.'
3. What appears to be normal output text for a number of seconds.  (I configured grub to display boot output.)
4. Black screen.
5. I can not access a VT.  ctrl+alt+F1, etc do not work.
6. Laptop is not getting a DHCP address.  DHCP server is not receiving the DHCPDiscover or DHCPRequest.
7. Can not connect by SSH. (not surprising, considering 6, above)
8. Apache is not responding.  (also not surprising)

I am in the process of downloading a new live cd, since mine went missing.  I am hoping to recover from this without a re-install.  

Any suggestions on where to start?
Please do not ask for any output, at least until I get the live cd running and the drives mounted.

---

### Post by ken.simon on 2009-12-17
OK, that was not quite as bad as it could have been.

I booted a live cd, then mounted the '/' drive:
sudo mkdir /mnt/disk1; sudo mount /dev/sda3 /mnt/disk1

I then renamed xorg.conf:
sudo mv /mnt/disk1/etc/X11/xorg.conf /mnt/disk1/etc/X11/xorg.conf.old

Reboot, and it appeard to be back to normal.

I know that this is GNU/Linux not ???dows, but sometimes it would be nice to see a warning such as "You are about to completely hose your computer.  Do you wish to continue?"

---

### Post by Menthu_Rae on 2009-12-17
> **ken.simon said:**
> **but sometimes it would be nice to see a warning such as "You are about to completely hose your computer.  Do you wish to continue?**"

Isn't that what the **password prompt** when running something using "sudo" or "gksu" is? :confused:

You are running something with root/super user privs... thus you can hose anything you want or anything you don't...

---

### Post by ken.simon on 2009-12-17
> **Menthu_Rae said:**
> Isn't that what the **password prompt** when running something using "sudo" or "gksu" is? :confused:

You are running something with root/super user privs... thus you can hose anything you want or anything you don't...

<rant>
Not really.  The password prompt is asking me if I am sure I want to do this.  It does not say 'You are about to hose your system'.  I understand that this can not always be done, but it is possible to create systems that can:
[LIST=1][*]Check that what you just did is not unreasonable, considering the hardware/OS/software.[*]Roll back a change if it is obvious that something has gone wrong, or has not been confirmed to be OK.
[/LIST]
I think, for example, of many video settings.  The tools will generally not allow you to choose settings that are know not to work, and then will roll back after a few seconds if there is no response.

I don't mean to rant, and I am NOT a developer, just a user.  I am just a bit upset that something as simple as this would create a situation where I could not even get to a cli.  OK, xorg-conf is messed up, so don't load X.  Just drop to a command prompt.
</rant>

OK. I'm done.

---

