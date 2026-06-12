---
title: "Wireless Stops working randomly - restart fixes"
date: 2010-07-05
forum: Networking &amp; Wireless
---

### Post by Stewie2kill on 2010-07-05
Hey guys,
 
     I recently helped my friend make the plunge into the wonderful world of Ubuntu and he's been loving it. I set him up on 10.04 and after plugging it into the ethernet connection it found his wirless driver (fwcutter) just fine and I was able to install it via the hardware drivers manager.

     He's been doing fairly good for about two weeks now until just recently when he's noticed that his internet connection will just disconnect at some point in the night. He likes to do his downloading at night over qBittorrent so that it doesn't slow the network traffic down too much - however when he wakes up he finds that his downloads have stopped and the network has disconnected. He can't reconnect to the network either. He's somewhat tech savvy and I trust his when he says he can't reconnect. 

     restarting his computer causes the internet to refresh and it connect just fine as usual. He's using a WEP encryption on his wifi i believe and no one else in the house is having this issue.

Any thoughts as to what I might be able to do to help my friend? He's been doing so good on Ubuntu and loves it - I'd hate for him to get a bad taste in his mouth about linux.

---

### Post by mmzdaniel on 2010-07-05
I seem to be getting the exact same problem. from what ive seen, its probably a bug with network manager. From my research I found that people with similar problems are told to get wicd instead of network manager, that might just work for you. Unfortunately it did not work for me but it might for your friend.

---

### Post by Stewie2kill on 2010-07-05
thanks for the tip. I'll see about trying that for him. The last time I tried to get wicd was about a year back though and things seemed to not go very smoothly when it came to the install... of course that was before the wonderful invention that is the software center so I'll try it as soon as I can. Thanks.

---

### Post by mmzdaniel on 2010-07-05
I dont really use that one but I remember seeing it in synaptic.
If it isn't there, try compiling it from source, if I can recall it was something like
```
python setup.py configure
python setup.py install
```
The tar has an install text file and it pretty much as everything there.

---

