---
title: "Wireless Troubles"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by Kanawinkie on 2010-03-30
Hello! I should start by saying that I am very new to Linux (less then a month) and I am not very computer savvy at all.

I had everything up and running; my wireless connection was working perfectly. Randomly this morning it began asking for me to re-enter the WPA password for my Network. I would do so, and it would try to find the Network then refresh to the re-enter the security password window.

I disconnected wireless networks (left-clicking the icon at the bottom of the screen) with the intention of reconnecting from scratch, although now I am unable to find any wireless settings; with Networks Enabled I can only see "Networks Available: None" greyed out and un-clickable. 

Rebooting hasn't helped.

Any suggestions on where I can go from here to reconnect my wireless internet would be much appreciated!
Thanks so much.

---

### Post by devildoc5 on 2010-03-30
havent been on in a little while so I am not sure if this is an answer but did you update the kernels or update the version of ubuntu at all?  Also what card are you using?  this will help out immensly...

---

### Post by Kanawinkie on 2010-03-30
Everything was up to date as of this morning that I'm aware of...

It is a Hama WLAN PCI Card; 54 Mbps 00062788

Thanks so much, let me know if there's any other info I can supply, I'll do my best to find it!

---

### Post by devildoc5 on 2010-03-30
ok but did you do an update?  like was there an update that CAUSED this to stop functioning?  Also try posting an lspci and lsusb report.

---

### Post by teejmya on 2010-03-31
It could always be the obvious.
Make sure that the Access Point is broadcasting.
Can any other wireless devices connect while this machine cannot?

Also, it could always be the driver.
Please type lspci and lsusb in the terminal separately, and copy/paste the results here.
([S]That might have been mentioned earlier, if so, my bad.[/S])
EDIT: It was said by devildoc5. My baaaad...

---

