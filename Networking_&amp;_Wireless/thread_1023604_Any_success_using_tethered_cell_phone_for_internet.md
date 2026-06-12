---
title: "Any success using tethered cell phone for internet access?"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by Donny Bahama on 2008-12-28
Is there some way to use a tethered cell phone for internet access?

My (Windows Mobile-based) cell phone has "Internet Sharing", which gets me better than dial-up throughput, but the linkage that makes this possible is MS ActiveSync, so it only works when I boot Windows. 

Is there a way to make this work in Ubuntu?

---

### Post by ieee488 on 2008-12-28
[http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu)

---

### Post by Donny Bahama on 2008-12-29
Let me get this straight...

In order to connect to the internet, you want me to install SynCE.
In order to install SynCE, I'm supposed to apt-get drivers and core libraries (which will require an internet connection?!)

---

### Post by ieee488 on 2008-12-29
Most people have a **wired** internet access.
If you don't, then you can forget about this idea. Simple as that.

---

### Post by Donny Bahama on 2008-12-29
As simple as that, is it. You don't think I could boot into Windows (where I *do* have net access via my WM cell phone), download the necessary .deb files and install the needed packages?

I appreciate you trying to help, but giving people false information does more harm than good.

---

### Post by ieee488 on 2008-12-29
What is "false" about the information I gave?

If you don't have it, then you can't use it.

With your snarky attitude, let someone else be the recipient of it.

Over and out.

---

### Post by razy60 on 2008-12-29
Not sure how it works using windows mobile, but if you can access the net just using a mobile network i.e 3 or vodafone etc(you wold have to decide the cost effectiveness, i pay a separate charge for mobile internet) you can use  your mobile phone as a modem. You would need network manager 0.7 or one of the other managers that can be found in synaptic.

Raz

---

### Post by rjmatthews62 on 2008-12-29
> **Donny Bahama said:**
> As simple as that, is it. You don't think I could boot into Windows (where I *do* have net access via my WM cell phone), download the necessary .deb files and install the needed packages?

I appreciate you trying to help, but giving people false information does more harm than good.

Try here:
[http://packages.ubuntu.com/intrepid/synce-kpm](http://packages.ubuntu.com/intrepid/synce-kpm)

---

### Post by Donny Bahama on 2008-12-29
> **ieee488 said:**
> What is "false" about the information I gave?You don't have to have net access from within Ubuntu. If you have net access from Windows (as I stated) then it *is* possible to get the needed packages from there, then boot into ubuntu and install there.> With your snarky attitude, let someone else be the recipient of it.Sorry if my attitude seemed "snarky"; I didn't intend that. I did say that I appreciated your help. But these forums support a lot of noobs, and giving out misinformation is a really bad thing. While I am quite a noob myself when it comes to ubuntu, I knew that it was not "as simple as that". (Things rarely are.)

---

### Post by Donny Bahama on 2008-12-29
> **razy60 said:**
> Not sure how it works using windows mobile, but if you can access the net just using a mobile network i.e 3 or vodafone etc(you wold have to decide the cost effectiveness, i pay a separate charge for mobile internet) you can use  your mobile phone as a modem. You would need network manager 0.7 or one of the other managers that can be found in synaptic.

RazThanks, Raz. I access the internet using AT&T's mobile network (and I, too, pay an extra monthly charge.) Not familiar with vodafone, etc., but my net access isn't limited or WAP, etc. It's full access, and I can connect my phone via USB to my notebook and full net access. (It's how I am connected at this moment.) But it requires ActiveSync to make it happen. You're saying that network manager 0.7 will recognize my phone as a USB modem somehow? If so, that'd be just what I'm looking for. Could you possibly direct me to where I can download the .deb package? I don't yet know ubuntu well enough to know where "synaptic" is.

---

### Post by Donny Bahama on 2008-12-29
> **rjmatthews62 said:**
> Try here:
[http://packages.ubuntu.com/intrepid/synce-kpm](http://packages.ubuntu.com/intrepid/synce-kpm)
I'm actually using gOS, which is based on Ubuntu, but I'm not sure it's intrepid. Is there some menu item somewhere that I can use to find this out?

---

### Post by razy60 on 2008-12-29
[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

above should be the link to the web site. there should be a help facility on the site, i would imagine that you would either need to download and install using a package manager, i use synaptic in Ubuntu or maybe you would need to manually install using a terminal(sorry cant help with that as im a bit new at this myself).
vodafone etc are uk mobile providers.

Raz

P.s the version you are running is normally under:System: About Ubuntu

---

### Post by SaintDanBert on 2009-03-03
> **Donny Bahama said:**
> Thanks, Raz. I access the internet using AT&T's mobile network (and I, too, pay an extra monthly charge.) ...  It's full access, and I can connect my phone via USB to my notebook and full net access. (It's how I am connected at this moment.) 

I'm trying to get my tethered phone working.
The logs show complaints about rndis_host 

kernel: usbcore: registered new interface
    driver cdc_ether
kernel: Device driver eth1 lacks bus 
    and class support for being resumed.
kernel: eth1: register 'rndis_host' at
    usb-0000:00:1a.1-1, RNDIS device, 
    80:00:60:0f:e8:00
kernel: usbcore: registered new interface 
    driver rndis_host
dhcdbd: message_handler: message handler 
    not found under /com/redhat/dhcp/eth1 
    for sub-path eth1.dbus.get.reason
dhcdbd: Unrequested down ?:3
kernel: usb 3-1: USB disconnect, address 2
kernel: eth1: unregister 'rndis_host' 
    usb-0000:00:1a.1-1, RNDIS device

When I run 'lsmod' the rndis_host module is loaded.

Can someone help me out?

~~~ 0;-D

---

### Post by rwslippey on 2009-03-03
Hello all,

Looking to tether my sprint phone a Palm Treo 800w with my laptop for mobile internet purposes.
Laptop is running 8.10

and yes I DO pay the extra monthly charge for the service, I'm just unable to use it currently (makes perfect sense doesn't it)

can anyone help?

Thanks in a advance.

---

### Post by srt4play on 2009-03-03
> **Donny Bahama said:**
> I'm actually using gOS, which is based on Ubuntu, but I'm not sure it's intrepid. Is there some menu item somewhere that I can use to find this out?

```
cat /etc/issue
``` should give a clue to your system version.  I can confirm network manager .7 in Ubuntu 8.10 works very well for tethering my laptop to my cell phone for internet access. The phone is a Samsung Omnia running windows mobile.  

I would strongly suggest anyone trying to do this to test the functionality with an intrepid live cd and then upgrade your system accordingly.

---

