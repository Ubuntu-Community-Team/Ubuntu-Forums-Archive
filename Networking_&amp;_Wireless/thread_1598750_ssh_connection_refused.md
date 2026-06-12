---
title: "ssh connection refused"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by tonymoloney on 2010-10-16
I'm feeling helpless here. I've read the manuals, checked the forums etc. but still no luck.
I have a laptop and a desktop connected to my router.
I know the uname and the hostname of each computer. I also know the IP address of each computer and on top of that, I can ping each computer from the other.
However, when I ssh <uname>@<IP address> I get "connection refused".
I also get the following message when I nmap localhost:

tony@tony-laptop:~$ nmap localhost

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-10-17 10:54 WST
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 999 closed ports
PORT    STATE SERVICE
631/tcp open  ipp

Nmap done: 1 IP address (1 host up) scanned in 0.12 seconds


Any ideas anyone?

---

### Post by SeijiSensei on 2010-10-17
Did you install openssh-server?  It doesn't come by default on Ubuntu installations.  If there's nothing listening on port 22, then sshd isn't running.

Also the client command is "ssh -l user host" rather than "user@host".

---

### Post by msherman123 on 2010-10-17
> **SeijiSensei said:**
> Did you install openssh-server?  It doesn't come by default on Ubuntu installations.  If there's nothing listening on port 22, then sshd isn't running.

Also the client command is "ssh -l user host" rather than "user@host".

Seij is correct.  sudo apt-get install ssh

uname@ip will work just fine. ' ssh -l user host' is the equivalent and will do the same thing.

---

### Post by tonymoloney on 2010-10-17
Thanks guys. Sorry for the delayed response, but it seems that living in Western Australia is not the ideal situation for quick turn-around on a forum.
I did what you suggested and nothing changed. Maybe I need to reboot my computer first. I'll do that now and get back to you.

---

### Post by tonymoloney on 2010-10-17
> **tonymoloney said:**
> Thanks guys. Sorry for the delayed response, but it seems that living in Western Australia is not the ideal situation for quick turn-around on a forum.
I did what you suggested and nothing changed. Maybe I need to reboot my computer first. I'll do that now and get back to you.
Duh! Adding ssh to BOTH computers would be a much better idea wouldn't it.
OK. I've done that and now the problem is solved.
Thanks for the help.

---

