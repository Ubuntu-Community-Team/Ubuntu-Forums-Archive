---
title: "Jaunty -- Intel 82945G/GZ -- Screen full of vertical lines, cannot logon"
date: 2009-06-10
forum: Multimedia Software
---

### Post by ichudov on 2009-06-10
This is possibly related to the Intel driver xserver-xorg-video-intel

This is my parents computer that they have 2000 miles away from me. THey were on Hardy and everything worked. I upgraded them (via ssh, do-release-upgrade) to Intrepid and rebooted, then upgraded to Jaunty. 

After that, they report that their screen is full of vertical lines and they cannot log on. Fortunately, that computer is set up for remote ssh access, so I have command line level access. 

This seems to be an Intel driver issue:

bunny:root:/var/log ###lsmod|grep i9
i915 65540 2
drm 96296 3 i915

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

This is a high priority issue to me, as I am deeply embarrassed by such poor performance on what seems to be a very mainstream PC (3 year old Dell). So if you have any downgrade suggestion for the meantime, let me know, I feel very badly about this.

I need help ASAP or suggestions on some lesser driver to downgrade to.

---

