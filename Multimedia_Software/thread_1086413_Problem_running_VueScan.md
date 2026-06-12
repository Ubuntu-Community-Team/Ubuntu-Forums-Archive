---
title: "Problem running VueScan"
date: 2009-03-04
forum: Multimedia Software
---

### Post by ~sparkles~ on 2009-03-04
I've recently bought an Epson Perfection v300 scanner and want to run vuescan.

Followed this guide: [http://www.cyfinity.com/2009/02/epson-perfection-v300-scanner-in-ubuntu-810/](http://www.cyfinity.com/2009/02/epson-perfection-v300-scanner-in-ubuntu-810/) to install the avasys drivers.

So no problem the scanner installed ok and it is recognised, works with xsane and iscan.

Now, downloaded and unpacked vuescan and installed the needed version of libstdc++ as recommend in the vuescan release notes.

When I start VueScan, it takes a looong time to load and I get this message:

> VueScan found an Epson Perfection V300, but no Epson software for this scanner was found on your system. Try downloading a driver for this scanner from [www.avasys.jp/english](www.avasys.jp/english). See the VueScan Release Notes for more information. Press 'Close' to start using VueScan.

I've tried this with my laptop running ubuntustudio intrepid and on my mthbuntu Hardy htpc, and I get the same result.

Any help to solve this would be greatly appreciated :)

---

### Post by julian.coccia on 2009-03-04
That's right. You need to download iscan (and the plugin) and use the iscan program to scan. I had the same exact problem with the V350 Photo scanner.

Check out this thread. I have also realized how to lift the dpi limitation imposed in iscan:

[http://ubuntuforums.org/showthread.php?t=1086953](http://ubuntuforums.org/showthread.php?t=1086953)

---

### Post by ~sparkles~ on 2009-03-04
Ummm... I have downloaded and installed iscan and it runs fine. The problem is that vuescan won't recognize the scanner.

---

### Post by ~sparkles~ on 2009-03-14
Still have this problem... can anyone help?

---

### Post by rcastberg on 2009-03-24
Hi,

Are you using a 64bit system by any chance?

I had a similar problem, after i had installed both iscan, and iscan-plugin-gt-x770, i was unable to detect my V500.

I removed both of these packages (64bit) and insalled the 32bit versions.
```
sudo dpkg -i --force-architecture iscan_2.18.0-2_i386.deb iscan-plugin-gt-x770_2.1.1-1_i386.deb 

```

Hope this helps.

René

---

### Post by elpenna86 on 2009-04-14
I've got the same problem with a 64bit system... intalling the 32bit packages doesn't fix the problem.

iscan and xsane work perfect but Vuescan don't find the scanner...

Any idea??

Thank you very much

---

### Post by Mekk on 2009-07-25
+1

Note: I used succesfully vuescan 8.4 on Ubuntu 8.04 . It required me to run iscan once after connecting the scanner to initialize it (otherwise it crashed) but after that it worked.

Now I am on 9.04. Haven't been scanning for some time and I found that scanner is no longer recognized using old drivers. So I downloaded new iscan packages from avasys, installed them - and iscan is worked fine. But neither vuescan 8.4, neither vuescan 8.5 (I upgraded to check whether it helps) detects the scanner software

---

