---
title: "Can't find wireless n networks with RT2860"
date: 2011-02-01
forum: Networking &amp; Wireless
---

### Post by psillymathhead on 2011-02-01
Hello,  I went out and purchased a Sabrent PCI wireless 802.11n card with the RT2860 chipset because it was on the ubunutu compatibility list and has linux driver available from the manufacturer.  I was impressed that the card worked in wireless G mode out of the box, which is a great start....

...However, I can't find any wireless N networks.  Dual booting I can find/use my N network, but in ubuntu I can only find my G network.  This is somewhat frustrating because I bought this card and a new (read: expensive) Linksys E3000 router specifically to run a nice new N network...

I have downloaded, made, and installed (reboot) the latest driver from the manufacturer, but it still won't find any N networks.  I found a few posts by searching here and google that alluded to changing this line: "HT_OpMode=1" (from 0 to 1) in the config file RT2860STA.dat located in /etc/Wireless/RT2860STA/ and a reboot.  It didn't work for me.

Frankly all this rebooting is starting to **** me off ;)... I have spent most of last night trying to setup my 180$ wireless network and its still no better than the freebie DDWRT54g based wifi it replaced.  I am frustrated, perhaps someone wiser in the ways of ubuntu and wireless N can shed some light on the situation....

(edit)
I forgot to mention I am on Karmic Kola, amd64 with the standard gnome.

Thanks
~Garrett

---

### Post by psillymathhead on 2011-02-01
is there an ubuntu version where this chip will actually work out of the box (as it should?).. or am I better off going back to a less-flash-more-works distro...?

thanks,

---

### Post by Lucretius on 2011-02-02
the bundled driver does not have wireless N (or "high throughput mode" as it is called) enabled by default I believe.

I have the same problem with mine.

Managing your network card really needs to be made easier under ubuntu

---

### Post by psillymathhead on 2011-02-02
yes, I understand that and have compiled/installed drivers from the manufacturer and also changed the only mentioned config file to enable "High throughput"; yet it still doesn't see any N networks.  Can anyone provide a true solution... I am willing write a script out of it for other users....if it works!

I mean, I can understand wireless is a pain when a lot of manufacturers don't put out linux drivers (broadcom comes to mind).... but this card IS supported for Linux.  

Ubuntu Fail.

Have you gotten it to work?  I was thinking to try a fresh install of 10.04LTS/10.10.  I really don't like ubuntu, but my wife likes the gnome and my work uses ubuntu for its linux-interface machines.... I must say that between keyboard map issues, VNC/NX issues, ctrl-alt-backspc zapping, and horrible wireless managers Ubuntu is going backwards... but it does look great while its failing...:lolflag:

---

