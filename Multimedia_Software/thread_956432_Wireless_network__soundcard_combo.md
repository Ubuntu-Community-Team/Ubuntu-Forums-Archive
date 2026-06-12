---
title: "Wireless network / soundcard combo"
date: 2008-10-23
forum: Multimedia Software
---

### Post by wintermute115 on 2008-10-23
[[crossposted to Networking & Wireless]]

The computer I've just built was originally going to be WinXP64, but (to cut a long story short) has ended up being Ubuntu64. However, this means that some of the hardware I got for it isn't working.

In particular, I have a [class N wireless card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833704031") and a [USB audio dongle]("http://www.microcenter.com/single_product_results.phtml?product_id=0219416"), neither of which seems to be working. When I go into Preferences > Sound, tell it to use USB Audio and click on "test" I get sound out of it, but that's the only way it makes any noise at all. Admittedly, I've not tried installing drivers for it yet, so that might be a factor. I've tried getting the wireless card to work with NdisWrapper, without success.

Anyway, my question is this: Given that I have precisely one free PCI slot and a couple of USB ports, what combination of audio and wireless networking hardware would you recommend? Ideally, I'd prefer solutions with native Linux drivers, but so long as I can get them to work, I'll be happy.

The lists of wireless chipsets supported are useful, but they don't make it easy for me to go into a shop and see what they have that I can safely buy, so I'm really looking for assembled products, if that's possible...

Thanks very much for your help.

---

### Post by markbuntu on 2008-10-23
You shouldn't need drivers for the usb audio, especially since it tests OK. It is most likely just a setup issue. Do you have an on-board sound chip or an HDMI video card?

---

### Post by wintermute115 on 2008-10-24
There's audio headers on the Mobo, but they're not connected to anything, and the back panel doesn't have any audio outs. No HDMI.

---

### Post by phowells on 2008-10-24
Have you tried diabling the on board audio?  It is likely that the onboard audio is being used as your default device.  Try pluging your head phones into the onboard audio and see if that is working.  If you are not going to use the on board then you can disable it in the BIOS which will then leave your USB sound as the default sound device.

---

### Post by wintermute115 on 2008-10-24
> **phowells said:**
> Try pluging your head phones into the onboard audio and see if that is working.

As I don't have any headphones that will plug into this, that could prove difficult...

[IMG]http://www.intel.com/support/motherboards/desktop/sb/img/fp_audio.jpg[/IMG]

---

