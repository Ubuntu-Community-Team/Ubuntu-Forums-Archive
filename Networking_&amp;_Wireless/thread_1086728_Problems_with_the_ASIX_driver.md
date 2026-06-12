---
title: "Problems with the ASIX driver"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by mindless1973 on 2009-03-04
Hi,

I try to get my Netgear FA-120 working. It seems that there is a problem with my ASIX driver:

dmesg:
> 
[ 2208.012463] asix: disagrees about version of symbol usbnet_set_msglevel
[ 2208.012471] asix: Unknown symbol usbnet_set_msglevel
[ 2208.012658] asix: disagrees about version of symbol usbnet_unlink_rx_urbs
[ 2208.012660] asix: Unknown symbol usbnet_unlink_rx_urbs
[ 2208.012720] asix: disagrees about version of symbol usbnet_get_msglevel
[ 2208.012721] asix: Unknown symbol usbnet_get_msglevel
[ 2208.012817] asix: disagrees about version of symbol usbnet_skb_return
[ 2208.012818] asix: Unknown symbol usbnet_skb_return
[ 2208.012945] asix: disagrees about version of symbol usbnet_get_settings
[ 2208.012947] asix: Unknown symbol usbnet_get_settings
[ 2208.013003] asix: disagrees about version of symbol usbnet_suspend
[ 2208.013005] asix: Unknown symbol usbnet_suspend
[ 2208.013059] asix: disagrees about version of symbol usbnet_get_drvinfo
[ 2208.013060] asix: Unknown symbol usbnet_get_drvinfo
[ 2208.013159] asix: disagrees about version of symbol usbnet_get_endpoints
[ 2208.013161] asix: Unknown symbol usbnet_get_endpoints
[ 2208.013286] asix: disagrees about version of symbol usbnet_nway_reset
[ 2208.013288] asix: Unknown symbol usbnet_nway_reset
[ 2208.013349] asix: disagrees about version of symbol usbnet_defer_kevent
[ 2208.013351] asix: Unknown symbol usbnet_defer_kevent
[ 2208.013447] asix: disagrees about version of symbol usbnet_disconnect
[ 2208.013448] asix: Unknown symbol usbnet_disconnect
[ 2208.013505] asix: disagrees about version of symbol usbnet_set_settings
[ 2208.013507] asix: Unknown symbol usbnet_set_settings
[ 2208.013546] asix: disagrees about version of symbol usbnet_probe
[ 2208.013547] asix: Unknown symbol usbnet_probe
[ 2208.013585] asix: disagrees about version of symbol usbnet_resume
[ 2208.013587] asix: Unknown symbol usbnet_resume


I remeber that it used to work on an older Ubuntu (Gutsy) for some time. Any ideas what is going wrong and how I can correct it?

Thanks,

bye
me.

---

