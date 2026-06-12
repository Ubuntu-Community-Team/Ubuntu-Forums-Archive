---
title: "Firestarter and pppoeconf, too many interfaces"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by Nibblyn on 2009-03-30
At the beginning she had an ADSL internet connection, coming with the telephone line. The computer was connected with an ethernet card through a standard ethernet cable (with a RJ-45 connector) to an ADSL modem, attached to the telephone line. Configuration was unnecessary as everything worked out of the box. Firestarter worked flawlessly doing a proper job.

Then she switch the internet provider. The new one is offering a cable connection. Actually she has a standard ethernet cable (with a RJ-45 connector) coming directly into the house, so she does not see any modem. The connection uses PPPoE and requires authentication (username, password). There is no local network as she only owns one single machine. She was unable to configure it through the NetworkManager applet but used pppoeconf instead as suggested in Ubuntu Help Center. Now the internet connection works well except for the firewall (firestarter). After every reboot the machine picks up a different interface (ppp0, ppp1, ppp2) which makes difficult to configure firestarter properly. She purged firestarter (removed all configuration) and reinstalled it. That obviously didn't help. She has to configure firestarter every time to use the proper interface (ppp0, ppp1 or ppp2) the one which actually has traffic coming through.

**Today ifconfig reports only ppp0 and ppp1 and not ppp2 which was the one in use yesterday. So... how is this possible?** Why so many interfaces? Take a look at the report below: how can traffic come through different interfaces with different ip? :confused: Well... if you can hint... many thanks.

The output of: (as attachments)
...ifconfig
......cat /etc/network/interfaces
..........cat /etc/ppp/peers/dsl-provider

---

