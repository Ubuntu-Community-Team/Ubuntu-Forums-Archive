---
title: "Disable / Enable Periodic Wireless Scans"
date: 2013-07-20
forum: Networking &amp; Wireless
---

### Post by anspectrum on 2013-07-20
Hey, 

Ubuntu is 12.04, Wireless card is Built-in Intel (Centrino) 6200G, Laptop Dell E6410.

Problem Description :
Wireless drivers installed either in Ubuntu or Microsoft have a default behavior of scanning for better channel / AP to get connected to. This default behavior induces lag while using realtime applications like Audio / Video calls or online gaming. The lag arises after a lapse of almost 60 seconds (depending upon the card manufacturer and drivers). This lag persists for a couple of seconds.

Diagnosis:
After much searching, I came across to know about the Wireless adapters behavior that is mentioned above. In MS this is overcome by having this utility [http://www.martin-majowski.de/wlanoptimizer/](http://www.martin-majowski.de/wlanoptimizer/)
This utility is verified and works by suppressing the periodic scans, thus applications run pretty smooth.

Solution for Ubuntu Required:
Some more searching and I found this [http://nilvec.com/disable-scanning-in-networkmanager-when-connected.html](http://nilvec.com/disable-scanning-in-networkmanager-when-connected.html)
But the problem is that this solution requires recompiling of the Network Manager (NM) and then using it. If NM is recompiled and installed then Periodic Scanning function will be gone forever. Like in noisy channel conditions WiFi will not switch to more cleaner channels.

I would like to know if this functionality of temporary Disabling / Enabling Periodic Wireless Scans can be achieved in Ubuntu (12.04)? How?

Thankyou

---

### Post by anspectrum2 on 2013-07-31
Posted as "anspectrum"

---

### Post by anspectrum on 2013-07-31
After reading and searching some more, I found out that this functionality of temporarily enabling / disabling WiFi periodic scanning can be achieved like this:

The Network Manager also periodically scans for better channels. Disable it and setup wireless manually. Here is a set of commands that will do the job.

-------------------------------------------------------------------------------------------------------------------

sudo iw dev wlan0 scan                            //Just in case you want to scan available APs

sudo service network-manager stop                    //disable NM services

sudo touch /etc/wpa_supplicant/your-conf-file.conf                //wpa_supplicant conf file used to exchange WPA keys with the AP

sudo wpa_passphrase <SSID> <Password> > /etc/wpa_supplicant/your-conf-file.conf    //command to supply WPA credentials to the conf file

sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant/your-conf-file.conf    //command to associate wlan0 (interface) with the AP

sudo ifconfig wlan0 up                            //command to bring up the wireless interface

sudo dhclient wlan0                            // command if you want IP configuration allocated through DHCP

----------------------------------------------------------------------------------------------------------------
Further details on these commands can be found here:

[https://bbs.archlinux.org/viewtopic.php?id=141414](https://bbs.archlinux.org/viewtopic.php?id=141414)

[https://wiki.archlinux.org/index.php/Wireless_Setup#Manual_setup](https://wiki.archlinux.org/index.php/Wireless_Setup#Manual_setup)

[https://wiki.archlinux.org/index.php/WPA_Supplicant](https://wiki.archlinux.org/index.php/WPA_Supplicant)

[https://wiki.archlinux.org/index.php/Wireless_Setup#Access_point_discovery](https://wiki.archlinux.org/index.php/Wireless_Setup#Access_point_discovery)


Hopefuly this would be helpful to others.:popcorn:

---

### Post by jason71 on 2014-03-20
I had this same problem when streaming from a NAS.  I found a simipler solution was just to prevent NetworkManager from running **after **it had made the initial connection.  You can do this using:

sudo killall -STOP NetworkManager # stop NetworkManager running and auto-scanning

Then when you want to re-enable auto-scan just let it run again:

sudo killall -CONT NetworkManager # let NetworkManager run again


> **anspectrum said:**
> After reading and searching some more, I found out that this functionality of temporarily enabling / disabling WiFi periodic scanning can be achieved like this:

The Network Manager also periodically scans for better channels. Disable it and setup wireless manually. Here is a set of commands that will do the job.

-------------------------------------------------------------------------------------------------------------------

sudo iw dev wlan0 scan                            //Just in case you want to scan available APs

sudo service network-manager stop                    //disable NM services

sudo touch /etc/wpa_supplicant/your-conf-file.conf                //wpa_supplicant conf file used to exchange WPA keys with the AP

sudo wpa_passphrase <SSID> <Password> > /etc/wpa_supplicant/your-conf-file.conf    //command to supply WPA credentials to the conf file

sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant/your-conf-file.conf    //command to associate wlan0 (interface) with the AP

sudo ifconfig wlan0 up                            //command to bring up the wireless interface

sudo dhclient wlan0                            // command if you want IP configuration allocated through DHCP

----------------------------------------------------------------------------------------------------------------
Further details on these commands can be found here:

[https://bbs.archlinux.org/viewtopic.php?id=141414](https://bbs.archlinux.org/viewtopic.php?id=141414)

[https://wiki.archlinux.org/index.php/Wireless_Setup#Manual_setup](https://wiki.archlinux.org/index.php/Wireless_Setup#Manual_setup)

[https://wiki.archlinux.org/index.php/WPA_Supplicant](https://wiki.archlinux.org/index.php/WPA_Supplicant)

[https://wiki.archlinux.org/index.php/Wireless_Setup#Access_point_discovery](https://wiki.archlinux.org/index.php/Wireless_Setup#Access_point_discovery)


Hopefuly this would be helpful to others.:popcorn:

---

### Post by anspectrum on 2014-03-29
> **jason71 said:**
> I had this same problem when streaming from a NAS.  I found a simipler solution was just to prevent NetworkManager from running **after **it had made the initial connection.  You can do this using:

sudo killall -STOP NetworkManager # stop NetworkManager running and auto-scanning

Then when you want to re-enable auto-scan just let it run again:

sudo killall -CONT NetworkManager # let NetworkManager run again

Good Find. =d>

---

