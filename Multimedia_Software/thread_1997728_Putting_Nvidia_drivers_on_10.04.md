---
title: "Putting Nvidia drivers on 10.04"
date: 2012-06-05
forum: Multimedia Software
---

### Post by emustrangler on 2012-06-05
Just installed 10.04 on a Dell Precision with a Quadro 600 video card.  The monitors menu in **System > Preferences** just gives me just two options for resolution settings 800 x 600 and 640 x 480.  As I have a 27" monitor, this is rather nauseating to use.  

No problem, says I, I'll just install the Nvidia provided video drivers.  But going to **System > Administration > Hardware Drivers**, I'm not given an option to install the proprietary Nvidia drivers (or any other drivers, for that matter).

In Synaptic, there's a Nvidia-Current package.  Can I just install that?  Does the fact that I wasn't given the option to use the Hardware Drivers wizard a sign of some deeper problem?  

Thanks for the help

---

### Post by emustrangler on 2012-06-05
Seems like the latest propriety driver that supports 10.04 doesn't support the Quadro 600.  So I took a chance and installed the latest driver (295.53) ([using the instruction here](https://help.ubuntu.com/community/NvidiaManual)) and it seems to work.  I know have access to my screens native resolution.  Hooray.

---

