---
title: "Mythtv ACPI automatic wakeup/shutdown how-to"
date: 2024-01-30
forum: Multimedia Software
---

### Post by vidtek on 2024-01-30
I have spent many hours on this after updates kept breaking this function.  The polkit changes are the ones that had me tearing out my hair.   Many thanks to the Archwiki community for their polkit page.


Notes on setting up Kubuntu Jammy with mythtv ACPI auto shutdown.

**1)** Go to here and read it all:[https://www.mythtv.org/wiki/ACPI_Wakeup]("https://www.mythtv.org/wiki/ACPI_Wakeup") ensure you have the files: setwakeup.sh and checklogin.sh in your ***/usr/sbin ***directory.    The contents can be found in this webpage.  

**2)** Once ACPI is working with the quick test detailed in the website above then enter mythtv-setup and set the mythtv shutdown/wakeup to the settings in the screenshot attached.

**3)**To ensure you have the correct permissions edit the sudoers file to include this line:
```
%mythtv ALL=NOPASSWD: /usr/sbin/setwakeup.sh, /usr/sbin/checklogin.sh, /usr/sbin/mythshutdowncheck.sh, /bin/systemctl, /usr/sbin/rtcwake, /sys/class/rtc/rtc0/wakealarm
```
Edit this file **ONLY** by opening a terminal and entering: sudo visudo

**4)**To ensure the system allows the shutdown sequence add this file to the *etc/polkit-1/rules.d/10-disable-suspend.rules*
Create the directories if necessary and add these contents to the file: 
```
#/etc/polkit-1/rules.d/10-disable-suspend.rules

polkit.addRule(function(action, subject) {
    if (action.id == "org.freedesktop.login1.suspend" ||
        action.id == "org.freedesktop.login1.suspend-multiple-sessions" ||
        action.id == "org.freedesktop.login1.hibernate" ||
        action.id == "org.freedesktop.login1.hibernate-multiple-sessions")
    {
        return polkit.Result.YES;
    }
});
```

Credit: [https://wiki.archlinux.org/title/Polkit]("Credit: https://wiki.archlinux.org/title/Polkit")

---

