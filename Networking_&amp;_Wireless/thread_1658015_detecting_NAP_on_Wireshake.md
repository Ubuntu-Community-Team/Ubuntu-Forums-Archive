---
title: "detecting NAP on Wireshake"
date: 2011-01-02
forum: Networking &amp; Wireless
---

### Post by smartmohi on 2011-01-02
I have Windows7 installed Oracle Virtual machine. On VirtualMachine i installed BackTrack4. I'm using datacard (India,Reliance ZTE EVDO3.1mbps) for my internet. I'm able to get internet on my backtrack OS via share using NAT. But when i try to use wireshake to trace my data i'm unable to trace the data send from my windows7 OS. plz help

---

### Post by mail2345 on 2011-01-02
My understanding of the situation:
When you are using wireshark to scan from inside a VM hooked to the network with NAT, you are scanning the VM's virtual network and not the real LAN. This is due to the nature of NATs.
Now to fix it, you need to get wireshark out of the VM's fakenetwork and onto the real network:
Install BackTrack natively, and use wireshark from there. Works the best, and only a small amount of work needed.
Install Wireshark to windows. You might need to fiddle with drivers.
Do some network jiggery to allow wireshark to act like a host on the real LAN. I doubt that Windows can actually do this.

---

