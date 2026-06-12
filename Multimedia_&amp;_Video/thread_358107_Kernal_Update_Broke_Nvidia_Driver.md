---
title: "Kernal Update Broke Nvidia Driver"
date: 2007-02-10
forum: Multimedia &amp; Video
---

### Post by awells527 on 2007-02-10
I upgraded to the 2.6.17-11-generic kernal this morning, and it broke my nvidia driver.  When I rebooted, X server failed to start.  The error message said that no screens were found - even if I reset the config file from scratch (nvidia-xconfig && dpkg-reconfigure -phigh xserver-xorg).  Nothing worked.  The only way to get my computer to boot was to go back to the nv driver, and that won't work.

I was using the beta nvidia drivers at the time, so I removed that extra repository, removed the drivers, and reinstalled the current release ones.  Still no luck.

Any advice would be greatly appreciated.

---

### Post by greenrabbi on 2007-02-10
Same problem. I rolled back to the previous kernel which fortunately was still on my boot menu, (for some reason, when I formatted windows off my computer, it keep the boot menu) 

As a side note, Is this abnormal to have the old kernel available to boot from? 

Is this going to be fixed in the near future so that I can upgrade without it messing up my graphics driver?

I'm a linux newbie... so, when I get locked out, I am somewhat doomed to being able to fix it. Luckily I could just roll it back.

---

### Post by zdotz on 2007-02-10
Yep, same here:

Failed to load Nvidia kernel module!
Screen(s) found, but none have a useable configuration
Fatal server error: No screens found

---

### Post by spinflick on 2007-02-10
And here, I had to use the previous kernel.

---

### Post by ehowell on 2007-02-10
It broke for me as well, since I think that I did not have the appropriate kernel headers for nvidia which /etc/X11/xorg.conf was trying to load.

What I did was follow the [guide in Lunapark]("http://lunapark6.com/?p=2717") for installing Envy and getting the nvidia drivers that way.

Envy will go out and grab the latest nvidia drivers for you and the appropriate files needed.

After running envy everything is fine again!

If you don't have envy yet (this is from that Lunapark article):

```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu6_all.deb

sudo dpkg -i  envy_0.8.1-0ubuntu6_all.deb

then press Alt+Cntrl+F1 to kill X-Windows and type

envy
```

If you already had envy first do:

```
sudo aptitude purge envy

sudo rm -R /usr/share/envy
```

It's really easy and works like a charm! I suggest reading the whole article at Lunapark to get more info as well! :)

The whole thing took me about 5 minutes to reinstall the drivers.

Hope that helps!

---

### Post by noodles90210 on 2007-02-10
Same here, bloody hell cattle trucking proprietary drivers and companies releasing it (Hi nVidia!). :mad: :mad: :mad:

---

### Post by greenrabbi on 2007-02-10
I was reading and a bunch of people were saying that the drivers need to be reinstalled under the new kernel. It took a song and dance to get my dual moniters to function properly, especially with beryl. So I am leary to go through this entire process again just to get this new kernel.

How often are there kernel updates, and where can i find out the advatages of the new kernel... or  additions/fixes?

---

### Post by david_2001 on 2007-02-10
> **greenrabbi said:**
> As a side note, Is this abnormal to have the old kernel available to boot from?
Quite normal.  A kernel upgrade will not uninstall the current kernel automatically.  A kernel upgrade also means that any custom kernel modules, e.g. "latest" nvidia and lirc, will need to be recompiled, as people are finding out.

---

### Post by greenrabbi on 2007-02-10
> **ehowell said:**
> 

If you already had envy first do:

```
sudo aptitude purge envy

sudo rm -R /usr/share/envy
```

It's really easy and works like a charm! I suggest reading the whole article at Lunapark to get more info as well! :)

The whole thing took me about 5 minutes to reinstall the drivers.

Hope that helps!

I installed the beta drivers last time for nvidia... does this code reinstall the standard nvidia drivers, or will it reinstall the beta ones I have?

(I miss the good old days when I used to feel like I knew what the hell I was talking about...)

---

### Post by noodles90210 on 2007-02-10
ehowell's post resolved problem for me. Thx!

---

### Post by daverave999 on 2007-02-10
Ta very much ehowell! Helped me out too ;)

---

### Post by awells527 on 2007-02-10
> **daverave999 said:**
> Ta very much ehowell! Helped me out too ;)

Ditto.  Just got it working again.  Thanks!!

---

### Post by ikester8 on 2007-02-10
Thanks, ehowell! It worked very well. My question is, can I run envy the same way next time or do I have to uninstall and re-download the latest script?

---

### Post by 3rd Rook on 2007-02-11
ehowell's post worked for me too.

Now, if only the rest of Linux configuration (track-pad, WiFi, bluetooth, web cams) was that easy.  

Thanks ehowell!

Oh, by the way, the five minutes he mentions included browsing for this thread. ;o)

---

### Post by konungursvia on 2007-02-12
In my case I'm running an Inspiron with the GeForce 4400 from Nvidia. This morning I rebooted into the new kernel and Xserver broke down. Before trying to re-run Envy, I told xorg.conf to use the generic "nv" driver and commanded "startx" to get here. In other words, I don't think I should use the newest Nvidia driver, but a legacy. Does anyone know if Envy will select the right driver for me if I run it again? Or should I run a newer version of Envy at all? Thanks guys.

---

### Post by wilberfan on 2007-02-14
I've just nominated ehowell for Penquin of the Month!  \\:D/ 

I had to UNinstall the nvidia driver via envy and reinstall the kernel (?) then REinstall the driver to get things back to normal, but all seems well now!  

Now, do I understand correctly that this will have to be repeated following every kernel update, or...?

(God, I love this forum!  I'd probably be in an ignorant fog, saving money for V*sta right now if not for the likes of ehowell!)

---

