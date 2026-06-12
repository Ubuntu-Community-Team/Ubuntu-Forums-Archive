---
title: "mt-daapd erroring, wont start"
date: 2008-03-26
forum: Multimedia &amp; Video
---

### Post by Cellwind929 on 2008-03-26
I'm trying to get mt-daapd running on my server computer. It's Gusty 7.10. I installed mt-daapd from the packet manager, but when I go to start it, I get these issues.
```

cellwind929@cellserver:/etc/init.d$ sudo mt-daapd start -f
Firefly Version svn-1586: Starting with debuglevel 2
Error loading plugin /usr/lib/mt-daapd/plugins/ssc-script.so: plugin declined to load
Plugin loaded: rsp/svn-1586
Plugin loaded: daap/svn-1586
Plugin loaded: ssc-ffmpeg/svn-1586
Starting rendezvous daemon
*** WARNING *** The programme 'mt-daapd' uses the HOWL compatiblity layer of Avahi.
*** WARNING *** Please fix your application to use the native API of Avahi!
*** WARNING *** For more information see <http://0pointer.de/avahi-compat?s=howl&e=mt-daapd>
Starting signal handler
Initializing database
Full reload...
Starting web server from /usr/share/mt-daapd/admin-root on port 3689
Listen port: Address already in use
Error staring web server: Address already in use
Aborting
cellwind929@cellserver:/etc/init.d$ Rendezvous socket closed (daap server crashed?)  Aborting.
Aborting

```

Heres some more info:
```
cellwind929@cellserver:/etc/init.d$ netstat -an | grep 3689
tcp        0      0 0.0.0.0:3689            0.0.0.0:*               LISTEN     
unix  3      [ ]         STREAM     CONNECTED     63689    /tmp/.ICE-unix/17733
cellwind929@cellserver:/etc/init.d$ ps waux | grep mt-daapd
mt-daapd   589  0.0  0.2  31564  2400 ?        Sl   23:11   0:00 /usr/sbin/mt-daapd
mt-daapd   591  0.0  0.2  31564  2592 ?        Sl   23:11   0:00 /usr/sbin/mt-daapd
1000       652  0.0  0.0   2976   752 pts/0    R+   23:15   0:00 grep mt-daapd
```

I have no clue how I'd even begin to troubleshoot this. I can't even hit the programs administrative page on localhost.

Thanks for any help in advance guys.

EDIT: turns out I just had to restart things and everything went away. Sorry for the useless post

---

### Post by talsemgeest on 2008-03-27
Mark this thread as solved. Glad you got it working btw.

---

### Post by Cellwind929 on 2008-03-27
I've been testing it to make sure everything is working. I got my music all scanned, and my config file appears to be all correct. Problem I'm facing now is that whenever I type in my password in Exaile on my laptop, it rejects the share regardless of what I type in for a password. Also, on the server status page, it says Bonjour isn't running, is that important?

Any ideas why my password is being rejected?

---

### Post by berthiggins on 2008-04-27
It always says bonjour is not running that is a bug ...:)
As for the password maybe check the config file /etc/mt-daap.conf?

---

### Post by Cellwind929 on 2008-04-27
> **Cellwind929 said:**
> I've been testing it to make sure everything is working. I got my music all scanned, **and my config file appears to be all correct.** Problem I'm facing now is that whenever I type in my password in Exaile on my laptop, it rejects the share regardless of what I type in for a password. Also, on the server status page, it says Bonjour isn't running, is that important?

Any ideas why my password is being rejected?

My config file was fine. I ended up switching to tangerine instead to get daap working. Everything works fine with it.

---

