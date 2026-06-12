---
title: "uninstall and reinstall nvidia driver"
date: 2006-06-13
forum: Multimedia &amp; Video
---

### Post by echo $USER on 2006-06-13
I installed the nvidia driver from apt-get for my 6800gs co.  But, I want to install the driver from the nvidia site.  I have installed it before on my fedora 5 box.  How do I go about uninstalling and reinstalling the driver?  Do I have to uninstall the first one?  Will the second just overwrite it?  Thanks in advance.

---

### Post by Dr. Nick on 2006-06-13
I would first download the nvidia driver from nvidia nad make sure you have the kernel-source and other things needed to build it. Then uninstall the nvidia-glx package from the repository. After removing them and restarting you will get some xorg erros and de dropped off to a command line. 


While in the command line run the nvidia installer, If it finishes sucessfully then reboot back into xorg, If it fails then change your zorg.conf driver from nvidia to nv to get back into a gui tempoarily.

The 2nd may overwrite it if you dont remove it, but on a update the new driver from nvidia could be overwriten by the apt-get driver

---

### Post by tseliot on 2006-06-14
[QUOTE=echo $USER]I installed the nvidia driver from apt-get for my 6800gs co.  But, I want to install the driver from the nvidia site.  I have installed it before on my fedora 5 box.  How do I go about uninstalling and reinstalling the driver?  Do I have to uninstall the first one?  Will the second just overwrite it?  Thanks in advance.[/QUOTE]
My script will do that for you:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

---

