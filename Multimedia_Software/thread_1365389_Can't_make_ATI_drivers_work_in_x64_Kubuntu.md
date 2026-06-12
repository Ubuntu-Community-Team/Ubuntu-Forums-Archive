---
title: "Can't make ATI drivers work in x64 Kubuntu"
date: 2009-12-27
forum: Multimedia Software
---

### Post by kemra on 2009-12-27
I have just put together a new machine with a ATI Radeon HD 4770 GPU. However I am having some problems getting it running.

Firstly Jockey doesn't work, it says the driver is not in use, but when I click Activate the driver name greys out and nothing happens.

I tried installing via the instructions here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#preview](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#preview) to download through the AMD website.

When running "fglrxinfo" it showed the Mesa drivers still in use so I rebooted. After rebooting and running "fglrxinfo" again I got the following message:

```
danny@cybertron:~$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16
```

I tried purging all ati related packages including the open source drivers and then reinstalling the "xorg-driver-fglrx" package from the command line. However that immediately gave me the same error as above. 

I have tried a few things I have seen on the web but nothing has worked so far.

One suggestion was:

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
aticonfig --initial
```

However there are two problems with this, if I run the first command I get:

```
danny@cybertron:~$ mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
mv: cannot stat `/etc/X11/xorg.conf': No such file or directory
```

And if I run the second command I get:

```
danny@cybertron:~$ aticonfig --initial
aticonfig: No supported adapters detected

```

Here is an extract from my /var/log/Xorg.0.log:

```
(II) Loading sub module "int10"                                         
(II) LoadModule: "int10"                                                
(II) Reloading /usr/lib/xorg/modules//libint10.so                       
(II) VESA(0): initializing int10                                        
(II) VESA(0): Primary V_BIOS segment is: 0xc000                         
(II) VESA(0): VESA BIOS detected                                        
(II) VESA(0): VESA VBE Version 3.0                                      
(II) VESA(0): VESA VBE Total Mem: 16384 kB                              
(II) VESA(0): VESA VBE OEM: ATI ATOMBIOS                                
(II) VESA(0): VESA VBE OEM Software Rev: 12.13                          
(II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) VESA(0): VESA VBE OEM Product: JUNIPER                             
(II) VESA(0): VESA VBE OEM Product Rev: 01.00                           
(II) VESA(0): virtual address = 0x7fd031cdb000,                         
        physical address = 0xd0000000, size = 16777216                  
(II) VESA(0): Setting up VESA Mode 0x124 (1280x1024)                    
(II) VESA(0): VBESetVBEMode failed...Tried again without customized values.
(==) VESA(0): Default visual is TrueColor                                  
(==) VESA(0): Backing store disabled                                       
(II) VESA(0): DPMS enabled                                                 
(==) RandR enabled                                                         
(II) Initializing built-in extension Generic Event Extension               
(II) Initializing built-in extension SHAPE                                 
(II) Initializing built-in extension MIT-SHM                               
(II) Initializing built-in extension XInputExtension                       
(II) Initializing built-in extension XTEST                                 
(II) Initializing built-in extension BIG-REQUESTS                          
(II) Initializing built-in extension SYNC                                  
(II) Initializing built-in extension XKEYBOARD                             
(II) Initializing built-in extension XC-MISC                               
(II) Initializing built-in extension SECURITY                              
(II) Initializing built-in extension XINERAMA                              
(II) Initializing built-in extension XFIXES                                
(II) Initializing built-in extension RENDER                                
(II) Initializing built-in extension RANDR                                 
(II) Initializing built-in extension COMPOSITE                             
(II) Initializing built-in extension DAMAGE                                
(EE) GLX error: Can not get required symbols.                              
(II) config/hal: Adding input device AT Translated Set 2 keyboard          
(II) LoadModule: "evdev"                                                   
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so                     
(II) Module evdev: vendor="X.Org Foundation"                               
        compiled for 1.6.4, module version = 2.2.5                         
        Module class: X.Org XInput Driver                                  
        ABI class: X.Org XInput driver, version 4.0                        
(**) AT Translated Set 2 keyboard: always reports core events              
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"             
(II) AT Translated Set 2 keyboard: Found keys                              
(II) AT Translated Set 2 keyboard: Configuring as keyboard                 
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)                                                                       
(**) Option "xkb_rules" "evdev"                                                 
(**) Option "xkb_model" "pc105"                                                 
(**) Option "xkb_layout" "gb"                                                   
(II) config/hal: Adding input device Power Button                               
(**) Power Button: always reports core events                                   
(**) Power Button: Device: "/dev/input/event1"                                  
(II) Power Button: Found keys                                                   
(II) Power Button: Configuring as keyboard                                      
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)       
(**) Option "xkb_rules" "evdev"                                                 
(**) Option "xkb_model" "pc105"                                                 
(**) Option "xkb_layout" "gb"                                                   
(II) config/hal: Adding input device Power Button                               
(**) Power Button: always reports core events                                   
(**) Power Button: Device: "/dev/input/event0"                                  
(II) Power Button: Found keys                                                   
(II) Power Button: Configuring as keyboard                                      
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)       
(**) Option "xkb_rules" "evdev"                                                 
(**) Option "xkb_model" "pc105"                                                 
(**) Option "xkb_layout" "gb"                                                   
(II) config/hal: Adding input device Macintosh mouse button emulation           
(**) Macintosh mouse button emulation: always reports core events               
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"              
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device PS/2+USB Mouse
(**) PS/2+USB Mouse: always reports core events
(**) PS/2+USB Mouse: Device: "/dev/input/event4"
(II) PS/2+USB Mouse: Found 3 mouse buttons
(II) PS/2+USB Mouse: Found x and y relative axes
(II) PS/2+USB Mouse: Found scroll wheel(s)
(II) PS/2+USB Mouse: Configuring as mouse
(**) PS/2+USB Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2+USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2+USB Mouse" (type: MOUSE)
(**) PS/2+USB Mouse: (accel) keeping acceleration scheme 1
(**) PS/2+USB Mouse: (accel) filter chain progression: 2.00
(**) PS/2+USB Mouse: (accel) filter stage 0: 20.00 ms
(**) PS/2+USB Mouse: (accel) set acceleration profile 0
(II) PS/2+USB Mouse: initialized for relative axes.
danny@cybertron:~$ cat /var/log/Xorg.0.log | grep fglrx
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
```

Any ideas how to proceed with this one?

---

### Post by lanec42 on 2009-12-31
Similar issues here. Using an ATI Radeon X1270 on Kubuntu 9.10 _x86_. Using aticonfig --initial yields "aticonfig: No supported adapters detected".

Also,
```
lanec42@lane:~$ fglrxinfo
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!
```

and xorg.conf doesn't exist for me either. (I don't think xorg.conf has been present in any recent (K)Ubuntu releases - I think RandR makes it unnecessary?)

This is frustrating, but I really want mah fglrx! Anyone solved this?

---

