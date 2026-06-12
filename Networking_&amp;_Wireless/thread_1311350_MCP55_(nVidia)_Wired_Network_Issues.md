---
title: "MCP55 (nVidia) Wired Network Issues"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by Sollus on 2009-11-02
Again, as with previous release, I've experienced the same loss of wired connections with 9.10. It's with an ASUS Striker II Extreme motherboard, specifically the nVidia dual ethernet ports. Drivers load, recognizing them as MCP55 nVidia parts but they always fail to connect to the internet. The solution still remains the same - or at the very least works. 

If someone has a better solution or correction to this one, please post it. 

Add the following line to: */etc/modprobe.d/options*

 *options forcedeth msi=0 msix=0*

 Then:
[I]
sudo update-initramfs -u[/I]
 

REBOOT


Please take precautions when using commands and as always, if you're not sure what a command is, use the man pages and google before you execute it.

---

