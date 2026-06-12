---
title: "Adding a video card"
date: 2006-01-24
forum: Multimedia &amp; Video
---

### Post by ed_d on 2006-01-24
OK, I want to replace my onboard video with another card, but can only use PCI. I acquired an TNT 16mb pci card and I wanted to install it in my system. I did a test run on a PC I have at work. So I went to synaptec and did a search for nvidia. Picked the kernal and the drivers for legacy. installed them, ran the enable command, shutdown the pc, installed the card and brought it back up. Well, I had video through the initial boot up, but when it is supposed to give you a login screen, I get nada. try opening a pseudo term, and I cant. So I shut down the pc, removed new card, broght back up with on board and back to where I started. Am I missing something? What else should I do?
btw, still looking for a better video card, but the 16 should be better than the onboard 8.
TIA
Ed

---

### Post by Dr. Nick on 2006-01-24
well, if replacing the nvidia with the onboard allowed the computer to boot into a full gui then I would say xorg is not set up right.

If the nvidia legacy drivers were properly enabled then using anything but a legacy  nvidia card should not allow a GUI to boot, you understand what I mean?

My advice would be to use the onboard and then manually configure your xorg.conf file to use the nvidia drivers, also note that you most likely need to set a BusID setting, though I am not sure what it is for pci. 

If you need help configuring xorg.conf then post that file up here for others to look at and make suggestions. After editing it then shut down, switch cards, and boot up again.

---

