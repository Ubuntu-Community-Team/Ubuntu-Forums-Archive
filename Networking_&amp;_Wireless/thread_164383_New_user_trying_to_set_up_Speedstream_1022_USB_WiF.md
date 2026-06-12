---
title: "New user trying to set up Speedstream 1022 USB WiFi - gcc error?"
date: 2006-04-22
forum: Networking &amp; Wireless
---

### Post by planetmn on 2006-04-22
Hello,
I am a new Ubuntu user (just installed 5.10 last night) and am trying to get my Speedstream 1022 USB WiFi adapter to work.  My hardware is an older Thinkpad i-Series with a C550 and 192MB of RAM.  The wireless adapter is the only way I have to connect it to the internet, so I am typing this from a different machine and would have to manually download and transfer any files.

It looks like ndiswrapper is the way to go, so I installed 1.14 on my system (in my home directory).  And I have been attempting to follow the directions included with ndiswrapper.

I also read that I need the build-essential library (version 11.1 installed) and the kernal headers (I have linux-headers-2.6.12-9 and linux-kernal-headers 2.6.11.2-0ubuntu13 installed).  So I thought I had everything, but then when I went to make sure there was a link to the kernal source from the modules directory (running the command "ls /lib/modules/2.6.12-9-386/build"), I found I have an include directory, but no .config file.

If I try to run make install, I get errors of "gcc-3.4: Command not found"

Looking back at Synaptic, it appears I have gcc (version 4:4.0.1-3), gcc-4.0 (version 4.0.1-4ubuntu9) and gcc-4.0-base (version 4.0.1-4ubuntu9) installed, but not gcc-3.4 (nor does synaptic have an option to install gcc-3.4, only gcc-3.3-base).

Any help would be appreciated.

Thanks,
dave

---

### Post by planetmn on 2006-04-23
Anybody?

---

### Post by planetmn on 2006-04-28
Another bump.  Does anybody know if I have to somehow change my gcc installation?

-dave

---

### Post by daxdog on 2007-02-10
Did you ever get this resolved?

---

### Post by planetmn on 2007-02-10
No I did not.  I stopped playing around with Ubuntu (was attempting to build a MythTV box), bought a tivo and was surprised to find out that the speedstream wifi worked with that.  I ended up buying a Zyxel router for free or cheap after rebate that can work as a wireless bridge, so whenever I've played around with Ubuntu since then, I just use that.

-dave

---

