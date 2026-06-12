---
title: "ZTE MF330 not detected by Network Manager (Ubuntu 9.10)"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by lol24h on 2009-12-23
Hi,
I'm struggling with ZTE MF330 modem ( from polish Orange provider). It's detected perfectly and works great with comgt(prev. gcom) and wvdial.
Here's dmesg :
```

[38555.912048] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted
into slot 0
[38555.912110] pci 0000:16:00.0: reg 10 32bit mmio: [0x000000-0x000fff]
[38555.912203] pci 0000:16:00.0: supports D1
[38555.912206] pci 0000:16:00.0: PME# supported from D1 D3hot D3cold
[38555.912218] pci 0000:16:00.0: PME# disabled
[38555.912294] pci 0000:16:00.2: reg 10 32bit mmio: [0x000000-0x0000ff]
[38555.912392] pci 0000:16:00.2: supports D1 D2
[38555.912393] pci 0000:16:00.2: PME# supported from D0 D1 D2 D3hot D3cold
[38555.912400] pci 0000:16:00.2: PME# disabled
[38555.912532] ohci_hcd 0000:16:00.0: enabling device (0000 -> 0002)
[38555.912541] ohci_hcd 0000:16:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ
16
[38555.912581] ohci_hcd 0000:16:00.0: setting latency timer to 64
[38555.912585] ohci_hcd 0000:16:00.0: OHCI Host Controller
[38555.912703] ohci_hcd 0000:16:00.0: new USB bus registered, assigned bus
number 8
[38555.912724] ohci_hcd 0000:16:00.0: irq 16, io mem 0x80000000
[38556.474343] usb usb8: configuration #1 chosen from 1 choice
[38556.474381] hub 8-0:1.0: USB hub found
[38556.474395] hub 8-0:1.0: 2 ports detected
[38556.474532] ehci_hcd 0000:16:00.2: enabling device (0000 -> 0002)
[38556.474542] ehci_hcd 0000:16:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ
16
[38556.474587] ehci_hcd 0000:16:00.2: setting latency timer to 64
[38556.474592] ehci_hcd 0000:16:00.2: EHCI Host Controller
[38556.474636] ehci_hcd 0000:16:00.2: new USB bus registered, assigned bus
number 9
[38556.496090] ehci_hcd 0000:16:00.2: irq 16, io mem 0x80001000
[38556.508050] ehci_hcd 0000:16:00.2: USB 2.0 started, EHCI 1.00
[38556.508159] usb usb9: configuration #1 chosen from 1 choice
[38556.508196] hub 9-0:1.0: USB hub found
[38556.508204] hub 9-0:1.0: 2 ports detected
[38556.529168] type=1400 audit(1261579894.732:685): avc:  denied  { read write
} for  pid=1762 comm="devkit-power-da" name="001" dev=tmpfs ino=94272
scontext=system_u:system_r:system_dbusd_t:s0
tcontext=system_u:object_r:usb_device_t:s0 tclass=chr_file
[38556.529181] type=1400 audit(1261579894.732:686): avc:  denied  { open } for
pid=1762 comm="devkit-power-da" name="001" dev=tmpfs ino=94272
scontext=system_u:system_r:system_dbusd_t:s0
tcontext=system_u:object_r:usb_device_t:s0 tclass=chr_file
[38559.068075] hub 9-0:1.0: unable to enumerate USB device on port 2
[38559.396060] usb 8-2: new full speed USB device using ohci_hcd and address 2
[38559.609290] usb 8-2: configuration #1 chosen from 1 choice
[38559.615247] option 8-2:1.0: GSM modem (1-port) converter detected
[38559.615331] usb 8-2: GSM modem (1-port) converter now attached to ttyUSB0
[38559.618238] option 8-2:1.1: GSM modem (1-port) converter detected
[38559.618311] usb 8-2: GSM modem (1-port) converter now attached to ttyUSB1
[38559.621228] option 8-2:1.2: GSM modem (1-port) converter detected
[38559.621292] usb 8-2: GSM modem (1-port) converter now attached to ttyUSB2

```
lusb shows:
```

Bus 008 Device 002: ID 19d2:0001 ONDA Communication S.p.A. 
...
  iProduct                2 ZTE CDMA Technologies MSM
...

```

This device is in /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
```

  <match key="@info.parent:usb.vendor_id" int="0x19d2">
        <!-- Qualcomm: Telstra/NextG CDMA , ZTE CDMA Tech -->
        <match key="@info.parent:usb.product_id" int_outof="0x0001;0xfffe">
          <match key="@info.parent:usb.interface.number" int="0">
            <append key="modem.command_sets" type="strlist">IS-707-A</append>
          </match>
        </match>

```


To show, modem work perfectly with comgt :
```

$ sudo comgt -d /dev/ttyUSB0 
[sudo] password for bartek: 

Enter PIN number: xxxx
Waiting for Registration..(120 sec max)...
Registered on Home network:  IDEA",260,3,"CS_ONLY","ROAM_OFF"
Signal Quality: 12,99

```

and then wvdial, config:
```

[Dialer Defaults]
Phone = *99***#
New PPPD = yes
Stupid Mode = 1 # Don't wait for prompt, there won't be
Modem = /dev/ttyUSB0
Username = internet
Password = internet

```
Running:
```


--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Sending: ATDT*99***#
--> Waiting for carrier.
ATDT*99***#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Dec 23 17:14:53 2009
--> Pid of pppd: 11146
--> Using interface ppp0
--> pppd: Ø+¹[08]Ø+¹[08]
--> pppd: Ø+¹[08]Ø+¹[08]
--> pppd: Ø+¹[08]Ø+¹[08]
--> pppd: Ø+¹[08]Ø+¹[08]
--> pppd: Ø+¹[08]Ø+¹[08]
--> pppd: Ø+¹[08]Ø+¹[08]
--> pppd: Ø+¹[08]Ø+¹[08]
--> local  IP address 91.94.119.200
--> pppd: Ø+¹[08]Ø+¹[08]
--> remote IP address 10.64.64.64
--> pppd: Ø+¹[08]Ø+¹[08]
--> primary   DNS address 217.116.100.65
--> pppd: Ø+¹[08]Ø+¹[08]
--> secondary DNS address 79.163.127.70
--> pppd: Ø+¹[08]Ø+¹[08]

```

As I said network-manager doesn't launch wizard or anything. If I connect my NokiaE51 then it launches and after setup it just works.

I don't know how to check what exactly happens. give me some specifics, please.

---

### Post by GeorgeVita on 2009-12-23
Hi **lol24h**, some points to check & try:

Info about network manager & 3g:
[https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)
[https://wiki.ubuntu.com/NetworkManager/Hardware/3G/Probing](https://wiki.ubuntu.com/NetworkManager/Hardware/3G/Probing)

From 9.10 network manager cooperates with modem-manager which handles all 'modem drivers'. ZTE modems are not adapted very well. In previous versions file 10-modem.fdi was used by HAL to set parameters but now HAL becomes deprecated (there is no 10-modem.fdi file within next Ubuntu 10.04).

Your 10-modem.fdi file uses CDMA/EVDO command set for 19d2:0001 so you can try to change 'modem.command_sets' parameters to see it as a GSM modem:
```
      <match key="@info.parent:usb.vendor_id" int="0x19d2">
        <!-- Qualcomm: Telstra/NextG CDMA , ZTE CDMA Tech -->
        <match key="@info.parent:usb.product_id" int_outof="0x0001;0xfffe">
          <match key="@info.parent:usb.interface.number" int="0">
            <append key="modem.command_sets" type="strlist">GSM-07.07</append>
            <append key="modem.command_sets" type="strlist">GSM-07.05</append>
          </match>
        </match>
... etc

```

You are using phone number *99***# which works (!) but I think the correct number must be *99# (general data call), *99*****1**# (to use the AT+CGDCONT=**1**,... PDP Context Identifier), etc

Regards,
George

---

### Post by souris00 on 2009-12-25
Hi all.
I'm really more unlucky than lol24h...as I'm not able to make system see ZTE MF330 card.
When I insert the card in the slot, LED color remains red.
Look and see what is stating dmseg:

***************
[   72.805216] usb 10-1: configuration #1 chosen from 1 choice
[   74.076144] usbcore: registered new interface driver usbserial
[   74.076161] USB Serial support registered for generic
[   74.076207] usbcore: registered new interface driver usbserial_generic
[   74.076209] usbserial: USB Serial Driver core
[   74.099443] USB Serial support registered for GSM modem (1-port)
[   74.099502] option 10-1:1.0: GSM modem (1-port) converter detected
[   74.099593] usb 10-1: GSM modem (1-port) converter now attached to ttyUSB0
[   74.099612] option 10-1:1.1: GSM modem (1-port) converter detected
[   74.099665] usb 10-1: GSM modem (1-port) converter now attached to ttyUSB1
[   74.099681] option 10-1:1.2: GSM modem (1-port) converter detected
[   74.099729] usb 10-1: GSM modem (1-port) converter now attached to ttyUSB2
[   74.099743] usbcore: registered new interface driver option
[   74.099745] option: v0.7.2:USB Driver for GSM modems
[   75.521399] lp: driver loaded but no devices found
[   75.530794] sr 6:0:0:1: [sr1] Unhandled sense code
[   75.530797] sr 6:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   75.530801] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[   75.530806] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[   75.530811] end_request: I/O error, dev sr1, sector 196352
[   75.530858] __ratelimit: 11 callbacks suppressed
[   75.530860] Buffer I/O error on device sr1, logical block 49088
[   75.530901] Buffer I/O error on device sr1, logical block 49089
[   75.540874] sr 6:0:0:1: [sr1] Unhandled sense code
[   75.540879] sr 6:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   75.540885] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[   75.540892] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[   75.540901] end_request: I/O error, dev sr1, sector 196352
[   75.540969] Buffer I/O error on device sr1, logical block 49088
[   75.541052] Buffer I/O error on device sr1, logical block 49089
[   75.553598] ppdev: user-space parallel port driver
[   76.001865] sr 6:0:0:1: [sr1] Unhandled sense code
[   76.001870] sr 6:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   76.001877] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[   76.001885] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[   76.001893] end_request: I/O error, dev sr1, sector 196584
[   76.001960] Buffer I/O error on device sr1, logical block 49146
[   76.002026] Buffer I/O error on device sr1, logical block 49147
[   76.017986] sr 6:0:0:1: [sr1] Unhandled sense code
[   76.017992] sr 6:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   76.017997] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[   76.018004] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[   76.018012] end_request: I/O error, dev sr1, sector 196584
[   76.018080] Buffer I/O error on device sr1, logical block 49146
[   76.018146] Buffer I/O error on device sr1, logical block 49147
[   76.028874] sr 6:0:0:1: [sr1] Unhandled sense code
[   76.028879] sr 6:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   76.028885] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[   76.028891] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[   76.028899] end_request: I/O error, dev sr1, sector 196600
[   76.028965] Buffer I/O error on device sr1, logical block 49150
[   76.039475] sr 6:0:0:1: [sr1] Unhandled sense code
[   76.039481] sr 6:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   76.039487] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[   76.039494] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[   76.039501] end_request: I/O error, dev sr1, sector 196600
[   76.039569] Buffer I/O error on device sr1, logical block 49150
[   76.052369] sr 6:0:0:1: [sr1] Unhandled sense code
[   76.052372] sr 6:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   76.052376] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[   76.052380] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[   76.052385] end_request: I/O error, dev sr1, sector 196600
[   76.063351] sr 6:0:0:1: [sr1] Unhandled sense code
[   76.063354] sr 6:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   76.063357] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[   76.063361] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[   76.063365] end_request: I/O error, dev sr1, sector 196600
[   76.073994] sr 6:0:0:1: [sr1] Unhandled sense code
[   76.073999] sr 6:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   76.074004] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[   76.074011] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[   76.074019] end_request: I/O error, dev sr1, sector 196600
[   76.085342] sr 6:0:0:1: [sr1] Unhandled sense code
[   76.085345] sr 6:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   76.085350] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[   76.085354] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[   76.085359] end_request: I/O error, dev sr1, sector 196600
[   76.995995] sr 6:0:0:1: [sr1] Unhandled sense code
[   76.996000] sr 6:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   76.996019] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[   76.996026] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[   76.996035] end_request: I/O error, dev sr1, sector 196600
[   77.006971] sr 6:0:0:1: [sr1] Unhandled sense code
[   77.006977] sr 6:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   77.006982] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[   77.006989] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[   77.006997] end_request: I/O error, dev sr1, sector 196536
[   77.021345] sr 6:0:0:1: [sr1] Unhandled sense code
[   77.021348] sr 6:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   77.021352] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[   77.021357] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[   77.021362] end_request: I/O error, dev sr1, sector 196592
[   77.476237] sr 6:0:0:1: [sr1] Unhandled sense code
[   77.476240] sr 6:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   77.476243] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[   77.476248] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[   77.476252] end_request: I/O error, dev sr1, sector 196600
[   77.938236] sr 6:0:0:1: [sr1] Unhandled sense code
[   77.938241] sr 6:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   77.938247] sr 6:0:0:1: [sr1] Sense Key : No Sense [current] 
[   77.938254] sr 6:0:0:1: [sr1] Add. Sense: No additional sense information
[   77.938262] end_request: I/O error, dev sr1, sector 196600
[   80.373066] i2c-adapter i2c-2: unable to read EDID block.
[   80.373071] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   80.377493] i2c-adapter i2c-2: unable to read EDID block.
[   80.377495] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   80.382701] i2c-adapter i2c-4: unable to read EDID block.
[   80.382704] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[   80.387436] i2c-adapter i2c-4: unable to read EDID block.
[   80.387438] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[   80.433305] [drm] TV-25: set mode NTSC 480i 0
[   80.577615] [drm] TV-25: set mode NTSC 480i 0
[   80.800809] i2c-adapter i2c-2: unable to read EDID block.
[   80.800814] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   80.806305] i2c-adapter i2c-2: unable to read EDID block.
[   80.806310] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   80.811352] i2c-adapter i2c-4: unable to read EDID block.
[   80.811357] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[   80.817187] i2c-adapter i2c-4: unable to read EDID block.
[   80.817192] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[   80.863396] [drm] TV-25: set mode NTSC 480i 0
[   81.005151] [drm] TV-25: set mode NTSC 480i 0
[  140.156060] i2c-adapter i2c-2: unable to read EDID block.
[  140.156065] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[  140.160758] i2c-adapter i2c-2: unable to read EDID block.
[  140.160760] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[  140.165450] i2c-adapter i2c-4: unable to read EDID block.
[  140.165453] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[  140.169865] i2c-adapter i2c-4: unable to read EDID block.
[  140.169867] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[  140.215639] [drm] TV-25: set mode NTSC 480i 0
[  140.355824] [drm] TV-25: set mode NTSC 480i 0
[  140.583983] i2c-adapter i2c-2: unable to read EDID block.
[  140.583987] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[  140.588404] i2c-adapter i2c-2: unable to read EDID block.
[  140.588406] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[  140.592862] i2c-adapter i2c-4: unable to read EDID block.
[  140.592864] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[  140.597284] i2c-adapter i2c-4: unable to read EDID block.
[  140.597287] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[  140.643053] [drm] TV-25: set mode NTSC 480i 0
[  140.783197] [drm] TV-25: set mode NTSC 480i 0
[  141.090843] i2c-adapter i2c-2: unable to read EDID block.
[  141.090848] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[  141.095746] i2c-adapter i2c-2: unable to read EDID block.
[  141.095752] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[  141.104310] i2c-adapter i2c-4: unable to read EDID block.
[  141.104316] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[  141.108876] i2c-adapter i2c-4: unable to read EDID block.
[  141.108879] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[  141.154734] [drm] TV-25: set mode NTSC 480i 0
[  141.297455] [drm] TV-25: set mode NTSC 480i 0
[  151.108018] i2c-adapter i2c-2: unable to read EDID block.
[  151.108022] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[  151.112695] i2c-adapter i2c-2: unable to read EDID block.
[  151.112698] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[  151.117382] i2c-adapter i2c-4: unable to read EDID block.
[  151.117384] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[  151.121803] i2c-adapter i2c-4: unable to read EDID block.
[  151.121805] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[  151.167573] [drm] TV-25: set mode NTSC 480i 0
[  151.307729] [drm] TV-25: set mode NTSC 480i 0
[  157.191846] wlan0: authenticate with AP 00:1e:2a:f3:f0:1c
[  157.193787] wlan0: authenticated
[  157.193791] wlan0: associate with AP 00:1e:2a:f3:f0:1c
[  157.196112] wlan0: RX AssocResp from 00:1e:2a:f3:f0:1c (capab=0x411 status=0 aid=1)
[  157.196117] wlan0: associated
[  157.199038] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  165.474976] ohci_hcd 0000:03:00.1: OHCI Unrecoverable Error, disabled
[  165.474987] ohci_hcd 0000:03:00.1: HC died; cleaning up
[  165.475035] usb 10-1: USB disconnect, address 2
[  165.475048] option: option_instat_callback: error -108
[  165.475054] ohci_hcd 0000:03:00.1: leak ed f2933040 (#81) state 0 (has tds)
[  165.475373] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  165.475407] option 10-1:1.0: device disconnected
[  165.475640] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  165.475681] option 10-1:1.1: device disconnected
[  165.475896] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  165.475925] option 10-1:1.2: device disconnected
***************

It seems that something fails in assigning bus no. 10 to the card.
lsusb doesn't find the card (and bus 10, too):

Bus 011 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0781:5530 SanDisk Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


I modified 10-modem.fdi as suggested by GeorgeVita.

I'm using  Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic), booting from a pendrive.

Can you help me?
Please consider I'm a real newbie, so please be patient. Thank you in advance.
souris00

---

### Post by GeorgeVita on 2009-12-26
Hi **souris00**, welcome to this forum!

Your kernel is the 'buggy' one for 3g modems! Ubuntu 9.10 came out with this ... so you need to update it using a wifi or ethernet connection. Then retry.
In case you have no other connection you must try an 'offline' solution by downloading kernel and install it manually (more complicate).

(read more at [http://ubuntuforums.org/showpost.php?p=8212747&postcount=11](http://ubuntuforums.org/showpost.php?p=8212747&postcount=11) and [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146))

Regards,
George

---

### Post by souris00 on 2009-12-28
Thank you George for your prompt reply (I wasn't able: out of home, my NOKIA 6630 with GPRS-only connection suffers a lot of drop call and very slow speed and long no-service...ah!).
I understand I must do an update of my installed UBUNTU 2.6.31-14 to a newer version to fix the bug.
Is there any easy way to make this update or is it better to re-install it from scratch?
Please consider I'm using and extrernal USB pendrive as a boot disk -company notebook PC ... no modification on the HD :(.
Thank you in advance for your kindness with a newbie like me.
souris00

---

### Post by GeorgeVita on 2009-12-28
Hi **souris00**,
it is difficult to update kernel on Ubuntu running from removable media (persistent).
As I have tested you can do it only with fully **installed** Ubuntu  on the USB memory stick (I am doing it on SDHC).
To succeed this you must boot from a USB stick (or LiveCD) and then  install to another USB stick. Just be careful about drive names and NOT format your HD! At my first try, I opened bottom cover of my laptop and removed my HD...

Regards,
George

---

### Post by lol24h on 2009-12-28
> **GeorgeVita said:**
> 

Your 10-modem.fdi file uses CDMA/EVDO command set for 19d2:0001 so you can try to change 'modem.command_sets' parameters to see it as a GSM modem:
```
      <match key="@info.parent:usb.vendor_id" int="0x19d2">
        <!-- Qualcomm: Telstra/NextG CDMA , ZTE CDMA Tech -->
        <match key="@info.parent:usb.product_id" int_outof="0x0001;0xfffe">
          <match key="@info.parent:usb.interface.number" int="0">
            <append key="modem.command_sets" type="strlist">GSM-07.07</append>
            <append key="modem.command_sets" type="strlist">GSM-07.05</append>
          </match>
        </match>
... etc

```


I've tried it with no result. I added position in wiki, and reported bug
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/501005]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/501005")

---

