---
title: "Video (Nvidia) Fuzzy Problem"
date: 2007-08-28
forum: Multimedia &amp; Video
---

### Post by teutatis on 2007-08-28
Pls help I don't want to switch back to windows :( 

My Hardware
HP Pavilion dv6545ea 
AMD 64 2x1.8 
2 Gig Ram 
nVidia GeForce Go 7150M 

IMHO It's not a drivers problem because I get the same screen with the nvidia apt-get drivers with the drivers from the nvidia website and even if I'm using the VESA driver. 
I have this Problem with 7.04 and with 7.10 beta too. 

The Problem is, while working I suddenly get this screen. 
[IMG]http://hits-for-kids.at/linux/fehler.jpg[/IMG]

The only cure is to make a hard reboot because if I do the: 
<ctr>+<alt>+<backspace> restart the xserver the screen pops up with the same error. 
And it isn't a special program or event. 

Sometimes I surf the web, edit a file with Kate or copy some data with nautilus. 

It isn't a special time. Sometime the computer works for 5 minutes and sometimes I can work for 20 minutes or more. 

My syslog: 
[PHP]Aug 28 00:59:37 cerberus-laptop avahi-autoipd(eth1)[9628]: SIOCSIFFLAGS failed: No such file or directory
Aug 28 01:01:34 cerberus-laptop firmware_helper[9712]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:03:00.0' with driver '(unknown)'
Aug 28 01:01:34 cerberus-laptop kernel: [  898.072000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Aug 28 01:01:39 cerberus-laptop NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device eth1: No such device 
Aug 28 01:03:39 cerberus-laptop firmware_helper[9784]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:03:00.0' with driver '(unknown)'
Aug 28 01:03:39 cerberus-laptop kernel: [ 1022.252000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Aug 28 01:03:43 cerberus-laptop NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device eth1: No such device 
Aug 28 01:05:43 cerberus-laptop firmware_helper[9966]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:03:00.0' with driver '(unknown)'
Aug 28 01:05:43 cerberus-laptop kernel: [ 1146.632000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Aug 28 01:05:48 cerberus-laptop NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device eth1: No such device 
Aug 28 01:06:06 cerberus-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Aug 28 01:06:06 cerberus-laptop dhclient: send_packet: Network is down
Aug 28 01:06:12 cerberus-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
Aug 28 01:06:12 cerberus-laptop dhclient: send_packet: Network is down
Aug 28 01:06:29 cerberus-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Aug 28 01:06:29 cerberus-laptop dhclient: send_packet: Network is down
Aug 28 01:06:37 cerberus-laptop dhclient: No DHCPOFFERS received.
Aug 28 01:06:37 cerberus-laptop dhclient: No working leases in persistent database - sleeping.
Aug 28 01:06:37 cerberus-laptop firmware_helper[9991]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:03:00.0' with driver '(unknown)'
Aug 28 01:06:37 cerberus-laptop avahi-autoipd(eth1)[9988]: SIOCSIFFLAGS failed: No such file or directory
Aug 28 01:06:37 cerberus-laptop kernel: [ 1200.224000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Aug 28 01:07:48 cerberus-laptop firmware_helper[10151]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:03:00.0' with driver '(unknown)'
Aug 28 01:07:48 cerberus-laptop kernel: [ 1271.624000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Aug 28 01:07:53 cerberus-laptop NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device eth1: No such device 
Aug 28 01:09:01 cerberus-laptop /USR/SBIN/CRON[10625]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Aug 28 01:09:53 cerberus-laptop firmware_helper[10659]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:03:00.0' with driver '(unknown)'
Aug 28 01:09:53 cerberus-laptop kernel: [ 1396.448000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Aug 28 01:09:56 cerberus-laptop NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device eth1: No such device 
Aug 28 01:10:07 cerberus-laptop gdm[6076]: Error reinitilizing server
Aug 28 01:10:38 cerberus-laptop init: tty4 main process (5454) killed by TERM signal
Aug 28 01:10:38 cerberus-laptop init: tty5 main process (5455) killed by TERM signal
Aug 28 01:10:38 cerberus-laptop init: tty2 main process (5457) killed by TERM signal
Aug 28 01:10:38 cerberus-laptop init: tty3 main process (5460) killed by TERM signal
Aug 28 01:10:38 cerberus-laptop init: tty1 main process (5461) killed by TERM signal
Aug 28 01:10:38 cerberus-laptop init: tty6 main process (5462) killed by TERM signal
Aug 28 01:10:43 cerberus-laptop kernel: [ 1446.304000] /dev/vmmon[10820]: Module vmmon: unloaded
Aug 28 01:10:43 cerberus-laptop kernel: [ 1446.356000] bridge-eth1: detached
Aug 28 01:10:44 cerberus-laptop avahi-daemon[6019]: Interface vmnet1.IPv4 no longer relevant for mDNS.
Aug 28 01:10:44 cerberus-laptop avahi-daemon[6019]: Leaving mDNS multicast group on interface vmnet1.IPv4 with address 172.16.131.1.
Aug 28 01:10:44 cerberus-laptop avahi-daemon[6019]: Withdrawing address record for fe80::250:56ff:fec0:1 on vmnet1.
Aug 28 01:10:44 cerberus-laptop avahi-daemon[6019]: Withdrawing address record for 172.16.131.1 on vmnet1.
Aug 28 01:10:47 cerberus-laptop avahi-daemon[6019]: Interface vmnet8.IPv4 no longer relevant for mDNS.
Aug 28 01:10:47 cerberus-laptop avahi-daemon[6019]: Leaving mDNS multicast group on interface vmnet8.IPv4 with address 172.16.58.1.
Aug 28 01:10:47 cerberus-laptop avahi-daemon[6019]: Withdrawing address record for fe80::250:56ff:fec0:8 on vmnet8.
Aug 28 01:10:47 cerberus-laptop avahi-daemon[6019]: Withdrawing address record for 172.16.58.1 on vmnet8.
Aug 28 01:10:48 cerberus-laptop mysqld[6280]: 070828  1:10:48 [Note] /usr/sbin/mysqld: Normal shutdown
Aug 28 01:10:48 cerberus-laptop mysqld[6280]: 
Aug 28 01:10:48 cerberus-laptop mysqld[6280]: 070828  1:10:48  InnoDB: Starting shutdown...
Aug 28 01:10:50 cerberus-laptop mysqld[6280]: 070828  1:10:50  InnoDB: Shutdown completed; log sequence number 0 43655
Aug 28 01:10:50 cerberus-laptop mysqld[6280]: 070828  1:10:50 [Note] /usr/sbin/mysqld: Shutdown complete
Aug 28 01:10:50 cerberus-laptop mysqld[6280]: 
Aug 28 01:10:50 cerberus-laptop mysqld_safe[10945]: ended
Aug 28 01:10:51 cerberus-laptop exiting on signal 15
[/PHP]

my xorg.conf 
[PHP]
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Jun 13 18:39:30 PDT 2007

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "de"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 67.0
    VertRefresh     30.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x800"
    EndSubSection
EndSection

[/PHP]


begging for help

pls

---

### Post by teutatis on 2007-08-28
My Question, if the vesa driver (framebuffer) is bringing me the same error the bug is in the NVIDIA Hardware and not in the driver right? 

I've tried Fedora and Suse and they all bring me the same Error. 
I've called HP Support and they said: "We don't support Linux" 

So I've installed Windows Vista (official supported OS for this computer) and the same problem after 5 - 10  minutes Vista Bluescreen. After rebooting Vista is saying get the latest driver. But I allready have the newest allready installed. 

Called HP Support again: "Pleas wait for the right driver". 
1st I bought the computer to work now not in 6 month and 
2nd I think the problem is not the driver it's the hardeware right? 

Because Linux randomly crashes under vesa driver (framebuffer).

---

### Post by tseliot on 2007-08-29
> **teutatis said:**
> My Question, if the vesa driver (framebuffer) is bringing me the same error the bug is in the NVIDIA Hardware and not in the driver right? 

I've tried Fedora and Suse and they all bring me the same Error. 
I've called HP Support and they said: "We don't support Linux" 

So I've installed Windows Vista (official supported OS for this computer) and the same problem after 5 - 10  minutes Vista Bluescreen. After rebooting Vista is saying get the latest driver. But I allready have the newest allready installed. 

Called HP Support again: "Pleas wait for the right driver". 
1st I bought the computer to work now not in 6 month and 
2nd I think the problem is not the driver it's the hardeware right? 

Because Linux randomly crashes under vesa driver (framebuffer).
if you can reproduce the problem in Windows Vista then it's definitely a hardware issue.

---

### Post by darknss on 2007-12-24
I have the same problem, but i can solve it in vista only when install the official driver for my model  from [www.hp.com](www.hp.com)

in linux maybe  with other version of the driver, but i don't probe that way, today i make some test with the official nvidia driver 169.xx for linux and post my results.

and 1 question........... u are secure the problem its the hardware??............

i have 2 laptops with that graphics card, diferent model, but only 1 have the problem..........
and the second laptop don't have but its more recent, i think that incorporate the newest version of the driver.


PD. sry for my bad english.

greetings form mexico.

---

