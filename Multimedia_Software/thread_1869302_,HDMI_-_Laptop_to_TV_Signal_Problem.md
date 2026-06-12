---
title: ",HDMI - Laptop to TV Signal Problem?"
date: 2011-10-25
forum: Multimedia Software
---

### Post by CollyMcKen on 2011-10-25
Hi,

I am trying to connect my Sony Vaio laptop to a 40" Panasonic HD TV.  Now when I select monitors I do see that ubuntu has picked up the Panasonic as a 2nd monitor - and I have tried all the various options, 50Hz/60Hz, changing the resolution, etc.  However the signal/picture it send to the TV is very poor - purple type colour and you cant really make out anything.  The weird thing is that I left the laptop as dual boot with Windows 7 still on there.  So I just tried out with Windows and it displays the picture 100% on the TV.  Anyone have any ideas on what to try in my ubuntu setup to try and resolve this?

---

### Post by papibe on 2011-10-25
Hi CollyMcKen. Welcome to the forums!

What graphic card do yo have? If you are not sure, just post the result of this command:
```
lspci | grep -i vga
```
It would be also helpful to check your Xorg log right after you boot with the TV connected. The log is located here:
```
/var/log/Xorg.0.log
```
You can open the file with an editor like this:
```
gedit  /var/log/Xorg.0.log
```
Paste the content using [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and post the link here.

Regards.

---

### Post by CollyMcKen on 2011-10-25
Hi papibe,

Many Thanks for your response.  I wont get a chance to post the Xorg log until I get home again tomorrow.  Will post it when I get it done.  Just as a learning point what is the Xorg log and what would it show?  Thanks.

Below is the result of the Graphics card command which you first mentioned.

```
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
```

---

### Post by papibe on 2011-10-25
I'm not very familiar with ATI/AMD cards, but I think it's relevant to know if you have installed the proprietary driver.

Have you? If not, may a good thing to try. I don't know any good tutorials, except [this]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") one. I also, as stated on that help doc, recommend using the driver offered and maintained by Ubuntu.

After you installed the driver you should use the AMD tool to setup your monitors. [Here]("http://askubuntu.com/questions/70108/dual-view-monitors-for-one-desktop-on-ati") are some general instructions.

Hope it helps, and let us know how it goes.
Regards.

EDIT: The xorg log shows details on how the monitors are being recognized, what resolutions and timings can be use on them, etc. A good start to tackle your problem.

---

### Post by CollyMcKen on 2011-10-26
Thanks for the help papide.  I will work on this when I get home from work today and let you know how I get on.  I will also post the Xorg log and thanks for the explanation on it.

---

