---
title: "Can't connect my Canon 20D in Ubuntu..."
date: 2006-09-16
forum: Multimedia &amp; Video
---

### Post by madcow72 on 2006-09-16
I should admit that I am very much a newbie to Linux - just made the switch about 2-3 weeks ago.  One of the last issues I can't seem to resolve yet, is the ability to connect my digital camera to my box.  I have a Canon EOS 20D DSLR and can't seem to connect.  In my limited knowledge, I expected that the camera would be recognized as a USB mass storage device when I connected, but nothing happens.  Is there any way of probing for the device / mounting it as a drive?  Also, can I expect that Linux will see the raw .cr2 files?  (This doesn't happen in Windows, which is why I ask.)

Any help / leads on this issue would be greatly appreciated!

---

### Post by slimdog360 on 2006-09-17
try picasa or gphoto2 (which picasa is based off).

---

### Post by vinnn on 2006-09-17
Your 20D, like my 350D should be in PTP connection mode by default, that's why it doesn't show as a mass storage device. (Although I ain't sure if it'd shown up in USB mode either).

Anyway, keep you camera in PTP mode and do a..

```
sudo apt-get install digikam digikamimageplugins kipi-plugins gimp-ufraw gimp-dcraw
```
This will give you RAW support in The GIMP and install digiKam (which is a great KDE based image organizer and editor, nicer and more featureful than Picasa or F-Spot) with a bunch of plugins including filters, effects & RAW support within digiKam.

You'll then be able to connect and download your images straight from your camera within digiKam and also do some neat stuff like automatically rotate and update EXIF orientation data as they transfer.

Tip: You have to enable the digikam & kipi plugins manually in digikam's preferences.

---

### Post by madcow72 on 2006-09-18
Vinnn, 

Thanks for the advice!  I hadn't checked out Digikam yet, it looks like a good program.  I realized that I was being stupid...my camera was not set to PTP-Mode on the menu.  As soon as I fixed this, my camera was immediately recognized by the computer, of course.  Unfortunately, Digikam is stalling when trying to import pictures from my camera and then giving me the error that it couldn't import.  I'll keep working on that.  Probably something stupid that I'm doing again - if I find something interesting, I'll post it in case anyone else has the same problem in the future.

Oh, by the way, apt tells me that gimp-ufraw and gimp-dcraw are conflicting packages, so I only installed gimp-dcraw...

---

### Post by madcow72 on 2006-09-18
OK, should be the last post in this session.  I just wanted to mention how I got my Canon EOS 20D to connect and download .cr2 images for editing in case anyone as clueless as I searches for help on the same subject:

1)  Make sure your camera is in PTP mode, (Menu -> Communication -> PTP)

2)  Install Digikam (This isn't necessary as other programs like Picasa will also work, but Digikam seems much cleaner and faster)
```
sudo apt-get install digikam digikamimageplugins kipi-plugins
sudo apt-get install gimp-dcraw
```

3) Configure Digikam to connect to your Camera, (Camera -> Add your Camera)

4) Turn your camera on and connect to the computer with USB.

5) Browse and Download your pictures by choosing your camera model under the "Camera" menu option.

As a last note, I want to add how much simpler this process is under Linux as opposed to Windows where you need particular Canon drivers and software to even connect the camera up and see images in the first place, not to mention obtaining the raw files.  If I wasn't convinced to stick with Linux before, I think I am now...

---

### Post by djinni on 2006-09-19
I'm running xubuntu on my Toshiba Satellite laptop.  I have a Canon Powershot 1S

I couldn't get the install working from the terminal.  But I was able to get digiKam and the other stuff installed using the synaptic package manager and the install CD.

digiKam works to download images directly from the camera using PTP.  It has some problems.  Sideways images are automatically rotated, even though the camera viewer shows them rotated properly.  I can rotate images using the digiKam software, but it seems to close out digiKam at the end of the operation.

After one restart, there were some error messages, but digiKam came up anyway.

Another issue I had is with photo-stitch images.  The camera has a feature where you snap a bunch of overlapping images.  The windows software can stitch these all together to make a single landscape portrait.  The images won't download using digiKam.

---

### Post by madcow72 on 2006-09-22
What sort of error messages are you getting when you try to re-start DigiKam?

You should be able to see your camera as a mass storage device appearing on your desktop after you plug in.  Have you tried manually copying the images onto your harddrive?  Are the images .jpg or some weird proprietary format?

Unfortunately, I'm too new to Linux right now to suggest any replacements for photo-stitch, although I'm sure they exist...

---

### Post by elevel on 2008-02-03
I just like to confirm, that the suggested approach using DigiKam also works fine with the Canon PowerShot G9. :)

Currently using openGEU which is based on Ubuntu 7.10

---

### Post by experttease on 2008-04-13
So is it not possible to see it as a drive? I would use picasa but it's on top of wine and a pain. F-Spot imports the photos but each time I have to move the photos, picasa on windows is awesome as it just indexes your photos and desn't make a pointless extra copy (unless you edit them, in which case it backs them up), whereas F-Spot thinks I want an extra copy of them when I import locally, and it...sorry, have I repeated myself?!...and it has this weird folder structure which is useless if you want to navigate them in nautilus...thanks for listening..

---

