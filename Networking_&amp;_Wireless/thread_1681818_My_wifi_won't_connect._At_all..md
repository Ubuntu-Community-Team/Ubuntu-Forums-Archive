---
title: "My wifi won't connect. At all."
date: 2011-02-04
forum: Networking &amp; Wireless
---

### Post by korb8495 on 2011-02-04
Hey guys ):P this is my first "bean" here. lol
I'm having a problem with the Wi-Fi.
Here's what's going on, I just installed Ubuntu today :). Everything is working perfectly except the wi-fi.
I've looked heavily into it, and have debunked it as being the WPA/WPA2 problems people have been having as my router security type is WEP-64 Bit. At first I thought it was my router security type as I went to configure the network properties on here (I'm running Ubuntu at the moment, with a wired connection) and it didn't show exactly WEP-64 Bit, it showed WEP 40/128-bit Key (HEX or ASCII) and WEP 128-bit passphrase. So I went to change my router security type to WEP 128-bit. After I did I tried to connect, but still no luck. It said I was connected, but whenever I tried to access anything that needed the Internet it wouldn't connect. I'm clueless at this point :confused:.
Being wired sucks.:sad:

---

### Post by korb8495 on 2011-02-05
Ok so, I've read up a little bit.
I tried to install ndiswrapper 1.56.
I got [Error 2] in the terminal. It's due to dependencies ndis relies on that I don't have. Anyone know how to get or install them?

---

### Post by ronnielsen1 on 2011-02-05
It's not a wep/wpa thing. Can you post the output of lspci -v in a terminal. Also, what is the manufacturer and model of your wireless router?

---

### Post by ronnielsen1 on 2011-02-06
Did you give up?

---

