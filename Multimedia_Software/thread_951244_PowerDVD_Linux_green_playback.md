---
title: "PowerDVD Linux green playback?"
date: 2008-10-17
forum: Multimedia Software
---

### Post by shizakapayou on 2008-10-17
I just bought PowerDVD for Hardy for my laptop.  The software downloaded and installed without a problem, but my DVD playback is dark and green.  I'm attaching an image to better show the problem - the screengrab is from Indiana Jones.

Laptop:
Gateway MX6030
Ubuntu 8.04.1 3-bit
Celeron-M 1.4Ghz
1 GB RAM
120GB HDD

This laptop played DVDs fine during it's Windows time, and playback itself in Ubuntu is smooth, just very bad looking.  I've tried VLC (it won't play a DVD), Totem (same green effect), and Mplayer (it plays but scrambles the image).  I have a flight tomorrow - hope someone has an idea tonight!

---

### Post by vginov on 2009-02-28
Hi..

Type this bellow commands 

1. **sudo apt-get update**

2. **sudo apt-get -y install gstrea***

3. [B]sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
[/B]

4. **sudo apt-get -y install xmms***

5. **sudo apt-get -y install ffmpeg***

6. **sudo apt-get -y gxine***

7. **sudo apt-get -y mplayer***

8. **sudo apt-get -y xvid***

9. **sudo apt-get -y libdvd***

To play all the DVD file open **Applications > Add/Remov**e.. and search for **DVD Movie**  **Check** all the software available and click on the **Apply Changes** Button.

Now you should be able to play all the files 
----------------------------------------------------------
more information visit 
[http://www.vginov.com](http://www.vginov.com)

---

