---
title: "Non root user unable to use sound!?"
date: 2010-08-24
forum: Multimedia Software
---

### Post by jruden on 2010-08-24
I am having sound problems on my 64bit lucid server.

The aplay -l command is supposed to list sound cards. Doing this as my ordinary user gives:
```
$ aplay -l
aplay: device_list:223: no soundcards found...

```
However, doing it as root gives:
```
$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
Home directory /home/john not ours.
card 1: default [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Is this a fault? Should aplay -l normally work on an ordinary user?

Moreover, trying to play an mp3 via command line DOES NOT work with:
```
mpg123 acdc-its_a_long_way_to_the_top.mp3
```
although the program does run and does not complain(where is it sending the sound?).

Doing the same as root with(notice i do not specify any explicit devices):
```
$ sudo mpg123 acdc-its_a_long_way_to_the_top.mp3
```
produces sound in my speakers.

Any ideas/pointers?

---

### Post by tjones00 on 2010-08-25
It depends on what type of install you did.

Usually this happens during a network install with no desktop (ubuntu minimal).

Or if you have just installed a program that needs to define/set a new group then add your user and you haven't logged out/rebooted since installing the software.

Or you've added a new user and haven't defined any groups.


The commands.

To list the users on the system.

```

cat /etc/passwd
```

To list the groups on the system.

```
cat /etc/group
```


To check the groups a user belongs to.

```
groups username
```

To add a user to a group (for alsa the groupname would be audio).
```

sudo usermod -a -G groupname username
```


Advanced reference about users/groups incase you're curious.

[http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html)

---

### Post by Yellow Pasque on 2010-08-25
Make sure your user is in the pulse group, and that the pulse group is in the audio group

---

### Post by jruden on 2010-08-25
Thanks guys for the replies! Fortunately I was able to solve my problem by adding my user to the audio group. I had attempted this yesterday also, but it turned out a reboot was needed as well before it started working. After this sole alteration my user can suddenly aplay, alsamixer and play music without sudo.

:D

---

