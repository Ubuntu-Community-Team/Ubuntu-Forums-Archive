---
title: "RTL8191su Wireless USB not waking up from sleep"
date: 2012-09-02
forum: Networking &amp; Wireless
---

### Post by dulbirakan on 2012-09-02
Hi there,

I have a wireless usb dongle with realtek RTL8191SU chipset in it. The device is working fine other than the slight problem I am having.

When the computer goes to sleep the device does not resume working. I have to unplug and re-plug it to work.

I am assuming my problem is similar to the one in [this thread]("http://ubuntuforums.org/showthread.php?t=1984394&highlight=wireless+usb").

I ran lsusb the relevant section is below:

```
Bus 001 Device 006: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
```


I also ran dmesg to see what was going on

```

[  611.191241] PM: resume devices took 5.520 seconds
[  611.191283] PM: Finishing wakeup.
[  611.191284] Restarting tasks ... done.
[  612.961180] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  613.036894] r8169 0000:03:00.0: eth0: link down
[  613.037294] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  613.063079] r8712u: in r8711_wx_set_scan: bDriverStopped=1
[  613.160092] r8712u: in r8711_wx_set_scan: bDriverStopped=1
[  633.137163] r8712u: in r8711_wx_set_scan: bDriverStopped=1
[  639.436292] usb 1-1.6: USB disconnect, device number 5
[  644.492223] usb 1-1.6: new high-speed USB device number 6 using ehci_hcd
[  644.587530] r8712u: DriverVersion: v7_0.20100831
[  644.587552] r8712u: register rtl8712_netdev_ops to netdev_ops
[  644.587555] r8712u: USB_SPEED_HIGH with 4 endpoints
[  644.588087] r8712u: Boot from EFUSE: Autoload OK
[  645.199026] r8712u: CustomerID = 0x0000
[  645.199030] r8712u: MAC Address from efuse = 94:0c:6d:8f:f4:45
[  645.199033] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"

```

I think this means the driver is not restarted upon waking up. You can also see that once I plug it off and on again, it is reinitializing the device. 

What can be done to solve this?

Thanks in advance

---

### Post by dulbirakan on 2012-09-03
OK I found the solution.

I found the drivers name with lsmod which in my case was r8712u

sudo lsmod

```

v4l2_compat_ioctl32    17128  1 videodev
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
nvidia              12336440  58 
**r8712u                189603  0 **
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    19256  1 mxm_wmi
mei                    41616  0 

```


Then I added a file into /etc/rc/config.d/90_rtl

sudo nano /etc/pm/config.d/90_rtl

and wrote the following line into it

```
SUSPEND_MODULES="r8712u"
```

The wireless was able to resume after suspending the computer after this.

---

