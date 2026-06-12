---
title: "Mythbuntu 10.04 Hauppauge PVR-500 aren't recognized on reboot"
date: 2010-06-15
forum: Mythbuntu
---

### Post by brian_hayward on 2010-06-15
I am running Mythbuntu 10.04 and i am running two Hauppauge PVR-500 cards.  Whenever i reboot the machine and i check the Mythlogs, i am notified that the cards aren't found and that i need to re-run the setup program (??? i think i got the wording of the message wrong hopefully you get the picture).  After i enter the backend setup, then open each card and do a scan for channel information on each card they are then recognized and working again.  Its a huge pain to do this and i would love to not go through those steps after each reboot.  Does anybody have any ideas on a fix?  Any suggestions and ideas are greatly appreciated.  Thanks.

---

### Post by klc5555 on 2010-06-15
> **brian_hayward said:**
> I am running Mythbuntu 10.04 and i am running two Hauppauge PVR-500 cards.  Whenever i reboot the machine and i check the Mythlogs, i am notified that the cards aren't found and that i need to re-run the setup program (??? i think i got the wording of the message wrong hopefully you get the picture).  After i enter the backend setup, then open each card and do a scan for channel information on each card they are then recognized and working again.  Its a huge pain to do this and i would love to not go through those steps after each reboot.  Does anybody have any ideas on a fix?  Any suggestions and ideas are greatly appreciated.  Thanks.

There appears to be a timing issue in 10.04 affecting old pvr-150s, wherein mythbackend seems to be starting before the 150's driver has initialized the card. 

Since a 500 is essentially two 150s, it might be affected as well. One of two workarounds (for the 150) seems to be generally used: 1) restarting the backend (rather than redoing the backend's setup as you have been), or 2) delaying the start of the backend until the card has initialized.

1) is likely simpler. When the symptom presents itself after boot, try (from a prompt) 

sudo /etc/init.d/mythtv-backend restart

If your card reappears to mythtv, you know you've got the problem nailed. 

If this does nail the problem, you can try adding (without "sudo") the line 

 /etc/init.d/mythtv-backend restart

to your /etc/rc.local file, which may get the restart happening after your card driver is properly loaded.

---

### Post by zukakog on 2010-06-17
After the upgrade to 10.04, my pvr-500 isn't even recognized. I can restart the backend, but it still doesn't recognize my card. When I try to scan, it can't find them. Any ideas?

---

### Post by klc5555 on 2010-06-18
> **zukakog said:**
> After the upgrade to 10.04, my pvr-500 isn't even recognized. I can restart the backend, but it still doesn't recognize my card. When I try to scan, it can't find them. Any ideas?

Hard to diagnose without information. But the place for you to start will be in the "Troubleshooting" section of the Mythtv Hauppauge PVR-500 wiki page here: [http://www.mythtv.org/wiki/Hauppauge_PVR-500](http://www.mythtv.org/wiki/Hauppauge_PVR-500)

---

### Post by zukakog on 2010-06-18
Heh, sorry about the lack of info. :oops: I was hoping that it was a common issue with 10.04, with an easy solution. I'll do my homework before posting again.

---

