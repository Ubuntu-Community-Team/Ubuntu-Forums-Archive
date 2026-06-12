---
title: "Transfering photos from cannon EOS 400D"
date: 2011-07-12
forum: Multimedia Software
---

### Post by Sylos on 2011-07-12
Hello and thanks for taking the time to look.

I am trying to set up a lubuntu  10.04 system to allow the user to transfer the photos from his canon EOS 400D digital camera. Sounds pretty easy but sadly a problem has been encountered. When you plug in the camera and turn it on you get the option to eitehr launch shotwell or open in file manager. So, the user opens shotwell and it loads and they do the import dance - and all seems to go well.
BUT...

Some of the files are not being transfered. Some of them appear to be transfered but when you try to open them you get an error saying the file contains no data. Other times the file just doesnt exist at all you skip from 404 to 406 (for example) in the file list.

I tried install F-spot and using that but it wont auto unmount the camera first meaning the user has to do it - and that is way more complicated than the user can handle. When I did get F-spot working it appeared to copy ok but I didnt have time to run a lot of tests.

So, being a reasonably practically minded guy I think 'ok...I'll write a little script to unmount the drive and then launch F-spot. OR I'll write one to auto copy the files from the camera to the HDD then the user can import them from shotwell later from the HDD.'

But where does it mount to....

I looked around and found that these canon EOS cameras use PTP to transfer files so the camera is not being mounted as a file system. When I tries to open the camera in file manager (when given the option after plugging it in) I can view and copy all of the files but using the stated location in terminal or a script just returns an error regarding file/folder not existing.

So im stuck. The user is not computer savvy and I really need to make this process as easy and 'one-click' as possible. But it needs to be reliable.

Any insights into how I go about this (be it fixing shotwell or scripting a way around it) will be very welcome.

Thanks

---

### Post by ~!geek!~ on 2011-07-12
OOps posted by mistake here! Removing it to appropriate thread.
[]("http://ubuntuforums.org/showthread.php?t=1480096&page=2")

---

### Post by Sylos on 2011-07-12
Update:

Having tried and failed at the time to use gphotofs I am now wondering if that might be the option (my failure was down to my error I think).

Could I write a script to gphotofs mount the camera to my Media folder (say under a folder called mount). The script could then cp /media/Camera/DCIM/127Canon/* /Home/pics to copy all of the files on the camera to the HDD. I think I would need to add the user to a group to use Fusemount before this would work. I would then also need the script to unmount the camera when it was done. And it would need some way of indicating when it was finished transfering.

Im an absolute fool when it comes to scripting. Could anyone help me out with how I structure the above (assuming it has any chance of working)?

Thanks

---

### Post by handy on 2011-07-13
My understanding is that you are best off not to connect DSLR or other cameras that contain sophisticated software to computers as there is a chance (small but still) of problems occurring on the camera side.

It is best to use a card reader & transfer your data that way. With any luck that may get around the problem that you have been facing.

My Nikon D90 is not recognised by my Arch (custom built) Linux system, but it has no problem auto mounting USB external HDDs, flash & card readers with various types of chips in it.

---

### Post by Sylos on 2011-07-13
Thanks for the reply handy.

I agree that (for most people) using a card reader and mounting it as a flash drive is the easiest way. Sadly this is my dads camera and PC and the less he needs to mess about pulling 'fiddly' bits out of the camera the better. Im keeping the SD card reader as a back up. Does the following look like it might work:

```
Gphotofs /Media/Camera; #Mount camera as filesystem
cp /Media/Camera/DCIM/127Canon/* /Home/username/Pics; # copy files from camera to HDD
fusermount -u /Media/Camera #unmount filesystem
```

Thanks

---

### Post by handy on 2011-07-13
Seeing that it seems that you don't mind messing with code, you may like to look at the attached code & modify it to suit, if you do, please let us know how you go:

---

### Post by Sylos on 2011-07-13
Thanks for the help handy.

As I am a proper code dunce I just wanted to clarify what your script is for. It appears that it is used for mounting the camera and showing it in nautilus when it is not mounting automatically - yes?

My problem is a little more difficult to play with. As the camera uses the PTP transfer protocol it doesnt mount the SD card as a filesystem - Im not sure what it does do but it seems to be a bit abstract (to me anyway). In order to access the SD card as a filesystem I have to create a kind of virtual filesystem using fusemount - achieved by using gphotofs. I should probabbly stress at this point that I am only repeating what I have read on the manpage for gphotofs and other such sources.


Anyway, I suppose the only way Im gonna sort this is to try some lines of code and see what happens. I doubt Im gonna achieve anything as tidy and elegant as yours - if I can just make it work I'll be pleased.

Cheers

---

### Post by handy on 2011-07-15
I'm all for credit where credit is due.

So you should know that I did not write that code. :)

Good luck with it.

---

