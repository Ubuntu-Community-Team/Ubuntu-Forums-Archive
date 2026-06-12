---
title: "Headless backend-only server &amp; &quot;low graphic mode&quot;"
date: 2009-09-02
forum: Mythbuntu
---

### Post by Vitani on 2009-09-02
Hi all,

I know this problem has been posted before, but I'm hoping that development has moved along a bit and there's now a software solution to the problem.

Basically I've installed Mythbuntu 9.04 onto my machine (backend only), with the intention of managing it through a combination of SSH, Webmin and VNC. I've got everything set up and working, but whenever I boot up the machine without a monitor connected it complains about being in "low graphics mode". Everything (except VNC) works, but every now & then I like to VNC onto the box to use GUI interfaces rather than command line.

Now the solution appears to be to either plug the graphics card into something (a monitor, or another graphics card) or create a [VGA dummy/nullifier](http://soerennielsen.dk/mod/VGAdummy/index_en.php). Neither of these solutions are *ideal*, and I was wondering if there is an option in the latest version of X to force it to use a configuration file (/etc/X11/xorg.conf) rather than detect at every boot, or something along those lines.

Anyway, if someone has any ideas, please let me know.

Cheers!

---

### Post by cybergalvez on 2009-09-02
what about installing nx (either freenx or the one from no Machine) and then using that rather then vnc.

---

