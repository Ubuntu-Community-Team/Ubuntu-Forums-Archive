---
title: "nm-applet wont show up mobile broadband"
date: 2009-04-22
forum: Networking &amp; Wireless
---

### Post by pytrisss on 2009-04-22
Hi folks,
I have installed 9.04 RC and set up a mobile broadband connection in nm-connection-editor. I just edited the automatic connection system created and I was able to see it in nm-applet and connect with it.
Suddenly like two days ago I rebooted and from then I cant see the broadband connection on nm-applet.
It is still in connection editor, but whatever I do or change wont show it up in the applet. I even tried to create a new one.
Restarting network manager and killing and starting nm-applet doesnt help either.

I get the usual when I try to plug the device in:
Apr 22 10:54:39 kuba-laptop kernel: [12255.392097] usb 8-1: new full speed USB device using ohci_hcd and address 2
Apr 22 10:54:39 kuba-laptop kernel: [12255.609117] usb 8-1: configuration #1 chosen from 1 choice
Apr 22 10:54:39 kuba-laptop kernel: [12255.629164] usb-storage: probe of 8-1:1.0 failed with error -5
Apr 22 10:54:39 kuba-laptop kernel: [12255.629191] option 8-1:1.0: GSM modem (1-port) converter detected
Apr 22 10:54:39 kuba-laptop kernel: [12255.629363] usb 8-1: GSM modem (1-port) converter now attached to ttyUSB0

apart from usb-storage probes which I dont think make any problems because its not a mass storage device.
Its a huawei EC500 card and I am able to connect through pppd or gnome-ppp.

Any help would be appreciated.

---

### Post by pytrisss on 2009-04-23
bump

---

### Post by JK3mp on 2009-05-02
I have the same issue only with my Fedora 10 install. For some reason i can make the connection in the manager and it doesn' show up in options when i hover over the nm icon.

---

### Post by pytrisss on 2009-05-02
> **JK3mp said:**
> I have the same issue only with my Fedora 10 install. For some reason i can make the connection in the manager and it doesn' show up in options when i hover over the nm icon.

what version of NM are you using?

---

### Post by akbardotinfo on 2009-06-29
Have you make sure the NetworkManager is start ?
> sudo /etc/init.d/NetworkManager start

---

### Post by pytrisss on 2009-06-30
> **akbardotinfo said:**
> Have you make sure the NetworkManager is start ?

well, of course :) I can connect to wifi or eth with no trouble whatsoever.
I just cant select mobile broadband because I dont have it in the applet :(

Maybe I will just settle in with a reinstall...

---

