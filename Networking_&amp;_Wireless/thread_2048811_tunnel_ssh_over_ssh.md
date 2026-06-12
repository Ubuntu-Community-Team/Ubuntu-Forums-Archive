---
title: "tunnel ssh over ssh"
date: 2012-08-27
forum: Networking &amp; Wireless
---

### Post by spiky001 on 2012-08-27
Hi  I have something I would like to solve. Pc with ssh server access internet(3g dongle) and lan via eth0 to hub, from hub to laptop1(ssh-client only) and laptop2(ssh-server). I want to go from laptop1 through pc to laptop2, at the moment by local lan.   I know I could ssh into pc then ssh to laptop2, is it possible to go through the pc (reason if i was to connect from outside internet).     Laptop1>>>>>pc>>>>>laptop2.   I have done this so far ```
ssh -p 1960 -fNL 8022:laptop3:22 server-user@server-fw
``` then this to connect```
ssh -p 8022 laptop-user@localhost
``` This is not correct, if I stop ssh server on pc I can still connect to laptop2

---

### Post by Lars Noodén on 2012-08-27
> **spiky001 said:**
> ... I want to go from laptop1 through pc to laptop2...

Something like this ought to do it.

```

ssh -o 'ProxyCommand=ssh %h nc *laptop2* 22' \
    -o 'HostKeyAlias=*laptop2*' \
    spiky001@pc

```

If the usernames are different on pc and laptop2, then some adjustments can be made.  If you don't want to type all that in each time you connect, then you can edit [~/.ssh/config](http://manpages.ubuntu.com/manpages/precise/en/man5/ssh_config.5.html)

```

Host jump
  ProxyCommand ssh %h nc *laptop2* 22
  HostKeyAlias *laptop2*
  Hostname *pc*
  User spiky001

```

That will make a shortcut called 'jump' and all you have to do is type [font=Courier New]ssh jump[/font] to take advantage of it.

---

### Post by spiky001 on 2012-08-27
ok I substituted the ip,s and port numbers. I have also tried the port number (spiky@10.42.43.1 1960). (spiky@10.42.43.1:1960) I have tried different options with port numbers    My ssh port is 1960 on all machines, all machines do connect if done seperatally. ```
ssh -o 'ProxyCommand=ssh %h nc 10.42.43.100 1960' \ -o 'HostKeyAlias=10.42.43.100 1960' \ spiky@10.42.43.1:1960
```    I get ```
command-line line 0: garbage at end of line; 1960.
``` All usernames are the same on all machines

---

### Post by Lars Noodén on 2012-08-27
The extra 1960 is probably what is causing the trouble with [ssh](http://manpages.ubuntu.com/manpages/precise/en/man1/ssh.1.html).

```

ssh -o 'ProxyCommand=ssh %h nc 10.42.43.100 1960' \
    -o 'HostKeyAlias=10.42.43.100' \ 
    -p 1960 \
    spiky@10.42.43.1

```
That's my next guess.

---

### Post by spiky001 on 2012-08-27
Thks Lars all works as predicted, 1 change was port number on pc```
ProxyCommand=ssh -p 1960 %h nc 10.42.43.100 1960'
```

---

### Post by spiky001 on 2012-08-29
Hi

Ok the tunnel command works good. I have been trying to expand on it with scp, I have tried numerous combinations to many to list. example

```
scp -o 'ProxyCommand=ssh -p 1960 %h nc 10.42.43.100 -P 1960:/path2file /destinationpath
```I know I have to use "-P" for scp.
  I did think think that with abit of playing with command I could get it to work but it appears not. :mad:

---

### Post by Lars Noodén on 2012-08-30
For scp, this should work:

```

scp  -o 'ProxyCommand=ssh -p 1960 %h nc 10.42.43.100 1960' \
     -o 'HostKeyAlias=10.42.43.100' \
     spiky@10.42.43.1:/path/to/file /destination/path/to/file/

```

I would still recommend using SFTP as described above that works and allows multiple actions per connection. Because making new connections is bit of hassle, that makes it a lot more efficient than scp if you are copying more than one item/pattern.

---

### Post by spiky001 on 2012-08-30
Hi Lars Noodén  That worked fine, How do you mean use sftp in the above?

---

### Post by Lars Noodén on 2012-08-31
Substitute [sftp](http://manpages.ubuntu.com/manpages/precise/en/man1/sftp.1.html) for scp or ssh in the working setup.

```

 sftp -o "Port=1960" \   
      -o 'ProxyCommand=ssh %h nc 10.42.43.100 1960'  \
      -o 'HostKeyAlias=10.42.43.100' \
      spiky@10.42.43.1

```

That allows you do more things, if you need to, on a single connection.

---

### Post by spiky001 on 2012-08-31
Hi   Thks Lars all works great.

---

### Post by Lars Noodén on 2012-09-01
Excellent.  Looking at it again, I think it can be shortened by one line.

```

 sftp -o 'ProxyCommand=ssh -p 1960 %h nc 10.42.43.100 1960'  \
      -o 'HostKeyAlias=10.42.43.100' \
      spiky@10.42.43.1

```

---

