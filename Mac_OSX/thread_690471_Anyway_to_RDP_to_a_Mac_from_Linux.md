---
title: "Anyway to RDP to a Mac from Linux?"
date: 2008-02-07
forum: Mac OSX
---

### Post by cprofitt on 2008-02-07
I have the Terminal Server Client for remote control of the Windows boxes I have... is there any client on the PC side that allows you to connect to a Mac other than VNC?

I know the Macs have RDP enabled... but the TS Client doesn't connect to them.

Thanks

---

### Post by vgrisham on 2008-02-19
> **PrivateVoid said:**
> I have the Terminal Server Client for remote control of the Windows boxes I have... is there any client on the PC side that allows you to connect to a Mac other than VNC?

I know the Macs have RDP enabled... but the TS Client doesn't connect to them.

Thanks

Bump. I'd like to know this too.

---

### Post by thatswhatshesaid on 2008-02-28
Why is VNC not an option?  Just curious...

---

### Post by DouglasAWh on 2008-03-03
Apple has RDP?  I thought they did ARP?  Can someone give a citation for that?

---

### Post by cprofitt on 2008-03-04
[citation?]("http://www.apple.com/remotedesktop/")

or

[citation?]("http://www.apple.com/support/remotedesktop/")

and according to [this]("http://images.apple.com/remotedesktop/pdf/ARD31_TO.pdf") documentation the client portion is pre-installed.

Apple, of course, does not discuss using anything other than their ARD Administration product for accessing the RD client... so that is why I was asking.

Is the built-in client using VNC? RDP? RDPv5? Some other protocol?

---

### Post by DouglasAWh on 2008-03-04
> **PrivateVoid said:**
> 
Is the built-in client using VNC? RDP? RDPv5? Some other protocol?

ARD* was the protocol*, but now it runs on VNC.

"On June 21, 2004 Apple announced Apple Remote Desktop 2 (released in July), which was designed to use the VNC protocol instead of Apple's original ARD protocol." - [http://en.wikipedia.org/wiki/Apple_remote_desktop](http://en.wikipedia.org/wiki/Apple_remote_desktop)

As far as I can tell, your "citations" say nothing about using RDP.  Maybe I'm missing something?

Perhaps this is the problem I am having "On October 18, 2007 Apple released version 3.2 which introduced Mac OS X Leopard support and compatibility for third party VNC viewers and servers."

Perhaps the built in version will not do other VNC viewers.

---

### Post by cprofitt on 2008-03-05
> **DouglasAWh said:**
> As far as I can tell, your "citations" say nothing about using RDP.  Maybe I'm missing something?

They don't say which protocol, but they use the words 'remote desktop' an awful lot. If I recall the preferences on the Mac use the terminology remote desktop as well... perhaps they are just obfuscating the fact that they are using VNC? I will give VNC a shot tomorrow after I build the Altiris server.

---

### Post by wheredidrealitygo on 2008-03-31
Sorry to bring up an old thread, but VNC definitely is the protocol Macs use. 

Has anyone been able to find a way to connect without using 'full' or 'millions of colours' when connecting to a Mac?

If I use xvnc4viewer (on my Eee or Ubuntu) to connect to my Mac, it (the Mac) will only accept connections that have full color, which is VERY slow over the internet, and only barely acceptable on the local network, especially on the Eee.

---

### Post by DouglasAWh on 2008-04-21
This is slightly off topic, so if people want me to start a new thread I'd be happy to, but my OS X remote administration woes have sprung up again:

[http://www.realvnc.com/pipermail/vnc-list/2006-August/055838.html](http://www.realvnc.com/pipermail/vnc-list/2006-August/055838.html)

> 
Vihan,

There is not, nor has there ever been, an RFB version 3.889.  Valid protocol
version numbers are 3.3, 3.7, 3.8 and 4.0.

This appears to be a bug in Apple Remote Desktop.  You should be able to
contact Apple for support for their product.

Regards,

Wez @ RealVNC Ltd.


However, the screenshot at [http://flickr.com/photos/dawhitfield/2432373526/sizes/o/](http://flickr.com/photos/dawhitfield/2432373526/sizes/o/) 

would suggest otherwise.  Does anybody know a work around?

THANKS!

---

