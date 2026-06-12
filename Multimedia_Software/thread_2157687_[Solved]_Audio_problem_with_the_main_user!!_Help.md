---
title: "[Solved] Audio problem with the main user!! Help"
date: 2013-06-26
forum: Multimedia Software
---

### Post by gugu88 on 2013-06-26
Hi everybody,

some time ago I installed skype 4.2 without success (it did not work properly), i tried several version. Meanwhile i installed some updates too. 
After that i removed everything and rebooted my system. Since then the audio stopped working!!!! 

I tried several solution looking on internet and finally i partially solved the problem by creating a new administrator user!!! Therefore now I have two administrator users, the old one with all my configuration (fovorites, bookmarks, history, softwares configuration, desktop, ecc..) but with the audio problem and the new one virgin but without the audio problem.

How is it possible??????? The settings should not be the same for they both???? 

 And how can I solve the problem in my original user????

I checked alsamixer and pulseaudio settings and everything should be right!!!

Please help me....

In attach alsamixer and audio configuration screenshots

P.S: sorry for my terrible english I hope I have been clear enough in describing my problem!!!!

[ATTACH=CONFIG]244183[/ATTACH][ATTACH=CONFIG]244184[/ATTACH]

---

### Post by artbio on 2013-06-26
Hi. Those words on the pictures seem like Italian. Your English is perfect!

That is possible. There are system wide settings. And there are per user settings. On the Home folder of each of your user accounts there is a ".pulse" hidden folder. Press Ctrl+H to see hidden files and folders.
I suggest you check what is different about those folders in both accounts. If there are differences then that might explain the observed behaviour. You might try deleting that folder (move to trash, so you can move back in case anything goes wrong). The folder should be recreated and then the system wide settings will be used.

---

### Post by Yellow Pasque on 2013-06-26
Note that the .pulse user files were moved to ~/.config in Ubuntu 13.04: [https://wiki.ubuntu.com/PulseAudio#Resetting_User_Configuration](https://wiki.ubuntu.com/PulseAudio#Resetting_User_Configuration)

---

### Post by gugu88 on 2013-06-26
thanks artbio!! Your solution worked, i removed the .pulse folder and after rebooting everything works fine!!!!!!!!!

Thank you very much, it's one week that i posted the same problem in the italian ubuntu forum but no one was able to help me!!!!!!!

Bye bye!!

---

### Post by artbio on 2013-06-27
I am glad it worked for you. I just forgot to tell you that you could restart pulseaudio without needing to reeboot your machine. Running "pulseaudio -k" on a terminal restarts the pulseaudio sound server.

---

