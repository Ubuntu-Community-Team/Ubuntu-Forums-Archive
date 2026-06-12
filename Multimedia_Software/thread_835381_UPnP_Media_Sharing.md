---
title: "UPnP Media Sharing"
date: 2008-06-20
forum: Multimedia Software
---

### Post by Venatu on 2008-06-20
Hi, im running the latest version of Ubuntu Server. I would like to share my music between multiple devices, can anyone recommend a program and a guide to getting started with it? I have installed mt-daapd and that is working great for iTunes, but I need a UPnP compatible one for my Xbox and relatives insistence on Media Player :)

Thanks, Venatu

---

### Post by radamo on 2008-06-20
Try MediaTomb... It works fairly well. 
RA

---

### Post by Venatu on 2008-06-20
I tried that and it was not accessable in WMP, it did not appear near library. I also tried uShare and managed to connect to it, but no songs were listed, yet I knew some were found as the console had said so. I can try them again, if someone could kindly walk me through setting them up.

Thanks, Venatu

---

### Post by fenian on 2008-06-20
You can use XBMC (xbox media player) [there is a how to here]("http://ubuntuforums.org/showthread.php?t=458675").

---

### Post by Venatu on 2008-06-21
Ibve gone back to try ushare as Uve had the most sucess with it. I can open a library in WMP, but it reports no files found. Does anyone know of a way for me to check the files its found, ro how to solve this?

I dont think xbmc would work as it uses a GUI, and im running on CLI on the server build

---

### Post by Venatu on 2008-06-22
No-one?

---

### Post by amak79 on 2008-06-22
Venatu,

What version of Windows are you using? If your using Windows XP then WMP doesn't have UPnP client support, only server. You will need Windows Vista for WMP UPnP client support.

---

### Post by zeronothing on 2008-06-22
You could try Coherence which is a python write DLNA/UPnP program. then for a easy frontend to Coherence download Gcoherence [[COLOR="Blue"]here[/COLOR]]("http://getdeb.net/app/GCoherence"). I forgot, you will also need to install the latest Coherence from [[COLOR="Blue"]here[/COLOR]]("https://coherence.beebits.net/wiki/WikiStart#Download"). you will need to install the SVN version because it has the most up-to-date fixes to work for new devices. I use this setup for my PS3 and it works great. if you need more help, message me on the forums.

---

### Post by pyroger101 on 2009-06-05
[http://helplinedirect.myfreeforum.org/Getting_xbox_360_and_PS3_to_pick_up_linux_servers_UPDATE_about69.html](http://helplinedirect.myfreeforum.org/Getting_xbox_360_and_PS3_to_pick_up_linux_servers_UPDATE_about69.html)

Im using ushare at home and most files are working fine with xbox,

try out that link and let me know how you get on .

all the best

ger

---

### Post by piraya on 2009-06-08
any one using the popcorn hour 110A media player as front end?

---

### Post by mushroomblue on 2009-09-10
currently using Ampache 3.5 as a backend for coherence, which has full Xbox 360 UPnP compatibility. streams all my music wonderfully. uses gstreamer for transcoding, and doesn't destroy my CPU while doing so. also has plugins for lolcats, flickr, BBC, Youtube, etc. it's the best solution I've found so far.

---

