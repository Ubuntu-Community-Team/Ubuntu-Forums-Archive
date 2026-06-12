---
title: "Problem with lirc and Creative SB-0540 receiver"
date: 2010-02-15
forum: Multimedia Software
---

### Post by el_Paraguayo on 2010-02-15
I've got Mythbuntu 8.04 up an running on an old Dell Dimension desktop but I'm having trouble getting lirc to work.
 
During the install I selected the Creative SB-0540 usb option but I can't seem to get any response from it.
 
I tried running "irw" but I get no response (tried a whole load of remotes!).
 
The SB-0540 is showing up as /dev/usb/hiddev0.
 
One thought I had, my TV tuner is a Hauppauge Nova-T PCI (it's like [this one]("http://www.hauppauge.co.uk/site/products/data_novatpci.html") except mine has aerial in and and out sockets). This has a socket for an IR receiver so I'm wondering if this is interfering.
 
If I do lsmod I see "ir_common" and, as far as I understand, this isn't part of lirc.
 
Can anyone help get my Creative receiver working?
 
Thanks.
 
el_P

---

