---
title: "&quot;Unable To Mount iPod Touch DBus error......&quot;"
date: 2011-05-28
forum: Multimedia Software
---

### Post by hexxd on 2011-05-28
I am trying to sync my 2g iPod Touch with my Banshee Music Player, running on Ubuntu Linux 11.04 (although this problem happened in 10.10 as well). When I plug the sync cord with the iPod on one end into the USB drive on my CPU (Dell Inspiron 15r (N5010)), and this message appears "Unable To Mount iPod Touch DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)" an image is attached.

Why is this happening?

---

### Post by robbiemacg on 2011-05-29
I'm experiencing the same issue, despite having libimobiledevice2, etc. installed.
I'm actually unable to mount using ifuse either, though I can see an Apple device when I run **lsusb**.

---

### Post by hughes532001 on 2011-06-07
Gentlemen
I was haveing the same problem with one of my machines.  I had done a re-install/upgrade leaving my "/home" intact.  I have just done a complete clean installation and my Ipod touch mounts and works fine now. So it seams the problem is likely to be in the configuration files in "/home" but I have not found out if that's true.

So if you still have the problem one solution is to back up all your personal files from "/home" and do a clean install and then restore your personal documents.

I'm sure there is a more sophisticated way of solving the issue but that way worked for me.

Good Luck

Trevor

---

### Post by robbiemacg on 2011-06-07
I'm grateful for [hughes532001]("http://ubuntuforums.org/member.php?u=972290")'s contribution, but I'm after a scientific solution. This is a little, "have you tried turning it off, and again?" 
To share a bit more information. I'm working on my partner's machine, which is running a fresh install of 11.04. She has all extras and appropriate libraries installed correctly... also happens to have been given an ipod touch running iOS 4.2.2. It's not playing nice.

---

### Post by smallblackanimal on 2011-06-23
[http://xmemory.tompium.com/2011/04/iphone-does-not-mount-after-ios421-or.html](http://xmemory.tompium.com/2011/04/iphone-does-not-mount-after-ios421-or.html)


werx for me

---

### Post by robbiemacg on 2011-06-28
Oh Snap! I'm nominating [smallblackanimal]("http://ubuntuforums.org/member.php?u=1224313") for HERO SQUAD!

As well as installing **libimobiledevice2** I had to also install **libimobiledevice-utils**.
I plugged in my partner's iPod touch got the infamous error message, ran the command  **idevicepair unpair** via CLI... unplugged the device, plugged it back in, and there it was in Banshee, no problem transferring songs, etc.

KABOOM!

---

### Post by robbiemacg on 2011-06-29
Have you tried this method, [hexxd]("http://ubuntuforums.org/member.php?u=1302473")? Made any progress on your own issue?
If it were up to me, I'd be marking this one **[Solved]**, but I'm curious to know how things are lookign on your end. Now that I'm all good I want to help you out if possible.

R.

---

### Post by djsuibhne on 2011-08-03
I was having the same problem.  Now I'm not.  I also would mark this one SOLVED.  :D
Many thanks from an Ubuntu noob.

---

### Post by robbiemacg on 2011-08-03
That's rad. Great job, [djsuibhne]("http://ubuntuforums.org/member.php?u=1374401")! 
It's pretty exciting when you can start solving your own problems with the help of the forum and your Linux-loving buds. Stick around, and get the most out of your distro by joining in discussions and posting questions.

R.

---

