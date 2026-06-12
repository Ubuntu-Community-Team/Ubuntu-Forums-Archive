---
title: "[SOLVED] Realtek 8187b ubuntu 8.10"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by balloooza on 2008-12-06
I apologize for starting a new thread, but I don't think the others are easy to read. I have been using a realtek 8187b wireless card on my toshiba laptop for a while. It has allways been very temperamental, I have tried ndiswrapper(with good success on 7.10 but not so much on 8.04) I jnow what I am doing with the ndiswrapper stuff, but I am still a little unsure about what it accualy dose.
My problem is very wierd, I had a messed up partition table, and the only way to get more space was to reinstall, so (2 hours ago, using my wireless network via the ubuntu 8.10 rt8187b driver (not ndiswrapper) backed up my computer) I did a clean install of ubuntu 8.10.  When I used 8.04, I used ndiswrapper and 2 hours ago I used the "ubuntu" supplied version with 8.10. now neither of them work. 

simply, reguardless of the crazy day I have had I am left tied to the wall on ethernet, and the once working ndiswrapper driver will pick up a network, but not finish the connect. I would prefer to use the "ubuntu driver" that I was USING COMPLEATLY SUCESSFULLY 2 hours ago, because it works with a suspend, and with ndiswrapper I have to reinstall the driver every time I wake from sleep

(this is how I do it)
```
#!/bin/bash
# Restart network...

ndiswrapper -e net8187b
if [ $? -ne 0 ]; then
    echo "ndiswrapper failed!" 1>&2
    exit 1
fi

sleep 3

ndiswrapper -i ~/RTL8187B/Win98/net8187b.inf
```
but it worked better with the ubuntu driver

I would also like to know what package the ubuntu wireless driver is in.

---

### Post by balloooza on 2008-12-10
I solved this myself by unloading the ndiswrapper driver

```
sudo modprobe -r ndiswrapper
```

then I loaded the rtl8187b driver

```
sudo modprobe rtl8187
```

---

