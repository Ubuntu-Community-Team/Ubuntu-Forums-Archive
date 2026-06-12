---
title: "simple tv tuner software"
date: 2010-10-24
forum: Multimedia Software
---

### Post by nae5 on 2010-10-24
I tried installing both tvtime and mythtv and i could not figure out the configuration and found the ui's to be.. more effort than I wanted at first.

     I was hoping to get some opinions on a tv tuner program that has a simple GUI.  All i want to do is watch the channels in real time.

     If there are any other programs out there that you might feel have an easier configuration and GUI let me know please.  Or, if these are in fact the best, any help on where to look, or what to do in the configuration of one of these would be most appreciated.

  

     02:00.0 VGA compatible controller: ATI Technologies Inc Juniper [Radeon HD 5700 Series]
02:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]

     07:00.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

     ubuntu 10.10 (very nice release on my pc)

---

### Post by tweaked on 2010-10-24
Well, I have just spent the last week trying to watch a baseball game on Ubuntu and about the last 12 hours straight today. My conclusion is to just go buy Windows 7 which is on sale $150/3 licenses. My tuner is supported so hardware has been no issue.

At your mention. I just tried Tvtime. That must be somebodies idea of a joke, I'm not seeing any way to channel scan, which btw is a common theme with all 5 viewers I currently have installed. None of them work. Not one. Kaffeine seems the most promising but nobody, in all my searching, has a clue how or where the mystical channels.dtv file is or how to make one so all I can get is 5 channels it has loaded somewhere. Klear has no documentation, at least in English, although the wiki claims a faq and forum. The going joke on the internet is that a working version of Mythtv is a myth and xine, after finally getting a legit channels,conf file assembled simply doesn't work. After 3 hours of searching I read thats a common theme too.

You will need a separate scanner, w_scan has been the best for me but no ui. 

My fallback all week in the baseball playoff season has been XP and Wintv. No problems. Good luck, see you on the darkside.

My

---

### Post by lswartz on 2010-11-17
How discouraging. I just found tvtime in the package manager & it worked perfectly the 1st time on a Hauppauge WinTV card. The 2d time was a little exciting as I lost the menu & punched all the keys until I found the 'h' gave me the setup menu & 'a' changed the format from 4:3 to 16:9. Well this is great, my wife just found that right click on the mouse gets the setup menu too. Tvtime does have a good web page that gives all the commands as well. 

MythTV - I could never figure out.
Zapping - never worked for me.
xawtv - worked for sever months then started freezing and/or loosing the picture completely.
tvtime- worked 1st time but it might behave like xawtv after several months. But today, my wife is happy.

---

### Post by unixisit on 2011-11-09
If you want a good and simple TV program you can try me_tv. This can be found at [https://launchpad.net/me-tv](https://launchpad.net/me-tv). However you will have to run configure and make in order to install it. You will also have to run w_scan here is a copy of the command that I use 
cd
cd .local/share/me-tv
rm channels.conf me-tv2.db
w_scan -c US -X >> ./channels.conf

---

