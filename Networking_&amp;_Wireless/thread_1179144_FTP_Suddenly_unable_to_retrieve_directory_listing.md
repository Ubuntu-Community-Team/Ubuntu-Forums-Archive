---
title: "FTP Suddenly unable to retrieve directory listing?"
date: 2009-06-05
forum: Networking &amp; Wireless
---

### Post by Ms_Angel_D on 2009-06-05
For quite some time I've been using Filezilla to upload/download files from my webhost, all the sudden I can't get a directory listing. No matter how I try to connect this happens. I have tried firefox, nautilus, fireftp and nothing will work, I just keep getting a time out error.

I contacted the isp and they said all their tests came back fine. I am able to navigate the site using Net2FTP but for some reason It just keeps timing out any other way.

I tried google and come up with nothing. Does anyone have any ideas as to what might be causing this and how I might fix it?

Thanks,
Angel

---

### Post by jonobr on 2009-06-06
Hello


The only way you can advance this problem (IMHO) is with a packet trace.

It sounds as if logging in is working but data transfer is not and Im thinking if you changed nothing or your end, its sounding as if your ISP is blocking FTP data.

FTP signaling goes on one port -21 known as the command port, and FTP data on port 20.

So as said above , the only way to get to the bottom of this is to sniff the packets,

You can do this two ways,
One is to install wireshark from synaptic , and trace the packets using the gui.
Or the other is to run a quick tcpdump to see whats going on and it may give you the answer.

You could run the following

tcpdump -vvv port 21

try logging in via ftp and see what happens and if you see packets going back and forth

then if your happy that its all working

try 
tcpdump -vvv port 20
to analyze the data port.

Login again ( you should see nothing as your sniffing on port 20 not 21 and then run your commands.

At the end of all this, you should be able to see if your packets are blocked by the ISP or if the remote end is not listening, or if your not sending packets in the first place

Cheers!

---

### Post by jonobr on 2009-06-06
Just to add,

I would also consider using sftp or scp as when you trace the ftp packets you will see everything - including username and passwords are transmitted in clear , easy to read text.

---

### Post by Ms_Angel_D on 2009-06-06
Hi Jonobr thanks for th reply,

I ran

tcpdump -vvv port 21 here's the output

```
angel@angel-desktop:~$ tcpdump -vvv port 21
tcpdump: no suitable device found
```

Also I should mention I spent the day re-installing windows, so I could flash my bios, then removing windows and re-installing ubuntu So I'm still having this issue on a fresh install.

Also I'm able to connect to other ftp servers with no problem and get a directory listing it's just this particular IP.

---

### Post by jonobr on 2009-06-06
Hello

Try doing an ifconfig 

you should see the device name, most likely eth0

try this

sudo tcpdump -vvv -i eth0 port 21

Or if you want shorthand you could type 

sudo tcpdump -vvv -i any port 21

I believer thats one whole letter less :-)

---

### Post by Ms_Angel_D on 2009-06-11
Hey guys, thanks for your help, but I am no longer having this issue, I enabled SSH on my hosting provider and they moved me to a new server to enable it. Since the move I can now access the host via both ftp & ssh.

Angel

---

### Post by jonobr on 2009-06-11
rock and roll

I would kick around wireshark and tcpdump as they are very useful troubleshooting tools which can help you immensly.

Cheers!!

---

### Post by dmizer on 2009-06-11
Just for curiosity's sake, I wonder if you had a firewall interfering:
```
sudo iptables -L
```

---

### Post by Ms_Angel_D on 2009-06-12
> **dmizer said:**
> Just for curiosity's sake, I wonder if you had a firewall interfering:
```
sudo iptables -L
```

```
angel@angel-desktop:~$ sudo iptables -L
[sudo] password for angel: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

---

### Post by dmizer on 2009-06-12
Well, that wasn't it :confused:. At least it's not a problem anymore.

---

### Post by Ms_Angel_D on 2009-06-12
Yeah I'm just glad I can connect and use it again.

---

