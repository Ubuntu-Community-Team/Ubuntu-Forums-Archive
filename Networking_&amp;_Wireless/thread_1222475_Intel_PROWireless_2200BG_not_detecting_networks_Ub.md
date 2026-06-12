---
title: "Intel PRO/Wireless 2200BG not detecting networks/ Ubuntu 9.04"
date: 2009-07-24
forum: Networking &amp; Wireless
---

### Post by amac2629 on 2009-07-24
Hi all,

I just dual booted Ubuntu 9.04 on my Dell Inspiron 6000 with XP, and my Intel PRO/Wireless 2200BG card does not seem to detect any networks. I believe it is a problem with the driver. Below is a summary of the information I've found from the operating system.

Results of iwconfig:

[html]lo   no wireless extensions

eth0   no wireless extensions

eth 1   unassociated   ESSID: off/any
          Mode: Managed   Channel =  0     Access Point: not assigned
          Bit Rate: 0     Tx-Power = 20dBm
          Sensitivity 8/0               Retry Limit : 7
          RTS Thr: off    Fragment thr: off
          Power Management: off
          ...everything else : 0 ....

pan0    no wireless extensions[/html]I believe that I have firmware installed because the following files exist in /lib/firmware:

ipw2200-bss.fw
ipw2200-ibss.fw
ipw2200-sniffer.fw

Finally, my Hardware Drivers window tells me that "No proprietary drivers are in use on this system."

I apologize in advance: I only have access to wireless internet, so I have to boot into XP to respond to posts since my ubuntu wireless is not working. Thus, I cannot just copy/paste shell output here; I have to boot into Ubuntu, copy the output by hand, then reboot into XP and type it up. Please keep this in mind when asking for command outputs. It will be much easier for me if you could tell me the exact lines or output you're looking for.

Thank you.

---

