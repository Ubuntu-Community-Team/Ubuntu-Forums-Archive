---
title: "Can't play DVD"
date: 2009-12-18
forum: Multimedia Software
---

### Post by mpolito1969 on 2009-12-18
When I insert a DVD, right click on the icon on the desktop and select "open with movie player" I can see totem starting and after a while it suddenly disappear.

Using dmesg I get:

```

[ 2478.084526] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2478.084536] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 2478.084544] sr 4:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
[ 2478.084557] end_request: I/O error, dev sr0, sector 1824
[ 2478.084565] __ratelimit: 123 callbacks suppressed
[ 2478.084570] Buffer I/O error on device sr0, logical block 456
[ 2478.084577] Buffer I/O error on device sr0, logical block 457
[ 2478.099550] totem[6925]: segfault at 1874 ip 002ced1d sp b4bfed44 error 4 in libpthread-2.10.1.so[2c7000+15000]


```

I've seen there is an How-to but it looks to me very complicated, I just want to see a DVD I've just bought, I can hardly believe I have to do all that stuff.

Does anybody have some suggestion about how to troubleshoot the issue?

I'm using Ubuntu 9.10 on an ASUS laptop. It works fine for everything else, I can see youtube video, mpeg video and so on, I just can't see any DVD.

Ciao,
Max

---

### Post by howefield on 2009-12-18
Try installing libdvdread4 with Synaptic Package Manager.

---

### Post by wojox on 2009-12-18
Open you termianal:

```
sudo apt-get update && sudo apt-get install libdvdread4
```

Then:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by mpolito1969 on 2009-12-18
Synaptic Package Manager says libdvdread4 is already installed.

Ciao,
Max

---

### Post by mpolito1969 on 2009-12-18
Command line says:

```
Reading state information... Done
libdvdread4 is already the newest version.
libdvdread4 set to manually installed.
The following packages were automatically installed and are no longer required:
  libdns50
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by howefield on 2009-12-18
Have you tried the second step in wojoxs' post ?

---

### Post by mpolito1969 on 2009-12-18
> **howefield said:**
> Have you tried the second step in wojoxs' post ?

Just now.

DVD starts but I can't listen to any sound (and it's a live concert :-) ).

Ciao,
Max

---

### Post by saltmore on 2009-12-18
Is gstreamer0.10-plugins-ugly installed? If not install it and see how it works. Mediabuntu repo of course.

---

### Post by mpolito1969 on 2009-12-18
> **saltmore said:**
> Is gstreamer0.10-plugins-ugly installed? If not install it and see how it works. Mediabuntu repo of course.

Yes, according to Synaptic Package Manager.

By the way... I've just noticed with Gnome MPlayer is OK both video and audio.

Ciao,
Max

---

### Post by howefield on 2009-12-18
> **saltmore said:**
> Is gstreamer0.10-plugins-ugly installed? If not install it and see how it works. Mediabuntu repo of course.

Not relevant to the OPs question, but those plugins do not depend on Medibuntu. They are in the universe repository.

To the OP, glad you have another player that seems ok, you could also try VLC, plays just about anything.

---

### Post by mpolito1969 on 2009-12-18
Thank you for your support, I'm now watching the concert :P

Ciao,
Max

---

