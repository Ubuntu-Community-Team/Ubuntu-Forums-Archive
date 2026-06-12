---
title: "Cannot get open ssh server to work properly"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by noravanq on 2010-03-04
I have been trying to run open ssh server on ubuntu 9.10 (running on an iMac) so I can connect to it from my Windows Vista Laptop.

I have installed the openssh server. 
I went through the guide at
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
I just wanted password authentication, so didn't make any changes to the sshd_config file.

```
$ps -A | grep sshd

```
returns

```
 5603 ?        00:00:00 sshd
 5613 ?        00:00:00 sshd
 5672 ?        00:00:00 sshd

```
```
$sudo netstat --inet -lpn | grep sshd

```
returns

```
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      5603/sshd

```
By
```
$ssh -v localhost

```
I can successfully connect.

But I am not able to connect using my laptop running windows vista. I used a port scanner on the internet, and it says that

```
(MY IP ADDRESS) isn't responding on port 22 (ssh).

```

```
$sudo iptables -L 

```

returns

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain INBOUND (0 references)
target     prot opt source               destination         

Chain LOG_FILTER (0 references)
target     prot opt source               destination         

Chain LSI (0 references)
target     prot opt source               destination         

Chain LSO (0 references)
target     prot opt source               destination         

Chain OUTBOUND (0 references)
target     prot opt source               destination         

Chain ufw-after-forward (0 references)
target     prot opt source               destination         

Chain ufw-after-input (0 references)
target     prot opt source               destination         

Chain ufw-after-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-after-output (0 references)
target     prot opt source               destination         

Chain ufw-before-forward (0 references)
target     prot opt source               destination         

Chain ufw-before-input (0 references)
target     prot opt source               destination         

Chain ufw-before-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-before-output (0 references)
target     prot opt source               destination         

Chain ufw-reject-forward (0 references)
target     prot opt source               destination         

Chain ufw-reject-input (0 references)
target     prot opt source               destination         

Chain ufw-reject-output (0 references)
target     prot opt source               destination         

Chain ufw-track-input (0 references)
target     prot opt source               destination         

Chain ufw-track-output (0 references)
target     prot opt source               destination      

```


I searched for and tried many suggestions but none of them worked. For example I added a rule to iptables by

```
# iptables -A INPUT -p tcp --dport ssh -j ACCEPT
```

but that didn't help. After trying other things I reset iptables using $sudo iptables -F

I am on my university's network, but I don't think the network is doing any blocking since when I boot into OS X instead of Ubuntu and enable remote desktop I am able connect via ssh using my Vista laptop.

Any help trying to get this work is appreciated. Sorry for the long explanation of what I have tried. Some of it is probably completely irrelevant. I can't tell though since I don't understand very well this stuff.

---

### Post by r939ick on 2010-03-05
Can you describe the network topology?  How is the laptop connected to the iMac?

Can you ping the iMac's IP address from the laptop?

---

### Post by noravanq on 2010-03-05
The iMac is connected to the university network by LAN. The laptop connects by WiFi. 

Yesterday I was using sites like [http://www.whatismyip.com/](http://www.whatismyip.com/) to find my ip. They show my ip as 128.42.***.***
I tried to ping this ip per your suggestion, but got no replies. 

I checked the ip using 
```
/sbin/ifconfig
```
and it showed my ip as 10.70.**.***

Why are these different?

I tried to ssh using this 10.70.**.*** ip and it worked.

Thanks for your help.

---

### Post by Iowan on 2010-03-05
> **noravanq said:**
> Why are these different? The 10.X.X.X is the local IP address - (hopefully) not visible from the Internet. Somewhere along the way (router?), that address gets "translated" into the "external" 128.42.X.X address. There may be scores of computers on your "local" network that all (to the rest of the internet) look like they have the same 128.42.X.X address that you have.
[Here]("http://www.howstuffworks.com/nat.htm") is an article that probably explains it better than I do...

---

### Post by noravanq on 2010-03-05
Thanks both of you for your help. 

I figured it out. Basically this is what's going on. I can't access my office computer (the iMac) from outside the university network. I realized that I still have ssh access to the departmental server, so now I can ssh to the departmental server and then since I am already on the campus network, I can ssh my office computer. 

The main reason I wanted to do this is to access files. It's a pity I have to do it in two steps and without a GUI but at least it works.

Thanks again.

---

