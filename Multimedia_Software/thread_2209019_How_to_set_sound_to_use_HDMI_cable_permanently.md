---
title: "How to set sound to use HDMI cable permanently"
date: 2014-03-03
forum: Multimedia Software
---

### Post by jr223 on 2014-03-03
Greetings All,

I have hooked up and Flat screen 37" TV to my ubuntu 13.10 MiniPC using HDMI cable.
Every time the PC is shut down and rebooted I have to go into the Sound control and reset it to HDMI.
Is there a configuration file that I can set to keep this setting or do I need another app to keep this setting?

Thanks
Cheers

---

### Post by Vladlenin5000 on 2014-03-03
I never had to do that, just selected once the OS and the nvidia drivers were installed and that was it. However, I don't have any other audio devices connected to the onboard sound card. Don't know if it matters but probably not.

---

### Post by frank18 on 2014-03-03
> **jr223 said:**
> Greetings All,

I have hooked up and Flat screen 37" TV to my ubuntu 13.10 MiniPC using HDMI cable.
Every time the PC is shut down and rebooted I have to go into the Sound control and reset it to HDMI.
Is there a configuration file that I can set to keep this setting or do I need another app to keep this setting?

Thanks
Cheers

Upgrade To Ubuntu 14.04

---

### Post by Yellow Pasque on 2014-03-04
Upgrading won't magically change the default sound device.

Show output of:
```
pacmd list-sinks
```

---

