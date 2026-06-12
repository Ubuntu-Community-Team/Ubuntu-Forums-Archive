---
title: "cant find wireless on my netbook"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by mbsrider145 on 2010-03-30
I have recently switched my samsung n130 with windows 7 starter to the ubuntu netbook remix. When I go onto it, it doesn't even look for a wireless connection. All there is is a wired auto ethos. How can i get my netbook to recognize my wireless connection in my house?

---

### Post by James Little on 2010-03-31
Maybe Ubuntu doesn't recognise the hardware at all? Run the following at the command prompt and paste the output:
iwconfig
lspci -vvnn

Also, what version of Ubuntu are you running? I assume Karmic?

---

