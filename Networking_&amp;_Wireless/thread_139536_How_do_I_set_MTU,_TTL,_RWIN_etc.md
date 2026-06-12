---
title: "How do I set MTU, TTL, RWIN etc?"
date: 2006-03-04
forum: Networking &amp; Wireless
---

### Post by Ruskie on 2006-03-04
Hello,

I used to have a smoothly running Internet connection both with Windows and Linux. My network schema was:


  My box <-- 192.168.2.0 --> Wi/Fi Router <-- 192.168.1.0 --> Adsl Modem
                       |
                       |
               Other Pc's

Suddenly, my provider must have changed something because internet access stopped working for most sites (while, strange enough, I could reach someone: google, my provider's, America's Army server, but NOT my provider's email for instance). Weirdly, all sites were pingable, also through their DNS name.

I now have my Windows box working because the IT support guided me through some changes, that is, using Dr Tcp they made me set:

Tcp Receive Window: 17520
Path MTU Discovery: Yes
Window Scaling: No
Black Hole Detection: No
Time Stamping: No
Max Duplicate ACKs: 2
Selective Acks: Yes
TTL: 128
Dial Up (RAS) MTU: -

Adapter Settings
	MTU: 1492

I would like to ask you: how can I replicate these changes to Linux (that still does not connect to most sites)?

Thank you very much for your help!

---

### Post by mips on 2006-03-05
[http://ubuntuforums.org/showthread.php?t=82093](http://ubuntuforums.org/showthread.php?t=82093)
[http://www.ubuntuforums.org/showthread.php?t=104371](http://www.ubuntuforums.org/showthread.php?t=104371)

A start...

---

### Post by Ruskie on 2006-03-06
Thank you MIPS, the first thread resumes what I already knew; I will try the suggestions in the 2 thread and in those quoted there.

---

### Post by Ruskie on 2006-03-07
Yeah, that did the trick, thank you very much.
And I even got to learn something new on tcp!  :D

Bye
Marco

---

