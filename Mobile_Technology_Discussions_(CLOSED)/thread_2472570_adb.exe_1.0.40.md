---
title: "adb.exe 1.0.40"
date: 2022-03-04
forum: Mobile Technology Discussions (CLOSED)
---

### Post by johnaaronrose on 2022-03-04
Ubuntu 20.04 sees phone with Linux adb v28 using 'adb devices'.
I've installed the usb driver for my Blackview A80 phone in VirtualBox  Windows 10 VM. However, VirtualBox Windows 10 VM fails to see my phone  with adb (v1.0.32 & 1.0.39). I'd like to download adb.exe v1.0.40  (as that's the requirement to run B4A Windows app under Wine in  Ubuntu.). But I can't find that version anywhere. Has anyone got adb.exe  v1.0.40?
I've followed the instructions on
[http://adbcommand.com/articles/How to build adb(1.0.40) for windows on Ubuntu]("http://adbcommand.com/articles/How%20to%20build%20adb%281.0.40%29%20for%20windows%20on%20Ubuntu") but I get 'fatal: cannot make .repo directory: Permission denied' on the step
repo init -u [https://android.googlesource.com/platform/manifest](https://android.googlesource.com/platform/manifest). I know nothing about repo. Anybody have any ideas about this repo problem?

---

### Post by mIk3_08 on 2022-03-04
> **johnaaronrose said:**
> Ubuntu 20.04 sees phone with Linux adb v28 using 'adb devices'.
I've installed the usb driver for my Blackview A80 phone in VirtualBox  Windows 10 VM. However, VirtualBox Windows 10 VM fails to see my phone  with adb (v1.0.32 & 1.0.39). I'd like to download adb.exe v1.0.40  (as that's the requirement to run B4A Windows app under Wine in  Ubuntu.). But I can't find that version anywhere. Has anyone got adb.exe  v1.0.40?
I've followed the instructions on
[http://adbcommand.com/articles/How to build adb(1.0.40) for windows on Ubuntu]("http://adbcommand.com/articles/How%20to%20build%20adb%281.0.40%29%20for%20windows%20on%20Ubuntu") but I get 'fatal: cannot make .repo directory: Permission denied' on the step
repo init -u [https://android.googlesource.com/platform/manifest](https://android.googlesource.com/platform/manifest). I know nothing about repo. Anybody have any ideas about this repo problem?
Have you tested apt adb via terminal? I think you should try it or try apt search via terminal. If you can't see any try install package manager maybe you can add it easily on package manager. Good Luck and cheers.

---

### Post by mIk3_08 on 2022-03-06
> **johnaaronrose said:**
> Has anyone got adb.exe  v1.0.40?
I've followed the instructions on
[http://adbcommand.com/articles/How to build adb(1.0.40) for windows on Ubuntu]("http://adbcommand.com/articles/How%20to%20build%20adb%281.0.40%29%20for%20windows%20on%20Ubuntu") but I get 'fatal: cannot make .repo directory: Permission denied' on the step
repo init -u [https://android.googlesource.com/platform/manifest](https://android.googlesource.com/platform/manifest). I know nothing about repo. Anybody have any ideas about this repo problem?

You do not need to do this. Android Debug Bridge is already available in Linux. You can just then install it directly. Good Luck and Cheers.

---

### Post by johnaaronrose on 2022-03-07
All versions of adb.exe on both VirtualBox Windows 10 VM & somebody's else's box)  but got Linux to see phone by using SDK files that somebody else pointed  me to.

---

### Post by mIk3_08 on 2022-03-07
As what I have said, adb (Android Debug Bridge) is already available in Linux. you can now install it via apt and also (android-sdk-platform-tools-common) is also available here in Linux Ubuntu Operating System. so, Good Luck and Regards.

---

