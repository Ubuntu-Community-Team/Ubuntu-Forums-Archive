---
title: "duplicate keystrokes from remote in Mythbuntu 10.10"
date: 2011-01-14
forum: Mythbuntu
---

### Post by samiller25 on 2011-01-14
I just upgraded to Mythbuntu 10.10, and now lirc seems to duplicate keystroke events from my DViCO FusionHDTV7 remote.  I know there have been several posts about a similar issue with the Streamzap remote, e.g., [http://ubuntuforums.org/showthread.php?t=1595018]("http://ubuntuforums.org/showthread.php?t=1595018") and [http://www.gossamer-threads.com/lists/mythtv/users/456911]("http://www.gossamer-threads.com/lists/mythtv/users/456911"), but this seems to be different, maybe because I'm using the devinput remote driver.  Still, using the Streamzap suggestions as a model, I have tried
[LIST]
[*][disabling the xinput device in xorg.conf]("http://wiki.xbmc.org/index.php?title=Streamzap_PC_Remote#Option_1:_Disable_Streamzap_Xinput_Device_usign_Xorg_Configuration")
[*][disabling the device in hal]("http://www.lirc.org/html/devinput.html")
[*]removing the rc_fusionhdtv_mce module (out of desperation)
[/LIST]
I've rebooted and verified that the device, called "i2c IR (FusionHDTV)", is not listed in "xinput list" and marked as ignored in "lshal".  Still, irw shows the following output when I press the remote up key, for example:

```
0000000080010067 00 KEY_UP devinput
0000000080010067 01 KEY_UP devinput
```

I cannot find anything else that would be capturing the remote code.  Help please!

-- Scott

---

### Post by ian dobson on 2011-01-14
Hi,

I had the same problem with my Hauppage remote on a Homebrew Serial IR reciever. It turned out to be a problem with the hauppage configuration file that listed several remotes and as the key pulse sent by the remote corresponded to several key presses in the config file the key was sent several times to mythtv.

Note the configuartion worked 100% in 10.04 and broke after updating to 10.10, which makes me believe that the problem was caused by modifications to the parser code in lirc that got implemented as part of the work to get lirc in-kernel.

Regards
Ian Dobson

---

### Post by samiller25 on 2011-01-14
The problem is definitely related to bringing lirc into the kernel.  Did you find a fix to your problem, Ian?

-- Scott

---

### Post by samiller25 on 2011-01-14
> **samiller25 said:**
> 
[LIST]
[*]removing the rc_fusionhdtv_mce module (out of desperation)
[/LIST]


Correction: I removed the module but didn't restart lirc.  When I restarted lirc (today) it didn't work, so I reloaded rc_fusionhdtv_mce.

Also, I found a work-around: setting "repeat = 0" in ~/.lirc/mythtv for all keys, so the duplicates are ignored.  I'd like to get a real fix, though, so I could restore the repeat on the volume keys, for instance.

-- Scott

---

### Post by ian dobson on 2011-01-14
Hi,

I solved it by manually editing the lirc remote configuration file (it's as a include in the hardware.conf file for lirc). In this file there were definitions for several hauppage remotes and I just deleted all of them appart from the one for my remote (Hauppage_350).

I don't have access to my frontend system at the moment, and I'm not sure if I'll make it home today or even this weekend (Commissioning on site and things aren't going too well, but that's not my fault)

Regards
Ian Dobson

---

