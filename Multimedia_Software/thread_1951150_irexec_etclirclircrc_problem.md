---
title: "irexec /etc/lirc/lircrc problem"
date: 2012-04-02
forum: Multimedia Software
---

### Post by STARDOUSER on 2012-04-02
**tl;dr** The default init process for irexec doesn't seem to work. (Precise beta2, but may apply to earlier versions)

I was reading about lirc ([lirc.org/html/configure.html]("http://www.lirc.org/html/configure.html")), which describes **/etc/lirc/lircrc** as the "configuration information of all clients in one place." So I wrote a simple lirc bind in /etc/lirc/lircrc which launches xbmc when I press a button on my remote:
> begin  
        prog = irexec
        button = KEY_HOME
        config = xbmc
end

It works when I run irexec in a terminal. I was going to add irexec to my startup applications, but then I noticed the lirc init script for ubuntu starts irexec if /etc/lirc/lirc exists. Here's the line where it launches irexec:
> start-stop-daemon --start --quiet --oknodo --exec /usr/bin/irexec -- -d /etc/lirc/lircrc < /dev/null
It launches irexec just fine:
> root@Precise:/etc/lirc# service lirc restart
 * Stopping execution daemon: irexec
   ...fail!
 * Stopping remote control daemon(s): LIRC
   ...done.
 * Loading LIRC modules
   ...done.
 * Starting remote control daemon(s) : LIRC 
   ...done.
 * Starting execution daemon: irexec
   ...done.
root@Precise:/etc/lirc# ps aux | grep irexec
root     28043  0.0  0.0   6360   100 ?        Ss   22:17   0:00 /usr/bin/irexe  -d /etc/lirc/lircrc
The problem is that my keybind didn't do anything afterwards. It didn't work.

To troubleshoot this, I opened a terminal, switched to root and ran irexec. I would assume that this wouldn't work, since I'm doing the same thing that the init script does. But it actually works just fine. It also works if I launch irexec as my normal user.  So to make my bind work, I'd be running two instances of irexec for some reason. 

What I could do is move my config from /etc/lirc/lircrc to ~/.lircrc and add irexec to my accounts startup applications. However, I'm still left wondering why the init script doesn't work with /etc/lirc/lircrc.  Since I couldn't figure it out on my own, I decided to drop a note here about it.

---

