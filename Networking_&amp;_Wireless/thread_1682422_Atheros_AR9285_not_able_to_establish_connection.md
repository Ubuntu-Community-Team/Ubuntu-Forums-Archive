---
title: "Atheros AR9285 not able to establish connection"
date: 2011-02-05
forum: Networking &amp; Wireless
---

### Post by gusbeto37 on 2011-02-05
After a while of experimenting by myself I came with the following, somewhat rudimentary SOLUTION:
I managed to fix the problem by installing the windows wireless driver utility. [Here is a tutorial]("https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html") on how to do it

So I just installed it, went to system/administration/windows wireless drivers and just installed it. Downloaded the file from [here]("http://www.nodevice.es/driver/AR9285/get64221.html")

It may not be the best way to fix it, but it does work. Still if you can use ethernet, dont hesitate to do it.






Hi all, this is my first post. I am kind of new to linux and have installed the lucid lynx ubuntu distro (10.04) and then "upgraded" it to ubuntu studio but it still says is the lucid lynx.

I got a Samsung Q430 laptop with the Atheros AR9285 wireless adapter.I have everything up and running EXCEPT my wireless card.

 The wireless card DOES work, it does see all the connections available, but when I choose to connect it does not, and keeps asking for the password. Weird thing is that when I use my samsung galaxy tab as the wireless adapter for its 3G signal, it does seem to work fine (although really slow). 

I have tried looking for a solution, some say to just install the drivers, but ubuntu does not recognize anything to need a driver except the video card.  I have installed linux-backports-modules-wireless-lucid-generic I have also tried the bleeding edge drivers, but nothing seems to fix the problem.

Any ideas?
Thanks for any help

---

### Post by gusbeto37 on 2011-02-05
Response from the command

```
sudo iwconfig
```

```
wlan0     IEEE 802.11bgn  ESSID:"Red de Gustavo Elizondo Flores"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on

```

```
lspci -v
```
returns
```
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Askey Computer Corp. Device 7167
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fc400000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k
```

Its supposed to connect to "Red de Gustavo Elizondo" but for some reason it does not and keeps asking for its password

---

### Post by wondr on 2011-02-06
I have the exact same problem. I have the wireless backports installed and ubuntu detects the card but when I'm trying to connect it just promts me for the password (which is correct)repeatedly.
I'm running 10.10.

I get similar outputs as op from iwconfig and lspci -v.

On rare occasions I connect to the network and then it's running stable but after reboot it goes back to normal :(

---

### Post by MorleyPotter on 2011-02-06
Just a thought, have you tried the madwifi drivers?
 
I had similar problems on an old laptop and these drivers fixed the problem.

---

### Post by wondr on 2011-02-06
Tried installing madwifi 0.9.4 drivers but ran into problems. When trying to "make" it I got kernel errors. Followed [this]("http://www.stchman.com/ath_drv.html") guide.

```
: make clean
./kernelversion.c.13: fatal error: linux/utrelease.h: The file doesn't exist
compilation terminated.
Makefile.inc:81: *** Cannot detect kernel version - please check compiler and KERNELPATH. Stop
```
(Translated command output.)

Any ideas?

---

### Post by MorleyPotter on 2011-02-06
> **wondr said:**
> Tried installing madwifi 0.9.4 drivers but ran into problems. When trying to "make" it I got kernel errors. Followed [this]("http://www.stchman.com/ath_drv.html") guide.
 
```
: make clean
./kernelversion.c.13: fatal error: linux/utrelease.h: The file doesn't exist
compilation terminated.
Makefile.inc:81: *** Cannot detect kernel version - please check compiler and KERNELPATH. Stop
```
(Translated command output.)
 
Any ideas?
 
[http://madwifi.org/HOWTO/](http://madwifi.org/HOWTO/) - Official site may be better for you?

---

### Post by wondr on 2011-02-06
Doesn't seem to be the instructions that's the problem. Same stuff on the official. /:
Gonna try ndiswrapper and see what happens.
thanks anyways

---

### Post by gusbeto37 on 2011-02-06
apparently the madwifi page is no longer the one provided above, every single link gives a 403 or 404. The proyect has since moved to [http://madwifi-project.org/](http://madwifi-project.org/) just so you know. 

Well, either way I cannot seem to install it, and the problem I do not think is the download, but the file itself as apparently it tries to do invalid things>

> gustavo@gustavo-laptop:~/Downloads/madwifi-0.9.4$ make
Checking requirements... ok.
Checking kernel configuration... ok.
touch: cannot touch `svnversion.h.tmp': Permission denied
cp: cannot stat `svnversion.h.tmp': No such file or directory
make -C /lib/modules/2.6.32-28-generic-pae/build SUBDIRS=/home/gustavo/Downloads/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-28-generic-pae'
  CC [M]  /home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.o
Assembler messages:
Fatal error: can't create /home/gustavo/Downloads/madwifi-0.9.4/ath/.tmp_if_ath.o: Permission denied
In file included from /home/gustavo/Downloads/madwifi-0.9.4/ath/../net80211/ieee80211_monitor.h:45,
                 from /home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:71:
/home/gustavo/Downloads/madwifi-0.9.4/ath/../ath/if_athvar.h:98: error: conflicting types for 'irqreturn_t'
include/linux/irqreturn.h:16: note: previous declaration of 'irqreturn_t' was here
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_attach':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:402: error: 'struct net_device' has no member named 'priv'
cc1: warnings being treated as errors
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:626: error: pointer targets in passing argument 1 of 'strcpy' differ in signedness
/usr/src/linux-headers-2.6.32-28-generic-pae/arch/x86/include/asm/string_32.h:9: note: expected 'char *' but argument is of type 'u_int8_t *'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:678: error: 'struct net_device' has no member named 'open'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:679: error: 'struct net_device' has no member named 'stop'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:680: error: 'struct net_device' has no member named 'hard_start_xmit'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:681: error: 'struct net_device' has no member named 'tx_timeout'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:683: error: 'struct net_device' has no member named 'set_multicast_list'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:684: error: 'struct net_device' has no member named 'do_ioctl'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:685: error: 'struct net_device' has no member named 'get_stats'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:686: error: 'struct net_device' has no member named 'set_mac_address'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:687: error: 'struct net_device' has no member named 'change_mtu'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_detach':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:958: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:1005: error: 'struct net_device' has no member named 'stop'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_vap_create':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:1014: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:1084: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_vap_delete':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:1248: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_suspend':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:1350: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_resume':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:1359: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_intr':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:1652: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_bmiss_tasklet':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:1843: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_init':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:1886: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_stop_locked':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:2014: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_stop':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:2078: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_reset':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:2182: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_startraw':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:2343: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_hardstart':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:2558: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_mgtstart':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:2875: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_alloc':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:3237: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_delete':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:3304: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_set':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:3380: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_update_begin':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:3395: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_update_end':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:3416: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_mode_init':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:3504: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_updateslot':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:3555: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_beacon_dturbo_config':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:3585: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_beacon_dturbo_update':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:3633: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_turbo_switch_mode':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:3776: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_bstuck_tasklet':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:4368: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_node_alloc':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:4820: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_node_cleanup':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:4855: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_node_free':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:4909: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rx_capture':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:5404: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_capture':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:5437: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_recv_mgmt':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:5502: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rx_tasklet':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:5574: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_grppoll_start':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:6013: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:6053: error: pointer targets in passing argument 1 of 'sscanf' differ in signedness
include/linux/kernel.h:197: note: expected 'const char *' but argument is of type 'u_int8_t *'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:6056: error: pointer targets in passing argument 1 of 'strcmp' differ in signedness
/usr/src/linux-headers-2.6.32-28-generic-pae/arch/x86/include/asm/string_32.h:21: note: expected 'const char *' but argument is of type 'const u_int8_t *'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:6056: error: pointer targets in passing argument 2 of 'strcmp' differ in signedness
/usr/src/linux-headers-2.6.32-28-generic-pae/arch/x86/include/asm/string_32.h:21: note: expected 'const char *' but argument is of type 'u_int8_t *'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:6060: error: pointer targets in passing argument 1 of 'sscanf' differ in signedness
include/linux/kernel.h:197: note: expected 'const char *' but argument is of type 'u_int8_t *'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:6061: error: pointer targets in passing argument 1 of 'strlen' differ in signedness
/usr/src/linux-headers-2.6.32-28-generic-pae/arch/x86/include/asm/string_32.h:30: note: expected 'const char *' but argument is of type 'u_int8_t *'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:6061: error: pointer targets in passing argument 1 of 'strlen' differ in signedness
/usr/src/linux-headers-2.6.32-28-generic-pae/arch/x86/include/asm/string_32.h:30: note: expected 'const char *' but argument is of type 'u_int8_t *'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_grppoll_stop':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:6226: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_wme_update':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:6441: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_uapsd_flush':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:6460: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_start':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:6655: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_tasklet_q0':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:7495: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_tasklet_q0123':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:7516: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_tasklet':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:7551: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_timeout':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:7574: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_calibrate':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:7937: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_scan_start':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:8003: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_scan_end':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:8023: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_set_channel':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:8041: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_set_coverageclass':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:8057: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_mhz2ieee':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:8067: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_newstate':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:8082: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_setup_stationkey':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:8471: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_newassoc':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:8631: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_getchannels':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:8662: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_xr_rate_setup':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:8832: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_setup_subrates':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:8861: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rate_setup':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:8904: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_getstats':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9141: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_set_mac_address':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9164: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_change_mtu':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9196: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_ioctl':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9283: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_sysctl_halparam':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9370: error: passing argument 5 of 'proc_dointvec' from incompatible pointer type
include/linux/sysctl.h:985: note: expected 'loff_t *' but argument is of type 'size_t *'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9370: error: too many arguments to function 'proc_dointvec'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9562: error: passing argument 5 of 'proc_dointvec' from incompatible pointer type
include/linux/sysctl.h:985: note: expected 'loff_t *' but argument is of type 'size_t *'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9562: error: too many arguments to function 'proc_dointvec'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: At top level:
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9574: error: initialization from incompatible pointer type
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9580: error: initialization from incompatible pointer type
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9586: error: initialization from incompatible pointer type
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9592: error: initialization from incompatible pointer type
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9598: error: initialization from incompatible pointer type
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9604: error: initialization from incompatible pointer type
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9610: error: initialization from incompatible pointer type
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9616: error: initialization from incompatible pointer type
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9623: error: initialization from incompatible pointer type
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9630: error: initialization from incompatible pointer type
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9636: error: initialization from incompatible pointer type
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9642: error: initialization from incompatible pointer type
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9648: error: initialization from incompatible pointer type
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9654: error: initialization from incompatible pointer type
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9660: error: initialization from incompatible pointer type
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9667: error: initialization from incompatible pointer type
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9673: error: initialization from incompatible pointer type
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9680: error: initialization from incompatible pointer type
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9686: error: initialization from incompatible pointer type
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_announce':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9779: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rcv_dev_event':
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9926: error: 'struct net_device' has no member named 'priv'
/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.c:9928: error: 'struct net_device' has no member named 'open'
make[3]: *** [/home/gustavo/Downloads/madwifi-0.9.4/ath/if_ath.o] Error 2
make[2]: *** [/home/gustavo/Downloads/madwifi-0.9.4/ath] Error 2
make[1]: *** [_module_/home/gustavo/Downloads/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-28-generic-pae'
make: *** [modules] Error 2

---

### Post by gusbeto37 on 2011-02-06
Hi all,

I managed to fix the problem by installing the windows wireless driver utility. [Here is a tutorial]("https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html") on how to do it

So I just installed it, went to system/administration/windows wireless drivers and just installed it. Downloaded the file from [here]("http://www.nodevice.es/driver/AR9285/get64221.html")

It may not be the best way to fix it, but it does work. Still if you can use ethernet, dont hesitate to do it.

---

### Post by MorleyPotter on 2011-02-09
glad to hear your problem is resolved.

---

