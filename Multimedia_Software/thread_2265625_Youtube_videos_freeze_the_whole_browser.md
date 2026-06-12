---
title: "Youtube videos freeze the whole browser"
date: 2015-02-16
forum: Multimedia Software
---

### Post by steblo94 on 2015-02-16
SOLVED

Hey guys! I am really new to linux, so if something is obvious, please don't hate me! :) 
I have downloaded the crouton version for chromebook, to get ubuntu 12.04. In the beginning everything worked perfectly, until a couple of weeks after the installation, and some updates. Now each time I try to play a video anywhere online, my whole browser freeze so I have to force quit it. Also when I am trying to play videos with Popcorn time, they never start to play (even if I try to stream to VLC).

* I have tried to uninstall and install flash player a million times.
* I use mozilla
* I have googled the internet down, and not found anything that works for me (including many outdated posts)

Thank you very much! :)

---

### Post by Kirboosy on 2015-02-17
Let me be the first to say, Welcome to the forums! :D

What if you switch the [Youtube player]("https://www.youtube.com/html5") to the HTML5 version? Does it still crash the browser? (You shouldn't need the Flash Player anymore)

How exactly did you install Flash Player?

Hope that helps!
~Caboose

---

### Post by steblo94 on 2015-02-17
Hey, tank you for the welcome, and answer! 
I have tried to use the html 5 version of youtube, but it did not seem to help. I also noticed that when i was trying to use the online spotify player, but then the browser freezed then also. I almost got the same problem with netflix, as it just keep loading, and never starts to play.
About the installation, i have installed it from software center, and also with terminal. I did it at once i installed the crouton ubuntu. I am not sure if i got it from the "restricted extras" package.
If you need anymore information, don't hesitate.

-Steblo

---

### Post by Kirboosy on 2015-02-18
What kind of graphics card are you using? As crazy as it sounds it seems to be a driver issue for GPUs. 

Also some people have reported better luck after installing the 'adblock plus' extension in their Firefox.

Hope that helps!
~Caboose

---

### Post by steblo94 on 2015-02-23
Thanks again! 
I installed the adblock plus, and the browser don't freeze anymore, but it just buffer, and the "start picture" of the video shows. But the video still doesn't start. 
This is the specs of my computer: [http://us.acer.com/ac/en/US/content/model/NX.MJAAA.004](http://us.acer.com/ac/en/US/content/model/NX.MJAAA.004) 

-Steblo

---

### Post by steblo94 on 2015-02-23
I found something that helped! 
"sudo apt-get purge flashplugin-installer"        
       
[http://ubuntuforums.org/showthread.php?t=1985689](http://ubuntuforums.org/showthread.php?t=1985689)

---

