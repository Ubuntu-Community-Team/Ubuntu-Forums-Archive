---
title: "Best router for Ubuntu and XP"
date: 2012-11-27
forum: Networking &amp; Wireless
---

### Post by paul4862 on 2012-11-27
Just install Ubuntu on redundant desk top, split hard drive in half. Half XP the other Ubuntu.
going to replace safecom lan card (and router down Stairs) because running wep security and cant get info on driver etc.
which is the best router and lan card that will support this set up?

---

### Post by ahallubuntu on 2012-11-27
By "lan" do you mean "wireless card?"  If your wireless card is not recognized by Ubuntu, you can post information about it here to get help trying to get it to work.

Any new router should work fine, any router sold in the last 5 years should support WPA2.

You don't need a "driver" for an old router.  You can set it up with any operating system unless it is an Apple Airport product (then special software is required).   However, if what you are saying is that the old router only supports WEP and not WPA2, replacing the router would be a good idea.  WEP is not very secure.

---

### Post by TheFu on 2012-11-27
"best" is completely subjective.  Based on your requirements ... which are extremely sparse, you want something that supports some version of Ubuntu and WinXP.  Since XP hasn't been supported for a few years, you need to look for used cards.

Usually, I search for Intel PRO/1000 cards for the greatest compatibility, price, performance, but with WinXP, you'll need to be careful as XP doesn't include drivers for the PRO/1000 line. Drivers exist, but you'll need to get them either from Intel or with the card.  You can't just get any card that is "Windows compatible" anymore, unless you intend to run Windows 7 or 8.

On the Linux side, it is a little easier.  Linux users have created databases with hardware that works.  Search for HCL - "hardware compatibility list" to get started.

I'd start with the Linux search first, then verify that WinXP works with that specific card.

Before you start searching, you'll need to know .... a few important things about the computer, like what adapter slot type it has?  PCIe, PCIx, or straight PCI?  You didn't say if a full-length card is needed, half-height card, or any slot specifics.  Is there a price issue - $1000 or $10?  Which version on XP and which specific version of Linux are you trying to use?  Does 10/100 work enough or would you want 10/100/1000 ethernet?

All this matters.

As to the best router, that is also subjective and based on what your needs are.  I just bought a TP-Link router 2 months ago, but my needs are not the same as yours.  After I replaced the firmware provided by the vendor with DD-WRT (took 4 steps flashing old, then german, then dd-wrt, then the dd-wrt version I wanted) to get it working. I suspect you would want an easier solution.  You should make a list of what are important features for the router in your judgment and search for a router that does those things and has a good reputation for working.  A few considerations:
* number of ports?
* bandwidth for each port 10/100, 10/100/1000
* wifi version supported?  B, G, N-150, N-300, N-450, N-600 or faster?
* Does it need to include a DSL or cable modem?
* Would you like it to be a print server?
* Would you like it to be a USB2 file server?
* Does the warranty length matter?
* Does it need to be compatible with DD-WRT, OpenWRT or Tomator firmwares?

Lots of questions.

---

