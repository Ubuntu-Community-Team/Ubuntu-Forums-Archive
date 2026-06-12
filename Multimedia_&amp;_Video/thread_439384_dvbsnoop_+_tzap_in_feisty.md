---
title: "dvbsnoop + tzap in feisty"
date: 2007-05-10
forum: Multimedia &amp; Video
---

### Post by axlf on 2007-05-10
Hi there.

In Etchy I used to do 
```
tzap -r "TV" 
```
and then in another window
```
dvbsnoop -s signal
```
In Feisty I can't do that anymore. I get the following:
```
axlf@ubuntu:~$ dvbsnoop -s signal
dvbsnoop V1.4.00 -- http://dvbsnoop.sourceforge.net/ 
Error(16): /dev/dvb/adapter0/frontend0: Device or resource busy

```
I looked at the rights:
```
axlf@ubuntu:~$ ls -l /dev/dvb
totalt 0
drwxr-xr-x 2 axlf root 120 2007-05-10 10:56 adapter0

```

What is wrong?


Regards, Alex

PS: I am aware of the bug that cx88 is not lodad by default.
Here comes a bit of my configuration.

lspci:
[HTML]01:00.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:00.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:00.4 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
[/HTML]

Occasionally I get the following dmesg, but that might have to do with bad reception.
```
 [ 8968.584643] cx88[0]: irq mpeg  [0x100000] ts_err?*
[ 8968.584656] cx88[0]/2-mpeg: general errors: 0x00100000
[10825.676070] cx88[0]/2-mpeg: cx8802_timeout

```

---

