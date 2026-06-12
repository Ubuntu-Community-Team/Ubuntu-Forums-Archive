---
title: "Problems w/ 9.04 and Sansa Clip"
date: 2009-05-06
forum: Multimedia Software
---

### Post by mirutsa on 2009-05-06
I recently connected my Sansa Clip to Ubuntu, in hopes of using that machine to work with the mp3 player.  I should note that the firmware for the Clip was updated to v02.02.32a.  I set the USB mode to MSC, anticipating that Auto-detect might cause problems.

When I plug the Clip into the USB, it seems to automount normally.  I can see all the root directory files and folders, and it even shows an icon in RhythmBox.  The problem is that the music files aren't there.  It reads in both the file browser and RhythmBox as having zero files.  I don't currently have any mp3s loaded onto my Linux box, so I haven't experimented with it from that angle.

Is there some way I can get Ubuntu to recognize the mp3s I loaded from Windows?

Update:
Experimented with loading an mp3 from Ubuntu itself (flash-drive'd it from another machine).  That single mp3 works perfectly, so it's just not picking up on the files I loaded from Windows.  Question remains.

---

### Post by motang on 2009-05-11
I have come to the conclusion that if you files loaded into your Snasa player (I have both the Clip and the Fuze) from Windows you can't see it in Ubuntu and vice versa. I think Ubuntu uses MTP mode and Windows uses MSC mode and they aren't compatable.

---

### Post by mirutsa on 2009-05-13
hmm... maybe if i force windows to use msc, then it'll start to work.  thanks for the reply; if it works, i'll post the results.

---

### Post by RamonB on 2009-05-17
mirutsa, I have a Sansa Fuze and I had the same problem. In my case, I started using it at Windows and the same occurred to me.

First at all, I copied all the Sansa files (including the demo files) to Windows and deleted all of them on Sansa. Then, I disconnected the player from the USB and changed USB Mode to **MSC**. Next, I reconnected it to Windows and transfered all the files I had deleted.

Ubuntu recognized all files that I recorded in Windows. I transfered more files to the player under Ubuntu and Windows recognized all of them.

This issue isn't a Ubuntu nor a Windows problem. I think that in most of players, files recorded in MTP mode aren't read when you're using MSC and vice-versa.

---

### Post by icheyne on 2009-06-20
RamonB is right.

I wrote some Sansa Clip instructions [here]("https://help.ubuntu.com/community/SansaClip").

---

### Post by Michael Schmidt on 2009-07-02
You may need to do a Format on the Sansa Clip before changing from MPT to MSC.  I did and everything works fine.  Of course, you will lose all the Clip files unless you back them up somewhere first.

---

### Post by SteveNorman on 2009-07-11
what and how do you format this to? just got one, wont mount, did icheyne's instructions for getting rythembox to work, but as I have just bought this I would like someone to do a quick tutorial for first time sansa users. you cant add songs to it with rhythm box can you?

---

### Post by SteveNorman on 2009-07-11
figured it out, for an out of the box sansa clip this worked for me in jaunty.

1 charge overnight
2 remove from usb
3 on the sansa clip >menu>settings>format
4 on the sansa clip >menu>settings>usb>MSC
5 turn the sansa clip off
6 plug into usb (this will power it on, if you plug it in while turned on it locks up)
7 it should pop up on desktop in gnome
8 click on icon for it, 
9 go to music, drag files in, 
10 right click desktop icon>eject when done
11 unplug from usb after sansa logo flashes
12 wait for the sansa to update media
13 rock out

this thing works and sounds awesome once you figure it out.

---

### Post by Cuba71 on 2009-09-29
I haven't and probably won't try my Sansa Clip+ with Windows, the reason being that it works great with Jaunty 9.04.  
Contrary to what it's been said in this post, my Clip+ work great set to "Auto Detect", could be a different firmware?  I don't know

---

### Post by gkh73 on 2010-03-19
I just got my Clip yesterday, 9.04 initially asked me if I wanted to mount it in Rhythmbox, I said yes, then it never showed up.  I read some instructions here, and went into the Clip's settings menu and switched the usb option from "Auto" to MSC. It works now!  
Listening to music just fine!  :)

---

### Post by chc1006 on 2010-04-27
Thanks SteveNorman. Works like a charm indeeed in Karmic as well.

---

