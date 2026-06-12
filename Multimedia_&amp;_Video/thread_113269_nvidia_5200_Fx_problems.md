---
title: "nvidia 5200 Fx problems"
date: 2006-01-06
forum: Multimedia &amp; Video
---

### Post by afriedel on 2006-01-06
This has been frustrating for a couple of weeks now.  I have gone through every tutorial I can find and nothing works.  I just can't get the nvidia driver to work on my breezy install.  I am using theu latest 386 kernel (I read somewhere that going to the 686 kernel broke it for someone).  When I change nv to nvidia in xorg.conf, x refuses to start.  

I have the linux restrict modules installed for my kernel as well as nvidia-glx.  I don't know if this is supposed to work, but when I run sudo modprobe nvidia I get 

FATAL: Error inserting nvidia (/lib/modules/2.6.12-10-386/volatile/nvidia.ko): No such device

The file is there.  I don't know enough to troubleshoot anymore.  From what I can tell everything is setup to work.  Any help would be greatly appreciated and if there is any more information I can provide please let me know.

---

### Post by Omnios on 2006-01-06
This is the Ubuntu Wiki entry for nvidia
 
 [http://help.ubuntu.com/starterguide/C/ch04.html#installnvidiadriver]("http://help.ubuntu.com/starterguide/C/ch04.html#installnvidiadriver")

 Did you do  "sudo nvidia-glx-config enable"
This part is important I had a problem before where I had difficulty getting it to work, I think it sets up Xorg for glx. 
 ```
sudo nvidia-glx-config enable 
```e

---

### Post by afriedel on 2006-01-06
Yes.  I do that, type ctl-alt-backspace to restart x and it barfs.  The message I see is something like can't load the driver or something.  If I type startx at the console x starts up just like nothing happened.  

One thing is wierd is that nothing gets printed out when I run nvidia-glx-config but while looking at the script, something should be written to the console.

---

### Post by Omnios on 2006-01-06
Did you use "nvidia-glx-config" or "sudo nvidia-glx-config"?

---

### Post by afriedel on 2006-01-06
I ran sudo nvidia-glx-config and it seems nothing happens

when I run it without sudo, it does come back and tell me I need to be root or use sudo.

---

### Post by Mustard on 2006-01-06
Have you installed the nvidia drivers from the nvidia website at any stage?

Also have you tried resetting the xorg.conf with either of these commands?

```
sudo dpkg-reconfigure -phigh xserver-xorg

sudo dpkg-reconfigure xserver-xorg
```

Have you fiddled around with any BIOS settings for your nvidia card?

I can imagine your frustration.  I'm running a 5200 FX myself and I have'nt had any issues with it.

---

### Post by afriedel on 2006-01-06
I don't believe I ever got anywhere with anything directly from nvidia.  I downloaded their stuff.  I tried to run it but I have never had any kernel source on my machine so I never got very far into the install, at least not far enough for it to install anything. 

I ran sudo dpkg-reconfigure xserver-xorg and accepted most of the defaults but change the nv to nvidia when it asked what driver to use.  as use as it exited and tried to start x again, it puked and I restored the old xorg.conf.

I had it working at one point with mandrake.  I got 2 new hard drives and installed breezy.

---

### Post by afriedel on 2006-01-06
Thanks everyone for their responses.  I have made a little progress based on a bit of info here:

[http://home.comcast.net/~andrex/Debian-nVidia/troubleshooting.html](http://home.comcast.net/~andrex/Debian-nVidia/troubleshooting.html)

It mentioned an issue with nvidiafb and sure enough, that module was loaded.  I did a sudo rmmod nvidiafb and then a sudo modprobe nvidia.  ctl-alt-backspace dropped me back to a console.  I typed startx and it glxgears gives me about 1300 fps now.

I am looking at why nvidiafb was loaded and if I can stop it before I reboot.  Does anybody know how to change the modules that are loaded by the kernel.

Sorry but I am not used to the way Debian/Ubuntu do things.  I am a Mandrake refugee.

---

### Post by reet on 2006-01-06
kernel modules that are loaded at boot are listed in /etc/modules

---

### Post by stratotak on 2006-01-07
actually all modules that load at boot arent listed in /etc/modules//my nvidia drivers isnt listed nor are my ipw2100 drivers listed and they load up at boot....but i think you have to add modules you dont want to load in your hotplug blacklist file...

---

