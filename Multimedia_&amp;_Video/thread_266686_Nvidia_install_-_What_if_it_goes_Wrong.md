---
title: "Nvidia install - What if it goes Wrong?"
date: 2006-09-27
forum: Multimedia &amp; Video
---

### Post by kyozo on 2006-09-27
Hi,

I'm thinking of installing the nvidia drivers nvidia-glx, but I have tried this before, and ended up reinstalling Ubuntu. I want to avoid doing this again, and I need a quick way to "undo" the installing if it goes wrong.

Can I just remove the package nvidia-gfx if for some reason the install progress goes wrong, or if the results were not as I expected?

Or is there anyway to do a full system backup, so that I can restore this if the nvidia driver install fu... up?

by the way, I just looked at my xorg.conf, and can see that my driver is set to nv not nvidia, as it is said in the guide, should I change this before installing the nvidia-glx package?

Thanks for your help.

Kyozo

---

### Post by tseliot on 2006-09-27
First of all there is no need to reinstall Ubuntu if the installation of the driver fails or if the driver doesn't work (and maybe requires only some tweaking).

Make sure that your card is supported. Post the output of this command:
```
lspci -n | grep 300
```

Then I will tell you if it's supported.

Usually I recommed Method 1 of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_1](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_1)

there is also this section in case of problems:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_TO_DO_IF_THE_METHOD_YOU_CHOSE_DID_NOT_WORK_OR_WORKED_PARTIALLY](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_TO_DO_IF_THE_METHOD_YOU_CHOSE_DID_NOT_WORK_OR_WORKED_PARTIALLY)

Or you can just ask for help here on the forums on my thread and I'll be glad to help you:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)


And if you want to uninstall the driver you will learn how to do that right after the instructions for method 1.

[COLOR="Red"][B]
Please don't mix Method 1 and Method 2 (if Method 1 doesn't work, Method 2 won't solve the problem)[/B][/COLOR]

---

### Post by pseudonym on 2006-09-27
If you want to be really safe you can do a system backup. The utility I use is called [partimage]("http://www.partimage.org/Main_Page"), and it's very easy to use. You can download a bootable linux rescue CD from [here]("http://www.sysresccd.org/Main_Page"), which contains partimage and many other useful tools.

Just boot up the rescue CD and it will bring you to a root prompt. You first need to create the directory where you will store your partition images. Another internal drive or (better) an external hard drive are the best options. Just mount your destination drive and create a mountpoint in /mnt for it. Now type 'partimage' at the prompt and follow the steps (which you should read about in the documentation first ;) ).

If your partition is not too big it doesn't take very long to complete. If you have your / partition as a standalone partition even better, because that's the only one that needs backing up (for this purpose anyway).

As far as editing xorg.conf goes, it doesn't matter when, so long as it's BEFORE you start X again after installing the driver. You really shouldn't have much to worry about if you follow closely the howtos by tseliot .

---

### Post by kyozo on 2006-09-29
Hi thanks for your replies.

Output of command lscpi -n | grep 300 is

```
0000:01:00.0 0300: 10de:0253 (rev a3)
``` which should be equal to a GeForce4 ti4200 (from MSI) and as far as I have found out, it should be compatible with the nvidia-glx drivers.

tseliot I have looked at your guides, and they look very comprehensive, so I have a little more confidense in trying to install the drivers again :). The reason I reinstalled my Ubuntu last time I tried installing the nvidia drivers was, that I removed too many packages when trying to remove the nvidia-glx package, and I couldn't boot X at all.

I do not have a lot of time or patiense reconfiguring my Ubuntu, that is the reason why I was interested in being able to do a system backup. Unfortunately my root partition uses most of an 160gb disk (although most data is stored in /home). So a full diskbackup would not be sensible - I have several other disks, but I haven't installed them at the moment.

I think I'll try to install the driver without making a backup. Hoping that some of you would be kind enough to help me if it goes bad :).

Unfortunately I'm quite busy this weekend, so I don't have the time to try it out until monday or tuesday, but that doesn't mean I have given up on the task :)

---

### Post by tseliot on 2006-09-29
> **kyozo said:**
> I think I'll try to install the driver without making a backup. Hoping that some of you would be kind enough to help me if it goes bad :).

Unfortunately I'm quite busy this weekend, so I don't have the time to try it out until monday or tuesday, but that doesn't mean I have given up on the task :)
If you have any problem we will help you ;) (even if the Xserver doesn't work any more)

---

### Post by kyozo on 2006-10-07
Hi, finally I had the time to try the install.

I installed the nvidia-glx drivers fine.

When I ran nvidia-glx-config enable it said something about my x config being altered but also said something about an error occurred and that I should my md5 checksum or manually edit my xorg.conf to change the driver section from nv to nvidia.

I changed the driver section from nv to nvidia. but I still get the same error. Although I get the nvidia logo when restarting X.

I tried playing some video, which looked fine, I also installed an OpenGL game (Critical Mass) and an OpenGL demo (Amoeba) both from the Synaptic package installer. These programs also run fine, and it looks like they are 3d accellerated.

When I try to run sudo nvidia-glx-config enable I still get the same error as before even though my xorg.conf has nvidia as the driver.

Should I do anything more, or is this working as supposed? Should I update the xorg.conf with the md5 hash?

Thanks for your help.

P.S. Is there any way to actually check that 3d accelleration is enabled?

P.P.S. It seems I can only run my resolution in 85hz which actually looks a little blurry, so I would like to go down to 75hz, but the screen resolution tool does not allow me to do that. I can change resolution fine, but not the refresh rate.

Cheers Kyozo

---

### Post by tseliot on 2006-10-07
> **kyozo said:**
> When I ran nvidia-glx-config enable it said something about my x config being altered but also said something about an error occurred and that I should my md5 checksum or manually edit my xorg.conf to change the driver section from nv to nvidia.
This means that you haven't read (or followed) my guide.

the command is:
```
sudo nvidia-xconfig
```


> **kyozo said:**
> I tried playing some video, which looked fine, I also installed an OpenGL game (Critical Mass) and an OpenGL demo (Amoeba) both from the Synaptic package installer. These programs also run fine, and it looks like they are 3d accellerated.

When I try to run sudo nvidia-glx-config enable I still get the same error as before even though my xorg.conf has nvidia as the driver.

Should I do anything more, or is this working as supposed? Should I update the xorg.conf with the md5 hash?
sudo nvidia-glx-config enable is broken. It is supposed to set the driver to "nvidia" in your xorg.conf, but that is something which you can do manually.

> **kyozo said:**
> P.S. Is there any way to actually check that 3d accelleration is enabled?
post the output of:
```
glxinfo | grep direct
```

> **kyozo said:**
> P.P.S. It seems I can only run my resolution in 85hz which actually looks a little blurry, so I would like to go down to 75hz, but the screen resolution tool does not allow me to do that. I can change resolution fine, but not the refresh rate.
Try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Then if that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by kyozo on 2006-10-07
Hi,

I read your guide, but I actually think I followed the [binaryDriverHowto/Nvidia]("<a href="https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia">") page on the wiki. I didn't notice the difference - my bad.

So the manual editing of the xorg.conf from nv to nvidia is all that it takes?. I shouldn't do anything about the md5hash?

the output of glxinfo | grep nvidia is
```
direct rendering: Yes
``` - so i assume this means 3d accelleration is enabled.

point 10 in the troubleshooting guide worked fine. I added this mode to my default resolution "1280x1024_75", and when I restarted X it ran in 75Hz.

Thanks for all your help and patience :)

---

