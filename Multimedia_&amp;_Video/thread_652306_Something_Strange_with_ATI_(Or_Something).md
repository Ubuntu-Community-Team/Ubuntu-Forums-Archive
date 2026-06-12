---
title: "Something Strange with ATI (Or Something)"
date: 2007-12-28
forum: Multimedia &amp; Video
---

### Post by teejay17 on 2007-12-28
I have an ATI Radeon x850 XT Platinum Edition video card. Strangely, when I install the Restricted driver for ATI, I can't get the "Extra" video effects to work; instead, I get a message saying that these effects will not work. However, when I uninstall the Restricted driver, these effects work like a charm. 
But...when I don't have the Restricted driver enabled, I can't really get 3D effects in the screen savers, or on the desktop Gdesklets, but the "extras" work no problem natively in Ubuntu.  
Does anyone know why this might be so? Conversely, is there a way to have both the Ubuntu "extras" work, and the 3D stuff in the screen savers and Gdesklets?

---

### Post by teejay17 on 2007-12-28
Anyone?

---

### Post by teejay17 on 2007-12-29
Yeah, basically as soon as I install the restricted driver, I am told that "the composite extension is not available." 
I'd sure like to get those visual effects back. Ideas, anyone?

---

### Post by erfahren on 2007-12-29
it sounds like to run the desktop effects with the restricted driver you just need to install xgl 

the ATI proprietary driver (fglrx) doesn't support compositing on its own

you could try installing the newer version of the driver if you want to get into that (it doesn't need xgl)
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by teejay17 on 2007-12-29
> **erfahren said:**
> it sounds like to run the desktop effects with the restricted driver you just need to install xgl 

the ATI proprietary driver (fglrx) doesn't support compositing on its own

you could try installing the newer version of the driver if you want to get into that (it doesn't need xgl)
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
Would I just install the "xserver-xgl" package in Synaptic, then, to make this work?

---

### Post by erfahren on 2007-12-29
oh, yeah "xserver-xgl" is the package name. sorry! that's the one you want.

note: if you ever need to disable xgl (for whatever reason) just make the (empty) file "~/.config/xserver-xgl/disable"

so in terminal:
```

touch .config/xserver-xgl/disable

```

---

### Post by lavinog on 2007-12-29
The restricted driver is blacklisted on compiz because it doesn't provide aiglx support. You would be better off using the proprietary driver (7.12 just came out this month) which does provide aiglx support. Aiglx works much better than xgl.
The guide posted earlier is what i use to install it:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

---

### Post by teejay17 on 2007-12-29
> **erfahren said:**
> oh, yeah "xserver-xgl" is the package name. sorry! that's the one you want.

note: if you ever need to disable xgl (for whatever reason) just make the (empty) file "~/.config/xserver-xgl/disable"

so in terminal:
```

touch .config/xserver-xgl/disable

```
Thanks.

---

### Post by teejay17 on 2007-12-29
> **lavinog said:**
> The restricted driver is blacklisted on compiz because it doesn't provide aiglx support. You would be better off using the proprietary driver (7.12 just came out this month) which does provide aiglx support. Aiglx works much better than xgl.
The guide posted earlier is what i use to install it:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
Thanks for that too. I guess some of the bugs have been worked out.
What method do you suggest I use to install? Method 1 or Method 2?

---

### Post by teejay17 on 2007-12-29
Actually, before I go any further, the Restricted Driver that I have enabled is already xorg-driver-fglrx.
When I uninstall the restricted driver, that's what gets removed.

---

### Post by erfahren on 2007-12-29
> **teejay17 said:**
> Actually, before I go any further, the Restricted Driver that I have enabled is already xorg-driver-fglrx.
When I uninstall the restricted driver, that's what gets removed.
When you use the version of fglrx that is available in Ubuntu 7.10 you need to install xserver-xgl to enable compositing (that version of the driver doesn't support it). If you installed xgl you should be able to get both the extra desktop effects and the screensavers to work well too (hopefully).

The "Method 2" on that guide is for installing the newer version of fglrx (ATI's proprietary driver), which *does* support compositing without needing XGL.  BUT... the fglrx driver available by enabling in the Restricted Drivers is pretty stable. The newer versions from ATI may or may not work as well. It may be worth a try for you though. (I've had problems with the newer versions myself, but by card is lower end.)

Apparently you have an ATI card that is fairly well supported by the opensource driver ("ati"). Which is why the desktop effects work. It just occured to me that *it just might be the case* to where you might need to just configure that one a little better in your /etc/X11/xorg.conf file to get everything to work well. You might look at: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by teejay17 on 2007-12-29
> **erfahren said:**
> When you use the version of fglrx that is available in Ubuntu 7.10 you need to install xserver-xgl to enable compositing (that version of the driver doesn't support it). If you installed xgl you should be able to get both the extra desktop effects and the screensavers to work well too (hopefully).

The "Method 2" on that guide is for installing the newer version of fglrx (ATI's proprietary driver), which *does* support compositing without needing XGL.  BUT... the fglrx driver available by enabling in the Restricted Drivers is pretty stable. The newer versions from ATI may or may not work as well. It may be worth a try for you though. (I've had problems with the newer versions myself, but by card is lower end.)

Apparently you have an ATI card that is fairly well supported by the opensource driver ("ati"). Which is why the desktop effects work. It just occured to me that *it just might be the case* to where you might need to just configure that one a little better in your /etc/X11/xorg.conf file to get everything to work well. You might look at: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
Okay, thanks. I'm going to try the first method...installing xserver-xgl from the repos, and see how that goes.
I do have the second and third options too, if all else fails. 
Thanks.

---

### Post by teejay17 on 2007-12-29
Thanks erfahren, it worked like a charm! Now I have 3D acceleration and desktop effects. 
The ATI fan is quicker now, too, (then slows down again, etc.) I guess this is a sign that the driver is working properly?

---

