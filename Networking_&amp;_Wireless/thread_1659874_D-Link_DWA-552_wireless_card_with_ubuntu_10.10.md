---
title: "D-Link DWA-552 wireless card with ubuntu 10.10"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by Tom77084 on 2011-01-04
This topic was beat to death about three years ago but most of the link and fixes prescribed on message boards at the time are now missing. I am a ubuntu know-nothing so even the most basic help will be a challenge. 

I have a server running ubuntu 10.10 and I'm trying to get a D-link DWA-552 wireless N card to work. The lspci command cannot see the card. Where do I begin?

---

### Post by Vermind on 2011-01-04
Hi,
I take it the card is a wireless card and PCI?
On my old laptop, a PC-Card D-Link required the use of ndiswrapper.
You can dig up your Windows driver disc for the wireless card, you will need it for this.
The alternative is to download and extract the driver package for Windows xp 32-bit or somesuch.

Now, I don't know if you have graphical access to the server. If yes, you can use synaptic and find the ndisgtk package. This gives you a GUI to ndiswrapper.
If you have console only, do sudo apt-get install ndiswrapper-utils-1.9 and read online on how to use it. For both ways you will need an INF file and possibly other files from the Windows driver package.

---

