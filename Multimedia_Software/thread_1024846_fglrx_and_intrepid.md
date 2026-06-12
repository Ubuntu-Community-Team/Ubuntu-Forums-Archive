---
title: "fglrx and intrepid"
date: 2008-12-29
forum: Multimedia Software
---

### Post by maclenin on 2008-12-29
I had success using this [_how-to_]("http://ubuntuforums.org/showpost.php?p=3056143&postcount=3") to get my Radeon x2300 video card up and running under Fesity...

> Re: ATI Mobility Radeon X2300 problems

I had excact the same problem when I just changed my laptop to HP 6910p
but I just solved this probelem.

steps below:

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
sudo /etc/init.d/gdm restart

(This solution was form [http://terenzioberni.blogspot.com/20...53jr-f3jr.html](http://terenzioberni.blogspot.com/20...53jr-f3jr.html))

-ckh



...however, having just used the Hardware Drivers application to install fglrx under Intrepid, I am not having similar success - the fonts and images are a tad "ghostly"....

Might a re-install of fglrx using the "Feisty" method be worth a try?

Might this command (from the Feisty method) be worth a shot...

```
sudo aticonfig --overlay-type=Xv
```

...or has Xv overlay already been configured with the Intrepid fglrx install? How can I tell?

How can I tweak/troubleshoot the functionality of fglrx (in Intrepid)?

I have used **fglrxinfo** to verify that the driver has - or seems to have - been installed "properly" under Intrepid.

Thanks for any help.

---

