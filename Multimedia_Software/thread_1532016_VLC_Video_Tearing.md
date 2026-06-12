---
title: "VLC Video Tearing"
date: 2010-07-15
forum: Multimedia Software
---

### Post by GeekDiscourse on 2010-07-15
I liek using VLC as my video player but when going fullscreen there is tearing. Is there a specific output I should try? I am running a GeForce 260 w/ the official drivers. It defaults to XVideo output.

---

### Post by mc4man on 2010-07-15
I've never had tearing with nvidia ( well not until maverick, bit that's due to the driver - 256- and an agp card.

I always set vsync wherever possible - 

In System -> Admin. -> Nvidia X Server ... there are 2 places to enable, the more useful is under "Xserver Xvideo Settings, also can be enabled under 'OpenGl Settings'.

Save the setting(s) with 'nvidia-settings Confirmation', will save to a file in  home folder- .nvidia-settings-rc

In lucid nividia-settings should autorun on startup, you can ck. in System -> Preferences -> Startup Applications

The other place is in System -> Preferences -> Compizconfig Settings Manager 
(if not installed go
```
sudo apt-get install compizconfig-settings-manager
```

Under the General -> General Options -> Display Settings enable sync to VBlank and make sure under the main tab that 'unredirect fullscreen windows is unchecked.

While there maybe set the refresh rate to what is actually being used.

Sometimes also useful to go to the 'Utility', and disable the 'Workarounds' and enable 'Video Playback'

---

### Post by aquarat on 2011-05-24
This helped me, thank you!

---

### Post by mc4man on 2011-05-24
> **aquarat said:**
> This helped me, thank you!

While I don't see tearing that often with nvidia in 10.10 & 11.04 - running a test file can say that there will Always be some tearing w/ nvidia and compiz 
The only way to truly eliminate here is to run with no effects (metacity), and disable compositing in an xorg.conf section

```
Section "Extensions"
Option "Composite" "disable"
EndSection

```

I guess it comes down to whether noticeable or not  - 
Am going to be curious to see how gnome-shell with mutter performs on 11.10 in this regard

---

