---
title: "Adjusting screen alignment with ATI Gatos driver"
date: 2007-05-19
forum: Multimedia &amp; Video
---

### Post by barney_1 on 2007-05-19
Hello Folks,

I've got a Radeon 9000 card in my MythTV box.  I just upgraded to Feisty and used the gatos TV-out patch to run the open source driver for tv out:
[http://wiki.cchtml.com/index.php/TV_Out]("http://wiki.cchtml.com/index.php/TV_Out")

The screen alignment is a little bit off so I compiled the tvo_set program and found that I can fix my alignment with this command:
```
tvo_set set hpos -5
```

The problem is that after a reboot I have to re-issue that command to properly align my screen.  Is there a way to include that alignment in the xorg.conf file?  If not, how can I make that command run automatically at boot time?

Thanks!

---

### Post by barney_1 on 2007-05-24
bump

---

### Post by barney_1 on 2007-06-01
In case anyone's wondering here's what I did:

I created a script file:
```
nano ScreenAlignment.sh
```
script contents:
```
#!/bin/bash
tvo_set set hpos -5
tvo_set set hsize -1
```
make it executable:
```
chmod +x ScreenAlignment.sh
```
I then went to the session options and set that script up to run at login.

---

