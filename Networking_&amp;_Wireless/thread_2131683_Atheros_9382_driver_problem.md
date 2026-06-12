---
title: "Atheros 9382 driver problem"
date: 2013-04-02
forum: Networking &amp; Wireless
---

### Post by tio289 on 2013-04-02
Hello, I bought half mini pcie card Atheros 9382. Problem is with Vendor ID. Card reports this one

```


Ethernet controller [0200]: Atheros Communications Inc. Device [168c:abcd] (rev 01)
```

I found this mailing list [http://www.mail-archive.com/ath9k-devel@lists.ath9k.org/msg05526.html](http://www.mail-archive.com/ath9k-devel@lists.ath9k.org/msg05526.html) and try to compile own compat-wireless with small edit in [COLOR=#000000][FONT=courier]drivers/net/wireless/ath/ath9k/pci.c file.

I add new line with abcd vendor id

[/FONT][/COLOR]```

        { PCI_VDEVICE(ATHEROS, 0x0030) }, /* PCI-E  AR9300 */
+       { PCI_VDEVICE(ATHEROS, 0xabcd) }, /* PCI-E  AR9300 */

```

After restart lspci -nv reports that card use Kernel module: ath9k, but dont use any driver.I think, that by adding new vendor id to pci.c file is not enough, because program doesn't know, what a card model. So I have to edit something other file to specify that vendor id abcd have to use ar9003 driver.Can somebody help me? Thnaks

---

### Post by wildmanne39 on 2013-04-02
Please post the output of:
```
lspci -nnk | grep -iA2 net
```
fun fun fun
Thanks

---

### Post by wildmanne39 on 2013-04-02
What ubuntu version are you using?
I recommend trying 12.04 or 12.10 from a live cd or usb and running the command I posted plus:
```
modinfo ath9k
```
to see if it is in loaded by defaut in the latest version of ubuntu.
It looks like that may not be the real pci id.
Thanks

---

