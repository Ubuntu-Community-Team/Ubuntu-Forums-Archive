---
title: "Request for a noob LIRC HOWTO on Ubuntu Lucid"
date: 2010-11-20
forum: Multimedia Software
---

### Post by YfoMp5QBh2 on 2010-11-20
Hi All,

I am a complete noob to LIRC and I'm trying to get it setup to control XBMC. I have found the following [HOWTO on Wiki]("http://wiki.xbmc.org/?title=HOW-TO_setup_Lirc_to_talk_to_XBMC")  but I can only get as far as the "Configure Lirc to understand your  remote's commands" and I get lost. Where do I go from here? I have  searched the forum but theres nothing specific to what I need to know.

I have the following:
Ubuntu 10.04 Lucid Lynx
Logitech Harmony Remote 550 (preset with MCE commands)
XBMC 9.10

Even better if someone has a similar setup and its possible to copy and  paste the codes into a config file of some sort, could someone please  post their own setup? This might save me from going through a long  winded setup using the ugly terminal

I have already posted the same question on the [XBMC]("http://forum.xbmc.org/showthread.php?t=85757") forums

Please help am really stuck.

---

### Post by YfoMp5QBh2 on 2010-12-06
Hi All,

Please help. I've been using the following [WIKI HOWTO]("http://wiki.xbmc.org/?title=HOW-TO_setup_Lirc_to_talk_to_XBMC") but I'm stuck after I type root@ubuntu:/etc/lirc#  irrecord --driver=irman --device=/dev/ttyS0 mceusb into the terminal I get the following:

```
jamie@ubuntu:~$ sudo -s
root@ubuntu:~# cd /etc/lirc
root@ubuntu:/etc/lirc#  irrecord --driver=irman --device=/dev/ttyS0 mceusb

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: could not open /dev/ttyS0
irrecord: irman_init(): Input/output error
irrecord: could not init hardware (lircd running ? --> close it, check permissions)
root@ubuntu:/etc/lirc# 

```

Can anyone help me with this??

---

### Post by YfoMp5QBh2 on 2010-12-18
....anyone have any advice? help?

---

