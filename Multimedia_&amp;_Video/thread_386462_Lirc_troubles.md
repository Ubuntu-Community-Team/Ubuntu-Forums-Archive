---
title: "Lirc troubles"
date: 2007-03-17
forum: Multimedia &amp; Video
---

### Post by bward1 on 2007-03-17
I have been working on setting up a mythtv "media center" and I have been successful in most regards.  Right now I am trying to get lirc to work so that i dont have to get up and move to the old school wired PS/2 keyboard.  I have a snapstream firefly mini remote control which has a usb receiver.  I found in this article: [http://mythtv.org/wiki/index.php/Snapstream_Firefly](http://mythtv.org/wiki/index.php/Snapstream_Firefly) that the lirc_atiusb kernel module (driver) is what I need even though it is not ati.  I recognize that this is the firefly and not the firefly mini, but the mini page doesn't specifically reference which driver to use, but does say "There are two version of this remote. The original full size rf firefly remote and the new mini-firefly remote that is IR based." - [http://www.mythtv.org/wiki/index.php/Snapstream_firefly_mini](http://www.mythtv.org/wiki/index.php/Snapstream_firefly_mini) . I am beginning to wonder now if the lirc_atiusb driver was the right one to choose, but even if it wasn't I wouldn't know which one to use instead.

Assuming that the atiusb driver is the one that I am suppose to use, I have had some troubles with it.  I can start and stop lirc, but when i do```
irw
```it just brings me to the next line instead of pausing to see my remote control input.  I then do```
dmesg
```to see what is going on and this is the result:```
[17179991.544000] lirc_dev: IR Remote Control driver registered, at major 61 
[17179991.548000] lirc_atiusb: no version for "lirc_unregister_plugin" found: kernel tainted.
[17179991.548000] 
[17179991.548000] lirc_atiusb: USB remote driver for LIRC v0.5
[17179991.548000] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
[17179991.548000] usbcore: registered new driver lirc_atiusb

```I think the "no version for "lirc_unregister_plugin" found; kernel tainted." message means that I did something wrong, and that is why it isn't working correctly.  This is the guide that I tried to follow to get it setup:  [https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy) .  I also have tried and failed to get this to work using the lirc cvs.  [http://www.lirc.org/cvs.html](http://www.lirc.org/cvs.html) .  Don't know if it matters, but I tried the cvs install first, and upon failure ran```
sudo make uninstall
sudo make clean
sudo reboot
```
Getting this setup is pretty critical to my mythtv setup.  Any help would be greatly appreciated.

---

### Post by nigel502 on 2007-04-01
Are you still having problems with this - I am having the same issues with my full firefly remote. Before I restarted I could see the values sent up from the remote, but after restarting everything seemed to just fall apart. 

I tried to follow the jist of this:

[http://www.mythtv.org/wiki/index.php/Talk:Lirc_on_Ubuntu_Dapper#Fix_for_erroring_lircd.2Firw](http://www.mythtv.org/wiki/index.php/Talk:Lirc_on_Ubuntu_Dapper#Fix_for_erroring_lircd.2Firw)

And it seems that they are having the same problems.

Now when I run

/etc/init.d/lirc stop 

and put in the line 

lircd -d /dev/lirc/0

and then run 

irw

I can view the codes from button pushes on the remote. However, whenever I hit irw after running:

/etc/init.d/lirc start 

irw subsequently halts. 

Does that help lead any insights?

---

### Post by bward1 on 2007-05-06
I fixed the problem.  First thing I did was reinstall the operating system to gentoo instead of ubuntu.  Then I emerged lirc and used the lirc_atiusb kernel module.  The secret was to link /dev/lircd to /dev/lirc/0 and after that irw worked in that it waited for an input.  The last and final step to getting the input to work properly was to replace the batteries in the remote.  That's how I got things to work, don't know if that is at all helpful as an ubuntu user, but if you have the patience to work with gentoo, then that is how you would do it.  Who would have thought I would have to switch to gentoo of all distros to get this thing working?

---

