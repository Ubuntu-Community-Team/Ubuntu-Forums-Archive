---
title: "VLC command interface"
date: 2009-05-26
forum: Multimedia Software
---

### Post by docjones2 on 2009-05-26
On my old Linux box I had VLC set up nicely.  Using sudo apt-get, right out of the box VLC was set up with no GUI whatsoever, and for playlist control I would type things like "next" and "prev".  I was thrilled.

On my new box, using the same sudo apt-get, this VLC has GUI and does not respond to input from the terminal, cvlc hides the GUI but is still unresponsive.  What files can I modify to fix this problem?

Thank you

---

### Post by urosg3 on 2009-05-26
Please post more information, witch Ubuntu, witch VLC...
usualy is good enough to enable  a "multiverse" mirror is listed in your /etc/apt/sources.list.
then

> % sudo apt-get update
% sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc


---

### Post by docjones2 on 2009-05-26
I'm using Ubuntu 9.04 and VLC 0.9.9a

All I want to do is remove the GUI and enable the CLI.

---

### Post by john_navarro on 2009-05-26
1) Launch VLC

2) Tools -> Add Interface -> Telnet Interface

3) From your terminal type:  telnet 127.0.0.1 4212

4) The default password is "admin"

---

### Post by andrew.46 on 2009-05-29
Hi docjones,

> **docjones2 said:**
> I'm using Ubuntu 9.04 and VLC 0.9.9a

All I want to do is remove the GUI and enable the CLI.

I should stress that I have not tested this as I use a different vlc package but I believe you may be after vlc-nox:

```

andrew@skamandros:~$ apt-cache search vlc-nox
vlc-nox - multimedia player and streamer (without X support)

```

I was not aware that the Ubuntu vlc package was split up in this way.

All the best,

Andrew

---

