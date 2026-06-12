---
title: "new install on new in box computer, really happy. But wifi will not work"
date: 2011-11-27
forum: Networking &amp; Wireless
---

### Post by SkeeterBum on 2011-11-27
Hello  everyone, 

First time user of any linux based system. I just installed 11.10 a little bit ago and I seem to have everything in line except, I cannot seem to get the wifi to work properly. 

-I go to settings->network->wifi and when I click "on" it slides over a second and then turns to "off".
-I have clicked on enable wireless in the broadcast icon in the top right hand corner but it does nothing it seems, I just click it is says nothing.
-I ran $ sudo lshw -c network and it said my network adapter is disabled. I have the switch on on the laptop i know, i can get to the internet on my windows 7 partition.
-I can get online if i am hard wired
-I ran update manager (236 updates) and that did nothing, i also looked for drivers but it came up with nothing. 


The laptop is a lenovo i5, windows 7 and ubuntu. It is new out of the box this morning.

---

### Post by SkeeterBum on 2011-11-28
What i have no figured out is that i have a intel centrino wireless-n 1000 card, I am trying to use ndiswrapper to utilize my existing windows driver but I am still having some problems because of how new i am to this.

First, I downloaded ndiswrapper and extracted it to a folder in windows. I then booted to ubuntu and ran the make file inside of the extracted file. I then type the commend $ndiswrapper -l and it says cannot find a version of nidswrapper.

My other problem is that on the wiki for ndis I am not even sure if my wifi card is supported, again i am new I am not exactly sure what i am doing.



A little background, i am a 3rd year cs student so i know a fair amount of computers in general. but i have used windows my entire life and a bash a few times to compile programs. i understand that a lot of corps. dont release documentation so drivers can be made for linux systems and thats why ndiswrapper is used so that the native windows driver can run inside/(alongside?) ubuntu.


Please move my thread if it should not be in here, i figured this is the right subtopic. Also sorry if this is all very newbish.

Bum Skeeter.

---

