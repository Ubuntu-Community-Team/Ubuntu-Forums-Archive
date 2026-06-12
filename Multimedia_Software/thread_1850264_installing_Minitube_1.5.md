---
title: "installing Minitube 1.5"
date: 2011-09-26
forum: Multimedia Software
---

### Post by lenighan on 2011-09-26
Minitube 1.3 in Software center does not run on Natty 11.04.

I have Minitube 1.5 downloaded & running perfectly, but only via the icon in my home folder.

I can't seem to move it into filesystem / urs / bin ~ permission denied.

Any solutions?

---

### Post by ajgreeny on 2011-09-26
You can either move it with the command ```
sudo mv /home/*user*/sourcefile /usr/bin/
``` or more simply make a folder in /home called bin, ie, /home/user/bin and put minitube there.  It will then execute simply from the command minitube, if that is the name of the executable file.

It would be good to know more about what you actually have in your home for minitube as I don't know it at all.

I also wonder if you are aware that you can get it from [https://launchpad.net/~ferramroberto/+archive/minitube/+build/2667770](https://launchpad.net/~ferramroberto/+archive/minitube/+build/2667770) but I'm not sure if there is a 64bit version if that is what you need.

---

