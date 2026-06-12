---
title: "xrdp on Lubuntu"
date: 2013-04-10
forum: Networking &amp; Wireless
---

### Post by SpeedoJoe on 2013-04-10
I am trying to configure Lubuntu to allow multiple remote X sessions via RDP from Windows clients for a remote support project at work. xrdp seemingly installs correctly but when it comes to connecting from one of the clients LXDE doesn't load after entering the username and password.
[IMG]http://i.imgur.com/hV35OSD.png[/IMG]

Any help would be appreciated.

---

### Post by steeldriver on 2013-04-10
Have you tried creating a minimal ~/.xrdp/.xsession in the target remote account? I don't know about LXDE specifically, but to get anything other than a plain gray root window from my regular 12.04 Ubuntu via RDP I had to specify a session there i.e.

```
$ cat ~/.xrdp/.xsession
gnome-session --session=ubuntu-2d
```

I don't know what the equivalent would be for Lubuntu / LXDE - maybe 

```
lxsession --session=lxde
```

or perhaps just

```
lxsession
```

---

### Post by piotrasbl on 2014-02-09
I'd really apperciate any help in this thread, as I'm facing the same issue.
Only difference I use lubuntu 13.10
edit:

I found a solution for the problem.
Since I wanted to use LXDE via xrdp(machine boots in text mode), all I had to do was to create .xsession file in /home.USAERNAME/ directory.
the file looks as below:

```
#!/bin/sh
xrdb $HOME/.Xresources
xsetroot -solid black
lxterminal &
/usr/bin/lxsession -s Lubuntu -e LXDE &
```

Now, whenever i connect via xrdp, I'm using LXDE :)

---

