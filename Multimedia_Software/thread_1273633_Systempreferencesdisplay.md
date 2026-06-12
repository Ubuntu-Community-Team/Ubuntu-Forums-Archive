---
title: "System/preferences/display"
date: 2009-09-23
forum: Multimedia Software
---

### Post by SantaFe on 2009-09-23
I have ubuntu 9.04 installed and it has the nvidia driver 180-44 installed.

I go to System/preferences then click display I get a box that says:

It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?

So I say yes and the nvidia X server settings comes up and I choose X server display configuration.

I pick X Screen and since I just want to go from 16.7 million colors to 65536 colors I click on it.  Then I click Apply and I get:

The current settings could not be completely applied due to one or more of the following reasons:

1. The location of an x screen has changed.
2. The location type of an x screen has changed.
3. The color depth of an x screen has changed.
4. An x screen has been added or removed.
5. Xinerama isbein enabled/disabled.

Then it mentions to save the configuration to the x config file and restart the x server.  The it gives two buttons, one says apply what is possible and the other is cancel.

Doesn't matter which I choose, I tried apply, then I tried the button to save the configruartion, but it errors out on me and I'm stuck at 16.7 million colors.

I've tried to re-install the nvidia drivers.  But no difference.

What do I need to do?

Thanks.

---

### Post by SantaFe on 2009-09-25
No ideas?  Anyone? :confused:

---

### Post by CatKiller on 2009-09-25
> **SantaFe said:**
> I tried the button to save the configruartion, but it errors out on me

run ```
gksudo nvidia-settings
``` so that you have the ability to write to xorg.conf.

---

