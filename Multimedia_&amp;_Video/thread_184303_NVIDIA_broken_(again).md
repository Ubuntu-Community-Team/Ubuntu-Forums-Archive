---
title: "NVIDIA broken (again)"
date: 2006-05-29
forum: Multimedia &amp; Video
---

### Post by pecanov on 2006-05-29
Since last update that included linux-restricted modules and nvidia-glx packages, the X fails to start warning about different versions of kernel module and X driver, the one being 8756 and the other 8972 I think.

Is there a way around this to use nvidia driver or should I wait for an update and stick to "nv" driver?

And by the way, does anyone else have this problem?

---

### Post by tseliot on 2006-05-29
You can try my script (the stable version):
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

---

### Post by Mamour on 2006-05-29
I had the same issue, but a reboot fixed it. I guess I was lucky :-D.

---

### Post by jecos on 2006-05-29
Its always wise to always reboot after driver updates, unless you really know how to rmmod the old and load the new in the right runlevel.

---

### Post by pecanov on 2006-05-29
Actually this thing happened AFTER the reboot, and AFTER the new module was loaded.
So rebooting doesn't solve it.

---

### Post by slugkilla on 2006-05-29
I have the same problem! [http://www.ubuntuforums.org/showthread.php?t=184166](http://www.ubuntuforums.org/showthread.php?t=184166)
This is way not cool. I think it is happening to me because I used the installer and the apt-get thing. Nothing I have done has worked :(

---

### Post by pecanov on 2006-05-29
Using the installer is the right way to go.
If you want to you can always install the driver from nvidia site, but that's not the issue. I want and need the ubuntu patches and updates, and that is the way it should be done. Without boring HOWTO's, Wiki's and scripts. If I wanted to do that I would stick to redhat and suse as I used to.

---

### Post by minisori on 2006-05-29
[QUOTE=pecanov]Since last update that included linux-restricted modules and nvidia-glx packages, the X fails to start warning about different versions of kernel module and X driver, the one being 8756 and the other 8972 I think.

Is there a way around this to use nvidia driver or should I wait for an update and stick to "nv" driver?

And by the way, does anyone else have this problem?[/QUOTE]

This usually happend when they are updating. Usually there is allways first the nvidia-glx package and then the restricted modules. At the moment they are both at the latest version, and working on my computer. Try updating and see if it works.

Next time take a look before updating :p

---

### Post by joshrobinson on 2006-05-29
this is also happening with the ati package

it broke big time

---

### Post by pecanov on 2006-05-29
Updating every hour ... sometimes twice ... no new packages related to nvidia.

---

### Post by berserker on 2006-05-29
I have a custom kernel (2.6.16-cks11) and build the Nvidia driver from source.  I updated to Dapper and now have "Failed to load glx module" and "Failed to load nvidia module" whenever I try to start KDM.  The latest driver 8762 compiles and installs fine but chokes unless I have "nv" in xorg.conf.  

I've tried tseliot's script for dapper and that doesn't work.

Any ideas?

Thanks.

---

### Post by trorion on 2006-05-29
I had to do a complete removal of "nvidia-glx" and "nvidia-kernel-common" then an install of "nvidia-glx" and now (after reboot) it's fine.
```
sudo apt-get remove nvidia-glx
sudo apt-get remove nvidia-kernel-common
sudo apt-get install nvidia-glx
```

---

### Post by tseliot on 2006-05-30
[QUOTE=slugkilla]I have the same problem! [http://www.ubuntuforums.org/showthread.php?t=184166](http://www.ubuntuforums.org/showthread.php?t=184166)
This is way not cool. I think it is happening to me because I used the installer and the apt-get thing. Nothing I have done has worked :([/QUOTE]
That's right. You should NOT mix method 1 and method 2 otherwise you have a driver mismatch.

press CTRL+ALT+F1 (you will see only the command line)
log in

type:
```
cd path_to_the_nvidia_installer(the one from Nvidia's website)
```
```
sudo sh name_of_the_installer --uninstall
```

Now remove also the driver from the repos:
```
sudo apt-get --purge remove linux-restricted-modules-`uname -r` linux-restricted-modules-common nvidia-glx nvidia-settings nvidia-kernel-common
```

Now install the driver from the repos:

```
sudo apt-get install nvidia-glx linux-restricted-modules-`uname -r`
```

```
sudo /etc/init.d/gdm restart (or "kdm restart" if you use KDM)
```

---

### Post by tseliot on 2006-05-30
[QUOTE=berserker]I have a custom kernel (2.6.16-cks11) and build the Nvidia driver from source.  I updated to Dapper and now have "Failed to load glx module" and "Failed to load nvidia module" whenever I try to start KDM.  The latest driver 8762 compiles and installs fine but chokes unless I have "nv" in xorg.conf.  

I've tried tseliot's script for dapper and that doesn't work.

Any ideas?

Thanks.[/QUOTE]
1) Did you compile also the kernel headers? If not, then my script won't work.

2) Can you try a kernel for Dapper?
you can try with:
```
sudo apt-get install linux-image-686 linux-headers-686
```
(you can replace 686 with k7 or 386, according to you architecture)
then reboot and try my script again

---

### Post by tseliot on 2006-05-30
[QUOTE=pecanov]Using the installer is the right way to go.
If you want to you can always install the driver from nvidia site, but that's not the issue. I want and need the ubuntu patches and updates, and that is the way it should be done. Without boring HOWTO's, Wiki's and scripts. If I wanted to do that I would stick to redhat and suse as I used to.[/QUOTE]
I know it can be boring but knowledge is power. Don't tell me that crashes are less boring.

---

### Post by pecanov on 2006-05-30
Knowledge we have... but don't want to waste my time on nvidia drivers. Have better things to do.
Crashes like this are solvable in metter of seconds (just replace nvidia with nv), while installing an nvidia driver is more time consuming ... download, get kernel-headers, install (compile), test ... and even then you are not sure where your at, or what to do when the next nvidia-glx package comes along.
My point is ubuntu isn't perfect, but at least it kept me away from searching for and reading the previously mentioned documents, more than any other distribution. Event more than Mandrake (which is a pretty good compliment when ubuntu came out).
Seems like the curse of the linux distributions has hit dapper in all it's strength. Spending time on this forums doesn't make me happy, and after 2 years (yes, from warty) I'm thinking about a clean install. That's not very encouraging.

---

### Post by malte on 2006-05-30
Remember this is STILL a beta version.
Anyway when X complained about NVIDIA drivers, I just
```

sudo modprobe -r nvidia
sudo modprobe nvidia
sudo /etc/init.d/gdm restart

```
et voilà!

---

### Post by tseliot on 2006-05-30
[QUOTE=malte]Remember this is STILL a beta version.[/QUOTE]
Dapper Drake has not been released yet. After June 1 I guess pecanov can have the right to complain about stability :p

---

### Post by pecanov on 2006-05-30
[QUOTE=tseliot]Dapper Drake has not been released yet. After June 1 I guess pecanov can have the right to complain about stability :p[/QUOTE]
That's the day after tomorrow.
... so I might as well start now.

---

### Post by Horizon on 2006-05-30
[QUOTE=pecanov]That's the day after tomorrow.
... so I might as well start now.[/QUOTE]
No...you'll start the day after tomorrow like all the (non-existant) good little boys :p 

Good thing i saw this coming in the lead up to June 1st and finished all my work on the weekend :D

PS: You're the type of person that doesn't like to tinker? and yet you have 161 posts? bummer

---

### Post by pecanov on 2006-05-30
I don't want to start an ego fight here.
Complaining is what I do here, and those 161 post say it wasn't a pleasant trip. (90% are on dapper forums).

Here is the bottom line:
Dapper was presented as enterprise scale piece of software. In the IT industry it means gaining a certain level of standards. It's said and frustrating for everyone that promotes ubuntu not only as an alternative but as a better OS. The frustration is everywhere around the forums. Many projects are now hanging in thin air because of the instabillity.
It's a mighty step back, so the right to complain is mine and it's justified. Maybe a over exadurate, since I've been editing conf files, and "configuring" and "making" for the last 8 years, but ubuntu had the chance to change that to a better form.
Saddly, there is a concensus is it fails for the time being. Maybe in another 3 years.

---

### Post by tseliot on 2006-05-30
[QUOTE=pecanov]I don't want to start an ego fight here.
Complaining is what I do here, and those 161 post say it wasn't a pleasant trip. (90% are on dapper forums).

Here is the bottom line:
Dapper was presented as enterprise scale piece of software. In the IT industry it means gaining a certain level of standards. It's said and frustrating for everyone that promotes ubuntu not only as an alternative but as a better OS. The frustration is everywhere around the forums. Many projects are now hanging in thin air because of the instabillity.
It's a mighty step back, so the right to complain is mine and it's justified. Maybe a over exadurate, since I've been editing conf files, and "configuring" and "making" for the last 8 years, but ubuntu had the chance to change that to a better form.
Saddly, there is a concensus is it fails for the time being. Maybe in another 3 years.[/QUOTE]
1 more reason NOT to complain about Dapper (now):
[Don't use Dapper as your primary desktop/OS]("http://ubuntuforums.org/showthread.php?t=93157")
And that was written by ubuntu_demon on November 21st, 2005

Didn't you read it?

No, really, Dapper is still potentially unstable.

---

### Post by pecanov on 2006-05-30
I agree... but is two days before deployment the time to be unstable?
Keep in mind dapper was suppose to be 6.04 not 6.06, and two months delay was suppose to be the path to stability.

---

### Post by henriquemaia on 2006-05-30
After this update I had also problems with Nvidia. Then I changed to nv driver, got here to the forums, used tseliot's script to uninstall Nvidia driver, and apt-get the new one. Now everything is ok.

Thanks a lot tseliot for your script! :)

---

### Post by pecanov on 2006-05-30
I guess ubuntu devs should put tselliots script in preinst on nvidia-glx package. :)

---

### Post by joepotter on 2006-05-30
[QUOTE=pecanov]I agree... but is two days before deployment the time to be unstable?
Keep in mind dapper was suppose to be 6.04 not 6.06, and two months delay was suppose to be the path to stability.[/QUOTE]


That is the main trouble with the Ubuntu development model. As predicted by many, we see an "experimental/unstable" branch become the "stable release" the next day. 

Similar things happened just weeks before Breezy went final. The Ubuntu developers will fix Dapper only after it is final. Same for the next one; it is the development model that tells us this will happen.

Have fun.

---

### Post by tseliot on 2006-05-30
[QUOTE=pecanov]I agree... but is two days before deployment the time to be unstable?
Keep in mind dapper was suppose to be 6.04 not 6.06, and two months delay was suppose to be the path to stability.[/QUOTE]
I know that it was already delayed...

I don't know why they decided to update the Nvidia driver so lately. Perhaps it's a gift to Dapper users (and it will work when Dapper is released).

---

### Post by tseliot on 2006-05-30
[QUOTE=pecanov]I guess ubuntu devs should put tselliots script in preinst on nvidia-glx package. :)[/QUOTE]
I have some projects on my mind, some of which consist in a better integration with Ubuntu's restricted modules and nvidia-glx.

Stay tuned

---

### Post by slugkilla on 2006-05-30
Thanks for the help, tseliot. I did exactly what you said but it still complains about a mismatch. The error message is a lot clearer now. It says that my NVIDIA GLX module is version 1.0-8756 and my X driver is 1.0-8762. How is that still there:confused: ? The uninstall program won't take care of it; says that there is no drivers installed. hmmmmm
Thanks again for the help.

---

### Post by alo on 2006-05-30
Well, the nvidia-glx package for 8762 has a wrong driver file name. Instead nvidia_drv.so it is nvidia_drv.o.

Change usr/lib/xorg/modules/drivers/nvidia_drv.o to usr/lib/xorg/modules/drivers/nvidia_drv.so and everything should be fine again.
Don't forget to delete the old nvidia_drv.so file before renaming.

I'm wondering why nobody catched that before... 

Cheers
alo

---

### Post by ramiro on 2006-05-30
[QUOTE=slugkilla]Thanks for the help, tseliot. I did exactly what you said but it still complains about a mismatch. The error message is a lot clearer now. It says that my NVIDIA GLX module is version 1.0-8756 and my X driver is 1.0-8762. How is that still there:confused: ? The uninstall program won't take care of it; says that there is no drivers installed. hmmmmm
Thanks again for the help.[/QUOTE]

make sure you are using the latest version of the kernel (2.6.15-23) and also the latest restricted modules for that kernel version. so run:

```
sudo apt-get update
sudo apt-get install linux-368 linux-restricted-modules-386 nvidia-glx
```

should ensure that you have the latest

once that's done you can just reboot and you should be up and running again. If that doesn't work, make sure you are running the latest version of the kernel 

```
$ uname -r
2.6.15-23-386
```

if you don't get that version, then you need to select the correct version in grub when you reboot. The older kernel versions still have the old nvidia kernel module

---

### Post by cleentrax on 2006-05-30
should read "linux-386", not "linux-368"

---

### Post by tseliot on 2006-05-31
[QUOTE=alo]Well, the nvidia-glx package for 8762 has a wrong driver file name. Instead nvidia_drv.so it is nvidia_drv.o.

Change usr/lib/xorg/modules/drivers/nvidia_drv.o to usr/lib/xorg/modules/drivers/nvidia_drv.so and everything should be fine again.
Don't forget to delete the old nvidia_drv.so file before renaming.

I'm wondering why nobody catched that before... 

Cheers
alo[/QUOTE]
Are you sure about that?

I've got both of them and I have no problem whatsoever.

Anyhow I'll look into that

---

### Post by pecanov on 2006-05-31
Yes, that is the case. It's nvidia_drv.o instead of nvidia_drv.so.
As I can see, manually removing the old driver fixes this problem, since it makes no difference if the file ends with .so or .o . I removed it, restarted X, and nothing changes.

I guess, it also explains the problem we had with the last upgrade and the 8756 driver being kept back.

---

### Post by firehead on 2006-05-31
tseliot you're THA MAN!!
i had the same issues as posted here. uninstalling my old proprietary NVIDIA-Driver (8756) and running your script for dapper solved all my issues!
so big thanx and keep up the good work. i can hardly see anyone spending so much time on this forum helping people with nvidia (and other) issues!!

---

### Post by berserker on 2006-05-31
[QUOTE=berserker]I have a custom kernel (2.6.16-cks11) and build the Nvidia driver from source.  I updated to Dapper and now have "Failed to load glx module" and "Failed to load nvidia module" whenever I try to start KDM.  The latest driver 8762 compiles and installs fine but chokes unless I have "nv" in xorg.conf.  

I've tried tseliot's script for dapper and that doesn't work.

Any ideas?

Thanks.[/QUOTE]

Finally figured out what was going wrong with my installation.  In summary:

1.  Old Nvidia modules were still on my system (e.g., libGL.so.1.0.7676) which Dapper did not tolerate.  Once I removed those then I could load the nvidia module but not the glx module.

2.  I determined that compiling and installing from source did not produce /usr/lib/xorg/modules/libglx.so.1.0.8762 or /usr/lib/xorg/modules/libglx.so that linked to it.

3.  So, I installed the nvidia-glx package, saved the glx module, uninstalled nvidia-glx, compiled and installed the Nvidia driver from source and then replaced the glx module.  

I now have a fully-functional system!

---

### Post by tseliot on 2006-05-31
[QUOTE=pecanov]Yes, that is the case. It's nvidia_drv.o instead of nvidia_drv.so.
As I can see, manually removing the old driver fixes this problem, since it makes no difference if the file ends with .so or .o . I removed it, restarted X, and nothing changes.

I guess, it also explains the problem we had with the last upgrade and the 8756 driver being kept back.[/QUOTE]
I have extracted the Nvidia installer (8762) from Nvidia's website and those files are included:
```
:~/NVIDIA-Linux-x86-1.0-8762-pkg1/usr/X11R6/lib/modules/drivers$ ls
[COLOR="Red"]nvidia_drv.o[/COLOR]  [COLOR="Red"]nvidia_drv.so[/COLOR]
```

---

### Post by slugkilla on 2006-05-31
Thanks guys. Still no luck. I think this is because I have lots of kernel versions. Including the intel ones. I need a K7. So I'm gonna get rid of the old ones. Is this a wise decision?

Edit: ok now I'm running the new k7 kernel still with out the nvidia driver. I tried it but it just wont work. Still says that there is a missmatch.

---

### Post by Owdy on 2006-05-31
[quote=Mamour]I had the same issue, but a reboot fixed it. .[/quote] Same here

---

### Post by s|k on 2006-05-31
I have just given up on proprietary drivers for now. It is just all messed up.

---

### Post by slugkilla on 2006-05-31
I can't give up. My card Is amazing. Just got it. I'm sure someone will figure it out.

---

### Post by tseliot on 2006-05-31
[QUOTE=slugkilla]I can't give up. My card Is amazing. Just got it. I'm sure someone will figure it out.[/QUOTE]
Can you try my script again? I have just solved the same problem on another computer with it.

---

### Post by slugkilla on 2006-05-31
Ok. But first. I found a file called nvidia_dri.o at /usr/lib/modules/drivers like has been said before. If I knew how to rename it, I think it might work. Can someone tell me how to rename it?

---

### Post by slugkilla on 2006-05-31
Wow, so this is where they moved this thread. Did you guys see that weird "no you can't have a poney" image under the global announcement? Twas up for a very short time. Any way, changing that name made everything good and happy. Thanks for the help.

---

### Post by shaungc on 2006-05-31
alo, THANK YOU.  moved the old .so to .so.bak and the .o to .so and everything came up.

---

### Post by ZephyrXero on 2006-06-01
Oddly enough, I was having the version mismatch problem too, but my X was still working.... I may not have rebooted since the update though?

Anyway, I completely uninstalled nvidia-glx, the reinstalled it, rebooted, and it's working again :D

---

### Post by phetre on 2006-06-01
[QUOTE=s|k]I have just given up on proprietary drivers for now. It is just all messed up.[/QUOTE]
I wish I could do the same, but my machine is a media PC with a TV as the primary monitor.  Unless I'm mistaken, TV-out on an FX 5200 requires the proprietary "nvidia" driver.

I really hope the devs are working on this, for the sake of those who can't simply revert to "nv."  By the way, **tseliot** -- may we complain now?  :)

---

### Post by tseliot on 2006-06-03
[QUOTE=phetre]I really hope the devs are working on this, for the sake of those who can't simply revert to "nv."  By the way, **tseliot** -- may we complain now?  :)[/QUOTE]
Yes, now you can :) 

Try removing all the packages:
```
sudo apt-get --purge remove nvidia-glx linux-restricted-modules-`uname -r` linux-restricted-modules-common
```

then
```
sudo apt-get --purge remove nvidia-glx-legacy nvidia-xconfig nvidia-settings linux-restricted-modules-`uname -r` linux-restricted-modules-common
```

then install the nvidia driver:
```
sudo apt-get install nvidia-glx linux-restricted-modules-`uname -r`
```

and reboot

---

### Post by phetre on 2006-06-05
[QUOTE=tseliot]Try removing all the packages:
```
sudo apt-get --purge remove nvidia-glx linux-restricted-modules-`uname -r` linux-restricted-modules-common
```[/QUOTE]

Hmm.  This returned an error:

```
Removing nvidia-glx ...
dpkg-divert: rename involves overwriting '/usr/lib/libGL.so.1.2' with different file '/usr/lib/nvidia/libGL.so.1.2.xlibmesa', not allowed
```

Before reading your guide, I used your method 2 on top of method 1 (that gravest of sins!), but the NVIDIA uninstall script seemed to clean things up.  When I try it now ("sudo sh ./NVIDIA-Linux-x86-1.0-8762-pkg1.run --uninstall"), it tells me "There is no NVIDIA driver currently installed."

Can you tell what the problem is?  By the way, *mille grazie* for your invaluable guides!!

---

### Post by tseliot on 2006-06-05
[QUOTE=phetre]Hmm.  This returned an error:

```
Removing nvidia-glx ...
dpkg-divert: rename involves overwriting '/usr/lib/libGL.so.1.2' with different file '/usr/lib/nvidia/libGL.so.1.2.xlibmesa', not allowed
```

Before reading your guide, I used your method 2 on top of method 1 (that gravest of sins!), but the NVIDIA uninstall script seemed to clean things up.  When I try it now ("sudo sh ./NVIDIA-Linux-x86-1.0-8762-pkg1.run --uninstall"), it tells me "There is no NVIDIA driver currently installed."

Can you tell what the problem is?  By the way, *mille grazie* for your invaluable guides!![/QUOTE]
try this:
1) backup the file:
```
cp /usr/lib/libGL.so.1.2 $HOME/
```

2)remove the file that causes the conflict
```
 sudo rm /usr/lib/libGL.so.1.2
```

then repeat the process which I had suggested before.

---

### Post by phetre on 2006-06-06
[QUOTE=tseliot]try this:[/QUOTE]
Hooray, it worked!  Everything's good again, even TV-out.

---

