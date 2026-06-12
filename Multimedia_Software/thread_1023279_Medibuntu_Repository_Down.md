---
title: "Medibuntu Repository Down?"
date: 2008-12-27
forum: Multimedia Software
---

### Post by diw on 2008-12-27
> sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list
--2008-12-28 00:07:09--  [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... failed: Name or service not known.
wget: unable to resolve host address `[www.medibuntu.org](www.medibuntu.org)'



**I've been trying all day.  Is the repo temporarily down or permanently?**

---

### Post by xc3RnbFO8P on 2008-12-28
Try this (just copy/paste into Terminal window):
> sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
<Enter>
> sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
<Enter>

---

### Post by steeleyuk on 2008-12-28
Not working here either.

---

### Post by xc3RnbFO8P on 2008-12-28
Strange 

> rob@rob-desktop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list 
[sudo] password for rob: 
--2008-12-28 12:56:00--  [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 230 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 230         --.-K/s   in 0s      

2008-12-28 12:56:00 (29,1 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [230/230]


---

### Post by steeleyuk on 2008-12-28
It must be my (our) local DNS server because I've tried accessing through a proxy and its working fine. Never mind...

---

### Post by diw on 2008-12-28
Thanks guys - seems to be ok for me tonight.

---

