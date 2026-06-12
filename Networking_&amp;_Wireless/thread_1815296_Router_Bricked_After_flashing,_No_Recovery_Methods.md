---
title: "Router Bricked After flashing, No Recovery Methods Working"
date: 2011-07-31
forum: Networking &amp; Wireless
---

### Post by Bryant.GhostInTheMachine on 2011-07-31
I have an older linksys wrt54g2 v1 wireless router that's been sitting in my closet which I have been trying to set up as a network bridge. The router did not support bridging natively, so i decided to flash the firmware with a new one which did support it. I followed the instructions on flashing for my model, and it was promptly bricked. I've been up for four hours trying to fix this thing... I've tried every solution available, but they all rely on using tftp with Windows and the ones that require you to hold the reset button to bring up some sort of emergency de-corruption utility have failed. I've pinged the router and it has been successful, but my web browser cannot connect to it at all. Since the firmware is corrupted, this isn't much of a surprise, but it's rather vexing. The best method that seems likely to succeed uses tftp to manually load a new firmware, but that hasn't worked for me because it requires Windows. (I have the tftp protocol installed from the repositories, but it won't accept any of the commands I give it and there's no online help that's even halfway intelligible).

Can someone please give me a solution? I don't want to have to buy another router when this one would have worked.

[EDIT]:

I found a method for ubuntu using atftp which appears to have semi-worked. At least, the router shows up now with the routel command whereas before it would not appear at all. However, I still can't seem to open it in my web browser, even though I re-installed the official firmware rather than the open source firmware I got offline. How can I get it to appear in my browser?

{EDIT EDIT}:

As of this morning I have managed to set up the alternative firmware successfully, but now it appears that I can't set it up as a network bridge because the router I'm connecting my Linksys router/bridge to is an Apple Airport... This is starting to become rather trying on my patience and nerves.

---

