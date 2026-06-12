---
title: "Can't get 2nd DTV2000H to work"
date: 2009-02-06
forum: Mythbuntu
---

### Post by laffinet on 2009-02-06
Okay, I hope that I'm just blind and there's a real simple solution to this:

I can't get my 2nd Leadtek DTV2000H to work. It gets recognised ok

lspci
```
01:06.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:06.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:06.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:07.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:07.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:07.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)

```

It shows up alright in the backend configuration, just like the 1st card. However, the thing I can't get done is assign the correct "DVB device number".

It warns me that 0 is already in use (for the other card), but I can't change it to 1. The pull down menu doesn't open, I can't type in 1, I just don't know how.

Anyone know how and where ? Please help me as this is driving me nuts !!!

---

### Post by laffinet on 2009-02-07
Okay, took me a lot of googleing and I was already worried that I might have to fiddle around with udev rules (which I haven't got the faintest clue about), but in the end it turned out to be pretty simple:

To get the tuner work initially the 

```
/etc/modprobe.d/options
```

 file had to be edited to include the line 

```
options cx88xx card=51
```

To get the second card working the 51 has to be added twice, separated by a comma. So now the line is

```
options cx88xx card=51,51
```

and the card can be setup as dvb device 1 in the backend configuration

---

