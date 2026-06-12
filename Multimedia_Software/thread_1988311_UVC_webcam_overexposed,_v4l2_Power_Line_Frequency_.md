---
title: "UVC webcam overexposed, v4l2 Power Line Frequency setting"
date: 2012-05-27
forum: Multimedia Software
---

### Post by belgianfries on 2012-05-27
Hello,

The internal UVC webcam of my Lenovo ThinkPad L420 overexposes in bright outdoor light in applications like Cheese, Kamerka and Skype.

I played with brightness and exposure related settings in v4l2ucp without success, until I changed the Power Line Frequency setting from "60 Hz" to "Disabled". With this setting, the exposure works fine in bright outdoor light, while in indoor artificial light, exposure is unchanged and works still well.

The problem is, that if I close the application (i.e. Cheese) and start it again, exposure is still fine, but after about a second it is overexposing again. The Power Line Frequency setting is still on "Disabled" (at least v4l2ucp says so), so I have to set it to "60 Hz" and again to "Disabled" to apply the setting.

Do applications like Cheese reset all v4l2 settings when they start up? And if so, why is Power Line Frequency still on "Disabled"?

Is there a way to permanently set the default of Power Line Frequency to "Disabled"? I think the default is "60 Hz".

Cheers,
Torsten

---

