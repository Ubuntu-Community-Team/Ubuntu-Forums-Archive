---
title: "Netgear WG111T USB Wireless adapter/ndiswrapper problems"
date: 2006-02-24
forum: Networking &amp; Wireless
---

### Post by overture8 on 2006-02-24
Hello all,

I am having a nightmare trying to get my WG111T USB network adapter to work.  I have installed the inf files using ndiswrapper and everything seemed to go well:-

ndiswrapper -l
athfmwdl      driver present, hardware present
netwg11t      driver present

So the hardware seems to be recognised but when I do:-

iwconfig
lo       no wireless extensions
eth0   no wireless extensions
sit0     no wireless extensions

No wlan0!! :( Since my knowledge of Linux is limited I am having real trouble with getting this issue solved myself.  Maybe there isn't even a solution??!

Can anyone help me? 

Much Thanks.

---

### Post by TheFr00n on 2006-04-08
The trick is to comple version 1.10 of ndiswrapper yourself. The version of ndiswrapper in the Ubuntu repository is several centuries out of date. Later versions also give problems during compilation - version 1.10 is your friend.

Make sure gcc 3.4 is installed so that you can compile stuff, and then head over to the wiki page on ndiswrapper, over [here](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto#head-46777dc8e45dd15e9504db4c6f7e613b97036809). 

In section 3 - Troubleshooting, there is an excellent step by step guide that should sort you out.

Let us know how you get on with that evil little dongle.

---

### Post by ORF1000 on 2006-07-27
This worked for my WG111T.  The version of ndiswrapper I ended up with is 1.21.  It was a minor pain, but certainly worth it in the end, because I like this adapter.

Dave

---

### Post by elpuerco on 2006-09-11
Hi,  I see that every page leads to the same WIKI alas the PC I am trying to sort out is an AMD64 and thus the WIKI says that the method stated is old and out of date?

I have installed Kubunt 6.06.1 and can see ndiswrapper is installed but it says no drivers installed?

HELP please

---

### Post by incubus on 2006-09-11
puerco,

I got exactly the same problem, namely, there's no 64bit driver for our dear Netgear wireless USB dongle (which means, you can't load the existing one into the 64bit kernel). I don't know any solution to this, so I've been using the network cable instead.

Very annoying.

Please let me know if you find any workaround.

incubus

---

### Post by elpuerco on 2006-09-12
Bums!

This will not please my brother!  I convinced him to convert to Kubuntu and the network is the most important thing OS wise these days!!

Will need to asses the options open to him...

Thnx

---

