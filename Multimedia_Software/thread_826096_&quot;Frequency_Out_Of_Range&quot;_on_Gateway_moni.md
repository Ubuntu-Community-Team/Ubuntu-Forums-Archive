---
title: "&quot;Frequency Out Of Range&quot; on Gateway monitor?"
date: 2008-06-11
forum: Multimedia Software
---

### Post by subinfinity on 2008-06-11
When running several games (most Linux native, but some under Wine), my monitor (model # on monitor is 700G, I think it's 17') blanks and displays a blue square saying "Frequency Out Of Range", which requires some blind hotkey acrobatics to either switch desktops, switch to a different terminal to kill the offending application, or reboot.  Two of the Linux programs were Tremulous and Warsow, and under Wine, Portal and Diablo II (the intro movie plays, but as soon as it reaches the actual menu screen, bam).  I checked gateway's website, but all they had to offer was a useless user's guide to the monitor (which included no error codes at all).  I guess it has to do with some unsupported resolution, but I never had this problem under windows.

According to the system configuration information the Gateway site pulled from my computer while I was still running windows, this is my video hardware info:

---------- Video ----------
Graphics Adapter: NVIDIA GeForce 6100
Screen Area/Colors: 1024x768 pixels, 16 million colors
Monitor: Gateway 5051

I am running Ubuntu Studio 8.04, and I do have the NVidia drivers enabled.

I don't think this is specifically a linux or ubuntu problem, but Gateway was no help, and the forums here are friendly and knowledgeable...

So, any ideas?

-D

---

### Post by syuusuke on 2008-06-11
you'll need the specs for your monitor from gateway.  they usually have a list of supported resolution modes with horizontal and vertical frequencies.  Using that information, you edit the xorg.conf file in /etc/X11/.  In that xorg.conf file you'll see a section called "Monitor".  In "Monitor" you'll have to enter in the list of supported resolutions/frequencies.

[http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html]("http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html")

Read that for more info, more specifically.. read about "Modeline"

I hope this somewhat helps :)

---

### Post by from_rus on 2009-11-04
> **subinfinity said:**
> When running several games (most Linux native, but some under Wine), my monitor (model # on monitor is 700G, I think it's 17') blanks and displays a blue square saying "Frequency Out Of Range", which requires some blind hotkey acrobatics to either switch desktops, switch to a different terminal to kill the offending application, or reboot.  Two of the Linux programs were Tremulous and Warsow, and under Wine, Portal and Diablo II (the intro movie plays, but as soon as it reaches the actual menu screen, bam).  I checked gateway's website, but all they had to offer was a useless user's guide to the monitor (which included no error codes at all).  I guess it has to do with some unsupported resolution, but I never had this problem under windows.

According to the system configuration information the Gateway site pulled from my computer while I was still running windows, this is my video hardware info:

---------- Video ----------
Graphics Adapter: NVIDIA GeForce 6100
Screen Area/Colors: 1024x768 pixels, 16 million colors
Monitor: Gateway 5051

I am running Ubuntu Studio 8.04, and I do have the NVidia drivers enabled.

I don't think this is specifically a linux or ubuntu problem, but Gateway was no help, and the forums here are friendly and knowledgeable...

So, any ideas?

-D

Greetings, at me the same problem. Probably a problem in card GF 7600. Whether there are any decisions on elimination? Forgive for my bad English.

---

