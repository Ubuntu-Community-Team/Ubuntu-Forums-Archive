---
title: "Export stored wifi keys from hardy?"
date: 2011-01-24
forum: Networking &amp; Wireless
---

### Post by antmenj on 2011-01-24
I am running hardy on my laptop and was thinking its time I upgraded.  One thing thats been holding me back is I have a number of wifi keys stored in there somewhere and can't remember what they were exactly.  Are they exportable?

---

### Post by gmargo on 2011-01-25
This may not apply to Hardy, but the Network Manager in Maverick seems to store the key info under **/etc/NetworkManager/system-connections/**.

I found that with a simple search of the filesystem, which should work for Hardy.  Substitute your Wifi name in the grep:
```

$ cd /etc
$ sudo find . -type f -exec grep -Hn WIFI_NET_NAME_HERE {} \;

```If it's not there, then check $HOME too.

---

### Post by antmenj on 2011-01-28
I'v found some info in /home/username/.gconf/system/networking/wireless/networks/

Only thing is what to do with it now??  Will they be compatable with Lucid.

Does your version contain a list of directories for each network with an xml file in it?

---

### Post by antmenj on 2011-01-31
Managed to contact the system admin at the main place I was after and get the password via conventional means:KS  It took him a wile to remember it last time but its writen down now:rolleyes:

Wile its not solved technicaly its solved for me:guitar:

---

