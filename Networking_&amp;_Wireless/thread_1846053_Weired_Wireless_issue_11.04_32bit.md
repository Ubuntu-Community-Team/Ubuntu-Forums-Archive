---
title: "Weired Wireless issue 11.04 32bit"
date: 2011-09-18
forum: Networking &amp; Wireless
---

### Post by Little_Ho on 2011-09-18
Hey i have an weired issue with my wireless and Ubuntu 11.04 32bit.

I use a Pogoplug which uses FUSE to communicate and to make it remotly available so it looks like a local plugged in Drive.

my problem is that after trying to move a file or several files to the drive i get this in the terminal:


[092153.270][374280][HBFUSE][02] MKDIR [1:'.Trash-1000'] Failed 13 'Permission denied'
[092154.856][658051][HBFUSE][02] RMDIR Failed 5 'Input/output error'
[092209.976][658051][HBFUSE][02]     -- UNLINK existing id: 616
[092213.702][458207][HBFUSE][02]     -- UNLINK existing id: 613
[092217.570][658051][HBFUSE][02]     -- UNLINK existing id: 631
[092221.789][458207][HBFUSE][02]     -- UNLINK existing id: 621
[092224.452][542134][HBFUSE][02]     -- UNLINK existing id: 618
[092228.481][247100][HBFUSE][02]     -- UNLINK existing id: 630
[092231.483][458207][HBFUSE][02]     -- UNLINK existing id: 637
[092236.087][542134][HBFUSE][02]     -- UNLINK existing id: 614
[092238.385][247100][HBFUSE][02]     -- UNLINK existing id: 619
[092241.091][658051][HBFUSE][02]     -- UNLINK existing id: 612
[092243.770][458207][HBFUSE][02]     -- UNLINK existing id: 624
[092246.521][458207][HBFUSE][02]     -- UNLINK existing id: 622
[092249.446][542134][HBFUSE][02]     -- UNLINK existing id: 638
[092251.992][374280][HBFUSE][02]     -- UNLINK existing id: 620
[092347.083][247100][BRSOCK][01] Failed [connect_complete]: 113: No route to host!
[092347.083][247100][CONNPO][02] >>> [[http://192.168.0.198:80]](http://192.168.0.198:80]) FAILED TO CONNECT: -10
[092356.139][542134][BRSOCK][01] Failed [connect_complete]: 113: No route to host!
[092356.139][542134][CONNPO][02] >>> [[http://192.168.0.198:80]](http://192.168.0.198:80]) FAILED TO CONNECT: -10
[092426.182][658051][CONNPO][02] >>> [[http://192.168.0.198:80]](http://192.168.0.198:80]) FAILED TO CONNECT: -11
[092438.203][374280][BRSOCK][01] Failed [connect_complete]: 113: No route to host!
[092438.203][374280][CONNPO][02] >>> [[http://192.168.0.198:80]](http://192.168.0.198:80]) FAILED TO CONNECT: -10


after that my internet connection is still saying its connected but i cant go online. 
after a forced restart or a disable/enable wireless its working again...

Is that a bug or something else???
I have that Pogoplug for a while and just recently noticed the issue...

Thanks for help

---

