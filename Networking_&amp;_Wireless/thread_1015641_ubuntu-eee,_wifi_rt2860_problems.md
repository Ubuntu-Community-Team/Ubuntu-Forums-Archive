---
title: "ubuntu-eee, wifi rt2860 problems"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by agatek on 2008-12-19
Hi,

I asked this question on ubuntu-eee forum but no response so far - perhaps no critical mass. If there are any information missing please tell me that it should be included. I am not pasting here logs/configs etc because I do not see anything suspicious over there or I am not that sure what may be relevant. 

It looks like I am slowly running out of new ideas how to make the wifi connection working on my asus eeepc901. Perhaps you can help me because I am clearly missing something. I will start with some symptoms/basic info that I think may be important:
[LIST]
[*]it worked very well right after installing the distribution (ubuntu-eee 8.04). Most likely stopped after an update.
[*]it does not work neither with ndiswrapper nor the native driver - the behaviour is quite similar: 
- with the native driver (I tried 1.7.0 and 1.8.0 versions) (iwconfig) shows that it is associated with the right AP (WPA2PSK/TKIP) but shows no essid and other data (encryption off, etc)
- with the ndiswrapper shows it is connected to AP and the essid is set. Sometimes it shows the encryption key.
[*]it shows continuous TX/RX activity so packets are transmitted and received. 
[*]iwconfig does not set essid, encryption etc from the command line.
[*]if I deliberately specify wrong wifi connection data and there is no AP associated there is no TX/RX traffic present.
[*]static or dhcp, does not matter
[*]the network via other interfaces (ethernet, modem) works with no problems.
 [/list]
By network not working I mean I can not even get ping/other response from the gateway.

I found the fact that I can not change essid and other parameters quite weird but I also found some posts saying it is quite normal. 

Any suggestions will be greatly appreciated 

Marcin

---

### Post by henriquemaia on 2008-12-19
Same problem here. Just giving a bump to bring the discussion on.

---

### Post by agatek on 2008-12-19
> **henriquemaia said:**
> Same problem here. Just giving a bump to bring the discussion on.

Mine is solved... For some reason the firewall blocks the in and out for the interface.
The main difficulty with all the current nicely looking linux distributions is that the philosophy behind is to think for the user. The problem is that often it thinks wrong and than you spend hours figuring out what is going on and finding the solution in the least expected places. On Fedora 9 I had to kill the Network manager in order to get the wifi working...
 
Try from command line and see whether this helps: 

```
sudo iptable -F
```

Marcin

---

### Post by Kobalt on 2008-12-19
Watch for your /etc/interfaces/network file, if it's edited then it can conflict with Network Manager. Somehow in your testing you must have entered values in here. For Network Manager to work correctly in roaming mode it needs a "clean" /etc/interfaces/network, containing only the "lo" interface section.

---

### Post by agatek on 2008-12-19
I said "solved" but unfortunately NOT. I can get the network working only with some command's specific order...
First I have to go to the Network Manager (NM) icon, click on "manual", change anything to the interface so NM reloads everything, then from command line I have to do ifdown wlan0; ifup wlan0; iptables -F and then edit resolv.conf and only then vuala, everything works fine...

> **Kobalt said:**
> Watch for your /etc/interfaces/network file, if it's edited then it can conflict with Network Manager. Somehow in your testing you must have entered values in here. For Network Manager to work correctly in roaming mode it needs a "clean" /etc/interfaces/network, containing only the "lo" interface section.

I am not using the roaming mode for this interface:
```
iface wlan0 inet static
address 192.168.52.102
netmask 255.255.255.0
gateway 192.168.52.254
wireless_mode managed
wpa-pairwise CCMP TKIP
wpa-group TKIP
wpa-ap-scan 2
wpa-psk <xxxx>
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid agatek-wlan

auto wlan0
```

..and this could be very well a problem with NM but what I also tried before was to kill NM and its dispatcher and do the down, up and flushing the tables with no success as per the network condition.  

Well, at least now I have a starting point... 

Marcin

---

### Post by agatek on 2008-12-19
Again I rushed without thoroughly verifying or it was just some kind of coincident. Sorry for chaotic posting. It looks like this is a combination of the Network Manager and the firewall.

For my network and the earlier given interface config I can make the network working the following way:

```
killall NetworkManager NetworkManagerDispatcher
ifdown wlan0
ifup wlan0
iptable -F
```

Could somebody please give me a hint where in ubuntu the iptables-save resulting file is typically stored?

Marcin

---

### Post by henriquemaia on 2008-12-19
In my case is more weird. I've installed xubuntu. No network. Then I grabbed a package I saw on another forum and installed it. No luck. I had ethernet at that time. So I plugged the router in and I installed the array.org packages. No luck still. Then I uninstalled the said package I had previously installed. That did the trick and finally my eee was finally wified. But then I restarted and the wifi was down again. Can't understand why.

---

### Post by griffjon on 2010-08-23
I found installing the backport of the wifi drivers from here: [http://packages.ubuntu.com/lucid/i386/linux-backports-modules-wireless-2.6.32-24-generic/download](http://packages.ubuntu.com/lucid/i386/linux-backports-modules-wireless-2.6.32-24-generic/download)
  helped me regain connectivity after an update.

---

### Post by myth-eeebox-ben on 2010-09-25
ufw (ubuntu fire-wall) is getting in the way.  Disable it with

```
sudo ufw disable
```and I can now set essid.  Don't know if this is a complete fix yet.

(I also clicked disable networking in the NetManager Applet in the GUI)

I'm trying to sort this out to bridge my eth0 <--> wlan0

[http://newyork.ubuntuforums.org/showthread.php?p=9889729#post9889729](http://newyork.ubuntuforums.org/showthread.php?p=9889729#post9889729)



EDIT
after a reboot it was not letting me change essid, but this worked once.

I have replicated this fix once, but did so many things including 

ifconfig wlan0 stop/start
kill NetworkManager
ufw disable
Connect wlan0 in GUI

Please can somebody who knows more than me answer this one with a bit more clarity?

---

