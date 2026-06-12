---
title: "Double gateway"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by SamLef on 2010-03-05
[FONT=Consolas][SIZE=3]Hi,[/SIZE][/FONT]
 
[FONT=Consolas][SIZE=3]Can anyone tell me how I can avoid that both interfaces (fixed and wireless) cause a double default gateway after startup? In that case, i don't have wan-connectivity. When i shutdown the wlan0 interface and it bring up again, the problem is solved. Why? I don't think that I always have to repeat this procedure after every startup.[/SIZE][/FONT]
 
[FONT=Consolas][SIZE=3]The fixed interface eth0 is manual configured and the wifi wlan0 uses dhcp with ath5k and wpa_supplicant.[/SIZE][/FONT]
[SIZE=3][FONT=Consolas]I recently uninstalled network-manager because it was always conflicting with wpa_supplicant. [/FONT][/SIZE]
 
```

[FONT=Courier New][SIZE=2]sam@Alix3d3:~$ netstat -r[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Kernel IP routing table[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]192.168.2.0     *               255.255.255.0   U         0 0          0 eth0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]192.168.2.0     *               255.255.255.0   U         0 0          0 wlan0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]link-local      *               255.255.0.0     U         0 0          0 eth0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]default         192.168.2.1     0.0.0.0         UG        0 0          0 eth0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]default         192.168.2.1     0.0.0.0         UG        0 0          0 wlan0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]sam@Alix3d3:~$ sudo ifconfig wlan0 down [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]sam@Alix3d3:~$ sudo ifconfig wlan0 up [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]sam@Alix3d3:~$ netstat -r Kernel IP routing table[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]192.168.2.0     *               255.255.255.0   U         0 0          0 eth0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]192.168.2.0     *               255.255.255.0   U         0 0          0 wlan0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]link-local      *               255.255.0.0     U         0 0          0 eth0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]default         192.168.2.1     0.0.0.0         UG        0 0          0 eth0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]sam@Alix3d3:~$[/SIZE][/FONT]

```
 
[FONT=Consolas][SIZE=3]Kind regards,[/SIZE][/FONT]
[SIZE=3][FONT=Consolas]Sam [/FONT][/SIZE]

---

