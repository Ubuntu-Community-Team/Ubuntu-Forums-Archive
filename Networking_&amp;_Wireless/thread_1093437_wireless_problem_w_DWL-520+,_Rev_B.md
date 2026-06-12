---
title: "wireless problem w/ DWL-520+, Rev B"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by Impsterette on 2009-03-11
I'm using a DWL-520+ Revision B card in my tower, with the Win98 drivers installed with ndiswrapper (I've also tried the WinXP ones)

Whenever I try to connect to my access point, it will prompt me for the WEP key, I enter it, it'll process, and it will prompt me again without connecting, and after a few more times of this, it'll just stop.

The WEP key isn't incorrect, I've changed it 2 or 3 times, and taken off encryption entirely twice, to no avail.

Also, when I sudo pccardctl ident, there is no output.

iwconfig pops up

wlan0:

IEEE 802.11b+ Nickname:"acx v0.3.36"
Mode:Managed Frequency:2.437 GHz Access Point: 00:80:C8:1B:6A:D1
Bit Rate:1 MB/s Tx-Power=18 dBm Sensitivty=176/255
Retry min limit:7 RTS thr:off
Power Management:off
Link Quality 62/100 Signal Level=48/100 Noise level=0/100
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

Also, I noted that the Mac Address listed under router settings is the same as above, except "D2". I don't know how that works though, so I don't know if that's normal.

My laptop connects fine to wireless, just my desktop has this issue.

---

