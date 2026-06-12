---
title: "ubuntu-desktop killed my internets!"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by peacemake on 2009-11-09
I installed ubuntu server 9.10 on my computer. No hassle there. When the installer program asked me what kind of use I'll be having there wasn't a tab for "everything" so I went with manual packages. Couldn't understand aptitude (sad...) and quit the manual selection. This took me forward without any extra packages. "Fine!" -I thought, and plodded onwards. I tested ifconfig: looking good. I tested ssh: works!

So I had a 'minimal' install server with working internets. I started installing stuff I felt I wanted. Teamspeak, irssi, samba... Next in line was a graphical interface because I wanted to be able to rdesktop into my server. 

```
sudo apt-get install ubuntu-desktop
```

2Gbs later I had me a working gnome desktop.

...without internet connection. ifconfig still shows everything like before: eth0 with the correct router-assigned IP, lo with jargon. The same as before. Only now I can't get to internet.

The funny thing is if I ping other machines in my LAN, the first packet goes through no problem. All others are lost. 

I am at my wit's end. Help, please.

---

