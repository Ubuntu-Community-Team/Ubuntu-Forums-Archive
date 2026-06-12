---
title: "Bittorrent performance faster in Windows"
date: 2010-04-19
forum: Networking &amp; Wireless
---

### Post by blazemore on 2010-04-19
I'm a long-time Linux user, Ubuntu in particular, but I also dual-boot with Windows.

Because I use both on a regular basis, I've had a lot of opportunities to compare the two, and while Ubuntu is almost always the winner in whatever category, there is one area where my Windows machine always comes up top, and that is bittorrent download speeds.

I haven't done any rigorous testing, but I've noticed that one torrent downloading on Windows with uTorrent will regularly exceed around 800kb/s (my absolute theoretical maximum is 1024kb/s)

On Ubuntu, the same torrent using Deluge, Transmission, Ktorrent, rTorrent, you name it (even uTorrent under Wine) will rarely achieve half that speed.

Same hardware, same torrent settings.

So why is this, do you think?
I'm interested in hearing any ideas!

---

### Post by never say never on 2010-04-19
First thought is perhaps you don't have the correct port(s) forwarded to your linux box (or open in your firewall).

Second thought would be an MTU issue.  How are you connected to the internet?

Ever done any speed tests for downloading and uploading?

---

### Post by blazemore on 2010-04-19
> **never say never said:**
> First thought is perhaps you don't have the correct port(s) forwarded to your linux box (or open in your firewall).

Second thought would be an MTU issue.  How are you connected to the internet?

Ever done any speed tests for downloading and uploading?

Firstly, it's the same network card, the same router (I don't use any software firewalls) and the exact same PC. On both Windows and Linux, the torrent software reports the ports as being open, as my router supports uPnP.

Secondly, I'm connected to the Internet with an ADSL connection over a wireless router. In a lot of cases, the wireless connection is the slowest point in the network, although it varies wildly.

Thirdly, this difference in speed occurs on straight HTTP traffic as well (say, downloading an Ubuntu iso) but the difference is far more pronounced when using Bittorrent.

---

### Post by never say never on 2010-04-19
It is either an MTU size issue or more likely a buffering issue, especially since you are using wireless.

Look up the wireless card and make sure your config files for the card optimize it's throughput.  There are a lot of options that can affect throughput over wireless.  For instance on my laptop under linux it sends out a weaker signal, until I adjusted the settings to increase the power.

---

### Post by terrrorr on 2010-04-19
> For instance on my laptop under linux it sends out a weaker signal, until I adjusted the settings to increase the power. 

I agree. I also encountered some difficulties with my laptops wireless connection previously. But when i tested another Wifi card (external) on my laptop, wireless connection started to work much faster and with better link quality.

current laptop: Lenovo R61
Old laptop: HP NX6120

---

### Post by blazemore on 2010-04-20
> **never say never said:**
> Look up the wireless card and make sure your config files for the card optimize it's throughput.  

Where can I find these options?

---

### Post by never say never on 2010-04-21
Take a look at iwpriv.  The options available vary by card.  You may or may not be able to adjust the settings to cure the problem.

---

