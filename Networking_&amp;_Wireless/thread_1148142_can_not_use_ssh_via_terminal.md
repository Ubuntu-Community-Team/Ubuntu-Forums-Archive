---
title: "can not use ssh via terminal"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by gaixixon on 2009-05-04
hello, I am trying to ssh to a remote server via terminal console and got following error:
> teppy@BP:~$ ssh -D 1080 [email]abc@myserver.com[/email]
[email]abc@myserver.com[/email]'s password: 
bind: Cannot assign requested address
channel_setup_fwd_listener: cannot listen to port: 1080
Could not request local forwarding.


I am using Hardy 8.04.

---

### Post by version7x on 2009-05-04
I'll take a stab at this and say it could be a permissions issue on the localhost or that the port you specified is already in use.

Take a look at your ports by issuing the following command -
```
netstat -anp |grep -w 1080
```

This should show you what's on that port(if anything), and also show some process info about what's using it.

If that doesn't give you anything useful, try executing your ssh command with sudo in front of it and use the "-l username" command to specify your username.
```
sudo ssh -l myuser -D 1080 abc@myserver.com
```

If that also doesn't work, post the output from the above two commands and we'll take a crack at those!

---

### Post by gaixixon on 2009-05-04
teppy@BP:~$ netstat -anp | grep -w 1080
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
teppy@BP:~$ sudo netstat -anp | grep -w 1080
[sudo] password for teppy: 
teppy@BP:~$ sudo ssh -l teppy -D 1080 [email]abc@myserver.com[/email]
[email]abc@myserver.com[/email]'s password: 
bind: Cannot assign requested address
channel_setup_fwd_listener: cannot listen to port: 1080
Could not request local forwarding.

---

### Post by version7x on 2009-05-05
Ok... here's my guess.  The only thing that looks plausible at this point is that your system may not have it's loopback device enabled.  SSH requires a loopback interface to enable tunneling.

Check /etc/network/interfaces for a commented out lo interface.

It should look like so:
```
auto lo
iface lo inet loopback
```

One other thing... I wasn't paying attention.  You don't have to use the user@server if you're using the -l user convention... you can go with either one.

---

### Post by gaixixon on 2009-05-10
my interfaces files looks exactly like yours but doesn't work.
thnx anyway..

---

### Post by Iowan on 2009-05-11
Maybe I don't understand what you're trying to do (ignore me in that case). To ssh to my server I use ```
ssh -p 1022 myadmin@mymachine
```

---

### Post by dmizer on 2009-05-12
Looks like port 1080 is reserved by something. Try a port other than 1080. I use 32768 for example. Are you able to ssh without the proxy switch?

---

### Post by gaixixon on 2009-05-26
I  change the port and it still doesn't work. I know for sure the problem is with the accepting the key from server.. but don't know how to work out.

---

### Post by cariboo on 2009-05-26
Are you sure the port is open? Install nmap, it is in the repositories, then in a terminal type:

```
nmap localhost
```

you should see whatever port you set in the output.

---

### Post by dmizer on 2009-05-26
UFW perhaps? On both the ssh server and client, run this command:

```
sudo ufw disable
```
And try to to ssh again.

---

### Post by Brandon Williams on 2009-05-26
Run ssh with the -v switch to get verbose output indicating what's going on. Post the resulting output if it doesn't immediately provide an answer.

---

