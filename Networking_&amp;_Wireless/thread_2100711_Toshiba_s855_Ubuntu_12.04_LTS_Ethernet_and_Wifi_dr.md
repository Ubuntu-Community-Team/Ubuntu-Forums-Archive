---
title: "Toshiba s855 Ubuntu 12.04 LTS Ethernet and Wifi drivers don't install"
date: 2013-01-02
forum: Networking &amp; Wireless
---

### Post by Rcode on 2013-01-02
i bought a Toshiba s855 where my  Ubuntu 12.04 LTS Ethernet and Wifi drivers don't install using the live CD.  Ethernet is a Qualcomm Atheros AR8161 PCI-E gigabyte controller and Wifi is a Realtek RT8723A wireless LAN 802.11 PCI-E NIC,

What do i need to do to get them to work. thanks for the help.

---

### Post by Calinou on 2013-01-02
Are you sure they did not install? Did you check "Install third party software"? Maybe you've incorrectly plugged in the Ethernet cable. Or, for the wifi, used the wrong SSID or password.

---

### Post by ubfan1 on 2013-08-07
With both ethernet and wireless broken in 12.04, I'd suggest installing 13.04, which supplies both working drivers.  If you insist on 12.04, use the 12.04.2 version, download (from a working setup/machine) the 8723 drivers (Google for rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz), compile and install, then after the first update, the ethernet will be updated and start working.

---

