---
title: "Automounting 2nd internal hard drive on boot"
date: 2007-07-09
forum: Multimedia Production
---

### Post by JTCP on 2007-07-09
Hi,

I was wondering if its possible to auto mount an additional internal hard drive on boot and if so, how would I go about doing that through the terminal.
I'm using feisty 7.04. Its the first time Ive used/installed any linux distro. I did a duel boot and I have to say, since Ive installed it, I havent booted into xp mce 2005 more than once or twice within the week that I've had Ubuntu installed! I've seen the light!! 
It took me a couple of days but I got all my hardware installed with drivers ans what-not. The only thing I dont like about Ubuntu is that there still some programs that I have to be a damn slave to windows for, I wish I could just erase the windows partition forever.
I think the sense of community you people have here is great and Im so happy to be apart of it, you people really are awesome. Keep up the great work everyone and in time when I learn a lot more, I look forward to contributing my share to everyone else. 

Thank You,

JTCP

P.S. where do I go to learn all the terminal commands/language?

---

### Post by distort on 2007-07-09
a good place to start learning about the GNU/Linux command line is

[http://linuxcommand.org/](http://linuxcommand.org/)

before you can mount the drive, you have to create at least one new filesystem on it using mke2fs.
after that, try to mount it manually with the mount command.
the df command shows you all currently mounted filesystems on a running system.
to learn about a command or a configfile or a topic, type
man [commandname]
where you substitute [commandname] with the name of the command you wish info about, for example:

man df

or, to get info about fstab

man fstab

as to automounting drives at boot time: this is done in the file /etc/fstab
but be careful not to delete any existing entries in it, because you could end up with a system that is not able to boot linux anymore.

greets

d.

---

### Post by stainless_steel on 2008-03-16
i did it graphicaly using: "The fourth - simple- method is to install the pysdm package (in Gutsy) and then use System-Administration-Storage Device Manager without any manual editing of the fstab file, and disregard most of the instructions that follow."
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by stainless_steel on 2008-03-16
ok, pysdm stinks. stick to the fstab file

---

