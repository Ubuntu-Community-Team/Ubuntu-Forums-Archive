---
title: "MonacoOPTIX not initializing under dispcalGUI"
date: 2011-08-23
forum: Multimedia Software
---

### Post by rebeltaz on 2011-08-23
I just got a MonacoOPTIX colorimeter, and I wanted to try it out. So I installed argyll 1.1.0-5, dispcalGUI 0.7.3.7 and gnome-color-manager 2.3.0-0. I plugged in the colorimeter, started dispcalGUI and the colorimeter was recognized in the drop-down list of devices as "i1 Display." I clicked on [Calibrate Only] then [Calibrate Only] (instead of [Create Profile Matrix]) and then [Start Measurement]. A terminal window pops up, too quickly for me to read, and then pops up the following error:

```
dispcal: Error - Configuring USB port 'usb:/bus0/dev4 (GretagMacbeth i1 Display)' to 1 failed with -71 (could not set config 1: Protocol error)
```

Can someone tell me why? and how to fix it? Thanks...

---

### Post by gesti on 2011-10-04
hello rebeltaz,

in **dispcalGUI** there is a **Show Log** option in **Tools menu**. This will show you the error from the console. (It probably will be the same error message that pops up for you after wards.)
See if this fixes it:

[LIST=1]
[*]Plug your colorimeter in
[*]Start dispcalGUI from terminal as root ( # sudo dispcalGUI )
[*]Try to get your measurement.
[/LIST]
Hope it will help.

PS: I can't see this MonacoOPTIX on the [supported hardware list here]("http://www.argyllcms.com/doc/ArgyllDoc.html"). Are you sure that your colorimeter supported by ArgyllCMS?

---

### Post by rebeltaz on 2011-10-27
I re-downloaded the latest versions of both software and that seems to have dome the trick. Thanks...

---

