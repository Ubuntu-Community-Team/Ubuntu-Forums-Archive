---
title: "suspend fails with usb wireless adapter"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by DiutisiH on 2009-02-08
I can't hibernate or suspend successfully if my USB wireless adapter is plugged in (netcomm np545).  the machine (an old dell inspiron 7500 laptop) appears to suspend succecssfully but it won't start up again unless I cycle power.

I've read/seen many suspend/hibernate issues but none so far that match my symptoms.

I'm an absolute newbie to linux (and this forum) any advice would be greatly appreciated (including being told that I posted in the wrong place...)

-thanks

btw - suspend and hibernate both work for me when connected via ethernet

---

### Post by DiutisiH on 2009-02-11
in case anyone has the same problem...  I found a solution at [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu) bug# 95144

this is the fix...

create /etc/pm/config.d/usb_suspend_workaround with the contents:
SUSPEND_MODULES="ehci_hcd uhci_hcd usbcore"

suspend and hibernate both work for me now.  on one resume I had to manually re-enable networking and I've seen some error messages as it goes down ( Error - Vendor Request 0x0a failed for offset ...) but all-in-all it seems a reasonable fix...

---

