---
title: "Can't import photos"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by Billy McCann on 2007-04-25
Howdy.  Thanks for looking in.

I bought a camera after having received suggestions about finding on that would work well with ubuntu.  

the Panasonic Lumix DMC-TZ3 was my choice and it worked very well ...

until today.  

Now I get the error message: An error occurred in the io-library ('Unspecified error'): Could not query kernel driver of device.

Really, it was working two days ago.  I haven't changed anything that I'm aware of.  


Any help is appreciated.  :KS

---

### Post by Billy McCann on 2007-04-25
Changing 

```
BUS!="usb*"
```

to 

```
BUS!="usb_device"
```

in /etc/udev/rules.d/45-libgphoto2.rules worked it like a charm!  

Launchpad rules!  

[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250)

---

### Post by Billy McCann on 2007-04-25
Weird.  

Once I plug in the camera, I get two "Camera detected" messages.  If I click on the first one, I get the above error.  If I wait until the second one pops up, everything works fine.  

Spooky.

---

### Post by jubxie on 2007-04-30
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				this worked for me on my two week old Feisty install. However mine looked like this:
```
SUBSYSTEM!="usb*", GOTO="libgphoto2_rules_end"
```
and I changed it to:
```
SUBSYSTEM!="usb_device*", GOTO="libgphoto2_rules_end"
```
And I agree, launchpad rocks.

---

### Post by sappman2 on 2007-05-07
Thanks, JUBXIE, for pointing me in the right direction.

Changing the *.rules file as JUBXIE suggested worked for me.

---

### Post by Ahunt on 2007-05-20
Hi everyone:

I realize that this thread maybe a bit stale, but I thought I would add my situation to it and see if anyone has any thoughts. 

I tried a new thread at [http://ubuntuforums.org/showthread.php?p=2685665](http://ubuntuforums.org/showthread.php?p=2685665) and didn't get any help other than one user who offered: "Wait for a fix or switch to a distro that features non-system-breaking updates ".

I am running Feisty and using a Panasonic DMC-FZ2 camera. I had a similar experience to others here. The camera was downloading photos a week ago - now it won't and I get an error that says:

"An error occurred in the io-library ('Unspecified error'): Could not query kernel driver of device"

Reading this post and the launchpad bug report at [https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250) I ran through everything suggested here and there that was reported as working, including changing SUBSYSTEM!="usb*" to SUBSYSTEM!="usb_device*" and even running sudo gthumb to see if it is a permissions problem. These solutions seem to have worked for others, but not in this case. I am a member of the "plugdev" group, too.

Can anyone suggest anything else to try to solve this?

Adam

---

### Post by igoddard on 2007-05-21
I'm having the same problem with an FZ20.  I had to resort to my window box.  It's not the first problem since the update to Feisty.  I had a problem with a USM stick which mysteriously got fixed.  And booting is flaky.  The guy who suggested switching to a dstro with non-system-breaking updates may have a point.  If only I could find one....

Ian

---

### Post by Ahunt on 2007-05-22
Dear Ian:

You may be right on that point.

I have my XP PC back from the shop and have confirmed that the camera downloads fine, so it is not a camera problem.

It is unfortunate that these sort of problems keep getting created in Ubuntu. Right now my camera and scanner won't work despite many attempts at work-arounds. (see [http://ubuntuforums.org/showthread.php?t=414474](http://ubuntuforums.org/showthread.php?t=414474) for the scanner issue). Overall this makes Ubuntu less useful than the OS it is supposed to replace. 

I am evaluating Ubuntu at home for future use as the potential OS for my workplace network when mainstream support for XP ends on 14 April 2009. The problem is that at work we rely on cameras and scanners to publish a newspaper and so Ubuntu won't be the replacement OS unless these sorts of issues can be consistently and reliably resolved in the next year or so (and in the case of the cameras where it was working and then stopped - can keep working once they start).

It will be interesting to see how Gutsy deals with cameras and scanners when released this fall.

Adam

---

### Post by igoddard on 2007-05-27
Adam,

One of the annoying things is that USB stuff was working OK in previous releases - Feisty broke it.  The Feisty upgrade also trampled rclocal which was setting permissions for my ancient parallel port scanner - not a big thing to fix but rclocal holds use-specified stuff and upgrades should respect it.

The other annoying thing is that for me Ubuntu isn't supposed to be replacing anything.  This laptop is my regular day-to-day PC.

Synaptic's just downloaded a good few updates including kernel modules so I'll see if that's fixed anything.  I hope so - I've just got back from the Celsea Flower Show with a load of photos & I don't want to spend ages downloading them onto the old W2K box, up to the NAS box and then down to the laptop. So let's do a quick reboot just in case....

---

### Post by igoddard on 2007-05-27
Hmmm.  Some improvement.

I now get the 2 dialog boxes others have mentioned, both correspond to (KDE) desktop icons in the form of a camera.

The first has a camera icon on the dialog box.  If I open that in Konqueror it has a URL of camera://Panasonic Lumix FZ5@[usb:002,00x] where x is the number of times I've opened it but it won't do anything useful.  I can also ignore it.

The second has a USB storage icon.  If I open from the dialog boxthat I can see the contents of the camera memory at /media/disk-1.

I can close & reopen the second any number of times but if I try to reopen the first icon it will fail and the second icon will then be removed and I can only get back into communication by disconnecting & reconnecting the camera.  So it's not quite as broken as before but still broken.

---

### Post by igoddard on 2007-05-27
And finally...

Changing to Gnome, I still get 2 dialogs.  If I dismiss the first I don't seem to get its icon left on the desktop & I can reopen the icon for the second OK.

---

### Post by Ahunt on 2007-05-27
Ian:

That is interesting news. I also downloaded a bunch of Ubuntu updates and just re-tried my Panasonic camera, but there is no change - it still gives the same error: 

```

"An error occurred in the io-library ('Unspecified error'): 
Could not query kernel driver of device".
```

I have done several shoots in the last few days and the camera is working fine - I just have to download them onto my XP PC and than back them up to CD and then install them on the Ubuntu PC from the CD drive.

Hopefully this will be addressed soon!

Adam

---

### Post by rare HERO on 2007-08-05
I'm getting the same error.

---

### Post by kellner on 2007-11-09
For what it's worth: I had the same problem (of the camera not being recognized) with Gutsy; in addition, the camera was shown as a DMC-FZ20, not as a DMC-TZ3. 

By googling, I ran into this tip which solved the problem for me: 

"The Panasonic DMC-TZ3 must be set to "Print mode" via the rotating dial that
sits atop the camera in order to be put in PTP mode.  Once the camera is set
to Print Mode in this way, both  digiKam and  gphoto2 work splendidly with
it"

From here: [http://mail.kde.org/pipermail/digikam-devel/2007-October.txt.gz](http://mail.kde.org/pipermail/digikam-devel/2007-October.txt.gz)

---

### Post by dtvarnum on 2007-11-17
I have the very same situation. Today I started getting this message. I have changed my file and it looks like the following:

# udev rules file for libgphoto2 devices (udev < 0.9
#
#BUS!=”usb*”, GOTO=”libgphoto2_rules_end”
SUBSYSTEM!=”usb_device”, GOTO=”libgphoto2_rules_end”
ACTION!=”add”, GOTO=”libgphoto2_rules_end”
ATTRS{idVendor}=="0553", ATTRS{idProduct}=="0202", MODE="0660", GROUP="plugdev"

However this hasn't helped. I still can connect my lumix camera the way I was just a few days ago. 

uggh, to many updates in Ubuntu.

---

### Post by JoJerome on 2007-11-18
This thread looks close enough to my problem so here it goes:

Distro: Feisty
Camera: Panasonic Lumix FZ10
Connecting camera to PC via USB

I can get photos from camera to PC just fine. But now I want to get some pics from the PC back onto the SD card in the camera. The error message:

"Writing to camera is not supported."

I tried exporting through digiKam but it isn't giving me the option to export to the camera.

It sounds like I need to install some other K/Ubuntu program that supports going from computer to camera? Ideas? Advice?

Thanks in advance...

- Jo

---

### Post by Raval on 2008-01-17
I have an LZ2  switch the camera to PTP instead of PC under USB mode to solve the problem

---

### Post by floflooo on 2008-01-26
> **Raval said:**
> I have an LZ2  switch the camera to PTP instead of PC under USB mode to solve the problem

OMG! Thanks Raval, that's totally what's needed for my digital camera :D. It's a Panasonic Lumix DMC-FX8. Digikam recognizes it as a Panasonic DMC-FZ20 (alternate id) but it was not actually importing picture - I would get a "Failed to connect to camera" error - until I activated the PictBridge mode in the camera menu (Menu > Config > Mode USB > PictBridge).

Now the camera is not detected as a USB Mass storage anymore. But it's handled very nicely: the only thing it does not be able to do is delete pictures from the camera.

---

### Post by Raval on 2008-01-26
> **floflooo said:**
> OMG! Thanks Raval, that's totally what's needed for my digital camera :D. It's a Panasonic Lumix DMC-FX8. Digikam recognizes it as a Panasonic DMC-FZ20 (alternate id) but it was not actually importing picture - I would get a "Failed to connect to camera" error - until I activated the PictBridge mode in the camera menu (Menu > Config > Mode USB > PictBridge).

Now the camera is not detected as a USB Mass storage anymore. But it's handled very nicely: the only thing it does not be able to do is delete pictures from the camera.

Here is something I learnt recently from my camera's manual. On page 85 with the title "Before Connecting to the PC or the Printer"

When [PC] is selected, the camera is connected via _USB Mass Storage_ communication system.

When [PicBridge (PTP) is selected, the camera is connected via PTP (_Picture Transfer Protocol_) communication system.

I'm willing to bet your manual says something similar.

Now that I know this I think Linux is importing pictures in a better way than Windows, in Linux all the import feature does is, well, import and leaves the deleting to the camera.

---

### Post by Raval on 2008-01-28
> **floflooo said:**
> OMG! Thanks Raval, that's totally what's needed for my digital camera :D. It's a Panasonic Lumix DMC-FX8. Digikam recognizes it as a Panasonic DMC-FZ20 (alternate id) but it was not actually importing picture - I would get a "Failed to connect to camera" error - until I activated the PictBridge mode in the camera menu (Menu > Config > Mode USB > PictBridge).

Now the camera is not detected as a USB Mass storage anymore. But it's handled very nicely: the only thing it does not be able to do is delete pictures from the camera.

About deleting pictures from the Camera, I'm using Digikam and on the import window there is an option to delete pictures on the camera. I'm attaching a screenshot so have a look.

---

