---
title: "autoloading network interfaces breaks ifupdown"
date: 2006-05-04
forum: Networking &amp; Wireless
---

### Post by hearnden on 2006-05-04
Hi all,

I have two network interfaces on my laptop, one wired one wireless.  I often switch between them to alternate speed and convenience.  I would much prefer to switch interfaces using a command-line than navigating through slow menus (network-admin), so I would like to be able to use ifdown and ifup to switch from one interface to the other.  I would also like my wireless interface to be automagically loaded on bootup, since that is what I usually use.

However if my wireless interface (wlan0) is automatically loaded (either by ifupdown with the 'auto' stanzas or by the hotplug subsystem in the 'mapping hotplug' stanza), then when I switch to my wired interface (sudo ifdown wlan0; sudo ifup eth0), nothing works.  Pings within my home network and beyond always give "sendmsg: operation not permitted" errors.

Thinks work fine if I do not auto-load the wireless interface on boot.  If I bring it up manually I can then switch between interfaces using ifupdown without a problem.  To make things more confusing, things also work fine when I auto-load the wired interface.

 Autoload wlan0 |  Autoload wlan0  |   Can switch      |
   (ifupdown)     |      (hotplug)      |  using ifupdown  |
----------------+-----------------+-----------------|
        Y             |         N             |          N            |
        N             |         Y             |          N            |
        Y             |         Y             |          N            |
        N             |         N             |          Y            |

Any hints would be greatly appreciated!

-David

Does anyone know *exactly* what happens when interfaces are autoloaded through ifupdown or through hotplug-network?

---

