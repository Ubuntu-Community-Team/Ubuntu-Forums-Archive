---
title: "ubuntu server and virgin media(cable)"
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by Vale- on 2009-12-03
Hey all,

I am about(after 2 weeks wait *sigh*) to receive my virgin media cable broadband connection. I will be given a wireless cable router(Netgear I believe) by virgin to set up my network which is fine but I have greater plans.

I want to set up my current ubuntu server as gateway to the net. It currently operates as a file server for my network using samba and nfs to dish out files to the various flavours of platforms I use.

What I want to do is connect my cable connection directly to the server from the cable modem(not the Netgear router, the little blue thingy) to my server.
i.e.

INTERWEBS <---> Cable Modem <---> Server <---> LAN

The server will need a firewall to keep me safe and be able to route data to and from my local network. It will also be configured to use DHCP and DNS.

I know of a few products that might be able to do this like IPCOP but I have not tried this before in ubuntu. So does anyone have any advice of what products are best? Or is this bad practice? Should have a cable router between the cable modem and server? i.e.

INTERWEBS <---> Cable Modem <---> Netgear Router <---> Server <---> LAN

Any help would be great.

Cheers,

Vale :D

---

### Post by Stunts on 2009-12-03
I have a very similar setup at home.
I used eBox to setup everything. It makes configurations pretty easy. It is rather well documented, and I do recommend it.
I am now more competent with a linux server then I was one year ago when  I first set it up, and I feel that despite doing most of the work for me eBox helped me learn a lot about my server config.
I still learn a lot with it. When I become even more competent I will probably let go of eBox and do it all manually, just for the kicks, but so far it's been working very well for me.

---

### Post by Vale- on 2009-12-04
Thanks a lot for the suggestion ebox looks interesting I will take a look into it.

I have looked into IPCOP a bit more, seems like its a stand alone distro but doesn't look like its capable of doing email or file sharing? Is it possible to add these capabilities after configuring it or is ebox the better solution?

Cheers,

Vale

---

### Post by Vale- on 2009-12-04
I have looked into ebox and it looks pretty much bang on what I need so I think I am going to go for ebox.

Thanks stunts for the help. :)

Vale

---

### Post by Stunts on 2009-12-04
You're welcome!

I'm always glad to help!

Enjoy your "new" home server. =-)

---

