---
title: "SSH : Connection refused"
date: 2013-02-13
forum: Networking &amp; Wireless
---

### Post by smss on 2013-02-13
Hi.
When I try to connect from the server to client, I faced with : 
```

smss@smss-network:~$ ssh smss@smss-desktop
ssh: connect to host smss-desktop port 22: Connection refused
smss@smss-network:~$

```
Whereas I connect from the client to server without any refused connections.
I done these :
- Add into two computers "/etc/hosts" computer names and IPs.
- Generating rsa SSH keys with "ssh-keygen -t rsa" and that steps...
- After I can establish SSH from the client to server, I copied client key's to server by "ssh-copy-id"
- And for first time, when I try to connect from the client to server, Asked from me the server password and server key added into client .
Also I copied a few things through "scp" from the client to server.
I using from the wireless network.
How to solve this connection refuse on server?
Thank you.

---

### Post by Doug S on 2013-02-13
Is the OpenSSH server running on the computer "smss-desktop"?
An example how to check (there are other ways also):```
doug@doug-64:~/tcpdump$ [COLOR=red]ps aux | grep sshd[/COLOR]
root       957  0.0  0.0  49956  2836 ?        Ss   Feb11   0:00 [COLOR=red]/usr/sbin/sshd -D[/COLOR]
root      2542  0.0  0.1 134512  6088 ?        Ss   Feb11   0:00 sshd: doug [priv]
doug      2721  0.0  0.0 134648  2352 ?        S    Feb11   0:01 sshd: doug@pts/0
root      4079  0.0  0.1 134512  6060 ?        Ss   Feb12   0:00 sshd: doug [priv]
doug      4265  0.0  0.0 134648  2372 ?        S    Feb12   0:01 sshd: doug@pts/1
doug      7044  0.0  0.0   9384   880 pts/1    S+   19:40   0:00 grep --color=auto sshd
```

---

### Post by lordievader on 2013-02-14
Is the ssh server listening to port 22?
You can see if something is listening to port 22 with the command:
```
netstat -lnpu|grep 22
```

If you have a line as follows:
```
0.0.0.0:22     0.0.0.0:*
```
There is something listening to port 22.

Hope this helps,
-lordievader.

---

### Post by SeijiSensei on 2013-02-14
Desktop Ubuntu does not come with an SSH server.  Install the **openssh-server** package and try again.

---

### Post by smss on 2013-02-14
Thanks, I install openssh-server package on "smss-desktop" and tried to connect from "smss-network" to "smss-desktop" again and it works.
Before, I checked the openssh-server running according to "Doug S" responed and openssh-server was not run.
Also I checked the 22 port based on the given advice, Then I checked the openssh-server to make sure it is being installed, but it was not. 
So I have to thanks from SeijiSensei for the recommandation that made it solved.
smss
[]("http://ubuntuforums.org/member.php?u=698195")

---

### Post by Doug S on 2013-02-14
> **lordievader said:**
> Is the ssh server listening to port 22?
You can see if something is listening to port 22 with the command:
```
netstat -lnpu|grep 22
```
 
If you have a line as follows:
```
0.0.0.0:22     0.0.0.0:*
```
There is something listening to port 22.
 
Hope this helps,
-lordievader.I realize this one is solved, but didn't you mean to say```
sudo netstat -lnp[COLOR=red]t[/COLOR] | grep 22
```Example (I have a local network at 192.168.122.XXX, so changed the grep command a little):```
doug@s15:~/iso$ sudo netstat -lnpt | grep ":22"
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1109/sshd
doug@s15:~/iso$ sudo netstat -lnpu | grep ":22"
doug@s15:~/iso$

```

---

### Post by lordievader on 2013-02-15
> **Doug S said:**
> ```
doug@s15:~/iso$ sudo netstat -lnpt | grep ":22"
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1109/sshd
doug@s15:~/iso$ sudo netstat -lnpu | grep ":22"

```

You're right, it should be a -t instead of a -u. Ssh is of course a tcp connection.

---

