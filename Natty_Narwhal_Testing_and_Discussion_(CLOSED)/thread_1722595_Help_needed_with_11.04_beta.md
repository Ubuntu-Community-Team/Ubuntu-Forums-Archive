---
title: "Help needed with 11.04 beta"
date: 2011-04-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by hunter99507 on 2011-04-05
I just downloaded and I am running 11.04 from a flash drive.  I am not sure how to desktop effects.  They used to be under appearance but now they are not.

Also I want to try out unity but it doesnt seem to work. How do I go about fixing this?  I go into terminal and this is what I get.

```
ubuntu@ubuntu:~$ unity
unity-panel-service: no process found
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
libprotobuf ERROR google/protobuf/message_lite.cc:123] Can't parse message of type "metadata.PluginBrief" because it is missing required fields: info
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
compiz (opengl) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (opengl) - Fatal: Software rendering detected
compiz (bailer) - Info: Ensuring a shell for your session
ubuntu@ubuntu:~$ Cannot register the panel shell: there is already one running.
Window manager warning: Type mismatch: Expected `int' got `bool' for key /apps/metacity/general/num_workspaces
Window manager warning: 0 stored in GConf key /apps/metacity/general/num_workspaces is out of range 1 to 36

```

---

### Post by uRock on 2011-04-05
Moved to NNT&D

---

### Post by hunter99507 on 2011-04-08
Its been a couple of days can anyone help? Thanks

---

### Post by VMC on 2011-04-08
> **hunter99507 said:**
> Its been a couple of days can anyone help? Thanks

I didn't see what video card you have, but you need to install your video driver for 3d. When that's done Unity will start automatically when you reboot. Providing you have the setting set for Ubuntu and not Classic.

Edit: While using the classic gnome, run the "Additional drivers" (jockey) to install your specific driver.

---

### Post by hunter99507 on 2011-04-09
My video card is a Nvidia 9600M GS, and I have enabled all of the drivers I can and it is still not working.  Any other suggestions?

---

### Post by mc4man on 2011-04-09
> **hunter99507 said:**
> I just downloaded and I am running 11.04 from a flash drive.  I am not sure how to desktop effects.  They used to be under appearance but now they are not.

Also I want to try out unity but it doesnt seem to work. How do I go about fixing this?  I go into terminal and this is what I get.


Are you running from a live cd or have you installed? (you seem to imply live cd

You can run unity with nvidia on a live cd but only with the nouveau 3d drivers and after installing them (just them), you need to log out and then in (username ubuntu
They don't make it easy because there is no log out option, use keyboard Ctrl+Alt+SysRq+k
screen is example of default unity login on live cd w/ nouveau3d

If using a persistent flash drive install never did here - you should clarify

---

### Post by hunter99507 on 2011-04-09
Sorry about the misleading information. In the begining I was running it on a flash drive but then in the middle of all of this I figured I would install it, so it is installed.  How would I go about installing that nouveau driver?  Normally I just used the Nvidia ones so I am not sure how.  Thanks

---

### Post by Quackers on 2011-04-09
Try de-activating the Experimental 3D driver. I don't think they can both be running at the same time. Then reboot.
It may also be worth marking Unity for re-installation, in synaptic, as you seem to have other problems with it.

---

### Post by ubuntu27 on 2011-04-09
> **hunter99507 said:**
> I just downloaded and I am running 11.04 from a flash drive.  I am not sure how to desktop effects.  They used to be under appearance but now they are not.
[/CODE]

The Effects Tab in Appearance has not arrived in Ubuntu Natty.
So, that means you do not have any problem. It is not supposed to be there YET.

You can change the effects by installing Compiz Settings Manager from Ubuntu Software Center or Synaptic Package Manger

```

[sudo apt-get install compizconfig-settings-manager]("apt://compizconfig-settings-manager")
```

---

### Post by hunter99507 on 2011-04-09
Ok so I got unity to work but I am not sure what I did and I was hoping that someone would explain it to me.  The website I used to fix the issue was 
```
http://ubuntuforums.org/showthread.php?t=1046504
```

The Command I did which made unity work was 
sudo apt-get --purge remove nvidia-glx-* nvidia-settings
sudo service gdm stop


What exactly do those 2 commands do? After I did the sudo service gdm stop, i restarted my computer and unity and graphics worked.  Thank you

---

### Post by Quackers on 2011-04-09
I suspect that instead of de-activating the 3D experimental driver, you have now removed the nvidia driver - I think :-)
Have a look at the Additional Drivers screen again and see what is/isn't activated.

---

### Post by terry_gardener on 2011-04-09
> **hunter99507 said:**
> 
The Command I did which made unity work was 
sudo apt-get --purge remove nvidia-glx-* nvidia-settings
sudo service gdm stop


What exactly do those 2 commands do? After I did the sudo service gdm stop, i restarted my computer and unity and graphics worked.  Thank you

using the above command will remove nvidia driver, therefore you are now using the experimental nouveau driver. 

like quackers has said run the additional drivers app to find out for sure.

---

