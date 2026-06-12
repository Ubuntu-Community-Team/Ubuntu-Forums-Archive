---
title: "Mythbuntu as uPnP client?"
date: 2008-08-16
forum: Mythbuntu
---

### Post by leeko on 2008-08-16
Hi,

Is it possible to run mythbuntu as a uPnP client? 

I have a Linksys NSLU2 on my network, serving music and videos via Twonkymedia uPnP server. My PDA (Dell Axim x51v, Pocket Player) sees the uPnP server and connects to it no problem. However, I can't see how this should be set up in the mythTV interface. Doing a google search for "mythbuntu upnp client" just turns up results relating to mythTV's uPnP server capability..

If anyone can point me in the right direction, I'd be really grateful!

Thanks,

Lee

---

### Post by newlinux on 2008-08-16
AFAIK, that functionality doesn't exist in myth unless someone wrote some kind of 3rd party plugin. You could just use mythvideo and mythmusic and mount a share that has your media.

---

### Post by leeko on 2008-08-16
ok, thanks for the info :). Now, I just have to figure out why I can't see my samba shares.... :P

Lee

---

### Post by zdude on 2008-08-16
I plugged my Directv HR-21 receiver into my network and when looking at "My Computer" in the Directv menu it popped up my Myth computer and showed ALL the music files and videos, recorded and otherwise, on the Directv screen! They obviously didn't play (you need media share, twonky or other share server) but I am not sure if Directv is able to *see* what all I have on my system. :confused:
How can you turn this feature off in Myth?

---

### Post by newlinux on 2008-08-16
> **zdude said:**
> I plugged my Directv HR-21 receiver into my network and when looking at "My Computer" in the Directv menu it popped up my Myth computer and showed ALL the music files and videos, recorded and otherwise, on the Directv screen! They obviously didn't play (you need media share, twonky or other share server) but I am not sure if Directv is able to *see* what all I have on my system. :confused:
How can you turn this feature off in Myth?
Yep, the mythtv upnp server isn't compatible with the HR-21s (and a lot of upnp servers aren't compatbile with them).

Use the --noupnp option with running the backend to turn off the upnp server.

---

