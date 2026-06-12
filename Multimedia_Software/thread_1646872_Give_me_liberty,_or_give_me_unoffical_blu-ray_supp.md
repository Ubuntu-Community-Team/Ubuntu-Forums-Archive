---
title: "Give me liberty, or give me unoffical blu-ray support for Ubuntu"
date: 2010-12-16
forum: Multimedia Software
---

### Post by boyevil on 2010-12-16
Just so you know, I did not create this fix, I am only sharing it with you.
This is what worked for me:

HowTo: Use lxbdplayer – the Open Source Blu-Ray Disc player for Linux
Posted on Monday, June 21, 2010 in Tutorials

Yes, you read that right – there is finally an Open Source Blu-Ray Disc player GUI for Linux, albeit unofficial and certainly very grey in legality depending on which country you are in.

lxbdplayer is the collaborative effort of four French Engineering students. What they have written is basically a frontend that combines the apps DumpHD and AACSKeys which I have used in previous Blu-Ray articles into one easy to use GUI. Decrypted BD streams are then piped into MPlayer for playback.

The end result is that you can now watch your BD movies almost as simply as a regular video player without the need to go through the process of ripping them into an MKV file first, or chewing up loads of drive space.

Now before you get all excited, this is a work in progress and you are ultimately limited to the decryption keys that have been discovered so far. You have no better ability to watch BD titles than you have with doing it all manually with DumpHD and AACSKeys. In fact, lxbdplayer already falls over in one area (for now), and that is it has no ability to process BD+ protected discs. Attempting to watch such movies will show a partially or fully corrupted video stream.

I tried using lxbdplayer with several of my BD titles under Ubuntu 10.04, and found that it played all my older titles pretty much perfectly. It’s only newer titles, especially those featuring BD+ protection that are problematic.

In short, this tool will only let you play older BD titles easily, but no doubt as DumpHD and AACSKeys progress in development, we will see those improvements filter down to lxbdplayer. I should also point out that lxbdplayer does not actually play the disc as such – it pulls out the titles available on the disc and allows you to play them by choosing them from a menu. It will not actually allow you to play the menu interfaces provided on the disc.

Your BD optical drive will also need to have been hacked with custom firmware to ignore the Player certificate, or use an imported BD drive that already ignores the Player certificates, or AACSKeys will not be able to retrieve the decryption key to decrypt the disc with.

Anyway, to use lxbdplayer, you will need to download the following:

    * The lxbdplayer itself. This package is a .deb for Ubuntu and Debian:
[http://sourceforge.net/projects/lxbdplayer/files/ubuntu_deb/lxbdplayer_0.2.1_all.deb](http://sourceforge.net/projects/lxbdplayer/files/ubuntu_deb/lxbdplayer_0.2.1_all.deb)
    * The AACSKeys plugin for lxbdplayer:
[http://www.mediafire.com/?d1n3zyyhz2h](http://www.mediafire.com/?d1n3zyyhz2h)
    * The MakeMKV package this is the 64-bit version:
[http://www.mediafire.com/?rnjoym0q1q4](http://www.mediafire.com/?rnjoym0q1q4)
 To get the 32-bit version, click here:
[http://www.mediafire.com/?mdimv3yobwo](http://www.mediafire.com/?mdimv3yobwo)
    * The ShowKeys library, again, this is the 64-bit version:
[http://www.mediafire.com/?yz2yj3it3il](http://www.mediafire.com/?yz2yj3it3il)
 To get the 32-bit version, click here:
[http://www.mediafire.com/?5ynetmrww21](http://www.mediafire.com/?5ynetmrww21)

   1. Install the packages by either double-clicking on them and let the GDebi installer install them, or use a terminal as follows:

      $ sudo dpkg -i lxbdplayer_0.2.1_all.deb lxbdaacs_0.2.1_all.deb makemkv_1.5.5b_amd64.deb libshowkeys_v1.5.5_amd64.deb

   2. A couple of dependencies will need to be downloaded, but otherwise the installation is small and quick.
      .
   3. Once the install is complete, import the decryption keys needed by typing in the following command (you do not need to use sudo here):

      $ bdkey-install

   4. Now you are ready to rock and/or roll.
      .
   5. Insert your BD movie disc into your BD drive. Within seconds you should be prompted by Gnome about what to do with the disc, and you will notice that there is a new default action for BD discs to launch lxbdplayer. Go ahead and allow lxbdplayer to launch, or alternatively launch it manually from Applications->Sound & Video->lxBDPlayer. If you manually launch, you need to tell the player where your BD title is mounted. Under Ubuntu Lucid, this will be under the /media directory.
      .
   6. Once your BD disc is located, lxbdplayer will process the disc for a short while before presenting you with a chapter list. To play a title, simply choose it from the list and hit the Play button. Almost right away you will see the video appear on your screen.

The player showing the video itself is simply MPlayer, and all its standard controls apply here.

Pat yourself on the back – and enjoy your movies. :)

---

### Post by rubylaser on 2010-12-16
This is interesting, but I'll just stick with MakeMKV for ripping and streaming all of my Bluray discs.

---

### Post by worldunix on 2012-07-24
Hello Everyone!
Has anyone figured this out yet?
I keep getting the NO AACS Plugin Found.

I have downloaded the keys but can not get it to run or install.

Showkeys install didn't work or i just didn't do it correct.
I can open the lxbdplayer ok but the AACS Plugin is an error.

I would love to just buy a blueray player for linux 
or a complete package for the Burning and movie player.

Does anyone know where we can buy this???

---

### Post by andrew.46 on 2012-07-24
> **worldunix said:**
> I would love to just buy a blueray player for linux 

Both MPlayer and vlc can now play bluray disks, and for those with BD+ encryption makemkv will stream the movie for either MPlayer or vlc...

---

### Post by wildmanne39 on 2012-07-24
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title. 
Thanks

---

