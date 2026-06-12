---
title: "ndiswrapper for dummies...i'm clueless"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by mfarquhar on 2006-07-12
what is ndiswrapper?

how can i get it?

Can i download it from windows then sneakernet it to ubuntu?

etc...etc...

please don't hurt the n00b:wink:

---

### Post by crei0 on 2006-07-12
NdisWrapper is wrapper for the Windows NDIS, wich means that you can load a windows driver for a wireless card in Linux...

more info @ [http://en.wikipedia.org/wiki/Ndiswrapper]("http://en.wikipedia.org/wiki/Ndiswrapper")

---

### Post by VirtuAlex on 2006-07-12
and you can install it with synaptic
package name is ndiswrapper-utils

---

### Post by mfarquhar on 2006-07-13
okay that answers that.

now my problem is that Internet only works in Windows right now so can i download it from somewhere then move it to Ubuntu?

---

### Post by Gustav on 2006-07-13
Use ndisgtk wich is a graphical front-end for ndiswrapper. It's much easier :)

---

### Post by VirtuAlex on 2006-07-13
> **mfarquhar said:**
> my problem is that Internet only works in Windows right now so can i download it from somewhere then move it to Ubuntu?

You can download the source from [http://ndiswrapper.sourceforge.net/]("http://ndiswrapper.sourceforge.net/"), and try to compile. If wire is not an option, then I suggest to get full ubuntu on DVD or set of CDs and uncheck all sources except cdrom in synaptic for now. Do not forget to check them back after you'll have internet so you'll be able to download updates.

---

### Post by mfarquhar on 2006-07-13
i have the regular dapper shipit CD. will that work (i have'nt upgraded yet so i'm still running breezy) if i upgrade will it do stuff automatically?

---

### Post by VirtuAlex on 2006-07-13
Then try it! You may be lucky and dapper will recognize your wirless card out of the box (didn't work for me though) so you wouldn't even need any ndiswrapper.

---

### Post by mfarquhar on 2006-07-17
whats the deal witht the Alternate install CD, would that have Ndiswrapper on it (it said for installs on systems without previous networking setup stuff) i might be able to get it if it would work

---

