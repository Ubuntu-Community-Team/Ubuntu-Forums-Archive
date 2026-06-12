---
title: "How to edit network connections using command line"
date: 2010-06-04
forum: Networking &amp; Wireless
---

### Post by caspersky345 on 2010-06-04
1. I'd like to know how to use command line to select or configure the wired network. Currently this can be done manually by right clicking the computer icon on the panel, then select Edit Connections...

2. Can you please also let me know if we can Enable/Disable wireless by command line. With right clicking on the computer icon on the panel, Enable/Disable Wireless can be selected manually

I am using Ubuntu 9.04. Thanks:P!

---

### Post by viralmeme on 2010-06-04
[http://nixcraft.com/shell-scripting/12767-shell-script-create-network-configuration.html](http://nixcraft.com/shell-scripting/12767-shell-script-create-network-configuration.html)

---

### Post by Iowan on 2010-06-04
As I recall, 9.04 still let */etc/network/interfaces* override Network Manager. Once again, I'm in the wrong place to check my 9.04 machine to see which file NM uses for configuration, but you *might* be able to run nm-applet from CLI.
 Something about mix/match GUI/CLI seems like potential problem.  If you intend to use CLI only, the aforementioned file makes more sense. Check **man ifconfig** for some more information...

---

