---
title: "Wireless Disapeared!!!"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by PerverseLeigh on 2009-11-21
[FONT=Comic Sans MS]OK. I'm new to Ubuntu but not computers. I'm not afraid of tech so if I can understand what I'm doing I can do it. 
My son likes downloading viruses so we got him Ubuntu for his Dell Inspiron 6400. After arguing with the Wireless for 12hrs I finally programed it to turn the wireless card on (no hardware toggle) and connect automatically. (YAY Forum!) So this morning when he points out that he can't get online I was TICKED! PLUS the place on the task bar, (near the clock,) where the little connection menu WAS is GONE.
I searched a LOT & found nothing helpful. could someone PLEASE tell me what's going on? We have Ubuntu and it says Gnome Desktop (??) but it also says Karmic Koala... I think it's out to make me miserable...
[/FONT]

---

### Post by tlois on 2009-11-21
Right click on the tool bar and try to add the NM icon back to it.  That happened to my stepdaughter too somehow.  When we added the icon back, there she was again.   It may have been Notification or something, but finding the correct icon was not obvious, so try that one.

see this too:

[http://ubuntuforums.org/showthread.php?t=1311790&highlight=network+manager+icon+disappeared](http://ubuntuforums.org/showthread.php?t=1311790&highlight=network+manager+icon+disappeared)

---

### Post by PerverseLeigh on 2009-11-21
That doesn't seem to apply in this instance =( I tried as you explained it & didn't see the connection menu in the list of things I can add to the panel

---

### Post by tlois on 2009-11-21
Did you follow this guy's instructions?  It is called Notification Area.

"Hello Everyone.

This morning, I booted up my laptop and tried to connect to the school's wireless when I noticed that the icon for Network Manager was missing from the toolbar. I checked to see that Network Manager was running and it was, the icon had just disappeared for some reason. After tinkering around with the panel a little bit, I discovered that if you remove the notification area on the panel (right click the three vertical dots and click "Remove From Panel") and then re-add it ( right click the panel, click "Add to Panel" and search for "Notification Area", then click it) the Network Manager icon will reappear, thus allowing you to connect to wireless networks.

Hope this works if you're having the same problem! "

I edited to add that link.

---

### Post by PerverseLeigh on 2009-11-21
Yes, thanks. I followed the directions; but no, this didn't help.

---

### Post by tlois on 2009-11-21
Well, that's all I got- sorry.

Post what wireless card you have and what you did to getting working initially and somebody will come along to help you.

---

### Post by PerverseLeigh on 2009-11-21
Thanks anyhow =)

it's a "Wireless WLAN MiniCard" in a Dell Inspiron 6400

Here's what I did to get it working in the 1st plc.:

First I installed the ndiswrapper & got the drivers from the Dell website. I followed the directions for the ndiswrapper & got the drivers installed properly.I ran the check & got a pos readout JUST to be sure. 
Then I noted that the device was CAPABLE of working but still not turning on. This computer was a gift & I don't use it, so you better be SURE I looked the entire thing up & down but found no hardware switch. I then noted, (with some under-breath cursing,) that the function key combo wasn't working either. So I went looking for instructions to turn it on using the command line (Terminal).
I used some of the instructions from threads 1002529, 1041523, 1284505 & 884215. Then I used some of the instructions from ubuntuforums.org/archive/index.php/t-1005000, t-332 & t-44861 after all of this the card turned on & I was able to configure it. After reboot it connected smoothly & was used happily for FB games for almost a week... now it won't connect AGAIN!

The little menu to connect is missing so I'm not sure what to do... although I may just walk through ALL of this AGAIN... but 1st I have to go to get some alcohol

---

### Post by williejones on 2009-11-21
Open a terminal and type

```
iwlist scan
```

See if any connections are being seen.

---

### Post by williejones on 2009-11-21
Another suggestion.  I am assuming you have the disk to reload Ubuntu.  If so, not knowing what caused the network manager icon to disappear, you may save time reloading Ubuntu.

Make sure you have the .inf file needed for Ndiswrapper on CD of USB storage to use after reinstall.  After reinstalling, you can use Synaptic Packager Manager to load the Ndiswrapper packages (3 of them) by enabling CDROM.

Takes about a half hour and might save a lot of time chasing down other solutions.

---

### Post by PerverseLeigh on 2009-11-21
the iwlist scan came back as follows :

lo               Interface doesn't support scanning

eth0           Interface doesn't support scanning

wmaster0   Interface doesn't support scanning

wlan0         No scan results

---

### Post by williejones on 2009-11-21
Try putting in your Ubuntu CD and see if Synaptic Package Manager can repair Ndiswrapper.  Remember to enable CDrom support in package manager.

---

### Post by PerverseLeigh on 2009-11-22
Thanks =) 
I think that my son will have no wireless 'till he figures out what he did to it. I'm not going to be fixing it all the time... & I have a bunch of ethernet cables of ALL sizes! hehe

---

### Post by Gregz on 2009-11-22
I don't want to get into family stuff....... but mine did it at log screen... Logged out went out for dinner came back. Logged back in and on mine no icon (was there when I left). I can log into wifes and there it is internet and all... (thats how I'm typing this) I don't think he did it is a ubuntu thing..

I can't get internet wirelessly on my log in, I have to use wives log in to get it..  wierd..............


                      Greg

---

### Post by PerverseLeigh on 2009-11-22
Thanks =) NP
I really do think it's a setting, (for both cases,) that got mis-set.  As I have had Ubuntu for less than a week IDK what the settings SHOULD be so I can't re-set it. I'm sure once I figure it out I'll be able to take 30sec's & fix it. lol

---

### Post by Gregz on 2009-11-22
I have mine fixed, re added Notification Area and it works fine. I don't know about Karmic that distro is too buggy for me  I use Jaunty...

---

