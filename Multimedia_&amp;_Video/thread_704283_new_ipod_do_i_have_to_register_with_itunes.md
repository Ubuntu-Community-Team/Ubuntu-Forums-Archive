---
title: "new ipod do i have to register with itunes ?"
date: 2008-02-22
forum: Multimedia &amp; Video
---

### Post by delta_9 on 2008-02-22
hey guys i just got  an ipod and want to use it on Ubuntu 7.10 do i need to register with itunes before using it . i have plugged it it in mounts and all i have copied  mp3's to it (drop and drag ) but it is not working any one got a clue ? i am sure some one has been here before. 

will it play standard MP3 ? or do i need to convert to some silly ipod only format
 (shakes fist holding rotten apple )  
thanx delta

---

### Post by cozmicharlie on 2008-02-22
No you don't have to register with itunes.  No you do not have to do anything special to play mp3 files on your ipod.  

Now to the harder question - why your ipod won't work.  From your post I assume it is new and you have never used it on Windows.  So lets start by getting more info.  When you say you moved files to the ipod how did you do it?  What program did you use?  

Have you installed the packages needed for multimedia such as the Ubuntu restricted extras? [https://help.ubuntu.com/community/RestrictedFormats#head-e69e0c62de07b1e2b560c1ad6b68823328906067](https://help.ubuntu.com/community/RestrictedFormats#head-e69e0c62de07b1e2b560c1ad6b68823328906067) .  

This should help also.  [https://help.ubuntu.com/community/PortableDevices/iPod?action=show&redirect=IPodHowto](https://help.ubuntu.com/community/PortableDevices/iPod?action=show&redirect=IPodHowto) 

If you still can't run the ipod post back.

---

### Post by delta_9 on 2008-02-22
many thanx to you and Amarok 8-)

[IMG]http:/http://goutham.files.wordpress.com/2006/12/appleipod.jpg[/IMG]

many thanx many thanx many thanx many thanx many thanx many thanx many thanx many thanx many thanx many thanx many thanx many thanx many thanx many thanx many thanx many thanx many thanx many thanx many thanx many thanx many thanx many thanx many thanx OK thats enough lol

---

### Post by delta_9 on 2008-02-23
this post is for the benefit of others who are unfamiliar with ipod in the hope this helps some one else.
i plugged in the ipod it mounted with Rythmbox than Rythmbox would disappear leaving an ipod icon on the desktop so i thought cool Linux has made this ipod like a generic mp3 player i can simply double click this icon and drag and drop mp3's in to it and it will work. i was wrong if you do this it will not work as it needs a file named iTunesDB among others. how i solved my problem well i followed the advise above with the restricted software. it is restricted as it it not open for development not because it is bad for your PC so please don't let the name scare you. than went and installed  Amarok  (applications>add/remove and search for Amarok) you need to use that to (THIS IS WHAT I HAD WRONG) "**IMPORT THE MUSIC**" than you are good to let the music roll on all night long. hope this helps some one out there

---

### Post by NOLU on 2008-02-24
I've recently switched to Ubuntu 7.10 and would like to know how I get songs on my iPod using Amarok please?

Not 100% sure how.

Thanks.

---

### Post by cozmicharlie on 2008-02-24
> **NOLU said:**
> I've recently switched to Ubuntu 7.10 and would like to know how I get songs on my iPod using Amarok please?

Not 100% sure how.

Thanks.

This shows you how
[http://www.simplehelp.net/2007/07/04/how-to-use-amarok-to-manage-your-ipod-in-ubuntu/](http://www.simplehelp.net/2007/07/04/how-to-use-amarok-to-manage-your-ipod-in-ubuntu/)
Post back if you have any problems

Enjoy

---

### Post by NOLU on 2008-02-24
Got it working thanks :)

---

### Post by timgerr on 2008-02-25
Hello all, I am having so many problems.  

I have just bought a new IPod 3rd Generation. 
4 GB, 
software version 1.1.

I am running Ubuntu at home but windows at work.  I can get my new iPod to work fine wit windows and itunes.  I can transfere files fine.  

When I hook the iPod up with Ubuntu via Amarok or gtkPod or Rythembox, I can see the device and the files fine. When I add music and eject the device, I look and all the music I added from Windows/Itunes is gone including the files that I added with Ubuntu.

No matter what I do, when I add files with any linux package, and eject the device, the device says that it doesn't have anything on it.

What am I doing worng???

Thanks,
timgerr

---

### Post by delta_9 on 2008-02-28
timgerr please tell me how your going about it step by step

---

### Post by cozmicharlie on 2008-02-28
timgerr - please do this - connect your ipod, run this command and note the firewire ID (the 16 digit number 

```
sudo lsusb -v | grep -i Serial
```

Note down your FirewireID from the list, its the 16 digit one.


>  iSerial                 1 0000:00:1a.1
  iSerial                 3 000A27001AD21163  [COLOR="Blue"]<----Example  IPOD FirewireID[/COLOR]
  iSerial                 3 3547160158733600
          line coding and serial state
          line coding and serial state
  iSerial                 0 
  iSerial                 1 0000:00:1d.7
  iSerial                 1 0000:00:1d.1
  iSerial                 1 0000:00:1d.0
  iSerial                 1 0000:00:1a.0
  iSerial                 0 
  iSerial                 0 
  iSerial                 0 
  iSerial                 1 0000:00:1d.2
  iSerial                 0 
  iSerial                 3 060114014271000001
  iSerial                 1 0000:00:1a.7

Now type or cut and paste the following in the terminal:

```
sudo gedit /media/IPOD/iPod_Control/Device/SysInfo
```

SysInfo should only contain:

> FirewireGuid: 0x<your firewire ID>

e.g. FirewireGuid: 0x000A27001AD21163

This should should match the Firewire ID you got above.  Let me know if they do or not.

---

