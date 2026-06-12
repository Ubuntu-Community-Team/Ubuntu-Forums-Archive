---
title: "Display trapped in 640x480"
date: 2010-03-20
forum: Multimedia Software
---

### Post by nss0000 on 2010-03-20
Gents:

Running x64-U_8.04.1/EVGA_nv9400/Viewsonic 19" LCD

On a concurrent forum--INSTALL-- thread I've reported being "trapped" in a 640x480 screen resolution after changing graphics cards. It is very difficult/impossible to use screen GUI-function as displays overlap and do-NOT "traverse". 

I have got installed the NVidia GUI tool which reports the proper card,  screen display ( 1280x1040 ) and the current X-WIn setting ( 640x480 ). 

A poster on <INSTALL> suggested use of the CLI command <xrandr> to fix screen display ... thus perhaps allowing full GUI function for changing X-WIN setting. Is use of <xrandr> the best-available method for me to get out of the 640x480 "trap" ? If a better options is available I would appreciate a clue.

---

### Post by diesch on 2010-03-20
Using xrandr is usually the best solution. See [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) for how to use it.

---

### Post by nss0000 on 2010-03-20
> **diesch said:**
> Using xrandr is usually the best solution. See [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) for how to use it.


My system does NOT include the <xrandr> command. It's very tough get as the GUI tools are impossible. I had a look at "xconfig" using <gedit> ... and it's quite obscure.

Any other options beside a re-install of the OS ?


Using apt-get I am assured that the package <xrandr> no longer is available.

---

### Post by diesch on 2010-03-20
Then you have to edit */etc/X11/xorg.conf*, see [https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf](https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf)

The supported modes should be showed somewhere in /var/log/Xorg.0.log (please attach that file if you need help finding them).

You can create other modes using *cvt* as shown in [https://wiki.ubuntu.com/X/Config/Resolution/#Use%20cvt/xrandr%20tool%20to%20add%20the%20highest%20mode%20the%20LCD%20can%20do](https://wiki.ubuntu.com/X/Config/Resolution/#Use%20cvt/xrandr%20tool%20to%20add%20the%20highest%20mode%20the%20LCD%20can%20do)
and add the resulting ModeLine to */etc/X11/xorg.conf *as shown in [https://wiki.ubuntu.com/X/Config/Resolution/#Setting%20resolution%20changes%20in%20xorg.conf](https://wiki.ubuntu.com/X/Config/Resolution/#Setting%20resolution%20changes%20in%20xorg.conf)

---

### Post by nss0000 on 2010-03-20
> **diesch said:**
> Then you have to edit */etc/X11/xorg.conf*, see [https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf](https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf)

The supported modes should be showed somewhere in /var/log/Xorg.0.log (please attach that file if you need help finding them).

You can create other modes using *cvt* as shown in [https://wiki.ubuntu.com/X/Config/Resolution/#Use%20cvt/xrandr%20tool%20to%20add%20the%20highest%20mode%20the%20LCD%20can%20do](https://wiki.ubuntu.com/X/Config/Resolution/#Use%20cvt/xrandr%20tool%20to%20add%20the%20highest%20mode%20the%20LCD%20can%20do)
and add the resulting ModeLine to */etc/X11/xorg.conf *as shown in [https://wiki.ubuntu.com/X/Config/Resolution/#Setting%20resolution%20changes%20in%20xorg.conf](https://wiki.ubuntu.com/X/Config/Resolution/#Setting%20resolution%20changes%20in%20xorg.conf)

I have twice looked at the xorg.conf file with <gedit>. To the non-expert it is a page of detailed alpha-numeric nonsense. Have no idea what is important and what not. I **COULD** simply change every occurrence of "640x480" to "1280x1040" and hope for the (unlikely) best --- is that the best shot???  Retrieving that file for view is impossible due to the screen-distortion covering options and hiding tool-bars. 

A sad thought that after 3-years of use & accumulated files Ubuntu has left me no other option than to re-install from scratch and destroy all accumulated data .. because straightforward access to screen display controls does not exist. That truly is  perverse and would embarrass 1985 DOS.

---

### Post by nss0000 on 2010-03-20
It is suggested by [www.ubuntugeek.com](www.ubuntugeek.com) to ruthlessly purge & re.install X.windows by:

sudo apt-get remove --purge xserver-xorg
sudo apt-get install xserver-xorg
sudo dpkg-reconfigure xserver-xorg

I CAN with some effort get to <terminal> and execute these commands ... assuming all the names, spaces and dashes are OKey.

---

### Post by nss0000 on 2010-03-21
> **nss0000 said:**
> It is suggested by [www.ubuntugeek.com](www.ubuntugeek.com) to ruthlessly purge & re.install X.windows by:

sudo apt-get remove --purge xserver-xorg
sudo apt-get install xserver-xorg
sudo dpkg-reconfigure xserver-xorg

I CAN with some effort get to <terminal> and execute these commands ... assuming all the names, spaces and dashes are OKey.

Problem solved ... proper screen.res returned: 1280x1040@60/24 :

After the above three commands purging and re.installing X-WIN I brought-down from 'terminal' the NVidia toolset:

sudo apt-get install nvidia-xconfig
...nvidia-glx-new
...nvidia-settings

Then after <sudo nvidia-xconfig> + re-boot proper screen resolution was automagically established. Thanks to various posters; you should know how important are your "road-trip" reports to those stumbling about on a similar path.

---

