---
title: "Two Network issues (remote SSH and Rsync) Please help :-0"
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by eddyg on 2009-04-19
Hey guys I'm trying to learn a litte bit about LAMP and getting it all started. I have the four components installed and they seem to be working but now I have an issue. 

1. If I use putty to SSH into my local server on IP 192.168.1.3 on port 22 its not a problem. I can login and control the system fine. BUT when I try to use my external IP 68.150.174.XXX I get connection refused (I have setup Port Forwarding in my router config to forward all port 22 connections to 192.168.1.3). How can I set this up so I can have remote access to it over the internet? 

2. The reason for the machine is to receive backups from a remote web server. I want to use rSync on my remote machine to send the backups to this machine. How can I go about doing that in plain English? Ive done a ton of googling and honestly I get so many different commands and whatnot that I don't know what to use. Can someone give me a brief explanation? 

Best regards and keep up the good work.

---

### Post by riseringseeker on 2009-04-19
> **eddyg said:**
> Hey guys I'm trying to learn a litte bit about LAMP and getting it all started. I have the four components installed and they seem to be working but now I have an issue. 

1. If I use putty to SSH into my local server on IP 192.168.1.3 on port 22 its not a problem. I can login and control the system fine. BUT when I try to use my external IP 68.150.174.XXX I get connection refused (I have setup Port Forwarding in my router config to forward all port 22 connections to 192.168.1.3). How can I set this up so I can have remote access to it over the internet? 

2. The reason for the machine is to receive backups from a remote web server. I want to use rSync on my remote machine to send the backups to this machine. How can I go about doing that in plain English? Ive done a ton of googling and honestly I get so many different commands and whatnot that I don't know what to use. Can someone give me a brief explanation? 

Best regards and keep up the good work.

I'm a long way from being an expert with this stuff, but do routinely access my desktop from the `net.

I am going to guess that the router is blocking port 22.  Not a problem if you are on the local network, but will stop you from doing it over the `net.  Unblock port 22 in the router, and for security with it opened, consider using something like DynDNS and DenyHosts, both of which can be found in the repositories.

---

### Post by superprash2003 on 2009-04-19
ensure that port 22 is open using this online port scanner [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

---

### Post by eddyg on 2009-04-19
Ok its not responding so it is blocked... Weird because I was just in the router config page and It didnt mention anything was blocked in terms of ports. 

I dont want any DNS added to this server just the IP address its only going to be used for backups anyhow. 

How can i open port 22 on my router? I checked the settings and it didnt mention that it was even blocked.

---

### Post by eddyg on 2009-04-19
I wonder if there is something blocking it on the server side? (backup server) maybe a firewall or something that doesn't allow outbound connections to SSH?

---

### Post by StuartN on 2009-04-19
> **eddyg said:**
> 2. The reason for the machine is to receive backups from a remote web server. I want to use rSync on my remote machine to send the backups to this machine. How can I go about doing that in plain English?

Here is a simple example. I have a Buffalo Linkstation and on that machine I have edited the file /etc/rsyncd.conf to say:

```
uid = Stuart
gid = hdusers
use chroot = yes
[Stuart]
  comment = Stuart's rsync
  path = /mnt/disk1/Stuart/
  list = yes
  read only = no
```

Which means user Stuart in group hdusers can run rsync. The block starting [Stuart] specifies a path to which Stuart can send rsync backups. The rsyncd.conf file can specify multiple users and multiple backup destinations. That is the complete setup on the receiving machine. You can get all the detail from man rsyncd.conf.

Now I can run the following command on any networked machine that I am logged in at:

```
rsync -avh --delete ~/Documents/ rsync://Stuart@192.168.1.111:/Stuart/Documents/ >> backup.log
```

This syncs in verbose archive mode and also deletes any files on the receiver that are not on the sender, so my Documents and all subfolder are identical in both machines.

---

### Post by riseringseeker on 2009-04-19
> **superprash2003 said:**
> ensure that port 22 is open using this online port scanner [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

nmap (in the repositories) will also let you know what ports are open on all computers on a network.

---

### Post by riseringseeker on 2009-04-19
> **eddyg said:**
> Ok its not responding so it is blocked... Weird because I was just in the router config page and It didnt mention anything was blocked in terms of ports. 

Most ports are blocked by default, and need to be opened with whatever tool the manufacturer gives you to do that with.  With the belkin that I use, it's a web interface where the web address of the router is [http://192.168.2.1](http://192.168.2.1).  I go to the firewall section and virtual servers to open/change open ports.

> I dont want any DNS added to this server just the IP address its only going to be used for backups anyhow. 

I think you misunderstand what DynDNS is.  It's a free service that will allow you to have a domain name for your IP address.  Most providers do not give static IP addresses without charging a large premium.  

With DynDNS (there is at least one other service out there who's name escapes me at the moment) you can have a domain name say eddyg.homelinux.org that will point to you IP address even if/when it changes.  You will have to set up ddclient for this as well, but it's pretty simple to do and in the repositories.

DenyHosts is a great security tool.  Since you have a port open, it ***will*** be attacked, not a question of if.  DenyHosts watches attempted logins and bans ones under a set of configurable rules set with a text file.  Again something fairly easy to set up, available in the repositories and a current, well supported (and thought of) way to frustrate hackers trying to gain access to your system.

> How can i open port 22 on my router? I checked the settings and it didnt mention that it was even blocked.

A google seach of your router model will likely give you the quickest results on the how-to.  What router are you using?  Many do have a web style interface, trying pointing firefox to the router (broadcast) local IP address.

---

### Post by eddyg on 2009-04-19
thanks for the quick replies guys! 

I've been inside the config area for my router (which is a NETGEAR WGR614v7). Under "block services" ive checked "never" and also in port forwarding I have ports 80, 22, 20, and 21 forwarding to this server. 

I understand the DNS a little better now I've signed up for a free account and setup the hostname "eddyg.homeip.net" but in order to activate it I think I need to checkout / pay? Are there free services that will do this? 

Also when I do get the dns for this server will I be SSHing into that domain and not the IP address? I'm assuming thats the reason for this DNS so that I dont have to record/check my changing IP address. 

best regards, 
Eddy

---

### Post by eddyg on 2009-04-19
ok i signed up for another DNS service but it seems like I HAVE to use DyDNS because thats the only option under "dynamic DNS" for my router. Is that true? 

I registered eddyg.mooo.com (with freedns.afraid.org) which points to my IP address. What now?

---

### Post by riseringseeker on 2009-04-19
> **eddyg said:**
> thanks for the quick replies guys! 

I've been inside the config area for my router (which is a NETGEAR WGR614v7). Under "block services" ive checked "never" and also in port forwarding I have ports 80, 22, 20, and 21 forwarding to this server. 

21 is for ftp, doubt you need that for what you've described, but it's your system, and it could be useful, can't recall what 20 is for, but I assume you do.

> I understand the DNS a little better now I've signed up for a free account and setup the hostname "eddyg.homeip.net" but in order to activate it I think I need to checkout / pay? Are there free services that will do this? 

(Disclaimer) I am not shilling for them, but I have used them and recommend them - I don't make a dime from it.

DynDNS is a free service for what it sounds like you want to do - be able to access your server from outside the local network without having to know the IP address.  Click [here]("http://www.dyndns.com/services/dns/dyndns/") and it will take you to the page to set up a free account.  

You will then have to set up ddclient (available in the repositories, and a wizard to set it up is on DynDNS.com), this will be what keeps track of your IP address and keeps the name pointing to the right place.

> Also when I do get the dns for this server will I be SSHing into that domain and not the IP address? I'm assuming thats the reason for this DNS so that I dont have to record/check my changing IP address. 

Either way will work, but since you have a name, may as well use it.

---

### Post by riseringseeker on 2009-04-19
> **eddyg said:**
> ok i signed up for another DNS service but it seems like I HAVE to use DyDNS because thats the only option under "dynamic DNS" for my router. Is that true? 

Hmmm, I wouldn't think your router would care (mine sure doesn't).  All DynDNS does is give a name to the IP address, and there are others that do the same for free, or a fee.

> I registered eddyg.mooo.com (with freedns.afraid.org) which points to my IP address. What now?

As I said before, I know there are other services out there, just don't know what they are, or honestly how to use them or set them up - maybe someone else can chip in with various names of other services and offer advice.  

I use DynDNS because everything I need to setup and run it (don't overlook DenyHosts) is in the repositories and runs great with *buntu.

---

### Post by eddyg on 2009-04-19
OK i see what everyones saying hehe I managed to find out how to do the actual DNS im now using DyDNS under [http://eddyg.webhop.biz/](http://eddyg.webhop.biz/) pointing to my IP address and it has updated. I forward these ports because I was testing some things on the server so Im using HTTP FTP and SSH (ill get rid of port 20 lol). 

does this take awhile to start? Also do i use this domain in my putty to connect to the server? Ill give that a try now.

---

### Post by eddyg on 2009-04-19
OK now I cant even connect to the server locally on 192.168.1.3 :-/ (Putty on Vista trying to connect to the backup server locally)

I restarted the service as well still no luck. 

what happened? lol

---

### Post by ktrnka on 2009-04-19
Try and see if ssh is running on your server:

```
ps wax | grep sshd
```

If you only see grep sshd then ssh server failed to start and something is probably wrong in your sshd_config file.

---

### Post by riseringseeker on 2009-04-20
> **eddyg said:**
> OK now I cant even connect to the server locally on 192.168.1.3 :-/ (Putty on Vista trying to connect to the backup server locally)

I restarted the service as well still no luck. 

what happened? lol

From a terminal on the server you can also try:
 
```
/etc/init.d/ssh status
```

If it says it's running, look to see if the local IP address is still 192.168.1.3 either with ifconfig on the server, or 

```
nmap -sP 192.168.1.1-255
```

or 

```
sudo nmap -O 192.168.1.1-255
```

from any (Linux) machine on the LAN.

---

