---
title: "Computers can't see each other over network"
date: 2012-01-16
forum: Networking &amp; Wireless
---

### Post by xly15 on 2012-01-16
I am having a problem. None of the computers on the network can see each other accept for the three computers that have windows 7 on them. One of those computers is a dual booter that has Ubuntu 11.10 on it.

None of the linux installations can see each other. The windows installations can't see the linux installations and the same going the other way. 

Can anyone help me?

---

### Post by wyliecoyoteuk on 2012-01-16
Have you installed Samba?
If not, you need to install Samba server and client.

---

### Post by xly15 on 2012-01-16
I ran the command to install samba and it told me that it is current. Shouldn't the linux computers just be able to see each naturally? Does anything need to be port forwarded or anything?

---

### Post by Iowan on 2012-01-16
You can try to **ping** one machine from another - either from a terminal or Network Tools. You will need to know the IP address of the target machine - available via **ifconfig -a** from a terminal or via Network Tools.
It's also possible that the workgroup/domain needs to be adjusted.

---

### Post by xly15 on 2012-01-16
Yes, pinging the target machines works. So maybe I should try changing the workgroup?

---

### Post by Iowan on 2012-01-16
This Natty (11.04) machine doesn't see other computers on Places>Network unless they are in a Windows network.
I had to change the definition in /etc/hosts:
```
127.0.1.1 Mybox.Mynet Mybox
```
should have been 
```
127.0.1.1 Mybox.mynet Mybox
``` (Apparently not the workgroup, in this case)

---

### Post by xly15 on 2012-01-16
Can you please interpret what you just wrote there? I really don't understand. What does the mybox.mynet thing mean?

Update: 

It has to be something wrong with my LAN then because I just used nautilus to explore my school's network and it was finding computers just like it should. So at least now I have narrowed down my problem. I will look over it when I get back home.

---

### Post by xly15 on 2012-01-17
Another update: 
The windows computers can see the my ubuntu and linux mint boxes. But they can't see the windows the computers neither can the linux boxes see each other. This problem is proving quite vexing to me as I would like to start using the the linux mint pc as a file server.

---

### Post by xly15 on 2012-01-18
It would be really nice if someone could help me. I have hit a wall and don't know what to do.

---

### Post by Reg71 on 2012-01-18
I'm no expert, but I googled for configuring samba on linux mint since you mentioned you wanted to use it.  here was the first link I saw that looked like it might help you: [http://www.liberiangeek.net/2010/04/how-to-quickly-share-files-between-windows-and-linux-mint/](http://www.liberiangeek.net/2010/04/how-to-quickly-share-files-between-windows-and-linux-mint/)

If you want more help on linux mint, you might be better served on linux mint forums although the two (ubuntu and mint) are pretty darn close AFAIK.  It would at least broaden out your search.  Also if you search the forums here you'll find several how-tos on doing this.  There are several I have read myself and had varying degrees of success.

---

### Post by xly15 on 2012-01-18
I tried following the guide here [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149) to resolve some of the problems, but whenever I add wins to my /etc/networking/nsswitch my browser ends up taking forever to load webpages or does not load them at all. I have almost given up hope of ever getting this to work properly.

---

### Post by xly15 on 2012-01-18
I think for the most part now I have it working. Now I just need to resolve the issue of my windows 7 pc being able to only see one of linux computers at a time.

---

### Post by xly15 on 2012-01-20
Even though the shares never show up in network pane in on windows 7 I have gotten it to work. Mapped network drive for the win.

---

