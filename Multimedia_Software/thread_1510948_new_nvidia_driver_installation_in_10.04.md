---
title: "new nvidia driver installation in 10.04"
date: 2010-06-16
forum: Multimedia Software
---

### Post by jepperstone on 2010-06-16
Hi everyone!

I wish to update my nvidia driver (I was running 195.36.24 and I want to update to 195.36.31). I followed all the instructions on this [thread (http://ubuntuforums.org/showthread.php?t=1467074)]("http://ubuntuforums.org/showthread.php?t=1467074") and everything went well until this part: ```
sudo sh blahblah.run
```. The error I get in the terminal reads: 

You appear to be running an X server; please exit X before installing. For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com). 

I have no idea how to exit X as it's not in my system processes.

Can anyone please help? I have updated my nvidia driver in the past but have never encountered this problem.
I'm running Ubuntu 10.04 on a Dell XPS M1530 if that matters.

Thanks very much,
Jepp

---

### Post by jepperstone on 2010-06-16
Solved it!
[URL="http://www.linuxforums.org/forum/ubuntu-help/136966-exit-x-server.html"]
http://www.linuxforums.org/forum/ubuntu-help/136966-exit-x-server.html[/URL]

The key was: ```
sudo /etc/init.d/gdm stop
``` after pressing CTRL+ALT+F1 in the terminal. And then ```
sudo /etc/init.d/gdm start
``` after I installed everything.

Hope this helps others too.

---

### Post by dino99 on 2010-06-16
better to install x-swat ppa to synaptic repo, i dont like headhaches

---

