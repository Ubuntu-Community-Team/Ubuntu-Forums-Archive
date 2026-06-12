---
title: "Broken Sound Menu in 12.04, Pulseaudio daemon startup  fails"
date: 2013-02-01
forum: Multimedia Software
---

### Post by spazzeri on 2013-02-01
Hello,

On Ubuntu 12.04 / Unity, the sound menu breaks every 2 or 3 days in at least one of my user profiles.
The machine can still play sound but it cannot be controlled by the sound menu, which displays the Mute icon.

When this happens, there is no pulseaudio process in the session.

```
pulseaudio --start
``` fails with:

E: [pulseaudio] main.c: Daemon startup failed.

I attached a pulseaudio verbose log. It contains:
> 
(   0.013|   0.000) E: [pulseaudio] module-udev-detect.c: inotify_init1() failed: Too many open files
(   0.013|   0.000) E: [pulseaudio] module.c: Failed to load module "module-udev-detect" (argument: ""): initialization failed.
Kernel: 3.2.0-36-generic
pulseaudio 1.1

---

### Post by spazzeri on 2013-02-01
It turns out that after raising the value of 

```
fs.inotify.max_user_instances
``` in /etc/sysctl.d or /etc/sysctl.conf and ```
sudo sysctl -p
``` then pulseaudio --start succeeds and the sound menu is back in shape.

Still, this does not explain why pulseaudio had crashed or failed to start in one user profile (with the inotify-related limits error message) while (this time at least) it was running fine in another user profile.

This problem had never occurred before. 
Does anyone have an idea ?

---

### Post by tswltd on 2013-02-04
I have this exact same problem and it is driving me nuts. The sound will not work for the default user but will work for any other user on the system including the guest account. I can even create new users and the sound will work for those accounts, but not the default user account. The only thing that fixes it is a reboot.

I looked at those files you referenced and the line "fs.inotify.max_user_instances" 
does not appear in any of the /etc/sysctl.d files or in /etc/sysctl.conf. 

The closest thing I found was "fs.inotify.max_user_watches". I am confused. More confusing is that there does not seem to be a fix for this problem. 

Any help would be appreciated.

Thanks

---

### Post by Yellow Pasque on 2013-02-04
Perhaps removing the problematic user's pulse files (so fresh ones get generated) will help?
```
rm -r ~/.pulse*; pulseaudio -k
```

---

### Post by spazzeri on 2013-02-06
> **tswltd said:**
> I have this exact same problem and it is driving me nuts. The sound will not work for the default user but will work for any other user on the system including the guest account. I can even create new users and the sound will work for those accounts, but not the default user account. The only thing that fixes it is a reboot.

I looked at those files you referenced and the line "fs.inotify.max_user_instances" 
does not appear in any of the /etc/sysctl.d files or in /etc/sysctl.conf. 

The closest thing I found was "fs.inotify.max_user_watches". I am confused. More confusing is that there does not seem to be a fix for this problem. 

Any help would be appreciated.

Thanks

I created a file /etc/sysctl.d/10-inotify.conf to raise the value of "fs.inotify.max_user_instances" (it was 128 before). The value can be checked with:
cat  /proc/sys/fs/inotify/max_user_instances.

I did that because logs produced by an attempt to start pulseaudio in verbose mode (see [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)) contained an error message about inotify:

```
[pulseaudio] module-udev-detect.c: inotify_init1() failed: Too many open files
```

This does not explain the phenomenon, but now at least it does not take a reboot to get pulseaudio. Perhaps a bug should be filed on launchpad.

---

### Post by spazzeri on 2013-02-06
@[Temüjin]("http://ubuntuforums.org/member.php?u=327594"): Apparently it did not do the trick. That said I had tried rm -r ~/.pulse, not ~/.pulse*.

---

