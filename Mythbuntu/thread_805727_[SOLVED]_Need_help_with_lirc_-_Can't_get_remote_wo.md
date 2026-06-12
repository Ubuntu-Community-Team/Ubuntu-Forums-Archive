---
title: "[SOLVED] Need help with lirc - Can't get remote working"
date: 2008-05-24
forum: Mythbuntu
---

### Post by Crusty Juggler on 2008-05-24
After dallying with Mythdora, I'm back to Mythbuntu, for the sole reason of understanding the filesystem and commands...  

Everything on my install seems to be working well, except I cannot get my remote working.  My tuner card is the Leadtek DTV2000H and the remote is the Y04G0044.

I've used the lircd.conf and lircrc files from [http://www.users.on.net/~promus/]("http://www.users.on.net/~promus/") which are purported to work [http://ubuntuforums.org/showthread.php?t=708217]("http://ubuntuforums.org/showthread.php?t=708217").  

I'm still new to all of this, so I'm not sure which info is pertinent to diagnosing the problem.  One thing I know is wrong is that when I reboot I get the following error:
Starting remote control daemon(s):LIRC  [fail]

Similarly, the following command
```
sudo /etc/init.d/lirc start --verbose 
```
gives:
```
 * Loading LIRC modules                                                  [ OK ] 
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

```

I think this is the last stepping stone to having a working mythbox...  Please help!

---

### Post by Crusty Juggler on 2008-05-24
Solved.

Solution is [here]("http://ubuntuforums.org/showthread.php?t=708217").

---

