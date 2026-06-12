---
title: "How to release data call correctly using script"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by bperng on 2010-10-13
[FONT=Arial][SIZE=3]I am the new user on Linux system.  Recently, I have tested my CDMA Data module (EV-DO Rev A) with the following scripts running on Kernel 2.6.32.24 without any issue to connect to Verizon network in US:[/SIZE][/FONT]
[FONT=Arial][SIZE=3]>>[/SIZE][/FONT]
[FONT=Courier New][FONT=Arial][SIZE=3][COLOR=blue]ABORT "BUSY"
ABORT "NO CARRIER"
""    ATZ\r
OK    ATM1L1\r
OK    ATDT#777
CONNECT[/COLOR][/SIZE][/FONT][/FONT]
[FONT=Courier New][FONT=Arial][SIZE=3]<<<[/SIZE][/FONT][/FONT]
[FONT=Courier New][FONT=Arial][SIZE=3]1. Is it a correct srcipt file to use or should I improve that to work better?[/SIZE][/FONT][/FONT]
[FONT=Courier New][FONT=Arial][SIZE=3]2. How do I release the data call with correct script file?  Can anyone provide one example of script file?  [/SIZE][/FONT][/FONT]
[FONT=Courier New][FONT=Arial][SIZE=3][/SIZE][/FONT][/FONT] 
[FONT=Courier New][FONT=Arial][SIZE=3]Currently, I used <cntl>Z to terminate the application from Linux which I think the data call is still connected to Verizon.  I believe it should have a script file for me to disconnect the data call like I did on "pppd" to initiate the data call connection.[/SIZE][/FONT][/FONT]
[FONT=Courier New][FONT=Arial][SIZE=3]
Thanks.
 
bp[/SIZE][/FONT][/FONT]

---

