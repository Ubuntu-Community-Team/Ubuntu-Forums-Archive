---
title: "Verizon/Novatel PC770"
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by FrostCyborg on 2009-12-08
I have an Verizon PC770 (Novatel branded ExpressCard CDMA Modem) and I can get 9.10 to recognize and connect automatically without having to use Gnome-PPP or setup up the device once I activated it on my Win 7 partition. Problem I have is that I want to fix it so that the "CD-ROM" portion of the ExpressCard containing the Windows drivers and software doesn't auto-mount. If I go into Disk Utility after inserting the PC770, then I can eject the mounted media and then access the Mobile Broadband connection option in NetworkManager. Is there anyway to change the device/configuration so it doesn't mount the "cd-rom?"

---

### Post by FrostCyborg on 2009-12-08
I looked in the forums for similar Novatel cards and found the entry that says to edit the 70-persistent-cd.rules file.  I went into it and looked at the entries.  Everytime I take the card out and put it back in, it creates a new entry with a new SYMLINK.  Nothing else is different with the entries except the SYMLINK.  Currently it's at "SYMLINK+="cdrom12"," and it duplicates all the way back to "SYMLINK+="cdrom1","

---

### Post by jasonrutherglen on 2009-12-23
I received the Verizon PC770, activated it on a spare Windows machine.  Now I'm trying to install the PC770 on Ubuntu 9.10 however it doesn't automatically install on the machine.  Despite browsing the web and searching in Google, I haven't found a solution.  I'm thinking of moving to a Macbook because of the PC770 not installing and OpenVPN not working properly on Ubuntu (which otherwise is a great OS).

---

### Post by pdc on 2009-12-23
it sounds as though it won't install jason, because linux sees it as a virtual CD-ROM device; 

you need to "flip" the device, as FrostCyBorg talks about three posts up (post #1):

after "flipping" the device, linux sees it as a modem;

to flip you

right-click on the icon that the device creates on your desktop and select "eject" 


so do that, and see what happens ........

does Ubuntu now prompt you to configure the device?

---

