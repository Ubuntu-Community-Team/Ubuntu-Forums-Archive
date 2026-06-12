---
title: "Connecting to my unRaid box from Ubuntu"
date: 2011-08-26
forum: Networking &amp; Wireless
---

### Post by MrLeek on 2011-08-26
Still quite a newbie so be gentle!

I've solved some of the growing pains from making the move across to Ubuntu (getting my Lexmark printer to work was especially pleasing!) but I've ground to a halt on this one.

In windows-speak I want to map a network drive to one of the share areas on my unRaid box. I've set the box to have a fixed IP address, but my Google skills are struggling - I've found a few possible guides on what to do, but I don't understand what's going on well enough.

I think the end result is a mount point for each of the share areas (so one for Movies, one for Documents, etc.). I also think that the following guides are semi-close to what I'm looking for, but I don't know if that's true...and I can't say I totally understand what's going on. Rather than run a series of sudo commands that I barely understand it's better to stop and ask for help.

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

So any advice, tips, step-by-step guides or just words of encouragement welcomed!

---

### Post by e79 on 2011-08-26
So if I understand correctly, you want to mount share from your UnRAID box in your Ubuntu installation. 

Firstly, Linux(Ubuntu) does not have the concept of 'mapped drives with letters' as Windows has, but rather bookmarks in Nautilus that would achieve the same.

In order to do so, the easiest way would be to oen Nautilus (i.e : your home folder), and then go to the top menu called : 'File' --> 'Connect to Server'  and enter your information as shown on the screenshot (obviously replacing with your own values) and make sure to check the 'Add Bookmark' and give it a name.

Hope I understood correctly and that helps.

---

### Post by MrLeek on 2011-08-26
That worked just fine! Had to tweak it slightly as putting too much information into the form confuses things (ended up with a weird smb connection error), but just specifying the IP address of the server enabled it to connect to the box. 

Sure it could see everything (unRaid allows "shares" to organise your data across multiple drives), so I could mount the USB stick that unRaid runs off...but I could also mount the Movies share as well as the others. Create your mounts and away you go!

Cheers e79! :KS

---

### Post by e79 on 2011-08-26
I'm glad we could help you solve your issue !

Best Regards ;)

---

### Post by MrLeek on 2011-08-27
Some quick footnotes on this (in case someone is trying to solve the same problem and finds this via Google):

The above enables you to link to the network drive, but it doesn't seem to be a permanent mount (remember I'm still a newbie at this!). The easiest guide to follow I've found is linked below, but here's my understanding of it:

[http://www.automaticable.com/2008-01-18/how-to-mount-a-network-drive-in-ubuntu/](http://www.automaticable.com/2008-01-18/how-to-mount-a-network-drive-in-ubuntu/)

- make a directory where the contents of your network drive is going to be mapped to (or mounted).
- Edit fstab in order for your system to find the network drive. I've read that editing fstab is a good way to cause major issues so make a copy before you start!
- The mount line (that you'll put in fstab) takes a little bit of translation if you're new. Mine works as the following:

```
//192.168.1.78/Movies  /media/Tower/Movies smbfs guest 0 0
```That's the static IP address of the unRaid box and the share name in question. Then it's the directory that you made earlier (where it get's mounted) and the last bit are options (which I'm learning about next!). 

I've not tried to write to the network drive yet, but I can read from it just fine so I'm not expecting any problems. 

Hope this helps someone!

---

