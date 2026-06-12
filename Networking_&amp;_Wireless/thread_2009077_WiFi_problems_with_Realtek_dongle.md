---
title: "WiFi problems with Realtek dongle"
date: 2012-06-23
forum: Networking &amp; Wireless
---

### Post by CargoPlayer on 2012-06-23
I recently purchased an old Toshiba Satellite laptop, to set up Ubuntu 12.04 as a LAMP enviroment to teach myself some new development tricks. It has a built in wireless card, but it was not working well - it would lock up the browser usually by the second page click. So I bought a Realtek wireless USB adapter, which says on the package works with Linux.

It does that thing that I have seen posted about a number of times, where it works fine for a bit, then disconnects. If I leave it for a bit, it can reconnect, or I have to reboot. Although I have gone into Edit Connections, and set the internal wireless connection to not start up, it seems to do so. When I go to reconnect the Realtek connection, the buld in card seems to start up a the same time, which is not good, of course.

I have found the drivers for the USB dongle, and wanted to install them to see if that would help, but cannot for the life of me figure out how to do that. Every note I find on the internet says to use the 'Additional Drivers' app, but that doesn't seem to find anything, and I can't direct it to a local USB drive. I don't know whether this means that there are no additional drivers, or it doesn't recognize the USB dongle, and therefore doesn't look for the drivers.

Everything is fine when I plug into the router directly. But I'm not much of one for sitting in my basement.

Here is the result of the following commands, as requested in another post. Any suggestions, help, thoughts would be very much appreciated.

cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod


rick@rick-test:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux rick-test 3.2.0-26-generic-pae #41-Ubuntu SMP Thu Jun 14 16:45:14 UTC 2012 i686 i686 i386 GNU/Linux

rick@rick-test:~$ lspci -nnk | grep -iA2 net
04:02.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] [168c:001a] (rev 01)
    Subsystem: Askey Computer Corp. Device [144f:7094]
    Kernel driver in use: ath5k
--
04:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Toshiba America Info Systems Device [1179:ff00]
    Kernel driver in use: 8139too
rick@rick-test:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 8564:1000  
Bus 001 Device 003: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN

rick@rick-test:~$ iwconfig
lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"dharma"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 14:79:C5:2D:18:BF   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:15   Missed beacon:0

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

rick@rick-test:~$ rfkill list all
0: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

rick@rick-test:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
joydev                 17393  0 
arc4                   12473  4 
snd_atiixp             19337  2 
snd_seq_midi           13132  0 
snd_atiixp_modem       18604  0 
snd_ac97_codec        106082  2 snd_atiixp,snd_atiixp_modem
ac97_bus               12642  1 snd_ac97_codec
ath5k                 145127  0 
ath                    19387  1 ath5k
snd_pcm                80845  3 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_rawmidi            25424  1 snd_seq_midi
ip6t_LOG               16846  4 
xt_hl                  12465  6 
ip6t_rt                12473  3 
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13139  1 nf_conntrack_ipv6
snd_seq_midi_event     14475  1 snd_seq_midi
ipt_REJECT             12512  1 
ipt_LOG                12783  5 
xt_limit               12541  12 
pcmcia                 39791  0 
xt_tcpudp              12531  18 
rtl8192cu              97722  0 
xt_addrtype            12596  4 
rtl8192c_common        69519  1 rtl8192cu
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
rtlwifi                95804  1 rtl8192cu
snd_timer              28931  2 snd_pcm,snd_seq
xt_state               12514  14 
mac80211              436455  4 ath5k,rtl8192cu,rtl8192c_common,rtlwifi
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
radeon                733693  2 
ip6table_filter        12711  1 
ip6_tables             18432  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12595  0 
nf_nat                 24959  1 nf_nat_ftp
nf_conntrack_ipv4      19084  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack           73847  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
x_tables               21974  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd                    62064  12 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
psmouse                72919  0 
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
serio_raw              13027  0 
cfg80211              178679  4 ath5k,ath,rtlwifi,mac80211
ttm                    65344  1 radeon
soundcore              14635  1 snd
drm_kms_helper         45466  1 radeon
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
drm                   197692  4 radeon,ttm,drm_kms_helper
rfcomm                 38139  0 
snd_page_alloc         14108  3 snd_atiixp,snd_atiixp_modem,snd_pcm
bnep                   17830  2 
parport_pc             32114  0 
i2c_piix4              13093  0 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
video                  19068  0 
i2c_algo_bit           13199  1 radeon
mac_hid                13077  0 
shpchp                 32325  0 
ati_agp                13242  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
pata_atiixp            12999  2 
8139too                23283  0 
8139cp                 26759  0 
usb_storage            39646  1

---

### Post by wildmanne39 on 2012-06-23
Hi, we have about equal chance of getting either device to work, maybe better odds with the internal card, please let us know if you want to try to get the internal card to work properly before we blacklist it's driver.
Thanks

---

### Post by CargoPlayer on 2012-06-24
If you think it's easier to get the internal card to work, then I'm happy with that. Do you need more info? At the same time, as there a USB device that you know will work?

---

### Post by wildmanne39 on 2012-06-24
Hi please do:
```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```
No I am not sure which usb adapter to recommend because there are so many different chip sets out there.

Also make sure your routers encryption is set to just wpa2, and the channel to 1 or 11.

You will need to make sure that in network manager the encryption is set to wpa/wpa2.

You will need to keep your usb adapter unplugged while we work on the internal card.
Thanks

---

### Post by CargoPlayer on 2012-06-24
Done. I have reset the router to channgel 11, WPA2.

Command results:

echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
options ath5k nohwcrypt=1

sudo modprobe -rfv ath5k
rmmod /lib/modules/3.2.0-26-generic-pae/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
rmmod /lib/modules/3.2.0-26-generic-pae/kernel/drivers/net/wireless/ath/ath.ko

sudo modprobe -v ath5k
insmod /lib/modules/3.2.0-26-generic-pae/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.2.0-26-generic-pae/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko nohwcrypt=1

---

### Post by wildmanne39 on 2012-06-24
Hi, give it a few minutes and see if it is better.
Thanks

---

### Post by CargoPlayer on 2012-06-24
It seems to be working beautifully. Thanks so much.

[on edit] I should ask, is that permanent, or is there more to be done?

---

### Post by wildmanne39 on 2012-06-24
Hi, it is permanent, please use thread tools at the top of the page to mark the thread solved.
Thanks

---

### Post by CargoPlayer on 2012-06-24
Done, and thanks again.

---

