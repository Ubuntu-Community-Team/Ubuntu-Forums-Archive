---
title: "usb_modeswitch (Oneiric , Natty )"
date: 2011-10-30
forum: Networking &amp; Wireless
---

### Post by alexfish on 2011-10-30
as mentioned in most of my bugs and workarounds "There is no specific fix for these devices at "kernel-level" so can only suggest

**Read All**

to configure usb_modeswitch for devices not listed in the original tar.gz file Look at this older post
**Re: Natty, known bugs, fixes and work arounds Post :   ** #[**30**]("http://ubuntuforums.org/showpost.php?p=10793568&postcount=30")
with a reference to "5. check the device_reference.txt"


Upgrading usb_modeswitch from other sources (esp latest debian): Don't Do It : your system may break : if have done so . and system is broken
 
Reinstall the original Ubuntu packages if necessary download onto usb_stick : need usb-modeswitch + usb-modswitch-data

If I see further posts on Upgrading usb_modswitch from external sources then a request will be made, "Guess The Request"

if your system is broken and can't connect try using the disk utility to "safely remove or eject".see what happens

there is a script at the foot of this page which will look for such a device and eject it (not safely remove)
the output will also list the parts which udev sees it may help with writing rules. Please read through

[How To : Mobile Broadband Connections [ Ubuntu 10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490") 

sakis3g may help with problematic devices (devices not hot plugging or device storage problems {look in the log files}, it is easy to spot )most of these bugs have been reported , look at the launchpad bugs ::yet

sakis3g will not work either : Reason

sakis3g looks in the /etc/usb_modeswitch.d

to get sakis3g working

from the terminal
```
sudo su
cd /etc/usb_modeswitch.d
tar xvf /usr/share/usb_modeswitch/configPack.tar.gz
```[*Sakis3G* - All-in-one script]("http://www.google.co.uk/url?sa=t&rct=j&q=sakis3g&source=web&cd=1&sqi=2&ved=0CBsQFjAA&url=http%3A%2F%2Fwww.sakis3g.org%2F&ei=mmutTvjXCcnK8gOutLSUCw&usg=AFQjCNFR0OA7GJQY3djYswddHkMjARyyDw&cad=rja")

Please Read through the Sakis3g Wiki as to it's usage from the commandline powers

If your device not switching Look to usb_modeswitch forum
[ModeSwitchForum]("http://www.draisberghof.de/usb_modeswitch/bb/")

the script
```
#!/bin/sh
# the next line restarts using tclsh \
exec tclsh "$0" "$@"

#############################

proc udevadm-sr {bit  bNumInterfaces} {    
    if { [catch {set udevadm_sr [exec udevadm info -a path -n /dev/$bit]} fid] } {
        puts $fid
        return
    } else {
        set cmds [split $udevadm_sr "\n"]
        foreach cmd $cmds {
            set cmd [string trim $cmd]
            puts ": $cmd"
            if {$bNumInterfaces == $cmd} {
                puts "ejecting $bit"
                set eject [exec eject $bit]
            }
                
        }

        }
        unset udevadm_sr
    return
}
proc eject_sr {} {
# set all the rules to look for
set bNumInterfaces "ATTRS{bNumInterfaces}=="
set bnum {" 1"}
set bNumInterfaces "$bNumInterfaces$bnum"

set dolist 1
    if { [catch {set List [exec ls -l /dev/disk/by-id]} fid] } {
        puts "$fid\n"
        return
    } else {
        puts "/dev/disk/by-id:\n\n$List\n"
        }
    #########################
    # parse device : sr*
    if {$dolist == 1} {
        set len [llength $List]
    foreach bit $List {
        set usb [string first {usb} $bit]
            if {$usb > -1} {
                puts "--------- Udevadm device info-------\n\n"
                puts "--$bit: "
            }

        set srbit [string first {sr} $bit]
            if {$srbit > -1} {
            set bit [string range $bit $srbit end]
            set udevsrbit "/dev/$bit"
            puts "$udevsrbit\n"
## for each sr* get the udev info
            udevadm-sr $bit $bNumInterfaces
            }
    }
  }
}
eject_sr
```alexfish

---

### Post by alexfish on 2011-11-10
have done a follow up of this thread at

[How To : Mobile Broadband Connections [ Ubuntu 11.04 : 10.10 : 10.04 : 9.10]]("http://ubuntuforums.org/showthread.php?t=1466490") 

POST #59 and #60

alexfish

---

