---
title: "How I finally got orinoco to work in monitor mode"
date: 2006-01-12
forum: Networking &amp; Wireless
---

### Post by wr0x2 on 2006-01-12
Tested on breezy with kernel 2.6.12

If you've got an orinoco card that you want to run in monitor mode, keep reading. All the FAQs and howtos on these forums did me no good, until I saw 1 comment nested into a giant orinoco_cs thread. Basically, you'll need to install your kernel headers and all that along with build-essential. Search for how to do this with apt, because I forget the exact package names.

Here's the real info. After you've done all of that, grab one of the files from here:[http://www.projectiwear.org/%7Eplasmahh/orinoco.html](http://www.projectiwear.org/%7Eplasmahh/orinoco.html)

These are the orinoco 0.13e drivers, but they've been patched to support both scan and monitor modes, which is what you're looking for if you want to run kismet or airsnort. The code is kernel specific, so if the latest doesn't work, try a less recent one. My kernel is 2.6.12, and I had to use the second from the bottom to get it to compile. Since the files are prepatched, you'll just need to 
make

and then 

sudo make install 

and you should be good. There's no need to apply the diffs included unless you want your drivers to be without monitor support. If everything goes smoothly but iwpriv does not list mode monitor, then try going into 

/lib/modules/*your kernel version*/kernel/drivers/net/wireless/ 

and 
rm orinoco* 
rm hermes*

After this, repeat the steps specified above to compile and install the 0.13e drivers. Removing / inserting your card should unload and load the proper modules, so there shouldn't be any need to reboot unless you feel like it.

This isn't really supposed to be a how-to, it's merely to tell people that YES, there is a way to get your orinoco card working in monitor mode.

---

### Post by bekamyn on 2006-01-13
[QUOTE=wr0x2]Tested on breezy with kernel 2.6.12

If you've got an orinoco card that you want to run in monitor mode, keep reading. All the FAQs and howtos on these forums did me no good, until I saw 1 comment nested into a giant orinoco_cs thread. Basically, you'll need to install your kernel headers and all that along with build-essential. Search for how to do this with apt, because I forget the exact package names.

Here's the real info. After you've done all of that, grab one of the files from here:[http://www.projectiwear.org/%7Eplasmahh/orinoco.html](http://www.projectiwear.org/%7Eplasmahh/orinoco.html)

These are the orinoco 0.13e drivers, but they've been patched to support both scan and monitor modes, which is what you're looking for if you want to run kismet or airsnort. The code is kernel specific, so if the latest doesn't work, try a less recent one. My kernel is 2.6.12, and I had to use the second from the bottom to get it to compile. Since the files are prepatched, you'll just need to 
make

and then 

sudo make install 

and you should be good. There's no need to apply the diffs included unless you want your drivers to be without monitor support. If everything goes smoothly but iwpriv does not list mode monitor, then try going into 

/lib/modules/*your kernel version*/kernel/drivers/net/wireless/ 

and 
rm orinoco* 
rm hermes*

After this, repeat the steps specified above to compile and install the 0.13e drivers. Removing / inserting your card should unload and load the proper modules, so there shouldn't be any need to reboot unless you feel like it.

This isn't really supposed to be a how-to, it's merely to tell people that YES, there is a way to get your orinoco card working in monitor mode.[/QUOTE]


Does this Wiki entry need updating, then? [https://wiki.ubuntu.com/OrinocoMonitorKismet2005Hoary?highlight=%28kismet%29](https://wiki.ubuntu.com/OrinocoMonitorKismet2005Hoary?highlight=%28kismet%29)

---

