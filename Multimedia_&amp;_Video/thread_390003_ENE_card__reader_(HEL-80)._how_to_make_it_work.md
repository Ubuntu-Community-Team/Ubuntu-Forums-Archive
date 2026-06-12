---
title: "ENE card  reader (HEL-80). how to make it work"
date: 2007-03-21
forum: Multimedia &amp; Video
---

### Post by band-aid on 2007-03-21
My Compal HEL-80 has a built in 3 in 1 card reader. By searching around on the manufacturers web site I was able to find out that it is a 

```

Built-in memory card reader: Secure Digital (SD/MMC) & MemoryStick/MemoryStick Pro (ENE PCI controller)

```

Apparently it is recognized by lspci giving the following output (grep'd)

```

lspci | grep ENE

06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)



```

How would I go about fixing this?

---

### Post by HarshReality on 2007-06-25
Long answer... you dont. This is the one thing holding me from doing an out and out conversion on my laptop.

---

