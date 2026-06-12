---
title: "Connecting Ubuntu to Windows Network"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by uzeshan on 2009-06-24
Hi

To start with, I am very new to Linux (Ubuntu). I have recently installed Unbuntu to 9.04.  and they is a windows network (all Win XP, Windows 2003 Server), . I manage to connect Ubuntu machine to my network and I can see Ubuntu machine from my PC and Ubuntu can see all my PC's and shared drive, so what is the problem.

The problem is that I cann't log in as network user but i can log in as local user. 

Is there any software or configuration i Need to do so i can log in as network user.

Ubuntu is a Brilliant OS and its Free.

Thanks

---

### Post by moody_mark on 2009-06-24
> **uzeshan said:**
> The problem is that I can't log in as network user but i can log in as local user.

Are you saying you want to login to and use a network account thats hosted on the windows server somewhere?

---

### Post by uzeshan on 2009-06-24
> **moody_mark said:**
> Are you saying you want to login to and use a network account thats hosted on the windows server somewhere?


yes

---

### Post by moody_mark on 2009-06-24
Ok, so im curious as to why you would need to do this? Here's my thinking, when I go to the office at work I can take this laptop running Ubuntu 8.04, plug into the LAN get an IP address on DHCP and access everything I need to. If you can see shares etc, what would the network account give you extra?

I think you'll find that you'll not be able to login to a windows network account on your Ubuntu laptop, you just configure users locally and then add shares and printers as you need them.

(Someone correct me if I'm wrong though)

---

### Post by uzeshan on 2009-06-24
Ok if you think its not possible then i won't bother. It was for just so that network users can pull their profile.

Thanks for ur help

---

### Post by vishnuvardan on 2009-06-24
try samba

apt-get install samba

---

### Post by uzeshan on 2009-06-24
I have already installed samba on it

---

### Post by blackxored on 2009-06-24
If you're new to ubuntu, I won't push you to samba and kerberos directly, you could try likewise-open, it's a one-command windows domain join.

---

### Post by uzeshan on 2009-06-24
where would i get likewise or is there any books or site where i can learn more abt ubuntu (network)

thanks

---

### Post by blackxored on 2009-06-24
```


sudo aptitude install likewise-open5


```and maybe the GUI, if you like it:

```

sudo aptitude install likewise-open5-gui

```hope you solve it.

It's pretty straightforward, if you need more info here's the upstream doc page: [http://www.likewise.com/resources/documentation_library/](http://www.likewise.com/resources/documentation_library/)

---

