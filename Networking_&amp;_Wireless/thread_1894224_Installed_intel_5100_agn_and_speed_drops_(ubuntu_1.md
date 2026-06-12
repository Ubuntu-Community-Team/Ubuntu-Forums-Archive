---
title: "Installed intel 5100 agn and speed drops (ubuntu 11.10 64 bit)"
date: 2011-12-12
forum: Networking &amp; Wireless
---

### Post by chuckyanutsup on 2011-12-12
I've just upgraded to an intel 5100 agn wireless card in the hopes of getting a 300n connection. It will say it's at 150Mb/s etc but the actual throughput seems to max out at 3-9MB/s (from my NAS) and sits closer to the 3MB/s mark after it's been connected for some time and has dropped right off once or twice. (which can cause filezilla to time out on me). Any ideas on how I might be able to pull more speed out of it? I've got channel in my router set to auto 1 and wpa2-psk security which seemed fine for my old card.

I've been hunting around the forums for the past few days and found a few things to try
I've disabled ipv6 with 
```
[B]# echo "#disable ipv6" | sudo tee -a /etc/sysctl.conf
# echo "net.ipv6.conf.all.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf
# echo "net.ipv6.conf.default.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf
# echo "net.ipv6.conf.lo.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf[/B]
``` I've also tried

```
# sudo -s "echo 'options iwlagn 11n_disable=0 11n_disable50=0 swcrypto=1 swcrypto50=1' >> /etc/modprobe.d/options.conf" # sudo modprobe -r iwlagn && sudo modprobe iwlagn
```I've added an options.conf file to /etc/modprobe.d/ and added
```
options iwlagn 11n_disable=0
``` to it

I've also tried adding 
```
**options ath9k nohwcrypt=1**
```to /etc/modprobe.d/ath9k.conf

Ok, so tests I've seen requested on other threads are.

```
root@christopher-Satellite-P505:~# lspci -nnk | grep -iA2 net
07:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)
    Subsystem: Toshiba America Info Systems Device [1179:ff50]
    Kernel driver in use: atl1c
--
08:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1211]
    Kernel driver in use: iwlagn

``````
# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11abgn  ESSID:"fetta"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: B0:48:7A:DE:19:98   
          Bit Rate=150 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:657  Invalid misc:2399   Missed beacon:0

``````
# sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: B0:48:7A:DE:19:98
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-27 dBm  
                    Encryption key:on
                    ESSID:"fetta"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001edd17ea1
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 00056665747461
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401051B00000000000000000000000000000000000000
                    IE: Unknown: 3D1601051B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010006004000
                    IE: Unknown: DD850050F204104A0001101044000102103B0001031047001000000000000010000000B0487ADE19981021000754502D4C494E4B1023000B544C2D5752313034334E4410240003312E3010420003312E301054000800060050F20400011011001B576972656C65737320526F7574657220544C2D5752313034334E44100800020086103C000101
          Cell 02 - Address: 00:22:75:A6:1A:5A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"Belkin_a61a5a"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000005734d40e175
                    Extra: Last beacon: 5652ms ago
                    IE: Unknown: 000D42656C6B696E5F613631613561
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A000110104400010110470010775B6680BFDE11D38D2F002275A61A5A103C000101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1113FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606070000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000014127A
                    IE: Unknown: DD1E00904C33EE1113FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406070000000000000000000000000000000000000000
                    IE: Unknown: DD07000C4307000000

``````
# iwlist chan
lo        no frequency information.

eth0      no frequency information.

wlan1     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.412 GHz (Channel 1)

``````
# ifconfig wlan1
wlan1     Link encap:Ethernet  HWaddr 00:16:ea:80:00:d2  
          inet addr:192.168.1.135  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8491 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3605667 (3.6 MB)  TX bytes:563804 (563.8 KB)

```This next one is ```
dmesg | grep iwl
``` but it had so much output that I couldn't scroll up enough in terminal to get it all. I suspect this may be where the issue is. Here is what I could copy

```
[23664.719011] iwlagn 0000:08:00.0:                FH_TSSR_TX_STATUS_REG: 0X07fd0001
[23664.719024] iwlagn 0000:08:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[23664.719077] iwlagn 0000:08:00.0: Start IWL Event Log Dump: display last 20 entries
[23664.719095] iwlagn 0000:08:00.0: EVT_LOGT:1319308785:0x00000001:0214
[23664.719106] iwlagn 0000:08:00.0: EVT_LOGT:1319308785:0x01002110:0209
[23664.719117] iwlagn 0000:08:00.0: EVT_LOGT:1319308809:0x00000000:0210
[23664.719128] iwlagn 0000:08:00.0: EVT_LOGT:1319308825:0x00000000:0207
[23664.719139] iwlagn 0000:08:00.0: EVT_LOGT:1319308827:0x01002110:0211
[23664.719149] iwlagn 0000:08:00.0: EVT_LOGT:1319308995:0x00000000:0212
[23664.719160] iwlagn 0000:08:00.0: EVT_LOGT:1319309035:0x00000000:0215
[23664.719171] iwlagn 0000:08:00.0: EVT_LOGT:1319309037:0x00000008:0220
[23664.719182] iwlagn 0000:08:00.0: EVT_LOGT:1319309495:0x0a07001c:0206
[23664.719192] iwlagn 0000:08:00.0: EVT_LOGT:1319309497:0x00000001:0204
[23664.719203] iwlagn 0000:08:00.0: EVT_LOGT:1319309500:0x00000001:0214
[23664.719214] iwlagn 0000:08:00.0: EVT_LOGT:1319309500:0x01002110:0209
[23664.719225] iwlagn 0000:08:00.0: EVT_LOGT:1319309523:0x00000000:0210
[23664.719236] iwlagn 0000:08:00.0: EVT_LOGT:1319309540:0x00000000:0207
[23664.719246] iwlagn 0000:08:00.0: EVT_LOGT:1319309542:0x01002110:0211
[23664.719257] iwlagn 0000:08:00.0: EVT_LOGT:1319309724:0x00000000:0212
[23664.719268] iwlagn 0000:08:00.0: EVT_LOGT:1319309771:0x00000000:0215
[23664.719279] iwlagn 0000:08:00.0: EVT_LOGT:1319309774:0x00000008:0220
[23664.719290] iwlagn 0000:08:00.0: EVT_LOGT:1319310702:0x0458004e:0401
[23664.719300] iwlagn 0000:08:00.0: EVT_LOGT:1319310716:0x00000000:0125
[23664.768943] iwlagn 0000:08:00.0: Stopping AGG while state not ON or starting
[23664.768952] iwlagn 0000:08:00.0: queue number out of range: 0, must be 10 to 19
[23671.076090] iwlagn 0000:08:00.0: iwlagn_tx_agg_start on ra = b0:48:7a:de:19:98 tid = 0
[24294.021857] iwlagn 0000:08:00.0: Microcode SW error detected.  Restarting 0x2000000.
[24294.021863] iwlagn 0000:08:00.0: Loaded firmware version: 8.83.5.1 build 33692
[24294.021938] iwlagn 0000:08:00.0: Start IWL Error Log Dump:
[24294.021940] iwlagn 0000:08:00.0: Status: 0x000412E4, count: 5
[24294.021943] iwlagn 0000:08:00.0: 0x00000005 | SYSASSERT                   
[24294.021945] iwlagn 0000:08:00.0: 0x0000325C | uPc
[24294.021947] iwlagn 0000:08:00.0: 0x0000312A | branchlink1
[24294.021949] iwlagn 0000:08:00.0: 0x0000312A | branchlink2
[24294.021951] iwlagn 0000:08:00.0: 0x00000916 | interruptlink1
[24294.021953] iwlagn 0000:08:00.0: 0x00000000 | interruptlink2
[24294.021955] iwlagn 0000:08:00.0: 0x41008035 | data1
[24294.021957] iwlagn 0000:08:00.0: 0x0000A906 | data2
[24294.021959] iwlagn 0000:08:00.0: 0x00000599 | line
[24294.021961] iwlagn 0000:08:00.0: 0xFD410173 | beacon time
[24294.021963] iwlagn 0000:08:00.0: 0x02876E8D | tsf low
[24294.021965] iwlagn 0000:08:00.0: 0x00000000 | tsf hi
[24294.021967] iwlagn 0000:08:00.0: 0x00000000 | time gp1
[24294.021969] iwlagn 0000:08:00.0: 0x258224C2 | time gp2
[24294.021971] iwlagn 0000:08:00.0: 0x00000000 | time gp3
[24294.021973] iwlagn 0000:08:00.0: 0x00010853 | uCode version
[24294.021975] iwlagn 0000:08:00.0: 0x00000054 | hw version
[24294.021977] iwlagn 0000:08:00.0: 0x00480303 | board version
[24294.021978] iwlagn 0000:08:00.0: 0x04B5004E | hcmd
[24294.021980] iwlagn 0000:08:00.0: CSR values:
[24294.021982] iwlagn 0000:08:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[24294.021988] iwlagn 0000:08:00.0:        CSR_HW_IF_CONFIG_REG: 0X00480303
[24294.021993] iwlagn 0000:08:00.0:          CSR_INT_COALESCING: 0X0000ff40
[24294.021999] iwlagn 0000:08:00.0:                     CSR_INT: 0X00000000
[24294.022004] iwlagn 0000:08:00.0:                CSR_INT_MASK: 0X00000000
[24294.022009] iwlagn 0000:08:00.0:           CSR_FH_INT_STATUS: 0X00000000
[24294.022013] iwlagn 0000:08:00.0:                 CSR_GPIO_IN: 0X00000000
[24294.022018] iwlagn 0000:08:00.0:                   CSR_RESET: 0X00000000
[24294.022023] iwlagn 0000:08:00.0:                CSR_GP_CNTRL: 0X080403c5
[24294.022029] iwlagn 0000:08:00.0:                  CSR_HW_REV: 0X00000054
[24294.022034] iwlagn 0000:08:00.0:              CSR_EEPROM_REG: 0X00000000
[24294.022039] iwlagn 0000:08:00.0:               CSR_EEPROM_GP: 0X90000004
[24294.022044] iwlagn 0000:08:00.0:              CSR_OTP_GP_REG: 0X00060000
[24294.022049] iwlagn 0000:08:00.0:                 CSR_GIO_REG: 0X00080044
[24294.022054] iwlagn 0000:08:00.0:            CSR_GP_UCODE_REG: 0X0000b5e1
[24294.022059] iwlagn 0000:08:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[24294.022064] iwlagn 0000:08:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[24294.022069] iwlagn 0000:08:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[24294.022074] iwlagn 0000:08:00.0:                 CSR_LED_REG: 0X00000058
[24294.022079] iwlagn 0000:08:00.0:        CSR_DRAM_INT_TBL_REG: 0X881b8488
[24294.022084] iwlagn 0000:08:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[24294.022089] iwlagn 0000:08:00.0:             CSR_ANA_PLL_CFG: 0X00880300
[24294.022094] iwlagn 0000:08:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[24294.022099] iwlagn 0000:08:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[24294.022101] iwlagn 0000:08:00.0: FH register values:
[24294.022114] iwlagn 0000:08:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X187d8400
[24294.022128] iwlagn 0000:08:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01ee0230
[24294.022141] iwlagn 0000:08:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000a8
[24294.022155] iwlagn 0000:08:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[24294.022168] iwlagn 0000:08:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[24294.022182] iwlagn 0000:08:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[24294.022195] iwlagn 0000:08:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[24294.022209] iwlagn 0000:08:00.0:                FH_TSSR_TX_STATUS_REG: 0X07fd0001
[24294.022222] iwlagn 0000:08:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[24294.022275] iwlagn 0000:08:00.0: Start IWL Event Log Dump: display last 20 entries
[24294.022293] iwlagn 0000:08:00.0: EVT_LOGT:0629285151:0x00000001:0214
[24294.022304] iwlagn 0000:08:00.0: EVT_LOGT:0629285151:0x01002110:0209
[24294.022315] iwlagn 0000:08:00.0: EVT_LOGT:0629285175:0x00000000:0210
[24294.022325] iwlagn 0000:08:00.0: EVT_LOGT:0629285191:0x00000000:0207
[24294.022336] iwlagn 0000:08:00.0: EVT_LOGT:0629285193:0x01002110:0211
[24294.022347] iwlagn 0000:08:00.0: EVT_LOGT:0629285375:0x00000000:0212
[24294.022357] iwlagn 0000:08:00.0: EVT_LOGT:0629285422:0x00000000:0215
[24294.022368] iwlagn 0000:08:00.0: EVT_LOGT:0629285425:0x00000008:0220
[24294.022379] iwlagn 0000:08:00.0: EVT_LOGT:0629285577:0x0ada001c:0206
[24294.022390] iwlagn 0000:08:00.0: EVT_LOGT:0629285579:0x00000001:0204
[24294.022400] iwlagn 0000:08:00.0: EVT_LOGT:0629285582:0x00000001:0214
[24294.022411] iwlagn 0000:08:00.0: EVT_LOGT:0629285582:0x01002110:0209
[24294.022422] iwlagn 0000:08:00.0: EVT_LOGT:0629285606:0x00000000:0210
[24294.022433] iwlagn 0000:08:00.0: EVT_LOGT:0629285622:0x00000000:0207
[24294.022443] iwlagn 0000:08:00.0: EVT_LOGT:0629285624:0x01002110:0211
[24294.022454] iwlagn 0000:08:00.0: EVT_LOGT:0629285806:0x00000000:0212
[24294.022465] iwlagn 0000:08:00.0: EVT_LOGT:0629285853:0x00000000:0215
[24294.022475] iwlagn 0000:08:00.0: EVT_LOGT:0629285856:0x00000008:0220
[24294.022486] iwlagn 0000:08:00.0: EVT_LOGT:0629286073:0x04b5004e:0401
[24294.022497] iwlagn 0000:08:00.0: EVT_LOGT:0629286086:0x00000000:0125
[24294.076864] iwlagn 0000:08:00.0: Stopping AGG while state not ON or starting
[24294.076872] iwlagn 0000:08:00.0: queue number out of range: 0, must be 10 to 19
[24300.304278] iwlagn 0000:08:00.0: iwlagn_tx_agg_start on ra = b0:48:7a:de:19:98 tid = 0
[26353.327647] iwlagn 0000:08:00.0: Aggregation not enabled for tid 6 because load = 1
[26503.108119] iwlagn 0000:08:00.0: iwlagn_tx_agg_start on ra = b0:48:7a:de:19:98 tid = 6
[58736.330691] iwlagn 0000:08:00.0: Microcode SW error detected.  Restarting 0x2000000.
[58736.330699] iwlagn 0000:08:00.0: Loaded firmware version: 8.83.5.1 build 33692
[58736.330778] iwlagn 0000:08:00.0: Start IWL Error Log Dump:
[58736.330783] iwlagn 0000:08:00.0: Status: 0x000412E4, count: 5
[58736.330788] iwlagn 0000:08:00.0: 0x00000005 | SYSASSERT                   
[58736.330792] iwlagn 0000:08:00.0: 0x0000325C | uPc
[58736.330795] iwlagn 0000:08:00.0: 0x0000312A | branchlink1
[58736.330799] iwlagn 0000:08:00.0: 0x0000312A | branchlink2
[58736.330803] iwlagn 0000:08:00.0: 0x00000916 | interruptlink1
[58736.330807] iwlagn 0000:08:00.0: 0x00000000 | interruptlink2
[58736.330810] iwlagn 0000:08:00.0: 0x41008035 | data1
[58736.330814] iwlagn 0000:08:00.0: 0x00008907 | data2
[58736.330817] iwlagn 0000:08:00.0: 0x00000599 | line
[58736.330821] iwlagn 0000:08:00.0: 0x6EC0C6CD | beacon time
[58736.330824] iwlagn 0000:08:00.0: 0x00985932 | tsf low
[58736.330828] iwlagn 0000:08:00.0: 0x00000000 | tsf hi
[58736.330832] iwlagn 0000:08:00.0: 0x00000000 | time gp1
[58736.330835] iwlagn 0000:08:00.0: 0x04E6897E | time gp2
[58736.330839] iwlagn 0000:08:00.0: 0x00000000 | time gp3
[58736.330842] iwlagn 0000:08:00.0: 0x00010853 | uCode version
[58736.330846] iwlagn 0000:08:00.0: 0x00000054 | hw version
[58736.330850] iwlagn 0000:08:00.0: 0x00480303 | board version
[58736.330854] iwlagn 0000:08:00.0: 0x0435004E | hcmd
[58736.330857] iwlagn 0000:08:00.0: CSR values:
[58736.330861] iwlagn 0000:08:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[58736.330869] iwlagn 0000:08:00.0:        CSR_HW_IF_CONFIG_REG: 0X00480303
[58736.330876] iwlagn 0000:08:00.0:          CSR_INT_COALESCING: 0X0000ff40
[58736.330883] iwlagn 0000:08:00.0:                     CSR_INT: 0X00000000
[58736.330890] iwlagn 0000:08:00.0:                CSR_INT_MASK: 0X00000000
[58736.330897] iwlagn 0000:08:00.0:           CSR_FH_INT_STATUS: 0X00000000
[58736.330904] iwlagn 0000:08:00.0:                 CSR_GPIO_IN: 0X00000000
[58736.330911] iwlagn 0000:08:00.0:                   CSR_RESET: 0X00000000
[58736.330918] iwlagn 0000:08:00.0:                CSR_GP_CNTRL: 0X080403c5
[58736.330925] iwlagn 0000:08:00.0:                  CSR_HW_REV: 0X00000054
[58736.330932] iwlagn 0000:08:00.0:              CSR_EEPROM_REG: 0X00000000
[58736.330939] iwlagn 0000:08:00.0:               CSR_EEPROM_GP: 0X90000004
[58736.330946] iwlagn 0000:08:00.0:              CSR_OTP_GP_REG: 0X00060000
[58736.330953] iwlagn 0000:08:00.0:                 CSR_GIO_REG: 0X00080044
[58736.330960] iwlagn 0000:08:00.0:            CSR_GP_UCODE_REG: 0X00004ca3
[58736.330967] iwlagn 0000:08:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[58736.330974] iwlagn 0000:08:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[58736.330981] iwlagn 0000:08:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[58736.330988] iwlagn 0000:08:00.0:                 CSR_LED_REG: 0X00000058
[58736.330995] iwlagn 0000:08:00.0:        CSR_DRAM_INT_TBL_REG: 0X881b8488
[58736.331002] iwlagn 0000:08:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[58736.331009] iwlagn 0000:08:00.0:             CSR_ANA_PLL_CFG: 0X00880300
[58736.331016] iwlagn 0000:08:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[58736.331023] iwlagn 0000:08:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[58736.331027] iwlagn 0000:08:00.0: FH register values:
[58736.331043] iwlagn 0000:08:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X187d8400
[58736.331058] iwlagn 0000:08:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01ee0230
[58736.331074] iwlagn 0000:08:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f0
[58736.331090] iwlagn 0000:08:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[58736.331105] iwlagn 0000:08:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[58736.331121] iwlagn 0000:08:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[58736.331137] iwlagn 0000:08:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[58736.331153] iwlagn 0000:08:00.0:                FH_TSSR_TX_STATUS_REG: 0X07fd0001
[58736.331168] iwlagn 0000:08:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[58736.331224] iwlagn 0000:08:00.0: Start IWL Event Log Dump: display last 20 entries
[58736.331244] iwlagn 0000:08:00.0: EVT_LOGT:0082215927:0x00000001:0214
[58736.331257] iwlagn 0000:08:00.0: EVT_LOGT:0082215928:0x01002110:0209
[58736.331270] iwlagn 0000:08:00.0: EVT_LOGT:0082215952:0x00000000:0210
[58736.331283] iwlagn 0000:08:00.0: EVT_LOGT:0082215968:0x00000000:0207
[58736.331296] iwlagn 0000:08:00.0: EVT_LOGT:0082215970:0x01002110:0211
[58736.331308] iwlagn 0000:08:00.0: EVT_LOGT:0082216138:0x00000000:0212
[58736.331321] iwlagn 0000:08:00.0: EVT_LOGT:0082216178:0x00000000:0215
[58736.331334] iwlagn 0000:08:00.0: EVT_LOGT:0082216180:0x00000008:0220
[58736.331347] iwlagn 0000:08:00.0: EVT_LOGT:0082216791:0x0a3d001c:0206
[58736.331359] iwlagn 0000:08:00.0: EVT_LOGT:0082216793:0x00000001:0204
[58736.331372] iwlagn 0000:08:00.0: EVT_LOGT:0082216796:0x00000001:0214
[58736.331385] iwlagn 0000:08:00.0: EVT_LOGT:0082216796:0x01002110:0209
[58736.331398] iwlagn 0000:08:00.0: EVT_LOGT:0082216820:0x00000000:0210
[58736.331410] iwlagn 0000:08:00.0: EVT_LOGT:0082216836:0x00000000:0207
[58736.331423] iwlagn 0000:08:00.0: EVT_LOGT:0082216838:0x01002110:0211
[58736.331436] iwlagn 0000:08:00.0: EVT_LOGT:0082217020:0x00000000:0212
[58736.331449] iwlagn 0000:08:00.0: EVT_LOGT:0082217067:0x00000000:0215
[58736.331461] iwlagn 0000:08:00.0: EVT_LOGT:0082217070:0x00000008:0220
[58736.331474] iwlagn 0000:08:00.0: EVT_LOGT:0082217333:0x0435004e:0401
[58736.331487] iwlagn 0000:08:00.0: EVT_LOGT:0082217346:0x00000000:0125
[58736.380811] iwlagn 0000:08:00.0: Stopping AGG while state not ON or starting
[58736.380819] iwlagn 0000:08:00.0: queue number out of range: 0, must be 10 to 19
[58736.380958] iwlagn 0000:08:00.0: Stopping AGG while state not ON or starting
[58736.380963] iwlagn 0000:08:00.0: queue number out of range: 0, must be 10 to 19
[58749.942641] iwlagn 0000:08:00.0: iwlagn_tx_agg_start on ra = b0:48:7a:de:19:98 tid = 0
[58768.647718] iwlagn 0000:08:00.0: Aggregation not enabled for tid 6 because load = 0
[58899.255714] iwlagn 0000:08:00.0: Stopping AGG while state not ON or starting
[58905.928287] iwlagn 0000:08:00.0: iwlagn_tx_agg_start on ra = b0:48:7a:de:19:98 tid = 0
[58975.434647] iwlagn 0000:08:00.0: Aggregation not enabled for tid 6 because load = 0
[59035.718601] iwlagn 0000:08:00.0: Aggregation not enabled for tid 6 because load = 0
[59224.770668] iwlagn 0000:08:00.0: Aggregation not enabled for tid 6 because load = 0
[59259.216604] iwlagn 0000:08:00.0: Aggregation not enabled for tid 6 because load = 0
[59315.629142] iwlagn 0000:08:00.0: Aggregation not enabled for tid 6 because load = 0
[59526.568667] iwlagn 0000:08:00.0: Aggregation not enabled for tid 6 because load = 0
[59587.409666] iwlagn 0000:08:00.0: Aggregation not enabled for tid 6 because load = 0
[59800.164916] iwlagn 0000:08:00.0: Aggregation not enabled for tid 6 because load = 0
[59857.537109] iwlagn 0000:08:00.0: Aggregation not enabled for tid 6 because load = 0
[59916.943891] iwlagn 0000:08:00.0: Aggregation not enabled for tid 6 because load = 1
[59958.956105] iwlagn 0000:08:00.0: Aggregation not enabled for tid 6 because load = 0
[60096.717455] iwlagn 0000:08:00.0: Aggregation not enabled for tid 6 because load = 0
[60349.382269] iwlagn 0000:08:00.0: Microcode SW error detected.  Restarting 0x2000000.
[60349.382277] iwlagn 0000:08:00.0: Loaded firmware version: 8.83.5.1 build 33692
[60349.382356] iwlagn 0000:08:00.0: Start IWL Error Log Dump:
[60349.382360] iwlagn 0000:08:00.0: Status: 0x000412E4, count: 5
[60349.382365] iwlagn 0000:08:00.0: 0x00000005 | SYSASSERT                   
[60349.382369] iwlagn 0000:08:00.0: 0x0000325C | uPc
[60349.382373] iwlagn 0000:08:00.0: 0x0000312A | branchlink1
[60349.382376] iwlagn 0000:08:00.0: 0x0000312A | branchlink2
[60349.382380] iwlagn 0000:08:00.0: 0x00000916 | interruptlink1
[60349.382384] iwlagn 0000:08:00.0: 0x00000000 | interruptlink2
[60349.382388] iwlagn 0000:08:00.0: 0x41008035 | data1
[60349.382391] iwlagn 0000:08:00.0: 0x0000A906 | data2
[60349.382394] iwlagn 0000:08:00.0: 0x00000599 | line
[60349.382398] iwlagn 0000:08:00.0: 0xCC40A66C | beacon time
[60349.382402] iwlagn 0000:08:00.0: 0x00266994 | tsf low
[60349.382405] iwlagn 0000:08:00.0: 0x00000000 | tsf hi
[60349.382409] iwlagn 0000:08:00.0: 0x00000000 | time gp1
[60349.382413] iwlagn 0000:08:00.0: 0x6024CCCD | time gp2
[60349.382416] iwlagn 0000:08:00.0: 0x00000000 | time gp3
[60349.382420] iwlagn 0000:08:00.0: 0x00010853 | uCode version
[60349.382423] iwlagn 0000:08:00.0: 0x00000054 | hw version
[60349.382427] iwlagn 0000:08:00.0: 0x00480303 | board version
[60349.382431] iwlagn 0000:08:00.0: 0x040E004E | hcmd
[60349.382434] iwlagn 0000:08:00.0: CSR values:
[60349.382438] iwlagn 0000:08:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[60349.382446] iwlagn 0000:08:00.0:        CSR_HW_IF_CONFIG_REG: 0X00480303
[60349.382453] iwlagn 0000:08:00.0:          CSR_INT_COALESCING: 0X0000ff40
[60349.382460] iwlagn 0000:08:00.0:                     CSR_INT: 0X00000000
[60349.382467] iwlagn 0000:08:00.0:                CSR_INT_MASK: 0X00000000
[60349.382474] iwlagn 0000:08:00.0:           CSR_FH_INT_STATUS: 0X00000000
[60349.382481] iwlagn 0000:08:00.0:                 CSR_GPIO_IN: 0X00000000
[60349.382488] iwlagn 0000:08:00.0:                   CSR_RESET: 0X00000000
[60349.382495] iwlagn 0000:08:00.0:                CSR_GP_CNTRL: 0X080403c5
[60349.382502] iwlagn 0000:08:00.0:                  CSR_HW_REV: 0X00000054
[60349.382509] iwlagn 0000:08:00.0:              CSR_EEPROM_REG: 0X00000000
[60349.382516] iwlagn 0000:08:00.0:               CSR_EEPROM_GP: 0X90000004
[60349.382523] iwlagn 0000:08:00.0:              CSR_OTP_GP_REG: 0X00060000
[60349.382530] iwlagn 0000:08:00.0:                 CSR_GIO_REG: 0X00080044
[60349.382537] iwlagn 0000:08:00.0:            CSR_GP_UCODE_REG: 0X0000196f
[60349.382544] iwlagn 0000:08:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[60349.382551] iwlagn 0000:08:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[60349.382558] iwlagn 0000:08:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[60349.382565] iwlagn 0000:08:00.0:                 CSR_LED_REG: 0X00000058
[60349.382572] iwlagn 0000:08:00.0:        CSR_DRAM_INT_TBL_REG: 0X881b8488
[60349.382579] iwlagn 0000:08:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[60349.382586] iwlagn 0000:08:00.0:             CSR_ANA_PLL_CFG: 0X00880300
[60349.382593] iwlagn 0000:08:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[60349.382600] iwlagn 0000:08:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[60349.382604] iwlagn 0000:08:00.0: FH register values:
[60349.382619] iwlagn 0000:08:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X187d8400
[60349.382635] iwlagn 0000:08:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01ee0230
[60349.382651] iwlagn 0000:08:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000c0
[60349.382666] iwlagn 0000:08:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[60349.382682] iwlagn 0000:08:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[60349.382698] iwlagn 0000:08:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[60349.382714] iwlagn 0000:08:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[60349.382729] iwlagn 0000:08:00.0:                FH_TSSR_TX_STATUS_REG: 0X07fd0001
[60349.382745] iwlagn 0000:08:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[60349.382800] iwlagn 0000:08:00.0: Start IWL Event Log Dump: display last 20 entries
[60349.382821] iwlagn 0000:08:00.0: EVT_LOGT:1613023263:0x00000001:0214
[60349.382834] iwlagn 0000:08:00.0: EVT_LOGT:1613023263:0x01002110:0209
[60349.382847] iwlagn 0000:08:00.0: EVT_LOGT:1613023286:0x00000000:0210
[60349.382860] iwlagn 0000:08:00.0: EVT_LOGT:1613023303:0x00000000:0207
[60349.382873] iwlagn 0000:08:00.0: EVT_LOGT:1613023305:0x01002110:0211
[60349.382886] iwlagn 0000:08:00.0: EVT_LOGT:1613023487:0x00000000:0212
[60349.382899] iwlagn 0000:08:00.0: EVT_LOGT:1613023534:0x00000000:0215
[60349.382911] iwlagn 0000:08:00.0: EVT_LOGT:1613023537:0x00000008:0220
[60349.382924] iwlagn 0000:08:00.0: EVT_LOGT:1613024058:0x0aaf001c:0206
[60349.382937] iwlagn 0000:08:00.0: EVT_LOGT:1613024060:0x00000001:0204
[60349.382950] iwlagn 0000:08:00.0: EVT_LOGT:1613024063:0x00000001:0214
[60349.382963] iwlagn 0000:08:00.0: EVT_LOGT:1613024063:0x01002110:0209
[60349.382975] iwlagn 0000:08:00.0: EVT_LOGT:1613024087:0x00000000:0210
[60349.382988] iwlagn 0000:08:00.0: EVT_LOGT:1613024103:0x00000000:0207
[60349.383001] iwlagn 0000:08:00.0: EVT_LOGT:1613024105:0x01002110:0211
[60349.383014] iwlagn 0000:08:00.0: EVT_LOGT:1613024287:0x00000000:0212
[60349.383027] iwlagn 0000:08:00.0: EVT_LOGT:1613024334:0x00000000:0215
[60349.383039] iwlagn 0000:08:00.0: EVT_LOGT:1613024337:0x00000008:0220
[60349.383052] iwlagn 0000:08:00.0: EVT_LOGT:1613024452:0x040e004e:0401
[60349.383065] iwlagn 0000:08:00.0: EVT_LOGT:1613024466:0x00000000:0125
[60349.436835] iwlagn 0000:08:00.0: Stopping AGG while state not ON or starting
[60349.436844] iwlagn 0000:08:00.0: queue number out of range: 0, must be 10 to 19
[60354.116114] iwlagn 0000:08:00.0: iwlagn_tx_agg_start on ra = b0:48:7a:de:19:98 tid = 0
[60517.045374] iwlagn 0000:08:00.0: Microcode SW error detected.  Restarting 0x2000000.
[60517.045382] iwlagn 0000:08:00.0: Loaded firmware version: 8.83.5.1 build 33692
[60517.045476] iwlagn 0000:08:00.0: Start IWL Error Log Dump:
[60517.045481] iwlagn 0000:08:00.0: Status: 0x000412E4, count: 5
[60517.045486] iwlagn 0000:08:00.0: 0x00000005 | SYSASSERT                   
[60517.045490] iwlagn 0000:08:00.0: 0x0000325C | uPc
[60517.045494] iwlagn 0000:08:00.0: 0x0000312A | branchlink1
[60517.045497] iwlagn 0000:08:00.0: 0x0000312A | branchlink2
[60517.045501] iwlagn 0000:08:00.0: 0x00000916 | interruptlink1
[60517.045505] iwlagn 0000:08:00.0: 0x00000000 | interruptlink2
[60517.045508] iwlagn 0000:08:00.0: 0x41008035 | data1
[60517.045512] iwlagn 0000:08:00.0: 0x00008907 | data2
[60517.045515] iwlagn 0000:08:00.0: 0x00000599 | line
[60517.045519] iwlagn 0000:08:00.0: 0x9880957D | beacon time
[60517.045522] iwlagn 0000:08:00.0: 0x07FE4A83 | tsf low
[60517.045526] iwlagn 0000:08:00.0: 0x00000000 | tsf hi
[60517.045529] iwlagn 0000:08:00.0: 0x00000000 | time gp1
[60517.045533] iwlagn 0000:08:00.0: 0x09FE2393 | time gp2
[60517.045537] iwlagn 0000:08:00.0: 0x00000000 | time gp3
[60517.045541] iwlagn 0000:08:00.0: 0x00010853 | uCode version
[60517.045544] iwlagn 0000:08:00.0: 0x00000054 | hw version
[60517.045548] iwlagn 0000:08:00.0: 0x00480303 | board version
[60517.045551] iwlagn 0000:08:00.0: 0x0430004E | hcmd
[60517.045555] iwlagn 0000:08:00.0: CSR values:
[60517.045558] iwlagn 0000:08:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[60517.045566] iwlagn 0000:08:00.0:        CSR_HW_IF_CONFIG_REG: 0X00480303
[60517.045573] iwlagn 0000:08:00.0:          CSR_INT_COALESCING: 0X0000ff40
[60517.045580] iwlagn 0000:08:00.0:                     CSR_INT: 0X00000000
[60517.045587] iwlagn 0000:08:00.0:                CSR_INT_MASK: 0X00000000
[60517.045594] iwlagn 0000:08:00.0:           CSR_FH_INT_STATUS: 0X00000000
[60517.045601] iwlagn 0000:08:00.0:                 CSR_GPIO_IN: 0X00000000
[60517.045608] iwlagn 0000:08:00.0:                   CSR_RESET: 0X00000000
[60517.045615] iwlagn 0000:08:00.0:                CSR_GP_CNTRL: 0X080403c5
[60517.045622] iwlagn 0000:08:00.0:                  CSR_HW_REV: 0X00000054
[60517.045629] iwlagn 0000:08:00.0:              CSR_EEPROM_REG: 0X00000000
[60517.045636] iwlagn 0000:08:00.0:               CSR_EEPROM_GP: 0X90000004
[60517.045643] iwlagn 0000:08:00.0:              CSR_OTP_GP_REG: 0X00060000
[60517.045650] iwlagn 0000:08:00.0:                 CSR_GIO_REG: 0X00080044
[60517.045657] iwlagn 0000:08:00.0:            CSR_GP_UCODE_REG: 0X00006eeb
[60517.045663] iwlagn 0000:08:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[60517.045670] iwlagn 0000:08:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[60517.045677] iwlagn 0000:08:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[60517.045684] iwlagn 0000:08:00.0:                 CSR_LED_REG: 0X00000058
[60517.045691] iwlagn 0000:08:00.0:        CSR_DRAM_INT_TBL_REG: 0X881b8488
[60517.045698] iwlagn 0000:08:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[60517.045705] iwlagn 0000:08:00.0:             CSR_ANA_PLL_CFG: 0X00880300
[60517.045712] iwlagn 0000:08:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[60517.045719] iwlagn 0000:08:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[60517.045723] iwlagn 0000:08:00.0: FH register values:
[60517.045739] iwlagn 0000:08:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X187d8400
[60517.045755] iwlagn 0000:08:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01ee0230
[60517.045770] iwlagn 0000:08:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[60517.045786] iwlagn 0000:08:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[60517.045801] iwlagn 0000:08:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[60517.045817] iwlagn 0000:08:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[60517.045833] iwlagn 0000:08:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[60517.045848] iwlagn 0000:08:00.0:                FH_TSSR_TX_STATUS_REG: 0X07fd0001
[60517.045864] iwlagn 0000:08:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[60517.045919] iwlagn 0000:08:00.0: Start IWL Event Log Dump: display last 20 entries
[60517.045940] iwlagn 0000:08:00.0: EVT_LOGT:0167647230:0x09fe17fd:1587
[60517.045953] iwlagn 0000:08:00.0: EVT_LOGT:0167647422:0x09fe18bd:1587
[60517.045966] iwlagn 0000:08:00.0: EVT_LOGT:0167647614:0x09fe197d:1587
[60517.045979] iwlagn 0000:08:00.0: EVT_LOGT:0167647806:0x09fe1a3d:1587
[60517.045991] iwlagn 0000:08:00.0: EVT_LOGT:0167647998:0x09fe1afd:1587
[60517.046004] iwlagn 0000:08:00.0: EVT_LOGT:0167648190:0x09fe1bbd:1587
[60517.046017] iwlagn 0000:08:00.0: EVT_LOGT:0167648382:0x09fe1c7d:1587
[60517.046029] iwlagn 0000:08:00.0: EVT_LOGT:0167648574:0x09fe1d3d:1587
[60517.046042] iwlagn 0000:08:00.0: EVT_LOGT:0167648766:0x09fe1dfd:1587
[60517.046055] iwlagn 0000:08:00.0: EVT_LOGT:0167648958:0x09fe1ebd:1587
[60517.046068] iwlagn 0000:08:00.0: EVT_LOGT:0167649110:0x09fe1f56:1587
[60517.046080] iwlagn 0000:08:00.0: EVT_LOGT:0167649302:0x09fe2016:1587
[60517.046093] iwlagn 0000:08:00.0: EVT_LOGT:0167649494:0x09fe20d6:1587
[60517.046106] iwlagn 0000:08:00.0: EVT_LOGT:0167649686:0x09fe2196:1587
[60517.046119] iwlagn 0000:08:00.0: EVT_LOGT:0167649878:0x09fe2256:1587
[60517.046132] iwlagn 0000:08:00.0: EVT_LOGT:0167650070:0x00000000:0264
[60517.046144] iwlagn 0000:08:00.0: EVT_LOGT:0167650139:0x00000000:0302
[60517.046157] iwlagn 0000:08:00.0: EVT_LOGT:0167650171:0x00000094:0303
[60517.046170] iwlagn 0000:08:00.0: EVT_LOGT:0167650186:0x0430004e:0401
[60517.046183] iwlagn 0000:08:00.0: EVT_LOGT:0167650200:0x00000000:0125
[60517.114112] iwlagn 0000:08:00.0: Stopping AGG while state not ON or starting
[60517.114122] iwlagn 0000:08:00.0: queue number out of range: 0, must be 10 to 19
[60527.552317] iwlagn 0000:08:00.0: iwlagn_tx_agg_start on ra = b0:48:7a:de:19:98 tid = 0
[61094.517674] iwlagn 0000:08:00.0: Microcode SW error detected.  Restarting 0x2000000.
[61094.517682] iwlagn 0000:08:00.0: Loaded firmware version: 8.83.5.1 build 33692
[61094.517778] iwlagn 0000:08:00.0: Start IWL Error Log Dump:
[61094.517783] iwlagn 0000:08:00.0: Status: 0x000412E4, count: 5
[61094.517787] iwlagn 0000:08:00.0: 0x00000005 | SYSASSERT                   
[61094.517792] iwlagn 0000:08:00.0: 0x0000325C | uPc
[61094.517795] iwlagn 0000:08:00.0: 0x0000312A | branchlink1
[61094.517799] iwlagn 0000:08:00.0: 0x0000312A | branchlink2
[61094.517803] iwlagn 0000:08:00.0: 0x00000916 | interruptlink1
[61094.517807] iwlagn 0000:08:00.0: 0x00000000 | interruptlink2
[61094.517810] iwlagn 0000:08:00.0: 0x41008035 | data1
[61094.517814] iwlagn 0000:08:00.0: 0x0000A906 | data2
[61094.517817] iwlagn 0000:08:00.0: 0x00000599 | line
[61094.517820] iwlagn 0000:08:00.0: 0x8080BE5E | beacon time
[61094.517824] iwlagn 0000:08:00.0: 0x0B0E81A2 | tsf low
[61094.517828] iwlagn 0000:08:00.0: 0x00000000 | tsf hi
[61094.517831] iwlagn 0000:08:00.0: 0x00000000 | time gp1
[61094.517835] iwlagn 0000:08:00.0: 0x226B4525 | time gp2
[61094.517839] iwlagn 0000:08:00.0: 0x00000000 | time gp3
[61094.517842] iwlagn 0000:08:00.0: 0x00010853 | uCode version
[61094.517846] iwlagn 0000:08:00.0: 0x00000054 | hw version
[61094.517849] iwlagn 0000:08:00.0: 0x00480303 | board version
[61094.517853] iwlagn 0000:08:00.0: 0x04EA004E | hcmd
[61094.517857] iwlagn 0000:08:00.0: CSR values:
[61094.517860] iwlagn 0000:08:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[61094.517868] iwlagn 0000:08:00.0:        CSR_HW_IF_CONFIG_REG: 0X00480303
[61094.517875] iwlagn 0000:08:00.0:          CSR_INT_COALESCING: 0X0000ff40
[61094.517883] iwlagn 0000:08:00.0:                     CSR_INT: 0X00000000
[61094.517890] iwlagn 0000:08:00.0:                CSR_INT_MASK: 0X00000000
[61094.517897] iwlagn 0000:08:00.0:           CSR_FH_INT_STATUS: 0X00000000
[61094.517903] iwlagn 0000:08:00.0:                 CSR_GPIO_IN: 0X00000000
[61094.517910] iwlagn 0000:08:00.0:                   CSR_RESET: 0X00000000
[61094.517917] iwlagn 0000:08:00.0:                CSR_GP_CNTRL: 0X080403c5
[61094.517924] iwlagn 0000:08:00.0:                  CSR_HW_REV: 0X00000054
[61094.517931] iwlagn 0000:08:00.0:              CSR_EEPROM_REG: 0X00000000
[61094.517939] iwlagn 0000:08:00.0:               CSR_EEPROM_GP: 0X90000004
[61094.517946] iwlagn 0000:08:00.0:              CSR_OTP_GP_REG: 0X00060000
[61094.517953] iwlagn 0000:08:00.0:                 CSR_GIO_REG: 0X00080044
[61094.517960] iwlagn 0000:08:00.0:            CSR_GP_UCODE_REG: 0X00008c76
[61094.517967] iwlagn 0000:08:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[61094.517974] iwlagn 0000:08:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[61094.517981] iwlagn 0000:08:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[61094.517988] iwlagn 0000:08:00.0:                 CSR_LED_REG: 0X00000058
[61094.517995] iwlagn 0000:08:00.0:        CSR_DRAM_INT_TBL_REG: 0X881b8488
[61094.518002] iwlagn 0000:08:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[61094.518009] iwlagn 0000:08:00.0:             CSR_ANA_PLL_CFG: 0X00880300
[61094.518016] iwlagn 0000:08:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[61094.518023] iwlagn 0000:08:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[61094.518027] iwlagn 0000:08:00.0: FH register values:
[61094.518045] iwlagn 0000:08:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X187d8400
[61094.518064] iwlagn 0000:08:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01ee0230
[61094.518083] iwlagn 0000:08:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000a8
[61094.518101] iwlagn 0000:08:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[61094.518120] iwlagn 0000:08:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[61094.518139] iwlagn 0000:08:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[61094.518157] iwlagn 0000:08:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[61094.518175] iwlagn 0000:08:00.0:                FH_TSSR_TX_STATUS_REG: 0X07fd0001
[61094.518193] iwlagn 0000:08:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[61094.518259] iwlagn 0000:08:00.0: Start IWL Event Log Dump: display last 20 entries
[61094.518283] iwlagn 0000:08:00.0: EVT_LOGT:0577454229:0x00000001:0214
[61094.518297] iwlagn 0000:08:00.0: EVT_LOGT:0577454229:0x01002110:0209
[61094.518312] iwlagn 0000:08:00.0: EVT_LOGT:0577454253:0x00000000:0210
[61094.518326] iwlagn 0000:08:00.0: EVT_LOGT:0577454269:0x00000000:0207
[61094.518340] iwlagn 0000:08:00.0: EVT_LOGT:0577454271:0x01002110:0211
[61094.518355] iwlagn 0000:08:00.0: EVT_LOGT:0577454453:0x00000000:0212
[61094.518369] iwlagn 0000:08:00.0: EVT_LOGT:0577454500:0x00000000:0215
[61094.518383] iwlagn 0000:08:00.0: EVT_LOGT:0577454503:0x00000008:0220
[61094.518397] iwlagn 0000:08:00.0: EVT_LOGT:0577455069:0x0a4b001c:0206
[61094.518412] iwlagn 0000:08:00.0: EVT_LOGT:0577455071:0x00000001:0204
[61094.518426] iwlagn 0000:08:00.0: EVT_LOGT:0577455074:0x00000001:0214
[61094.518440] iwlagn 0000:08:00.0: EVT_LOGT:0577455074:0x01002110:0209
[61094.518454] iwlagn 0000:08:00.0: EVT_LOGT:0577455098:0x00000000:0210
[61094.518468] iwlagn 0000:08:00.0: EVT_LOGT:0577455114:0x00000000:0207
[61094.518484] iwlagn 0000:08:00.0: EVT_LOGT:0577455116:0x01002110:0211
[61094.518498] iwlagn 0000:08:00.0: EVT_LOGT:0577455298:0x00000000:0212
[61094.518512] iwlagn 0000:08:00.0: EVT_LOGT:0577455345:0x00000000:0215
[61094.518527] iwlagn 0000:08:00.0: EVT_LOGT:0577455348:0x00000008:0220
[61094.518541] iwlagn 0000:08:00.0: EVT_LOGT:0577455388:0x04ea004e:0401
[61094.518555] iwlagn 0000:08:00.0: EVT_LOGT:0577455401:0x00000000:0125
[61094.576682] iwlagn 0000:08:00.0: Stopping AGG while state not ON or starting
[61094.576691] iwlagn 0000:08:00.0: queue number out of range: 0, must be 10 to 19
[61109.244466] iwlagn 0000:08:00.0: iwlagn_tx_agg_start on ra = b0:48:7a:de:19:98 tid = 0
[63187.505762] iwlagn 0000:08:00.0: Aggregation not enabled for tid 6 because load = 0
[63474.712064] iwlagn 0000:08:00.0: iwlagn_tx_agg_start on ra = b0:48:7a:de:19:98 tid = 6
[75893.648519] iwlagn 0000:08:00.0: Stopping AGG while state not ON or starting
[75895.029504] iwlagn 0000:08:00.0: PCI INT A disabled
[75895.226064] iwlagn: Unknown parameter `disable_hw_scan'
[75997.507015] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[75997.507019] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[75997.507129] iwlagn 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[75997.507143] iwlagn 0000:08:00.0: setting latency timer to 64
[75997.507182] iwlagn 0000:08:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[75997.529068] iwlagn 0000:08:00.0: device EEPROM VER=0x11f, CALIB=0x4
[75997.529072] iwlagn 0000:08:00.0: Device SKU: 0Xb
[75997.529098] iwlagn 0000:08:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[75997.529189] iwlagn 0000:08:00.0: irq 47 for MSI/MSI-X
[75997.560434] iwlagn 0000:08:00.0: loaded firmware version 8.83.5.1 build 33692
[75997.560972] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[76016.965484] iwlagn 0000:08:00.0: Aggregation not enabled for tid 0 because load = 10
[76021.270292] iwlagn 0000:08:00.0: Aggregation not enabled for tid 0 because load = 10
[76036.071826] iwlagn 0000:08:00.0: Aggregation not enabled for tid 0 because load = 0
[76067.669581] iwlagn 0000:08:00.0: Aggregation not enabled for tid 0 because load = 0
[76111.370081] iwlagn 0000:08:00.0: PCI INT A disabled
[76111.523346] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[76111.523350] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[76111.523461] iwlagn 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[76111.523475] iwlagn 0000:08:00.0: setting latency timer to 64
[76111.523519] iwlagn 0000:08:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[76111.545683] iwlagn 0000:08:00.0: device EEPROM VER=0x11f, CALIB=0x4
[76111.545686] iwlagn 0000:08:00.0: Device SKU: 0Xb
[76111.545743] iwlagn 0000:08:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[76111.545925] iwlagn 0000:08:00.0: irq 47 for MSI/MSI-X
[76111.553103] iwlagn 0000:08:00.0: loaded firmware version 8.83.5.1 build 33692
[76111.556578] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[76131.337289] iwlagn 0000:08:00.0: Aggregation not enabled for tid 0 because load = 5
[76135.537511] iwlagn 0000:08:00.0: Aggregation not enabled for tid 0 because load = 6
[76183.474749] iwlagn 0000:08:00.0: Aggregation not enabled for tid 0 because load = 1
[76187.497984] iwlagn 0000:08:00.0: PCI INT A disabled
[76187.654825] iwlagn: Unknown parameter `11n_disable50'
[76340.038204] iwlagn: Unknown parameter `11n_disable50'
[76464.113816] iwlagn: Unknown parameter `11n_disable50'
[76499.660617] iwlagn: Unknown parameter `11n_disable50'
[76523.711231] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[76523.711234] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[76523.711328] iwlagn 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[76523.711340] iwlagn 0000:08:00.0: setting latency timer to 64
[76523.711378] iwlagn 0000:08:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[76523.733229] iwlagn 0000:08:00.0: device EEPROM VER=0x11f, CALIB=0x4
[76523.733233] iwlagn 0000:08:00.0: Device SKU: 0Xb
[76523.733254] iwlagn 0000:08:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[76523.733338] iwlagn 0000:08:00.0: irq 47 for MSI/MSI-X
[76523.736843] iwlagn 0000:08:00.0: loaded firmware version 8.83.5.1 build 33692
[76523.737506] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[76532.516146] iwlagn 0000:08:00.0: iwlagn_tx_agg_start on ra = b0:48:7a:de:19:98 tid = 0
[76896.999469] iwlagn 0000:08:00.0: Aggregation not enabled for tid 6 because load = 0
[77604.978060] iwlagn 0000:08:00.0: Aggregation not enabled for tid 6 because load = 0
[77666.747395] iwlagn 0000:08:00.0: Aggregation not enabled for tid 6 because load = 1
[77698.832326] iwlagn 0000:08:00.0: iwlagn_tx_agg_start on ra = b0:48:7a:de:19:98 tid = 6

```and finally
```
lsmod
Module                  Size  Used by
iwlagn                314213  0 
mac80211              462092  1 iwlagn
cfg80211              199587  2 iwlagn,mac80211
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_hdmi     32040  1 
uvcvideo               72711  0 
snd_hda_codec_conexant    62197  1 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
arc4                   12529  2 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73882  0 
serio_raw              13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sparse_keymap          13890  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
i915                  566711  3 
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
ahci                   26002  2 
libahci                26861  1 ahci
atl1c                  41643  0 
i2c_algo_bit           13423  1 i915
firewire_ohci          40722  0 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
video                  19412  1 i915
wmi                    19256  0 
vesafb                 13809  0 

```I've been tinkering a lot. I'm still a pretty new to linux, but I'm trying to learn. Any help would be greatly appreciated. The only info I've found thus far is to disable n which means I wasted my time installing my new card :(

---

### Post by praseodym on 2011-12-12
> ```
[75895.226064] iwlagn: Unknown parameter `disable_hw_scan'
...
[76187.654825] iwlagn: Unknown parameter `11n_disable50'
```
Remove those parameters. This file can be removed:
```
sudo rm /etc/modprobe.d/ath9k.conf
```
because you have an Intel device, not Atheros. Which mode does the router send (b+g)? You activated the N-mode of the module, which is [COLOR="Red"]not[/COLOR] recommended because of a bug.

> wlan1     IEEE 802.11abg[COLOR="Red"]n[/COLOR]  ESSID:"fetta"  
In red should be "=1" to deactivate the N-mode.
> ```
# sudo -s "echo 'options [COLOR="Red"]iwlagn 11n_disable=0[/COLOR] 11n_disable50=0 swcrypto=1 swcrypto50=1' >> /etc/modprobe.d/options.conf" # sudo modprobe -r iwlagn && sudo modprobe iwlagn
```

---

### Post by chuckyanutsup on 2011-12-12
[SIZE=1]Thank you for your prompt reply :)

My old device was Atheros I believe. So N-mode is not recommended on this device due to a bug? Or is it just in general with 11.10? I didn't have problems with speed before changing to the Intel card, just wanted to try and push it past 150Mb. If the bug is 5100agn specific, then I'd be better off putting my old card back in as it was stable at 150Mb.

I'll remove the 2x config lines. That was just me trying various things.

Router details below 

[/SIZE][SIZE=1]Wireless Radio:[/SIZE][SIZE=1]Enable[/SIZE][SIZE=1]Name (SSID):[/SIZE][SIZE=1]fetta[/SIZE][SIZE=1]Channel:[/SIZE][SIZE=1]Auto (Current channel 1)[/SIZE][SIZE=1]Mode:[/SIZE][SIZE=1]11bgn mixed[/SIZE][SIZE=1]Channel Width:[/SIZE][SIZE=1]40MHz[/SIZE][SIZE=1]Max Tx Rate:[/SIZE][SIZE=1]300Mbps[/SIZE][SIZE=1]


> **praseodym said:**
> Remove those parameters. This file can be removed:
```
sudo rm /etc/modprobe.d/ath9k.conf
```because you have an Intel device, not Atheros. Which mode does the router send (b+g)? You activated the N-mode of the module, which is [/SIZE][SIZE=1][COLOR=Red]not[/COLOR][/SIZE][SIZE=1] recommended because of a bug.


In red should be "=1" to deactivate the N-mode.  [/SIZE][SIZE=1]

[/SIZE]

---

### Post by praseodym on 2011-12-12
Its in general with Intel devices using the iwlagn driver. N-mode deactivation is recommended.

If you go back to the Atheros device deactivating the hardware encryption as you already did is recommended to get full speed (little bug, too).

---

### Post by chuckyanutsup on 2011-12-12
Thanks mate, I looked through so many bug reports that I wasn't sure which if any applied to me. It's disappointing that I can't use my intel card above g speeds though. Looks like I'll have to go back to the Atheros card and a more stable 150Mb. It's not 300Mb, but it's not terrible either.

Is there any specific bug report you'd recommend I subscribe to?

> **praseodym said:**
> Its in general with Intel devices using the iwlagn driver. N-mode deactivation is recommended.

If you go back to the Atheros device deactivating the hardware encryption as you already did is recommended to get full speed (little bug, too).

---

### Post by chuckyanutsup on 2011-12-12
Just an update on the output for ```
dmesg | grep iwl
``` now that I've gotten rid of 
11n_disable50
disable_hw_scan


```
dmesg | grep iwl
[   21.283052] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   21.283055] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   21.283144] iwlagn 0000:08:00.0: enabling device (0000 -> 0002)
[   21.283155] iwlagn 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.283167] iwlagn 0000:08:00.0: setting latency timer to 64
[   21.283202] iwlagn 0000:08:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   21.305400] iwlagn 0000:08:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   21.305403] iwlagn 0000:08:00.0: Device SKU: 0Xb
[   21.307809] iwlagn 0000:08:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   21.307900] iwlagn 0000:08:00.0: irq 47 for MSI/MSI-X
[   21.505400] iwlagn 0000:08:00.0: loaded firmware version 8.83.5.1 build 33692
[   21.515174] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   37.224127] iwlagn 0000:08:00.0: Aggregation not enabled for tid 0 because load = 6
[   54.318975] iwlagn 0000:08:00.0: Aggregation not enabled for tid 6 because load = 0
[   59.658351] iwlagn 0000:08:00.0: Aggregation not enabled for tid 0 because load = 1
[   68.360275] iwlagn 0000:08:00.0: Aggregation not enabled for tid 0 because load = 3
[   72.619888] iwlagn 0000:08:00.0: iwlagn_tx_agg_start on ra = b0:48:7a:de:19:98 tid = 0
[  191.494726] iwlagn 0000:08:00.0: Aggregation not enabled for tid 6 because load = 1
[ 1007.752316] iwlagn 0000:08:00.0: iwlagn_tx_agg_start on ra = b0:48:7a:de:19:98 tid = 6
[ 9677.078982] iwlagn 0000:08:00.0: PCI INT A disabled
[ 9677.241887] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[ 9677.241890] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[ 9677.241982] iwlagn 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 9677.241996] iwlagn 0000:08:00.0: setting latency timer to 64
[ 9677.242038] iwlagn 0000:08:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[ 9677.264300] iwlagn 0000:08:00.0: device EEPROM VER=0x11f, CALIB=0x4
[ 9677.264307] iwlagn 0000:08:00.0: Device SKU: 0Xb
[ 9677.265320] iwlagn 0000:08:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 9677.265425] iwlagn 0000:08:00.0: irq 47 for MSI/MSI-X
[ 9677.269386] iwlagn 0000:08:00.0: loaded firmware version 8.83.5.1 build 33692
[ 9677.271703] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 9697.149040] iwlagn 0000:08:00.0: Aggregation not enabled for tid 0 because load = 10
[ 9700.843795] iwlagn 0000:08:00.0: Aggregation not enabled for tid 0 because load = 5
[ 9710.996701] iwlagn 0000:08:00.0: Aggregation not enabled for tid 0 because load = 1
[ 9729.386950] iwlagn 0000:08:00.0: Aggregation not enabled for tid 0 because load = 0
[ 9745.356050] iwlagn 0000:08:00.0: iwlagn_tx_agg_start on ra = b0:48:7a:de:19:98 tid = 0

```

---

### Post by praseodym on 2011-12-12
Did you also change to "11n_disable=1"?

---

### Post by chuckyanutsup on 2011-12-13
> **praseodym said:**
> Did you also change to "11n_disable=1"?
Not as yet. Won't that reduce my maximum speed to 54Mb? I'll change back to my old card next chance I get if there are no other workarounds.

---

### Post by chuckyanutsup on 2011-12-13
Thank you for your help [praseodym]("http://ubuntuforums.org/member.php?u=1411497"), I'm marking this as solved as it appears there is nothing further we can do until the bug gets fixed. I will keep an eye on the various bug reports to see if the issue gets resolved.

---

