---
title: "Unable to import channels.conf and missing channels on scan"
date: 2009-11-21
forum: Mythbuntu
---

### Post by jensk on 2009-11-21
I have a 9.10/0.22 test setup that i try out before upgrading my present 9.04/0.21 backend.

My major problem is that I am not able to get all my DVB_T channels when i scan for channels. It looks like if there is a HD channel in a mux only the HD channel is found. the other 4 channels isn't found on scan.

So instead i tried to issue the command ```
scan -a 0 -f 1 >> channels.conf
``` to create a channels.conf to import.

In channels.conf all the channels in all 5 mux'es are found.

My problem now is that when i select import channels.conf under scan for channels in mythtv-setup it says that it cant find the file - no matter how i enter the path.

Can anybody tell me the correct form of the path statement?

My tunercard is a Hauppauge HVR-4000. I have added the v4l-dvb-fixes to get the HVR-4000 card working.

/jk

---

