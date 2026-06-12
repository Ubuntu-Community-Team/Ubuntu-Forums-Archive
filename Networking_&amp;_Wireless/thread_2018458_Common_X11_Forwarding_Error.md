---
title: "Common X11 Forwarding Error"
date: 2012-07-06
forum: Networking &amp; Wireless
---

### Post by acupofjava on 2012-07-06
When I try to connect to my Ubuntu setup remotely from a Mac using,
```
ssh -Y username@domain
```
I get the following when I log in,
```
Warning: No xauth data; using fake authentication data for X11 forwarding.
```
If I test it by running firefox, it works fine. However, I get the message in the terminal screen:
```
Xlib: extension "RANDR" missing on display "localhost:10.0
```

I've done a ton of searching around, it seems the consensus is to just ignore the message? I feel like I need to somehow generate xauth data, but how can I? I've read the man page to no avail.

---

### Post by Kirk Schnable on 2012-07-11
I am not particularly concerned about that error, as long as the X forwarding is actually working.

However, I did do some Googling myself, and you might try adding this line to your /etc/ssh/ssh_config

```
XAuthLocation /usr/bin/xauth
```

See if that fixes the error message.



As far as the RANDR error, RANDR is a display extension on your computer, it has nothing to do with the X forwarding.  

[http://en.wikipedia.org/wiki/RandR](http://en.wikipedia.org/wiki/RandR)

I believe that my computer doesn't have RANDR extension loaded because I am using Xinerama with my nVidia drivers.

There are a lot of reasons to be missing the RANDR extension.  It's no big deal.

Kirk

---

