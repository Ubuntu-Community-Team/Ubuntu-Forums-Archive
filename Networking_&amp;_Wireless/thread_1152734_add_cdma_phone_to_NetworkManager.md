---
title: "add cdma phone to NetworkManager"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by makan on 2009-05-08
i have a haier c2000 cdma phone. i can use it using wvdial.
now, i want to set NetworkManager auto detect when i insert my phone to usb.

i have tried create additional entry in /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
```
      <!-- Haier/Qualcomm -->
      <match key="@info.parent:usb.vendor_id" int="0x05c6">
        <!-- Haier C2000 -->
        <match key="@info.parent:usb.product_id" int_outof="0x3197">
          <match key="@info.parent:usb.interface.number" int="0">
            <append key="modem.command_sets" type="strlist">IS-707-A</append>
          </match>
        </match>
      </match>
```

but it not work at all..
can somebody help me to solve this issue?


and here is lsusb -v result:

```

Bus 002 Device 003: ID 05c6:3197 Qualcomm, Inc. CDMA Wireless Modem/Phone
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        16
  idVendor           0x05c6 Qualcomm, Inc.
  idProduct          0x3197 CDMA Wireless Modem/Phone
  bcdDevice            0.00
  iManufacturer           1 Qualcomm, Incorporated
  iProduct                2 Qualcomm CDMA Technologies MSM
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           62
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              3 Data Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval             128
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x8a  EP 10 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0b  EP 11 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              3 Data Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)

```

---

### Post by GeorgeVita on 2009-05-08
Hi **makan**,
does the system creates any **/dev/ttyUSBx** (or /dev/ttyACMx) port to communicate with your modem?

You can check it with the terminal command: **ls /dev/ttyU* /dev/ttyA***

Reboot without modem, wait for the system to stabilize, attach the modem, after 15 seconds open a terminal window and: **dmesg**

See last 10-15 lines ragarding the modem or any driver (option, usbserial, etc). If you need help post here those (10-15) lines.

If you don't see any port try: **sudo modprobe usbserial vendor=0x05c6 product=0x3197**

Also in your "patch" place **int="0x3197"**  instead of int_outof="0x3197" as this is the **only** parameter.

Regards,
George

---

### Post by makan on 2009-05-11
hi Goerge...

thank you for your respond, but NetworkManager still cannot find my cdma phone :(

here is dmesg and ls result

```

[  167.048082] usb 2-2: new full speed USB device using uhci_hcd and address 3
[  167.266976] usb 2-2: configuration #1 chosen from 1 choice
[  167.313968] USB Serial support registered for moto-modem
[  167.314000] moto-modem 2-2:1.0: moto-modem converter detected
[  167.314117] usb 2-2: moto-modem converter now attached to ttyUSB0
[  167.314133] moto-modem 2-2:1.1: moto-modem converter detected
[  167.314207] usb 2-2: moto-modem converter now attached to ttyUSB1
[  167.314231] usbcore: registered new interface driver moto-modem

$ ls /dev/ttyUSB*
/dev/ttyUSB0  /dev/ttyUSB1

```

and i have edit 10-modem.fdi as you suggested
```

      <match key="@info.parent:usb.vendor_id" int="0x05c6">
        <match key="@info.parent:usb.product_id" **int="0x3197**">
          <match key="@info.parent:usb.interface.number" int="0">
            <append key="modem.command_sets" type="strlist">IS-707-A</append>
          </match>
        </match>
      </match>

```

since my jaunty recognize my cdma phone (according to dmesg), so i don't need to run "sudo modprobe usbserial vendor=0x05c6 product=0x3197". however, when i tried to run it return with :

*FATAL: Module usbserial not found.*

---

### Post by GeorgeVita on 2009-05-11
Hi again.
as 9.04 is NOT backward compatible with wvdial, usbserial etc., you need to install these packages via synaptic manager, BUT in your case you don't need to do this. There are other drivers working for your modem and the needed serial ports are created.

Also you do not need to add anything into 10-modem.fdi file as the description already exists. Check by yourself: open the file and search for **5c6** (0x05c6, 0x5c6 and 0x00005c6 is the same HEXadecimal number)

SO: remove your lines, boot without modem. Attach it, wait 10-20 seconds for any auto-run applet (if not try manually) that will help you setup the connection.

If still not working something else matters.

Regards,
George

---

### Post by makan on 2009-05-11
hi goerge,

fyi, jaunty default configuration doesn't recognize my cdma phone. that's way i tried to edit 10-modem.fdi.


i just found out that 10-modem.fdi state "<match key="info.category" string="serial">" on line 5, since jaunty doesn't provide *Module usbserial* so i create another file (10-modem_Q.fdi) and i fill it with 

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- xml -*- -->

<deviceinfo version="0.2">
  <device>
    **<match key="info.category" string="usb_device">**

<!-- ***************************************************** 
	ID 05c6:3197 Qualcomm, Inc. CDMA Wireless Modem/PhoneUSB devices
     ***************************************************** --> 
      <match key="@info.parent:usb.vendor_id" int="0x05c6">
        <match key="@info.parent:usb.product_id" int="0x3197">
          <match key="@info.parent:usb.interface.number" int="0">
            <append key="modem.command_sets" type="strlist">IS-707-A</append>
          </match>
        </match>
      </match>

    </match>
  </device>
</deviceinfo>
```

and the result, NetworkManager found my phone but ignoring it :(

```

May 12 04:48:38 IS00286 kernel: [  369.228058] usb 2-2: new full speed USB device using uhci_hcd and address 3
May 12 04:48:38 IS00286 kernel: [  369.451613] usb 2-2: configuration #1 chosen from 1 choice
May 12 04:48:38 IS00286 kernel: [  369.541588] USB Serial support registered for moto-modem
May 12 04:48:38 IS00286 kernel: [  369.541622] moto-modem 2-2:1.0: moto-modem converter detected
May 12 04:48:38 IS00286 kernel: [  369.541765] usb 2-2: moto-modem converter now attached to ttyUSB0
May 12 04:48:38 IS00286 kernel: [  369.541783] moto-modem 2-2:1.1: moto-modem converter detected
May 12 04:48:38 IS00286 kernel: [  369.541860] usb 2-2: moto-modem converter now attached to ttyUSB1
May 12 04:48:38 IS00286 kernel: [  369.541885] usbcore: registered new interface driver moto-modem
[B]May 12 04:48:38 IS00286 nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/usb_device_5c6_3197_noserial_if0_serial_usb_0, iface: (null)): iface not found
May 12 04:48:38 IS00286 NetworkManager: <info>  (ttyUSB0): found serial port (udev:  hal:CDMA) 
May 12 04:48:38 IS00286 NetworkManager: <info>  (ttyUSB0): ignoring due to lack of probed mobile broadband capabilties 
May 12 04:48:38 IS00286 NetworkManager: <info>  (ttyUSB1): ignoring due to lack of mobile broadband capabilties
```[/B]

hope someone can help me to solve this issue

---

