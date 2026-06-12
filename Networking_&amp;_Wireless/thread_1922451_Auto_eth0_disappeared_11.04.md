---
title: "Auto eth0 disappeared 11.04"
date: 2012-02-08
forum: Networking &amp; Wireless
---

### Post by ee08 on 2012-02-08
I am running 11.04 for a while now. I can no longer find the Auto eth0 wired connection. Until a couple of days ago my wired connection worked fine, when I plugged in the network cable it detected the network, but now it doesn't. I didn't make any changes to the computer so I am not sure why this happened. My wireless is still working fine. Does anyone have suggestions?
Thanks!
-David

---

### Post by brpylko on 2012-02-08
If you click on your network icon, then on edit connections, is there anything under the wired tab?

If not, go into a terminal and type `ifconfig', 2(3 with wireless) or more interfaces should show up. One is `lo', there should be one called eth0(possibly eth1, eth2, etc)(remember this name)(if there is not one starting with eth, please post the names of the ones that do show up(unless you want to figure out which one to use through trial and error)). Back in the wired tab of edit connections, click Add..., then under `device MAC address', choose the name of your interface that you found out in the previous step. Then under the IPv4 tab, set the method to manual and check `require IPv4 addressing for this connection to complete'. Click save and you should be good to go!

(If there is no ethernet interface or the connection exists in the wired tab, then it is probably a hardware or driver problem)

PS: I am not 100% certain that these will be the location of the buttons/names of menus/etc because I am using 11.10, it should be the same though.

---

### Post by ee08 on 2012-02-08
Under the wired tab I have Wired connection 1 which is a wired connection I made for a different network which needs a static IP.

ifconfig gives me eth0 and lo. Back under the edit tab in the wired connections, when I add another one, if I type in 'eth0' as you suggest to the device MAC address, the save button greys out, so I tried putting int the HWaddr returned from ifconfig for eth0. In the IPv4 tab I set the method to manual, but I need to type in an IP address and I am not sure what I should be typing in.

Next to eth0 it says Link encap:Ethernet and gives the hardware address, but when I look under connection information it lists the active network connections and it says Interface: 802.11WiFi (etho0) and lists the same hardware address as was listed for the ethernet in ifconfig. So I am a bit confused.

thanks again for your help.

---

### Post by ee08 on 2012-02-08
Okay, this is strange. I restarted my computer, flicked my wireless off, plugged in the ethernet cable and then restarted the computer. It now recognizes the wired connection, and under edit connections I have Auto eth0 again, but now when I unplug the wire and turn on the wireless it doesn't start looking for wireless networks. Also, under ifconfig now it gives a different hardware address.

---

### Post by ee08 on 2012-02-08
Well it seems that upon restarting yet again, with the wire unplugged and then plugging in after the wireless network was recognized, it then recognized the wired network. I don't know why it works now and didn't before, but I'll take it until I have problems again...

---

