---
title: "YAPQ (Yet Another Prism2_cs Question)"
date: 2005-03-20
forum: Networking &amp; Wireless
---

### Post by diver on 2005-03-20
first dive into ubuntu and must say, "very nice".  but, for an old FreeBSD
droid, i have have some issues.

running horay 2.6.10.4 on dell 5ke. want to get my senao ext+ pcmcia
wifi card going. installed linux-wlan-ng via synaptic and no joy, prism2_cs
not found.

not a problem, thought I would just synaptic the kernel sources and headers,
then build wlan-ng. however, wlan-ng wants full sources/headers and so-on.
have not been able to locate them on the machine, at least in a form that will
satisfy wlan-ng's 'make config'.

it seems that with the depth of package availability for ubuntu, prism2_cs
should be a slam dunk.

i've read simular questions here on the forums but, none seem to have been
answered, at least as a reply to the forum.

i really don't want to rebuild the kernel since i'm sure to break a bunch of
stuff and want to keep this a pleasant experience.

what am i missing here?

tia,

--
joe

---

### Post by mmuller on 2005-03-20
The only light i might be able to shed is from my experience in downloading the linux-source from synaptic. It seems that to keep the size down you get a tar.gz file in /usr/src which i guess needs to be de-compressed after downloading as synaptic just left me with that.

Hope that helps a little.

mmuller

---

### Post by diver on 2005-03-20
thanks mmuller,

but, done all that.  i think wlan-ng 'make config' is complaining that
there is no .config at the root of the kernel source tree.

unable to get the configuration from the kernel i'm running ( in /proc)
so, not going to chase this down, would be a real bag of snakes.

may wind up back on Slackware, more BSDish.

ciao,

--
joe

---

### Post by az on 2005-03-21
It should work with the orinoco drivers.  I have been having problems with the orinoco drivers in hoary.  Lok at this:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=6566](https://bugzilla.ubuntu.com/show_bug.cgi?id=6566)

Try Warty.  Just boot the installer and see if it can detect your network card.  You do not have to go through with the install.

If this is the problem, please add relevant information to the bugzilla thread.

---

### Post by diver on 2005-03-29
Actually the card is recognized however, there are issues with using
monitor mode. Other discussions have disclosed timing issues when
using the orinoco drivers w/ prism2.x chipsets in monitor mode.

In my case using ubuntu w/ orinoco support for prism2.5 specifically:
kismet just doesn't work using the prism2.5 card as a source.

I guess I just don't understand why the wlan_ng prism2_cs driver
is exclude from the package library when prism2_pci and prism2_usb
are supported especially knowing that orinoco drivers have timing
problems w/ prism2.x chipsets.

I suppose I could volunteer to build a wlang_ng prism2_cs package
but, as stated earlier, the ubuntu environment is quit alien to me
and the ROI just isn't there in light of the numerous options. :eek:

'Time to move along' "Time to move along"

taw,

--
joe

---

### Post by poofyhairguy on 2005-04-08
[QUOTE=diver]Actually the card is recognized however, there are issues with using
monitor mode. Other discussions have disclosed timing issues when
using the orinoco drivers w/ prism2.x chipsets in monitor mode.

In my case using ubuntu w/ orinoco support for prism2.5 specifically:
kismet just doesn't work using the prism2.5 card as a source.

I guess I just don't understand why the wlan_ng prism2_cs driver
is exclude from the package library when prism2_pci and prism2_usb
are supported especially knowing that orinoco drivers have timing
problems w/ prism2.x chipsets.

I suppose I could volunteer to build a wlang_ng prism2_cs package
but, as stated earlier, the ubuntu environment is quit alien to me
and the ROI just isn't there in light of the numerous options. :eek:

'Time to move along' "Time to move along"

taw,

--
joe[/QUOTE]


I just got it to work. This did it:

[http://www.ubuntulinux.org/wiki/OrinocoMonitorKimset2005Hoary/view?searchterm=kismet](http://www.ubuntulinux.org/wiki/OrinocoMonitorKimset2005Hoary/view?searchterm=kismet)

---

