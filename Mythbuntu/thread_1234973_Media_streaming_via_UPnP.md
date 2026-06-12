---
title: "Media streaming via UPnP"
date: 2009-08-08
forum: Mythbuntu
---

### Post by NautiusMaximus on 2009-08-08
I've just bought a Zyxel DMA-1000, which in theory should be able to stream videos etc from my Mythbuntu box. According to the page at [http://www.mythtv.org/wiki/ZyxelDMA1000](http://www.mythtv.org/wiki/ZyxelDMA1000), it should "detect MythTV without any configuration".

Sadly, it doesn't. Not a sausage.

I have yet to RTFM for the Zyxel device, and that may well contain some clues. However, in the meantime, is there anything obvious I need to do in Mythbuntu? For example, is UPnP deactivated by default and I need to activate it somewhere?

Thanks
NM

---

### Post by geekyhawkes on 2009-08-08
UPNP is definatly not switched off by default, sorry.  I sadly cannot help you anymore other than to say I am looking at running mediatomb on my myth backend as it sorts the music much more logically than myth does for UPNP.

---

### Post by NautiusMaximus on 2009-08-09
It's OK, I've cracked it.

On the MythTV wiki page for UPnP ([http://www.mythtv.org/wiki/UPnP](http://www.mythtv.org/wiki/UPnP)), there was an instruction "Make sure you set the proper external IP in mythtv-setup, otherwise you will be able to see your server via UPnP, but the file location urls will contain the default 127.0.0.1 IP address."

It seems there are a couple of places that are set to 127.0.0.1 by default. I think to start with I set the local backend server IP address to the proper machine address, but there's another place to set the master backend server IP address, which I missed the first time. Once I'd set that, it just worked.

However, now there's another slightly annoying problem. When I view recordings via the Zyxel device, it shows me everything I've previously recorded, even shows that I've since deleted, which makes the screen more cluttered than I'd like.

Is there any way of getting deleted shows properly deleted?

Thanks
NM

---

