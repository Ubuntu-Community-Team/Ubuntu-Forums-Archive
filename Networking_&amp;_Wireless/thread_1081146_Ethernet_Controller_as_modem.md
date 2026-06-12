---
title: "Ethernet Controller as modem?"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by amkr on 2009-02-26
Can I use PCI Express Fast Ethernet Controller as a dial-up modem? I have a Toshiba L300 (see config [here]("http://www.thietbidaucuoi.com/shop.html?page=shop.product_details&flypage=flypage.tpl&product_id=72&category_id=23") )
How can I set up a dial-up broadband connection?

---

### Post by ModelM on 2009-02-26
If you are meaning connecting the telephone line to the ethernet card, no that won't work.

A dialup modem has circuitry, called the Data Access Arrangement  (DAA), which allows connecting directly to the telephone line. It presents the proper impedance to the telephone line (and the central office), can withstand the ringer voltage (usually around 90 volts), and other specialized tasks. This circuitry is not present in an ethernet adapter, which is designed for connection to a very different type of circuit.

---

