---
title: "Send AT commands to LG GW620g"
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by anchise on 2010-10-06
Hi,

I need to send AT commands (hayes commands) to my LG GW620g (amongst other purposes, for receiving and sending SMS from the shell).
Can somebody help me and tell me what I have to do in order to connect a mobile phone (or _this_ mobile phone) as ttyS0 or ttyACM? I guess it has something to do with udev, but I am not sure there. Or is there another way to open a terminal connection to this device?

Any help is appreciated.

Thank you in advance.

anchise

(ubuntu 10.04 64-bit desktop)

---

### Post by duanedesign on 2010-12-18
plugin the  cell phone and type the command:

```
tail -s 3 -f /var/log/messages
```

you should be able to see if the phone is recognised and what name it is assigned, if any.

Gnoki is a good FOSS app for sending SMS using your phone. here is a [decent guide]("http://www.developershome.com/sms/gnokiiIntro.asp#1.2.1.Introduction|outline"). And of course [the Gnokii site]("http://gnokii.org/").

---

