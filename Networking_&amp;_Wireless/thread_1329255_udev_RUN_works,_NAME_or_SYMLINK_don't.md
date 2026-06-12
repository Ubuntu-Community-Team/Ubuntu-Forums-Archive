---
title: "udev RUN works, NAME or SYMLINK don't"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by jbernardo on 2009-11-17
Hi,
Trying to get my Huawei E1692 to work with karmic, I ended up installing the Huawei MobilePartner software provided by my ISP (Tim Italia). It works, in that the modem now gets properly detected and ppp works, but the MobilePartner software itself compains that can't detect the modem. Trying to find out why, I ended up by finding that the udev rules installed by the Huawei software work if I use them to run a command, and don't work if I want to do a symlink or change a device name. A example:
```
BUS=="usb", SYSFS{modalias}=="usb:v12D1p140C*", KERNEL=="ttyUSB*", SYSFS{bInterfaceNumber}=="00", SYSFS{bInterfaceProtocol}=="ff", NAME="ttyUSB_utps_modem"

```
This rule doesn't work, and "udevadm test /bus/usb-serial/devices/ttyUSB0" doesn't detect it. But if I change it to:
```
BUS=="usb", SYSFS{modalias}=="usb:v12D1p140C*", KERNEL=="ttyUSB*", SYSFS{bInterfaceNumber}=="00", SYSFS{bInterfaceProtocol}=="ff", RUN+="/usr/local/bin/makelink0.sh"
```
then it gets detected by udevadm test, and the script in /usr/local/bin/makelink0.sh gets executed when I insert the key.
Any ideas on what is wrong here?
Here is the output of "udevadm info -a -p/devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1:1.0/ttyUSB0"
```
Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device     
found, all possible attributes in the udev rules key format.         
A rule to match, can be composed by the attributes of the device     
and the attributes from one single parent device.                    

  looking at device '/devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1:1.0/ttyUSB0':
    KERNEL=="ttyUSB0"                                                           
    SUBSYSTEM=="usb-serial"                                                     
    DRIVER=="option1"                                                           
    ATTR{port_number}=="0"                                                      

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1:1.0':
    KERNELS=="1-1:1.0"                                                         
    SUBSYSTEMS=="usb"                                                          
    DRIVERS=="option"                                                          
    ATTRS{bInterfaceNumber}=="00"                                              
    ATTRS{bAlternateSetting}==" 0"                                             
    ATTRS{bNumEndpoints}=="03"                                                 
    ATTRS{bInterfaceClass}=="ff"                                               
    ATTRS{bInterfaceSubClass}=="ff"                                            
    ATTRS{bInterfaceProtocol}=="ff"                                            
    ATTRS{modalias}=="usb:v12D1p140Cd0000dc00dsc00dp00icFFiscFFipFF"           
    ATTRS{supports_autosuspend}=="0"                                           

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1/1-1':
    KERNELS=="1-1"                                                     
    SUBSYSTEMS=="usb"                                                  
    DRIVERS=="usb"                                                     
    ATTRS{configuration}=="Huawei   Configuration"                     
    ATTRS{bNumInterfaces}==" 6"                                        
    ATTRS{bConfigurationValue}=="1"                                    
    ATTRS{bmAttributes}=="e0"                                          
    ATTRS{bMaxPower}=="500mA"                                          
    ATTRS{urbnum}=="39340"                                             
    ATTRS{idVendor}=="12d1"                                            
    ATTRS{idProduct}=="140c"                                           
    ATTRS{bcdDevice}=="0000"                                           
    ATTRS{bDeviceClass}=="00"                                          
    ATTRS{bDeviceSubClass}=="00"                                       
    ATTRS{bDeviceProtocol}=="00"                                       
    ATTRS{bNumConfigurations}=="1"                                     
    ATTRS{bMaxPacketSize0}=="64"                                       
    ATTRS{speed}=="480"                                                
    ATTRS{busnum}=="1"                                                 
    ATTRS{devnum}=="44"                                                
    ATTRS{version}==" 2.00"                                            
    ATTRS{maxchild}=="0"                                               
    ATTRS{quirks}=="0x0"                                               
    ATTRS{authorized}=="1"                                             
    ATTRS{manufacturer}=="HUAWEI Technology"                           
    ATTRS{product}=="HUAWEI Mobile"                                    

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1':
    KERNELS=="usb1"                                                
    SUBSYSTEMS=="usb"                                              
    DRIVERS=="usb"                                                 
    ATTRS{configuration}==""                                       
    ATTRS{bNumInterfaces}==" 1"                                    
    ATTRS{bConfigurationValue}=="1"                                
    ATTRS{bmAttributes}=="e0"                                      
    ATTRS{bMaxPower}=="  0mA"                                      
    ATTRS{urbnum}=="1214"                                          
    ATTRS{idVendor}=="1d6b"                                        
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="8"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.31-15-lpia ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.7"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7':
    KERNELS=="0000:00:1d.7"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x8117"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{subsystem_device}=="0x83ce"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="19"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{modalias}=="pci:v00008086d00008117sv00001043sd000083CEbc0Csc03i20"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""
    ATTRS{companion}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```

Any ideas?

---

### Post by aksonlyaks on 2010-10-22
hello jbernardo, 
same problem i was also facing while allocating numbers to my modem, after googling a bit what i found that udev does not traverse through the parent nodes itself. so as a modification your udev libnes can be like
```
BUS=="usb", SUBSYSTEMS=="usb", SYSFS{modalias}=="usb:v12D1p140C*", SYSFS{bInterfaceNumber}=="00", SYSFS{bInterfaceProtocol}=="ff", SYSFS{../idVendor}=="12d1", SYSFS{../idProduct}=="140c", NAME="ttyUSB_utps_modem"
```

i think it should work now...

---

