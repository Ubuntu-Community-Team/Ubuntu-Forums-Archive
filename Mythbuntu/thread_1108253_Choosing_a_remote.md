---
title: "Choosing a remote"
date: 2009-03-27
forum: Mythbuntu
---

### Post by itlarson on 2009-03-27
What remote control should I get? Mostly I just want something easy to set up.  The only other real requirement is that it be a learning universal remote.  RF would be worth paying a bit extra for, if it sets up easily.  Can someone tell me what is involved in setting up a remote?

---

### Post by klc5555 on 2009-03-27
> **itlarson said:**
> What remote control should I get? Mostly I just want something easy to set up.  The only other real requirement is that it be a learning universal remote.  RF would be worth paying a bit extra for, if it sets up easily.  Can someone tell me what is involved in setting up a remote?

My preferences certainly aren't typical, but for the frontend the family uses, after fiddling around for a week or two with a defective LIRC driver, I decided that dealing with LIRC etc. just wasn't worth the nuisance. So I picked up a Snapstream Firefly mini (IR), whose receiver operates through the USB port and the configuration was no more complicated than composing a text file for xmodmap to load when X stats up. There's a how-to for it on the mythtv wiki. 
[http://www.mythtv.org/wiki/Snapstream_firefly_mini](http://www.mythtv.org/wiki/Snapstream_firefly_mini)

To supplement this, I bought a few cheap Philips universal programmable remotes (at $15 or so a pop) and programmed them with the Mythtv keys I use from the Firefly mini's remote (which remote I then tucked away in a desk drawer for future reference), and finally added my other devices to the cheapo Philips remotes in the usual fashion with device codes.

Works fine, but I realize most people prefer to get LIRC working. I just didn't really need to.

Cheers! :)

---

### Post by Slate8 on 2009-03-27
I have always used the windows media center version 2 remote. It works out the box with mythbuntu and the buttons are sensibly laid out. I got a few for about 20 GBP each from eBay. On most models you can program the tv power and volume buttons from your original tv controller.

More info at [http://www.mythtv.org/wiki/MCE_Remote]("http://www.mythtv.org/wiki/MCE_Remote")

I've not tried an RF remote but would be interested to hear about the options too.

[IMG]http://www.oneweb.co.uk/mythtv/wp-content/uploads/2009/02/mce-remote.jpg[/IMG]

---

### Post by itlarson on 2009-03-27
Actually the full sized Snapstream Firefly with RF looks interesting.  Can anyone point me towards something like a step by step procedure for getting it (or other RF remotes) to work?  My previous efforts to get a lirc device to work were futile.

---

