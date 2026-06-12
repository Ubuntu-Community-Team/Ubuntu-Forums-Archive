---
title: "[SOLVED] for NWZ Walkman"
date: 2008-10-25
forum: Multimedia Software
---

### Post by amr_essam on 2008-10-25
dear there .
i have a mp3 walkman video player , which uses the MTP protocol ,
when i first plugged it , it couldn'y be mounted
so i used the following commands

sudo apt-get install pmount
ls /dev/disk/by-label -lah
pmount /dev/sdd1 WALKMAN

and then it works gr8 only for one time , after i unplug the walkman and plug it again , it appears in my computer , but i cant see the files inside 

so i tried again the previous commands , but it tells me that there is already a mount file for this drivers

Hope that my problem is clear 

Regards 
Amr Essam

---

### Post by amr_essam on 2008-10-27
Hey guys 
2 days without any answer 
please help

Regards

---

### Post by valmorel on 2008-10-27
> **amr_essam said:**
> dear there .
i have a mp3 walkman video player , which uses the MTP protocol ,
when i first plugged it , it couldn'y be mounted
so i used the following commands

sudo apt-get install pmount
ls /dev/disk/by-label -lah
pmount /dev/sdd1 WALKMAN

and then it works gr8 only for one time , after i unplug the walkman and plug it again , it appears in my computer , but i cant see the files inside 

so i tried again the previous commands , but it tells me that there is already a mount file for this drivers

Hope that my problem is clear 

Regards 
Amr Essam

Hi, I just got your message/saw your post. Which version of Ubuntu are you using? If is 32 bit, and you can run 64 bit, this problem has been fixed in 64 bit. In 32 bit 8.04, you need to modify the Hal file to fix it, or if you just want to transfer files, you could use Gnomad2, which is written specifically to manage files on an MTP protocol player. If you want to modify Hal to allow drag and drop from file manager, just reply to this, and I will try to find the link for you giving instructions. It is actually somewhere on the Xubuntu forums.

---

### Post by amr_essam on 2008-10-27
> **valmorel said:**
> Hi, I just got your message/saw your post. Which version of Ubuntu are you using? If is 32 bit, and you can run 64 bit, this problem has been fixed in 64 bit. In 32 bit 8.04, you need to modify the Hal file to fix it, or if you just want to transfer files, you could use Gnomad2, which is written specifically to manage files on an MTP protocol player. If you want to modify Hal to allow drag and drop from file manager, just reply to this, and I will try to find the link for you giving instructions. It is actually somewhere on the Xubuntu forums.


Okay ,
first: actually i dont know either if i am 64 bit or 32 bit 
so plz tell me how to know that .

Second: i tried the GNOMAD2 and it's so boooring , i need the drag and drop way ,it 's better anyway

Thanks for ur response 
Regards

---

### Post by valmorel on 2008-10-27
Ok, I understand you man. You are not running 64 bit Ubuntu at the moment, because if you were, you would not have this problem. The easiest way to find out if you can, is to download a 64bit .iso, make a live cd, and see if you can boot it.
Anyway, if you dont want to do this, follow the instructions here [http://kubuntuforums.net/forums/index.php?topic=3096598](http://kubuntuforums.net/forums/index.php?topic=3096598)  It sounds way more scary than it really is.
After doing this, your Walkman will mount normally like a USB stick, allowing drag and drop direct from file manager, but will ALSO mount via MTP in a program like Gnomad2, which is very cool.
I leave it to you to confirm you are using Ubuntu Hardy Heron, which is the version these mods are aimed at.
It worked great for me. After, Ubuntu will keep trying to tell you to update to the latest version of Hal. Obviously, ignore it.
As another alternative, you could try Puppy Linux, which will mount your Walkman normally as is. Good luck, let me know how it goes.

---

### Post by amr_essam on 2008-10-28
> **valmorel said:**
> Ok, I understand you man. You are not running 64 bit Ubuntu at the moment, because if you were, you would not have this problem. The easiest way to find out if you can, is to download a 64bit .iso, make a live cd, and see if you can boot it.
Anyway, if you dont want to do this, follow the instructions here [http://kubuntuforums.net/forums/index.php?topic=3096598](http://kubuntuforums.net/forums/index.php?topic=3096598)  It sounds way more scary than it really is.
After doing this, your Walkman will mount normally like a USB stick, allowing drag and drop direct from file manager, but will ALSO mount via MTP in a program like Gnomad2, which is very cool.
I leave it to you to confirm you are using Ubuntu Hardy Heron, which is the version these mods are aimed at.
It worked great for me. After, Ubuntu will keep trying to tell you to update to the latest version of Hal. Obviously, ignore it.
As another alternative, you could try Puppy Linux, which will mount your Walkman normally as is. Good luck, let me know how it goes.



Well , that helped
thanks soo much , finally i can use my MP4

Thanks again
marked as solved

Regards 
Amr Essam

---

### Post by valmorel on 2008-10-28
UPDATE..... I tried the latest release candidate for 8.10 Intrepid Ibex, and it automounts the Walkman just fine. Praise the Lord!
FYI, so does Puppy Linux...........

---

