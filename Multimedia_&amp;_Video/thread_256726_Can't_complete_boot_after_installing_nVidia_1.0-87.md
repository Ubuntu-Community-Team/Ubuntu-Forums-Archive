---
title: "Can't complete boot after installing nVidia 1.0-8774 drivers"
date: 2006-09-13
forum: Multimedia &amp; Video
---

### Post by Giggity on 2006-09-13
So, after installing Google Earth, I was told that for it to run properly, I should update my graphics drivers.  Following this suggestion appears to have been a mistake, because I can't boot back into KDE.  I downloaded the nVidia drivers version 1.0-8774 from the nVidia site, followed the instructions, and the installation program completed with no problems.

I had to exit KDE to perform the installation.  Maybe these drivers will make Google Earth run better.  Trouble is, after rebooting, I can't complete the boot into KDE (kubuntu 6.06.1).  The little blue bar fills up completely while the boot process is listing, but then the screen blanks, and an instant later, the "kubuntu" splash is back up with the blue bar empty, as if nothing has loaded.

The computer is still responsive, because I can still Ctrl-Alt-Del to shut it down and reboot it.

What gives?  Was updating my drivers an extremely stupid thing for me to try?  How do I go about uninstalling these drivers so I can boot back into KDE?

---

### Post by tseliot on 2006-09-13
Boot in Recovery mode and try this:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#HOW_TO_UNINSTALL_THE_DRIVER_.28FROM_METHOD_2.29](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#HOW_TO_UNINSTALL_THE_DRIVER_.28FROM_METHOD_2.29)

Read where it says "HOW TO UNINSTALL THE DRIVER (FROM METHOD 2)"

---

### Post by Giggity on 2006-09-13
Thanks, I'll try that when I get home from school (in about 10 hours from now, and I'll let you know how it works out!

---

### Post by Giggity on 2006-09-14
Okay, so your advice worked like a charm to get me back to where I started, using the opensource "nv" drivers.  Just for kicks, I tried installing the drivers again, using "Method 1" in that link you provided (I had apparently used "Method 2" previously, having used the installer provided directly by nVidia).

Method 2 yielded the same unfortunate result.  The kernel loads and shows me the "kubuntu" splash screen with the blue bar, with everything saying [ok] during the boot.  But then, the screen goes blank for a second or so, then reappears with the kubuntu splash screen, only now the blue bar is all dark.  I had to repeat the uninstallation to get back here.

What gives?  I'm sorry to bother with such basic problems, and simplistic descriptions of what's going on, but I didn't see this listed under the "Problems" header in the link you sent above.

I suppose I can just go ahead and continue using the "nv" drivers, but Google Earth is complaining that my drivers are insufficient (it shows in the application's performance), and wants me to update with new drivers.

Anxiously awaiting your sage advice...

---

### Post by tseliot on 2006-09-14
uninstall the driver from Method 2 again.

Use method 1

and try point 4 of the Problems Section

---

### Post by Giggity on 2006-09-14
Well, on the bright side, I've grown quite proficient at uninstalling the driver after failures!  But, alas, I'm afraid that section 4 of the Problems header did not solve my problem.  The kernel boots, and all drivers load with [ok] status, but then the screen blanks, and the splash screen returns with the blue bar empty (dark blue), and nothing happening, also, the boot messages are gone.

[quote="Help File, Problems #4"]...your system freezes but you can still move the mouse pointer...[/quote]

I should mention, however, that the computer is *not* frozen, per se.  Indeed, when the blue bar splash is displayed (with no boot messages underneath), I can hit Ctrl-Alt-Del at any moment, and the shutdown procedure commences!  Also, there is no pointer to be able to move like it says.

Thanks for your continued patience!

---

### Post by tseliot on 2006-09-14
post the output of this command:
```
lspci -n | grep 300
```

---

### Post by Giggity on 2006-09-14
```
rob@rob-desktop:~$ lspci -n | grep 300
0000:05:00.0 0300: 10de:0091 (rev a1)
```I have no idea what any of that means, but then again, I'm no "Master Roaster".  I hope this tells you what you need to know, but for now I'm gonna have to get some sleep.  I'll check back in the morning.

Thank you so much for your vigilance.

---

### Post by tseliot on 2006-09-14
Your card is a GeForce 7800 GTX right?

let's try to diagnose the error:

Boot with the "nv" driver in your xorg.conf

Then (after Ubuntu has booted) Set the driver to "nvidia" in your /etc/X11/xorg.conf
Log out and Press CTRL+ALT+F1

You will get to the command line (no GUI)
Type:

```
sudo /etc/init.d/gdm stop (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm stop (if you use KDM)
```

Then:
```
startx -- -verbose 5 -logverbose 5
```

You will see several lines with the same error.

Then if you can't get to the command line press CTRL+ALT+F1 or CTRL+C (select NO if it asks you if you want to see the output of the error or something like that)

Then type this in order to copy the output of the error to your home folder:
```
sudo cp /var/log/Xorg.0.log /home/your_username/Xorg.0.log
```
(Of course you have to replace "your_username" with your username)

Access the GNOME or KDE again in the following way:
```
sudo nano /etc/X11/xorg.conf
```
Set the driver back to "nv" instead of "nvidia"
CTRL+O to save
CTRL+X to exit

Then
```
sudo /etc/init.d/gdm restart (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm restart (if you use KDM)
```


Post the content of that file (which you can find under /home/your_username/Xorg.0.log )

---

### Post by Giggity on 2006-09-14
It's very large, so I'll just attach the log rather than post it inline.  This has all been very interesting finding out how to tweak these little "behind-the-scenes" files =].

I had fully uninstalled the driver, and removed all directories before performing that last task, however.  Was I supposed to do this with the nVidia drivers still on my system?

---

### Post by tseliot on 2006-09-14
can you post the output of this command:
```
uname -r
```

---

### Post by Giggity on 2006-09-14
```
rob@rob-desktop:~$ uname -r
2.6.15-26-386
```And in new breaking developments, I'm now unable to "Power On" my WindowsXP Professional VM in VMWare Workstation v5.5.2 build-29772 (it's the first time I've tried since the beginning of this current fiasco).  VMWare Workstation loads properly, but when "Power On" is pressed, the following series of error dialogs is presented:
```
Could not open /dev/vmmon: No such file or directory.
Please make sure that the kernel module `vmmon' is loaded.
``````
Failed to initialize monitor device.
``````
Unable to change virtual machine power state: Cannot find a valid peer process to connect to.
```I gather this has something to do with when I executed: ```
sudo dpkg-reconfigure xserver-xorg
```to reinstall the "nv" driver after uninstalling the nVidia proprietary driver.

I'm sorry if I seem to keep dragging this farther away from solution!

---

### Post by Giggity on 2006-09-14
Never mind that trouble with VMWare... i ran:
```
rob@rob-desktop:~$ sudo /etc/init.d/vmware start
Password:
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done

```
and now it works properly... I don't know what made me have to do that, though!

Solution:  I had started KDE from bash in recovery mode, which does not load the necessary drivers for VMWare and other non-essential processes...

Now that that's out of the way, we can go on with finding out what's wrong with my nVidia driver installations...

---

### Post by Giggity on 2006-09-15
I thought I'd mention that while eagerly awaiting your return, I've tried installing the legacy drivers (Method 1).  This fails in the same manner.  I hope that helps you narrow down my particular problem...

---

### Post by tseliot on 2006-09-15
read this thread:
[http://ubuntuforums.org/showthread.php?t=257459](http://ubuntuforums.org/showthread.php?t=257459)

---

### Post by Giggity on 2006-09-15
Hmmm... nothing in that thread seems to address the problem.  I received update/upgrade alerts shortly before your last post, and let the manager update the kernel and all.  I then tried reinstalling the nVidia drivers, and restarted the machine, and again after the boot processes finish, just "kubuntu" with a dark blue bar underneath it and nothing more.  It's not frozen, as I can still ALT-F1 to get back to bash login, and I can Ctrl-Alt-Del to reboot the machine.

Just can't get the Desktop Manager to load.  This makes me sad.

uname-r still says:
```
rob@rob-desktop:~$ uname -r
2.6.15-26-386
```

---

### Post by tseliot on 2006-09-15
Try Envy:
1) use the Uninstall function
2) then use the Install function

you can get it here:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)

---

### Post by Giggity on 2006-09-15
Success!

I am not sad anymore.  This time, when I Alt-F1'ed out of the "kubuntu blue bar" screen, I actually saw activity... this was envy in operation, redownloading and installing the driver.

When asked if I wanted to restart the X Server, I said yes, and this time, a nice little nVidia splash flashed on the screen for an instant, and KDE was up and running.

Google Earth runs much smoother now, and I suppose many more applications will do the same thanks to this new driver.  Thank you very much for your assistance in its installation, and especially your patience!

---

