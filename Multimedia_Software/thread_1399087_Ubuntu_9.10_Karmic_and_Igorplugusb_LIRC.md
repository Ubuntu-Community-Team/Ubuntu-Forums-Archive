---
title: "Ubuntu 9.10 Karmic and Igorplugusb LIRC"
date: 2010-02-05
forum: Multimedia Software
---

### Post by m.bluemle on 2010-02-05
Hello,

has anyone running the *Igor USB Receiver* under *Ubuntu 9.10*?
I´ve made an *minimal Ubuntu 9.10* installation and after install and configuring *LIRC* with the *Igor Cesko´s USB Receiver* the system holds by loading the modules.

By trying a reconfiguration, the system says, that *LIRC* is defect.

If I try the load the needed modules by hand, there is no problem to load **lirc_dev**, but I get the same system hold by loading **lirc_igorplugusb**.

Are there any known problems with **lirc_igorplugusb** and *Ubuntu 9.10*? 


              
                                                                                                                                           [[IMG]http://www.unixboard.de/vb3/images/bluesaint/buttons/quote.gif[/IMG]]("http://www.unixboard.de/vb3/newreply.php?do=newreply&p=345877")

---

### Post by m.bluemle on 2010-02-12
Can nobody help me? *Lirc* ist starting without a fail message and I can record my commands with *irrecord*! But the issue by using* irw* is not the name of the buttons, it´s like a RAW issue. I thin this is because the **lirc_igorplug** is not loaded!

---

