---
title: "Teamviewer alternatives"
date: 2013-05-13
forum: Networking &amp; Wireless
---

### Post by justinflux on 2013-05-13
Hi there

I am wanting to remote desktop to an ubuntu 12.04 server over public internet.
Teamviewer is expensive and I don't need file transfer capabilites.
What are my options as I cannot VPN to the server as it is connected to the internet using a USB 3G modem which blocks port access on incoming.
Can I achieve this somehow without paying alot?

Thanks, Justin

---

### Post by PowerBarry43 on 2013-05-13
Hi

Hamachi ([https://secure.logmein.com/labs/#HamachiforLinux](https://secure.logmein.com/labs/#HamachiforLinux)) VPN should still work with rdesktop or VNC.

Hope this helps!

Barry

---

### Post by justinflux on 2013-05-13
I dont believe Logmein supports linux server?
Are there any other alternatives to Logemein or Teamviewer for continuous remote access?

---

### Post by PowerBarry43 on 2013-05-13
logmein hamachi for linux is in beta, there is no graphical user interface although a third party one has been developed called haguichi which works a treat. To be clear, although you are installing onto a linux server, what you actually need is a VPN _client_ with the server provided by logmein for free hamachi fulfils this requirement. I have hamachi running on my home linux server and the machine that I am currently typing this post from (ubuntu 13.04) all working no problems. to install hamachi on linux run:

for 64 bit
 
```
wget https://secure.logmein.com/labs/logmein-hamachi_2.1.0.86-1_amd64.deb
sudo dpkg -i logmein-hamachi_2.1.0.86-1_amd64.deb ; sudo apt-get install -f
```

for 32 bit

```
wget https://secure.logmein.com/labs/logmein-hamachi_2.1.0.86-1_i386.deb
sudo dpkg -i logmein-hamachi_2.1.0.86-1_i386.deb ; sudo apt-get install -f
```

Barry

---

### Post by slickymaster on 2013-05-13
What about [VNC]("https://help.ubuntu.com/community/VNC")?

---

### Post by justinflux on 2013-05-13
Hi Barry

Thanks for these insights.
Can you explain further regarding needing a VPN client.
Is there a recipe of sorts you would recommend?

Justin

---

