---
title: "Wireless button not working on Compaq Presario C713NR"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by intiem on 2010-02-27
I installed Ubuntu 9.10 on my laptop (a Compaq Presario C713NR) a while ago to play around with it, and I still can't figure out how to get the wireless to work. The wireless card is Broadcom BCM4311 (rev 02 according to lspci).

I installed the Broadcom b43 drivers, and Hardware Drivers shows that the drivers work but are not in use. The laptop has a button to toggle the wireless. When booting into Windows, the the button turns blue and the wireless works, but it stays off in Ubuntu even if I press the button. I think this might be the problem, but I'm not sure.

Is there a way to get the wireless working?

---

### Post by chili555 on 2010-02-27
Please open Applications-Accessories-Terminal and do:```
rfkill list
iwconfig
```Please post the results. Thanks.

---

### Post by intiem on 2010-02-27
rfkill list doesn't show anything.

iwconfig shows:

```

lo    no wireless extentions.
eth0  no wireless extensions.

```

---

### Post by chili555 on 2010-02-27
Let's take a look at:```
dmesg | grep b43
```Thanks.

Do you have a working ethernet connection?

---

### Post by intiem on 2010-02-27
That doesn't show anything either.

Yes, the internet works fine through an Ethernet connection.

---

### Post by Anhedonia on 2010-02-28
Have you checked the motherboard bios to see if there is a override "set on" option there?

---

### Post by intiem on 2010-02-28
I checked the BIOS, and there was no setting for the wireless at all.

The wireless is working now. I ended up reinstalling Ubuntu and now the drivers are being used.

---

