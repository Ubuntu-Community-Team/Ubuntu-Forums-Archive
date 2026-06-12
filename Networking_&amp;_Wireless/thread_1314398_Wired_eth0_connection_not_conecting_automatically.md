---
title: "Wired eth0 connection not conecting automatically"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by awworrell on 2009-11-04
Hello All,
 
To give you a little background on my problem, I have been working with Karmic Koala to try to use it as a base to test new software. I have managed to assign the eth0 connection a static ip address which includes my subnet mask and default gateway. When I restart the computer the network manager says that the connection is connected; however, the system acts as if it is not connected to anything.
 
I have also read that this is a bug? If so, what patches are available if any?
 
Also, upon setting up the static ip, I went about doing it through the network preferences. When doing this, the /ect/network/interfaces file still is the same. I have tried editing it with vi, vim, emacs, and gedit. This doesn't work since the file system is mounted as read only. Is there a way to change this? Do I need to edit that file?
 
I apologize for all of the questions up front. I am new to this system and am working to learn as much as possible.

---

### Post by awworrell on 2009-11-04
Could anyone give me a hand?

---

### Post by zika on 2009-11-04
> **awworrell said:**
> Could anyone give me a hand?You say that Your file-system is read-only. That suggests that You have some problems with Your file system. Without further insight the only thing I could advise is that You boot with LiveCd and, once Your system is operational with LiveCD, You should do fsck /dev/sdXX where XX should be substituted with Your actual values for that partition. Then You could reboot and boot with Your HDD Karmic and try to change network connection settings ...

---

### Post by awworrell on 2009-11-04
> **zika said:**
> You say that Your file-system is read-only. That suggests that You have some problems with Your file system. Without further insight the only thing I could advise is that You boot with LiveCd and, once Your system is operational with LiveCD, You should do fsck /dev/sdXX where XX should be substituted with Your actual values for that partition. Then You could reboot and boot with Your HDD Karmic and try to change network connection settings ...

Thank you for the help. I will look toward that way and try t figure it out. Thanks again

---

### Post by zika on 2009-11-04
> **awworrell said:**
> Thank you for the help. I will look toward that way and try t figure it out. Thanks againGreat! Just take it easy and I'm sure You will sort this out in no time.

---

### Post by awworrell on 2009-11-04
I have used the LiveCD to check the partition; however, nothing seems to have changed. Is there anyway in particular to change the file system from read-only to a format in which I can write to? I would try to reinstall Ubuntu; however, this has occurred before the first time I installed it. 

What other information may be helpful in solving this problem?

---

### Post by ant2ne on 2009-11-04
you are```
sudo nano /etc/network/interfaces
```, Right?


if not sudo, then you can't write changes.

---

### Post by Iowan on 2009-11-04
> **awworrell said:**
> This doesn't work since the file system is mounted as read only. Is the file system mounted read-only (as reported by **mount**) - or is it simply a problem with saving an edited file? Read-only file system is a problem, saving an edited file may be as simple as the **sudo** suggestion by **ant2ne**.

---

### Post by awworrell on 2009-11-05
> **ant2ne said:**
> you are```
sudo nano /etc/network/interfaces
```, Right?


if not sudo, then you can't write changes.

I apologize for the delay in answering. That is correct. I have tried sudo nano /ect/network/interfaces. I have also tired that with a vi, vim and gedit editors. It opens a new file each time which I cannot save to the file system. If I follow the path and open the interfaces file directly from the folder with gedit, the file cannot be saved due to it being read only.

Iowan, It is a problem from not saving the file. I was unaware of mount; however, will look into it to see what it does and how to use it. This is my second or third install of Ubuntu and I have had this problem both times.

---

### Post by ant2ne on 2009-11-08
what file system are you using?

---

### Post by peepingtom on 2009-11-08
To let you know, changes in NetworkManager are not reflected in /etc/network/interfaces. In fact, any configuration of an interface in /etc/network/interfaces will stop NetworkManager from controlling that interface. 

Unless you are familiar with the command line, you should reverse these changes by restoring /etc/interfaces to it's original state:
```
auto lo
iface lo inet loopback
```

For more info: [http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager)

Check the permission on your mount points using the comand
```
mount
```

Check the permission of /etc/network/interfaces using the commands 

```
cd /etc/network
ls -l 

```

They should be ```
drwxr-xr-x 2 root root 4096 2009-10-27 21:01 if-down.d
drwxr-xr-x 2 root root 4096 2009-10-27 20:56 if-post-down.d
drwxr-xr-x 2 root root 4096 2009-10-14 01:48 if-pre-up.d
drwxr-xr-x 2 root root 4096 2009-10-27 21:01 if-up.d
-rw-r--r-- 1 root root   32 2009-11-08 21:28 interfaces

```

The chmod command can be used to change permissions.

```
sudo chmod 644 /etc/network/interfaces/interfaces
```

Am I oversimplifying your problem?

---

