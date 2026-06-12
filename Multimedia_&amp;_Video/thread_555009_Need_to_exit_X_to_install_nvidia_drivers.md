---
title: "Need to exit X to install nvidia drivers?"
date: 2007-09-19
forum: Multimedia &amp; Video
---

### Post by iangregson on 2007-09-19
Hi there,

Can anyone help, I need to exit X to install some nvidia drivers... actually i have v .09 installed ... and now i found .19 .. i run it use sh name of package... and it runs fine but says X is running and must exit X first..

Still very new to ubuntu ... how do i exit X ... i presume to a command prompt...

Any help really appreciated

thanks in advance

Ian

---

### Post by aidanr on 2007-09-19
> sudo gedit /etc/default/linux-restricted-modules-common


DISABLED_MODULES="nv"                        [COLOR="Red"]#add this line, save and exit[/COLOR]

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev


sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common


sudo rm /etc/init.d/nvidia-*                        [COLOR="#ff0000"]#careful here, type it exactly[/COLOR]


- Logout


- hit ctrl+alt+F6 to switch to another tty, and login


- sudo /etc/init.d/gdm stop


- sudo sh NVIDIA-Linux-x86-100.14.19-pkg1.run


- sudo /etc/init.d/gdm start 

.

---

### Post by yabbadabbadont on 2007-09-19
Logout.  At the login screen, hit control-alt-F1.  Login at the text login prompt.  Run "sudo -i".  You are not effectively the root user.  Stop X by running, "/etc/init.d/gdm stop".  Now run your nvidia driver installer using the instructions that they provide.  Type "reboot" when finished to restart the machine.

Edit: Looks like I took too long typing up my reply.  :D

---

### Post by anarcholis on 2007-09-19
Or you can just hit Ctrl-Alt-F5 to kill X and drop you to the command line, then type "startx" to start the GUI again once installation is done.

---

### Post by iangregson on 2007-09-20
thanks everyone for the comments, i am currently at work but when i get home i will be trying them... thank you

Ian

---

### Post by iangregson on 2007-09-20
Thanks everyone.. got pretty far, allowed me to stop x ..and loaded up verison 19 of the nvidia drivers but it says i alreayd have a version installed... it is true, this is not the restricted version that comes with ubuntu ... but a verison i installed .. which was 09

NVIDIA-Linux-x86-100.14.09-pkg1.run

How do i uninstall this ?

I tried going to add/remove and searching for nvidia but nothing was displayed that was installed..

I should think it will work as long as i can uninstall this old version

thanks

---

### Post by aidanr on 2007-09-20
the installer should uninstall any previous versions, however if it's not for some reason, try running it with the --uninstall switch
```
sudo sh NVIDIA-Linux-x86-100.14.09-pkg1.run --uninstall
```

---

### Post by iangregson on 2007-09-20
Yep! that was it  --uninstall, then i had to reboot as it didn't seem to work and then i was able to install!! thanks a lot... i now have .19 version installed..

---

### Post by iangregson on 2007-09-20
Just out of interest whats the difference between ctrl-atl-f5    f6   or f1.. they all seem to do the same... is there a doc giving you these key definition with descriptions??

just interested..

also the init.d directory... obviously is where i can stop GDM .. and start it...  is it used for other things too?

Thanks once again .. i now have the latest drivers..

---

### Post by aidanr on 2007-09-20
> **iangregson said:**
> is there a doc giving you these key definition with descriptions??

Yup, [_it's_]("http://humanreadable.nfshost.com/howtos/x_keyboard_assignments.htm") [_called_]("http://www.scit.wlv.ac.uk/cgi-bin/mansec?4+init.d") [_google_]("http://www.google.com") ;)

---

### Post by iangregson on 2007-09-20
Ah Ah .. thanks... again for all your help... 

Much appreciated

Ian

---

