---
title: "Soundcards Disappeared after Update"
date: 2010-03-24
forum: Multimedia Software
---

### Post by Mr. Matt on 2010-03-24
After having a bunch of trouble getting sound to work with 9.10, I finally got a system.  After each linux kernel upgrade, I would just need to upgrade Alsa back to the latest version to get it working again.

A couple days ago, I noticed new kernel headers in the update package and was prepared to upgrade Alsa again.  However, today when I went to do the upgrade I find that my soundcards are no longer available!

What can I do to get sound working again?

```
matt@matt-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Mar 10 2010 for kernel 2.6.31-20-generic (SMP).
matt@matt-laptop:~$ sudo /etc/init.d/alsa-utils stop
[sudo] password for matt: 
 * Shutting down ALSA...                                                         * warning: 'alsactl store' failed with error message 'alsactl: save_state:1502: No soundcards found...'...                                              [fail] 
matt@matt-laptop:~$ aplay -l
aplay: device_list:223: no soundcards found...

```

---

### Post by Mr. Matt on 2010-03-25
Bump.  Anyone?

---

### Post by Yellow Pasque on 2010-03-25
Why did you stop ALSA and then check for devices?

---

### Post by lidex on 2010-03-25
What is the output of this command:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

Run these commands and reboot:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```

---

### Post by lidex on 2010-03-25
> **Temüjin said:**
> Why did you stop ALSA and then check for devices?

That's a good question. Mr Matt, after your alsa upgrade did you reboot? Or were you trying to restart alsa?

---

### Post by Mr. Matt on 2010-03-26
> **lidex said:**
> What is the output of this command:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

Run these commands and reboot:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```

```
matt@matt-laptop:~$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
Cannot stat /dev/dsp*: No such file or directory
Cannot stat /dev/dsp*: No such file or directory
```

I was going to follow the instructions here -http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/ - as when the linux kernel is upgraded, the alsa drivers are reverted to the original version installed with Ubuntu.  But then I noticed that something was different from last time because I got the error when stopping Alsa.

I ran the second set of commands but nothing changed.  Also, it doesn't look like the kernel was upgraded even though it said in the update manager that it would be.  Perhaps there was an error updating?

---

