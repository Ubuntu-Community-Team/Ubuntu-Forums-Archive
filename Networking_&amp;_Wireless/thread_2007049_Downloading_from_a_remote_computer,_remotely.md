---
title: "Downloading from a remote computer, remotely"
date: 2012-06-20
forum: Networking &amp; Wireless
---

### Post by rodeoears on 2012-06-20
Here's the set up. I have a server at school, a server at home, and a netbook from which I control everything. I ssh into my home server from my netbook, and I can download things from the server at school to my home server through ssh. Is there any way that I can initialize a download from the school server to my home server, and then be able to close the ssh connection between my netbook and home server, but keep the download going?

---

### Post by hawkmage on 2012-06-22
There are a couple of ways of doing this.  The first way is to use nohup and background the copy process:
```
nohup scp /local/file/path server:/destination/path/on/other/system & 
```
This assumes that you are using ssh key authentication and you do not have to type a password since as soon as the process is in the background you can't easily send your password to it.  

The second way is to use a utility called screen.  This is basically a text based terminal emulator that allows multiple virtual terminals.  The screen process will not die when you log out so you can start screen and then run the copy in the virtual terminal and exit screen and log out of the system and come back to it later.  Here is a quick over view of how to use screen: [http://www.howtoforge.com/linux_screen](http://www.howtoforge.com/linux_screen)

---

### Post by rodeoears on 2012-06-22
Thanks a lot! Screen works perfectly. It's exactly what I was looking for and then some.

---

