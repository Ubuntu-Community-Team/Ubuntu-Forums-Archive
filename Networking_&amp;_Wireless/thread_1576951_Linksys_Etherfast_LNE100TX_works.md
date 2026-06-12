---
title: "Linksys Etherfast LNE100TX works"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by leewiest on 2010-09-18
I searched the threads of this combo for hours, most saying they can't get it to work, just giving up and going to another card.

However, I found this: [http://manpages.ubuntu.com/manpages/maverick/man4/if_dc.4freebsd.html#toptoc3](http://manpages.ubuntu.com/manpages/maverick/man4/if_dc.4freebsd.html#toptoc3)

**[B]NAME**[/B]

     **dc** - DEC/Intel 21143 and clone 10/100 Ethernet driver  **[B]SYNOPSIS**[/B]

     To compile this driver into the kernel, place the following lines in your      kernel configuration file:             **device** **miibus**            **device** **dc**       Alternatively, to load the driver as a module at boot time, place the      following line in [loader.conf]("http://manpages.ubuntu.com/manpages/maverick/man5/loader.conf.5.html")(5):             if_dc_load="YES"

I opted for the alternate. There is no loader file, so I just: 
sudo gedit /boot/loader.conf and created the file.

Rebooted, and walla - LTSP works (that was what I was trying to do -- my ltsp network (eth1) worked and I could make connections and log on.

Everything else seems to be workinig as well.

---

