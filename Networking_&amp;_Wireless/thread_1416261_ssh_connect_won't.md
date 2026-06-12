---
title: "ssh connect won't"
date: 2010-02-25
forum: Networking &amp; Wireless
---

### Post by wgcampbell on 2010-02-25
I have a remote network where I can access one of the machines (actually through a reverse ssh tunnel).  Anyway, I am able to successfully access that machine and get to a shell prompt.

On that same private network, there is a small [server machine] that records motion and temperatures.  Until the other day, I was able to ssh to that [server machine] with a simple ssh command:  ssh geoff@192.168.11.55

Now, I'm getting:


```
guest@rdesktop:~$ ssh -vvv geoff@192.168.11.55
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.11.55 [192.168.11.55] port 22.
debug1: connect to address 192.168.11.55 port 22: Connection refused
ssh: connect to host 192.168.11.55 port 22: Connection refused
```

My problem is that this network is remote (very remote) and I can't get there to login directly.  I'm suspecting that maybe the sshd process is down or needs to be reset.  I've googled "ssh_connect: needpriv 0" but can't find what that is telling me.  Also, currently the  [server machine] is keeping a reverse ssh tunnel connection alive with one of my local machines - but I can't access through that connection either.

I'm fearing that sshd needs to be restarted, but I can't get there without a 1200 mile plane ride.

Anyone have any suggestions?  With that reverse tunnel established, is there any other way to access a shell on the [server machine]?

---

### Post by dmizer on 2010-02-25
Are you connected to the 192.168.11.x network via VPN or some other remote access protocol? If not, then your problem is that you're trying to ssh into a local network over the internet.

The 192.168.x.x IP range is what's called a [non routable IP address]("http://wiki.answers.com/Q/What_is_a_nonroutable_IP_address"). This means it cannot be accessed over the internet.

---

### Post by wgcampbell on 2010-02-26
> Are you connected to the 192.168.11.x network via VPN or some other remote access protocol? If not, then your problem is that you're trying to ssh into a local network over the internet.

I can connect to another machine [rdesktop] on the remote network through a reverse ssh connection.  So I should be able to connect from that remote shell [rdesktop] to the [server machine] through an ssh connection.

I can ping the [server machine] from that shell [rdesktop], and as I mentioned I know the [server machine] is still alive since it is also maintaining a reverse ssh connection with one of my local machines.

What I'm really after here is some way to definitively determine whether or not sshd is active on the [server machine] and specifically what "ssh_connect: needpriv 0" would indicate.  Does that message come from sshd?

Or, since I'm still maintaining this reverse connection from the [server machine] then is there some other way to access the [server machine] through that reverse connection other than ssh?

---

