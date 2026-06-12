---
title: "puppy huawei e220 connection"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by unclejack3 on 2009-03-13
i am using puppy,with  usb huawei e220 card but it does not work.I downloaded this file huawei tar.bz2 and i need to do 
this,,

If you want to make a connection right after the modem is plugged in,
	with this package, you can create a /root/.huawei-config file
	with the following content:

	--- 8< ---
	wvdial --config /etc/wvdial-huawei.conf
	--- >8 ---

	or if you prefer 
	--- 8< ---
	pppd call huawei-e220
	--- >8 ---

how do i do this ??and where...

---

