---
title: "Problem accessing internet via wireless connection"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by mguidoux on 2009-03-29
Hi!

I have two PCs, one running, Intrepid Ibex (let's call it Ibex), is  with a D-link wireless router connected to a DSL modem. On the other one I'm using Gutsy Gibbon (let's call it Gibbon), connected to a D-link wireless adapter (DWL-G122). 

The fact is using Gibbon I find several wireless networks, including the one I've created on Ibex. Everythings seems to be working fine, I choose to connect on the network I created, a window pops open asking for the passphrase. I type in the passphrase and the icon with the network status bar appears on the toolbar saying "Wireless network connection to 'My network' (87%).

The problem is, even though Gibbon is connected to the network, I can't use internet. I open firefox and it can't open any webpage ('Server not found').

I'm using the same internet connection on Ibex and it's working fine.

Can anyone shed a light?

---

### Post by s.dalas on 2009-03-29
it may sound a little stupid but you have you check if the "work offline" is unchecked in the web browser?

---

### Post by mguidoux on 2009-03-29
No, that option is not checked. The problem is not just with Firefox, Piding and even the Update Manager can't find any internet connection.

:(

---

### Post by s.dalas on 2009-03-29
there are also some privileges under system-administration-user and groups (let user connect to wireless , connect to internet and other). try this also but i can't think of something else... :(:confused:

---

### Post by mguidoux on 2009-03-29
The only related privilege I've found under system-administration-user and groups is "Connect to internet using a MODEM" and it is checked. But the only privileges that are NOT checked are "Allow use o fuse filesystems", "Send and receive faxes" and "Use tape drives".

---

### Post by mguidoux on 2009-03-29
I don't know if this means the connection is breaking, but now, every few minutes a Wireless Network Key Required window pops up, asking me for the passphrase. I type it in it connects as usual (87%) and then a few minutes later the window pops up again.

But still no internet...

---

### Post by transmition on 2009-03-29
Maybe you are not getting an IP address assigned. What is the output of iwconfig?

---

### Post by mguidoux on 2009-03-29
The output of iwconfig is:

> 
lo            no wireless extensions.

eth0          no wireless extensions.

wmaster0      no wireless extensions.

wlan0         IEEE 802.11g ESSID:"Bonobo"
              Mode:"Managed" Frequency:2.437GHz Access point: 00:21:91:72:9B:B8
              Retry min limit:7  RTS thr:off  Fragment thr:2346 B
              Link Signal Level:-38 dBm
              Rx invalid nwid:0  Rx invalid crypt:0 Rx invalid frag:0
              Tx excessive retries:0  Invalid misc:0   Missed beacon:0


---

### Post by mguidoux on 2009-03-29
I don't know what this output means, can anyone help?

---

### Post by mguidoux on 2009-03-29
I run $ dmesg | tail -50 and got the following output:

> [11165.456000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[11167.672000] wlan0: Initial auth_alg=0
[11167.672000] wlan0: authenticate with AP 00:21:91:72:9b:b8
[11167.672000] wlan0: RX authentication from 00:21:91:72:9b:b8 (alg=0 transaction=2 status=0)
[11167.672000] wlan0: authenticated
[11167.672000] wlan0: associate with AP 00:21:91:72:9b:b8
[11167.676000] wlan0: RX AssocResp from 00:21:91:72:9b:b8 (capab=0x431 status=0 aid=1)
[11167.676000] wlan0: associated
[11167.676000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[11172.756000] wlan0: deauthenticate(reason=3)
[11173.200000] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[11178.380000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[11222.252000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[11375.220000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[11376.324000] wlan0: Initial auth_alg=0
[11376.324000] wlan0: authenticate with AP 00:21:91:72:9b:b8
[11376.324000] wlan0: RX authentication from 00:21:91:72:9b:b8 (alg=0 transaction=2 status=0)
[11376.324000] wlan0: authenticated
[11376.324000] wlan0: associate with AP 00:21:91:72:9b:b8
[11376.328000] wlan0: RX AssocResp from 00:21:91:72:9b:b8 (capab=0x431 status=0 aid=1)
[11376.328000] wlan0: associated
[11376.328000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[11386.680000] wlan0: no IPv6 routers present
[11437.712000] wlan0: deauthenticate(reason=3)
[11438.340000] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[11439.096000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[11441.124000] wlan0: Initial auth_alg=0
[11441.124000] wlan0: authenticate with AP 00:21:91:72:9b:b8
[11441.124000] wlan0: RX authentication from 00:21:91:72:9b:b8 (alg=0 transaction=2 status=0)
[11441.124000] wlan0: authenticated
[11441.124000] wlan0: associate with AP 00:21:91:72:9b:b8
[11441.128000] wlan0: RX ReassocResp from 00:21:91:72:9b:b8 (capab=0x431 status=0 aid=1)
[11441.128000] wlan0: associated
[11441.128000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[11451.776000] wlan0: no IPv6 routers present
[11490.748000] wlan0: deauthenticate(reason=3)
[11491.128000] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[11492.132000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[11494.156000] wlan0: Initial auth_alg=0
[11494.156000] wlan0: authenticate with AP 00:21:91:72:9b:b8
[11494.160000] wlan0: RX authentication from 00:21:91:72:9b:b8 (alg=0 transaction=2 status=0)
[11494.160000] wlan0: authenticated
[11494.160000] wlan0: associate with AP 00:21:91:72:9b:b8
[11494.160000] wlan0: RX ReassocResp from 00:21:91:72:9b:b8 (capab=0x431 status=0 aid=1)
[11494.160000] wlan0: associated
[11494.164000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[11505.060000] wlan0: no IPv6 routers present
[11600.996000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[11600.996000] wlan0: deauthenticate(reason=3)
[11603.508000] ADDRCONF(NETDEV_UP): wlan0: link is not ready


I don't know if the "wlan0: deauthenticate(reason=3)" has something to do with it asking me from time to time to type in the passphrase.

Anyone?

---

### Post by mguidoux on 2009-04-07
No one can help me?

---

### Post by mguidoux on 2009-04-21
Upgraded the Ubuntu to Hardy and still have the same issue. :/

---

