---
title: "webcam problem"
date: 2009-07-01
forum: Multimedia Software
---

### Post by anystupidname on 2009-07-01
I thought that this cam was supported by the gspca driver but after getting through the compile problems for the driver, I am not able to get ubuntu to add /dev/video0. (which I understand to indicate cam is working and available to apps) Any help would be much appreciated!



> lsmod | grep gspca
gspca                 700624  0
compat_ioctl32         18304  1 gspca
videodev               45184  2 gspca,compat_ioctl32


> dmesg
[  153.015510] Linux video capture interface: v2.00
[  153.117509] usbcore: registered new interface driver gspca
[  153.117514] gspca: gspca driver 01.00.20 registered
[  423.984079] usb 4-1: USB disconnect, address 2
[  428.864033] usb 5-2: new full speed USB device using uhci_hcd and address 2
[  429.010191] usb 5-2: configuration #1 chosen from 1 choice

> sudo lsusb -s 5:2 -v                                  

Bus 005 Device 002: ID 06a5:d800 Divio Chicony TwinkleCam
Device Descriptor:                                       
  bLength                18                              
  bDescriptorType         1                              
  bcdUSB               1.10                              
  bDeviceClass            0 (Defined at Interface level) 
  bDeviceSubClass         0                              
  bDeviceProtocol         0                              
  bMaxPacketSize0        64                              
  idVendor           0x06a5 Divio                        
  idProduct          0xd800 Chicony TwinkleCam           
  bcdDevice            1.10                              
  iManufacturer           0                              
  iProduct                0                              
  iSerial                 0                              
  bNumConfigurations      1                              
  Configuration Descriptor:                              
    bLength                 9                            
    bDescriptorType         2                            
    wTotalLength          249                            
    bNumInterfaces          1                            
    bConfigurationValue     1                            
    iConfiguration          0                            
    bmAttributes         0x80                            
      (Bus Powered)                                      
    MaxPower              300mA                          
    Interface Descriptor:                                
      bLength                 9                          
      bDescriptorType         4                          
      bInterfaceNumber        0                          
      bAlternateSetting       0                          
      bNumEndpoints           3                          
      bInterfaceClass       255 Vendor Specific Class    
      bInterfaceSubClass    255 Vendor Specific Subclass 
      bInterfaceProtocol    255 Vendor Specific Protocol 
      iInterface              0                          
      Endpoint Descriptor:                               
        bLength                 7                        
        bDescriptorType         5                        
        bEndpointAddress     0x81  EP 1 IN               
        bmAttributes            3                        
          Transfer Type            Interrupt             
          Synch Type               None                  
          Usage Type               Data                  
        wMaxPacketSize     0x0001  1x 1 bytes            
        bInterval               1                        
      Endpoint Descriptor:                               
        bLength                 7                        
        bDescriptorType         5                        
        bEndpointAddress     0x82  EP 2 IN               
        bmAttributes            1                        
          Transfer Type            Isochronous           
          Synch Type               None                  
          Usage Type               Data                  
        wMaxPacketSize     0x0000  1x 0 bytes            
        bInterval               1                        
      Endpoint Descriptor:                               
        bLength                 7                        
        bDescriptorType         5                        
        bEndpointAddress     0x83  EP 3 IN               
        bmAttributes            1                        
          Transfer Type            Isochronous           
          Synch Type               None                  
          Usage Type               Data                  
        wMaxPacketSize     0x0000  1x 0 bytes            
        bInterval               1                        
    Interface Descriptor:                                
      bLength                 9                          
      bDescriptorType         4                          
      bInterfaceNumber        0                          
      bAlternateSetting       1                          
      bNumEndpoints           3                          
      bInterfaceClass       255 Vendor Specific Class    
      bInterfaceSubClass    255 Vendor Specific Subclass 
      bInterfaceProtocol    255 Vendor Specific Protocol 
      iInterface              0                          
      Endpoint Descriptor:                               
        bLength                 7                        
        bDescriptorType         5                        
        bEndpointAddress     0x81  EP 1 IN               
        bmAttributes            3                        
          Transfer Type            Interrupt             
          Synch Type               None                  
          Usage Type               Data                  
        wMaxPacketSize     0x0001  1x 1 bytes            
        bInterval               1                        
      Endpoint Descriptor:                               
        bLength                 7                        
        bDescriptorType         5                        
        bEndpointAddress     0x82  EP 2 IN               
        bmAttributes            1                        
          Transfer Type            Isochronous           
          Synch Type               None                  
          Usage Type               Data                  
        wMaxPacketSize     0x03c0  1x 960 bytes          
        bInterval               1                        
      Endpoint Descriptor:                               
        bLength                 7                        
        bDescriptorType         5                        
        bEndpointAddress     0x83  EP 3 IN               
        bmAttributes            1                        
          Transfer Type            Isochronous           
          Synch Type               None                  
          Usage Type               Data                  
        wMaxPacketSize     0x0001  1x 1 bytes            
        bInterval               1                        
    Interface Descriptor:                                
      bLength                 9                          
      bDescriptorType         4                          
      bInterfaceNumber        0                          
      bAlternateSetting       2                          
      bNumEndpoints           3                          
      bInterfaceClass       255 Vendor Specific Class    
      bInterfaceSubClass    255 Vendor Specific Subclass 
      bInterfaceProtocol    255 Vendor Specific Protocol 
      iInterface              0                          
      Endpoint Descriptor:                               
        bLength                 7                        
        bDescriptorType         5                        
        bEndpointAddress     0x81  EP 1 IN               
        bmAttributes            3                        
          Transfer Type            Interrupt             
          Synch Type               None                  
          Usage Type               Data                  
        wMaxPacketSize     0x0001  1x 1 bytes            
        bInterval               1                        
      Endpoint Descriptor:                               
        bLength                 7                        
        bDescriptorType         5                        
        bEndpointAddress     0x82  EP 2 IN               
        bmAttributes            1                        
          Transfer Type            Isochronous           
          Synch Type               None                  
          Usage Type               Data                  
        wMaxPacketSize     0x0380  1x 896 bytes          
        bInterval               1                        
      Endpoint Descriptor:                               
        bLength                 7                        
        bDescriptorType         5                        
        bEndpointAddress     0x83  EP 3 IN               
        bmAttributes            1                        
          Transfer Type            Isochronous           
          Synch Type               None                  
          Usage Type               Data                  
        wMaxPacketSize     0x0001  1x 1 bytes            
        bInterval               1                        
    Interface Descriptor:                                
      bLength                 9                          
      bDescriptorType         4                          
      bInterfaceNumber        0                          
      bAlternateSetting       3                          
      bNumEndpoints           3                          
      bInterfaceClass       255 Vendor Specific Class    
      bInterfaceSubClass    255 Vendor Specific Subclass 
      bInterfaceProtocol    255 Vendor Specific Protocol 
      iInterface              0                          
      Endpoint Descriptor:                               
        bLength                 7                        
        bDescriptorType         5                        
        bEndpointAddress     0x81  EP 1 IN               
        bmAttributes            3                        
          Transfer Type            Interrupt             
          Synch Type               None                  
          Usage Type               Data                  
        wMaxPacketSize     0x0001  1x 1 bytes            
        bInterval               1                        
      Endpoint Descriptor:                               
        bLength                 7                        
        bDescriptorType         5                        
        bEndpointAddress     0x82  EP 2 IN               
        bmAttributes            1                        
          Transfer Type            Isochronous           
          Synch Type               None                  
          Usage Type               Data                  
        wMaxPacketSize     0x0300  1x 768 bytes          
        bInterval               1                        
      Endpoint Descriptor:                               
        bLength                 7                        
        bDescriptorType         5                        
        bEndpointAddress     0x83  EP 3 IN               
        bmAttributes            1                        
          Transfer Type            Isochronous           
          Synch Type               None                  
          Usage Type               Data                  
        wMaxPacketSize     0x0001  1x 1 bytes            
        bInterval               1                        
    Interface Descriptor:                                
      bLength                 9                          
      bDescriptorType         4                          
      bInterfaceNumber        0                          
      bAlternateSetting       4                          
      bNumEndpoints           3                          
      bInterfaceClass       255 Vendor Specific Class    
      bInterfaceSubClass    255 Vendor Specific Subclass 
      bInterfaceProtocol    255 Vendor Specific Protocol 
      iInterface              0                          
      Endpoint Descriptor:                               
        bLength                 7                        
        bDescriptorType         5                        
        bEndpointAddress     0x81  EP 1 IN               
        bmAttributes            3                        
          Transfer Type            Interrupt             
          Synch Type               None                  
          Usage Type               Data                  
        wMaxPacketSize     0x0001  1x 1 bytes            
        bInterval               1                        
      Endpoint Descriptor:                               
        bLength                 7                        
        bDescriptorType         5                        
        bEndpointAddress     0x82  EP 2 IN               
        bmAttributes            1                        
          Transfer Type            Isochronous           
          Synch Type               None                  
          Usage Type               Data                  
        wMaxPacketSize     0x0280  1x 640 bytes          
        bInterval               1                        
      Endpoint Descriptor:                               
        bLength                 7                        
        bDescriptorType         5                        
        bEndpointAddress     0x83  EP 3 IN               
        bmAttributes            1                        
          Transfer Type            Isochronous           
          Synch Type               None                  
          Usage Type               Data                  
        wMaxPacketSize     0x0001  1x 1 bytes            
        bInterval               1                        
    Interface Descriptor:                                
      bLength                 9                          
      bDescriptorType         4                          
      bInterfaceNumber        0                          
      bAlternateSetting       5                          
      bNumEndpoints           3                          
      bInterfaceClass       255 Vendor Specific Class    
      bInterfaceSubClass    255 Vendor Specific Subclass 
      bInterfaceProtocol    255 Vendor Specific Protocol 
      iInterface              0                          
      Endpoint Descriptor:                               
        bLength                 7                        
        bDescriptorType         5                        
        bEndpointAddress     0x81  EP 1 IN               
        bmAttributes            3                        
          Transfer Type            Interrupt             
          Synch Type               None                  
          Usage Type               Data                  
        wMaxPacketSize     0x0001  1x 1 bytes            
        bInterval               1                        
      Endpoint Descriptor:                               
        bLength                 7                        
        bDescriptorType         5                        
        bEndpointAddress     0x82  EP 2 IN               
        bmAttributes            1                        
          Transfer Type            Isochronous           
          Synch Type               None                  
          Usage Type               Data                  
        wMaxPacketSize     0x0200  1x 512 bytes          
        bInterval               1                        
      Endpoint Descriptor:                               
        bLength                 7                        
        bDescriptorType         5                        
        bEndpointAddress     0x83  EP 3 IN               
        bmAttributes            1                        
          Transfer Type            Isochronous           
          Synch Type               None                  
          Usage Type               Data                  
        wMaxPacketSize     0x0001  1x 1 bytes            
        bInterval               1                        
    Interface Descriptor:                                
      bLength                 9                          
      bDescriptorType         4                          
      bInterfaceNumber        0                          
      bAlternateSetting       6                          
      bNumEndpoints           3                          
      bInterfaceClass       255 Vendor Specific Class    
      bInterfaceSubClass    255 Vendor Specific Subclass 
      bInterfaceProtocol    255 Vendor Specific Protocol 
      iInterface              0                          
      Endpoint Descriptor:                               
        bLength                 7                        
        bDescriptorType         5                        
        bEndpointAddress     0x81  EP 1 IN               
        bmAttributes            3                        
          Transfer Type            Interrupt             
          Synch Type               None                  
          Usage Type               Data                  
        wMaxPacketSize     0x0001  1x 1 bytes            
        bInterval               1                        
      Endpoint Descriptor:                               
        bLength                 7                        
        bDescriptorType         5                        
        bEndpointAddress     0x82  EP 2 IN               
        bmAttributes            1                        
          Transfer Type            Isochronous           
          Synch Type               None                  
          Usage Type               Data                  
        wMaxPacketSize     0x0180  1x 384 bytes          
        bInterval               1                        
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       7
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0100  1x 256 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval               1
Device Status:     0x0000
  (Bus Powered)


---

### Post by sir_cheats_a_lot on 2009-07-06
looks like it is supported,though i could and might entirely be wrong,  otherwise i don't think you'd have even gotten that much output.  looks like you are simply pointing it at the wrong v4l device, if you have more then one video capture device installed. try /dev/video1 or /dev/video2.    otherwise. 
  i predict i'd have a similar problem when i get my webcam, as i have a TV tuner card installed as well(which shows as /dev/video0 on my computer, btw).

---

### Post by anystupidname on 2009-07-06
> **sir_cheats_a_lot said:**
> looks like it is supported,though i could and might entirely be wrong,  otherwise i don't think you'd have even gotten that much output.  looks like you are simply pointing it at the wrong v4l device, if you have more then one video capture device installed. try /dev/video1 or /dev/video2.    otherwise. 
  i predict i'd have a similar problem when i get my webcam, as i have a TV tuner card installed as well(which shows as /dev/video0 on my computer, btw).

Thanks. The only problem is, there are no /dev/vid* anythings and no other v4l devices.

---

