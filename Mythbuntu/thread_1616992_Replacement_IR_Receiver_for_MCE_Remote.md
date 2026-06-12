---
title: "Replacement IR Receiver for MCE Remote"
date: 2010-11-08
forum: Mythbuntu
---

### Post by crbnrod on 2010-11-08
So I'm working on mythbox #2 and opted for the Hauppauge HVR-2250.
I got the "new" version that has an IR cord that plugs straight into the card instead of the old-style USB IR receiver. The IR cord isn't currently supported by the driver, but the MCE remote is perfectly usable, and since I have the exact same MCE remote on mythbox #1, I'd like to use the MCE remote on box #2 as well (wife-learning-curve-factor).

I can't seem to find a standalone IR receiver that'll work. This feels like a stupid question, but either I'm using the wrong search term on various online shopping sites, or a replacement receiver doesn't really exist. 

So I figured I'd outsmart everyone, or at least myself, and just buy a cheap MCE-knockoff remote and use its receiver with the remote. So I picked this thing up:
[http://www.amazon.com/gp/product/B00224ZDFY](http://www.amazon.com/gp/product/B00224ZDFY)
Which it turns out the IR receiver only works with the included remote, apparently because (I discovered after buying, of course) a lot of the cheapy MCE remotes work not so much as remotes that LIRC gets along with, but as Human Interface Devices. 
Which if you feel like screwing around with the remote and doing some xmodmap calesthenics, you can get those kinds of remotes to work, but after playing with it for quite some time, it seemed hinky at best and uncooperative at worst, and really, the MCE remote works pretty darn well with myth.

So, long & verbose post short - anyone know where I can get a USB IR receiver that'll work with an MCE remote, or barring that, how can I be sure the MCE remote I shell out another $30 for will actually work as a remote that plays nice with LIRC?

---

### Post by teet on 2010-11-09
I am a big fan of the MCE remotes.  Very easy to set up to work with mythbuntu.  Unfortunately, they're getting harder to find.  I would suggest ebay.  A quick search turned up this result:
[http://cgi.ebay.com/Microsoft-MCE-Media-Center-Remote-Control-Complete-Kit-/320581648301?pt=LH_DefaultDomain_0&hash=item4aa427bfad](http://cgi.ebay.com/Microsoft-MCE-Media-Center-Remote-Control-Complete-Kit-/320581648301?pt=LH_DefaultDomain_0&hash=item4aa427bfad)

Here's just the receiver:
[http://cgi.ebay.com/Microsoft-Remote-Control-USB-IR-RECEIVER-MCE-VISTA-/110549716625?pt=LH_DefaultDomain_0&hash=item19bd46ce91](http://cgi.ebay.com/Microsoft-Remote-Control-USB-IR-RECEIVER-MCE-VISTA-/110549716625?pt=LH_DefaultDomain_0&hash=item19bd46ce91)

-teet

---

### Post by keepitsimpleengr on 2010-11-09
I did the same trick you did and got the same remote.

Mine wouldn't work at all until I put the receiver into a working Windows box, then it worked but as a usb keyboard/mouse.

It's awkward to set up but the twiddle pad mouse is nice.

I found this helful

[http://www.mythtv.org/wiki/Adesso_ARC-1100]("http://www.mythtv.org/wiki/Adesso_ARC-1100")

---

### Post by crbnrod on 2010-11-11
Thanks for the responses. Think I'll go the e-bay route for the receiver.

---

