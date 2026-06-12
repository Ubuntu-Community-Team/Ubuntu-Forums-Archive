---
title: "Firefox plugins - Adobe Flash &amp; Real Player"
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by rmhodv on 2007-11-07
Hi

Please could someone help me to install the aforementioned. I have looked at the instructions via the Firefox website, but don't understand what to do? :)

---

### Post by rmhodv on 2007-11-08
C'mon guys......Please:guitar:

---

### Post by ccprog on 2007-11-08
If you want to install them via the Synaptic package manager, add [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") to your sources. After that, it's really easy.

---

### Post by aysiu on 2007-11-08
I don't know about Real Player, but you can install Flash by following these instructions:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by paulbeattie87 on 2007-11-08
I'm having trouble getting Realplayer to work with Firefox it has installed ok and the files are in the plugin directory but it doesn't doesn't seem them and I forgot how I got it working previously! 

Nobody wanted to help me on my separate thread.

---

### Post by icelechi on 2007-11-08
Hi,
I got my Adobe Flash plugin by going to System / Administration / Synaptic Package Manager.
There you should go to the Settings menu and select Repositories. Select the Main, Universe and Multiverse check boxes.
Close and go back to the Synaptic Package Manager and hit the Reload button
Scroll down and find 'flashplugin-nonfree' and select that.
Hit the Apply button and Bob's your uncle!!

That's that for Adobe Flash. For Real Player, you can go to [http://www.real.com/linux](http://www.real.com/linux) and click on 'Download RealPlayer.'
When it is downloaded, open up a terminal by going to  Applications / Accessories / Terminal.
use the command cd to get to the directory that the file downloaded to .eg. If it downloaded to the desktop, use 

cd ~/Desktop

when you get there, type in:

"chmod a+x RealPlayer10GOLD.bin" 
and hit enter. Then type in:

"sudo ./RealPlayer10GOLD.bin"
and hit enter. You will be asked where you want to save; I saved mine in /usr/bin/RealPlayer.
The next question answer y and the following, just hit enter.
It should work now.

Well that's how I got these two working. Hope that was useful.

---

### Post by rmhodv on 2007-11-09
Hi

Thank you all very much. I have managed to install both of them ok. The problem I now have is that I have installed Media Player Connectivity and it defaults to VLC.  Thinking about it the MPC is being a bit of a pain. How do I uninstall it. :)

---

### Post by rmhodv on 2007-11-12
Can anyone help me :)

---

### Post by Robbot5000 on 2007-11-12
The same way you uninstall any Firefox Extension.   Go to "Tools->Add-ons" then select the Extensions Tab.  You should see MediaPlayerConnectivity listed in the window.  Select it and then click uninstall.  Then just restart Firefox and everything should be good.  You can also adjust the preferences of MPC to have it active only with certain media.  Hope this helped.

---

