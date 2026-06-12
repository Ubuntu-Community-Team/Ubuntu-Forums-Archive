---
title: "best way to share/access remote files?"
date: 2012-03-17
forum: Networking &amp; Wireless
---

### Post by JohnDillinger43 on 2012-03-17
I'm a recent convert to Ubuntu, and am looking for a good way to access files on my desktop from my laptop.  I still have one laptop running WinXP, so I've been using samba and have had no problem accessing files on my Ubuntu desktop from the WinXP laptop.  However, when I try to access the desktop files from my Ubuntu laptop, everything runs excruciatingly slowly, to the point that I don't even bother, and instead use the WinXP laptop when I need to open the desktop files from another room.  Since the Ubuntu laptop is my other main computer, I figure there's no reason not to use a native Linux method for file sharing, but I'm not sure where to start.  I've read that SSH can be somewhat slow (and slow access has been my main barrier), but I've also read good things about using sshfs.

Does anyone have a recommendation for accessing files on my desktop from my laptop?  They're both connected to the same wireless router; I work from home most of the time so I'm not too concerned with accessing the desktop files from a different network.  Mostly I'm just looking for a good way to mount a remote folder and work on a file on my desktop from another room.

---

### Post by papibe on 2012-03-17
Hi JohnDillinger43.

ssh will help you, if any, to speed up the traffic out of your Ubuntu laptop, but not the incoming data from your XP desktop.

Since you the problem comes in one direction, I'm inclined to think there is a configuration issue. I would start checking if both machines have the same network configuration.

Could you post the result of these commands in Ubuntu?
```
ifconfig

route -n
```
And the same for this one on XP?
```
ipconfig /all
```

Then, I would check some basic samba discovery commands on Ubuntu:
```
sudo smbtree

smbclient -L your_XP_machine
```
(if root's password is asked just press enter).

Regards.

---

