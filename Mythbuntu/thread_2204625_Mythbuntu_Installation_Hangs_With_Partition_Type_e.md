---
title: "Mythbuntu Installation Hangs With Partition Type ee"
date: 2014-02-09
forum: Mythbuntu
---

### Post by Twinkel on 2014-02-09
This morning, I tried a couple of times to install Mythbuntu 12.04.3 (64-bit) from a USB thumb drive on to a Zotac ZBOX with a brand new, 1TB Western Digital SATA drive.  This installation would fail just before the selection of where to install (right after the "Preparing to install Mythbuntu" dialog).  The system would just sit there with a blank screen.  I booted Knoppix 7.0.4 from an external CD drive instead, and poked around to see if my hard drive was being detected.  fdisk said that the partition type was set to ee, that such a type was not supported by fdisk and that I should use gparted, instead.  I should have taken that as a hint, but instead I installed Kubuntu 13.04B2 (x86_64)... just the last DVD I had burned.  Kubuntu installed fine, but instead of rebooting into it I decided to try Mythbuntu one more time.  I suspect, since the Kubuntu install altered the partitions, that this is what helped Mythbuntu install properly.  I should really be submitting this to a bug tracker somewhere, but it might be useful to someone who is having problems.

---

