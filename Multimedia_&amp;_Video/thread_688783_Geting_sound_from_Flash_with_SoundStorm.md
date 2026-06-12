---
title: "Geting sound from Flash with SoundStorm"
date: 2008-02-05
forum: Multimedia &amp; Video
---

### Post by Dukenukemx on 2008-02-05
I'm following the guide from this thread.
[http://ubuntuforums.org/showpost.php?p=1716845&postcount=61](http://ubuntuforums.org/showpost.php?p=1716845&postcount=61)

I'm totally new to linux but so far I got Dobly Digital sound working from his other guide.  Now I'm trying to get sound through Flash but I haven't got a clue.  

I'm actually stuck at the first step.
_**build-essential; libicu34; libicu34-dev; libssl0.9.8; libssl-dev; linux-headers-<kernel name> package for your kernel (or unpacked and symlinked kernel source tree in /usr/src if you built your kernel from scratch)**_

I have no idea what kernel Ubuntu has so I typed this.
**_build-essential; libicu34; libicu34-dev; libssl0.9.8; libssl-dev; linux-headers-generic_**

I got this output.
[B][I]bash: build-essential: command not found
bash: libicu34: command not found
bash: libicu34-dev: command not found
bash: libssl0.9.8: command not found
bash: libssl-dev: command not found
bash: linux-headers-generic: command not found[/I][/B]

What am I doing wrong?

---

### Post by Metaljaz on 2008-02-05
to check your kernel version type this in the terminal window:

uname -r

you may also need to install the build-essentials from the synaptic package manager…or you can install it by typing in the terminal:

sudo aptitude install build-essentials

---

### Post by Dukenukemx on 2008-02-06
The name of the kernal came up as 2.6.22-14-generic.  Then I entered this into Terminal.
**_sudo aptitude install build-essentials_**

So I typed this in Terminal.  
**_build-essential; libicu34; libicu34-dev; libssl0.9.8; libssl-dev; linux-headers-2.6.22-14-generic_**



Then I got this output.  
[B][I]bash: build-essential: command not found
bash: libicu34: command not found
bash: libicu34-dev: command not found
bash: libssl0.9.8: command not found
bash: libssl-dev: command not found
bash: linux-headers-2.6.22-14-generic: command not found[/I][/B]

Help please. :(

---

### Post by Dukenukemx on 2008-02-06
/bump

Nobody can help?

---

### Post by jocko on 2008-04-19
> **Dukenukemx said:**
> /bump

Nobody can help?

Just in case you still haven't managed to fix this:
That line:```
build-essential; libicu34; libicu34-dev; libssl0.9.8; libssl-dev; linux-headers-2.6.22-14-generic
```is, as the post you linked to says, a list of packages you need to install.
Either find them in synaptic (but notice that the two "libicu" packages in gutsy have different numbers; 36 instead of 34), or use this command in a terminal:
```
sudo apt-get install build-essential libicu36  libicu36-dev  libssl0.9.8  libssl-dev  linux-headers-generic
```

---

