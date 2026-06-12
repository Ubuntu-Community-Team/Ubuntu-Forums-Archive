---
title: "lan via bluetooth on ubuntu 9.10"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by Tarasov on 2010-01-10
Good day.
----------------------------------------------------------------------------------------------------------
The situation is this:
There is a desktop PC which has internet from  cable modem. (eth1 interface)
There netbook ASUS PC EEE 901.
On both machines cost UBUNTU 9.10.
----------------------------------------------------------------------------------------------------------

Objective - to distribute the Internet from desktop  on netbook from  bluetooth.
----------------------------------------------------------------------------------------------------------

What was done:
both companies, the following packages:
1.bluez
2.bluez-compact
3.bluez-hcidump
4.bluez-utils
5.libbluetooth3
6.libbluetooth-dev
7.bluez-gstreamer
8.bluez-cups
9.btscanner
10.bluetooth
11.blueman
With blueman able to connect PC and netbook, transfer files, find the phone and use it as a modem.
To configure the network using bluetooth Similar articles [http://lice.wordpress.com/2006/10/29/inet-forwarding-via-bluetooth/](http://lice.wordpress.com/2006/10/29/inet-forwarding-via-bluetooth/), which many on the forum and not only. Immediately it became clear that:
1.In directory / etc / bluetoth no file / etc / bluetooth / hcid.conf. There are only these: audio.conf input.conf main.conf network.conf rfcomm.conf.
2.On server  (desktop PC) do
```
pand –listen –role NAP 
```On client (netbook) do
```
 pand –connect DESKTOP_MAC_ADDRESS 
```the server window appears to enter a PIN code (which is fast disappearing somewhere for 5 seconds, but you can manage to lead 111) and then the same window appears on the client but does not disappear. After the exchange of PIN codes should appear bnep0 interface but this does not happen, and the command pand-l produces no output ..
If you try to ifconfig bnep0 10.0.0.1 on the server receives
</span>```
SIOCSIFADDR: No such device
bnep0: &#1054;&#1064;&#1048;&#1041;&#1050;&#1040; &#1087;&#1088;&#1080; &#1087;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1080;&#1080; &#1092;&#1083;&#1072;&#1075;&#1072; &#1080;&#1085;&#1090;&#1077;&#1088;&#1092;&#1077;&#1081;&#1089;&#1072;: No such device

```I suspect that this is due to the fact that not working bnep0.
------------------------------------------------------------------------------------------------------
Friends, if someone set up the network via bluetooth to 9.10 ubuntu  show me how I can do that. Also interesting
1. Why no files / etc / bluetooth / hcid.conf
2.Why input box pin code so quickly rolled on the server
3. Why  bnep0 is not working.

---

