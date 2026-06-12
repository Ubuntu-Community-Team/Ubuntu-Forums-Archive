---
title: "x in endless loop"
date: 2010-02-04
forum: Multimedia Software
---

### Post by ulao on 2010-02-04
I just did an install and after loading X is close and start X again, in a loop?

So I dropped to another session and looked at xorg.conf, its set up for what looks like auto detection. ( Identifier "Default Screen" Monitor "Configured Monitor" )I tried to put in the refresh rate but do to the fact its not set up right X failed to load. I put the xorg.conf back and rebooted, not X tried to load then exists with
saw signal 11. Server aborting
ddxSigGiveUp: Closing log
ddxSigGiveUp: re-raising 11
connection to X server lost

I get this just after the desktop loads completely

Tried sudo dpkg-reconfigure xserver-xorg but I get no installed. I also have trouble getting the nic working so not net connection atm.

any ideas?

---

### Post by troyer81 on 2010-02-04
Do you have anything interesting (i.e. Error messages) in /var/log/Xorg.0.log?  I believe the line will start with (EE) if there is an error.  You can type "more /var/log/Xorg.0.log" to see what's in the file.  I believe that's where an X-server related error would show up. If there's nothing there, you can also run "dmesg" and look for error messages.  Hopefully that will pinpoint the issue a little closer.

Jon

---

### Post by ulao on 2010-02-05
I wish I had a way to post the logs ;(

Xorg.0.log does not contain (EE), but does have that ddxSigGveUp: closing log in it.

dmesg, shows a lot of info but thing that I can see about my card. it does however show my nic, and that I find interesting as its not creating the eth0 interface as well. Also this is a new install and I have 5 dmesg archive already? but  as the X session loops these files dont change.


Well I took out the ati, and put in in a nvidia after readon some info on that net about ati driver being all bugged in 9.10/ Wether or not the case its working ok now.

---

### Post by ulao on 2010-02-07
Ok I was able to get my network issues working, but I had to move to a board with an on-board-video. And now the problem is back? I have no idea what the video is, guessing ati, not sure..

So now that I have a net connection.. what log may give a hint? the Xorg has no EE's found but the one in the rem line of course ;)

Here is the current state of xorg.conf

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
#       HoriZSync       31-101
#       VertRefrech     60-160



EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

removing the files seem to get X to load ? Though I tried that? All working disregard.

---

