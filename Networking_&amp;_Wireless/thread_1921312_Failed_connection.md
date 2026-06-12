---
title: "Failed connection"
date: 2012-02-06
forum: Networking &amp; Wireless
---

### Post by bluegti02 on 2012-02-06
Alright, I've recently switched to Verizon FiOS 3 months ago and I have a Dell Latitude X1 laptop running Ubuntu 11.10 server edition. I mainly use it as an FTP server but wanted to setup OpenSSH. I went to download it and the connection failed. I then tried pinging google ```
ping www.google.com 
``` and it failed as well. It says 

```
ping: unknown host [www.google.com]("http://www.google.com/")
```What is strange is that I can connect to my FTP server from an outside network at least last week it did. I only have one setting set on my router to allow the ftp through. I cannot get my laptop running server 11.10 out to the Internet. I need to do updates and download OpenSSH server and client. What can I do?  I think its my laptop since I've tried the cable its plugged into on another computer and it works fine. 

On a side note, if the mods want I can create a new thread for this. I wish to setup the WiFi on this laptop but have no idea how to install the WiFi drivers through command line in Linux if its even possible.

---

### Post by barong234 on 2012-02-06
add the firmware to the kernel and install your driver. reboot your machine it should work. and about your connection, is all in your router and firewall setting.

---

### Post by bluegti02 on 2012-02-07
barong234 thanks for your reply but unfortinatly, I am a windows dude converting to ubuntu so not really sure what you said :D

Why do you think its router if I take the same cable and test it on another computer and it works fine?

---

### Post by bluegti02 on 2012-02-07
alright nevermind about the connection issue...i tried to change my config back to dhcp and it didnt work so i changed it back to my static settings and now I have web access....

---

### Post by Iowan on 2012-02-07
> **bluegti02 said:**
> 
On a side note, if the mods want I can create a new thread for this. I wish to setup the WiFi on this laptop but have no idea how to install the WiFi drivers through command line in Linux if its even possible.It'd be easier to attract the help you need it the title described the problem... so I'd recommend a new thread for the WiFi problem.  Also, when/if your problem is solved, [here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") is the way to mark it [SOLVED].

---

