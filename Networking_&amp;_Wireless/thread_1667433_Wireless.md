---
title: "Wireless"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by shibby4555 on 2011-01-14
Hey,
So I'm having an issue recently with Ubuntu 10.04 x64

Connecting to my wifi is not working. I believe it is some kind of issue with the router. On Windows 7 the only way that I could connect to the net was by copying the network profile to a usb flashdrive from another computer and loading it mine.

The wireless signal just keeps attempting to connect.

Any ideas? Thanks
-shibby

---

### Post by quixote on 2011-01-15
I think we need a bit more data before it'll be possible to find a solution.  What kind of router do you have?  What kind of encryption are you using? (WEP? WPA-PSK? etc) 

Can you print out the network profile from the flash drive?  If it's not too long, just include it in your answer, otherwise attach it.  Also, open a terminal (Applications > Accessories > Terminal), and type: ```
ifconfig
``` and ```
iwlist scan
```You can use the mouse to select the output, and then hit Ctrl-Shift-C to copy to a text editor.  Include that output with your answer too.

What happens if you turn all security off?  Can you connect then?

---

