---
title: "ubuntu wireless and linksys wrt-54gs with dd-wrt"
date: 2006-06-28
forum: Networking &amp; Wireless
---

### Post by djsamsel on 2006-06-28
i just "upgraded" my 54gs using the firmware from dd-wrt. all of my windoze computers still connect just fine. however, my ubuntu wireless connection either does not connect, or will connect after 3 to 5 minutes and then lose the signal immediatly after connecting. i have the same router at my office, that i have not upgraded and i have no problems connecting there. i'm using g-network-manager to manage my connections. sometimes i get a pop us asking for wep security passphrase, then one of the green lights on g-n-m comes on, the arrows circle for a couple of minutes, then the second light, then the bars show up for a second showing 100% connection for about 2 seconds then it drops to 0%. sometimes it will cycle like that, other times it just quits trying. any suggestions on how to fix this, or how to even diagnose what's going on? thanks, doug

---

### Post by bswindell77 on 2007-02-15
I started with DD-Wrt on my wrt54g and thought that the wireless card on my laptop wasn't working (bcm4318) tried for days and found out it was the router after I replaced the firmware back to linksys.

I tried DD-WRT, VxWare, And that other linux based one and they all did that. I guess linux can't handshake with other linux.

I read in a  forum somewhere that it has something to do with the first bit of info sent for the handshake. The handshake is achknoldeged then dropped or something like that.

---

### Post by tiepolo on 2007-02-15
I'm using wrt-54g v5 with dd-wrt since a long time - no problem of any kind with bcm43xx card, neither a rt2500, nor with another wrt-54g dd-wrt used as a bridge. I was never able to use network-manager, but it runs perfectly by setting wpa parameters in /etc/network/interfaces and /etc/wpa_supplicant.conf.
No packet lost; I can help if needed

---

### Post by bswindell77 on 2007-02-16
Maybe djsamsel will use your help. I think I am going to stick with linksys firmware. I didn't really need all the features of DD-WRT. Just thought that is was cool to do. The only thing I really messed with was the txPower and that did help much anyway. I have wrt54g v 4 and not using as a bridge... Maybe that is the difference.

thanks

---

### Post by bionnaki on 2007-02-16
I recommend thibor 15c instead: [http://www.thibor.co.uk](http://www.thibor.co.uk)

I use it (wrt54g v4) with a wmp54g (rt2500 cvs driver) and it works flawlessly.

---

