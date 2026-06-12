---
title: "How to start vncserver at startup"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by davidbd on 2006-06-05
Hello,
I installed Ubuntu server with x server ( minimal install ) on a computer without a screen.
I would like to boot and then connect to the server via vnc client or via x-server.

currently I installed ssh server on the linux server and ssh client ( putty ) and x-server ( cygwin-x ) on the PC .

Then I used the ssh to connect to the server and then run vncserver and other tools.

I know there is an option to enable the XDMP service and connect with external x-server running on other machine.

I whould like to enbale the following at automatically start up:
- XDMP server
- VNC server

What are the excat step to do so and what is recomendad ?

Regards,
David.

---

### Post by davidbd on 2006-06-06
Any answer ?

---

### Post by mjfarina on 2006-06-11
I would love to see someone answer this!!

---

### Post by tronica on 2006-06-11
i'm trying to find a guide that i used a long time ago but i know that it has something to do with ~.vnc/xstartup

also try here
[http://72.14.203.104/search?q=cache:z19uY089sEkJ:www.linuxjournal.com/article/5499+vncserver+xstartup&hl=en&gl=us&ct=clnk&cd=26](http://72.14.203.104/search?q=cache:z19uY089sEkJ:www.linuxjournal.com/article/5499+vncserver+xstartup&hl=en&gl=us&ct=clnk&cd=26)

and go down to configuring vnserver

---

### Post by tronica on 2006-06-13
here yah go

[http://ubuntuforums.org/showthread.php?t=191564&highlight=vnc+gnome](http://ubuntuforums.org/showthread.php?t=191564&highlight=vnc+gnome)

---

### Post by viper52b on 2006-06-13
If you just want vncserver to start at system startup, you can just add it to the correct runlevel: this will probably be /etc/rc3.d/ (console login, not graphical, with networkin support).  To make vncserver startup automatically just add a symlink here to /etc/init.d/vncserver

```

# cd /etc/rc3.d
# sudo ln -s /etc/init.d/ssh S99vncserver

```

The number S99 just means it will be executed as the last program. (numbering goes to 100).  This way just makes vncserver start automatically...
Hope it helps! :)

---

### Post by Slim Odds on 2006-06-13
[quote=viper52b]If you just want vncserver to start at system startup, you can just add it to the correct runlevel: this will probably be /etc/rc3.d/ (console login, not graphical, with networkin support).  To make vncserver startup automatically just add a symlink here to /etc/init.d/vncserver

```

# cd /etc/rc3.d
# sudo ln -s /etc/init.d/ssh S99vncserver

``` 
The number S99 just means it will be executed as the last program. (numbering goes to 100).  This way just makes vncserver start automatically...
Hope it helps! :)[/quote]

Why the heck would you link it to ssh?

---

### Post by viper52b on 2006-06-14
my mistake...

should be vncserver offcourse :)

(was testing it on my pc for ssh server)

---

