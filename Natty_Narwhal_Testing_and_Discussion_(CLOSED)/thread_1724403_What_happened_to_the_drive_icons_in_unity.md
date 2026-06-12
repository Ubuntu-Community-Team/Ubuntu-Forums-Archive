---
title: "What happened to the drive icons in unity?"
date: 2011-04-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by psusi on 2011-04-08
Earlier in the development cycle when I installed lvm2 on the livecd, icons for each of my logical volumes showed up in the unity panel.  This seems to have gone away.  Why?  I liked that.

---

### Post by macroshaft on 2011-04-08
> **psusi said:**
> Earlier in the development cycle when I installed lvm2 on the livecd, icons for each of my logical volumes showed up in the unity panel.  This seems to have gone away.  Why?  I liked that.

They have now been replaced by the files and folders icon (magnifying glass with a file icon inside it)

---

### Post by MacUntu on 2011-04-08
Run dconf-editor and go to 'desktop/unity/devices'. There's a key devices-option that lets you decide whether you want devices, only mounted devices, or no devices in the launcher bar.

---

### Post by mc4man on 2011-04-08
As far as internal partitions (drives), it's an option - the default has been changed to 'OnlyMounted'
If this is what you are referring to it can be changed in dconf-editor or gsettings in a limited fashion
> ~$ gsettings range com.canonical.Unity.Devices devices-option
enum
'Never'
'OnlyMounted'
'Always'

```
gsettings set com.canonical.Unity.Devices devices-option Always
```

---

### Post by psusi on 2011-04-08
Ahh, nifty!

---

### Post by mc4man on 2011-04-08
A nice addition down the road would be to set an option individually based on something, maybe volume label, time will tell...

---

