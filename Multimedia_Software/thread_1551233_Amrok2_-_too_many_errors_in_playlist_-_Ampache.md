---
title: "Amrok2 - too many errors in playlist - Ampache"
date: 2010-08-12
forum: Multimedia Software
---

### Post by devonpen on 2010-08-12
After a lot of google action I found an answer that worked for me and is very simple.  So I thought I would share it and a full set of instructions on getting running.

I am running Ubuntu 10.04 with an Ampache server and Amrok2 running.  Found I wanted to remote control the catalogs themselves whilst seated and rather than stream over the Wifi to my crappy speaker on a Dell Streak, I decided the 5 inch subs in my living room would be much better sounding.  So, whilst at home Amrok is perfect for controlling all my music fom any room in the house.

After installing Amrok2 you need to enable Ampache in Amrok from *>settings>configure amrok*.  Click on the tab for *>internet settings* and then enable Ampache by filling in all the server details as here:

[http://ampache.org/wiki/config:amarok](http://ampache.org/wiki/config:amarok)

Make sure your ACL's are also set up correctly in Ampache (should be done automatically if you have installed the most recent version of Ampache).

Now you should be able to connect to the Ampache catalogue and see your songs. At this point I got the playlist error and couldn't play any of the mp3s in my catalogue.  I discovered Ubuntu doesnt ship with the required mp3 codecs (Kubuntu does as Amrok is native) and so you need to install the following package via package manager (or terminal for clever people)
[I]
kubuntu-restricted-extras package[/I]

Thanks to mamarok for this [http://forum.kde.org/viewtopic.php?f=115&t=88822](http://forum.kde.org/viewtopic.php?f=115&t=88822)

Once installed restart and mp3s should play away.  

Now for the Amrok2  Remote.  You need to install a plugin from script which is dead easy as Amrok2 has a script manager built in - so just follow these instructions:

[http://h0lger.de/android-amarok2-remote/](http://h0lger.de/android-amarok2-remote/)

Now all you have to do is go to android market and download the free Amrok2 Remote app and fill in your server ip details in *the >settings *tab like xxx.xxx.xxx.xxx:8484 (you need the port - 8484 is default). 

This setup up works great on my Dell Streak.  I can now control my media server remotely whilst at home and if you install amdroid too you can access Ampache from anywhere for streaming.

WOW!! Micro who?? - Maybe but if Ableton Live goes linux then i'm moving home full time.  Hope this helps someone.  Thanks to all who support Linux and Ubuntu - I love it!!

---

