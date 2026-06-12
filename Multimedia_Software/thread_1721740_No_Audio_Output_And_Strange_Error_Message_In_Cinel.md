---
title: "No Audio Output And Strange Error Message In Cinelerra"
date: 2011-04-04
forum: Multimedia Software
---

### Post by giddyup306 on 2011-04-04
I did quite a bit of searching last night, and as far as the audio goes, it looks like there may have been a problem with Pulse Audio.  I uninstalled that, and installed esuond, which did nothing.  After updating the system, and trying several things, I am still empty-handed.  I read on a Cinelerra FAQ site, that I might have to go into settings, and select ALSA for sound.  The drop-down menu has nothing in it.  When I start the program, I get this error (see attachment).  When I try and run the line of code, it says "permission denied". I tried searching for that specific code and found nothing.  I really don't know how to go about fixing this problem.  

Thanks.

---

### Post by giddyup306 on 2011-04-05
Okay I fixed half of my problem.  I have no idea how or why, but now I have my audio problem fixed.  I had to restart my computer for something else, and now all of a sudden it works.  Before it only gave me the OSS option for audio.  Now it had about 8 options.  I just decided to set it to ALSA, and now it works...  This is really funny because I was messing with this program all night last night, and I restarted my computer several times.  I did do a system update tho...

I still don't know what to do about the other part of the problem.

---

### Post by giddyup306 on 2011-04-05
After doing some more searching, I found this.

[http://ubuntuforums.org/archive/index.php/t-666123.html](http://ubuntuforums.org/archive/index.php/t-666123.html)

Now this is back from 7.10, so I don't know if something is different in 10.10.

Either this doesn't work, or I'm doing it wrong.  I tried adding kernel/shmmax=0x7fffffff and kernel.shmmax = 2147483647 to the etc/sysctl.conf file at two different times, and rebooted both times.  Still didn't work.  What am I missing?  Is there a specific place I need to put that line?  I tried it both with and without a "#", and still nothing.

---

### Post by giddyup306 on 2011-04-05
I forgot to mention that I did run the following long before I made this post.  

```
sudo su

echo "0x7fffffff" > /proc/sys/kernal/shmmax
```It then came back and said:

```
bash: /proc/sys/kernal/shmmax: No such file or directory

```I also tried

```
sudo sh -c "echo '0x7fffffff' > /proc/sys/kernal/shmmax"

```and it gave me a similar message:

```
sh: cannot create /proc/sys/kernal/shmmax: Directory nonexistent

```Someone please help.  I've been trying to get this to work since Friday.

I found this on their site, but I still get the error messages...

> ** 21.9.3 Freeing more shared memory **

  The GNU/Linux kernel only allows 32MB of shared memory to be allocated by default.  This needs to be increased to do anything useful.  When launched, Cinelerra may remind you that with the following error message: 

The following errors occurred:
void MWindow::init_shm0: WARNING:/proc/sys/kernel/shmmax is 0x2000000, which is too low.
Before running Cinelerra do the following as root:
echo "0x7ffffff">/proc/sys/kernel/shmmax
For a permanent change, add to the `/etc/sysctl.conf' file the following line: 
kernel/shmmax=0x7fffffff
or if you prefer: 
kernel.shmmax = 2147483647
For the first time, to avoid restarting your computer, use the following command as root: 
sysctl -p


---

