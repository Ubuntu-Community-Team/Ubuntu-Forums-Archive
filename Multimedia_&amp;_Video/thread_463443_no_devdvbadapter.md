---
title: "no /dev/dvb/adapter"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by birkensteen on 2007-06-03
new Fiesty install, trying to get pchdtv-5500 card working.

using the dtvsignal i show signal strength, so that's promising..

but when trying dtvsignal or dtvscan i see this error:

```
mythtv-01:~$ dtvsignal 42
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
ERROR: failed opening '/dev/dvb/adapter0/frontend0' (No such file or directory)
dtvsignal ver 1.0.5 - by Jack Kelliher (c) 2002,2005,2006
channel = 42 freq = 641000000Hz
 30db       0%         25%         50%         75%        100%
Signal:     |     .     :     .     |     ._____:_____._____|
Signal: 090 $$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$
```

or 

```
mythtv-01:~$ dtvscan
dtvscan ver 1.0.5 - by Jack Kelliher (c) 2002,2005,2006
Attempting to open /dev/dtv
/dev/dvb/adapter0/frontend0: No such file or directory
```

Any ideas? The pchdtv forums are heavily spammed, so I'm trying here first. FWIW I didn't have this problem with Edgy...

---

