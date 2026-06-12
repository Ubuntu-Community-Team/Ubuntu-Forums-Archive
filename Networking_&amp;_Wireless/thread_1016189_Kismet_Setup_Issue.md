---
title: "Kismet Setup Issue"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by xNIAx1 on 2008-12-19
I am following a guide on how to install/run kismet on ubuntu.

[http://tonylog.altervista.org/2007/10/04/how-to-install-and-configure-kismet-on-ubuntu-feisty-fawn/](http://tonylog.altervista.org/2007/10/04/how-to-install-and-configure-kismet-on-ubuntu-feisty-fawn/)

I am pretty sure I did everything right. I am only running into one problem. When the guide tells me to type in: 

sudo iwconfig eth0 mode monitor

I get this error: Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth0 ; Operation not supported.

Anyone know what I did wrong? Or does Kismet not support my card? BCM4310

Thanks in advance!

---

### Post by albinootje on 2008-12-19
> **xNIAx1 said:**
> I am following a guide on how to install/run kismet on ubuntu.

[http://tonylog.altervista.org/2007/10/04/how-to-install-and-configure-kismet-on-ubuntu-feisty-fawn/](http://tonylog.altervista.org/2007/10/04/how-to-install-and-configure-kismet-on-ubuntu-feisty-fawn/)

I am pretty sure I did everything right. I am only running into one problem. When the guide tells me to type in: 

sudo iwconfig eth0 mode monitor

I get this error: Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth0 ; Operation not supported.


Are you using Ndiswrapper ?
Long time ago i heard that Ndiswrapper doesn't support monitor mode.
See here, it seems to be the case :
[http://ubuntuforums.org/showthread.php?t=114204](http://ubuntuforums.org/showthread.php?t=114204)

(Ndiswrapper was/is imho meant to fill in the gap of lacking wifi-card drivers for Linux, which is probably to blame to the hardware-vendors going for the big $$ and not willing to cooperate to help to produce wifi card drivers for Linux, and apart from that, Linux-programmers need cards like that in their bare hands to be able to write drivers for it.)

Apart from all this, configuring kismet is not so very easy.
Are you sure you edited the line with 
```

source=ipw3945,eth0,Wireless Card

```
correctly ?
I remember it was not so very easy to find out what had to be filled in there for my orinoco or atheros card.

---

### Post by xNIAx1 on 2008-12-19
Thanks for the replay.

no I don't use Ndiswrapper. I have only downloaded kismet and followed the guide from the site. I haven't done anything else..

This what I edited in the config.

# Sources are defined as:
# Source=ipw3945,eth0,Wireless Card
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=none,none,addme


Any other ideas?

Thanks again,
Nick

---

### Post by albinootje on 2008-12-19
> **xNIAx1 said:**
> Thanks for the replay.

no I don't use Ndiswrapper. I have only downloaded kismet and followed the guide from the site. I haven't done anything else..



Okay, good that you don't need Ndiswrapper :)

> 
This what I edited in the config.

# Sources are defined as:
# 
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=none,none,addme


But this is a problem.
You need to look up in the kismet documentation, and perhaps even with help from a search-engine, what needs to be edited there.

The line : ```
Source=ipw3945,eth0,Wireless Card
```
from the webpage you mentioned earlier on, is a good example for a specific card.

That line should be more or less similar for your card, otherwise it cannot work. 
Especially the first part (in the example it's : ipw3945) is important to look up.

Read the kismet documentation, in /usr/share/doc/kismet or on the kismet website.

---

