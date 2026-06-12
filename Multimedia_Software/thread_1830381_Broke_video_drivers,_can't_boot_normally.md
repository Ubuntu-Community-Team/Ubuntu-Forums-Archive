---
title: "Broke video drivers, can't boot normally"
date: 2011-08-21
forum: Multimedia Software
---

### Post by hyper2hottie on 2011-08-21
I recently got a second monitor and while I was trying to get it to work in ubuntu I found in Additional Drivers that the nvidia_current driver was activated but not in use.  I decided to find out what this means and in another thread I was told to follow these commands.

```
sudo apt-get remove --purge nvidia*
sudo apt-get install nvidia-current
sudo nvidia-settings

          (saved xorg config here, said default device was not a valid field)

sudo update-grub
         (had seen that this problem had once in the past been caused by grub booting the wrong kernel)
uname -a
        (checked against the new grub file)
```I followed the steps and rebooted.  At this point I found I couldn't boot without going into safe mode and restarting x.

When I looked at the error messages given in safe mode it said that x server was already running for screen 0.

I have fiddled for about a week with no luck.  My current xorg.conf, Xorg.0.log, and etc/modules files are attatched.

I do know that I could just do a fresh install, and I will if no one has any ideas, but that hardly seems fun.

Thank for any help.

EDIT: I forgot to mention that i have a NVIDIA GeForce GTX 560 Ti graphics card.

---

### Post by hyper2hottie on 2011-08-22
bump

---

### Post by BicyclerBoy on 2011-08-22
The jockey driver method seems to be broken & reports the driver is not in use, I would not trust it or use it.

Open synaptic manager
click reload
search for nvidia
re-install the nvidia-current package.
click on details & study the process
check for errors..


nvidia 270 seems to support the GTX560ti but you can get later drivers from..
x-swat team ppa or xorg-edgers launchpad ppa.

I would backup/delete your xorg.conf file
then run
nvidia-xconfig
to make a new one.

reboot then post /var/log/Xorg.0.log again..

---

### Post by hyper2hottie on 2011-08-22
So i tried to reinstall nvidia-current from synaptic.  That didn't fix it. 
I attached the log file from that. 
There were no errors during the install.

I decided to try out the nvidia 280 driver from x-swat.  That also did not work.
I attached the log file from that boot as well.
There were no errors during install.

An interesting point to note is that to run nvidia-xconfig I must type:
sudo /usr/lib/nvidia-current/bin/nvidia-xconfig


I am starting to wonder if I have broken something other than my drivers.
I have reinstalled them a lot of times.

Oh and when i go into safe mode and say to boot into low graphics mode there is an option to look at startup errors.   It stills say that it is unable to start x-server because it is already running for display 0.

---

### Post by BicyclerBoy on 2011-08-23
nvidia-settings & nvidia-xconfig should be in the path..

Have you previously installed nvidia driver from console login ?
As root ?

Both your monitors are plugged into the GTX560 ?

I would use this sequence
sudo apt-get remove --purge nvidia*
sudo update-grub

< reboot>
sudo apt-get update

---

### Post by realzippy on 2011-08-23
Your logfile clearly shows the problem:


```
[    15.459] (II) LoadModule: "nvidia"
[    15.471] (WW) Warning, couldn't open module nvidia
[    15.471] (II) UnloadModule: "nvidia"
[    15.471] (II) Unloading nvidia
[    15.471] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    15.471] (EE) No drivers available.
```

You might try:
```
sudo dpkg-reconfigure nvidia-current
```

```
sudo apt-get install linux-generic
```

---

### Post by hyper2hottie on 2011-08-24
@realzippy- no luck with those commands.  No change in errors and the log didn't change either.

@BicyclerBoy
- both monitors are hooked into the gtx 560.
- those commands do not seem to have helped.  My Xorg.0.log is now empty but I still can't boot normally. Not sure what that means yet.
-I have never installed the drivers from console login.  I don't actually know what to do for that .

Thanks.

Edit: Ok i booted in again and it still failed.  This time it froze at "stopping user bootsplash" or "stopping user bootspace". It used to freeze at "checking battery state".  The log has returned to the usual "can't load driver nvidia".

---

### Post by BicyclerBoy on 2011-08-24
Your Xorg.0.log file shows kernel 2.6.38-10 Jun 28th.
The current 11.04 kernel is 2.6.38-11.

Wild conjecture follows..
The graphics driver install has a kernel-space module & a user-space driver module.
The kernel module is compiled against your kernel version & is made part of the kernel boot image.
Maybe you still have one half without the other.

Maybe a newer kernel install with the nvidia drivers un-installed will boot properly..
Remove the nvidia driver before updating kernel.
If you run synaptic (or update manager) & clicked reload, then mark all updates you should get a new kernel build. 
Check the new kernel is booted/loaded with
uname -r
Confirm the computer works okay before trying the nvidia driver again.

Does your machine boot properly from the install/live CD/DVD ?

---

### Post by hyper2hottie on 2011-08-25
Ok I got it to boot normally by doing
```

sudo apt-get remove --purge nvidia*
sudo update-grub
sudo rm /etc/X11/xorg.conf

```
I was previously only purging nvidia and updating grub, then changing the xorg.conf to load nouveau drivers. I will try update the kernel now and then attempt to reinstall the nvidia drivers.

---

### Post by hyper2hottie on 2011-08-25
I updated the kernel and was still able to boot normally, so long as the xorg.conf file was deleted.
After reinstalling the drivers I did the following:
```

hyper2hottie@hyper2hottie-MS-7642:~$ sudo /usr/lib/nvidia-current/bin/nvidia-xconfig

WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'


```
So i thought I would replace the xorg.conf file with a backed up version, then call nvidia-xconfig. 
It said that it worked except it did not change the xorg.conf file.  It stayed the same as the old one.  So for some reason my nvidia-xconfig doesn't work properly.

---

### Post by realzippy on 2011-08-25
```
New X configuration file written to '/etc/X11/xorg.conf'
```

So it seems to work..
You can open the file,on it's top there should be an info about
time/date/tool which created it.

---

### Post by hyper2hottie on 2011-08-25
Well I guess I failed to read that message properly.  Sorry about that.
So now that an xorg.conf file exists I can not boot normally.  I still get errors about my nvidia drivers not existing.  I attatched my current xorg.conf and Xorg.0.log files. 
The xorg.conf file header seems correct except that it is clearly august, not july.

---

### Post by BicyclerBoy on 2011-08-26
The later video drivers do not need the xorg.conf file except in special circumstances..
Don't replace the new one with your old file..there is nothing in it worth keeping.
So I suggest you delete your 
/etc/X11/xorg.conf
(burn it in the back yard on the bbq)

Please run these cmds..
which nvidia-xconfig
which nvidia-settings

& run this with **NO PATH**.
[sudo] nvidia-xconfig

This program is NOT installed at the path your were using..

Please check the log file you were postings as from
/var/log/Xorg.0.log ??? yes no ??

---

### Post by realzippy on 2011-08-26
```
[    17.714] (II) LoadModule: "nvidia"
[    17.728] (WW) Warning, couldn't open module nvidia
[    17.728] (II) UnloadModule: "nvidia"
[    17.728] (II) Unloading nvidia
[    17.728] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    17.728] (EE) No drivers available.
[    17.728] 
Fatal server error:
[    17.728] no screens found
```

---

### Post by BicyclerBoy on 2011-08-26
Yes, sadly I did see that..
If that log file did not have the correct date I would have suspected the file was an older backup copy.

---

### Post by hyper2hottie on 2011-08-26
Ok here is the results of those commands.

```

hyper2hottie@hyper2hottie-MS-7642:~$ which nvidia-xconfig
hyper2hottie@hyper2hottie-MS-7642:~$ which nvidia-settings
/usr/bin/nvidia-settings
hyper2hottie@hyper2hottie-MS-7642:~$ sudo nvidia-xconfig
sudo: nvidia-xconfig: command not found

```

The reason I was running the other xconfig was because this one says command not found.  So I tried to find the full path through google.  Guess I found a bad path. Oops.

The log file is the one from /var/log/Xorg.0.log

---

### Post by hyper2hottie on 2011-08-27
I've done that.  Many times.  I have uninstalled the drivers through command line, synaptic, and the additional drivers method.  I have also installed a newer version of the drivers, hoping that would fix it.  So far nothing has worked.

---

### Post by BicyclerBoy on 2011-08-27
I know this stating the patently obvious but..your nvidia driver install is really badly broken.

The reason I asked you to check the path info was to find out why you were using a full path to nvidia-xconfig.
It is normally in the /usr/bin/ folder .

Do you have a folder 
/usr/lib/nvidia-glx-280   ? or similar ?

My limited experience does not include anything like your problem.
But I would like to know how you ended up in this situation...
I don't think your driver install is completing without fatal error.
Is there anything in
/var/log/dpkg.log   file about nvidia ?

---

### Post by hyper2hottie on 2011-08-28
I have a nvidia-current folder in usr/lib.  That is the only folder with nvidia in the name.  Synaptic says I have nvidia installed.

There is a rather exceptional amount of stuff in there about nvidia.
Most of the nvidia stuff looks like this:
```


2011-08-24 22:16:31 install nvidia-current <none> 280.13-0ubuntu1~natty~xup1
2011-08-24 22:16:31 status half-installed nvidia-current 280.13-0ubuntu1~natty~xup1
2011-08-24 22:16:37 status triggers-pending man-db 2.5.9-4
2011-08-24 22:16:37 status half-installed nvidia-current 280.13-0ubuntu1~natty~xup1
2011-08-24 22:16:41 status unpacked nvidia-current 280.13-0ubuntu1~natty~xup1
2011-08-24 22:16:41 status unpacked nvidia-current 280.13-0ubuntu1~natty~xup1
2011-08-24 22:16:41 install nvidia-settings <none> 280.13-0ubuntu1~natty~xup1
2011-08-24 22:16:41 status half-installed nvidia-settings 280.13-0ubuntu1~natty~xup1
2011-08-24 22:16:41 status half-installed nvidia-settings 280.13-0ubuntu1~natty~xup1
2011-08-24 22:16:41 status unpacked nvidia-settings 280.13-0ubuntu1~natty~xup1
2011-08-24 22:16:41 status unpacked nvidia-settings 280.13-0ubuntu1~natty~xup1
2011-08-24 22:16:41 trigproc man-db 2.5.9-4 2.5.9-4
2011-08-24 22:16:41 status half-configured man-db 2.5.9-4
2011-08-24 22:16:43 status installed man-db 2.5.9-4
2011-08-24 22:16:44 startup packages configure
2011-08-24 22:16:44 configure nvidia-current 280.13-0ubuntu1~natty~xup1 <none>
2011-08-24 22:16:44 status unpacked nvidia-current 280.13-0ubuntu1~natty~xup1
2011-08-24 22:16:44 status unpacked nvidia-current 280.13-0ubuntu1~natty~xup1
2011-08-24 22:16:44 status half-configured nvidia-current 280.13-0ubuntu1~natty~xup1
2011-08-24 22:17:17 status installed nvidia-current 280.13-0ubuntu1~natty~xup1
2011-08-24 22:17:17 status triggers-pending python-gmenu 2.30.5-0ubuntu3
2011-08-24 22:17:17 status triggers-awaited nvidia-current 280.13-0ubuntu1~natty~xup1
2011-08-24 22:17:17 status triggers-pending bamfdaemon 0.2.90-0ubuntu3
2011-08-24 22:17:17 status triggers-awaited nvidia-current 280.13-0ubuntu1~natty~xup1
2011-08-24 22:17:17 configure nvidia-settings 280.13-0ubuntu1~natty~xup1 <none>
2011-08-24 22:17:17 status unpacked nvidia-settings 280.13-0ubuntu1~natty~xup1
2011-08-24 22:17:17 status half-configured nvidia-settings 280.13-0ubuntu1~natty~xup1
2011-08-24 22:17:18 status installed nvidia-settings

```

I would upload it but its 280KB so thats a no go.

This is the first mention of nvidia 
```


2011-08-08 21:55:33 status installed nvidia-current 270.41.06-0ubuntu1
2011-08-08 21:55:36 remove nvidia-current 270.41.06-0ubuntu1 <none>
2011-08-08 21:55:36 status half-configured nvidia-current 270.41.06-0ubuntu1
2011-08-08 21:55:59 status triggers-pending python-gmenu 2.30.5-0ubuntu3
2011-08-08 21:56:00 status half-configured nvidia-current 270.41.06-0ubuntu1
2011-08-08 21:56:00 status triggers-pending bamfdaemon 0.2.90-0ubuntu3
2011-08-08 21:56:00 status half-configured nvidia-current 270.41.06-0ubuntu1
2011-08-08 21:56:00 status triggers-pending libc-bin 2.13-0ubuntu13
2011-08-08 21:56:00 status half-installed nvidia-current 270.41.06-0ubuntu1
2011-08-08 21:56:00 status triggers-pending man-db 2.5.9-4
2011-08-08 21:56:00 status half-installed nvidia-current 270.41.06-0ubuntu1
2011-08-08 21:56:00 status config-files nvidia-current 270.41.06-0ubuntu1
2011-08-08 21:56:00 status config-files nvidia-current 270.41.06-0ubuntu1
2011-08-08 21:56:00 trigproc python-gmenu 2.30.5-0ubuntu3 <none>
2011-08-08 21:56:00 status half-configured python-gmenu 2.30.5-0ubuntu3
2011-08-08 21:56:01 status installed python-gmenu 2.30.5-0ubuntu3
2011-08-08 21:56:01 status triggers-pending python-support 1.0.10ubuntu3
2011-08-08 21:56:01 trigproc bamfdaemon 0.2.90-0ubuntu3 <none>
2011-08-08 21:56:01 status half-configured bamfdaemon 0.2.90-0ubuntu3
2011-08-08 21:56:01 status installed bamfdaemon 0.2.90-0ubuntu3
2011-08-08 21:56:01 trigproc libc-bin 2.13-0ubuntu13 <none>
2011-08-08 21:56:01 status half-configured libc-bin 2.13-0ubuntu13
2011-08-08 21:56:01 status installed libc-bin 2.13-0ubuntu13
2011-08-08 21:56:01 trigproc man-db 2.5.9-4 <none>
2011-08-08 21:56:01 status half-configured man-db 2.5.9-4
2011-08-08 21:56:02 status installed man-db 2.5.9-4
2011-08-08 21:56:02 trigproc python-support 1.0.10ubuntu3 <none>
2011-08-08 21:56:02 status half-configured python-support 1.0.10ubuntu3
2011-08-08 21:56:04 status installed python-support 1.0.10ubuntu3
2011-08-08 21:56:06 startup packages remove
2011-08-08 21:56:06 status installed nvidia-settings 270.29-0ubuntu1
2011-08-08 21:56:06 remove nvidia-settings 270.29-0ubuntu1 <none>
2011-08-08 21:56:06 status half-configured nvidia-settings 270.29-0ubuntu1
2011-08-08 21:56:06 status half-installed nvidia-settings 270.29-0ubuntu1
2011-08-08 21:56:06 status triggers-pending man-db 2.5.9-4
2011-08-08 21:56:06 status half-installed nvidia-settings 270.29-0ubuntu1
2011-08-08 21:56:06 status config-files nvidia-settings 270.29-0ubuntu1
2011-08-08 21:56:06 status config-files nvidia-settings 270.29-0ubuntu1
2011-08-08 21:56:06 status config-files nvidia-settings 270.29-0ubuntu1
2011-08-08 21:56:07 status config-files nvidia-settings 270.29-0ubuntu1
2011-08-08 21:56:07 status not-installed nvidia-settings <none>

```

As for how I ended up in this situation.  Well I can't really give you any more information than I gave in the first post.  I'm guessing that when I tried to purge nvidia and install the purge didn't work and then the install broke.  Thats the best guess I have.

So it's not looking to promising for fixing this.  I'm going to try a clean install in a day or two, unless you have more suggestions or would like to get more information about whats happened.  I'm not in a huge hurry to fix this so if you want me to try more stuff I can. 

Other than that I'd like to say thanks for all the help.  It's been fun and I learned a lot.

---

### Post by BicyclerBoy on 2011-08-28
The folder /usr/lib/nvidia-current seems okay for 11.04 install.
I just use the std repos version 270.

My 10.04 HTPC uses a 3rd party nvidia ppa & has different folder name..

Nothing stands out in the dpkg log file..

From my basic understanding..
Somewhere there should be a log file listing the driver unpacking/compiling the kernel module with the linux headers package & then inserting it into the boot image with dkms.
I don't know where this log file is..

---

### Post by Panna-cakkhu on 2011-12-01
I have exactly the same problems in Ubuntu 11.10 and after weeks on it i switched back to Ubuntu 10.04... and same problem again!! I'll try to fix it and let you know of the results. The main problem (obviously) is that the Nvidia module is not loaded.

PS: i also have a GTX 560

---

### Post by Panna-cakkhu on 2011-12-01
Ok i found a solution, hope it works for others! Here is what i did:

1) Download the latest Nvidia drivers from [here]("http://www.nvidia.com/Download/index5.aspx?lang=en-us")

2) Blacklist a certain number of modules

    gksudo gedit /etc/modprobe.d/blacklist.conf

    Add this:

    blacklist vga16fb
    blacklist nouveau
    blacklist rivafb
    blacklist nvidiafb
    blacklist rivatv

3) Purge all previous Nvidia drivers installed files:

    sudo apt-get --purge remove nvidia-*

4) Reboot

5) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)

6) Login and cd to the directory where you saved your file

7)Install drivers

    sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run

(I choose the 32-bit OpenGL compatible drivers for my 64-bit system and also accepted to configure X and thus create a new Xorg.conf file )

---

### Post by BicyclerBoy on 2011-12-02
For this to succeed you need the:
- linux kernel headers package (that matches the current kernel)
- build tools etc
- ia32 bit libraries package to build the 32bit openGL support (Wine etc).

most folks do not have any of these installed..

The driver package readme file spells out every step..

The blacklisting should be done by the driver package install scripts..

---

