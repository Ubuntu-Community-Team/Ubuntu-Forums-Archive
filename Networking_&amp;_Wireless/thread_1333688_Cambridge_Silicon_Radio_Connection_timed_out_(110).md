---
title: "Cambridge Silicon Radio: Connection timed out (110)"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by beyossi on 2009-11-21
Hi,

This issue was discussed in the past, and I saw that bugs were sumitted, however I didn't understand the bottom line: Can an Ubuntu user use that bluetooth dongle or not?


quado@quado-desktop:~$ lsusb
...
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
...

quado@quado-desktop:~$ hciconfig 
hci0:    Type: USB
    BD Address: 00:00:00:00:00:00 ACL MTU: 1021:4 SCO MTU: 180:1
    DOWN 
    RX bytes:41 acl:0 sco:0 events:3 errors:0
    TX bytes:9 acl:0 sco:0 commands:5 errors:2


quado@quado-desktop:~$ sudo hciconfig hci0 up
Can't init device hci0: Connection timed out (110)

quado@quado-desktop:~$ sudo hciconfig hci0 reset
Can't init device hci0: Connection timed out (110)


Thanks,
Yossi

---

### Post by Jophish on 2010-02-04
I am also trying to get this to work.
At least mine shows a valid BT address.

```
$ sudo hciconfig
hci0:   Type: USB
        BD Address: 00:1F:81:00:02:50 ACL MTU: 1021:4 SCO MTU: 180:1
        DOWN
        RX bytes:1971 acl:0 sco:0 events:61 errors:0
        TX bytes:983 acl:0 sco:0 commands:92 errors:35

```

```
$ sudo hciconfig hci0 up
Can't init device hci0: Connection timed out (110)

```

```
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Device Descriptor:                                                                       
  bLength                18                                                              
  bDescriptorType         1                                                              
  bcdUSB               2.00                                                              
  bDeviceClass          224 Wireless                                                     
  bDeviceSubClass         1 Radio Frequency                                              
  bDeviceProtocol         1 Bluetooth                                                    
  bMaxPacketSize0        64                                                              
  idVendor           0x0a12 Cambridge Silicon Radio, Ltd                                 
  idProduct          0x0001 Bluetooth Dongle (HCI mode)                                  
  bcdDevice           19.15                                                              
  iManufacturer           0                                                              
  iProduct                0                                                              
  iSerial                 0                                                              
  bNumConfigurations      1                                                              
  Configuration Descriptor:                                                              
    bLength                 9                                                            
    bDescriptorType         2                                                            
    wTotalLength          193                                                            
    bNumInterfaces          3                                                            
    bConfigurationValue     1                                                            
    iConfiguration          0                                                            
    bmAttributes         0xc0                                                            
      Self Powered                                                                       
    MaxPower                0mA                                                          
    Interface Descriptor:                                                                
      bLength                 9                                                          
      bDescriptorType         4                                                          
      bInterfaceNumber        0                                                          
      bAlternateSetting       0                                                          
      bNumEndpoints           3                                                          
      bInterfaceClass       224 Wireless                                                 
      bInterfaceSubClass      1 Radio Frequency                                          
      bInterfaceProtocol      1 Bluetooth                                                
      iInterface              0                                                          
      Endpoint Descriptor:                                                               
        bLength                 7                                                        
        bDescriptorType         5                                                        
        bEndpointAddress     0x81  EP 1 IN                                               
        bmAttributes            3                                                        
          Transfer Type            Interrupt                                             
          Synch Type               None                                                  
          Usage Type               Data                                                  
        wMaxPacketSize     0x0010  1x 16 bytes                                           
        bInterval               1                                                        
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
        bEndpointAddress     0x02  EP 2 OUT                                              
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
      bInterfaceClass       224 Wireless                                                 
      bInterfaceSubClass      1 Radio Frequency                                          
      bInterfaceProtocol      1 Bluetooth                                                
      iInterface              0                                                          
      Endpoint Descriptor:                                                               
        bLength                 7                                                        
        bDescriptorType         5                                                        
        bEndpointAddress     0x83  EP 3 IN                                               
        bmAttributes            1                                                        
          Transfer Type            Isochronous                                           
          Synch Type               None                                                  
          Usage Type               Data                                                  
        wMaxPacketSize     0x0020  1x 32 bytes                                           
        bInterval               1                                                        
      Endpoint Descriptor:                                                               
        bLength                 7                                                        
        bDescriptorType         5                                                        
        bEndpointAddress     0x03  EP 3 OUT                                              
        bmAttributes            1                                                        
          Transfer Type            Isochronous                                           
          Synch Type               None                                                  
          Usage Type               Data                                                  
        wMaxPacketSize     0x0020  1x 32 bytes                                           
        bInterval               1                                                        
    Interface Descriptor:                                                                
      bLength                 9                                                          
      bDescriptorType         4                                                          
      bInterfaceNumber        1                                                          
      bAlternateSetting       1                                                          
      bNumEndpoints           2                                                          
      bInterfaceClass       224 Wireless                                                 
      bInterfaceSubClass      1 Radio Frequency                                          
      bInterfaceProtocol      1 Bluetooth                                                
      iInterface              0                                                          
      Endpoint Descriptor:                                                               
        bLength                 7                                                        
        bDescriptorType         5                                                        
        bEndpointAddress     0x83  EP 3 IN                                               
        bmAttributes            1                                                        
          Transfer Type            Isochronous                                           
          Synch Type               None                                                  
          Usage Type               Data                                                  
        wMaxPacketSize     0x0009  1x 9 bytes                                            
        bInterval               1                                                        
      Endpoint Descriptor:                                                               
        bLength                 7                                                        
        bDescriptorType         5                                                        
        bEndpointAddress     0x03  EP 3 OUT                                              
        bmAttributes            1                                                        
          Transfer Type            Isochronous                                           
          Synch Type               None                                                  
          Usage Type               Data                                                  
        wMaxPacketSize     0x0009  1x 9 bytes                                            
        bInterval               1                                                        
    Interface Descriptor:                                                                
      bLength                 9                                                          
      bDescriptorType         4                                                          
      bInterfaceNumber        1                                                          
      bAlternateSetting       2                                                          
      bNumEndpoints           2                                                          
      bInterfaceClass       224 Wireless                                                 
      bInterfaceSubClass      1 Radio Frequency                                          
      bInterfaceProtocol      1 Bluetooth                                                
      iInterface              0                                                          
      Endpoint Descriptor:                                                               
        bLength                 7                                                        
        bDescriptorType         5                                                        
        bEndpointAddress     0x83  EP 3 IN                                               
        bmAttributes            1                                                        
          Transfer Type            Isochronous                                           
          Synch Type               None                                                  
          Usage Type               Data                                                  
        wMaxPacketSize     0x0011  1x 17 bytes                                           
        bInterval               1                                                        
      Endpoint Descriptor:                                                               
        bLength                 7                                                        
        bDescriptorType         5                                                        
        bEndpointAddress     0x03  EP 3 OUT                                              
        bmAttributes            1                                                        
          Transfer Type            Isochronous                                           
          Synch Type               None                                                  
          Usage Type               Data                                                  
        wMaxPacketSize     0x0011  1x 17 bytes                                           
        bInterval               1                                                        
    Interface Descriptor:                                                                
      bLength                 9                                                          
      bDescriptorType         4                                                          
      bInterfaceNumber        1                                                          
      bAlternateSetting       3                                                          
      bNumEndpoints           2                                                          
      bInterfaceClass       224 Wireless                                                 
      bInterfaceSubClass      1 Radio Frequency                                          
      bInterfaceProtocol      1 Bluetooth                                                
      iInterface              0                                                          
      Endpoint Descriptor:                                                               
        bLength                 7                                                        
        bDescriptorType         5                                                        
        bEndpointAddress     0x83  EP 3 IN                                               
        bmAttributes            1                                                        
          Transfer Type            Isochronous                                           
          Synch Type               None                                                  
          Usage Type               Data                                                  
        wMaxPacketSize     0x0019  1x 25 bytes                                           
        bInterval               1                                                        
      Endpoint Descriptor:                                                               
        bLength                 7                                                        
        bDescriptorType         5                                                        
        bEndpointAddress     0x03  EP 3 OUT                                              
        bmAttributes            1                                                        
          Transfer Type            Isochronous                                           
          Synch Type               None                                                  
          Usage Type               Data                                                  
        wMaxPacketSize     0x0019  1x 25 bytes                                           
        bInterval               1                                                        
    Interface Descriptor:                                                                
      bLength                 9                                                          
      bDescriptorType         4                                                          
      bInterfaceNumber        1                                                          
      bAlternateSetting       4                                                          
      bNumEndpoints           2                                                          
      bInterfaceClass       224 Wireless                                                 
      bInterfaceSubClass      1 Radio Frequency                                          
      bInterfaceProtocol      1 Bluetooth                                                
      iInterface              0                                                          
      Endpoint Descriptor:                                                               
        bLength                 7                                                        
        bDescriptorType         5                                                        
        bEndpointAddress     0x83  EP 3 IN                                               
        bmAttributes            1                                                        
          Transfer Type            Isochronous                                           
          Synch Type               None                                                  
          Usage Type               Data                                                  
        wMaxPacketSize     0x0021  1x 33 bytes                                           
        bInterval               1                                                        
      Endpoint Descriptor:                                                               
        bLength                 7                                                        
        bDescriptorType         5                                                        
        bEndpointAddress     0x03  EP 3 OUT                                              
        bmAttributes            1                                                        
          Transfer Type            Isochronous                                           
          Synch Type               None                                                  
          Usage Type               Data                                                  
        wMaxPacketSize     0x0021  1x 33 bytes                                           
        bInterval               1                                                        
    Interface Descriptor:                                                                
      bLength                 9                                                          
      bDescriptorType         4                                                          
      bInterfaceNumber        1                                                          
      bAlternateSetting       5                                                          
      bNumEndpoints           2                                                          
      bInterfaceClass       224 Wireless                                                 
      bInterfaceSubClass      1 Radio Frequency                                          
      bInterfaceProtocol      1 Bluetooth                                                
      iInterface              0                                                          
      Endpoint Descriptor:                                                               
        bLength                 7                                                        
        bDescriptorType         5                                                        
        bEndpointAddress     0x83  EP 3 IN                                               
        bmAttributes            1                                                        
          Transfer Type            Isochronous                                           
          Synch Type               None                                                  
          Usage Type               Data                                                  
        wMaxPacketSize     0x0031  1x 49 bytes                                           
        bInterval               1                                                        
      Endpoint Descriptor:                                                               
        bLength                 7                                                        
        bDescriptorType         5                                                        
        bEndpointAddress     0x03  EP 3 OUT                                              
        bmAttributes            1                                                        
          Transfer Type            Isochronous                                           
          Synch Type               None                                                  
          Usage Type               Data                                                  
        wMaxPacketSize     0x0031  1x 49 bytes                                           
        bInterval               1                                                        
    Interface Descriptor:                                                                
      bLength                 9                                                          
      bDescriptorType         4                                                          
      bInterfaceNumber        2                                                          
      bAlternateSetting       0                                                          
      bNumEndpoints           0                                                          
      bInterfaceClass       254 Application Specific Interface                           
      bInterfaceSubClass      1 Device Firmware Update                                   
      bInterfaceProtocol      0                                                          
      iInterface              0                                                          
      Device Firmware Upgrade Interface Descriptor:                                      
        bLength                             7                                            
        bDescriptorType                    33                                            
        bmAttributes                        7                                            
          Will Not Detach                                                                
          Manifestation Tolerant                                                         
          Upload Supported                                                               
          Download Supported                                                             
        wDetachTimeout                   5000 milliseconds                               
        wTransferSize                    1023 bytes                                      
can't get device qualifier: Protocol error                                               
can't get debug descriptor: Protocol error                                               
cannot read device status, Protocol error (71)
```

---

### Post by beyossi on 2010-02-05
Jophish, good luck. Let me know if you have good results at the end.
I gave up due to time constraints and moved to alternative solutions, though I may still prefer that BT alternative.

---

### Post by MaikoID on 2011-04-26
Hi, I've the same situation. I'm giving up too.

---

### Post by keithspg on 2012-02-10
still no joy with this dongle. The deal is that this is a specifi revision which has a problem. I have an earlier version which works fine, but if the dongle reports "bcdDevice           19.15", it will probably not work.

Fedora is also aware of this. It works under Win7 x64. Currently, it will load and scan for devices, but when any data transfer is tried, it panics and freezes the computer.

Keith

---

