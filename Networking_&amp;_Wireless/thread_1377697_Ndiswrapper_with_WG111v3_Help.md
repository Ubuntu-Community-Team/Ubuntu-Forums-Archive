---
title: "Ndiswrapper with WG111v3 Help"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by Burky on 2010-01-10
I'm am using Ubuntu Karmic Koala (64bit) with a NetGear WG111v3 USB wireless card. This particular wireless card uses the rtl8187b chipset. Out of the box Ubuntu recognises this and proceeds to use the rtl8187 driver with the wireless card. This is a glitchy slow driver. Instead I'd like to use Ndiswrapper.

So, I installed this driver from [here]("http://www.avengergear.com/upload/WG111v3.tar.bz2") by typing the following command into the terminal.
```
sudo ndiswrapper -i WG111/WG111v3.inf

```

This successfully installed; in NdiswrapperGTK it showed it was correctly installed by stating that hardware was present underneath the installed driver.

I then proceeded to blacklist the rtl8187 driver by placing "blacklist rtl8187" in /etc/modprobe.d/blacklist.conf and "ndiswrapper" to /etc/modules.

This did not work, can anyone help me? What am I doing wrong?

---

### Post by Burky on 2010-01-10
If it helps I've got this method to work on Linux Mint 8 32bit.

---

### Post by 73ckn797 on 2010-01-10
There is also a graphical tool to install a wireless driver. Look in System/Administration/Synaptic Package Manager and install "ndisgtk". You can then install the wireless driver for, typically, the Windows XP driver.

---

### Post by Burky on 2010-01-10
> **73ckn797 said:**
> There is also a graphical tool to install a wireless driver. Look in System/Administration/Synaptic Package Manager and install "ndisgtk". You can then install the wireless driver for, typically, the Windows XP driver.

Ah yes, in which it would be titled as "Windows Wireless Drivers" under System? That was what I meant by "NdiswrapperGTK". If I open this it shows "WG111v3" with "Hardware present: yes" underneath it.

---

### Post by 73ckn797 on 2010-01-10
> **Burky said:**
> Ah yes, in which it would be titled as "Windows Wireless Drivers" under System? That was what I meant by "NdiswrapperGTK". If I open this it shows "WG111v3" with "Hardware present: yes" underneath it.


OPPS, I misread the original post. Not used to seeing "ndiswrappergtk". I have had to install a wireless driver using ndisgtk and solved a weak signal issue present with the Ubuntu driver. The wireless card worked fine otherwise for myself.

---

### Post by Burky on 2010-01-10
> **73ckn797 said:**
> OPPS, I misread the original post. Not used to seeing "ndiswrappergtk". I have had to install a wireless driver using ndisgtk and solved a weak signal issue present with the Ubuntu driver. The wireless card worked fine otherwise for myself.

Are you using the WG111v3 USB wireless card?

---

### Post by 73ckn797 on 2010-01-10
> **Burky said:**
> Are you using the WG111v3 USB wireless card?

Not that particular card. 2 Trendnet and one Linksys.

---

### Post by Burky on 2010-01-10
> **73ckn797 said:**
> Not that particular card. 2 Trendnet and one Linksys.

Does it use the rtl8187 chipset?

---

### Post by 73ckn797 on 2010-01-10
> **Burky said:**
> Does it use the rtl8187 chipset?


I will have to check but I believe it does. It is the WMP54G card.

---

### Post by Burky on 2010-01-10
> **73ckn797 said:**
> I will have to check but I believe it does. It is the WMP54G card.

Well if it does you got it to work with Ndiswrapper on 64bit?

---

