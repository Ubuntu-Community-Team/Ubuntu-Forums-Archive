---
title: "WLan upload extrem slow (3 kbit/s)"
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by LeChuck on 2009-10-16
Hi,

After getting new hardware and problems with its configuration using Jaunty, I decided to update and installed a fresh 9.10 (I know it's beta). Now, everything appears to work fine, except of WLAN which worked with 9.04

Though a connection to the internet exists, it's horribly slow. 

Even more strange, only uploading seems to be slowing down the connection, while downloading is somewhat okay (e.g. could update the system):

Download: ~3.855 kbit/s (482 kbyte/s)
Upload: ~3 kbit/s (0 kbyte/s)

I read in the forums I could solve this problem by manually setting the bit rate from 1 to 11 with
```
iwconfig wlan0 rate 11
```
but it has no effect on the upload.

After hours of reading and trying I couldn't fix this issue, and get tired, but maybe you have an idea. Any help is greatly appreciated.

---

### Post by raidmin on 2009-10-17
Hi LeChuck,

I have the same problem here with Jaunty. I checked the speed with a online speedcheck website and it says only 3 kbit upload too. Do you have already found a solution?
I also write a post in this thread [http://ubuntuforums.org/showthread.php?t=960642&highlight=rt2870&page=10#93](http://ubuntuforums.org/showthread.php?t=960642&highlight=rt2870&page=10#93)
Hope there's someone who knows how to fix this issue.

---

### Post by LeChuck on 2009-10-17
No, unfortunately not. Tried it once again, and reinstalled Jaunty where everything works fine on my computer, then upgraded to Karmic and had the same results - 3 kbit/s upload.

However, I noticed the bit rate dropped during upgrading from 54 MB/s to 1 MB/s. Maybe some configuration or scripts changed ... have no clue. Next I'll try to modify or configure the driver (mine's zd1211rw) somehow.

Otherwise Jaunty will replace Karmic for me, as long it's beta or doesn't work.

OT: Damn, these are my first serious configuration problems with Linux/Ubuntu since years. Reminds me to Linux usage long time ago, when configuration was a daily occurrence. It's great to see how well it's constructed meanwhile. Hope Ubuntu keeps up the good work and solves the problem with the final release.

---

### Post by raidmin on 2009-10-17
I just updated to Karmic and my wlan-stick was run as a wlan0 iface wich can't connect to my AP. I googled a bit and found this [http://www.mail-archive.com/ubuntu-server-bugs@lists.ubuntu.com/msg15142.html](http://www.mail-archive.com/ubuntu-server-bugs@lists.ubuntu.com/msg15142.html)
Actually I'm not serious about what it exactly does, but for me it changed the iface to ra0 and I was able to connect my AP and fixed the upload bug. The connection seems to run without draft, only on 130 mbit/s. In my case, I only use the WLAN as a separated subnet for the connection between my linux-router and my dsl-router so im fine with the speed. Maybe, it's just a configuration error but as long as it works I'll leave it.

---

### Post by LeChuck on 2009-10-30
No, karmic doesn't work here. Guess I'll get Debian instead.

---

### Post by wilk on 2009-11-01
> **LeChuck said:**
> 

I read in the forums I could solve this problem by manually setting the bit rate from 1 to 11 with
```
iwconfig wlan0 rate 11
```
but it has no effect on the upload.


For me, it did fix the upload problem, but you have to type :
```
sudo iwconfig wlan0 rate 11M
```

don't forget the M.

I don't know how to make it permanent though.

---

### Post by LeChuck on 2009-11-01
I could fix the problem thanks to [this tread](http://ubuntuforums.org/showthread.php?t=1305161) ... was a DNS problem here.

---

