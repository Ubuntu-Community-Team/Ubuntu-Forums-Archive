---
title: "cntlm- Automatic Proxy configuration URL"
date: 2011-11-03
forum: Networking &amp; Wireless
---

### Post by baby_panda on 2011-11-03
Hi my college uses an automatic proxy configuration url ([http://****.com/proxy.pac](http://****.com/proxy.pac)) for using the internet. (used in Mozilla Firefox, etc.). How should i configure cntlm to use this url? /etc/cntlm.conf has entries for providing proxy name and port. Can i I specify the url there (at the field Proxy) ? (I want to use cntlm for updating ubuntu and installing packages.)

---

### Post by kungfujones on 2011-11-03
I am having a similar issue. I have set my network proxy setting to my auto proxy url just like baby_panda has done, and then clicked the apply system wide button. However, when I attempt to download software using the ubuntu software center it fails to connect. If I try to change my software source it doesn't help, and if I click the choose best server button it says it cannot connect to the internet (asks me to check my internet connection). My internet connection works fine through mozilla, but for some reason the software center is unable to connect. Any ideas?
Thanks.

---

### Post by GreySpike on 2012-04-09
I know this is an old thread, but this may not be a proxy issue as such.

*sudo apt-get ...* doesn't inherit the proxy settings as almost all the environment is removed

[I]sudo -i
apt-get ...[/I] does get the proxy environment settings and therefore works for me via cntlm

Hope this helps.

---

### Post by filipovskii_off on 2012-04-13
> **baby_panda said:**
> Hi my college uses an automatic proxy configuration url ([http://****.com/proxy.pac](http://****.com/proxy.pac)) for using the internet. (used in Mozilla Firefox, etc.). How should i configure cntlm to use this url? /etc/cntlm.conf has entries for providing proxy name and port. Can i I specify the url there (at the field Proxy) ? (I want to use cntlm for updating ubuntu and installing packages.)

You can save the file with automatic configuration, by opening given url in your browser. In this file you can find proxy address and port, that have to be specified in /etc/cntlm.conf

That solution doesn't work, if you have lots of complex rules in proxy configuration. 

Maybe there is another way of doing it.

---

