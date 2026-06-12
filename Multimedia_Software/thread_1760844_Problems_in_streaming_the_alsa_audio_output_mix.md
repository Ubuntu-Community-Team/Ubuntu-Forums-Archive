---
title: "Problems in streaming the alsa audio output mix"
date: 2011-05-17
forum: Multimedia Software
---

### Post by mrjackv on 2011-05-17
I am currently using Ubuntu 11.04 and I would like to stream the outgoing audio of my computer via rtsp with vlc.
I am currently willing to use the following command
```
vlc -vvv alsa://hw:0,3 --sout '#rtp{sdp=rtsp://:6655/def.ogg} :no-sout-rtp-sap :no-sout-standard-sap :ttl=1 :sout-keep'
```(the output I am trying to use is under hw0,3 and it has been selected in the alsa mixer as capture)

However when I try running the command I get errors such as
```
stream chain failed for `rtp{sdp=rtsp://:6655/def.ogg} :no-sout-rtp-sap :no-sout-standard-sap :ttl=1 :sout-keep'
```and
```
socket bind error (Permission denied)
main access out error: cannot create socket(s) for HTTP host

```^ This happened when I tried to switch to http streaming and happens with very big ports (eg 55656) 
So, am I making some mistake in the line arguments or is there some other setting I have to change in order for the stream to work?
(I am trying to send the sound to the computer with IP "192.168.1.9" and any port > 6000)

Thanks in advance

---

### Post by mrjackv on 2011-05-17
anybody?

---

### Post by mrjackv on 2011-05-18
...

---

### Post by alchemist.vk on 2011-11-18
Hi all , i too facing the same problem. Any suggetions to overcome this.
 Also I want to know how to stream mp3 file using cvlc.

Thanks in advance

---

