---
title: "Trying to set up a scan to a network folder."
date: 2012-10-17
forum: Networking &amp; Wireless
---

### Post by MadMcGlory on 2012-10-17
Hi i'm quite new to Linux. I am trying to sort out our HP officejet pro 8500a plus printer to enable it to scan to a network folder rather then the e-mail method it can use which in our small office can bottleneck our internet usage. We are using Ubuntu 10.04.

The issue is that its asking for a network path but when I use a Linus path it wont accept it. I have added a picture so you can see the screen i'm trying to enter the path into. How should this network path be set up, what is the windows path for the networked folder on our Ubuntu server?

Thank you.

---

### Post by SlugSlug on 2012-10-17
your slashes are wrong for a network path

it shoudl be \\192.168.1.17\path\to\share

is there a share setup on 192.168.1.17?   You would need samba if its a linux box

---

### Post by MadMcGlory on 2012-10-18
Thank you for your speedy response.

How do I go about creating a share for that Ip as I've not done much with Linux or Samba before. When you say Linux box you mean a Linux server right? and not duel boot?

---

### Post by MadMcGlory on 2012-10-22
Ok I can set up a samba shared network folder on my Ubuntu server and I can connect to it but not with the scan to function on my HP.

Any ideas.

---

### Post by SlugSlug on 2012-10-22
not sure, 

I'd take a look at the logs in /var/log

---

### Post by MadMcGlory on 2012-10-23
Its fine I've solved the issue, I was putting the full path when all it wanted was \\192.168.1.17\scan and not the middle part of the path.

---

