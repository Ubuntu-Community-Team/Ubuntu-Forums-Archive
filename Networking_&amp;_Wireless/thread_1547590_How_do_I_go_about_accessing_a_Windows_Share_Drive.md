---
title: "How do I go about accessing a Windows Share Drive?"
date: 2010-08-06
forum: Networking &amp; Wireless
---

### Post by s050399b on 2010-08-06
Hi,

I have a Windows server which has a shared drive; example: \\192.168.1.254\Movies

How can I access the movies from the shared drive from mythbuntu?

I have never use Linux before, and have no idea whats going on.....

---

### Post by Mia1990 on 2010-08-07
Samba file sharing i tried to set it up between 2 ubuntu pc's but it was slow samba is made for sharing between linux and windows here's a [guide]("http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/") about it.Good luck

---

### Post by s050399b on 2010-08-07
Perhaps I am not clear on my question?

I have a windows server which is sharing a path; \\192.168.1.254\movies


I need Mythbuntu to access that path.

How can I do that?

---

### Post by Mia1990 on 2010-08-07
Install samba on Mythbuntu to access the windows share.A quick google search on samba should tell you how to set it up.

---

### Post by s050399b on 2010-08-07
I'm a bit confused, I thought Samba server is installed on Linux to allow windows user to access file from Linux?......

---

### Post by s050399b on 2010-08-07
btw, I have found this post:
[http://ubuntuforums.org/archive/index.php/t-388194.html](http://ubuntuforums.org/archive/index.php/t-388194.html)

Can I use this?

Where can I find the terminal?

---

### Post by Mia1990 on 2010-08-07
it works from linux to windows and from windows to linux.you only need to set up samba look in synaptic and see if it is installed.

---

### Post by s050399b on 2010-08-07
where can I find synaptic?

---

### Post by Mia1990 on 2010-08-07
That looks about right i am not a samba expert but it should there is also a gui and a way to set it up under that but i can't remember how to do that.Sorry

---

### Post by s050399b on 2010-08-07
thanks Mia1990,
i'll try to find it

---

### Post by Mia1990 on 2010-08-07
systems->administration->synaptic package manager

---

### Post by s050399b on 2010-08-07
> **Mia1990 said:**
> systems->administration->synaptic package manager



Thanks! :)

---

### Post by Mia1990 on 2010-08-07
your welcome

good luck

---

### Post by s050399b on 2010-08-07
one more question:
in windows, if we want to know if the machine is alive, we using ping <ip address>


what is the command for linux?

---

