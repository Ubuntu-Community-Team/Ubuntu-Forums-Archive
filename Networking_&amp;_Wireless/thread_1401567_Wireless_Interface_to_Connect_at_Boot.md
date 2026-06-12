---
title: "Wireless Interface to Connect at Boot"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by afrik on 2010-02-08
Hello All

I've got a problem with setting up automatic wireless connection on boot (without using GUI tool). I have got some basic Linux experience from years before wireless wasn't in use yet. Therefore I know how to move around Linux but have not previous exposure to configuring wireless. I hope you can help me with that. 

I've been through various threads and websites and still can't figure it out myself.

I've enclosed some information with my current configuration as that might be usefull. If you need anything else just let me know.


Thanks,
afrik


   NetBook: Toshiba NB100 11R 
    model no. PLL 10E - 00x00ten
      ############
         
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
############   
ath1      Link encap:Ethernet  HWaddr 00:21:63:a1:f3:75                inet6 addr: fe80::221:63ff:fea1:f375/64 Scope:Link
                UP BROADCAST MULTICAST  MTU:1500  Metric:1 

            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 

            collisions:0 txqueuelen:0 
              RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
        

  ath1      IEEE 802.11g  ESSID:"meru-test-local"  Nickname:""
              Mode:Managed  Frequency:2.467 GHz  Access Point: Not-Associated   
              Bit Rate:1 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
              Retry:off   RTS thr:off   Fragment thr:off
              Power Management:off
              Link Quality=0/70  Signal level=-87 dBm  Noise level=-87 dBm
              Rx invalid nwid:238  Rx invalid crypt:0  Rx invalid frag:0
              Tx excessive retries:0  Invalid misc:0   Missed beacon:0
        ############
         
wlan_scan_sta          14720  1 
    wlan                  249968  4 wlan_scan_sta,ath_rate_sample,ath_pci
        ############
        

[   40.107353] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
    [   40.107367] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
    [   40.107390] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
    [   40.107408] wifi0: ath_announce: Use hw queue 1 for WME_AC_BE traffic
    [   40.107415] wifi0: ath_announce: Use hw queue 0 for WME_AC_BK traffic
    [   40.107421] wifi0: ath_announce: Use hw queue 2 for WME_AC_VI traffic
    [   40.107427] wifi0: ath_announce: Use hw queue 3 for WME_AC_VO traffic
    [   40.107434] wifi0: ath_announce: Use hw queue 8 for CAB traffic
    [   40.107440] wifi0: ath_announce: Use hw queue 9 for beacons
    [   40.176953] ath_pci: wifi0: Atheros 5424/2424: mem=0x32100000, irq=23
    [   40.023355] MadWifi: ath_attach: Switching rfkill capability off
    [   40.105953] MadWifi: ath_attach: Switching per-packet transmit power control off
    [   42.962245] udev: renamed network interface ath0 to ath1
    [   53.800261] ath1: no IPv6 routers present
        [   64.723855] ADDRCONF(NETDEV_UP): ath1: link is not ready
[   64.740234] ADDRCONF(NETDEV_CHANGE): ath1: link becomes ready
    [   74.731343] ath1: no IPv6 routers present
        ############
         
  *-network
           description: Ethernet interface
           product: RTL8101E PCI Express Fast Ethernet controller
           vendor: Realtek Semiconductor Co., Ltd.
           physical id: 0
           bus info: pci@0000:01:00.0
           logical name: eth1
           version: 02
             serial: 00:1e:33:7c:99:ed 

         capacity: 1GB/s
             width: 64 bits 

         clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
           configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
   
     *-network 

        description: Wireless interface
             product: AR242x 802.11abg Wireless PCI Express Adapter 

         vendor: Atheros Communications Inc.
             physical id: 0 

         bus info: pci@0000:02:00.0
             logical name: wifi0 

         version: 01
             serial: 00:21:63:a1:f3:75 

         width: 64 bits
             clock: 33MHz 

         capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
           configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
        ############
        

  ath1      Scan completed :
                 Cell 08 - Address: 0E:06:FE:A1:F3:75 

                      ESSID:"meru-test-wpa2"
                        Mode:Master
                          Frequency:2.437 GHz (Channel 6) 

                      Quality=54/70  Signal level=-41 dBm  Noise level=-95 dBm
                          Encryption key:on 

                      Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                                    11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 

                                48 Mb/s; 54 Mb/s
                          Extra:bcn_int=100 

                      IE: IEEE 802.11i/WPA2 Version 1
                              Group Cipher : CCMP 

                          Pairwise Ciphers (1) : CCMP
                              Authentication Suites (1) : PSK 

                      Extra:wme_ie=dd180050f2020101030003a4000027a4000042435e0062322f00
  ############
   
      Description:     Ubuntu 8.04.1
    2.6.24-19-lpia i686
        ############
   
      sudo /etc/init.d/networking restart >> wifi.txt
     [sudo] password for year1: 
         There is already a pid file /var/run/dhclient.ath1.pid with pid 6570
     killed old client process, removed PID file
     Internet Systems Consortium DHCP Client V3.0.6
     Copyright 2004-2007 Internet Systems Consortium.
     All rights reserved.
      For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

   
      wifi0: unknown hardware address type 801 

  wifi0: unknown hardware address type 801
    Listening on LPF/ath1/00:21:63:a1:f3:75
     Sending on   LPF/ath1/00:21:63:a1:f3:75
     Sending on   Socket/fallback
     DHCPRELEASE on ath1 to 192.168.10.2 port 67
     There is already a pid file /var/run/dhclient.ath1.pid with pid 134519072
     Internet Systems Consortium DHCP Client V3.0.6
     Copyright 2004-2007 Internet Systems Consortium.
     
All rights reserved.
     For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
   
      wifi0: unknown hardware address type 801
    wifi0: unknown hardware address type 801
     Listening on LPF/ath1/00:21:63:a1:f3:75
     Sending on   LPF/ath1/00:21:63:a1:f3:75
     Sending on   Socket/fallback
     DHCPDISCOVER on ath1 to 255.255.255.255 port 67 interval 5
     DHCPOFFER of 192.168.10.110 from 192.168.10.2
     DHCPREQUEST of 192.168.10.110 on ath1 to 255.255.255.255 port 67
     DHCPACK of 192.168.10.110 from 192.168.10.2
     bound to 192.168.10.110 -- renewal in 13745 seconds.
            ############


        ctrl_interface=/var/run/wpa_supplicant
          network={ 

              ssid="meru-test-wpa2"
                  scan_ssid=0 

              proto=RSN
                  key_mgmt=WPA-PSK 

                psk="1234567890" 

              pairwise=CCMP
                  group=CCMP 

  }
    ############
   
          #!/bin/sh -e

 #
      # rc.local 

  #
      # This script is executed at the end of each multiuser runlevel. 

  # Make sure that the script will "exit 0" on success or any other
      # value on error. 

  #
      # In order to enable or disable this script just change the execution 

  # bits.
      # 

  # By default this script does nothing.
  

  ifconfig eth1 down 

  ifconfig ath1 down
      dhclient -r ath1 

  iwconfig ath1 essid meru-test-local
      iwconfig ath1 mode Managed 

  ifconfig ath1 up
    dhclient
   
      exit 0
        ############

---

