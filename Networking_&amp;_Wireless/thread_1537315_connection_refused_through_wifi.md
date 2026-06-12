---
title: "connection refused through wifi"
date: 2010-07-23
forum: Networking &amp; Wireless
---

### Post by Xyr2 on 2010-07-23
Hello everybody,
I cant connect with ssh to my workstation using my notebooks wireless lan. with cable I'm able to connect.

so the funny thing is, if I first establish a connection from my workstation to my notebook (like ssh it or just ping the notebook) I'm able to create a ssh connection from my laptop to the workstation using wireless lan. 

scanning my workstation from the wireless lan of my notebook with
```
nmap -sT -p 22 ventury
```says port 22 is closed

scanning it from the notebook with cable lan
it says port 22 is opened

scanning it from the wireless lan of my notebook an have sent a ping from the workstation before
says port 22 is opened

I've spent the hole day trying to fix this problem, and found some  threads where users had the same problem, but I couldn't find a  solution.

I got a 64bit version of Kubuntu 10.04, up to date, installed on both,  my workstation(ventury) and my notebook (defiant).

So the question is: Do I always have to ping my notebook first if I want to ssh from it to my workstation or is there some other solution? And why does it work fine with cable, but not with WiFi?

Thanks for your help

---

### Post by dca on 2010-07-23
Check your wireless router, mine @ home is only allowed to admin through cable, you can't access other workstation on net wirelessly or access router config wierelessly...
 
Should be just a click button to allow connections to other workstations, mine's a Cisco and I think it's under 'Wireless Security' settings...

---

### Post by Xyr2 on 2010-07-23
Thank you for your fast help, but II don't think that this is the problem, because  I'm able to connect to other machines in my LAN through the wifi of my notebook. My Workstation is the only machine that refuses connections through wifi:(

EDIT:
In this thread there was a similar problem, but they didn't came to a solution
[http://ubuntuforums.org/showthread.php?t=926928](http://ubuntuforums.org/showthread.php?t=926928)

---

### Post by dca on 2010-07-23
Still sounds like the router to me...  Is there a place in the router to set ports?  If router is set to allow connections between hosts on your network it generally looks for tcp/udp 137, 138, & another one, it's somewhere here thinking it's for DFS purposes between Windows:
 
[http://support.microsoft.com/kb/832017](http://support.microsoft.com/kb/832017)
 
...port 22 is special...
 
...the router assumes anything goes when connected via cable because you quote/unquote have physical access (as far as Linksys, et al are concerned)...

---

### Post by Xyr2 on 2010-07-23
but why I'm able to ssh to the 2 debian workstations in our LAN through the notebooks wlan, but cant ssh into my kubuntu workstation?
i can't imagine that it is a network bug. all 3 machines (my workstation and the 2 debian systems) are cabled and there are no differences between them in the router configuration. But only my kubuntu system refuses the connection through wlan. if it is a network issue, why does it work with the debian machines?

Is there any security option or something like that what refuses all connections coming from wlan in ubuntu?

---

