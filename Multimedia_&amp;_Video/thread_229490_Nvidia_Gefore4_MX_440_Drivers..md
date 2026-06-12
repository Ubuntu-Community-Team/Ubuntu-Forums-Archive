---
title: "Nvidia Gefore4 MX 440 Drivers."
date: 2006-08-04
forum: Multimedia &amp; Video
---

### Post by Iskander on 2006-08-04
[COLOR="Red"]I am using the Nvidia Geforce4 MX 440 Video card in my system. I would love to know how to install the drivers for Ubuntu Linux every guide I look at talks about Xconfig and stuff like that and yes you guessed it I am bran new to Ubuntu Linux and am still learning several things about it Im learning slowly but am learning if someone can tell me how to install my Nvidia Drivers it'd be greatly appreciated.

Cheers, Iskander.[/COLOR]

---

### Post by Iskander on 2006-08-04
OK I Did it through SPM, and got the:

NVIDIA binary XFree86 4.x/X.Org driver
These XFree86 4.x/X.Org binary drivers provide optimized hardware acceleration
of OpenGL applications via a direct-rendering X Server and support the newer
GeForce, nForce and Quadro families of NVIDIA chipsets.  AGP, TV-out and
flat panel displays are also supported.

If you have a TNT, TNT2, or older GeForce, you may need the nvidia-glx-legacy
package instead of this one.

To enable the driver, run "sudo nvidia-glx-config enable".
-------------------------------------------

But when I run the command "sudo nvidia-glx-config enable", I get this:

iskander@iskander-desktop:~$ sudo nvidia-glx-config enable

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.


Can someone please tell me what I am doing wrong and what I need to do to fix this please. And What driver is correct right now I am just trying to get Things fixed to where I can run My games on Wine and Cedega when I get it.

---

### Post by matko on 2006-08-04
if you are new try [http://www.ubuntuforums.org/showthread.php?t=177646]("http://www.ubuntuforums.org/showthread.php?t=177646")
otherwise you have to change your xorg.conf manually.

you can paste it here if you dont want use automaix.

---

### Post by tseliot on 2006-08-04
You should try Method 1 of this guide:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

and use also point 7 of the Problems Section of the same guide.

---

### Post by Fully216 on 2006-08-04
I was able to go to nvidia.com and get the latest driver from there, which I believe might be more up to date than the one found in the ubuntu repos.  They have an install guide that was easy to follow and works.  

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Just pick your architecture (mine is amd64), and follow the steps they list.  They also have a utility that will configure your x config file for you.  It is as simple as following the on screen menus after you run the following from the terminal window.

sh NVIDIA-Linux-x86_64-1.0-8762-pkg2.run (if you have amd64 system like me)

Hope this helps!

---

