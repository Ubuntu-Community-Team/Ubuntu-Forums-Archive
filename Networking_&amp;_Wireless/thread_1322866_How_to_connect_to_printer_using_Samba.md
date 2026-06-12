---
title: "How to connect to printer using Samba?"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by iEthan on 2009-11-11
Right now, I'm on a laptop running Ubuntu 9.10, connecting wirelessly to a router. The router is connected to the family computer, which runs WinXP SP3. I want to be able to share a printer (preferably using Samba). How would I go about this?

---

### Post by dmizer on 2009-11-11
Don't use Samba. It's extremely tricky to get a printer share to work through Samba. Use the default CUPS interface to configure your printer, it will work just fine with Windows.

Here's how to configure the Ubuntu print server: [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#Ubuntu%20Print%20Server](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#Ubuntu%20Print%20Server)
Here's how to configure the Windows client: [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#WindowsXP%20Client%20Machine](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#WindowsXP%20Client%20Machine)

More information: [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by iEthan on 2009-11-11
I installed HPLIP (as it is an HP Photosmart C6200), and it connects fine. But when I print, it says it prints successfully, but in reality, it doesn't.

---

### Post by dmizer on 2009-11-11
> **iEthan said:**
> I installed HPLIP (as it is an HP Photosmart C6200), and it connects fine. But when I print, it says it prints successfully, but in reality, it doesn't.

What line did you enter in the network printer blank on the Windows machine?

---

