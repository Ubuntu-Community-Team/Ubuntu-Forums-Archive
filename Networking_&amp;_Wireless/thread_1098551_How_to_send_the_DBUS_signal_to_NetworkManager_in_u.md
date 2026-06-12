---
title: "How to send the DBUS signal to NetworkManager in user space?"
date: 2009-03-17
forum: Networking &amp; Wireless
---

### Post by huananhu on 2009-03-17
Dear All:
 
   I have a data card, and it can support the usb ether feature.
 
   But there are some problems to use in the linux systems:
 
   1. While I plug the data card into the linux, and after the cdc_ether.ko driver is attached to the device, the NetworkManager will be activated to add our device in its list, and detach the IP of our device.
    In this case, which signal or method_call will be received by the NetworkManager from DBUS or HAL?
 
   2. While I dial-up the data card to connect to the Ethernet, the NetworkManager will not be activated to refresh the information, such as IP, for our data card in the linux system.
     I want to send some signal or method_call to NetworkManager by DBUS to activate it in the user space.
     Which signal or method_call can I send ? How to send them?
 
   Hope for your help as soon as possible, thanks very much.

---

