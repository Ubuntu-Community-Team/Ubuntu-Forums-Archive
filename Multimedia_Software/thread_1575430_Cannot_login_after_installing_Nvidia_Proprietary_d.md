---
title: "Cannot login after installing Nvidia Proprietary drivers"
date: 2010-09-15
forum: Multimedia Software
---

### Post by sjesimon on 2010-09-15
I recently installed 9.04 and upgraded to 9.10. I ran the computer fine for several days before a notification pooped up to tell me I could upgrade my Nvidia driver to a proprietary driver. I did so, and restarted the machine. It gets only as far as the ubuntu screen with the spotlight shining down and freezes. I have tried booting into recovery and running this command (found in a search on forums, don't even know if it's applicable to my particular situation):

sudo dpkg-reconfigure xserver-xorg
Same result at startup.

I was going to overwrite the xorg.conf with xorg.conf.failsafe (also a fix i found in forums) but my machine does not have an xorg.conf.

I was looking for, but can't seem to find a way to undo the proprietary driver install from recovery mode. The answer may be buried in the forums, but I can't seem to find it.

Can anyone point me to an answer or have any ideas?

Thanks in advance...

Stephen

---

### Post by NT4usB on 2010-09-15
How froze is it? Does the numlock light go on and off when you press the key?
Can you Ctrl+Alt+F1 to a terminal screen?

iirc, the command is:```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Maybe you could uninstall the nvidia and it will boot to VGA:```
sudo apt-get remove nvidia*
```
Then you'll have a GUI to work with anyway...

---

### Post by SeePU on 2010-09-15
> **sjesimon said:**
> I recently installed 9.04 and upgraded to 9.10. I ran the computer fine for several days before a notification pooped up to tell me I could upgrade my Nvidia driver to a proprietary driver. I did so, and restarted the machine. It gets only as far as the ubuntu screen with the spotlight shining down and freezes. I have tried booting into recovery and running this command (found in a search on forums, don't even know if it's applicable to my particular situation):

sudo dpkg-reconfigure xserver-xorg
Same result at startup.

I was going to overwrite the xorg.conf with xorg.conf.failsafe (also a fix i found in forums) but my machine does not have an xorg.conf.

I was looking for, but can't seem to find a way to undo the proprietary driver install from recovery mode. The answer may be buried in the forums, but I can't seem to find it.

Can anyone point me to an answer or have any ideas?

Thanks in advance...

StephenI think they're all bad for upgrades to new drivers... the processes just don't work very well.  I think when you upgraded your Ubuntu version, you upgrade the kernel as well so it broke things.  You need corresponding kernel headers and linux headers with the nvidia modules and maybe the new install of the driver didn't establish this or something?

I would check to see if you still have a backup of the original xorg.conf file if you had one and copy this to the new one to get the opportunity to log in, at least.  You might be able to have VESA drivers or the open source nvidia driver to at least allow a log in.  You might have to look at your kernel headers and make sure everything matches up.  When you try to upgrade the kernel, things have a good chance of getting broken.  Another idea is to boot up a previous kernel or some safe mode option and then fix things.

Edit:  Oh. upon re-read, it seems you were using the Nouveau driver and tried the package manager in the repo that contains the default Nvidia driver which is used to try install.  I would download the latest Nvidia driver from the Nvidia website and install the 'Nvidia' way.  It's a bit of a process but if you can log in at some point, read up on that and see if it interests you.

---

### Post by NT4usB on 2010-09-16
> **SeePU said:**
> ...I would download the latest Nvidia driver from the Nvidia website and install the 'Nvidia' way.  It's a bit of a process but if you can log in at some point, read up on that and see if it interests you.

Not my first choice, if ease of maintenance/updating is the goal.
These **will** break every kernel upgrade.
The drivers installed via the restricted drivers mangler *should* update right along with the kernel.

---

### Post by sjesimon on 2010-09-16
Well good news and bad news. Good news is that deleting Nvidia via recovery console allowed me to login and download Nvidia drivers and install per their website instructions. Bad news is I had the same result. this time though, Nvidia created a xorg.conf, so i just renamed it via recovery console and was able to login again in low graphics mode. 

Seems like my system does not like Nvidia drivers for some reason. 

Do you suggest I upgrade to 10.04 and see if that will allow me to install Nvidia drivers or might that just complicate the problem?

---

### Post by XerXeX on 2010-09-17
I'm having the same problems as sjesimon and have not found any solution yet. It's a pitty that you have to hold your breath every time there is a kernel upgrade or new drivers cuz more often than not, something is going to be totally messed up after the upgrade.

---

### Post by XerXeX on 2010-09-17
This did the trick: [http://ubuntuforums.org/showpost.php?p=9755451&postcount=9](http://ubuntuforums.org/showpost.php?p=9755451&postcount=9)

---

### Post by SeePU on 2010-09-17
> **NT4usB said:**
> Not my first choice, if ease of maintenance/updating is the goal.
These **will** break every kernel upgrade.
The drivers installed via the restricted drivers mangler *should* update right along with the kernel.Perhaps, but then you're relying on software doing it properly.

I haven't come across any distro that does it well including Ubuntu.

I found that the initial pita process of trying it manually ultimately does two things for you:
1) you get familiar with the routine and learn what to expect and what is needed
2) you have the option of more up to date drivers so if there is a bug fix, feature addition or whatever in recent or beta drivers, if you know how to install it the manual way, you can test whatever driver you want.

Using the driver installer built-in to the distro usually only fetches whatever driver was up-to-date at the time of the distro release and even then I'm not sure you get up-to-date drivers as updates in the repo.  

The other problem is when the installer doesn't work all that well or if there's a problem in the install, it's harder to troubleshoot because you're used to just sitting there letting things happen.  

XerXeX's solution above appears to be the installer basically doing the commands you would do manually but it's installing an older driver.

I have installed the Nvidia driver manually in Ubuntu and I have had the 'black screen' and had to repair my xorg.conf file more than once.  It's a hassle but once you realize what you need to do in CLI, it allows installs of later driver versions and you have a clue of what's going on even if it's not much of one. ;)

---

### Post by NT4usB on 2010-09-17
> **SeePU said:**
> Perhaps, but then you're relying on software doing it properly.

I haven't come across any distro that does it well including Ubuntu....

Video has been the biggest bugaboo for me in Ubuntu. Over the years I've learned to work around it. Tip #1, recycle xorg.conf. I've used the same xorg.conf, tweaking as I go, since Dapper days.

I agree, once the console is mastered, it's much easier to work with the binary driver... up to 10.04 that is.

10.04 threw me a new twist. I've had a couple kernel upgrades that broke nvidia but simply reinstalling from a terminal fixes it.
Then, after the last kernel update, and nvidia broke, I couldn't get to a terminal no how, no way. Recovery mode was black. Ctrl+Alt+Fx, black.
The box wasn't locked up as the numlock light worked and Ctrl+bla was switching between consoles, all black.
Tried blind typing to kill/restart gdm. Couldn't remember the sequence of Tabs and Enters to install nvidia blind.
For whatever reason networking broke at the same time so no ssh.

Had to switch from the pae kernel to the generic kernel, then boot to the onboard Intel video and install nvidia from there.
If the board didn't have onboard video, don't know what I'd have done.
Not for the feint of heart.

---

