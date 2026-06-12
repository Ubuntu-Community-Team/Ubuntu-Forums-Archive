---
title: "VPN to get UK IP?"
date: 2010-11-11
forum: Networking &amp; Wireless
---

### Post by pabc on 2010-11-11
I've recently started to work a couple of days at a time abroad (home is the UK) and Swedish hotel TV isnt great so I'd like to watch the bbc iplayer.

However the content is locked to UK IP addresses.

Is there a way I can set up my netbook proxy setting to point to my home PC and have that relay my http request so that the IP address the BBC sees is valid?

I understand there are commercial solutions to do this, and some open proxies but if I can just use my home PC it would be cheaper / more reliable.

Is VPN the way to go, and if it will do what I want, can anyone point me at a guide to set it up?

---

### Post by pabc on 2010-11-11
ignore that. looks like I can just ssh tunnel into the home box and set up a proxy server.... the googling continues

---

### Post by ottosykora on 2010-11-11
if you succed, let me know, I need similar solution not just for tV, but other things as well. 
Trying to make vpn, but my adsl modem/router does not like it. Dyn DNS account is ok, but the portforwarding in some of those routers is pain.

---

### Post by Jethro_uk on 2010-11-11
Not sure what your netook is running, but I managed something very similar last year, using Putty, on Windows.

Basically I got Putty to SSH to my home machine, and then used it as a proxy. It allowed me to circumvent the firewall of hell that my company ran. I know my brother uses the same approach from the US, for the same reason as you (iPlayer).

---

### Post by pabc on 2011-05-11
i followed this guide : [http://www.linux.com/archive/feed/56945](http://www.linux.com/archive/feed/56945) 
 
then wrote a couple of scripts to wake my home PC using wakeonlan then set up a ssh tunnel on a specific port then configured FF to use that port and voila - a UK IP address in FF and a Swedish one in Chrome.
 
When finished I just ssh into the home box and do a 'shutdown -P now' to drop it again

---

