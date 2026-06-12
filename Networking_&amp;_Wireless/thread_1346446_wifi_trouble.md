---
title: "wifi trouble"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by gustengroda on 2009-12-05
I have been using ubuntu on my laptop for a few years. My d-link dwl-g650+ has been working fine with ndiswrapper until I upgraded to 9.10.

Now it seams like there are some interference between gnome network manager and the previous setup.

I have not managed gnome network manager to connect to my router (WEP).

After every boot I have to disable wireless in gnome network manager and run:

sudo ifdown wlan0
sudo ifup wlan0

The wireless connection is much more unstable in my view and I sometimes has to reinsert my wireless PCMCIA card.

Any ides what to do to get the computer boot with a functional wireless connection?
Thanks,

---

### Post by bridgetbruston on 2009-12-05
With the new release of ubuntu 7.04 the Network Management has become the standard way of connecting to wireless or wired networks in Ubuntu..The connection is only established on login, so time doesn't get synced with the internet on startup.It is a great way for all the Linux roadwarriors to easily connect to all sorts of networks. In this mini-howto I will show you how it is done. I will also show you how to automatically connect after the login without needing to enter your gnome-keyring password.

---

### Post by gustengroda on 2009-12-05
> **bridgetbruston said:**
> With the new release of ubuntu 7.04 the Network Management has become the standard way of connecting to wireless or wired networks in Ubuntu..The connection is only established on login, so time doesn't get synced with the internet on startup.It is a great way for all the Linux roadwarriors to easily connect to all sorts of networks. In this mini-howto I will show you how it is done. I will also show you how to automatically connect after the login without needing to enter your gnome-keyring password.


How do I find your mini-howto?

---

