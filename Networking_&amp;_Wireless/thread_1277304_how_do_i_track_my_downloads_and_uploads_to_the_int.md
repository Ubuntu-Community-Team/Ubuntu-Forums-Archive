---
title: "how do i track my downloads and uploads to the internet"
date: 2009-09-28
forum: Networking &amp; Wireless
---

### Post by jarrah-95 on 2009-09-28
i have been looking for a download tracker for about a week (mainly serching this forum and googleing) but have not succeded.
is there any program that i can use to track the amount of data i have downloaded and uploaded.

---

### Post by badger_fruit on 2009-09-28
> **jarrah-95 said:**
> i have been looking for a download tracker for about a week (mainly serching this forum and googleing) but have not succeded.
is there any program that i can use to track the amount of data i have downloaded and uploaded.

Depends how you connect to the internet; if you go through a router then you can use it's status pages to tell you the amount of data pushed and pulled through the internet port although usually, this is a total since last reboot so no good if you want to monitor without rebooting to reset the counter.

If your router supports SNMP then you can hook into that using various tools (consult the user guide of your router to confirm if it has SNMP on it).

---

### Post by jarrah-95 on 2009-09-30
thanks but im using wireless broadband with plugs straght into the computer via usb so the tracker needs to be on the computer

---

### Post by badger_fruit on 2009-09-30
> **jarrah-95 said:**
> thanks but im using wireless broadband with plugs straght into the computer via usb so the tracker needs to be on the computer

In that case, ask google for "linux bandwith useage monitor"

---

### Post by jarrah-95 on 2009-10-01
ok thanks ive got it vnstat does it perfictaly with the command ```

vnstat -m

```

---

