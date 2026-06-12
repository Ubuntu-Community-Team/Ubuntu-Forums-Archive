---
title: "Auto starting MythWelcome/Disabling MythTV Exit?"
date: 2008-06-15
forum: Mythbuntu
---

### Post by Lindsay.Mathieson on 2008-06-15
Hi All,

I'd like to disable the ability to exit the mythfrontend and as far as I can tell the best way to do that is to use mythwelcome. If mythfrontend is exited then mytwelcome can be used to restart it.

However I'm not sure how to get mythwelcome to autostart on boot rather than mythfrontend?

---

### Post by db260179 on 2008-06-17
Very easy.

goto /home/<yourusername>/.config/autostart/

Remove the mythfrontend script. (just a link to /usr/share/mythtv/mythfrontend.sh)

Create a new script, call it mythwelcome.sh, enter as follows in the new script:

#!/bin/sh
rm ~/.ICEauthority
sleep 1
exec /usr/bin/mythwelcome

then copy the script into the same location as previous script i.e /usr/share/mythtv/

make the script executable i.e chmod +x mythwelcome.sh

then link the file to that location in
/home/<yourusername>/.config/autostart/

A few tips: 1. once mythwelcome is loaded, press F12 to load a xterm terminal
2. Pressing F11 will run the internal setup of mythwelcome.

Hope this helps?

> **Lindsay.Mathieson said:**
> Hi All,

I'd like to disable the ability to exit the mythfrontend and as far as I can tell the best way to do that is to use mythwelcome. If mythfrontend is exited then mytwelcome can be used to restart it.

However I'm not sure how to get mythwelcome to autostart on boot rather than mythfrontend?

---

### Post by Lindsay.Mathieson on 2008-06-17
Thanks db!

slightly different on my setup - .autostart had a mythtv.desktop file symlinked from /usr/share/applications/mythtv.desktop. I just duplicated that for mythwelcome.

Cheers,

Lindsay

---

