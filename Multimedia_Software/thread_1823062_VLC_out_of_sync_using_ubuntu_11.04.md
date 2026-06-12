---
title: "VLC out of sync using ubuntu 11.04"
date: 2011-08-11
forum: Multimedia Software
---

### Post by kingjimbo on 2011-08-11
Dear Ubuntu community,

I am in desperate need of your help. Yesterday I said goodbye to Ubuntu 10.04 to trade it in for Ubuntu 11.04.
Everything works exactly like it used to. However, I am having troubles with VLC media player. For some reason the audio is no longer in sync with the video. The delay is about 0.3 seconds. I have googled hell out of this problem but all to no avail. 
I updated VLC to version 1.1.11, I have messed around with the sync option in the preferences > audio menu and I messed around with the output options. 

On the website: [http://www.st4ck.com/en/post/ubuntu-11-04-vlc-out-of-sync/#Runtime](http://www.st4ck.com/en/post/ubuntu-11-04-vlc-out-of-sync/#Runtime)
there is a solution for this problem. I looked up the file and tried to change it but for some reason that is not possible. 

I was hoping that someone could help me out and or explain how to change the code in the file for I am craving to see the rest of the Office Season 5. 

Thanks a lot in advance

---

### Post by tjones00 on 2011-08-11
> **kingjimbo said:**
> 

On the website: [http://www.st4ck.com/en/post/ubuntu-11-04-vlc-out-of-sync/#Runtime](http://www.st4ck.com/en/post/ubuntu-11-04-vlc-out-of-sync/#Runtime)
there is a solution for this problem. I looked up the file and tried to change it **but for some reason that is not possible**. 



In a terminal type

```
gksudo gedit /etc/pulse/default.pa
```

to edit the default.pa file

---

### Post by kingjimbo on 2011-08-12
> **tjones00 said:**
> In a terminal type

```
gksudo gedit /etc/pulse/default.pa
```to edit the default.pa file

Thanks for helping! It worked!

Time for the Office!

---

### Post by praveenmarkandu on 2011-08-27
> **kingjimbo said:**
> Dear Ubuntu community,

I am in desperate need of your help. Yesterday I said goodbye to Ubuntu 10.04 to trade it in for Ubuntu 11.04.
Everything works exactly like it used to. However, I am having troubles with VLC media player. For some reason the audio is no longer in sync with the video. The delay is about 0.3 seconds. I have googled hell out of this problem but all to no avail. 
I updated VLC to version 1.1.11, I have messed around with the sync option in the preferences > audio menu and I messed around with the output options. 

On the website: [http://www.st4ck.com/en/post/ubuntu-11-04-vlc-out-of-sync/#Runtime](http://www.st4ck.com/en/post/ubuntu-11-04-vlc-out-of-sync/#Runtime)
there is a solution for this problem. I looked up the file and tried to change it but for some reason that is not possible. 

I was hoping that someone could help me out and or explain how to change the code in the file for I am craving to see the rest of the Office Season 5. 

Thanks a lot in advance


thanks for finding this. solved my problem

---

### Post by Rasa1111 on 2011-08-27
Thanks!
Worked here to. :) lol

---

### Post by shantiq on 2011-08-27
**Thanx** guys been on the Narwhal for a while now and this fix actually **works!!!**

Allow me to break it down blow by blow


**1.**   ```
gksudo gedit /etc/pulse/default.pa

```    to modify pulse settings which were the problem on 11.04

[B]
2.[/B] Find line 45  where it says

```
load-module module-udev-detect

```

and replace with

```
load-module module-udev-detect tsched=0

```


then to restart pulse with new settings

```
pulseaudio -k

```


**and this my friends** fixes a huge problem that has plagued the VLC users   (Everyone ???) on Narwhal for a bunch of months

Better late than never and thank you :KS

---

### Post by ituxicity on 2011-09-19
Thanks for the link!

---

### Post by rakydude on 2011-09-20
Thanks a lot! It worked for me as well.. :)

---

### Post by Charger Fan on 2011-09-28
This fix worked perfectly. Thx's for the link and break down :)

---

### Post by SirPecanGum on 2011-10-09
Worked for me too in 11.10, thank you!

---

### Post by chuckyanutsup on 2011-10-20
Worked on 11.10 for me as well. Thank you kindly.

---

### Post by LanceRooke on 2011-10-22
Worked for me too.  Now can you tell me how to get it to run more smoothly?  Mine is a touch jerky.  I don;t think it's a DMA issue.

---

### Post by chuckyanutsup on 2011-10-23
mine has since started to gradually go out of sync as a vid plays. Pausing and unpausing gets it back in sync but I need to do this 5-10 times through a 45min vid. I've tried all kinds of different configurations in vlc. I've also noticed banshee crashing.

---

### Post by chuckyanutsup on 2011-10-23
[http://askubuntu.com/questions/66023/audio-and-video-are-out-of-sync](http://askubuntu.com/questions/66023/audio-and-video-are-out-of-sync) this helped me.

---

### Post by pixelatedragon on 2011-11-21
Using Ubuntu 11.04 and VLC 1.1.9 sound was going slowly out of sync.  The fix posted in the OP worked for me.  Perfect sync again. :D

---

### Post by beew on 2011-11-21
> **pixelatedragon said:**
> Using Ubuntu 11.04 and VLC 1.1.9 sound was going slowly out of sync.  The fix posted in the OP worked for me.  Perfect sync again. :D

Or you can install VLC 1.1.12 from getdeb. 

[http://www.ubuntuupdates.org/ppa/getdeb_apps?dist=natty](http://www.ubuntuupdates.org/ppa/getdeb_apps?dist=natty)

The problem is apparently fixed. :)

---

### Post by BenettFreeman on 2012-02-08
The real question is WHY OH WHY the makers of VLC and Ubuntu Natty Narwhal haven't fixed things so this problem doesn't exist when people use it 'out of the box'.

It is annoying little things like this that drive thousands of people away from Ubuntu and Linux. People want OS's that work out of the box and they are sick of messing around with driver issues and the command line.

When oh when will it end?

---

