---
title: "Gigabyte lan, ubuntu to win7 file copy very fast, other way slow, in fact worthless"
date: 2013-01-03
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2013-01-03
I recently reconfigured the home network. I have an ubuntu pc connected directly to a win7 pc. Nic to Nic
I can copy very fast from ubuntu to win7 PC 30MB/sec, but the other way is measured in kb/sec

I turned on jumbo frames and have a gigabyte connection between them.

so what do you think is going on?
Hurdles.

---

### Post by sdowney717 on 2013-01-04
Temporarily solved I think.
I set jumbo frames back to 1500
in win7 I set jumbo frames to diasabled
And set to to 1.0gbs full duplex and enabled lots of options such as large send offload

Currently now getting 50MB/sec

---

### Post by sdowney717 on 2013-01-04
I found out that Large Send offload v2 should be ENABLED ip4 and 6, even though many web forums claim set to disabled speeds up the lan. I found with it disabled, transfer speeds fell from 50 to 10Mb/s

Not even understanding what this does.

contrary web forum posts are here.
[http://www.networksteve.com/windows/topic.php/Windows_7_Ultimate_-_Painfully_slow_file_transfer_on_ethernet_ne/?TopicId=5820&Posts=3](http://www.networksteve.com/windows/topic.php/Windows_7_Ultimate_-_Painfully_slow_file_transfer_on_ethernet_ne/?TopicId=5820&Posts=3)

---

