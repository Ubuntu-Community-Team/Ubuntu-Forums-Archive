---
title: "Camera auto-mounted, but cannot download photos with &quot;Import Photos&quot;"
date: 2008-11-01
forum: Multimedia Software
---

### Post by swerner on 2008-11-01
Hello,

In Hardy Heron this worked without any problems: when I plugged in the camera (Canon S5 IS) the "Import Photos" dialog would appear and I could import the photos without any problems.  However, the camera was not auto-mounted (this is not a problem for me).

Now after upgrading to Intrepid Ibex, when I plug in the camera, it is auto-mounted and when the "Import Photos" dialog appears I get the following error message:
```
An error occurred in the io-library ('Could not lock the device'): Camera is already in use.
```

Any ideas? Yes, I can umount the volume, but this is not tidy.  Is there a way to turn off auto-mount for the camera? Or better yet, can the "Import Photos" work nicely when the camera is mounted?

---

### Post by Denis on 2008-11-12
I experienced the same problem as you do. 

It seems that gvfs automatically mounts the camera and f-spot unmounts it when photographs are being imported. Gthumb (which downloaded your pictures in Hardy) doesn't seem to be able to unmount. 

I figured out how to manually unmount my camera in gvfs. 

You get a list of the mounted devices with "gvfs-mount -l" 
With your camera inserted, the command outputs a line similar to this: "Mount(0): Nikon Corp. NIKON DSC D40 -> gphoto2://[usb:002,019]/"

If I wanted to unmount the volume I could type "gvfs-mount -u  gphoto2://[usb:002,013]/"
But since the device number would change every time, you'd better use this command "gvfs-mount -s  gphoto2". It unmounts all volumes with "gphoto2" in it (which will be your cameras). 

So, to unmount the volume and import when the camera is connected I checked "Import digital photographs when connected" in Preferences > Removable drives and media. In Command I typed "**gvfs-mount -s  gphoto2 & gnome-volume-manager-gthumb %h**"
This will unmount the camera and start gthumb, as you were used to. 

For now, this solution seems to work most times. The command doesn't change anything permanent either, so it's safe to use. 

I hope It works for you too ;)

---

### Post by swerner on 2008-11-12
> **Denis said:**
> ...
So, to unmount the volume and import when the camera is connected I checked "Import digital photographs when connected" in Preferences > Removable drives and media. In Command I typed "**gvfs-mount -s  gphoto2 & gnome-volume-manager-gthumb %h**"
This will unmount the camera and start gthumb, as you were used to. 

For now, this solution seems to work most times. The command doesn't change anything permanent either, so it's safe to use. 

I hope It works for you too ;)

Yes, this works brilliantly for me.  Thanks!!!!

---

### Post by wolfen69 on 2008-11-12
an easier way is to just right click the camera icon and unmount. gthumb will then import. worked for me.

---

### Post by pumrum on 2008-12-02
Along the same lines -- I'm trying to prevent Ubuntu Intrepid from auto-mounting any USB device as a camera, specifically my iPhone. I have been on Gutsy for almost a year and it did not auto-mount the iPhone, but now it does on Intrepid. I'm sure this is a nice feature for some, but I sync my iPhone with iTunes inside VMWare and it is very frustrating to have Ubuntu and VMWare fighting over the iPhone every few seconds, opening all sorts of error boxes in the background that I have to minimize other windows to get to.

Is there something I can blacklist in modprobe.d, or does anyone know where the "Do not automatically mount cameras" option was moved to in Intrepid? You can see the original post relating to the iPhone here:

[http://ph.ubuntuforums.com/showthread.php?t=978623&](http://ph.ubuntuforums.com/showthread.php?t=978623&)

Thanks!

---

### Post by Denis on 2008-12-03
> **pumrum said:**
> Along the same lines -- I'm trying to prevent Ubuntu Intrepid from auto-mounting any USB device as a camera, specifically my iPhone. I have been on Gutsy for almost a year and it did not auto-mount the iPhone, but now it does on Intrepid. I'm sure this is a nice feature for some, but I sync my iPhone with iTunes inside VMWare and it is very frustrating to have Ubuntu and VMWare fighting over the iPhone every few seconds, opening all sorts of error boxes in the background that I have to minimize other windows to get to.

Is there something I can blacklist in modprobe.d, or does anyone know where the "Do not automatically mount cameras" option was moved to in Intrepid? You can see the original post relating to the iPhone here:

[http://ph.ubuntuforums.com/showthread.php?t=978623&](http://ph.ubuntuforums.com/showthread.php?t=978623&)

Thanks!
I've looked around for a moment and it seems indeed that some options in "removable drives and media" have disappeared. Also I checked the "Configuration editor" and I found the settings that appear in "removable drives and media". 

You find these settings under desktop > gnome > volume_manager. All the options are there, including automount_drives and _media. Maybe unchecking automount_media stop the automount of your iPhone? I don't know if you find that a good solution, because it will probably stop automounting of any USB disc. I think at least you'll see all the options that were previously available in "removable drives and media".

---

### Post by pumrum on 2008-12-03
> **Denis said:**
> I've looked around for a moment and it seems indeed that some options in "removable drives and media" have disappeared. Also I checked the "Configuration editor" and I found the settings that appear in "removable drives and media". 

You find these settings under desktop > gnome > volume_manager. All the options are there, including automount_drives and _media. Maybe unchecking automount_media stop the automount of your iPhone? I don't know if you find that a good solution, because it will probably stop automounting of any USB disc. I think at least you'll see all the options that were previously available in "removable drives and media".


I went looking for these, but I could not find 'volume_manager' under desktop > gnome. I also searched for camera, mount, gphoto, gvfs, usb, volume -- none of these turned up anything. Are you using Intrepid? It seems like all of the media options have vanished! :confused:


[edit] I also ran 'sudo gconf-editor' as well, just in case some settings were hidden from regular users. There were no additional options presented when logged in as root.

---

### Post by Denis on 2008-12-04
> **pumrum said:**
> I went looking for these, but I could not find 'volume_manager' under desktop > gnome. I also searched for camera, mount, gphoto, gvfs, usb, volume -- none of these turned up anything. Are you using Intrepid? It seems like all of the media options have vanished! :confused:


[edit] I also ran 'sudo gconf-editor' as well, just in case some settings were hidden from regular users. There were no additional options presented when logged in as root.

I am using Intrepid, but I've updated from Hardy. Maybe that's why I still have these settings. 

I'm not sure if all the settings work. You could try to make a "volume_manager" directory and add automount_media (unchecked box). But honestly I think you'd better find out which program mounts your iPhone. If it is gvfs, then the method I described could be used to unmount it every time. 

There must be a better solution however, but I can't really help you with that.

---

### Post by zzztownsend on 2008-12-04
Hi folks 

With a fresh install of intrepid there is no 
System-->Preferences--> Removable Devices and Media

after some hunting I found that this is now in NAUTILUS, under 
Edit--> Preferences --> Media tab

You can change the photos drop down to a different program. Only problem is that under 'open with other application' and then custom command, you can't put a whole command in - only a single appliction

To get round this I did:
create file in home folder called 'get-photos'
containing <snip>

#!/bin/bash
gvfs-mount -s gphoto2
gthumb --import-photos

<end of snip>

then do
$ chmod +x get-photos

then back in nautilus 'open with other applicaition' 'custom command', use the command /home/username-/get-photos

Bosh! fixed

Thanks to Denis for the hard (by my standards!!) gvfs bit!

---

### Post by Denis on 2008-12-04
That sure is useful information zzztownsend! I had no idea the dialog wasn't there in Intrepid. The preferences in nautilus seem very complete, I wished the developers had placed them somewhere more visible. 

Nice of you to include a bash script. I think this can really help people ;)

---

### Post by rfurman24 on 2009-01-07
This is ridiculous. I had to turn off the import photos under system>preferences>removable drives and media. Then make your bash script only with Digikam and set the bash script to run in the Nautilus file management preferences. I wish I had never left Feisty. Gutsy, Hardy, and Intrepid have all sucked imo. This same issue is causing problems with my cd tray closing immediately after ejecting any time I insert an audio disc with pics on it.

---

### Post by RJARRRPCGP on 2009-01-07
> **swerner said:**
> Hello,

In Hardy Heron this worked without any problems: when I plugged in the camera (Canon S5 IS) the "Import Photos" dialog would appear and I could import the photos without any problems.  However, the camera was not auto-mounted (this is not a problem for me).

Now after upgrading to Intrepid Ibex, when I plug in the camera, it is auto-mounted and when the "Import Photos" dialog appears I get the following error message:
```
An error occurred in the io-library ('Could not lock the device'): Camera is already in use.
```

Any ideas? Yes, I can umount the volume, but this is not tidy.  Is there a way to turn off auto-mount for the camera? Or better yet, can the "Import Photos" work nicely when the camera is mounted?

It looks a lot like the auto mount is causing a conflict.

---

### Post by rsay on 2009-02-08
Thanks guys,

This thread helped me to make using my camera much easier than before. This failure to connect error was causing my wife a lot of grief and she was calling me into the den every time she wanted to download photos off her camera. Here is the script that I call from nautilus preferences>media>photos. It is the same script that I use to start digikam from the Applications menu.

```
#!/bin/bash

# The umask bit sets the default rw properties of any newly created folders
# so that group members can read and write to them
umask 0002

# This part checks to see if gphoto2 has a camera mounted      
if gvfs-mount -l | grep -q "gphoto2" ;then
    # This first command unmounts the camera so digikam can get to it
    gvfs-mount -s gphoto2

    # This part runs digikam under the group users and opens the import dialog
    sg users -c "digikam --detect-camera"

else
    # This runs digikam under the group users without attempting to start an import dialog
    sg users -c digikam
fi
    
# This part changes back to the default r/w properties of newly created folders
umask 0022

```

My wife and I store our photos on a shared drive. The sg and umask parts allow us to be able to access folders and edit photos that the other person created. They could be taken out for somebody that is not using a shared drive.

---

### Post by hvlugger on 2009-03-23
> **Denis said:**
> I experienced the same problem as you do. 

It seems that gvfs automatically mounts the camera and f-spot unmounts it when photographs are being imported. Gthumb (which downloaded your pictures in Hardy) doesn't seem to be able to unmount. 

I figured out how to manually unmount my camera in gvfs. 

You get a list of the mounted devices with "gvfs-mount -l" 
With your camera inserted, the command outputs a line similar to this: "Mount(0): Nikon Corp. NIKON DSC D40 -> gphoto2://[usb:002,019]/"

If I wanted to unmount the volume I could type "gvfs-mount -u  gphoto2://[usb:002,013]/"
But since the device number would change every time, you'd better use this command "gvfs-mount -s  gphoto2". It unmounts all volumes with "gphoto2" in it (which will be your cameras). 

So, to unmount the volume and import when the camera is connected I checked "Import digital photographs when connected" in Preferences > Removable drives and media. In Command I typed "**gvfs-mount -s  gphoto2 & gnome-volume-manager-gthumb %h**"
This will unmount the camera and start gthumb, as you were used to. 

For now, this solution seems to work most times. The command doesn't change anything permanent either, so it's safe to use. 

I hope It works for you too ;)


Denis, I tried this and have to report on Ubuntu Intrepid I needed TWO '&' signs, but then it worked very well, thank you for your work :D

---

### Post by rfurman24 on 2009-04-29
Wanted to bring this back to the top as it seems Jaunty suffers from the same stupidity. So far Jaunty does seem to be a good release.

---

### Post by Denis on 2009-05-01
> **rfurman24 said:**
> Wanted to bring this back to the top as it seems Jaunty suffers from the same stupidity. So far Jaunty does seem to be a good release.

Have you managed to fix it again with zzztownsend's script? Do you get an error with F-spot or do you just prefer to use another program? If your camera doesn't work with the default setting you might consider filing  a bug. 

I'm afraid the developers have selected F-spot as the default photo importer, with no option to chose any other program. I preferred gthumb thought, but maybe F-spot is worth another try...

I haven't updated to Jaunty yet, but on LiveCD it looked promising :)

---

### Post by rfurman24 on 2009-05-02
I use Digikam. I have dedicated many hours to trying to make F-spot work but it is worthless imo. Maybe I am missing something but if I can not browse by folder then I do not need the program.

---

### Post by greenstar on 2009-05-08
I agree with rfurman24's assessment of g-spot. It saves my photos in a labyrinth of subdirectories and does not allow me to easily navigate my photos in an intuitive manner. I have always preferred gthumb & picasa.

---

### Post by jejones3141 on 2009-06-02
Jaunty has the same problem with gvfs and f-spot not playing well together. Under KDE there's no problem.

I seriously hope this is corrected; worst case I will use the workaround, for which many thanks. My wife and I have started a photo booth service for Renaissance fairs--we dress you up, take your picture, and print it for you to take with or pick up at the end of the day, and the whole "workflow" counts on being able to just connect the camera via USB cable and have a program come up automatically to let us snarf the photos quickly while the next person or group is being dressed. Having to fiddle with gvfs-mount would be an extreme pain.

---

### Post by 4ebees on 2009-12-15
> **jejones3141 said:**
> Jaunty has the same problem with gvfs and f-spot not playing well together. Under KDE there's no problem.

I seriously hope this is corrected; worst case I will use the workaround, for which many thanks. My wife and I have started a photo booth service for Renaissance fairs--we dress you up, take your picture, and print it for you to take with or pick up at the end of the day, and the whole "workflow" counts on being able to just connect the camera via USB cable and have a program come up automatically to let us snarf the photos quickly while the next person or group is being dressed. Having to fiddle with gvfs-mount would be an extreme pain.

Hi there. 

There are similar problems listed in this post:

[http://ubuntuforums.org/showthread.php?p=8503224#post8503224](http://ubuntuforums.org/showthread.php?p=8503224#post8503224)

My solution:

Karmic Koala
Kubuntu 9.10

I use a card reader and take the card out of the camera then DO NOT mount the card when I plug it in the reader. This seems to work really well - annoying, but not too bad.

---

### Post by thockin on 2010-01-06
FWIW : Karmic STILL has this problem.  Sigh.  A thousand cuts indeed.  This is stuff that Mickeysoft XP got right in 2001.

---

### Post by jpmeijers on 2010-02-22
I have a Canon G5 with which I want to do remote capturing. Neither gphoto2 nor capture is able to get it going. As far as I can see it is because Ubuntu automounts the camera in "normal" mass-storage mode. The camera then thinks it must reply in normal mode and thus do not react to PTP commands. When I am fast enough with capture's start command, I can manage to run it before ubuntu's automount and thus be able to capture photo's in PTP mode.

This post is the only one that seems to be talking about the same issue. I tried Ubuntu 8.10-9.10 and all of them has got it. 

Does anyone know how I con disable ubuntu's automount and let capture and gphoto2 do their own magic?

---

### Post by Fran on 2010-05-01
> **Denis said:**
> 
So, to unmount the volume and import when the camera is connected I checked "Import digital photographs when connected" in Preferences > Removable drives and media. In Command I typed "**gvfs-mount -s  gphoto2 & gnome-volume-manager-gthumb %h**"
This will unmount the camera and start gthumb, as you were used to. 

For now, this solution seems to work most times. The command doesn't change anything permanent either, so it's safe to use. 

I hope It works for you too ;)

"**gvfs-mount -s  gphoto2 && sleep 1 && gnome-volume-manager-gthumb %h**" works better for me.  

1.  You need double ampersands, I think.

2.  The sleep 1 gives the unmount time to do its thing.

---Fran

---

### Post by Denis on 2010-05-02
> **Fran said:**
> "2.  The sleep 1 gives the unmount time to do its thing.


Very true. I recently had to issue the commands manually because gvfs-mount didn't unmount fast enough. 

Adding "sleep 1" will probably make the command work better for everyone ;)

---

