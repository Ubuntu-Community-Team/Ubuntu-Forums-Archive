---
title: "Maverick Meerkat GDM"
date: 2010-08-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Include4eto on 2010-08-10
Hey everybody. I just upgraded Ubuntu on my laptop from 10.04 LTS to 10.10 and I'm having a problem with my video card.
My laptop is an ASUS K50IN and the video card is NVIDIA G102M. I have the drivers installed and as far as the Hardware Drivers Utility knows - they are working properly. But Ubuntu is still not loading them. On normal boot the gmd doesn't even load, although the service seems to be running. I've also tried to reconfigure xorg and nvidia (nvidia-xconfig) but without luck. Failsafe works for me and i'm sure the problem isn't in the drivers themselves, but rather in Xorg.
I've tried all the drivers available from the repository, as well as the 195.36.31 from NVIDIA and have removed/reinstalled all of them several times.

Please excuse my English and my Linux skills :D (i seem to have spent(and lost) too much time with the Win32 API :( )

---

### Post by lidex on 2010-08-11
Maverick is in testing (Alpha) right now. Use at your own risk. My system is broken as well. Have a look at the maverick forum:
[http://www.uluga.ubuntuforums.org/forumdisplay.php?f=385](http://www.uluga.ubuntuforums.org/forumdisplay.php?f=385)

---

### Post by dcstar on 2010-08-11
> **lidex said:**
> Maverick is in testing (Alpha) right now. Use at your own risk. My system is broken as well. Have a look at the maverick forum:
[http://www.uluga.ubuntuforums.org/forumdisplay.php?f=385](http://www.uluga.ubuntuforums.org/forumdisplay.php?f=385)

People should:

[LIST=1]
[*]**Never** post any issues for development software in the forums which are specifically for released and supported software;
[*]Realise that using development software is bound by the conditions spelt out in every development release, and one of those is **not** to use the software for production - that means real - use.
[/LIST]

---

### Post by philinux on 2010-08-11
Moved to Testing forum.

---

### Post by VMC on 2010-08-11
> **Include4eto said:**
> Hey everybody. I just upgraded Ubuntu on my laptop from 10.04 LTS to 10.10 and I'm having a problem with my video card.
My laptop is an ASUS K50IN and the video card is NVIDIA G102M. I have the drivers installed and as far as the Hardware Drivers Utility knows - they are working properly. But Ubuntu is still not loading them. On normal boot the gmd doesn't even load, although the service seems to be running. I've also tried to reconfigure xorg and nvidia (nvidia-xconfig) but without luck. Failsafe works for me and i'm sure the problem isn't in the drivers themselves, but rather in Xorg.
I've tried all the drivers available from the repository, as well as the 195.36.31 from NVIDIA and have removed/reinstalled all of them several times.

Please excuse my English and my Linux skills :D (i seem to have spent(and lost) too much time with the Win32 API :( )

I'm guessing not all nVidia chips are equal. Some having nVidia cards.chips work ok, mine doesn't.

This type into a terminal:

```
 lspci|grep VGA
```

Output will be something similar to mine, but different:

```
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
```

I have to jump through hoops getting Maverick installed. I haven't updated from one OS to another in years, so I can't be of much help there.

Another important idea is to review the log files - "/var/log/syslog, /var/log/kern.log, and /var/log/Xorg.0.log"

00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)

The contents of _*Xorg.0.log*_ will be the telltale indicator.

---

### Post by cecilpierce on 2010-08-11
you could try removing xorg.conf while in recovery mode and then type startx to see if it will boot to X.
i had to do that till i finally got the 256.44 to work right, using a nvidia geforce 6200 dvi card.

cecil

---

### Post by cariboo on 2010-08-11
The solution for some of us with nvidia graphics cards is in [this]("http:///ubuntuforums.org/showthread.php?t=1549195") thread

---

### Post by ronacc on 2010-08-11
there are major changes to the Xserver being done right now, not all cards/chips are supported yet ( mine isn't) hang in there and keep updating and it will eventually straighten out . and in the future don't pull the trigger on upgrades until a version is released (not developement ) unless you are prepared and willing to accept breakages .

---

### Post by clivejo on 2010-08-12
Use the "nomodeset" kernel option to disable the new boot screen thingie ma-bob. Its probably best adding it to Grub2 to do this automatically (instructions are on numerous posts)

Install your drivers as per instruction on their website.  It should then work fine!!  :popcorn:

---

### Post by taavikko on 2010-08-12
> **cariboo907 said:**
> The solution for some of us with nvidia graphics cards is in [this]("http:///ubuntuforums.org/showthread.php?t=1549195") thread

Just did a clean install with alpha3
Put X updates on hold and upgraded everything else :)

The IgnoreABI with newer 256.44 driver and newer X lead sporadically to freeze.

---

