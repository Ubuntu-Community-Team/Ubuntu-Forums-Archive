---
title: "Minimum Compact Flash size for running OS on"
date: 2008-08-07
forum: Mythbuntu
---

### Post by uMuppet on 2008-08-07
I'm looking at running my OS off a Compact Flash card to cut down on noise and power consumption.  I'm told this will speed up read and write speeds too.  I'll be using a CF - IDE converter.

At the moment I have a 640GB HD, so what I would like to do is mount the CF card under / and the hard disk under /var/lib/mythtv.  And I guess the swap on the 640GB HD, but I do have 2GB RAM so might not need much swap.

What is the minimum size CF card I would need?  I could move /home to the hard disk too to save space.  Can I get away with a 2GB CF?

---

### Post by superm1 on 2008-08-07
You should be able to get away with a 2 gig flash if you don't do updates, but I would actually just keep all of /var on the hard drive and get a 4 gig if you can.  This will future proof you as you will probably end up wanting to add more apps in later, or maybe upgrade to 8.10 etc

---

### Post by nickrout on 2008-08-08
mytharchive can use heaps of space in /var/lib/mytharchive and logs in /var/log can grow very large, especially if you have errors. Therefore as the other poster said, you may be better to have /var on the hard drive.

---

### Post by uMuppet on 2008-08-08
I have seen that suggested before but was unsure why, thanks for clearing that up for me.  

So this is what I will do,

Compact Flash (4GB)
/

Hard Drive (640GB)
/home
/var

---

### Post by nickrout on 2008-08-08
don't think you will need /home on the hard drive, they should be kept pretty empty unless you are also using the machine for non myth purposes.

---

