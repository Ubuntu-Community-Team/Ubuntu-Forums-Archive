---
title: "Intel Corporation PRO/Wireless 2200BG"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by mbele3000 on 2009-08-10
Hi I got a dell latitude d610 laptop and well its got the good ol, Intel Corporation PRO/Wireless 2200BG wireless card and blue tooth and well after 2 days of surfing the forums and 2 fresh installs later still nothing!  
 I ran nm-tools and got the following:

 Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        00:00:00:00:00:00

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         100.100.0.12
    Prefix:          24 (200.200.200.0)
    Gateway:         100.100.0.1

    DNS:             24.92.226.40
    DNS:             24.92.226.41


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2200
  State:             disconnected
  Default:           no
  HW Address:        00:00:00:00:00:00

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

  *And that's that I am wanting to use this thing as a door stop but I have such great success installing it on other computers. What to do and help is greatly appreciated!

---

### Post by chili555 on 2009-08-10
> Driver: ipw2200
State: disconnectedI wonder if that means the wireless switch or key combination is switched off. If you manipulate the switch, does the LED turn on and off or flicker? Please open a terminal and do:```
sudo cat /var/log/messages | grep -i rfkill
```Any clues?

---

### Post by mbele3000 on 2009-08-10
I ran that in terminal and nothing happened at all. It knows the card is there but the wireless and the blue tooth are "out to lunch" for some reason. The  most frustrating thing is that this is a old laptop so you would think that their would be some sort of fix! Again any help is greatly appreciated. Any more ideas please and thank you  - thanks Chilli

---

### Post by chili555 on 2009-08-11
Did you check to be sure that wireless and bluetooth are _both_ enabled in the BIOS. In my laptop, if the bluetooth is disabled in the BIOS, the wireless doesn't work. Also, please try:```
sudo rmmod -f ipw2200
sudo modprobe ipw2200 bt_coexist=1
```If that does it, we will need to take additional steps to make it permanent. Also, please post:```
dmesg | grep 2200
```Thanks.

---

