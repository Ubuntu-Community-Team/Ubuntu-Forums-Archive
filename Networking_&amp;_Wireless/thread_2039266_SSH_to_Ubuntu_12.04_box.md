---
title: "SSH to Ubuntu 12.04 box"
date: 2012-08-08
forum: Networking &amp; Wireless
---

### Post by shanksjp on 2012-08-08
Hi all,

I recently upgraded my desktop from Ubuntu 10.10 to 12.04LTS. When running on 10.10, I had everything set up so I could SSH into my Ubuntu box using a DynDNS static address. 

However, after upgrading to 12.04LTS, I've started having SSH problems. Here is a list of things I've found not working so far:

1) "sudo service ssh start" claims to start a new process: 
```
ssh stop/pre-start, process 5358
```
...however, if I immediately follow that up with trying to stop or restart the process, I get the following:
```
stop: Unknown instance: 
```

I have confirmed that SSH is indeed installed (openssh-server and openssh-client). Additionally, I am able to do "ssh localhost" without any issues. I am not able to SSH from any other machine to the Ubuntu desktop.

Doing a ps aux | grep ssh yields only the "ps" itself:
```
shanksj   5376  0.0  0.0  13580   936 pts/2    S+   11:51   0:00 grep --color=auto sshd
```


2) I am able to ping my Ubuntu desktop's dynDNS address from my Windows laptop (on the same network, but pinging address.dyndns-remote.com). However, I am NOT able to ping the Ubuntu desktop from another (off-site) Linux machine.

I've been searching through forums for the past two days, without any luck. Thanks in advance for any suggestions!

---

### Post by TheFu on 2012-08-08
Could be all sorts if issues. At this point, it seems that your ssh-server installation isn't working right.  I say this because you can't find sshd running in the process table.  

```
\ps aux | grep sshd
```
The leading \ prevents an alias being used.

If sshd isn't running, it is probably worth purging the install and reinstalling it. Obviously, do this from a console, not over ssh. ;)

Also have to ask a few questions.

[LIST]
[*]if your router is forwarding the correct port from the internet to your internal ssh box?
[*]What does syslog say about ssh connections?
[*]What does the auth log say?
[*]Does the name you are using for the hostname resolve as expected? Can you ping it?  Name resolution changed in 12.04 - /etc/resolve.conf can't be edited directly anymore.
[*]Are you running fail2ban?
[*]Are you running a firewall that doesn't allow ssh inbound?
[*]In your sshd_config file, do you allow password-based logins, key-based logins or both? Do you prevent certain logins completely, like root?
[/LIST]
This [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)  might help improve ssh security, once you get this working.

---

### Post by shanksjp on 2012-08-08
> **TheFu said:**
> Could be all sorts if issues. At this point, it seems that your ssh-server installation isn't working right.  I say this because you can't find sshd running in the process table.  

```
\ps aux | grep sshd
```
The leading \ prevents an alias being used.

Agreed!

> If sshd isn't running, it is probably worth purging the install and reinstalling it. Obviously, do this from a console, not over ssh. ;)

Purge the SSH install, or the Ubuntu install? I'm kind of hoping I don't have to go to the extent of reinstalling Ubuntu (set up as a dual-boot, it was kind of a pain with one SSD and one standard HDD-- hence why I did an upgrade and not a clean install to begin with), but if that's what's necessary, I'll do it.

> 
Also have to ask a few questions.

if your router is forwarding the correct port from the internet to your internal ssh box?


Yep, verified it. I'm using a port other than 22, and the port is being forwarded from the router. The Ubuntu desktop is on a wired network with the router, with a static IP. 

> 
What does syslog say about ssh connections?
What does the auth log say?


Unfortunately I'm not too well-versed in Linux administration, so I don't really know what I'm looking for. If it helps at all, /var/log/auth.log has several entries along the lines of the following:

```

Aug  8 13:17:01 Calcifer CRON[5897]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug  8 13:17:01 Calcifer CRON[5897]: pam_unix(cron:session): session closed for user root

```

/var/log/syslog has several repeated entries (same entry, different time stamps) with:

```

Aug  8 12:40:12 Calcifer NetworkManager[1111]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)

```

Also, I've just noticed that under System Settings / Network, it claims "airplane mode" is on... anything to be concerned about?

> 
Does the name you are using for the hostname resolve as expected? Can you ping it?  Name resolution changed in 12.04 - /etc/resolve.conf can't be edited directly anymore.


The hostname being my DNS address (address.dyndns-remote.com)? Or the computer's name? (Again, sorry for the newbie-level clarifications needed) I am able to ping the dyndns address from another computer inside the network, as well as from the desktop itself. However, I *cannot* ping the Ubuntu desktop from another Linux box from outside the local network.

> 
Are you running fail2ban?
Are you running a firewall that doesn't allow ssh inbound?


Unless either of these are installed / running by default, they aren't present. UFW is disabled for debugging.

> 
In your sshd_config file, do you allow password-based logins, key-based logins or both? Do you prevent certain logins completely, like root?


For now, I have both password-based and key-based logins enabled in sshd_config. My hope is to disable password-based, and go to strictly key-based. Does this seem reasonable? PermitRootLogin is disabled.

> 
This [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)  might help improve ssh security, once you get this working.

Thanks for the reference!

---

### Post by TheFu on 2012-08-08
Sorry, just purge ssh-server, then reinstall it.  For something like this, reinstalling the OS would be 1000x overkill. ;)

BTW, installing fail2ban is a really, really good idea at this point.  If you aren't trying to ssh in as root, then someone else is. It would be good to block them after  a few failed attempts.  Fail2ban sorta just works out of the box. You can tweak the settings if you like, but the defaults are reasonable for inbound ssh.
```

sudo apt-get purge ssh-server
sudo apt-get install ssh-server fail2ban
```That should do it.

The package might be named "openssh-server".

I sorta hope that this doesn't fix the issue, since this assumes something was fouled up before, somehow.

---

### Post by shanksjp on 2012-08-08
> **TheFu said:**
> Sorry, just purge ssh-server, then reinstall it.  For something like this, reinstalling the OS would be 1000x overkill. ;)

BTW, installing fail2ban is a really, really good idea at this point.  If you aren't trying to ssh in as root, then someone else is. It would be good to block them after  a few failed attempts.  Fail2ban sorta just works out of the box. You can tweak the settings if you like, but the defaults are reasonable for inbound ssh.
```

sudo apt-get purge ssh-server
sudo apt-get install ssh-server fail2ban
```That should do it.

The package might be named "openssh-server".

I sorta hope that this doesn't fix the issue, since this assumes something was fouled up before, somehow.

So I've done as suggested, and did the purge / reinstall of openssh-server, as well as installing fail2ban. No change in symptoms:

-Unable to ping Ubuntu desktop from outside local network (but still able to ping dynDNS address from a computer inside the network)
-Unable to start SSH process (as shown by ps aux | grep sshd)

Good to rule out the easy stuff first, though.

---

### Post by sulemanhasib43 on 2012-08-09
purge and re install worked for me!

---

### Post by TheFu on 2012-08-09
> **shanksjp said:**
> 
-Unable to ping Ubuntu desktop from outside local network (but still able to ping dynDNS address from a computer inside the network)
-Unable to start SSH process (as shown by ps aux | grep sshd)

Good to rule out the easy stuff first, though.

Well, you need to figure out why sshd isn't starting. What do the log files say?
```
sudo egrep -i sshd /var/log/*log|more
```
Is where I'd start after a fresh reboot.  auth.log and fail2ban.log are the most interesting on my boxes, but dmesg and syslog could have data too.

BTW, the pings on the internet are only getting to your router, not the PC.

---

### Post by shanksjp on 2012-08-09
Output of the suggested egrep is below, after a fresh boot. I've tried to only include the relevant entries written after the the boot.

```

/var/log/auth.log:Aug  9 23:04:45 Calcifer sshd[858]: Received signal 15; terminating.
/var/log/auth.log:Aug  9 23:04:45 Calcifer sshd[1055]: Server listening on 0.0.0.0 port 2222.
/var/log/auth.log:Aug  9 23:04:45 Calcifer sshd[1055]: Server listening on :: port 2222.
/var/log/auth.log:Aug  9 23:05:26 Calcifer sudo:  shanksj : TTY=pts/1 ; PWD=/home/shanksj ; USER=root ; COMMAND=/bin/egrep -i sshd /var/log/alternatives.log /var/log/auth.log /var/log/boot.log /var/log/boots
trap.log /var/log/dpkg.log /var/log/fail2ban.log /var/log/faillog /var/log/fontconfig.log /var/log/jockey.log /var/log/kern.log /var/log/lastlog /var/log/mail.log /var/log/pm-powersave.log /var/log/pycentral
.log /var/log/syslog /var/log/ufw.log /var/log/Xorg.0.log
/var/log/auth.log:Aug  9 23:05:52 Calcifer sudo:  shanksj : TTY=pts/1 ; PWD=/etc/ssh ; USER=root ; COMMAND=/usr/bin/vi sshd_config
/var/log/auth.log:Aug  9 23:06:11 Calcifer sudo:  shanksj : TTY=pts/1 ; PWD=/etc/ssh ; USER=root ; COMMAND=/bin/egrep -i sshd /var/log/alternatives.log /var/log/auth.log /var/log/boot.log /var/log/bootstrap.
log /var/log/dpkg.log /var/log/fail2ban.log /var/log/faillog /var/log/fontconfig.log /var/log/jockey.log /var/log/kern.log /var/log/lastlog /var/log/mail.log /var/log/pm-powersave.log /var/log/pycentral.log 
/var/log/syslog /var/log/ufw.log /var/log/Xorg.0.log


```

I'm not really sure what I'm looking for, or what would even look anomalous in this output... any thoughts?

---

### Post by TheFu on 2012-08-10
sshd is running on a non-standard port, 2222 according to the logs. Are you really certain it isn't running?
\ps aux | grep sshd

Running on a non-standard port is fine, but it means you always need to force every client to use that port too. You'd also need to forward the ssh port from the router to the IP:2222 or this will never work. To me, that's the hard way.

Are you doing all those things?

Honestly, a better way to handle the non-standard port for ssh is at the router, but still leave the ssh server running on the default port, 22, internally. This will make life easier on your LAN, and you'd only need to worry about the non-standard port at the router and when you are remote.   A good way to deal with that is in the ~/.ssh/config file per host settings. [http://www.linuxjournal.com/content/use-sshconfig-simplify-your-life](http://www.linuxjournal.com/content/use-sshconfig-simplify-your-life) explains.

Not all routers support port translations - ext_IP:2222 to int_IP:22, so you might be stuck. I know some Netgear routers do not. I've never seen a Linksys that couldn't do the port translation and if your router is running dd-wrt or tomoto or open-wrt, port translation is easy.

---

### Post by shanksjp on 2012-08-11
Oddly enough-- now it seems to be running, as you pointed out. And on the correct port (2222, which is what I had tried to set previously, and had been forwarding from my Linksys router when I had 10.10 installed). Perhaps when I was running updates, something in there fixed it? 

Either way, thanks for your assistance!

---

