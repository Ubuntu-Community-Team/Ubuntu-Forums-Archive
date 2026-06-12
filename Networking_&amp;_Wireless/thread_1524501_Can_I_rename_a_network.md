---
title: "Can I rename a network?"
date: 2010-07-05
forum: Networking &amp; Wireless
---

### Post by beardo_jax on 2010-07-05
I have found some threads that seem to be similar but none that directly seem to solve the issue that I am having.

I am run Lucid on a my laptop that is connected to a network with other Windows OS's. I installed a Windows program from one of the servers, which installed properly but when I try to run it it says

"You have spaces in the current Directory name. This can create problems. Please change the directory name before using CLIP."

The network that is mounted is named "netclip on grandisland2" and I don't know how to rename it. I don't know of anymore information that might help, but if you have any suggestions I will be greatful

---

### Post by Morbius1 on 2010-07-05
> I installed a Windows program from one of the servers, which installed  properly but when I try to run it it says
You installed a windows program onto Ubuntu?

Where is this windows program located - Ubuntu, Wine, in a Virtual Machine, on another networked machine, ......

---

### Post by beardo_jax on 2010-07-05
The program is on a machine running Windows, but it requires installing other files on the machine that is opening the program to run it.

I did use wine to install it. From my laptop using ubuntu I found the setup.exe file on host machine through the network and used autorun. It then created a shortcut on my ubuntu Desktop. That is all the same as when I installed it on other Windows machines, but I also had to map the network drive on those machines. I had the same problem before with a Windows install but then move the dir up so that there weren't any spaces which solved the problem then. My problem seems to be the "netclip on grandisland2". grandisland2 being the host.

Thank you for the quick response. I'm not a total n00b, but I wouldn't say I'm very experienced either.

---

### Post by Morbius1 on 2010-07-05
DIdn't understand a word of that. 

If "netclip on grandisland2" is on a linux machine and you can't rename it then create a symbolic link to some place else and rename that.

For example:
```
ln -s /home/morbius/.gvfs/"netclip on grandisland2" /home/morbius/TEMP
```Now rename the link:
```
mv /home/morbius/TEMP/"netclip on grandisland2" /home/morbius/TEMP/netclip
```Now if you do a ls -al /home/morbius/TEMP
> drwxrwxrwx  2 morbius morbius 4096 2010-07-05 18:03 .
drwxr-xr-x 87 morbius morbius 4096 2010-07-05 17:57 ..
lrwxrwxrwx  1 morbius morbius   35 2010-07-05 18:02 netclip -> /home/morbius/.gvfs/netclip on grandisland2Now point your application to /home/morbius/TEMP/netclip

There's probably a more elegant way to do this but I've never been very good with symlinks.

---

