---
title: "Erratic video issues - Nvidia GT 640"
date: 2013-02-21
forum: Multimedia Software
---

### Post by RodBarnes on 2013-02-21
[I'm a computer engineer of about 30 years, mostly Windows.  Reatively new to Linux.]

I have two monitors connected to the GT640.  Upon first install, I was successful in getting it to span the desktop across both monitors using the default xorg video driver.  This worked fine for a while and then I began getting compiz failures regularly.  I tried using the 310 driver and that seemed to work great - I was able to span the desktop, could run the nvidia-settings, etc.  Then, soon, compiz again began giving errors.  But I just said to ignore them and leave it closed - yet the desktop continued to function.

Next time I booted into Ubuntu, I logged in and got the desktop background but nothing else - no launcher, no menu bar, nothing.  I could Ctrl-Alt-Del to log out and get back to the login screen but that was it.  So I re-installed Ubuntu and go back to where i was.

I've now been through that scenario several times and have gone to only mirroring the monitors to see if that makes a difference.  so far, so good -- though not acceptable long-term.

Now, I tried switching to the 310-experimental from the default xorg driver (still with mirrored monitors) and it works -- but nvidia-settings reports:

[FONT="Courier New"]You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.[/FONT]

I tried that command and it made no difference.

"lspci -nn | grep -i vga" reports:
[FONT="Courier New"]01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107 [GeForce GT 640] [10de:0fc1] (rev a1)/FONT]

"sudo lshw -C display" reports:
[FONT="Courier New"]PCI (sysfs)  
  *-display               
       description: VGA compatible controller
       product: GK107 [GeForce GT 640]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:e4000000-e4ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:a000(size=128) memory:d2000000-d207ffff[/FONT]

System test "graphics/compiz_check" reports:  FAILED
[FONT="Courier New"]OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x301)
OpenGL version string: 2.1 Mesa 9.0
Not software rendered: no
Not blacklisted: yes
GLX fbconfig: yes
GLX texture from pixmap: yes
GL npot or rect textures: yes
Compiz supported: no[/FONT]

---

### Post by papibe on 2013-02-21
Hi RodBarnes. Welcome to the forums ):P

It looks like you indeed are **not** using the Nvidia driver, but nouveau instead:
> **RodBarnes said:**
> driver=nouveau

I would start by installing the current driver, and only upgrading to a  upper version only if you have problems.

Let's start by cleaning the house. Uninstall all Nvidia packages:
```
sudo apt-get purge nvidia-*
```
Then remove the Xorg config file (actually rename it):
```
sudo mv -iv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Then restart. Once on the desktop, install the recommended Nvidia driver, usually named nvidia-current (recommended).

If you are not able to install it from the GUI, try doing it from the command line:
```
sudo apt-get install nvidia-current
```
Before you reboot to take effect. Create a custom Xorg config file:
```
sudo nvidia-xconfig
```

Another reboot, will get you using the stable Nvidia proprietary driver.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by RodBarnes on 2013-02-21
The first two commands to clean-up the nvidia mess were succesful; the subsequent reboot brought me back to an operational desktop again.  Thanks for the help.

I then opened System Settings -> Software Sources -> Additional Drivers which was showing that is was now using the "X.Org X server" as expected.  However, none of them are listed as a "recommended" driver. Besides the X.Org it is either:

It lists an "nvidia-current", "nvidia-experimental-310", nvidia-current-updates", or "nvidia-experimental-304".

I tried the "nvidia-current" and "nvidia-current-updates" drivers but when I run nvidia-settings for either, it still complains:

[FONT="Courier New"]You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.[/FONT]

This is just odd because when I first used the nvidia drivers (310) I had it running for several days and was able to run nvidia-settings without issue.  Not sure what has changed that is causing this.

I've also noticed that, with any of the drivers, there is a very noticeable performance hit when I span the desktop to both monitors.  I don't see any of this poor performance or behavior running the Nvidia drivers for Win7.  Although, those drivers are up to 314 as of a few days ago.

---

### Post by papibe on 2013-02-21
Could you post the content of this file:
```
/var/log/Xorg.0.log
```
Paste it here: [http://pastebin.ubuntu.com/]("http://pastebin.ubuntu.com/") and post back the link to it.

Regards.

---

### Post by RodBarnes on 2013-02-22
Done: [http://pastebin.ubuntu.com/5556414/]("http://pastebin.ubuntu.com/5556414/")

Some additional information which may or may not be related or helpful:  I've installed Ubuntu 12.10 maybe 10-15 times now (always with the option to delete and install clean) and have experienced different video behavior each time.  For example, the slowness I mentioned when I extend the desktop:  I've experienced this every time I've installed Ubuntu (even when the nvidia drivers were working) but then, at some point (I've yet to determine any identifiable pattern), the desktop will miraculously begin performing tolerably well.  So far this time 'round, it remains slow and still mirrors the login screen at boot, only extending desktop after login.

In conjunction with this, I see a change during boot-up. Instead of the login screen being mirrored on both monitors and then extending the desktop only after login, it will begin displaying the login only on the primary (physical) monitor and just an Ubuntu icon centered in the other monitor.

It is notable that the performance increase happens whether or not I am extending the desktop.  Even while mirroring monitors, I will eventually see the UI performance improve dramatically at some point.

Honestly, when I first began trying Ubuntu, I found the UI performance to be ridiculously slow compared to what I experience when running Win7 on the same hardware.  I kept at it only because I wanted to check out Ubuntu.  Even with the performance increase it is still significantly slower than Win7.  But maybe I'll eventually see Unity at its best. :-)

---

### Post by RodBarnes on 2013-02-22
FYI: Just after posting the last reply, it again came up with a "Compiz has closed unexpectedly".  I've seen this nearly every time following an install.  It works for a while and then at some indeterminate point (often while clicking to close a window), the desktop will freeze for about 30-60 seconds.  It will finally refresh and then present the error message.  I've tried both the [Relaunch] and [Leave Closed] but neither seems to make a difference. in what happens later - with the exception that if I relaunch, it eventually dies again and produces the error.  But Unity continues to operate.

I could provide the details of the error but can't copy/paste them -- seems an oversight not to be able to do that.  But I've always checked the "Send error report" box so maybe that is sufficient.

This is the XsessionErrors section:
[FONT="Courier New"](gnome-control-center:3277): Gtk-CRITICAL **:gtk_box_pack:assertion `gtk_widget_get_parent(child) == NULL' failed
gnome-session[2222]: WARNING: Application 'comppiz.desktop' killed by signal 11
gnome-session[2222]: WARNING: App 'compiz.desktop'respawning too quickly
gnome-session[2222]: CRITICAL: We failed, but the fail whale is dead. Sorry...[/FONT]

---

### Post by papibe on 2013-02-22
```
...
[    18.217] (II) LoadModule: "nvidia"
[    18.218] (WW) Warning, couldn't open module nvidia
[    18.218] (II) UnloadModule: "nvidia"
[    18.218] (II) Unloading nvidia
[    18.218] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    18.218] (II) LoadModule: "nouveau"
...
```
Puzzling :confused:

Could you post the result of these commands?
```
lsmod | grep -i nvidia

ls /usr/lib/xorg/modules/drivers/nvidia_drv.so

apt-cache policy nvidia-common

apt-cache policy nvidia-current
```
Regards.

---

### Post by RodBarnes on 2013-02-22
Output below...  One thing that may affect the output is that I did an apt-get clean and apt-get autoremove trying to clean up some of this mess.  During the output I did see it removing "nvidia-settings".  I didn't see any other nvidia labels during the process.  Right now it is running the X.Org video driver.

```
rod@brawn:~$ lsmod | grep -i nvidia
rod@brawn:~$ ls /usr/lib/xorg/modules/drivers/nvidia_drv.so
ls: cannot access /usr/lib/xorg/modules/drivers/nvidia_drv.so: No such file or directory
rod@brawn:~$ apt-cache policy nvidia-common
nvidia-common:
  Installed: (none)
  Candidate: 1:0.2.71.1
  Version table:
     1:0.2.71.1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/universe amd64 Packages
     1:0.2.71 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/universe amd64 Packages
rod@brawn:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: (none)
  Candidate: 304.51.really.304.43-0ubuntu1
  Version table:
     304.51.really.304.43-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/restricted amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by papibe on 2013-02-22
Thanks.

There's no sign of the Nvidia driver. My first guess is that the 'Additional Drivers' failed to installed and it didn't report the correct error.  

Could you post the result of these command?
```
apt-cache policy linux-headers-$(uname -r)

apt-cache policy linux-headers-generic
```
Regards.

EDIT: another command added.

---

### Post by RodBarnes on 2013-02-22
Below...  BTW: I've pretty well confirmed the issue is Compiz occurs in conjunction with closing a window.  (Not sure if this is related to my video issue or is separate.)  Last time it died, I didn't relaunch it.  Now, periodically - not every time, though - it will reset the desktop when I close a window.

```
linux-headers-3.5.0-25-generic:
  Installed: (none)
  Candidate: 3.5.0-25.38
  Version table:
     3.5.0-25.38 0
        500 http://us.archive.ubuntu.com/ubuntu/ quantal-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ quantal-security/main amd64 Packages
```

---

### Post by papibe on 2013-02-22
Sorry, I edited by previous post. Could you post both commands?

---

### Post by papibe on 2013-02-22
Now I think it not that important.

There's a (apparently) known problem in 12.10. The linux-headers are not installed by default, but they are required to install proprietary drivers. This problem is not present on 12.04 BTW.

To solve this:

Clean the house:
```
sudo apt-get purge nvidia-*

sudo mv -iv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo apt-get install **linux-headers-generic**
```
Restart.

Install the nvidia driver:
```
sudo apt-get install nvidia-current

sudo nvidia-xconfig
```
Restart.

That should be it. If this didn't work, please post again what I requested you on posts #4 and #7.

Let us know how it goes.
Regards.

---

### Post by RodBarnes on 2013-02-22
Followed the steps in your post including the restart between.  A couple of notable items:

```
sudo mv -iv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```reported that /etc/X11/xorg.conf didn't exist

I proceeded and did the install of linux-headers-generic and then did the restart.

Afterwards, I installed nvidia-current which didn't present any obvious errors that I noticed.

But the nvidia-xconfig statement reported:

```
WARNING: Unable to locate/open X configuration file.
New X configuration file written to '/etc/X11/xorg.conf'
```

I assume because there still wasn't one out there.

[Additional Drivers] does have the nvidia-current driver marked as being used.

But when I run nvidia-settings it still reports the error "You do not appear be to using the NVIDIA X driver."

So, nothing is blowing up (yet, we'll see) but still unable to run nvidia-settings.  Very odd considering I was able to run it back the first time I tried the Nvidia drivers.  But that was with the experimental driver.  Maybe that is the difference?  Or maybe some other update has occurred to change things?

---

### Post by RodBarnes on 2013-02-22
Here's the output of those two commands, just in case you need them:

```
rod@brawn:~$ apt-cache policy linux-headers-$(uname -r)
linux-headers-3.5.0-25-generic:
  Installed: 3.5.0-25.38
  Candidate: 3.5.0-25.38
  Version table:
 *** 3.5.0-25.38 0
        500 http://us.archive.ubuntu.com/ubuntu/ quantal-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ quantal-security/main amd64 Packages
        100 /var/lib/dpkg/status
rod@brawn:~$ apt-cache policy linux-headers-generic
linux-headers-generic:
  Installed: 3.5.0.25.31
  Candidate: 3.5.0.25.31
  Version table:
 *** 3.5.0.25.31 0
        500 http://us.archive.ubuntu.com/ubuntu/ quantal-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ quantal-security/main amd64 Packages
        100 /var/lib/dpkg/status
     3.5.0.17.19 0
        500 http://us.archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
rod@brawn:~$ 
```

---

### Post by papibe on 2013-02-22
> **papibe said:**
> If this didn't work, please post again what I requested you on posts**[COLOR="Red"] #4 [/COLOR]**and **[COLOR="Red"]#7[/COLOR]**.

:) would you?

---

### Post by RodBarnes on 2013-02-22
Sorry, missed that note earlier.  Output is found at the bottom.  But you should read the next paragraphs as it likely altered what you would've have seen before.

I had been working along since installing nvidia-current.  I'd had a couple desktop "resets" (mentioned these earlier where it resets the desktop and repaints all the windows, and this happens when I close a window, though not with every close).

Then just a few minutes ago, I closed a window, it reset again - but this time there was no launcher and it repainted the windows without frames, menu bars, or controls; and I could not change the z-order of the windows, and some could not enter focus, etc.

So I logged off and the logoff screen came up very large (as I expected it would - it has before in this condition) but logging in just brought it back to a blank desktop.

So I tried to take the "shutdown" option but it wouldn't.  I ended up hitting the reset button and restarting the computer.

This time it came up to the login screen as it should -- unmirrored with the primary screen showing a login and the secondary screen showing the ubuntu logo.  (Plus, as it was booting, it actually showed the correct "Ubuntu 12.10" graphic rather than video garbage as it has been.)

After logging in, it is now performing much better (mentioned that behavior in previous messages) - widows drag smoothly and quickly, window open with a snap, and - drum roll - I can run nvidia-settings!

Weird, weird, weird.  I had left all the video stuff alone since our last exchange but something finally flipped and it is all nice now.  Wonder how long this will last...

Here's the output of the commands.  I expect it is different than what you would have seen prior to this latest reset.

Contents of "/var/log/Xorg.0.log" found here: [http://pastebin.ubuntu.com/5557072/]("http://pastebin.ubuntu.com/5557072/")

Output of other commands:
```
rod@brawn:~$ ls /usr/lib/xorg/modules/drivers/nvidia_drv.so
/usr/lib/xorg/modules/drivers/nvidia_drv.so
rod@brawn:~$ apt-cache policy nvidia-common
nvidia-common:
  Installed: (none)
  Candidate: 1:0.2.71.1
  Version table:
     1:0.2.71.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ quantal-updates/universe amd64 Packages
     1:0.2.71 0
        500 http://us.archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
rod@brawn:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 304.51.really.304.43-0ubuntu1
  Candidate: 304.51.really.304.43-0ubuntu1
  Version table:
 *** 304.51.really.304.43-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ quantal/restricted amd64 Packages
        100 /var/lib/dpkg/status
rod@brawn:~$
```

---

### Post by papibe on 2013-02-22
Thanks.

You missed this two:
```
lsmod | grep -i nvidia

ls /usr/lib/xorg/modules/drivers/nvidia_drv.so
```
It looks that finally the driver is installed, running and in use:
```
[    19.398] (II) LoadModule: "nvidia"
[    19.398] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    19.612] (II) Module nvidia: vendor="NVIDIA Corporation"
[    19.612] 	compiled for 4.0.2, module version = 1.0.0
[    19.612] 	Module class: X.Org Video Driver
```
Try opening the 'Nvidia X Server Settings' to fine tune your displays.

I'm a little confused as how the package nvidia-common is not installed, since you need it on 10.04 and 12.04 (may be you don't in 12.10 ;)).

Let us know how it goes.
Regards.

---

### Post by RodBarnes on 2013-02-23
The output of the 2nd of your latest commands was actually at the top of the output in my last reply.  It probably wasn't noticeable with all the rest that was in there.

```
rod@brawn:~$ lsmod | grep -i nvidia
nvidia              11257760  42 
rod@brawn:~$ ls /usr/lib/xorg/modules/drivers/nvidia_drv.so
/usr/lib/xorg/modules/drivers/nvidia_drv.so
rod@brawn:~$ 
```

Still running well this morning, still performing well.  But afraid to do much of anything for fear it will start all over again. :)

---

### Post by papibe on 2013-02-23
It seems to be working OK.

The nvidia module is loaded, the driver installed, and running.

:D I'm glad it is performing well.

Regards.

---

