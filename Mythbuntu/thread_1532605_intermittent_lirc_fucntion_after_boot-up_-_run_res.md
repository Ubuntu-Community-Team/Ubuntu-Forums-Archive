---
title: "intermittent lirc fucntion after boot-up - run restart command at boot"
date: 2010-07-16
forum: Mythbuntu
---

### Post by Don Giovanni on 2010-07-16
I have had this issue come and go over the past two years and my different installs of ubuntu with lirc/mythtv.

Intermittently lirc will not work after a boot or reboot and I need to restart it with "sudo /etc/init.d/lirc restart", after that the remote works fine.
I'd estimate it as every third or fourth boot this happens.  The rest of the time it works as expected.

I can't find anything in the logs to see what is happening those odd times and my lirc setup works fine otherwise.

What I would like to do is set up the init.d lirc restart command to automatically run say 15 to 30 seconds or so after boot up.  So this way those times it doesn't load properly after boot I am not left to go find the keyboard, exit myth frontend and run the restart command manually.  It will just restart on its own.

What is the best way to accomplish this?
(I know this doesn't address the real issue but it should get the job done)

---

### Post by nickrout on 2010-07-16
add the following to /etc/rc.local```
sleep 15
service lirc restart
```

---

### Post by Don Giovanni on 2010-07-16
thanks nickrout I'll give it a try and see how things work out.

*Update*Additionally had to add a delay to the mythfrontend autostart (20sec) as I was having to exit and then reenter the mythfrontend for the remote to work sometimes after the lirc restart.  But it works perfectly now.

---

### Post by one30nav on 2011-07-23
Don, just let you know know, with my Tira-2 Receiver setup, all that was required was a 15 second delay in the mythfrontend autostart. In other words, you may not need the "service lirc restart" in "/etc/rc.local" at all.

In my case, the autostart was conflicting with lirc. Thanks for your post (and nickrout too). This helped me with a huge headache.

I did a "sudo nano /usr/bin/mythfrontend"
```
[COLOR="Red"]**sleep 15**[/COLOR]
pidof mythfrontend.real 2>&1 >/dev/null && wmctrl -a "MythTV Frontend" 2>/dev/null && exit 0

```

---

### Post by ian dobson on 2011-07-24
> **one30nav said:**
> Don, just let you know know, with my Tira-2 Receiver setup, all that was required was a 15 second delay in the mythfrontend autostart. In other words, you may not need the "service lirc restart" in "/etc/rc.local" at all.

In my case, the autostart was conflicting with lirc. Thanks for your post (and nickrout too). This helped me with a huge headache.

I did a "sudo nano /usr/bin/mythfrontend"
```
[COLOR="Red"]**sleep 15**[/COLOR]
pidof mythfrontend.real 2>&1 >/dev/null && wmctrl -a "MythTV Frontend" 2>/dev/n$

```

I think you have a copy/paste error at the end of the line (2>/dev/n$) I imagine it should be /dev/null

Regards
Ian Dobson

---

### Post by one30nav on 2011-07-24
Thanks, Ian. Corrected.

---

