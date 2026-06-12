---
title: "Backend stops responding"
date: 2009-11-30
forum: Mythbuntu
---

### Post by movieman on 2009-11-30
So after a while my backend stops responding to the frontend and Mythweb: the only way to get it back is to restart the backend service, and there's nothing in the logs to indicate why it's not responding.

This happened last night and I restarted it and it worked for about 24 hours before it stopped responding again.

I can set up a cron job to auto-restart it every hour just in case it's locked up, but that's a bit crap when it could run for weeks without a restart on 9.04.

---

### Post by radnor on 2009-12-01
I have a similar problem...  I have a FE/BE running 9.10.  I have a RFE also running 9.10.

On the FE/BE system after some time, the DESKTOP does NOT respond.  I can still access the BE from the RFE without problems.  And I agree with what you said about 9.04.

---

### Post by movieman on 2009-12-01
Interesting, I didn't try access from the remote front end at the time, only from the local one and Mythweb.

---

### Post by jrhartley on 2009-12-01
Im having the same issue. I just completed a FE/BE unit. I use to use mythdora without any issues.that was when I was using hd tuner cards and tuning unencrypted qam from local cable. I switched to mythbuntu 9.10 because of better support for firewire. now im using firewire with a dch3200....everything was working well(6 hrs) then BE quit responding..It has now happened 2 times....i was thinking it had something to do with firewire but if other people are having the same issue now im not so sure....help please

---

### Post by movieman on 2009-12-01
Yeah, no Firewire here, I'm using a PVR-150.

---

### Post by radnor on 2009-12-01
> **jrhartley said:**
> now im using firewire with a dch3200....

If you dont mind me asking, who do you have service with?  I have a DCH3416 on Concast and I think they neutered it.  I cannot access it VIA cat5.  Never tried FW.

---

### Post by jrhartley on 2009-12-01
Time Warner cable Dallas.....from what i understand its the law that firewire be open in the USA.... i haven't tried the eithernet port but from what i understand its reserved for future use...

---

### Post by radnor on 2009-12-02
Either of you guys try a RFE yet when the desktop is locked up on the BE?

I was thinking it was my BE setup, it's kinda strange....   

My BE:
I purchased a Dell off of Ebay P4 system 80G HDD 1G RAM.  I added a 2nd HDD from Ebay, 500G.  It was supposed to be IDE (listed as), turned out to be SATA.  So I added a PCI SATA controller with 6 ports.

There is one MINOR issue with the PCI controller...  I think the BIOS on the card is looking for FAT32 or NTFS, I KNOW it is NOT looking for a Linux file system.  So it complains for a second or two about no file system then goes on it's happy way and WORKS just fine....

WOL works great on the BE.  When the desktop crashes, SSH to shutdown (which is what I do anyway).

---

