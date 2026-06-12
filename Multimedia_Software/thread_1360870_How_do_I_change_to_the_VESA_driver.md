---
title: "How do I change to the VESA driver?"
date: 2009-12-21
forum: Multimedia Software
---

### Post by Talon2 on 2009-12-21
I need to be able to change a system from the Intel video driver to the VESA driver.  How do I do this?

Problem:  The Intel video driver is still problematic with some older chipsets.  See [here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel?field.searchtext=&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=")

TIA

---

### Post by HappyFeet on 2009-12-21
Go to /etc/X11/xorg.conf and in the "device" section, change intel to vesa.

---

### Post by Talon2 on 2009-12-21
> **HappyFeet said:**
> Go to /etc/X11/xorg.conf and in the "device" section, change intel to vesa.

xorg.conf doesn't exist on my system (Ubuntu 9.10).

I used to use the method you suggested but there have been a lot of changes in the video subsystem.

---

### Post by Melcar on 2009-12-21
Drop to command prompt mode, stop gdm from running, and run:

```
sudo Xorg -configure
```

You can also boot into safe mode and simply drop to a root command prompt, and perform the above command.
The command generates a file named xorg.conf.new and drops it inside your root folder.  Open the file for editng:

```
sudo nano /root/xorg.conf.new
```

You can safely remove everything in the file.  Leave the sections you want to change.  In your case leave the "Device" section and change the driver to vesa (it should be intel by default).  Save the file as *xorg.conf* and move it to your /etc/X11/ folder:

```
sudo mv /root/xorg.conf /etc/X11/xorg.conf
```

Reboot the machine.

---

