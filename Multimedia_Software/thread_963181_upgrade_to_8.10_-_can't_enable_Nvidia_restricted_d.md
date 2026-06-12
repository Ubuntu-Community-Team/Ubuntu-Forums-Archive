---
title: "upgrade to 8.10 - can't enable Nvidia restricted drivers"
date: 2008-10-30
forum: Multimedia Software
---

### Post by mageus on 2008-10-30
Upgraded from 8.04.1 to 8.10 (x64).  GF 7600GT.  Athlon X2 64.  Starts up using the unaccelerated drivers.

Using 'Hardware Drivers' I try to enable the 177 driver, get error dialog:

"Reconfiguring X.org video drivers is not possible: /etc/X11/xorg.conf if invalid"

- tried deleting xorg.conf
- tried dpkg-reconfig xserver-xorg
- tried nvidia-xconfig

None of these work.

- /var/log/Xorg.0.log doesn't show any syntax errors with any of these xorg.conf files.

Any ideas?

---

### Post by cariboo on 2008-10-30
Start in recovery mode and at the menu select xfix. The will create a new /etc/X11/xorg.conf. then try install the restricted drivers.

Jim

---

### Post by Spinalcracker on 2008-10-30
I am having a similar issue.  I can activate the 177.80 driver through the restricted driver manager and have tried manually installing it by downloading it direct from nvidia's website etc.

The installations go through fine but on reboot X fails to start and I get a console login prompt.  Re-installing in the console does not work.  Manually trying to set the driver in xorg.conf to nv does not work.  Booting to recovery mode and choosing xfix does not work.  

Any ideas?

8800GT is the card.

---

### Post by eternalnewbee on 2008-10-30
Try this:
```
sudo apt-get install nvidia-glx-177
```

---

### Post by PendragonUK on 2008-10-30
I'm also experiencing an issue when installing the restricted drivers. After reboot I hear the tomtom drums for login but the screen is black. 

A few releases ago it would have been a case of editing xorg.conf and manually forcing the refresh rate, Vertical and horizontal for my monitor. Things have changed since I last installed ubuntu using this monitor.

Any help would be appreciated...

---

### Post by Spinalcracker on 2008-10-30
> **eternalnewbee said:**
> Try this:
```
sudo apt-get install nvidia-glx-177
```

Yes that will install the driver without error.  When you reboot, or try to restart X though it drops to a console, texted login and the only way to get a graphical interface back that I have found is by doing a reinstall.

It just seems that when the nvidia driver is loaded DKMS is not using it correctly, and any attempts I have made to change the driver at that point through the traditional xorg.conf is not working.

To me, this is a major bug.  Enabling the drivers through any package manager or the restricted driver manager should not result in breaking X in a way that you can't at least default back to the nv driver.

I appreciate the post but like I said, I have tried installing the driver in many ways.  Each way it installs fine with no errors, but then cannot start X.  Says it cannot find any screens.

---

### Post by skankster on 2008-10-30
I'm getting the same issue. The drivers appear installed in Synaptic but the system doesn't think they're there. If I use the Hardware drivers dialogue and try and Activate NVidia 177 it pops up a dialogue for a couple of seconds with a progress bar, then that goes away and nothing else happens. That's it.

I tried reinstalling the drivers, but with no affect. Not sure where I should be looking for any error messages.

---

### Post by celticninja on 2008-10-30
I too am having the same problem. I have activated using Jockey, but every time I reboot it pops up with the same error message. I went into the NVIDIA X SERVER SETTINGS and it says I am not using a NVIDIA X driver. Jockey says the driver is activated but not currently in use. I have reinstalled the drivers manually at least twice, yet to no avail.

Any help would be appreciated.

---

### Post by atomicbaum on 2008-10-30
Same problem here. Broadcom wireless driver worked right out of the box however. Never happened before.  I think its not connecting with the source server (I am connected to a wired network though). The "Downloading and Installing driver" box pops up and disappears. Tried both version 173 and 177. hmmmm.

---

### Post by Scaryclouds on 2008-10-31
> **Spinalcracker said:**
> Yes that will install the driver without error.  When you reboot, or try to restart X though it drops to a console, texted login and the only way to get a graphical interface back that I have found is by doing a reinstall.

It just seems that when the nvidia driver is loaded DKMS is not using it correctly, and any attempts I have made to change the driver at that point through the traditional xorg.conf is not working.

To me, this is a major bug.  Enabling the drivers through any package manager or the restricted driver manager should not result in breaking X in a way that you can't at least default back to the nv driver.

I appreciate the post but like I said, I have tried installing the driver in many ways.  Each way it installs fine with no errors, but then cannot start X.  Says it cannot find any screens.

This is the exact same problem I am having. My graphics card is 7950 GT, though this seems to be a driver and not a card issue, I'm also running X86-64.

---

### Post by faceoftheearth on 2008-10-31
I had the same problem as above. I did a clean install of 8.10 onto a computer with an Nvidia 6800. When I go to the restricted hardware drivers and try to activate either Nvidia 177 or 173 it pops up the gksudo, I auth, it then says it's downloading the driver and the bar goes back and forth on 0% for a second and then the box disappears without the driver being activated. This happens on any internet connection I try.

However, I ran the updater and it downloaded and installed some kernel header files and suddenly the driver activation worked. I'm not sure if it was because of the update or now but whatever it did it fixed it.

---

### Post by tootlet on 2008-10-31
I'm using AMD_64 version of Xubuntu and a 7600. I also can't get the restricted Nvidia drivers to install. It managed to get to 88% but then just stopped after multiple attempts. Haven't tried CLI yet but don't anticipate it working. Will keep an eye on this thread.

---

### Post by redredrooster on 2008-10-31
Sorry no answers just issues.

I have a done a fresh install of 8.10 64-bit and run the update manager after install, I have a nVidia 9600GT and when trying to install the drivers it will sit on 0% for a while then close.

---

### Post by Laibcoms on 2008-10-31
> **redredrooster said:**
> Sorry no answers just issues.

I have a done a fresh install of 8.10 64-bit and run the update manager after install, I have a nVidia 9600GT and when trying to install the drivers it will sit on 0% for a while then close.


Try this ^_^

Re-quoting myself:
> 
I am not sure if this will work, but I had a problem like yours that 177 won't activate.

So I did:
1) Open Synaptic Package Manager
2) Search nvidia
3) Installed all the 177 that are not yet installed (except those with the -dev suffix)
4) Made sure nvidia-settins is installed as well
5) Restarted
6) Went to "Hardware Drivers"
7) Activated 177
8) Voila

Hope that helps.
Then:
```

gksudo nvidia-settings

```

---

### Post by redredrooster on 2008-10-31
Hey thanks for the advice.

I ran 
```
gksudo nvidia-settings
```
and it seemed to sort out the issues straight away and now it runs fine.

---

### Post by skankster on 2008-10-31
It's a bit difficult to work on this issue right now, but I've checked in Synaptic and all the 177 stuff (except -dev) is installed. The driver still won't activate.

I tried running gksudo nvidia-settings but it just tells me that I'm not using nvidia drivers and to run nvidia-xconfig. I have tried doing that but it's not fixed anything.

So I need to work out at which point the failure's happening - is it not installing properly, or is it failing to load for some other reason. 

Can anyone post here what the correctly installed driver should look like on the file system (files, locations, permissions, configs, etc.) or point to somewhere that does (I haven't found one yet)? Then I can check the install side of it at least.

---

### Post by skankster on 2008-10-31
Fixed my issue.

See here: 

[http://ubuntuforums.org/showthread.php?p=6071927#post6071927](http://ubuntuforums.org/showthread.php?p=6071927#post6071927)

for details.

---

### Post by Jackbandit on 2009-02-20
Hey I am pretty new to linux and Ubuntu for the most part too. I had the same problem also. I had to click both the check mark boxes in the third party software tab of my software sources. That makes new nvidia drivers appear. Then do this > 
 
So I did:
1) Open Synaptic Package Manager
2) Search nvidia  
3) Installed all the 177 that are not yet installed (except those with the -dev suffix)
4) Made sure nvidia-settins is installed as well
5) Restarted
6) Went to "Hardware Drivers"
7) Activated 177
Voila


---

### Post by chipppy on 2009-02-20
Just a quick note.  Using both Ubuntu and Mythbuntu and also using both a 0400GT and 8400GS card on both system I use the restricted driver mananger to update to the lateset drive (not the 177 driver), and all has worked perfect so far.

---

### Post by vmwareee on 2009-03-07
If you are doing a new install the reason you can not enable the nVidia restricted driver is because the apt repository has not been update yet.

from a shell prompt : sudo apt-get update

Once the repository has been updated you will be able to enable the restricted driver.

---

### Post by norwoods on 2009-03-07
i update to the latest releases, 180.37 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using synaptic package manager.
i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
for a fresh install, you might also want or need:
jockey-common
jockey-gtk or jockey-kde
nvidia-settings
nvidia-xconfig

---

