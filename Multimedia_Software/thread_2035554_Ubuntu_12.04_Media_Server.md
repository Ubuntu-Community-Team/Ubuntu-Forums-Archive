---
title: "Ubuntu 12.04 Media Server"
date: 2012-07-30
forum: Multimedia Software
---

### Post by neutronforrest on 2012-07-30
Dear Forum,

I have a home server where I did a fresh install from 11.10 to 12.04.  I have a single hdd with the operating system.  I then have 2 500gb hdd with raid 1.  

I have tried to install minidlna, mediatomb, and serviio.  I have not been able to.get any of these to work.  With the last operating system (11.10) I used serviio and it worked perfect.  I don't understand what is prohibiting me from getting a media server to work.  

Thanks for the help in advance..Chad

---

### Post by kingtiger01 on 2012-07-31
Well its not much help, not Stating WHATS not working...  i use PS3MediaServer myself(Better FFMPEG/MENCODER support for Certian Devices)
And it works fine for my setup?
I used MediaTomb in the past and it worked fine...

----
have you installed the Required Codecs?
do you have a copy of FFmpeg on youre system?
have you Checked File/Folder Permissions?

---

### Post by neutronforrest on 2012-07-31
Yes..you are correct.  I was not clear.  I will list the following issues.

I was unable to get my dlna device to recognize the **minidlna**.  I followed a proceedure were I changed the minidlna.conf file.  I then uninstalled minidlna.

I installed **MediaTomb** and was able to get my dlna to see the folders and content in the folders.  But when I would try to stream the content I would get the following error "onclet media not able to stream"  

I then installed **Serviio**.  Here I have read that I need to rebuild ffmpeg.  Also, I think I have an issue with the current java version.

I just have been having so much trouble trying to get anything to work.  I had Ubuntu 11.10 and Serviio worked perfect.  Does anyone have instruction for the proper installation of Serviio?  Is there another program that might be better suited for 12.04?

Thanks for the response...Chad

---

### Post by evilsoup on 2012-07-31
I spent a frustrating, fruitless evening trying to get mediatomb to work.
Then I installed ps3mediaserver. I suggest trying that - I didn't have to mess around with any config files, it just worked & all the settings I need are available through the GUI.

You have to use a PPA (**ppa:happy-neko/ps3mediaserver**).

---

### Post by sparvik on 2012-08-06
I was wondering if anyone has used mediatomb to upnp to a U-verse receiver. I was able to to get it to work one time but since then it is scetchy.  It will show up for a second and then disappear. When it stays in the list long enough for to select it it streams fine, and it works fine on upnpbubble with my android. 

Anyone have any ideas?

---

