---
title: "No sound with EWX 24/96 (Fresh Install)"
date: 2007-05-10
forum: Multimedia &amp; Video
---

### Post by jessdog9001 on 2007-05-10
Hello all,

I just installed Ubuntu 7.04 Feisty Fawn, and so far I like it! However, I am unable to get my soundcard to work. My soundcard is a Terratec EWX 24/96, which uses the ICE1712 driver. In most cases, it runs out of the box. I have successfully used it in Debian and other distros without any custom configuration. 

What is really frustrating is that I have had this card working in earlier versions of Ubuntu. I didn't even need to do manual configuration, because it worked from the start! 

So I have tried some things already. The card shows up in lspci: 
```
01:0d.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
```

However, if I try aplay -l, I get the following results: 
```
aplay: device_list:222: no soundcards found...

```

alsamixer and Gnome's volume control give me similar errors (no device found). Anybody have any ideas what might be wrong? If I can't get sound working, Ubuntu is nearly useless to me because I want to use it to record music. I appreciate any help you can give me! :)

---

