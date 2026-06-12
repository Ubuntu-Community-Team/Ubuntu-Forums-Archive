---
title: "nvidia driver installation hangups"
date: 2012-07-29
forum: Multimedia Software
---

### Post by G4dget on 2012-07-29
Yet again posting to try and figure out the exact problem I am encountering.

I want to install the newest nvidia drivers from the web (driver 295.59) as the nvidia-current from either synaptic or hardware drivers is not installing properly or offer the same support for my card (Geforce 9800 GT) that the new driver does.

I understand the steps needed to do this as far as disabling X-server and the nouveau drivers.

If I drop to a root shell from recovery without blacklisting the nouveau drivers then the install script fails because of the nouveau drivers running. If I blacklist the nouveau driver I can boot normally into a gdm environment but if I try to ctrl+alt+(F1,F2,F3) then the screen flickers and the hangs up with with a bad image of the desktop with a bunch of lines through it. The only thing to do is to ctrl+alt+del to reboot the computer.

With nouveau driver still blacklisted if I try to boot to recovery mode from Grub it never gets to the point of asking how far I want to boot (ie shell with networking, shell, recovery) and just hangs on a blank screen and have to ctrl+alt+del to reboot.

I have tried to edit from grub using "nomodeset" "single" and forcing vga=769 with no luck. Either boot hangs on blank screen or boots normally to gdm environment. 

The only thing I can think to do but not sure how is to un-blacklist nouveau and boot to root shell from recovery and unload nouveau from the kernal without rebooting.

I tried this using ```
rmmod nouveau
``` but get a response of that the module is in use.


-Note I was going to give up on trying to install newest drivers and just use nvidia-current from hardware drivers as at this point i think I just needed to unload nouveau and reboot for the nvidia to take effect but now my computer does not even recognize that there is a nvidia card installed as hardware drivers just turns up blank. This could be due to using ```
sudo apt-get remove --purge nvidia*
```


-Note2
I just want to do multimedia editing (Ubuntu Studio) on my desktop so if I can do this without the nvidia driver and just use nouveau (however they dont fully support my specific card GeForce 9800 GT) and tweeak that then I will.

-Note3
Currently using kernel 3.0.0-23-generic on 10.04.4 Should I get backports or a newer kernel if I keep using nouveau

---

### Post by G4dget on 2012-07-29
So since I had just installed ubuntu 10.04.4 and had separate drives for storage I went ahead and just re-installed to start fresh. Before doing so I was able to get the newest driver installed by using this ppa ```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
```

However I still had a few issues to actually have synaptic get it installed and once installed was unable to successfully blacklist nouveau to keep them from loading and was unable to update the x-server using ```
sudo nvidia-xconfig
``` as it would return an error of command not found.

May not have had to do a complete re-install but figured that might be best for the time being in getting the issue fixed and having a concise install. 

2 main issues still unresolved at the moment are

1 - If using the repositories or Hardware Drivers (even the first time around) was unable to use ```
sudo nvidia-xconfig
``` as it always returned command not found

2 - When trying to use the install script from nvidia.com I always received an error that nouveau was still in use but if I blacklisted it then I was unable to drop to or boot to shell (blacklisting worked at that point)

---

### Post by G4dget on 2012-07-29
Marking this solved I (even though I formatted and re-installed), as I now have the recommended driver from nvidia installed and working correctly. Here are the steps I took following a fresh install and updates (via Update Manager including all the nvidia stuff that was suggested) of Ubuntu 10.04.4 with kernal 3.0.0-23-generic

1. After restart I selected the nvidia-current(recommended) driver from Hardware Drivers which failed (as this one did not support my card I believe)

2. Ran ```
sudo nvidia-xconfig
```

3. Restart

4. Upon boot from restart I was notified that the nvidia driver was unable load due to no driver present

5. Blacklist nouveau via ```
gksu gedit /etc/modprobe.d/blacklist.conf
``` then adding "blacklist nouveau" at the bottom of page

6. Download the recommended driver from [[COLOR="Blue"]*here*[/COLOR]]("http://www.nvidia.com/Download/index.aspx?lang=en-ushttp://") and save it where ever you like.

7. Reboot and at the Grub Menu select your current kernel's recovery option and go to a root shell with no networking

8. Once shell is loaded check that no drivers are currently loaded for your card with ```
lshw -c display
``` print out should resemble this ```
  *-display               
       description: VGA compatible controller
       product: Radeon Mobility M6 LY
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list rom
       configuration:latency=66 mingnt=8 resources: irq:11 memory:e8000000-efffffff(prefetchable) ioport:3000(size=256) memory:d0100000-d010ffff memory:d0120000-d013ffff(prefetchable)

``` noting that no driver is displayed. (this is from my laptop so hence why its not an nvidia card.)

9.Now you can install the actual driver by running this ```
sudo sh /home/"usrname"/Downloads/N[tab]
``` or whatever directory you saved it to. I used the tab completion feature to avoid typing the whole name out.

10. The install will warn you that you should run this in runlevel 3 however when I tried to ```
telinit 3
``` my computer just froze and I had to ctrl+alt+del to reboot. So I just went ahead with the install in runlevel 1 and just let it do the rest.

11. After install was finished I went ahead and used ```
reboot
```
After I was logged back into my Desktop I was able to use the Nvidia Settings App and set up my second monitor and do everything else that I should be able to. Going to find a Linux video benchmark and see about tweaking the settings and will post later.

---

