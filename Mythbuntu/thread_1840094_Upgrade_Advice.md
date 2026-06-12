---
title: "Upgrade Advice"
date: 2011-09-06
forum: Mythbuntu
---

### Post by bah1976 on 2011-09-06
Ok - I'll admit it - I haven't been here in awhile.  In '08, I got a stable 8.04 system running, and haven't touched it since.  Now I'd like to upgrade, and I'm not sure where to start.  Is it as easy as downloading the current iso from mythbuntu.org, booting from it, and choosing upgrade?  I've put some other stuff on my BE/FE that will be my own issues (backup client, vmware server) but I want to make sure when this upgrades I don't break anything (mythtv) permanently.  That would really hurt the WAF.

So - any tips?  recommendations? caveats? Is my new in '08 hardware going to be ok?  OS is a single drive - all recordings & such are on a lvm raid5.  Is there such a thing as a dual-boot/parallel install to different mythbuntu versions?  I know how to do that in windows, but not in linux.

I appreciate any thoughts...

---

### Post by klc5555 on 2011-09-07
Right up front I'll point out that I'm an advocate of leaving a perfectly functioning and perfectly configured system alone until the wheels fall off the hardware, or unless there's a killer new feature or fix that makes an otherwise unnecessary upgrade worth the trouble. Admittedly that's not the Ubuntu Way, where even security updates to a version stop after a mere 1.5 to 3 years.

That said, the normal way to handle this upgrade is from LTS to LTS: you'd go from 8.04 LTS to 10.04 LTS by using the Upgrade Manager or from the command prompt. The standard Ubuntu instructional doc is here: [https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

Will the upgrade be smooth? Probably. Will there be a bit of minor breakage? Sure --there's always a bit of breakage when upgrading. Your 2008 hardware should be almost as OK for 10.04 as it is for 8.04. Back up a copy of your current mythconverg database and keep it safe, just in case.

---

### Post by Chewiesw on 2011-09-08
+1 . I firmly believe if it isn’t broken don’t try to fix it ( I however never follow my own advice). I  highly recommend cloning your stable 8.04 setup with clonezilla or some other cloning tool and then if possible testing the image before you make any changes.

If I were in your shoes I might just buy and new hard drive and remove the stable 8.04 and start from scratch, that way if it doesn’t work out you can just put the working “old” disk back. 

Good Luck

---

