---
title: "No system sounds and no Flash 10 audio"
date: 2009-08-27
forum: Multimedia Software
---

### Post by figneutron on 2009-08-27
It's now 20 days after I installed 9.04, and I'm still trying to get system event sounds and Flash 10 player audio to work. I have confirmed that Flash 10 is installed and working, because the Flash test animation says so when I visit the Flash page on the Adobe website. Yet, when I play a video on YouTube, I get video only. The Tools/Add-ons listing for Firefox 3.0.13 says that only one version of Flash player is installed, and it is Flash 10. Removing the swfdec 0.8.2 mozilla plug-in didn't help. Flash 10 is also functional when I run Opera, yet I get no audio then as well.

 I followed the steps in the comprehensive ALSA sound guide and determined that my Chaintech 710 audio controller, which has the VIA VT1720/24 chip onboard, is installed with the correct ALSA driver ICE 1724. I know this because the sound tests on Preference/Sound/Device are successful if Chaintech AV-710 ICE 1724 (OSS) is selected for Sound Events and for Music and Movies. Also, the .ogg Ubuntu system sound files are installed in the correct directory. I have no problems playing music cds or movie dvds or listening to Internet radio. As far as I can tell, my only audio issues are with system sound events and Flash 10.

Curiously, several times in the past week my audio problem disappeared when I switched to the Guest account (but not every time I switched!). This was an intermittent change, and I can no longer replicate it. I should add that when I got audio on YouTube running Firefox under the Guest account, swfdec was playing the Flash content and not Flash 10, why I don't know.

It must be evident that I don't know much overall, either. Please tell me what you would do next if you were in my place.

---

### Post by Yellow Pasque on 2009-08-27
For system sounds, check if you can play something with canberra, e.g:
```
canberra-gtk-play --file=/usr/share/sounds/ubuntu/stereo/bell.ogg 
```

Since OSS output works for gstreamer, try making Flash use OSS output. Assuming you're using 32-bit/x86 Ubuntu, save this file: [http://ubuntuforums.org/attachment.php?attachmentid=69426&d=1210377383](http://ubuntuforums.org/attachment.php?attachmentid=69426&d=1210377383)

Extract that to /usr/lib and then run the ldconfig command. Close any open Firefox windows and restart Firefox.

---

### Post by figneutron on 2009-08-28
First: I ran *canberra-gtk-play --file=/usr/share/sounds/ubuntu/stereo/bell.ogg* with no success. I heard nothing.

Second, I did this after putting libflashplayer.so in /usr/lib:

 *root@douglasn:/usr/lib*# *ldconfig libflashplayer.so*
 
and bash responded:

[I]/sbin/ldconfig.real: relative path 'libflash.so' used to build cache

[/I]Then I started Firefox, went to YouTube, and played a Modest Mouse music video. It played silently.

Did I do something wrong? I interpreted the instruction "Extract that to /usr/lib and then run the ldconfig command" to mean execute[I] root@username:/usr/lib# ldconfig libflashplayer.so
[/I]

---

### Post by figneutron on 2009-08-28
I mistyped the root@usrname:/usr/lib# command. I ran *ldconfig libflashsupport.so *and not *ldconfig libflashplayer.so* as I said in my first reply to Temujin.
 
Still, no audio on YouTube with Flash 10.

---

