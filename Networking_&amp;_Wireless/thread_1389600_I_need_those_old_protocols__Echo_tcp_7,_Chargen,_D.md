---
title: "I need those old protocols  Echo tcp 7, Chargen, Dischard, DayTime ..."
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by n45w73 on 2010-01-24
hi

noob question :P

I need those old protocols  Echo tcp 7, Chargen, Dischard, DayTime ...

I didn't found any software in the repo,  neither Kamic seems to respond to them  ....

Any suggestions for bundle software and or  some howto ?

Thanks.

---

### Post by n45w73 on 2010-01-30
bump !

i can see my thread  isn't really popular ! ...
but anyways here what i found elsewhere...

all standards tcp/udp  servers,  Echo, Chargen, Dischard, Daytime ...  are implemented by on superserver  named  inetd.

ubuntu doesn't have it by default,  u have to install it.
there's is 2 choices it seems  openbsd-inetd  and xinetd.
xinetd seems a little bit better cause u can specified some options not include in basic inetd and it is a bit easier to configure...
also openbsd-inetd doesn't provide example of configuration file,  so u will need to surf in other linux distros to find useful hints ...

so .. there u go ! :)

---

