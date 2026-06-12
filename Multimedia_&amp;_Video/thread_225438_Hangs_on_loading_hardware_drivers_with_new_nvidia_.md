---
title: "Hangs on loading hardware drivers with new nvidia card"
date: 2006-07-29
forum: Multimedia &amp; Video
---

### Post by Duo Maxwell on 2006-07-29
Ok, this is killing me, got my cousin to try ubuntu on her emachine t2895 and all was well, till we decided to try it with a better then intergrated videocard, I found this [http://72.14.203.104/search?q=cache:jnV6skW-TxYJ:www.newegg.com/Product/Product.asp%3FItem%3DN82E16814143058+3d+Fuzion+6200+pci+128Mb&hl=en&gl=us&ct=clnk&cd=1](http://72.14.203.104/search?q=cache:jnV6skW-TxYJ:www.newegg.com/Product/Product.asp%3FItem%3DN82E16814143058+3d+Fuzion+6200+pci+128Mb&hl=en&gl=us&ct=clnk&cd=1)
 on a decent deal, or so I thought... Having used the AGP version 6200( EVGA 256a8n341dx) in my old P4 runnind Breezy I figured all would be fine and good. I got 6.06 installe, picasa, automatix, and now that we got the card used automatix as I had on my comp to install the nvidia drivers. followed the instructions, restarted, went into the bios, disabled the intergrated graphics and plugged the monitor into the vga port on the new graphics card. The machine loads normally 
up to the point where it it says loading hardware drivers and hangs.

So I try grabbing my copy of Kororaa 0.2 and trying that, hangs too, try it again, using verbose mode the 2nd time around and get this after the line saying kernal panic:

```
Oops : 0003 [#24]
PREEMPT SMP
Modules linked in: intel_agp agpgart i2c_i801 i1c_core dm_mirror sbp2 ohcieee1394 sl811_hcd ohci_hcd uhci_hcd usb_storage usbhid echi_hcd usbcore
CPU: 0
EIP: 0060: [<b011b370>] Not tainted VLI
EFLAGS: 00010006 (2.6.16-archck1 #4)
EPI is at clear_local_APIC+0x20/0xe0

```

least I think I got it all down right...


Yeah, I have a screenshot of the thing atomatix told my to put in if it failed, can't use it tho... [http://img60.imageshack.us/img60/4169/screenshotgd3.png](http://img60.imageshack.us/img60/4169/screenshotgd3.png)

---

