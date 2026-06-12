---
title: "Getting irexec to call a suspend script"
date: 2008-09-10
forum: Mythbuntu
---

### Post by leeko on 2008-09-10
Hi everyone,

Sorry for the long post - I've been working at this for a while :P

I'm trying to get lirc and irexec to allow me to suspend my computer from the remote control (packard bell fastmedia serial remote). I had problems when running irexec as myself (leeko), and major issues with trying to get it to run as user mythtv (suggested on another forum). Eventually, I rewrote my sudoers file and it now runs as mythtv. Unfortunately, even running as mythtv does not allow irexec to call the suspend script. I even tried running it as root, and it still doesn't work.

Here is my complete setup:
- Mythbuntu 8.04, fully up-to-date
- Set to auto-login as user leeko
- lircd autostarts as root user. All lircd functions work perfectly within mythtv/mplayer
- An irexec daemon autostarts as user leeko. I don't know where this is set to do this. I have removed all entries from /config/autostart, and rc.local, and I don't have any scripts set. So, I autorun a script:  /usr/local/bin/irexeclauncher. This script kills the existing irexec process, waits 30 seconds, then restarts it as user mythtv (or root). This works fine now.

```

leeko@leeko-media:~$ cat /usr/local/bin/irexeclauncher
#!/bin/bash
# Launcher for IREXEC because it's STUPID and won't launch properly in startup scripts!
sleep 10
killall irexec
sleep 30
sudo -u mythtv irexec /home/leeko/.lircrc
#sudo irexec /home/leeko/.lircrc
exit 0

```

- After giving the script time to run, "ps aux | grep ir" shows:
```

leeko@leeko-media:~$ ps aux |grep ir
root         4  0.0  0.0      0     0 ?        S<   11:43   0:00 [ksoftirqd/0]
mysql     4977  0.1  3.6 128268 18624 ?        Sl   11:43   0:01 /usr/sbin/mysqld --basedir=/usr--datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root      5495  0.0  0.1   2932   584 ?        S<s  11:44   0:00 /usr/sbin/lircd --device=/dev/lirc0
leeko     5913  0.0  0.2   4264  1428 ?        Ss   11:44   0:00 /bin/bash /usr/local/bin/irexeclauncher
mythtv      5979  0.0  0.1   1716   516 ?        S    11:44   0:00 irexec /home/leeko/.lircrc
leeko     6862  0.0  0.1   3008   772 pts/1    R+   12:06   0:00 grep ir

```

- My /home/leeko/.lircrc file has an entry to call /home/leeko/scripts/suspend.sh when I press button "SRS" on the remote:
```

leeko@leeko-media:~$ cat /home/leeko/.lircrc
#Custom lircrc generated via mythbuntu-lirc-generator
#All application specific lircrc files are within ~/.lirc
include ~/.lirc/mythtv
include ~/.lirc/mplayer
include ~/.lirc/xine
include ~/.lirc/vlc
include ~/.lirc/xmame
include ~/.lirc/xmess
include ~/.lirc/totem
include ~/.lirc/elisa
# include ~/.lirc/irexec

begin
    remote = PackBell
    prog = irexec
    button = SRS
    config = /home/leeko/scripts/suspend.sh
    repeat = 0
    delay = 0
end

```

- Here are the contents of the suspend.sh script:
```

leeko@leeko-media:~$ cat scripts/suspend.sh
#!/bin/bash
sudo /usr/sbin/pmi action suspend

```

- Immediately after login, I am able to manually suspend the computer using the suspend script. I am not asked for a password, as I have specified that user leeko can run "pmi action suspend" without a password.
-I have tried changing the ownership of the file from "leeko" to "mythtv" - no joy. 

My sudoers file:
```

# /etc/sudoers
Defaults        env_reset
%admin ALL=(ALL) ALL
leeko ALL = ALL
leeko ALL = NOPASSWD: /usr/bin/irexec
leeko ALL = (mythtv) NOPASSWD: ALL
leeko ALL = NOPASSWD: /usr/sbin/pmi
mythtv ALL = NOPASSWD: /usr/sbin/pmi
mythtv ALL = NOPASSWD: /usr/bin/irexec
mythtv ALL = ALL
mythtv ALL = NOPASSWD: /sbin/halt,/sbin/shutdown,/sbin/reboot,/bin/umount

```

- My lircd.conf has the following entry for button "SRS"
 SRS                      0x0000000000004EB1

- Using irw, pressing the button SRS gives:
```

leeko@leeko-media:~$ irw
00000000f7089d62 00 SRS PackBell
00000000f7089d62 01 SRS PackBell

```

As far as I can tell, everything is set up correctly. I can't figure out why irexec won't do what I'm asking!

My only clue is auth.log. Whenever I press the power button, auth.log appends this to the tail:

```

Sep 10 12:31:47 leeko-media sudo: pam_unix(sudo:auth): authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=mythtv

```

Any help with this issue would be very much appreciated. I'm knackered from getting up off the couch to switch this machine off!

Thanks,

Lee
----------

---

### Post by leeko on 2008-09-11
How incredibly weird!

As an act of desperation, I tried one last thing in the script:

- kill the rogue autostarted "irexec -d /home/leeko/.lircrc" process, which was owned by user leeko
- wait 30 seconds
- restart irexec as the same user, leeko, with "irexec /home/leeko/.lircrc" (no daemon flag this time).

It works this time - pressing the power button suspends the computer. Woooo!

I conclude that irexec:
- doesn't work properly when autostarted
- doesn't work properly when the -d flag is set
- is a pain in the backside to get working properly!

Of course, these conclusions only hold true for my setup (which is not too unusual...).

Thanks for the input,

Lee

---

### Post by vikjon0 on 2009-04-18
Hello,

I have the same problem. I have not isolated the exact cuase but I managed to get to work by adding 

> %admin ALL=NOPASSWD: ALL

at the end of sudoers. This is of course not good, but I do not know linux very well.

Please see details on 
[http://vikjonlinuxhowto.blogspot.com/2009/04/howto-setup-remote-for-ubuntu-804-xbmc.html]("http://vikjonlinuxhowto.blogspot.com/2009/04/howto-setup-remote-for-ubuntu-804-xbmc.html")

//J

---

### Post by elitenoobboy on 2009-07-17
> **vikjon0 said:**
> Hello,

I have the same problem. I have not isolated the exact cuase but I managed to get to work by adding 



at the end of sudoers. This is of course not good, but I do not know linux very well.

You should be able to use crontab to get it to run as root so you don't have to compromise your system. 
[http://swinky-linuxblog.blogspot.com/2009/03/how-to-use-lirc-with-amarok-2-exaile.html](http://swinky-linuxblog.blogspot.com/2009/03/how-to-use-lirc-with-amarok-2-exaile.html)

---

### Post by azmyth on 2009-07-18
Irexec doesn't work well with mythbuntu when starting manually like you could with other distros. It's easy to setup though to make it start on boot. The only problem is if you restart lirc it won't restart irexec.

[http://myubuntulinuxblog.blogspot.com/2009/04/setting-up-irw-to-start-on-boot.html](http://myubuntulinuxblog.blogspot.com/2009/04/setting-up-irw-to-start-on-boot.html)

---

