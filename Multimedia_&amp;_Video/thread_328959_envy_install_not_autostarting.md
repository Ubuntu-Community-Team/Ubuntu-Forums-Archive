---
title: "envy install not autostarting"
date: 2006-12-31
forum: Multimedia &amp; Video
---

### Post by dan_mcdonald on 2006-12-31
Hi all,

I'm having problems getting the nvidia driver to startup when I log in. I can find the server app under applications>system tools and when I click on the app the configuration starts but not until then. The thing that tips me off that it's not working is that I have "digital vibrance" set in the app and the wallpaper color jumps out once I start the app but not before. 

The xorg.conf file was not matching the app version so I replaced it but it didn't help. Any help please!

Thanks,

Dan.

---

### Post by tseliot on 2006-12-31
> **dan_mcdonald said:**
> Hi all,

I'm having problems getting the nvidia driver to startup when I log in.
I'm sure the nvidia driver is being loaded at boot otherwise you might see a black screen

> **dan_mcdonald said:**
> I can find the server app under applications>system tools and when I click on the app the configuration starts but not until then. The thing that tips me off that it's not working is that I have "digital vibrance" set in the app and the wallpaper color jumps out once I start the app but not before. 

The xorg.conf file was not matching the app version so I replaced it but it didn't help. Any help please!

I think you're talking about nvidia-settings.

Try launching it with sudo:
```
sudo nvidia-settings
```

and configure the digital vibrance or whatever you need. Then save the file and exit.

---

### Post by dan_mcdonald on 2007-01-01
Hi Alberto,

Thanks for your reply. You are right, the driver is loading (the nvidia splash screen comes up)  but the settings for digital vibrance won't work from xorg.conf.  That is the bootup file isn't it?

It was suggested that I manually add this line  to xorg.conf:

Option         "DigitalVibrance" "40"

and it made no difference. Is it possible that the app can modify settings that xorg.conf can't? Should I look into the EDID.BIN file?

Thanks,

Dan.

---

### Post by dan_mcdonald on 2007-01-01
Oh, I should mention that I did as you suggested but it didn't work.

Dan

---

