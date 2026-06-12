---
title: "Mobile Broadband with Huawei E620 on KPN Mobile"
date: 2009-02-27
forum: Networking &amp; Wireless
---

### Post by sanderj on 2009-02-27
Hi,

I've got a Huawei E620 with KPN Mobile SIM Card. I don't know how to get Internet working. Tips welcome. It might be as simple (and stupid) as "click on icon/program x to start the connection"

Situaton: 
When I plug the PCMCIA card, there are a lot of /var/log/messages (see below). 

When I click Network Connections -> Mobile Broadband shows "KPN Mobile", which is correct. Looking in the KPN Mobile info, there are a lot of settings already filled out.
The green LED on the Huawei is blinking slowly. There is no IP address assigned. There is no ifconfig interface for the Huawei card.

Do I need to start a program to get a connection?


FWIW: 
To be complete I've also included the messages during removal.
I'm running Linux Mint 6, which has the same internals as Ubuntu 8.10. If needed, I can live-boot Ubuntu 8.10

```

Feb 27 20:07:19 linuxmint6 kernel: [  140.392080] pccard: CardBus card inserted into slot 0
Feb 27 20:07:19 linuxmint6 kernel: [  140.392274] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot
Feb 27 20:07:19 linuxmint6 kernel: [  140.392285] pci 0000:09:00.0: PME# disabled
Feb 27 20:07:19 linuxmint6 kernel: [  140.392459] pci 0000:09:00.1: PME# supported from D0 D1 D2 D3hot
Feb 27 20:07:19 linuxmint6 kernel: [  140.392469] pci 0000:09:00.1: PME# disabled
Feb 27 20:07:19 linuxmint6 kernel: [  140.532890] ohci_hcd 0000:09:00.0: enabling device (0000 -> 0002)
Feb 27 20:07:19 linuxmint6 kernel: [  140.532905] ohci_hcd 0000:09:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 27 20:07:19 linuxmint6 kernel: [  140.532933] ohci_hcd 0000:09:00.0: OHCI Host Controller
Feb 27 20:07:19 linuxmint6 kernel: [  140.533775] ohci_hcd 0000:09:00.0: new USB bus registered, assigned bus number 6
Feb 27 20:07:19 linuxmint6 kernel: [  140.535068] ohci_hcd 0000:09:00.0: irq 16, io mem 0x5c000000
Feb 27 20:07:19 linuxmint6 kernel: [  140.618172] usb usb6: configuration #1 chosen from 1 choice
Feb 27 20:07:19 linuxmint6 kernel: [  140.618685] hub 6-0:1.0: USB hub found
Feb 27 20:07:19 linuxmint6 kernel: [  140.618970] hub 6-0:1.0: 1 port detected
Feb 27 20:07:19 linuxmint6 kernel: [  140.721403] ohci_hcd 0000:09:00.1: enabling device (0000 -> 0002)
Feb 27 20:07:19 linuxmint6 kernel: [  140.721424] ohci_hcd 0000:09:00.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Feb 27 20:07:19 linuxmint6 kernel: [  140.721468] ohci_hcd 0000:09:00.1: OHCI Host Controller
Feb 27 20:07:19 linuxmint6 kernel: [  140.722750] ohci_hcd 0000:09:00.1: new USB bus registered, assigned bus number 7
Feb 27 20:07:19 linuxmint6 kernel: [  140.723163] ohci_hcd 0000:09:00.1: irq 16, io mem 0x5c001000
Feb 27 20:07:19 linuxmint6 kernel: [  140.806084] usb usb7: configuration #1 chosen from 1 choice
Feb 27 20:07:19 linuxmint6 kernel: [  140.806690] hub 7-0:1.0: USB hub found
Feb 27 20:07:19 linuxmint6 kernel: [  140.806907] hub 7-0:1.0: 1 port detected
Feb 27 20:07:22 linuxmint6 kernel: [  143.500087] usb 6-1: new full speed USB device using ohci_hcd and address 2
Feb 27 20:07:22 linuxmint6 kernel: [  143.715445] usb 6-1: configuration #1 chosen from 1 choice
Feb 27 20:07:22 linuxmint6 kernel: [  143.900669] usbcore: registered new interface driver usbserial
Feb 27 20:07:22 linuxmint6 kernel: [  143.900694] usbserial: USB Serial support registered for generic
Feb 27 20:07:22 linuxmint6 kernel: [  143.900743] usbcore: registered new interface driver usbserial_generic
Feb 27 20:07:22 linuxmint6 kernel: [  143.900746] usbserial: USB Serial Driver core
Feb 27 20:07:22 linuxmint6 kernel: [  143.914038] usbserial: USB Serial support registered for GSM modem (1-port)
Feb 27 20:07:22 linuxmint6 kernel: [  143.914079] option 6-1:1.0: GSM modem (1-port) converter detected
Feb 27 20:07:22 linuxmint6 kernel: [  143.914309] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB0
Feb 27 20:07:22 linuxmint6 kernel: [  143.914327] option 6-1:1.1: GSM modem (1-port) converter detected
Feb 27 20:07:22 linuxmint6 kernel: [  143.914417] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB1
Feb 27 20:07:22 linuxmint6 kernel: [  143.914434] option 6-1:1.2: GSM modem (1-port) converter detected
Feb 27 20:07:22 linuxmint6 kernel: [  143.914523] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB2
Feb 27 20:07:22 linuxmint6 kernel: [  143.914545] usbcore: registered new interface driver option
Feb 27 20:07:22 linuxmint6 kernel: [  143.914552] option: USB Driver for GSM modems: v0.7.2
Feb 27 20:07:22 linuxmint6 kernel: [  143.946039] usbcore: registered new interface driver libusual

```


```

Feb 27 20:08:20 linuxmint6 kernel: [  201.718625] pccard: card ejected from slot 0
Feb 27 20:08:20 linuxmint6 kernel: [  201.718636] usb 6-1: USB disconnect, address 2
Feb 27 20:08:20 linuxmint6 kernel: [  201.722451] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Feb 27 20:08:20 linuxmint6 kernel: [  201.722486] option 6-1:1.0: device disconnected
Feb 27 20:08:20 linuxmint6 kernel: [  201.723129] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Feb 27 20:08:20 linuxmint6 kernel: [  201.723154] option 6-1:1.1: device disconnected
Feb 27 20:08:20 linuxmint6 kernel: [  201.723791] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Feb 27 20:08:20 linuxmint6 kernel: [  201.723817] option 6-1:1.2: device disconnected
Feb 27 20:08:20 linuxmint6 kernel: [  201.752581] ohci_hcd 0000:09:00.0: remove, state 0
Feb 27 20:08:20 linuxmint6 kernel: [  201.752606] usb usb6: USB disconnect, address 1
Feb 27 20:08:20 linuxmint6 kernel: [  201.753341] ohci_hcd 0000:09:00.0: USB bus 6 deregistered
Feb 27 20:08:20 linuxmint6 kernel: [  201.753444] ohci_hcd 0000:09:00.0: PCI INT A disabled
Feb 27 20:08:20 linuxmint6 kernel: [  201.753574] ohci_hcd 0000:09:00.1: remove, state 0
Feb 27 20:08:20 linuxmint6 kernel: [  201.753587] usb usb7: USB disconnect, address 1
Feb 27 20:08:20 linuxmint6 kernel: [  201.754135] ohci_hcd 0000:09:00.1: USB bus 7 deregistered
Feb 27 20:08:20 linuxmint6 kernel: [  201.754217] ohci_hcd 0000:09:00.1: PCI INT B disabled

```

---

