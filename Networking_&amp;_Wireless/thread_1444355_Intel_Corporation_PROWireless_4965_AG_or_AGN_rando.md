---
title: "Intel Corporation PRO/Wireless 4965 AG or AGN randomly shuts off"
date: 2010-04-01
forum: Networking &amp; Wireless
---

### Post by jeremi.thebeau on 2010-04-01
I'm looking for help with some strange behavior that I have been
getting from my wireless adapter. This has been going on for quite
some time but only now am I able to see a pattern.

The behavior seems to be the following: Start up, connects to network
and work fine until I suspend my machine. On wake up, it works again
but after a seemingly random amount of time the connection is lost and
I can no longer find any networks.

Attached is dmesg output after startup and connecting to a wireless
network (dmesgAfterConecting.txt) and the same after the connection
has been lost (dmesgAfterConnectLost.txt). I get this error which seems important:

```
wlagn 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
```

Normal iwconfig outup while connected:

```
jeremi@linux64:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"NaosJena-SO53"
         Mode:Managed  Frequency:2.422 GHz  Access Point: 02:16:01:58:DF:43
         Bit Rate=54 Mb/s   Tx-Power=15 dBm
         Retry  long limit:7   RTS thr:off   Fragment thr:off
         Power Management:off
         Link Quality=60/70  Signal level=-50 dBm  Noise level=-93 dBm
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
         Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

and after it drops off:

```
jeremi@linux64:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"NaosJena-SO53"
         Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated
         Tx-Power=15 dBm
         Retry  long limit:7   RTS thr:off   Fragment thr:off
         Power Management:off
         Link Quality:0  Signal level:0  Noise level:0
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
         Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```


I've tried the following:

1. disabling hardware scan by creating */etc/modprobe.d/local* with the
following in it:

```
options iwlagn disable_hw_scan=1
```

2. running this:
```
sudo rmmod iwlagn && sudo modprobe iwlagn
```
after the connection drops. This usually results in the system no
longer recognizing that there is a wireless network adapter.

3. Toggling the wireless on/off switch.

None of these solutions have worked. Also of note is the random
behaviour of the wireless LED that is supposed to tell me if wireless is on or not. After wake up it is on or off, in either state wireless has been working or not.

I've also tried WICD 1.6.1 and Network Manager.

Environment:

I have an Asus F3Sv laptop with the following:

```
jeremi@linux64:~$ lspci | grep Network
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or
AGN [Kedron] Network Connection (rev 61)
```

and am running:
```
jeremi@linux64:~$ uname -a
Linux linux64 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC
2010 x86_64 GNU/Linux
```

with Ubuntu Karmic 64 bit.

As a temporary solution, does anyone know if it posible to "reboot"
just the wireless adapter. I though if this was possible it could be a
stopgap measure since it works well after a fresh start up.

Also if this is not the right place to post this, please let me know
and suggest where else to post it.

Thanks

Jeremi

---

### Post by chili555 on 2010-04-01
> As a temporary solution, does anyone know if it posible to "reboot"
just the wireless adapter. I though if this was possible it could be a
stopgap measure since it works well after a fresh start up.You might try:```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn fw_restart4965=1
sudo ifconfig wlan0 up
```I also have doubts about this:> /etc/modprobe.d/local I suggest:```
sudo mv /etc/modprobe.d/local  /etc/modprobe.d/iwlagn.conf
```Let us know if you have any improvement. If your connection stays stable after those commands, we will tweak two files.

---

