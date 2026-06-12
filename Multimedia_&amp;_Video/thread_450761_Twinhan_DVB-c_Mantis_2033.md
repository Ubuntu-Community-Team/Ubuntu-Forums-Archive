---
title: "Twinhan DVB-c Mantis 2033"
date: 2007-05-21
forum: Multimedia &amp; Video
---

### Post by cPH on 2007-05-21
Hi, 

I am growing more and more desperate ](*,). On my way of building a media center PC (Ubuntu Feisty + MythTV) I need to make my DVB-c card work properly with my system (Twinhan DVB-c 2033 Mantis). As I am a newbie, I try learning a lot. Nevertheless, I's still not able handling proprietary hardware like this TV card. I am not sure if it is supported by Ubunty Feisty as default. I still don't know much about custom kernels and/or modules. 
Anyway, there are still some infos that I'd like to share with you:
[LIST=1]
[*]lspci -v responds with```
04:09.0 Multimedia controller: Twinhan Technology Co. Ltd Mantis DTV PCI Bridge Controller [Ver 1.0] (rev 01)
Subsystem: Twinhan Technology Co. Ltd Unknown device 0008
Flags: bus master, medium devsel, latency 32, IRQ 11
Memory at fdaff000 (32-bit, prefetchable) [size=4K]
```
[*]Twinhan offers a linux download at [http://www.twinhan.com/files/driver/AW/AZLinux_v1.4.2_CI_FC6.tar.gz]("http://www.twinhan.com/files/driver/AW/AZLinux_v1.4.2_CI_FC6.tar.gz"). Maybe this is the solution for integrating this DVB-c card into Ubuntu Feisty
[*]Twinhan is formerly known as Azurewave
[/LIST]
Hopefully, somebody can help and guide me through making this card powering MythTV. 

Thanks in advance, 
cPH ;)

---

### Post by jmartich on 2007-10-24
I know you posted this a long time ago. I got my hands on one of these things, & I can't get it to work with a windows machine my next step was going to be my linux box. I was wondering how far you got with this project?  as for that driver link if you noticed that it had the letters FC in it, that's for another linux distro, called Fedora Core Which I'm pretty sure you figured out by now. I'm also pretty sure that u understand that ubuntu is a debian linux distro, it uses deb file extesion's which are the equivalent of rpm's in fedora core aka redhat, I don't care whut anyone says. N-E wayz I really wanna know if you got this to work. i know you asked for help 1st, but I'm asking now. check out my crappy website some time [http://martekx2.dvrdns.org](http://martekx2.dvrdns.org)

---

### Post by vemon on 2007-10-25
I'm interested in this too. I just found instructions in Finnish from the Finnish Ubuntu forums ([http://forum.ubuntu-fi.org/index.php?topic=3535.msg80675#msg80675](http://forum.ubuntu-fi.org/index.php?topic=3535.msg80675#msg80675)) and I took liberty to transate it to english. This guide has been reported to work at least in Ubuntu Gutsy:

-----------------------

1. Install tools necessary for building the driver:

sudo apt-get install build-essential linux-headers-`uname -r`

2. Download driver:

wget [http://jusst.de/manu/mantis-v4l-dvb.tar.bz2](http://jusst.de/manu/mantis-v4l-dvb.tar.bz2)

3. Unpack the driver:

tar -xf mantis-v4l-dvb.tar.bz2

4. Move to the unpacked directory

cd v4l-dvb

5. Set the kernel version for make

make release VER=`uname -r`

6. Build the driver

make

7. Install the driver

sudo make install

8. Boot the machine and keep your fingers crossed

-----------------------

I haven't had time to try it out myself yet but I'll post the results to this thread when I do. Please post your results here too :).

NOTE: For all the channels to show up in scanning from Finnish cable network a patch is needed. Finnish people can grab it from this thread: [http://www.linuxtv.fi/viewtopic.php?t=2415](http://www.linuxtv.fi/viewtopic.php?t=2415)

---

### Post by zapmandm500c on 2007-11-24
Tried this but cannot get it to work. Is a ubuntu (and linux) newbie. Really want my twinhan mantis 2033 card to work in ubuntu.

Please give me some extra advice.

---

### Post by jackcy on 2007-11-24
Hi there,
this worked fine for (k)ubuntu 7.04
I am really glad I didn't wipe the whole system, instead I made a test installation.

When compiling the driver on 7.10 the following error occurs during make:

  CC [M]  /home/xxx/download/v4l-dvb/v4l/dvb_net.o
/home/xxx/download/v4l-dvb/v4l/dvb_net.c: In function 'dvb_net_eth_type_trans':
/home/xxx/download/v4l-dvb/v4l/dvb_net.c:186: error: 'struct sk_buff' has no member named 'mac'
make[3]: *** [/home/xxx/download/v4l-dvb/v4l/dvb_net.o] Error 1
make[2]: *** [_module_/home/xxx/download/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** [default] Fehler 2
make[1]: Verlasse Verzeichnis '/home/xxx/download/v4l-dvb/v4l'
make: *** [all] Fehler 2

Does anybody know how to get rid of this?

thanks

---

### Post by jackcy on 2007-11-25
So, finally I got rid of this cruel compilation error. I found a hint on [http://www.vdr-portal.de/board/print.php?threadid=54364&page=2&sid=a0849abc71732fb9a79875c8af56b11a](http://www.vdr-portal.de/board/print.php?threadid=54364&page=2&sid=a0849abc71732fb9a79875c8af56b11a)
Here is how I could compile the mantis driver for Twinhan Technology Co. Ltd Mantis DTV PCI Bridge Controller [Ver 1.0] (rev 01) on 
Kubuntu 7.10


cd /tmp
#make sure_ krenel sources are installed
sudo apt-get install build-essential linux-headers-`uname -r`
#downloading driver
wget -c [http://jusst.de/manu/mantis-v4l-dvb.tar.bz2](http://jusst.de/manu/mantis-v4l-dvb.tar.bz2)
#unpacking driver
tar -xf mantis-v4l-dvb.tar.bz2
#modifying dvb_net
sed "s/skb->mac.raw=skb->data;/skb_set_mac_header(skb,0);/g" /tmp/v4l-dvb/linux/drivers/media/dvb/dvb-core/dvb_net.c > /tmp/dvb_net.c
#copying new dvb_net to correct directory
cp /tmp/dvb_net.c /tmp/v4l-dvb/linux/drivers/media/dvb/dvb-core/dvb_net.c
cd v4l-dvb
#run installation
make distclean
make release VER=`uname -r`
make
sudo make install

Perhaps someone needs this too.

---

### Post by McBlau on 2007-12-02
i had no problems with compiling the above sources on Ubuntu 7.04 (Server), but the card tuned only to 1 channel :-(

what i did, was merging the sources (and commented some stuff out) from digitalrise into these from jusst.de and now everything is ok  - well the channel search and epg-grab in mythtv was a nightmare, but with spending enough time.. ;-) 

meanwhile something seemed to move on, see [http://forum.digitalrise.biz/viewtopic.php?t=1103]("http://forum.digitalrise.biz/viewtopic.php?t=1103")

---

### Post by sabbe on 2008-01-01
Nice. Very useful :)

---

### Post by MagnusL on 2008-04-27
I have one of these cards (I believe, it's Azurwave DVB-C AD-CP300) - but I cannot get it to work. I am running Gutsy for the moment. I have tried compiling the source from [http://jusst.de/manu/mantis-v4l-dvb.tar.bz2](http://jusst.de/manu/mantis-v4l-dvb.tar.bz2) with: 

make distclean
make release VER=`uname -r`
make
sudo make install

And I tried the fix presented earlier in this thread, 

#modifying dvb_net
sed "s/skb->mac.raw=skb->data;/skb_set_mac_header(skb,0);/g" /tmp/v4l-dvb/linux/drivers/media/dvb/dvb-core/dvb_net.c > /tmp/dvb_net.c
#copying new dvb_net to correct directory
cp /tmp/dvb_net.c /tmp/v4l-dvb/linux/drivers/media/dvb/dvb-core/dvb_net.c

Both ways the complie and install works fine - however, there seems to be some conflict with ivtv, as my earlier installed Hauppauge PVR-350 stops working. 

In Mythtv, the card seems to be detected, though sometimes it says "ERROR_OPEN". And I cannot scan any channels. 

So what are the status for the rest of you using this dvb-c card? Anyone got it working right, including CI/CA-module?

Magnus L

---

### Post by jackcy on 2008-06-27
There is a modified driver available for the card at [http://jusst.de/hg/mantis/]("http://jusst.de/hg/mantis/") which works without modifying the source.

It seems to recognize the common interface too, but yet the austrian orf card is not working. Other channels work fine when ci is removed.

---

