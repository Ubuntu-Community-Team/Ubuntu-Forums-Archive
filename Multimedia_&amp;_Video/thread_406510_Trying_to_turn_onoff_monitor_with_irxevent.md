---
title: "Trying to turn on/off monitor with irxevent"
date: 2007-04-11
forum: Multimedia &amp; Video
---

### Post by ebike on 2007-04-11
Hi All,

I want my lirc remote to turn on/off my plasma monitor using dpms and xset.
I found a howto somewhere with the following instructions.

> 
Put this stanza in .lircrc

# Power Button
begin
prog = irexec
button = POWER
repeat = 4
config = /usr/local/bin/monitorpowerbutton.sh
end

And this script as /usr/local/bin/monitorpowerbutton.sh

#!/bin/bash

STATUS=`xset -q | grep "Monitor is" | awk '{print $3}'`

if [ "${STATUS}" = "On" ]
then
xset dpms force off
else
xset dpms force on
fi
exit 0



The script seems to work, but irexec complains about the line:

> config = /usr/local/bin/monitorpowerbutton.sh


It says it is not a valid config line. Can anyone help here.

Thanks

---

### Post by ebike on 2007-04-11
Bump

---

