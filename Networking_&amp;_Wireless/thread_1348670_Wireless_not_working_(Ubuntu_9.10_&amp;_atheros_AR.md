---
title: "Wireless not working (Ubuntu 9.10 &amp; atheros AR5007EG)"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by Pattoow on 2009-12-07
as the topic says it just dont work trie'd almost everyting to get it working but it still doesnt work.

Atm I am useing wicd network manager,
someone please help me...

---

### Post by amsum on 2009-12-07
Look into the file
/etc/modprobe.d/blacklist-ath_pci.conf

and then comment out the line...
blacklist ath5k

so it should look like
#blacklist ath5k

Now Save it and reboot the system. It must recognize the wireless after rebooting.

---

### Post by Pattoow on 2009-12-07
there is no line in that file...

---

### Post by kp4djt on 2009-12-15
Folks,
I have a Lenovo S10, I wanted to run Kismet on it, but the Broadcom Wifi radio does not allow for scanning and other stuff that Kismet needs to do, so I ordered a Atheros AR5007EG card for the machine. It arrived and works
great, it sees AP's that the broadcom board never saw, but somehow the thing
goes to sleep, it must be activity controlled because it never happens when
I am using the thing, but say when I leave it several hours or finish in the
evening, then check it the next morning, the RF connection is lost, if I do a iwconfig it says it is not associated, if I try to do a association nothing happens. Beyond this issue, the little board works great runs circles around the broadcom board.

Has anyone else seen this issue, I have looked in the logs to see if I can find where it did it's exit but I see nothing. The system reports it is there but it just not active. 

I love it using kismet, it really works, I was out in a park that had always looked like a wast land RF wise, but with the Atheros card I see
stuff I did not even know was there with the Broadcom. Of course it is all
locked down so I can not access it, but at least I can see it.

Look for your notes.

---

### Post by kp4djt on 2009-12-15
Oh yes, the other thing I notice is when I list the network stuff it shows the card as a AR5001 not sure if that is just the generic driver, of what. I do not think it is loading the madwifi driver as it does not show up as such. Perhaps I need to load a newer driver than the AR5001?

---

### Post by drpjkurian on 2009-12-16
Hi Guys

Please give a try to my thread. It might help you.

[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

With regards
Dr Kurian

---

