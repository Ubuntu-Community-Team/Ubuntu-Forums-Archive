---
title: "System hang when using Intel Pro/Wireless 2915ABG on Ubuntu 10.10"
date: 2010-12-16
forum: Networking &amp; Wireless
---

### Post by m31ark on 2010-12-16
Greetings!

My system hangs within a few minutes after I turn on the Intel Pro/Wireless 2915ABG interface built into my motherboard or if I boot with the interface turned on.  I have been having this problem for a couple of years and tried to fix it myself from time to time.  (I think that I even asked for help in the Forum once.)  The wireless interface used to work fine with Ubuntu and I kept hoping that the problem would "magically" disappear with each upgrade.  I also read about the recent problems with ndiswrapper and similar interfaces.  But this doesn't seem to be my problem.

The entries in /var/log/messages just prior to the last hang were

Dec 15 09:09:47 periwinkle rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="824" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Dec 15 09:09:47 periwinkle rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="824" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Dec 15 09:20:18 periwinkle kernel: [ 1841.024720] ptrace of non-child pid 3757 was attempted by: gdb (pid 3764)
Dec 15 09:21:04 periwinkle kernel: [ 1887.346796] ptrace of non-child pid 3787 was attempted by: gdb (pid 3794)

I don't know what process gdb was trying to trace.  Since I was testing the system, I was only running Firefox, which has always triggered the problem.

The output from "dmesg | grep -e ndis -e ipw" was

[   19.121563] libipw: 802.11 data/management/control stack, git-1.1.13
[   19.121566] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   19.161180] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   19.161182] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   19.171428] ipw2200 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   19.185277] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[   19.552671] ipw2200: Radio Frequency Kill Switch is On:
[   19.554255] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
[   24.300029] ipw2200: Failed to send POWER_MODE: Command timed out.
[   28.590022] ipw2200: Failed to send POWER_MODE: Command timed out.

In previous version of Ubuntu, the messages just before the hang used to complain about the firmware in the interface being buggy.

I intended to send the output from iwconfig and "sudo iwlist eth1 scan" as well.  But I can't turn on the interface without hanging the system and thereby destroying this post.

I just upgraded from the 64-bit version of Ubuntu 10.4 to 10.10 over the network using the Update Manager.  But when I chose the "About Ubuntu" option from the System menu, I was surprised to see it say that I am running Natty Narwhal 11.4.  My system is a Linux Certified LC2464T ([http://www.linuxcertified.com/linux-laptop-lc2464t.html](http://www.linuxcertified.com/linux-laptop-lc2464t.html)).

Any help would be very greatly appreciated!

Mark

---

### Post by chili555 on 2010-12-16
> [ 19.552671] ipw2200: Radio Frequency Kill Switch is On:What do you make of this? Do you turn the switch on after you boot? Is the behavior the same if you boot with the hardware switch already on?> But when I chose the "About Ubuntu" option from the System menu, I was surprised to see it say that I am running Natty Narwhal 11.4.I am surprised to see it on my own system as well, I did a fresh install from the live CD. Therefor, I think it's wrong and may safely be ignored.> I don't know what process gdb was trying to trace.It's hard to determine after the system has locked and hard-booted. The previous message:> rsyslogd was HUPed, type 'lightweight'.Simply means the syslog filled up; it was stopped and another fresh copy was started. If you are looking at an on-going problem, it suggests you also look in /var/log/syslog.1.

What does this tell us?```
rfkill list all
```

---

### Post by m31ark on 2010-12-16
Thanks for responding.  The behavior is the same whether I turn the kill switch on after booting or before.

Thanks for setting me straight on the log switching.

Here's the info you requested.  The first output was obtained with the switch off, the second with the switch on.

mark@periwinkle:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
mark@periwinkle:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

I'm also currently using a wired connection.  So I'm not expecting to get a hang since the traffic should all be flowing through the wire.  (Actually, I noticed that my routing is now screwed up and isn't working properly.  So I had to turn the wireless interface off.)

Here's a little more info

mark@periwinkle:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"moops2"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:3F:7E:BD:A1   
          Bit Rate:48 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=67/100  Signal level=-60 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:6

mark@periwinkle:~$ sudo iwlist eth1 scan
[sudo] password for mark: 
eth1      Scan completed :
          Cell 01 - Address: 00:18:3F:7E:BD:A1
                    ESSID:"moops2"mark@periwinkle:~$ sudo iwlist eth1 scan
[sudo] password for mark: 
eth1      Scan completed :
          Cell 01 - Address: 00:18:3F:7E:BD:A1
                    ESSID:"moops2"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=64/100  Signal level=-62 dBm  
                    Extra: Last beacon: 0ms ago
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=64/100  Signal level=-62 dBm  
                    Extra: Last beacon: 0ms ago

Hope this helps!  Thanks again!

Mark

---

### Post by chili555 on 2010-12-16
> I'm also currently using a wired connection. So I'm not expecting to get a hang since the traffic should all be flowing through the wire.Why are you doing this? Network Manager is designed to disallow this: [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has been managed for themNow, if you want a wireless connection to the WAN and wired to the LAN, that can be done, but NM will not be your friend.

Is the wireless and NM and therefor the computer stable with the wire disconnected?

---

### Post by m31ark on 2010-12-16
I just turned on the wireless interface momentarily to gather information.  I never otherwise operate both simultaneously.  (I may be somewhat ignorant.  But I'm not that ignorant.)  And the answer is "No, the computer is not stable with only the wireless running"  It has only been stable with the wired connection, which is how I've had to exclusively run it for the past couple years.

Mark

---

### Post by chili555 on 2010-12-16
No offense intended; I have seen this issue many times and I never know until I ask. I wonder what the syslog has to say about the firmware. Please post:```
sudo cat /var/log/syslog | grep -e ipw -e firm
```If there is scant data here, also look at syslog.1.

I have a Thinkpad with the same wireless card, so I can compare if a fixable error doesn't jump out at us.

---

### Post by chili555 on 2010-12-16
No offense intended; I have seen this issue many times and I never know until I ask. I wonder what the syslog has to say about the firmware. Please post:```
sudo cat /var/log/syslog | grep -e ipw -e firm
```If there is scant data here, also look at syslog.1.

I have a Thinkpad with the same wireless card, so I can compare if a fixable error doesn't jump out at us.

---

### Post by m31ark on 2010-12-16
The last hang was yesterday morning (Dec 15th) around 9 a.m.  So I had to go back to syslog.2.  There was also another hang on the evening of the 14th.  Here's the output of "sudo gunzip -c /var/log/syslog.2.gz | grep -e ipw -e firm"

Dec 14 15:01:25 periwinkle kernel: [18387.760029] ipw2200: Failed to send POWER_MODE: Command timed out.
Dec 14 16:17:27 periwinkle kernel: [   24.451497] libipw: 802.11 data/management/control stack, git-1.1.13
Dec 14 16:17:27 periwinkle kernel: [   24.451501] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Dec 14 16:17:27 periwinkle kernel: [   25.003085] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Dec 14 16:17:27 periwinkle kernel: [   25.003090] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 14 16:17:27 periwinkle kernel: [   25.003292] ipw2200 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 14 16:17:27 periwinkle kernel: [   25.003350] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
Dec 14 16:17:27 periwinkle kernel: [   26.557476] ipw2200: Radio Frequency Kill Switch is On:
Dec 14 16:17:27 periwinkle kernel: [   26.558680] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
Dec 14 16:17:39 periwinkle NetworkManager[1366]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 14 16:17:41 periwinkle NetworkManager[1366]: <info> (eth1): new 802.11 WiFi device (driver: 'ipw2200' ifindex: 3)
Dec 14 16:17:47 periwinkle kernel: [   52.670027] ipw2200: Failed to send POWER_MODE: Command timed out.
Dec 14 16:17:55 periwinkle kernel: [   61.010027] ipw2200: Failed to send POWER_MODE: Command timed out.
Dec 14 16:49:54 periwinkle kernel: [   15.683064] libipw: 802.11 data/management/control stack, git-1.1.13
Dec 14 16:49:54 periwinkle kernel: [   15.683068] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Dec 14 16:49:55 periwinkle kernel: [   16.470672] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Dec 14 16:49:55 periwinkle kernel: [   16.470676] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 14 16:49:55 periwinkle kernel: [   16.470847] ipw2200 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 14 16:49:55 periwinkle kernel: [   16.470902] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
Dec 14 16:49:56 periwinkle kernel: [   17.883596] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
Dec 14 16:50:08 periwinkle NetworkManager[1052]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 14 16:50:11 periwinkle NetworkManager[1052]: <info> (eth1): new 802.11 WiFi device (driver: 'ipw2200' ifindex: 3)
Dec 14 16:53:22 periwinkle kernel: [   20.474999] libipw: 802.11 data/management/control stack, git-1.1.13
Dec 14 16:53:22 periwinkle kernel: [   20.475003] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Dec 14 16:53:22 periwinkle kernel: [   20.517840] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Dec 14 16:53:22 periwinkle kernel: [   20.517843] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 14 16:53:22 periwinkle kernel: [   20.540190] ipw2200 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 14 16:53:22 periwinkle kernel: [   20.552037] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
Dec 14 16:53:22 periwinkle kernel: [   20.989569] ipw2200: Radio Frequency Kill Switch is On:
Dec 14 16:53:23 periwinkle kernel: [   21.141326] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
Dec 14 16:53:23 periwinkle NetworkManager[864]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 14 16:53:23 periwinkle NetworkManager[864]: <info> (eth1): new 802.11 WiFi device (driver: 'ipw2200' ifindex: 3)
Dec 14 16:53:26 periwinkle kernel: [   24.180017] ipw2200: Failed to send POWER_MODE: Command timed out.
Dec 14 16:53:30 periwinkle kernel: [   28.430025] ipw2200: Failed to send POWER_MODE: Command timed out.
Dec 14 18:47:32 periwinkle kernel: [   19.467685] libipw: 802.11 data/management/control stack, git-1.1.13
Dec 14 18:47:32 periwinkle kernel: [   19.467689] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Dec 14 18:47:32 periwinkle kernel: [   19.522636] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Dec 14 18:47:32 periwinkle kernel: [   19.522640] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 14 18:47:32 periwinkle kernel: [   19.532566] ipw2200 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 14 18:47:32 periwinkle kernel: [   19.544550] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
Dec 14 18:47:32 periwinkle kernel: [   19.944523] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
Dec 14 18:47:32 periwinkle NetworkManager[1110]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 14 18:47:32 periwinkle NetworkManager[1110]: <info> (eth1): new 802.11 WiFi device (driver: 'ipw2200' ifindex: 3)
Dec 15 08:49:56 periwinkle kernel: [   19.174581] libipw: 802.11 data/management/control stack, git-1.1.13
Dec 15 08:49:56 periwinkle kernel: [   19.174585] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Dec 15 08:49:56 periwinkle kernel: [   19.251666] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Dec 15 08:49:56 periwinkle kernel: [   19.251668] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 15 08:49:56 periwinkle kernel: [   19.261883] ipw2200 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 15 08:49:56 periwinkle kernel: [   19.275808] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
Dec 15 08:49:56 periwinkle kernel: [   19.641904] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
Dec 15 08:49:56 periwinkle NetworkManager[846]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 15 08:49:56 periwinkle NetworkManager[846]: <info> (eth1): new 802.11 WiFi device (driver: 'ipw2200' ifindex: 3)

and here's the output of "sudo cat /var/log/syslog.1 | grep -e ipw -e firm"

Dec 15 20:43:55 periwinkle kernel: [   23.464378] libipw: 802.11 data/management/control stack, git-1.1.13
Dec 15 20:43:55 periwinkle kernel: [   23.464383] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Dec 15 20:43:55 periwinkle kernel: [   23.489778] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Dec 15 20:43:55 periwinkle kernel: [   23.489780] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 15 20:43:55 periwinkle kernel: [   23.511430] ipw2200 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 15 20:43:55 periwinkle kernel: [   23.520243] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
Dec 15 20:43:55 periwinkle kernel: [   23.943639] ipw2200: Radio Frequency Kill Switch is On:
Dec 15 20:43:55 periwinkle kernel: [   24.008706] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
Dec 15 20:43:56 periwinkle NetworkManager[866]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 15 20:43:56 periwinkle NetworkManager[866]: <info> (eth1): new 802.11 WiFi device (driver: 'ipw2200' ifindex: 3)
Dec 15 20:44:01 periwinkle kernel: [   29.990035] ipw2200: Failed to send POWER_MODE: Command timed out.
Dec 15 20:44:09 periwinkle kernel: [   34.220027] ipw2200: Failed to send POWER_MODE: Command timed out.
Dec 15 21:34:39 periwinkle kernel: [   22.410576] libipw: 802.11 data/management/control stack, git-1.1.13
Dec 15 21:34:39 periwinkle kernel: [   22.410581] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Dec 15 21:34:39 periwinkle kernel: [   22.416895] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Dec 15 21:34:39 periwinkle kernel: [   22.416899] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 15 21:34:39 periwinkle kernel: [   22.442331] ipw2200 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 15 21:34:39 periwinkle kernel: [   22.454327] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
Dec 15 21:34:39 periwinkle kernel: [   22.864070] ipw2200: Radio Frequency Kill Switch is On:
Dec 15 21:34:39 periwinkle kernel: [   22.931771] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
Dec 15 21:34:39 periwinkle NetworkManager[843]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 15 21:34:40 periwinkle NetworkManager[843]: <info> (eth1): new 802.11 WiFi device (driver: 'ipw2200' ifindex: 3)
Dec 15 21:34:43 periwinkle kernel: [   27.070021] ipw2200: Failed to send POWER_MODE: Command timed out.
Dec 15 21:34:51 periwinkle kernel: [   31.190022] ipw2200: Failed to send POWER_MODE: Command timed out.
Dec 16 10:09:48 periwinkle NetworkManager[874]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 16 10:09:48 periwinkle kernel: [   19.121563] libipw: 802.11 data/management/control stack, git-1.1.13
Dec 16 10:09:48 periwinkle kernel: [   19.121566] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Dec 16 10:09:48 periwinkle kernel: [   19.161180] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Dec 16 10:09:48 periwinkle kernel: [   19.161182] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 16 10:09:48 periwinkle kernel: [   19.171428] ipw2200 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 16 10:09:48 periwinkle kernel: [   19.185277] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
Dec 16 10:09:48 periwinkle kernel: [   19.552671] ipw2200: Radio Frequency Kill Switch is On:
Dec 16 10:09:48 periwinkle kernel: [   19.554255] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
Dec 16 10:09:49 periwinkle NetworkManager[874]: <info> (eth1): new 802.11 WiFi device (driver: 'ipw2200' ifindex: 3)
Dec 16 10:09:53 periwinkle kernel: [   24.300029] ipw2200: Failed to send POWER_MODE: Command timed out.
Dec 16 10:09:57 periwinkle kernel: [   28.590022] ipw2200: Failed to send POWER_MODE: Command timed out.

Anything look odd?

I very much appreciate your help.

Mark

---

### Post by chili555 on 2010-12-16
> Anything look odd?Not a thing, unfortunately. I just got back to my IPW2915 equipped laptop and the logs look exactly the same, aside from these parts:> Dec 16 10:09:48 periwinkle kernel: [ 19.552671] ipw2200: Radio Frequency Kill Switch is On:
Dec 16 10:09:53 periwinkle kernel: [ 24.300029] ipw2200: Failed to send POWER_MODE: Command timed out.
Dec 16 10:09:57 periwinkle kernel: [ 28.590022] ipw2200: Failed to send POWER_MODE: Command timed out.If the switch is off, I assume it's normal. I think we have to look elsewhere, other than the driver, for the hang problem. It may be Network Manager, Firefox, flash or wpa_supplicant. I am not too sure how to proceed aside from grepping syslog. Perhaps:```
sudo cat /var/log/syslog | grep -i Network
```Substitute wpa, flash and Firefox. I suggest you look at the log after you crash it and reboot.

---

### Post by m31ark on 2010-12-17
Hi Again.

The system hung sometime around Dec 16 21:23:54 and I brought it up again sometime around Dec 16 21:27:57.  This is the discontinuity in /var/log/syslog.  According to both /var/log/syslog and /var/log/messages, flash does seem to be segfaulting occasionally.  But the times aren't anywhere near the times of the hangs.  My first impulse eons ago was that flash was probably the culprit.  But it doesn't seem to be true.  Also, there was no mention of Firefox in either /var/log/messages or /var/log/syslog.

Here is the relevant output from "cat /var/log/messages | grep -i network"

Dec 16 21:12:33 periwinkle kernel: [   19.268420] type=1400 audit(1292562752.114:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=642 comm="apparmor_parser"
Dec 16 21:12:33 periwinkle kernel: [   19.357787] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Dec 16 21:12:33 periwinkle kernel: [   19.371428] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
Dec 16 21:12:33 periwinkle kernel: [   20.095988] type=1400 audit(1292562752.944:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=851 comm="apparmor_parser"

and here is the relevant output from "cat /var/log/syslog | grep -i network"

Dec 16 21:17:02 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  completed -> disconnected
Dec 16 21:17:02 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Dec 16 21:17:03 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  scanning -> associating
Dec 16 21:17:03 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  associating -> associated
Dec 16 21:17:03 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  associated -> completed
Dec 16 21:17:03 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  completed -> disconnected
Dec 16 21:17:04 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Dec 16 21:17:05 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  scanning -> associating
Dec 16 21:17:07 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  associating -> associated
Dec 16 21:17:07 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  associated -> completed
Dec 16 21:17:11 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  completed -> disconnected
Dec 16 21:17:11 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Dec 16 21:17:12 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  scanning -> associating
Dec 16 21:17:12 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  associating -> associated
Dec 16 21:17:12 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  associated -> completed
Dec 16 21:17:12 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  completed -> disconnected
Dec 16 21:17:12 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Dec 16 21:17:13 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  scanning -> associating
Dec 16 21:17:15 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  associating -> associated
Dec 16 21:17:15 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  associated -> completed
Dec 16 21:20:59 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  completed -> disconnected
Dec 16 21:21:00 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Dec 16 21:21:00 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  scanning -> associating
Dec 16 21:21:01 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  associating -> associated
Dec 16 21:21:01 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  associated -> completed

There may be a funky cycle here.

Similarly, here is the output from "cat /var/log/syslog | grep -i wpa"

Dec 16 21:13:00 periwinkle wpa_supplicant[1192]: Associated with 00:18:3f:7e:bd:a1
Dec 16 21:13:00 periwinkle wpa_supplicant[1192]: CTRL-EVENT-CONNECTED - Connection to 00:18:3f:7e:bd:a1 completed (auth) [id=0 id_str=]
Dec 16 21:17:02 periwinkle wpa_supplicant[1192]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Dec 16 21:17:03 periwinkle wpa_supplicant[1192]: Trying to associate with 00:18:3f:7e:bd:a1 (SSID='moops2' freq=2437 MHz)
Dec 16 21:17:03 periwinkle wpa_supplicant[1192]: Associated with 00:18:3f:7e:bd:a1
Dec 16 21:17:03 periwinkle wpa_supplicant[1192]: CTRL-EVENT-CONNECTED - Connection to 00:18:3f:7e:bd:a1 completed (reauth) [id=0 id_str=]
Dec 16 21:17:03 periwinkle wpa_supplicant[1192]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Dec 16 21:17:05 periwinkle wpa_supplicant[1192]: Trying to associate with 00:18:3f:7e:bd:a1 (SSID='moops2' freq=2437 MHz)
Dec 16 21:17:07 periwinkle wpa_supplicant[1192]: Associated with 00:18:3f:7e:bd:a1
Dec 16 21:17:07 periwinkle wpa_supplicant[1192]: CTRL-EVENT-CONNECTED - Connection to 00:18:3f:7e:bd:a1 completed (reauth) [id=0 id_str=]
Dec 16 21:17:11 periwinkle wpa_supplicant[1192]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Dec 16 21:17:12 periwinkle wpa_supplicant[1192]: Trying to associate with 00:18:3f:7e:bd:a1 (SSID='moops2' freq=2437 MHz)
Dec 16 21:17:12 periwinkle wpa_supplicant[1192]: Associated with 00:18:3f:7e:bd:a1
Dec 16 21:17:12 periwinkle wpa_supplicant[1192]: CTRL-EVENT-CONNECTED - Connection to 00:18:3f:7e:bd:a1 completed (reauth) [id=0 id_str=]
Dec 16 21:17:12 periwinkle wpa_supplicant[1192]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Dec 16 21:17:13 periwinkle wpa_supplicant[1192]: Trying to associate with 00:18:3f:7e:bd:a1 (SSID='moops2' freq=2437 MHz)
Dec 16 21:17:15 periwinkle wpa_supplicant[1192]: Associated with 00:18:3f:7e:bd:a1
Dec 16 21:17:15 periwinkle wpa_supplicant[1192]: CTRL-EVENT-CONNECTED - Connection to 00:18:3f:7e:bd:a1 completed (reauth) [id=0 id_str=]
Dec 16 21:20:59 periwinkle wpa_supplicant[1192]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Dec 16 21:21:00 periwinkle wpa_supplicant[1192]: Trying to associate with 00:18:3f:7e:bd:a1 (SSID='moops2' freq=2437 MHz)
Dec 16 21:21:01 periwinkle wpa_supplicant[1192]: Associated with 00:18:3f:7e:bd:a1
Dec 16 21:21:01 periwinkle wpa_supplicant[1192]: CTRL-EVENT-CONNECTED - Connection to 00:18:3f:7e:bd:a1 completed (reauth) [id=0 id_str=]

It looks to me like there is some strange cycling between connecting and disconnecting.  Could my router be part of the problem?

The corresponding section of /var/log/syslog, without grepping away portions, is

Dec 16 21:17:02 periwinkle wpa_supplicant[1192]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Dec 16 21:17:02 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  completed -> disconnected
Dec 16 21:17:02 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Dec 16 21:17:03 periwinkle wpa_supplicant[1192]: Trying to associate with 00:18:3f:7e:bd:a1 (SSID='moops2' freq=2437 MHz)
Dec 16 21:17:03 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  scanning -> associating
Dec 16 21:17:03 periwinkle wpa_supplicant[1192]: Associated with 00:18:3f:7e:bd:a1
Dec 16 21:17:03 periwinkle wpa_supplicant[1192]: CTRL-EVENT-CONNECTED - Connection to 00:18:3f:7e:bd:a1 completed (reauth) [id=0 id_str=]
Dec 16 21:17:03 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  associating -> associated
Dec 16 21:17:03 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  associated -> completed
Dec 16 21:17:03 periwinkle wpa_supplicant[1192]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Dec 16 21:17:03 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  completed -> disconnected
Dec 16 21:17:04 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Dec 16 21:17:05 periwinkle wpa_supplicant[1192]: Trying to associate with 00:18:3f:7e:bd:a1 (SSID='moops2' freq=2437 MHz)
Dec 16 21:17:05 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  scanning -> associating
Dec 16 21:17:07 periwinkle wpa_supplicant[1192]: Associated with 00:18:3f:7e:bd:a1
Dec 16 21:17:07 periwinkle wpa_supplicant[1192]: CTRL-EVENT-CONNECTED - Connection to 00:18:3f:7e:bd:a1 completed (reauth) [id=0 id_str=]
Dec 16 21:17:07 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  associating -> associated
Dec 16 21:17:07 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  associated -> completed
Dec 16 21:17:11 periwinkle wpa_supplicant[1192]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Dec 16 21:17:11 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  completed -> disconnected
Dec 16 21:17:11 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Dec 16 21:17:12 periwinkle wpa_supplicant[1192]: Trying to associate with 00:18:3f:7e:bd:a1 (SSID='moops2' freq=2437 MHz)
Dec 16 21:17:12 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  scanning -> associating
Dec 16 21:17:12 periwinkle wpa_supplicant[1192]: Associated with 00:18:3f:7e:bd:a1
Dec 16 21:17:12 periwinkle wpa_supplicant[1192]: CTRL-EVENT-CONNECTED - Connection to 00:18:3f:7e:bd:a1 completed (reauth) [id=0 id_str=]
Dec 16 21:17:12 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  associating -> associated
Dec 16 21:17:12 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  associated -> completed
Dec 16 21:17:12 periwinkle wpa_supplicant[1192]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Dec 16 21:17:12 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  completed -> disconnected
Dec 16 21:17:12 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Dec 16 21:17:13 periwinkle wpa_supplicant[1192]: Trying to associate with 00:18:3f:7e:bd:a1 (SSID='moops2' freq=2437 MHz)
Dec 16 21:17:13 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  scanning -> associating
Dec 16 21:17:15 periwinkle wpa_supplicant[1192]: Associated with 00:18:3f:7e:bd:a1
Dec 16 21:17:15 periwinkle wpa_supplicant[1192]: CTRL-EVENT-CONNECTED - Connection to 00:18:3f:7e:bd:a1 completed (reauth) [id=0 id_str=]
Dec 16 21:17:15 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  associating -> associated
Dec 16 21:17:15 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  associated -> completed
Dec 16 21:18:08 periwinkle dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Dec 16 21:18:11 periwinkle dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Dec 16 21:18:14 periwinkle dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Dec 16 21:18:21 periwinkle dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Dec 16 21:18:36 periwinkle dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Dec 16 21:18:43 periwinkle dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Dec 16 21:18:53 periwinkle dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Dec 16 21:19:09 periwinkle dhclient: No DHCPOFFERS received.
Dec 16 21:19:09 periwinkle dhclient: No working leases in persistent database - sleeping.
Dec 16 21:20:59 periwinkle wpa_supplicant[1192]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Dec 16 21:20:59 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  completed -> disconnected
Dec 16 21:21:00 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Dec 16 21:21:00 periwinkle wpa_supplicant[1192]: Trying to associate with 00:18:3f:7e:bd:a1 (SSID='moops2' freq=2437 MHz)
Dec 16 21:21:00 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  scanning -> associating
Dec 16 21:21:01 periwinkle wpa_supplicant[1192]: Associated with 00:18:3f:7e:bd:a1
Dec 16 21:21:01 periwinkle wpa_supplicant[1192]: CTRL-EVENT-CONNECTED - Connection to 00:18:3f:7e:bd:a1 completed (reauth) [id=0 id_str=]
Dec 16 21:21:01 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  associating -> associated
Dec 16 21:21:01 periwinkle NetworkManager[832]: <info> (eth1): supplicant connection state:  associated -> completed
Dec 16 21:22:53 periwinkle dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Dec 16 21:22:56 periwinkle dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Dec 16 21:23:00 periwinkle dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Dec 16 21:23:06 periwinkle dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Dec 16 21:23:18 periwinkle dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Dec 16 21:23:18 periwinkle acpid: client 1150[0:0] has disconnected
Dec 16 21:23:18 periwinkle acpid: client connected from 1150[0:0]
Dec 16 21:23:18 periwinkle acpid: 1 client rule loaded
Dec 16 21:23:25 periwinkle dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Dec 16 21:23:42 periwinkle dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Dec 16 21:23:54 periwinkle dhclient: No DHCPOFFERS received.
Dec 16 21:23:54 periwinkle dhclient: No working leases in persistent database - sleeping.

There's certainly some unwanted cycling in the wireless connection here, though I don't understand why it would hang the system.

What do you think?

Mark

---

### Post by chili555 on 2010-12-17
I don't see anything here that screams FIXME. I certainly see where the wireless connects, drops, connects, etc., but that shouldn't cause a lockup. That could be caused by RFI on the channel you have the router set to due to dimmers, cordless phones, microwaves, etc., or by an excessive distance from the router. In any event, it's not likely, as far as I have seen, to cause a lockup.

What does this tell us?```
sudo cat /var/log/syslog | grep -i error
```We might also try:```
sudo rmmod -f ipw2200
sudo modprobe ipw2200 hwcrypto=1
```Is there any improvement? If so, we can write one file to make it permanent.

---

### Post by m31ark on 2010-12-17
Okay here are all of the errors in the current syslog, which includes the time that I last crashed the machine.

mark@periwinkle:~$ cat /var/log/syslog | grep -i error
Dec 16 11:58:37 periwinkle kernel: [ 6548.469563] npviewer.bin[1996]: segfault at f596e04c ip 00000000f61b9ee7 sp 00000000ffba6410 error 4 in libflashplayer.so[f5e1a000+b2e000]
Dec 16 13:07:23 periwinkle kernel: [   18.973655] amd64_edac: probe of 0000:00:18.2 failed with error -22
Dec 16 13:07:23 periwinkle NetworkManager[873]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Dec 16 13:41:36 periwinkle NetworkManager[873]: <error> [1292535696.667891] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Dec 16 13:41:36 periwinkle NetworkManager[873]: <error> [1292535696.764829] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Dec 16 14:29:13 periwinkle kernel: [   19.345711] amd64_edac: probe of 0000:00:18.2 failed with error -22
Dec 16 14:29:13 periwinkle NetworkManager[857]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Dec 16 14:29:27 periwinkle NetworkManager[857]: <error> [1292538567.211650] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Dec 16 14:29:27 periwinkle NetworkManager[857]: <error> [1292538567.279832] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Dec 16 21:12:33 periwinkle kernel: [   19.224732] amd64_edac: probe of 0000:00:18.2 failed with error -22
Dec 16 21:12:34 periwinkle NetworkManager[832]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Dec 16 21:12:51 periwinkle NetworkManager[832]: <error> [1292562771.162121] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Dec 16 21:12:51 periwinkle NetworkManager[832]: <error> [1292562771.227033] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Dec 16 21:27:57 periwinkle kernel: [   21.855238] amd64_edac: probe of 0000:00:18.2 failed with error -22
Dec 16 21:27:57 periwinkle NetworkManager[854]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Dec 16 21:29:58 periwinkle NetworkManager[854]: <error> [1292563798.4305] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Dec 16 21:29:58 periwinkle NetworkManager[854]: <error> [1292563798.80103] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Dec 17 19:18:35 periwinkle kernel: [   19.309544] amd64_edac: probe of 0000:00:18.2 failed with error -22
Dec 17 19:18:35 periwinkle NetworkManager[903]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Dec 17 19:19:52 periwinkle NetworkManager[903]: <error> [1292642392.79785] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Dec 17 19:19:52 periwinkle NetworkManager[903]: <error> [1292642392.176891] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name

I don't see anything close enough to the time of the crash (around 21:23:54) to be the culprit.  Anything strike you as suspicious?

I'll try your other suggestion too.  But I'll have to make a second post with the results since I booted with the wired connection this time.

Mark

---

### Post by chili555 on 2010-12-18
There are some pretty ugly sounding things in there, notably:> [COLOR="Red"]segfault[/COLOR] at f596e04c ip 00000000f61b9ee7 sp 00000000ffba6410 error 4 in libflashplayer.so[f5e1a000+b2e000]I am guessing that's our old friend "flash crash."

Also:> amd64_edac: probe of 0000:00:18.2 failed with error -22I am not sure an error at the exact time of your lockup is necessarily required. I wonder if an error in one or more processes can cascade so that the system eventually just can no longer keep up. I am speculating a bit here; I am no kernel developer.

I suggest we google the errors as well as the Network Manager error and try to solve them. I suspect (but don't know for sure) that your lockups will go away.

I still see nothing whatever that says the wireless driver *ipw2200 *is at fault.

---

### Post by chili555 on 2010-12-18
Here is a clue: [https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/560279](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/560279)

Post #7 is your exact symptom. Does post #6 help you?

---

### Post by m31ark on 2010-12-19
You're right.  It sounds like the same symptoms.  But, although Mechano said he found a fix, he didn't post it.  Launchpad also lists the status as "In***plete" and the problem as "Unassigned".  So I'm not sure how to proceed based on this report.  Any suggestions?

Last night, I tried your re***mendation of adding the hwcrypto=1 option to the driver.  On my first attempt, the system crashed right after I logged in, before I could even reload the driver with the suggested option.  On my second attempt, I was able to reload the driver but the system crashed in the usual fashion not long after I started Firefox.  By the way, where did you read about this option -- in the driver docs or the driver code?

Here's the lead-up to the first crash from syslog:

Dec 17 19:18:45 periwinkle kernel: [   29.960018] ipw2200: Failed to send POWER_MODE: ***mand timed out.
Dec 17 19:18:46 periwinkle kernel: [   30.550011] eth0: no IPv6 routers present
Dec 17 19:19:45 periwinkle gdm-session-worker[1432]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Dec 17 19:19:52 periwinkle NetworkManager[903]: <error> [1292642392.79785] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Dec 17 19:19:52 periwinkle NetworkManager[903]: <error> [1292642392.176891] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Dec 17 19:19:56 periwinkle gnome-session[1627]: WARNING: Could not launch application 'gnome-volume-manager.desktop': Unable to start application: Failed to execute child process "/usr/lib/gnome-volume-manager/gnome-volume-manager" (No such file or directory)
Dec 17 19:19:56 periwinkle rtkit-daemon[1451]: Successfully made thread 1720 of process 1720 (n/a) owned by '1000' high priority at nice level -11.
Dec 17 19:19:56 periwinkle rtkit-daemon[1451]: Supervising 4 threads of 2 processes of 2 users.
Dec 17 19:19:57 periwinkle gnome-session[1627]: WARNING: Could not launch application 'tracker-applet.desktop': Unable to start application: Failed to execute child process "tracker-applet" (No such file or directory)
Dec 17 19:19:57 periwinkle rtkit-daemon[1451]: Successfully made thread 1729 of process 1720 (n/a) owned by '1000' RT at priority 5.
Dec 17 19:19:57 periwinkle rtkit-daemon[1451]: Supervising 5 threads of 2 processes of 2 users.
Dec 17 19:19:57 periwinkle rtkit-daemon[1451]: Successfully made thread 1730 of process 1720 (n/a) owned by '1000' RT at priority 5.
Dec 17 19:19:57 periwinkle rtkit-daemon[1451]: Supervising 6 threads of 2 processes of 2 users.
Dec 17 19:19:58 periwinkle gnome-session[1627]: WARNING: Could not launch application 'trackerd.desktop': Unable to start application: Failed to execute child process "trackerd" (No such file or directory)
Dec 17 19:19:58 periwinkle rtkit-daemon[1451]: Successfully made thread 1747 of process 1747 (n/a) owned by '1000' high priority at nice level -11.
Dec 17 19:19:58 periwinkle rtkit-daemon[1451]: Supervising 7 threads of 3 processes of 2 users.
Dec 17 19:19:58 periwinkle pulseaudio[1747]: pid.c: Daemon already running.
Dec 17 19:19:58 periwinkle NetworkManager[903]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Dec 17 19:20:04 periwinkle pulseaudio[1720]: module-x11-xsmp.c: module-x11-xsmp may no be loaded twice.
Dec 17 19:20:04 periwinkle pulseaudio[1720]: module.c: Failed to load  module "module-x11-xsmp" (argument: "display=:0.0 session_manager=local/periwinkle:@/tmp/.ICE-unix/1627,unix/periwinkle:/tmp/.ICE-unix/1627"): initialization failed.
Dec 17 19:20:58 periwinkle NetworkManager[903]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Dec 17 19:23:36 periwinkle anacron[1085]: Job `cron.daily' started
Dec 17 19:23:36 periwinkle anacron[2066]: Updated timestamp for job `cron.daily' to 2010-12-17
Dec 17 19:32:57 periwinkle cracklib: no dictionary update necessary.
Dec 17 19:33:08 periwinkle rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="876" x-info="http://www.rsyslog.***"] rsyslogd was HUPed, type 'lightweight'.
Dec 17 19:34:46 periwinkle anacron[1085]: Job `cron.daily' terminated
Dec 17 19:34:46 periwinkle anacron[1085]: Normal exit (1 job run)

A perusal of the logs shows behavior similar to previous crashes in the second crash with some additional activity by avahi-autoipd just before the crash.

---

### Post by chili555 on 2010-12-19
Man, oh man! A new log with new problems. Here is a whole thread about Flash on a 64-bit system: [http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591) It's a bit scary because there are many replies that say it worked and a few that say it doesn't. I am not sure that Flash is the worst problem we have, so I'd probably keep that one in reserve.

Lots of these:> WARNING: Could not launch application 'gnome-volume-manager.desktop': Unable to start application: Failed to execute child process "/usr/lib/gnome-volume-manager/gnome-volume-manager" (No such file or directory)I am confused. Gnome-volume-manager was replaced after 9.04. Was your system a clean install or an upgrade? If an upgrade, did it go perfectly or were there some glitches?> WARNING: Could not launch application 'tracker-applet.desktop': Unable to start application: Failed to execute child process "tracker-applet" (No such file or directory)
WARNING: Could not launch application 'trackerd.desktop': Unable to start application: Failed to execute child process "trackerd" (No such file or directory)I don't understand this one at all. I do not have *tracker* on my system and my syslog shows NO errors or warnings.> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))Are there any entries in */etc/network/interfaces *other than loopback?

When you open System > Administration > Synaptic and select Edit > Fix Broken, is Synaptic able to find and fix anything? I am very interested in your upgrade or installation process.

---

### Post by m31ark on 2010-12-19
Well, I wouldn't want you to get bored.  Heh, heh.  I have upgraded this system twice this year.  At the beginning of the year, it was running 8.04 LTS.  Then I upgraded it to 10.4 LTS.  Finally, I upgraded it to 10.10.  Neither upgrade was clean.  Our friend Flash stubbornly refused to upgrade after the first system upgrade.  It took a fair bit of digging around through the Forums, several partial upgrades, and some fooling around with dpkg before I was able to solve that problem, assuming it was truly solved.  Unfortunately, I didn't keep track of the thread where I found a solution.  So I can't refer you to it.  Then, in the course of the second upgrade, the upgrade system attempted to remove the fglrx package and failed.  It took 2 partial upgrades before the offending package was removed and a couple of associated packages were upgraded.

I used to always do clean installations using new hard drives.  Then I'd attach the old system drive to the system and merge the configuration files.  But I've gotten lazy and have too many old hard drives lying around.  So trying the upgrade facility seemed like a good idea.

According to Synaptic, gnome volume manager is not installed.  Maybe there's a reference to it in some configuration file that has persisted through the upgrades.

The command "sudo grep -ri volume /etc | grep -i gnome | grep -i manager" revealed a couple of broken symbolic links and led me to the file /etc/xdg/autostart/gnome-volume-manager.desktop and /etc/hal/fdi/policy/preferences.fdi, both of which refer to gnome volume manager.  The first file seems to connect the now missing gnome volume manager to the desktop and the second is an XML file that only contains comments that show "how to use hal fdi files for system preferences".  Also, there is no directory /usr/lib/gnome-volume-manager.  The file  /usr/lib/gnome-volume-manager/gnome-volume-manager is the value of the  variable EXEC in /etc/xdg/autostart/gnome-volume-manager.desktop.  My inclination is to remove the first file and delete the stanza in the second file that has to do with the volume manager.  Does this sound reasonable?

Similar to the gnome volume manager case, there are files for tracker-applet and trackerd in /etc/xdg/autostart.  Should I remove these as well?  It doesn't seem to me like having these orphaned configuration files lying around should cause any real trouble since the corresponding programs are gone.

The contents of /etc/network/interfaces are

auto lo
iface lo inet loopback
iface eth0 inet dhcp
auto eth0

Should I remove the last 2 lines?

There are no packages marked as broken.

I read the information at [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889) and this bug seems fairly innocuous.  It's just a workaround for a bug in the offline detection feature in Firefox 3 and doesn't seem like it would have any negative collateral consequences.

It seems like the changes I outlined above should eliminate a lot of the warnings/errors we've seen in the logs.  Is there anywhere else I should look for remnants of these programs?  Unless there was a problem with the packages or the package manager, any other remnants should have been removed when the parent packages were deleted.

The 64-bit version of flash sounds promising, although I would generally prefer not to run alpha code.  It's probably worth a try, especially since there is a way to easily undo all of the changes.

It seems like we might be making a little bit of progress.  It will be great if we can get this machine fully functioning again.  It's my fastest machine and a real pleasure to use, aside from the annoying problem we've been hammering away at.  My other machines are very old, one of them almost 13 years old, and have their limitations.  Thanks a lot for digging around to help me!  I really appreciate it!

Mark

---

### Post by chili555 on 2010-12-20
Yikes!

I am going to give you two opinions; you should take whichever you feel the most comfortable with. First, I believe your issues have really exceeded my area of expertise, networking, particularly wireless. I suggest you take the problem over to General Help: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

If it were my machine, I'd back up my Home directory to, ideally, a DVD or else a USB key and reinstall after a full format. I'd set up a separate /home partition so that I could reinstall at any time in the future, if necessary, and preserve my documents, digital photos and, especially, irate letters to various government officials. 

It sounds like you have many issues. I suspect that wireless is the proverbial straw that breaks the kernel's back. It is fascinating that when you look for errors with the driver, ipw2200, or the interface, eth1, there are none.

On a properly running system with no extraordinary measures taken to do so, the should be very few errors or warnings in syslog. What are there should show clear signs that the error was recovered.

---

### Post by m31ark on 2010-12-20
In case the tales of my upgrades mislead you, I will say that I've been having a problem with similar symptoms since long before this year's upgrades.  I also had a similar problem with 8.04 LTS and both versions of 7.x and I was using completely clean installations of all of these, as I described.  I think that 7.04 is where the problem started.  Of course, it would have been better to ask for help then.  But I always do whatever I can to try to solve problems myself before bugging anyone else with them.

Regardless, I very much appreciate your help!  Thanks for rubbing my nose back in the logs and for bearing with me through our lengthy back and forth.  Best wishes and Happy Holidays!

Mark

---

