---
title: "cannot detect wireless and no sound"
date: 2011-08-20
forum: Networking &amp; Wireless
---

### Post by edward091810 on 2011-08-20
hi i'm sorry for being a noob but, i should ask this to get information straight to the point. i installed a ubuntu 10.04 netbook edition side by side with windows 7 professional on my netbook hp mini 110-3000 ee pc, ubuntu loaded very fine but the problem is after downloading all the required software and install everything ubuntu cannot detect wireless, (whereas windows 7 can detect) and even if i installed all needed plug-ins i still can't hear any sound tying to play mp3 or in youtube. anyone would like to help me i tried browsing the forums but none of it gave a best answer. thank you in advance...

---

### Post by sanderj on 2011-08-20
Can you install Ubuntu 11.04 and see if that works for your wifi and sound? 

And: no need to worry about "netbook edition" etc: that was only a name for 10.04 with the now common Unity interface. Your netbook has a x86 processor, so you can run the plain Ubuntu version.

---

### Post by edward091810 on 2011-08-20
> **sanderj said:**
> Can you install Ubuntu 11.04 and see if that works for your wifi and sound? 

And: no need to worry about "netbook edition" etc: that was only a name for 10.04 with the now common Unity interface. Your netbook has a x86 processor, so you can run the plain Ubuntu version.

how can i upgrade to 11.04 or shall i DL the file and install it once again? okay ill try re-installing it

---

### Post by edward091810 on 2011-08-20
> **sanderj said:**
> Can you install Ubuntu 11.04 and see if that works for your wifi and sound? 

And: no need to worry about "netbook edition" etc: that was only a name for 10.04 with the now common Unity interface. Your netbook has a x86 processor, so you can run the plain Ubuntu version.

miredo already installed ipv6 is okay

---

### Post by edward091810 on 2011-08-20
> **sanderj said:**
> Can you install Ubuntu 11.04 and see if that works for your wifi and sound? 

And: no need to worry about "netbook edition" etc: that was only a name for 10.04 with the now common Unity interface. Your netbook has a x86 processor, so you can run the plain Ubuntu version.

done installing miredo ipv6 ok

Test with IPv4 DNS record	 	
ok (1.544s) using ipv4
Test with IPv6 DNS record	 	
ok (1.927s) using ipv6 Teredo
Test with Dual Stack DNS record	 	
ok (1.211s) using ipv4
Test for Dual Stack DNS and large packet	 	
ok (1.164s) using ipv4
Test IPv4 without DNS	 	
ok (0.638s) using ipv4
Test IPv6 without DNS	 	
ok (1.389s) using ipv6 Teredo
Test IPv6 large packet	 	
ok (1.911s) using ipv6 Teredo
Test if your ISP's DNS server uses IPv6	 	
bad (0.706s)



after typing iwconfig 


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

teredo    no wireless extensions.

---

### Post by edward091810 on 2011-08-20
i manage to solve it downloading rt3090 and installed it the after reboot i instantly got a connection

---

