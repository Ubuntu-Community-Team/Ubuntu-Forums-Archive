---
title: "Sony Vaio laptop and Fn key brightness"
date: 2010-10-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by coffeecat on 2010-10-01
I know that different model Vaios use different implementations for their Fn keys, but are there any Vaio laptop owners testing Maverick?

When I bought this Vaio VGN-NS20S last year I installed Jaunty and was pleasantly surprised to find that the Fn keys for sound volume and brightness worked out of the box. My previous now nearly 6-year old Vaio required some serious hacking to get the Fn keys to work.

Karmic came and went on it with the Fn keys still working, and they still worked in Lucid. I've been testing Maverick on my other (Acer) laptop and have only just installed Maverick on the Vaio with the RC live CD. I find that the Fn key combinations for brightness don't work, but those for audio do. A disappointment and a regression for me.

The gnome panel brightness applet does work, except for an odd little glitch with mouse control. So - calling Vaio owners. What model do you have and what is your experience?

---

### Post by Quackers on 2010-10-01
For my Vaio Lucid and Meerkat have the same responses. The eject button works only if there is a disc in the drive - not when empty. The volume and mute buttons work. Fn + F5 or F6 do nothing (should be brightness). I don't know if S1 or S2 work because they are not allocated a function. The AV mode button works even though the TV card doesn't.

---

### Post by tjeremiah on 2010-10-01
My model is in my sig. I started with the beta of Ubuntu 10.10 since the beginning and I can say, the FN Key for brightness has not worked. Also, sometimes the keyboard would start acting up not allowing me to space my letters. Im sure its a Kernel issue, I just dont know what Kernel would solve the issues.

---

### Post by taavikko on 2010-10-02
Vaio (VPC)F11S1E
Brightness controls don't work.

---

### Post by NightwishFan on 2010-10-02
Try booting with acpi_backlight=vendor as a kernel parameter. If you do not know how, you have to hold shift, highlight your kernel, press E, find the line that ends in "quiet splash" append a space, then the above parameter.

---

### Post by pasa on 2010-10-02
i have same problem with my sony(vgn-fw21e). if i change it with vendor , i cant change brightness anyway.  But now only fn+f5 and Fn+f6 doesnt work and vendor doesnt work for me.

Powercontrol and brightness control work great , only keys doesnt work on maverick.


Ps: i open new bug report  about open brightness control. 

Bug link;

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/653473](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/653473)

---

### Post by coffeecat on 2010-10-02
I've discovered that this is a kernel issue, but more below.

I'm sorry that no one reported their experiences on earlier versions of Ubuntu or other distros. This is important. As I said before, Sony's implementation of acpi varies - they have different versions. It seems that in Lucid and Karmic some Sony Vaio models worked fine, but other didn't. So if you have this problem, it may be for a different reason than mine. So that I am clear about this, I have done some more tests with different distros. On my VGN-NS20S, the function key combinations are:

Fn+F2 = mute
Fn+F3 = volume down
Fn+F4 = volume up
Fn+F5 = brightness down
Fn+F6 = brighntess up
Fn+F12 = hibernate

There is also Fn+F7 to toggle between laptop screen, external monitor and both which I've never bothered to test in Linux. And Fn+F9 and Fn+F10 for zoom out and in which only work in some apps in Vista anyway. :rolleyes:

I have Karmic and Fedora 13 as well as Maverick installed on this Sony and all the first six Fn key combinations work in those two. I booted into the Lucid live CD to double-check and the first five Fn key combinations work. Obviously, I couldn't check hibernation. Out of interest, I tried the live CDs for the gnome versions of Opensuse 11.3 and PCLinuxOS. Suse works as Lucid does and in PCLinuxOS, perversely, the brightness key-combinations work but not the sound ones.

> **NightwishFan said:**
> Try booting with acpi_backlight=vendor as a kernel parameter. If you do not know how, you have to hold shift, highlight your kernel, press E, find the line that ends in "quiet splash" append a space, then the above parameter.

Thanks - good idea, but unfortunately it doesn't work on this model. So that you don't have to edit the kernel line every time, you can edit /etc/default/grub so that the GRUB_CMDLINE_LINUX line reads:

```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```

After which you need to run 'sudo update-grub'.

Anyway, it's a kernel issue. I've installed the latest Lucid kernel (2.6.32-25-generic) and I'm posting from Maverick running the Lucid kernel. The Fn+F5 and Fn+F6 combinations now work just fine. This is clearly not a satisfactory fix - the Maverick 2.6.35 kernel needs attention - so I'll see if I can get a bug report filed.

To all of those who said that the brightness keys don't work, what happens in Lucid? Run the live CD if you need to.

---

### Post by AlanR8 on 2010-10-02
Vaio VGN-FZ21S

The media keys work well and have done since Jaunty. The brightness controls F5-F6 never worked until I installed Maverick so I was quite impressed until I installed the recommended Nvidia driver that blew out the brightness controls.....

Bugger

---

### Post by coffeecat on 2010-10-02
> **AlanR8 said:**
> Vaio VGN-FZ21S

The media keys work well and have done since Jaunty. The brightness controls F5-F6 never worked until I installed Maverick so I was quite impressed until I installed the recommended Nvidia driver that blew out the brightness controls.....

Talk about ymmv. :|

If you are not gaming and just want a few gee-whiz compiz effects, you can do so with the nouveau driver in Maverick with this useful tip:

[http://ubuntuforums.org/showpost.php?p=9904532&postcount=2](http://ubuntuforums.org/showpost.php?p=9904532&postcount=2)

**Edit:** I'm making an assumption about gaming. Tbh, I don't know, but I was impressed to get wobbly windows and a rotating cube with the nouveau driver in Maverick on a desktop machine.

---

### Post by joop! on 2010-10-02
Although the site is dedicated to a different vaio model, you could try the solutions from [http://code.google.com/p/vaio-f11-linux/wiki/DisplayBacklight](http://code.google.com/p/vaio-f11-linux/wiki/DisplayBacklight)

---

### Post by AlanR8 on 2010-10-02
In fairness the brightness controls do not excite me much. I'd much rather the Motion Eye web cam worked straight out the box! There's another thread elsewhere on this forum about this issue but with a little effort all is well.

The key words there were a "little" and "effort". One of the last times I reinstalled XP on the wife's Dell it took 6 hours to install and get all the drivers installed. A couple of days later she asked why she couldn't play videos. Had to go get the codecs!

WHAT A DISASTER. And that was only about 2 years ago.

She now runs an iMac and in the main gets on OK with it.

---

### Post by deaffob on 2010-10-04
SZ680N Brightness buttons don't work either since 10.10RC

---

