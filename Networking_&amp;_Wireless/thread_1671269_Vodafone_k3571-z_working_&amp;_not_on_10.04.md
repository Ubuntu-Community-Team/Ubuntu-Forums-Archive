---
title: "Vodafone k3571-z working &amp; not on 10.04"
date: 2011-01-19
forum: Networking &amp; Wireless
---

### Post by Jack44 on 2011-01-19
Been trying to get the Vodafone K3571-z 3g pre-paid mobile broadband usb dongle working on Ubuntu 10.04. For a couple of days could not even get it recognized. Eventually found that Sakis3g

[www.sakis3g.org]("http://www.sakis3g.org")

was able to get me a connection, although I had registered the k3571-z on Windows XP beforehand. 
The sakis3g connection is consistent and seems to cause no other problems.
I would recommend that anyone experiencing the same problem try sakis3g first. In this case a search of the forums may not be a good idea, as mobile broadband technologies are evolving daily and even recent posts contain solutions not relevant to the k3571-z. Please let me know if I am wrong on this, but I am hoping to save other users a lot of time and frustration. 

Incidentally I feel I should mention that for me Betavine Connection Manager did not work, was a pain to install, had many dependencies not mentioned on their webpage, and once installed, it simply loaded up then just disappeared. It was complicated to clean up, so I just re-installed Ubuntu.

Once I had a working internet connection I downloaded and installed all recommended Ubuntu updates, and after that my Vodafone connection started to show up in Network Connections list, and was able to connect without sakis3g - sometimes.

If someone has the time I would like some help in tracking why this native connection is intermittent

some of the symptoms are

- it generally connects after a reboot, but only if I reboot from Ubuntu, and not from the Windows XP partition, and not when switching the computer on for the first time

- after a reboot the virtual CD from the k3571-z doesn't show up, and this is when Ubuntu seems to have recognised it as a modem and connects without a problem

- in the case that the modem is not recognised, running "lsusb" shows that the dongle had actually been switched over to modem mode ie it's number is 1010 ( it is 1009 in virtual CD mode)

- if the connection is not established on the first try, it won't connect on the second third fourth fifth etc.
- the first failed connection takes about half a minute, subsequent attempts fail immediately. 

- after failed connections, physically disconnecting/reconnecting modem, waiting for the virtual cd to show up, then ejecting it can get the modem to show up and connect -sometimes.

- the above refers to the native Ubuntu network connections and not sakis3g which pretty much connects consistently.

- from the log it looks like four different usb ports have been recognised as a modem

Jan 20 10:32:11 kernel: [   12.644347] USB Serial support registered for GSM modem (1-port)
Jan 20 10:32:11 kernel: [   12.644642] option 2-2:1.0: GSM modem (1-port) converter detected
Jan 20 10:32:11 kernel: [   12.644845] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
Jan 20 10:32:11 kernel: [   12.644869] option 2-2:1.1: GSM modem (1-port) converter detected
Jan 20 10:32:11 kernel: [   12.645042] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
Jan 20 10:32:11 kernel: [   12.645064] option 2-2:1.2: GSM modem (1-port) converter detected
Jan 20 10:32:11 kernel: [   12.645235] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
Jan 20 10:32:11 kernel: [   12.645258] option 2-2:1.3: GSM modem (1-port) converter detected
Jan 20 10:32:11 kernel: [   12.645464] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB3
Jan 20 10:32:11 kernel: [   12.645487] option 2-2:1.4: GSM modem (1-port) converter detected
Jan 20 10:32:11 kernel: [   12.645672] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB4
Jan 20 10:32:11 kernel: [   12.645708] usbcore: registered new interface driver option
Jan 20 10:32:11 kernel: [   12.645710] option: v0.7.2:USB Driver for GSM modems

This was the log from the boot after a restart (Ubuntu to Ubuntu), once connected the connection information said that the modem was attached to ttyUSB3.

My main question is, which programs are involved in getting the modem recognized and connected? This is my first experience with Linux, but am prepared to reading, learn and experiment, just need a few  pointers in the right direction. Any help appreciated.

---

### Post by ukch on 2011-02-08
When you first plug it in in Linux, it will see it as a CD drive - running 'sudo eject /dev/sr1' will cause the fake CD to disappear and be replaced by the modem. Hope that helps somewhat!

---

### Post by Red_Acid on 2011-02-08
Man... I really, REALLY know that feeling! :-# I've passed through all those symptoms you described and about a month ago, I've found Sakis3G and it was the Oasis I was needing!

I'm sure this thread will help a lot of folks, at least, until something gets solved out-of-the-box (whether it's kernel, network-manager or 'whatever' related). So, it's an **awesome thread** to let everyone (who's in need of something like this) know about it! Thanks for that! ;)

---

### Post by alexfish on 2011-02-08
in your quest here are 3 areas  look at 
HAL UDEV and SYS/BUS

can also google HAL and UDEV to see some of what lays ahead for Linux

these two bits of code : will direct the output to your home directory, they are quite long

```
lshal > `pwd`/lshalinfo
```
```
udevadm info --export-db > `pwd`/udevinfo
```

for the /sys/bus/usb/devices/ have pre-prepared a script, to save getting in a tangle
**edit the ID's according to the device from the lsusb command:this will save a man hunt**

have put wish window to hold the terminal , to save sh,ing the file , or in absence of apt-runner
```
#!/bin/sh
# the next line restarts using wish\
exec wish "$0" "$@"
    ################################
    # NO PROCS
    #   Set ids and paths
    global voda
    set voda            0
# EDIT THE TWO IDS Vendor and Product : assumed device is switched : 
    set Vendor "19d2"
    set Product "0031"
    set vodafone_ID "$Vendor:$Product"     
    set dir "/sys/bus/usb/devices/"
    puts "Searching Dir $dir"
    set devices [ glob -nocomplain -directory $dir *]
    #set dev [llength $devices]
    #set devices [lreplace $devices 0 0]
    ###############################
    # check vendor exist infile + check ids
    #-*
    foreach device $devices {
        puts $device
        set count 0
        set more [ glob -nocomplain -directory $device *]
        #--*
        foreach mdevice $more {
            incr count
            set checkvendor [string first {idVendor} $mdevice]
            #---*
            if {$checkvendor > -1 } {
                set vend [open $mdevice r]
                set idVendor [read $vend]
                set idVendor [string trim $idVendor]
                close $vend
                #----*                                
                if {$idVendor == $Vendor } {
                    set prodpath "$device/idProduct"
                    set prod [open $prodpath r]
                    set idProduct [read $prod]
                    set idProduct [string trim $idProduct]
                    set deviceVend "$idVendor:$idProduct"
                    close $prod
                    #-----*
                    if {$vodafone_ID == $deviceVend} {
                        set voda             1
                        puts "Directory of Vodafone Device $vodafone_ID $device"
                        set wild [string trim $device $dir]
                        puts $wild
                        set dirs_inf [ glob -nocomplain -directory $dir $wild*]
                        puts "Start Stats"
                        foreach inf $dirs_inf {
                            set dirs_inf [ glob -nocomplain -directory $inf *]
                            foreach infos $dirs_inf {puts $infos}
                        }
                        
                    }
                }
            }
        }
    }
#-----*
############################################
# if exist then get the bits
############################################
if {$voda} {
    puts "DONE"
    } else {
    puts "Device $vodafone_ID does not exist"
    }
#############################################
```

the outputs will give indication of the where on the system your device is . then look up
each one to find the info,

another command is modinfo <module>

see if the  script "usb-devices" on system
```
usb-devices
```the listing may indicate the driver , to find the info about the driver
example of option driver
```
modinfo option
```the driver may also be found in all of the previous methods.
then have a look at the sakis3g script , then reason to why sakis3g is sakis3g
to highlight one  area not mentioned, plug-ins , although sakis3g , has this facility

---

### Post by ukch on 2011-02-10
I've found the root of the problem - once the modem is recognised as a modem, it creates 5 /dev/ttyUSBX devices. Ubuntu assumes that ttyUSB1 is the modem, but the modem is actually ttyUSB3. I will try and find the right config file to change and post it here.

---

