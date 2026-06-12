---
title: "How do I add a vpn?"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by Johnsie on 2009-06-23
When I go into the 'vpn' tab in 'network connections' the  add button is disabled. How do I enable it so that I can add a VPN connection? Do I need to run network connections as sudo? If so how do I do that?

Using a fresh install of jaunty by the way.

---

### Post by hardke01 on 2009-06-23
dependant on the type of vpn you are connecting to. However you will need to install one of the following packages to get the add/import options available in network manager.

sudo apt-get install network-manager-vpnc
sudo apt-get install network-manager-openvpn
sudo apt-get install network-manager-pptp

---

### Post by Johnsie on 2009-06-23
ok, I'll give this a shot. Hopefully in future versions this will work out of the box because VPN access is essential for many IT professionals.

---

### Post by skywriter on 2009-07-07
I have just installed Xubuntu Jaunty. I've got disabled "Add" button in VPN tab of network-manager.

According to recomendation I decided to install network-manager-pptp because i use pptp connection with current provider.

I typed "apt-cache show network-manager". And it said me "network-manager" conflicts to "network-manager-pptp".

How i can enable my "Add" button?

---

### Post by digitalpure on 2009-07-15
I was able to import my VPN settings into the network manager after I installed the openvpn network manager.  How, do I make it connect to the VPN.  

I am using WiTopia services, and they suggest gopenvpn but I am having dependecy issues trying to use that.  Can anyone suggest a way to make the VPN launch, and route. 

The system is a brand new clean install of 9.04 Ubuntu with only the update manager being run and installing the supported updates.  Then installed the openvpn network manager.

---

