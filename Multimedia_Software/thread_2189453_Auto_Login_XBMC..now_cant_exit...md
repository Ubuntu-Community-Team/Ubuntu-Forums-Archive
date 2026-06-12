---
title: "Auto Login XBMC..now cant exit.."
date: 2013-11-22
forum: Multimedia Software
---

### Post by macpj on 2013-11-22
I had installed XBMC on my Dell running 12.10. I was looking at the login's for my Ubuntu dekstop sessions and saw there was one for XBMC. So, I thought I'd give it a try. Well, it didnt work. I get a black sqaure about 3/4 the size of the screen and am unable to do anything. If I do a hard reboot, because my last session was XBMC, it goes right back to the same screen and I cant log out. So basically I'm stuck rebooting into the XBMC session and the machine is frozen and cant do anything.
Any idea's ? Maybe doing something from Recovery Mode or shell prompt ??

---

### Post by steeldriver on 2013-11-22
If you have set up auto-login via lightdm, you can disable it by editing the [SeatDefaults] section of the /etc/lightdm/lightdm.conf file

The easiest way would be to switch to one of the 'virtual terminals' (Ctrl-Alt-F1 thru Ctrl-Alt-F6) and log in using your regular username and password and (assuming that account is a sudoer)

```

sudo service lightdm stop

sudo nano /etc/lightdm/lighdm.conf

```

Once you're done editing you can save (Ctrl-o) and exit (Ctrl-x) then

```

sudo service lightdm start

```

It should pop you back to the lightdm GUI screen on tty7, but if it doesn't for some reason you can pres Ctrl-Alt-F7

If you can't get to a virtual terminal, then you can do basically the same steps from the recovery console root shell (no sudo needed there) but you will need to make the filesystem writeable first - either by manually remounting it or by selecting the 'Enable networking' option first and then dropping to a root shell ('Enable networking' remounts rw as a side effect).

See this recent thread --> [http://ubuntuforums.org/showthread.php?t=2187685](http://ubuntuforums.org/showthread.php?t=2187685)

---

