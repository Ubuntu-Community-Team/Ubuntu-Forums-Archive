---
title: "How can I downgrade xserver-xorg-video-ati driver to feisty version (from hardy)"
date: 2008-05-19
forum: Multimedia Software
---

### Post by omairkhawaja on 2008-05-19
I need help with downgrading my ATI driver (xserver-xorg-video-ati driver) to the Feisty Fawn version.

My setup (briefly)

- Hardy Heron
- ATI Radeon 9100 graphics card

I've been having some troubles lately with both video playback as well as compiz and I'm not entirely sure what caused it.  In particular the following things that weren't present are now happening:
1) Compiz works but I see some strange behavior that I didn't see earlier, E.g.
a) When using the Shift Switcher plugin when I hit <Super><tab> the windows fade but I see nothing, but when I switch windows as I expected
b) The Enhanced zoom plugin doesn't work...  
there is other quirky behavior as well
2) mplayer does not work with xv (xvideo) output.  It used to work before...

I'm running hardy heron and I recall everything working fine...

There were a couple of critical updates I installed recently but I only restarted my computer two days ago after installing a new hard drive.  I suspect that one of the updates may have broken it... 

After searching a bit on the net... I found the following bug [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/150519](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/150519) and after reading I decided to downgrade... I'm having troubles however.  

I've tried the following:
a) Downloaded the driver from [http://packages.ubuntu.com/feisty/x11/xserver-xorg-video-ati](http://packages.ubuntu.com/feisty/x11/xserver-xorg-video-ati) and tried to install using   sudo dpkg -i %filename%.. but I get the following error:

dpkg - warning: downgrading xserver-xorg-video-ati from 1:6.8.0-1 to 1:6.6.3-2ubuntu6.
dpkg: regarding xserver-xorg-video-ati_6.6.3-2ubuntu6_i386.deb containing xserver-xorg-video-ati:
 xserver-xorg-core conflicts with xserver-xorg-video-1.0
  xserver-xorg-video-ati provides xserver-xorg-video-1.0 and is to be installed.
dpkg: error processing xserver-xorg-video-ati_6.6.3-2ubuntu6_i386.deb (--install):
 conflicting packages - not installing xserver-xorg-video-ati
Errors were encountered while processing:
 xserver-xorg-video-ati_6.6.3-2ubuntu6_i386.deb

b) I added the feisty fawn repository to synaptic's list of repositories and then selected the xserver-xorg-video-ati driver and selected the feisty fawn version using the Force-Version option.  This is problematic because it then forces me to mark for uninstall all of the dependencies of xserver-xorg-video-ati...

Can anyone help me out here?

Thanks...

---

### Post by bornagainpenguin on 2008-05-27
Hi, I need this also--only I would prefer to use the Gutsy version of the ATI drivers and my card is a ATI Radeon 7000.  Other threads on this subject (I've been searching) mention pinning and upgrading from Gutsy to Hardy--is there a way to simply downgrade the xorg drivers?  Really, just because ATI no longer supports these cards doesn't mean Ubuntu has to drop their support as well...given all the known issues with these cards I would have thought this type of situation would have been handled already!

--bornagainpenguin

---

### Post by kagashe on 2008-06-27
I have Radeon IGP 330M/340M/350M and it was working fine, even dual head was working in Gutsy.

When I installed Hardy, dual head stopped working. I switched to vesa so that I could use the external monitor. I also tried to downgrade but it failed.

There was a [bug report]("http://bugs.freedesktop.org/show_bug.cgi?id=15708") for my card. I followed the bug report very closely and found that it was resolved recently in Git, however, compiling and installing a version from Git was beyond my capability. I waited till the Git update was applied in Debian Sid and .deb package of the driver was released. I removed the ati driver of Hardy and installed following .deb packages from Debian Sid:
xserver-xorg-video-ati_6.8.192-1_i386.deb
xserver-xorg-video-mach64_6.8.0-1_i386.deb
xserver-xorg-video-r128_6.8.0-1_i386
xserver-xorg-video-radeon_6.8.192-1_i386

My dual head problem is resolved now. My experience is it is possible to upgrade not downgrade.

If I search for Radeon 9100 and Radeon 7000, I find many bugs but I hope they are getting resolved. There is no use blaming Ubuntu because it is using the driver provided by freedesktop.org.

Hope it helps.

kagashe

---

