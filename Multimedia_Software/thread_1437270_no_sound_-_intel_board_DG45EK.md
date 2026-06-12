---
title: "no sound - intel board DG45EK"
date: 2010-03-23
forum: Multimedia Software
---

### Post by 007casper on 2010-03-23
I dont have any sound at all.

Everytime I boot the system.  I get a warning to ignore HDA Intel(AD198x Analog)  I say no.  I go to system settings > media picked Audio Output > Music, then picked PulseAudio, click on test... nothing.  I picked HDA, clicked on test.  Nothing.

I picked pulseaudio test, nothing.  Apply.  Logout, then login.  Nothing. Restart computer.  

It said kde forgot the load one of the harddrives ignore HDA Intel(AD198x Analog). I said no.

please, advise.

Thank you.

---

### Post by RedSingularity on 2010-03-23
First remove pulseaudio

sudo apt-get autoremove pulseaudio

---

### Post by 007casper on 2010-03-23
removed... and then

---

### Post by RedSingularity on 2010-03-23
In a terminal type 

alsamixer 

make sure all the levels are up.

---

### Post by 007casper on 2010-03-23
master 100
headphone is off I cant get it to turn on
pcm 100
front 100
front mi 100 
front mi 100
surround 100
center 100
LFE 100
line 100
line-in 100
CD 100
Mic 100

I wonder how I can turn the headphone on besides that one, all levels are up.  Test no sound

---

### Post by RedSingularity on 2010-03-23
Post your output of 

aplay -l

---

### Post by 007casper on 2010-03-23
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by RedSingularity on 2010-03-23
Good now post 

lspci -v

---

### Post by 007casper on 2010-03-23
lspci -v                                          
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
        Subsystem: Intel Corporation Device 1004                                
        Flags: bus master, fast devsel, latency 0                               
        Capabilities: <access denied>                                           
        Kernel driver in use: agpgart-intel                                     
        Kernel modules: intel-agp                                               

00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
        Subsystem: Intel Corporation Device 1004                                                             
        Flags: bus master, fast devsel, latency 0, IRQ 25                                                    
        Memory at d0000000 (64-bit, non-prefetchable) [size=4M]                                              
        Memory at c0000000 (64-bit, prefetchable) [size=256M]                                                
        I/O ports at f220 [size=8]                                                                           
        Capabilities: <access denied>                                                                        
        Kernel driver in use: i915                                                                           
        Kernel modules: i915                                                                                 

00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
        Subsystem: Intel Corporation Device 1004                                                      
        Flags: bus master, fast devsel, latency 0                                                     
        Memory at d0400000 (64-bit, non-prefetchable) [size=1M]                                       
        Capabilities: <access denied>                                                                 

00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
        Subsystem: Intel Corporation Device 1004                                             
        Flags: bus master, fast devsel, latency 0, IRQ 16                                    
        Memory at d0526900 (64-bit, non-prefetchable) [size=16]                              
        Capabilities: <access denied>                                                        
        Kernel driver in use: heci                                                           
        Kernel modules: heci                                                                 

00:03.2 IDE interface: Intel Corporation 4 Series Chipset PT IDER Controller (rev 03) (prog-if 85 [Master SecO PriO])
        Subsystem: Intel Corporation Device 1004                                                                     
        Flags: 66MHz, fast devsel, IRQ 18                                                                            
        I/O ports at f210 [size=8]                                                                                   
        I/O ports at f200 [size=4]                                                                                   
        I/O ports at f1f0 [size=8]                                                                                   
        I/O ports at f1e0 [size=4]                                                                                   
        I/O ports at f1d0 [size=16]                                                                                  
        Capabilities: <access denied>                                                                                

00:03.3 Serial controller: Intel Corporation 4 Series Chipset Serial KT Controller (rev 03) (prog-if 02)
        Subsystem: Intel Corporation Device 1004                                                        
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17                                        
        I/O ports at f1c0 [size=8]                                                                      
        Memory at d0525000 (32-bit, non-prefetchable) [size=4K]                                         
        Capabilities: <access denied>                                                                   
        Kernel driver in use: serial                                                                    

00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
        Subsystem: Intel Corporation Device 1004                                            
        Flags: bus master, fast devsel, latency 0, IRQ 24                                   
        Memory at d0500000 (32-bit, non-prefetchable) [size=128K]                           
        Memory at d0524000 (32-bit, non-prefetchable) [size=4K]                             
        I/O ports at f0e0 [size=32]                                                         
        Capabilities: <access denied>                                                       
        Kernel driver in use: e1000e                                                        
        Kernel modules: e1000e                                                              

00:1a.0 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #4 (rev 02)
        Subsystem: Intel Corporation Device 1004                                                   
        Flags: bus master, medium devsel, latency 0, IRQ 16                                        
        I/O ports at f0c0 [size=32]                                                                
        Capabilities: <access denied>                                                              
        Kernel driver in use: uhci_hcd                                                             

00:1a.1 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #5 (rev 02)
        Subsystem: Intel Corporation Device 1004                                                   
        Flags: bus master, medium devsel, latency 0, IRQ 21                                        
        I/O ports at f0a0 [size=32]                                                                
        Capabilities: <access denied>                                                              
        Kernel driver in use: uhci_hcd                                                             

00:1a.2 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #6 (rev 02)
        Subsystem: Intel Corporation Device 1004                                                   
        Flags: bus master, medium devsel, latency 0, IRQ 18                                        
        I/O ports at f080 [size=32]                                                                
        Capabilities: <access denied>                                                              
        Kernel driver in use: uhci_hcd                                                             

00:1a.7 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20)
        Subsystem: Intel Corporation Device 1004                                                                 
        Flags: bus master, medium devsel, latency 0, IRQ 18                                                      
        Memory at d0526400 (32-bit, non-prefetchable) [size=1K]                                                  
        Capabilities: <access denied>                                                                            
        Kernel driver in use: ehci_hcd                                                                           

00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
        Subsystem: Intel Corporation Device 1004                                              
        Flags: bus master, fast devsel, latency 0, IRQ 22                                     
        Memory at d0520000 (64-bit, non-prefetchable) [size=16K]                              
        Capabilities: <access denied>                                                         
        Kernel driver in use: HDA Intel                                                       
        Kernel modules: snd-hda-intel                                                         

00:1d.0 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #1 (rev 02)
        Subsystem: Intel Corporation Device 1004                                                   
        Flags: bus master, medium devsel, latency 0, IRQ 23                                        
        I/O ports at f060 [size=32]                                                                
        Capabilities: <access denied>                                                              
        Kernel driver in use: uhci_hcd                                                             

00:1d.1 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #2 (rev 02)
        Subsystem: Intel Corporation Device 1004                                                   
        Flags: bus master, medium devsel, latency 0, IRQ 19                                        
        I/O ports at f040 [size=32]                                                                
        Capabilities: <access denied>                                                              
        Kernel driver in use: uhci_hcd                                                             

00:1d.2 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #3 (rev 02)
        Subsystem: Intel Corporation Device 1004                                                   
        Flags: bus master, medium devsel, latency 0, IRQ 18                                        
        I/O ports at f020 [size=32]                                                                
        Capabilities: <access denied>                                                              
        Kernel driver in use: uhci_hcd                                                             

00:1d.7 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20)
        Subsystem: Intel Corporation Device 1004                                                                 
        Flags: bus master, medium devsel, latency 0, IRQ 23                                                      
        Memory at d0526000 (32-bit, non-prefetchable) [size=1K]                                                  
        Capabilities: <access denied>                                                                            
        Kernel driver in use: ehci_hcd                                                                           

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a2) (prog-if 01)
        Flags: bus master, fast devsel, latency 0                           
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32       
        Capabilities: <access denied>                                       

00:1f.0 ISA bridge: Intel Corporation 82801JDO (ICH10DO) LPC Interface Controller (rev 02)
        Subsystem: Intel Corporation Device 1004                                          
        Flags: bus master, medium devsel, latency 0                                       
        Capabilities: <access denied>                                                     
        Kernel modules: iTCO_wdt                                                          

00:1f.2 IDE interface: Intel Corporation 82801JD/DO (ICH10 Family) 4-port SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Intel Corporation Device 1004
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at f1b0 [size=8]
        I/O ports at f1a0 [size=4]
        I/O ports at f190 [size=8]
        I/O ports at f180 [size=4]
        I/O ports at f170 [size=16]
        I/O ports at f160 [size=16]
        Capabilities: <access denied>
        Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801JD/DO (ICH10 Family) SMBus Controller (rev 02)
        Subsystem: Intel Corporation Device 1004
        Flags: medium devsel, IRQ 18
        Memory at d0526800 (64-bit, non-prefetchable) [size=256]
        I/O ports at f000 [size=32]
        Kernel driver in use: i801_smbus
        Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801JD/DO (ICH10 Family) 2-port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
        Subsystem: Intel Corporation Device 1004
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at f150 [size=8]
        I/O ports at f140 [size=4]
        I/O ports at f130 [size=8]
        I/O ports at f120 [size=4]
        I/O ports at f110 [size=16]
        I/O ports at f100 [size=16]
        Capabilities: <access denied>
        Kernel driver in use: ata_piix

---

### Post by RedSingularity on 2010-03-23
Try this in a terminal 

modprobe snd-hda-intel

and check your sound again.

---

### Post by 007casper on 2010-03-23
I really appreciate your help.

I still dont get any sound.

eidt:  I logout- log back in, still dont have any sound

---

### Post by RedSingularity on 2010-03-23
Well it seems ubuntu recognizes your card so apparently the driver is loading.  Are you sure it is not muted anywhere?  Maybe in the BIOS?

---

### Post by 007casper on 2010-03-23
I am going to check the bios.  It is weird.  I got this pop again.

Removed Sound Devices
KDE detected that one or more internal sound devices were removed.
Do you want KDE to permanently forget about these devices?
This is the list of devices KDE thinks can be removed:
Capture: HDA Intel (AD198x Analog) #1

do not ask again for these devices

yes no manage devices

---

### Post by RedSingularity on 2010-03-23
I have never seen a message like that but then again I am a Gnome user.

---

### Post by gizmobay on 2010-03-23
I'm running into the same issue as well. You can issue a 

sudo alsa force-reload

to fix the problem but the downside is you have to do this on every reboot. You'll then get the popup asking to remove about 4 devices when you do the alsa force-reload command.

Anyone know how to fix this without doing the alsa coomand?

---

### Post by RedSingularity on 2010-03-23
> **gizmobay said:**
> I'm running into the same issue as well. You can issue a 

sudo alsa force-reload

to fix the problem but the downside is you have to do this on every reboot. You'll then get the popup asking to remove about 4 devices when you do the alsa force-reload command.

Anyone know how to fix this without doing the alsa coomand?


What about making a startup script so you dont have to enter the command yourself.  It will enter at boot time.

---

### Post by gizmobay on 2010-03-23
Guess you could do that. Don't know how far in the boot process you have to force a reload. Could always add to sudoers and add it to the kde auto start dir. Seems like a tough way to solve an issue though :o

---

### Post by 007casper on 2010-03-23
sound works now.  It still gives me pulseaudio error.  I thought I removed pulseaudio, but I think it reloads on boot.  Due to the error, the computer gives me the pop up error, and then I cant connect to online.  I shutdown, restart, logout-login... still didnt get internet connection.

After several attempts, it seemed that if I wait a while after the pop error message.  Then, load tabbed browsing, then open up firefox it works.  However, if I load firefox first, it doesnt.  It is buggy.

any ideas

---

### Post by 007casper on 2010-03-23
I checked out pulseaudio under software management.  There isnt any app installed for pulseaudio. what is recommended?  There are tons of them.  I am not sure which one is the most suitable app.

I figure maybe that will solve the problem

thank you.

---

### Post by gizmobay on 2010-03-24
I also have gnome installed. No issues with this. Also, I think the sound issues in KDE were preventing me from logging out, shutdown, etc from the start menu. Guess I'll stick with gnome until they sort out the issues in 4.4.1.

---

### Post by 007casper on 2010-03-24
It could be that KDE is buggy.  Sound works now.  However, I still get error pop up.

Thanks everyone.

---

### Post by gizmobay on 2010-03-24
> **gizmobay said:**
> I also have gnome installed. No issues with this. Also, I think the sound issues in KDE were preventing me from logging out, shutdown, etc from the start menu. Guess I'll stick with gnome until they sort out the issues in 4.4.1.

I checked my computer this morning and sound doesn't work in gnome either. Didn't logout or reboot as it just stopped on it's own.

---

