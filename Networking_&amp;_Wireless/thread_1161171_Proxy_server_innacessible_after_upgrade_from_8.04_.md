---
title: "Proxy server innacessible after upgrade from 8.04 to 8.10"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by robgwynne on 2009-05-16
Sorry for the inane question - I'm sure I've just done something dumb, but I upgraded to 8.10 from 8.04 yesterday and since then have not managed to persuade the 8.10 system to use the existing (unmodified) proxy server (cable modem router / WAP - Azurewave NR580).

I can't easily post screenshots as there is (now) no internet connection on the machine that has the problem - sorry!

ifconfig reported that eth0 (the main ethernet connection on the machine) had a static IP.  Managed to sort that out and now it gets an IP address from the router and the router has the machine logged in its client list, but that's as far as I can get :-(

I've set up all combos of Direct/Manual/Automatic proxy settings in the System->Preferences->Network_Proxy_settings app... no difference - except on auto Firfox times out and other apps report they can't use Automatic proxy settings detection. I've tried setting all combos of proxy setting in the Firefox control panel too - either times out or reports '400 Bad Request' if I select Manual and point to the router.

I've scanned the router and port 80 seems to be the one to use for http - I've tried all the other common ones too... to no avail.

I can ping the router and open its admin web page from the broken machine. I can also see every other machine on the network.  

I've run out of obvious things to do and now I'm stuck:-(

I hope someone can tell me the obvious, dumb mistake I've made... there was me thinking that an upgrade would be straight forward!  That'll teach me :-)

Thanks in advance for any suggestions!
rob

---

