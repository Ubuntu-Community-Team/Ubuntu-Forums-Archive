---
title: "Belkin F5D7001uk"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by yogiman_uk on 2010-02-26
Hello Everyone

I am somewhat puzzled. I have a pc with a Belkin F5D7001uk card installed.

When I boot from the live CD 9.04 (9.10 not working) the wireless card is detected and I am offered restricted drivers to use with it, if I select them and give it a wireless key it works perfectly.

However when I actually install 9.04 onto the machine and reboot it does not offer me the restricted driver and so the card does not work.

A similar thing happens on a different machine with an NVIDIA video card and I am offered restricted drivers live and installed which again makes the Belkin problem even more odd.

Can anyone help me with this problem?

Thanks


Yogiman!

---

### Post by yogiman_uk on 2010-02-26
> **yogiman_uk said:**
> Hello Everyone

I am somewhat puzzled. I have a pc with a Belkin F5D7001uk card installed.

When I boot from the live CD 9.04 (9.10 not working) the wireless card is detected and I am offered restricted drivers to use with it, if I select them and give it a wireless key it works perfectly.

However when I actually install 9.04 onto the machine and reboot it does not offer me the restricted driver and so the card does not work.

A similar thing happens on a different machine with an NVIDIA video card and I am offered restricted drivers live and installed which again makes the Belkin problem even more odd.

Can anyone help me with this problem?

Thanks


Yogiman!

Hi Again

Solved the problem myself.

Run the live CD.

When You have a desktop make sure you have a wired connection and that it is working.

Goto System

Admin - Hardware Drivers

You should now see the broadcom restricted driver listed.

Select and active it.

Then click your wireless connection and select your router.

Enter the WPA key.

Once installed and running, install the live CD to your pc.

When the install completes you should now find that it identified the card during installation and it is now available to set-up the same way you set it up when booting live.

Regards

Yogiman!

---

