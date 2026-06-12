---
title: "ATI Radeon - Reboot and No Picture"
date: 2008-04-09
forum: Multimedia &amp; Video
---

### Post by thenders on 2008-04-09
Hi,

I just installed the ATI Radeon driver through restricted driver window. On reboot I get message on monitor saying Format not supported. Is it possible the default resolution is not supported by my LCD? How do I reverse this given that I cant see anything to do anything at the mo? Is there a way to adjust resolution through recovery mode?

cheers

Todd

---

### Post by warp99 on 2008-04-10
Do you get a splash screen or boot to a login screen? Also what is the resolution your using?

---

### Post by thenders on 2008-04-10
I get a black screen with a box saying "Not Supported Mode" this is the message from my LCD. I can see the initial boot up process and Ubuntu logo, but blank screen for logon.

---

### Post by warp99 on 2008-04-10
Boot to recovery mode, when the "Grub" loading screen appears press escape, then choose "Recovery mode". Once booted to a command prompt issue the following:

```
dpkg-reconfigure xserver-xorg
```

Choose 'ati' as you driver, then when get to monitor resolution choose a resolution that you want and remove any resolution **ABOVE** that from the list presented. When completed issue a 'reboot' command:

If that driver does not produce a login screen repeat the same process, but use the video driver 'vesa' instead of 'ati'. It may also be that the highest resolution that auto-configuration thinks it can run it too high, therefore you would choose a resolution just below the maximum size and remove anything higher, here's an example:

My Apple ibook's maximum resolution was 800x600, but auto-configuration thought that a resolution of 1028x768 could be obtained. The repair was to remove the resolution choice of 1024x768 during reconfiguration of xserver-xorg.

---

