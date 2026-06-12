---
title: "sudo lshw -c network doesn't output anything?"
date: 2011-03-09
forum: Networking &amp; Wireless
---

### Post by Tydoskus on 2011-03-09
[LEFT]*[SIZE=3]sudo lshw -c network[/SIZE]*
[SIZE=3]and[/SIZE]
*[SIZE=3]sudo lshw -class network[/SIZE]*
[SIZE=3]do not output anything in the Terminal.[/SIZE]

[SIZE=3]It shows a glimse of DMI, PCI(sysfs), and SCSI then it's done.
And yes i waited to see if it outputs anything else but it doesn't.
[/SIZE] [/LEFT]

---

### Post by Iowan on 2011-03-09
My machine doesn't like **sudo lshw -c network** (it prefers **sudo lshw -C network**) - but responds to **sudo lshw -class network**. Do you get any results from simply **sudo lshw**? If the machine doesn't recognize the network hardware...

(What kind of card are you using?)

---

