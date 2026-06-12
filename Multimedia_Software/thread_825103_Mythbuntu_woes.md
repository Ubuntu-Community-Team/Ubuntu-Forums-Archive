---
title: "Mythbuntu woes"
date: 2008-06-10
forum: Multimedia Software
---

### Post by mthaddon on 2008-06-10
Hi Folks,

I'm having some problems with Mythbuntu and would really love to get them solved - I'm so close to having the perfect setup that I'm very happy with. So here's what I'm missing:

I've just bought a Pinnacle PCTV HD Card as per [http://www.bestbuy.com/site/olspage.jsp?skuId=8512424&type=product&id=1186005934822](http://www.bestbuy.com/site/olspage.jsp?skuId=8512424&type=product&id=1186005934822) and I'm trying to configure it to worth with my hardy Mythbuntu install.

I've been following the instructions on [http://mythtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_(800i](http://mythtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_(800i)) and have extracted the firmware, and compiled the v4l-dvb drivers per that page. I'm then able to see the device as an option in mythtvsetup. I've configured it as an MPEG-2 encoder card, and in the "Probed Info" section it's showing "Pinnacle PCTV HD800i [cx8800]". I've then setup Schedules Direct as a Video Source, and under "Input Connections" I've defined "[MPEG: /dev/video0] (Television) -> Schedules Direct". I've then performed the "Scan for Channels" and have got a bunch of channels showing up (I'm just using rabbit ears, don't have cable or satellite), but when I go to "Watch TV" on the mythfrontend I get a blank screen for a few seconds and then I'm returned to the main menu. I see the following in the frontend log:

2008-06-07 09:28:57.828 TV: Attempting to change from None to WatchingLiveTV
2008-06-07 09:28:57.829 Using protocol version 40
2008-06-07 09:29:03.102 GetEntryAt(-1) failed.
2008-06-07 09:29:03.103 EntryToProgram(0@Wed Dec 31 16:00:00 1969) failed to get pginfo
2008-06-07 09:29:03.103 TV Error: LiveTV not successfully started
2008-06-07 09:29:03.138 TV Error: LiveTV not successfully started
2008-06-07 09:29:03.234 TV: Deleting TV Chain in destructor
2008-06-07 09:29:03.238 DPMS Deactivated
2008-06-07 09:29:03.238 DPMS Reactivated.

And then after I think an update to linux-restricted-modules, whenever I run the mythtv-setup script and try to go to any of the pages (General, Capture Cards, Video Source, etc.) I get a message saying "If this is the master backend server, please run mythfilldatabase to populate the database with channel information". The only option is "OK" at which point mythtv-setup exits and I'm asked to run that command. If I do, it runs fine, but still I get the same message when I re-run mythtv-setup. So now I can't see my current config, or change it in any way...

My second issue is that I'd applied some updates (including updates to linux-restricted-modules) and rebooted. I then tried gxine for the first time and all the colors where bluish. I uninstalled, but discovered that it was affecting all media players. I was able to play a video without problems in xine before running it in gxine (which now has affected all players despite a reboot), but now I'm unable to revert the behaviour. I've tried setting the hue to 0 in totem, but it doesn't seem to persist...

My graphics card is an nVidia Corporation GeForce 8300 GS.

Any help appreciated.

Thanks, Tom

---

### Post by mthaddon on 2008-06-10
> **mthaddon said:**
> My second issue is that I'd applied some updates (including updates to linux-restricted-modules) and rebooted. I then tried gxine for the first time and all the colors where bluish. I uninstalled, but discovered that it was affecting all media players. I was able to play a video without problems in xine before running it in gxine (which now has affected all players despite a reboot), but now I'm unable to revert the behaviour. I've tried setting the hue to 0 in totem, but it doesn't seem to persist...

My graphics card is an nVidia Corporation GeForce 8300 GS.

I've got this working thanks to a suggestion on this bug [https://bugs.edge.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/184440](https://bugs.edge.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/184440) about using xvattr.

One down, one to go (except that using xine rather than gxine means I also have to figure out how to work around this bug - [https://bugs.edge.launchpad.net/ubuntu/+source/xine-ui/+bug/231507](https://bugs.edge.launchpad.net/ubuntu/+source/xine-ui/+bug/231507) )...

---

