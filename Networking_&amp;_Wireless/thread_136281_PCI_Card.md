---
title: "PCI Card"
date: 2006-02-25
forum: Networking &amp; Wireless
---

### Post by swooshvapors13 on 2006-02-25
I put in a PCI card so I could get wireless internet but Linux hasn't recognized it and it doesn't seem to work. The driver CD i got with it was for windows:( It is a trendnet PCI card. Can anyone help me?

---

### Post by ltmon on 2006-02-25
Hi there,

The first step to wireless is to check your card against the following wiki page: [https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)

You might be able to find some good details about your card there.

Some wireless chipsets have Linux native drivers, but many don't.  In this case you need to use "ndiswrapper", which is  a wrapper around windows drivers so you can use them on Linux.  Check out this page for more info: [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto)

After reading those pages and trying those suggestions post back with any questions or problems you may still have.

L.

---

