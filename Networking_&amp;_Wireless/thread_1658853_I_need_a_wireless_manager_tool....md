---
title: "I need a wireless manager tool..."
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by q8_legend on 2011-01-03
Hi
I need a wireless manager tool instead of the default one in ubuntu. I mean a powerful tool that can show me the available wireless networks also with its encryption method and the other details.

Do you recommend a good one ?

Thanks alot ;)

---

### Post by KryptoRoxx on 2011-01-03
WICD....it's easy too. I installed from the synaptic package manager and that was that. Afterwards I removed the network manager and it improved performance and I like it better for the details as well.

---

### Post by PatchesTheCaveman on 2011-01-03
You'll want to uninstall NetworkManager first.  Some people have difficulties when both programs are installed.  You can do so easily from the terminal:
```
sudo apt-get remove network-manager
sudo apt-get update
sudo apt-get install wicd
```

---

### Post by q8_legend on 2011-01-04
Is there is another tool than WICD ?? because unfortunately, i need a tool that can scan for the available networks in a specific area automatically, not every time i move my laptop or another network be available, i have to click the scan button... because this is what is done in the WICD...

I hope i'm clear with my explanation...

Thank you very much guys alot......

---

