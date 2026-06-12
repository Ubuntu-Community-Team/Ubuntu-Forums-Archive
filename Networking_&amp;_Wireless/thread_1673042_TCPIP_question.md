---
title: "TCP/IP question"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by brivy on 2011-01-21
I want to ask the community if Ubuntu's implementation of the TCP/IP stack is more, or less, efficient when compared to Microsoft's implementation?  I have found when working with XP, Vista, and to a lesser degree, 7, that the stack requires an enormous amount of tweaking to get decent throughput with an acceptable amount of packet loss. I have never been able to figure out if this has been poor engineering on Microsoft's part, or just conservatism to the point of ineptitude. I have searched through the forums for a guide that would assist me in tuning Ubuntu but haven't found anything.  If someone could point me in the right direction with this it would be greatly appreciated.

---

### Post by CharlesA on 2011-01-21
TCP/IP is TCP/IP.

I haven't noticed any difference between Windows and Linux in that regard.

---

### Post by SeijiSensei on 2011-01-22
The stack in recent Windows implementations has some built-in [limits on the number of multiple connections]("http://serverfault.com/questions/51597/how-to-fix-tcp-ip-has-reached-the-security-limit-event-message") that can exist at one time.  These were supposedly added to protect against problems from malware.  They also pose a problem for BitTorrent users since BT routinely sets up dozens of connections to peers. 

There's nothing like this in the Linux networking stack that I know of.

---

### Post by brivy on 2011-01-22
Thank you for your replies. I thought that might be the case considering the nature of Linux and the Linux community. It is always such a nightmare when dealing with Windows.

---

