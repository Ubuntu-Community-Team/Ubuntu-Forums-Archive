---
title: "How to get &quot;sudo iwconfig eth1 power off&quot; to stick after plugging/unplugging power"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by DodgeV83 on 2010-10-15
After much research, I have found the solution to my intermittent wireless problem!  Whenever the laptop is plugged into power, wireless is perfect, when I'm on battery, wireless is horrible.

Here is the fix:

```
sudo iwconfig eth1 power off
``` 

Unfortunately, I have to type this in **everytime I unplug the laptop**.

While plugged in:

```
sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abgn  ESSID:"guest7255"  
          Mode:Managed  Channel:149  Access Point: 00:1A:1E:C0:CA:61   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          **Power Management:off**
          Link Quality=5/5  Signal level=-49 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Unplugging laptop:

```
sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abgn  ESSID:"guest7255"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1A:1E:C0:CA:61   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          **Power Managementmode:All packets received**
          Link Quality=5/5  Signal level=-49 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Running the sudo iwconfig eth1 power off:

```
sudo iwconfig eth1 power off
sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abgn  ESSID:"guest7255"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1A:1E:C0:CA:61   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          **Power Management:off**
          Link Quality=5/5  Signal level=-49 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Immediately plugging then unplugging again:

```
sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abgn  ESSID:"guest7255"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1A:1E:C0:CA:61   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          **Power Managementmode:All packets received**
          Link Quality=5/5  Signal level=-48 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


Here is what doesn't work:

[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9972607&postcount=6](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9972607&postcount=6)
[http://ubuntuforums.org/showpost.php?p=8538558&postcount=2](http://ubuntuforums.org/showpost.php?p=8538558&postcount=2)

I would prefer not to recompile my kernel.  Anyone have a solution to this?

---

### Post by DodgeV83 on 2010-10-16
Solution found :)

[URL="https://bbs.archlinux.org/viewtopic.php?pid=825440"]
Broadcom wireless very slow connection speed when on battery power[/URL]

First I had to install "laptop-mode-tools"

```
sudo apt-get install laptop-mode-tools
```

Then I had to edit the following file:

/etc/laptop-mode/conf.d/wireless-iwl-power.conf

```
sudo gedit /etc/laptop-mode/conf.d/wireless-iwl-power.conf
```

At the bottom of this file is:

```
# Levels passed to "/sys/class/net/*/device/power_level" for the iwlwifi
# wireless chipsets. The allowed values are:
# 0 = most power usage
# ...
# 5 = least power usage
IWL_AC_POWER=0
IWL_BATT_POWER=3
```

Change the "IWL_BATT_POWER=3" to "IWL_BATT_POWER=0".  Problem solved!

---

### Post by DodgeV83 on 2010-10-17
Update: Installing laptop-mode removed pm-utils, which is needed for suspend and hibernate!  I re-added pm-utils (and acpi-support which was also removed) and did the following...

[http://uselessuseofcat.com/?p=67](http://uselessuseofcat.com/?p=67)

Essentially, I created a blank file called "wireless" in /etc/pm/power.d

This made my sudo iwconfig eth1 power off stick :)

Update: I found that instead of adding a blank "wireless" file to /etc/pm/power.d, I added the "iwconfig eth1 power off" line to the file.  Now I no longer have to type it in after startup.

---

### Post by eombah on 2011-05-21
This problem still exists in natty, the command solves it.

Installing laptop-mode-tools on natty broke my usb mouse...

---

### Post by nilbus on 2012-04-22
I confirm that DodgeV83's second solution works. In summary:

```
echo iwconfig eth1 power off | sudo tee /etc/pm/power.d/wireless
```

And it works! No need to install laptop-mode-tools.

---

### Post by eombah on 2012-04-30
problem still exists in 12.04.
see bug at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/991232](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/991232)

workaround from that bug:
> 
Disable the power saving measures implemented by /usr/lib/pm-utils/power.d/wireless.
To disable them do:
sudo touch /etc/pm/power.d/wireless

You now should have an empty file named wireless without the executable bit set in /etc/pm/power.d.
Check with:
ls -lh /etc/pm/power.d/
You should see a file like this:
-rw-r--r-- 1 root root 0 2010-12-31 18:53 wireless


---

