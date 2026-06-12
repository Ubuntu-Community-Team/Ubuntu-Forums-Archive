---
title: "XGL/Compiz Troubles"
date: 2006-07-04
forum: Multimedia &amp; Video
---

### Post by aglc2005 on 2006-07-04
I have installed the most recent versions of Compiz and XGL, but when attempting to launch Compiz I get the error:

> compiz: no composite extension
and then  this line is repeated about a dozen times

> (gnome-window-decorator:17075): Pango-CRITICAL **: pango_colot_parse: assertion 'spec != NULL' failed

and if I try to edit the preferences of Compiz it crashes (well what running of it).
I have no clue what to do, I have look all over this forum and Compiz's forum trying to find a solution and have found nothing that will help. Thanks in advance for any help.

---

### Post by ciscosurfer on 2006-07-05
If you've followed the previous threads on how to setup and install Xgl/Compiz properly (including setting up 3D acceleration, proper files downloaded, etc.) then you should check out this link for an absolutely awesome way of setting up / running Xgl and Compiz:

[Howto-compiz-xgl-on-ubuntu-for-the-morbidly-lazy-2]("http://chromakode.blogsome.com/2006/02/16/howto-compiz-xgl-on-ubuntu-for-the-morbidly-lazy-2") \\:D/

Please post your results!

---

### Post by aglc2005 on 2006-07-05
I followed that tutorial and after reboot no Compiz effects or XGL, just my standard X.

edit: I also attemted to start Compiz manually in terminal and I got the same error about "compiz: no composite extension"

---

### Post by ciscosurfer on 2006-07-06
Okay.  Maybe try [this tutorial]("http://tazforum.thetazzone.com/viewtopic.php?t=2189").  Don't skip around, and follow the directions exactly.  Unfortunately, not knowing what you've already installed (or not installed) makes fixing this issue a bit difficult.  You may have introduced dependency problems or the like, and so in effect, you've "broken" your system.  Have no fear, though.  Take a deep breath, try out the link, and see what happens.  Please post your results again when you're done!

---

### Post by MarkSheely on 2006-07-06
Do you have anything like the following in Xorg?

Section "Extensions"
Option "Composite" "Enable"
EndSection

--Mark

---

### Post by aglc2005 on 2006-07-06
Ok that seemed to work, the only thing is that I have to start compiz in the terminal with 
> sudo startcompiz
in order to get it working. One other question, is there a way to edit the options, like turning off the wobbling windows for example?

---

### Post by ciscosurfer on 2006-07-07
> **aglc2005 said:**
> Ok that seemed to work, the only thing is that I have to start compiz in the terminal with 

in order to get it working. One other question, is there a way to edit the options, like turning off the wobbling windows for example?

You can try going to your Configuration Editor (**gconf-editor**) and drilling down to the **/apps/compiz/plugins/wobbly/screen0/options** screen and messing with the values there.  To turn off the wobbly effect for specific types, go to the entry titled **move_window_types** and try deleting certain values that you want.  Haven't tried this, but it looks like this is where you can do it.  

(An easy, graphical way) [T]o turn off the wobbly effect entirely can be achieved by installing **gset-compiz** through apt.  Once you've done that, you can simply run **gset-compiz** (should be in your Ubuntu menu under Applications > Accessories > Gset-compiz) and completely disable the plugin from there. Hope this helps.  Check [here]("https://help.ubuntu.com/community/CompositeManager/ConfiguringCompiz") for further details.

Another *excellent* tutorial to get Xgl/Compiz working on your machine can be found [here]("https://help.ubuntu.com/community/CompositeManager").  Remember to follow the tutorials entirely, paying special attention to your unique setup and circumstances.   Happy tweaking!  ;)

---

### Post by aglc2005 on 2006-07-07
Ok, thanks a lot for the help.

---

### Post by aglc2005 on 2006-07-18
Ok, I just had to reinstall Ubuntu for various reasons I will not go into, I followed the second tutorial seeing how that worked, but when I entered

> sudo nvidia-glx-config enable

I recieved this error

> Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

I tried the md5sum and after I rebooted my computer later on X was all messed up and I ended up doing a clean install again, when I reached this point again, I recieved the same error so I looked in the xorg.conf and the driver is already switched to 'nvidia' so now I have no clue as to what I am suppose to do.

---

### Post by tseliot on 2006-07-18
> **aglc2005 said:**
> Ok, I just had to reinstall Ubuntu for various reasons I will not go into, I followed the second tutorial seeing how that worked, but when I entered



I recieved this error



I tried the md5sum and after I rebooted my computer later on X was all messed up and I ended up doing a clean install again, when I reached this point again, I recieved the same error so I looked in the xorg.conf and the driver is already switched to 'nvidia' so now I have no clue as to what I am suppose to do.
"sudo nvidia-glx-config enable" is broken in Ubuntu Dapper.

reconfigure your xorg.conf:
```
sudo dpkg-reconfigure xserver-xorg
```

select the "nvidia" driver and press ENTER whenever you don't know how to answer to the other questions.

The next time you want to install the Nvidia driver you can follow (Method 1 of) my guide:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

---

### Post by aglc2005 on 2006-07-18
> **tseliot said:**
> "sudo nvidia-glx-config enable" is broken in Ubuntu Dapper.

reconfigure your xorg.conf:
```
sudo dpkg-reconfigure xserver-xorg
```

select the "nvidia" driver and press ENTER whenever you don't know how to answer to the other questions.

The next time you want to install the Nvidia driver you can follow (Method 1 of) my guide:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

Thanks, that worked perfectly[-o< , and I bookmarked your guide too.\\:D/

---

