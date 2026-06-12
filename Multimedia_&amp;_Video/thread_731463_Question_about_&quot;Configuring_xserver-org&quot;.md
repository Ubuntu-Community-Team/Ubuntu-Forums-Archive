---
title: "Question about &quot;Configuring xserver-org&quot;"
date: 2008-03-21
forum: Multimedia &amp; Video
---

### Post by Thrasonic on 2008-03-21
I'm trying to get my video card and resolution worked out and am frequently having to do the whole "sudo dpkg-reconfigure xserver-xorg" command to fix my xorg.conf file when I break it.  FYI, I have an PCIe x16 ATI Radeon X1600 w/512 MB RAM.  I have a few questions about some of the screens during that process.

About the 3rd screen in it asks me to choose a X server driver.  It always defaults to vesa.  I've tried Radeon, ATI, and fglrx and none of them have worked.  Any other ideas from this screen?

About the 5th screen in it talks about specifying the BusID.  The next screen, screen 6, defaults to PCI:3:0:0.  How do I find out if this is accurate or if I should be changing this?  Who knows, maybe this is my problem?

On the next screen, screen 7, it asks how much memory in kB is to be used by my video card.  It's a 512 MB card so I always put 512000.  Any problems with that?

On the next screen, screen 8, it asks if I want to use kernel framebuffer device interface.  I always go with the default, No.  Any problems with that?

Even further in it correctly identifies my monitor, a Westinghouse LCM-22w2 (22" wide screen with a preferred resolution of 1680x1050 @ 60 Hz) and makes all of the resolutions available on the next screen.  Than it gets into the Simple, Medium, and Advanced settings for selecting monitor characteristics.  I've tried all three (simple, medium, and advanced) to no avail.

I'm just looking at this time for answers to the questions I've asked.  Once I have those I feel I might be able to resolve my issue (never being able to get my resolution above 1280x1024).  I'd appreciate any help with the questions I've posted.  Thanks.

---

### Post by Thrasonic on 2008-03-22
bump

---

### Post by Thrasonic on 2008-03-22
bump

---

### Post by unutbu on 2008-03-22
What is your current state? Does X work for you at all, or are you being thrown to the command line?

---

### Post by Thrasonic on 2008-03-22
> **unutbu said:**
> What is your current state? Does X work for you at all, or are you being thrown to the command line?

Thanks for the reply, unutbu.  I do have a desktop environment.  X is working.  What happens is that I try to change it to use my ATI card (so I can have a higher resolution) and that ends up breaking it.  So I boot into recovery mode and run "sudo dpkg-reconfigure xserver-xorg" and just go with all the defaults.  That brings my display back up.

---

### Post by unutbu on 2008-03-22
I was recently told that 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

will ask fewer questions than without the -phigh flag. It will ask for your desired resolution though. Perhaps give that a try.

---

### Post by Thrasonic on 2008-03-22
> **unutbu said:**
> I was recently told that 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

will ask fewer questions than without the -phigh flag. It will ask for your desired resolution though. Perhaps give that a try.

Well, I tried it but it didn't help.  Any other ideas?  Anyone?

---

