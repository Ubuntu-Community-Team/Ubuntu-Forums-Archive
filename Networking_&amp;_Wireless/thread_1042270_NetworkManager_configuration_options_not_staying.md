---
title: "NetworkManager configuration options not staying"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by rmjb on 2009-01-17
Hello,

I'm using NetworkManager 0.7 to connect to the internet via CDMA. If I leave the ppp compression options on I get a dead connection. When I turn the three compression options off my net connection works, but the compression options come back on after a little while.

Is there a way to get the configuration to stay? Where is the configuration stored?

- rmjb

---

### Post by sandip26879 on 2009-01-17
I also use CDMA by TATA INDICOM. It is already present in network manager's Mobile Broadband in India. But its ISP phone number is erroneous. I rectified it and tried to connect. But in failure. Then I saw that "Auto Mobile Broadband (CDMA) Connection" has been added automatically, again with wrong phone number. So again I corrected it and choose the option "Automatic Connection". Now it gets connected automatically as I plug the USB CDMA modem. But the internet is very slow.

Then I planned a different thing. I disabled the network from network manager. After that I configured wvdial from command prompt. The modem is detected and configured automatically. Then I edited /etc/wvdial.conf and put the user name, password and phone number. Now I connect using the command sudo wvdial. Now I got a tremendous improvement in browsing as well as downloading.
So the culprit was network manager. Perhaps it needs more development.

---

### Post by rmjb on 2009-01-19
To get around this I deleted the network and when I added it back I chose System Setting and turned off the compression options during the creation of the entry. On doing this they stayed.

- rmjb

---

