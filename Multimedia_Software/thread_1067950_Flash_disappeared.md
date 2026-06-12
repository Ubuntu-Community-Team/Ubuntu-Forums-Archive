---
title: "Flash disappeared"
date: 2009-02-12
forum: Multimedia Software
---

### Post by halvgud on 2009-02-12
hi,
All the sudden, after one update I guess, all the movies i was watching in my Mozilla web-browser aren't appearing anymore..it's like transparent. At one point i had a message saying the plug-in was missing but didn't find one that would solve my problem. I am on Ubuntu, Hardy Heron. I have been trying to assign one player like totem, or VLC to read those files, but then i get a message saying there is nothing to start the stream...Well, i really don't know what to do...Thank you for helping me.

---

### Post by redroad55 on 2009-02-12
follow this thread : [http://ubuntuforums.org/showthread.php?t=1067107]("http://ubuntuforums.org/showthread.php?t=1067107")
Post back with any results and or questions...Best to you

Make sure you Identify your kernel correctly 32 bit or 64 bit ?

---

### Post by halvgud on 2009-02-12
Hi, thanks for your help. Well, i did follow the thread, and now i am stuck with no Flash player....i tried to install one from the adobe site, but i can't seem to be able to extract it..i don't get it...

Actually it seems like i have Flash player installed according to the add/remove function, but on the page it says i need the newest version of flash player...

---

### Post by redroad55 on 2009-02-12
If you look at post #9 on the thread posted above you must first copy and paste that command in terminal that takes all flash away..then follow the second part ..If you are not sure on the second part post back what file you have saved to your desktop(either the tar or deb) and I'll try to make more clear the remaining process .. Post back

---

### Post by grouchyolddude on 2009-02-12
> **redroad55 said:**
> If you look at post #9 on the thread posted above you must first copy and paste that command in terminal that takes all flash away..then follow the second part ..If you are not sure on the second part post back what file you have saved to your desktop(either the tar or deb) and I'll try to make more clear the remaining process .. Post back

[http://ubuntuforums.org/showthread.php?p=6723505#post6723505](http://ubuntuforums.org/showthread.php?p=6723505#post6723505)
flash had disapeared in my case too. When I typed the purge command, I got a return that said it couldn't be found. ..not installed.
 I used the synaptic repos to reinstall , after following redroads thread. 
Working fine after restart..

---

### Post by halvgud on 2009-02-12
I did follow what was written in that post. Do you think i should restart my computer ? I'll try and then I'll get back here to tell what's happened.

Ok, i did restart my computer and nothing happened, so i downloaded the tar.gz version of flash player but then i am stuck, as always with these non self-extracting files.

---

### Post by redroad55 on 2009-02-12
So with the tar version of the file sitting on your desktop > double click > In open window double click again on the file it should open to 2 files > drag the file labled libflashplayer.so to the desktop with your mouse > Open terminal > then paste this command in terminal>
> sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo ln -sf /usr/lib/flashplugin-nonfree/libflashplayer.so /etc/alternatives/firefox-flashplugin && sudo ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplayer-alternative.so
You may now restart your web browser and use the plugin. Post back
with any results and or questions...Best to you

---

### Post by halvgud on 2009-02-12
I tried your solution and i don't think it did the trick for me. I even tried to install the .Tar version without success, and finally i downloaded the .deb version and at last it's working.

Thank you very much for time.

Best to you too.

---

