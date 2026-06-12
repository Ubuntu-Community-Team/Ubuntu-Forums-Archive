---
title: "Gnome Display recognise same refresh rate as nVidia server?"
date: 2010-01-04
forum: Multimedia Software
---

### Post by Don Scapp on 2010-01-04
Is it possible to have gnome's display settings recognise higher refresh rates than 56hz, as my nvidia is set to 85hz, but gnome display still thinks its 56hz, and I believe this is causing many programs I'm using to refresh at 56hz. Compiz works beautifully after overriding the refresh rate inside it, as it too thought I was using 56hz instead of 85 but many games aswell as CairoDock as jerky, which makes me think it is a refresh issue.

How can I make gnome know I'm using 85hz?

---

### Post by Don Scapp on 2010-01-05
I'm wondering if it may be a Xorg.conf problem, but I'm not sure what to put in the conf file to make gnome run at 1024x768 at 85hz - I've searched the forums for a similar problem, but nobody seems to have had this happen?

---

### Post by realzippy on 2010-01-05
Think that GNOME &#8222;Screen Resolution Preferences&#8220; panel has wrong infos when running NVIDIA driver.To see your current refresh rate,type:

**nvidia-settings --query RefreshRate**

---

### Post by Don Scapp on 2010-01-05
Thanks, I believe it is runnings okay as my eyes dont hurt, and my monitor tells me the refresh in its menu, but some 2d games run jerky (3d ones are smooth) and all the dockbars were jerky, whereas in any distro that has nvidia AND the native display dialog says 85hz, 3d games and dockbars are smooth and non-jerky. Can I make it say the right info?

---

### Post by Don Scapp on 2010-01-07
Sorry to bump, but I'd like to know if there are any commands/conf edits that will add extra refresh rates to gnome display when I have nVidia drivers running?

---

### Post by Don Scapp on 2010-01-08
Fixed!! The secret, is to add this line to the screen scetion of your xorg.conf file.

> Option   "DynamicTwinView"   "False"

That'll make the display show as 85hz if you are running at 85hz like I am.

---

