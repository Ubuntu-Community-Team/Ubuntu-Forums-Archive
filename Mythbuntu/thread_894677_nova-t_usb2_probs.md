---
title: "nova-t usb2 probs"
date: 2008-08-19
forum: Mythbuntu
---

### Post by Crowie on 2008-08-19
Ive recently added the above usb device to an existing box with kernel 2.6.24-21-generic on mythbuntu Hardy with a hauppauge nova-t pci card which works fine.
Ive added the correct driver dvb-usb-nova-t-usb2-02.fw to /lib/firmware and it picks it up.  I can tune channels fine however, when I come to watch them it freezes up and cannot lock or change channels.  In dmesg, I get loads of 
```
dvb-usb: bulk message failed: -71 
```

Ive tried same with kaffeine aswell as mythtv

out put of messages:

```
Aug 19 14:15:33 shaggy kernel: [   30.094426] dvb-usb: downloading firmware from file 'dvb-usb-nova-t-usb2-02.fw'
Aug 19 14:15:33 shaggy kernel: [   30.172943] usbcore: registered new interface driver dvb_usb_nova_t_usb2
Aug 19 14:15:33 shaggy kernel: [   30.175292] usb 4-2: USB disconnect, address 3
Aug 19 14:15:33 shaggy kernel: [   30.177186] dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.
Aug 19 14:15:33 shaggy kernel: [   30.344854] usb 1-1: reset full speed USB device using ohci_hcd and address 4
Aug 19 14:15:33 shaggy kernel: [   30.551058] lirc_dev: lirc_register_plugin: sample_rate: 0
Aug 19 14:15:33 shaggy kernel: [   30.557040] lirc_mceusb2[4]: Philips eHome Infrared Transceiver on usb1:4
Aug 19 14:15:33 shaggy kernel: [   30.557083] usbcore: registered new interface driver lirc_mceusb2
Aug 19 14:15:33 shaggy kernel: [   31.740723] lp0: using parport0 (interrupt-driven).
Aug 19 14:15:33 shaggy kernel: [   31.926063] usb 4-2: new high speed USB device using ehci_hcd and address 4
Aug 19 14:15:33 shaggy kernel: [   32.027647] Adding 2265124k swap on /dev/sda5.  Priority:-1 extents:1 across:2265124k
Aug 19 14:15:33 shaggy kernel: [   32.059994] usb 4-2: configuration #1 chosen from 1 choice
Aug 19 14:15:33 shaggy kernel: [   32.060359] dvb-usb: found a 'Hauppauge WinTV-NOVA-T usb2' in warm state.
Aug 19 14:15:33 shaggy kernel: [   32.060559] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Aug 19 14:15:33 shaggy kernel: [   32.064419] DVB: registering new adapter (Hauppauge WinTV-NOVA-T usb2)
Aug 19 14:15:33 shaggy kernel: [   32.065867] dvb-usb: MAC address: 00:0d:fe:03:9a:c7
Aug 19 14:15:33 shaggy kernel: [   32.067733] DVB: registering frontend 1 (DiBcom 3000MC/P)...
Aug 19 14:15:33 shaggy kernel: [   32.131493] dvb-usb: Hauppauge WinTV-NOVA-T usb2 successfully initialized and connected.

```

Does any know of a fix for this
thanks

---

### Post by Crowie on 2008-08-20
anyone had these probs??

---

### Post by Neon Dusk on 2008-08-20
Have you tried 
options usbcore autosuspend=-1

in /etc/modprobe.d/options ?

---

### Post by Crowie on 2008-08-20
yep I added that previously still no success.  Also disabled the onboard remote and that hasnt had any affect either.

---

### Post by Neon Dusk on 2008-08-20
Are you getting a good signal? 
( I don't think that the Nova cards work well with a low signal)

---

### Post by Crowie on 2008-08-20
signal is fine, I have a nova-t 500 in pci slot which is working perfectly.  This nova-t usb2 works fine on windows and tested on mates mythbox running fedora and an earlier kernel.

in frontend log also get 

2008-08-20 16:03:15.932 NVP: Prebuffer wait timed out 10 times.
2008-08-20 16:03:17.533 NVP: Prebuffer wait timed out 10 times.

together with dvb-usb: bulk message failed in dmesg

any other suggestions??

---

### Post by Neon Dusk on 2008-08-20
It's a Nova-T 500 that I use. Hopefully someone with a Nova-T usb2 will be able to help you.

Edit: It's the Nova-T usb2 not the pci

---

### Post by Crowie on 2008-08-20
ok, thanks anyway.  Its the nova-t usb2 that im having the issues with.  The pci card works fine just the newly added nova-t usb2

---

