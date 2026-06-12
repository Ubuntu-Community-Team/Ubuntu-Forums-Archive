---
title: "Browsing an SD card mounted on the wifi InkJet?"
date: 2013-07-05
forum: Networking &amp; Wireless
---

### Post by Unterseeboot_234 on 2013-07-05
I used to insert an SD card into the printer's SD slot reader and Ubuntu saw the mount as a drive. I think that was direct connect of a USB cable. Any way to do that with wifi? How can I detect the SD card over a wifi network?

---

### Post by tgalati4 on 2013-07-05
What is the model of the printer?  Some printers allow you to access memory card through the built-in webserver:  [http://192.168.1.118/memory_card](http://192.168.1.118/memory_card)  That is an address that works with my HP OfficeJet 7310 with a wired ethernet connection to a wireless router.  Transfer performance is quite slow, so don't get your hopes up.  Some printers only allow SD/memory card transfer through USB only.

The other way to connect is to use the file manager and go to the SAMBA shared address:  file:///run/user/tgalati4/gvfs/smb-share:server=192.168.1.118,share=memory_card/  
Again, the transfer speed is slow.

Substitute *192.168.1.118* for the network address that your printer is set to.

---

### Post by Unterseeboot_234 on 2013-07-05
I want to come back to this SD card question. The immediate problem I have to solve now is I have no Samba shares. I physically moved this Ubuntu computer away from a Windows LAN, then upgraded to 12.04 and now I have to untangle smb.config.

If I can create a shared folder on the network I will then begin to try your suggestions. BTW, I have the HP PhotoSmart 5520. I had no problems accessing the SD card on the Windows LAN (created in Ubuntu on my box). I could insert the SD card on the HP OfficeJet and browse over to it.

---

