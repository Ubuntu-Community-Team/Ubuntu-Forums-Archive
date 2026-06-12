---
title: "Changing Load Screen Resolution"
date: 2008-05-22
forum: Multimedia Software
---

### Post by MatthewPlanchard on 2008-05-22
Hello!

Okay, I remember doing this once to fix a problem with the loading screen (Ubuntu logo and progress bar) going black upon logging in in Gutsy.

With the Heron upgrade, the login screen is now huge and off-centered.

Which file can I edit to adjust the resolution of the login screen?

thanks!

---

### Post by mc4man on 2008-05-22
post your xorg.conf, many times this can be fixed from there (not always)

---

### Post by wootah on 2008-05-22
Hey there!

If you are referring to the loading screen that displays the Ubuntu Logo and the progress bar that appears before you can login, then the change needs to be made in _/boot/grub/menu.lst_. If the logo is off centre, too large, or you can't read the text, then we need to configure a [kernel boot option]("https://help.ubuntu.com/community/BootOptions#head-e95c9e129e9eb9fca524fe278cd57fcdb39db62d"), but don't worry because it's wicked simple!

You need to edit the /boot/grub/menu.lst using anything you like, nano, gedit, whatever. The permissions on this file are root:root, 644 so you will need to use sudo for nano or gksudo for gedit. **Before you start, make sure you backup menu.lst**!

Find the the following lines:
```

<snip>
## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
**kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=df1efe7b-4feb-4dc9-bf44-4bb294cffc18 ro splash**
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

```
We are interested in the kernel line. Here we need to append an option called **vga**. See [http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers]("http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers") to view the correct number to use. Ex: for 1280x1024 @ 24 bit we use **795 **or for 1024x768 @ 24 bit we use **792**. All we have to do is append vga=*<number>*:
```

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=df1efe7b-4feb-4dc9-bf44-4bb294cffc18 ro splash [COLOR="Red"]vga=792[/COLOR]
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

```

Save your changes and reboot! After setting it to the correct number, things should be ok!

Good luck, and **don't forget to backup your menu.lst before hand**!

---

### Post by MatthewPlanchard on 2008-05-22
Thanks, that worked perfectly. I ended up using 352 for 1280x800. At first I didn't see it on the list, to my dismay, but then discovered it hiding in the footnotes.

Thanks again.

---

### Post by wootah on 2008-05-22
Glad I could help! Mark thread as solved ?

---

