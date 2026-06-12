---
title: "command to know current net speed"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by sulekha on 2009-02-12
Hi all,

whenever i download files using wget it will show download speed as 60kbps etc.

now what is the command to get current net speed without downloading any file ?

i tried the following

sudo ethtool -S eth0
[sudo] password for user:

NIC statistics:
early_rx: 0
tx_buf_mapped: 0
tx_timeouts: 0
rx_lost_in_ring: 0

but still i am not getting the speed in kbps

---

### Post by Neural oD on 2009-02-12
sudo apt-get install iftop

---

### Post by sanemanmad on 2009-02-12
Are you wanting to know your download speeds from the WWW, or from your Home LAN? If the first is the case then wget is probably accurate, however, you must take in account the network load or your routers capabilities. Try performing a speed test at a website that tests down/up speeds.

One way to be more precise, If you have cable or dsl, then you should be able to connect directly to the modem via cat5e and attempt wget.

perform a wget from a known website, ie, sourceforge, download.com.

Also GOOGLE is your friend, In my case I usually google what i am looking for ex (DWA-556 Atheros wireless card ubuntu) and it usually points here anyway :P

---

### Post by Neural oD on 2009-02-12
wasn't thinking too clearly - sorry - I had discovered another tool a while ago that works great - bwm-ng 
it's in the repos

---

### Post by sulekha on 2009-02-12
what about this line of thinking ?

you need to download/upload something in order to see the actual speed.
However, your speed is limited by the speed of the other site.

---

### Post by sanemanmad on 2009-02-12
Heck, You can use apt-get update && apt-get upgrade and watch the speeds that way too.

---

### Post by ragestar on 2009-02-12
Heck,apt-get install iptraf:)

---

