---
title: "SSH doesn't work any more"
date: 2010-01-29
forum: Networking &amp; Wireless
---

### Post by CHW on 2010-01-29
Hello,

My SSH connection doesn't work any more.

I have two Computers A and B, which are in the same home-network.

This morning a was still able to connect by SSH from A to B.
I did some general configuration on B so I might have messed up something,
but I have no clue what it could be, as, as far as I can remember only accessed the /usr/share folder.

Then I switched B off and worked on A. After some hours I restarted B again, but couldn't connect any more from A to B.

On A:

```
$ ssh myname@B
ssh: connect to host B port 22: Connection refused.
```

but on B:

```
$ ssh myname@A
```
works.

After some testing I rebooted both A and B, without any result.
Also disabling the firewall on both A and B didn't change anything.

```
$ sudo ufw disable

```
Pinging from A to B and vice-versa works.

On A:
```
$ ssh localhost 
```
works.

But on B:
```
$ ssh localhost 
ssh: connect to host localhost port 22: Connection timed out
```

On A:
```
$ netstat -lnptu
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:65487           0.0.0.0:*               LISTEN      2208/wish8.5    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp6       0      0 :::139                  :::*                    LISTEN      -               
tcp6       0      0 :::22                   :::*                    LISTEN      -               
tcp6       0      0 ::1:631                 :::*                    LISTEN      -               
tcp6       0      0 :::445                  :::*                    LISTEN      -               
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           -               
udp        0      0 ***.***.***.***:137     0.0.0.0:*                           -               
udp        0      0 0.0.0.0:137             0.0.0.0:*                           -               
udp        0      0 ***.***.***.***:138     0.0.0.0:*                           -               
udp        0      0 0.0.0.0:138             0.0.0.0:*                           -               
udp        0      0 0.0.0.0:54162           0.0.0.0:*                           -       
```

But on B: 
```
$ sudo netstat -lnptu
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           992/avahi-daemon: r
udp        0      0 0.0.0.0:44693           0.0.0.0:*                           992/avahi-daemon: r
```

It seems that B isn't listening on port 22.

I hope I provided enough informations, I would be happy for any help! :)

Regards,
CHW

---

### Post by Skaperen on 2010-01-29
Make sure you didn't un-install the openssh-server package. You can check for the file /usr/sbin/sshd being present to verify that. If it is there, try this:```
sudo /etc/init.d/ssh restart
```to see if that will get the ssh daemon running. Watch for any error messages.

---

### Post by CHW on 2010-01-29
Thank you for your fast reply, but it seems to run:

```
sudo /etc/init.d/ssh restart
 * Restarting OpenBSD Secure Shell server sshd                           [ OK ] 
```

---

### Post by Iowan on 2010-01-29
Check **ls -al /etc/ssh** for modification times on the config files. I don't see why it would change, but **sshd_config** is where the server configuration data should be stored.

---

### Post by CHW on 2010-01-30
> **Iowan said:**
> Check **ls -al /etc/ssh** for modification times on the config files. I don't see why it would change, but **sshd_config** is where the server configuration data should be stored.

I checked, but the files didn't change.

But I have good news, I reinstalled every SSH packet with Synaptic and now I can reconnect again :) :) :)

Why is the simplest solution not the first one which came to my mind?...

Thank you for your support, I really appreciated it!

Regards,
CHW

---

### Post by CHW on 2010-01-31
Update:

The problem was still not solved, after each boot SSH was broken.
I did some more research and found this threat:

[http://ubuntuforums.org/showthread.php?t=1305226](http://ubuntuforums.org/showthread.php?t=1305226)

So it seems to be a bug.
Downgrading upstart fixed the problem for me.

Update: I could fix the bug, there was an entry missing in my /etc/network/interfaces file.
Adding this entry restored normal behavior. I could update upstart again.

---

