---
title: "Help---capturing with kino!!!!"
date: 2007-12-26
forum: Multimedia &amp; Video
---

### Post by thekylehome@gmail.com on 2007-12-26
I am trying to capture footage from my canon hv10 to kino... but for some reason its like kino doesn't recognize my camcorder. Could it possibly be my iee1934 driver? or maybe it is because my camcorder is high def... I don't know! I have never captured before so I could just be doing something wrong!
I appreciate any help!

---

### Post by dannyboy79 on 2007-12-26
i can't say that I have experience with this camera but I can capture video from my cable box using a utility called test-mpeg or something like that. I found this about kino:

Before opening Kino turn the camera on and go to Playback (or VCR) mode. On your PC open a terminal window and type the command line 'kino'. Press Enter and Kino opens.

Are you doing what the above states? Also, have you tried dvgrab? WHat does the following command return?

lsmod | grep 1394

Also, you have to hit play on the camera for it to be captured by kino.

---

### Post by thekylehome@gmail.com on 2007-12-26
Here is what I get after Ismod | grep 1394:

video1394              22416  0 
raw1394                33072  0 
dv1394                 23568  0 
ohci1394               38984  2 video1394,dv1394
ieee1394              109528  5 video1394,sbp2,raw1394,dv1394,ohci1394

Okay, I did what you said and opened kino in the terminal, but that still did not solve the problem...
Yes, I have hit play to try capturing but it never works!
I'm trying dvgrab now... I'll see if that works!

Also, something to note is that in preferences under IEEE 1394 it says that "The IEEE 1394 Subsystem is not responding."

Hope I can get this figured out!

---

### Post by dannyboy79 on 2007-12-27
when you start up your machine, do you see any errors about ieee1394 or raw1394 or any other modules? what type of firewire card is it or is it built into the motherboard? I have read that some firewire cards are not so good compared to select few. I wish I could help more.

---

### Post by ecullerton on 2007-12-27
check the bottom of kino in the status bar, there might be something like read/write error to /proc/dev/raw1394.

If there is, change the write permission of that file.

You have to create a root password and become a superuser.  Then use chmod 777 to change the write permissions..

Ed

---

### Post by suj2007 on 2007-12-27
My self also facing same problem. The PCI IEEE1394 fireware card detected by the system but it is not detected by KINO. In the KINO under edit>preference> IEEE1394 there shown a error like this
> The RAW 1394 moudle must be loaded, and you must have read write access  in /dev/raw1394

Now how to rectify this error.

---

### Post by theacoustician on 2007-12-27
> **suj2007 said:**
> My self also facing same problem. The PCI IEEE1394 fireware card detected by the system but it is not detected by KINO. In the KINO under edit>preference> IEEE1394 there shown a error like this


Now how to rectify this error.

Change the permissions of the 1394 port.

sudo chmod 777 /dev/raw1394

That will only last as long as you're logged into your session.  To make it persistant, [http://www.kinodv.org/article/view/155/1/13/](http://www.kinodv.org/article/view/155/1/13/)  Go to the bottom of the page under Extras.

---

### Post by suj2007 on 2007-12-27
I have done accordingly. Lets see now what happen. Will post later the result.
thanks

---

### Post by thekylehome@gmail.com on 2007-12-27
> **dannyboy79 said:**
> when you start up your machine, do you see any errors about ieee1394 or raw1394 or any other modules? what type of firewire card is it or is it built into the motherboard? I have read that some firewire cards are not so good compared to select few. I wish I could help more.

no I do not see any errors when I start up... the ieee 1394 is built in to the motherboard...

---

### Post by thekylehome@gmail.com on 2007-12-27
> **ecullerton said:**
> check the bottom of kino in the status bar, there might be something like read/write error to /proc/dev/raw1394.

If there is, change the write permission of that file.

You have to create a root password and become a superuser.  Then use chmod 777 to change the write permissions..

Ed

Okay, you are right! I do see a read/write error in the status bar that says something about /dev/raw1394... so you say to change the write permission, but I don't know how! (I'm still really new to all of this)
Thanks!

---

### Post by dannyboy79 on 2007-12-27
sudo chmod 666 /dev/raw1394
should make it work. this will make it read/writable by all.

Here is a solution that should make it work even after you reboot your machine. just follow the link and copy paste what it says witin the link into a terminal session. that should do it.

[http://www.bxlug.be/en/articles/220](http://www.bxlug.be/en/articles/220)

---

### Post by thekylehome@gmail.com on 2007-12-27
Okay, I tried to do as the link said... I entered /etc/modules into the root terminal, but I just got Permission denied! I don't know what to do!!!!

---

### Post by thekylehome@gmail.com on 2007-12-27
> **dannyboy79 said:**
> sudo chmod 666 /dev/raw1394
should make it work. this will make it read/writable by all.

Here is a solution that should make it work even after you reboot your machine. just follow the link and copy paste what it says witin the link into a terminal session. that should do it.

[http://www.bxlug.be/en/articles/220](http://www.bxlug.be/en/articles/220)

Hey, I think I might be getting somewhere... I was able to get into gedit and changed it from 'GROUP="disk"' to 'GROUP="VIDEO"'

I'll post in a few minutes how things are... If I can finally capture my footage!

---

### Post by thekylehome@gmail.com on 2007-12-27
Oh my! I still cannot capture!!!!!!!! I am still getting the warning: raw1394 kernel module not loaded or failure to read/write /dev/raw1394! in the status bar... :confused:
Well I hope I'm not too far off!

---

### Post by ecullerton on 2007-12-27
I think this is how to do it.  Try...

$ sudo passwd root

<pick a password for your root account>

enter super user mode (root) now that you have a root account and password

$ su

<enter root password>

Change file permissions to read/write/execute for all:

$ chmod 777 /dev/raw1394

your done!

---

### Post by dannyboy79 on 2007-12-27
there's no need to setup a root password to do this but it doesn't hurt.

YOUR password should work when issuing commands with "sudo" Unless of course you're not the first account created and you have limited privelages.

so you just do what I said, 

sudo chmod 666 /dev/1394
when it asks for sudo password, enter your password that you setup when you installed ubuntu.

Also, there's no need to set /dev/1394 to 777, that will make it be able to run executables from that location. There's no need for this as it's a device location, not a place you store executables. 666 will be fine.

---

### Post by dannyboy79 on 2007-12-27
> **thekylehome@gmail.com said:**
> Oh my! I still cannot capture!!!!!!!! I am still getting the warning: raw1394 kernel module not loaded or failure to read/write /dev/raw1394! in the status bar... :confused:
Well I hope I'm not too far off!

if you changed something from group=disk to group=VIDEO, and you ahd opened it in gedit without sudo, then most likely it didn't save the file. Also, upper and lower case DO matter in linux. group=VIDEO is not the same as group=video. Look into these things and let us know.

---

### Post by ecullerton on 2007-12-27
Dannyboy79 is probably right...

I'm a little new to ubuntu and not quite used to not having the root privelages yet!

He's probably also correct that it isn't neccessary to include execute permissions for the file too!

This link explains the secret code of chmod...

[http://www.ss64.com/bash/chmod.html](http://www.ss64.com/bash/chmod.html)

good luck!

---

### Post by thekylehome@gmail.com on 2007-12-27
when I try: "sudo chmod 666 /dev/1394" it just says no such file or directry! also, I did open gedit with sudo, and I have checked multiple times and it did save it! Here is how it exactly looks... (GROUP="video")
Hope this helps!

---

### Post by ecullerton on 2007-12-27
$ sudo chmod 666 /dev/raw1394

---

### Post by thekylehome@gmail.com on 2007-12-27
> **ecullerton said:**
> $ sudo chmod 666 /dev/raw1394

when I put this into the terminal I get no such file or directory!

---

### Post by ecullerton on 2007-12-27
Double check the path name name that you see in the status bar at the bottom of Kino.

---

### Post by thekylehome@gmail.com on 2007-12-27
Yes, the path name is correct!

---

### Post by ecullerton on 2007-12-27
That's all I can help..  reached the limit of what I know..

good luck..

---

### Post by thekylehome@gmail.com on 2007-12-27
I appreciate all the help you gave me!

---

### Post by thekylehome@gmail.com on 2007-12-27
Well, I hate to totally give up on this... because my mac (yes, its really a mac) is in for repair right now, and I am trying to send a video to some of my friends, I was hoping that I could use Ubuntu... (of course if my mac were not in for repairs, I would most definitely use it [because I have Final Cut on it])
Oh, would dvgrab work if I can't get kino to? I went into the synaptic manager and searched for "dvgrab" and came up with something (I think it is the right thing? called 'dvgrab') and marked it for install, but then after I installed I could not find anywhere on the computer, but it says that it is installed!:lolflag:
Oh well, I just don't want my friends to miss out!!!

---

### Post by thekylehome@gmail.com on 2007-12-27
Another thought: I have Cinelerra installed (which was a big enough project itself) but I was wondering if there might be a chance that I could capture with that...

---

### Post by dannyboy79 on 2007-12-27
> **thekylehome@gmail.com said:**
> Another thought: I have Cinelerra installed (which was a big enough project itself) but I was wondering if there might be a chance that I could capture with that...

the link I provided shows how to create the node for /dev/raw1394 or whatever it was. Did you do that? Also, are you firewire modules being loaded?  This is what I get when I enter this command
lsmod | grep iee
ieee1394              299448  4 sbp2,raw1394,dv1394,ohci1394

---

### Post by thekylehome@gmail.com on 2007-12-28
Alright I'll try it... Thanks!

---

### Post by jjandrj6679 on 2007-12-30
Samsung VP-D372WH/ XEU  Mini-DV Camcorder wont recognize and neither will IEEE1394
Hi all, nice to be back in linux after a 6 month xp session,
I have lost the plot when it come to installing anything that isn't in either the  Add/Remove or Synaptic Packet manager. So If any of you would be prepared to do a step by step till I get re-aquainted with Ubuntu Terminal. 

So my problem is this, on 2 Xp pc's and 2 Xp laptops & 1 Ubuntu 7.10 Quad core pc I am unable to get the above camera to work.

In xp all I get is 61883 Class Bus Code 10 Device cannot start.

In Linux, well I cant even find the raw1394 files, Ive installed everything in Synaptic that I can see but I'm never able to find them & if I do get them to work. Like Kino

Samsung are useless beyond belief. Ill never buy another one of their products again.

So i'm prepared to start afresh.
So any help would be really appreciated and will get my partner off my back. 3 days we have been at it and still nothing.

To be brutally honest I left linux coz I couldnt get anything to work and it was no use to me really as I am a prolific Gamer and Overclocker. which linux isn't either or recognized as. And now here I am again begging for advice. 
Why is Linux so hard to get to grips with?
Wheres the plain and simple device manager? I found a Tree with devices but ??? 
Wheres the Task manager to see whats going on in my pc?

I hate Microsoft and every thing it stands for, but there is no alternative, I love linux but just cant get it to work.
Sorry for the rant.

---

### Post by ZxEfR on 2008-05-30
/dev/raw1394  only exists while your camera (or something else) is plugged in....so.....you can only chmod or chown  /dev/raw1394  when your camera is plugged in.

---

### Post by hodenkat on 2008-06-02
I solved the problem!


Plugged my camcorder into the port running Hardy, nothing happened.

Launched Kino and got an error on the IEEE1394 control tab saying something about raw1394 not loaded or no read write access.

Rebooted into Windows, plugged camcorder in, dialog box came up asking if I wanted to capture video using Windows Movie Maker...
so I did!

Kino is broken. IF YOU'RE LUCKY...one of the solutions listed will work for you. For me, ...not so much.
Just go to [https://launchpad.net/ubuntu/](https://launchpad.net/ubuntu/) and see for youself what a mess it is out there! Search for Kino.

---

### Post by ZxEfR on 2008-06-02
> **hodenkat said:**
> I solved the problem!


Plugged my camcorder into the port running Hardy, nothing happened.

Launched Kino and got an error on the IEEE1394 control tab saying something about raw1394 not loaded or no read write access.

Rebooted into Windows, plugged camcorder in, dialog box came up asking if I wanted to capture video using Windows Movie Maker...
so I did!

Kino is broken. IF YOU'RE LUCKY...one of the solutions listed will work for you. For me, ...not so much.
Just go to [https://launchpad.net/ubuntu/](https://launchpad.net/ubuntu/) and see for youself what a mess it is out there! Search for Kino.

Linux isn't for everybody!

I always say use what works best for you.

Kino is working great for me with very little effort....it's pretty basic compared to say premiere....but if basic is all I need the Kino is all I need.

If you wanna talk about something hard to get working that'd be an ATI X800 Pro video card!!! :O)

---

