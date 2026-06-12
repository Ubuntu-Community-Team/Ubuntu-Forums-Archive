---
title: "Wireless connection doesnt work"
date: 2011-09-21
forum: Networking &amp; Wireless
---

### Post by egregor on 2011-09-21
Ive run into a pretty stange problem after having installed 11.4.. any attempts to connect to my router result in a successful connection according to networkmanager, but no connectivity. The syslog indicates DHCP is successful, and it receives a local ip, but I can't ping anything. A few more notes:
- occasionally, immediately after connecting to my ssid, i can connect to external sites by ip address only, but DNS never works. After about 10 seconds, even IP access fades and i cant reach anything until i reconnect. 
- this is ocurring when attempting with multiple cards, whether individually or simultaneously. One is a rt2860 pci-e card, the other is ath9k_htc based. In both cases, the same problem happens so it doesnt seem to be driver-specific (i think?)
- Ive tried one of these cards on Windows, no problems at all. 
- encryption is open for the time being, so no issues there. 

Running out of ideas.. thoughts?

---

### Post by Porcini M. on 2011-09-22
Not sure about the losing IP access part, but for some reason when setting up a media server with Xubuntu (having it connect via wireless card), it lost the ability to resolve hostnames. I had to fix it by installing rsolvconf, to have it automatically set /etc/resolv.conf at each restart.

---

### Post by SparTacux on 2011-09-22
I don't use DHCP these days and prefer static IP's and choosing my own DNS Server settings in Network connections. The good thing about static IP's is that you can keep track of traffic for different computers and know which computer has been accessing what. Also less security risks imo .... I Digress. 

You didn't say if you used a different version of Ubuntu before this latest install or is this the first time? Either way - have a look in your modem/router to see what DNS settings you specified there as a default installation of Ubuntu will be using your modem DNS settings. I could be wrong - I haven't used DHCP in some time. 

You may want to give some more info including ip address given, broadcast address, subnet mask, default route, Primary DNS and Secondary DNS ( As viewed in network connection information )

---

### Post by egregor on 2011-09-22
The 11.4 install is a fresh one as of yesterday... regarding DHCP, i changed things to be static & set the IP/netmask/gateway in networkmanager. This time i used google's DNS ( 8.8.8.8 ) instead of pointing to my router, and it let me connect to websites by name, but it still loses connectivity permanently after a few seconds... so nearly the same problem

---

### Post by varunendra on 2011-09-24
Have you got any kind of firewall setup, or any kind of filters set in the router?

Please post the outputs of
```
cat /etc/network/interfaces
ifconfig
iwconfig
sudo lshw -C network
lsmod
```

For better readability, wrap the outputs in [noparse]```
..and..
```[/noparse] tags as described [here]("http://ubuntuforums.org/misc.php?do=bbcode#code"). You can simply click **# **symbol on the top of edit-box to generate the tags, then paste the output between them.

---

### Post by egregor on 2011-09-25
Eh, I put too many hours in debugging this.. I tried wiping and opensuse and arch installations with both cards, reset my router to factory, attempted building different drivers from source, used all kinds network manager utils.. dunno what happened here but I ended up just cutting up the wiring in my place so i could plug in directly. Thx for the help though.

---

