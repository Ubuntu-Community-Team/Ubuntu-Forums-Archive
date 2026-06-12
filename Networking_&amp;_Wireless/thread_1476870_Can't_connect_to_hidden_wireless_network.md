---
title: "Can't connect to hidden wireless network"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by viniciuscarvalho on 2010-05-08
Hello there! My network has SSID broadcast turned off, it took me several attempts before the crappy ubuntu network manager figured out that I want to connect to that network automatically.

Yesterday my laptop ran out of battery and entered on hibernation. Now, the crappy network manager can not connect to the network anymore. I tried everything. I restarted, I removed the connection from the list. But after asking to connect to the network, and enter the SSID and the WEP key, it simply won't connect.

The worst part is when I tried to load a pre-defined configuration using "Edit Connections", It displays the connection name, but the "Connect" button is disable. WTF??? 

Is there any way to connect to this hidden network? Or it is not supported.

I Love linux, and gnome, but network manager gotta be the worst software ever made for gnome.

---

### Post by Troublegum on 2010-05-08
I once had problems with the network manager after an unsuccessful resume, too. Manual network configuration using the interfaces file worked though. I got rid of the problem by reinstalling the network-manager package via synaptic. You might want to try that

---

