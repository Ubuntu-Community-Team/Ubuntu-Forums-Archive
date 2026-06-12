---
title: "Need to revert back to default drivers"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by Burnz316 on 2008-12-15
Hey...

Installed Ubuntu with no problems and my wireless card was detected and it connected to the net right away. My only problem was that the net was abit slow compared to Vista, so I ran ndiswrapper and installed the correct drivers for the network card.

Now my problem is that it won't connect to the wireless network at all. I would like to revert my wireless card drivers back to the default ones that were used when I first installed Ubuntu, anyone know how I would do that?

Thanks.

---

### Post by Ayuthia on 2008-12-15
Do you know what your previous driver was?  If not, can you post the results of:
```
lspci -nn
ndiswrapper -l
```

---

### Post by Burnz316 on 2008-12-15
no idea what the driver was..


lspci -nn

04:05.0 Network Controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev01)

(guessing you only needed that part about the network card)


ndiswrapper -1

I don't currently have the windows driver installed since I've been trying to get it to use a default one, so nothing showed up.

---

### Post by Ayuthia on 2008-12-16
You might try:
```
sudo mopdrobe -r ndiswrapper rt2500pci
sudo modprobe rt2500pci
sudo /etc/init.d/networking restart
```

---

### Post by Burnz316 on 2008-12-16
yay it worked.. thanks alot for your help!

---

### Post by Burnz316 on 2008-12-17
only problem is now I have to type this in every time i restart to computer.

> sudo modprobe rt2500pci

---

### Post by Ayuthia on 2008-12-18
> **Burnz316 said:**
> only problem is now I have to type this in every time i restart to computer.

Just add the following:
```
echo rt2500pci | sudo tee -a /etc/modules
```
and that should get it to load automatically when you boot.

---

