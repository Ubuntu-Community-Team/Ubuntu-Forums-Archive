---
title: "Howto Install Madwifi for Atheros in Lucid"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by drpjkurian on 2010-05-15
Hi guys in this thread you will the instructions to install [COLOR="Red"]**Madwifi**[/COLOR] drivers for [COLOR="Red"]**Atheros**[/COLOR] wireless cards. Please follow the instructions to the word.

Open the 'terminal' by navigating through Applications-->Accessories--> Terminal

Now type the following commands in terminal

1. ```
sudo nano /etc/apt/sources.list
```

From there make sure you uncomment anything that starts with "deb" in there. So changer it from "#deb" to "deb" Something along thoes lines. To exit and save hit "CTRL+X" the answer "YES" to do you want to save, then finally hit "ENTER"

2. ```
sudo apt-get update && sudo apt-get upgrade
```

3. ```
sudo apt-get install build-essential libssl-dev
```

4. ```
sudo apt-get install linux-headers-`uname -r`
```

5. ```
sudo apt-get install subversion
```

6. ```
sudo -i
```

7. ```
sudo svn checkout http://svn.madwifi-project.org/madwifi/trunk/ madwifi-ng
```

8. ```
cd madwifi-ng
```

9. ```
echo "" >> /etc/modprobe.d/blacklist
```

10. ```
echo "#Remove To Install MadWIFI Drivers" >> /etc/modprobe.d/blacklist
```

11. ```
echo "blacklist ath9k" >> /etc/modprobe.d/blacklist
```

12. ```
echo "blacklist ath5k" >> /etc/modprobe.d/blacklist
```

13. ```
make && make install
```

14. ```
echo ath_pci >> /etc/modules
```

Restart your machine.
It should work

Well i use Wicd to connect to the wireless modem
To install Wicd type the following commands in terminal
```
sudo apt-get update
```

```
sudo apt-get install wicd
```


:KS Kernal updates of your system will kill your driver. Well no need to worry about that.Just recompile your driver.
For that you open a terminal and type the command```
sudo -i
``` and just repeat the steps from No 8. Your madwifi will cone back to life again.:popcorn:

Best of Luck
Dr Kurian

---

### Post by reckik on 2010-06-15
Have had some problems with keeping the connection on my machine. Am using it now for a few hours and appears to be working. Hope the connection wont drop again. Actually am using it on my Crunchbang machine.

this appears to be working on my acer aspire one with a atheros ar5001 chipset.

---

### Post by drpjkurian on 2010-06-15
Hi Reckik

Please install the backport modules of wireless and backport modules of lucid generic by synaptic package manager if you are getting intermittent connections.

please see the screenshot of post 43 of this thread if you have doubts
[http://ubuntuforums.org/showthread.php?p=9452499#post9452499](http://ubuntuforums.org/showthread.php?p=9452499#post9452499)

---

### Post by TomDoe on 2010-06-15
You Sir are my hero!
I've struggled for a few days with the wifi on my Acer Aspire One A150, but your guide got it working fully and I can now enjoy my Ubuntu Netbook Remix.
A big thanks to you and the rest of this community for all your time and effort, its really appreciated!! :grin:

---

### Post by drpjkurian on 2010-06-16
oh its you...i have shot you a mail.  
thanks buddy.

---

### Post by reckik on 2010-06-19
after following this my connection did get better. It did sometimes stop to connect thought. I installed the files u recommended, but it doesnt seem to get better.

I get an error, but my computer then freezs. As soon as it does again ill try to post the dmesg log. 

It says something about unable to change channel

thx
harm

---

### Post by brion@cbkidder.com on 2010-06-19
Thanks DrKurian. Technically this fix did get my Acer Aspire's wireless working, but at an alarmingly slow speed. My other Ubuntu laptop gets about 9.5MBPS but this Acer is only getting 0.9MBPS running wicd and madwifi.

It's a shame the wireless won't work on this netbook because I just hate Windows. But a netbook without wireless is just silly so I guess it's a win for MS this time...

Thanks again for the tutorial tho.

---

### Post by reckik on 2010-06-21
well this doesn't work at all for me. Crunchbang keeps freezing up now, and i know its the wireless driver. Its doing exactly the same as Ubuntu did when i installed it. Sometimes after a few minutes, sometimes after a few hours or even minutes. Really annoying cause i have to do a hard reset - nothing else works.

Can i still go back to my previous drivers? or is it better to reinstall crunchbang, just had it installed last week.

thx

---

### Post by drpjkurian on 2010-06-23
> **reckik said:**
> well this doesn't work at all for me. Crunchbang keeps freezing up now, and i know its the wireless driver. Its doing exactly the same as Ubuntu did when i installed it. Sometimes after a few minutes, sometimes after a few hours or even minutes. Really annoying cause i have to do a hard reset - nothing else works.

Can i still go back to my previous drivers? or is it better to reinstall crunchbang, just had it installed last week.

thx

Hi
I am not sure whether the solutions for Ubuntu which is debian based solve crunchbag issues. Wireless drivers unlikely freezes the whole system. So I presume your 'freeze' has nothing to do with the wireless driver.

Well why not try the crunchbag forums?

---

### Post by drpjkurian on 2010-06-23
> **brion@cbkidder.com said:**
> Thanks DrKurian. Technically this fix did get my Acer Aspire's wireless working, but at an alarmingly slow speed. My other Ubuntu laptop gets about 9.5MBPS but this Acer is only getting 0.9MBPS running wicd and madwifi.

It's a shame the wireless won't work on this netbook because I just hate Windows. But a netbook without wireless is just silly so I guess it's a win for MS this time...

Thanks again for the tutorial tho.

Hi
Why not give a last try by following the instructions mentioned in post#3 of this thread.

---

### Post by ledenjes on 2010-07-14
HALLELUJAAAAAAAAAAAAAAAAHHHHHHHHHHHHHHHHH!!!!!!!!!!!!!!
FINALLYYYYYYYYYYYYYYYYYYY!!!!!!!!!!!!!!!!!!!!!!!!!!

THANK YOU!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

All Linux distributions were driving me completely nuts since about october 2009. Since then, Internet was so terribly/horribly slow on my laptop.

I have the Atheros AR5005G 802.11abg WLAN controller. Apparantly, the ath5k driver is absolutely worthless for my kind of WLAN controller.

I'm so glad that the madwifi driver resolves this matter.

---

### Post by drpjkurian on 2010-07-15
hi
Thanks buddy

---

### Post by schnelle on 2010-09-03
Thanks a lot buddy! It works :)

---

### Post by fig_wright on 2010-09-04
Unfortunately this didnt make any difference for me - laptop wireless keeps dropping out and wont reconnect. I have a Toshiba with AR2413 802.11bg (although Windows is convinced it is an AR5000!)

It's definitely using the ath_pci driver instead of the ath5000.

What's bizzare is that if I boot into windows then back into Linux the wifi will work for 5 mins and then die. I guess the linux driver puts the card into some crazy mode that only he win driver can rescue.

I've tried installing:
linux-backports-modules-wireless-lucid-generic
linux-backports-modules-wireless-2.6.32-24-generic

but that made no difference at all. This laptop is essentially unusable without wifi, so it will have to stay in Windows :(

---

### Post by szogun on 2010-10-12
I've done everything step by step. Oh sorry svn checkout didn't work so I downloaded packed files and put in folder. After reboot i've checked 'lshw -c network' and i get this ```
xxxxx@xx:~$ sudo lshw -c network
[sudo] password for xxxxx: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
       resources: memory:faaf0000-faafffff
```Can somebody help me? I don't know what i've done wrong.
Oh and wifi doesn't work.

---

### Post by Speedwagon on 2010-10-12
I got up to the make command, and it gave me an error:

```
make && make install
make: *** No targets specified and no makefile found.  Stop.

```

---

### Post by drpjkurian on 2010-10-13
Hi
You have to navigate to the folder where you have copied the files/folder for installation by using 'cd' commands and then try the command 'make install'. If you are not able to solve this issue, then please follow the instructions mentioned in my first post..

---

### Post by RainKap on 2010-10-13
Another "Thank you" from a (nearly) satisfied customer. I found that there's one step which I needed to take & which is missing from your instructions in the first post of this thread: in /etc/modprobe.d on my Aspire One (clean install of Lucid) there's a file blacklist-ath_pci.conf, which (as its name suggests) blacklists ath_pci. Once I'd commented out that line in the file, my wireless worked fine. Maybe a small edit to your instructions would be in order?

Thanks again

Ian

---

### Post by szogun on 2010-10-15
I've decided to try one more time and i notice that i get error in "make && make install"
```
root@Asusik:/home/szogun/Desktop/madwifi-0.9.4# make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.32-25-generic/build SUBDIRS=/home/szogun/Desktop/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-25-generic'
  CC [M]  /home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.o
In file included from /home/szogun/Desktop/madwifi-0.9.4/ath/../net80211/ieee80211_monitor.h:45,
                 from /home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:71:
/home/szogun/Desktop/madwifi-0.9.4/ath/../ath/if_athvar.h:98: error: conflicting types for 'irqreturn_t'
include/linux/irqreturn.h:16: note: previous declaration of 'irqreturn_t' was here
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_attach':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:402: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:678: error: 'struct net_device' has no member named 'open'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:679: error: 'struct net_device' has no member named 'stop'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:680: error: 'struct net_device' has no member named 'hard_start_xmit'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:681: error: 'struct net_device' has no member named 'tx_timeout'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:683: error: 'struct net_device' has no member named 'set_multicast_list'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:684: error: 'struct net_device' has no member named 'do_ioctl'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:685: error: 'struct net_device' has no member named 'get_stats'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:686: error: 'struct net_device' has no member named 'set_mac_address'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:687: error: 'struct net_device' has no member named 'change_mtu'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_detach':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:958: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:1005: error: 'struct net_device' has no member named 'stop'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_vap_create':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:1014: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:1084: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_vap_delete':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:1248: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_suspend':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:1350: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_resume':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:1359: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_intr':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:1652: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_bmiss_tasklet':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:1843: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_init':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:1886: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_stop_locked':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:2014: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_stop':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:2078: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_reset':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:2182: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_startraw':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:2343: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_hardstart':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:2558: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_mgtstart':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:2875: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_alloc':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:3237: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_delete':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:3304: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_set':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:3380: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_update_begin':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:3395: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_update_end':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:3416: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_mode_init':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:3504: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_updateslot':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:3555: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_beacon_dturbo_config':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:3585: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_beacon_dturbo_update':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:3633: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_turbo_switch_mode':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:3776: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_bstuck_tasklet':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:4368: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_node_alloc':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:4820: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_node_cleanup':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:4855: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_node_free':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:4909: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rx_capture':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:5404: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_capture':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:5437: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_recv_mgmt':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:5502: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rx_tasklet':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:5574: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_grppoll_start':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:6013: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_grppoll_stop':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:6226: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_wme_update':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:6441: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_uapsd_flush':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:6460: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_start':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:6655: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_tasklet_q0':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:7495: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_tasklet_q0123':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:7516: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_tasklet':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:7551: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_timeout':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:7574: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_calibrate':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:7937: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_scan_start':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:8003: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_scan_end':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:8023: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_set_channel':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:8041: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_set_coverageclass':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:8057: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_mhz2ieee':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:8067: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_newstate':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:8082: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_setup_stationkey':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:8471: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_newassoc':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:8631: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_getchannels':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:8662: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_xr_rate_setup':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:8832: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_setup_subrates':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:8861: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rate_setup':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:8904: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_getstats':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9141: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_set_mac_address':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9164: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_change_mtu':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9196: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_ioctl':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9283: error: 'struct net_device' has no member named 'priv'
cc1: warnings being treated as errors
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_sysctl_halparam':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9370: error: passing argument 5 of 'proc_dointvec' from incompatible pointer type
include/linux/sysctl.h:985: note: expected 'loff_t *' but argument is of type 'size_t *'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9370: error: too many arguments to function 'proc_dointvec'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9562: error: passing argument 5 of 'proc_dointvec' from incompatible pointer type
include/linux/sysctl.h:985: note: expected 'loff_t *' but argument is of type 'size_t *'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9562: error: too many arguments to function 'proc_dointvec'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: At top level:
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9574: error: initialization from incompatible pointer type
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9580: error: initialization from incompatible pointer type
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9586: error: initialization from incompatible pointer type
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9592: error: initialization from incompatible pointer type
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9598: error: initialization from incompatible pointer type
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9604: error: initialization from incompatible pointer type
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9610: error: initialization from incompatible pointer type
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9616: error: initialization from incompatible pointer type
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9623: error: initialization from incompatible pointer type
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9630: error: initialization from incompatible pointer type
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9636: error: initialization from incompatible pointer type
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9642: error: initialization from incompatible pointer type
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9648: error: initialization from incompatible pointer type
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9654: error: initialization from incompatible pointer type
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9660: error: initialization from incompatible pointer type
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9667: error: initialization from incompatible pointer type
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9673: error: initialization from incompatible pointer type
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9680: error: initialization from incompatible pointer type
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9686: error: initialization from incompatible pointer type
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_announce':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9779: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rcv_dev_event':
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9926: error: 'struct net_device' has no member named 'priv'
/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.c:9928: error: 'struct net_device' has no member named 'open'
make[3]: *** [/home/szogun/Desktop/madwifi-0.9.4/ath/if_ath.o] Error 1
make[2]: *** [/home/szogun/Desktop/madwifi-0.9.4/ath] Error 2
make[1]: *** [_module_/home/szogun/Desktop/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'
make: *** [modules] B&#322;&#261;d 2
```I really don't know what this means. 
'iwconfig' shows
```
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

pan0      no wireless extensions.
```
'lshw -c network' shows
```
szogun@Asusik:~$ sudo lshw -c network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
       resources: memory:faaf0000-faafffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: d
       bus info: pci@0000:00:0d.0
       logical name: eth0
       version: 10
       serial: 00:1e:8c:5d:92:5c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.102 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:17 ioport:d400(size=256) memory:febfcc00-febfccff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

Can somebody help me ?

---

### Post by flash63 on 2010-10-15
Hello,
you better use  version 0.10.5.6

You can find all Madwifi Snapshots here [http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/)

```
sudo apt-get install linux-headers-$(uname -r) build-essential
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r4126-20100324.tar.gz
tar xvf madwifi-hal-0.10.5.6-r4126-20100324.tar.gz
cd madwifi-hal-0.10.5.6-r*
make
sudo make uninstall
sudo make install
```

Change the Entries in /etc/modprobe.d/blacklist-ath_pci.conf
```
sudo gedit /etc/modprobe.d/blacklist-ath_pci.conf
```
```
...
# blacklist ath_pci
blacklist ath5k
```
Restart your system an check it out
```
modinfo ath_pci | egrep 'versi|filen'
lsmod | grep ath
dmesg | grep ath
iwconfig
iwlist chan
sudo iwlist scan
```

Try to connect.

---

### Post by szogun on 2010-10-15
I've done every thing this time there was no errors.
After restart i made what u said. Thats result
```
szogun@Asusik:~$ modinfo ath_pci | egrep 'versi|filen'
filename:       /lib/modules/2.6.32-25-generic/net/ath_pci.ko
version:        svn r4126 (branch madwifi-hal-0.10.5.6)
srcversion:     8A443DE7DABEFD2C364037B
vermagic:       2.6.32-25-generic SMP mod_unload modversions 586 
szogun@Asusik:~$ lsmod | grep ath
ath_rate_sample        11700  1 
ath_pci               201468  0 
wlan                  220754  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               301194  3 ath_rate_sample,ath_pci

szogun@Asusik:~$ dmesg | grep ath
[    0.498280] device-mapper: multipath: version 1.1.0 loaded
[    0.498284] device-mapper: multipath round-robin: version 1.0.0 loaded
[   15.849328] ath_hal: module license 'Proprietary' taints kernel.
[   16.104348] ath_pci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.104364] ath_pci 0000:02:00.0: setting latency timer to 64
[   16.599735] MadWifi: ath_attach: Switching rfkill capability off.
[   16.745895] ath_pci: wifi0: Atheros 5424/2424: mem=0xfaaf0000, irq=16
[   29.008035] ath0: no IPv6 routers present

szogun@Asusik:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

pan0      no wireless extensions.

szogun@Asusik:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

wifi0     no frequency information.

ath0      22 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

vboxnet0  no frequency information.

pan0      no frequency information.

szogun@Asusik:~$ sudo iwlist scan
[sudo] password for szogun: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results

vboxnet0  Interface doesn't support scanning.

pan0      Interface doesn't support scanning.
``` Wifi still doesn't work. 
And is this ok?
```
[   16.745895] ath_pci: wifi0: Atheros 5424/2424: mem=0xfaaf0000, irq=16
``` i have atheros AR5001.

P.S.
I must change something in wicd? Wireless interface to ath0?

---

### Post by flash63 on 2010-10-15
Ok,
looks good so far, but only Chanel 1-11 are supported. I don't know what locale settings are required. We can change that.

Activate channel 1 to 13
```
echo 'options ath_pci rfkill=0 countrycode=276' | sudo tee -a /etc/modprobe.d/ath_pci.conf
sudo modprobe -rf ath_pci
sudo modprobe ath_pci
iwlist ath0 chan
rfkill list
```

Manual scan again
```
sudo iwlist ath0 scan
```
Try to find your own Network.

---

### Post by szogun on 2010-10-15
Still nothing. At home we use chanel 8.
```
szogun@Asusik:~$ echo 'options ath_pci rfkill=0 countrycode=276' | sudo tee -a /etc/modprobe.d/ath_pci.conf
options ath_pci rfkill=0 countrycode=276
szogun@Asusik:~$ sudo modprobe -rf ath_pci
szogun@Asusik:~$ sudo modprobe ath_pci
szogun@Asusik:~$ iwlist ath0 chan
ath0      no frequency information.

szogun@Asusik:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
szogun@Asusik:~$ sudo iwlist ath0 scan
ath0      Interface doesn't support scanning.
```

---

### Post by flash63 on 2010-10-15
Restart and test again.

---

### Post by szogun on 2010-10-15
Done but result is still the same.

---

### Post by flash63 on 2010-10-15
The ath5k driver does not work also?

Exist a WLAN-Switch in Front of your Laptop?  Works your Wifi with Windows?

Maybe it's a hardware damage!? Can you try another Live-CD (Distribution).

---

### Post by szogun on 2010-10-15
ath5k show networks but when it connects u have maybe 3 minutes and its down, its common isue with ath cards on linux.
WLAN-Switch exist and it's on "ON". When i had windows for few days a long time ago wlan worked great.
Hardware isn't damaged on 9.04 wlan worked also great (but my graphic card didn't work). I think i can download other distros, but i tried 10.10 and it's the same problem on ath5k it connects for 1-2 minutes and thats all.

---

### Post by pwabrahams on 2010-10-15
I was running my Atheros-based system under 10.04 Lucid just fine, but I cannot get a wireless connection after upgrading (?) to Meerkat.  My wireless is able to detect the router without any trouble, but the password authentication for WPA fails every time.  (I verified via a Windows partition that the password itself is OK.)  I've tried various permutations of blacklisting ath5k and ath9k; it seems that blacklisting ath9k causes the network itself not to be detected, but none of the permutations solves the problem.  I've reinstalled madwifi and wicd but that doesn't help either.  I'm using the wicd interface to try to make the connection.

One other clue: the following message appeared three times in dmesg:
> ath9k: Two wiphys trying to scan at the same time


Are others having similar troubles with Meerkat?  Any solutions?

---

### Post by flash63 on 2010-10-16
To szogun ...
You use wicd. The Network-Manager was copletely removed?
```
sudo apt-get remove --purge network-manager network-manager-gnome
```

Go back to ath5k. Change the entry in /etc/modprobe.d/blacklist-ath_pci.conf
```
...
blacklist ath_pci
# blacklist ath5k
```and restart. Connect.

Some Systeminformation please
```
uname -a
lspci -nnk | grep -i net -A2
lsmod
ifconfig
iwconfig
iwlist chan
sudo iwlist scan     # mark your own Cell
```

Try to find the error when the connection fails after a while
```
dmesg > dmesg.txt
iwconfig
ifconfig
```
The dmesg output is very long and therefore redirected to a text file. Attach the file here. I'd like to seen the complete output.

---

### Post by drpjkurian on 2010-10-16
Hi Pwarbraham
Please see this [link]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093"), It may help you out

---

### Post by pwabrahams on 2010-10-16
I had the wireless working just fine in Lucid, thanks in great part to Dr. Kurian.  The problem I have now is that the methods I used in Lucid don't seem to work in Meerkat. The symptom is also unusual: an inability to recognize the WPA/PSK password as being correct.  In other words, it behaves just as though I'm using an incorrect password, even though the password is correct.

---

### Post by ledenjes on 2010-12-10
> **pwabrahams said:**
> I had the wireless working just fine in Lucid, thanks in great part to Dr. Kurian.  The problem I have now is that the methods I used in Lucid don't seem to work in Meerkat. The symptom is also unusual: an inability to recognize the WPA/PSK password as being correct.  In other words, it behaves just as though I'm using an incorrect password, even though the password is correct.The method worked even in Ubuntu 10.04, but indeed no longer in Ubuntu 10.10 (Meerkat). After some error messages, which I ignored, my wireless internet stopped working, completely. I had to re-install Ubuntu from scratch. I am not giving up, though. If I find a way, I'll let you know how I resolved it.

---

### Post by shadramon on 2011-04-28
Thanks..i was struggling until i found this thread :D:D:D:D

*FYI I'm using Ubuntu 10.10 Maverick Meerkat and i started from step 8.

---

### Post by drpjkurian on 2011-05-01
most welcome buddy

---

### Post by budde on 2011-05-03
Oh my God I love you so much!

I have had so many problems with my ath9k driver. The endless bad password/reconnect loop was the most annyoing one. Been trying everything, all different kinds of encryptions and passwords and then I found this thread and voila! Problem solved.

Thank you thank you thank you!

EDIT: Apparently the issue is still there. Being asked for password again and again :(

---

### Post by Astroe on 2011-06-12
Thanks Doc :) Back a few months ago I gave up on Linux all together because every time I tried to install the madwifi drivers, I screwed it up so badly that the only way I knew to fix it was re-installing the whole system.

So now I have them running, but I have a question, why is it going so slowly? I'm running Kubuntu 11.04 dual-booted with Win 7 (For GTA) and I know my ISP is throttling my internets but before the install of the madwifi I was still pulling 150 - 160kb/s, now it's down to 15 - 20 kb/s and that is unacceptable. I did see an error message during install, something about requiring another option ( -E I think) unfortuantely I didn't think to get any screens of it till after the fact, but I was wondering if there is a way to get back to full speed?

Oh and I've been using wicd for a bit, it threw me for a loop when I had to switch wlan0 to ath0. Freaked right out till I figured that one out.

EDIT:
Thought maybe that becuase I didn't install the backports somebody mentioned that that might fix it, so after un-commenting those repositories I re-did the install. Here's the output. I've yet to restart my computer to see if that took care of it though.
```
astro@astro-desktop:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for astro: 
Ign http://archive.canonical.com natty InRelease                                    
Ign http://security.ubuntu.com natty-security InRelease                             
Ign http://extras.ubuntu.com natty InRelease                                        
Ign http://ppa.launchpad.net natty InRelease                                        
Ign http://ppa.launchpad.net natty InRelease                                        
Ign http://us.archive.ubuntu.com natty InRelease                                    
Ign http://us.archive.ubuntu.com natty-updates InRelease                            
Ign http://us.archive.ubuntu.com natty-backports InRelease                          
Hit http://archive.canonical.com natty Release.gpg                                  
Hit http://security.ubuntu.com natty-security Release.gpg                           
Get:1 http://extras.ubuntu.com natty Release.gpg [72 B]                             
Get:2 http://ppa.launchpad.net natty Release.gpg [316 B]                            
Hit http://us.archive.ubuntu.com natty Release.gpg                                  
Hit http://archive.canonical.com natty Release                                      
Hit http://security.ubuntu.com natty-security Release                               
Hit http://extras.ubuntu.com natty Release                                          
Hit http://ppa.launchpad.net natty Release.gpg                                      
Hit http://us.archive.ubuntu.com natty-updates Release.gpg                          
Hit http://archive.canonical.com natty/partner Sources                              
Get:3 http://ppa.launchpad.net natty Release [9,775 B]                              
Ign http://ppa.launchpad.net natty Release                                          
Get:4 http://us.archive.ubuntu.com natty-backports Release.gpg [198 B]              
Hit http://security.ubuntu.com natty-security/main Sources                          
Hit http://extras.ubuntu.com natty/main Sources                                     
Hit http://archive.canonical.com natty/partner i386 Packages                        
Ign http://archive.canonical.com natty/partner TranslationIndex                     
Hit http://ppa.launchpad.net natty Release                                          
Hit http://us.archive.ubuntu.com natty Release                                      
Hit http://security.ubuntu.com natty-security/restricted Sources                    
Hit http://security.ubuntu.com natty-security/universe Sources                      
Hit http://security.ubuntu.com natty-security/multiverse Sources                    
Hit http://security.ubuntu.com natty-security/main i386 Packages                    
Hit http://security.ubuntu.com natty-security/restricted i386 Packages              
Hit http://extras.ubuntu.com natty/main i386 Packages                               
Ign http://extras.ubuntu.com natty/main TranslationIndex                            
Ign http://ppa.launchpad.net natty/main Sources/DiffIndex                           
Ign http://ppa.launchpad.net natty/main i386 Packages/DiffIndex                     
Ign http://ppa.launchpad.net natty/main TranslationIndex                            
Hit http://us.archive.ubuntu.com natty-updates Release                               
Hit http://security.ubuntu.com natty-security/universe i386 Packages                 
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages               
Ign http://security.ubuntu.com natty-security/main TranslationIndex                 
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex           
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex           
Ign http://security.ubuntu.com natty-security/universe TranslationIndex             
Hit http://ppa.launchpad.net natty/main Sources                                     
Hit http://ppa.launchpad.net natty/main i386 Packages                               
Ign http://ppa.launchpad.net natty/main TranslationIndex                            
Hit http://ppa.launchpad.net natty/main Sources                                     
Get:5 http://us.archive.ubuntu.com natty-backports Release [23.3 kB]                
Hit http://ppa.launchpad.net natty/main i386 Packages                               
Hit http://us.archive.ubuntu.com natty/main Sources                                 
Hit http://us.archive.ubuntu.com natty/restricted Sources                           
Hit http://us.archive.ubuntu.com natty/universe Sources                             
Hit http://us.archive.ubuntu.com natty/multiverse Sources                           
Hit http://us.archive.ubuntu.com natty/main i386 Packages                           
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages                     
Hit http://us.archive.ubuntu.com natty/universe i386 Packages                       
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages                     
Ign http://us.archive.ubuntu.com natty/main TranslationIndex                        
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex                  
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex                  
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex                    
Hit http://us.archive.ubuntu.com natty-updates/main Sources                         
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources                   
Hit http://us.archive.ubuntu.com natty-updates/universe Sources                     
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources                   
Hit http://us.archive.ubuntu.com natty-updates/main i386 Packages                   
Hit http://us.archive.ubuntu.com natty-updates/restricted i386 Packages             
Hit http://us.archive.ubuntu.com natty-updates/universe i386 Packages               
Ign http://archive.canonical.com natty/partner Translation-en_US                    
Hit http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages             
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex                
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex          
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex          
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex            
Ign http://archive.canonical.com natty/partner Translation-en                       
Get:6 http://us.archive.ubuntu.com natty-backports/main Sources [1,651 B]           
Get:7 http://us.archive.ubuntu.com natty-backports/restricted Sources [14 B]        
Get:8 http://us.archive.ubuntu.com natty-backports/universe Sources [4,320 B]       
Ign http://security.ubuntu.com natty-security/main Translation-en_US                
Get:9 http://us.archive.ubuntu.com natty-backports/multiverse Sources [709 B]       
Get:10 http://us.archive.ubuntu.com natty-backports/main i386 Packages [2,150 B]    
Get:11 http://us.archive.ubuntu.com natty-backports/restricted i386 Packages [14 B] 
Get:12 http://us.archive.ubuntu.com natty-backports/universe i386 Packages [6,984 B]
Get:13 http://us.archive.ubuntu.com natty-backports/multiverse i386 Packages [702 B]
Ign http://us.archive.ubuntu.com natty-backports/main TranslationIndex              
Ign http://security.ubuntu.com natty-security/main Translation-en                   
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US          
Ign http://extras.ubuntu.com natty/main Translation-en_US                           
Ign http://ppa.launchpad.net natty/main Translation-en_US                           
Ign http://us.archive.ubuntu.com natty-backports/multiverse TranslationIndex        
Ign http://us.archive.ubuntu.com natty-backports/restricted TranslationIndex        
Ign http://us.archive.ubuntu.com natty-backports/universe TranslationIndex          
Ign http://security.ubuntu.com natty-security/multiverse Translation-en             
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US          
Ign http://security.ubuntu.com natty-security/restricted Translation-en             
Ign http://security.ubuntu.com natty-security/universe Translation-en_US            
Ign http://security.ubuntu.com natty-security/universe Translation-en               
Ign http://extras.ubuntu.com natty/main Translation-en                              
Ign http://ppa.launchpad.net natty/main Translation-en                              
Ign http://ppa.launchpad.net natty/main Translation-en_US                           
Ign http://ppa.launchpad.net natty/main Translation-en                              
Ign http://us.archive.ubuntu.com natty/main Translation-en_US                       
Ign http://us.archive.ubuntu.com natty/main Translation-en                          
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US                 
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en                    
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US                 
Ign http://us.archive.ubuntu.com natty/restricted Translation-en                    
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US                   
Ign http://us.archive.ubuntu.com natty/universe Translation-en                      
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US               
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en                  
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US         
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en            
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US         
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en            
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US           
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en              
Ign http://us.archive.ubuntu.com natty-backports/main Translation-en_US             
Ign http://us.archive.ubuntu.com natty-backports/main Translation-en                
Ign http://us.archive.ubuntu.com natty-backports/multiverse Translation-en_US       
Ign http://us.archive.ubuntu.com natty-backports/multiverse Translation-en          
Ign http://us.archive.ubuntu.com natty-backports/restricted Translation-en_US       
Ign http://us.archive.ubuntu.com natty-backports/restricted Translation-en          
Ign http://us.archive.ubuntu.com natty-backports/universe Translation-en_US         
Ign http://us.archive.ubuntu.com natty-backports/universe Translation-en            
Fetched 40.4 kB in 11s (3,420 B/s)                                                  
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8AA1FAA3F055C03
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ natty/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_binary-i386_Packages)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
astro@astro-desktop:~$ sudo apt-get install build-essential libssl-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
libssl-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev x11proto-kb-dev libxdmcp-dev xtrans-dev x11proto-core-dev
  libxt-dev x11proto-input-dev libpthread-stubs0-dev libxau-dev libpthread-stubs0
  libx11-dev libxcb1-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
astro@astro-desktop:~$ sudo apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.38-8-generic-pae is already the newest version.
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev x11proto-kb-dev libxdmcp-dev xtrans-dev x11proto-core-dev
  libxt-dev x11proto-input-dev libpthread-stubs0-dev libxau-dev libpthread-stubs0
  libx11-dev libxcb1-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
astro@astro-desktop:~$ sudo apt-get install subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
subversion is already the newest version.
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev x11proto-kb-dev libxdmcp-dev xtrans-dev x11proto-core-dev
  libxt-dev x11proto-input-dev libpthread-stubs0-dev libxau-dev libpthread-stubs0
  libx11-dev libxcb1-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
astro@astro-desktop:~$ sudo -i
root@astro-desktop:~# sudo svn checkout http://svn.madwifi-project.org/madwifi/trunk/ madwifi-ng

Fetching external item into 'madwifi-ng/tools/ath_info'
Checked out external at revision 4144.

Checked out revision 4144.
root@astro-desktop:~# cd madwifi-ng
root@astro-desktop:~/madwifi-ng# echo "" >> /etc/modprobe.d/blacklist
root@astro-desktop:~/madwifi-ng# echo "#Remove To Install MadWIFI Drivers" >> /etc/modprobe.d/blacklist
root@astro-desktop:~/madwifi-ng# echo "blacklist ath9k" >> /etc/modprobe.d/blacklist
root@astro-desktop:~/madwifi-ng# echo "blacklist ath5k" >> /etc/modprobe.d/blacklist
root@astro-desktop:~/madwifi-ng# make && make install
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.38-8-generic-pae/build SUBDIRS=/root/madwifi-ng modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic-pae'
  Building modules, stage 2.
  MODPOST 14 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic-pae'
make -C ./tools all || exit 1
make[1]: Entering directory `/root/madwifi-ng/tools'
for d in ath_info; do \
                make -C $d || exit 1; \
        done
make[2]: Entering directory `/root/madwifi-ng/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/root/madwifi-ng/tools/ath_info'
make[1]: Leaving directory `/root/madwifi-ng/tools'
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.38-8-generic-pae/build SUBDIRS=/root/madwifi-ng modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic-pae'
  Building modules, stage 2.
  MODPOST 14 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic-pae'
sh scripts/find-madwifi-modules.sh -r 2.6.38-8-generic-pae 
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
                make -C $i install || exit 1; \
        done
make[1]: Entering directory `/root/madwifi-ng/ath'
test -d //lib/modules/2.6.38-8-generic-pae/net || mkdir -p //lib/modules/2.6.38-8-generic-pae/net
install -m 0644 ath_pci.ko //lib/modules/2.6.38-8-generic-pae/net
make[1]: Leaving directory `/root/madwifi-ng/ath'
make[1]: Entering directory `/root/madwifi-ng/ath_hal'
test -d //lib/modules/2.6.38-8-generic-pae/net || mkdir -p //lib/modules/2.6.38-8-generic-pae/net
install -m 0644 ath_hal.ko //lib/modules/2.6.38-8-generic-pae/net
make[1]: Leaving directory `/root/madwifi-ng/ath_hal'
make[1]: Entering directory `/root/madwifi-ng/ath_rate'
for i in amrr/ onoe/ sample/ minstrel/; do \
                make -C $i install || exit 1; \
        done
make[2]: Entering directory `/root/madwifi-ng/ath_rate/amrr'
test -d //lib/modules/2.6.38-8-generic-pae/net || mkdir -p //lib/modules/2.6.38-8-generic-pae/net
install -m 0644 ath_rate_amrr.ko //lib/modules/2.6.38-8-generic-pae/net
make[2]: Leaving directory `/root/madwifi-ng/ath_rate/amrr'
make[2]: Entering directory `/root/madwifi-ng/ath_rate/onoe'
test -d //lib/modules/2.6.38-8-generic-pae/net || mkdir -p //lib/modules/2.6.38-8-generic-pae/net
install -m 0644 ath_rate_onoe.ko //lib/modules/2.6.38-8-generic-pae/net
make[2]: Leaving directory `/root/madwifi-ng/ath_rate/onoe'
make[2]: Entering directory `/root/madwifi-ng/ath_rate/sample'
test -d //lib/modules/2.6.38-8-generic-pae/net || mkdir -p //lib/modules/2.6.38-8-generic-pae/net
install -m 0644 ath_rate_sample.ko //lib/modules/2.6.38-8-generic-pae/net
make[2]: Leaving directory `/root/madwifi-ng/ath_rate/sample'
make[2]: Entering directory `/root/madwifi-ng/ath_rate/minstrel'
test -d //lib/modules/2.6.38-8-generic-pae/net || mkdir -p //lib/modules/2.6.38-8-generic-pae/net
install -m 0644 ath_rate_minstrel.ko //lib/modules/2.6.38-8-generic-pae/net
make[2]: Leaving directory `/root/madwifi-ng/ath_rate/minstrel'
make[1]: Leaving directory `/root/madwifi-ng/ath_rate'
make[1]: Entering directory `/root/madwifi-ng/net80211'
test -d //lib/modules/2.6.38-8-generic-pae/net || mkdir -p //lib/modules/2.6.38-8-generic-pae/net
for i in wlan.o wlan_wep.o wlan_tkip.o wlan_ccmp.o wlan_acl.o wlan_xauth.o wlan_scan_sta.o wlan_scan_ap.o; do \
                f=`basename $i .o`; \
                install -m 0644  $f.ko //lib/modules/2.6.38-8-generic-pae/net; \
        done
make[1]: Leaving directory `/root/madwifi-ng/net80211'
(export KMODPATH=/lib/modules/2.6.38-8-generic-pae/net; /sbin/depmod -ae 2.6.38-8-generic-pae)
WARNING: -e needs -E or -F
make -C ./tools all || exit 1
make[1]: Entering directory `/root/madwifi-ng/tools'
for d in ath_info; do \
                make -C $d || exit 1; \
        done
make[2]: Entering directory `/root/madwifi-ng/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/root/madwifi-ng/tools/ath_info'
make[1]: Leaving directory `/root/madwifi-ng/tools'
make -C ./tools install || exit 1
make[1]: Entering directory `/root/madwifi-ng/tools'
for d in ath_info; do \
                make -C $d || exit 1; \
        done
make[2]: Entering directory `/root/madwifi-ng/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/root/madwifi-ng/tools/ath_info'
install -d /usr/local/bin
for i in athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig wpakey; do \
                install $i /usr/local/bin/$i; \
                strip /usr/local/bin/$i; \
        done
install -d /usr/local/man/man8
install -m 0644 man/*.8 /usr/local/man/man8
install ../scripts/madwifi-unload /usr/local/bin/madwifi-unload
for d in ath_info; do \
                make -C $d install || exit 1; \
        done
make[2]: Entering directory `/root/madwifi-ng/tools/ath_info'
install -d /usr/local/bin
install -m 755 ath_info /usr/local/bin
install -d /usr/local/share/man/man8
install -m 644 ath_info.8 /usr/local/share/man/man8
make[2]: Leaving directory `/root/madwifi-ng/tools/ath_info'
make[1]: Leaving directory `/root/madwifi-ng/tools'
root@astro-desktop:~/madwifi-ng# echo ath_pci >> /etc/modules
root@astro-desktop:~/madwifi-ng# exit

```

---

### Post by Astroe on 2011-06-23
So that didn't work out for me at all. My Internet is still unbearably slow and I had to switch to *shudder* Windows for a while since I had work to do.

But I really really don't want to have to re-install Kubuntu again and re-do all the settings once more, so if anyone knows how to uninstall madwifi and re-install my old Atheros drivers a link would be appreciated. A google search proved fruitless but I'd really like to be able to come back to Linux without the two hour settings changes :(

---

### Post by Orlando84 on 2011-06-30
Hi all.
I've installed Ubuntu 10.10 netbook edition on Acer Aspire One a150. Folllowed the instructions to setup madwifi. But there is a problem: wicd says that there are no networks.
Ok, I'm giving you my settings and some system variables

lsmod
Module                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_realtek   217980  1 
snd_hda_intel          22107  4 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  3 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
wlan_scan_sta          12012  1 
snd_rawmidi            17783  1 snd_seq_midi
ath_rate_sample        11424  1 
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ath_pci               179564  0 
snd_timer              19067  2 snd_pcm,snd_seq
joydev                  8735  0 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  291004  4 
drm_kms_helper         30200  1 i915
snd                    49006  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wlan                  220280  4 wlan_scan_sta,ath_rate_sample,ath_pci
drm                   168054  5 i915,drm_kms_helper
soundcore                880  1 snd
ath_hal               396940  3 ath_rate_sample,ath_pci
i2c_algo_bit            5168  1 i915
uvcvideo               55847  0 
videodev               43098  1 uvcvideo
psmouse                59033  0 
video                  18712  1 i915
serio_raw               4022  0 
led_class               2633  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lp                      7342  0 
v4l1_compat            13359  2 uvcvideo,videodev
acerhdf                 6895  0 
output                  1883  1 video
parport                31492  3 parport_pc,ppdev,lp
intel_agp              26360  2 i915
agpgart                32011  2 drm,intel_agp
r8169                  36489  0 
mii                     4425  1 r8169

ifconfig
ath0      Link encap:Ethernet  HWaddr 00:22:69:0d:88:fa  
          inet6 addr: fe80::222:69ff:fe0d:88fa/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1e:68:ac:5f:72  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:feac:5f72/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21847 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12301 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32038578 (32.0 MB)  TX bytes:1021463 (1.0 MB)
          Interrupt:44 Base address:0x2000 

lo        Link encap:&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback)  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-22-69-0D-88-FA-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:409 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:0 (0.0 B)  TX bytes:25246 (25.2 KB)
          Interrupt:18 


iwlist ath0 scanning 
ath0      No scan results

sudo lshw -C Network
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:ac:5f:72
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.101 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:44 ioport:3000(size=256) memory:51010000-51010fff memory:51000000-5100ffff memory:51020000-5103ffff
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:22:69:0d:88:fa
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 multicast=yes wireless=IEEE 802.11g
       resources: irq:18 memory:55200000-5520ffff

Any suggestions would be very useful for my problem.

---

### Post by Orlando84 on 2011-06-30
> **Astroe said:**
> So that didn't work out for me at all. My Internet is still unbearably slow and I had to switch to *shudder* Windows for a while since I had work to do.

But I really really don't want to have to re-install Kubuntu again and re-do all the settings once more, so if anyone knows how to uninstall madwifi and re-install my old Atheros drivers a link would be appreciated. A google search proved fruitless but I'd really like to be able to come back to Linux without the two hour settings changes :(

Simply remove lines from /etc/modprobe.d/blacklist.conf where you added ath5k and ath9k
sudo nano /etc/modprobe.d/blacklist.conf - here is the command
Then add to this file "blacklist ath_pci". And remove this driver from /etc/modules. Restart, if works - tell me please.

---

### Post by Astroe on 2011-07-14
That didn't wok at all either. In fact following your instructions to the letter shut my internet down all together. Wicd couldn't detect any networks at all.

So I've re-installed Windows on the whole hard drive for the foreseeable future :(

---

### Post by Delinquentme on 2011-08-30
So I ran all this .. word-for-word

and it doesn't work ... so I was wondering if there is a quick removal for all of the above edits?

[http://blog.homelinux.org/?p=170](http://blog.homelinux.org/?p=170)
^^ this is my next options and it looks much simpler that the above.

---

