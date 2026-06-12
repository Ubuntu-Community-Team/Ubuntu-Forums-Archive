---
title: "Understanding IW command / options"
date: 2012-03-30
forum: Networking &amp; Wireless
---

### Post by hpng on 2012-03-30
I went to this page....

[COLOR=Blue]http://manpages.ubuntu.com/manpages/natty/en/man8/iw.8.html[/COLOR]

and saw this:
**[COLOR=Blue][B]IW** **-** **COMMAND** **SYNTAX**[/COLOR][/B]

[COLOR=Blue]   _OBJECT_        **dev** **<interface** **name>**               - network interface.         **phy** **<phy** **name>**               - wireless hardware device (by name).         **phy#<phy** **index>**               - wireless hardware device (by index).         **reg**    - regulatory agent.[/COLOR]

I am not sure how to use it.
For example:  iw phy <phy name>[COLOR=Red]
Where can I get correct Linux name for phy?[/COLOR]
The Ubuntu man pages is quite vague and lack many description.
[COLOR=Red]Is there a better reference?[/COLOR]
[B]
the I went here:[/B]
**[COLOR=Blue]http://wireless.kernel.org/en/users/Documentation/iw#Adding_interfaces_with_iw[/COLOR]**
and saw this:
[COLOR=Blue]For example to add a monitor interface: [/COLOR]
[COLOR=Blue]iw phy phy0 interface add moni0 type monitor[/COLOR][COLOR=Blue]where you can replace monitor by anything else and moni0 by the interface name, and need to replace phy0  by the PHY name for your hardware (usually phy0 will be correct unless  you hotplugged or reloaded any modules.) If your udev is configured  incorrectly, the newly created virtual interface may be renamed by it  right away, use ip link to list all interfaces. [/COLOR]

It still does not explain where they got phy name ( phy0 ).
In fact the entire description on iw needs better examples and explanation....
[COLOR=Red]So I think I am missing a link here to complete my understanding[/COLOR].
**Is there a reference discussing how names are assigned to hardware devices?**
i wonder a Linux driver development type book may shed some light....., if there is such a book or reference....

Comments please.
 
Thanks.

---

### Post by Ms. Daisy on 2012-03-31
To discover the names of hardware devices on your computer, type in a terminal
```
lshw
```
You're not looking for a generic name of a hardware device, you're looking for the specific name of your specific hardware.  That won't be in any textbook.

---

### Post by cw9000 on 2013-04-11
I used the command ```
iw phy phy0 
```for my wlan0 and it worked.  you can get information about a particular device using
```
iw dev wlan0 info
```  you will see

```
iwphy #
```    where # is an actual integer.   And your entirely right, there isn't much documentation on it ( or any )

---

### Post by Iowan on 2013-04-11
Old thread.

---

