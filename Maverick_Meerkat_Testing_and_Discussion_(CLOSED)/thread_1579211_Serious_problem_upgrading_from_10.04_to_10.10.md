---
title: "Serious problem upgrading from 10.04 to 10.10"
date: 2010-09-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by scandido on 2010-09-21
I attempted to upgrade my system from 10.04 to 10.10 today. I simply ran "update-manager -d" and clicked the button to get the new distribution. After rebooting (when prompted) the system loads a purple, text-based screen. It says:

Ubuntu 10.10

.... [OK]
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service S50cups start

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the start(8) utility, e.g. start s50 cups start: Unknown job: S50cups
* PulseAudio configured for per-user sessions
saned disabled; edit /etc/default/saned
* Enabling additional executable binary formats binfmt-support [OK]
* Checking battery state... [OK]

At this point, nothing happens. I can switch to a terminal by clicking Alt+F5 and login to a shell. I tried typing "startx" to get a GUI, because that is what I used to do back in the day, but it just gives some error messages.

Can anyone suggest what I should be doing here to get my computer to boot again?

Thanks in advance for your help.

---

### Post by scandido on 2010-09-21
So although it was completely nonintuitive from what was being displayed, this was actually a problem with proprietary graphics drivers. Hopefully, if you've reached this thread because of the indexing of the error message, the two links below will be helpful to you.

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1559465](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1559465)
[http://ubuntuforums.org/showthread.php?t=1572254](http://ubuntuforums.org/showthread.php?t=1572254)

---

### Post by jstarr20052005 on 2010-09-21
I was having a **real** problem upgrading as well..

I followed the same steps the user above did to upgrade , but had different results. could use some help.
 see the picture, link below.

When I boot, I get to Grub and choose the first selection then get this screen. I have tried what it says, to no avail.. and I have tried all my options in grub.. 


thanks - jake
[http://www.flickr.com/photos/27218645@N03/5013391054/](http://www.flickr.com/photos/27218645@N03/5013391054/)

---

### Post by Iowan on 2010-09-22
Moved to Maverick Meerkat Testing and Discussion

---

