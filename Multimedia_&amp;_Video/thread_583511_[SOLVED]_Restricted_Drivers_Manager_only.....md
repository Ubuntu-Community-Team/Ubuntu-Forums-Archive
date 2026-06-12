---
title: "[SOLVED] Restricted Drivers Manager only...."
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by Cariboo1938 on 2007-10-20
Hi all, 
What is to do to get the open source Nvidia driver "nvidia-glx-new" installed when the tool 'Resticted Drivers Manager' only shows me "nvidia-glx"?
Does somebody know if I can just install the "...-new" with Synaptic? 
If it is installed that way, would it be enough to change /etc/X11/xorg.conf at the device section from "nv" to "nvidia" to run the new driver?:confused:

---

### Post by Steveway on 2007-10-20
What graphics-card do you have?
nvidia-glx-new is only for fx-series and later, afaik.

---

### Post by Cariboo1938 on 2007-10-20
> **Steveway said:**
> What graphics-card do you have?
nvidia-glx-new is only for fx-series and later, afaik.Hi Steveway and thanks for the response!
My card is identified by the '-->Sytem -->Preferences -->Hardware Information' tool as "GeForce FX 5200"! (That's exactly what I bought!)

---

### Post by Steveway on 2007-10-21
You should be able to install the nvidia-glx-new package via synaptic.

---

### Post by Cariboo1938 on 2007-10-21
> **Steveway said:**
> You should be able to install the nvidia-glx-new package via synaptic.OK, I installed it and now the trouble begins....after reboot,  Xserver won't start and I had to change the '/etc/X11/xorg.conf' file, i.e. replace "nvidia" with "nv" in the device section to get my graphical interface back running.

---

### Post by Cariboo1938 on 2007-10-21
with the Restricted Drivers Manager I cannot get the graphical interface - xserver - running after I enabled the 'NVIDIA accelerated graphics driver'. 
I followed the instructions [HERE]("http://www.psychocats.net/ubuntu/nvidia"), 
I tried [ENVY]("http://albertomilone.com/nvidia_scripts1.html"), 
I tried [THIS]("http://www.nvnews.net/vbulletin/showthread.php?t=72490") and 
it seems I'm the only person who has the problem that, after reboot, getting a black screen with some text about "failed to start xserver' and finally a command prompt to login. 
I attach the /var/log/Xorg.0.log file (the extension .zip means nothing) once again hoping that somebody can figure out what I do wrong or what is wrong or missing on my Feisty 7.04 amd64 installation. 
Which files else would be needed/helpfull for analyzing the issue:confused:

---

### Post by Cariboo1938 on 2007-10-22
Hello all,
any ideas on this one? Please, any response is appreciated!!!:(

---

### Post by alb@nian on 2007-10-22
I'm noob with ubuntu and with linux.

I had something like your problem. With Fiesty 7.04 but when I upgraded with the new 7.10 and using the automatic update:

```
sudo apt-get install nvidia-glx-new
```

The problem is fixed. Maybe you should try this way.

---

### Post by JohnSGruber on 2007-10-22
Cariboo1938:
It would be helpful to see the Xorg.0.log file from when you started with the nvidia driver in addition to the nv one you posted. The previous log file is saved as Xorg.0.log.old. Please note the time you try it and attach that log to a posting. A log message about the log at the beginning gives the time the log was made (X was started). It would also be helpful to see your xorg.conf file.

In what resolution is your display running when using the nv driver?

I believe your display is an LG CRT with resolution of up to 1280x1040, is that correct?

Thanks.

---

### Post by Cariboo1938 on 2007-10-23
Thanks JohnSGruber for your response;
1) Yes,  my display is an LG CRT with resolution of up to 1280x1040!
2) I attached both Xorg.log files. (BTW the .zip extension is for overcoming the file limits for the attachments.....to open with Text Editor)


Edit:
I had to edit /boot/grub/menu.lst:

1) Find this section and add "iommu=noaperture":
Quote:
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e4af70f0-d555-49ab-8dd0-687cc3e7f81c ro [COLOR="Magenta"]iommu=noaperture[/COLOR]

2) Save the file and type:
Code: "sudo update-grub"

and then
3) restart my computer!

BTW:
There must be a conflict between my BIOS (Phoenix Award Ga -K8NS Ultra-939 F5) and the kernel so that AGP aperture is not reported correctly.

---

### Post by JohnSGruber on 2007-10-23
I'm afraid you didn't copy the log before you started the Xserver with the nv driver a second time. Neither is a start using the restricted (proprietary) nvidia driver. The logs are from Monday at about 10:30 AM and Sunday at about 1:47 PM and they don't contain anything that surprises me. They look clean since the nv driver doesn't do glx, and since I assume you don't have touchpad equipment.

If you like you could try to capture that log again. You can note the time you try it and then compare it with the time in about the 13th line in the log files to see that you have the right file.

It would be good if you could post your /etc/X11/xorg.conf file, too.

Good luck.

---

### Post by JohnSGruber on 2007-10-23
I don't understand how you actually got nvidia-glx-new installed from the various methods you listed.

If you simply installed it via the Ubuntu repositories (apt-get or synaptics to install nvidia-glx-new, for example) I see that there is a command that takes care of enabling the package. It changes an unchanged xorg.conf file to use the nvidia X driver, and puts the nvidia kernel driver into the kernel. It can also be used to disable the new driver. If this is your method of installation you might want to see if you have a /usr/share/doc/nvidia-glx-new folder with documentation from nvidia and Ubuntu.

I certainly don't know if I'll be able to be of any help, but that log file and config file should be helpful to anyone who wants to run down the error you are getting.
Since you are using nvidia-glx-new rather than nvidia-glx you may want to list the output of
```
lspci
```
and
```
lspci -n 
```

---

