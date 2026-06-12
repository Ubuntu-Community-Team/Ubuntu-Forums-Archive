---
title: "My Realtek 8187 hates me..."
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by Silent Warrior on 2009-05-03
I actually think this is a somewhat new issue - at least not common enough to have stickies all over the world dealing with it.
So, I'm trying to get started in LinuxMint 6 (Felicia GNOME, based on 8.10), with my above mentioned Realtek 8187 network thingy. (In the process of checking out different distributions. Linux promiscuity ftw!) I'm posting this here because I can't seem to register on the Mint-forums - I can think of no explanation for that.
I get the impression the kernel should have support for it, but it's not detected and having its drivers loaded, so I try to use ndiswrapper. And this is where the "fun" starts...

I'm using a laptop, and I have easily accessible Windows-drivers on the Windows-partition (not quite ready to let go, but it's not far off) - yay, Toshiba! So I open the ndis-GUI, look for the drivers, and install among a rich picking of XP and Vista 32-/64-bit versions. I looked at the ndiswrapper-sticky, and can confirm the futility of loading the 32-bit drivers. But the XP 64-bit build is where I run into a wall, face first... When I do load it, I finally get some action with the Network Manager (I see a tick-box and list-entry for a wireless connection, which is GOOD). It also blocks the OS on so many levels I'm honestly afraid of what I'll see if I boot into Mint now... It won't even shut down on its own!
I can right-click the NM-icon, but left-clicking makes the OS freeze up for a while (20s?), with exception for the mouse. I can't open any menu or anything until whatever process is going on times out.

Suffice to say, the next attempt will be the Vista driver... Something else of note: I'm posting this from the preinstalled Vista - so the card should still be in good order.

Any ideas? This has to be the first time installing what seems to be the CORRECT version of a driver hoses the system...

---

