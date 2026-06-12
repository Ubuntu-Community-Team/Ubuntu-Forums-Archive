---
title: "Ubuntu &amp; NVIDIA Drivers"
date: 2010-10-12
forum: Multimedia Software
---

### Post by Thrashdance on 2010-10-12
I've seen a lot of people asking about how to install NVIDIA drivers other than the proprietary ones. Since I was trying to do the same I decided to write a little guide on how I do it. There's a lot of ways to install them, this is just what works best for me and I'd like to share it.

Before I begin it's important to understand that NVIDIA drivers will integrate only with the Linux Kernel you are using. The installer must be run from the current kernel in use. To find the kernel you are using open a terminal and type:

*uname -r*

Right down the kernel so you are sure you don't forget it in case there are more than one kernels installed in your system.

Download the latest NVIDIA drivers for your graphics card: [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
Save them in a location you can remember.

This is optional in case you don't have root enabled.
Open a terminal and type:

*sudo passwd root*

Type the new password you want for root and now you can change to root or login as root any time you like.

This is also optional in order to keep GRUB up-to-date with your kernels if you recently upgraded or installed other Linux distributions
Open a terminal and type:

*sudo update-grub*

Reboot your system and in GRUB menu (if it doesn't show up press the SHIFT key immediately after BIOS load) choose the kernel that you previously wrote down in **recovery mode**. _Make sure the kernel you use is the same you boot into in recovery mode_.

After the system loads choose **Drop to root shell prompt** option.
Type the root password and you're logged in.
Now type:

*telinit 3 *

(This is because NVIDIA installer needs the specific runlevel to operate correctly)

After the system loads again type: *root *and then your password as before and you're logged in as root in runlevel 3.

Now go to the folder where you saved the NVIDIA drivers (e.g. if you saved them to your Desktop it would be something like this: /home/*yourusername/Desktop) *and type this:

*sh* _your-NVIDIA-drivers-version_.run

If the installer says that something failed but still offers an option to continue you continue.
If the installer finds that your NOUVEAU drivers are in use it will offer an option to disable them and the installation will continue after you reboot. You do that and make it again to runlevel 3 as you did before (no normal just select recovery mode from GRUB etc...) 

Now you run the installer again with the *sh* command as before and this time the installation will continue as intended with the NEUVEAU driver disabled. Some prompts and options will appear that are not all the same for all the NVIDIA drivers (e.g. it will offer to install 32-bit compatibility if you're using 64-bit OS so do it :) )

At the end it will ask to merge the existing configuration file with the new one. Do it.
When it's done it will drop you to the shell prompt again.
Type: *reboot*

This time boot in normal mode to your system and if everything went right you will have the latest NVIDIA drivers in your system.

Any tips or corrections are welcome :P

Hope I helped somebody.
Cheers!

---

