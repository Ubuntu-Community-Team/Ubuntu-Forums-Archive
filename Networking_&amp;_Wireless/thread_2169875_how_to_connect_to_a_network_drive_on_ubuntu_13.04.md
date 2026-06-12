---
title: "how to connect to a network drive on ubuntu 13.04"
date: 2013-08-23
forum: Networking &amp; Wireless
---

### Post by lfmartind on 2013-08-23
I have tried the instructions on the wiki to set permanently a connection to my network drive, but I got lost in the changes in Ubuntu from 12.04 to 13.04 there is no "places" anymore and the network id do not reside where they used to be. I consider myself in the middle with regards of skills. I appreciate if someone can lead me in the right direction. This is the last thing I did:

1. I created a new directory : media/windowsshare

2. I opened the /etc/fstab file using sudo and added the following line:

//servername/sharename  /media/windowsshare  cifs  guest,uid=1000,iocharset=utf8  0  0 

3. under servername I used the IP address located on the network connection information and for sharename I used the identifier of my 
network drive "MybookLive"

4. on the terminal i did; sudo mount -a

5. I got this: Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

I am lost, because I do not understand what should I look for on the manual...

Any help will be greatly Appreciated.

---

### Post by zero2xiii on 2013-08-24
Hay I think this:

> **lfmartind said:**
> 
//servername/sharename  /media/windowsshare  cifs  guest,uid=1000,iocharset=utf8  0  0 


Should be:
```
//servername/sharename /media/windowsshare cifs guest,uid=1000,iocharset=utf8,**sec=ntlm** 0 0 
```

This is due to:
[https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=81bcd8b795229c70d7244898efe282846e3b14ce](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=81bcd8b795229c70d7244898efe282846e3b14ce)

ntlm is no longer the default security (for 13.04 basically and up) and thus you need to specify it.
Something like that anyway. Give it a try and see what happens.

Cheers

---

### Post by lfmartind on 2013-09-15
Thanks, that solved the original problem. Now I do have a message saying unable to find suitable address. where can I find the IP address of my network drive?

---

