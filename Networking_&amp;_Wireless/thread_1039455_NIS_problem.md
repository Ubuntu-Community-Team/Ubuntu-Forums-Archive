---
title: "NIS problem"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by 480silverton on 2009-01-14
Does anyone know how to set up NIS properly?

All the information I find these days don't work properly.

(The whole centralized user Database.)



For some reason the client computers can't bind to the NIS server.
Did I set up the client wrong or the server?

---

### Post by mshenoy4573 on 2009-01-15
well whats the setup you did.... I have tried NIS a couple of times....

did you check the /etc/hosts on both 
and did u build the nis db ?
how about the /etc/nsswitch.conf ?

---

### Post by 480silverton on 2009-01-15
Well I tried several.
Basically what I could find on the Google Search.

Yeah I did all of them that you said.

But I still have the problem.
I was thinking that maybe the Firewall?

Because its what I had to do for NFS.

---

### Post by albinootje on 2009-01-15
> **480silverton said:**
> Does anyone know how to set up NIS properly?

Check the content of /usr/share/doc/nis/
Since years I'm successfully using NIS on Debian and Ubuntu based on that documentation.

A good start is, to start a terminal, and run this :
```

zless /usr/share/doc/nis/nis.debian.howto.gz 

```
Use page-up, page-down to scroll, and "q" to quit.

There's one possible add-on you will need.
And that's editing the /etc/default/nis file on your NIS-server.

To check whether NIS is running, use this :
```

rpcinfo -p

```
And see whether ypbind is there.

And, just for your information, in case you didn't know :
NIS is simple and handy for small networks, but it uses plain text over the network for username and passwords.

---

### Post by 480silverton on 2009-01-18
Thanks I'll try that!

---

### Post by kvtb on 2009-02-21
you are not doing anything wrong, the default installation of NIS is severely broken, and I think it has something to do with network-manager.

This is already the case for years, and also in the next version, 9.04 it is broken (I just tested Alpha 4).

---

### Post by 480silverton on 2009-04-08
> **kvtb said:**
> you are not doing anything wrong, the default installation of NIS is severely broken, and I think it has something to do with network-manager.

This is already the case for years, and also in the next version, 9.04 it is broken (I just tested Alpha 4).

Dang....
Thats just great...
Maybe Using Fedora as the server might fix the problem?

---

### Post by 480silverton on 2009-10-09
Wait I figured out the problem
There is one mistake in the HOW TO documentation from Ubuntu.

---

### Post by asmahosna on 2011-01-11
Hi,
I set NFS for server-client that works properly. Now I am trying to set NIS server-client on same PC's. 
I am following the instruction from [COLOR=black]"[/COLOR][[COLOR=black]SettingUpNISHowTo[/COLOR]]("https://help.ubuntu.com/community/SettingUpNISHowTo?action=fullsearch&context=180&value=linkto%3A%22SettingUpNISHowTo%22")[COLOR=black]" from [https://help.ubuntu.com/community/SettingUpNISHowTo](https://help.ubuntu.com/community/SettingUpNISHowTo) [/COLOR]link.
 
But in step-10, "[COLOR=black]sudo /etc/init.d/nis restart".......it show error fail.[/COLOR]
 
Can anyone able to get rid out from this problem?
Is all the step in the document is proper to configure the NIS server?
In last post I saw someone figure out problem on this document...could you explain this.......?
Thanks in advance.

---

