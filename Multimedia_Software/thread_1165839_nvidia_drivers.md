---
title: "nvidia drivers"
date: 2009-05-21
forum: Multimedia Software
---

### Post by smurfgod on 2009-05-21
I just installed the jaunty jackelop and am trying to configure my nvidia driver for dual screens.When I go to the nvidia x server thingy it says "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. " I tried to find the config file to change it(to what I don't know)...I have no idea what I am doing.I want to run dual screens.I have an nvidia mx440 grphics card. i downloaded the driver from nvidia but when i install it it says "gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again."


What can I do.I need the dual screens so I can watch my movies.I had Intrepid and it was easy but know I can't set it up.Please help.

thanks

smurf

---

### Post by vikingsraven on 2009-05-21
Im getting the same thing NVidia Geforce 8500, tried envy NG and that doesnt work either says the kernel header is missing.
NOOBIE by the way, so be gentle.:)

---

### Post by stefangr1 on 2009-05-21
This could have to do with the fact that Ubuntu has already some Nvidia stuff installed by default. If you don't delete that first, it might not work. You can delete them by:

sudo apt-get remove nvidia-glx

You can get the kernel headers of your running kernel with:

sudo apt-get install linux-headers-`uname -r`

If you go to the installation procedure again after this and let the installer update your xorg.conf, there's a good chance that things will work.

---

### Post by smurfgod on 2009-05-21
i got mine to work but the only way to get dual screens is to have them as clones and I was needing independent screens.I am dual booting and ubuntu seems slow.Is it cuz i'm dual booting??

---

### Post by stefangr1 on 2009-05-21
No, when you're dual booting the operating systems are really independent and not aware of each other. I'm not sure why Ubuntu is slow on your system (though you shouldn't expect it to be faster than windows).

---

### Post by lukeiamyourfather on 2009-05-21
You really don't even need the proprietary nVidia drivers for that card, and the current drivers on their site might not even support that card. With a fresh install of Ubuntu you should be able to go to the screen resolution properties in GNOME and deselect the mirror option, then click okay. After that the desktop should be extended across both monitors. Cheers!

---

### Post by smurfgod on 2009-05-22
After I typed that last response I said "Screw MS" and whiped it out.I know only have Ubuntu and I can-not get my dual screens to run as I want them.As it stands right know,I do have dual screens running,but it's as clones.I can-not get 2 independent screens.I didn't have to download the drivers from Nvidia.

Also,I installed Wine and have uTorrent installed but can't get my port to forward.I thought I could just keep it the same within uTorrent,just have it go to the port I had forwarded with Windows but it's not letting me do it.If someone could let me know about that to,that would be great.


smurf

---

### Post by stefangr1 on 2009-05-22
> **smurfgod said:**
> After I typed that last response I said "Screw MS" and whiped it out.I know only have Ubuntu and I can-not get my dual screens to run as I want them.As it stands right know,I do have dual screens running,but it's as clones.I can-not get 2 independent screens.I didn't have to download the drivers from Nvidia.

Also,I installed Wine and have uTorrent installed but can't get my port to forward.I thought I could just keep it the same within uTorrent,just have it go to the port I had forwarded with Windows but it's not letting me do it.If someone could let me know about that to,that would be great.


smurf


You have to do the port forwarding on your router. The problem is probably that the port your forwarded to windows is not the default port in utorrent. So if you know what port you forwarded to your windows torrent client, you can just change it in the utorrent settings, otherwise you first have to find that out.

---

