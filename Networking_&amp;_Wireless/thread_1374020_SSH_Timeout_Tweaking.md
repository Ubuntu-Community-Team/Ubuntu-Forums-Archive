---
title: "SSH Timeout Tweaking"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by abohsin on 2010-01-06
Hi everyone, I am asking this very much repeated question, but i didn't read a definite solution for it. I am an Ubuntu client connecting to remote machines using ssh from a terminal. When I connect for a few minutes it timesout and screen freezes. However, I installed putty ssh client, and in the properties of the connection there is a keep alive option, which is very nice, any sessions opened using putty ssh with that option enabled does not time out, but i don't like putty (with all the respect) because i cannot group several sessions into one window as i can inside a terminal, it is an organizational issue, no offense. So i searched the net for similar parameters, installed openssh server, adjusted following parameters in /etc/ssh/sshd_config (TCPKeepAlive yes, ClientAliveInterval 30, ClientAliveCountMax 99999) then restarted the sshd. However i still have the same problem persisting, when a session is open through terminal, it still freezes after sometime.

By the way I also checked the LoginGraceTime in sshd_config and it is set to 120, but I don't know if that is related or not. But with the above configs please suggest to me how i can keep the session alive until i actually choose to close it, it would be very helpful.

Thanks in advance and sorry for the extra details.

---

### Post by puppywhacker on 2010-01-06
I was a happy user of securecrt, but my new department doesn't have licenses. Putty is very good from the inside, but very poor on the outside. So when I have to use windows I use the putty connection manager on top of putty for pretty much the same reason as why you don't like putty

[http://puttycm.free.fr/](http://puttycm.free.fr/)

As for the TCPKeepAlive in ssh, I think it is a client setting, so you should add it in the /etc/ssh/ssh_config (not the ssh[COLOR="Red"]**d**[/COLOR]_config)

you can also run it (great for testing) as commandline option
```
ssh -o TCPKeepAlive=yes ssh.server.com
```

---

### Post by abohsin on 2010-01-07
Thanks for the note. I tried the command as you mentioned and left the session for sometime, it still timed out. So i used the following:
ssh -o TCPKeepAlive=yes -o ServerAliveInterval=60 servername.domain
The session stayed alive. Then I added these exact entries in /etc/ssh/ssh_config:
TCPKeepAlive yes
ServerAliveInterval 60

Things are now smooth, no need to restart any services or anything, just open a new 'ssh servername' command and the above options will apply to all new sessions.

Thanks for the hint.

---

### Post by kuthulu on 2010-02-23
if you use putty connection manager in windows then you may like this
[http://kuthulu.com/gcm](http://kuthulu.com/gcm)

it's a gui ssh/telnet manager with autologin, you can split screen too, just check it out

---

