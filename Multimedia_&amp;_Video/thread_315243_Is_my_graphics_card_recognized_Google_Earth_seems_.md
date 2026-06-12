---
title: "Is my graphics card recognized? Google Earth seems to say it is not."
date: 2006-12-08
forum: Multimedia &amp; Video
---

### Post by Tominator on 2006-12-08
I am playing with 6.06 on an older IBM P3. I installed Google Earth and it runs very slowly and never resolves properly. When i start that program i am given the following message......
You are currently running Google Earth in "Open GL" with software emulation. In this mode, Google Earth will work but it will run very slowly. If you want to run Google Earth more quickly we suggest that you upgrade your graphics card driver. At Google Earth's help center, I learned that a computer runs in software emulation mode when the graphics card is not detected. My question is twofold, how do I get this card to be recognized, and is there an updated driver I should try to install/ howto?
Here is the result of lspci, thanks in advance, Tom.

lspci
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bri dge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridg e (rev 03)
0000:00:02.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:02.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:02.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:02.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:03.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100]  (rev 05)
0000:00:10.0 Multimedia audio controller: Ensoniq ES1370 [AudioPCI] (rev 01)
0000:01:01.0 VGA compatible controller: S3 Inc. Trio 64 3D (rev 01)

I have done enough research to understand that Trio 64 3D is my card. thanks again, Tom.

---

### Post by Paul41 on 2006-12-08
If you can find the proprietary drivers for you video card it should fix it. I looked on this page [https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto) but didn't see a how to for your card. I also didn't see it here [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards?highlight=%28video%29%7C%28card%29](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards?highlight=%28video%29%7C%28card%29) as a supported card. Hopefully someone else will know of a way you can get the proprietary drivers for you card.

---

### Post by Tominator on 2006-12-08
Thanks Paul, I went to IBM's driver site but I could not automatically update as I no longer have Windows on this machine. At any rate, if anyone can help,  according to IBM the BRAND is 'desktops', the FAMILY IS 'PC 300PL', the TYPE IS 6862, the MODEL is 'V4U'. The system has been upgraded to 256 MB RAM and a 13GB HD. I can't figure out what to download and if I knew that, i would not know how to install it. Thanks again all, Tom.

---

### Post by Zer0Nin3r on 2007-01-04
I"m running an old ATI Rage XL video card, I'm hearing that I will want to stay with the default drivers that came with Linux.  I've checked my xorg.conf and the card is being recognized, but I'm trying to figure out how to utilize the graphics card instead of running Google Earth in software emulation...yadda...yadda...yadda.  Drop a line if anything.

---

