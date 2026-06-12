---
title: "cinelerra - a specialist question I think"
date: 2007-05-26
forum: Multimedia Production
---

### Post by koenya on 2007-05-26
After installing cinelerra in ubuntu feisty I get the following error after start-up:

VOID MWINDOW::init_shm():WARNING: /proc/sys/kernel/shmmax is 0x2000000, which is too low
Before running cinelerra do the following as root:

echo "0x7fffffff" >/proc/sys/kernel/shmmax

1) what does this mean?
2) can I type in the echo command ( is it a command??) as it is written above
3) what will happen and what are the risks?

Thanks!!

EDIT: I typed in the command and it works ;)

EDIT 2: for people having difficulties installing cinelerra, just enter the repository in  synaptics and install...

---

### Post by nedecor on 2007-05-26
To get the best performance, Cinelerra requires a bit more shared memory. So shmmax is a kernel parameter for SHared Memory MAXimum. Yes it is safe, there are no risks that I am aware of.

Jake

---

### Post by kayosiii on 2007-05-27
For a permanent change, add to the &#8220;`/etc/sysctl.conf&#8217;&#8221; file the following line:
 
 kernel/shmmax=0x7fffffff
 
 For the first time, to avoid restarting your computer, use the following command as root:
 
 sysctl -p

Stolen from here [http://ubuntuforums.org/showthread.php?t=320701&page=7&highlight=cinelerra](http://ubuntuforums.org/showthread.php?t=320701&page=7&highlight=cinelerra)

Tip: you can often find answers to your questions by searching these forums.

---

### Post by fsman on 2007-05-28
I ignore the error and haven't experienced any problems

---

### Post by Dylnuge on 2007-05-28
You will get that error every time you start Cinelerra, until you enter the command.

All it means is that Cinelerra can't preform as well as it could if you ran the command. The command is harmless.

Follow Kayosiii's advice if you don't want to see the error anymore (and in addition get max preformance). Otherwise you need to enter the command every time you reboot the machine.

---

