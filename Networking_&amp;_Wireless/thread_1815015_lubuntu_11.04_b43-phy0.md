---
title: "lubuntu 11.04 b43-phy0"
date: 2011-07-30
forum: Networking &amp; Wireless
---

### Post by edadasiewicz on 2011-07-30
I have been trying to run the lubuntu 11.04 live cd from my laptop (HP zd7000A) and it will not boot into the graphical portion.  I get the initial lubuntu graphic with the 5 blinking dots but eventually it drops into command line mode with the errors:

b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found

I get the same error if I try to install lubuntu rather than just run it.  I have even disabled wireless in the bios and plugged the laptop into my router but still get the same error.  Note that I do have the latest xubuntu already installed on the laptop with no wireless problems.  All I really wanted to do was try out lubuntu.  Any ideas?  Thanks.

---

### Post by wildmanne39 on 2011-07-30
Hi, more then likely you need to use a nomodeset parameter to be able to boot up here is a link for that.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Probably a video card issue.

---

### Post by edadasiewicz on 2011-07-30
I'm beginning to thank that there is either some parameter of which I am unaware or something wrong with the .iso file -- I have downloaded it twice.  I just tried the CD on a desktop (no wireless) and although it did not give any errors about b43, it eventually dropped into command line mode and entering startx threw all sorts of errors.

---

### Post by wildmanne39 on 2011-07-30
Hi, you will need to use that link I gave you in my previous post, then let us know if it worked.
Thank you

---

### Post by edadasiewicz on 2011-07-30
Sorry about the previous post, I was entering it at the same time you were responding.  You were correct, the nomodeset allowed it to boot into the graphical portion.  The b43 error was still there but I can get around that later.  There is probably something similar for the desktop.  I should start paying more attention to bottom of the live CD boot screens.

Thanks much for the *quick* response.

---

### Post by nm_geo on 2011-07-30
> **edadasiewicz said:**
> Sorry about the previous post, I was entering it at the same time you were responding.  You were correct, the nomodeset allowed it to boot into the graphical portion.  The b43 error was still there but I can get around that later.  There is probably something similar for the desktop.  I should start paying more attention to bottom of the live CD boot screens.

Thanks much for the *quick* response.

That error has to do with your wireless card needing firmware downloaded and installed.  As long as you are using the live/CD and ethernet cable it means very little.  If you decide to install the OS it will help identify you wireless driver and firmware needed.

Looking at the error we can see that you have a Broadcom wireless probably BCM4311 or 4312..

---

### Post by wildmanne39 on 2011-07-30
Hi, your welcome! When you have ubuntu installed you will need to use the nomodeset to get into ubuntu, then go to additional drivers and see if there is a driver for your video card there if so install it then restart your computer and it will most likely boot fine,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

If you have more trouble you should most in the general section or absolute beginners section unless it is a wireless issue then post that here.

You may have to install wireless drivers depending on your system.
Thank you

---

### Post by calavicci on 2012-07-25
A little late, but for anyone still troubled by this:

nm_geo is correct. It is NOT a video card issue. The problem is that the b43 driver for the Broadcom wireless needs code from Broadcom's proprietary firmware. The fact that this halts the boot process is just bad OS design.

When the LiveCD presents the boot prompt, boot with 
```

boot: live modprobe.blacklist=b43

```to prevent the b43 module from loading, erring out, and halting the boot. The wifi will be unavailable, but at least the OS will load. If you can get networking via some other hardware, e.g. ethernet, then you can use the instructions and downloads here: [http://linuxwireless.org/en/users/Drivers/b43/](http://linuxwireless.org/en/users/Drivers/b43/) to get wifi working.

If this does not work for you, you may need to use
```

boot: live modprobe.blacklist=b43legacy

```instead. VERY old OS versions may need
```

boot: live modprobe.blacklist=bcm43xx

```HTH.

---

### Post by wildmanne39 on 2012-07-25
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

