---
title: "pam_mount - No Volumes To Mount"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by Johari on 2010-05-04
Hi All, 
        I have beating my brains out trying to get Lucid Lynx connected to an SME Server 7.4 to automatically mount windows shares.   The winbind stuff seems to work okay after I installed a restart script in /etc/network/if-up.d (kudos to OsGnuru & bobpaul for that) There is a short wait on network up before winbind can validate but that is not a show stopper. I have looked at (what I think) is the correct log for pam_mount and it seems to be running through to the end process okay.  It looks like it is either not reading the pam_mount.conf.xml file or I have not configured it correctly as it just reports "No Volumes to Mount".  I have appended the log file, pam_mount auth, password, session & common conf files as well as the pam_mount.conf.xml file for review.  Thanks for any assistance or suggestions that you may have.#-o

---

### Post by g1zmo on 2010-05-26
I'm having the same problem, but I can't help you because I haven't found a solution.

After installing a clean 10.04, I copied over the pam_mount.conf.xml from my old 8.04 to the new system and it no longer mounts my CIFS shares at login.  I also see in the logs where it simply says "No volumes to mount", even though there are 5 volumes defined in pam_mount.conf.xml.

I verified that I can manually mount these shares on the new 10.04 using a plain old "mount -t cifs ...".

I filed a Launchpad report, but I'm sure that'll be months before anyone notices, based on my experience with previous bug reports.

---

