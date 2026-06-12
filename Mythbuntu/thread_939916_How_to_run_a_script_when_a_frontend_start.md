---
title: "How to run a script when a frontend start??"
date: 2008-10-06
forum: Mythbuntu
---

### Post by impossibilechecisiaquesto on 2008-10-06
Hi, i have three frontend and i like to know how can i run a script (that Turn On my decoder) when a start a frontend.

Thanks.

---

### Post by ian dobson on 2008-10-06
Hi,

Have a look at rc.local, it starts when you boot the PC.

or create a script that looks to see if mythfrontend is running and if yes do something. I've written this to restart the frontend when it dies:-

```
#! /bin/bash
# Provides:          check if the Myth-Frontend is still running
# Short-Description: if it dies restart it
# Author:            Ian Dobson (i.dobson {at} planet-ian.com
sleep 30
while [ "1" != "0" ]; do
   Active=`ps -A| grep "mythfrontend"`
   if [ "$Active" == "" ]; then
      killall -15 gdm
      sleep 5
      /etc/init.d/gdm start
     sleep 15
   fi
   sleep 30
done
```

Just change the code about abit to call your decoder script then wait until frendend is no longer running then restart the script from the top.

Regards
Ian Dobson

---

### Post by impossibilechecisiaquesto on 2008-10-08
thanks

---

