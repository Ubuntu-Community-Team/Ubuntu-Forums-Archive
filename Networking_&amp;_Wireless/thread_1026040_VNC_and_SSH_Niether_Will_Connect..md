---
title: "VNC and SSH: Niether Will Connect."
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by wirewrapped on 2008-12-30
[FONT="Georgia"]Hello. I'm going to give a short introduction since I'm new here, just for politeness sake.[/FONT]
[FONT="Arial"]
[SIZE="1"]I've been using Ubuntu since this last summer. I started with Hardy and have loved it ever since. It fulfills my needs for the most part, with some of the missing ones being fixed every day. I'm tinker with tech, and enjoy artistic productions and learning new things.
[/SIZE][/FONT]

[FONT="Georgia"][INDENT]Now, to the heart of my issue, please. Here's my setup:

- 2 laptops: [HP Compaq, Acer Aspire 1] both running Intrepid Ibex.
- 1 [generic?] cable modem with Time Warner ISP
- 1 Netgear Wireless-G Router Model:WGR614v7[/FONT]

[FONT="Georgia"]The Ethernet line is connected to my HP Compaq through the lan of the Netgear Router. The Acer connects to the wireless Netgear.[/INDENT]

I've set up the Acer for *VNC*, and connected a few times, but when I discovered that I couldn't transfer files I went on to learn about *SSH*. Setting that up was a pain, because it would not connect. Then, I installed firestarter to open port 22, but I could not get SSH to work, even after opening port 22. After uninstalling firestarter, neither *VNC* nor *SSH* will connect! I get timeouts from both protocols. 

Can anyone help me tune these settings? :confused: Or what is the best way to use *SSH* and *VNC*? I prefer *SSH* for its security.
[/FONT]
**Much Thanks!**

---

### Post by jpkotta on 2008-12-30
Try disabling the firewalls and get things working.  One less thing to worry about.  When you have it working, enable the fw and work out any new issues.

Here is a script I use to tunnel VNC through SSH.  You need openssh-server and x11vnc installed on the remote machine.
```
#!/bin/bash

usage="$0 [user@]remote_host [<DISPLAY>]"

login="$1"
if [ -z "$login" ] ; then
    echo $usage
    exit 1
fi

disp="$2"
if [ -z "$disp" ] ; then
    disp=:0
fi

ssh "$login" "x11vnc -localhost -display '$disp' -scale 4/5 -bg" 
vncviewer -via "$login" localhost"$disp"
```

---

