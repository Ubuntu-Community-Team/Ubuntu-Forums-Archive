---
title: "Help installing Ubuntu on laptop - graphics driver problem"
date: 2007-07-14
forum: Multimedia &amp; Video
---

### Post by tokker73 on 2007-07-14
I 've just bought myself a brand new Acer Travelmate 4720 with Windows Vista already on it. I created 80 Gb of free space for the Ubuntu partition. I did that using the alternate install cd because the Live CD of Feisty Fawn didn't work . Everything seemed to work fine until I had to reboot to take my first look at my installed system.

Now it gives me the message: 
"Failed to start the X-server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

If I say yes I get a bunch of computer gibberish.
If I say no it says that "the X server is now disabled. Restart GDM when it is configured correctly"

I found the command line to configure it (sudo dpkg-reconfigure xserver-xorg) but then you get to choose your interface. Intel is not even listed! I've chosen some other things (vesa,...) but then they start asking all kinds of configuration question of which I don't have a clue.

I've been surfing the net for 3 hours now and it hasn't helped me at all.

I've seen a post about the graphics card (Intel Graphics Media Accelerator X3100) that is also in my PC but this thread is completely useless to me as I can't access my system (except for the command line interface) and I am a rookie.

So can somebody please explain to me step by step what I have to do to make the darn thing work before I give up on Ubuntu. I had Ubuntu installed on my old laptop 3 months ago and that already cost me blood sweat and tears (not really but nevertheless...). Although I liked what I 've seen once it started working, I am very close to agreeing with all the critics that Ubuntu is only for geeks and not ready for everyday simple use...

Thanks in advance,Tom

---

### Post by Subfusc on 2007-07-14
can you get it to connect to the internett?
"xserver-xorg-video-intel" is the name of the driver deb for intell chipsets, and according to wikipedia, yours is supported.

---

### Post by tokker73 on 2007-07-14
As I said in my original post, i have a command line but no access to the desktop. It might be possible but I don't see how i could access the internet through the command line and then install it as well...

---

### Post by JoSch on 2007-07-16
You can download nearly anything with wget```
wget http://my.url.com/myfile
```
For downloading the attachments of ubuntuforums.org you need to be logged in.
With cookie managment even this is possible with wget but it is more complicated.
So for the ease of use just try a command line browser```
sudo apt-get install lynx
lynx
```With that you can browse to ubuntuforums, log into your account and download the attachment.
You can then install the downloaded file with dpkg like```
dpgk -i mypackage.deb
```

---

### Post by cdrigby on 2007-08-29
> **tokker73 said:**
> I 've just bought myself a brand new Acer Travelmate 4720 with Windows Vista already on it. I created 80 Gb of free space for the Ubuntu partition. I did that using the alternate install cd because the Live CD of Feisty Fawn didn't work . Everything seemed to work fine until I had to reboot to take my first look at my installed system.

Now it gives me the message: 
"Failed to start the X-server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"


Hello Tom,

You beat me to purchasing just this model by a couple of weeks, apparently. I found your post while I was searching for a way to get the sound working. I have succeeded in getting  the Intel GMA X3100 graphics card working as well as everything else I care about EXCEPT sound, so I am replying to let you know what I did.

First I found this thread in the forums discussing the backport of the X3100 driver from the next release of Ubuntu, 7.10 Gutsy Gibbon: 

[http://ubuntuforums.org/showthread.php?t=506744&highlight=X3100]("http://ubuntuforums.org/showthread.php?t=506744&highlight=X3100")

Another option (and the one I opted for) was to install Gutsy Gibbon Tribe 4 itself. This mostly worked, including the eye-candified desktop. Access to my DVD+/-RW arrived with a kernel update just under a week ago. So, if you want to go this route, you might as well grab Tribe 5 of the brachiating great ape:

[http://www.ubuntu.com/testing/tribe5]("http://www.ubuntu.com/testing/tribe5")

I'll report back to this thread if/when I get sound working.

Regards,
CDR

---

