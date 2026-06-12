---
title: "audio no longer works after reinstall"
date: 2007-08-09
forum: Multimedia &amp; Video
---

### Post by ymirscorpse on 2007-08-09
As late as yesterday, audio was working perfectly with my ubuntu install, so I know that my sound card is compatible.  However, yesterday I had to reinstall the OS to prepare for a project.  Previously, Linux was the only operating system that was installed.  Yesterday, I repartitioned my two hard drives, installed Windows Server 2003 on one partition, Ubuntu on another partition, and formatted the other two partitions as NTFS for general data storage.  Additionally, I added a new NIC to one of my PCI slots, so that I can use this machine as a domain controller connecting to a second machine with Windows XP Pro installed (I am studying for an MCSA).

I don't know that the addition of the new NIC has caused a conflict -- the tribal drumming start-up sound at the Ubuntu login screen does play, but audio does not work after logging in.  I have installed all of the recommended packages to allow restricted audio/video formats to work.  But no sound.  When I attempt to open the volume control, I get the following message:

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured."

Curiously, audio also does not work with Windows Server 2003.  I am missing the drivers for them, but I can't easily load them -- this is an onboard sound device in a motherboard that came with an Emachines computer, and Emachines computers don't come with installation CDs -- you only get one "restore DVD."  I'll have to track them down online.

However, I don't really care whether or not audio works with Win2k3, but I'd like to get it working with Linux again.  I believe I have found my audio device in Device Manager.  It says "VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio."  I am not sure why the drivers aren't already available to me -- I never had to track them after previous installs.  Sound always worked without a hitch.

Any advice on how to resolve this would be much appreciated.  I don't have any experience in configuring devices with Linux.

Thanks,
Chris

---

