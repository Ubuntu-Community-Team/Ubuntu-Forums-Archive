---
title: "nmap configuration file"
date: 2013-01-20
forum: Networking &amp; Wireless
---

### Post by Slimmons on 2013-01-20
Hi, I need to modify my nmap config file, and I can't seem to find the correct config file.  I need the default service enumeration to output ftp, telnet, ssh, etc...  I know the command to run what I want, but I really just need to edit the config file to do it automatically when i run nmap.  The command is:

nmap -sV -p 20,23,22,80,443,69,587 192.168.1.1-255 --timing insane

can anyone point me in the right direction to even find the nmap config file?
I've tried usr/share/nmap but nothing there seems to  be the config file.  Please tell me if I'm wrong.  Thanks,

---

### Post by Cheesemill on 2013-01-20
I didn't think that nmap *had* a config file...

If all you need is quick access to that command then I would use an alias, just add the following line to your .bashrc file...
```
alias scan='nmap -sV -p 20,23,22,80,443,69,587 192.168.1.1-255 --timing insane'
```

Then you can just type the command 'scan' every time you need to.

---

### Post by haqking on 2013-01-20
[http://nmap.org/book/data-files.html](http://nmap.org/book/data-files.html)

---

### Post by Slimmons on 2013-01-20
So far what I've figured out is that nmap pulls its list of services from etc/services.  The alias command was a good answer for my question, but not quite what I'm looking for.  The reason I'm asking is because I have a school assignment that I've been working on, and I have a lot of it done, but this one question confuses the mess out of me.  I'm not sure about it because of the way it's written, and I'm trying to interpret it since I'm fairly new to the subject.  the question is:

Modify your nmap configuration of its default service enumeration by creating a new service list that is composed only of the following:  ftp etc.......

I think the answer is to actually change the etc/services file.  I'm only posting this in case someone runs across it and my question confuses them like I was.  Thanks for the responses, and If I'm still incorrect, please let me know.  Thanks agian!

---

### Post by haqking on 2013-01-20
> **Slimmons said:**
> So far what I've figured out is that nmap pulls its list of services from etc/services.  The alias command was a good answer for my question, but not quite what I'm looking for.  The reason I'm asking is because I have a school assignment that I've been working on, and I have a lot of it done, but this one question confuses the mess out of me.  I'm not sure about it because of the way it's written, and I'm trying to interpret it since I'm fairly new to the subject.  the question is:

Modify your nmap configuration of its default service enumeration by creating a new service list that is composed only of the following:  ftp etc.......

I think the answer is to actually change the etc/services file.  I'm only posting this in case someone runs across it and my question confuses them like I was.  Thanks for the responses, and If I'm still incorrect, please let me know.  Thanks agian!


Did you read the link I posted ?

Homework is not supported here though. NO dont edit your /etc/services file.

Anyways if you look in your nmap directory which on linux is /usr/share/nmap then you will find the nmap-services file

---

