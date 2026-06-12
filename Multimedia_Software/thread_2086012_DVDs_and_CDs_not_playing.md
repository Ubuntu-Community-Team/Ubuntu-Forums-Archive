---
title: "DVDs and CDs not playing"
date: 2012-11-19
forum: Multimedia Software
---

### Post by tnob on 2012-11-19
Greetings all,

I just noticed that DVDs or CDs won't play - neither in VLC. VLC just sort of hiccups (little flash at the left edge of the screen); Movie Player doesn't do anything at all.

I'm on Ubuntu Studio 12.04 LTS.

tnob

---

### Post by andrew.46 on 2012-11-19
Could you try with SMplayer:

```
sudo apt-get install mplayer smplayer
```

and if this fails post the SMplayer and MPlayer logs? These can be found under Options --> View Logs. Make sure you also have the dvd decryption library installed by copying and pasting the following single command into a Terminal window:

```

sudo apt-get install libdvdread4 && \
sudo /usr/share/doc/libdvdread4/install-css.sh

```

Should be working soon hopefully :).

---

### Post by tnob on 2012-11-21
Thanks andrew,46,

Although I'm most definitely the legal owner, Terminal doesn't accept my password, for some reason.

If you're online now, can this be rectified with Synaptic as well?

tnob

---

### Post by tnob on 2012-11-21
Hi Andrew.45,

In addition to the previous post:
As to

[SIZE="1"]sudo apt-get mplayer smplayer[/SIZE]

Terminal keeps insisting I'm not the legal owner;

as to

[SIZE="1"]sudo apt-get install libdvdread4 && \
sudo /usr/share/doc/libdvdread4/install-css.sh[/SIZE]

Terminal suddenly accepts password (very same as previously) and gives me this:

[SIZE="1"]peter@peter-toshiba:~$ sudo apt-get install libdvdread4 && \
> sudo /usr/share/doc/libdvdread4/install-css.sh
[sudo] password for peter: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/SIZE]

I'm not very good with Terminal, so might Synaptic be an option here?

tnob

---

### Post by andrew.46 on 2012-11-21
You can certainly use Synaptic or even the software centre for smplayer and mplayer. The error seems to suggest you may already have either of these open. Close all applications and start again...

---

