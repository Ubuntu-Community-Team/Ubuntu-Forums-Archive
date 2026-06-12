---
title: "HD3000 with MythTV on Feisty"
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by ebob on 2007-05-05
I have followed the MythTV guide at [https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend) and appear to have run into a problem.  So far, the only thing I have done differently is set the TV Format to ATSC rather than NTSC due to the fact that the HD3000 is a digital-capable card.  I had done this previously when setting up this box in Edgy.  The problem is that when I go to set up the card in Capture Card Setup, I select DVB DTV capture card (as I had done with Edgy), and it says "Could not open card #0" and "No such file or directory".  Any clue as to what is going on and possible resolutions?  Thanks in advance.

---

### Post by Bigchris on 2007-05-06
I've got two HD3000s running just fine in Feisty.  You must add cx88_dvb to the end of the /etc/modules file and then reboot.  
I'd also recommend  that you go back and set ATSC back to NTSC.  The change you made isn't needed or useful and would probably prevent the analog tuner on your HD3000 from working if you tried to use it.   
If the problem persists, check the following.  If the card is being recognized correctly you should have a /dev/dvb/adapter0 and a /dev/video0.  If they are present you probably have a Mythtv problem.  If they're not present, you have a Ubuntu or hardware problem.

---

