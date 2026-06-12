---
title: "Networking with  9.04 Remix"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by mark1692 on 2009-04-26
I have the new Asus PC1000HE which came with Windows XP and it works fine with my networked systems and printers.   

[SIZE="4"]The problem;[/SIZE] now that I have installed the 9.04 Remix on this same PC1000 Netbook Computer everything works except for the networked devices and printers.  When running Remix it will connect to the Internet just fine but when I try to connect to any of my networked devices I get this message ( UNABLE TO MOUNT SOURCE ).   I also get the same message when trying to setup a networked printer.

Anybody got any ideas?  Am I missing something?   I am not a nubee with linux or Ubuntu and as I said the standard desktop edition works fine with my other computers and devices so is the problem with REMIX or am I just missing something. 

This computer works perfectly with my network when connected via Cat 5 cable to the router with the wireless disabled.

I am using it right now with Remix to write this post and I love this little machine so connecting to my network is essential for this to work out.

Any help here would be greatly appreciated.   Thanks;  Mark

---

### Post by 81377 on 2009-04-26
I am having a similar problem with networking since upgrading to 9.04. An automatic update following initial 9.04 upgrade caused networking to stop working completely. Network Connections shows no devices, ie eth1. The interface is listed in /etc/network/interfaces. Does anyone have a clue or similar problem? Thanks for any help you can provide.

Sorry this was for the Desktop version. I found the problem was solved by eliminating any modifications I made to /etc/network/interfaces, which had worked previously.

---

### Post by mark1692 on 2009-04-26
What system are you using?  Netbook ?  Laptop?  elaberate please!

The Remix version is only designed for netbooks!

---

### Post by dsabecky on 2009-04-26
> **mark1692 said:**
> What system are you using?  Netbook ?  Laptop?  elaberate please!

They just said remix. Remix is only for netbooks.

---

### Post by mark1692 on 2009-05-02
I wish to Explain the networking problem a little further.

The Asus PC100HE running Remix 9.04 will sometimes connect wirelessly with my Windows shared devices and Printers.  But the connection usually only lasts for a few minutes and then becomes unavailable or unable to mount source or samba share list unavailable.  These are the messages that appear when I try to connect to the devices.  All the while the connection to the internet through the same wireless router continues to work uninterrupted.

This very same computer still running Remix 9.04 when connected via Cat 5 network cable to my router will connect and share and print to all my networked device with no problem as long as the wireless is disabled,   As soon as the wireless is re enabled everything stops working except for the internet connection, even the with the Cat 5 cable still connected.   This has to be a bug in the Remix system somewhere because the same computer running Window XP works perfectly through the same network wirelessly with no problems at all.

I have two other Laptops running the standard desktop edition of 9.04 with wireless connections to my network that work flawlessly. 

Can somebody please explain this or help me fix this? Please!

---

