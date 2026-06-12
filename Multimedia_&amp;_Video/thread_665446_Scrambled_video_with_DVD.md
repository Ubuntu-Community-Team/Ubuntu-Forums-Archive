---
title: "Scrambled video with DVD"
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by ksujason on 2008-01-12
When I play anything from a DVD, my video is scrambled. It does not matter if it is off of an encrypted or non encrypted DVD.
I am able to play video from any flash sites without any problems.

I have a video card ordered, but in the mean time I am using just the VGA from my motherboard. (MSI K9MM-V)
I have my 17 inch LCD set up with resolution of 1280 X 1024 at 75Hz.

Any suggestions on settings that I perhaps can check would be appreciated.
__________________

---

### Post by rune0077 on 2008-01-12
What exactly does scrambled mean? Try enabling deinterlacing.

---

### Post by Scorpuk on 2008-01-12
I think what is happening is thet the driver you have installed for your graphics card, probably vesa, cant cope with the video stream and it looks blocky and almost like a negative?

Having a hunt around I think you have the following graphics card: VIA® K8M800 Chipset 

You can find a link to some drivers for via products here: [http://www.viaarena.com/default.aspx?PageID=2](http://www.viaarena.com/default.aspx?PageID=2) , BUT no ubuntu driver for this particular chipset :(

Have a look around for K8M800/K8N800 UniChrome Pro integrated graphics, it may help. It may not :( :(

---

### Post by ksujason on 2008-01-12
I tried taking a screenshot of the scrambled video, but when you view the .png afterwords it is not scrambled.

How do you enable the deinterlacing?

Thanks for your help everyone.

---

### Post by rune0077 on 2008-01-12
If you're using Totem, it's in the View menu. Just check the box. Normal DVD's should be able to play fine without it, though, but if the DVD's are burned then this might fix it.

---

### Post by ksujason on 2008-01-12
I tried the deinterlaced selection on the totem player, and it did not make a difference. Here is a screen shot of what it looks like.

---

### Post by Giannis68 on 2008-01-12
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
sudo /usr/share/doc/libdvdread3/install-css.sh
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#head-780db298b62beea3e785ce27b68ec2f52d443515](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#head-780db298b62beea3e785ce27b68ec2f52d443515)

---

