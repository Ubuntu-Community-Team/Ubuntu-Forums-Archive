---
title: "Mythbuntu Installation with AMD Radeon HD 5450 impossible?"
date: 2010-05-15
forum: Mythbuntu
---

### Post by Gee3 on 2010-05-15
Hello dear mythbuntu/ubuntu pro's,

I'm trying to install mythbuntu 10.04 on my HTPC.

Problem is, I don't even get an Installation screen because of my graphics card.

I'm using an [ASUS EAH5450 SILENT/DI/1GD3(LP)]("http://www.heise.de/preisvergleich/a512467.html") and the screen gets blank a few moments after the boot up screen.

Is it possible to install mythbuntu with some start up parameters?

Some information about my setup:

[LIST]
[*]Case: [**Antec Fusion** silver]("http://www.heise.de/preisvergleich/a214298.html")
[*]Processor: [**AMD Athlon X2 4850e**]("http://www.heise.de/preisvergleich/a324706.html")
[*]Motherboard: [**DFI LANparty JR 790GX-M2RS**]("http://www.heise.de/preisvergleich/a364099.html")
[*]DVB-C card: [**TechnoTrend Budget C-1500**]("http://www.heise.de/preisvergleich/a229054.html")
[*]some DVD-Burner
[*]HD: [**Samsung SpinPoint T166 500GB**]("http://www.heise.de/preisvergleich/a224182.html")
[/LIST]

It would be great if somebody could help me!

Thanks

 Gee3

---

### Post by LowSky on 2010-05-15
If the Ubuntu Live CD isn't working for you, try the  Alternative Install CD. It isn't as pretty but it should work:
32bit
[http://releases.ubuntu.uasw.edu/10.04/ubuntu-10.04-alternate-i386.iso](http://releases.ubuntu.uasw.edu/10.04/ubuntu-10.04-alternate-i386.iso)
64bit
[http://releases.ubuntu.uasw.edu/10.04/ubuntu-10.04-alternate-amd64.iso](http://releases.ubuntu.uasw.edu/10.04/ubuntu-10.04-alternate-amd64.iso)

---

### Post by superm1 on 2010-05-15
Boot with nomodeset.  its in the f6 menu

---

### Post by superm1 on 2010-05-15
> **LowSky said:**
> If the Ubuntu Live CD isn't working for you, try the  Alternative Install CD. It isn't as pretty but it should work:
32bit
[http://releases.ubuntu.uasw.edu/10.04/ubuntu-10.04-alternate-i386.iso](http://releases.ubuntu.uasw.edu/10.04/ubuntu-10.04-alternate-i386.iso)
64bit
[http://releases.ubuntu.uasw.edu/10.04/ubuntu-10.04-alternate-amd64.iso](http://releases.ubuntu.uasw.edu/10.04/ubuntu-10.04-alternate-amd64.iso)

I don't see how that would cause it to suddenly work over the next boot after install.  It's the same graphics driver used when it's installed as when it's booted in live mode..

---

### Post by LowSky on 2010-05-15
> **superm1 said:**
> I don't see how that would cause it to suddenly work over the next boot after install.  It's the same graphics driver used when it's installed as when it's booted in live mode..

he doesn't get the installation screen, its why I proposed the AltCD install

you can also boot in recovery mode, then to a command prompt, then install the proprietary driver, then reboot.

```
sudo apt-get install fglrx fglrx-amdcccle*
```

---

### Post by superm1 on 2010-05-15
> **LowSky said:**
> he doesn't get the installation screen, its why I proposed the AltCD install

you can also boot in recovery mode, then to a command prompt, then install the proprietary driver, then reboot.

```
sudo apt-get install fglrx fglrx-amdcccle*
```

That information would be valid for < 10.04.

With 10.04 KMS is active for radeon even before you get to X.  That means the black screen will likely persist on the alternate disks - meaning no console..

---

### Post by Gee3 on 2010-05-19
Thanks for all your answers!

Booting with **nomodeset** didn't help either.
Today I attached a normal display not via HDMI like the TV but with DVI and was able to complete the setup.

Now I'm having some different problems, but the problem of this post are solved for now ;-)

 Gee3

---

### Post by goatlord on 2010-07-23
For ATI cards use xforcevesa option while installing os:

[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)


greets
g

---

