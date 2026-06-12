---
title: "Network Manager Gnome clobbered?"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by anechoic on 2009-07-29
I ran across a major noob gotacha yesterday
I attempted to try the rt kernel 2.6.29 on my Dell Studio 15 and found that Wireless didn't work. 

So I thought I'd try out a different network manager, 'wicd'. I didn't realize that by installing this it would overwrite the Network Manager Gnome and Network Manager already installed. 
I tested wicd, found it wasn't able to connect then (here's the big mistake) un-installed it. 

So this left me without wireless on the Dell Studio 15 and of course no way to connect to a repository to reinstall NMG and NM. I also wasn't able to install or find either package on the 9.04 CDROM/DVD - even though I added the CDROM to the repository list and unchecked all the online repos. But this was a different rathole and chose not to go down.

After searching online (using my backup Ubuntu netbook) I found another person who had done this very same thing and followed the links he posted to the needed NMG and NM packages here:
[http://packages.ubuntu.com/jaunty/net/](http://packages.ubuntu.com/jaunty/net/)

I downloaded the Network Manager Gnome and Network Manager packages to a USB stick, sneaker-netted them to the Dell Studio 15, dragged them to the desktop and used the Gdebi Package Installer to install both.

I rebooted and everything is now back to normal.

But I think this is a serious enough gotcha that the developers should consider fixing in some way...maybe a script that prevents or at least warns you that un-installing your network manager will result in a loss of connectivity?

anyway, just wanted to share my experience with others.
Hope it helps someone!
:)

---

