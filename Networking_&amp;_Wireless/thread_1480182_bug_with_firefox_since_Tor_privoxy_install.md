---
title: "bug with firefox since Tor /privoxy install"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by yayou on 2010-05-11
Hi everybody

I really need your help. I tried to configure Tor with privoxy yesterday. I followed ubuntu.fr tutorial but since today, I can't access Internet from firefox whereas I've succeeded to ping [www.google.fr](www.google.fr). 
I went on firefox settings and choose Manual proxy configuration. This is my Proxy HTTP field: localhost and my port field: 8118.
I've also checked Use this proxy for all protocol and erase informations in the field No proxy for.
Finally, I went to see my logfile in /var/log/privoxy and this is what is written:
May 10 11:31:31.205 b786B8D0 Fatal error: can't bind to localhost:8118 The hostname is not resolvable (so this is for yesterday)
and for today it's the same.

Please could you help me? I thought of desactivating or deinstalling Tor or/and privoxy but I don't know if this could bring back my previous good configuration.

---

### Post by yayou on 2010-05-12
Please, just tell me if it could be good to deinstall Tor and privoxy?

thanks to all for devoting some of your time to my problem.

---

### Post by yayou on 2010-05-12
I also have to tell you that I didn't install torButton.

---

### Post by impert on 2010-05-12
Hi yayou,  salut!
I've just installed Tor, so I'm no expert. I installed the Torbutton from Firefox addons, and then followed the instructions on the [Tor Debian/Ubuntu]("http://http://www.torproject.org/docs/debian.html.en#ubuntu") page and had no problems. Tor advise you to copy their [**polipo config**]("http://https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/config/polipo.conf") file and use it in place of the privoxy one; and that is what I did. The installation also worked perfectly (so far) on Trisquel (Debian variant), using the Ubuntu karmic repo. I did nothing about configuring ports etc., I just followed the instructions.
I think it's worth installing the Torbutton - Tor is inevitably slower than normal browsing, you probably won't want to use it all the time.
If you want to keep privoxy and not change to polipo, you could try deleting your ~/.mozilla file and then restarting Firefox.

---

### Post by yayou on 2010-05-13
thank you impert,
My problem now is that Internet is not accessible for me now since I tried to install Tor/Privoxy.
I think that the only thing I can do is to deinstall Tor and Privoxy, but first of all I wanted to know it could make things worst.

I'm searching if there is a deinstall procedure for both software.

---

### Post by yayou on 2010-05-18
First of all, I would like to say thanks to you impert. Finally I went on tor project site and realized that the problem source could be that I've downloaded packages from synaptic. So I have deinstalled Tor and now I can access Internet. Now the only problem I'm facing is that my synaptic update don't work anymore.

---

