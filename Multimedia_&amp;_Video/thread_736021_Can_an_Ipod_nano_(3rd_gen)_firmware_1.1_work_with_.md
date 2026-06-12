---
title: "Can an Ipod nano (3rd gen) firmware 1.1 work with ubuntu?"
date: 2008-03-26
forum: Multimedia &amp; Video
---

### Post by darth.k on 2008-03-26
Is this possible?  I've tried both Amarok and Gtkpod without any luck.  They seem to transfer the music to the ipod and I can play from it when docked but the ipod itself can't recoqnise any files.

After reading a bit I think it may be something to do with the firmware version (1.1) although I could be completely wrong.

Thanks for any help.

---

### Post by darth.k on 2008-03-26
bump.  ok after a bit of work I got the ipod finally to work, but this caused another problem!

Now Amarok won't auto detect the ipod.  Instead I have to go to settings add the device manually everytime.  However not only is this a nuisance but I have to give the ipod a new name every time because its says I cannot specify two devices with the same name??  

Can someone please help me here, I spent the guts of two days on this.

---

### Post by Horomancer on 2008-03-27
I'm also having a devil of a time with my new iPod nano. I'm trying the latest version of gtkpod in the add/remove program library and it can mount and 'write' to the nano, but the nano is blank after i eject it.
What did you do to your Amarok to allow it to write to the ipod?

---

### Post by drewsimon on 2008-04-04
I can't get my brand new ipod nano video to work either. I even upgraded to Heron to see if that made any difference. 

Ubuntu automounts the drive and I can transfer songs to it. I can even read those song from the ipod whenever it's docked. But I can't read those songs from the ipod nano when it's not connected to the computer. It just keeps saying that there are no songs on it.

Any help?

---

### Post by numberonealcove on 2008-04-06
I was able to get my 3G nano (firmware 1.1) to write successfully using Amarok 1.4.8 after installing  libgpod3.  But now like Dark.K  I have to manually add the device every time; also, when I eject the iPod within Amarok, my DVD drive opens.

---

### Post by drazgo on 2008-04-07
how can you manage to get gtkpod or amarok use libgpod3 instead of libgpod2? cuz every time i want to uninstall libgpod2, it says it has to uninstall gtkpod and amarok too :s should i wait till hardy's out?

---

### Post by drazgo on 2008-04-08
bump...

---

### Post by numberonealcove on 2008-04-08
Just re-install gtkpod and amarok once libgpod2 is un-installed.  You don't need to wait for hardy; but you will need to install some programs from the hardy repository.  This tutorial worked for me: [http://ubuntuforums.org/showthread.php?t=658523&highlight=ipod+nano](http://ubuntuforums.org/showthread.php?t=658523&highlight=ipod+nano)

Once again, after this fix I still need to manually mount the iPod within Amarok; but that's not a big deal to me.  It's better than using a Windows box or trying to get iTunes to work in Wine.

---

### Post by oiler920 on 2008-04-09
:lolflag:

**_You do not need to install Hardy or use its packages._** You need to use libgpod 0.6.0. My iPod nano 3rd gen has firmware 1.1 and works fine. Just follow this guide: [http://maketecheasier.com/how-to-sync-amarok-with-ipod-classic-3rd-generation-ipod-nano/2008/03/10]("http://maketecheasier.com/how-to-sync-amarok-with-ipod-classic-3rd-generation-ipod-nano/2008/03/10")

You don't need to install Amarok, just follow the set-up instructions and stop when you get to the Configuring Amarok part, then launch gtkpod (install the "gtkpod-aac" package) to set the iPod model. :)

---

