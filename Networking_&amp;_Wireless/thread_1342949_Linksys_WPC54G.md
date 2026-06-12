---
title: "Linksys WPC54G"
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by Dhaann on 2009-12-01
Hello everybody,
I've installed Ubuntu 9.10 on my laptop and I have a Linksys WPC54G v3.1 network card. I installed the Windows driver with ndiswrapper, but it's still not working. I've searched for hours on the internet and tried many things, but nothing works. Anyoe here that can help?

Thanks!

---

### Post by steveneddy on 2009-12-01
Did you try a Google search?

[http://www.google.com/search?hl=en&source=hp&q=WPC54G+ubuntu&aq=f&oq=&aqi=g3g-m1](http://www.google.com/search?hl=en&source=hp&q=WPC54G+ubuntu&aq=f&oq=&aqi=g3g-m1)

This is the first link in the search:

[http://ubuntuforums.org/showthread.php?t=5645](http://ubuntuforums.org/showthread.php?t=5645)

Seems simple.

Follow the instructions. Post back here is you have any issues referencing the guides you used.

Please do not start a new thread.

Post back here if you find success and give details how you got it fixed. (this will help someone else in the future)

Good Luck

---

### Post by Dhaann on 2009-12-01
This is what I did:

- Installed packages 'ndiswrapper-common' and 'ndiswrapper-utils-1.9'
- Downloaded drivers (I got 3 directories: 2KXP, 98ME and VISTA, I picked the Vista driver but not sure if that is the right one)
- Installed the driver by typing 'ndiswrapper -i lsbcmnds.inf' (when in the Vista dir)
- Run the command 'modprobe ndiswrapper'
- And then 'echo ndiswrapper >> /etc/modules'
- Restarted and no result

Actually, when I click the network icon in the upper-right corner, my network card isn showing anymore (it did before I installed those drivers) but I didn't got any errors :S

EDIT: Now my network card is showing, but only says 'not connected'. How can I search for networks or something?

---

