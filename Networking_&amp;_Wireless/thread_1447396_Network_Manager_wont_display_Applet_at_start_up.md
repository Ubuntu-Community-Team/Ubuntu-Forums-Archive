---
title: "Network Manager wont display Applet at start up"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by Dyffo on 2010-04-05
I am running Ubuntu Karmic - At start up I cannot get the Network Manager applet to display. If I open terminal and enter :
  " nm-applet --sm-disable" 
my applet shows up. If I close the terminal it goes away.Network manager is running.I just need this displayed on the launch panel. Any ideas please.

---

### Post by Cabalbl4 on 2010-04-05
There is an issue with buggy nm-applet freezing at startup. As a temporary solution You may try to ```
killall gnome-panel
``` it usually restarts with no problem.

In general, adding some sleep time before nm-applet starts helps with this issue, howewer, not always.

And yeah, You just may have found another bug in it :)

PS. It can also be a problem of a password keyring. NM cannot connect without gaining access to passwords stored there, giving applet some time of confusion :)  Maybe making default keyring password blank using seahorse may also help.

---

### Post by Dyffo on 2010-04-06
> **Cabalbl4 said:**
> There is an issue with buggy nm-applet freezing at startup. As a temporary solution You may try to ```
killall gnome-panel
``` it usually restarts with no problem.

In general, adding some sleep time before nm-applet starts helps with this issue, howewer, not always.

And yeah, You just may have found another bug in it :)

PS. It can also be a problem of a password keyring. NM cannot connect without gaining access to passwords stored there, giving applet some time of confusion :)  Maybe making default keyring password blank using seahorse may also help.

Problem solved - changed my opening screen at boot up from Failsafe Gnome to Gnome.Hey Presto all works fine.

---

