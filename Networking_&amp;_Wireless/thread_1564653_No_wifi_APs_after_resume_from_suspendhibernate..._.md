---
title: "No wifi APs after resume from suspend/hibernate... sometimes"
date: 2010-08-30
forum: Networking &amp; Wireless
---

### Post by darthmowzy on 2010-08-30
After I resume from hibernate with my cpu frequency manually set to the highest settings (2ghz) the network manager shows not wifi APs.

"wlan0" shows under both ifconfig and iwconfig but "iwlist wlan0 scan" says no results. "sudo iwlist wlan0 scan" also says no results. Ive tried rmmod then modprobe with no luck. Rebooting is the only way I can get wifi working.

I can get wifi working again by:
     - rebooting
     - changing the cpu scaling to a lower setting then hibernate/resume
     - changing the cpu scaling to a lower setting then `sudo rmmod ath9k; sudo modprobe ath9k;`

Im using Ubuntu 10.04 with Atheros ar5008 (AR5BXB72) using ath9k drives

```
$ lspci |grep Atheros
0e:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)

``````
$ uname -r
2.6.32-24-generic
```

---

### Post by darthmowzy on 2010-09-01
I just encountered this problem again after resuming from hibernation.

Before:
```

$ iwconfig
wlan0     IEEE 802.11g  ESSID:"DS9"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:23:69:9A:32:34   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:68/100  Signal level:-52 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 ...
          Cell 14 ...

```After:
```
$ ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:1b:9e:92:7a:46  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:258520 errors:0 dropped:0 overruns:0 frame:0
          TX packets:188088 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:312495335 (312.4 MB)  TX bytes:21874600 (21.8 MB)
          Interrupt:18 Memory:f8200000-f8210000 

$ iwconfig
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


$ iwlist wlan0 scan
wlan0     No scan results

```

---

### Post by darthmowzy on 2010-09-02
I created a bug ticket: [https://bugs.launchpad.net/ubuntu/+bug/628310]("https://bugs.launchpad.net/ubuntu/+bug/628310")

This only occurs after suspending and resuming while the cpu frequency is manually set to the highest setting (2ghz).

Why would cpu throttling break my wifi?

---

### Post by darthmowzy on 2010-09-07
...Any ideas...?

---

### Post by darthmowzy on 2010-09-08
I tried Linux Mint, which is based on Ubuntu, to a separate partition with linux backports but the problem also exists on Linux Mint.

---

### Post by darthmowzy on 2010-09-08
This problem also exists in Fedora

---

### Post by darthmowzy on 2010-09-09
Did I post this in the wrong thread? This is "Networking & Wireless" right?

---

### Post by darthmowzy on 2010-09-13
One last desperate bump to try to get at least one response.

Is there a way to automatically run a command after resuming from suspend or hibernate?

---

### Post by darthmowzy on 2010-10-02
I created this script to automatically remove and reload ath9k when resuming under /usr/lib/pm-utils/sleep.d to work around this issue

```
#!/bin/sh

. "${PM_FUNCTIONS}"

module="ath9k"

fix_mouse()
{
    echo "\*\*\*\* FIXING THE MOUSE \*\*\*\*"
    /bin/chvt 1
    /bin/chvt 7
    #gtk-update-icon-cache /usr/share/icons/hicolor/
    echo "mouse should be fixed now"
}

fix_wifi()
{
    echo "\*\*\*\* FIXING THE WIFI \*\*\*\*"
    
    cur_freq=`sudo cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq`
    min_freq=`sudo cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_min_freq`
    echo "cpu speed is $cur_freq"
    echo "changing cpu speed to $min_freq"
    #cpufreq-selector -f $min_freq #TIME COMMAND TAKES A WHILE FOR SOME REASON
    cpufreq-set -f $min_freq #THIS COMMAND IS FASTER FOR SOME REASON
    echo "cpu speed set to $min_freq"
    
    echo "sleeping for 1 second"
    sleep 1
    echo "done sleeping"
    
    echo "removing module $module"
    rmmod $module
    echo "probing module $module"
    modprobe $module
    
    # echo "changing cpu speed back to $cur_freq"
    # cpufreq-selector -f $cur_freq
}

case "$1" in
    hibernate|suspend)
        echo "BLAH status: $1"
        ;;
    thaw|resume)
        echo "status: $1"
        fix_mouse
        
        #fix_wifi
        ;;
    *)  
        exit $NA
        ;;
esac
```Also, cpufreq-selector seems to have a bug which causes it to take 30 seconds to set the cpu speed. So I installed cpufreq-set which works instantly.

---

### Post by darthmowzy on 2010-10-02
This echo chamber is working great. Thanks for all the help everyone! :mad:

---

