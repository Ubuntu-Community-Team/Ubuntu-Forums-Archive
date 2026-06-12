---
title: "Suggested cheap video card Asus MV2-MX"
date: 2009-06-01
forum: Multimedia Software
---

### Post by OscarFoxtrot on 2009-06-01
Hi

Suggestions please for a cheap video card for use with ASUS MV2-MX mobo, which I'm told doesn't play nicely with Linux, and which following a failed upgrade 8.04-8.10 refuses to run X from install (but will run it from live). Compiz might be nice, but I'm looking for stability rather than performance.

Might the following from Messrs Misco's bargain bucket end of the range be suitable?

Sapphire Radeon HD4350 256MB
PNY GeForce 8400GS 256Mb PCI
PNY GeForce 7300GS 256Mb PCI

Thanks awfy.

---

### Post by OscarFoxtrot on 2009-06-02
?Please

---

### Post by coffeecat on 2009-06-02
> **OscarFoxtrot said:**
> Might the following from Messrs Misco's bargain bucket end of the range be suitable?

Sapphire Radeon HD4350 256MB
PNY GeForce 8400GS 256Mb PCI
PNY GeForce 7300GS 256Mb PCI

Are you sure you mean PCI card? Doesn't your motherboard have a PCIe slot? Generally, PCI graphics cards (when you can get them) are more expensive than PCIe. Probably because they're older technology and you don't get volume pricing. Whatever, you're far better off with PCIe.

I'm using a GeForce 8400GS PCIe card and compiz is fine. It would be with a 7300GS as well. What were the Misco prices? Can you provide a link? I paid about £25 for my (much better make than PNY) 8400GS from Scan.

---

### Post by OscarFoxtrot on 2009-06-03
> **coffeecat said:**
> Are you sure you mean PCI card? Doesn't your motherboard have a PCIe slot? 
I'm using a GeForce 8400GS PCIe card and compiz is fine. It would be with a 7300GS as well. What were the Misco prices? Can you provide a link? I paid about £25 for my (much better make than PNY) 8400GS from Scan.

Sorry, yes, PCIe.
PNY 8400GS card is 25.99 inc VAT
[http://www.misco.co.uk/applications/SearchTools/item-details.asp?EdpNo=283229&CatId=0](http://www.misco.co.uk/applications/SearchTools/item-details.asp?EdpNo=283229&CatId=0)

I did ask Misco if it worked with Linux but they said it didn't come with Linux drivers :(

Maybe I should have mentioned I need a VGA type connector too.

Would any GeForce 8400GS card work okay?

Computers used to be so much simpler in the days when MEMMAKER was new and exciting. 

I do have other problems; I got a working display with Jaunty Xubuntu apart from a corrupted big square pretending to be a pointer, until I asked if it wanted to do compositing (thought that might help with the pointer) when it froze and now only boots into text mode telling me I#ve got the wrong password.

---

### Post by rob2uk on 2009-06-03
I'm using a GeForce 7900 GS with no problems, if it's any help.

Worked right out the box

---

### Post by coffeecat on 2009-06-03
> **OscarFoxtrot said:**
> Sorry, yes, PCIe.
PNY 8400GS card is 25.99 inc VAT
[http://www.misco.co.uk/applications/SearchTools/item-details.asp?EdpNo=283229&CatId=0](http://www.misco.co.uk/applications/SearchTools/item-details.asp?EdpNo=283229&CatId=0)


Yes, that will work fine with Ubuntu, and give you good compiz effects as well. Trouble is, PNY use cheap, nasty cooling fans and that card will make a continous, nasty droning noise. Take it from me: I've heard it - that very same card.

What I bought was:

[http://www.scan.co.uk/Products/256MB-Gainward-8400-GS-PCI-E-(x16)-Mem-700MHz-GDDR2-GPU-450MHz-8-Cores-D-Sub-DVI-HDMI]("http://www.scan.co.uk/Products/256MB-Gainward-8400-GS-PCI-E-%28x16%29-Mem-700MHz-GDDR2-GPU-450MHz-8-Cores-D-Sub-DVI-HDMI")

Same chipset, a better make, a bit cheaper and, above all, **silent** because it's passively cooled. Seems to be out of stock at the moment, but this is the one I use and it works fine. If you look in the Scan website, there's a 512MB version for only a few pounds more if you prefer.

> **OscarFoxtrot said:**
>  I did ask Misco if it worked with Linux but they said it didn't come with Linux drivers :(

Not a problem. The open source 'nv' driver for that card comes in the kernel, so you'll get good graphics, but no acceleration, out of the box. Then you can install the proprietary 'nvidia' driver and get desktop effects.

To be honest, it's not worth using the CD that comes with the card even with Windows. Windows users are far better going to the nvidia site and downloading the latest driver, so you might as well chuck the CD away anyway.

> **OscarFoxtrot said:**
>  Maybe I should have mentioned I need a VGA type connector too.

The Gainward card has that. Most/many cards have that still.

> **OscarFoxtrot said:**
> Would any GeForce 8400GS card work okay?

Yes.

---

### Post by OscarFoxtrot on 2009-06-23
I have bought one of these cards, fitted it and put on a clean install of ubuntu jaunty.

Jaunty only wants to work in 800x600. It asked me if I wanted to use nvidia drivers, I did sudo nvidia-config and restarted, Now I'm back to black cscreen and corrupted mouse pointer, I can do a recovery boot in 800x600 but not any higher res.

---

### Post by OscarFoxtrot on 2009-06-24
> **OscarFoxtrot said:**
> I have bought one of these cards, fitted it and put on a clean install of ubuntu jaunty.

Jaunty only wants to work in 800x600. It asked me if I wanted to use nvidia drivers, I did sudo nvidia-config and restarted, Now I'm back to black cscreen and corrupted mouse pointer, I can do a recovery boot in 800x600 but not any higher res.

This worked as long as I did a recovery boot. I once did an ordinary boot and now get a blank desktop with no menu/icons. Can't get back to a normal desktop again. 

Have done another install of Jaunty. What is the best thing to do with drivers please?

---

### Post by devilmafia on 2010-01-20
[IMG]http://www.mypictureshare.com/img/O/P.gif[/IMG]i think the best way is to find it on misco.co.uk or amazon
[IMG]http://www.mypictureshare.com/img/T/P.gif[/IMG]

---

