---
title: "NVIDIA 169.xx DRIVERS OPENGL PROBLEM"
date: 2008-05-09
forum: Multimedia Software
---

### Post by sulligogs on 2008-05-09
Hi all

If you are using an NVDIA graphics card with an old(ish) CPU then you may find that your OpenGL will not work.

This is because as from driver version 169.07 NVIDIA has dropped support for CPUs that do not have SSE capabilities.  Such processors are AMD Durons, Athlons and pre-Pentium 3s.

One of my systems has got an AMD Duron 750MHZ and running "glxgears" from a terminal will result in a "illegal instruction" error.

The only workaround for this right now is to download an archived driver from NVIDIA's website.  The driver that I found to be most adequate is this:-

[http://www.nvidia.com/object/linux_display_ia32_100.14.19.html](http://www.nvidia.com/object/linux_display_ia32_100.14.19.html)

It's not really an old driver as it dates to 2007.  This driver will still give full support for non SSE capable CPUs.  It uses version 1.13 of the NVIDIA X Server Settings application whilst the current is 1.14.

To install:-

[SIZE=4]1)[/SIZE] Download the driver to your desktop

[SIZE=4]2)[/SIZE] Launch a terminal window and enter:-

```

sudo /etc/init.d/gdm stop

```[SIZE=4]3)[/SIZE] Change to the directory of your desktop, such as:-

```

cd /home/MYUSERNAME/Desktop

```[SIZE=4]4)[/SIZE] Run the installer:-

```

sudo sh NVIDIA-Linux-x86-100.14.19-pkg1.run

```[SIZE=4]5)[/SIZE] Follow the simple onscreen instructions!

If the installer asks to download a kernel module for your system I find it's just as good to tell it no and the installer will build a new one for you.

Now, my Xubuntu 8.04 install is running like a dream with excellent 2D and 3D capabilities!

---

### Post by lessgov2007 on 2008-05-09
I had this same problem...  I used EnvyNG and manually selected the NVidia-glx drivers...  Although, the restricted drivers manager shows no active drivers everything works good...  

The nvidia website even suggests using the nvidia-new driver but, it wont work.  My system is AMD also with nvidia 6200...

---

### Post by sulligogs on 2008-05-09
> **lessgov2007 said:**
> I had this same problem...  I used EnvyNG and manually selected the NVidia-glx drivers... 

Yeah, that was my first action, to get EnvyNG to try different drivers.  Whilst they all installed correctly, each one gave irritating results.

The 7x drivers meant that I couldn't get the NVIDIA X Server Settings application to run.  Not a big deal, but it really bugged me!

The 9x drivers gave me a default of really ridiculous low res modes on startup.  Even when I managed to change them on the next restart it reverted back to how it was.

Anyway, glad to hear you got things sorted out.  Not entirely happy about what NVIDIA have decided to do as regards supporting older CPUs.  What is the advantage?  Linux is a system of users from A to Z.  Some run new hardware and others run old.  That's the beauty of Linux you can customise how your systems runs.

Now, I would understand 286 processors....

---

### Post by cogadh on 2008-05-10
Are you certain the processor was actually the problem? I ran into a lack of functional OpenGL support on a system with 2GHz Pentium 4, certainly not in the same class as those processors you listed. I was never able to fix it so I went back to using Gutsy.

---

### Post by sulligogs on 2008-05-10
> **cogadh said:**
> Are you certain the processor was actually the problem?

Well, according to zander at [http://www.nvnews.net/vbulletin/showthread.php?t=104914&highlight=sulligogs](http://www.nvnews.net/vbulletin/showthread.php?t=104914&highlight=sulligogs) this is the problem.

I haven't officially verified it.  I haven't seen any bulletins describing their decision.  But, the drivers I used [http://www.nvidia.com/object/linux_display_ia32_100.14.19.html](http://www.nvidia.com/object/linux_display_ia32_100.14.19.html) have certainly done the trick.

The system felt like a fresh XP install.  Everything blazing.

Anybody else to verify this matter?

---

