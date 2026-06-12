---
title: "System starts in low graphics mode and never shows the desktop"
date: 2010-06-05
forum: Multimedia Software
---

### Post by ibbqalot on 2010-06-05
Hi,

i'm pretty new to the whole linux system for a start.

anyway, i downloaded a linux kernel from linux.org to check what is the kernel is about, i clicked on make_file or make sth .. and in the same session i downloaded a program called login window.

now the problem is that the system boots ok, it gives me a msg saying that system is running in low graphics mode, when i press ok i get a few options like troubleshootin or restart x or use back up configuration .. and nothing works .. when i press start normally it never stops loading .. i can see the terminal when clicking ctrl + alt + f1,f2 ... but when i press ctrl + alt + f7 or return back to the desktop ubuntu is still loading .. it never stops loading.

and after using ubuntu for a while i really hate windows 7 .. i have it on the system, so is there a way to fix this problem?

Thanks! :popcorn::popcorn::popcorn:

---

### Post by nss0000 on 2010-06-05
> **ibbqalot said:**
> Hi,

i'm pretty new to the whole linux system for a start.

anyway, i downloaded a linux kernel from linux.org to check what is the kernel is about, i clicked on make_file or make sth .. and in the same session i downloaded a program called login window.

now the problem is that the system boots ok, it gives me a msg saying that system is running in low graphics mode, when i press ok i get a few options like troubleshootin or restart x or use back up configuration .. and nothing works .. when i press start normally it never stops loading .. i can see the terminal when clicking ctrl + alt + f1,f2 ... but when i press ctrl + alt + f7 or return back to the desktop ubuntu is still loading .. it never stops loading.

and after using ubuntu for a while i really hate windows 7 .. i have it on the system, so is there a way to fix this problem?

Thanks! :popcorn::popcorn::popcorn:

Yeah ... remove Ubuntu. All recent updates unrecoverably corrupt the graphics.  You are scr*wwed.

---

### Post by ibbqalot on 2010-06-05
> **nss0000 said:**
> Yeah ... remove Ubuntu. All recent updates unrecoverably corrupt the graphics.  You are scr*wwed.

JESUS!! how do i remove it?:popcorn::popcorn::popcorn:

---

### Post by Paddy Landau on 2010-06-08
I've just seen this thread.

Are you using Ubuntu or are you using something else? Do you have a dual-boot with Windows? If so, does your Windows start? We need to know a bit more about your set-up.

The reason I ask is that in Ubuntu, you would never "download a linux kernel" and compile it. All installation is done through a package manager called *Synaptic*. Synaptic Package Manager takes care of all downloading, controlling dependencies, installing and uninstalling for you.

Let us know your situation and then we perhaps could help you further.

---

### Post by ibbqalot on 2010-06-08
Well, what i did is i re-partitioned my hard drive to deleting the linux partition, but GRUB was still there, it is probably installed on the windows partition or something.  and then just re-installed Ubuntu.

As for my boot, i really don't understand how it happens, but when i start the computer, i get the grub screen and can choose between ubuntu and windows 7 .. when i click on windows 7 i get 2 choices between ubuntu netbook (which i removed by just deleting it from linux) and windows.

is there anyway just to use one booting screen instead of two? because when i click on the ubuntu netbook i get nothing because it's not there.

---

### Post by Paddy Landau on 2010-06-08
> **ibbqalot said:**
> is there anyway just to use one booting screen instead of two?
Did you install Wubi at any stage?

You may have to reinstall grub. I don't know how to do that with grub2, but there are several threads on that topic.

---

### Post by ibbqalot on 2010-06-08
Thank you, i will try reinstalling grub

---

