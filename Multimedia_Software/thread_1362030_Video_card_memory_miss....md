---
title: "Video card memory miss..."
date: 2009-12-22
forum: Multimedia Software
---

### Post by billdoors on 2009-12-22
I have a ATI radeon hd 2400 pro. From the website of the manufacturer, it has 256M memory. But Catalyst Control Center told me only 128M exists. Anyone know what happened? How can I find the lost memory?

Config:
Ubuntu 9.10

---

### Post by Qola on 2009-12-22
[s]Is it agp or pci-e?[/s]

Scratch that. What driver version are you using?

---

### Post by billdoors on 2009-12-22
[B] 	Version

[/B] 
	      	9.12  	



> **Qola said:**
> [s]Is it agp or pci-e?[/s]

Scratch that. What driver version are you using?

---

### Post by Qola on 2009-12-22
Ok, well a quick google search shows that 128 meg 2400s do exist. Are you certain that your card has 256 meg?

---

### Post by billdoors on 2009-12-22
it is Ati radeon hd 2400 [COLOR=Red]**Pro**[/COLOR], only 256 M. Thanks

> **Qola said:**
> Ok, well a quick google search shows that 128 meg 2400s do exist. Are you certain that your card has 256 meg?

---

### Post by Qola on 2009-12-22
[http://www.google.co.uk/products/catalog?hl=en&source=hp&q=ati+radeon+2400+pro+128mb&um=1&ie=UTF-8&cid=7802401313205285998&ei=MUcxS7SIApGl4QaU_eGqCA&sa=X&oi=product_catalog_result&ct=result&resnum=3&ved=0CBEQ8wIwAg#ps-sellers](http://www.google.co.uk/products/catalog?hl=en&source=hp&q=ati+radeon+2400+pro+128mb&um=1&ie=UTF-8&cid=7802401313205285998&ei=MUcxS7SIApGl4QaU_eGqCA&sa=X&oi=product_catalog_result&ct=result&resnum=3&ved=0CBEQ8wIwAg#ps-sellers)

Are you absolutely certain that your card has 266 meg memory?

---

### Post by billdoors on 2009-12-22
this is the results when I run command:
$ lspci -v | less

02:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]
        Subsystem: Dell Device 0302
        Flags: bus master, fast devsel, latency 0, IRQ 27
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at fdcf0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at bc00 [size=256]
        Expansion ROM at fdcc0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: fglrx_pci
        Kernel modules: fglrx, radeon


> **billdoors said:**
> it is Ati radeon hd 2400 [COLOR=Red]**Pro**[/COLOR], only 256 M. Thanks

---

### Post by billdoors on 2009-12-22
after running: 
$ lspci -v | less

I see:
02:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]
        Subsystem: Dell Device 0302
        Flags: bus master, fast devsel, latency 0, IRQ 27
        Memory at e0000000 (64-bit, prefetchable) **[size=256M]**
        Memory at fdcf0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at bc00 [size=256]
        Expansion ROM at fdcc0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: fglrx_pci
        Kernel modules: fglrx, radeon

so I think it is 256M


> **Qola said:**
> [http://www.google.co.uk/products/catalog?hl=en&source=hp&q=ati+radeon+2400+pro+128mb&um=1&ie=UTF-8&cid=7802401313205285998&ei=MUcxS7SIApGl4QaU_eGqCA&sa=X&oi=product_catalog_result&ct=result&resnum=3&ved=0CBEQ8wIwAg#ps-sellers](http://www.google.co.uk/products/catalog?hl=en&source=hp&q=ati+radeon+2400+pro+128mb&um=1&ie=UTF-8&cid=7802401313205285998&ei=MUcxS7SIApGl4QaU_eGqCA&sa=X&oi=product_catalog_result&ct=result&resnum=3&ved=0CBEQ8wIwAg#ps-sellers)

Are you absolutely certain that your card has 266 meg memory?

---

### Post by Qola on 2009-12-22
That is pretty strange. Does your motherboard have an integrated chip by any chance?

---

