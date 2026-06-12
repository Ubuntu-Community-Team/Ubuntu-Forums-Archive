---
title: "Help slow internet speed test in Ubuntu"
date: 2013-04-26
forum: Networking &amp; Wireless
---

### Post by southie4905 on 2013-04-26
[SIZE=3][FONT=arial black]***Help slow internet speed test in Ubuntu***
[/FONT][/SIZE]
[SIZE=3][FONT=arial black]
[/FONT][/SIZE]
[SIZE=3][FONT=arial black]New to Linux. Just installed Ubuntu 13.04 and love it. Was previous on Windows Vista Home. Unfotunatly I experience slow internet speed as tested with Speedtest.net in Ubuntu 12.04 and 13.04 as compared with Windows over a period of 3 days.
[/FONT][/SIZE]
[SIZE=3][FONT=arial black]
[/FONT][/SIZE]
[SIZE=3][FONT=arial black]I run a wired connection to a fibre broadband 30/10 over a Pace V5542 Gateway router. Tested speeds as follow:[/FONT][/SIZE]
[SIZE=3][FONT=arial black]
[/FONT][/SIZE]
[SIZE=3][FONT=arial black]Windows[/FONT][/SIZE]
[SIZE=3][FONT=arial black]Download: between 23.72 to 27.88[/FONT][/SIZE]
[SIZE=3][FONT=arial black]Upload: between 8.64 to 9.58[/FONT][/SIZE]

[SIZE=3][FONT=arial black]
[/FONT][/SIZE]
[SIZE=3][FONT=arial black]Ubuntu 13.04[/FONT][/SIZE]
[SIZE=3][FONT=arial black]
[/FONT][/SIZE]
[SIZE=3][FONT=arial black]Download: 7.25 to 14.36[/FONT][/SIZE]
[SIZE=3][FONT=arial black]Upload: 7.93 to 9.52[/FONT][/SIZE]
[SIZE=3][FONT=arial black]
[/FONT][/SIZE]
[SIZE=3][FONT=arial black]What can I do to better the speed?[/FONT][/SIZE]
[SIZE=3][FONT=arial black]  
[/FONT][/SIZE]

---

### Post by ahallubuntu on 2013-04-26
~

---

### Post by bobblex on 2013-04-27
Check the MTU settings for your network card.  Mine were defaulted to "Auto".  I changed it to 1492 and regained my 50/25 Mbps speeds.

---

