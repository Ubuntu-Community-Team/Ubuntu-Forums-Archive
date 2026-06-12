---
title: "How to configure MPD"
date: 2011-05-19
forum: Multimedia Software
---

### Post by Deathmanlp on 2011-05-19
Hi there :)
I'm new to ubuntu and I decided to try Sonata, but I can't configure MPD. Sonata uses localhost by default but it's already used by Apache. I tried disabling Apache but it still doesn't work. What IP should I use to be able to use Apache and Sonata in the same time ?

---

### Post by vanadium on 2011-05-21
I have also the biggest trouble to get mpd/sonata to work under Ubuntu 11.04. It has worked, today I start to play a song, the time counter does not move, and sonata disconnects. restart, reboot: sonata does not connect.

Anyway, with respect to your question: it is perfectly possible to have mpd and apache running on localhost. It is just that they should both use a different port. I guess that will be so by default.

If needed, you can configure the port mpd listens to in the /etc/mpd.conf file. Change the port number in the line
```

port				"6600"

```
You need to stop and restart mpd for the change to take effect:
```

sudo /etc/init.d/mpd restart

```

---

### Post by Deathmanlp on 2011-05-21
> **vanadium said:**
>  Anyway, with respect to your question: it is perfectly possible to have mpd and apache running on localhost. It is just that they should both use a different port. I guess that will be so by default.

If needed, you can configure the port mpd listens to in the /etc/mpd.conf file. Change the port number in the line
```

port                "6600"

```You need to stop and restart mpd for the change to take effect:
```

sudo /etc/init.d/mpd restart

```

I already tried this
```

ge0rgi@ge0rgi-pc:~$ sudo mpd
[sudo] password for ge0rgi: 
Failed to bind to '127.0.0.1:6600': Address already in use

```phpinfo ()

```

**Configuration**

 **apache2handler**

Hostname:Port 127.0.1.1:80 

```The ports are different but it still doesn't work.
However I moved to Clementine witch fits my needs for now :)
Thanks for helping :)

---

