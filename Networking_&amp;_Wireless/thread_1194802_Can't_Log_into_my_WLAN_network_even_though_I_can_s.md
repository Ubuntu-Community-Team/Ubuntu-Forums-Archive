---
title: "Can't Log into my WLAN network even though I can see it - Ubuntu 9.04"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by AJack10600 on 2009-06-23
Hi, 
 
I'm brand new, have just installed Ubuntu to give it a try and am already stuck... Have installed Ubuntu 9.04 on my 2nd PC and am now trying to get the network connection to work. 
 
Now Ubuntu does see my network and also asks me for my key but it refuses to take on my 128bit WEP ASCII 13 digit key. I can entre it all right, but then it just keeps trying to connect until it stops and asks for the key again. 
 
I've got no idea what the other settings are there for but I tried pretty much all combinations. 
 
Judging from the forum and other comments on the net, Networking does not seem to be the strength of Ubuntu... hope I woant regret installing it.. 
 
Any help is much appreciated..

---

### Post by AJack10600 on 2009-06-23
If anybody else is having a similar issue, please feel free to comment.. ;)

---

### Post by AJack10600 on 2009-06-23
Ok apparently a lot of people have this problem judging from the number of reads 
;) Did some reading up on this and come to the following conclusion...
 
It seems that Ubuntu 9.04 does not support 64 and 128 bit HEX WEP key... now that is funny cos apparently the last Ubuntu did not support it either... WTF :confused:
 
Apparently WCID can fix it ? Will have an attempt when I get home.

---

### Post by AJack10600 on 2009-06-24
I solved this myself... 
 
The problem is that Network Manager and WICD want Hex code...
 
My Key was 128 Bit ASCII... 
 
But you can convert ASCII into Hex code. 
 
When translating ASCII into Hex code and entering that Hex string, it woks perfectly.. 
 
(you can find a hex converter here:
[[SIZE=2][COLOR=#52768f]http://www.mml.uni-hannover.de/einhorn/jstools/wepkey.html[/COLOR][/SIZE]]("http://www.mml.uni-hannover.de/einhorn/jstools/wepkey.html")[SIZE=2] )[/SIZE]
 
I find it strange that the Network Manager and WICD can not make the conversion. 
 
Anyhow, problem solved for me, hope that helps some of you out there! 
 
Good Luck !

---

