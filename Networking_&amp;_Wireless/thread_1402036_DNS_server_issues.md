---
title: "DNS server issues"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by matt897 on 2010-02-08
Hi, i'm new to Gnome/Ubuntu and i'm using version 9. Actually its a distro called ABC Linux which has the ability to automatically create Beowulf clusters. 

I'm having a hard time changing the DNS servers for the nic. This machine is being used on a business LAN and must connect to the DNS server in order to reach the internet. 
I know i somehow have to edit the file called etc/resolv.conf however it doesn't let me. I need root access.

Can someone please help me with the terminal commands i need to use so i an edit this?  Like i said, i'm not familiar with Linux terminal at all and would appreciate the steps verbatim. 


Thanks!!!!

---

### Post by davec64 on 2010-02-08
I'm not familiar with ABC linux, is a Ubuntu derivative?

If so, it will probably have the sudo command available, so at the terminal prompt try:

```
sudo <editor of choice> etc/resolv.conf 
```

If you've got a graphical desktop you could use "gedit" for your editor or "nano" if it's a server install without a graphical desktop.

Enter your login password and the file should open for editing.

Hope that helps! :)

---

### Post by matt897 on 2010-02-08
hmmm ok well i tried that and it did open the text editor properly but its opening it in /home/username/etc instead of the etc folder on the file system....any thoughts?


Thanks btw for the help!!!!!!!!!

---

### Post by Iowan on 2010-02-08
Try it as ```
sudo nano [COLOR="Red"]/[/COLOR]etc/resolv.conf
``` or, if you prefer (and machine has) a graphical editor```
gksudo gedit [COLOR="Red"]/[/COLOR]etc/resolv.conf
```

---

### Post by matt897 on 2010-02-08
ok the 'sudo nano /etc/resolv.conf' opened up an editor perfectly, i made the changes...pulled a ctrl X command to exit, it asked if i wanted to save the buffer and i said yes however it gives me a permission denied and won't save it.
thanks in advance

---

### Post by Iowan on 2010-02-08
Are you running it "...in live mode or by installing the software in the front-end"?

[http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/ABC-GNU-Linux-52373.shtml]("http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/ABC-GNU-Linux-52373.shtml")

---

### Post by matt897 on 2010-02-08
If you mean am i running in from cd or hd? its installed onto the hd

---

### Post by Iowan on 2010-02-09
Yes, I suppose that was the question. I'm not sure how configuration changes are saved on a Live CD system.

I usually use CTRL-O to write out the file before I exit - but either way *should* work...

---

### Post by matt897 on 2010-02-09
Well i tried it again this time doing ctrl - o to write out and it gives me permission denied. This is the second time i've clean installed it, so i can't see it being a configuration issue especially since i haven't changed anything.....

Any further ideas? 


Thanks again!

---

### Post by Iowan on 2010-02-09
<Scratches head in confusion>
Unless ABC does things differently, that *should* work. I just tried editing my system via **sudo nano /etc/resolv.conf**, deleted a blank line, and saved via CTRL-O without problem... :confused:

---

### Post by matt897 on 2010-02-09
yea i looked into it more, turns out the immutable bit was set. I did a 
lsattr /etc/resolv.conf and found the output to be
 ------i----- 
so i ran a sudo chattr -i /etc/resolv.conf
This changed the permissions. I was able to then edit the resolv.conf perfectly fine!!

Only problem is after reboot, its gone back to what it was...... 
:-( I need to rerun these commands on reboot, plus the nic isn't exactly grasping an IP from the dns server (i assume it needs a reboot?)


Thanks for the help again!!!!!!!

---

### Post by Iowan on 2010-02-09
I'm glad you got the changes to take... I was a little concerned that the file might get overwritten - (what if you set tie immutable bit afterward?)

The NIC would either have static IP address, static lease (from DHCP server) or DHCP IP address - what IP would it grasp from DNS server?

---

### Post by matt897 on 2010-02-09
ok  i finally figured it out on my own. Thanks again for all the help. I was able to save the changes after i changed out the nic card...looks like it was holding up everything

Again, thanks for the quick responses!!!!!!!!!!!!!!!!!

---

