---
title: "Solution to wireless switching on/off Atheros A928X"
date: 2011-03-05
forum: Networking &amp; Wireless
---

### Post by Lexworth on 2011-03-05
Anyone having problems with this chipset such as poor signal reception, wireless cutting in and out I finally found a solution. I've been working on this for about a week now. Running Ubuntu 10.10 64bit, it says that this wireless configuration just works but I, along with a few others I have seen, have had less than optimal performance. 

What you need to do is download the compat-wireless drivers from this website [http://wireless.kernel.org/en/users](http://wireless.kernel.org/en/users). You have to download the source and compile it, but its not that hard. I'm pretty new to Ubuntu and was able to figure it. There are plenty of source compilation guides that can help. 

Anyway, I installed the updated ath9k drivers and wireless performance has been flawless ever since. Only problem is that I lost my bluetooth in the process. Think this was a result of the sudo unload all command I used.

Hope this is at least somewhat helpful to others out there who are searching for a solution to this.

---

