---
title: "Can someone help me out..."
date: 2009-09-26
forum: Multimedia Software
---

### Post by Cuco3 on 2009-09-26
I'm using an Intel® 845GV mobo chipset that uses the Intel® 82845G integrated graphics video card.

Does anyone know if Jaunty supports this video card at all (I've tried the safe configuration described in the sticky but there's no 2D performance improvement) ?

How bout an older distribution of Ubuntu?

If there is a driver for this card available can someone point me to a link that explains where to DL and how to install it?

I really appreciate any help.

---

### Post by Cuco3 on 2009-09-27
Please?

---

### Post by arnab_das on 2009-09-27
see if this helps:

[http://ubuntuforums.org/showthread.php?t=493082](http://ubuntuforums.org/showthread.php?t=493082)

---

### Post by Cuco3 on 2009-09-27
Hi arnab_das,

That link you posted leads basically suggests to follow another thread. Is that last thread the thread you intended for me to read? Either way, I tried the last thread's suggestion of installing the intel drivers. I still don't get any "Proprietary Hardware Drivers" when I go to System > Administrator > Hardware drivers. And when I installed the drivers, according to the guide, it didn't ask for a restart. Does anybody know of a way to verify if the driver is installed and running?

Tested the new driver. Don't know if it's installed and running since I have no way to verify. Either way, it's still choppy when I scroll or watch flash videos. I got no performance increase and the computer desktop still flickers randomly when trying to use Ubuntu (9.04) after coming out of suspend. :(

Any other suggestions out there?

---

### Post by Cuco3 on 2009-09-27
I actually noticed that video performance has decreased and scrolling / video playback is even more choppier than before. :( :( :(

---

### Post by blackmail on 2009-09-27
I think you should check out this link 
```
http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=13815&lang=eng[/CODE
or if you might want something else you can select from
[CODE]http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&keyword=%22Intel+82845G%22
```
and after you choose which driver to download/compile you can follow this documentation
```
https://help.ubuntu.com/community/CompilingEasyHowTo
```
Note that you have to prepare the computer for the compilation process, after that you quit the x server and then enter the comands for compiling.
Also typing
```
sudo /etc/init.d/gdm stop
```
can cause trouble, because you may not be able to type in the instructions for compiling, but you can use instead you do Ctrl-Alt-F1 from the GUI. This should give you a console while leaving the GUI still there on Ctrl-Alt-F7, use
```
sudo /etc/init.d/gdm stop
```
and other commands from there. I think if you use
```
sudo /etc/init.d/gdm
```
you won't be able to go back to the gui, and so to shut down/restart use the shutdown command e.g. shutdown now.
Hope this helps

---

### Post by Cuco3 on 2009-09-27
I'm gonna give it a try, blackmail.

I have a few question though:

1. Do you suggest downloading all available drivers until I find one that works?
2. How can I tell if a specified driver is installed (System > Administration > Hardware Drivers says I have no proprietary drivers installed).
3. How do I remove the driver later on?

Thanks.

---

### Post by Cuco3 on 2009-09-28
Hmm. I tried installing "checkinstall" but it just stalls with "Setting up checkinstall ( 1.6-1.8 )"

---

### Post by blackmail on 2009-09-28
since there are source files over there, you can make .deb packages from them.This is very theoretical, but the main thing is that if you install a .deb package you should be able to remove it after with
```
sudo spt-get autoremove [package_name]
```
autoremove actually removrs the config files also if i remember right.
I don't know if i remember right but there was a driver i clicked on at the link i gave oyu and it said that it is a viable driver for all the video cards from that family.

---

### Post by blackmail on 2009-09-28
try make and after that make install

---

