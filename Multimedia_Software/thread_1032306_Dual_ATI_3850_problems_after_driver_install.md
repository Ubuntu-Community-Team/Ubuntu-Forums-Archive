---
title: "Dual ATI 3850 problems after driver install"
date: 2009-01-06
forum: Multimedia Software
---

### Post by ckiraly2007 on 2009-01-06
i'm a n00b to the linux world so please bare with me...i just installed Ubuntu 8.10 64-bit onto my desktop and everything worked great!  after my system updated i got a notice that there were restricted graphics drivers available.  i installed them, rebooted and after the splash screen appears instead of the gnome desktop appearing i get a screen of text.  i'm stuck.  i can't figure out:

a) how to uninstall the driver to at least get back to where i can use my system

but more importantly

b) how to install the latest ATI 8.12 64-bit drivers onto my computer

i currently have 2 ATI 3850 cards in my pc that were setup in Crossfire under Windows.  is this a problem?
there has to be an easy way to install the ATI drivers.  i just really don't want to have to reinstall ubuntu everytime a mistake happens

thanks

---

### Post by markbuntu on 2009-01-06
The newest drivers from ati support crossfire in linux. When you get to the commmad prompt which is $ type

sudo aticonfig -f

it will ask for your password. type your password in.

when the prompt comes back reboot.

If you get any error messages please include them in your next post.

---

### Post by ckiraly2007 on 2009-01-07
thanks for the response markbuntu.  in the mean time i ended up reinstalling ubuntu then downloading the latest ati driver and installing manually.  i installed using sudo sh ati-driver-installer-8-12-x86.x86_64.run and it seemed to work.  i didn't see any options for crossfire in the CCC though, but i guess i could manually enable using aticonfig.  thanks again!

---

### Post by markbuntu on 2009-01-07
Yes, type aticonfig --help for the options.

---

