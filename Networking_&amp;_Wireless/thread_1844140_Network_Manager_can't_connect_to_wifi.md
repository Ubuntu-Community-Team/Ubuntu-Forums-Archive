---
title: "Network Manager can't connect to wifi"
date: 2011-09-14
forum: Networking &amp; Wireless
---

### Post by Oliviakrk on 2011-09-14
Hi 

I would like to have truly minimal system. I decided to install ubuntu 10.10 netinstall with openbox.

Of course, I have problem with wifi. I installed network-manager-gnome, but it is not working. I have tint2(minimalistic panel with notification area). When i start network manager with command nm-applet it normally shows in tray, but It can't connect to wireless network. I tried to remove /etc/NetworkManager but I didn't help. 
Error:
```


** (nm-applet:1272): WARNING **: <WARN>  activate_connection_cb(): Connection activation failed: No user settings service available

```

While wired network works flawlessly. 

Anyone knows what to do??

```


sudo iwlist wlan0 scanning
[sudo] password for olivia: 
wlan0     Scan completed :
          Cell 01 - Address: D8:5D:4C:FA:0A:E4
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"Olivia's Private Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000027384ec18e
                    Extra: Last beacon: 260ms ago
                    IE: Unknown: 00184F6C6976696127732050726976617465204E6574776F726B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: DD730050F204104A00011010440001021041000100103B0001031047001074ACE768B14AC4AA5B5B709E659FC6221021000754502D4C494E4B1023000754502D4C494E4B1024000631323334353610420004313233341054000800060050F20400011011000954442D57383936304E100800020088
                    IE: Unknown: DD090010180201F4050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001300000000000000000000000000000000000000

```

My system:
Maverick, amd64, netinstall, kernel 3.0

```


03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)


```

---

### Post by praseodym on 2011-09-14
With kernel 3 you can try a module parameter for this device:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rf ath9k
sudo modprobe -v ath9k
sudo service network-manager restart
```
Sometimes "blanks" in the ESSID cause problems, too. Dont remove the network-manager config files, you may want to reinstall the NM:

```
sudo apt-get install --reinstall network-manager network-manager-gnome
```

---

### Post by Oliviakrk on 2011-09-14
I did everything as you listed, I even changed the name of my network to elimate whitespaces - but still there is no difference.

All the time:
```


nm-applet
** Message: applet now removed from the notification area
** Message: applet now embedded in the notification area
** (nm-applet:1391): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1391): DEBUG: old state indicates that this was not a disconnect 0

** (nm-applet:1391): WARNING **: <WARN>  activate_connection_cb(): Connection activation failed: No user settings service available

** (nm-applet:1391): DEBUG: old state indicates that this was not a disconnect 2
** (nm-applet:1391): DEBUG: foo_client_state_changed_cb
** (nm-applet:1391): DEBUG: foo_client_state_changed_cb
^@** (nm-applet:1391): DEBUG: foo_client_state_changed_cb
** (nm-applet:1391): DEBUG: going for offline with icon: notification-network-ethernet-disconnected

** (nm-applet:1391): WARNING **: <WARN>  activate_connection_cb(): Connection activation failed: No user settings service available

** (nm-applet:1391): DEBUG: going for offline with icon: notification-network-ethernet-disconnected

** (nm-applet:1391): WARNING **: <WARN>  activate_connection_cb(): Connection activation failed: No user settings service available


** (nm-applet:1391): WARNING **: <WARN>  activate_connection_cb(): Connection activation failed: No user settings service available

** (nm-applet:1391): DEBUG: old state indicates that this was not a disconnect 2
** (nm-applet:1391): DEBUG: foo_client_state_changed_cb

```

---

