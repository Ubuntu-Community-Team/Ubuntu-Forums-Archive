---
title: "No internet but SSH works"
date: 2011-02-15
forum: Networking &amp; Wireless
---

### Post by jerhurwitz on 2011-02-15
I had wired networking working on my computer and also set up SSH and could VNC through my SSH tunnel to my Ubuntu 10.10 computer.

Then I installed a new wireless adapter using these instructions:
[http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html](http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html)

The wireless adapter works but it disconnects my SSH and VNC connections when it is on. So I unplugged it and just used wired for now.

Now I can SSH both locally and remotely with no problems but the internet on the Ubuntu computer will not work. Originally I could also use VNC but now that is not working either (I assume unrelated).

Seems like a DNS issue to me but I'm not certain how to fix this on an Ubuntu computer.

EDIT:
GAh! It makes no sense. I had restarted the computer and restarted networking and done all sorts of things and nothing had worked. I edited /etc/network/interfaces back to DHCP and the internet worked again. Then I recopied the interfaces file with the static IP that I had just deleted back and everything works. Makes no sense to me.

---

