---
title: "Gutsy - Ati driver replaced with mesa driver on reboot."
date: 2007-11-22
forum: Multimedia &amp; Video
---

### Post by araaran on 2007-11-22
FINALLY got Ubuntu Gutsy 7.10 to load using the latest Ati driver:
ati-driver-installer-7-11-x86.x86_64.run

Results successful:
[IMG]http://marks-halayenka.com/images/Screenshot.jpg[/IMG]

But upon reboot I get this:
[IMG]http://marks-halayenka.com/images/Screenshot2.jpg[/IMG]

I have meticulously followed the instructions several times.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

This INCLUDES the mesa-problem instructions.

It appears that this is the same problem a number of people have; Namely that upon reboot (note: restarting x using ctrl+alt+backspc is ok) the MESA drivers are loaded instead of the ATI drivers.

HELP ME PLEASE!
I have spent 4 days on two driver versions, two different Ubuntu flavours and many patient hours online following instructions to the letter.

I am using Ubuntu 7.10 and a Sapphire ATI HD2900XT 1GB card. I wish to use Blender, so this is really important for me.

---

### Post by Kibbo on 2007-11-22
I'm having a similar problem, following the instructions [here]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide").

I think I've isolated the problem to the point where the sym-link disappears.

```
sudo ln -s /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko 
```

I tried adding the script suggested in that guide, but no luck.

---

### Post by araaran on 2007-11-22
Im glad its not just me. I am SERIOUSLY considering moving to a GeForce 8800GTS :(

---

### Post by Mark Phelps on 2007-11-24
Araaran:

You're not alone.  Exactly the same thing happened to me (at least, now I know that I'M not crazy!!)

I, too, had the fglrx and direct rendering and then, when I booted the next day, the Mesa text is back.  

I've spent hours reinstalling using the manual method in the Ubuntu Gutsy Installation Guide -- with no success.

Sorry I didn't have good news.

---

### Post by peakshysteria on 2007-12-11
Same problem as araaran here upon restarting X or rebooting. Graphics and screen tell me the driver is enabled/green (but not checked). And the desktop looks awesome. Restarting gives me the Mesa info as araaran. Checking the driver in the Graphics and screens menu and restarting scrambles my whole desktop and i just have to start over again.

Maybe araaran could tell us which howto he used to get the catalyst control center going? I'm a real n00b so i don't think a can get any further actually. The only thing i need for a complete move to Ubuntu is enabling the tv-out in a satisfactory way.

araaran and the others experiencing the same problems on resboot/restart of X check out:

Post-Installation Checks
[edit] Verifying

Run the following command to check its output to ensure the fglrx driver
is installed properly:

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7059 Release

The OpenGL vendor string should read ATI and not Mesa.

If it still says Mesa and not ATI, even after re-enabling the driver
from the Restricted-manager: You can try the following:

        * Remove all the packages provided by the xserver-xorg-video-all
meta-package (search for it using Synaptic or Adept), then restart the
machine. The X Server should now use the new fglrx driver by force
(provided the driver is being used in xorg.conf).

        If you can't log in after this, you'll have to log in to a
terminal in the login screen, and reinstall the xserver-xorg-video-all
package. Your problem is probably somewhere else. (taken from [1]).

If it says libGL.so.1: cannot open shared object file: No such file or
directory... Check if you have a /usr/lib/libGL.so.1.2, if so do this:

sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

Note: Here is the glxinfo of a good install (for those interested).

This is from the [Ubuntu Gutsy Installation Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide").

I think this at least should solve araaran's problem. And please post solutions if you guys come by them. And screenshots are very appreciated.

I haven't tried [Troubleshooting Solving the 'Mesa nightmares' mystery]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=569654&highlight=600m+gutsy") since i 'm in windows a the time, but it seems to be a nice aproach as well.

---

### Post by schmildo on 2007-12-11
LOL I had that issue too. I found that the xorg.conf file wasn't saving my changes.

I was just trying to change that bit in the 'device' section from ati to fglrx or somethingorother, and that was suppposed to give me what I wanted : ATI and not Mesa after running fglxrinfo.

But it kept jipping me. So I posted [here]("http://ubuntuforums.org/showthread.php?t=631500").

And i realised that for some reason my manually edited versions were being backed up, but if i ran the aticonfig command I could change the file and it would stay there after a reboot. There is also a command for the nvidia cards also.

I think I ran this command:

[COLOR="DarkSlateBlue"]aticonfig --initial --input=/etc/X11/xorg.conf[/COLOR]

Oh, yeah, and that fixed the problem.

---

### Post by acoustibop on 2007-12-11
> **Kibbo said:**
> I'm having a similar problem, following the instructions [here]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide").

I think I've isolated the problem to the point where the sym-link disappears.

```
sudo ln -s /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko 
```

I tried adding the script suggested in that guide, but no luck.

That's right, Kibbo - Gutsy appears to remove the link on rebooting.  However, I've found that the script in the Unofficial Wiki for the ATI Linux Driver works perfectly for me: don't forget you have to make the file executable and start before gdm for it to work:

```
NOTE : On my Gutsy install, after a reboot this link was always removed automatically leaving me without an fglrx module loaded, and thus no ATI rendering. There have been several ways of getting around this suggested here, and here is the one that worked for me:

sudo gedit /etc/init.d/ati-module-fix

And put this in it:

#!/bin/sh -e

# For loading ATI display drivers

ln -sf /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko
exit 0


Make it executable

sudo chmod ugo+x /etc/init.d/ati-module-fix

Now, make this run before gdm (which starts with sequence number 13)

sudo update-rc.d ati-module-fix defaults 12

It is possible that gdm sequence number is different. To find the gdm sequence number:

ls /etc/rc2.d/

And substitute 12 in the previous command with gdm sequence number - 1.
```

---

### Post by peakshysteria on 2007-12-15
Hmm, yeah, i've been there twice now acoustibop. I know i'm doing something wrong. But not sure what yet. So irritating. I've also tried Envy. Without success (and uninstalled it). No thinking more abput going for Hardy Heron Alpha 1 even though i'm a n00b. It might have better support for my ATI Hightech Excalibur X700 PRO. Without proper and stable display running and tv-out support i cant use Ubuntu as default anyway. Then have to stick with boring Win XP.

Have anyone had any good experiences with upgrading to Hardy Heron when it comes to the problem of the ATI/Ubuntu hell??

Edit: and since no one answered i went on with it last night. Everything seemed to go fine (update-manager -d). Had two or three errors (one of them where problems with installing fglrx i think) but the upgrade went on. Upon restart, after the boot screen the display start with 1600 x 1024 OUT OF RANGE. Can't seem to go any further from there on.

After upgrade the system is recognized as Ubuntu 8.04. Upon reboot the boot manager identifies the main OS as Ubuntu 7.10. So any help with getting to my desktop so i can manage the Ati driver is welcome. If there is no other way, also tips on going back to a stable Gutsy are appreciated.

---

