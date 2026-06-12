---
title: "Problems with Skype Video Since Upgrade to 2.2"
date: 2011-04-08
forum: Multimedia Software
---

### Post by falsedichotomies on 2011-04-08
Hello and thanks in advance for any assistance.

I'm running 32-bit Ubuntu 10.10 on a Macbook 3,1 and using my computer's built in iSight. Up until recently, before making the switch to Skype Beta 2.2, I was having no problems using Skype's video chat feature. However, now I am only able to get video working if I open a terminal window and type in:

"LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype"

Does anyone know of a way to get Skype functioning normally again? The launchers from my menu/panel no longer load the Skype that can use video, and when I tried to change the launch command to what what I use in terminal, it keeps telling me that "there was an error creating the child process for this terminal."

Thoughts, suggestions, etc.?

---

### Post by ryanomara on 2011-04-09
[http://ubuntuforums.org/showthread.php?p=6934020](http://ubuntuforums.org/showthread.php?p=6934020)

Had the same problem- fixed my video for the test anyways, but I am also having a bit of sound input troubles.  

If it doesn't work, scroll to the bottom of the page there is a tip for 32 bit linux, which I use but the first suggestion fixed it for me anyways. 


Good luck, 

Ryan

---

### Post by falsedichotomies on 2011-04-09
Thanks Ryan. I appreciate it.

---

### Post by phyzik on 2011-04-11
Does anyone else have a problem with pidgin-skype integration since the upgrade?

My Pidgin chat windows no longer receive messages (it can still send them). I'm thinking about downgrading Skype...

---

### Post by tenaka on 2011-04-13
> **damien37 said:**
> Does anyone else have a problem with pidgin-skype integration since the upgrade?

My Pidgin chat windows no longer receive messages (it can still send them). I'm thinking about downgrading Skype...

first of all i have stopped pidgin and skype then i have deinstalled pidgin-skype with:

```
sudo apt-get remove pidgin-skype
```

and installed the last .deb for ubuntu from [http://eion.robbmob.com/]("http://eion.robbmob.com/")

```
sudo dpkg -i skype4pidgin.deb
```

then i restarted pidgin and it worked for me :D

---

