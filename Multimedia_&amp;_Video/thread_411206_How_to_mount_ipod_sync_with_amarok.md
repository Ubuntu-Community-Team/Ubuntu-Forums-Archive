---
title: "How to mount ipod: sync with amarok"
date: 2007-04-16
forum: Multimedia &amp; Video
---

### Post by HgBoy on 2007-04-16
I have an ipod mini, and my computer brings up an icon when I plug it in. I cant get amarok to recognize it. It almost seems as if the computer sees it as just a removable drive,not a music player. My ipod has nothing on it, I just want to be able to put music back on it. (amarok prefferred to gtkpod)

---

### Post by panty31772 on 2007-04-16
Amarok

    * Homepage: [http://amarok.kde.org/](http://amarok.kde.org/)
    * Version: 1.4.4 (10/30/2006)
    * Platform: GNU/Linux, Unix
    * License: GNU GPL



> Amarok is a GNU/Linux audio player. While developed initially for KDE, it’s currently desktop independent. One of its advantages is support for many audio devices, including iPod, iRiver, etc. Upon the first run, you’re given the opportunity to set up your library. Unfortunately, out of the box on Ubuntu 6.10, the iPod wasn’t detected, but a quick configuration change made all the difference: Settings&#8594;Configure Amarok&#8594;Media Device&#8594;Add Device&#8594;Plugin (Apple iPod), name (iPod), and mount point (/media/ipod).

One of [Amarok’s] advantages is support for many audio devices, including iPod, iRiver...

Copying music from the iPod is as simple as right-clicking and selecting Manage Files&#8594;Copy Track to Collection. As it adds files to Amarok’s library, the file is neatly named and placed in an appropriate folder (you’re given the option of which folder naming scheme you’d like). Copying to the iPod from your collection is similarly easy: right-click, Transfer to Media Device, select the Media Device and click Transfer. Amarok automatically checks for duplicate tracks, which is nice. The album cover function works quite nicely, fetching the image from Amazon or another external source. Playlists also work quite well.


Hope this might help you a bit !!

---

### Post by HgBoy on 2007-04-16
I have been using amarok for a while now. The problem is, amarok can't recognize my ipod. I can't connect to it for some reason.I have tried creating /mnt/ipod, but it still doesnt seem to work. Is there any way to reformat my ipod to use this directory, or just find which location my ipod is currently using?

---

### Post by sujith_m82 on 2007-04-17
After plugging in your ipod you can use "mount" command to find out the mount point.
For Example, in my system it's like this :

sujith@sujith-lnx:~$ mount
/dev/sdb2 on /media/SUJITH type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)

sujith@sujith-lnx:~$ dmesg | grep -i ipod
[ 2175.064000] scsi 2:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0

sujith@sujith-lnx:~$ sudo fdisk -l
Disk /dev/sdb: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          10       80293+   0  Empty
/dev/sdb2              11        3648    29222235    b  W95 FAT32

So, my ipod has been mounted to /media/SUJITH.
You will have a similar mount point which must be configured in Amarok.
In Configure Amarok->Media Devices->Add device, enter the details and you are good to go.

Hope this helps,
Sujith.

---

### Post by HgBoy on 2007-04-17
Worked like a charm. Thanks for all your help.

---

### Post by mceven on 2007-06-05
Can anyone explain the above directions?  It says "enter the details and you're good to go" -- I can't figure out what details I'm supposed to enter.  I've got Amarok up and running, Ubuntu recognizes my ipod without a problem, but when I try to connect to my media device in Amarok, it brings up the dialog box asking for mount and eject instructions.  I tried entering "mount /media/ipod" and "eject /media/ipod" in those fields but Amarok still doesn't recognize my device.  

Thanks in advance for your help.  Provided I can connect to my ipod, Amarok is a great program!  I like it better than itunes already.

---

### Post by hkahwaji on 2007-06-05
I do not have amarok installed since I use gtkpod instead and it works well with Ubuntu-Gnome. However, you might want to explore how to use the mount command. Open a terminal and type man mount. You can use with -t option.

Also, if you go to Places -> Computer: Does your IPOD show up there?

On the other hand, if you are running Ubuntu, try installing gtkpod and see if that recognizes your IPOD.

To install gtkpod, run the following command sudo apt-get install gtkpod

---

### Post by mceven on 2007-06-05
My ipod shows up in places -> computer

gtkpod doesn't recognize my ipod.

I'll do some investigation with the mount command.

---

### Post by mceven on 2007-06-06
I still can't configure Amarok to work with my ipod.  I read the material on the "mount" command by using "man mount" but it didn't seem to make things clearer.  I tried typing "mount -t /media/<ipod name>" into the dialog box but Amarok still doesn't allow me to connect to my device.  Can someone spell out what I have to do here?  I'm guessing it's just a matter of typing the right command into the dialog box but I can't figure out what that would be.

Thanks in advance.

---

### Post by L1vingd3ad on 2007-06-06
Don't think you need to fiddle with that dialog box. Instead try going to "settings" on the top, "configure amarok", "media devices". You should be able to see your ipod there.

---

### Post by cleopete on 2007-06-08
> **L1vingd3ad said:**
> Don't think you need to fiddle with that dialog box. Instead try going to "settings" on the top, "configure amarok", "media devices". You should be able to see your ipod there.

Thanks, that did the trick for me.  Ubuntu continues to make me giddy.

---

### Post by Kreat on 2007-08-28
Hey this seems to have worked well for be except that now I run into the problem, when i click connect so the ipod will connect to amarok I get this message:
> Media Device: could not find iTunesDB on device mounted at /media/DAN'S IPOD. Should I try to initialize your iPod? 
 I click initialize and get these two erros:
> Media device: failed to write iPod database
> Media Device: Failed to initialize iPod mounted at /media/DAN'S IPOD

any idea why this could be happening?

---

### Post by Kreat on 2007-08-28
I decided to check to see if my songs were still on my ipod and for some reason when i connected it the first time to the linux machine it deleted all my songs, so after i did a restore on windows it worked 100%!

---

### Post by Orfeus on 2007-08-31
Amarock cannot find my ipod anywhere.  What am i suppose to do?

---

### Post by Yfrwlf on 2008-01-10
I don't know if this will help any of you, but the way I got mine working was pretty simple.  First, you have to format the ipod.  The fastest way to do this is through iTunes.  Unfortunately, Apple and Microsoft haven't blessed (or cursed?) Linux users with this piece of proprietary software. ;)  The way I did it was by plugging the ipod into a Windows computer with iTunes on it, and letting it format the device.  I do not know if there would be any problems with formatting it to a Mac format, but the way I did it was with Windows.  Next, plug in the device into your Linux computer, and it should show up on your desktop.  Next, go to Amarok > Settings > Configure Amarok > Media Devices, and you should see it there in the list of media devices.  If you need help figuring out which one is your music player, you can click on "details".  Then, choose your device from the plugin list.  There is one for Apple iPod Media Device for iPods.  Then, click apply or just OK, and your music player should now show up under the Devices tab in the side panel in the main window.

Hope this helps someone. :)

---

