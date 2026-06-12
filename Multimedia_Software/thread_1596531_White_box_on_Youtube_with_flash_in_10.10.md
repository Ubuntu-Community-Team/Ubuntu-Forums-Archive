---
title: "White box on Youtube with flash in 10.10"
date: 2010-10-14
forum: Multimedia Software
---

### Post by Sir Rodness on 2010-10-14
I'm getting a odd issue and it appears to be only on Youtube at the moment. Play back of any video there is just a white box with audio. Otherwise, well at least so far, any other site I've been to with flash video works just fine. Anyone experiencing the same thing?

Another note, which may or may not be related. If I try to remove or install Flash in Ubuntu Tweak it always says Update Failed. However I go to the Ubuntu Software Center and I can install and remove Flash with no trouble at all.

---

### Post by Sir Rodness on 2010-10-16
> **Sir Rodness said:**
> I'm getting a odd issue and it appears to be only on Youtube at the moment. Play back of any video there is just a white box with audio. Otherwise, well at least so far, any other site I've been to with flash video works just fine. Anyone experiencing the same thing?

Another note, which may or may not be related. If I try to remove or install Flash in Ubuntu Tweak it always says Update Failed. However I go to the Ubuntu Software Center and I can install and remove Flash with no trouble at all.

Found the solution on this site posted as grey box instead of white box. How they figured out that purging the PPA "erik-b-andersen/rgba-gtk" would do the trick I don't know, but it definitely worked. Flash playback is back to normal. Appears that PPA requires some update before it will play nice with Youtube. In the meantime compiz opacity will do just fine.

---

### Post by Sunships on 2010-10-16
> **Sir Rodness said:**
> Found the solution on this site posted as grey box instead of white box. How they figured out that purging the PPA "erik-b-andersen/rgba-gtk" would do the trick I don't know, but it definitely worked. Flash playback is back to normal. Appears that PPA requires some update before it will play nice with Youtube. In the meantime compiz opacity will do just fine.

Hiya, could you please elaborate on how to do this? I am having the same problem, but I can't find the thread that you mention, and don't want to delete anything I shouldn't.

---

### Post by Sir Rodness on 2010-10-17
Sorry folks, 

Forgot to mention that post I followed for my similar situation was "Adobe Flash plugin gray box (sound works)". The 10# post by gsedej indicating to purge RGBA transparency is what I did to get my flash working again.

[http://ubuntuforums.org/showthread.php?t=1564848&highlight=Adobe+Flash+plugin+gray+box+%28sound+works%29](http://ubuntuforums.org/showthread.php?t=1564848&highlight=Adobe+Flash+plugin+gray+box+%28sound+works%29)

hope this link work properly to get you there directly.

---

### Post by garvinrick4 on 2010-10-17
> **Sir Rodness said:**
> I'm getting a odd issue and it appears to be only on Youtube at the moment. Play back of any video there is just a white box with audio. Otherwise, well at least so far, any other site I've been to with flash video works just fine. Anyone experiencing the same thing?

Another note, which may or may not be related. If I try to remove or install Flash in Ubuntu Tweak it always says Update Failed. However I go to the Ubuntu Software Center and I can install and remove Flash with no trouble at all. Just for the sake of getting a new package of flash. Open a terminal and:
```
sudo apt-get remove flashplugin-installer
```
```
sudo apt-get clean
```
```
sudo apt-get install flashplugin-installer
```
This will remove old
clean out cache so can go fetch a new package and not the same one.
install new flash
Always nice to get a fresh copy from repositories:

---

### Post by Sunships on 2010-10-17
Hi, I've tried the fix above, but do not have the erik-b-andersen/rgba-gtk packages mentioned above. Are there any other names for this package, or is there another package which could also be responsible?

Thank you.

---

### Post by Sunships on 2010-10-18
*bump*

---

### Post by Sunships on 2010-10-21
> **Sunships said:**
> Hi, I've tried the fix above, but do not have the erik-b-andersen/rgba-gtk packages mentioned above. Are there any other names for this package, or is there another package which could also be responsible?

Thank you.

Just in case anyone else has the same problem, in the absence of the rgba packages, I have since found that in my case the problem is due to my using 64-bit Ubuntu, and I was able to fix it using the protocol described here: [http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)

---

### Post by Yellow Pasque on 2010-10-21
> **Sunships said:**
> Just in case anyone else has the same problem, in the absence of the rgba packages, I have since found that in my case the problem is due to my using 64-bit Ubuntu, and I was able to fix it using the protocol described here: [http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)
If you downloaded the 64-bit Flash version from the Softpedia link in that article, I suggest you remove it, as it's no longer supported and contains known security vulnerabilities. You can get the new native 64-bit Flash 10.2 preview from: [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p2_64bit_linux_092710.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p2_64bit_linux_092710.tar.gz)

---

### Post by Sir Rodness on 2010-10-24
I'll have to keep that in mind if I decide to try out 64 bit again. 

Cheers.

---

### Post by Sunships on 2010-11-01
> **Temüjin said:**
> If you downloaded the 64-bit Flash version from the Softpedia link in that article, I suggest you remove it, as it's no longer supported and contains known security vulnerabilities. You can get the new native 64-bit Flash 10.2 preview from: [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p2_64bit_linux_092710.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p2_64bit_linux_092710.tar.gz)

Thanks for the tip Temujin, I have done as you advised.

---

