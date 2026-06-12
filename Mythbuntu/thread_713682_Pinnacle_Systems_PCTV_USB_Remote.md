---
title: "Pinnacle Systems PCTV USB Remote"
date: 2008-03-03
forum: Mythbuntu
---

### Post by nasha on 2008-03-03
Hey guys,
Just bought a Pinnacle remote: [HTML]http://www.pinnaclesys.com/PublicSite/us/Products/Consumer+Products/PCTV+Tuners/PCTV+Vista+Companion/Pinnacle+Remote+Kit+for+Windows+Media+Center.htm[/HTML]
Anyone have any suggestions on how to set it up, cant seem to find any reffering to this model remote.

Another option is, i have a serial IR adaptor here. If someone is able to provide the lircd.conf for this remote, than i can just use that :)

This guide was the closest i came, but the link to the lircd.conf is dead :(
[HTML]http://www.mythtv.org/wiki/index.php/Ubuntu_lirc_install[/HTML]

Thanks in advance,
Nasha

---

### Post by foxbuntu on 2008-03-04
you will need to use irw and irrecord with an IR receiver that works with lirc and generate your own lircd.conf and .lircrc files if you are unable find find one.

---

### Post by terryva on 2008-03-09
I have my Pinnacle PCTV USB RC6 remote working with the generic MCE lirc.conf file (after patching lirc_mceusb2.c file) 

Most of the buttons work but some things are missing or wrong. I am hoping to find a conf file that some one has already done for this remote :)

I f I cant, i will make one and post it.

Cheers,

Terry

---

### Post by nasha on 2008-03-10
That would be great if you were able to get a working conf file :D

---

### Post by Castrato on 2008-04-28
Hey all - I'm using the latest mythbuntu 8.04 with a Pinnacle PCTV pro remote control.  It was hard to find a config, as most of you have encountered.  However, if you go to [http://lircconfig.commandir.com/]("http://lircconfig.commandir.com/") you will be able to make your own config with the simple web gui.  Below are the conf files I made for myself.  One goes in /etc/lirc/lircd.conf and the other goes in your home dir that contains your lircrc file (mine was in ~/.mythtv/lircrc).  Lircd.conf is the config for your controller; lircrc is the config for mythtv.  Good luck.


UPDATE 4/29/08: These were my steps in order:
1. Install hardy and configure remote (pinnacle pctv pro) during the install process then reboot
2. sudo apt-get install lirc lirc-modules-source module-assistant
3. sudo dpkg-reconfigure lirc-modules-source   (this gave me an error)
4. sudo nano /etc/lirc/hardware.conf  (change REMOTE_DRIVER="pinsys")
5. locate the lircrc files for mythtv and replace them with my file below or go to the website i mentioned and make your own
6. sudo nano /etc/lirc/lircd.conf and paste mine or go to the website and make your own.
7. sudo m-a update,prepare
   sudo rm /usr/src/lirc*deb
   sudo m-a clean lirc
   sudo m-a a-i -f lirc
   sudo depmod -a
8. sudo /etc/init.d/lirc restart

use irw to test.

should work now.

UPDATE 5/1/08:  Last update.  I reinstalled my mythbuntu system, followed my own steps, and it didn't work.  syslog was giving me an error about readlink() failed for /dev/lirc.  So I created a script in /etc/init.d/ called lirc_symlink_in_dev.  So it's full path would be /dev/init.d/lirc_symlink_in_dev.  In it, I simply typed:
#! /bin/sh
ln -s /dev/lircd /dev/lirc

saved it, then sudo chmod +x /etc/init.d/lirc_symlink_in_dev to make it executable.  Then, of course, I installed the sysv-rc-conf utility from apt-get to make the script start in the default runlevels (2-5).

Works like a champ again!

---

### Post by nasha on 2008-05-04
Castrato:
Appreciate your response, and posting of the configs. Im overseas in Europe, due home in a week, will attempt to give it a shot. One question... Im running Gutsy, will anything need to be altered?

---

### Post by Castrato on 2008-05-04
> **nasha said:**
> Castrato:
Appreciate your response, and posting of the configs. Im overseas in Europe, due home in a week, will attempt to give it a shot. One question... Im running Gutsy, will anything need to be altered?
nash - really glad it was helpful.  i know how frustrating it is to find documentation.

As for your version, I don't think anything needs to be altered.  make sure the paths to the files are the same.  the syntax probably hasn't changed.  make backups of your original files first (cp -p ./orig ./orig-backup), then run the locate command to see if they are, indeed, in the same location.  

Then if you want, you could run the diff command on the 2 files to see what the differences are between them.

If you try it and it doesn't work, you can always revert to your backups.

Good luck!

---

### Post by nasha on 2008-05-12
No such luck :(
Not sure what im doing wrong or right, but i doesnt want to play nice.
Not to mention i havent touched linux in a month, and everything seems to happen the long way!
Dont happen to have some spare time to ssh me and take a look? If you dont mind of course, really wouldnt mind getting a remote operational!

PM Sent

---

### Post by jmw86069 on 2008-06-08
I don't know where things stand, but the best I can tell the Pinnacle HDTV Pro USB stick using the "pinsys" REMOTE_DRIVER still doesn't recognize all the buttons.

I can't try it now, I haven't gone through the 100 random incantations required to get the v4l em28xx drivers to work on this week's Hardy kernel (I hope everyone involved recognizes my appreciation of their work, but the temporary slam for breaking many TV tuners and ffmpeg, sort of taking the fun out of MythTV.) So the remote isn't showing up in /proc/bus/input/devices for me anymore. But when it did... I remembered a day when...

I tried "irrecord" using "devinput" as the REMOTE_DRIVER instead of "pinsys". Look for the remote section in the file /proc/bus/input/devices and take the trailing number from the "event11" field (or event# or whatever) and substitute it for input11 below:
```
irrecord -H devinput -d /dev/input/input11
```

I went through the irrecord steps, and what I found [ymmv] was that it could record all the buttons! Very cool, huh? The "pinsys" driver cannot recognize the buttons yet, so maybe this can help someone.

However, I last got stumped [you know, during the last time the driver and kernel were functional together for 15 minutes] because the v4l drivers had hard-coded the IR (not using lirc) and I couldn't trace back where to turn it off.

For what it's worth, here are the codes I grabbed, in case it helps someone else:

```

      begin codes
          channel+                 0x0192
          channel-                 0x0193
          volume+                  0x0073
          volume-                  0x0072
          pinnacle                 0x001E
          mute                     0x0071
          fullscreen               0x0174
          t                        0x0014
          playpause                0x00CF
          rewind                   0x00A8
          fastforward              0x009F
          stop                     0x0080
          record                   0x00A7
          help                     0x0166
          power                    0x0074
          1                        0x0002
          2                        0x0003
          3                        0x0004
          4                        0x0005
          5                        0x0006
          6                        0x0007
          7                        0x0008
          8                        0x0009
          9                        0x000A
          0                        0x000B
      end codes
```

If I get the remote input to work again, I'll push ahead and post an updated how-to.

---

### Post by nasha on 2008-06-08
Thanks for the info, still dont have a working conf file. But i think thats the least of my problems. Getting the actual USB receiver to work is where my problems lie from memory (Been a while since i fiddled with this problem).

I'm using the PinSys PCTV Remote Kit, which i would only assume would be similar if not the same to the other PinSys remotes

---

### Post by Castrato on 2008-06-10
the down button on my pctv pro remote wasn't working today after i did some apt-get upgrades.  it seems Chan+Stop is now recognized as Chan-Stop.  After changing the + to a - and a quick reboot, all is well again.

nash - did you go to [http://lircconfig.commandir.com/](http://lircconfig.commandir.com/) to see if there is anything there that would help you?  sorry for the delay - i was in europe as well.  back home now.

---

### Post by nasha on 2008-06-10
Hi Castrato,
i have browsed that website, but its not the actual remote config that im having issues with. Its getting the USB IR reciever to work thats my issue

---

### Post by necochino on 2010-03-19
anyone got this thing to work?  I made a mistake and bought one without checking here.   Needless to say, I'm having the same issues.  The receiver does not work.  Sometimes will work for a few minutes, then lock the computer.  Often, is as if it did not exist at all.

---

