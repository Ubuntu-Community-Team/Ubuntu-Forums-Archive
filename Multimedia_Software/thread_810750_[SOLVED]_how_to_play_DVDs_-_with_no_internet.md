---
title: "[SOLVED] how to play DVDs - with no internet"
date: 2008-05-28
forum: Multimedia Software
---

### Post by savsav on 2008-05-28
I have Kubuntu - but NO internet connection

So I cannot turn to "apt get" to download the codecs, etc needed to view DVDs.

I connect to the internet thru my windows computer.

So how can I get DVD playback on my kubuntu computer?

---

### Post by sim-value on 2008-05-28
Just try to playback the DVD then look which packages are required and then download them from packages.ubuntu.com 

This files you can install just by clicking them

---

### Post by savsav on 2008-05-28
I am a newbie ... so I will need a bit of help.

When I try to play a DVD, it says it must download:


LibDVDCSS

Searching for LibDVDCSS at packages.ubuntu.com produces numerous results!

What -- exactly -- do I need to download for kubuntu 8.04

---

### Post by savsav on 2008-05-28
A little help, people!

---

### Post by IHATEDLINK on 2008-05-28
You **NEED** an internet connection to **DOWNLOAD** the codecs!
Try hooking up your PC to the phone line to get temporal internet access, download the codecs, install them and disconnect your PC.
**NOTE**: You won't be able to make phone calls or receive them while you are connected and the time that you are connected will be charged as a phone call.
Of you think that this post was useful remember to thanks me by clicking the little star button on the bottom-right of the post ;)

---

### Post by savsav on 2008-05-28
Your post was not helpful, IHATEDLINK 

I have an internet connection ... read the first post of this thread.

So, can someone help?

Or is it impossible to bring over the DVD codecs and libraries
to my kubuntu computer?

---

### Post by IHATEDLINK on 2008-05-29
I'm not familiar with Kubuntu apps, but I think the best way to go with it is by connecting your kubuntu computer to the internet, insert a dvd and let kubuntu ask you for downloading the appropriate codecs (that's the way it goes with Ubuntu). 
That's the only thing that I can think of, so, hope I helped. :)

---

### Post by mc4man on 2008-05-29
libdvdcss2 has no deps so you can grab it here - 10th from bottom will be good for 8.04 (27-Sep -2007)
[http://packages.medibuntu.org/pool/free/libd/libdvdcss/](http://packages.medibuntu.org/pool/free/libd/libdvdcss/) 
Try that and see. You may need some plugins for kaffeine (libxine-all-plugins) I'll fire up a kubuntu install and ck. if there needed for dvds and if add. depends
If you wanted another player like vlc you'll need all the addintional deps, some people have mentioned here - read thru carefully for method
[http://nonetdebs.unixpod.com/](http://nonetdebs.unixpod.com/)

---

### Post by cariboo on 2008-05-29
Make sure you have libdvdread3 installed then got to /usr/share/doc/libdvdread3 and run:

```
sudo ./install-css.sh
```

You can find it here:

 [http://mirror.arcticnetwork.ca/pub/ubuntu/packages/pool/main/libd/libdvdread/](http://mirror.arcticnetwork.ca/pub/ubuntu/packages/pool/main/libd/libdvdread/)

Pick the one for your distribution download it then transfer it to the other computer. Just double click on it and a program will open to install it, don't know what it is called in kde but in gnome it's called gebi.

You should really find a way to share your internet connection as the only way to do most of what most people want to do, is to install extra software.

Good luck

Jim

---

### Post by savsav on 2008-05-31
I solved my problem!

I can now watch DVDs perfectly.

In case I didn't make myself clear in my first post of this thread, this was my problem:

1) I had Kubuntu 8.04 on computer with NO internet.

2) I could not play DVDs

3) I could not download codecs and dependencies to play DVDs.

4) I have a second computer, windows machine, with internet.

My hero, forum user "nucleuskore", answered my problem here:

[http://ubuntuforums.org/showthread.php?t=795859](http://ubuntuforums.org/showthread.php?t=795859)

I downloaded from my windows machine the ISO image created by nucleuskore, burned a CD, and took that CD to my Kubuntu machine.

I then installed all the DVD codecs and more.

I am playing a DVD right now!

Thanks, nucleuskore!

---

### Post by the8thstar on 2008-05-31
First, go here: [http://packages.ubuntu.com/hardy/libs/libdvdread3]("http://packages.ubuntu.com/hardy/libs/libdvdread3")

For libdvdcss2, get it from: [http://packages.medibuntu.org/pool/free/libd/libdvdcss/]("http://packages.medibuntu.org/pool/free/libd/libdvdcss/")

You should be able to download what you need. Copy the files onto a USB key or a CD, reboot into Ubuntu and install the files.

---

### Post by disturbedite on 2008-05-31
> **the8thstar said:**
> First, go here: [http://packages.ubuntu.com/hardy/libs/libdvdread3](http://packages.ubuntu.com/hardy/libs/libdvdread3)

For libdvdcss2, get it from: [http://packages.medibuntu.org/pool/free/libd/libdvdcss/](http://packages.medibuntu.org/pool/free/libd/libdvdcss/)

You should be able to download what you need. Copy the files onto a USB key or a CD, reboot into Ubuntu and install the files.
yeah, much better/more convenient solution imo.  (particularly using a flash drive in conjunction with this method).

---

### Post by nig_nig_the_conqueror on 2008-05-31
I don't understand...are your Windows(connected) and Kubuntu(unconnected) computers not in the same house?  How many places do you keep your computers?  I suspect that connecting your Kubuntu pc to the internet might solve a few of your problems, but that's just me thinking outside the box again.

---

