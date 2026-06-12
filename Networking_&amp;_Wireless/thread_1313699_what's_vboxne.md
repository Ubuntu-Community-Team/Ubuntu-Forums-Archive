---
title: "what's vboxne?"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by Ufogos on 2009-11-03
Hi, after installing ubuntu 9.10, I install virtualbox (non-free version) to run a vista machine, the question is why in firestarter appears besides the normal eth0 and eth1, this one:vboxne, you may thinks is because the vista machine has access to internet, but when a saw that, the virtual machine was shutdown and virtualbox too.
So if someone know something please let us know.

---

### Post by FreedomOverdose on 2010-08-21
+1!!

---

### Post by ryniek on 2011-02-14
I have the same question, so decided to reresh topic. I use Lucid and non-free VBox ver. 4.0.2 r69518. Lookin' @ Firestarter GUI, i can see that **vboxne** device already sent 5.9 MB, same amount as **eth0** which is handling jDownloader now. But i still don't know why vboxne is on, if no VM nor VirtualBox is running?
Can someone explain?

---

### Post by ryniek on 2011-02-19
I see, no one knows, that's why no replies i get.

---

### Post by GrouchyGaijin on 2011-03-27
bump

---

### Post by savaan on 2011-04-12
I'm getting the exact same thing running 10.10

---

### Post by Kuro Ame on 2011-04-23
I had the same question.   I did some searching and found that Virtual Box causing this to show up in the firewall.  I am not sure what it is doing there but when you uninstall virtual box it disappears.

---

### Post by Fily1982 on 2011-05-10
It's my opinion that VirtualBox clones statistics uploading, however can be removed modules that causes the problem; I use this command:
```
lsmod | grep vbox
```so you see the modules that creates a vboxne:
vboxnetadp
vboxnetflt
vboxdrv
then delete this modules with this command:

```
sudo rmmod vboxnetadp
```

```
sudo rmmod vboxnetflt
```

```
sudo rmmod vboxnetdrv
```

---

### Post by Fily1982 on 2011-05-10
to permanently remove the modules, you can create a script or use this command
```
sudo chmod -x /etc/init.d/virtualbox-ose 
```to restart the modules will no longer be loaded

---

### Post by TedinOz on 2011-06-10
Happening here too on 10.10. If these commands are done what will the effect on VirtualBox operation be, if any?

---

