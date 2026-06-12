---
title: "GDM problems with Maverick"
date: 2010-09-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by wolf187 on 2010-09-08
Hello

I have upgraded to Maverick Meerkat yesterday and my GDM does not seem to work, the reason I believe this is that when I logon it goes to a console login and then I remove the GDM package using *sudo apt-get remove gdm* and then I restart and reload the backend Xorg configuration and then go to a console login and install the gdm again using *sudo apt-get install gdm *and then when I reboot I get a graphical login but the screen resolution is 800 X 600 and this is hard to use. I am using GNOME 2.31 and GDM version 2.30.5, I have a sis 771/671 graphics card. Before on Lucid Lynx I had used another method of loading the sis driver and it worked fine but now there are no threads to help with Maverick Meerkat, can anyone help, please, Thanks in advance.

---

### Post by coffeecat on 2010-09-08
> **wolf187 said:**
> but now there are no threads to help with Maverick Meerkat,

This is where you need to be:

[http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)

I'll ask a mod to move this for you.

---

### Post by Joeb454 on 2010-09-08
*Thread moved to **Maverick Meerkat Testing and Discussion***.

Thanks for reporting it, coffeecat :)

---

### Post by wolf187 on 2010-09-08
Thanks, I'm sorry just that i'm used to posting hardware problems in the Hardware and Laptops area, I hadn't seen the Maverick area.

---

### Post by coffeecat on 2010-09-08
Don't worry, you're not the only person to miss the testing subforum. :) It's fairly well hidden if you don't know where to look.

I've done a quick search for 'SiS' and there are three threads in this subforum where that string pops up, but as there are over 500 pages to check through, I thought I'd leave that to you. :p Here:

[http://ubuntuforums.org/showthread.php?t=1549195&highlight=sis](http://ubuntuforums.org/showthread.php?t=1549195&highlight=sis)

[http://ubuntuforums.org/showthread.php?t=1476691&highlight=sis](http://ubuntuforums.org/showthread.php?t=1476691&highlight=sis)

[http://ubuntuforums.org/showthread.php?t=1503555&highlight=sis](http://ubuntuforums.org/showthread.php?t=1503555&highlight=sis)

What's your hardware? Is that a laptop or a desktop? Because, if a desktop, an investment in an nvidia card would save you a lot of heartache and hassle. From what I've read, SiS cards (and motherboard chipsets) can be  a grim experience in Linux.

Good luck!

---

### Post by wolf187 on 2010-09-08
It is a laptop, If it was a desktop I would've changed a long time ago because sis seems to give a lot of issues with regard to drivers and installation.

---

### Post by wolf187 on 2010-09-10
I still cannot find any drivers for the SiS 771/671/672 Graphics card I even tried the xorg-edgers repository and still with no avail. Can someone please help me because 800 X 600 screen resolution really sucks especially with no 3D acceleration

Thanks in advance, any help would be greatly appreciated.

---

### Post by dino99 on 2010-09-10
found this thread: [http://ubuntuforums.org/showthread.php?t=1483069](http://ubuntuforums.org/showthread.php?t=1483069)

---

### Post by wolf187 on 2010-09-13
Thanks I'm going to try it out now but there are so many posts for SiS 671/771, Why don't they just include a package for the graphics card if there are so many requests for it? It might be a suggestion for the Development team of ubuntu, but thanks for your help.

---

### Post by wolf187 on 2010-09-14
Hello
 
I got a major problem, I tried some of the stuff and now my ubuntu only boots up in console mode, then I tried and removed the gdm package and then it came up with the whole low graphics session option and then I selected to choose to use generic configuration and then when I restarted it then I realised that I had to reinstall the GDM package however this would be easy if it read the repository from the CDROM but eventhough the CDROM is one of the respositories it still tries to download the files from za.archive.ubuntu.com but this does not work because the wireless network cannot be enabled from the console. I have tried to add the CD as a respository again and still with no avail. If someone can help me to access my wireless network(it was configured before when I had a GUI) or help me to remove the other repositories(which is the main server to download the updates)  and allow only the CDROM to be used as a repository it will be a great help, I thought 800 X 600 resolution sucked but now using only console login sucks. Please help as soon as possible and thanks in advance.

---

### Post by coffeecat on 2010-09-14
I don't know how to connect wirelessly from the console. Perhaps someone else can help. If you want to try disabling the distant repositories, you can do this by editing /etc/apt/sources.list. From the console:

```
sudo nano -w /etc/apt/sources.list
```Comment each repository line with a # character at the beginning of the line, except the CDROM line. I'm sorry, I don't know what  that line looks like - I've never used the CD as a repo.

When you've finished editing, ctrl-O to write out the edited file, and ctrl-X to exit. Now:

```
sudo apt-get update
``` ... and hopefully it will try to update the package metadata only from the CD. However, are you sure the package you want is on the CD?

---

### Post by VMC on 2010-09-14
[delete comment]

---

### Post by wolf187 on 2010-09-15
Yes, I am sure this package is on the CD because I used it before, hopefully the CD is not corrupted, I'm just crossing thumbs here because I got a lot of work to do and is due tomorrow. Thanks for the help though.

---

### Post by wolf187 on 2010-09-28
Thanks everyone for the help with the graphics problem, however I still need to find a way to install drivers for the SiS 672 graphics card and unfortunately none of the above suggestions work. I would rather someone else risk their computer and test out the various new methods then me. But I will try and forward the problem to the developers of Ubuntu 10.10.

---

