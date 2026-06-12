---
title: "processes using the internet"
date: 2006-04-30
forum: Networking &amp; Wireless
---

### Post by akudewan on 2006-04-30
Hi,

This is a little hard to explain.

Sometimes I notice that some mysterious process is downloading data from the internet. (gkrellm shows me that data is being downloaded, even though I'm not doing anything). This is probably just "apt-get update" running in the background. But is there any way to tell for sure which process are sending and receiving data from the internet?

I did a little research on this, and I found that "netcat" could probably help me out. But using it seems very complicated...Can someone help me out? Or is there a better/easier way?

Thanks in advance.

---

### Post by towsonu2003 on 2006-04-30
I use ```
sudo lsof -i -n
``` for that, but there is something called trojanscan which does a better job (in terms of readability). I don't have the link to it, but here is what its readme says: 
> 
Trojan scan is a simple shell script that allows for simple but relatively
effective checking for trojans, rootkits and other malware that may be using
your server and network for unwanted (and possibly illegal) purposes.

It works by listing all process that use the Internet with the lsof command
(using -Pni flags). This list is then transformed into signatures in the form
of <process_name>:<port_number>:<user>. These signatures then are matched
against the allowed process defined in the configuration. If any signatures of
running processes are found that do not match the allowed signatures, an email
report is sent including ps, ls, and optional lsof output (see also: lsof).
you can also use ethereal to monitor what your computer is doing. ethereal is in the repos (run it "as root" with sudo) while trojanscan is not.

---

### Post by akudewan on 2006-04-30
Wow, thats exactly what I needed :) 

For the record, this is the homepage of Trojanscan (did a google): [http://www.derks.it/tools.html](http://www.derks.it/tools.html)

Linux is so cool when it comes to these kind of things. Thanks towsonu.

---

