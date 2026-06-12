---
title: "Computer suddenly won't boot to desktop"
date: 2012-01-21
forum: Multimedia Software
---

### Post by Crimson_Tider on 2012-01-21
I upgraded to Oneiric in November and after some trouble, got my video card working perfectly. Today, for some reason, my computer suddenly stopped booting to the desktop. Now it goes the BIOS screen and then goes to a dark purple background, which it usually shows for a few seconds before displaying the splash screen, but now it just stays on that blank screen with the dark purple background. I have the NVIDIA GeForce 7025 onboard video. Any help would be appreciated. Thanks!

---

### Post by sanderd17 on 2012-01-21
In grub, can you press 'e' to go to the edit mode?

There you should delete the words "quiet splash" and try to boot.

Now you will see a bunch of text instead of a splash screen. Can you tell us where it hangs?

EDIT: If you don't see any error message or so, you can take a picture of the screen, check that the text is readable, and upload it here.

---

### Post by ashwinrao on 2012-01-21
While you are presented with Grub screen, press keyboard button 'e'. You'll be presented with the lines code of Grub. Find the term 'quiet splash' in it. Replace those with 'nomodeset' and try to log in. If the issue persists, please provide us with error message or screen shot as suggested by '[sanderd17]("http://ubuntuforums.org/member.php?u=742644")'.

---

### Post by Crimson_Tider on 2012-01-21
My computer never goes to the grub menu. I think it's set that way by default, right? I can get to a console with Ctrl+Alt+F1. How can I get the grub to show up using that?

---

### Post by sanderd17 on 2012-01-21
> **Crimson_Tider said:**
> My computer never goes to the grub menu. I think it's set that way by default, right? I can get to a console with Ctrl+Alt+F1. How can I get the grub to show up using that?

Oh, so your computer completely boots, but you just don't get gdm.

changing grub things won't help with that (as far as I see).

maybe try from the tty to do
```

sudo rc.d restart gdm

```

and see what you get.

---

### Post by Crimson_Tider on 2012-01-21
> **sanderd17 said:**
> Oh, so your computer completely boots, but you just don't get gdm.

changing grub things won't help with that (as far as I see).

maybe try from the tty to do
```

sudo rc.d restart gdm

```

and see what you get.

```
sudo: rc.d: command not found
```

---

### Post by sanderd17 on 2012-01-21
> **Crimson_Tider said:**
> ```
sudo: rc.d: command not found
```

Sorry, drop the rc.d. And I forgot that oneiric uses lightdm, so try

```

sudo restart gdm

```
AND
```

sudo restart lightdm

```

---

### Post by nipunshakya on 2012-01-21
I would suggest you remove your graphics card once and try to boot....see what happens...sometimes your video card might cause boot failure too....Goodluck

---

### Post by Crimson_Tider on 2012-01-21
```

sudo restart gdm

```

gives me

```
restart: Unknown job: gdm
```

and

```

sudo restart lightdm

```[/QUOTE]

gives me

```
restart: Unknown instance:
```

---

### Post by Crimson_Tider on 2012-01-21
> **WinuxUser said:**
> I would suggest you remove your graphics card once and try to boot....see what happens...sometimes your video card might cause boot failure too....Goodluck

I don't actually have a graphics card.  I have onboard video.

---

### Post by Crimson_Tider on 2012-01-21
I ran the command

```
sudo apt-get remove nvidia-*
```

earlier.  Would that be why those commands are not working?

---

### Post by Crimson_Tider on 2012-01-21
Still needing help. Thanks for the help so far!

---

### Post by Crimson_Tider on 2012-01-22
Is there anyone who can help me out?

---

### Post by nipunshakya on 2012-01-22
I think there is some problem with your video stuff...as u said its onboard, but u said u had some problems with it earlier during installation too... still one more time i suggest u do something with your onboard stuff...Goodluck

---

### Post by Crimson_Tider on 2012-01-22
> **WinuxUser said:**
> I think there is some problem with your video stuff...as u said its onboard, but u said u had some problems with it earlier during installation too... still one more time i suggest u do something with your onboard stuff...Goodluck

What exactly should I do? I'm still new to handling problems like this in Ubuntu--I need to know what commands I need to run. Thanks!

---

### Post by nipunshakya on 2012-01-22
ok i got this from somewhere......
Boot to live mode from the cd.
There open gparted and see if u find anything unusual with your partition stuff....
then,open terminal and try the following:
```
sudo add apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
```
add the repo...and then install boot repair with following
```
sudo apt-get install -y boot-repair && boot-repair
```
it will scan your system. Try the recommended repair and see if it works.


Goodluck
Regards,WinuxUser

---

### Post by Crimson_Tider on 2012-01-22
> **WinuxUser said:**
> ok i got this from somewhere......
Boot to live mode from the cd.
There open gparted and see if u find anything unusual with your partition stuff....
then,open terminal and try the following:
```
sudo add apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
```
add the repo...and then install boot repair with following
```
sudo apt-get install -y boot-repair && boot-repair
```
it will scan your system. Try the recommended repair and see if it works.


Goodluck
Regards,WinuxUser
O
I don't have a live CD, and the live USB drive that I used to install isn't being recognized by my computer for some reason.  It's a brand new device.  Maybe you could help me get that mounted?

---

### Post by nipunshakya on 2012-01-22
Sorry mate, I haven't tried out linux from pendrives till now so i have no idea what is needed to be done. 
Still, have u changed ur BIOS settings to boot from your pendrive and restarted your machine?? Looks funny to ask but still....

---

### Post by Crimson_Tider on 2012-01-22
> **WinuxUser said:**
> Sorry mate, I haven't tried out linux from pendrives till now so i have no idea what is needed to be done. 
Still, have u changed ur BIOS settings to boot from your pendrive and restarted your machine?? Looks funny to ask but still....

No, that didn't seem to make sense because it doesn't seem to be recognizing it at all, but I will try that now anyway.

---

### Post by Crimson_Tider on 2012-01-22
> **Crimson_Tider said:**
> No, that didn't seem to make sense because it doesn't seem to be recognizing it at all, but I will try that now anyway.

That didn't work.  It's not showing as a boot option in the BIOS screen.

---

### Post by Crimson_Tider on 2012-01-22
> **Crimson_Tider said:**
> That didn't work.  It's not showing as a boot option in the BIOS screen.

I've now tried 2 USB drives and an SD card, and none of them are showing up in /media.  Do I need to mount them with a command or something?

---

### Post by nipunshakya on 2012-01-22
man, seriously, im running out of ideas. 

Now the only thing for me to sugest you is...A Clean Installation from LiveCD. Don't go for pendrive installation this time, coz u saw na how these pendrives respond when in trouble>? hehe

---

### Post by Crimson_Tider on 2012-01-22
> **WinuxUser said:**
> man, seriously, im running out of ideas. 

Now the only thing for me to sugest you is...A Clean Installation from LiveCD. Don't go for pendrive installation this time, coz u saw na how these pendrives respond when in trouble>? hehe

I'm thinking it has something to do with the mounting process, and I don't know how that works.  How do I force it to mount my drive?

---

### Post by sanderd17 on 2012-01-22
[s]Why is that restarting of services different for all distros.

Now, this should work:

```

sudo /etc/init.d/lightdm restart

```

or gdm instead of lightdm.[/s]

Edit: missed a number of pages, will have to read the whole thread before I post.

---

### Post by sanderd17 on 2012-01-22
Ok, your devices are not loading because it's gnome that looks for the auto-mounting. They should appear in /dev though (probably as sdb or sdc).

But back to the lightdm restarting, can you retry to restart the service? Sorry for the problems, but restarting services is different in a lot of OS.

Now, this should work:

```


sudo /etc/init.d/lightdm restart
```

or gdm instead of lightdm.

---

### Post by Crimson_Tider on 2012-01-22
> **sanderd17 said:**
> Ok, your devices are not loading because it's gnome that looks for the auto-mounting. They should appear in /dev though (probably as sdb or sdc).

But back to the lightdm restarting, can you retry to restart the service? Sorry for the problems, but restarting services is different in a lot of OS.

Now, this should work:

```


sudo /etc/init.d/lightdm restart
```

or gdm instead of lightdm.

That gives me

```
sudo: /etc/init.d/lightdm: command not found
```

---

### Post by Crimson_Tider on 2012-01-22
> **Crimson_Tider said:**
> That gives me

```
sudo: /etc/init.d/lightdm: command not found
```

I tried that again, but this time I changed the directory to /etc/init.d and then executed the command.  When I did this, I got a totally black screen.  Did you read post #11 of this thread?  I'm still thinking that might have something to do with what it's doing now.

---

### Post by Crimson_Tider on 2012-01-22
By the way, using gdm instead gave me the same command not found error.

---

### Post by Crimson_Tider on 2012-01-22
It really would be nice if I could access the files on any USB drive.  But for some reason I am unable to mount any of the three.  I ran lshw -class disk, and it showed all of them.  One of them is sdc, so I did

```
mkdir /mnt/usbdrive0
mount /dev/sdc /mnt/usbdrive0 -t devtmpfs
```

After that, I did

```
ls /media
```

And got

```
External Hard Drive
```

But I don't even have an external hard drive connected, and it still isn't showing the USB drive there.

I'm very much a newbie, but that seems really strange to me.  Why am I unable to mount and access my USB drive?

---

### Post by Crimson_Tider on 2012-01-22
Anyone?

---

### Post by sanderd17 on 2012-01-23
> **Crimson_Tider said:**
> It really would be nice if I could access the files on any USB drive.  But for some reason I am unable to mount any of the three.  I ran lshw -class disk, and it showed all of them.  One of them is sdc, so I did

```
mkdir /mnt/usbdrive0
mount /dev/sdc /mnt/usbdrive0 -t devtmpfs
```

After that, I did

```
ls /media
```

And got

```
External Hard Drive
```

But I don't even have an external hard drive connected, and it still isn't showing the USB drive there.

I'm very much a newbie, but that seems really strange to me.  Why am I unable to mount and access my USB drive?

With the above commands, you mounted it to /mnt. so you should ls /mnt instead of /media.

---

### Post by Crimson_Tider on 2012-01-23
> **sanderd17 said:**
> With the above commands, you mounted it to /mnt. so you should ls /mnt instead of /media.

I did that also, and it gave me a huge list of files or directories that included sda, sda1, sda2, etc., tty10, tty11, tty12, etc., cdrom, cdrw, and a bunch of other things.  Certainly not the contents of my SD card or USB drive.

---

### Post by sanderd17 on 2012-01-24
> **Crimson_Tider said:**
> I did that also, and it gave me a huge list of files or directories that included sda, sda1, sda2, etc., tty10, tty11, tty12, etc., cdrom, cdrw, and a bunch of other things.  Certainly not the contents of my SD card or USB drive.

That should be the content of /dev.

Can you do the following commands, and give me the output of the entire terminal session?

```

ls /dev
sudo mkdir /media/usbdisk
sudo mount /dev/sdc1 /mnt/usbdisk
ls /media/usbdisk

```

---

### Post by Crimson_Tider on 2012-01-24
> **sanderd17 said:**
> That should be the content of /dev.

Can you do the following commands, and give me the output of the entire terminal session?

```

ls /dev
sudo mkdir /media/usbdisk
sudo mount /dev/sdc1 /mnt/usbdisk
ls /media/usbdisk

```

I'm in a hurry to get to work, so I don't have enough time to post everything, but that finally gave me the contents of my USB drive.  I may be able to handle it from here, because now I can reinstall my video driver.

---

### Post by sanderd17 on 2012-01-24
Ok, great to hear that.

Sorry it took so long, but it's just like we missed each other post after post.

---

### Post by Crimson_Tider on 2012-01-26
Well, I was wrong; I'm not able to reinstall the video driver yet.  After I uninstalled the old driver, I tried to install the new one.  It told me the new one was an x86, whereas I have the 64-bit Oneiric installed.  So that file was one I had downloaded a couple of months ago and it is the wrong one.  So I switched over to my Windows machine and downloaded the 64-bit driver to both my USB drive and my SD card.  When I tried to mount each of those on the Ubuntu computer, I got an error saying that I needed to specify the filesystem type.  I did the mount command again with the filesystem type, msdos, and it told me that I have a bad superblock on both drives.  I am quite certain this is not true because the USB drive is totally new.  Someone palease help me fix this drive issue, and I really think I can take it from there.

---

### Post by Crimson_Tider on 2012-01-26
I just thought of something.  Is there any way to download the driver from the NVIDIA website using the console commands?  I've never done that before, and I don't know how.

---

### Post by nipunshakya on 2012-01-27
> **Crimson_Tider said:**
> I just thought of something.  Is there any way to download the driver from the NVIDIA website using the console commands?  I've never done that before, and I don't know how.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368)
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

Check those and see if any one could help you out...Goodluck.

Regards,WinuxUser

---

### Post by sanderd17 on 2012-01-27
> **Crimson_Tider said:**
> I just thought of something.  Is there any way to download the driver from the NVIDIA website using the console commands?  I've never done that before, and I don't know how.

you can download a file with wget

---

### Post by Crimson_Tider on 2012-01-27
> **sanderd17 said:**
> you can download a file with wget

I tried wget and finally--something worked the way it should! [-o<

The real source of most of my trouble in this was the continued failure of my USB drive and SD card. I may have to start another thread to find the problem with those if I can't find some good advice elsewhere in the forums.

Thanks guys!

---

