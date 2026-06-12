---
title: "[SOLVED] GTX280 woes. :-("
date: 2008-08-31
forum: Multimedia Software
---

### Post by Stenrad on 2008-08-31
Hi All!

Have just got myself a nice new shiny system, (see sig for details). However I have just spent the last two hours trying to get the following NVidia drivers to work but with no success:-

[http://www.nvidia.co.uk/object/linux_display_amd64_177.67_uk.html]("http://www.nvidia.co.uk/object/linux_display_amd64_177.67_uk.html")

I use the following method for installation:

Ctrl+Alt+F5
sudo /etc/init.d/gdm stop
sh NVIDIA-Linux-x86_64-177.67.pkg2.run
sudo /etc/init.d/gdm start

I searched these forums for an answer and came up with the following threads:-

[http://ubuntuforums.org/showthread.php?t=892164&highlight=gtx280]("http://ubuntuforums.org/showthread.php?t=892164&highlight=gtx280")

[http://ubuntuforums.org/showthread.php?t=863522&highlight=gtx280]("http://ubuntuforums.org/showthread.php?t=863522&highlight=gtx280") 

[http://ubuntuforums.org/showthread.php?t=846942&highlight=gtx280]("http://ubuntuforums.org/showthread.php?t=846942&highlight=gtx280")

Still no luck! Can`t even get the command "gksudo displayconfig-gtk" to work. When I try it nothing happens. Also, when I reboot the machine it comes up with the "Low Resolution Setting" and won`t go any higher than 800x600. :-( I am running Ultimate 1.9 if that helps?

Thanks in advance for any help you can give me! :-)

Stenrad.

Btw - forgot to mention that my motherboard is an Asus M3N-HT Deluxe.

---

### Post by scarab72 on 2008-09-09
Well I've got my GTX280 working on Beta drivers, I'm a bit of a N00b to Ubuntu, so the steps I took are as follows:

1) Downloaded the Beta 64 bit drivers from Nvidia [http://www.nvnews.net/vbulletin/showthread.php?t=118602]("http://www.nvnews.net/vbulletin/showthread.php?t=118602") it mentions support coming in 177.67 for our lovely little GTX280 and since release is 177.13 it looks like it's a Beta existence.

2) Stop X, I ended up going **System->Administration->Services** unlocked it, then unticked the Graphical Login manager.

3) **Control-Alt-Delete** to get the PC to reboot then come up with an X-less interface. Login and change directories to where you downloaded the driver.

4) Run the driver as follows
> sudo sh NVIDIA-Linux-x86_64-177.70-pkg2.run
follow the screens through and let it do it's thang.

5) Restart X
> sudo /etc/init.d/gdm start

6) Login and go back in and reactivate the Graphical Login manager in **System->Administration->Services**.

7) (this one took me a little while) make sure "nv" is listed against **DISABLED_MODULES** in **/etc/default/linux-restricted-modules-common** or you'll loose the lovely screen resolution next time you reboot...

If anyone knows a cleaner way I could have done this, or if there are better drivers I'd be happy to hear.

Mark

---

### Post by Baneblade on 2008-09-21
Having similar issues here. Scarab72, iv follwed your directions you posted and it worked great (Thankyou!). However, when setting my res to native 1680x1050 it resets itself to 1280 after a reboot. 
I have tried running the nvidia manager with sudo to stop the error that it doesnt have suffiecient privs to overwrite the .conf file. Nothing.
I have even tried manually editing the .conf file and removing all other resolutions, and it still somehow manages to set itself to 1280!!!
Anyone kn0w of a workaround for this?

---

### Post by soxs on 2008-09-21
Did you install the driver requirements?

Post the output from:
```
cat /etc/X11/xorg.conf|grep Device
```

---

