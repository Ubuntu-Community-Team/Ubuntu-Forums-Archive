---
title: "Hauppauge HVR-2250 With Mythbuntu"
date: 2008-10-09
forum: Mythbuntu
---

### Post by paulin on 2008-10-09
Hello everyone.

Well I've finally decided to try and build my first PVR.  Anyway I'm still in the early research phase and I'm stuck on the Capture Card.  Anyway I found the Hauppauge HVR-2250 which seems like a good option.  However I've been searching around to see if it is supported by Linux and MythTV. 

Is anyone using it and how is it working?

Thanks
steve

---

### Post by paulin on 2008-10-09
I did find this

[http://www.gossamer-threads.com/lists/mythtv/users/343983](http://www.gossamer-threads.com/lists/mythtv/users/343983)

[INDENT]> Re: Need a Dual turner Capture card for myCable, WinTV-PVR 500 is discontinued* CONFIRMED * so what do you recommend	?

well I started the thread so I will close it, I finally ended up buying the hauppauge 2250, linux drivers are on their way ( it is even stated on hauppauge webpage ), basically this will be the replacement for the PVR 500, since they are getting a lot of heat from FCC to not sell any cards that can't decode digital, as I said on a post before, I think this card will serve 2 purposes, first the intended one and second I could help do a lot of beta testing ( or even dust my old C knowledge and work a bit on the driver ) 

Thank you all for your responses. 
Roberto. 
[/INDENT]

But I'm still not sure if this answer if it fully works or not.

Thoughts or anyone using it?
steve

---

### Post by agamotto on 2008-10-12
> **paulin said:**
> I did find this

[http://www.gossamer-threads.com/lists/mythtv/users/343983](http://www.gossamer-threads.com/lists/mythtv/users/343983)

[INDENT][/INDENT]

But I'm still not sure if this answer if it fully works or not.

Thoughts or anyone using it?
steve

No drivers as of today.  I contacted Hauppauge about this a month or two back, and they don't do any in-house linux support for any of their product.

---

### Post by pompeyjohn on 2008-10-24
according to the mythtv wiki work is preceding on getting this to work.

I have one of these cards, and I'll be using it for mythtv - until the, mediaportal it is...

---

### Post by pompeyjohn on 2008-11-04
anybody have an update on this?

---

### Post by smgendler on 2009-01-10
Development is on ice...which is very disappointing because it does look like the perfect tuner card.  See [http://article.gmane.org/gmane.linux.drivers.dvb/46504](http://article.gmane.org/gmane.linux.drivers.dvb/46504)

---

### Post by janascii on 2009-03-02
The development may be starting up again.  [http://www.steventoth.net/blog/hvr-2250/](http://www.steventoth.net/blog/hvr-2250/)  this is the blog of the developer that originally started the driver for the hvr-2250.  Apparently enough people have been bugging him to start on the 2250 that he is accepting donations to work on the project.  I'm keeping an eye on this before I buy the card.  Thought others would want to know.

---

### Post by LowSky on 2009-05-24
there seems to be a beta driver, but I have no idea how to install it, anyone care to help, [http://www.steventoth.net/blog/products/hvr-2250/](http://www.steventoth.net/blog/products/hvr-2250/)

I would live to get mythtv up and running.
I'm not really happy with Win7 media center

---

### Post by squidboy on 2009-05-24
Use this to understand how to setup and build the drivers-

[http://www.linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers)


then this is where you get the drivers 

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2250](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2250)

Tell me if you have any luck!!
Thanks

---

### Post by LowSky on 2009-05-25
Hello Mythbuntu users. Here is a new EDIT for 11.04 and 11.10.

I want to give credit to Sketchy's post: [#420]("http://ubuntuforums.org/showpost.php?p=10980475&postcount=420") I'm pretty sure this works

No one should need to upload any kernel drivers using 11.04+, only the firmware is needed.

I created a link on my server to host all of the firmware versions made a while back and will host as long as possible. I may move them to a public dropbox location later. I will update if needed.


Grab the firmware.
```
wget -c http://www.robotbeard.com/hvr-2250/HVR-2250_firmware.zip
```

Unzip the files
```
unzip HVR-2250_firmware.zip
```

copy the files to the /lib/firmware folder
```
sudo cp *fw /lib/firmware
```

Now check if the card can be located and what value the system has given it
```
dmesg | grep saa7164
```

on the 3rd or 4th line you should see what you are looking for it will look like this
```
[card=8,autodetected]
```
What this says is my HVR-2250 was detected at card 8, you may (probably will) get a diferent number. If your card says "unknown" choose the last option, usually 8.

Now we need to enter this card number into modprobe.d/options.conf file (I like to use gedit)
```
sudo gedit /etc/modprobe.d/options.conf
```

place this line of code in the file
```
options saa7164 card=x
```
*x = your card's number*

Reboot and check mythtv backend to see if it is listed correctly.


Here are the older instructions if still needed for users still using older distros.


EDIT: I have updated this tutorial for use with 10.04, here is a direct link:
[http://ubuntuforums.org/showpost.php?p=9219191&postcount=212]("http://ubuntuforums.org/showpost.php?p=9219191&postcount=212")


OK here is the awesome news, I got it working, but it took forever as I had to go through miles of web pages just to get this to work! I'll list my sources at the bottom if I missed something and you need to look through it for answers.

So I'm going to be nice and do some people some favours and post what I did to get it working in MythTV. 

**This driver is a BETA** and only works on digital side of the tuner, 

_NO ANALOGUE_ and _please be careful using_.

**_*I am not responsible for the outcome of you using my tutorial.*_** 

As I think my tutorial is rather crude and may miss an important step, please see the sources listed below. This is not for people new to Linux, as it might break (and it might, I've only had this running for about 30 minutes, so fingers crossed). 

If you really need to use this card for analogue and need a free OS, try the Windows 7 MCE, the free RC is currently available and should work until May 2010 before MS make you purchase a real copy and works completely with this tuner card.

Instructions for using HVR-2250 in MythTV (also works on HVR-2200 or any video capture card using the SAA7164 chipset)

EDIT:this has been updated for Mythbuntu 10.04 but will work for versions of *buntu 8.10 and higher

Enter this into your Terminal it is the code for the firmware and to install it
```

wget http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip
wget http://www.steventoth.net/linux/hvr22xx/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
wget http://www.steventoth.net/linux/hvr22xx/extract.sh
```
```

sh extract.sh
sudo cp *fw /lib/firmware

```
you need to install mercurial and build essential for the next steps
```
sudo apt-get install mercurial libncurses5-dev
```

then we need the driver using this command to fetch
```
hg clone http://kernellabs.com/hg/saa7164-stable/
```

now change to the directory
```
cd saa7164-stable
```

then run make
```
make CONFIG_DVB_FIREDTV:=n
```

that will take some time, go grab a drink and wait it out, when it completes run this command
```
sudo make install
```

wait for that to complete and reboot
from the command line
```
sudo reboot
```

Note that an application like TVtime will not work, TVtime only works on Analog signals, and so far this driver only gets the digital stuff working.

then install MythTV using whatever method you like, I personally went into synaptic and installed the frontend and backend and extra plug-ins

once installed and you set up your passwords go to
System> administration> MythTV backend setup

once there go to Capture Cards, Should be choice #2
choose new capture card, you will ave to do this step twice (this card has two tuners)
At card Type, pick DTB DTV
the first will be device number 0, 
repeats choosing capture card to add the second tuner
the second device will be #1 (Linux starts counting at 0, good thing to know, especially for hard drives)

then go to video sources, pick your options, will vary so mine will not work with yours most likely, so I dont want to post something I dont know)

then go to Input Connections, again you will have 0 and 1, configure both

then edit channels and directories as needed.

close let it fill database, for some reason mine keeps running in a loop, just exit after you see it finish the first or second time

now go to Applications > Sound & Video > MythTV Frontend

And you should be able to watch TV

I must say the Linux HTPC community is way too technical for most people, they need to make these things simpler, Windows 7 MCE is  10 times better at setting up these things.

[SIZE="3"]Notes[/SIZE]
I used Ubuntu 9.04, results should work for anyone using *buntu 8.10 releases, including Mythbuntu
I must say the configuring MythTV is exhausting so if I missed something or it doens't work please post better steps.
Special thanks to Steven over at [KernelLabs]("http://www.kernellabs.com/blog/?page_id=17"), the person who made the drivers.


**[SIZE="3"]Sources[/SIZE]**

[http://www.linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers)
[http://www.kernellabs.com/blog/?page_id=17](http://www.kernellabs.com/blog/?page_id=17)
[http://kernellabs.com/hg/saa7164-stable/](http://kernellabs.com/hg/saa7164-stable/)
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)
[http://www.linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers#Using_Mercurial](http://www.linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers#Using_Mercurial)
[http://www.steventoth.net/blog/products/hvr-2250/](http://www.steventoth.net/blog/products/hvr-2250/)
[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200)

---

### Post by epi 1:10,000 on 2009-05-28
Thx LowSky your tutorial works a treat!!!

I followed your instructions but a little modified 

I started with my old 9.04 x86_64 mythbuntu  JAvenard VDPAU patches install.
  I opened the frontend and deleted all upcoming recordings for the day and shut down the frontend.
  Then I stoped my backend w/ a
   
  sudo /etc/init.d/mythtv-backend stop
   
  command in the terminal and then proceeded to the beginning of your tutorial @
    [FONT=&quot]wget [http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip](http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip)[/FONT]
  [FONT=&quot]wget [http://www.steventoth.net/linux/hvr22xx/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip](http://www.steventoth.net/linux/hvr22xx/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip)[/FONT]
  [FONT=&quot]wget [http://www.steventoth.net/linux/hvr22xx/extract.sh](http://www.steventoth.net/linux/hvr22xx/extract.sh)[/FONT]
  
   
   and followed you instructions all the way to 
  sudo make install
   
   
  I rebooted and entered the backend setup and configured the 2 new tuners.   When I started the frontend and went to Live TV both the tuners on my new HVR-2250 were receiving a perfect OTA ATSC signal.  I will test their ability to record over the next few days
   
  On a side note the analog tuner on my HVR-1600 works better now.  There is no shuttering video on the first capture after startup and there seem to be less interference defects.  It might just be all in my head.....   placebo effect

---

### Post by LowSky on 2009-05-28
> **epi 1:10,000 said:**
> Thx LowSky your tutorial works a treat!!!

  On a side note the analog tuner on my HVR-1600 works better now.  There is no shuttering video on the first capture after startup and there seem to be less interference defects.  It might just be all in my head.....   placebo effect

Thanks for the feedback.

your other tuner probably works better because of a channel rescan or better placement of your antenna.

---

### Post by scotto on 2009-05-29
Yeah thanks for the great howto! I've been hoping someone would put it all together for the 2250.

So I tried this procedure on Knoppmyth R6 2nd preview release, which is now based on Arch Linux instead of Debian. I'm able to compile and install the driver, and I'm even able to set up the DTB card under mythtv, but I can't seem to pull any QAM channels off of Comcast, even tho my TV pulls them fine. Either of you have luck with QAM channels with this driver under Mythbuntu? I'd like to figure out if this is a driver issue or a Linux issue.

Thanks much.
--sa

---

### Post by LowSky on 2009-05-30
QAM works fine for me, I have Cablevision. One thing I noticed is some cable splitters can effect channel grabbing. If you can try to connect your cable as directly as you can. Once you have scanned for channels you can rehook up the splitter as needed. and all should work.

---

### Post by epi 1:10,000 on 2009-05-30
Update:

Recording 2 ota ATSC channels at the same time works w/o problems.

experimental design-
recording CBS's Latt late show and NBS's Late night w/ Jimmy fallon concurently on the HVR-2250.   Show were watched by scaned through the recordings to to make sure that there were no picture artifacts or audio sinc problems.
experiment repeated 3 times

equipment-
Mythbuntu 9.04 x86_64 w/ Avenard VDPAU patches    Nvidia 180.51 drivers
   [FONT=&quot]ANTEC|THREE HUNDRED BK RT [/FONT]
    [FONT=&quot]GIGABYTE GA-EP43-UD3L 775 P43 R [/FONT]
    [FONT=&quot]GIGABYTE GV-N95TD3-512I 9500GT [/FONT]
   [FONT=&quot]TV TUNER HAUPPAUGE|  HVR-2250 MC Model 1229 [/FONT]
       [FONT=&quot]HAUPPAUGE|1183 RT HVR-1600 [/FONT]
    [FONT=&quot]HAUPPAUGE 1196 HVR-1250 RT[/FONT]
    [FONT=&quot]PSU FSP|FSP350-60GLN(80) 350W[/FONT]
    [FONT=&quot]C2D E7400 2.8G [/FONT]
    [FONT=&quot]MEM 1Gx2|PNY MD2048KD2-800-X4 R [/FONT]
    [FONT=&quot]1.5T Seagate ST31500341AS  32M [/FONT]
    [FONT=&quot]KB ADESSO|WKB-3000UB RT [/FONT]
    [FONT=&quot]DVD ROM LITE-ON|iHDP118-08 18X RTL[/FONT]
    [FONT=&quot]DVD BURN LG|GH22NS30 22X SATA [/FONT]
      [FONT=&quot]Antenna RCA ANT3020X NA CAW 03 [/FONT]
  
 

Bug-
After a reboot the frontend fails to to see the 2 HVR-2250 tuners in Live TV.

Fix-
After every reboot you need to enter the backend settup and exit in order for the frontend to see the 2 HVR-2250 tuners

---

### Post by LowSky on 2009-05-30
make sure to add the mythtv backend to your starting applications at login

---

### Post by epi 1:10,000 on 2009-05-31
I assumed it was installed that way by default...   Am I mistaken?

---

### Post by LowSky on 2009-06-01
It think it is, but make sure, it cant hurt

---

### Post by epi 1:10,000 on 2009-06-13
The previous problem with the Frontend not detecting the HVR-2250 on strartup has bin fixed!!!
 
I rescaned after the digital transition and then one of my HVR-2250 tuners stoped locking onto channels. I restarted a couple times and rechecked my conections and the problem persisted.  I figured now is as good a time as any to update so I backed up the DB and updated then restarted and everything is fixed.  It seems if you install this card its best to follow LowSky's instructions fully and update or install MythTV after you instal the drivers/firmware.

---

### Post by theotherguy27 on 2009-06-17
Hello Im in the process of trying to get this to work using a fresh in stal of the Mythbuntu distro.
and i  Kept getting an unzip error while trying to process the part of code that follows

_s_[B]_h extract.sh_[I][U]
sudo cp *fw /lib/firmware[/U][/I][/B]

 well i figured out what the issue was, and im a newbie to Linux, and maybe this is something that is common knowledge, but apperently this distro doesnt have the unzip program complied into it so you need to use the following command
[I][B]
_sudo apt-get install unzip_[/B][/I]

Hope this Helps Other Newbies Out there!
Peace Out~
H/NK

---

### Post by vronp on 2009-08-16
Hi all,

I'd like to insert a NOOB question here.

I am building a MythTV front/back end box now and I play to use the 2250.

Here is my question.  In addition to getting OTA signals, can I pipe the output from a DirecTV HD receiver into this card?

thanks !

---

### Post by vronp on 2009-08-16
To expand on my post a bit.

To get OTA (digital obviously) AND HD DirecTV into Mythbuntu, do I need both the HVR-2250 AND the Hauppage HD-PVR ?

---

### Post by LowSky on 2009-08-17
The HVR-2250 only has one input for TV signals, so no it will not work with two different signals. So yes you will need another card to do what you are looking to do.

hope that helps.

---

### Post by vronp on 2009-08-17
> **LowSky said:**
> The HVR-2250 only has one input for TV signals, so no it will not work with two different signals. So yes you will need another card to do what you are looking to do.

hope that helps.

Well, I have since determined that the HD PVR is a "must have" for recording HD content from a DirecTV receiver.  So, I am going to order one of those.

So, let me change the question a bit.  What is the hot setup for just an OTA card?

thanks again,
Dave

---

### Post by LowSky on 2009-08-17
HVR-2250 ius a great card, it has basically 4 built in tuners, with the ability to record two shows at the same time., its only downside is it having one input so you cannot use two different sources. but the qualtiy is great, it has onboard encoding to save processor speed. So for OTA the card is worth it., just get a good antenna, as digital signals in some areas can be weak.

---

### Post by EternalStudent on 2009-08-17
[vronp]("http://ubuntuforums.org/member.php?u=150212"), I'm not very familiar with this (seen it, never done it). But I know it is possible to combine cable inputs into one line if you have the correct coaxial combiner. I did some research last year when setting up my outdoor OTA antenna.  Depending on your setup, a simple coax combiner may be able to work.   They also make channel restrictive combiners.  I don't have any idea if the 2250 can handle it though, since that may mean OTA digital and possibly cable analog.

---

### Post by xinix on 2009-08-20
Just dropping in a note to confirm that this card works as expected for me as well.  The hardest part was finding the mplex for some channels and then having to manually enter them into the db.

---

### Post by Tomlin on 2009-08-26
I'm getting:

"abort: error: Connection timed out"

when trying to connect to [http://kernellabs.com](http://kernellabs.com)

Is this site still active, or maybe just temporarily down?

Thanks

---

### Post by ktmom on 2009-08-28
> **Tomlin said:**
> I'm getting:

"abort: error: Connection timed out"

when trying to connect to [http://kernellabs.com](http://kernellabs.com)

Is this site still active, or maybe just temporarily down?

Thanks
FWIW - I have been on the [http://kernellabs.com](http://kernellabs.com) site today

---

### Post by thesponge on 2009-09-03
ok so I had it all working in mythbuntu 8.10.  Then I upgraded to 9.04 and the 2250 drivers are no longer listed in Hardware drivers and if I try and go through the steps again it errors out like the drivers are already installed.  I am fairly new to linux so kid gloves are appreciated.

---

### Post by LowSky on 2009-09-03
> **thesponge said:**
> ok so I had it all working in mythbuntu 8.10.  Then I upgraded to 9.04 and the 2250 drivers are no longer listed in Hardware drivers and if I try and go through the steps again it errors out like the drivers are already installed.  I am fairly new to linux so kid gloves are appreciated.

First things first, you will need to reinstall the drivers. the drivers are related to the kernel, so any kernel upgrade and they will break.

Second, for HTPC the best thing to do is to  not upgrade versions often. Best thing is to use the LTS or keep a current version for longer. But don't upgrade as things will break, and you will have to reload the drivers and modules all over again.

---

### Post by thesponge on 2009-09-03
Thanks, I was having trouble reloading the drivers.  Finally I just renamed the saa7164-stable to saa7164-stable_old and, followed the steps from the hg clone step and my tuners seem to be installed.  Having trouble connecting to the backend server database so I will have to research that now

---

### Post by williammanda on 2009-09-06
To troubleshoot the database issue:
1. Goto /home/william/.mythtv/mysql.txt and retreive the password.
2. Open mythbuntu control center and launch mythtv setup and edit the password.
Thanks

---

### Post by jgull8502 on 2009-09-20
I'm thinking of buying a card for my desktop so I can get MythTV set up on it. This card looks like a good option and it seems people have it working in linux. This may be a stupid question, but I'll ask it anyway. Right now, I have comcast cable (no HD stations) and just have the coaxial cable plugged into the back of the TV. I'm assuming this card will be able to handle the stream like my TV does.

---

### Post by jgull8502 on 2009-09-20
Check that. I just realized that this card is PCI-Express and I only have PCI. I guess that means that the HVR-1600 would be my best bet.

---

### Post by LowSky on 2009-09-21
Regardless of what model you have you will pick up cable, but not all your channels, only what is availible without a box. Even HD as Cable usually offers it for free over the line.

---

### Post by silverdulcet on 2009-09-21
> **thesponge said:**
> Thanks, I was having trouble reloading the drivers.  Finally I just renamed the saa7164-stable to saa7164-stable_old and, followed the steps from the hg clone step and my tuners seem to be installed.  Having trouble connecting to the backend server database so I will have to research that now

Just a follow-up. Instead of downloading the source from the mercurial repo with the hg clone command each time there is a kernal update, just follow the instructions detailed in this post:
[http://ubuntuforums.org/showpost.php?p=7749033&postcount=12]("http://ubuntuforums.org/showpost.php?p=7749033&postcount=12")

---

### Post by ktmom on 2009-09-21
> **jgull8502 said:**
> ***Right now, I have comcast cable (no HD stations)*** and just have the coaxial cable plugged into the back of the TV. I'm assuming this card will be able to handle the stream like my TV does.


This card only works for digital signals (HD) under linux at this time.  The drivers are being developed by Steven Toth independently of manufacturer support.  Your Comcast cable probably has a few (couple) HD signals but all of the analog will not work on linux as of yet.

[http://www.steventoth.net/blog/products/hvr-2250/]("http://www.steventoth.net/blog/products/hvr-2250/")

[http://www.kernellabs.com/blog/?p=721]("http://www.kernellabs.com/blog/?p=721")

---

### Post by bsntech on 2009-09-22
I think the HVR-1600 is probably the best card at the moment - especially for those that need two inputs.  the HVR-1600 has a separate analog and digital tuner so you can put two inputs into the unit.  As an example, you can run your coax from cable TV through the analog, and then use an antenna for OTA HD local stations.  Of course, you can always hook another coax from cable TV to the digital tuner as well.

Just seems like it gives more room for inputs.  The HVR-2250 is nice that it has two tuners and both will do analog or digital, but only one input for one connection.  However, the analog does not work with Linux - hence another reason to choose the HVR-1600 (at least at the present time).

---

### Post by juicedM3 on 2009-09-23
Has anybody tried the lastest drivers?  Just wondering.

Name: 22xxdrv_27223.zip
Size: 9.2 MB
Updated: 8/18/2009

[http://hauppauge.lightpath.net/software/drivers/22xxdrv_27223.zip](http://hauppauge.lightpath.net/software/drivers/22xxdrv_27223.zip)

The extract.sh script needs to be modified slightly, for example:

```

unzip -jo $IFILE 22xxdrv_27086/Driver89/HcwWiltF103.bin
unzip -jo $IFILE 22xx_drv_27223/Driver89/HcwWiltF103.bin

```

Thanks,
Justin

---

### Post by jgull8502 on 2009-09-23
Thanks for the input! Perhaps I'll go with the 1600 then!

---

### Post by Tomlin on 2009-09-24
I had no success with Mythbuntu 9.04 and the 2250. I went with 9.04 and the HVR-1250 - it works great BTW. I still would like the dual tuner option though. Are you guys saying if I drop back to 8.10 I should be good to go?

I may have a spare drive that I could swap with the currently installed (9.04) one.

Thanks.

---

### Post by ktmom on 2009-09-26
> **Tomlin said:**
> I had no success with Mythbuntu 9.04 and the 2250. I went with 9.04 and the HVR-1250 - it works great BTW. I still would like the dual tuner option though. Are you guys saying if I drop back to 8.10 I should be good to go?


I'm using Mythbuntu 9.04 with the 2250 (digital tuner only) with no problems.  Have you installed the drivers are directed in this thread?

---

### Post by Tomlin on 2009-09-28
> **ktmom said:**
> I'm using Mythbuntu 9.04 with the 2250 (digital tuner only) with no problems.  Have you installed the drivers are directed in this thread?

Yup...I did this:

```
Enter this into your Terminal it is the code for the firmware and to install it
Code:

wget http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip
wget http://www.steventoth.net/linux/hvr22xx/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
wget http://www.steventoth.net/linux/hvr22xx/extract.sh

Code:

sh extract.sh
sudo cp *fw /lib/firmware

you need to install mercurial and build essential for the next steps
Code:

sudo apt-get install mercurial build-essential

then we need the driver using this command to fetch
Code:

hg clone http://kernellabs.com/hg/saa7164-stable/

now change to the directory
Code:

cd saa7164-stable

then run make
Code:

make

that will take some time, go grab a drink and wait it out, when it completes run this command
Code:

sudo make install

wait for that to complete and reboot
from the command line
Code:

sudo reboot


```

Here's a snippet of the output from dmesg:

```
[   18.514907] nvidia: module license 'NVIDIA' taints kernel.
[   18.771436] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   18.771448] nvidia 0000:01:00.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   18.771455] nvidia 0000:01:00.0: setting latency timer to 64
[   18.772618] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[   18.947600] saa7164 driver loaded
[   18.947659] saa7164 0000:02:00.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   18.947664] saa7164[0]: Your board isn't known (yet) to the driver.
[   18.947665] saa7164[0]: Try to pick one of the existing card configs via
[   18.947666] saa7164[0]: card=<n> insmod option.  Updating to the latest
[   18.947668] saa7164[0]: version might help as well.
[   18.947671] saa7164[0]: Here are valid choices for the card=<n> insmod option:
[   18.947674] saa7164[0]:    card=0 -> Unknown
[   18.947676] saa7164[0]:    card=1 -> Generic Rev2
[   18.947677] saa7164[0]:    card=2 -> Generic Rev3
[   18.947679] saa7164[0]:    card=3 -> Hauppauge WinTV-HVR2250
[   18.947681] saa7164[0]:    card=4 -> Hauppauge WinTV-HVR2200
[   18.947683] saa7164[0]:    card=5 -> Hauppauge WinTV-HVR2200
[   18.947685] saa7164[0]:    card=6 -> Hauppauge WinTV-HVR2200
[   18.947687] saa7164[0]:    card=7 -> Hauppauge WinTV-HVR2250
[   18.947689] saa7164[0]:    card=8 -> Hauppauge WinTV-HVR2250
[   18.947984] CORE saa7164[0]: subsystem: 1131:0000, board: Unknown [card=0,autodetected]
[   18.947991] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xd3000000
[   18.947997] saa7164 0000:02:00.0: setting latency timer to 64
[   18.948031] saa7164_initdev() Unsupported board detected, registering without firmware

```

Anyone???

---

### Post by xinix on 2009-10-17
How can I revert to an older version of the driver?  I just updated after seeing that new patches were moved into the stable branch.  Unfortunately I cannot tune some channels that I could (and had recorded) shortly before doing the upgrade.

Thanks

Edit::Well, I went with the -dev version and the channels are tuning in again.

---

### Post by ScottBla on 2009-10-24
Trying to do this on the Mythbuntu 9.10 pre-release and getting a bunch of no such file errors trying to build. I imagine I'm just missing some package, but I haven't figured out whichone yet...Any suggestions?  Thanx!

  CC [M]  /home/scott/Downloads/hvr22xx/saa7164-stable/v4l/firedtv-1394.o
/home/scott/Downloads/hvr22xx/saa7164-stable/v4l/firedtv-1394.c:21:17: error: dma.h: No such file or directory
/home/scott/Downloads/hvr22xx/saa7164-stable/v4l/firedtv-1394.c:22:21: error: csr1212.h: No such file or directory
/home/scott/Downloads/hvr22xx/saa7164-stable/v4l/firedtv-1394.c:23:23: error: highlevel.h: No such file or directory
/home/scott/Downloads/hvr22xx/saa7164-stable/v4l/firedtv-1394.c:24:19: error: hosts.h: No such file or directory
/home/scott/Downloads/hvr22xx/saa7164-stable/v4l/firedtv-1394.c:25:22: error: ieee1394.h: No such file or directory
/home/scott/Downloads/hvr22xx/saa7164-stable/v4l/firedtv-1394.c:26:17: error: iso.h: No such file or directory
/home/scott/Downloads/hvr22xx/saa7164-stable/v4l/firedtv-1394.c:27:21: error: nodemgr.h: No such file or directory

---

### Post by ScottBla on 2009-10-24
So...I did some research to find that it looks like I need the full kernel source instead of just the linux-headers pkg.  So I grabbed the linux-source, extracted it and it still fails because its looking under the /lib/modules/2.6.31-14-generic/build dir (matching my `uname -r` value)...but that's a symlink pointing into the -headers dir tree.  I tried changing the symlink to point at my extracted linux-source, but then it starts looking for a .config file.  Copied the .config file over from the -headers dir, but there are a whole pile more errors trying to build.

It seems that I've got to be missing some basic trick here...I suppose I could do a full build, but I have a feeling that will end up being a whole can o worms I don't want to step into... :)

---

### Post by xinix on 2009-10-24
> **ScottBla said:**
> It seems that I've got to be missing some basic trick here...I suppose I could do a full build, but I have a feeling that will end up being a whole can o worms I don't want to step into... :)

I tried building this on Karmic.  it would not build using the headers, going with the linux-source route worked; sort of.  It built but would not load.  I forget the exact error but it is the same one you'd get if you try to load a module on the wrong kernel.  

look here for what seems like a working 'fix' to get it to build using the headers:
[http://ubuntuforums.org/showthread.php?t=1281341](http://ubuntuforums.org/showthread.php?t=1281341)

If you really want to use the linux-source you need to do more than copy the .config file.  You need to do these steps (as sudo/root) after you copy the .config file.
```
make oldconfig
make prepare0
make scripts
```

---

### Post by ScottBla on 2009-10-24
> **xinix said:**
> look here for what seems like a working 'fix' to get it to build using the headers:
[http://ubuntuforums.org/showthread.php?t=1281341](http://ubuntuforums.org/showthread.php?t=1281341)

Thanx!  That helps a lot!
> **xinix said:**
> 
If you really want to use the linux-source you need to do more than copy the .config file.  You need to do these steps (as sudo/root) after you copy the .config file....


Cool - I'll keep that in mind if end up needing to build it for some reason...

---

### Post by danbaatar on 2009-10-27
@ScottBla  The problem you're seeing is a result of the fact that repository you download in these instructions is a complete branch of the v4l tree and one of the drivers (the firedtv one) needs the full kernel source to compile.  You can disable the compilation of that driver by executing:

```
make CONFIG_DVB_FIREDTV:=n || return
```

instead of the first make command and then running the

```
make install
```

---

### Post by wartstew on 2009-10-31
Hi thanks for the tip (disabling the FireDTV device).

 I had been pursuing down the "installing the kernel source" route, and found that the original kernel would not accept the module do to the versioning restrictions it was configured with (how do you deal with this?).   This was leading me needing to compile a whole new kernel.  Since this MythTV box is not even mine (I am helping a friend and Linux Newbie with his and was working on his box remotely through an SSH tunnel), I did not want to get things too non-stock on this box which could likely confuse him later.

By the way, if you want to do the "menuconfig" instead of the "CONFIG_DVB_FIREDTV:=n" thing, then you have to install the ncurses developer package:

sudo apt-get install libncurses5-dev

before the ncurses based "menuconfig" will come up.

--------------

So now he is going to try to get the IR remote to the HVR to work, so he may be calling on me again if any instructions he might follow doesn't work out.

---

### Post by xinix on 2009-10-31
You don't need to use the full kernel source if you disable the "FireDTV" option.  If you just want the driver, I would use the headers way.  It works just fine.

---

### Post by sgreene59 on 2009-11-04
Using the latest sources the drivers fail to compile even with the FIREDTV module excluded.

[INDENT]/home/[account]/saa7164-stable-da41142e212f/v4l/dib7000p.h: In function 'dib7000p_pid_filter':
/home/[account]/saa7164-stable-da41142e212f/v4l/dib7000p.h:100: error: parameter name omitted
make[3]: *** [/home/sgreene/saa7164-stable-da41142e212f/v4l/cx23885-dvb.o] Error 1
make[2]: *** [_module_/home/sgreene/saa7164-stable-da41142e212f/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/[account]/saa7164-stable-da41142e212f/v4l'
make: *** [all] Error 2[/INDENT]

---

### Post by golond on 2009-11-05
Danbaatar resolved it for me with 'make CONFIG_DVB_FIREDTV:=n'.  Thanks a ton.

---

### Post by aflores3 on 2009-11-18
Even when I try with "make CONFIG_DVB_FIREDTV:=n" I get:```

make -C /2250/saa7164-stable/v4l 
make[1]: Entering directory `/2250/saa7164-stable/v4l'
Updating/Creating .config
Preparing to compile for kernel version 2.6.31
File not found: /lib/modules/2.6.31-14-server/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.
make[1]: Leaving directory `/2250/saa7164-stable/v4l'
make: *** [all] Error 2
bash: return: can only `return' from a function or sourced script
```

Not sure why its not making the .config file...

---

### Post by aflores3 on 2009-11-18
> Not sure why its not making the .config file...

Ok, I managed to work this out...

In case anyone is having the same problem, check out: [http://www.linuxtv.org/wiki/index.php/Talk:How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/Talk:How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

---

### Post by aflores3 on 2009-11-19
Ok, so I finally got the drivers installed. Thank you to all who have posted.

Now, when I go to mythtv-setup and try to add a card (type DVB DTV), it says: ```
Frontend ID: Could not get card info for card '/dev/dvb/adapter0/frontend0' Subtype: Unknown
```

dmesg|grep -i dvb spits out
```
[   20.080374] tveeprom 1-0000: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   20.884666] DVB: registering new adapter (saa7164)
[   20.884670] DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   24.388210] DVB: registering new adapter (saa7164)
[   24.388215] DVB: registering adapter 1 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...

```
Thanks in advance


**Edit**
Could this be because I'm trying to go through a set-top box from the cable company? I'm at work right now, so I can't test it... maybe I'll go home for lunch.

---

### Post by damies on 2009-11-22
Hi,

I get stuck at this point:

hg clone [http://kernellabs.com/hg/saa7164-stable/](http://kernellabs.com/hg/saa7164-stable/)

abort: error: Connection timed out

is there another site where we can get this file? any suggestions?

Dave.

---

### Post by Barry_IA on 2009-11-22
> **damies said:**
> Hi,

I get stuck at this point:

hg clone [http://kernellabs.com/hg/saa7164-stable/](http://kernellabs.com/hg/saa7164-stable/)

abort: error: Connection timed out

is there another site where we can get this file? any suggestions?

Dave.

Dave: 

Looks correct to me; perhaps there is a problem in an earlier step, which is why this one doesn't work?  I'm presuming your Internet connection works correctly -- try Firefox (can either access it via the Applications pull-down or typing Firefox in Terminal).

LowSky's instructions work, however I found I needed to start with "sudo apt-get install unzip" before the first 'wget' command.  Should get an error message at the "sh extract.sh" command line, though.

And should you get an error message with 'sudo apt-get install unzip' command, do the following:

1. Make sure your Internet connection is working.  (Test using Firefox to the outside world.)

2. "sudo apt-get check"  (Not sure if this command is necessary: I was following instructions in a book.)

3. "sudo apt-get --install-recommends update"  (Note the two hyphens before 'install'.)

Good Luck!

---

### Post by scotthew1 on 2009-12-17
gah help!!!
i've gotten the driver to install and myth tv seems to be recognizing the card correctly and everything. however, once i do a scan for channels (i'm not even sure if i'm doing the right scan even there're so many scan options) it comes up with a quite a few possible channels. however, when i go into the frontend, either nothing is really displayed, or the channel seems to tune, but it is shown in a very distorted double with no audio. am i doing something wrong? my tv itself can tune channels just fine and i know that they're all clear qam digital. it's very frustrating that i can't get to get the card to tune any channels!! also i have fios. can anyone please help?

---

### Post by JeepFreak on 2009-12-18
> **scotthew1 said:**
> gah help!!!
i've gotten the driver to install and myth tv seems to be recognizing the card correctly and everything. however, once i do a scan for channels (i'm not even sure if i'm doing the right scan even there're so many scan options) it comes up with a quite a few possible channels. however, when i go into the frontend, either nothing is really displayed, or the channel seems to tune, but it is shown in a very distorted double with no audio. am i doing something wrong? my tv itself can tune channels just fine and i know that they're all clear qam digital. it's very frustrating that i can't get to get the card to tune any channels!! also i have fios. can anyone please help?

I came her to post, basically, the exact same thing.  Although, I haven't tried to watch the few channels that came up in the scan yet.  I'm trying to find more info on the settings that should be used for the scan.  I'm in the US btw and using OTA digital cable from Comcast (in case it matters).

TIA!
Billy

---

### Post by JeepFreak on 2009-12-18
> **JeepFreak said:**
> I came her to post, basically, the exact same thing.  Although, I haven't tried to watch the few channels that came up in the scan yet.  I'm trying to find more info on the settings that should be used for the scan.  I'm in the US btw and using OTA digital cable from Comcast (in case it matters).

TIA!
Billy

OK, so now I get a great picture, but the scan only finds a dozen or so channels.  I've tried running it multiple times.  Of the channels that it does find, many are mislabeled in the guide (ie, it says FOX, but it's actually CSPAN.)  I'm pulling the listings from SchedulesDirect.  I've already created a new lineup with the channels that my TV gets straight from the cable outlet.  I'm going to mess with it again tonight, but if anybody knows what I should try, I'd appreciate it!

Thanks,
Billy

---

### Post by damies on 2009-12-19
The site was just down when i tried it. its working again now the same as it had for previous builds. 

perhaps a mirror site would be a good idea?

cheers,

Dave

---

### Post by LowSky on 2009-12-21
I've been away from this project for a while, and maybe I should revise it. If anyone wants to send me suggestions or notes on some issues I will look into them, maybe collaborate with me in testing and what not too. It will be a few weeks before a new guide is posted, because of the holiday's and then my weeklong vacation to Vegas. So I cant really start until maybe January 15 2010.

---

### Post by scotthew1 on 2009-12-22
hey thanks for the offer!

i ran through the entirety of your setup instructions except i had to use 
```
make CONFIG_DVB_FIREDTV:=n
```
instead of just "make"

my computer seems to recognize the drivers and the card itself. i was also able to set up the tuners in mythtv just as you said to. then i went to scan for channels and everything seemed to go well. i found a lot of "possible channels." i have verizon fios and i know that they do send some clear qam channels and i've gotten them all to tune just fine by plugging the cable directly into my tv. however, when i go to watch tv in mythtv. it only seems to be able to tune just a very few channels (i can get a few dozen on the tv by itself), and the few channels it does tune are sown on the tv twice (two stretched pictures on the screen). also there seems to be no sound, although i have recently found that mythtv itself hasn't been outputting any sound on my computer for a still unknown reason... if you could offer any suggestions i would be so grateful. getting everything to work has been very frustrating and so far the $100 purchase for this card has felt like a waste =[
also i'm using 9.10 if that is of any help to you.

thanks!
-scott

---

### Post by scotthew1 on 2009-12-23
and now i've discovered that the driver for the tuner must somehow be restricting mythtv from outputting audio... i'm not sure if this makes any sense at all, but i just earlier installed updates on my computer (which apparently required me to reinstall the driver for the tuner). so before the updates, i couldn't get mythtv to output any sound. after i did the update, i was able to play videos thru mythtv and the sound worked, i was so happy! but then i realized that i needed to reinstall the driver for the tuner. after i did that i can't get mythtv to output any sound....
i really don't understand why it would be the drivers for the card but that seems to be the case...

---

### Post by LowSky on 2009-12-23
I doubt MYthTV is restricting the sounds, your case might be a simple one all you might have to do is change the audio source. It cold be something simple like going to the sound preferences and checking the hardware tab and making sure all devices are functioning. 

I would also check to see if pulse audio is working correctly
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

and if you have intel chipset take a look at this 
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by scotthew1 on 2009-12-26
no its nothing with the system itself i don't think. outside of mythtv all my audio works just fine. its only mythtv itself that doesn't seem to produce any sound. and i think it is because of something in this driver... i have no idea why that would be but i'm trying to figure out how to uninstall the driver to see if this is really the case. how would i uninstall the driver?

---

### Post by nPoc on 2009-12-30
So I've been following this thread, and I wanted to make sure everyone was aware that the drivers from Steven Toth have been merged into the linuxtv repositories.

I'm not sure how much active maintenance is going on at the kernellabs site, but I'm more concerned about bug fixes for my other cards.

So I'm going to try building off the repository available at linuxtv.  Wish me luck.  If I remember, I'll post back here on the results.  Also did someone end up trying the new firmware *(I might have missed a post, but I'm not sure).

[http://www.linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers)

---

### Post by nPoc on 2009-12-30
So I tried building off the linuxtv.org repo on 9.10, and was able to successfully get my 2250 up and running unfortunately my wintv 250 and fusionhdtv 5 stopped working.  

Dec 30 13:19:50 bonus kernel: [30982.637274] cx88xx: disagrees about version of symbol v4l2_i2c_new_subdev_cfg
Dec 30 13:19:50 bonus kernel: [30982.637285] cx88xx: Unknown symbol v4l2_i2c_new_subdev_cfg
.... and it goes on.

the ivtv driver has a similar issue.
Dec 30 04:43:39 bonus kernel: [   11.669010] ivtv: Unknown symbol ir_codes_hauppauge_new_table
Dec 30 04:43:39 bonus kernel: [   11.671008] ivtv: Unknown symbol ir_codes_rc5_tv_table


Back to the drawing board.  I'm going to try installing only the saa7164 driver, and try to follow the dependency tree on down. 

Any ideas would be greatly appreciated.

---

### Post by YogiPaolo on 2010-01-02
This sounds really great. thanks everyone for all the information.

I'm building a little HTPC right now. All the parts are on order from NewEgg save for the tuner card which I cannot decide on. I found this thread and I'm leaning towards the 2250.

This box will also double as a file server. The specs should have enough juice. Here are the details for your purusal:
```

Mushkin Enhanced Blackline 2GB 240-Pin DDR2 SDRAM DDR2 1066

3 for a raid 5 SAMSUNG EcoGreen F2 HD103SI 1TB 5400 RPM SATA 3.0Gb/s 3.5"

ASUS M3A78-CM AM2+/AM2 AMD 780V Micro ATX AMD Motherboard 

CORSAIR CMPSU-400CX 400W ATX12V V2.2 80 PLUS Certified Power Supply

AMD Phenom 9150E 1.8GHz Socket AM2+ 65W Quad-Core Processor 

Thermaltake LANBOX Lite VF6000BWS Black SECC Japanese steel Gaming Cube Computer Case 
```

I believe that I'll take the leap with the 2250. 

Be sure to look back here for my progress...

---

### Post by YogiPaolo on 2010-01-11
> **scotthew1 said:**
> hey thanks for the offer!

i ran through the entirety of your setup instructions except i had to use 
```
make CONFIG_DVB_FIREDTV:=n
```
instead of just "make"

my computer seems to recognize the drivers and the card itself. i was also able to set up the tuners in mythtv just as you said to. then i went to scan for channels and everything seemed to go well. i found a lot of "possible channels." i have verizon fios and i know that they do send some clear qam channels and i've gotten them all to tune just fine by plugging the cable directly into my tv. however, when i go to watch tv in mythtv. it only seems to be able to tune just a very few channels (i can get a few dozen on the tv by itself), and the few channels it does tune are sown on the tv twice (two stretched pictures on the screen). also there seems to be no sound, although i have recently found that mythtv itself hasn't been outputting any sound on my computer for a still unknown reason... if you could offer any suggestions i would be so grateful. getting everything to work has been very frustrating and so far the $100 purchase for this card has felt like a waste =[
also i'm using 9.10 if that is of any help to you.

thanks!
-scott

This seems to be working for me, but it's still compiling. Once again I'm grateful to everyone for help. I'd like to contribute back by describing my project. I've taken notes this time and would like to share. Would it be wise to start a new thread or might someone suggest a thread in the way of mythbox building ?

AH! it seems to have compiled sucessfully!!!

more later...

---

### Post by AJBalettie on 2010-01-13
Ok, so I am trying to get this card to work with MythTV in Karmic (9.10) by running the scripts detailed on the first page.  Is there something else I'm missing?

TIA

-Andrew :popcorn:

---

### Post by YogiPaolo on 2010-01-13
> **AJBalettie said:**
> Ok, so I am trying to get this card to work with MythTV in Karmic (9.10) by running the scripts detailed on the first page.  Is there something else I'm missing?

TIA

-Andrew :popcorn:

I'm not sure, but I'd be happy to help. I got the card working, but there are a few wrinkles that I'm checking back here to try solving.

That's how I found your post.

Could you be more specific?
When you restart and run lsmod, do you see the mmodules saa7164?
Did the scripts build with no errors?

Feed us more info and we can help. I'll be posting later...

---

### Post by silverdulcet on 2010-01-14
> **YogiPaolo said:**
> I'm not sure, but I'd be happy to help. I got the card working, but there are a few wrinkles that I'm checking back here to try solving.

That's how I found your post.

Could you be more specific?
When you restart and run lsmod, do you see the mmodules saa7164?
Did the scripts build with no errors?

Feed us more info and we can help. I'll be posting later...

You can also issue this command at a Terminal:
```
dmesg | grep saa
```

If the driver compiled correctly and you have the firmware in the correct place it should return something similar to this:
```
[   12.552294] saa7164 driver loaded
[   12.552328] saa7164 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.552676] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   12.552681] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfd400000
[   12.552685] saa7164 0000:02:00.0: setting latency timer to 64
[   12.712533] saa7164_downloadfirmware() no first image
[   12.712571] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[   12.712574] saa7164 0000:02:00.0: firmware: requesting v4l-saa7164-1.0.3.fw
[   13.739734] saa7164_downloadfirmware() firmware read 3978608 bytes.
[   13.739737] saa7164_downloadfirmware() firmware loaded.
[   13.739743] saa7164_downloadfirmware() SecBootLoader.FileSize = 3978608
[   13.739749] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   13.739750] saa7164_downloadfirmware() BSLSize = 0x0
[   13.739751] saa7164_downloadfirmware() Reserved = 0x0
[   13.739752] saa7164_downloadfirmware() Version = 0x51cc1
[   20.596027] saa7164_downloadimage() Image downloaded, booting...
[   20.700026] saa7164_downloadimage() Image booted successfully.
[   22.744026] saa7164_downloadimage() Image downloaded, booting...
[   24.408017] saa7164_downloadimage() Image booted successfully.
[   24.445211] saa7164[0]: Hauppauge eeprom: model=88061
[   25.048429] DVB: registering new adapter (saa7164)
[   27.930326] DVB: registering new adapter (saa7164)

```

Have you configured the tuner(s) in mythtv-setup?

---

### Post by kpholmes on 2010-01-14
i was just looking at cards for mythTV and i cant believe i stumbled upon this thread cause i was thinking about getting the 2250. knowing what you know now, would you recommend this card or maybe another one? thanks

---

### Post by AJBalettie on 2010-01-14
> **silverdulcet said:**
> You can also issue this command at a Terminal:
```
dmesg | grep saa
```

this didn't do anything in my terminal :(

also, i can't configure the card in the mythtv backend because they don't show up as devices, which is why i don't think i did the driver correctly.

---

### Post by silverdulcet on 2010-01-14
> **kpholmes said:**
> i was just looking at cards for mythTV and i cant believe i stumbled upon this thread cause i was thinking about getting the 2250. knowing what you know now, would you recommend this card or maybe another one? thanks

I'd absolutely recommend this card. 
Pros: 
* 2 tuners with internal splitter, record 2 ATSC shows or 2 cable QAM shows.

* Multirec works, meaning you can record multiple shows that are on the same multiplex (eg, PBS 2.1, 2.2, 2.3) and only use one of the tuners.

* PCIE card, includes low profile bracket as well.

Cons: 
* Internal PCIE card, if you don't have room in your case or lack a PCIE slot, perhaps a usb tuner or HDHomerun (network tuner) would be better for you.

* There is no support for in the driver for the analog encoder yet.

* The driver does not support the IR remote chip that is on this card, so you'll need either a USB IR receiver, IR module included on your case, or the IR from another tuner.

* Not really a con, but if you don't need 2 tuners, there are cheaper single tuner cards available as well. 

Just an update on the drivers, as of Sept. 17 2009 they are included in the linuxtv.org v4l-dvb mercurial repo, see [http://www.kernellabs.com/blog/?p=721]("http://www.kernellabs.com/blog/?p=721")

This means if you have other cards that are not supported by the current release of mythbuntu you can compile the updated drivers all from one place.

---

### Post by silverdulcet on 2010-01-14
> **AJBalettie said:**
> this didn't do anything in my terminal :(

also, i can't configure the card in the mythtv backend because they don't show up as devices, which is why i don't think i did the driver correctly.

Ok, when you are on this step:
now change to the directory
```
cd saa7164-stable

```
then run make
```
make
```

Can you post the output of this command? Perhaps the last ~20 or so lines. Look for any "Error" messages.

---

### Post by AJBalettie on 2010-01-14
```

/home/andrew/saa7164-stable/v4l/firedtv-1394.c: In function 'fcp_request':
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:167: error: dereferencing pointer to incomplete type
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:168: error: dereferencing pointer to incomplete type
/home/andrew/saa7164-stable/v4l/firedtv-1394.c: In function 'node_probe':
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:182: error: dereferencing pointer to incomplete type
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:182: warning: type defaults to 'int' in declaration of '__mptr'
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:182: warning: initialization from incompatible pointer type
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:182: error: invalid use of undefined type 'struct unit_directory'
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:187: error: dereferencing pointer to incomplete type
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:187: error: 'quadlet_t' undeclared (first use in this function)
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:188: error: implicit declaration of function 'CSR1212_TEXTUAL_DESCRIPTOR_LEAF_DATA'
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:188: error: dereferencing pointer to incomplete type
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:188: warning: assignment makes pointer from integer without a cast
/home/andrew/saa7164-stable/v4l/firedtv-1394.c: At top level:
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:243: warning: 'struct unit_directory' declared inside parameter list
/home/andrew/saa7164-stable/v4l/firedtv-1394.c: In function 'node_update':
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:245: error: dereferencing pointer to incomplete type
/home/andrew/saa7164-stable/v4l/firedtv-1394.c: At top level:
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:253: error: variable 'fdtv_driver' has initializer but incomplete type
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:254: error: unknown field 'name' specified in initializer
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:254: warning: excess elements in struct initializer
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:254: warning: (near initialization for 'fdtv_driver')
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:255: error: unknown field 'update' specified in initializer
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:255: warning: excess elements in struct initializer
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:255: warning: (near initialization for 'fdtv_driver')
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:256: error: unknown field 'driver' specified in initializer
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:256: error: extra brace group at end of initializer
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:256: error: (near initialization for 'fdtv_driver')
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:259: warning: excess elements in struct initializer
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:259: warning: (near initialization for 'fdtv_driver')
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:262: error: variable 'fdtv_highlevel' has initializer but incomplete type
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:263: error: unknown field 'name' specified in initializer
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:263: warning: excess elements in struct initializer
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:263: warning: (near initialization for 'fdtv_highlevel')
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:264: error: unknown field 'fcp_request' specified in initializer
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:264: warning: excess elements in struct initializer
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:264: warning: (near initialization for 'fdtv_highlevel')
/home/andrew/saa7164-stable/v4l/firedtv-1394.c: In function 'fdtv_1394_init':
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:271: error: implicit declaration of function 'hpsb_register_highlevel'
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:272: error: invalid use of undefined type 'struct hpsb_protocol_driver'
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:273: error: implicit declaration of function 'hpsb_register_protocol'
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:276: error: implicit declaration of function 'hpsb_unregister_highlevel'
/home/andrew/saa7164-stable/v4l/firedtv-1394.c: In function 'fdtv_1394_exit':
/home/andrew/saa7164-stable/v4l/firedtv-1394.c:283: error: implicit declaration of function 'hpsb_unregister_protocol'
make[3]: *** [/home/andrew/saa7164-stable/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/andrew/saa7164-stable/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/andrew/saa7164-stable/v4l'
make: *** [all] Error 2

```

---

### Post by silverdulcet on 2010-01-14
> **AJBalettie said:**
> ```

make[3]: *** [/home/andrew/saa7164-stable/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/andrew/saa7164-stable/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/andrew/saa7164-stable/v4l'
make: *** [all] Error 2

```

See post #65:

i ran through the entirety of your setup instructions except i had to use 
```
make CONFIG_DVB_FIREDTV:=n
```
instead of just "make"

Try it with that command and see if it compiles correctly. Alternatively you could use the linuxtv.org mercurial repository instead. See this Howto: [http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers]("http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers")

It just pulls the drivers from a different place and you have to change to a different directory:
```
cd v4l-dvb
```
then 
```
make
```
or if you get that firedtv error
```
make CONFIG_DVB_FIREDTV:=n
```
as above.

finally
```
sudo make install
```

Then reboot and try that dmesg command once more to see if the drivers were successfuly loaded.

---

### Post by AJBalettie on 2010-01-14
forgive me for being noob-ish, but when am I entering these lines?

---

### Post by silverdulcet on 2010-01-14
> **AJBalettie said:**
> forgive me for being noob-ish, but when am I entering these lines?

To use the saa7164-stable source you've already downloaded just issue the "make" command as before. Instead of using just the "make" command we are telling it to not build support for the firedtv module which is causing those errors that you posted above.

Ok, when you are on this step:
now change to the source directory

```
cd saa7164-stable
```

then run make, with the switch to not build the firedtv module

```
make CONFIG_DVB_FIREDTV:=n
```

It will start building the modules, and when it completes you should not see any of those "Error" lines at the end. If there are "Error" lines please post them here. If not then proceed to with the install step:

```
sudo make install
```

Once the modules are installed you can now reboot, and check to see if the driver and firmware loaded correctly with the command:

```
dmesg | grep saa
```

See my previous post that gives you an example of what the driver and firmware loading looks like.

---

### Post by YogiPaolo on 2010-01-14
I'm having a new and interesting problem with the 2250 card.

I can record TV and watch live TV while recording. Things are going along smoothly and then without warning, I can't tune any channels. It's as if the card does not exist anymore. The tedius process of removing and adding the tuners in mythbackend solves the problem for a while. The problem returns repeatedly for three days now.

I did some digging in dmesg and found this interesting tidbit:

 > IRQ 16/saa7164[0]: IRQF_DISABLED is not guaranteed on shared IRQs

I am assuming that my 2.6.31-17-generic kernel is compiled with IRQF_DISABLED set to Y.

If this is the case, then why?
How can I check what options my kernel is compiled with?
I tried to download the source as per the Kernel compile wiki:[https://help.ubuntu.com/community/Kernel/Compile#AltBuildMethod](https://help.ubuntu.com/community/Kernel/Compile#AltBuildMethod)

But apt-get says it's not available. 

How do I check the config of the current kernel?

I remember from my masochistic days running Gentoo the basics of how to compile. I'm looking into compiling another kernel...

---

### Post by AJBalettie on 2010-01-15
I can not thank you guys enough for the help!  My mythtv box now recognizes that there is a tv tuner in it!

now, when i scan for channels in the backend, it doesn't pick any up :-(

---

### Post by AJBalettie on 2010-01-15
crap...i just read that this driver supports digital broadcast only...so if i have basic cable, i'm screwed right?

---

### Post by JeepFreak on 2010-01-16
> **AJBalettie said:**
> crap...i just read that this driver supports digital broadcast only...so if i have basic cable, i'm screwed right?

You should get some channels in HD.  I have Comcast basic cable and I get 8 to 12 channels I think.

On to my own somewhat related question...
Programs that are "broadcast in high definition" on "standard definition" channels - can these programs be viewed with the HVR-2250?  I'm currently viewing them on my PVR-250 because the channel didn't come up on the channel scan and the quality is clearly _not_ HD.  Should I be doing something different?

Thanks a bunch!
Billy

---

### Post by jeremycobert on 2010-01-17
> **AJBalettie said:**
> crap...i just read that this driver supports digital broadcast only...so if i have basic cable, i'm screwed right?

if you have an hdtv with a built in tuner card, you can try to scan everything and see if it picks up some unencrypted QAM channels. i get 7 of them on my basic cable. if you do get some to show up, then just setup the card and scan for QAM 256 and see if your mythbox finds any channels. if you do get this far, listen to mythtvcast epidsode 3 (i think) it explains how to re align the QAM channels to match your guide. [http://mythtvcast.com/](http://mythtvcast.com/)

---

### Post by kpholmes on 2010-01-19
so i purchased the 2250 and i have it in a frontEnd/backEnd config running mythbuntu, but i have ran into a problem. i followed the thread and was able to get the capture card drivers installed and mythTV recognizes the card just fine, but when i go to watch live tv, it shows a black screen with the program info from schedules direct; and tells me my signal strength is 0%, and then closes with a pop up saying "error opening jump program file"

i've done a full QAM-256, and 64 scan, but cant seem to get any channels.

i have time warner cable and live in southern california if that helps, but im just trying to pick up the channels from 3 to 90. it would be greatly appreciated if someone could point me in the right direction on fixing this or if they need more info just let me know. 

thanks

---

### Post by LowSky on 2010-01-19
kpholmes did you scan for channels?

---

### Post by kpholmes on 2010-01-19
ya. I scanned for QAM-64 and 256.  Didn't find anything.  I'm going to try 128 and see if I get anything.

---

### Post by kpholmes on 2010-01-19
During the scans it can find encrypted channels but it also gets a fair amount of "time outs" and "possible channels"

---

### Post by cedyathome on 2010-01-19
Does the Scan command give you any channels? See this link  [http://parker1.co.uk/mythtv_dvb.php](http://parker1.co.uk/mythtv_dvb.php)   Also, increase the timeouts in mythtv. It is in the capture card menu. I found that worked for me with a Pinnacle HD PCI (800i) card.

---

### Post by LowSky on 2010-01-19
Check your connections, if you have cable splitter installed it can effect quality. I have seen the same problem occur when channel scanning. The purer the signal the better reception for picking up the channel. Note: once you have tuned the channels reinstall the splitter, it may not be an issue once the Tuner has the correct frequencies.

read this it might help if you still have problems
[http://www.mythtv.org/wiki/Working_QAM_cable_layout](http://www.mythtv.org/wiki/Working_QAM_cable_layout)

---

### Post by kpholmes on 2010-01-20
well turns out its not going to work.

>  Digital Cable is typically encrypted, or encoded so that you need a cable box or CableCARD to view it. If you have 500 digital cable channels that you receive with a cable box, then the majority of these channels will be encrypted. A Clear QAM tuner cannot receive encrypted digital cable; it cannot receive the majority of your digital cable channels. 
Therefore, you cannot use a cable box via Clear QAM, and you cannot receive most of your channels via Clear QAM. 

thats what time warner told me when i sent them an email, i should of asked first :(

i was at a linux users group and they mentioned something about a card that my cable provider has to supply for this kind of situation where a customer wants a DVR but doesn't want to rent the cable providers hardware.

well im going to be off searching around why i can watch cable on my tv and not my computer. if i find anything useful ill be sure to post it, or if anyone has any ideas or info that might help im all ears.

thanks

---

### Post by LowSky on 2010-01-20
kpholmes, I dont have TW but you should get a few channels in HD without a cable box, usually the local broadcastors or their affiliates like NBC, CBS, FOX, and ABC.

if your using a cable box that goes into the PC tuner, then you might have issues. because using a cable box with coax is actually a analog signal and wont work with this tuner card.

---

### Post by cedyathome on 2010-01-20
Make sure the cable is connected to the top connector. I wasted a couple of hours because my cable was connected to the FM-input.  Now, I'm struggling with jerky live-tv & horrible video quality.

---

### Post by LowSky on 2010-01-20
> **cedyathome said:**
> Make sure the cable is connected to the top connector. I wasted a couple of hours because my cable was connected to the FM-input.  Now, I'm struggling with jerky live-tv & horrible video quality.

Good thing to bring up.

---

### Post by kpholmes on 2010-01-20
that makes sense since there isnt an analog driver for this card. haha    : /

thanks for all the help. im going to try use a set top box connected to myth tv via firewire and see if i get any luck.

---

### Post by kpholmes on 2010-01-20
> **cedyathome said:**
> Make sure the cable is connected to the top connector. I wasted a couple of hours because my cable was connected to the FM-input. 

haha ya i remembered to double check that. i wish that was the problem though:D

---

### Post by lokness on 2010-01-20
im having the same problem... but i have a time warner STB.  i have a coax from the STB to the pvr2250 (the top coax) and im not getting any channels.

i am going to try and increase the max time outs and see what that does for me

---

### Post by lpnb on 2010-01-21
Hi guys, don't know if anyone is subscribed to this tread but I really need some help.... maybe I am getting old but I have been working with linux for a few years now and built many Mythtv in various distros but this is driving me crazy....I normally try to figure things out but I am at the end of my rope on this one.

HVR-2250, mythbuntu 9.10, athon x64 5000+ ...the install went smoothly  with the 64 bit version of mythbuntu:

```
dmesg | grep saa 
```
or
```
dmesg | grep dvb
```
or
```
dmesg | grep hvr
```

yield nothing . so that's one thing, but should that stop the install of the driver.

I have followed a few of the install howto's including the one that I think is in this thread.

I had to install unzip as the first hurdle, and I also got an error  after running 

```
make menuconfig
```

I got an error :

```
 *** Unable to find the ncurses libraries or the
 *** required header files.
 *** 'make menuconfig' requires the ncurses libraries.
 *** 
 *** Install ncurses (ncurses-devel) and try again.
 *** 
make[3]: *** [scripts/kconfig/dochecklxdialog] Error 1
make[2]: *** [v4l-mconf] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: *** [/lib/modules/2.6.31-14-generic/build/scripts/kconfig/mconf] Error 2
make[1]: Leaving directory `/home/lpnb/Downloads/saa7164-stable/v4l'
make: *** [menuconfig] Error 2

```

Now, I suspect this is related the the error I get when I run 'make'.

I have tried install ncurses devel but this does not fix the problem.

one of the howto's misses the ```
make menuconfig
``` step which I don't understand.

I tried both the stable and the Devel releases no dice either way.

O.K. so there is two issues one is that I can't see it at all with dmesg and the other is the driver install errors. I had this driver installed on exactly the same system (sans new sata DVD drive) and it worked....I rebuilt because it was very unstable due to the massive amount customisation and it was broken. So I thought I would upgrade in the hope it would be more stable and see more of my hardware. 

FYI,
the system also has a biostar TF560+ mobo, 750GB Green and quiet drive, nvidia Gigabyte 9600GT Silent graphics, 3 Noctua fans tuned to an acceptable speed for noise, MX-810 "universal remote control" (very nice but pricey) 100% custom made black anodised case. When I say custom I mean custom....even the HDD and CD brackets are hand made.... I started this damn thing 4 years ago and it has never been 100% with remote and tuner card working correctly. I have the remote working now....just need this nice tuner working.

thanks for listening!
Lachlan

---

### Post by LowSky on 2010-01-21
you would you need make menuconfig?

your tuner should get up and running using my tutorial on page 1

---

### Post by lpnb on 2010-01-21
Thankyou very much for the reply.

yes I followed that one, it is much the same as one I followed on a wiki site .....can't remember where that was but it was the same Except for the make menuconfig that I mentioned I have tried both..


> **LowSky said:**
> you would you need make menuconfig?

your tuner should get up and running using my tutorial on page 1

---

### Post by lpnb on 2010-01-21
O.K. so I tried this little nugget of information:

[http://www.mail-archive.com/ubuntu-devel-discuss@lists.ubuntu.com/msg09422.html](http://www.mail-archive.com/ubuntu-devel-discuss@lists.ubuntu.com/msg09422.html)

which basically says:

> For anyone else having this problem I was able to get some resolution from
the guys in #v4l on IRC.

Basically the Firedtv driver needs the entire kernel source to compile - not
just the headers. They said they are aware of the problem and will address
it at some point.

So a quick work around is to disable the firedtv driver by modifying the
./v4l/.config file and changing '=m' to '=n' on the firedtv line.

The longer solution is to install the kernel source and then modify the
makefile configuration options to use that instead of the headers (it will
default to using the headers still if not configured correctly). If you're
not using firedtv, this is not worth it.

Thanks all who helped!

Now that was for v4l which I actually also tried to install but still could not see the card.

anyhow I found the same .config file in the /saa7164-stable/v4l directory and changed the line mentioned above....I did new 

```
make 
sudo make install
```

seemed to install now without any errors this time and rebooted.

dmesg | grep saa still does not yield anything. :-(

---

### Post by lpnb on 2010-01-21
O.K. so I also checked that the fw files were there also:

l```
test@mythbox:~/Downloads/saa7164-stable$ cd /lib/firmware/
test@mythbox:/lib/firmware$ ls | grep 7164
[B]v4l-saa7164-1.0.2.fw
v4l-saa7164-1.0.3.fw[/B]
test@mythbox:/lib/firmware$ 
```

I also notice the the 2.6.31-14 headers were installed so I removed them....as when the make was running I noticed that is says that it is using them.....I'll try again.

---

### Post by lpnb on 2010-01-21
O.K. looks like it installed but still not listed in dmesg

but

```
test@mythbox:/lib/modules/2.6.31-17-generic/kernel/drivers/media/video/saa7164$ ls
saa7164.ko
test@mythbox:/lib/modules/2.6.31-17-generic/kernel/drivers/media/video/saa7164$ 


```

```

~$ modprobe saa7164
FATAL: Module saa7164 not found.

```

---

### Post by lpnb on 2010-01-21
more:

```
$ lspci |grep 7164
03:00.0 Multimedia controller: Philips Semiconductors Device 7164 (rev 81)
 
```

```
$ modprobe -l | grep saa71
kernel/drivers/media/common/saa7146.ko
kernel/drivers/media/common/saa7146_vv.ko
kernel/drivers/media/video/saa7110.ko
kernel/drivers/media/video/saa7115.ko
kernel/drivers/media/video/saa717x.ko
kernel/drivers/media/video/saa7127.ko
kernel/drivers/media/video/saa7185.ko
kernel/drivers/media/video/saa7134/saa6752hs.ko
kernel/drivers/media/video/saa7134/saa7134.ko
kernel/drivers/media/video/saa7134/saa7134-empress.ko
kernel/drivers/media/video/saa7134/saa7134-alsa.ko
kernel/drivers/media/video/saa7134/saa7134-dvb.ko
$ 
```

```
$ modprobe -l | grep dvb-core
kernel/drivers/media/dvb/dvb-core/dvb-core.ko 
```


Also there is no /dev/dvb 

dvb-core does not seem to be loading either.

---

### Post by lokness on 2010-01-23
so, does using a coax cable from an STB to the 2250 card mean that the signal is not digital?

if so, should i be using s-video connection from STB to 2250 card?

---

### Post by dmacindoe on 2010-01-23
I downloaded the HVR-2250 firmware and drivers this afternoon (Jan 23).  As the MAKE process progressed, several errors were displayed, such as:
 
[SIZE=2][FONT=Times New Roman]  CC [M]  /home/david/saa7164-stable/v4l/et61x251_core.o [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=2]/home/david/saa7164-stable/v4l/et61x251_core.c: In function 'et61x251_ioctl_v4l2': [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]/home/david/saa7164-stable/v4l/et61x251_core.c:2493: warning: the frame size of 1256 bytes is larger than 1024 bytes [/SIZE][/FONT]
 
[SIZE=2][FONT=Times New Roman]  CC [M]  /home/david/saa7164-stable/v4l/firedtv-fe.o [/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]  CC [M]  /home/david/saa7164-stable/v4l/firedtv-1394.o [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=2]/home/david/saa7164-stable/v4l/firedtv-1394.c:21:17: error: dma.h: No such file or directory [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]/home/david/saa7164-stable/v4l/firedtv-1394.c:22:21: error: csr1212.h: No such file or directory [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]/home/david/saa7164-stable/v4l/firedtv-1394.c:23:23: error: highlevel.h: No such file or directory [/SIZE][/FONT]
 
finishing up with:
 
[FONT=Times New Roman][SIZE=2]/home/david/saa7164-stable/v4l/firedtv-1394.c: In function 'fdtv_1394_exit': [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]/home/david/saa7164-stable/v4l/firedtv-1394.c:283: error: implicit declaration of function 'hpsb_unregister_protocol' [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]make[3]: *** [/home/david/saa7164-stable/v4l/firedtv-1394.o] Error 1 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]make[2]: *** [_module_/home/david/saa7164-stable/v4l] Error 2 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic' [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]make[1]: *** [default] Error 2 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]make[1]: Leaving directory `/home/david/saa7164-stable/v4l' [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]make: *** [all] Error 2 [/SIZE][/FONT]
 
Has anything recently changed in the driver?
 
Thanks for the help!
 
David

---

### Post by silverdulcet on 2010-01-23
> **dmacindoe said:**
> I downloaded the HVR-2250 firmware and drivers this afternoon (Jan 23).  As the MAKE process progressed, several errors were displayed, such as:
 
[SIZE=2][FONT=Times New Roman]  CC [M]  /home/david/saa7164-stable/v4l/et61x251_core.o [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=2]/home/david/saa7164-stable/v4l/et61x251_core.c: In function 'et61x251_ioctl_v4l2': [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]/home/david/saa7164-stable/v4l/et61x251_core.c:2493: warning: the frame size of 1256 bytes is larger than 1024 bytes [/SIZE][/FONT]
 
[SIZE=2][FONT=Times New Roman]  CC [M]  /home/david/saa7164-stable/v4l/firedtv-fe.o [/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]  CC [M]  /home/david/saa7164-stable/v4l/firedtv-1394.o [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=2]/home/david/saa7164-stable/v4l/firedtv-1394.c:21:17: error: dma.h: No such file or directory [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]/home/david/saa7164-stable/v4l/firedtv-1394.c:22:21: error: csr1212.h: No such file or directory [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]/home/david/saa7164-stable/v4l/firedtv-1394.c:23:23: error: highlevel.h: No such file or directory [/SIZE][/FONT]
 
finishing up with:
 
[FONT=Times New Roman][SIZE=2]/home/david/saa7164-stable/v4l/firedtv-1394.c: In function 'fdtv_1394_exit': [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]/home/david/saa7164-stable/v4l/firedtv-1394.c:283: error: implicit declaration of function 'hpsb_unregister_protocol' [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]make[3]: *** [/home/david/saa7164-stable/v4l/firedtv-1394.o] Error 1 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]make[2]: *** [_module_/home/david/saa7164-stable/v4l] Error 2 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic' [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]make[1]: *** [default] Error 2 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]make[1]: Leaving directory `/home/david/saa7164-stable/v4l' [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]make: *** [all] Error 2 [/SIZE][/FONT]
 
Has anything recently changed in the driver?
 
Thanks for the help!
 
David

Post [#81]("http://ubuntuforums.org/showpost.php?p=8662140&postcount=81") on [Page 9]("http://ubuntuforums.org/showthread.php?t=942403&page=9") addresses this very same problem. Earlier somewhere around Post #65 the work-around was posted. Search this Thread is your friend. ;)

If you only have this tuner. I'd recommend using the main linuxtv.org v4l-dvb mercurial repo instead of just the driver that is posted in the original how-to. The reason for this is that you won't run into the firedtv errors anymore. 

This includes the fixes for all the tuners supported by v4l-dvb. A warning however, its possible that other cards supported by v4l-dvb might stop working. In my experience they fix problems like that fairly quickly. I am currently using the linuxtv.org v4l-dvb mercurial repo for my HVR-2250 and my HVR-1600.

If you insist on using the driver from kernellabs, then use the option mentioned in the posts I linked above to exclude the firedtv module.

---

### Post by lpnb on 2010-01-23
> **lokness said:**
> so, does using a coax cable from an STB to the 2250 card mean that the signal is not digital?

if so, should i be using s-video connection from STB to 2250 card?

It depends on the set top box. but this driver only supports a digital signal. so if you have it working and you are watching TV under linux then it must be digital.

do you change channels via the STB or the linux box. if it is the linux box then the signal that you are receiving is just a passed through signal from the antenna so it is as if you just have the antenna connected to the linux box.

---

### Post by lokness on 2010-01-24
thanks lpnb, i am not seeing anything and i cant even get the backend setup to pickup a channel.  must not be digital.  it seems like the rest of the setup has worked but i cant get any channels. bummer.

thanks

---

### Post by lokness on 2010-01-24
just for the rest of the community who might have what i have and its working for you and im just missing something.

i have a scientific atlanta explorer 4240HDC time warner digital cable STB
-- digital channels from 104-178 (San Antonio, Tx with TW Digital Basic Cable)

my box: [COLOR=#666666]
[/COLOR][SIZE=2]Acer X1200 X2 X64
Athlon X2  Dual Core 2.5GHz[/SIZE]
Integrated NVIDIA GeForce 8200
and of course
Hauppauge hvr 2250

[    5.306241] saa7164 driver loaded
[    5.306358] saa7164 0000:04:00.0: PCI INT A -> Link[AE2A] -> GSI 16 (level, low) -> IRQ 16
[    5.306669] CORE saa7164[0]: subsystem: 0070:8891, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[    5.306675] saa7164[0]/0: found at 0000:04:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfd400000
[    5.306680] saa7164 0000:04:00.0: setting latency timer to 64
[    5.306684] IRQ 16/saa7164[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    5.510018] saa7164_downloadfirmware() no first image
[    5.510028] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[    5.510032] saa7164 0000:04:00.0: firmware: requesting v4l-saa7164-1.0.3.fw
[    6.462109] saa7164_downloadfirmware() firmware read 3978608 bytes.
[    6.462112] saa7164_downloadfirmware() firmware loaded.
[    6.462120] saa7164_downloadfirmware() SecBootLoader.FileSize = 3978608
[    6.462126] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[    6.462127] saa7164_downloadfirmware() BSLSize = 0x0
[    6.462129] saa7164_downloadfirmware() Reserved = 0x0
[    6.462130] saa7164_downloadfirmware() Version = 0x51cc1
[   13.640014] saa7164_downloadimage() Image downloaded, booting...
[   13.740013] saa7164_downloadimage() Image booted successfully.
[   16.130017] saa7164_downloadimage() Image downloaded, booting...
[   17.570016] saa7164_downloadimage() Image booted successfully.
[   17.610480] saa7164[0]: Hauppauge eeprom: model=88061
[   18.334677] DVB: registering new adapter (saa7164)
[   21.688068] DVB: registering new adapter (saa7164)
.
.
.
[   17.610463] tveeprom 2-0000: Hauppauge model 88061, rev C3F2, serial# 6446729
[   17.610466] tveeprom 2-0000: MAC address is 00-0D-FE-62-5E-89
[   17.610469] tveeprom 2-0000: tuner model is NXP 18271C2_716x (idx 152, type 4)
[   17.610471] tveeprom 2-0000: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   17.610474] tveeprom 2-0000: audio processor is SAA7164 (idx 43)
[   17.610476] tveeprom 2-0000: decoder processor is SAA7164 (idx 40)
[   17.610478] tveeprom 2-0000: has radio, has IR receiver, has no IR transmitter


i guess the blaster isnt supported?  when i plug it in, the blaster light stays on - hmm weird.

well, like i said, i believe it is working, i just cant seem to get any channels using mythbuntu's scanning function in the backend setup.

i have scanned using 'Cable High' QAM256 and QAM64.  i have also changed the tuning and scan interval from their defaults to greater values.

---

### Post by lokness on 2010-01-24
arrrgghh, i forgot to add that the acer has an hdmi output and that is what i am using to connect to my TV.

---

### Post by silverdulcet on 2010-01-24
> **lokness said:**
> just for the rest of the community who might have what i have and its working for you and im just missing something.

i have a scientific atlanta explorer 4240HDC time warner digital cable STB
-- digital channels from 104-178 (San Antonio, Tx with TW Digital Basic Cable)

my box: [COLOR=#666666]
[/COLOR][SIZE=2]Acer X1200 X2 X64
Athlon X2  Dual Core 2.5GHz[/SIZE]
Integrated NVIDIA GeForce 8200
and of course
Hauppauge hvr 2250

[    5.306241] saa7164 driver loaded
[    5.306358] saa7164 0000:04:00.0: PCI INT A -> Link[AE2A] -> GSI 16 (level, low) -> IRQ 16
[    5.306669] CORE saa7164[0]: subsystem: 0070:8891, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[    5.306675] saa7164[0]/0: found at 0000:04:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfd400000
[    5.306680] saa7164 0000:04:00.0: setting latency timer to 64
[    5.306684] IRQ 16/saa7164[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    5.510018] saa7164_downloadfirmware() no first image
[    5.510028] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[    5.510032] saa7164 0000:04:00.0: firmware: requesting v4l-saa7164-1.0.3.fw
[    6.462109] saa7164_downloadfirmware() firmware read 3978608 bytes.
[    6.462112] saa7164_downloadfirmware() firmware loaded.
[    6.462120] saa7164_downloadfirmware() SecBootLoader.FileSize = 3978608
[    6.462126] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[    6.462127] saa7164_downloadfirmware() BSLSize = 0x0
[    6.462129] saa7164_downloadfirmware() Reserved = 0x0
[    6.462130] saa7164_downloadfirmware() Version = 0x51cc1
[   13.640014] saa7164_downloadimage() Image downloaded, booting...
[   13.740013] saa7164_downloadimage() Image booted successfully.
[   16.130017] saa7164_downloadimage() Image downloaded, booting...
[   17.570016] saa7164_downloadimage() Image booted successfully.
[   17.610480] saa7164[0]: Hauppauge eeprom: model=88061
[   18.334677] DVB: registering new adapter (saa7164)
[   21.688068] DVB: registering new adapter (saa7164)


i guess the blaster isnt supported?  when i plug it in, the blaster light stays on - hmm weird.

well, like i said, i believe it is working, i just cant seem to get any channels using mythbuntu's scanning function in the backend setup.

Just to clarify the analogue part of this card is not supported in the drivers yet. 

You can either tune OTA ATSC with an antenna or with some cable providers you can plug the cable feed directly from the wall into the card and scan for unencrypted QAM channels. There are several modes to try in mythtv-setup. 

If you want to use a set-top box you need a card that can record by connecting the box via SVIDEO, or component cables (such as the Hauppauge HD-PVR, which is an external box).

Yes, the blaster is not yet supported AFAIK. This is also mentioned earlier in this thread.

---

### Post by lpnb on 2010-01-24
:D fixed it!

I used the repo and the info here:
[www.linuxtv.org/rep](www.linuxtv.org/rep)

I thought that I had tried it before but anyway this time it worked.

Thanks silverdulcet for your suggestions and help!!!

now I just need to get it to scan....its not getting anything.

last time I had this card working under another build I had to manual specify the transports....anyway I am sure it won't take too long.

---

### Post by gmoser on 2010-01-24
So does anyone know why:
cp *fw /lib/firmware

Results in:

cp: cannot create regular file `/lib/firmware/dvb-fe-tda10048-1.0.fw': Permission denied
cp: cannot create regular file `/lib/firmware/v4l-saa7164-1.0.2.fw': Permission denied
cp: cannot create regular file `/lib/firmware/v4l-saa7164-1.0.3.fw': Permission denied

Big Linux fan but it's stuff like this that is forcing me back to Windows :(

---

### Post by lpnb on 2010-01-24
This is may be the first time I have ever offered linux help!!  but for me I needed:

```
**sudo** cp *fw /lib/firmware
```

mostly normal users don't have the permissions required for lots of system directories.

I feel like that occasionally myself. but for some reason I am sticking with it. I just get a lot of satisfaction once it is going. :-) and I have a passionate about my dislike of M$ and what they stand for....off topic...sorry...

Anyway, I'll help if I can but there are much more qualified people on this forum than I.

Also I can recommend the v4l post I put up just before and was very successfull for me....though I am still having trouble scanning for channels.

> **gmoser said:**
> So does anyone know why:
cp *fw /lib/firmware

Results in:

cp: cannot create regular file `/lib/firmware/dvb-fe-tda10048-1.0.fw': Permission denied
cp: cannot create regular file `/lib/firmware/v4l-saa7164-1.0.2.fw': Permission denied
cp: cannot create regular file `/lib/firmware/v4l-saa7164-1.0.3.fw': Permission denied

Big Linux fan but it's stuff like this that is forcing me back to Windows :( 

---

### Post by cedyathome on 2010-01-25
I see that there is a new firmware version on the Happaugue site. 
How do I extract the firmware from that release?   
Are the drivers dependent on the firmware release? 
There are instructions on post #40, but no one confirmed that it works.   

Secondly, in MythTV, I always see a signal strength of 0 (or a blank field). 
Does anyone else see a signal strength? 
My TV works just fine and I seem to be seeing most channels in my scan.  

Thank you.

---

### Post by LowSky on 2010-01-25
> **cedyathome said:**
> I see that there is a new firmware version on the Happaugue site. 
How do I extract the firmware from that release?   
Are the drivers dependent on the firmware release? 
There are instructions on post #40, but no one confirmed that it works.   

Thank you.

That isn't firmware it's a Windows driver, The V4L driver is newer, please use that.

---

### Post by LowSky on 2010-01-25
By this weekend I hope to get the Tutorial updated, Sorry I have not done it sooner I have just been really busy and wish I didn't have so much work to do.

If anyone feels I should use a certain method or step I forget to include before please feel free to PM me or leave a note in this thread.

---

### Post by lpnb on 2010-01-25
I am now watching Tellie!! 

woo hoo.... its working well and hasn't crashed yet!!! 

I was scanning the channels before and was getting NOTHING just timeouts....but in my efforts to get the driver installed I had re-compiled the kernel to make sure all the modules installed (dvb-core was not loading). after re-compiling I had some luck and got it to install the driver with the v4l-org install but I don't think that the kernel was what helped in this case.

So Anyway, after getting the device to be detected I could not scan successfully even with specifying the transports manually. I reverted back to the old generic kernel 2.6.31.17-generic (I think) suddenly and with no other changes it successfully scanned all channels without any specified transports. woohooo.....

Well I can say that it seems to me to be a bit faster than the DViCO Dual Digital to that eventually died and jut never worked right and it also seems a lot more stable with this newer Mythbuntu release. 9.10 .... 

lots of tweaking to do and set up the graphics driver for my silly 1366x768 TV but thats o.k. I have done that a million times. 

Anybody that has had similar problems I will do my best to help.

---

### Post by Hwy120 on 2010-01-26
> **LowSky said:**
> By this weekend I hope to get the Tutorial updated, Sorry I have not done it sooner I have just been really busy and wish I didn't have so much work to do.

If anyone feels I should use a certain method or step I forget to include before please feel free to PM me or leave a note in this thread.

I am fairly new to Linux/Ubuntu and Myth TV.  In addition to updating the procedure, please provide the correct steps to use when the kernel is updated and the drivers need to be reinstalled.  I have had problems with reinstalling the drivers.  The error I received was about directories not being empty.  So I assume that reinstalling the drivers should be done differently.

Thank you for the guidance you, and others, have provided in this thread.

---

### Post by cedyathome on 2010-01-26
Lowsky,
I followed your tutorial right after installing mythbuntu 9.10. Here are the only 2 points where I needed to deviate from the scripts (both have been covered in previous posts on this thread)

1. install unzip. this isn't included in mythbuntu 9.10. so, the 

```
# sudo apt-get install unzip 
```should be added right at the beginning.

2. The "make" command bombs out because some card in there needs the whole kernel source. DanBataar pointed out the command to exclude that card.
```
make CONFIG_DVB_FIREDTV:=n || return
```Thanks for taking the time to create the tutorial.

---

### Post by cedyathome on 2010-01-26
bump. Anyone?

> **cedyathome said:**
> ...

Secondly, in MythTV, I always see a signal strength of 0 (or a blank field). 
Does anyone else see a signal strength? 
My TV works just fine and I seem to be seeing most channels in my scan.  

Thank you.

---

### Post by LowSky on 2010-01-26
cedyathome I will try to look into your signal issue. I could have sworn that was a minor issue with the 2250 driver... I'll keep an eye out.

Just to clarify My original tutorial used regular Ubuntu, and MythTV was installed on a current system, so maybe I didn't notice a few packages that are required.

I'm really bummed I haven't been working on this project to update it. I've been just too busy. I wanted to begin after getting back from CES, but too much work mixed with family and friend obligations are keeping me away. It's one thing to post a comment on the forum for help, but building a new system and documenting the process is a lot of work.

To shed more light on my new project I will at least start off by listing the components I will use


[LIST]
[*]Ubuntu 9.10, I will used the MythTV packages from the Repo's. Sorry if this offends anyone but I prefer it over Mythbuntu
[*]AMD Phenom 9950 Agena 2.6GHz
[*]GIGABYTE GA-MA78GM-S2H AM2+/AM2 AMD 780G HDMI Micro ATX AMD Motherboard
[*]SAPPHIRE 100252HDMI Radeon HD 4550 512MB 64-bit GDDR3 PCI Express 2.0 x16 HDCP Ready CrossFireX Support Low Profile Ready Video Card
[*]Hauppauge WinTV-HVR-2250 Media Center Kit Dual TV Tuner 1213 PCI-Express x1
[*]Samsung 750GB SATA Hard Drive - for OS and Video recording
[*]Seagate 500GB SATA Hard Drive - For backed up movies and music.

[/LIST]

---

### Post by clutzer on 2010-01-28
Has anyone figured out how to get the remote (which is NOT USB) working with this card?  I suspect LIRC (lirc_i2c) needs be updated to support it.  I say this because the IR cable and plug seem almost exactly the same as my old Hauppage PVR-250 card which used lirc_i2c.  Thoughts?

---

### Post by lpnb on 2010-01-28
Don't know but I bought a  HP OVU400102/71 Media centre remote receiver and remote off ebay for a few dollars which works straight out of the box. although it controls my partners HP Laptop at the same time which has some interesting results!! LOL 

> **clutzer said:**
> Has anyone figured out how to get the remote (which is NOT USB) working with this card?  I suspect LIRC (lirc_i2c) needs be updated to support it.  I say this because the IR cable and plug seem almost exactly the same as my old Hauppage PVR-250 card which used lirc_i2c.  Thoughts?

---

### Post by lokness on 2010-01-29
[    5.481365] saa7164 driver loaded
[    5.481450] saa7164 0000:04:00.0: PCI INT A -> Link[AE2A] -> GSI 16 (level, low) -> IRQ 16
[    5.481795] CORE saa7164[0]: subsystem: 0070:8891, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[    5.481801] saa7164[0]/0: found at 0000:04:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfd400000
[    5.481806] saa7164 0000:04:00.0: setting latency timer to 64
[    5.481810] IRQ 16/saa7164[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    5.690012] saa7164_downloadfirmware() no first image
[    5.690022] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[    5.690026] saa7164 0000:04:00.0: firmware: requesting v4l-saa7164-1.0.3.fw
[    6.143458] saa7164_downloadfirmware() firmware read 3978608 bytes.
[    6.143461] saa7164_downloadfirmware() firmware loaded.
[    6.143469] saa7164_downloadfirmware() SecBootLoader.FileSize = 3978608
[    6.143474] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[    6.143475] saa7164_downloadfirmware() BSLSize = 0x0
[    6.143477] saa7164_downloadfirmware() Reserved = 0x0
[    6.143478] saa7164_downloadfirmware() Version = 0x51cc1
[   13.430043] saa7164_downloadimage() Image downloaded, booting...
[   13.540019] saa7164_downloadimage() Image booted successfully.
[   15.930014] saa7164_downloadimage() Image downloaded, booting...
[   17.360017] saa7164_downloadimage() Image booted successfully.
[   17.400598] saa7164[0]: Hauppauge eeprom: model=88061
[   18.154789] DVB: registering new adapter (saa7164)
[   21.418377] DVB: registering new adapter (saa7164)

[   17.400581] tveeprom 2-0000: Hauppauge model 88061, rev C3F2, serial# 6446729
[   17.400585] tveeprom 2-0000: MAC address is 00:0d:fe:62:5e:89
[   17.400587] tveeprom 2-0000: tuner model is NXP 18271C2_716x (idx 152, type 4)
[   17.400590] tveeprom 2-0000: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   17.400592] tveeprom 2-0000: audio processor is SAA7164 (idx 43)
[   17.400594] tveeprom 2-0000: decoder processor is SAA7164 (idx 40)
[   17.400596] tveeprom 2-0000: has radio, has IR receiver, has no IR transmitter


ok, i see this from dmesg but i still cant get any channels to come up.  i also dont see QAM in the TV standards line.  could this be my problem?

i am connected from my STB to the 2250 using s-video

arrrgghh, what am i doing wrong?

---

### Post by LowSky on 2010-01-29
> **lokness said:**
> 

ok, i see this from dmesg but i still cant get any channels to come up.  i also dont see QAM in the TV standards line.  could this be my problem?

i am connected from my STB to the 2250 using s-video

arrrgghh, what am i doing wrong?

S-video does not work, only digital cable works. Take the cable box out of the equation connect your cable directly to the PC and scan for channels. Note you will not get anywhere near the number you have with a cable box.

Sorry but if you want to watch from your cable box you will need a different TV card. Specifically one that has analog support.

---

### Post by gmoser on 2010-01-30
> **lpnb said:**
> This is may be the first time I have ever offered linux help!!  but for me I needed:

```
**sudo** cp *fw /lib/firmware
```

mostly normal users don't have the permissions required for lots of system directories.

I feel like that occasionally myself. but for some reason I am sticking with it. I just get a lot of satisfaction once it is going. :-) and I have a passionate about my dislike of M$ and what they stand for....off topic...sorry...



Thanks for that!  I tried Sudo as well and no luck.  I figured this was just outdated so I await the re-release of the tutorial.  I may pick up a different card as analog support may be required down the road.  If by "digital" I will only receive the HD broadcasted signals via coax it will net me about 10 channels.  Hardly enough!  How do I go on with life missing people getting Tazed on Cops??

---

### Post by lokness on 2010-01-30
has anyone here tried to use the channels.conf option when scanning for channels?  i would like to maybe build a channels.conf file but dont know how.

and im still not getting any channels either directly using the coax cable and taking the STB out or through the STB using s-video - bummer.

the scan doesnt seem to use the broadcast-digital (4-1) channels.  it seems to skip over them.

---

### Post by gmoser on 2010-01-30
> **lokness said:**
> 
and im still not getting any channels either directly using the coax cable and taking the STB out or through the STB using s-video - bummer.

the scan doesnt seem to use the broadcast-digital (4-1) channels.  it seems to skip over them.

You won't get any thru the S-video since analog is not supported.  It's in about every page of this 14 page thread.  I hope that is resolved shortly though.

---

### Post by lpnb on 2010-01-31
Take the STB out of the equation altogether. plug your antenna into the card and try a scan.

you could also try manually adding the transports and then do a scan. once before that worked for me but that was on an earlier version of the beta driver for this card.

here is a link to a thread containing some transport for newcastle. (are you in Australia?)
[http://www.mythtvtalk.com/forum/installation-issues/6993-channel-scan-abc-australia.html](http://www.mythtvtalk.com/forum/installation-issues/6993-channel-scan-abc-australia.html)

I never have been able to find a list of all the transports for all the transmitters around Australia.

Also try using w_scan:
[http://edafe.org/vdr/w_scan/](http://edafe.org/vdr/w_scan/)



> **lokness said:**
> has anyone here tried to use the channels.conf option when scanning for channels?  i would like to maybe build a channels.conf file but dont know how.

and im still not getting any channels either directly using the coax cable and taking the STB out or through the STB using s-video - bummer.

the scan doesnt seem to use the broadcast-digital (4-1) channels.  it seems to skip over them.

---

### Post by 440corbon on 2010-02-07
I have finally managed to get the drivers installed and scan for channels with a set top antenna hooked up. I am locking on possible channels but getting no signal lock. I am wondering if this is an issue with the card(have it in a pcie 2 slot,I don't have pcie 1 slots on my motherboard) or if this is just too week of a signal. If anyone has an answer to this it would help me out a lot. TIA

---

### Post by 440corbon on 2010-02-07
OK. I'm an idiot. I thought it wasn't working. But I'm watching the Super Bowl right now. However it still shows no signal strength. I also added a few permissions in ubuntu I didn't have ticked.

---

### Post by perato on 2010-02-07
You might need to increase the time mythtv waits for the signal to lock on.  There is an option buried in mythtv-setup.  I'm using archlinux with mythtv from the extra repository.  I recommend setting it to 7 to 10 seconds.

---

### Post by gmoser on 2010-02-07
So I re-tried the steps listed on page one, and its still no go.  I run LSPCI and here's what I get:

> 00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
03:00.0 Multimedia controller: Philips Semiconductors Device 7164 (rev 81)
04:00.0 Communication controller: Agere Systems Device 0630 (rev 01)


I don't think its in there... ARRRGGG!  Lil help?

---

### Post by 440corbon on 2010-02-07
Perato....it is working.I can watch tv. I did increase my scan times to 7ooo ms. I still don't get anything on the strength meter though. In the spring I will mount a roof antenna and see how things work out. But I thank you for the input. I know it may help some others

---

### Post by 440corbon on 2010-02-07
here is what I get from dmesg | grep saa
[   21.335540] saa7164 driver loaded
[   21.335785] saa7164 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   21.335997] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   21.336002] saa7164[0]/0: found at 0000:01:00.0, rev: 129, irq: 19, latency: 0, mmio: 0xf9800000
[   21.336006] saa7164 0000:01:00.0: setting latency timer to 64
[   21.336010] IRQ 19/saa7164[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   21.540035] saa7164_downloadfirmware() no first image
[   21.540081] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[   21.540084] saa7164 0000:01:00.0: firmware: requesting v4l-saa7164-1.0.3.fw
[   21.553090] saa7164_downloadfirmware() firmware read 3978608 bytes.
[   21.553092] saa7164_downloadfirmware() firmware loaded.
[   21.553098] saa7164_downloadfirmware() SecBootLoader.FileSize = 3978608
[   21.553138] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   21.553139] saa7164_downloadfirmware() BSLSize = 0x0
[   21.553140] saa7164_downloadfirmware() Reserved = 0x0
[   21.553141] saa7164_downloadfirmware() Version = 0x51cc1
[   28.420070] saa7164_downloadimage() Image downloaded, booting...
[   28.530075] saa7164_downloadimage() Image booted successfully.
[   30.890073] saa7164_downloadimage() Image downloaded, booting...
[   32.320055] saa7164_downloadimage() Image booted successfully.
[   32.360733] saa7164[0]: Hauppauge eeprom: model=88061
[   33.084657] DVB: registering new adapter (saa7164)
[   36.398085] DVB: registering new adapter (saa7164)

---

### Post by 440corbon on 2010-02-07
from low sky's post in the become famous thread.

```
wget http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip
wget http://www.steventoth.net/linux/hvr22xx/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
wget http://www.steventoth.net/linux/hvr22xx/extract.sh
```
```
sh extract.sh
sudo cp *fw /lib/firmware
```


you need to install mercurial and build essential for the next steps

```
sudo apt-get install mercurial build-essential

```


then we need the driver using this command to fetch

```
hg clone http://kernellabs.com/hg/saa7164-stable/

```
now change to the directory

```
cd saa7164-stable
```

for fixing after kernal update only otherwise go to next step

```
make distclean
```

then from silver dulcet on page 9 of this thread

```
make CONFIG_DVB_FIREDTV:=n
```

```
sudo make install
```
```
sudo reboot
```
```
dmesg | grep saa
```
if everything worked out you  will have something like my previous post as a result.

---

### Post by LowSky on 2010-02-08
440corbon I hope all is working...

Sorry I havent been around. I went to to do my upgrade and found out the RAM I'm using is bad, and it needs more testing to find out if its one stick or both, and then an RMA for replacement. I know Awesome... Right!

---

### Post by 440corbon on 2010-02-08
Everything was good until this morning. I broke something. I couldn't access my server. So I just reformatted. I'll be back up and running in a few hours. I actually pieced together your guide to help someone out last night. lol...Now I am going to be using it again.
 And a Major THANKS for the work you have done.

---

### Post by gmoser on 2010-02-11
Thanks bud!  Seemed like the piece mail instructions weren't doing anything, but followed this one line by line and I have them listed in myth now.

Still trying to get channels listed and live TV but at least one portion is working correctly!

---

### Post by jjwest85 on 2010-02-12
These instructions worked perfectly for me too!  

I would like to bring up the issue with the packaged remote control.  I know the driver does not support it currently, but I was curious if there are plans to get this working?  

If there are no plans, then I was curious if anybody has a good recommendation for a remote/receiver that works with Ubuntu 9.10 out of the box?

---

### Post by Hwy120 on 2010-02-13
Do the TV tuner drivers eventually get integrated into the product, or will we always have to reinstall them after every kernel update?

---

### Post by 440corbon on 2010-02-14
I would really like them to get integrated into the kernel. as well as the fm capabilities

---

### Post by jimko on 2010-02-14
The [DVB wiki page]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2250") for the Hauppauge2250, updated in Dec '09, says support is expected in the 2.6.32 kernel.

i just installed this card yesterday and seems to be working correctly in Mythbuntu Karmic on AMD64. However, it went crazy overnight and filled my disk with log messages like the following:

```
Feb 14 07:47:09 myth1 kernel: [55883.613679] saa7164_api_i2c_read() error, ret(1) = 0xc
Feb 14 07:47:09 myth1 kernel: [55883.613683] s5h1411_readreg: readreg error (ret == -5)
Feb 14 07:47:09 myth1 kernel: [55883.663584] saa7164_cmd_send() No free sequences

```

It repeated this enough to write out about 2G of log messages before it ran out of resources. It's cyclic, so I don't know if I've displayed the sequence in the correct order. I built the drivers from the stable branch of the drivers and it seemed to finish clean.  

After I cleared the space and rebooted, mythfrontend status reported both tuners as "asleep." Starting and stopping mythbackend woke them back up and they seem to be functioning normally again.

Right now, my plan is to hope it doesn't happen again.

---

### Post by rayok on 2010-02-15
Hello.. as a "noob" I'm having problems with this card. I'm running Mythbuntu 9.10 AMD64, kernel 2.6.31-19-generic, all updates. I first followed 440carbon's instructions above. The compile and install went fine but when watching TV I get a duplicate view. That is, the image is shown twice, on the top-half and bottom-half of the screen. I figured it was the driver so I ran sudo make unload and sudo make rminstall to hopefully remove that driver and try the V4L-DVB linuxtv driver. Well, after using the same CONFIG_DVB_FIRETV:=n on that it compiles and installs but same exact duplicate view. What gives? :???:

Also when switching channels it sometimes errors with the message "Error opening jump program file buffer" but I think this one is fixed in future releases but have no idea about those..

Thanks in advance..

---

### Post by Xailia on 2010-02-15
Rayok - I forget the exact setting, but instead the playback settings you have to adjust the interlacing.  Guess and check unless someone else knows off the top of their head.

---

### Post by Xailia on 2010-02-15
Thanks for all the instructions and suggestions on getting this working - I appreciate the time you guys have put into this.

After getting my first HVR-2250 working with myth I was encouraged to buy a second one.  The strange this is that the second one seems to only work after I delete all the tuner cards from the mythtv-setup.  After a little while of idle time (maybe an hour) I am unable to get a signal from the second card. (deleting all tuners fixes the issue).

Any thoughts on where to start with this issue?  I am at a lose.

---

### Post by xinix on 2010-02-16
[S]I'm having an annoying issue with this card.  The card itself works really well after I restart the backend.  I think it is because the driver is loading after the backend has been started, just my best guess though.  After a cold boot the tuner is reported as offline even though dmesg clearly shows the driver loaded just fine. It is reported as online once the backend is restarted.

Any ideas?[/S]

Never mind, I found a thread with a solution.

---

### Post by rayok on 2010-02-16
> **Xailia said:**
> Rayok - I forget the exact setting, but instead the playback settings you have to adjust the interlacing.  Guess and check unless someone else knows off the top of their head.

Yay! That kinda fixed it :) After a while of searching I finally hit the magical M (menu) key and found the only place that setting exists. It's under Video Scan and it was set to "Detect" (ha!) and had to set it to Progressive (even though I think its 1080i) and it worked fine. Thanks again..

The picture itself is OK. Its a little washed out/too bright compared to the TV itself and I can see horizontal interlacing artifacts albeit very small. My guess is either the video driver (ATI resticted on integrated HD4200) or the fact its not live and is being recorded. I'm not sure how to set it to 100% live TV, its always 4-5 seconds behind. On top of all this I tried recording. I mean, I think its recording but I'm not sure. After a few hours of "recording" I went back to check on it and it crashed saying something like the video buffer failed too many times. After that I could not get back to watching TV or see if the recording worked. When I checked system status it says its recording and the HD light is blinking but I have no idea how to confirm anything. I exited the frontend and tried to kill it but it wouldn't let me. I gave up and shut down for the night..

So anyway, I'm happy that I got this far but then again I'm so frustrated at how many retarded things I have to go through to get there.. I would like to help if I can but don't have the time outside of work and other projects. In the meantime I think I'll take a look at Linux MCE..

---

### Post by 440corbon on 2010-02-18
Glad to see people getting things working. I just want to clarify that my prior post were taken from Silver and lowsky. They are the ones that deserve the thanks not me. 
 Now for those who have not been able to get their cards to scan for channels. In the video sources section of your backend setup label it. Run this twice giving it a different name for each one. I just called it schedule0 and the second one schedule1. In input connections (which you will also need to run twice. Put the name of one of your video sources. This was the hiccup I had when trying to scan for channels. I hadn't labeled where it should look fo information.

---

### Post by dwhecht on 2010-02-21
Thanks for your help here.  I followed the directions and I'm successfully recording digital TV now.  Quality looks great and seems reliable.

I have a related question.  I see an absence of information regarding the IR receiver and blaster that come with the 2250 product.  The IR receiver and blaster do not have linux drivers that work for them, correct?  I see people asking for it on some kernellabs posts for the saa1764, but I wanted some additional confirmation.

Thanks,

David

---

### Post by 440corbon on 2010-02-21
I have not seen anything positive about the ir yet. But this is an incredible group of people and I am hopeful it will be resolved.

---

### Post by gmoser on 2010-02-22
i was reading on the hvr-1600 and it looks like that one has ir as well and should work.  i may pick one up and test it out.  can never have too many tuner cards right

---

### Post by LowSky on 2010-02-22
> **xinix said:**
> [S]I'm having an annoying issue with this card.  The card itself works really well after I restart the backend.  I think it is because the driver is loading after the backend has been started, just my best guess though.  After a cold boot the tuner is reported as offline even though dmesg clearly shows the driver loaded just fine. It is reported as online once the backend is restarted.

Any ideas?[/S]

Never mind, I found a thread with a solution.

Could you post a copy of the thread here, it may help others.

---

### Post by xinix on 2010-02-22
> **LowSky said:**
> Could you post a copy of the thread here, it may help others.

I haven't taken the time to implement the fix, but here is the thread.

[http://ubuntuforums.org/showthread.php?t=1345079](http://ubuntuforums.org/showthread.php?t=1345079)

---

### Post by LowSky on 2010-02-22
Thanks xinix, I'll look into it, I seem to be having the same issue, so I'm hoping this will fix it

---

### Post by LowSky on 2010-02-24
I've run into a few snags with Hulu Desktop running when the frontend is up.
It seems to be a pulseaudio/HDMI sound issue, something I'm a bit sketchy about

also Xinix that link you gave me is breaking my backend too. I think it fixes the driver issue, but then causes a nice MySQL problem, which then breaks the server connection from backend to fronted. Not good...Sure my Machine stays on most of the time, so having to restart the backend after a reboot might not be that annoying. The fix is to create scripts to delay the startup of other apps, but This is becoming too much work for me, I'm going cross eyed.

Also having an issue with deleting saved recordings, i think its just me being tired, but probably not...

This project is being a huge bummer... 


also why is the program guide super slow, it was faster for me to look up program names, forget trying to see what on later tonight and just recording on impulse. This is a major issue...

Is it me or is MythTv not so polished after all these years? Boxee is a lot younger and it looks lightyears ahead. Heck Windows 7 Media center runs flawlessly compared to MytTv, I would run tha if the DRM wasn't killing my streaming ability

---

### Post by xinix on 2010-02-24
Too bad the thread was a dud.  I was going to try it out tonight while I did a little maintenance to the computer (new vid card).  I may still give it a try to see if the concept can still be applied, that is tell the startup script to wait for the driver to finish loading.

---

### Post by Xailia on 2010-02-24
> **LowSky said:**
> Is it me or is MythTv not so polished after all these years? Boxee is a lot younger and it looks lightyears ahead. Heck Windows 7 Media center runs flawlessly compared to MytTv, I would run that if the DRM wasn't killing my streaming ability

I agree on some fronts that MythTV isn't polished (one example: having to manually setup the trans-coding settings after install...the defaults intentionally are not set or having to reset all the IPs addresses manually so they don't point to localhost, etc.).  The problem is not always MythTV though.  

The drivers for the 2250 are a perfect example.  The number of (not so obvious) steps you have to go through to get this working is kind of crazy.  Even now, I am still getting an error with my second card that fills up my kern.log each day and I have to do a cold boot to fix the issue.

The reality is that the hardware companies put all their efforts into Windows and leave us Linux folk on our own.  We are fortunate to have people like Steven, who developed the 2250 drivers that we are using.  

It is frustrating though - MythTV has just enough benefits over Media Center that I would prefer to get MythTV working.  The issue is that configuring MythTV to work properly takes a long time and is somewhat different for each system.  In Windows Land, you just click "Install" and everything is done for you...

Sorry, I will get off my soap-box.  I enjoy the Ubuntu/Myth community and intend to keep helping where I can, but I just wish things would just work out of the box sometimes...you know?

---

### Post by jjwest85 on 2010-02-25
So I've been doing some on-line research and I came across this old thread that talks about hooking an IR receiver to a normal microphone input.  I went to radioshack and found a converter that I think works for the Hauppauge IR receiver.  It is a female 2.5mm stereo to male 3.5mm stereo and only cost $3!!  I haven't gotten too far in this thread:

[FONT=sans-serif][SIZE=2][http://ubuntuforums.org/showthread.php?t=477958](http://ubuntuforums.org/showthread.php?t=477958)

but I have some hope for it.  I tried having my IR receiver plugged into my 'line-in' port and got the microphone input level scale in sound preferences to go up when I would push buttons on the remote.  Let me know if anyone has heard about this before?
[/SIZE][/FONT]

---

### Post by LowSky on 2010-02-25
jjwest85 thats a great idea. Also just buying a USB IR reciever would work too.

---

### Post by iQuizzle on 2010-02-28
> **lpnb said:**
> Hi guys, don't know if anyone is subscribed to this tread but I really need some help.... maybe I am getting old but I have been working with linux for a few years now and built many Mythtv in various distros but this is driving me crazy....I normally try to figure things out but I am at the end of my rope on this one.

HVR-2250, mythbuntu 9.10, athon x64 5000+ ...the install went smoothly  with the 64 bit version of mythbuntu:

```
dmesg | grep saa 
```
or
```
dmesg | grep dvb
```
or
```
dmesg | grep hvr
```

yield nothing . so that's one thing, but should that stop the install of the driver.

I have followed a few of the install howto's including the one that I think is in this thread.

I had to install unzip as the first hurdle, and I also got an error  after running 

```
make menuconfig
```

I got an error :

```
 *** Unable to find the ncurses libraries or the
 *** required header files.
 *** 'make menuconfig' requires the ncurses libraries.
 *** 
 *** Install ncurses (ncurses-devel) and try again.
 *** 
make[3]: *** [scripts/kconfig/dochecklxdialog] Error 1
make[2]: *** [v4l-mconf] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: *** [/lib/modules/2.6.31-14-generic/build/scripts/kconfig/mconf] Error 2
make[1]: Leaving directory `/home/lpnb/Downloads/saa7164-stable/v4l'
make: *** [menuconfig] Error 2

```

Now, I suspect this is related the the error I get when I run 'make'.

I have tried install ncurses devel but this does not fix the problem.

one of the howto's misses the ```
make menuconfig
``` step which I don't understand.

I tried both the stable and the Devel releases no dice either way.

O.K. so there is two issues one is that I can't see it at all with dmesg and the other is the driver install errors. I had this driver installed on exactly the same system (sans new sata DVD drive) and it worked....I rebuilt because it was very unstable due to the massive amount customisation and it was broken. So I thought I would upgrade in the hope it would be more stable and see more of my hardware. 

FYI,
the system also has a biostar TF560+ mobo, 750GB Green and quiet drive, nvidia Gigabyte 9600GT Silent graphics, 3 Noctua fans tuned to an acceptable speed for noise, MX-810 "universal remote control" (very nice but pricey) 100% custom made black anodised case. When I say custom I mean custom....even the HDD and CD brackets are hand made.... I started this damn thing 4 years ago and it has never been 100% with remote and tuner card working correctly. I have the remote working now....just need this nice tuner working.

thanks for listening!
Lachlan

That's weird. I haven't tried to install the driver, but did you try installing libncurses5-dev? It doesn't install with the ncurses-base from the repository... maybe that's what it needs. :confused:

---

### Post by xinix on 2010-02-28
oddly I have found that I have to do "sudo make menuconfig" for it to work.

---

### Post by LowSky on 2010-03-01
OK so I've been sort of running for about a week. This week I will try to record as much as possible and hope it all works as planned. the stuff I ran last week looked better and had much better sound (volume) than my Windows 7 Media Center experiences.

Side Note: I had a huge power outage starting Thursday night going into Saturday, in fact many homes are still without power in my area, thanks to a massive snow storm that cripples nearly 140,000 homes.

I have been documenting some of the issues I think many people would like to learn about if they are new to MythTV. I wasn't able to look into fixes for the issues I'm having so I cant fix them yet. Hopefully soon.

1. If you are using a router give you media center a reserved address. Not doing do might cause the frontend to fail and many people will mistake it for a MySQL or Backend problem.

2. Still some issue with MythTV at boot. the issue is Myth starting before the TV tuner card drivers load completely cause them to seem offline., my only fix is to restart MythTV Backend once a boot is complete. Otherwise look into stretching the time between the driver is loaded and the time Myth and MySQL start.

3. Trying to run another application on top of the frontend (like Hulu Desktop) and using HDMI for sound equals no sound... special thanks to PulseAudio. Exit from the frontend and sound will work on other applications, not preferred but it's helpful. Many people will be moving to HDMI as VGA is slowly dying away on HDTV's. This is important for fixing.

---

### Post by 440corbon on 2010-03-04
I'm pretty sure the kernel update broke my driver for the card. If anyone else has an issue give a shout out.

---

### Post by pjgroudas on 2010-03-06
> **440corbon said:**
> I'm pretty sure the kernel update broke my driver for the card. If anyone else has an issue give a shout out.

I have the same problem.  I remember jumping through all these hoops a couple months ago and then I did a system update and mythtv stopped working.  I totally forgot that i needed to recompile the saa7164 driver whenever the kernel updates.  How does everyone else deal with this problem?  Just remember?  Is there a simple way to automate the process?

I'm going to use this as an oppurtunity to upgrade my hard drive and go through this process on a fresh 9.10 image.  Hopefully with this thread as reference it won't be so bad! :D

---

### Post by 440corbon on 2010-03-06
Right now I am just playing with things. I am still putting my server together. But by June I would like to have everything up and running. Complete with a fresh install of Mythbuntu 10.4 On the next setup there will be no desktop. and an outdoor antenna set up.

---

### Post by jimko on 2010-03-06
I had problems after the 2.6.31.20 update too. The saa7164 drivers aren't expected to be in the kernel until 2.6.32 at best, so you (we) have to compile whenever there is an update.  My problem was the "make" step seemed to want to use the 2.6.31.19 headers and the "make install" step tried to install to the /lib/modules/2.6.31.19 directory. I was in a hurry, so I just made symlinks to the right headers and lib/modules folders and it seems to have fooled it. Check the output of your make/make install steps, look at the versions carefully and compare to the output from "uname -a" to see if your getting a mismatch.

---

### Post by cgfirecoral on 2010-03-06
> **jimko said:**
> ...
i just installed this card yesterday and seems to be working correctly in Mythbuntu Karmic on AMD64. However, it went crazy overnight and filled my disk with log messages like the following:

```
Feb 14 07:47:09 myth1 kernel: [55883.613679] saa7164_api_i2c_read() error, ret(1) = 0xc
Feb 14 07:47:09 myth1 kernel: [55883.613683] s5h1411_readreg: readreg error (ret == -5)
Feb 14 07:47:09 myth1 kernel: [55883.663584] saa7164_cmd_send() No free sequences

```It repeated this enough to write out about 2G of log messages before it ran out of resources...


I've been suffering from the same problem pretty much since I built my system in January.  Have you found a solution to this?  I did send a note to Steve Toth, but didn't hear anything back.  (It's kind of hard to find a place to report or discuss these issues).
Thanks much!

---

### Post by pjgroudas on 2010-03-06
> **cgfirecoral said:**
> I've been suffering from the same problem pretty much since I built my system in January.  Have you found a solution to this?  I did send a note to Steve Toth, but didn't hear anything back.  (It's kind of hard to find a place to report or discuss these issues).
Thanks much!

What logs are you looking at?  I'd like to check mine in the morning and see if I'm suffering the same thing.

---

### Post by cgfirecoral on 2010-03-06
> **pjgroudas said:**
> What logs are you looking at?  I'd like to check mine in the morning and see if I'm suffering the same thing.

/var/log/kern.log

> Mar  6 18:42:18 mythback1 kernel: [862821.943006] saa7164_cmd_send() No free sequences
Mar  6 18:42:18 mythback1 kernel: [862821.943016] saa7164_api_i2c_read() error, ret(1) = 0xc
Mar  6 18:42:18 mythback1 kernel: [862821.943021] s5h1411_readreg: readreg error (ret == -5)
Mar  6 18:42:18 mythback1 kernel: [862821.943027] saa7164_cmd_send() No free sequences
Mar  6 18:42:18 mythback1 kernel: [862821.943031] saa7164_api_i2c_read() error, ret(1) = 0xc
Mar  6 18:42:18 mythback1 kernel: [862821.943035] s5h1411_readreg: readreg error (ret == -5)
Mar  6 18:42:18 mythback1 kernel: [862821.943044] saa7164_cmd_send() No free sequences
Mar  6 18:42:18 mythback1 kernel: [862821.943048] saa7164_api_i2c_read() error, ret(1) = 0xc
Mar  6 18:42:18 mythback1 kernel: [862821.943052] s5h1411_readreg: readreg error (ret == -5)reboot fixes it briefly, but within 48 hours, it hits again.

---

### Post by silverdulcet on 2010-03-07
> **jimko said:**
> I had problems after the 2.6.31.20 update too. The saa7164 drivers aren't expected to be in the kernel until 2.6.32 at best, so you (we) have to compile whenever there is an update.  My problem was the "make" step seemed to want to use the 2.6.31.19 headers and the "make install" step tried to install to the /lib/modules/2.6.31.19 directory. I was in a hurry, so I just made symlinks to the right headers and lib/modules folders and it seems to have fooled it. Check the output of your make/make install steps, look at the versions carefully and compare to the output from "uname -a" to see if your getting a mismatch.

Following a kernel update you need to run the command to clear the previous build files from the source directory
```
make distclean
```

Run that command from within the src directory prior to running your 
```
make
make install
```
commands

---

### Post by Xailia on 2010-03-08
**Update (3/10/10)**: Since my original post on 3/8/10 I decided to try out a theory: what would happen if I never watched liveTV, only recordings.  It has been two days and I have not had the error occur yet.  I have recorded shows on all 4 tuners and have played back the recordings on two different frontends.  Also, I also changed from getting listing data OTA to using schedules direct.  I will keep this post updated as I further track down the issue.

> **cgfirecoral said:**
> /var/log/kern.log

reboot fixes it briefly, but within 48 hours, it hits again.

I am so happy I am not alone with this!  I have been trying to track this down for a few weeks.

I have a similar issue, but mildly different.  I have two separate HVR-2250s in my system.  One of them always works, and the second one errors out the same way both of yours does.

Here is the output (when both are working from my dmesg):

```
[    7.363018] saa7164 driver loaded
[    7.363102] saa7164 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.363441] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[    7.363452] saa7164[0]/0: found at 0000:05:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfa000000
[    7.363462] saa7164 0000:05:00.0: setting latency timer to 64
[    7.363469] IRQ 16/saa7164[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    7.529015] saa7164_downloadfirmware() no first image
[    7.529027] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[    7.529033] saa7164 0000:05:00.0: firmware: requesting v4l-saa7164-1.0.3.fw
[    7.887837] saa7164_downloadfirmware() firmware read 3978608 bytes.
[    7.887842] saa7164_downloadfirmware() firmware loaded.
[    7.887863] saa7164_downloadfirmware() SecBootLoader.FileSize = 3978608
[    7.887872] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[    7.887876] saa7164_downloadfirmware() BSLSize = 0x0
[    7.887879] saa7164_downloadfirmware() Reserved = 0x0
[    7.887883] saa7164_downloadfirmware() Version = 0x51cc1
[   14.748122] saa7164_downloadimage() Image downloaded, booting...
[   14.852023] saa7164_downloadimage() Image booted successfully.
[   17.005022] saa7164_downloadimage() Image downloaded, booting...
[   18.672753] saa7164_downloadimage() Image booted successfully.
[   18.727525] saa7164[0]: Hauppauge eeprom: model=88061
[   19.537167] DVB: registering new adapter (saa7164)
[   22.525980] DVB: registering new adapter (saa7164)
[   22.526386] saa7164 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   22.526734] CORE saa7164[1]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   22.526745] saa7164[1]/0: found at 0000:03:00.0, rev: 129, irq: 18, latency: 0, mmio: 0xfa800000
[   22.526755] saa7164 0000:03:00.0: setting latency timer to 64
[   22.526762] IRQ 18/saa7164[1]: IRQF_DISABLED is not guaranteed on shared IRQs
[   22.692023] saa7164_downloadfirmware() no first image
[   22.692069] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[   22.692075] saa7164 0000:03:00.0: firmware: requesting v4l-saa7164-1.0.3.fw
[   22.704063] saa7164_downloadfirmware() firmware read 3978608 bytes.
[   22.704068] saa7164_downloadfirmware() firmware loaded.
[   22.704090] saa7164_downloadfirmware() SecBootLoader.FileSize = 3978608
[   22.704099] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   22.704103] saa7164_downloadfirmware() BSLSize = 0x0
[   22.704106] saa7164_downloadfirmware() Reserved = 0x0
[   22.704109] saa7164_downloadfirmware() Version = 0x51cc1
[   29.568024] saa7164_downloadimage() Image downloaded, booting...
[   29.672036] saa7164_downloadimage() Image booted successfully.
[   31.796022] saa7164_downloadimage() Image downloaded, booting...
[   33.460072] saa7164_downloadimage() Image booted successfully.
[   33.496508] saa7164[1]: Hauppauge eeprom: model=88061
[   34.080780] DVB: registering new adapter (saa7164)
[   36.970107] DVB: registering new adapter (saa7164)
```

I think it is a little strange both of them are "[card =7,autodetect]" - should these be different cards?  Could this be related?

Here is my kern.log right as the error began (March 2nd was the last time the log was written too before this)  :

```

Mar  5 01:22:57 media-desktop kernel: [183711.464017] Event timed out
Mar  5 01:22:57 media-desktop kernel: [183711.464026] saa7164_api_i2c_read() error, ret(1) = 0x32
Mar  5 01:22:57 media-desktop kernel: [183711.464031] s5h1411_readreg: readreg error (ret == -5)
Mar  5 01:22:58 media-desktop kernel: [183712.488017] Event timed out
Mar  5 01:22:58 media-desktop kernel: [183712.488026] saa7164_api_i2c_read() error, ret(1) = 0x32
Mar  5 01:22:58 media-desktop kernel: [183712.488030] s5h1411_readreg: readreg error (ret == -5)
Mar  5 01:23:07 media-desktop kernel: [183721.464023] Event timed out
Mar  5 01:23:07 media-desktop kernel: [183721.464031] saa7164_api_i2c_read() error, ret(1) = 0x32
Mar  5 01:23:07 media-desktop kernel: [183721.464036] s5h1411_readreg: readreg error (ret == -5)
Mar  5 01:23:08 media-desktop kernel: [183722.488024] Event timed out
Mar  5 01:23:08 media-desktop kernel: [183722.488039] saa7164_api_i2c_read() error, ret(1) = 0x32
Mar  5 01:23:08 media-desktop kernel: [183722.488044] s5h1411_readreg: readreg error (ret == -5)
```

Finally, here is my mythbackend log outputted at the same time:
```
2010-03-05 01:21:21.100 [mpeg2video @ 0x6a426c0]ac-tex damaged at 26 60
2010-03-05 01:21:21.118 [mpeg2video @ 0x6a426c0]skipped MB in I frame at 10 64
2010-03-05 01:21:21.136 [mpeg2video @ 0x6a426c0]ac-tex damaged at 81 66
2010-03-05 01:21:21.154 [mpeg2video @ 0x6a426c0]ac-tex damaged at 66 67
2010-03-05 01:22:37.346 DVBSM(/dev/dvb/adapter1/frontend0), Warning: Can not measure S/N
			eno: Invalid argument (22)
2010-03-05 01:23:00.120 DVBSM(/dev/dvb/adapter3/frontend0), Warning: Can not measure S/N
			eno: Invalid argument (22)
2010-03-05 01:23:12.836 DevRdB(/dev/dvb/adapter0/frontend0) Error: Poll giving up
2010-03-05 01:23:12.859 DVBSH(/dev/dvb/adapter0/frontend0) Error: Device error detected
2010-03-05 01:23:41.507 Reschedule requested for id -1.
2010-03-05 01:23:41.626 Scheduled 1 items in 0.1 = 0.05 match + 0.07 place
2010-03-05 01:23:42.935 DVBRec(1:/dev/dvb/adapter0/frontend0) Error: Stream handler died unexpectedly.
2010-03-05 01:23:43.142 TVRec(1): Changing from Watching RecordingOnly to None
2010-03-05 01:23:43.227 Reschedule requested for id 0.
2010-03-05 01:23:43.336 Recording designated 1080i/p because width was 1920
2010-03-05 01:23:43.382 Scheduled 1 items in 0.1 = 0.04 match + 0.10 place
```

I wasn't actually watching TV at this point - the system was autoflagging commercials.  

I too emailed Steven Toth, he replied initially acknowledging that other had reported the issue; I haven't heard back from him since.

Before installing MythTV I tried using Kaffiene's TV viewer for a few days on all 4 of my inputs and never had these errors occur.  I am not sure if this issue is within the MythTV code, the drivers, or some combination.

Any thoughts on what to check/testing ideas would be fantastic.  If we can't figure this out, I am going to see if the MythTV-users list has any ideas...

Thanks!

---

### Post by jjwest85 on 2010-03-27
Does anyone know if the saa7164 driver is going to be included in the ubuntu 10.04 kernal?  I believe ubuntu 10.04 is coming with 2.6.32.  Has anyone heard for sure one way or another?

---

### Post by 440corbon on 2010-03-27
Silver I added the make distclean command to the compilation on page 15 thank for the input.

---

### Post by xinix on 2010-03-30
Ok I've been putting up with something long enough and it's time to fix it.  My HVR-2250 keeps trying to change to analog channels when I'm watching tv.  I have a PVR-150 in the machine too and when I browse to a non digital channel the HVR-2250 tries to switch to it instead.  In schedulesdirect I have two lineups, one for the PVR-150 with all the analog channels I want selected and a second with only the clear qam digital channels selected.  Is there a better way to set this up.

If I navigate the OSD menu and switch to the analog tuner then there are no problems

---

### Post by dallas8101 on 2010-04-02
I am having an issue with about half of my recordings on the HVR2250.  I use the removecommercials script to cut the commercials.  During the run it often errors out with an error 232.  I can play the files, but they do appear to be corrupted in some fashion.  I have had the HVR2250 drivers installed since about the time Steven released the original stable last year.  Has anyone run into this and found a solution?  

I have also tried the "ffmpeg -acodec copy -vcodec copy" to remux the file that is often suggested for this, but that does not complete either.

removecommercials: mythtranscode: Transcoding cruft out of original file (2111_20100201190000.mpg)
+ mythtranscode -c 2111 -s 2010-02-01-19-00-00 --mpeg2 --honorcutlist -o /var/lib/mythtv/recordings/2111_20100201190000.mpg.mpeg
2010-04-02 09:08:56.038 Using runtime prefix = /usr
2010-04-02 09:08:56.086 Empty LocalHostName.
2010-04-02 09:08:56.176 New DB connection, total: 1
2010-04-02 09:08:56.197 Closing DB connection named 'DBManager0'
2010-04-02 09:08:56.198 Enabled verbose msgs: important
2010-04-02 09:08:56.200 New DB connection, total: 2
2010-04-02 09:08:57.093 Deadlock detected.  One buffer is full when
                the other is empty!  Aborting

+ ERROR=232
+ '[' 232 -ne 0 ']'
+ echo 'removecommercials: mythtranscode: Transcoding failed for 2111_20100201190000.mpg with error 232'

---

### Post by 440corbon on 2010-04-03
I am having an issue with card being busy after ripping dvds using handbrake. Is this an issue with the card drivers or using gnome desktop with myth? it is easily resolved by restarting backend but I was wondering the root cause.

---

### Post by wildmanne39 on 2010-04-03
Hi, I wanted to ask if anyone can tell me how to purge the driver and firmware for this card, I have not been able to get it to work I have tried several times but the card does not show up, so I think I need a fresh start but I do not know how to get rid of the old driver and firmware. If anyone can help it will be greatly appreciated, I love the 2250 card but I want to use it with ubuntu not windows.

---

### Post by LowSky on 2010-04-05
> **440corbon said:**
> I am having an issue with card being busy after ripping dvds using handbrake. Is this an issue with the card drivers or using gnome desktop with myth? it is easily resolved by restarting backend but I was wondering the root cause.

this is an odd issue, and would put the blame on the cards drivers, but I think it has more to do with handbrake. More than likely handbrake and Myth are both using the same application for use and one is corrupting the other. basically a Multitasking error.

what if you use another application for ripping like Acidrip, do you get the same errors?

---

### Post by LowSky on 2010-04-05
> **wildmanne39 said:**
> Hi, I wanted to ask if anyone can tell me how to purge the driver and firmware for this card, I have not been able to get it to work I have tried several times but the card does not show up, so I think I need a fresh start but I do not know how to get rid of the old driver and firmware. If anyone can help it will be greatly appreciated, I love the 2250 card but I want to use it with ubuntu not windows.

Hi Wildmanne,

what instruction set are you using to install the firmware and drivers? hopefully it mine (shameless plug). What application are you using to play incoming feeds and how is the tuner hooked up. Have you done a channel scan? One big error many people fail to notice is that the 2250 only works as a digital tuner for Linux, which means it will not work with analog feeds. This sometimes causes confusion especially when people try to use this card with a cable box.

One of my issues currently is needing to manual reboot MythTV when the computer is turned on because of how the drivers get loaded at boot time. This issue could be yours and is simple to fix by restarting the MythTv backend.

Sorry for all the questions but its important to get an  idea of what is wrong

---

### Post by milesnorth on 2010-04-05
I followed the 440corbon summary of the lowsky procedure for the Hauppauge HVR-2250 drivers on page 15 of this thread and got following errors:

kurt@mythbuntu:~/Downloads/saa7164-stable$ make CONFIG_DVB_FIREDTV:=n

make -C /home/kurt/Downloads/saa7164-stable/v4l 
make[1]: Entering directory `/home/kurt/Downloads/saa7164-stable/v4l'
No version yet, using 2.6.31-20-generic
make[1]: Leaving directory `/home/kurt/Downloads/saa7164-stable/v4l'
make[1]: Entering directory `/home/kurt/Downloads/saa7164-stable/v4l'
scripts/make_makefile.pl
make[1]: execvp: scripts/make_makefile.pl: Permission denied
Updating/Creating .config
/bin/sh: ./scripts/make_kconfig.pl: Permission denied
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.
make[1]: Leaving directory `/home/kurt/Downloads/saa7164-stable/v4l'
make: *** [all] Error 2

I'm a linux neophyte running mythbuntu 9.10 with a Kubuntu KDE 4.3.2 frontend.  Had everything working originally using the lowsky procedure.  I likely broke something trying to mount ~home on a different hard drive partition.  Then I could only run the tv card in Mythtv after first running the mythtv backend and mythfill modules after every reboot.

Now that I updated the kernel two days ago, I can't reinstall the 2250 drivers.  I wondered if these two problems might be related to my somehow incorrectly mounting ~home on a new partition with some incorrect permissions ???

I first tried a distclean & make to update the kernel and got the same errors.  Then I tried to remove the v4l-saa files and started over from the beginning to load the drivers, which is where I am now.

Please let me know what additional information might be required and thanks for any help.

---

### Post by JohnAStebbins on 2010-04-05
> **LowSky said:**
> this is an odd issue, and would put the blame on the cards drivers, but I think it has more to do with handbrake. More than likely handbrake and Myth are both using the same application for use and one is corrupting the other. basically a Multitasking error.

what if you use another application for ripping like Acidrip, do you get the same errors?

Umm, ...no. HandBrake doesn't use any external programs to do it's job.  It is completely self contained, even to the point that most of the libraries it uses are statically linked.

But handbrake is a multithreaded application that puts a heavy load on the computer.  If there are any hardware stability issues with the machine, handbrake will certainly expose them.

---

### Post by jlp_engineer on 2010-04-05
I have been monitoring progress on the HVR-2250 with respect to Mythbuntu and have to admire everyone with the stamina to keep up the effort on this card.  On the surface, this card seems the perfect addition to anyone's home theater setup.  

I got my feet wet with Mythbuntu using an old P4 system and three PVR-150's.  I wanted to move to a tuner card that would tune digital channels and work under Mythbuntu.  I found an ATi HDTV Wonder card, and while I was never able to get it to work 100%, I learned a lot about Mythbuntu in the process.  

I don't really care much about the IR support for the card, but I am interested in support for the analog tuners.  It's because our local cable company does not offer that many unencrypted digital channels, so most of what I watch is still on analog cable.  I don't believe in purchasing anything that I cannot fully use...maybe because of some deep seated OCD issues.  Is there even a whisper or rumor when the analog side of this card will be supported?

TIA

---

### Post by DurkenV on 2010-04-06
> **LowSky said:**
> OK here is the awesome news, I got it working, but it took forever as I had to go through miles of web pages just to get this to work! I'll list my sources at the bottom if I missed something and you need to look through it for answers.

So I'm going to be nice and do some people some favours and post what I did to get it working in MythTV. 

**This driver is a BETA** and only works on digital side of the tuner, 

_NO ANALOGUE_ and _please be careful using_.

**_*I am not responsible for the outcome of you using my tutorial.*_** 

As I think my tutorial is rather crude and may miss an important step, please see the sources listed below. This is not for people new to Linux, as it might break (and it might, I've only had this running for about 30 minutes, so fingers crossed). 

If you really need to use this card for analogue and need a free OS, try the Windows 7 MCE, the free RC is currently available and should work until May 2010 before MS make you purchase a real copy and works completely with this tuner card.

Instructions for using HVR-2250 in MythTV (also works on HVR-2200 or any video capture card using the SAA7164 chipset)

you need to be running Ubuntu 8.10 or higher for these drivers

Enter this into your Terminal it is the code for the firmware and to install it
```

wget http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip
wget http://www.steventoth.net/linux/hvr22xx/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
wget http://www.steventoth.net/linux/hvr22xx/extract.sh
```
```

sh extract.sh
sudo cp *fw /lib/firmware

```
you need to install mercurial and build essential for the next steps
```
sudo apt-get install mercurial build-essential
```

then we need the driver using this command to fetch
```
hg clone http://kernellabs.com/hg/saa7164-stable/
```

now change to the directory
```
cd saa7164-stable
```

then run make
```
make
```

that will take some time, go grab a drink and wait it out, when it completes run this command
```
sudo make install
```

wait for that to complete and reboot
from the command line
```
sudo reboot
```

Note that an application like TVtime will not work, TVtime only works on Analog signals, and so far this driver only gets the digital stuff working.

then install MythTV using whatever method you like, I personally went into synaptic and installed the frontend and backend and extra plug-ins

once installed and you set up your passwords go to
System> administration> MythTV backend setup

once there go to Capture Cards, Should be choice #2
choose new capture card, you will ave to do this step twice (this card has two tuners)
At card Type, pick DTB DTV
the first will be device number 0, 
repeats choosing capture card to add the second tuner
the second device will be #1 (Linux starts counting at 0, good thing to know, especially for hard drives)

then go to video sources, pick your options, will vary so mine will not work with yours most likely, so I dont want to post something I dont know)

then go to Input Connections, again you will have 0 and 1, configure both

then edit channels and directories as needed.

close let it fill database, for some reason mine keeps running in a loop, just exit after you see it finish the first or second time

now go to Applications > Sound & Video > MythTV Frontend

And you should be able to watch TV

I must say the Linux HTPC community is way too technical for most people, they need to make these things simpler, Windows 7 MCE is  10 times better at setting up these things.

[SIZE="3"]Notes[/SIZE]
I used Ubuntu 9.04, results should work for anyone using *buntu 8.10 releases, including Mythbuntu
I must say the configuring MythTV is exhausting so if I missed something or it doens't work please post better steps.
Special thanks to Steven over at [KernelLabs]("http://www.kernellabs.com/blog/?page_id=17"), the person who made the drivers.


**[SIZE="3"]Sources[/SIZE]**

[http://www.linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers)
[http://www.kernellabs.com/blog/?page_id=17](http://www.kernellabs.com/blog/?page_id=17)
[http://kernellabs.com/hg/saa7164-stable/](http://kernellabs.com/hg/saa7164-stable/)
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)
[http://www.linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers#Using_Mercurial](http://www.linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers#Using_Mercurial)
[http://www.steventoth.net/blog/products/hvr-2250/](http://www.steventoth.net/blog/products/hvr-2250/)
[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200)

I've done all the steps as above. All went great till I had to add the capture card. When I add the card I can not edit the DVB Device Number field. Please help.... Trying to get this to work on very slow Internet connection. Finally all done and now sitting with new problem. 

At card Type, pick DTB DTV
the first will be device number 0, 
repeats choosing capture card to add the second tuner
the second device will be #1 (Linux starts counting at 0, good thing to know, especially for hard drives)

This part is it. Please help

---

### Post by DurkenV on 2010-04-06
> **LowSky said:**
> OK here is the awesome news, I got it working, but it took forever as I had to go through miles of web pages just to get this to work! I'll list my sources at the bottom if I missed something and you need to look through it for answers.

So I'm going to be nice and do some people some favours and post what I did to get it working in MythTV. 

**This driver is a BETA** and only works on digital side of the tuner, 

_NO ANALOGUE_ and _please be careful using_.

**_*I am not responsible for the outcome of you using my tutorial.*_** 

As I think my tutorial is rather crude and may miss an important step, please see the sources listed below. This is not for people new to Linux, as it might break (and it might, I've only had this running for about 30 minutes, so fingers crossed). 

If you really need to use this card for analogue and need a free OS, try the Windows 7 MCE, the free RC is currently available and should work until May 2010 before MS make you purchase a real copy and works completely with this tuner card.

Instructions for using HVR-2250 in MythTV (also works on HVR-2200 or any video capture card using the SAA7164 chipset)

you need to be running Ubuntu 8.10 or higher for these drivers

Enter this into your Terminal it is the code for the firmware and to install it
```

wget http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip
wget http://www.steventoth.net/linux/hvr22xx/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
wget http://www.steventoth.net/linux/hvr22xx/extract.sh
```
```

sh extract.sh
sudo cp *fw /lib/firmware

```
you need to install mercurial and build essential for the next steps
```
sudo apt-get install mercurial build-essential
```

then we need the driver using this command to fetch
```
hg clone http://kernellabs.com/hg/saa7164-stable/
```

now change to the directory
```
cd saa7164-stable
```

then run make
```
make
```

that will take some time, go grab a drink and wait it out, when it completes run this command
```
sudo make install
```

wait for that to complete and reboot
from the command line
```
sudo reboot
```

Note that an application like TVtime will not work, TVtime only works on Analog signals, and so far this driver only gets the digital stuff working.

then install MythTV using whatever method you like, I personally went into synaptic and installed the frontend and backend and extra plug-ins

once installed and you set up your passwords go to
System> administration> MythTV backend setup

once there go to Capture Cards, Should be choice #2
choose new capture card, you will ave to do this step twice (this card has two tuners)
At card Type, pick DTB DTV
the first will be device number 0, 
repeats choosing capture card to add the second tuner
the second device will be #1 (Linux starts counting at 0, good thing to know, especially for hard drives)

then go to video sources, pick your options, will vary so mine will not work with yours most likely, so I dont want to post something I dont know)

then go to Input Connections, again you will have 0 and 1, configure both

then edit channels and directories as needed.

close let it fill database, for some reason mine keeps running in a loop, just exit after you see it finish the first or second time

now go to Applications > Sound & Video > MythTV Frontend

And you should be able to watch TV

I must say the Linux HTPC community is way too technical for most people, they need to make these things simpler, Windows 7 MCE is  10 times better at setting up these things.

[SIZE="3"]Notes[/SIZE]
I used Ubuntu 9.04, results should work for anyone using *buntu 8.10 releases, including Mythbuntu
I must say the configuring MythTV is exhausting so if I missed something or it doens't work please post better steps.
Special thanks to Steven over at [KernelLabs]("http://www.kernellabs.com/blog/?page_id=17"), the person who made the drivers.


**[SIZE="3"]Sources[/SIZE]**

[http://www.linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers)
[http://www.kernellabs.com/blog/?page_id=17](http://www.kernellabs.com/blog/?page_id=17)
[http://kernellabs.com/hg/saa7164-stable/](http://kernellabs.com/hg/saa7164-stable/)
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)
[http://www.linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers#Using_Mercurial](http://www.linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers#Using_Mercurial)
[http://www.steventoth.net/blog/products/hvr-2250/](http://www.steventoth.net/blog/products/hvr-2250/)
[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200)

My Mythbuntu installation worked up untill 
At card Type, pick DTB DTV
the first will be device number 0, 
repeats choosing capture card to add the second tuner
the second device will be #1 (Linux starts counting at 0, good thing to know, especially for hard drives)

I can't edit the DVB Device Number field to "0" or "1" so can't add 2nd card or get the 1st one to work. Please Help.

---

### Post by kuehlc on 2010-04-22
> **cgfirecoral said:**
> /var/log/kern.log

reboot fixes it briefly, but within 48 hours, it hits again.

I'm having this same I2C error problem on a mythbuntu system I built a few months ago. Is anyone aware of a fix for this? Unless this gets resolved soon I'm going to bite the bullet and try a windows DVR for awhile.

---

### Post by dividehex on 2010-04-23
> **jimko said:**
> The [DVB wiki page]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2250") for the Hauppauge2250, updated in Dec '09, says support is expected in the 2.6.32 kernel.

i just installed this card yesterday and seems to be working correctly in Mythbuntu Karmic on AMD64. However, it went crazy overnight and filled my disk with log messages like the following:

```
Feb 14 07:47:09 myth1 kernel: [55883.613679] saa7164_api_i2c_read() error, ret(1) = 0xc
Feb 14 07:47:09 myth1 kernel: [55883.613683] s5h1411_readreg: readreg error (ret == -5)
Feb 14 07:47:09 myth1 kernel: [55883.663584] saa7164_cmd_send() No free sequences

```It repeated this enough to write out about 2G of log messages before it ran out of resources. It's cyclic, so I don't know if I've displayed the sequence in the correct order. I built the drivers from the stable branch of the drivers and it seemed to finish clean.  

After I cleared the space and rebooted, mythfrontend status reported both tuners as "asleep." Starting and stopping mythbackend woke them back up and they seem to be functioning normally again.

Right now, my plan is to hope it doesn't happen again.

I've experienced the I2C error also for the past 8 months and I don't believe there is a fix to it yet.  Just have to reboot the system for a temporary fix (2 - 36 hours).  I have been compiling the latest saa7164-dev tree every time i see an update to it but nothing changed so far to have fixed the problem.  One thing I have noticed is it only seems to be triggered when both tuners are recording.  Sometimes it only takes a couple hours of uptime to be triggered and sometimes it will run for a few days before it happens.

Ive been holding off on buying another HVR-2250 for my box and/or build mythtv systems for my family members until this bug has been found and squashed.  

As for the tuners being asleep after a reboot, this seems to be an upstart timing issue.  I believe the mythtv-backend is coming up before the drivers are ready.  Yes restarting the mythtv-backend manually after a reboot is annoying but it is now where close to the I2C hassle.

If anyone else has found a solution to the I2C bug or have heard anything from Steve about it, I would like to hear about it.

---

### Post by LowSky on 2010-04-23
Hmm -- I am not receiving this I2C error, which Version of the card do you own? My uptime has been a few weeks.
I need to check the to see what Kernel I'm using when I get home. Maybe rolling back is the answer.
I too suffer the issue of the cards being asleep after a fresh boot. I'm still trying to figure that out.

Anyone using 10.04 yet. Can anyone confirm the same issue or lack thereof.

---

### Post by dividehex on 2010-04-23
> **LowSky said:**
> Hmm -- I am not receiving this I2C error, which Version of the card do you own? My uptime has been a few weeks.
You would know if you were receiving I2C error since your HD would fill up with a constant stream of errors to the kern.log and your recordings will be 0 byte files from that point on. I'm not sure which version of the card I have.  Anyway to probe for it? Or tell from the card itself?

> **LowSky said:**
> 
I need to check the to see what Kernel I'm using when I get home. Maybe rolling back is the answer.
I'm running Linux mythtv 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

> **LowSky said:**
> 
I too suffer the issue of the cards being asleep after a fresh boot. I'm still trying to figure that out.
Anyone using 10.04 yet. Can anyone confirm the same issue or lack thereof.
I am going to rebuild my system tonight with 10.04 in hopes that it will fix the 'asleep after reboot' issue.  I'll post a reply when I'm done. :P

---

### Post by LowSky on 2010-04-23
> **dividehex said:**
> You would know if you were receiving I2C error since your HD would fill up with a constant stream of errors to the kern.log and your recordings will be 0 byte files from that point on. I'm not sure which version of the card I have.  Anyway to probe for it? Or tell from the card itself?
As far as I know there are 2 models. 
One has the IR blaster soldered to the card, and well, doesn't work, the other, original card (and the one I have) uses a USB blaster/reciever

> 
I'm running Linux mythtv 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

I Believe Im still using 2.6.29 (I'm at work so I can't check it), I haven't updated my system since getting mythtv fully running. I decided to only d Ubuntu version upgrades.

> 
I am going to rebuild my system tonight with 10.04 in hopes that it will fix the 'asleep after reboot' issue.  I'll post a reply when I'm done. :P

thanks for the pioneer work. I know many of us will love to know the results.

---

### Post by dividehex on 2010-04-23
It just gets worst from here on...

So I completely rebuilt my mythtv system with 10.04 and it seems nice.  No big hangups except that I just figured out that my cable company (Comcast - SF Bay Area) switched over digital channels above 33 to encryption a few days ago.  ](*,)

It also seems that the 'tuner asleep after reboot' issue hasn't gone away and it is too early to start seeing I2C errors but I'm sure they're just around the corner...

And here they are after about 7 mins into a dual recording.  The system had only been up for about 40 mins and had successfully recorded dual shows on the previous 30min block.
```

[110261.945417] s5h1411_readreg: readreg error (ret == -5)
[110261.945424] saa7164_cmd_send() No free sequences
[110261.945427] saa7164_api_i2c_read() error, ret(1) = 0xc
[110261.945432] s5h1411_readreg: readreg error (ret == -5)
[110261.945438] saa7164_cmd_send() No free sequences
[110261.945442] saa7164_api_i2c_read() error, ret(1) = 0xc
[110261.945446] s5h1411_readreg: readreg error (ret == -5)
[110261.980267] saa7164_cmd_send() No free sequences
[110261.980272] saa7164_api_i2c_read() error, ret(1) = 0xc
[110261.980277] s5h1411_readreg: readreg error (ret == -5)
[110261.980285] saa7164_cmd_send() No free sequences
[110261.980289] saa7164_api_i2c_write() error, ret(1) = 0xc

```

---

### Post by greensoap on 2010-04-27
I get these same errors.  I am on Ubuntu 9.10. 

I was able to track the error messages to saa7164_cmd_send() in saa7164-cmd.c. Search for "Event timed out" as it is the first error in kern.log before the errors start dumping continuously. 

It looks like the driver is keeping track of some list of commands to send to the I2C bus and eventually the command buffer fills up and has no more run to store commands.  I would also guess that the card is basically timing out and so old commands cannot get sent to clear the command buffer.  

I was able to track -5 to be the EIO error from asm/errno-base.h which seems to get assigned in master_xfer() which is called in i2c_transfer().

```
#define	EIO		     5	/* I/O error */
```

I really don't know anything about Linux Kernel programming so I doubt I will be able to figure out how to recompile and update drivers to test out ways of avoiding the error.  Maybe a longer timeout on the command  would help?

The first set of errors appear every ten seconds once the initial timeout occurs.

> 
Apr 26 01:08:17 backuppc kernel: [49014.404031] tda18271_init: [2-0060|S] error -5 on line 831
Apr 26 01:08:17 backuppc kernel: [49014.404035] tda18271_tune: [2-0060|S] error -5 on line 909
Apr 26 01:08:17 backuppc kernel: [49014.404039] tda18271_set_params: [2-0060|S] error -5 on line 990
Apr 26 01:08:17 backuppc kernel: [49014.404479] saa7164_irq_dequeue() found timed out command on the bus
Apr 26 01:08:27 backuppc kernel: [49023.888013] Event timed out
Apr 26 01:08:27 backuppc kernel: [49023.888022] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 26 01:08:27 backuppc kernel: [49023.888027] s5h1411_writereg: writereg error 0x19 0xf5 0x0000, ret == -5)
Apr 26 01:08:27 backuppc kernel: [49023.888434] saa7164_irq_dequeue() found timed out command on the bus

This next set appear almost continuously until I reboot my computer.  I should mention that I don't have any recordings or live TV going on when these occur.  Sometimes I get a few hours without error sometimes I get less than an hour.  

> Apr 26 01:25:34 backuppc kernel: [50050.888515] saa7164_api_i2c_read() error, ret(1) = 0xc
Apr 26 01:25:34 backuppc kernel: [50050.888518] s5h1411_readreg: readreg error (ret == -5)
Apr 26 01:25:34 backuppc kernel: [50050.888521] saa7164_cmd_send() No free sequences
Apr 26 01:25:34 backuppc kernel: [50050.888523] saa7164_api_i2c_read() error, ret(1) = 0xc
Apr 26 01:25:34 backuppc kernel: [50050.888526] s5h1411_readreg: readreg error (ret == -5)
Apr 26 01:25:34 backuppc kernel: [50050.888530] saa7164_cmd_send() No free sequences
Apr 26 01:25:34 backuppc kernel: [50050.888533] saa7164_api_i2c_write() error, ret(1) = 0xc
Apr 26 01:25:34 backuppc kernel: [50050.888536] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
Apr 26 01:25:34 backuppc kernel: [50050.888539] saa7164_cmd_send() No free sequences
Apr 26 01:25:34 backuppc kernel: [50050.888542] saa7164_api_i2c_write() error, ret(1) = 0xc

---

### Post by LowSky on 2010-04-28
I can think of two issues. One the card is bad or Two the driver installation went wrong.

If its neither I would send an email to Steven Toth over at Kernel Labs:
[email]stoth@kernellabs.com[/email]
 Let him know the issue, it might be something he can look into and fix.

---

### Post by dividehex on 2010-04-28
I think in my case, it would be safe to say the card isn't bad since I had it running successfully for over 5 months in a windows box without any issue.  Although, it could have been damaged when I installed it in my current linux system.
I also don't think the driver installation has been bad, I have been following SkyLows awesome install instructions. :) 
There is one thing I have always wondered about which weren't in the driver installation instructions.  I have always assumed that since the card has 2 tuners and each tuner can record 1 channel at a time, I have been changing the Mythtv default 'max recordings' under the 'recording options' to from 2 to 1 for each tuner on the card. Is this correct?

My next test is going to be running Myth with only one side of the card  (single tuner), since my timeouts only seem to appear in the middle of a  dual recordings.
I will report back in a few days.... <see my post on page 22>

---

### Post by greensoap on 2010-04-28
As dividehex mentioned, the card works fine in Windows and works beautifully in mythtv when the errors are not present.  They leads me away from the card being the issue.  Though it is entirely possible.  I was also think that it might be the firmware that is being used during the installation process.  

I used LowSky's install instructions as well.  What I noticed is that the drivers from which the firmware is extracted are different versions than the windows drivers that ship with the card.  Now whether the frimware has changed is another story.

I did find one piece of advise about disabling the EIT (Over the air guide broadcast) for all the channels.  I tried that and have not had any errors yet today.  But nothing is recording right now.  I will start a couple of recordings and see if anything happens. 

dividehex, I look forward to your test results.

---

### Post by LowSky on 2010-04-28
dividehex the name is LowSky  LOL :P

Also I REALLY REALLY need to make time to update this tutorial with 10.04 around the corner. My biggest concern is the driver, as it has not been updated in 3 months over at Kernel Labs, and its supposed inclusion into the Linux Kernel. Hopefully these new issues are not something we will see more of.

I will also point out my HTPC hasn't done an Ubuntu update since loading the drivers a few months ago. Maybe an Ubuntu Update broke something? I hope not. It doesn't seem many others are having this issue. I'm thinking of buying a second card for a 'test box' but I'm broke due to spending my money on my education (earning my BS in International Business).
Anybody what to donate to my test computer? I will accept PayPal. LOL!

---

### Post by greensoap on 2010-04-28
dividhex,

I created a script that will email me when my Myth Box dies so I can log on and reboot.  Just thought I would share.

The script uses ssmptp but sendmail could be used as well.

```
#!/bin/bash
tail -n10 /var/log/kern.log | grep -q "saa7164_api_i2c_read() error"

if [ $? -eq 0 ]  ## MythTV Error
then

touch -d '-1 hour' limit

if [ limit -nt last_notification ]; then

        /usr/sbin/ssmtp **YOUR EMAIL HERE** < ***PATH TO YOUR ERROR MESSAGE FILE***
        touch last_notification
fi

fi

```

---

### Post by dividehex on 2010-04-28
> dividehex the name is LowSky  LOL :razz:Yeah, SkyLow, SkyWalker.... LowSky... whatever your name is.  I'm really sorry, dyslexia is a bchit.

On another note, I would like to point out that this has been a problem on all the installs I have done with this card over the past year or so from 8.10, 9.10 and now 10.04.  And I also never do an updates once installed.

greensoap, thanks for the script. I will put it to use asap.

---

### Post by greensoap on 2010-04-29
Dividehex,

I unset useonairguide on all my channels (useonairguide=0) and since then I have not had a single crash.  Being up for about 24 hours, which is a record for me.

Maybe you can try unsetting this option as well and see if it clears up the issue.  

For the record, I am using Schedules Direct for my guide info.

---

### Post by LowSky on 2010-04-29
I upgraded last night to lucid and myth broke. The frontend wouldn't work and I could figure it out at all. I tried nearly everything and nothing worked. So I gave up and decided to do clean install. So far the install failed and I hadto use the alt install cd. Hopefully I can have this working tonight. Looks like upgrading is going to be nightmare for us. I'll keep everyone posted.

---

### Post by dividehex on 2010-04-30
> **greensoap said:**
> Dividehex,

I unset useonairguide on all my channels (useonairguide=0) and since then I have not had a single crash.  Being up for about 24 hours, which is a record for me.

Maybe you can try unsetting this option as well and see if it clears up the issue.  

For the record, I am using Schedules Direct for my guide info.


Thanks for the info. I found these were already unchecked so I am not sure that is causing my problems, although I hope it is successful for you.  Currently, I have disabled one of the tuners on my card and it seems be stable so far with a 2 day uptime. Obviously, this is not a final solution, but I hope it help determine what is the problem is.

I'm also using schedule direct for my guide info.

---

### Post by cgfirecoral on 2010-05-01
As one of the original posters of the saa7164_api_i2c_read() error, ret(1) = 0xc issues, I've been following this post hoping for a solution.  Email to Steve Toth went unanswered.

Eventually, I gave up trying to work with the 2250 and went out and bought a 1600 which I threw in the available PCI slot in my backend server.  After seeing the post about the problems cropping up when the 2250 is recording two shows, I turned on one of the 2250 tuners last week (so now I'm running the 1600 and a single 2250 tuner).  The backend has been solid over the last week, with a number of dual recordings taking place.

I bought my 2250 in January.  I suspect this problem may afflict recent production models, but that's purely anecdotal and I don't feel like pulling the card out to read the detailed numbers, unless it can really help debugging.

---

### Post by tjbron on 2010-05-01
> **greensoap said:**
> dividhex,
 
I created a script that will email me when my Myth Box dies so I can log on and reboot. Just thought I would share.
 
The script uses ssmptp but sendmail could be used as well.
 
```
#!/bin/bash
tail -n10 /var/log/kern.log | grep -q "saa7164_api_i2c_read() error"
 
if [ $? -eq 0 ]  ## MythTV Error
then
 
touch -d '-1 hour' limit
 
if [ limit -nt last_notification ]; then
 
        /usr/sbin/ssmtp **YOUR EMAIL HERE** < ***PATH TO YOUR ERROR MESSAGE FILE***
        touch last_notification
fi
 
fi

```
 
 
Ok, dumb question time. I would love to use this, (maybe to make the box beep) but I don't do Linux a lot and I'm still learning. Do you run this as a cron job, or what? If you set it up to run on startup, won't it only run once? How did you get it to run continuously?
 
Thanks!

---

### Post by greensoap on 2010-05-01
So I create a file called checkMyth and chmod 777 the file (to make it executable).  The script I pasted above goes in the checkMyth file.

Then I used crontab -e to open up the cron file for editing.  This is the file that cron uses to run scheduled jobs.  (I am sort of glossing the details there, but just google cron, crontab, or scheduling jobs).

This is a quick job, so I set it to run every minute.  Here is the text from my crontab file

```
# m h  dom mon dow   command
  * *  *   *   *     /home/**USERNAME**/checkMyth
```

So, this runs every minute but will only send an email once an hour.  If you look at the script it "touches" a file called limit and marks the time of that file as one hour prior to the current time.  It then checks the timestamp of the last_notification file.  If the last notification file is older (meaning a notification was sent more than an hour ago), then it notifies me again by email.  This way I don't get an email every minute, but I do get one every hour.  It might be a little overkill, but I have some simple scripts setup so that I can SSH via my iphone (yes, there is an app for that) and restart my box and mythTV.  This way, I can usually restart everything before any recordings get missed.

I hope that explanation helps.

---

### Post by tjbron on 2010-05-02
Yup, that answers my question.  I had figured out what the script was doing, just wasn't sure how you kept it running.  cron is the key!
Thanks again.
 
An interesting thing yesterday.  My 2250 crashed as we've been discussing, and the dd, syslogd and klogd were running in top, but my kern.log file doesn't show any entries since April 9 when I was getting the saa7164_api_i2c_read() error once before.  The file was 2GB so I cleaned it out and started fresh.  Dunno.  :confused:

---

### Post by LowSky on 2010-05-02
Ok so Here's the Tutorial for using 10.04. 

I don't recommended using it, but maybe you will have better luck. I'm having a few issues with mythconverge, HDMI sound, andchanging channels without a tuner crashing. 

This is the update to the guide I posted a while ago. Most is very much the same but a few differences. 

_This driver only works for digital recording, sorry there is no analog support and please be careful using_.

**_*I am not responsible for the outcome of you using my tutorial.*_** This tutorial is based on my equipment and needs. If a setting I use does not work for you, I encourage people to post problems and/or solutions. This is not for people new to Linux, as it might break (and it might, as Mythbuntu 10.04 uses MythTV 0.23 which isn't a stable release version yet). I have placed little notes about certain thing to be careful of. If you see a number with a plus symbol (example: +47) look a few lines down for the note on this section.

If you really need to use this card for analog, try  Windows 7. The card is fully supported with that operating system.

These instructions are for using the Hauppauge WinTV-HVR-2250 in MythTV (also works on HVR-2200 or any video capture card using the SAA7164 chipset).

This Tutorial is for Mythbuntu 10.04 but may work for versions of *buntu 8.10 and higher. Versions 8.04 and lower will not work because of the required kernel support for the drivers. +1

 +1 Mythbuntu 10.04 uses MythTV 0.23, which as of May 1, 2010 is not a stable release. If you experience problems using Mythbuntu 9.10 might be a better option for you.



[SIZE="3"]Let's Get Started[/SIZE]


1. Open a Terminal

You will need to install these applications to install the drivers and firmware
```
sudo apt-get install mercurial libncurses5-dev unzip
```  

2. This next part is to download and install the firmware. Download them to your /home/user folder and not the desktop.

To change directories
```
cd /home/username
```

Now download the firmware
```

wget http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip
wget http://www.steventoth.net/linux/hvr22xx/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
wget http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw
wget http://www.steventoth.net/linux/hvr22xx/extract.sh
```


The next commands will extract the files and the copy them to Mythbuntu's /lib/firmware folder
```
sh extract.sh
sudo cp *fw /lib/firmware

```

3a. This part is for people using a version of Ubuntu 8.10 - 9.10. 10.04 alredy has the driver install. 10.04 users should know that if the drivers become updated before a new Linux Kernel release they can use this method for installation. If you are using 10.04 you may skip to step 3b. You may wish to use this step to install a newer kernel driver than the one included in 10.04.
```
lspci
```
If see a line that says Phillips SAA-7164 or something close to that, you can skip to instruction 3b.

Next we need download the driver using these command to fetch and install, I'm using the stable branch from Kernel labs, but you can use Linuxtv.org version if you wish.
```
hg clone http://kernellabs.com/hg/saa7164-stable/
```

now change to the directory:
```
cd saa7164-stable
```

Then run the command make:
```
make CONFIG_DVB_FIREDTV:=n
```

That will take some time, go grab a drink and wait it out, when it completes run this command:
```
sudo make install
```

3b. Next Reboot the system to insure the driver and firmware are installed and running:
```
sudo reboot
```

4. To get the card running open the MythTV Backend Setup (Applications>System>MythTV Backend Setup)

Once it  is running go to Capture Cards, choice #2.
Choose new capture card, you will have to do this step twice (this card has two tuners)
At card Type, pick DTB DTV.
The first will be device number 0, 
Repeat choosing capture card to add the second tuner. The second device will be  number 1 (Linux starts counting at 0, a good thing to know, especially for hard drives).** Important but I'm not at the machine at the time of edit.** There is a menu here once you choose the adapter, one is for satellites the other for tuner options I think. Choose the tuner options, or the one on the right of satellite optins, Make sure the number of tuners or recordings (sorry drawing a blank) numbered 1, and not 2 like it is by default. The system will think each tuner is two tuners (total of 4...its messy). This will cause recordings to fail if you don't.

5. Go to video sources, pick your options, I had to setup an account with SchedulesDirect.org, so that I could get local channel guide information in the USA. Your country may have other options.

6. Next go to Input Connections, again you will have 0 and 1, configure for both.

7. Edit channels and directories as needed. Sorry I can't really help with this. A word of suggestion is learn the directories that data is stored. If you setup your machine and didn't use the entire disk, make sure to change the directories for recorded data as they will fill the root partition if you are not careful. Remember that the directories you create need to have write access for the MythTV group. Since my /home directory was on a separate 500GB hard drive I wanted to use that. I created a Folder named within the /home/mythtv/ folder. I added over 80 or so hours of record time doing this. I found out 1.2TB is roughly 200+ hours of recording time for HD video.

8. Close MythTV Backend by hitting ESC, it will then ask to fill the database, let it. The Database will take a good amount of time, and may look like it is running in a loop. Don't worry its collecting data for 14 days worth of channel listings if you used ShedulesDirect.org. This may take up to a half hour. The more channels you have the longer. 

9. Now go to Applications >Multimedia > MythTV Frontend.

The next part is from my setup, but for many it might be required (I would love feedback).

First go to Utilities / Setup, its the last option. Choose Setup, then Appearance.

The first page is to choose your theme (A little about me: my choice is MythCenter-wide).
Next page is important: If you have more than one monitor, pick the one you want to display the GUI on. The second is the Monitor Aspect Ratio, be sure to set it to your TV or monitor's correct display size, Mine is 16:9 your's may be 16:10 or 4:3. A good rule of thumb I follow is most HDTV's are 16:9, most PC monitors are 16:10, SDTV is 4:3. Failure to set this might result in a horrible picture. Also on this page is to hide the mouse cursor. If you want to use a mouse over a keyboard or remote, then uncheck the box.
The next few pages I don't touch, sorry your on your own if you want to edit those.

10. Now back to  Utilities / Setup > Setup

Choose TV Settings. Again for most of this its all your preference. But one thing I found odd and I needed it fixed. On the Page 3/8 (labeled Playback Profiles), I had to set the Current Video Playback Profile to High Quality(+2). If I didn't I got a TV screen showing the image twice as if playing a FPS like GoldenEye in multiplayer. I'm know, I'm dating myself, but that game rocked back in the day. Anyway; go to the main menu and try to watch live TV. If you are using HDMI output on your TV and there is no sound, don't panic just yet, keep reading, I'm getting to that.

+2 If you are using Nvidia graphics card choosing, VDPUA might be a good option. I have an ATI video card so I have no idea if this works as it should. (again: feedback please)

11. This next part is for users who need sound through HDMI.
Right now I only have sound working with MythTV using this part of the Tutorial. Sound isn't working for the regular desktop through the HDMI feed, so if you are using this for a PC that will be used for web browsing or services like Hulu Desktop, you will need a set of speakers or headphones plugged into the normal stereo jack on your PC for that to work.  If your HDTV has a VGA port using that with a speaker connection or have a dual monitor set up and/or desktop speakers will get around this issue as well. I have instructions for certain newer Nvidia card on 11b.

**So that I'm clear: This is really for those who are only looking to use MythTV (and MythTV only) on their Mythbuntu setup and need HDMI sound.**

11a. Exit MythTV, and Go to Applications>Multimedia>Sound Mixer

In the drop down box pick you HDMI output
Make sure the option for IEC958 or whatever is checked, then close the Mixer.

Next open a Terminal, we will now check for what channel your HDMI device is using for playback.
```
aplay -l
```
look for the data that has HDMI in the title, on mine it was 
```
Card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
Now we need to add the next few lines to the asound.conf file, the file is normally empty, so be sure your editing the correct file.
[code]sudo nano /etc/asound.conf
```
```

  ctl.!default {
     type hw
     card 1
  }
```
NOTE: My card was card 1, yours might be different. 

Then reboot the system (+3). Then restart MythTV frontend. Go into  Utilities / Setup > General. Hit next until you get to the 4th screen the page's title is: Audio System.

Now we need to change the line named Audio output device to

```
ALSA:plughw:x,y
```
x is the sound card number from the asound -l command.
y is the device number from the asound -l command.
For example here is mine
```
ALSA:plughw:1,3
```

+3 Another issue currently is that the Tuner card will only work if you first start up the MythTV backend after a reboot or powering on so that the tuner card will work. If anyone can help me with this part. That would be great. I cant seem to find a way around this, but I leave my system on 24/7 so its a small problem.  **This issue is resolved if you upgrade MythTV to version .23.1.** Use the Mythbuntu Autobuild package from their website to upgrade or the 23.1 PPA.


11b. > **jjwest85 said:**
> ...For anyone with an nVidia card and not able to get sound to go through their HDMI cable and does not even show HDMI or digital as an option in sound preferences this may be able to help:

1.  Add "ppa:ubuntu-audio-dev/ppa" to the repository in synaptic.  Refresh synaptic.

2.  Upgrade all the pulse-audio packages

3. find out your kernel version:  type "uname -r" in a terminal.  Mine came out to be 2.6.32-21-generic (default ubuntu 10.04).  

4.  install "linux-alsa-driver-modules-2.6.32-21-generic" (your kernel may be different).  

I got this package from a launchpad bug that listed it as a possible fix to the dreaded sound through HDMI cables problem.  Installing this package gave me the options in sound preferences to choose digital sound/HDMI (IEC958 ).  I'm not 100% sure that being able to see IEC958 in sound preferences came right after updating all pulse-audio packages or if it only came after installing this package.  

I did also have to change some sound setting on MythTV's frontend.  Go to Utilities/Setup -> General -> Audio system -> Audio output device -> change to ALSA:spdif

Let me know if anyone else had/has this problem



Other options that MythTV includes are all up to you, hopefully following this guide gives you a working system. If not ask a question and I or someone else on the forums will answer it.

You should now be able to watch/record TV.



A Few Things:

I must say the Linux HTPC community is way too technical for many people, they need to make these things simpler, Windows 7 MCE is 10 times better at setting up these things, oh and it supports this tuner completely so if you want or need Analog support, right now Windows is the answer for people who want things to "just work". Think about the cost, as Windows Home Premium  is about $100US for an OEM copy, and while Mythbuntu is free, the channel guide from ScheduleDirect.org is $20US a year. So if you expect 5 years from your machine and don't want to worry about an update breaking the system then Windows pays for itself. I like using MythTV over Windows Media Center for a few reasons, the first being no DRM, the second being better network options. Lastly I turn updates off once the system is running to ensure nothing changes. You might not think its a safe option but for a system that is working properly and is not used for other purposes its more than likely fine.

A special thanks to Steven over at [KernelLabs]("http://www.kernellabs.com/blog/?page_id=17"), the person who made the drivers.


**[SIZE="3"]Sources[/SIZE]**
[http://www.linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers)
[http://www.kernellabs.com/blog/?page_id=17](http://www.kernellabs.com/blog/?page_id=17)
[http://kernellabs.com/hg/saa7164-stable/](http://kernellabs.com/hg/saa7164-stable/)
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)
[http://www.linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers#Using_Mercurial](http://www.linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers#Using_Mercurial)
[http://www.steventoth.net/blog/products/hvr-2250/](http://www.steventoth.net/blog/products/hvr-2250/)
[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200)

---

### Post by dividehex on 2010-05-03
Once again, Great instructions!  One thing I would like to point out is I did not have to download/compile/install the driver source since the default kernel (2.6.32-21) with 10.04 already has it.  The only thing I had to do was download/unzip/install the firmware.  Once I did that, the card was detected and initialized properly on reboot.

BTW, running on HVR-2250 with only one tuner setup in mythtv is going strong with 5 days uptime. This is the longest uptime I've ever seen on my hvr-2250+mythtv system.

---

### Post by LowSky on 2010-05-03
> **dividehex said:**
> Once again, Great instructions!  One thing I would like to point out is I did not have to download/compile/install the driver source since the default kernel (2.6.32-21) with 10.04 already has it.  The only thing I had to do was download/unzip/install the firmware.  Once I did that, the card was detected and initialized properly on reboot.

BTW, running on HVR-2250 with only one tuner setup in mythtv is going strong with 5 days uptime. This is the longest uptime I've ever seen on my hvr-2250+mythtv system.

Thanks for the info. Any reason why the other tuner isn't working? my own system wouldnt keep stable using 10.04 so I reverted back to 9.10. Things like sound over HDMI and channel changing were more important. I left the driver info in because at anytime new drivers could come out supporting the analog capabilities.  Maybe i'll fix that part so that its more universal. We will see. This thing cost me my whole weekend, I need some sleep!

---

### Post by dividehex on 2010-05-03
>  Any reason why the other tuner isn't working?
It really isn't an issue of my second tuner not working. In fact, both tuners work fine by the driver point of view.  I purposely did not configure the second tuner to show that the i2c errors were only triggered when both tuners would record. Since I only configured one tuner and therefore can record only one thing at a time the system has be very stable.  If I were to configure the second tuner and wait for the hvr-2250 to begin recording from both tuners, the driver would inevitably crash and flood the kern.log with i2c errors.  When I have some time, I will see it if I can force the i2c errors outside of mythtv.  If I can recreate the errors manual, I will send Steve an email with the info in the hopes that he might spare some of his time to find and fix the issue.

---

### Post by tjbron on 2010-05-03
dividehex,
For what it's worth, I set up that script to beep at me when the i2c read errors start showing up in the kern.log.  What I discovered is that I get them occasionally even when the tuners are still working.  Just thought that was interesting.

---

### Post by dividehex on 2010-05-03
> **tjbron said:**
> dividehex,
For what it's worth, I set up that script to beep at me when the i2c read errors start showing up in the kern.log.  What I discovered is that I get them occasionally even when the tuners are still working.  Just thought that was interesting.

1. Out of curiosity, when was the last time you updated the saa-7164 driver?
2. Also, when you say you get i2c errors occasionally when both tuners are working, do you mean when both tuners are recording at the same time or when both tuners are configured but only one is recording?
3. Last, when you get an i2c error does the card stop working and then flood kern.log with more i2c errors or does it just report a few errors and then continue working?

---

### Post by tjbron on 2010-05-03
> **dividehex said:**
> 1. Out of curiosity, when was the last time you updated the saa-7164 driver?
2. Also, when you say you get i2c errors occasionally when both tuners are working, do you mean when both tuners are recording at the same time or when both tuners are configured but only one is recording?
3. Last, when you get an i2c error does the card stop working and then flood kern.log with more i2c errors or does it just report a few errors and then continue working?
 
1. yeesh, uh, I don't think I've touched it since I built the system. Early 2009 maybe? I can check the version.
 
2. Sorry, I meant both tuners are configured. At the time I noticed the errors, I would have been recording on only one or none, however I do make use of the over-the-air schedule. So that could make things more convoluted. It very well may have been using both tuners (one for recording, one for OTA schedule).
 
3. In the past, I have only looked at the kern.log when it was flooding with errors, so I assumed that was the only time it happened. Last night after I set up the alarm script, it was beeping at me (a few kern.log i2c errors within a few minutes) but the tuners seemed to be working still. I could still go to live tv, for instance.
 
I will correlate my myth and kern logs and try to figure out the circumstances of the error message.
 
Thanks for being involved in this, by the way. For awhile, I couldn't find anyone else who was having these issues and I figured it was just because it was my first linux system.

---

### Post by kuehlc on 2010-05-03
> **tjbron said:**
> 1. yeesh, uh, I don't think I've touched it since I built the system. Early 2009 maybe? I can check the version.
 
2. Sorry, I meant both tuners are configured. At the time I noticed the errors, I would have been recording on only one or none, however I do make use of the over-the-air schedule. So that could make things more convoluted. It very well may have been using both tuners (one for recording, one for OTA schedule).
 
3. In the past, I have only looked at the kern.log when it was flooding with errors, so I assumed that was the only time it happened. Last night after I set up the alarm script, it was beeping at me (a few kern.log i2c errors within a few minutes) but the tuners seemed to be working still. I could still go to live tv, for instance.
 
I will correlate my myth and kern logs and try to figure out the circumstances of the error message.
 
Thanks for being involved in this, by the way. For awhile, I couldn't find anyone else who was having these issues and I figured it was just because it was my first linux system.

Well you are definitely not alone as I'm having the same issue. I haven't had a ton of time to debug this but have been watching your thread for awhile. I did email Steve Toth regarding this a few weeks ago and was surprised to get a prompt response asking if I was running the current version. I replied that I hadn't seen any changes in the driver that seemed relevant so I hadn't updated anything. To that I received the reply "so thats a no then?" and haven't heard anything else.

Is anyone seeing this error in 10.04 with the new driver in the kernel?

---

### Post by dividehex on 2010-05-03
> **kuehlc said:**
> Is anyone seeing this error in 10.04 with the new driver in the kernel?

Yes, I have been running 10.04 with the stock driver and it is the same problem i had with the previous ubuntu versions.

---

### Post by tjbron on 2010-05-03
> **tjbron said:**
> 1. yeesh, uh, I don't think I've touched it since I built the system. Early 2009 maybe? I can check the version.[COLOR=RoyalBlue]
Update:  I installed the driver in July 2009, running the jackalope.
[/COLOR]  
2. Sorry, I meant both tuners are configured. At the time I noticed the errors, I would have been recording on only one or none, however I do make use of the over-the-air schedule. So that could make things more convoluted. It very well may have been using both tuners (one for recording, one for OTA schedule).
[COLOR=RoyalBlue]Update: it was ticking away the errors this evening while the tuners were still operational.  I was not running them, but the OTA schedule may have been updating.  kern.log included below.[/COLOR]
 
3. In the past, I have only looked at the kern.log when it was flooding with errors, so I assumed that was the only time it happened. Last night after I set up the alarm script, it was beeping at me (a few kern.log i2c errors within a few minutes) but the tuners seemed to be working still. I could still go to live tv, for instance.
 
I will correlate my myth and kern logs and try to figure out the circumstances of the error message.
 


Hopefully this is helpful to someone.  If you scroll down a bit you will start seeing read as well as write errors (i2c).  My tuners were still operational during this.
Thanks again.
```

May  3 17:17:18 bronson-myth kernel: [    6.509069] lirc_mceusb2[2]: Topseed Technology Corp. eHome Infrared Transceiver on usb2:2
May  3 17:17:18 bronson-myth kernel: [    6.509120] usbcore: registered new interface driver lirc_mceusb2
May  3 17:17:18 bronson-myth kernel: [    6.588198] Linux agpgart interface v0.103
May  3 17:17:18 bronson-myth kernel: [    6.910058] ACPI: I/O resource piix4_smbus [0x400-0x407] conflicts with ACPI region SM00 [0x400-0x407]
May  3 17:17:18 bronson-myth kernel: [    6.910062] ACPI: Device needs an ACPI driver
May  3 17:17:18 bronson-myth kernel: [    6.910069] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x400, revision 0
May  3 17:17:18 bronson-myth kernel: [    6.932151] ppdev: user-space parallel port driver
May  3 17:17:18 bronson-myth kernel: [    6.975825] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
May  3 17:17:18 bronson-myth kernel: [    7.453541] psmouse serio1: ID: 10 00 64<4>nvidia: module license 'NVIDIA' taints kernel.
May  3 17:17:18 bronson-myth kernel: [    7.893632] nvidia 0000:02:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
May  3 17:17:18 bronson-myth kernel: [    7.899690] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.20  Thu Jun 25 19:23:24 PDT 2009
May  3 17:17:18 bronson-myth kernel: [    7.954185] saa7164 driver loaded
May  3 17:17:18 bronson-myth kernel: [    7.954313] saa7164 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
May  3 17:17:18 bronson-myth kernel: [    7.954610] CORE saa7164[0]: dev->lmmio  = 0xe0b00000
May  3 17:17:18 bronson-myth kernel: [    7.954611] CORE saa7164[0]: dev->lmmio2 = 0xe1980000
May  3 17:17:18 bronson-myth kernel: [    7.954613] CORE saa7164[0]: dev->bmmio  = 0xe0b00000
May  3 17:17:18 bronson-myth kernel: [    7.954615] CORE saa7164[0]: dev->bmmio2 = 0xe1980000
May  3 17:17:18 bronson-myth kernel: [    7.954617] CORE saa7164[0]: subsystem: 0070:8891, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
May  3 17:17:18 bronson-myth kernel: [    7.954623] saa7164[0]/0: found at 0000:01:00.0, rev: 129, irq: 18, latency: 0, mmio: 0xfd800000
May  3 17:17:18 bronson-myth kernel: [    7.954629] saa7164 0000:01:00.0: setting latency timer to 64
May  3 17:17:18 bronson-myth kernel: [    8.051033] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
May  3 17:17:18 bronson-myth kernel: [    8.092479] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
May  3 17:17:18 bronson-myth kernel: [    8.120026] saa7164_downloadfirmware() no first image
May  3 17:17:18 bronson-myth kernel: [    8.120038] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
May  3 17:17:18 bronson-myth kernel: [    8.120042] saa7164 0000:01:00.0: firmware: requesting v4l-saa7164-1.0.3.fw
May  3 17:17:18 bronson-myth kernel: [   10.327185] saa7164_downloadfirmware() firmware read 3978608 bytes.
May  3 17:17:18 bronson-myth kernel: [   10.327188] saa7164_downloadfirmware() firmware loaded.
May  3 17:17:18 bronson-myth kernel: [   10.327190] Firmware file header part 1:
May  3 17:17:18 bronson-myth kernel: [   10.327191]  .FirmwareSize = 0x0
May  3 17:17:18 bronson-myth kernel: [   10.327192]  .BSLSize = 0x0
May  3 17:17:18 bronson-myth kernel: [   10.327194]  .Reserved = 0x3cb57
May  3 17:17:18 bronson-myth kernel: [   10.327195]  .Version = 0x3
May  3 17:17:18 bronson-myth kernel: [   10.327196] saa7164_downloadfirmware() SecBootLoader.FileSize = 3978608
May  3 17:17:18 bronson-myth kernel: [   10.327202] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
May  3 17:17:18 bronson-myth kernel: [   10.327204] saa7164_downloadfirmware() BSLSize = 0x0
May  3 17:17:18 bronson-myth kernel: [   10.327205] saa7164_downloadfirmware() Reserved = 0x0
May  3 17:17:18 bronson-myth kernel: [   10.327207] saa7164_downloadfirmware() Version = 0x51cc1
May  3 17:17:18 bronson-myth kernel: [   11.381103] usb-storage: device scan complete
May  3 17:17:18 bronson-myth kernel: [   11.387089] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
May  3 17:17:18 bronson-myth kernel: [   11.393083] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
May  3 17:17:18 bronson-myth kernel: [   11.399079] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
May  3 17:17:18 bronson-myth kernel: [   11.405078] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
May  3 17:17:18 bronson-myth kernel: [   11.415238] sd 4:0:0:0: [sdb] Attached SCSI removable disk
May  3 17:17:18 bronson-myth kernel: [   11.415340] sd 4:0:0:0: Attached scsi generic sg2 type 0
May  3 17:17:18 bronson-myth kernel: [   11.427182] sd 4:0:0:1: [sdc] Attached SCSI removable disk
May  3 17:17:18 bronson-myth kernel: [   11.427292] sd 4:0:0:1: Attached scsi generic sg3 type 0
May  3 17:17:18 bronson-myth kernel: [   11.436271] sd 4:0:0:2: [sdd] Attached SCSI removable disk
May  3 17:17:18 bronson-myth kernel: [   11.436396] sd 4:0:0:2: Attached scsi generic sg4 type 0
May  3 17:17:18 bronson-myth kernel: [   11.456241] sd 4:0:0:3: [sde] Attached SCSI removable disk
May  3 17:17:18 bronson-myth kernel: [   11.456344] sd 4:0:0:3: Attached scsi generic sg5 type 0
May  3 17:17:18 bronson-myth kernel: [   17.184026] saa7164_downloadimage() Image downloaded, booting...
May  3 17:17:18 bronson-myth kernel: [   17.288017] saa7164_downloadimage() Image booted successfully.
May  3 17:17:18 bronson-myth kernel: [   17.288041] starting firmware download(2)
May  3 17:17:18 bronson-myth kernel: [   19.412025] saa7164_downloadimage() Image downloaded, booting...
May  3 17:17:18 bronson-myth kernel: [   21.076021] saa7164_downloadimage() Image booted successfully.
May  3 17:17:18 bronson-myth kernel: [   21.076042] firmware download complete.
May  3 17:17:18 bronson-myth kernel: [   21.076999] saa7164[0]: i2c bus 0 registered
May  3 17:17:18 bronson-myth kernel: [   21.077080] saa7164[0]: i2c bus 1 registered
May  3 17:17:18 bronson-myth kernel: [   21.077160] saa7164[0]: i2c bus 2 registered
May  3 17:17:18 bronson-myth kernel: [   21.112265] tveeprom 1-0000: Hauppauge model 88061, rev C3F2, serial# 6225133
May  3 17:17:18 bronson-myth kernel: [   21.112268] tveeprom 1-0000: MAC address is 00-0D-FE-5E-FC-ED
May  3 17:17:18 bronson-myth kernel: [   21.112270] tveeprom 1-0000: tuner model is NXP 18271C2_716x (idx 152, type 4)
May  3 17:17:18 bronson-myth kernel: [   21.112272] tveeprom 1-0000: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
May  3 17:17:18 bronson-myth kernel: [   21.112274] tveeprom 1-0000: audio processor is SAA7164 (idx 43)
May  3 17:17:18 bronson-myth kernel: [   21.112276] tveeprom 1-0000: decoder processor is SAA7164 (idx 40)
May  3 17:17:18 bronson-myth kernel: [   21.112278] tveeprom 1-0000: has radio, has IR receiver, has no IR transmitter
May  3 17:17:18 bronson-myth kernel: [   21.112280] saa7164[0]: Hauppauge eeprom: model=88061
May  3 17:17:18 bronson-myth kernel: [   21.505221] tda18271 2-0060: creating new instance
May  3 17:17:18 bronson-myth kernel: [   21.509576] TDA18271HD/C2 detected @ 2-0060
May  3 17:17:18 bronson-myth kernel: [   21.760963] DVB: registering new adapter (saa7164)
May  3 17:17:18 bronson-myth kernel: [   21.760970] DVB: registering adapter 0 frontend 611647248 (Samsung S5H1411 QAM/8VSB Frontend)...
May  3 17:17:18 bronson-myth kernel: [   22.045258] tda18271 3-0060: creating new instance
May  3 17:17:18 bronson-myth kernel: [   22.049734] TDA18271HD/C2 detected @ 3-0060
May  3 17:17:18 bronson-myth kernel: [   22.300741] DVB: registering new adapter (saa7164)
May  3 17:17:18 bronson-myth kernel: [   22.300748] DVB: registering adapter 1 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
May  3 17:17:18 bronson-myth kernel: [   22.401630] lp0: using parport0 (interrupt-driven).
May  3 17:17:18 bronson-myth kernel: [   22.608972] Adding 2385644k swap on /dev/sda4.  Priority:-1 extents:1 across:2385644k
May  3 17:17:18 bronson-myth kernel: [   23.239565] EXT3 FS on sda2, internal journal
May  3 17:17:18 bronson-myth kernel: [   24.129254] kjournald starting.  Commit interval 5 seconds
May  3 17:17:18 bronson-myth kernel: [   24.129525] EXT3 FS on sda3, internal journal
May  3 17:17:18 bronson-myth kernel: [   24.129530] EXT3-fs: mounted filesystem with ordered data mode.
May  3 17:17:18 bronson-myth kernel: [   24.602595] type=1505 audit(1272932236.482:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1996
May  3 17:17:18 bronson-myth kernel: [   24.602743] type=1505 audit(1272932236.482:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1996
May  3 17:17:18 bronson-myth kernel: [   24.602788] type=1505 audit(1272932236.482:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1996
May  3 17:17:18 bronson-myth kernel: [   24.602830] type=1505 audit(1272932236.482:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1996
May  3 17:17:18 bronson-myth kernel: [   24.747091] type=1505 audit(1272932236.626:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2001
May  3 17:17:18 bronson-myth kernel: [   24.747296] type=1505 audit(1272932236.626:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2001
May  3 17:17:18 bronson-myth kernel: [   24.774153] type=1505 audit(1272932236.654:8): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2005
May  3 17:17:18 bronson-myth kernel: [   24.800814] type=1505 audit(1272932236.682:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2009
May  3 17:17:18 bronson-myth kernel: [   26.809399] slamr: SmartLink AMRMO modem.
May  3 17:17:18 bronson-myth kernel: [   26.809416] slamr: device 1057:3052 is grabbed by another driver
May  3 17:17:28 bronson-myth kernel: [   36.396796] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
May  3 17:17:28 bronson-myth kernel: [   36.396799] Bluetooth: BNEP filters: protocol multicast
May  3 17:17:28 bronson-myth kernel: [   36.418773] Bridge firewalling registered
May  3 17:17:29 bronson-myth kernel: [   37.296571] tda18271: performing RF tracking filter calibration
May  3 17:17:32 bronson-myth kernel: [   40.501767] tda18271: RF tracking filter calibration complete
May  3 17:17:34 bronson-myth kernel: [   42.118249] eth0: link down
May  3 17:17:34 bronson-myth kernel: [   42.118358] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  3 17:17:34 bronson-myth kernel: [   42.164020] Event timed out
May  3 17:17:34 bronson-myth kernel: [   42.164026] saa7164_api_i2c_write() error, ret(1) = 0x32
May  3 17:17:34 bronson-myth kernel: [   42.164030] s5h1411_writereg: writereg error 0x19 0x3e 0x77ee, ret == -5)
May  3 17:17:34 bronson-myth kernel: [   42.164455] found timed out command on the bus
May  3 17:17:34 bronson-myth kernel: [   42.164483] ret = 0
May  3 17:17:34 bronson-myth kernel: [   42.164484]  timeout continue
May  3 17:17:34 bronson-myth kernel: [   42.465264] tda18271: performing RF tracking filter calibration
May  3 17:17:36 bronson-myth kernel: [   44.921844] tda18271: RF tracking filter calibration complete
May  3 17:18:37 bronson-myth kernel: [  105.992203] Clocksource tsc unstable (delta = -272837835 ns)
May  3 17:44:11 bronson-myth kernel: [ 1639.164030] Event timed out
May  3 17:44:11 bronson-myth kernel: [ 1639.164039] saa7164_api_i2c_read() error, ret(1) = 0x32
May  3 17:44:11 bronson-myth kernel: [ 1639.164045] s5h1411_readreg: readreg error (ret == -5)
May  3 17:44:11 bronson-myth kernel: [ 1639.164495] found timed out command on the bus
May  3 17:44:11 bronson-myth kernel: [ 1639.164525] ret = 0
May  3 17:44:11 bronson-myth kernel: [ 1639.164528]  timeout continue
May  3 17:45:17 bronson-myth kernel: [ 1705.736028] Event timed out
May  3 17:45:17 bronson-myth kernel: [ 1705.736037] saa7164_api_i2c_write() error, ret(2) = 0x32
May  3 17:45:17 bronson-myth kernel: [ 1705.736044] s5h1411_writereg: writereg error 0x19 0xf5 0x0000, ret == -5)
May  3 17:45:17 bronson-myth kernel: [ 1705.736455] found timed out command on the bus
May  3 17:45:17 bronson-myth kernel: [ 1705.736688] ret = 0
May  3 17:45:17 bronson-myth kernel: [ 1705.736690]  timeout continue
May  3 17:55:51 bronson-myth kernel: [ 2339.784037] Event timed out
May  3 17:55:51 bronson-myth kernel: [ 2339.784047] saa7164_api_i2c_read() error, ret(2) = 0x32
May  3 17:55:51 bronson-myth kernel: [ 2339.784053] s5h1411_readreg: readreg error (ret == -5)
May  3 17:55:51 bronson-myth kernel: [ 2339.784467] found timed out command on the bus
May  3 17:55:51 bronson-myth kernel: [ 2339.784699] ret = 0
May  3 17:55:51 bronson-myth kernel: [ 2339.784702]  timeout continue
May  3 17:59:16 bronson-myth kernel: [ 2544.568034] Event timed out
May  3 17:59:16 bronson-myth kernel: [ 2544.568044] saa7164_api_i2c_read() error, ret(2) = 0x32
May  3 17:59:16 bronson-myth kernel: [ 2544.568050] s5h1411_readreg: readreg error (ret == -5)
May  3 17:59:16 bronson-myth kernel: [ 2544.568495] found timed out command on the bus
May  3 17:59:16 bronson-myth kernel: [ 2544.568727] ret = 0
May  3 17:59:16 bronson-myth kernel: [ 2544.568730]  timeout continue
May  3 18:12:36 bronson-myth kernel: [ 3344.956059] Event timed out
May  3 18:12:36 bronson-myth kernel: [ 3344.956069] saa7164_api_i2c_read() error, ret(2) = 0x32
May  3 18:12:36 bronson-myth kernel: [ 3344.956076] tda18271_read_regs: ERROR: i2c_transfer returned: -5
May  3 18:12:36 bronson-myth kernel: [ 3344.957163] found timed out command on the bus
May  3 18:12:36 bronson-myth kernel: [ 3344.957303] ret = 0
May  3 18:12:36 bronson-myth kernel: [ 3344.957306]  timeout continue
May  3 18:24:17 bronson-myth kernel: [ 4045.536032] Event timed out
May  3 18:24:17 bronson-myth kernel: [ 4045.536042] saa7164_api_i2c_read() error, ret(2) = 0x32
May  3 18:24:17 bronson-myth kernel: [ 4045.536047] s5h1411_readreg: readreg error (ret == -5)
May  3 18:24:17 bronson-myth kernel: [ 4045.536759] found timed out command on the bus
May  3 18:24:17 bronson-myth kernel: [ 4045.536993] ret = 0
May  3 18:24:17 bronson-myth kernel: [ 4045.536996]  timeout continue
May  3 18:44:00 bronson-myth kernel: [ 5228.964038] Event timed out
May  3 18:44:00 bronson-myth kernel: [ 5228.964048] saa7164_api_i2c_read() error, ret(1) = 0x32
May  3 18:44:00 bronson-myth kernel: [ 5228.964054] s5h1411_readreg: readreg error (ret == -5)
May  3 18:44:00 bronson-myth kernel: [ 5228.964489] found timed out command on the bus
May  3 18:44:00 bronson-myth kernel: [ 5228.964523] ret = 0
May  3 18:44:00 bronson-myth kernel: [ 5228.964525]  timeout continue
May  3 19:39:28 bronson-myth kernel: [ 8556.524030] Event timed out
May  3 19:39:28 bronson-myth kernel: [ 8556.524040] saa7164_api_i2c_read() error, ret(2) = 0x32
May  3 19:39:28 bronson-myth kernel: [ 8556.524047] s5h1411_readreg: readreg error (ret == -5)
May  3 19:39:28 bronson-myth kernel: [ 8556.524526] found timed out command on the bus
May  3 19:39:28 bronson-myth kernel: [ 8556.524659] ret = 0
May  3 19:39:28 bronson-myth kernel: [ 8556.524662]  timeout continue
May  3 19:40:30 bronson-myth kernel: [ 8618.240030] Event timed out
May  3 19:40:30 bronson-myth kernel: [ 8618.240040] saa7164_api_i2c_read() error, ret(2) = 0x32
May  3 19:40:30 bronson-myth kernel: [ 8618.240046] s5h1411_readreg: readreg error (ret == -5)
May  3 19:40:30 bronson-myth kernel: [ 8618.240515] found timed out command on the bus
May  3 19:40:30 bronson-myth kernel: [ 8618.240648] ret = 0
May  3 19:40:30 bronson-myth kernel: [ 8618.240651]  timeout continue
May  3 19:40:31 bronson-myth kernel: [ 8619.404030] Event timed out
May  3 19:40:31 bronson-myth kernel: [ 8619.404039] saa7164_api_i2c_write() error, ret(2) = 0x32
May  3 19:40:31 bronson-myth kernel: [ 8619.404046] tda18271_write_regs: ERROR: i2c_transfer returned: -5
May  3 19:40:31 bronson-myth kernel: [ 8619.404838] found timed out command on the bus
May  3 19:40:31 bronson-myth kernel: [ 8619.404972] ret = 0
May  3 19:40:31 bronson-myth kernel: [ 8619.404974]  timeout continue
```

---

### Post by dividehex on 2010-05-04
Hmmm. Interesting. I wonder if these are two different bugs.  I've never gotten i2c errors without the card going completely fubar.  In my setup, I am connected to cable (comcast SF Bay Area) and not using OTA. I use schedule direct to get programming data.

Here is a snippet of my kern.log when it first begins.
```
Apr 26 23:09:14 mythtv kernel: [   17.301416] CPU1 attaching sched-domain:
Apr 26 23:09:14 mythtv kernel: [   17.301417]  domain 0: span 0-1 level MC
Apr 26 23:09:14 mythtv kernel: [   17.301419]   groups: 1 0
Apr 26 23:09:18 mythtv kernel: [   21.780249] saa7164_downloadimage() Image downloaded, booting...
Apr 26 23:09:18 mythtv kernel: [   21.890080] saa7164_downloadimage() Image booted successfully.
Apr 26 23:09:18 mythtv kernel: [   21.890105] starting firmware download(2)
Apr 26 23:09:21 mythtv kernel: [   24.230107] saa7164_downloadimage() Image downloaded, booting...
Apr 26 23:09:22 mythtv kernel: [   25.660061] saa7164_downloadimage() Image booted successfully.
Apr 26 23:09:22 mythtv kernel: [   25.660089] firmware download complete.
Apr 26 23:09:22 mythtv kernel: [   25.700421] tveeprom 4-0000: Hauppauge model 88061, rev C3F2, serial# 6236058
Apr 26 23:09:22 mythtv kernel: [   25.700425] tveeprom 4-0000: MAC address is 00-0D-FE-5F-27-9A
Apr 26 23:09:22 mythtv kernel: [   25.700427] tveeprom 4-0000: tuner model is NXP 18271C2_716x (idx 152, type 4)
Apr 26 23:09:22 mythtv kernel: [   25.700430] tveeprom 4-0000: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
Apr 26 23:09:22 mythtv kernel: [   25.700432] tveeprom 4-0000: audio processor is SAA7164 (idx 43)
Apr 26 23:09:22 mythtv kernel: [   25.700434] tveeprom 4-0000: decoder processor is SAA7164 (idx 40)
Apr 26 23:09:22 mythtv kernel: [   25.700437] tveeprom 4-0000: has radio, has IR receiver, has no IR transmitter
Apr 26 23:09:22 mythtv kernel: [   25.700439] saa7164[0]: Hauppauge eeprom: model=88061
Apr 26 23:09:22 mythtv kernel: [   26.098479] tda18271 5-0060: creating new instance
Apr 26 23:09:22 mythtv kernel: [   26.102797] TDA18271HD/C2 detected @ 5-0060
Apr 26 23:09:23 mythtv kernel: [   26.445053] DVB: registering new adapter (saa7164)
Apr 26 23:09:23 mythtv kernel: [   26.445060] DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
Apr 26 23:09:23 mythtv kernel: [   26.729896] tda18271 6-0060: creating new instance
Apr 26 23:09:23 mythtv kernel: [   26.734056] TDA18271HD/C2 detected @ 6-0060
Apr 26 23:09:23 mythtv kernel: [   26.740128] eth0: no IPv6 routers present
Apr 26 23:09:23 mythtv kernel: [   27.084739] tda18271: performing RF tracking filter calibration
Apr 26 23:09:26 mythtv kernel: [   29.717802] tda18271: RF tracking filter calibration complete
Apr 26 23:09:26 mythtv kernel: [   29.718073] DVB: registering new adapter (saa7164)
Apr 26 23:09:26 mythtv kernel: [   29.718079] DVB: registering adapter 1 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
Apr 26 23:10:14 mythtv kernel: [   78.011310] Clocksource tsc unstable (delta = -289910092 ns)
Apr 26 23:13:58 mythtv kernel: [  301.953817] CE: hpet increasing min_delta_ns to 15000 nsec
Apr 27 00:43:22 mythtv kernel: [ 5665.500599] tda18271: performing RF tracking filter calibration
Apr 27 00:43:25 mythtv kernel: [ 5668.139518] tda18271: RF tracking filter calibration complete
Apr 27 12:58:43 mythtv kernel: [49786.691293] CE: hpet increasing min_delta_ns to 22500 nsec
Apr 27 21:40:32 mythtv kernel: [81095.341654] Event timed out
Apr 27 21:40:32 mythtv kernel: [81095.341668] saa7164_api_i2c_read() error, ret(1) = 0x32
Apr 27 21:40:32 mythtv kernel: [81095.341676] s5h1411_readreg: readreg error (ret == -5)
Apr 27 21:40:32 mythtv kernel: [81095.710180] Event timed out
Apr 27 21:40:32 mythtv kernel: [81095.710194] saa7164_api_i2c_read() error, ret(1) = 0x32
Apr 27 21:40:32 mythtv kernel: [81095.710201] s5h1411_readreg: readreg error (ret == -5)
Apr 27 21:40:42 mythtv kernel: [81105.340173] Event timed out
Apr 27 21:40:42 mythtv kernel: [81105.340186] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 21:40:42 mythtv kernel: [81105.340196] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
Apr 27 21:40:42 mythtv kernel: [81105.710233] Event timed out
Apr 27 21:40:42 mythtv kernel: [81105.710247] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 21:40:42 mythtv kernel: [81105.710255] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
Apr 27 21:40:52 mythtv kernel: [81115.340066] Event timed out
Apr 27 21:40:52 mythtv kernel: [81115.340081] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 21:40:52 mythtv kernel: [81115.340089] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
Apr 27 21:40:52 mythtv kernel: [81115.710201] Event timed out
Apr 27 21:40:52 mythtv kernel: [81115.710214] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 21:40:52 mythtv kernel: [81115.710223] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
Apr 27 21:40:56 mythtv kernel: [81119.480196] Event timed out
Apr 27 21:40:56 mythtv kernel: [81119.480209] saa7164_api_transition_port() error, ret = 0x32
Apr 27 21:40:56 mythtv kernel: [81119.480215] saa7164_dvb_pause_tsport() pause transition failed, ret = 0x32
Apr 27 21:40:56 mythtv kernel: [81119.500218] Event timed out
Apr 27 21:40:56 mythtv kernel: [81119.500232] saa7164_api_transition_port() error, ret = 0x32
Apr 27 21:40:56 mythtv kernel: [81119.500238] saa7164_dvb_pause_tsport() pause transition failed, ret = 0x32
Apr 27 21:41:02 mythtv kernel: [81125.340047] Event timed out
Apr 27 21:41:02 mythtv kernel: [81125.340061] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 21:41:02 mythtv kernel: [81125.340070] s5h1411_writereg: writereg error 0x19 0xf5 0x0001, ret == -5)
Apr 27 21:41:02 mythtv kernel: [81125.710060] Event timed out
Apr 27 21:41:02 mythtv kernel: [81125.710080] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 21:41:02 mythtv kernel: [81125.710088] s5h1411_writereg: writereg error 0x19 0xf5 0x0001, ret == -5)
Apr 27 21:41:06 mythtv kernel: [81129.480216] Event timed out
Apr 27 21:41:06 mythtv kernel: [81129.480231] saa7164_api_transition_port() error, ret = 0x32
Apr 27 21:41:06 mythtv kernel: [81129.480238] saa7164_dvb_acquire_tsport() acquire transition failed, ret = 0x32
Apr 27 21:41:06 mythtv kernel: [81129.500172] Event timed out
Apr 27 21:41:06 mythtv kernel: [81129.500187] saa7164_api_transition_port() error, ret = 0x32
Apr 27 21:41:06 mythtv kernel: [81129.500193] saa7164_dvb_acquire_tsport() acquire transition failed, ret = 0x32
Apr 27 21:41:12 mythtv kernel: [81135.340076] Event timed out
Apr 27 21:41:12 mythtv kernel: [81135.340092] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 21:41:12 mythtv kernel: [81135.340101] tda18271_write_regs: ERROR: idx = 0x5, len = 1, i2c_transfer returned: -5
Apr 27 21:41:12 mythtv kernel: [81135.340108] tda18271_init: error -5 on line 826
Apr 27 21:41:12 mythtv kernel: [81135.340113] tda18271_tune: error -5 on line 904
Apr 27 21:41:12 mythtv kernel: [81135.340118] tda18271_set_params: error -5 on line 985
Apr 27 21:41:12 mythtv kernel: [81135.710069] Event timed out
Apr 27 21:41:12 mythtv kernel: [81135.710082] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 21:41:12 mythtv kernel: [81135.710091] tda18271_write_regs: ERROR: idx = 0x5, len = 1, i2c_transfer returned: -5
Apr 27 21:41:12 mythtv kernel: [81135.710098] tda18271_init: error -5 on line 826
Apr 27 21:41:12 mythtv kernel: [81135.710102] tda18271_tune: error -5 on line 904
Apr 27 21:41:12 mythtv kernel: [81135.710108] tda18271_set_params: error -5 on line 985
Apr 27 21:41:16 mythtv kernel: [81139.480059] Event timed out
Apr 27 21:41:16 mythtv kernel: [81139.480074] saa7164_api_transition_port() error, ret = 0x32
Apr 27 21:41:16 mythtv kernel: [81139.480079] saa7164_dvb_stop_tsport() stop transition failed, ret = 0x32
Apr 27 21:41:16 mythtv kernel: [81139.501622] Event timed out
Apr 27 21:41:16 mythtv kernel: [81139.501635] saa7164_api_transition_port() error, ret = 0x32
Apr 27 21:41:16 mythtv kernel: [81139.501641] saa7164_dvb_stop_tsport() stop transition failed, ret = 0x32
Apr 27 21:41:22 mythtv kernel: [81145.340049] Event timed out
Apr 27 21:41:22 mythtv kernel: [81145.340065] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 21:41:22 mythtv kernel: [81145.340074] s5h1411_writereg: writereg error 0x19 0xf5 0x0000, ret == -5)
Apr 27 21:41:22 mythtv kernel: [81145.710175] Event timed out
Apr 27 21:41:22 mythtv kernel: [81145.710190] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 21:41:22 mythtv kernel: [81145.710199] s5h1411_writereg: writereg error 0x19 0xf5 0x0000, ret == -5)
Apr 27 21:41:32 mythtv kernel: [81155.342056] Event timed out
Apr 27 21:41:32 mythtv kernel: [81155.342073] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 21:41:32 mythtv kernel: [81155.342082] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
Apr 27 21:41:32 mythtv kernel: [81155.710305] Event timed out
Apr 27 21:41:32 mythtv kernel: [81155.710319] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 21:41:32 mythtv kernel: [81155.710327] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
Apr 27 21:41:42 mythtv kernel: [81165.340448] Event timed out
Apr 27 21:41:42 mythtv kernel: [81165.340463] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 21:41:42 mythtv kernel: [81165.340472] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
Apr 27 21:41:42 mythtv kernel: [81165.710194] Event timed out
Apr 27 21:41:42 mythtv kernel: [81165.710213] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 21:41:42 mythtv kernel: [81165.710222] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
Apr 27 21:41:53 mythtv kernel: [81176.340105] Event timed out
Apr 27 21:41:53 mythtv kernel: [81176.340121] saa7164_api_i2c_read() error, ret(1) = 0x32
Apr 27 21:41:53 mythtv kernel: [81176.340130] s5h1411_readreg: readreg error (ret == -5)
Apr 27 21:41:53 mythtv kernel: [81176.710513] Event timed out
Apr 27 21:41:53 mythtv kernel: [81176.710529] saa7164_api_i2c_read() error, ret(1) = 0x32
Apr 27 21:41:53 mythtv kernel: [81176.710537] s5h1411_readreg: readreg error (ret == -5)
Apr 27 21:42:03 mythtv kernel: [81186.340372] Event timed out
Apr 27 21:42:03 mythtv kernel: [81186.340386] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 21:42:03 mythtv kernel: [81186.340395] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
Apr 27 21:42:03 mythtv kernel: [81186.711626] Event timed out
Apr 27 21:42:03 mythtv kernel: [81186.711640] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 21:42:03 mythtv kernel: [81186.711648] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
Apr 27 21:42:13 mythtv kernel: [81196.340041] Event timed out
Apr 27 21:42:13 mythtv kernel: [81196.340055] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 21:42:13 mythtv kernel: [81196.340063] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
Apr 27 21:42:13 mythtv kernel: [81196.710070] Event timed out
Apr 27 21:42:13 mythtv kernel: [81196.710093] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 21:42:13 mythtv kernel: [81196.710103] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
Apr 27 21:42:23 mythtv kernel: [81206.340063] Event timed out
Apr 27 21:42:23 mythtv kernel: [81206.340080] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 21:42:23 mythtv kernel: [81206.340089] s5h1411_writereg: writereg error 0x19 0xf5 0x0001, ret == -5)
Apr 27 21:42:23 mythtv kernel: [81206.710074] Event timed out
Apr 27 21:42:23 mythtv kernel: [81206.710088] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 21:42:23 mythtv kernel: [81206.710096] s5h1411_writereg: writereg error 0x19 0xf5 0x0001, ret == -5)
Apr 27 21:42:33 mythtv kernel: [81216.340215] Event timed out
Apr 27 21:42:33 mythtv kernel: [81216.340231] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 21:42:33 mythtv kernel: [81216.340240] tda18271_write_regs: ERROR: idx = 0x5, len = 1, i2c_transfer returned: -5
Apr 27 21:42:33 mythtv kernel: [81216.340246] tda18271_init: error -5 on line 826
Apr 27 21:42:33 mythtv kernel: [81216.340257] tda18271_tune: error -5 on line 904
Apr 27 21:42:33 mythtv kernel: [81216.340262] tda18271_set_params: error -5 on line 985
Apr 27 21:42:33 mythtv kernel: [81216.710049] Event timed out
Apr 27 21:42:33 mythtv kernel: [81216.710064] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 21:42:33 mythtv kernel: [81216.710073] tda18271_write_regs: ERROR: idx = 0x5, len = 1, i2c_transfer returned: -5
Apr 27 21:42:33 mythtv kernel: [81216.710079] tda18271_init: error -5 on line 826
Apr 27 21:42:33 mythtv kernel: [81216.710084] tda18271_tune: error -5 on line 904
Apr 27 21:42:33 mythtv kernel: [81216.710089] tda18271_set_params: error -5 on line 985
Apr 27 21:42:43 mythtv kernel: [81226.340399] Event timed out

```And here the errors seem to change... (maybe from mythtv trying to start a new recording?)
```
Apr 27 22:00:57 mythtv kernel: [82320.340090] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 22:00:57 mythtv kernel: [82320.340100] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
Apr 27 22:00:57 mythtv kernel: [82320.710355] Event timed out
Apr 27 22:00:57 mythtv kernel: [82320.710370] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 22:00:57 mythtv kernel: [82320.710379] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
Apr 27 22:01:07 mythtv kernel: [82330.341284] Event timed out
Apr 27 22:01:07 mythtv kernel: [82330.341299] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 22:01:07 mythtv kernel: [82330.341308] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
Apr 27 22:01:07 mythtv kernel: [82330.710306] Event timed out
Apr 27 22:01:07 mythtv kernel: [82330.710320] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 22:01:07 mythtv kernel: [82330.710329] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
Apr 27 22:01:17 mythtv kernel: [82340.341289] Event timed out
Apr 27 22:01:17 mythtv kernel: [82340.341306] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 22:01:17 mythtv kernel: [82340.341315] s5h1411_writereg: writereg error 0x19 0xf5 0x0001, ret == -5)
Apr 27 22:01:17 mythtv kernel: [82340.710117] Event timed out
Apr 27 22:01:17 mythtv kernel: [82340.710131] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 22:01:17 mythtv kernel: [82340.710140] s5h1411_writereg: writereg error 0x19 0xf5 0x0001, ret == -5)
Apr 27 22:01:27 mythtv kernel: [82350.340284] Event timed out
Apr 27 22:01:27 mythtv kernel: [82350.340299] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 22:01:27 mythtv kernel: [82350.340308] tda18271_write_regs: ERROR: idx = 0x5, len = 1, i2c_transfer returned: -5
Apr 27 22:01:27 mythtv kernel: [82350.340315] tda18271_init: error -5 on line 826
Apr 27 22:01:27 mythtv kernel: [82350.340320] tda18271_tune: error -5 on line 904
Apr 27 22:01:27 mythtv kernel: [82350.340325] tda18271_set_params: error -5 on line 985
Apr 27 22:01:27 mythtv kernel: [82350.340344] saa7164_cmd_send() No free sequences
Apr 27 22:01:27 mythtv kernel: [82350.340348] saa7164_api_i2c_write() error, ret(1) = 0xc
Apr 27 22:01:27 mythtv kernel: [82350.340353] s5h1411_writereg: writereg error 0x19 0xf5 0x0000, ret == -5)
Apr 27 22:01:27 mythtv kernel: [82350.340359] saa7164_cmd_send() No free sequences
Apr 27 22:01:27 mythtv kernel: [82350.340363] saa7164_api_i2c_write() error, ret(1) = 0xc
Apr 27 22:01:27 mythtv kernel: [82350.340368] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
Apr 27 22:01:27 mythtv kernel: [82350.340373] saa7164_cmd_send() No free sequences
Apr 27 22:01:27 mythtv kernel: [82350.340377] saa7164_api_i2c_write() error, ret(1) = 0xc
Apr 27 22:01:27 mythtv kernel: [82350.340382] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
Apr 27 22:01:27 mythtv kernel: [82350.710390] Event timed out
Apr 27 22:01:27 mythtv kernel: [82350.710405] saa7164_api_i2c_write() error, ret(1) = 0x32
Apr 27 22:01:27 mythtv kernel: [82350.710414] tda18271_write_regs: ERROR: idx = 0x5, len = 1, i2c_transfer returned: -5
Apr 27 22:01:27 mythtv kernel: [82350.710420] tda18271_init: error -5 on line 826
Apr 27 22:01:27 mythtv kernel: [82350.710425] tda18271_tune: error -5 on line 904
Apr 27 22:01:27 mythtv kernel: [82350.710431] tda18271_set_params: error -5 on line 985
Apr 27 22:01:27 mythtv kernel: [82350.710452] saa7164_cmd_send() No free sequences
Apr 27 22:01:27 mythtv kernel: [82350.710456] saa7164_api_i2c_write() error, ret(1) = 0xc
Apr 27 22:01:27 mythtv kernel: [82350.710462] s5h1411_writereg: writereg error 0x19 0xf5 0x0000, ret == -5)
Apr 27 22:01:27 mythtv kernel: [82350.710468] saa7164_cmd_send() No free sequences
Apr 27 22:01:27 mythtv kernel: [82350.710472] saa7164_api_i2c_write() error, ret(1) = 0xc
Apr 27 22:01:27 mythtv kernel: [82350.710477] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
Apr 27 22:01:27 mythtv kernel: [82350.710482] saa7164_cmd_send() No free sequences
Apr 27 22:01:27 mythtv kernel: [82350.710486] saa7164_api_i2c_write() error, ret(1) = 0xc
Apr 27 22:01:27 mythtv kernel: [82350.710490] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
Apr 27 22:01:28 mythtv kernel: [82351.341094] saa7164_cmd_send() No free sequences
Apr 27 22:01:28 mythtv kernel: [82351.341106] saa7164_api_i2c_read() error, ret(1) = 0xc
Apr 27 22:01:28 mythtv kernel: [82351.341111] s5h1411_readreg: readreg error (ret == -5)
Apr 27 22:01:28 mythtv kernel: [82351.341119] saa7164_cmd_send() No free sequences
Apr 27 22:01:28 mythtv kernel: [82351.341124] saa7164_api_i2c_write() error, ret(1) = 0xc
Apr 27 22:01:28 mythtv kernel: [82351.341130] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
Apr 27 22:01:28 mythtv kernel: [82351.341136] saa7164_cmd_send() No free sequences
Apr 27 22:01:28 mythtv kernel: [82351.341139] saa7164_api_i2c_write() error, ret(1) = 0xc

```

---

### Post by LowSky on 2010-05-04
tjbron do you get these error messages if you turn off OTA scheduling?


dividehex and tjbron are either of you using Power-saving features like suspend? What kind of hardware are you using, especially the Motherboard model? Its a long shot but some motherboards have BIOS enabled power saving modes that might be interfering with this card functioning optimally 

Lastly has anyone tried another Linux Distro, like Fedora, Debian KnoppMyth, or Opensuse? Dare I say Arch?

---

### Post by greensoap on 2010-05-04
In the interest of helping to debug things.  I mentioned that I was going to disable the OTA guide for each channel and use only Schedules Direct.  I did this 6 days ago and I have not had a single error or downtime since.  Using the mythweb interface I navigated to [http://ipaddress/mythweb/settings/tv/channels](http://ipaddress/mythweb/settings/tv/channels) and unchecked useonairguide for each individual channel.

I should mention that I am using just the hvr-2250 in my setup, unlike dividehex who is using two cards (the 1650? and 2250, I believe).

Also, like dividehex, I never received the i2c error (to my knowledge) without the entire card crashing.

Dividehex, in regards to the log changing, I believe there is a command buffer that fills up eventually and that is when the "no free sequences" start.  I don't think it has anything to do with a channel change or start of recording, just an internal buffer in the driver filling up after all the commands were buffered and not flushed because the commands are trying to execute and are timing out.

---

### Post by greensoap on 2010-05-04
One thing to note with tjbron's log, is that the errors are not occurring in rapid succession.  When this happened to me, I received blocks of error messages every ten seconds, which is what can be found in dividehex's log.  tjbron's log on the other hand has full minutes inbetween.  It seems that his system is "recovering" from the time out and able to reprocess the failed command without the card dying completely.  

Lastly, when I got these errors before, the only thing that corrected the issue was a reboot of my computer followed by a restart of myth-tv because for some reason myth-tv tends to start up before the hvr-2250 is initialized.

> **tjbron said:**
> Hopefully this is helpful to someone.  If you scroll down a bit you will start seeing read as well as write errors (i2c).  My tuners were still operational during this.
Thanks again.
```

May  3 17:17:18 bronson-myth kernel: [    6.509069] lirc_mceusb2[2]: Topseed Technology Corp. eHome Infrared Transceiver on usb2:2
May  3 17:17:18 bronson-myth kernel: [    6.509120] usbcore: registered new interface driver lirc_mceusb2
May  3 17:17:18 bronson-myth kernel: [    6.588198] Linux agpgart interface v0.103
May  3 17:17:18 bronson-myth kernel: [    6.910058] ACPI: I/O resource piix4_smbus [0x400-0x407] conflicts with ACPI region SM00 [0x400-0x407]
May  3 17:17:18 bronson-myth kernel: [    6.910062] ACPI: Device needs an ACPI driver
May  3 17:17:18 bronson-myth kernel: [    6.910069] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x400, revision 0
May  3 17:17:18 bronson-myth kernel: [    6.932151] ppdev: user-space parallel port driver
May  3 17:17:18 bronson-myth kernel: [    6.975825] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
May  3 17:17:18 bronson-myth kernel: [    7.453541] psmouse serio1: ID: 10 00 64<4>nvidia: module license 'NVIDIA' taints kernel.
May  3 17:17:18 bronson-myth kernel: [    7.893632] nvidia 0000:02:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
May  3 17:17:18 bronson-myth kernel: [    7.899690] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.20  Thu Jun 25 19:23:24 PDT 2009
May  3 17:17:18 bronson-myth kernel: [    7.954185] saa7164 driver loaded
May  3 17:17:18 bronson-myth kernel: [    7.954313] saa7164 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
May  3 17:17:18 bronson-myth kernel: [    7.954610] CORE saa7164[0]: dev->lmmio  = 0xe0b00000
May  3 17:17:18 bronson-myth kernel: [    7.954611] CORE saa7164[0]: dev->lmmio2 = 0xe1980000
May  3 17:17:18 bronson-myth kernel: [    7.954613] CORE saa7164[0]: dev->bmmio  = 0xe0b00000
May  3 17:17:18 bronson-myth kernel: [    7.954615] CORE saa7164[0]: dev->bmmio2 = 0xe1980000
May  3 17:17:18 bronson-myth kernel: [    7.954617] CORE saa7164[0]: subsystem: 0070:8891, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
May  3 17:17:18 bronson-myth kernel: [    7.954623] saa7164[0]/0: found at 0000:01:00.0, rev: 129, irq: 18, latency: 0, mmio: 0xfd800000
May  3 17:17:18 bronson-myth kernel: [    7.954629] saa7164 0000:01:00.0: setting latency timer to 64
May  3 17:17:18 bronson-myth kernel: [    8.051033] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
May  3 17:17:18 bronson-myth kernel: [    8.092479] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
May  3 17:17:18 bronson-myth kernel: [    8.120026] saa7164_downloadfirmware() no first image
May  3 17:17:18 bronson-myth kernel: [    8.120038] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
May  3 17:17:18 bronson-myth kernel: [    8.120042] saa7164 0000:01:00.0: firmware: requesting v4l-saa7164-1.0.3.fw
May  3 17:17:18 bronson-myth kernel: [   10.327185] saa7164_downloadfirmware() firmware read 3978608 bytes.
May  3 17:17:18 bronson-myth kernel: [   10.327188] saa7164_downloadfirmware() firmware loaded.
May  3 17:17:18 bronson-myth kernel: [   10.327190] Firmware file header part 1:
May  3 17:17:18 bronson-myth kernel: [   10.327191]  .FirmwareSize = 0x0
May  3 17:17:18 bronson-myth kernel: [   10.327192]  .BSLSize = 0x0
May  3 17:17:18 bronson-myth kernel: [   10.327194]  .Reserved = 0x3cb57
May  3 17:17:18 bronson-myth kernel: [   10.327195]  .Version = 0x3
May  3 17:17:18 bronson-myth kernel: [   10.327196] saa7164_downloadfirmware() SecBootLoader.FileSize = 3978608
May  3 17:17:18 bronson-myth kernel: [   10.327202] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
May  3 17:17:18 bronson-myth kernel: [   10.327204] saa7164_downloadfirmware() BSLSize = 0x0
May  3 17:17:18 bronson-myth kernel: [   10.327205] saa7164_downloadfirmware() Reserved = 0x0
May  3 17:17:18 bronson-myth kernel: [   10.327207] saa7164_downloadfirmware() Version = 0x51cc1
May  3 17:17:18 bronson-myth kernel: [   11.381103] usb-storage: device scan complete
May  3 17:17:18 bronson-myth kernel: [   11.387089] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
May  3 17:17:18 bronson-myth kernel: [   11.393083] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
May  3 17:17:18 bronson-myth kernel: [   11.399079] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
May  3 17:17:18 bronson-myth kernel: [   11.405078] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
May  3 17:17:18 bronson-myth kernel: [   11.415238] sd 4:0:0:0: [sdb] Attached SCSI removable disk
May  3 17:17:18 bronson-myth kernel: [   11.415340] sd 4:0:0:0: Attached scsi generic sg2 type 0
May  3 17:17:18 bronson-myth kernel: [   11.427182] sd 4:0:0:1: [sdc] Attached SCSI removable disk
May  3 17:17:18 bronson-myth kernel: [   11.427292] sd 4:0:0:1: Attached scsi generic sg3 type 0
May  3 17:17:18 bronson-myth kernel: [   11.436271] sd 4:0:0:2: [sdd] Attached SCSI removable disk
May  3 17:17:18 bronson-myth kernel: [   11.436396] sd 4:0:0:2: Attached scsi generic sg4 type 0
May  3 17:17:18 bronson-myth kernel: [   11.456241] sd 4:0:0:3: [sde] Attached SCSI removable disk
May  3 17:17:18 bronson-myth kernel: [   11.456344] sd 4:0:0:3: Attached scsi generic sg5 type 0
May  3 17:17:18 bronson-myth kernel: [   17.184026] saa7164_downloadimage() Image downloaded, booting...
May  3 17:17:18 bronson-myth kernel: [   17.288017] saa7164_downloadimage() Image booted successfully.
May  3 17:17:18 bronson-myth kernel: [   17.288041] starting firmware download(2)
May  3 17:17:18 bronson-myth kernel: [   19.412025] saa7164_downloadimage() Image downloaded, booting...
May  3 17:17:18 bronson-myth kernel: [   21.076021] saa7164_downloadimage() Image booted successfully.
May  3 17:17:18 bronson-myth kernel: [   21.076042] firmware download complete.
May  3 17:17:18 bronson-myth kernel: [   21.076999] saa7164[0]: i2c bus 0 registered
May  3 17:17:18 bronson-myth kernel: [   21.077080] saa7164[0]: i2c bus 1 registered
May  3 17:17:18 bronson-myth kernel: [   21.077160] saa7164[0]: i2c bus 2 registered
May  3 17:17:18 bronson-myth kernel: [   21.112265] tveeprom 1-0000: Hauppauge model 88061, rev C3F2, serial# 6225133
May  3 17:17:18 bronson-myth kernel: [   21.112268] tveeprom 1-0000: MAC address is 00-0D-FE-5E-FC-ED
May  3 17:17:18 bronson-myth kernel: [   21.112270] tveeprom 1-0000: tuner model is NXP 18271C2_716x (idx 152, type 4)
May  3 17:17:18 bronson-myth kernel: [   21.112272] tveeprom 1-0000: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
May  3 17:17:18 bronson-myth kernel: [   21.112274] tveeprom 1-0000: audio processor is SAA7164 (idx 43)
May  3 17:17:18 bronson-myth kernel: [   21.112276] tveeprom 1-0000: decoder processor is SAA7164 (idx 40)
May  3 17:17:18 bronson-myth kernel: [   21.112278] tveeprom 1-0000: has radio, has IR receiver, has no IR transmitter
May  3 17:17:18 bronson-myth kernel: [   21.112280] saa7164[0]: Hauppauge eeprom: model=88061
May  3 17:17:18 bronson-myth kernel: [   21.505221] tda18271 2-0060: creating new instance
May  3 17:17:18 bronson-myth kernel: [   21.509576] TDA18271HD/C2 detected @ 2-0060
May  3 17:17:18 bronson-myth kernel: [   21.760963] DVB: registering new adapter (saa7164)
May  3 17:17:18 bronson-myth kernel: [   21.760970] DVB: registering adapter 0 frontend 611647248 (Samsung S5H1411 QAM/8VSB Frontend)...
May  3 17:17:18 bronson-myth kernel: [   22.045258] tda18271 3-0060: creating new instance
May  3 17:17:18 bronson-myth kernel: [   22.049734] TDA18271HD/C2 detected @ 3-0060
May  3 17:17:18 bronson-myth kernel: [   22.300741] DVB: registering new adapter (saa7164)
May  3 17:17:18 bronson-myth kernel: [   22.300748] DVB: registering adapter 1 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
May  3 17:17:18 bronson-myth kernel: [   22.401630] lp0: using parport0 (interrupt-driven).
May  3 17:17:18 bronson-myth kernel: [   22.608972] Adding 2385644k swap on /dev/sda4.  Priority:-1 extents:1 across:2385644k
May  3 17:17:18 bronson-myth kernel: [   23.239565] EXT3 FS on sda2, internal journal
May  3 17:17:18 bronson-myth kernel: [   24.129254] kjournald starting.  Commit interval 5 seconds
May  3 17:17:18 bronson-myth kernel: [   24.129525] EXT3 FS on sda3, internal journal
May  3 17:17:18 bronson-myth kernel: [   24.129530] EXT3-fs: mounted filesystem with ordered data mode.
May  3 17:17:18 bronson-myth kernel: [   24.602595] type=1505 audit(1272932236.482:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1996
May  3 17:17:18 bronson-myth kernel: [   24.602743] type=1505 audit(1272932236.482:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1996
May  3 17:17:18 bronson-myth kernel: [   24.602788] type=1505 audit(1272932236.482:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1996
May  3 17:17:18 bronson-myth kernel: [   24.602830] type=1505 audit(1272932236.482:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1996
May  3 17:17:18 bronson-myth kernel: [   24.747091] type=1505 audit(1272932236.626:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2001
May  3 17:17:18 bronson-myth kernel: [   24.747296] type=1505 audit(1272932236.626:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2001
May  3 17:17:18 bronson-myth kernel: [   24.774153] type=1505 audit(1272932236.654:8): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2005
May  3 17:17:18 bronson-myth kernel: [   24.800814] type=1505 audit(1272932236.682:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2009
May  3 17:17:18 bronson-myth kernel: [   26.809399] slamr: SmartLink AMRMO modem.
May  3 17:17:18 bronson-myth kernel: [   26.809416] slamr: device 1057:3052 is grabbed by another driver
May  3 17:17:28 bronson-myth kernel: [   36.396796] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
May  3 17:17:28 bronson-myth kernel: [   36.396799] Bluetooth: BNEP filters: protocol multicast
May  3 17:17:28 bronson-myth kernel: [   36.418773] Bridge firewalling registered
May  3 17:17:29 bronson-myth kernel: [   37.296571] tda18271: performing RF tracking filter calibration
May  3 17:17:32 bronson-myth kernel: [   40.501767] tda18271: RF tracking filter calibration complete
May  3 17:17:34 bronson-myth kernel: [   42.118249] eth0: link down
May  3 17:17:34 bronson-myth kernel: [   42.118358] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  3 17:17:34 bronson-myth kernel: [   42.164020] Event timed out
May  3 17:17:34 bronson-myth kernel: [   42.164026] saa7164_api_i2c_write() error, ret(1) = 0x32
May  3 17:17:34 bronson-myth kernel: [   42.164030] s5h1411_writereg: writereg error 0x19 0x3e 0x77ee, ret == -5)
May  3 17:17:34 bronson-myth kernel: [   42.164455] found timed out command on the bus
May  3 17:17:34 bronson-myth kernel: [   42.164483] ret = 0
May  3 17:17:34 bronson-myth kernel: [   42.164484]  timeout continue
May  3 17:17:34 bronson-myth kernel: [   42.465264] tda18271: performing RF tracking filter calibration
May  3 17:17:36 bronson-myth kernel: [   44.921844] tda18271: RF tracking filter calibration complete
May  3 17:18:37 bronson-myth kernel: [  105.992203] Clocksource tsc unstable (delta = -272837835 ns)
May  3 17:44:11 bronson-myth kernel: [ 1639.164030] Event timed out
May  3 17:44:11 bronson-myth kernel: [ 1639.164039] saa7164_api_i2c_read() error, ret(1) = 0x32
May  3 17:44:11 bronson-myth kernel: [ 1639.164045] s5h1411_readreg: readreg error (ret == -5)
May  3 17:44:11 bronson-myth kernel: [ 1639.164495] found timed out command on the bus
May  3 17:44:11 bronson-myth kernel: [ 1639.164525] ret = 0
May  3 17:44:11 bronson-myth kernel: [ 1639.164528]  timeout continue
May  3 17:45:17 bronson-myth kernel: [ 1705.736028] Event timed out
May  3 17:45:17 bronson-myth kernel: [ 1705.736037] saa7164_api_i2c_write() error, ret(2) = 0x32
May  3 17:45:17 bronson-myth kernel: [ 1705.736044] s5h1411_writereg: writereg error 0x19 0xf5 0x0000, ret == -5)
May  3 17:45:17 bronson-myth kernel: [ 1705.736455] found timed out command on the bus
May  3 17:45:17 bronson-myth kernel: [ 1705.736688] ret = 0
May  3 17:45:17 bronson-myth kernel: [ 1705.736690]  timeout continue
May  3 17:55:51 bronson-myth kernel: [ 2339.784037] Event timed out
May  3 17:55:51 bronson-myth kernel: [ 2339.784047] saa7164_api_i2c_read() error, ret(2) = 0x32
May  3 17:55:51 bronson-myth kernel: [ 2339.784053] s5h1411_readreg: readreg error (ret == -5)
May  3 17:55:51 bronson-myth kernel: [ 2339.784467] found timed out command on the bus
May  3 17:55:51 bronson-myth kernel: [ 2339.784699] ret = 0
May  3 17:55:51 bronson-myth kernel: [ 2339.784702]  timeout continue
May  3 17:59:16 bronson-myth kernel: [ 2544.568034] Event timed out
May  3 17:59:16 bronson-myth kernel: [ 2544.568044] saa7164_api_i2c_read() error, ret(2) = 0x32
May  3 17:59:16 bronson-myth kernel: [ 2544.568050] s5h1411_readreg: readreg error (ret == -5)
May  3 17:59:16 bronson-myth kernel: [ 2544.568495] found timed out command on the bus
May  3 17:59:16 bronson-myth kernel: [ 2544.568727] ret = 0
May  3 17:59:16 bronson-myth kernel: [ 2544.568730]  timeout continue
May  3 18:12:36 bronson-myth kernel: [ 3344.956059] Event timed out
May  3 18:12:36 bronson-myth kernel: [ 3344.956069] saa7164_api_i2c_read() error, ret(2) = 0x32
May  3 18:12:36 bronson-myth kernel: [ 3344.956076] tda18271_read_regs: ERROR: i2c_transfer returned: -5
May  3 18:12:36 bronson-myth kernel: [ 3344.957163] found timed out command on the bus
May  3 18:12:36 bronson-myth kernel: [ 3344.957303] ret = 0
May  3 18:12:36 bronson-myth kernel: [ 3344.957306]  timeout continue
May  3 18:24:17 bronson-myth kernel: [ 4045.536032] Event timed out
May  3 18:24:17 bronson-myth kernel: [ 4045.536042] saa7164_api_i2c_read() error, ret(2) = 0x32
May  3 18:24:17 bronson-myth kernel: [ 4045.536047] s5h1411_readreg: readreg error (ret == -5)
May  3 18:24:17 bronson-myth kernel: [ 4045.536759] found timed out command on the bus
May  3 18:24:17 bronson-myth kernel: [ 4045.536993] ret = 0
May  3 18:24:17 bronson-myth kernel: [ 4045.536996]  timeout continue
May  3 18:44:00 bronson-myth kernel: [ 5228.964038] Event timed out
May  3 18:44:00 bronson-myth kernel: [ 5228.964048] saa7164_api_i2c_read() error, ret(1) = 0x32
May  3 18:44:00 bronson-myth kernel: [ 5228.964054] s5h1411_readreg: readreg error (ret == -5)
May  3 18:44:00 bronson-myth kernel: [ 5228.964489] found timed out command on the bus
May  3 18:44:00 bronson-myth kernel: [ 5228.964523] ret = 0
May  3 18:44:00 bronson-myth kernel: [ 5228.964525]  timeout continue
May  3 19:39:28 bronson-myth kernel: [ 8556.524030] Event timed out
May  3 19:39:28 bronson-myth kernel: [ 8556.524040] saa7164_api_i2c_read() error, ret(2) = 0x32
May  3 19:39:28 bronson-myth kernel: [ 8556.524047] s5h1411_readreg: readreg error (ret == -5)
May  3 19:39:28 bronson-myth kernel: [ 8556.524526] found timed out command on the bus
May  3 19:39:28 bronson-myth kernel: [ 8556.524659] ret = 0
May  3 19:39:28 bronson-myth kernel: [ 8556.524662]  timeout continue
May  3 19:40:30 bronson-myth kernel: [ 8618.240030] Event timed out
May  3 19:40:30 bronson-myth kernel: [ 8618.240040] saa7164_api_i2c_read() error, ret(2) = 0x32
May  3 19:40:30 bronson-myth kernel: [ 8618.240046] s5h1411_readreg: readreg error (ret == -5)
May  3 19:40:30 bronson-myth kernel: [ 8618.240515] found timed out command on the bus
May  3 19:40:30 bronson-myth kernel: [ 8618.240648] ret = 0
May  3 19:40:30 bronson-myth kernel: [ 8618.240651]  timeout continue
May  3 19:40:31 bronson-myth kernel: [ 8619.404030] Event timed out
May  3 19:40:31 bronson-myth kernel: [ 8619.404039] saa7164_api_i2c_write() error, ret(2) = 0x32
May  3 19:40:31 bronson-myth kernel: [ 8619.404046] tda18271_write_regs: ERROR: i2c_transfer returned: -5
May  3 19:40:31 bronson-myth kernel: [ 8619.404838] found timed out command on the bus
May  3 19:40:31 bronson-myth kernel: [ 8619.404972] ret = 0
May  3 19:40:31 bronson-myth kernel: [ 8619.404974]  timeout continue
```

---

### Post by dividehex on 2010-05-04
> dividehex and tjbron are either of you using Power-saving features like  suspend? What kind of hardware are you using, especially the Motherboard  model? Its a long shot but some motherboards have BIOS enabled power  saving modes that might be interfering with this card functioning  optimally No, I do not use any powersaving feature except for a black screen saver.  The motherboard I am using is Asus M3N78-EM.

> Lastly has anyone tried another Linux Distro, like Fedora, Debian  KnoppMyth, or Opensuse? Dare I say Arch?     Nope. And I don't think I am that adventurous.

> I should mention that I am using just the hvr-2250 in my setup, unlike  dividehex who is using two cards (the 1650? and 2250, I believe).I am not using any other card. Just a hvr-2250. The only thing I have done differently is configure one tuner in mythtv and not the other (hvr-2250 has 2 tuners).  Since doing this, I have not had any i2c errors and the system is completely stable.  The obvious downside is that I can only record one thing at a time.

> Dividehex, in regards to the log changing, I believe there is a command  buffer that fills up eventually and that is when the "no free sequences"  start.  I don't think it has anything to do with a channel change or  start of recording, just an internal buffer in the driver filling up  after all the commands were buffered and not flushed because the  commands are trying to execute and are timing out.     And this is why I believe the issue lies in the driver or the combination of the driver and mythtv.

---

### Post by jjwest85 on 2010-05-05
I hate to change the subject to something else with such productive talk on this error is occuring.  I wanted to bring up LowSky's sound problem one more time.  I also have my computer connected to an HDTV.  I have an nVidia card as opposed to an ATI graphics card.  

For anyone with an nVidia card and not able to get sound to go through their HDMI cable and does not even show HDMI or digital as an option in sound preferences this may be able to help:

1.  Add "ppa:ubuntu-audio-dev/ppa" to the repository in synaptic.  Refresh synaptic.

2.  Upgrade all the pulse-audio packages

3. find out your kernel version:  type "uname -r" in a terminal.  Mine came out to be 2.6.32-21-generic (default ubuntu 10.04).  

4.  install "linux-alsa-driver-modules-2.6.32-21-generic" (your kernel may be different).  

I got this package from a launchpad bug that listed it as a possible fix to the dreaded sound through HDMI cables problem.  Installing this package gave me the options in sound preferences to choose digital sound/HDMI (IEC958 ).  I'm not 100% sure that being able to see IEC958 in sound preferences came right after updating all pulse-audio packages or if it only came after installing this package.  

I did also have to change some sound setting on MythTV's frontend.  Go to Utilities/Setup -> General -> Audio system -> Audio output device -> change to ALSA:spdif

Let me know if anyone else had/has this problem

---

### Post by dividehex on 2010-05-06
Just to wrap up the i2c error, I email Steve and got a prompt reply stating that he was aware of the issues and believes they are localized to AMD systems.   He also indicated he will be looking in to the problem.  So sit tight everyone and I will post an update when I get any new information. :-D

---

### Post by LowSky on 2010-05-06
jjwest85 - I'm going to include what you mentioned in my tutorial. Thanks for the info, it will help people out


dividehex -- AMD systems? My system is AMD based and working fine with 9.10 but not 10.04. I can see this being a driver issue, but I can't test it without buying an Intel processor and motherboard. donations are wlecomed. LOL. Its probably a problem on how the motherboard's driver communicates PCI channels.

---

### Post by jjwest85 on 2010-05-06
LowSky - thanks for adding my info.  In case people wanted to know my specific graphics card it is an nVidia 9800 gtx+ from Asus.  

As for the i2c error.  My system is running on an i5 Intel processor.  I did "tail kern.log" and found out I also have this i2c error.  See below.  (my system has been up and running for 3 days at this point)

```

May  6 16:36:22 maximus2 kernel: [336613.205470] s5h1411_readreg: readreg error (ret == -5)
May  6 16:36:22 maximus2 kernel: [336613.205475] saa7164_cmd_send() No free sequences
May  6 16:36:22 maximus2 kernel: [336613.205478] saa7164_api_i2c_read() error, ret(1) = 0xc
May  6 16:36:22 maximus2 kernel: [336613.205481] s5h1411_readreg: readreg error (ret == -5)
May  6 16:36:22 maximus2 kernel: [336613.205486] saa7164_cmd_send() No free sequences
May  6 16:36:22 maximus2 kernel: [336613.205488] saa7164_api_i2c_read() error, ret(1) = 0xc
May  6 16:36:22 maximus2 kernel: [336613.205491] s5h1411_readreg: readreg error (ret == -5)
May  6 16:36:22 maximus2 kernel: [336613.205496] saa7164_cmd_send() No free sequences
May  6 16:36:22 maximus2 kernel: [336613.205498] saa7164_api_i2c_read() error, ret(1) = 0xc
May  6 16:36:22 maximus2 kernel: [336613.205501] s5h1411_readreg: readreg error (ret == -5)

```I also noticed that my kern.log file is 18Gb.  When I went to Mythtv Frontend -> Information Center -> System Status, I also noticed that my RAM only had 1% of the 3.9Gb free.  When I tried to watch live TV, I did not get any error and it looked like it would have worked if I had some free space.  It only gave me a black screen with the channel identification pop-up on screen, but would not lock onto a channel.  Restarting my computer and then MythTV backend did let me watch live TV again.

---

### Post by LowSky on 2010-05-06
I did some digging I havent read all of it but it seems Austrailia has has similar issues with the HVR-2200
[http://www.xpmediacentre.com.au/community/linux-general-setup-support-discussion/38038-hvr-2200-install-issues.html](http://www.xpmediacentre.com.au/community/linux-general-setup-support-discussion/38038-hvr-2200-install-issues.html)
[http://www.kernellabs.com/blog/?p=676](http://www.kernellabs.com/blog/?p=676)

---

### Post by sidesh0w on 2010-05-06
Greetings from Australia :)

I have this tuner running on mythbuntu 9.10 and manually compiled drivers - works perfect.

I heard 10.04 has native drivers which would be great as everytime I update my kernel at the moment I have to re-compile the tuner drivers to get tv working again.

Can anyone confirm that 10.04 works out of the box with this tuner? Any guides out there?

Thanks for any info

---

### Post by LowSky on 2010-05-06
> **sidesh0w said:**
> Greetings from Australia :)

I have this tuner running on mythbuntu 9.10 and manually compiled drivers - works perfect.

I heard 10.04 has native drivers which would be great as everytime I update my kernel at the moment I have to re-compile the tuner drivers to get tv working again.

Can anyone confirm that 10.04 works out of the box with this tuner? Any guides out there?

Thanks for any info

Page 1 with my original tutorial has been updated with the new instructions with the link at the top. Yes the driver is in the kernel, but me and a few others are experiencing issues while recording tv. Read the last few pages here for more info. The issue is more than likely with mythtv because the newest version of Ubuntu uses an development version of mythtv. This weekend I'm thinking of installing another distro and using the stable version of mythtv to try and find more info on what's effected.

---

### Post by greensoap on 2010-05-06
> **dividehex said:**
> Just to wrap up the i2c error, I email Steve and got a prompt reply stating that he was aware of the issues and believes they are localized to AMD systems.   He also indicated he will be looking in to the problem.  So sit tight everyone and I will post an update when I get any new information. :-D


Just to mention, I am running an Intel CPU, not an AMD, and an ATI Radeon X1600.

```
*-cpu
          product: Intel(R) Pentium(R) D CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.6.2
          size: 3GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc
pebs bts pni dtes64 monitor ds_cpl vmx cid cx16 xtpr pdcm lahf_lm tpr_shadow
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
```

---

### Post by sidesh0w on 2010-05-06
> **LowSky said:**
> Page 1 with my original tutorial has been updated with the new instructions with the link at the top. Yes the driver is in the kernel, but me and a few others are experiencing issues while recording tv. Read the last few pages here for more info. The issue is more than likely with mythtv because the newest version of Ubuntu uses an development version of mythtv. This weekend I'm thinking of installing another distro and using the stable version of mythtv to try and find more info on what's effected.

Found it, thanks for that.

Looks really detailed and I am also on HDMI video / sound.

Think I will try an upgrade and keep my recordings and if I fail miserably ill do a clean.

Thanks again!

---

### Post by tjbron on 2010-05-07
> **jjwest85 said:**
>  
As for the i2c error. My system is running on an i5 Intel processor. I did "tail kern.log" and found out I also have this i2c error. See below. (my system has been up and running for 3 days at this point)
I also noticed that my kern.log file is 18Gb. When I went to Mythtv Frontend -> Information Center -> System Status, I also noticed that my RAM only had 1% of the 3.9Gb free. When I tried to watch live TV, I did not get any error and it looked like it would have worked if I had some free space. It only gave me a black screen with the channel identification pop-up on screen, but would not lock onto a channel. Restarting my computer and then MythTV backend did let me watch live TV again.
 
Yep, those are the exact symptoms. Also, you will notice that any show that it tried to record will have a zero file size.
 
My i2c error "alarm" is now a joke at my house because it beeps every half hour even if the system is working :) (I get those errors randomly even while things are working). FWIW, I have an AMD system, but it looks like jjwest85 has Intel.
 
Also, I spoke with a guy I work with and he has no problems with the 2250 on an AMD system, but he is running LINHES, not Ubuntu.

---

### Post by Hwy120 on 2010-05-08
[QUOTE=LowSky;9219191]Ok so Here's the Tutorial for using 10.04. 

[code]hg clone http://kernellabs.com/hg/saa7164-stable/

LowSky, if I do the instructions listed above on my system, that has had drivers installed before, I get the following error:
    abort: destination 'saa7164-stable' is not empty

I then need to:
rm -r saa7146-stable
this will remove the directory and allow me to continue. 

I do not know if this is just my system, but it may be something to add to your very helpful instructions for those of us who are new to Linux.

---

### Post by LowSky on 2010-05-08
Hwy120, If you have the drivers installed before, why whould you re-add them?

I want to bring up that this forum is not very keen on the use of rm codes. Due to how easily they can brick a system if one is not careful.

It is easier to ask a person to delete the folder in question through using the GUI, by going into nautilus and deleting the folder that way.

If you wish to update the drivers there is another option:
```

cd saa7164-stable
hg pull -u http://kernellabs.com/hg/saa7164-stable/
```

---

### Post by dividehex on 2010-05-08
I just got an email from Steve and he has made some changes to the saa-7164 stable tree. I'm going to compile and test it now.

---

### Post by xinix on 2010-05-09
Having just upgraded to 10.4, I'm curious about the i2c problem some folk have been having.  Is this an error that appears in the log right away or does the system work perfectly with no errors and then seemingly randomly starts filling the log with the message?  I've been using a fresh install without compiling the driver and have not seen this error (yet).
I'd like to try to reproduce the channel change crash that has been mentioned as well.  I don't watch much live tv but a quick run through the channels worked for me.

---

### Post by LowSky on 2010-05-09
> **xinix said:**
> Having just upgraded to 10.4, I'm curious about the i2c problem some folk have been having.  Is this an error that appears in the log right away or does the system work perfectly with no errors and then seemingly randomly starts filling the log with the message?  I've been using a fresh install without compiling the driver and have not seen this error (yet).
I'd like to try to reproduce the channel change crash that has been mentioned as well.  I don't watch much live tv but a quick run through the channels worked for me.

Its an odd error from what I'm told. Some people get a warning ever 1/2 hour, even with the card working fine, some go days between error log filling up until it cripples the system.

As for the channel change error, but I can confirm it happening to me. I have little knowledge of it as I reinstalled 9.10 to quickly get a working system again.

I compiled the new update for the driver last night and with 9.10 it seems to run great. No issues at all. Hopefully the same for 10.04

---

### Post by xinix on 2010-05-09
So I started to encounter problems with 10.4.  Now that I've reverted to 9.10 I cannot get the firmware to load with the new drivers.  It complains that it cannot find the right file.  Did the firmware change?

---

### Post by tjbron on 2010-05-10
> **LowSky said:**
> Its an odd error from what I'm told. Some people get a warning ever 1/2 hour, even with the card working fine, some go days between error log filling up until it cripples the system.
 
I compiled the new update for the driver last night and with 9.10 it seems to run great. No issues at all. Hopefully the same for 10.04
 
Sorry for the confusion, I have a script that watches the log every 30 minutes for the i2c error. That's where the 1/2 hour comes from. The log seems to be clear for a few hours, then starts logging the error every few minutes randomly (maybe tied to updating the OTA schedule or other usage of the box). Then sometimes it goes full-on logfile loading with a crashed tuner.
 
Also, that's great news on the driver update! Thanks for contacting Steve Toth about it. Please keep us updated on your uptime and if the problems appear to stay fixed.

---

### Post by dividehex on 2010-05-10
> Also, that's great news on the driver update! Thanks for contacting Steve Toth about it. Please keep us updated on your uptime and if the problems appear to stay fixed.I really don't want to jump the gun here and declare the issue fixed just yet, but I will say that my uptime right now is 41 hours and that is pretty good for my system considering it's uptime history.  I really hope other people with the i2c errors will update their driver ([http://www.kernellabs.com/hg/saa7164-stable/](http://www.kernellabs.com/hg/saa7164-stable/)) and report back here.

---

### Post by dividehex on 2010-05-10
> **xinix said:**
> So I started to encounter problems with 10.4.  Now that I've reverted to 9.10 I cannot get the firmware to load with the new drivers.  It complains that it cannot find the right file.  Did the firmware change?

If you upgrade to 10.04 and want to use the stock driver, you will probably need to install a new firmware in /lib/firmware

```

wget http://www.steventoth.net/linux/hvr22xx/firmwares/3978608/v4l-saa7164-1.0.3.fw
sudo cp v4l-saa7164-1.0.3.fw /lib/firmware

```If you compile the the new driver directly from the repository then you will need this firmware
```

wget http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw 
sudo cp v4l-saa7164-1.0.3-3.fw /lib/firmware

```

---

### Post by tjbron on 2010-05-10
> **dividehex said:**
> I really don't want to jump the gun here and declare the issue fixed just yet, but I will say that my uptime right now is 41 hours and that is pretty good for my system considering it's uptime history. I really hope other people with the i2c errors will update their driver ([http://www.kernellabs.com/hg/saa7164-stable/](http://www.kernellabs.com/hg/saa7164-stable/)) and report back here.
 
 
I'd love to try the new driver.  Do I have to follow LowSky's original how-to again, or is there a way to update the driver more directly?  I am running 9.04.

Thanks!

---

### Post by dividehex on 2010-05-10
> **tjbron said:**
> I'd love to try the new driver.  Do I have to follow LowSky's original how-to again, or is there a way to update the driver more directly?  I am running 9.04.

Thanks!

Follow LowSky's how-to. It is as direct as you can get. ;-)

---

### Post by tjbron on 2010-05-10
> **dividehex said:**
> Follow LowSky's how-to. It is as direct as you can get. ;-)
 
:oops:  It is a great how-to, I just meant I didn't know if there was an "update" procedure, or if I just needed to start over, delete some things, etc.
Seems like last time I had to uninstall MythTV before doing the LowSky how-to.  Sorry, still a newb. :confused:

---

### Post by dividehex on 2010-05-10
> **tjbron said:**
> :oops:  It is a great how-to, I just meant I didn't know if there was an "update" procedure, or if I just needed to start over, delete some things, etc.
Seems like last time I had to uninstall MythTV before doing the LowSky how-to.  Sorry, still a newb. :confused:
That's no problem. You have to start somewhere. :P   If you have followed LowSky instructions already and already have the driver working, you can update it by running a portion of the instructions.

NOTE: See here for LowSky's entire how-to:  [http://ubuntuforums.org/showpost.php?p=9219191&postcount=212](http://ubuntuforums.org/showpost.php?p=9219191&postcount=212)

This downloads the lastest source code from the authors website
```
hg clone http://kernellabs.com/hg/saa7164-stable/
```Change directory
```
cd saa7164-stable
```This compiles and links the source
```
make CONFIG_DVB_FIREDTV:=n
```This will install the newly compiled driver to the OS
```
sudo make install
```Now reboot so the new driver will load
```
sudo reboot
```After the reboot, check to see if the driver is finding the firmware properly.
```
dmesg | grep saa7164_downloadfirmware
```If the output looks like this, then the driver loaded the firmware properly and _**your done**_.
```
saa7164_downloadfirmware() no first image
saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3-3.fw)
saa7164_downloadfirmware() firmware read 4038864 bytes.
saa7164_downloadfirmware() firmware loaded.
saa7164_downloadfirmware() SecBootLoader.FileSize = 4038864
saa7164_downloadfirmware() FirmwareSize = 0x1fd6
saa7164_downloadfirmware() BSLSize = 0x0
saa7164_downloadfirmware() Reserved = 0x0
saa7164_downloadfirmware() Version = 0x1d1c
```Otherwise, if the output looks like this, then you will need to install the firmware
```
saa7164_downloadfirmware() no first image
saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3-3.fw)
saa7164_downloadfirmware() Upload failed. (file not found?)
```Download the extracted firmware
```
wget http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw 
```Copy the firmware to /lib/firmware
```
sudo cp v4l-saa7164-1.0.3-3.fw /lib/firmware
```
Reboot once more
```
sudo reboot
```
Hope this is more informative and helpful.

---

### Post by Hwy120 on 2010-05-11
> **LowSky said:**
> Hwy120, If you have the drivers installed before, why whould you re-add them?

The reason I would reinstall the drivers is that after each kernel update was that it seemed to be the only way I could get the 2250 working again.  If I skipped any steps I had errors and no video capture card.


> I want to bring up that this forum is not very keen on the use of rm codes. Due to how easily they can brick a system if one is not careful.

It is easier to ask a person to delete the folder in question through using the GUI, by going into nautilus and deleting the folder that way.I am still learning, but  I do not see nautilus as a choice under any of the Gnome menus.

> If you wish to update the drivers there is another option:
```

cd saa7164-stable
hg pull -u http://kernellabs.com/hg/saa7164-stable/
```Thank you for the update driver information.

---

### Post by BigPacks on 2010-05-13
> **dividehex said:**
> After the reboot, check to see if the driver is finding the firmware properly.
```
dmesg | grep saa7164_downloadfirmware
```If the output looks like this, then the driver loaded the firmware properly and _**your done**_.
```
saa7164_downloadfirmware() no first image
saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3-3.fw)
saa7164_downloadfirmware() firmware read 4038864 bytes.
saa7164_downloadfirmware() firmware loaded.
saa7164_downloadfirmware() SecBootLoader.FileSize = 4038864
saa7164_downloadfirmware() FirmwareSize = 0x1fd6
saa7164_downloadfirmware() BSLSize = 0x0
saa7164_downloadfirmware() Reserved = 0x0
saa7164_downloadfirmware() Version = 0x1d1c
```Otherwise, if the output looks like this, then you will need to install the firmware
```
saa7164_downloadfirmware() no first image
saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3-3.fw)
saa7164_downloadfirmware() Upload failed. (file not found?)
```Download the extracted firmware
```
wget http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw 
```Copy the firmware to /lib/firmware
```
sudo cp v4l-saa7164-1.0.3-3.fw /lib/firmware
```Reboot once more
```
sudo reboot
```Hope this is more informative and helpful.

[dividehex]("http://ubuntuforums.org/member.php?u=1058922"),

I've got a brand new MythBuntu 10.04 and a HVR-2200 and I can't seem to get this to work.  Using *dmesg | grep saa7164*, I get the following feedback:

```

[   12.587557] saa7164 driver loaded
[   12.812470] saa7164 0000:02:00.0: PCI INT A -> Link[APC7] -> GSI 16 (level, low) -> IRQ 16
[   12.812473] saa7164[0]: Your board isn't known (yet) to the driver.
[   12.812474] saa7164[0]: Try to pick one of the existing card configs via
[   12.812475] saa7164[0]: card=<n> insmod option.  Updating to the latest
[   12.812476] saa7164[0]: version might help as well.
[   12.813374] saa7164[0]: Here are valid choices for the card=<n> insmod option:
[   12.813654] saa7164[0]:    card=0 -> Unknown
[   12.813842] saa7164[0]:    card=1 -> Generic Rev2
[   12.814039] saa7164[0]:    card=2 -> Generic Rev3
[   12.814235] saa7164[0]:    card=3 -> Hauppauge WinTV-HVR2250
[   12.814449] saa7164[0]:    card=4 -> Hauppauge WinTV-HVR2200
[   12.814663] saa7164[0]:    card=5 -> Hauppauge WinTV-HVR2200
[   12.814877] saa7164[0]:    card=6 -> Hauppauge WinTV-HVR2200
[   12.815092] saa7164[0]:    card=7 -> Hauppauge WinTV-HVR2250
[   12.815306] saa7164[0]:    card=8 -> Hauppauge WinTV-HVR2250
[   12.815839] CORE saa7164[0]: subsystem: 0070:8940, board: Unknown [card=0,autodetected]
[   12.815844] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xf0000000
[   12.815849] saa7164 0000:02:00.0: setting latency timer to 64
[   12.815870] saa7164_initdev() Unsupported board detected, registering without firmware

```I've noticed that [Tomlin]("http://ubuntuforums.org/member.php?u=32522") got the same error a while ago ([http://ubuntuforums.org/showpost.php?p=8020583&postcount=44](http://ubuntuforums.org/showpost.php?p=8020583&postcount=44)), but I couldn't find any answers?

Does anybody know how can resolve this?:confused:

Thanks
:)

---

### Post by LowSky on 2010-05-13
try to redownload the firmware

```
wget http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw
```

```
sudo cp *.fw /lib/firmware
```

```
sudo reboot
```

---

### Post by dividehex on 2010-05-13
> **BigPacks said:**
> [dividehex]("http://ubuntuforums.org/member.php?u=1058922"),

I've got a brand new MythBuntu 10.04 and a HVR-2200 and I can't seem to get this to work.  Using *dmesg | grep saa7164*, I get the following feedback:

```

[   12.587557] saa7164 driver loaded
[   12.812470] saa7164 0000:02:00.0: PCI INT A -> Link[APC7] -> GSI 16 (level, low) -> IRQ 16
[   12.812473] saa7164[0]: Your board isn't known (yet) to the driver.
[   12.812474] saa7164[0]: Try to pick one of the existing card configs via
[   12.812475] saa7164[0]: card=<n> insmod option.  Updating to the latest
[   12.812476] saa7164[0]: version might help as well.
[   12.813374] saa7164[0]: Here are valid choices for the card=<n> insmod option:
[   12.813654] saa7164[0]:    card=0 -> Unknown
[   12.813842] saa7164[0]:    card=1 -> Generic Rev2
[   12.814039] saa7164[0]:    card=2 -> Generic Rev3
[   12.814235] saa7164[0]:    card=3 -> Hauppauge WinTV-HVR2250
[   12.814449] saa7164[0]:    card=4 -> Hauppauge WinTV-HVR2200
[   12.814663] saa7164[0]:    card=5 -> Hauppauge WinTV-HVR2200
[   12.814877] saa7164[0]:    card=6 -> Hauppauge WinTV-HVR2200
[   12.815092] saa7164[0]:    card=7 -> Hauppauge WinTV-HVR2250
[   12.815306] saa7164[0]:    card=8 -> Hauppauge WinTV-HVR2250
[   12.815839] CORE saa7164[0]: subsystem: 0070:8940, board: Unknown [card=0,autodetected]
[   12.815844] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xf0000000
[   12.815849] saa7164 0000:02:00.0: setting latency timer to 64
[   12.815870] saa7164_initdev() Unsupported board detected, registering without firmware

```I've noticed that [Tomlin]("http://ubuntuforums.org/member.php?u=32522") got the same error a while ago ([http://ubuntuforums.org/showpost.php?p=8020583&postcount=44](http://ubuntuforums.org/showpost.php?p=8020583&postcount=44)), but I couldn't find any answers?

Does anybody know how can resolve this?:confused:

Thanks
:)

If re-downloading/installing the firmware doesn't work for you, can you post the output from:
```
lspci -v
```

---

### Post by BigPacks on 2010-05-14
> **dividehex said:**
> If re-downloading/installing the firmware doesn't work for you, can you post the output from:
```
lspci -v
```

dividehex,

Nope, that didn't work. The output from the *sudo lspci -v *is attached.

FYI - The *dmesg | grep saa7164 *command looks the same as before.  Also there's no */dev/dvb/* directory (which I think is the only place MythTV looks for the tuners?)

Thanks
:)

---

### Post by LowSky on 2010-05-14
Its showing up in the log for lspci, so your issue is really odd.

Something has to be messed up with your install. I have no idea why it isn't pointing to the right file

Please run through these instructions again

```

cd /home/***username***
wget http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip
wget http://www.steventoth.net/linux/hvr22xx/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
wget http://www.steventoth.net/linux/hvr22xx/extract.sh
sh extract.sh
sudo cp *fw /lib/firmware
sudo reboot
```

---

### Post by LowSky on 2010-05-14
Just saw this in another thread. It may help with the problem of having to restart the mythtv backend after booting to get the tuner working..
[http://ubuntuforums.org/showpost.php?p=9292366&postcount=3](http://ubuntuforums.org/showpost.php?p=9292366&postcount=3)

try it out

---

### Post by dividehex on 2010-05-14
> **BigPacks said:**
> dividehex,

Nope, that didn't work. The output from the *sudo lspci -v *is attached.

FYI - The *dmesg | grep saa7164 *command looks the same as before.  Also there's no */dev/dvb/* directory (which I think is the only place MythTV looks for the tuners?)

Thanks
:)

After comparing your subdevice ID to what is in the driver source, it looks like your card might be a new hardware version and that is why the driver doesn't recognize the cards version.  I will send Steve a email about this.  If I'm correct, he will have to add it to the driver.

---

### Post by dividehex on 2010-05-14
> **LowSky said:**
> Just saw this in another thread. It may help with the problem of having to restart the mythtv backend after booting to get the tuner working..
[http://ubuntuforums.org/showpost.php?p=9292366&postcount=3](http://ubuntuforums.org/showpost.php?p=9292366&postcount=3)

try it out

I increased the sleep timer to 60 and it works great!
Thanks LowSky

---

### Post by BigPacks on 2010-05-14
> **dividehex said:**
> After comparing your subdevice ID to what is in the driver source, it looks like your card might be a new hardware version and that is why the driver doesn't recognize the cards version.  I will send Steve a email about this.  If I'm correct, he will have to add it to the driver.

Thanks,

I thought I was doing this right?

---

### Post by gkbeer on 2010-05-15
I believe I may be seeing the same problem as BigPacks.  I also find no /dev/dvb devices.

The download & installation was at about 5pm today. 

If it helps the box says "WINTV-HVR-2250 MC BOARD MODEL 1229"

```
 lspci text
    01:00.0 Multimedia controller: Philips Semiconductors Device 7164 (rev 81)
    Subsystem: Philips Semiconductors Device 0000
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fd800000 (64-bit, non-prefetchable) [size=4M]
    Memory at fd400000 (64-bit, non-prefetchable) [size=4M]
    Capabilities: <access denied>
    Kernel driver in use: saa7164
    Kernel modules: saa7164

``````
 dmesg text
[    6.569310] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[    6.569316] saa7164 0000:01:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
[    6.569321] saa7164[0]: Your board isn't known (yet) to the driver.
[    6.569322] saa7164[0]: Try to pick one of the existing card configs via
[    6.569323] saa7164[0]: card=<n> insmod option.  Updating to the latest
[    6.569324] saa7164[0]: version might help as well.
[    6.569327] saa7164[0]: Here are valid choices for the card=<n> insmod option:
[    6.569329] saa7164[0]:    card=0 -> Unknown
[    6.569331] saa7164[0]:    card=1 -> Generic Rev2
[    6.569333] saa7164[0]:    card=2 -> Generic Rev3
[    6.569334] saa7164[0]:    card=3 -> Hauppauge WinTV-HVR2250
[    6.569336] saa7164[0]:    card=4 -> Hauppauge WinTV-HVR2200
[    6.569338] saa7164[0]:    card=5 -> Hauppauge WinTV-HVR2200
[    6.569340] saa7164[0]:    card=6 -> Hauppauge WinTV-HVR2200
[    6.569341] saa7164[0]:    card=7 -> Hauppauge WinTV-HVR2250
[    6.569343] saa7164[0]:    card=8 -> Hauppauge WinTV-HVR2250
[    6.569345] saa7164[0]:    card=9 -> Hauppauge WinTV-HVR2200
[    6.569786] CORE saa7164[0]: subsystem: 1131:0000, board: Unknown [card=0,autodetected]
[    6.569791] saa7164[0]/0: found at 0000:01:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfd800000
[    6.569796] saa7164 0000:01:00.0: setting latency timer to 64
[    6.569811] saa7164_initdev() Unsupported board detected, registering without firmware
[    6.574606] Linux agpgart interface v0.103

```Ok I read the dmesg and after 
sudo rmmod saa7164
sudo modprobe saa7164 card=9

dmesg said:```

[ 3513.686574] saa7164 0000:01:00.0: PCI INT A disabled
[ 3691.190797] saa7164 driver loaded
[ 3691.190922] saa7164 0000:01:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
[ 3691.191944] CORE saa7164[0]: subsystem: 1131:0000, board: Hauppauge WinTV-HVR2200 [card=9,insmod option]
[ 3691.191954] saa7164[0]/0: found at 0000:01:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfd800000
[ 3691.191965] saa7164 0000:01:00.0: setting latency timer to 64
[ 3691.348023] saa7164_downloadfirmware() no first image
[ 3691.348035] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3-3.fw)
[ 3691.348041] saa7164 0000:01:00.0: firmware: requesting v4l-saa7164-1.0.3-3.fw
[ 3691.352622] saa7164_downloadfirmware() Upload failed. (file not found?)
[ 3691.352634] Failed to boot firmware, no features registered

```It's not finding the firmware now.

followup: Found the firmware at [Index of /linux/hvr22xx/firmwares/4038864 ]("http://steventoth.net/linux/hvr22xx/firmwares/4038864/")
Tested options 9 thru 3. With card=3 the dev files appeared for both tuners. 

But, the system died due to an overheat that crashed the system and left the drive un-bootable.  

Rebuilding now.

---

### Post by jugglingcats on 2010-05-17
Hi, I am running 10.04 so the driver that uses firmware v4l-saa7164-1.0.3.fw is pre-loaded. However, have seen the problem that the card crashes while recording in some cases and another thread suggests firmware v4l-saa7164-1.0.3-3.fw fixes this. So I rebuilt the driver using hg, did make install, etc. but at boot time it is still looking for v4l-saa7164-1.0.3.fw. Does this mean the old driver is hanging around? How can I check and make it use the new firmware?

Many thanks,
Alfie.

---

### Post by BigPacks on 2010-05-17
> **gkbeer said:**
> Ok I read the dmesg and after 
sudo rmmod saa7164
sudo modprobe saa7164 card=9

dmesg said:```

[ 3513.686574] saa7164 0000:01:00.0: PCI INT A disabled
[ 3691.190797] saa7164 driver loaded
[ 3691.190922] saa7164 0000:01:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
[ 3691.191944] CORE saa7164[0]: subsystem: 1131:0000, board: Hauppauge WinTV-HVR2200 [card=9,insmod option]
[ 3691.191954] saa7164[0]/0: found at 0000:01:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfd800000
[ 3691.191965] saa7164 0000:01:00.0: setting latency timer to 64
[ 3691.348023] saa7164_downloadfirmware() no first image
[ 3691.348035] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3-3.fw)
[ 3691.348041] saa7164 0000:01:00.0: firmware: requesting v4l-saa7164-1.0.3-3.fw
[ 3691.352622] saa7164_downloadfirmware() Upload failed. (file not found?)
[ 3691.352634] Failed to boot firmware, no features registered

```It's not finding the firmware now.

followup: Found the firmware at [Index of /linux/hvr22xx/firmwares/4038864 ]("http://steventoth.net/linux/hvr22xx/firmwares/4038864/")
Tested options 9 thru 3. With card=3 the dev files appeared for both tuners. 

But, the system died due to an overheat that crashed the system and left the drive un-bootable.  

Rebuilding now.

gkbeer,

Just checking, was the overheat cause you changed the firmware?  I.e. don't try it?

---

### Post by tjbron on 2010-05-19
> **dividehex said:**
> That's no problem. You have to start somewhere. :P If you have followed LowSky instructions already and already have the driver working, you can update it by running a portion of the instructions.
 
 
Hope this is more informative and helpful.
 
Fantastic help, dividehex and LowSky.
New driver (and firmware) installed.  I haven't had it running much since, but no errors are showing up in the kern.log so far.  It was getting to where it wouldn't go much past a few hours after reboot.
 
Thanks!

---

### Post by gkbeer on 2010-05-19
> **BigPacks said:**
> gkbeer,

Just checking, was the overheat cause you changed the firmware?  I.e. don't try it?

No, the system ([HP  Slimline)]("http://h10010.www1.hp.com/wwpc/ca/en/ho/WF06b/12132708-12133156-12133158-12133158-12133158-80230533-80451688.html")  I'm working with is marginal for cpu cooling. Unless I crank the cpu fan up to objectionable noise levels, the system sometimes fails to restart. This time the filesystem was somehow corrupted in the restart. 

I have it rebuilt now but something is different. When I "make install" it finishes with an error. The depmod command reports bus error, and the module saa7164 is not being loaded during boot.

---

### Post by BigPacks on 2010-05-19
> **gkbeer said:**
>  I have it rebuilt now but something is different. When I &quot;make install&quot; it finishes with an error. The depmod command reports bus error, and the module saa7164 is not being loaded during boot.

 Can you let me know if you get this working?  I haven't touched my system since last week.

---

### Post by BigPacks on 2010-05-20
> **gkbeer said:**
> Ok I read the dmesg and after 
sudo rmmod saa7164
sudo modprobe saa7164 card=9

dmesg said:```

[ 3513.686574] saa7164 0000:01:00.0: PCI INT A disabled
[ 3691.190797] saa7164 driver loaded
[ 3691.190922] saa7164 0000:01:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
[ 3691.191944] CORE saa7164[0]: subsystem: 1131:0000, board: Hauppauge WinTV-HVR2200 [card=9,insmod option]
[ 3691.191954] saa7164[0]/0: found at 0000:01:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfd800000
[ 3691.191965] saa7164 0000:01:00.0: setting latency timer to 64
[ 3691.348023] saa7164_downloadfirmware() no first image
[ 3691.348035] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3-3.fw)
[ 3691.348041] saa7164 0000:01:00.0: firmware: requesting v4l-saa7164-1.0.3-3.fw
[ 3691.352622] saa7164_downloadfirmware() Upload failed. (file not found?)
[ 3691.352634] Failed to boot firmware, no features registered

```It's not finding the firmware now.

followup: Found the firmware at [Index of /linux/hvr22xx/firmwares/4038864 ]("http://steventoth.net/linux/hvr22xx/firmwares/4038864/")
Tested options 9 thru 3. With card=3 the dev files appeared for both tuners. 

But, the system died due to an overheat that crashed the system and left the drive un-bootable.  

Rebuilding now.

Peoples,

I've tried using this firmware and used the following commands:

[LIST]
[*]sudo rmmod saa7164
[*]sudo modprobe saa7164 card=4
[/LIST]
FYI - I get the following message, but I'm not sure if it's important:

*WARNING: All config files need .conf: /etc/modprobe.d/lirc-blacklist, it will be ignore in a future release.*

The *dmesg | grep saa7164_downloadfirmware* output is as follows:

saa7164_downloadfirmware() no first image
saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3-3.fw)
saa7164_downloadfirmware() firmware read 4038864 bytes.
saa7164_downloadfirmware() firmware loaded.
saa7164_downloadfirmware() SecBootLoader.FileSize = 4038864
saa7164_downloadfirmware() FirmwareSize = 0x1fd6
saa7164_downloadfirmware() BSLSize = 0x0
saa7164_downloadfirmware() Reserved = 0x0
saa7164_downloadfirmware() Version = 0x1d1c

I've managed to get it to work (i.e. MythTV Backend can see the tuners and I can watch TV via the MythTV Frontend), **BUT** when I reboot it doesn't work?  I.e. it's back to how it was before the *sudo rmmod saa7164* & *sudo modprobe saa7164 card=4* commands.

The *dmesg | grep saa7164* says:

```
[   12.488943] saa7164 driver loaded
[   12.491844] saa7164 0000:02:00.0: PCI INT A -> Link[APC7] -> GSI 16 (level, low) -> IRQ 16
[   12.491848] saa7164[0]: Your board isn't known (yet) to the driver.
[   12.491848] saa7164[0]: Try to pick one of the existing card configs via
[   12.491849] saa7164[0]: card=<n> insmod option.  Updating to the latest
[   12.491850] saa7164[0]: version might help as well.
[   12.492022] saa7164[0]: Here are valid choices for the card=<n> insmod option:
[   12.492067] saa7164[0]:    card=0 -> Unknown
[   12.492108] saa7164[0]:    card=1 -> Generic Rev2
[   12.492150] saa7164[0]:    card=2 -> Generic Rev3
[   12.492192] saa7164[0]:    card=3 -> Hauppauge WinTV-HVR2250
[   12.492235] saa7164[0]:    card=4 -> Hauppauge WinTV-HVR2200
[   12.492278] saa7164[0]:    card=5 -> Hauppauge WinTV-HVR2200
[   12.492320] saa7164[0]:    card=6 -> Hauppauge WinTV-HVR2200
[   12.492363] saa7164[0]:    card=7 -> Hauppauge WinTV-HVR2250
[   12.492406] saa7164[0]:    card=8 -> Hauppauge WinTV-HVR2250
[   12.492754] CORE saa7164[0]: subsystem: 0070:8940, board: Unknown [card=0,autodetected]
[   12.492759] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xf0000000
[   12.492763] saa7164 0000:02:00.0: setting latency timer to 64
[   12.492784] saa7164_initdev() Unsupported board detected, registering without firmware

```Does anybody have any ideas?  :confused:Is there a way to tell it that I want card 4?

Thanks:)

---

### Post by dividehex on 2010-05-20
BigPacks, According to your dmesg the subsystem id is 8940.
```
[   12.492754] CORE saa7164[0]: subsystem: 0070:8940, board: Unknown [card=0,autodetected]

```
Steve Toth, added this card to the driver 5 days ago so it looks like you don't have the latest driver.

Follow LowSky's instructions on downloading and installing  the latest saa-7164 driver.  After that, it should autodetect the card on boot.

Gkbeer, what kind of errors do you get from 'make install'?  Make sure you run it with 'sudo' ie 'sudo make install'

jugglingcats, did you get any error when you ran 'make' or 'sudo make install'?

---

### Post by BigPacks on 2010-05-21
> **dividehex said:**
> BigPacks, According to your dmesg the subsystem id is 8940.
```
[   12.492754] CORE saa7164[0]: subsystem: 0070:8940, board: Unknown [card=0,autodetected]

```Steve Toth, added this card to the driver 5 days ago so it looks like you don't have the latest driver.

Follow LowSky's instructions on downloading and installing  the latest saa-7164 driver.  After that, it should autodetect the card on boot.

Gkbeer, what kind of errors do you get from 'make install'?  Make sure you run it with 'sudo' ie 'sudo make install'

jugglingcats, did you get any error when you ran 'make' or 'sudo make install'?


I got it working!!!:P

Since I had a machine with nothing on it I decided to blank the hard disk and re-install Mythbuntu 10.04.  I followed [these]("http://ubuntuforums.org/showpost.php?p=9219191&postcount=212") instructions (skipping the 3a part) with no luck.  Then I tried doing the 3b part, but no luck.

THEN I looked around and found the new driver here ([http://www.kernellabs.com/hg/~stoth/saa7164-dev/]("http://www.kernellabs.com/hg/%7Estoth/saa7164-dev/")).  Note that while that says the driver is from Jan 2010, on [http://www.kernellabs.com/hg/~stoth/]("http://www.kernellabs.com/hg/%7Estoth/") it says the driver is from 15-May-10.

I did the following (based on [Lowsky's]("http://ubuntuforums.org/showpost.php?p=9219191&postcount=212") instructions):

```

sudo apt-get install mercurial libncurses5-dev unzip

wget http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip
wget http://www.steventoth.net/linux/hvr22xx/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
wget http://www.steventoth.net/linux/hvr22xx/extract.sh
sh extract.sh
sudo cp *fw /lib/firmware
[B]
hg clone http://www.kernellabs.com/hg/~stoth/saa7164-dev/[/B]

cd saa7164-stable
make CONFIG_DVB_FIREDTV:=n
sudo make install

sudo reboot

```Really the only difference was getting the newer driver for my HVR-2200 from a different location.

Thanks heaps to dividehex and Lowsky for your help getting this working.
:)

---

### Post by LowSky on 2010-05-21
BigPacks thanks for the info on what you needed to do.

It is so hard to keep on track the changes going on for this card.

Because you are using the development branch, can you keep us informed of any issues. I'm weary of putting the info into my tutorial unless we know things are safe.

---

### Post by BigPacks on 2010-05-21
> **LowSky said:**
> Because you are using the development branch, can you keep us informed of any issues. I'm weary of putting the info into my tutorial unless we know things are safe.

I'm going to try and play with it this weekend.  I've got another tuner card (DViCO FusionHDTV DVB-T Dual Digital 4) which I'm going to put into this machine (which is currently in another machine) and that seems to be ok.

I'm new to MythTV, so I'm not really that familiar yet with how to tweak it.  But at least I'll be able to compare the two.

Thanks again for your help:P

---

### Post by BigPacks on 2010-05-24
> **BigPacks said:**
> I got it working!!!:P

Since I had a machine with nothing on it I decided to blank the hard disk and re-install Mythbuntu 10.04.  I followed [these]("http://ubuntuforums.org/showpost.php?p=9219191&postcount=212") instructions (skipping the 3a part) with no luck.  Then I tried doing the 3b part, but no luck.

THEN I looked around and found the new driver here ([http://www.kernellabs.com/hg/~stoth/saa7164-dev/]("http://www.kernellabs.com/hg/%7Estoth/saa7164-dev/")).  Note that while that says the driver is from Jan 2010, on [http://www.kernellabs.com/hg/~stoth/]("http://www.kernellabs.com/hg/%7Estoth/") it says the driver is from 15-May-10.

I did the following (based on [Lowsky's]("http://ubuntuforums.org/showpost.php?p=9219191&postcount=212") instructions):

```

sudo apt-get install mercurial libncurses5-dev unzip

wget http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip
wget http://www.steventoth.net/linux/hvr22xx/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
wget http://www.steventoth.net/linux/hvr22xx/extract.sh
sh extract.sh
sudo cp *fw /lib/firmware
[B]
hg clone http://www.kernellabs.com/hg/~stoth/saa7164-dev/[/B]

cd saa7164-stable
make CONFIG_DVB_FIREDTV:=n
sudo make install

sudo reboot

```Really the only difference was getting the newer driver for my HVR-2200 from a different location.

Thanks heaps to dividehex and Lowsky for your help getting this working.
:)

I made a mistake in my earlier instructions

```

sudo apt-get install mercurial libncurses5-dev unzip

wget http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip
wget  http://www.steventoth.net/linux/hvr22xx/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
wget http://www.steventoth.net/linux/hvr22xx/extract.sh
sh extract.sh
sudo cp *fw /lib/firmware

hg clone http://kernellabs.com/hg/saa7164-stable/

cd saa7164-stable
make CONFIG_DVB_FIREDTV:=n
sudo make install
wget http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw 
sudo cp v4l-saa7164-1.0.3-3.fw /lib/firmware
sudo reboot

```I must have been using the stable version instead of the dev version cause I should get the dev version to work.

Note - I'm also having issues with this, database issues.  I can get it working, but when I reboot it can't find them.  Haven't had a chance to properly look at this, but I've noticed that when I close the MythTV Backend setup, the window says it's having issues connected to the database.

I haven't changed any of the address in the MythTV settings (i.e. they're still localhost or 127.0.0.1).

I don't have this problem with another MythTV setup with a DViCO FusionHDTV DVB-T Dual Digital 4.

---

### Post by BigPacks on 2010-05-25
> 
Note - I'm also having issues with this, database issues. I can get it working, but when I reboot it can't find them. Haven't had a chance to properly look at this, but I've noticed that when I close the MythTV Backend setup, the window says it's having issues connected to the database.

I haven't changed any of the address in the MythTV settings (i.e. they're still localhost or 127.0.0.1).

I don't have this problem with another MythTV setup with a DViCO FusionHDTV DVB-T Dual Digital 4.I can't get this to work properly. I can get it to play TV via the MythTV Frontend, but if I exit the frontend (or reboot) it most likely won't work next time. If I run the MythTV Backend Setup, quit and re-run MythTV it'll work.

I'm not sure if this is an issue with the HVR-2200, or it's something I haven't setup properly (I'm new to MythTV). As I mentioned above, I don't seem to have these issues with a DViCO FusionHDTV DVB-T Dual Digital 4 (which worked without fiddling).

What happens why I try and watch TV I usually I'll get this message:

* "Error: MythTV is using all inputs, but there are no active recordings?*"

I'm not recording anything and, as I understand, while MythTV records all TV, it'll give up the resource.  So I'm not sure why it won't let me watch TV?

I was wondering if it had anything to do with the "Input connections" -> "Interaction between inputs" in the MythTV Backend Setup? Currently I have both cards set as follows:


[LIST]
[*]     Input priority = 0
[*]Input group 1: Generic
[*]Input group 2: Generic
[/LIST]
 
Does anybody have any suggestions what the problem is?  Or what I should be looking for in the log files?

Thanks

---

### Post by LowSky on 2010-05-25
Bigpacks, see this thread it seems to help with the issue with MythTV starting before the driver is loaded.
[http://ubuntuforums.org/showpost.php?p=9292366&postcount=3](http://ubuntuforums.org/showpost.php?p=9292366&postcount=3)


I posted this info on page 26 of this thread. A few people have used it and swear it works.

---

### Post by BigPacks on 2010-05-27
> **LowSky said:**
> Bigpacks, see this thread it seems to help with the issue with MythTV starting before the driver is loaded.
[http://ubuntuforums.org/showpost.php?p=9292366&postcount=3](http://ubuntuforums.org/showpost.php?p=9292366&postcount=3)


I posted this info on page 26 of this thread. A few people have used it and swear it works.

Lowsky,

I tried this (changed the name of the location of the backend log) and I couldn't get it to work.  Tried changing the wait from 1s to 60s, but no luck.  Then I tried to try the original [mythtv-backend.conf]("http://ubuntuforums.org/attachment.php?attachmentid=156768&d=1273755274") file, now I can't get the tuner to work at all.

Also I tried deleting the cards in reconfiguring them with the MythTV Backend setup, but that wouldn't work either.

I've checked *dmesg | grep saa* and I noticed the following:

```

[   12.465006] saa7164 driver loaded
[   12.502032] saa7164 0000:02:00.0: PCI INT A -> Link[APC7] -> GSI 16 (level, low) -> IRQ 16
[   12.502299] CORE saa7164[0]: subsystem: 0070:8940, board: Hauppauge WinTV-HVR2200 [card=9,autodetected]
[   12.502304] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xf0000000
[   12.502308] saa7164 0000:02:00.0: setting latency timer to 64
[   13.300046] saa7164_downloadfirmware() no first image
[   13.300285] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3-3.fw)
[   13.300288] saa7164 0000:02:00.0: firmware: requesting v4l-saa7164-1.0.3-3.fw
[   13.502941] saa7164_downloadfirmware() firmware read 4038864 bytes.
[   13.502943] saa7164_downloadfirmware() firmware loaded.
[   13.502950] saa7164_downloadfirmware() SecBootLoader.FileSize = 4038864
[   13.502955] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   13.502956] saa7164_downloadfirmware() BSLSize = 0x0
[   13.502958] saa7164_downloadfirmware() Reserved = 0x0
[   13.502959] saa7164_downloadfirmware() Version = 0x1d1c
[   20.720015] saa7164_downloadimage() Image downloaded, booting...
[   20.830014] saa7164_downloadimage() Image booted successfully.
[   23.060014] saa7164_downloadimage() Image downloaded, booting...
[   24.490014] saa7164_downloadimage() Image booted successfully.
[   24.530349] saa7164[0]: Hauppauge eeprom: model=89619
[   24.935305] DVB: registering new adapter (saa7164)
[   27.968199] DVB: registering new adapter (saa7164)
[   29.432892] saa7164 0000:02:00.0: firmware: requesting dvb-fe-tda10048-1.0.fw
[   35.596441] saa7164 0000:02:00.0: firmware: requesting dvb-fe-tda10048-1.0.fw

```First I tried to copy the *dvb-fe-tda10048-1.0.fw* into /lib/firmware, then I tried to re-install the tuner card as before, but it didn't work.

Do you know an easy way to reinstall the tuner card?  Or should I just re-install Mythbuntu?

Thanks

_________________

Ignore this, I'm reinstalling anyway.

---

### Post by BigPacks on 2010-05-28
> **BigPacks said:**
> Lowsky,

I tried this (changed the name of the location of the backend log) and I couldn't get it to work.  Tried changing the wait from 1s to 60s, but no luck.  Then I tried to try the original [mythtv-backend.conf]("http://ubuntuforums.org/attachment.php?attachmentid=156768&d=1273755274") file, now I can't get the tuner to work at all.

Also I tried deleting the cards in reconfiguring them with the MythTV Backend setup, but that wouldn't work either.


I think I changed something else which stuffed this up.  I reinstalled Mythbuntu 10.04 and now the tuner cards will work from the MythTV frontend (if the MythTV Backend setup is run).  Now I'd say it's a database issue rather than a tuner card issue.

Gotta spend some time playing around to figure out what exactly the problem is.  Thanks again for your help.

BTW I tried something different getting the tuner card working this time.  This time I added a file to the */etc/modprobe.d* directory called *saa7164.conf*, which had the following:

```

options saa7164 card=4

```

---

### Post by dhjohnson on 2010-06-11
I'm having issues with "hiccupping" when playing back the recordings from my 2250.  Every minute or two the recording will jump forward a few seconds.  The issue started when I did a fresh install of Ubuntu Server 10.4 and installed mythbuntu-desktop.  My records were just fine under 9.10.  Have you seen this before?

---

### Post by LowSky on 2010-06-11
> **dhjohnson said:**
> I'm having issues with "hiccupping" when playing back the recordings from my 2250.  Every minute or two the recording will jump forward a few seconds.  The issue started when I did a fresh install of Ubuntu Server 10.4 and installed mythbuntu-desktop.  My records were just fine under 9.10.  Have you seen this before?


Have you tried playing a recording using VLC or another application? Is LiveTV working?

If live TV is unaffected it could be writing issue with the hard drive.

Otherwise download the newest firmware's and see if those help. Lastly try the development driver, I believe BigPacks gives instructions for it a few posts up.

---

### Post by reedstrm on 2010-06-22
Good to see I wasn't crazy back in Oct. when I first reported this problem. Even better to see code changes that look like they may address the issue. Just upgraded my mediapc to 9.10, and grabbed the latest firmware and drivers. We'll see how it goes.

---

### Post by epi 1:10,000 on 2010-06-26
I am having the same problem as BigPacks.   On boot into the most recent kernel for 9.04 and most recent driver via LowSky install,  the firmware fails to load.   On boot it is looking for v4l-saa71064-1.0.3-3.fw but the LowSky method downloades v4l-saa71064-1.0.3.fw.  Booting into the previous kernel, and therfor older driver/firmware, everyting works fine.

update:
Copying the firmware from  [Index of /linux/hvr22xx/firmwares/4038864]("http://steventoth.net/linux/hvr22xx/firmwares/4038864/") into the /lib/firmware directory seems to work after a reboot.  I will need some time to see if it continues to work.

---

### Post by LowSky on 2010-07-12
Anyone using Multiplex with this tuner? I ddin't even know I could record two+ shows from one tuner at the same time... in case you have no idea what I'm talking about this means we might be able to record 4+ shows at once using this card as long as we have bandwidth.

I'm going to do a bit of research tonight to see if its possible.

---

### Post by silverdulcet on 2010-07-12
> **LowSky said:**
> Anyone using Multiplex with this tuner? I ddin't even know I could record two+ shows from one tuner at the same time... in case you have no idea what I'm talking about this means we might be able to record 4+ shows at once using this card as long as we have bandwidth.

I'm going to do a bit of research tonight to see if its possible.

I've tested multiplex recording many times on my HVR-2250. I tested recording a channel with a total of 4 sub-channels on one tuner and also recorded 2 sub-channels on one tuner. I settled for setting mutli-record so I have only 1 virtual tuner for each tuner in the 2250. I never tested recording 8 sub-channels (4 on each of the 2250's tuners, 1 real tuner and 3 virtual tuners for each of the hardware tuners on the 2250)

---

### Post by LowSky on 2010-07-12
Thanks for the feedback silverdulcet. I haven't played with this feature set yet so I have no idea how possible it will be on my system. I'm concerned over how my channels are packed together. I'm going to try using virtual tuners either tonight or sometime this week.

---

### Post by Barry_IA on 2010-07-19
[QUOTE=LowSky;9219191]Ok so Here's the Tutorial for using 10.04. 

<snip>

1. Open a Terminal

<snip>
[CODE]
wget http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip


If there is a problem with wget not downloading try adding the 'continue' switch:

[CODE]
wget -c  http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip

---

### Post by LowSky on 2010-07-19
> **LowSky said:**
> Ok so Here's the Tutorial for using 10.04. 

<snip>

1. Open a Terminal

<snip>

```
wget http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip
```

> **Barry_IA said:**
> 
If there is a problem with wget not downloading try adding the 'continue' switch:


```
wget -c  http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip
```
You forgot end tags for you post [/CODE], see how much nicer this looks.

---

### Post by Barry_IA on 2010-07-19
> **LowSky said:**
> You forgot end tags for you post [/CODE], see how much nicer this looks.

Oops!  I knew something was missing!  I'll learn eventually! <g>

---

### Post by jjwest85 on 2010-08-22
I don't know if anyone has seen this post on KernelLabs.com yet:

[http://www.kernellabs.com/blog/?p=1443](http://www.kernellabs.com/blog/?p=1443)

> SAA7164 Analog support complete?

First draft is available from [http://kernellabs.com/hg/~stoth/saa7164-v4l](http://kernellabs.com/hg/~stoth/saa7164-v4l)
 Firmware is available from [http://www.steventoth.net/linux/hvr22xx/firmwares/4019072](http://www.steventoth.net/linux/hvr22xx/firmwares/4019072)
 Comments welcome.

I haven't seen anything yet about IR support though.  A big thanks to Steven Toth for all his hard work!

---

### Post by LowSky on 2010-08-22
tried to get analog working yesterday and could get one channel to lock... I might have done something wrong but not sure

---

### Post by Barry_IA on 2010-08-23
> **LowSky said:**
> tried to get analog working yesterday and could get one channel to lock... I might have done something wrong but not sure

Hi LowSky!

We doubt you did anything wrong: you know *everything*!! <g>   Guess the first thing I would do is see if there is more than one analog station available in your area.  Even if more, are they receivable and worth receiving?  Locally there are two analog stations, one has of-interest programming and is repeated on one of the sub-carriers (virtual 8.3).  The other one has programming I'm not interested in so isn't worth the bother for me.

---

### Post by LowSky on 2010-08-23
> **Barry_IA said:**
> Hi LowSky!

We doubt you did anything wrong: you know *everything*!! <g>   Guess the first thing I would do is see if there is more than one analog station available in your area.  Even if more, are they receivable and worth receiving?  Locally there are two analog stations, one has of-interest programming and is repeated on one of the sub-carriers (virtual 8.3).  The other one has programming I'm not interested in so isn't worth the bother for me.
Thanks for the vote of confidence! ):P I just tried using my cable connection, but since I have no idea if I still get analog channels over the line (I a have a HD TV and Digital cable boxes), I have no clue on if the new analog tuner work. It really doesn't effect me but I want to keep things updated on the tutorial.

---

### Post by JMcFly on 2010-08-24
Do you need a RAID5 array or similar for handling the load of multiplex recording, or can a normal 3gb/s SATA drive handle it?

---

### Post by LowSky on 2010-08-24
> **JMcFly said:**
> Do you need a RAID5 array or similar for handling the load of multiplex recording, or can a normal 3gb/s SATA drive handle it?

I have 3 recordings going on at once on to a 5400RPM SATA 2. Not a problem. I'm not sure of the limit but how many shows are you trying to record at once onto one drive.

---

### Post by JMcFly on 2010-08-24
I'm adding a 2250 to my current Haup 1600, so the new max would be 3 HD streams and 1 SD stream, but I bet it will normally be 2 HD streams and an SD stream at the same time. I'm not even sure what's available on multiplex in my area, I usually just search for program names rather than browse listings.
 
Currently I have one recording drive but I'm adding a second drive with its own storage group so the GF won't clog "my" space with her shows.

---

### Post by elventear on 2010-08-25
Has anyone been able to use Mythbuntu with the analog tree of the SAA7164 drivers from Kernel Labs?

I have compiled the analog support and I am able to tune into channels, but when I try to use MythTV I get the following on the backend:


> [FONT="Courier New"]MPEGRec(/dev/video0) Error: Device error detected
DevRdB(/dev/video0): Stop(): Not running.
DevRdB(/dev/video0) Error: Problem reading fd(36)
eno: Bad address (14)
[/FONT]

---

### Post by Barry_IA on 2010-08-25
> **LowSky said:**
> Thanks for the vote of confidence! ):P I just tried using my cable connection, but since I have no idea if I still get analog channels over the line (I a have a HD TV and Digital cable boxes), I have no clue on if the new analog tuner work. It really doesn't effect me but I want to keep things updated on the tutorial.

Hi LowSky!

Locally (Quad City metropolitan area: Davenport/Bettendorf, IA, Moline/Rock Island/East Moline, IL -- yes, that's five, and some businesses, etc., did go with Quint Cities, but what would we have called ourselves when a sixth town grew?!?!) the cable company is still offering analog service.  I'm not sure if the digital TV frequencies are similar to the old analog ones.  I'm thinking the current analog stations have to be transmitting using the same frequencies, bandwidth, etc., as were in effect before the transition else the (analog) televisions would not be able to receive them.  And since the analog tuners follow those rules I'm thinking they should be able to pick up any analog stations in your area.  The two stations locally using analog come in weakly on the various TVs here.   LIS, haven't attempted to check then out.  FWIW I did find out a wire ~21" long helped to pick up "Ch 4" which is transmitting on RF 4 (VHF -- one of the few VHF stations in the country) with my and friends' "digital converter boxes".

---

### Post by LowSky on 2010-08-26
Barry_IA, analog and digital work on completley different frequencies. A great example would be similar to AM and FM radio. It would seem analog in my area is gone (NYC metro area). I'm not too concerned at the loss, but maybe I can try the composite or S-Video inputs to see if those work, but again as my home is completely digital I don't have much to test.

---

### Post by Wrostek on 2010-08-26
I am still having i2c errors, it seems like the messages related to i2c have ceased in the past few months, have they been resolved? If so how?

I have installed Ubuntu 10.04 2.6.32-24-generic , with two tuner cards -  hvr-2250 and hvr-1850 and my processor is an i5-661.  I am running mythfrontend and mythbackend on the same machine.  Usually my processor usage is less than 10% even while watching HD and recording 2 or 3 simultaneous programs.

The i2c error most often occurs when nothing else is taking place, say at 4 am, with nothing being watched or recorded. When the i2c error happens, two processes ( mythfrontend and Xorg ) shoot up to 100% and stay there. The  kernel.log fills up with these messages:

```

Aug 26 04:48:10 mr-slate kernel: [28855.850582] Event timed out
Aug 26 04:48:10 mr-slate kernel: [28855.850590] saa7164_api_i2c_read() error, ret(1) = 0x32
Aug 26 04:48:10 mr-slate kernel: [28855.850592] s5h1411_readreg: readreg error (ret == -5)
Aug 26 04:48:11 mr-slate kernel: [28856.550004] Event timed out
Aug 26 04:48:11 mr-slate kernel: [28856.550007] saa7164_api_i2c_read() error, ret(1) = 0x32
Aug 26 04:48:11 mr-slate kernel: [28856.550009] s5h1411_readreg: readreg error (ret == -5)
Aug 26 04:48:20 mr-slate kernel: [28865.842333] Event timed out
Aug 26 04:48:20 mr-slate kernel: [28865.842337] saa7164_api_i2c_read() error, ret(1) = 0x32
Aug 26 04:48:20 mr-slate kernel: [28865.842340] s5h1411_readreg: readreg error (ret == -5)
Aug 26 04:48:21 mr-slate kernel: [28866.541754] Event timed out
Aug 26 04:48:21 mr-slate kernel: [28866.541756] saa7164_api_i2c_read() error, ret(1) = 0x32
Aug 26 04:48:21 mr-slate kernel: [28866.541758] s5h1411_readreg: readreg error (ret == -5)
Aug 26 04:48:30 mr-slate kernel: [28875.834084] Event timed out
Aug 26 04:48:30 mr-slate kernel: [28875.834088] saa7164_api_i2c_write() error, ret(1) = 0x32
Aug 26 04:48:30 mr-slate kernel: [28875.834091] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
Aug 26 04:48:31 mr-slate kernel: [28876.533505] Event timed out
Aug 26 04:48:31 mr-slate kernel: [28876.533507] saa7164_api_i2c_write() error, ret(1) = 0x32
Aug 26 04:48:31 mr-slate kernel: [28876.533509] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
Aug 26 04:48:40 mr-slate kernel: [28885.825836] Event timed out
Aug 26 04:48:40 mr-slate kernel: [28885.825840] saa7164_api_i2c_write() error, ret(1) = 0x32
Aug 26 04:48:40 mr-slate kernel: [28885.825843] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
Aug 26 04:48:41 mr-slate kernel: [28886.525257] Event timed out
Aug 26 04:48:41 mr-slate kernel: [28886.525260] saa7164_api_i2c_write() error, ret(1) = 0x32
Aug 26 04:48:41 mr-slate kernel: [28886.525262] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
Aug 26 04:48:50 mr-slate kernel: [28895.817589] Event timed out
Aug 26 04:48:50 mr-slate kernel: [28895.817593] saa7164_api_i2c_write() error, ret(1) = 0x32
Aug 26 04:48:50 mr-slate kernel: [28895.817596] s5h1411_writereg: writereg error 0x19 0xf5 0x0001, ret == -5)
Aug 26 04:48:51 mr-slate kernel: [28896.517010] Event timed out
Aug 26 04:48:51 mr-slate kernel: [28896.517012] saa7164_api_i2c_write() error, ret(1) = 0x32
Aug 26 04:48:51 mr-slate kernel: [28896.517014] s5h1411_writereg: writereg error 0x19 0xf5 0x0001, ret == -5)
Aug 26 04:48:53 mr-slate kernel: [28898.585610] ata5: lost interrupt (Status 0x58)
Aug 26 04:48:53 mr-slate kernel: [28898.731373] ata5: drained 32768 bytes to clear DRQ.
Aug 26 04:48:53 mr-slate kernel: [28898.731388] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Aug 26 04:48:53 mr-slate kernel: [28898.731391] sr 4:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Aug 26 04:48:53 mr-slate kernel: [28898.731397] ata5.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Aug 26 04:48:53 mr-slate kernel: [28898.731398]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 26 04:48:53 mr-slate kernel: [28898.731400] ata5.00: status: { DRDY }
Aug 26 04:48:53 mr-slate kernel: [28898.731420] ata5: soft resetting link
Aug 26 04:48:54 mr-slate kernel: [28898.945999] ata5.00: configured for UDMA/33
Aug 26 04:48:54 mr-slate kernel: [28898.946257] ata5: EH complete
Aug 26 04:49:00 mr-slate kernel: [28905.809341] Event timed out
Aug 26 04:49:00 mr-slate kernel: [28905.809345] saa7164_api_i2c_write() error, ret(1) = 0x32
Aug 26 04:49:00 mr-slate kernel: [28905.809349] tda18271_write_regs: [5-0060|S] ERROR: idx = 0x5, len = 1, i2c_transfer returned: -5
Aug 26 04:49:00 mr-slate kernel: [28905.809352] tda18271_init: [5-0060|S] error -5 on line 831
Aug 26 04:49:00 mr-slate kernel: [28905.809354] tda18271_tune: [5-0060|S] error -5 on line 909
Aug 26 04:49:00 mr-slate kernel: [28905.809355] tda18271_set_params: [5-0060|S] error -5 on line 990
Aug 26 04:49:01 mr-slate kernel: [28906.508762] Event timed out
Aug 26 04:49:01 mr-slate kernel: [28906.508765] saa7164_api_i2c_write() error, ret(1) = 0x32
Aug 26 04:49:01 mr-slate kernel: [28906.508767] tda18271_write_regs: [4-0060|M] ERROR: idx = 0x5, len = 1, i2c_transfer returned: -5
Aug 26 04:49:01 mr-slate kernel: [28906.508769] tda18271_init: [4-0060|M] error -5 on line 831
Aug 26 04:49:01 mr-slate kernel: [28906.508771] tda18271_tune: [4-0060|M] error -5 on line 909
Aug 26 04:49:01 mr-slate kernel: [28906.508772] tda18271_set_params: [4-0060|M] error -5 on line 990
Aug 26 04:49:05 mr-slate kernel: [28910.505132] BUG: soft lockup - CPU#0 stuck for 61s! [mythfrontend.re:9123]
Aug 26 04:49:05 mr-slate kernel: [28910.505135] Modules linked in: rt3070sta nls_utf8 udf crc_itu_t pppoe pppox xt_recent xt_state xt_tcpudp xt_mac ipt_MASQUERADE iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack nf_defrag_ipv4 ipt_LOG iptable_filter ip_tables x_tables binfmt_misc ppdev cx8800 cx88xx ivtv bttv i2c_algo_bit lirc_i2c s5h1411 mt2131 s5h1409 snd_hda_codec_nvhdmi tda18271 tda8290 tuner cx25840 snd_hda_codec_via snd_hda_intel snd_hda_codec snd_usb_audio snd_pcm_oss snd_hwdep snd_usbmidi_lib snd_mixer_oss cx23885 snd_pcm cx2341x snd_seq_dummy v4l2_common snd_seq_oss videodev v4l1_compat v4l2_compat_ioctl32 videobuf_dma_sg snd_seq_midi snd_seq_midi_event videobuf_dvb snd_seq videobuf_core snd_rawmidi snd_timer ir_common btcx_risc snd_seq_device joydev asus_atk0110 xpad lirc_mceusb led_class ff_memless lirc_dev snd ir_core saa7164 psmouse dvb_core soundcore tveeprom serio_raw snd_page_alloc intel_agp nvidia(P) xhci lp parport hid_belkin usbhid hid skge ohci1394 ahci pata_jmicron ieee1394 r8169 mii [last un
Aug 26 04:49:05 mr-slate kernel: loaded: rt3070sta]
Aug 26 04:49:05 mr-slate kernel: [28910.505180] CPU 0:
Aug 26 04:49:05 mr-slate kernel: [28910.505181] Modules linked in: rt3070sta nls_utf8 udf crc_itu_t pppoe pppox xt_recent xt_state xt_tcpudp xt_mac ipt_MASQUERADE iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack nf_defrag_ipv4 ipt_LOG iptable_filter ip_tables x_tables binfmt_misc ppdev cx8800 cx88xx ivtv bttv i2c_algo_bit lirc_i2c s5h1411 mt2131 s5h1409 snd_hda_codec_nvhdmi tda18271 tda8290 tuner cx25840 snd_hda_codec_via snd_hda_intel snd_hda_codec snd_usb_audio snd_pcm_oss snd_hwdep snd_usbmidi_lib snd_mixer_oss cx23885 snd_pcm cx2341x snd_seq_dummy v4l2_common snd_seq_oss videodev v4l1_compat v4l2_compat_ioctl32 videobuf_dma_sg snd_seq_midi snd_seq_midi_event videobuf_dvb snd_seq videobuf_core snd_rawmidi snd_timer ir_common btcx_risc snd_seq_device joydev asus_atk0110 xpad lirc_mceusb led_class ff_memless lirc_dev snd ir_core saa7164 psmouse dvb_core soundcore tveeprom serio_raw snd_page_alloc intel_agp nvidia(P) xhci lp parport hid_belkin usbhid hid skge ohci1394 ahci pata_jmicron ieee1394 r8169 mii [last un
Aug 26 04:49:05 mr-slate kernel: loaded: rt3070sta]
Aug 26 04:49:05 mr-slate kernel: [28910.505213] Pid: 9123, comm: mythfrontend.re Tainted: P           2.6.32-24-generic #41-Ubuntu System Product Name
Aug 26 04:49:05 mr-slate kernel: [28910.505215] RIP: 0010:[<ffffffffa05a587f>]  [<ffffffffa05a587f>] _nv021081rm+0x20/0x22 [nvidia]
Aug 26 04:49:05 mr-slate kernel: [28910.505364] RSP: 0018:ffff8800b37c7c00  EFLAGS: 00000212
Aug 26 04:49:05 mr-slate kernel: [28910.505365] RAX: 0000000000480019 RBX: ffff88011568aca8 RCX: 0000000000400308
Aug 26 04:49:05 mr-slate kernel: [28910.505366] RDX: ffffc90012780000 RSI: ffff88012237e000 RDI: ffff880138ede800
Aug 26 04:49:05 mr-slate kernel: [28910.505367] RBP: ffffffff81013cae R08: ffff880122264000 R09: ffff88011568acc8
Aug 26 04:49:05 mr-slate kernel: [28910.505369] R10: 0000000000000000 R11: 0000000000000000 R12: 0000000000000000
Aug 26 04:49:05 mr-slate kernel: [28910.505370] R13: 0000000000000000 R14: ffff88011568acb0 R15: ffffffff81013cae
Aug 26 04:49:05 mr-slate kernel: [28910.505371] FS:  00007fe9709e37a0(0000) GS:ffff880028200000(0000) knlGS:0000000000000000
Aug 26 04:49:05 mr-slate kernel: [28910.505373] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Aug 26 04:49:05 mr-slate kernel: [28910.505374] CR2: 00007fe95333fb78 CR3: 00000000ac04e000 CR4: 00000000000006f0
Aug 26 04:49:05 mr-slate kernel: [28910.505375] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 26 04:49:05 mr-slate kernel: [28910.505376] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 26 04:49:05 mr-slate kernel: [28910.505378] Call Trace:
Aug 26 04:49:05 mr-slate kernel: [28910.505496]  [<ffffffffa04eb342>] ? _nv021814rm+0x1c7/0x1dd [nvidia]
Aug 26 04:49:05 mr-slate kernel: [28910.505625]  [<ffffffffa03e4ba0>] ? _nv014245rm+0xb6/0x11a [nvidia]
Aug 26 04:49:05 mr-slate kernel: [28910.505755]  [<ffffffffa0418b5f>] ? _nv015427rm+0x75/0x10e [nvidia]
Aug 26 04:49:05 mr-slate kernel: [28910.505872]  [<ffffffffa0322188>] ? _nv002669rm+0xb8/0x13c [nvidia]
Aug 26 04:49:05 mr-slate kernel: [28910.505992]  [<ffffffffa03223b2>] ? _nv002668rm+0x1a6/0x1b4 [nvidia]
Aug 26 04:49:05 mr-slate kernel: [28910.506112]  [<ffffffffa03227ef>] ? _nv009760rm+0x389/0x51a [nvidia]
Aug 26 04:49:05 mr-slate kernel: [28910.506231]  [<ffffffffa031e77a>] ? _nv009654rm+0x821/0x837 [nvidia]
Aug 26 04:49:05 mr-slate kernel: [28910.506350]  [<ffffffffa0319863>] ? _nv009651rm+0x106/0x1e2 [nvidia]
Aug 26 04:49:05 mr-slate kernel: [28910.506422]  [<ffffffffa00ece93>] ? _nv002236rm+0x5e6/0x6cb [nvidia]
Aug 26 04:49:05 mr-slate kernel: [28910.506488]  [<ffffffffa00f86f5>] ? _nv001725rm+0xac/0xf0 [nvidia]
Aug 26 04:49:05 mr-slate kernel: [28910.506553]  [<ffffffffa00f86c0>] ? _nv001725rm+0x77/0xf0 [nvidia]
Aug 26 04:49:05 mr-slate kernel: [28910.506655]  [<ffffffffa05b1df5>] ? _nv002112rm+0x4d5/0x67f [nvidia]
Aug 26 04:49:05 mr-slate kernel: [28910.506757]  [<ffffffffa05ae6a5>] ? rm_ioctl+0x2f/0x67 [nvidia]
Aug 26 04:49:05 mr-slate kernel: [28910.506858]  [<ffffffffa05cbfdc>] ? nv_kern_ioctl+0x15c/0x460 [nvidia]
Aug 26 04:49:05 mr-slate kernel: [28910.506959]  [<ffffffffa05cc331>] ? nv_kern_unlocked_ioctl+0x21/0x30 [nvidia]
Aug 26 04:49:05 mr-slate kernel: [28910.506964]  [<ffffffff81153d92>] ? vfs_ioctl+0x22/0xa0
Aug 26 04:49:05 mr-slate kernel: [28910.506968]  [<ffffffff81541f43>] ? thread_return+0x21b/0x418
Aug 26 04:49:05 mr-slate kernel: [28910.506969]  [<ffffffff81154041>] ? do_vfs_ioctl+0x81/0x380
Aug 26 04:49:05 mr-slate kernel: [28910.506971]  [<ffffffff811543c1>] ? sys_ioctl+0x81/0xa0
Aug 26 04:49:05 mr-slate kernel: [28910.506975]  [<ffffffff810131b2>] ? system_call_fastpath+0x16/0x1b
Aug 26 04:49:10 mr-slate kernel: [28915.801094] Event timed out
Aug 26 04:49:10 mr-slate kernel: [28915.801099] saa7164_api_i2c_write() error, ret(1) = 0x32
Aug 26 04:49:10 mr-slate kernel: [28915.801102] s5h1411_writereg: writereg error 0x19 0xf5 0x0000, ret == -5)
Aug 26 04:49:11 mr-slate kernel: [28916.500516] Event timed out
Aug 26 04:49:11 mr-slate kernel: [28916.500519] saa7164_api_i2c_write() error, ret(1) = 0x32
Aug 26 04:49:11 mr-slate kernel: [28916.500521] s5h1411_writereg: writereg error 0x19 0xf5 0x0000, ret == -5)
Aug 26 04:49:20 mr-slate kernel: [28925.792845] Event timed out
Aug 26 04:49:20 mr-slate kernel: [28925.792850] saa7164_api_i2c_write() error, ret(1) = 0x32
Aug 26 04:49:20 mr-slate kernel: [28925.792853] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
Aug 26 04:49:21 mr-slate kernel: [28926.492266] Event timed out


``` The errors just pretty much repeat and fill up kernel.log.  At this point, I am unable to access my desktop, though I am still able to ssh into the machine.  Any attempt to restart the machine fails, it starts to go down, but then hangs at some point.  The only solution is to give it a cold boot.

 Has anyone found a solution for this? I noticed some reference to nvidia drivers in the errors, I am using version 256.44, and mythtv release-0-23-fixes (25609). Also, the reference to ata5 is my NEC DVD Drive ND-3520AW.

---

### Post by markuswells on 2010-08-26
I must be missing something and I hope someone can help me get back on track. Had Ubuntu 9.04 with an hvr-1600, when the card went bad, I decided to install the 2250. I followed this tutorial but never got mythtv to recognize the card. I tried several different things and finally decided to just start from scratch. I installed Ubuntu 10.04 got all the updates, then again installed the firmware via this tutorial.

I do now have mythtv recognizing the card, I have 2 schedules direct lineups (1 antenna for digital and 1 for my cable provider, analog). When I go to inputs and scan for channels, using every variation of settings I can think of, they all respond as timed out. I read that I could change the timeout, but I can not find that setting.

lspci DOES show the card, so I have 2 questions.
1) How can I be sure the card is installed correctly, without using mythtv?
2) Where is the timeout setting and do you think thats my issue?

---

### Post by agamotto on 2010-08-26
> **markuswells said:**
> 
I do now have mythtv recognizing the card, I have 2 schedules direct lineups (1 antenna for digital and 1 for my cable provider, analog). When I go to inputs and scan for channels, using every variation of settings I can think of, they all respond as timed out. I read that I could change the timeout, but I can not find that setting.

lspci DOES show the card, so I have 2 questions.
1) How can I be sure the card is installed correctly, without using mythtv?
2) Where is the timeout setting and do you think thats my issue?

I am not sure of the timeout settings, so I won't be of much help there.  As far as checking the card is working...

In Backend setup, go to the digital lineup selection, enter the choice from SD, then go to the scan section.  Manually scan for the channels.  Whatever the tuner finds should match up with your SD data for your digital source.  Exit setup, hit watch tv.  Something should come up.  If the screen stays black, try going into the playback settings for the frontend, and choose something non-VDPAU like NORMAL or SLIM.  If nothing still comes up, then something is FUBAR with the tuner set up.

---

### Post by agamotto on 2010-08-26
> **LowSky said:**
> Barry_IA, analog and digital work on completley different frequencies. A great example would be similar to AM and FM radio. It would seem analog in my area is gone (NYC metro area). I'm not too concerned at the loss, but maybe I can try the composite or S-Video inputs to see if those work, but again as my home is completely digital I don't have much to test.

Yes, you are correct.  However, Mediacom is sending the QAM-256 local channels along with the analog stream.  I have two Mythboxes setup with 'analog' cable, and Mediacom is passing the local 'OTA' digital channels on the same coax.

---

### Post by agamotto on 2010-08-26
No, you don't need anything special for multiplex recording.  My two Mythboxes are setup with Hauppauge 1800 cards, and I can record three streams at once with no trouble, as long as I don't watch something at the same time.  This has to do with my CPU and GFX card not being cutting-edge.  The hds hum along just fine.

---

### Post by markuswells on 2010-08-27
Thanks agamotto, but thats the whole point, the scan says 'timed our, no signal'. I need to be sure this card is not a dud.

Anyone got any help, I either need to get mythtv working, or at least test the card somehow (without M$ win)

---

### Post by LowSky on 2010-08-27
> **markuswells said:**
> Thanks agamotto, but thats the whole point, the scan says 'timed our, no signal'. I need to be sure this card is not a dud.

Anyone got any help, I either need to get mythtv working, or at least test the card somehow (without M$ win)

how new is the card, you may need the newer firmware installed.

[http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw](http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw)

---

### Post by markuswells on 2010-08-27
so instead of
```

wget [http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip](http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip)
wget [http://www.steventoth.net/linux/hvr22xx/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip](http://www.steventoth.net/linux/hvr22xx/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip)
wget [http://www.steventoth.net/linux/hvr22xx/extract.sh](http://www.steventoth.net/linux/hvr22xx/extract.sh)

sh extract.sh
cp *fw /lib/firmware

```
try this?
```

wget [http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw](http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw)

cp *fw /lib/firmware

```

and since I plan to also do analog, should I also wget NXP7164-2010-03-10.1.fw

---

### Post by LowSky on 2010-08-27
```
wget http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw

cp *fw /lib/firmware
```

---

### Post by ellisgen on 2010-08-29
> wget [http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw](http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw)

cp *fw /lib/firmware

This is an older firmware, why should we be using this? Would this not be better:```
wget http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw
cp *fw /lib/firmware
```

I tried this new firmware even though I only use the HVR-2250 for ATSC tuning. It may have broken my frontend, though. Either that or something to do with the cd/dvd drive. I hadn't been using it very long, so I just reinstalled. I'm looking for a way to make a backup dvd (clone) of my entire Mythbuntu setup once I get everything like I want it.

After installing the newest driver, I shutdown the machine while a dvd movie was in the dvd-rom drive. I booted into Windows 7, played around with the remote and tuning the antenna (since I can't seem to find a signal meter for non-hdhomerun cards). After getting the antenna arranged, I restarted, booting back into Mythbuntu and found that my frontend would attempt to start and then fail after connecting to the backend, complaining (in terminal) about not being able to mount /dev/sda ...

Anyways, just thought I would document this here in case it happens to someone else and add the link to the newest firmware.

Cheers,
Wes

---

### Post by LowSky on 2010-08-29
Wes you have a few issues, first is your drives  or partition that MYthTV use are somehow not mounted and you need to fix that. That cant be cause by a tuner firmware issue, that was more than likely caused by booting into Windows.

NXP7164 firmware is for the analog tuner, it wont help digital tuning and you need to grab the mercurial repos for it from kernellabs for it to work. just adding the NXP7164 without also grabing the repo will not do anything.

Read this for backing up mythtv's database
[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

---

### Post by ellisgen on 2010-08-29
Thanks LowSky. I don't really quite understand firmware/driver stuff.

Exactly what I did to get the tuners working before setting up mythbackend: ```
wget http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip
wget http://www.steventoth.net/linux/hvr22xx/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
wget http://www.steventoth.net/linux/hvr22xx/extract.sh

sh extract.sh
cp *fw /lib/firmware

```

That and a reboot was all that was necessary to get the card working. 

I finally got my system back up and running this morning. Set up my recordings and watched a little tv before heading off to bed. I left mythfrontend open when I went to bed. (I work nights). The only thing that has happened between now and then is my wife closed mythfrontend and watched some thaitv through Firefox, and I installed xkb-plugin and changed keyboard layouts.

Mythfrontend will not start again and gives me the same error as before:```
2010-08-29 16:18:51.001 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-08-29 16:18:51.002 Using protocol version 56
mount: can't find /dev/sdb in /etc/fstab or /etc/mtab
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
Segmentation fault
```

What can I do?

dmesg | grepp saa output:```
[   15.213497] saa7164 driver loaded
[   15.213980] saa7164 0000:03:00.0: PCI INT A -> Link[APC6] -> GSI 16 (level, low) -> IRQ 16
[   15.214239] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   15.214246] saa7164[0]/0: found at 0000:03:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfd400000
[   15.214252] saa7164 0000:03:00.0: setting latency timer to 64
[   15.214257] IRQ 16/saa7164[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   15.604101] saa7164_downloadfirmware() no first image
[   15.604381] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[   15.604387] saa7164 0000:03:00.0: firmware: requesting v4l-saa7164-1.0.3.fw
[   15.745640] saa7164_downloadfirmware() firmware read 3978608 bytes.
[   15.745644] saa7164_downloadfirmware() firmware loaded.
[   15.745657] saa7164_downloadfirmware() SecBootLoader.FileSize = 3978608
[   15.745664] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   15.745666] saa7164_downloadfirmware() BSLSize = 0x0
[   15.745668] saa7164_downloadfirmware() Reserved = 0x0
[   15.745670] saa7164_downloadfirmware() Version = 0x51cc1
[   22.876033] saa7164_downloadimage() Image downloaded, booting...
[   22.980022] saa7164_downloadimage() Image booted successfully.
[   25.300021] saa7164_downloadimage() Image downloaded, booting...
[   26.968026] saa7164_downloadimage() Image booted successfully.
[   27.004687] saa7164[0]: Hauppauge eeprom: model=88061
[   27.628808] DVB: registering new adapter (saa7164)
[   30.513903] DVB: registering new adapter (saa7164)

```

lspci output ```
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Multimedia controller: Philips Semiconductors Device 7164 (rev 81)

```

Thanks,
Wes

---

### Post by markuswells on 2010-08-29
I am having no luck getting this card installed.

```

dmesg | grep saa
[   28.048833] saa7164 driver loaded
[   28.063862] saa7164 0000:02:00.0: PCI INT A -> Link[LNEA] -> GSI 17 (level, low) -> IRQ 17
[   28.064166] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   28.064173] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 17, latency: 0, mmio: 0xfe400000
[   28.064179] saa7164 0000:02:00.0: setting latency timer to 64
[   28.064183] IRQ 17/saa7164[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   28.260044] saa7164_downloadfirmware() no first image
[   28.260247] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[   28.260251] saa7164 0000:02:00.0: firmware: requesting v4l-saa7164-1.0.3.fw
[   28.276777] saa7164_downloadfirmware() Upload failed. (file not found?)

```

```

lspci | grep 7164
02:00.0 Multimedia controller: Philips Semiconductors Device 7164 (rev 81)

```
I have tried this with just the 1.0.3.3 and with the zip and extract. Any suggestions where to go from here?

---

### Post by ellisgen on 2010-08-29
> since I plan to also do analog, should I also wget NXP7164-2010-03-10.1.fw

From what I understand, just unzipping the firmware and copying is not enough to make it work. The current mythbuntu version, 10.04, already supports the v4l-saa7164-1.0.3.fw (meaning the driver is included, I think). So, if you are running 10.04, all you have to do to get it running is follow the first step on the mythtv wiki page for the HVR-2250:

```
wget http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip
wget http://www.steventoth.net/linux/hvr22xx/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
wget http://www.steventoth.net/linux/hvr22xx/extract.sh

sh extract.sh
cp *fw /lib/firmware
sudo reboot
```

If want to use any newer firmware, you'll have to follow the whole set of instructions provided by LowSky. This will take you through downloading, unzipping, and copying the firmware to /lib/firmware; then building a new driver and adding it to your mythbuntu/ubuntu install. 

Still trying to find out why my card works for a short period, and then doesn't after quitting mythfrontend.

---

### Post by LowSky on 2010-08-29
> **markuswells said:**
> I am having no luck getting this card installed.

```

dmesg | grep saa
[   28.048833] saa7164 driver loaded
[   28.063862] saa7164 0000:02:00.0: PCI INT A -> Link[LNEA] -> GSI 17 (level, low) -> IRQ 17
[   28.064166] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   28.064173] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 17, latency: 0, mmio: 0xfe400000
[   28.064179] saa7164 0000:02:00.0: setting latency timer to 64
[   28.064183] IRQ 17/saa7164[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   28.260044] saa7164_downloadfirmware() no first image
[   28.260247] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[   28.260251] saa7164 0000:02:00.0: firmware: requesting v4l-saa7164-1.0.3.fw
[   28.276777] saa7164_downloadfirmware() Upload failed. (file not found?)

```

```

lspci | grep 7164
02:00.0 Multimedia controller: Philips Semiconductors Device 7164 (rev 81)

```
I have tried this with just the 1.0.3.3 and with the zip and extract. Any suggestions where to go from here?

```
sudo apt-get install mercurial
hg clone http://kernellabs.com/hg/saa7164-stable/
cd saa7164-stable
make CONFIG_DVB_FIREDTV:=n
sudo make install
sudo reboot
```


it should then work
if not follow the instructions again from beginning to end
[http://ubuntuforums.org/showpost.php?p=9219191&postcount=212](http://ubuntuforums.org/showpost.php?p=9219191&postcount=212)

---

### Post by JMcFly on 2010-08-29
I had the digital side (didn't try the analog drivers) of my 2250 working for a few minutes earlier today (along with the analog side of my 1600, didn't feel like setting up a splitter for the antenna today), then Mythfilldatabase decided it didn't need any digital channels and I spent a few hours fighting with it and SchedulesDirect.  I manually filled in all the ATSC channels in the backend and managed to get the guide data back but now when I hit Watch TV I do not have the option of switching to the 2250 and I'm stuck on analog. The System Status menu reports all four tuners on the 2250 (I have each tuner set to a max of two) as 'has an error'. :mad:

---

### Post by ellisgen on 2010-08-29
What does your dmesg | grep 7164 say? 

What does lspci say?

I think you may have the same problem as me, only that you have another card for mythtv to connect to, so mythfrontend actually opens for you.

Also, do you have any errors when launching mythfrontend from the terminal?

---

### Post by LowSky on 2010-08-29
ellisgen your issue is that /dev/sdb changed location... meaning a hard drive partition or complete drive is not mounted to the same place it was when you set up MythTV.. you need to fix that.

Not knowing how you configured your system, I can only assume you have multiple partitions that you linked with MythTV, and that partition didn't mount at boot as it might supposed to.

Check nautilus to make sure all of your partitions are mounted, if not, you have found the drive that is an issue, the next step is to fix it's mount point and to have it mount at boot. To do that look up mounting a partition in fstab.

---

### Post by ellisgen on 2010-08-30
I only have one drive in this computer, and while there are other partitions on the drive that I will be removing soon, they are not used for data storage at this time and should have no need to be loaded. I have found that by running ```
mythfrontend --reset
``` I can get mythfrontend to open. It still complains about missing /dev/sdb PLUS /dev/sdc and /dev/sr0. But it starts with some default theme that I hate and plays recordings fine. 

I have found that the problem is somewhere after quitting mythfrontend. On shutdown it gives me the following warning:```
010-08-30 08:48:10.615 ~MythContext waiting for threads to exit.
2010-08-30 08:48:10.632 ~MythContext waiting for threads to exit.
2010-08-30 08:48:15.173 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
```

And the next time it is started up, it crashes after complaining about not being able to connect to /dev/sdb.


UPDATE: I am sure it has nothing to do with partitions because I set up mythbackend to record only on the partition the OS is on (which is already mounted). I found this thread: [http://www.gossamer-threads.com/lists/mythtv/users/441523]("http://www.gossamer-threads.com/lists/mythtv/users/441523"), which suggests that there is a bug with mythtv that has been fixed, but you've got to use auto builds to make it work. So that's what I'm off to do. Wish me luck.

UPDATE 2: using auto builds worked for me.

---

### Post by LowSky on 2010-08-30
/dev/sr0 is normally an optical drive, something really seems to be wrong with you install if your drives are dissapearing like that. check the cables to see if they are loose.

the other partitions are not mounted. Just an FYI more than likely they are not being mounted at boot, and I'm guessing you are trying to store recordings on these drives. If yes you are going to ake sure these drive mount at boot, or change the directories that myhtv records to

---

### Post by JMcFly on 2010-08-30
dmesg:
> [   17.277891] saa7164 driver loaded
[   17.293564] saa7164 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.293672] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   17.293677] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 17, latency: 0, mmio: 0xf7800000
[   17.293682] saa7164 0000:02:00.0: setting latency timer to 64
[   18.110038] saa7164_downloadfirmware() no first image
[   18.110249] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3-3.fw)
[   18.110253] saa7164 0000:02:00.0: firmware: requesting v4l-saa7164-1.0.3-3.fw
[   18.188319] saa7164_downloadfirmware() firmware read 4038864 bytes.
[   18.188322] saa7164_downloadfirmware() firmware loaded.
[   18.188329] saa7164_downloadfirmware() SecBootLoader.FileSize = 4038864
[   18.188335] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   18.188336] saa7164_downloadfirmware() BSLSize = 0x0
[   18.188337] saa7164_downloadfirmware() Reserved = 0x0
[   18.188339] saa7164_downloadfirmware() Version = 0x1d1c
[   25.590038] saa7164_downloadimage() Image downloaded, booting...
[   25.700024] saa7164_downloadimage() Image booted successfully.
[   28.040045] saa7164_downloadimage() Image downloaded, booting...
[   29.580037] saa7164_downloadimage() Image booted successfully.
[   29.620640] tveeprom 8-0000: audio processor is SAA7164 (idx 43)
[   29.620642] tveeprom 8-0000: decoder processor is SAA7164 (idx 40)
[   29.620645] saa7164[0]: Hauppauge eeprom: model=88061
[   30.374719] DVB: registering new adapter (saa7164)
[   33.658230] DVB: registering new adapter (saa7164)lspci:
> 00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:05.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port B)
00:07.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port D)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)
02:00.0 Multimedia controller: Philips Semiconductors Device 7164 (rev 81)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:07.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
mythfrontend:
> 2010-08-30 17:09:11.433 mythfrontend version: branches/release-0-23-fixes [24158] [www.mythtv.org]("http://www.mythtv.org")
2010-08-30 17:09:11.434 Using runtime prefix = /usr
2010-08-30 17:09:11.434 Using configuration directory = /home/john/.mythtv
2010-08-30 17:09:12.125 Empty LocalHostName.
2010-08-30 17:09:12.125 Using localhost value of QuadAMD
2010-08-30 17:09:12.126 Testing network connectivity to '192.168.1.90'
2010-08-30 17:09:12.145 New DB connection, total: 1
2010-08-30 17:09:12.168 Connected to database 'mythconverg' at host: 192.168.1.90
2010-08-30 17:09:12.169 Closing DB connection named 'DBManager0'
2010-08-30 17:09:12.188 ScreenSaverX11Private: XScreenSaver support enabled
2010-08-30 17:09:12.190 DPMS is disabled.
2010-08-30 17:09:12.200 Primary screen: 0.
2010-08-30 17:09:12.218 Connected to database 'mythconverg' at host: 192.168.1.90
2010-08-30 17:09:12.220 Using screen 0, 1024x768 at 0,0
2010-08-30 17:09:12.247 Desktop video mode: 1024x768 60.006 Hz
2010-08-30 17:09:12.291 MythUI Image Cache size set to 20971520 bytes
2010-08-30 17:09:12.322 Enabled verbose msgs:  important general
2010-08-30 17:09:12.333 Primary screen: 0.
2010-08-30 17:09:12.334 Using screen 0, 1024x768 at 0,0
2010-08-30 17:09:12.335 Using theme base resolution of 1280x720
2010-08-30 17:09:12.359 LIRC: Successfully initialized '/var/run/lirc/lircd' using '/home/john/.mythtv/lircrc' config
2010-08-30 17:09:12.359 JoystickMenuThread Error: Joystick disabled - Failed to read /home/john/.mythtv/joystickmenurc
2010-08-30 17:09:12.456 Using Frameless Window
2010-08-30 17:09:12.456 Using Full Screen Window
2010-08-30 17:09:12.591 Using the Qt painter
2010-08-30 17:09:12.641 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/metallurgy/base.xml'
2010-08-30 17:09:12.668 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-08-30 17:09:12.678 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-08-30 17:09:12.681 New DB connection, total: 2
2010-08-30 17:09:12.684 Current MythTV Schema Version (DBSchemaVer): 1254
2010-08-30 17:09:12.697 Connected to database 'mythconverg' at host: 192.168.1.90
2010-08-30 17:09:13.481 Registering Internal as a media playback plugin.
2010-08-30 17:09:13.547 Cannot load language en_us for module mytharchive
2010-08-30 17:09:13.659 MediaMonitorUnix::AddDevice() - empty device path.
2010-08-30 17:09:13.660 MediaMonitorUnix::AddDevice() - empty device path.
2010-08-30 17:09:13.660 MediaMonitorUnix::AddDevice() - empty device path.
2010-08-30 17:09:13.661 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-08-30 17:09:13.661 Cannot load language en_us for module mythgallery
2010-08-30 17:09:13.667 Cannot load language en_us for module mythmovies
2010-08-30 17:09:13.706 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-08-30 17:09:13.818 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-08-30 17:09:13.836 Cannot load language en_us for module mythmusic
2010-08-30 17:09:13.854 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-08-30 17:09:13.932 Cannot load language en_us for module mythvideo
2010-08-30 17:09:13.949 Cannot load language en_us for module mythweather
2010-08-30 17:09:13.954 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/metallurgy/menu-ui.xml
2010-08-30 17:09:14.038 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-08-30 17:09:14.039 Found mainmenu.xml for theme 'metallurgy'
2010-08-30 17:09:14.059 MythContext: Connecting to backend server: 192.168.1.90:6543 (try 1 of 1)
2010-08-30 17:09:14.060 Using protocol version 56
I tried adding the 1600's digital side and linking it to the antenna input in the backend (but without the physical connection to the antenna), going into System Status then says tuners 1 (1600 analog), 2 (1600 dig), 3, 4, 5 and 6 are not recording without any error messages.  When I went to Watch TV, it started on 1600 analog, I switched input to tuner 4 and now Mythfrontend is locked on a black screen with no sound or responses to keypresses (ETA: same result when I pick the 1600 digital side), I am able to alt-tab away from it but I have to kill the process and restart it.

ETA:
Here is what I get when I try to start Live TV with only the 2250 install (both sides of the 1600 deleted), unlike with the 1600 installed after a few seconds it will return me to the frontend main screen:
> 2010-08-30 18:45:27.406 Spawning LiveTV Recorder -- begin
2010-08-30 18:45:27.465 Spawning LiveTV Recorder -- end
2010-08-30 18:45:27.466 GetEntryAt(-1) failed.
2010-08-30 18:45:27.469 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2010-08-30 18:45:27.469 TV Error: HandleStateChange(): LiveTV not successfully started
2010-08-30 18:45:27.469 We have a RingBuffer
2010-08-30 18:45:27.528 TV Error: LiveTV not successfully started

---

### Post by jimko on 2010-08-30
> **ellisgen said:**
> 
mount: can't find /dev/sdb in /etc/fstab or /etc/mtab
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
Segmentation fault

I used to get this error if I tried to start frontend when a dvd was in the drive. Remove the dvd and it started fine. To solve it, I enabled [upstream fixes]("http://www.mythbuntu.org/auto-builds"). It did a big scary update and everything worked much better with the optical drive. I still have it enabled, but I don't seem to see frequent updates coming from that repository. Good luck.

To the forum in general: How about a separate thread for the analog discussion? This one is pretty big and still active. I'm still getting an i2c logging frenzy every couple days with the latest drivers and firmware so I'm sure there's more to be said on this topic.

---

### Post by markuswells on 2010-08-31
The good news is I did get digital working. I saw on the [kernellabs]("http://www.kernellabs.com/blog/?cat=3") site where someone recommended [s]hg clone [http://kernellabs.com/hg/~stoth/saa7164-v4l](http://kernellabs.com/hg/~stoth/saa7164-v4l)[/s]
when I followed your tutorial I kept taking out the -stable

So now that I have digital working, on to analog. Do I just copy the new firmware to /lib/firmware/ or do I also need to run this again?
```
hg clone http://kernellabs.com/hg/saa7164-stable/
cd saa7164-stable
make CONFIG_DVB_FIREDTV:=n
sudo make install
sudo reboot
```

and should it be stable still, or is analog support somewhere else?

---

### Post by LowSky on 2010-08-31
> **markuswells said:**
> The good news is I did get digital working. I saw on the [kernellabs]("http://www.kernellabs.com/blog/?cat=3") site where someone recommended [s]hg clone [http://kernellabs.com/hg/~stoth/saa7164-v4l](http://kernellabs.com/hg/~stoth/saa7164-v4l)[/s]
when I followed your tutorial I kept taking out the -stable

So now that I have digital working, on to analog. Do I just copy the new firmware to /lib/firmware/ or do I also need to run this again?
```
hg clone http://kernellabs.com/hg/saa7164-stable/
cd saa7164-stable
make CONFIG_DVB_FIREDTV:=n
sudo make install
sudo reboot
```

and should it be stable still, or is analog support somewhere else?



Grab the firmware from here
```
wget -c http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw
```
Then move that file to /lib/firmware

```
sudo cp NXP7164-2010-03-10.1.fw /lib/firmware
```
grab the kernel drivers doing this

```
hg clone http://kernellabs.com/hg/~stoth/saa7164-v4l
cd saa7164-v4l
make CONFIG_DVB_FIREDTV:=n
sudo make install
sudo reboot
```


that should get it working... just an FYI I haven't been able to test it to confirm that it works... sorry people but I don't really need analog

---

### Post by Barry_IA on 2010-08-31
> **markuswells said:**
> I am having no luck getting this card installed.

Markuswells:

Perhaps something in my thread re: wget not working properly may help:
    [http://ubuntuforums.org/showthread.php?t=1531757](http://ubuntuforums.org/showthread.php?t=1531757)
    "wget Download Problem"

(add the -c switch)

I'm thinking maybe something didn't download completely and a new download and install is needed.

---

### Post by markuswells on 2010-08-31
ok, lots of progress, I have 2 digitals recording at the same time. I even played with the number of recordings per adapter and was watching 1 show and recording 2 others. this card is going to ROCK!

I set the recording back to 1 per and installed the analog part, now I get
```

dmesg | grep saa
[   29.713246] saa7164 driver loaded
[   29.820322] saa7164 0000:02:00.0: PCI INT A -> Link[LNEA] -> GSI 18 (level, low) -> IRQ 18
[   29.820628] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   29.820634] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 18, latency: 0, mmio: 0xfe400000
[   29.820639] saa7164 0000:02:00.0: setting latency timer to 64
[   29.820642] IRQ 18/saa7164[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   30.110077] saa7164_downloadfirmware() no first image
[   30.110283] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[   30.110287] saa7164 0000:02:00.0: firmware: requesting NXP7164-2010-03-10.1.fw
[   30.550420] saa7164_downloadfirmware() firmware read 4019072 bytes.
[   30.550423] saa7164_downloadfirmware() firmware loaded.
[   30.550431] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[   30.550436] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   30.550438] saa7164_downloadfirmware() BSLSize = 0x0
[   30.550439] saa7164_downloadfirmware() Reserved = 0x0
[   30.550440] saa7164_downloadfirmware() Version = 0x1661c00
[   34.545095] saa7164_downloadimage() Image downloaded, booting...
[   34.545100] saa7164_downloadimage() Image booted successfully.
[   37.390701] saa7164_downloadimage() Image downloaded, booting...
[   39.050044] saa7164_downloadimage() Image booted successfully.
[   39.100571] saa7164[0]: Hauppauge eeprom: model=88061
[   40.386493] DVB: registering new adapter (saa7164)
[   44.238862] DVB: registering new adapter (saa7164)
[   44.239432] saa7164[0]: registered device video0 [mpeg]
[   44.468957] saa7164[0]: registered device video1 [mpeg]
[   44.679466] saa7164[0]: registered device vbi0 [vbi]
[   44.679524] saa7164[0]: registered device vbi1 [vbi]
[   54.722802] saa7164[0]-FWMSG: 0-00:01:17.233;thread 0xd1833363;dbgtmmhSysPwstMan;switching off analog reception...

```

Does the last line mean what I think and if so how do I turn on analog reception, because I am not able to scan or watch any analog or digital.

I know some of you do not have analog but I only get about 8 digitals, so analog is a big deal.

---

### Post by JMcFly on 2010-09-01
I managed to fix all of my 2250 problems, turns out I screwed things up trying to compile v4l-dvb in 10.04 using instructions for 9.10 and before. I formatted my / drive and reinstalled mythbuntu 10.04, restored my database, deleted all tuners and used lowsky's post 212 on page 22 of this thread, being very careful about only following the 10.04 instructions. 

My 1600 problems were caused by multiplex issues, database thought the 1600 could multiplex, found it by starting mythbackend from a terminal window and looking at the output.

---

### Post by LowSky on 2010-09-02
JMcFly I'm glad you fixed your issues.

---

### Post by markuswells on 2010-09-03
So no one knows why the firmware is throwing the message about "switching off analog reception"? Anyone? Or is this something I am going to have to ask Steven about, maybe?
```

[   54.722802] saa7164[0]-FWMSG: 0-00:01:17.233;thread 0xd1833363;dbgtmmhSysPwstMan;switching off analog reception...

```

---

### Post by jjwest85 on 2010-09-03
[markuswells]("http://ubuntuforums.org/member.php?u=307842"),

I started a new thread for analog issues with this card at:

[http://ubuntuforums.org/showthread.php?p=9803387#post9803387](http://ubuntuforums.org/showthread.php?p=9803387#post9803387)

---

### Post by sharkcohen on 2010-09-28
I walked through LowSky's HowTo on the first page of this thread, and it seemed to go well without errors.  However, the card does not appear to be happy.  This is a fresh kubuntu 10.04 install.

```

[   12.481263] saa7164_downloadfirmware() no first image
[   12.481305] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3-3.fw)
[   12.481307] saa7164 0000:01:00.0: firmware: requesting v4l-saa7164-1.0.3-3.fw
[   12.922713] saa7164_downloadfirmware() Upload failed. (file not found?)
[   12.922752] Failed to boot firmware, no features registered

```

I don't have v4l-saa7164-1.0.3-3.fw:

```

ls -la /lib/firmware/v4l-saa7164-1.0.3-3.fw
ls: cannot access /lib/firmware/v4l-saa7164-1.0.3-3.fw: No such file or directory

```

But I do have this:

```

ls -la /lib/firmware/v4l-saa7164*
-rw-r--r-- 1 root root 3978608 2010-09-28 19:24 /lib/firmware/v4l-saa7164-1.0.2.fw
-rw-r--r-- 1 root root 3978608 2010-09-28 19:24 /lib/firmware/v4l-saa7164-1.0.3.fw

```

---

### Post by silverdulcet on 2010-09-28
> **sharkcohen said:**
> I walked through LowSky's HowTo on the first page of this thread, and it seemed to go well without errors.  However, the card does not appear to be happy.  This is a fresh kubuntu 10.04 install.

```

[   12.481263] saa7164_downloadfirmware() no first image
[   12.481305] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3-3.fw)
[   12.481307] saa7164 0000:01:00.0: firmware: requesting v4l-saa7164-1.0.3-3.fw
[   12.922713] saa7164_downloadfirmware() Upload failed. (file not found?)
[   12.922752] Failed to boot firmware, no features registered

```

I don't have v4l-saa7164-1.0.3-3.fw:

```

ls -la /lib/firmware/v4l-saa7164-1.0.3-3.fw
ls: cannot access /lib/firmware/v4l-saa7164-1.0.3-3.fw: No such file or directory

```

But I do have this:

```

ls -la /lib/firmware/v4l-saa7164*
-rw-r--r-- 1 root root 3978608 2010-09-28 19:24 /lib/firmware/v4l-saa7164-1.0.2.fw
-rw-r--r-- 1 root root 3978608 2010-09-28 19:24 /lib/firmware/v4l-saa7164-1.0.3.fw

```

All the firmware versions are available from the [www.steventoth.net](www.steventoth.net) site. Here is the direct link:
[http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw]("http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw")

---

### Post by sharkcohen on 2010-09-29
> **silverdulcet said:**
> All the firmware versions are available from the [www.steventoth.net](www.steventoth.net) site. Here is the direct link:
[http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw]("http://http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw")

Thanks, that did the trick.

---

### Post by Parrallax on 2010-11-04
Hi,

I tried to install my HVR-2200 using the process at the start of thread. When I tried the make command though I got a pile of errors. But when I went and looked at the 10.04 at [http://ubuntuforums.org/showpost.php?p=9219191&postcount=212](http://ubuntuforums.org/showpost.php?p=9219191&postcount=212) it says you can skip that step if lspci shows up a Phillips SAA-7164 device, which mine does. 
So I continued to reboot and for a day or so my TV card worked. Now however whenever I try to watch TV it goes to a black screen, displays some writing about what channel I'm watching and signal strength and whatnot, and then logs me out! I go back to the login page, where I have to enter my password again. I log back in, try again, and exactly the same thing happens. It doesn't reboot, just logs out.
Can someone please help me with this problem. Or at least let me know what log files I should put up here to try and resolve the problem? Any help would be very appreciated.

Thanks!

---

### Post by Parrallax on 2010-11-06
Please? Someone? At the moment it's so frustrating to not have it working.

---

### Post by LowSky on 2010-11-06
This might seem like a tuner card issue but it is not. It's a software issue regarding X server crashing I'm guessing.

There have been people who have posted the the same issue with different tuners.

If you can please post your logs so we can see the problem.

---

### Post by zoom79 on 2010-11-24
Parrallax,

Although I'm using Fedora as a Myth BE (I have 2 Ubuntu FEs running on other machines), I was having the same problem as I tried to get a new install of Fedora 14 up & running.  I posted my problem on another forum & got a suggestion to try switching to VDPAU.  This was a GREAT 1st step & allowed me to find that I was also having some sound card issues that were hanging things.

Here's what I did in Myth FE:
- Setup - TV Settings - General - Playback (screen 3 of 8), Change profile to VDPAU

- Setup - General - 4th screen (or so) select "Scan for Audio Devices", then select the Audio Output Device that includes your sound card.

System's up & running.  Now I just need to sit down & figure out what I need to change around on my Ubuntu boxes so I can download the right Myth version that will let me access 0.24's 1264 schema my BE now uses . . .

One other thought, you should check your /var/log/dmesg file to see if your saa7164 firmware successfully loads.  I had some issues getting the right files copied into /lib/firmware at first, but once I did (given that the drivers are already a part of the kernels we are both using) it worked & you should be able to search in dmesg (using gedit) for something like the following:

saa7164_downloadimage() Image downloaded, booting...
saa7164_downloadimage() Image booted successfully.
starting firmware download(2)
saa7164_downloadimage() Image downloaded, booting...
saa7164_downloadimage() Image booted successfully.
firmware download complete.
tveeprom 1-0000: Hauppauge model 88061, rev C4F2, serial# 7229421
tveeprom 1-0000: MAC address is 00:0d:fe:6e:4f:ed
tveeprom 1-0000: tuner model is NXP 18271C2_716x (idx 152, type 4)
tveeprom 1-0000: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
tveeprom 1-0000: audio processor is SAA7164 (idx 43)
tveeprom 1-0000: decoder processor is SAA7164 (idx 40)
tveeprom 1-0000: has radio, has IR receiver, has no IR transmitter
saa7164[0]: Hauppauge eeprom: model=88061
tda18271 2-0060: creating new instance
TDA18271HD/C2 detected @ 2-0060
DVB: registering new adapter (saa7164)
DVB: registering adapter 1 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
tda18271 3-0060: creating new instance
TDA18271HD/C2 detected @ 3-0060
tda18271: performing RF tracking filter calibration
tda18271: RF tracking filter calibration complete
DVB: registering new adapter (saa7164)
DVB: registering adapter 2 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...

Best of Luck!

---

### Post by LowSky on 2010-11-24
zoom79 not everyone has an nvidia card, so VDPAU will not always work

---

### Post by dreww_1972 on 2010-12-10
Sorry to cross-post but this thread forked. I wanted to catch those that still are reading this thread but wish to get their hvr-2250 working for NTSC ("analog") inputs and mythtv. 

There is an important comment in Steve Toth's development blog:
"Steven,
 
Got things working with analog in Mythtv (Mythdora). Used Erol instructions above from Aug 6 post.

 The only thing that was a little screwy was in the MythTV backend   setup of the Capture Card. When setting the card type as “IVTV MPEG-2   Encoder” the PVR-2250 card did not show up when I scrolled through the   Video Devices. However, if I manually set the Video Device to   /dev/video# the card showed up and everything went fine."
--Credit to Robert Pollack I am simply re-posting it for folks here.  

Took me 1/2 day to get my card up and running to satisfaction. YIKES

So, to be clear, you can get the NTSC ("analog") tuner to function with  mythtv by initializing the tuner as an "IVTV MPEG-2 Encoder" defined for  /dev/video0 and /dev/video1. Then go on to define the video source  (basic cable), inputs, scan, fetch, mythfilldatabase, etc.

I have deleted all the Digital ATSC tuners (QAM and ATSC) for now. I'll enable them in a bit.

I am using the latest driver from [http://kernellabs.com/hg/~stoth/saa7164-v4l]("http://kernellabs.com/hg/%7Estoth/saa7164-v4l") (CRC value [8da3bd06a289]("http://kernellabs.com/hg/%7Estoth/saa7164-v4l/rev/8da3bd06a289")).

Latest firmwares
[http://www.steventoth.net/linux/hvr2...wares/4019072/]("http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/")
[http://www.steventoth.net/linux/hvr2...wares/4038864/]("http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/")

And compiled the driver without firedtv as indicated previously when making this module.

Hope this helps.

---

### Post by dreww_1972 on 2010-12-12
Someone also posted about the recording volume being loud when recording NTSC streams. For this use the following commands:
v4l2-ctl --set-ctrl volume=10 -d /dev/video0
v4l2-ctl --set-ctrl volume=10 -d /dev/video1

valid volume settings are from 0-24. The default for me is 20 which is too loud for my recordings/preference.

I put the following commands in my /etc/rc.local to set the recording volume on boot:
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
v4l2-ctl --set-ctrl volume=10 -d /dev/video0
v4l2-ctl --set-ctrl volume=10 -d /dev/video1
# to check settings 
#v4l2-ctl --list-ctrls -d /dev/video0
# to check settings 
#v4l2-ctl --list-ctrls -d /dev/video1

exit 0

---

### Post by keepitsimpleengr on 2010-12-14
I've been using the HVR-2250 exclusively for over the air local broadcasts, and I've had some serious headaches.  ](*,)

The latest thread is [here]("http://ubuntuforums.org/showthread.php?p=10239157#post10239157").

Thought readers of this thread might like to know..., or possibly help!

---

### Post by dreww_1972 on 2010-12-14
> **keepitsimpleengr said:**
> I've been using the HVR-2250 exclusively for over the air local broadcasts, and I've had some serious headaches.  ](*,)

The latest thread is [here]("http://ubuntuforums.org/showthread.php?p=10239157#post10239157").

Thought readers of this thread might like to know..., or possibly help!

From what I can tell this thread is the main source of info on the hvr-2250. 

Your referenced post on OTA reception of ATSC transmissions is one thing I never had a problem with and, as far as I have seen, has been a properly functioning aspect of the saa7164 driver for some time now. My comments focus on current problems relating to NTSC (a.k.a. "Analog") reception with these cards which is functionality recently added (~3months ago) to the saa7164 driver. 

Best of luck with your reception issues. I haven't had any troubles at all in that regard so I can't help you there.

---

### Post by dabone on 2010-12-19
Thanks for all this info. I needed to get a analog tuner up and running today and both my pvr500's have bit the dust. (really snowy pic on one, diagional interference patterns on the other), so I was pulling my hair out trying to get something working on this machine when I can across this thread. I had removed my 2250 after comcast removed all the clearqam off my service, and put it back in today. It took me all of 10 mins to get it running and looking great. Now I just have to wait for EPB to come with my new service on the 28th to get 77 channels to all my tvs again. (And 30 megabit bi directional internet :) ). Double the speed, no converter boxes and I'm saving about 10 dollars a month.


Later,
dabone

---

### Post by BoxOfSnoo on 2010-12-31
Is kernellabs.org down?  I can't seem to get the latest code, or even get to the main page.  My HVR2250 just stopped tuning in after working perfectly for about 9 months, so I'd like to make sure I have everything compiled correctly.

If not, does someone know of a mirror?  Does this latest driver work with the 2.6.35 kernel?

---

### Post by BoxOfSnoo on 2011-01-02
I guess the server was rebooted or something.  I got past the usb_buffer_* errors by manually changing a couple of function names, now I get this:

```

  CC [M]  /home/jonathan/Source/HVR/saa7164-v4l-8da3bd06a289/v4l/dvb_net.o
/home/jonathan/Source/HVR/saa7164-v4l-8da3bd06a289/v4l/dvb_net.c:1190: warning: 'struct dev_mc_list' declared inside parameter list
/home/jonathan/Source/HVR/saa7164-v4l-8da3bd06a289/v4l/dvb_net.c:1190: warning: its scope is only this definition or declaration, which is probably not what you want
/home/jonathan/Source/HVR/saa7164-v4l-8da3bd06a289/v4l/dvb_net.c: In function 'dvb_set_mc_filter':
/home/jonathan/Source/HVR/saa7164-v4l-8da3bd06a289/v4l/dvb_net.c:1197: error: dereferencing pointer to incomplete type
/home/jonathan/Source/HVR/saa7164-v4l-8da3bd06a289/v4l/dvb_net.c: In function 'wq_set_multicast_list':
/home/jonathan/Source/HVR/saa7164-v4l-8da3bd06a289/v4l/dvb_net.c:1247: error: 'struct net_device' has no member named 'mc_list'
/home/jonathan/Source/HVR/saa7164-v4l-8da3bd06a289/v4l/dvb_net.c:1249: error: dereferencing pointer to incomplete type
/home/jonathan/Source/HVR/saa7164-v4l-8da3bd06a289/v4l/dvb_net.c:1249: warning: left-hand operand of comma expression has no effect
/home/jonathan/Source/HVR/saa7164-v4l-8da3bd06a289/v4l/dvb_net.c:1249: warning: value computed is not used
/home/jonathan/Source/HVR/saa7164-v4l-8da3bd06a289/v4l/dvb_net.c:1250: warning: passing argument 2 of 'dvb_set_mc_filter' from incompatible pointer type
/home/jonathan/Source/HVR/saa7164-v4l-8da3bd06a289/v4l/dvb_net.c:1190: note: expected 'struct dev_mc_list *' but argument is of type 'struct dev_mc_list *'
make[3]: *** [/home/jonathan/Source/HVR/saa7164-v4l-8da3bd06a289/v4l/dvb_net.o] Error 1
make[2]: *** [_module_/home/jonathan/Source/HVR/saa7164-v4l-8da3bd06a289/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/jonathan/Source/HVR/saa7164-v4l-8da3bd06a289/v4l'
make: *** [all] Error 2

```

Now I'm beyond what I know how to do... any hints/direct instructions?

---

### Post by smontclair on 2011-01-03
Has anything changed with mythbuntu 10.10? I'm planning on doing a clean reinstall...

are the lowsky instructions at 

[http://ubuntuforums.org/showpost.php?p=9219191&postcount=212](http://ubuntuforums.org/showpost.php?p=9219191&postcount=212)

still applicable?

Thanks all!

---

### Post by LowSky on 2011-01-03
nothing has changed. follow the instructions from 10.04

---

### Post by BoxOfSnoo on 2011-01-04
> **LowSky said:**
> nothing has changed. follow the instructions from 10.04

um yes it has....  Read the latest posts.  The driver won't compile with the latest kernel.

---

### Post by LowSky on 2011-01-04
> **BoxOfSnoo said:**
> um yes it has....  Read the latest posts.  The driver won't compile with the latest kernel.

Just read you earlier posts, and all it says it a error but you didn't copy the entire log so I dont know what commands you ran to compile the driver.

Note you do not need the driver if you are running 10.04 or higher as it is now included in the kernel, unless you need analog support. More than likely all you need to do is add the firmware to the correct folders so it can load properly at boot.

I will also mention kernellabs is up and running as of Jan 4 at 7:01PM EST.

BoxOfSNoo if you need help getting things running I can gladly help as best I can. Please PM me or post here. If you suffered a breakdown after months of the system working it can only mean a software update may have broken something, or hardware failure which while rare can happen. A new kernel can have that problem if the firmware is not installed where it thinks it should be. Sometimes installing the firmware directly to the kernel /lib/firmware folder can work. Doing that solved a wifi issue I had a while back.

---

### Post by BoxOfSnoo on 2011-01-05
> **LowSky said:**
> Just read you earlier posts, and all it says it a error but you didn't copy the entire log so I dont know what commands you ran to compile the driver.


After the hg clone/hg update/unzip of the source...

```

make CONFIG_DVB_FIREDTV:=n

```

just like you suggested.  Of course it fails on the USB functions, but once I fixed that it comes up with the other errors that seem a lot harder to fix.

> **LowSky said:**
> 
Note you do not need the driver if you are running 10.04 or higher as it is now included in the kernel, unless you need analog support. More than likely all you need to do is add the firmware to the correct folders so it can load properly at boot.


Do you think I could have overwritten the modules?  Wouldn't they be the same?

> **LowSky said:**
> 
I will also mention kernellabs is up and running as of Jan 4 at 7:01PM EST.


Yes though it was down for a good 3 days I think.

> **LowSky said:**
> 
BoxOfSNoo if you need help getting things running I can gladly help as best I can. Please PM me or post here. If you suffered a breakdown after months of the system working it can only mean a software update may have broken something, or hardware failure which while rare can happen. A new kernel can have that problem if the firmware is not installed where it thinks it should be. Sometimes installing the firmware directly to the kernel /lib/firmware folder can work. Doing that solved a wifi issue I had a while back.

I had them installed to the /lib/firmware folder already.  I recopied them there just to see if there was file corruption.  I also copied them to the kernel-specific folder.

Edit: I just rebooted and no difference, I get the firmware downloaded message OK on boot but it gets 0%/no lock when I go to watch TV.

---

### Post by LowSky on 2011-01-06
Did you scan for channels?
You will not get a "lock" or a signal %, those features have not be worked on. But you should still channels if you did a scan and used schedulesdirect.

---

### Post by navodeo on 2011-01-06
> **LowSky said:**
> Did you scan for channels?
You will not get a "lock" or a signal %, those features have not be worked on. But you should still channels if you did a scan and used schedulesdirect.

When the scan finishes it says no channels found.   I'm using kernel 2.6.35.24 is that a problem?  I've seen some posts suggesting that the analog side is broken past a certain kernel?  If so what is the last kernel I should try?  Thanks for any help.

---

### Post by BoxOfSnoo on 2011-01-06
> **LowSky said:**
> Did you scan for channels?
You will not get a "lock" or a signal %, those features have not be worked on. But you should still channels if you did a scan and used schedulesdirect.

I think there's two of us looking for your help here, now - though we seem to have the same issues.  I tried to scan again; though nothing had changed from my working setup a month ago AFAIK... it came up with zero new channels.  I also am using SchedulesDirect, which was all set up for the few (but awesome) Clear QAM channels I get.

---

### Post by navodeo on 2011-01-07
BoxofSnoo- my apologies.  This has become so frrustrating - there are shards of info here & there on setting this card up.  Lowsky's instructions are the best I have found but I still can't get it to work.  Apparently receiving analog cable channels isn't very much in demand anymore but it's what I've got to do.  Wish at this point I had never built the thing!

---

### Post by BoxOfSnoo on 2011-01-07
> **navodeo said:**
> BoxofSnoo- my apologies.  This has become so frrustrating - there are shards of info here & there on setting this card up.  Lowsky's instructions are the best I have found but I still can't get it to work.  Apparently receiving analog cable channels isn't very much in demand anymore but it's what I've got to do.  Wish at this point I had never built the thing!

No need to apologize. I know how frustrating it can be!

I just want to get digital channels at this point because I already have 2 analog capture cards. I wish I knew what broke it.

---

### Post by LowSky on 2011-01-07
i am sorry if people are having issues, i and many others clearly are not. i understand the frustration. let me mention a few things.

1. digital tuner drivers and firmware still work on the newest kernel. 
2. i have not looked at the analog tuner drivers as i have no need. there are others working hard to get things working. i believe there is another thread.
3. if a card stops working months into working fine you have a few places to look, like rolling back updates, testing the signal of the feed, and testing the card to see if broken. 

navodeo if you need this card to work and the current kernel is the issue, use an older version of ubuntu that did work. 

BoxOfSnoo my instructions are clear and precise if you are still having issues with the card, why not RMA it for repair/replacement if it still possible.

---

### Post by Barry_IA on 2011-01-08
> **BoxOfSnoo said:**
> No need to apologize. I know how frustrating it can be!

I just want to get digital channels at this point because I already have 2 analog capture cards. I wish I knew what broke it.

[FONT=Palatino Linotype]Any possibility the download wasn't completed?  Take a look at my thread "[Solved] wget Download Problem".  Fixed my issue with the HVR-2250 cards not working under 10.04.   The part that might help is where I'm told to add the -c option.     [/FONT]

---

### Post by BoxOfSnoo on 2011-01-09
> **LowSky said:**
> 
2. i have not looked at the analog tuner drivers as i have no need. there are others working hard to get things working. i believe there is another thread.
3. if a card stops working months into working fine you have a few places to look, like rolling back updates, testing the signal of the feed, and testing the card to see if broken. 

navodeo if you need this card to work and the current kernel is the issue, use an older version of ubuntu that did work. 

BoxOfSnoo my instructions are clear and precise if you are still having issues with the card, why not RMA it for repair/replacement if it still possible.

Not possible, like I said the card is about 9 months old.  I am only trying to get the digital signal working again, it stopped about the 21st.  It was only a week or so later that I realized that the tuner stopped working.  Only then did I start trying to figure out how to compile the driver again.

I tested the signal by taking the same cable straight into my TV and it works fine.
:confused:

---

### Post by nbredthauer on 2011-01-18
Hello,

I am new here and to mythtv/mythbuntu and I hope I am in the right spot, I am just getting ready to attemt to build my first system.

I have free basic cable about 100 channels from Comcast but no cable box (they hooked it up with my internet) and said plug it in to the back of my tv, it pulls in chanels like 3,4,5,ect but also has chanels like 7-1,7-2,7-3.

I can get a couple of free Hauppauge HVR-2250's, would they be a good option or should I look for something else.

I think I read that it cant do analog, are the channels 3,4,5 analog, do I need another capture device to get them?

I would also like to be able to hook up my old VHS and copy them to digital.

Any hardware recommendations/points in the right direction would be a great help.

Thank you in advance!

---

### Post by silverdulcet on 2011-01-18
> **nbredthauer said:**
> Hello,

I am new here and to mythtv/mythbuntu and I hope I am in the right spot, I am just getting ready to attemt to build my first system.

I have free basic cable about 100 channels from Comcast but no cable box (they hooked it up with my internet) and said plug it in to the back of my tv, it pulls in chanels like 3,4,5,ect but also has chanels like 7-1,7-2,7-3.

I can get a couple of free Hauppauge HVR-2250's, would they be a good option or should I look for something else.

I think I read that it cant do analog, are the channels 3,4,5 analog, do I need another capture device to get them?

I would also like to be able to hook up my old VHS and copy them to digital.

Any hardware recommendations/points in the right direction would be a great help.

Thank you in advance!

The HVR-2250 will tune in any Clear QAM channels that Comcast broadcasts in your area. This is often your local broadcast stations and many non-premium channels. It varies depending on your area. 

The analogue portion of the HVR-2250 has support in the development driver. I have not tried it, perhaps other people who have can comment on how well it works currently. Otherwise you can check for information on the kernelabs.com site. 

It has two analogue inputs via the s-video/composite (RCA) breakout cable and an expansion bracket for the second one which takes up another card slot bracket. You can use these to record from your VCR or other analogue video source.

---

### Post by trueegor on 2011-01-25
I have looked and looked for an answer to this and no one seems to be talking about it.  I have some questions about the firmware.

1. What is the source of the firmware, Hauppauge?
2. Is it an upgrade/downgrade?
3. Will the card still work in Windows with the different firmware?  While I would like to switch my HTPC to Linux, I am not willing to break it in Windows while I mess around getting it to work.  

Thanks

---

### Post by silverdulcet on 2011-01-25
> **trueegor said:**
> I have looked and looked for an answer to this and no one seems to be talking about it.  I have some questions about the firmware.

1. What is the source of the firmware, Hauppauge?

The firmware is from Hauppauge, with regards to linux part of the firmware comes from kernelabs.org. 
> 2. Is it an upgrade/downgrade?

It is neither. Like many devices, the card does not store the firmware on the card it is loaded from disk every time your system boots. When you install the driver whether windows or linux that includes the firmware for that version of the driver. Ubuntu stores firmware under /lib/firmware.

> 3. Will the card still work in Windows with the different firmware?  While I would like to switch my HTPC to Linux, I am not willing to break it in Windows while I mess around getting it to work.  

It will absolutely still work with Windows with a different firmware. When Windows boots it will load the firmware from disk that is installed with whichever version of the driver you have installed. The same goes for Linux.

You are probably thinking of devices that store the firmware on flash. To upgrade the firmware on those this flash has to be re-written. This is not the case for this card.

---

### Post by azich on 2011-01-26
I was able to get an HVR-2250 working on Ubuntu 11.04 2.6.35-24-generic by substituting the basic hg clone / make / make install with something a bit more complicated but ultimately successful for me:

```

0. `sudo apt-get install v4l-conf`
1. `hg clone http://kernellabs.com/hg/~stoth/saa7164-v4l`
2. Use this as v4l/.config: [http://pastebin.com/4GPrszBV](http://pastebin.com/4GPrszBV)
4. `make`

5. For all files with implicit declaration of function 'usb_buffer_free', add the following to the top after the #includes.

#define usb_buffer_alloc(a, b, c, d) usb_alloc_coherent(a, b, c, d)
#define usb_buffer_free(a, b, c, d) usb_free_coherent(a, b, c, d)

6. Repeat steps 4 and 5 until you no longer encounter the 'usb_buffer_free' errors.

7. You should now encounter the 'struct net_device' errors. Download the full linux-source-2.6.35, decompress it, and copy the following to the v4l directory.

linux-source-2.6.35/drivers/media/dvb/dvb-core/*.h
linux-source-2.6.35/drivers/media/dvb/dvb-core/*.c

8. `make`
9. You may encounter more 'usb_buffer_free' errors, if so, repeat steps 4 and 5 again until it goes away.
10. `sudo make install`
11. `sudo modprobe -r saa7164; sudo modprobe saa7164` or `reboot`

```

Here is the relevant section of the kernel log after the modprobe: [http://pastebin.com/rWB6WBhB](http://pastebin.com/rWB6WBhB)



Hope this helps!

---

### Post by kciampi319 on 2011-01-26
I had the saa7164-stable driver running, but I need to use the analog inputs so I removed the stable driver and installed the development driver. Now I can't get any version of the driver working.  Is there something I could have missed?  I ran make remove and made sure there were no stray saa7174*.fw files hanging around in /lib/firmware.  Am I missing anything?

---

### Post by LowSky on 2011-01-26
> **azich said:**
> I was able to get an HVR-2250 working on Ubuntu 11.04 2.6.35-24-generic by substituting the basic hg clone / make / make install with something a bit more complicated but ultimately successful for me:

```

0. `sudo apt-get install v4l-conf`
1. `hg clone http://kernellabs.com/hg/~stoth/saa7164-v4l`
2. Use this as v4l/.config: [http://pastebin.com/4GPrszBV](http://pastebin.com/4GPrszBV)
4. `make`

5. For all files with implicit declaration of function 'usb_buffer_free', add the following to the top after the #includes.

#define usb_buffer_alloc(a, b, c, d) usb_alloc_coherent(a, b, c, d)
#define usb_buffer_free(a, b, c, d) usb_free_coherent(a, b, c, d)

6. Repeat steps 4 and 5 until you no longer encounter the 'usb_buffer_free' errors.

7. You should now encounter the 'struct net_device' errors. Download the full linux-source-2.6.35, decompress it, and copy the following to the v4l directory.

linux-source-2.6.35/drivers/media/dvb/dvb-core/*.h
linux-source-2.6.35/drivers/media/dvb/dvb-core/*.c

8. `make`
9. You may encounter more 'usb_buffer_free' errors, if so, repeat steps 4 and 5 again until it goes away.
10. `sudo make install`
11. `sudo modprobe -r saa7164; sudo modprobe saa7164` or `reboot`

```

Here is the relevant section of the kernel log after the modprobe: [http://pastebin.com/rWB6WBhB](http://pastebin.com/rWB6WBhB)

Congrats on getting it to work with 11.04, but that version of Ubuntu is still in development and we shouldn't be trying anything until its more stable.

Hope this helps!

> **kciampi319 said:**
> I had the saa7164-stable driver running, but I need to use the analog inputs so I removed the stable driver and installed the development driver. Now I can't get any version of the driver working.  Is there something I could have missed?  I ran make remove and made sure there were no stray saa7174*.fw files hanging around in /lib/firmware.  Am I missing anything?

First off if you can get the driver working at all, you did something catastrophic, as its built into the kernel. All you need is the firmware for basic digital use.


The dev driver does nothing for analog support, its only for unstable features for the digital side. There is a separate driver for analog all together.


Here is the analog firmware [http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw](http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw)

here is the driver [http://kernellabs.com/hg/~stoth/saa7164-v4l](http://kernellabs.com/hg/~stoth/saa7164-v4l)

---

### Post by kciampi319 on 2011-01-26
> **LowSky said:**
> First off if you can get the driver working at all, you did something catastrophic, as its built into the kernel. All you need is the firmware for basic digital use.


The dev driver does nothing for analog support, its only for unstable features for the digital side. There is a separate driver for analog all together.


Here is the analog firmware [http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw](http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw)

here is the driver [http://kernellabs.com/hg/~stoth/saa7164-v4l](http://kernellabs.com/hg/~stoth/saa7164-v4l)

Well i don't think anything catastrophic under lspci it lists as 

```
28:00.0 Multimedia controller: Philips Semiconductors Device 7164 (rev 81)
```

I have NXP7164-2010-03-10.1.fw, dvb-fe-tda10048-1.0.fw  and the 1.0.2 1.0.3-3 and 1.0.3 versions of the V4L-saa7164 firmware in my /lib/firmware folder.

I also have the firedtv config set to n 

My problem appears to be because i get errors when i compile the driver.  I probably wasn't paying attention when did the first install blew through it, and the driver that was already installed worked. Anyway this seems to be the relevant output of running:
```
make CONFIG_DVB_FIREDTV:=n
```
```
/home/kciampi/saa7164-v4l/v4l/au0828-video.c: In function 'au0828_uninit_isoc':
/home/kciampi/saa7164-v4l/v4l/au0828-video.c:185: error: implicit declaration of function 'usb_buffer_free'
/home/kciampi/saa7164-v4l/v4l/au0828-video.c: In function 'au0828_init_isoc':
/home/kciampi/saa7164-v4l/v4l/au0828-video.c:255: error: implicit declaration of function 'usb_buffer_alloc'
/home/kciampi/saa7164-v4l/v4l/au0828-video.c:256: warning: assignment makes pointer from integer without a cast
make[3]: *** [/home/kciampi/saa7164-v4l/v4l/au0828-video.o] Error 1
make[2]: *** [_module_/home/kciampi/saa7164-v4l/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/kciampi/saa7164-v4l/v4l'
make: *** [all] Error 2

```

---

### Post by kciampi319 on 2011-01-26
To answer my own question for anyone else looking I have a brand new installation of 10.10 with the the 2.6.35-24-generic which is causing my problem. 

My issue was covered here:

[http://art.ubuntuforums.org/showthread.php?t=1567490&page=6](http://art.ubuntuforums.org/showthread.php?t=1567490&page=6)

From what I see there the issue is still unresolved...
I just bought the card so I think I am going to return it.

---

### Post by Ubu_Fester on 2011-01-29
I was able to install the HVR-2250 without any problems.  I am on 10.10 with MythTV 0.23.

I followed Lowsky's installation instructions (from earlier in this post) and everything's good.  I now have a HVR-1600 and HVR-2250 side by side on the same box, with over the air (OTA) reception.

This thread was very helpful.  Thanks!     :P

---

### Post by schlidel on 2011-02-09
So do both hybrid analog/digital tuners work on the HVR-2250? I want to tune clear QAM channels and analog cable ntsc? channels with MythTV.

ie: record at one time 2xAnalog, 2xDigital or 1xDigital-1xAnalog 

I already own the HVR-2250 and have never used Linux before; just trying to find out if can proceed without too much difficulty. Thanks.

---

### Post by LowSky on 2011-02-09
> **schlidel said:**
> So do both hybrid analog/digital tuners work on the HVR-2250? I want to tune clear QAM channels and analog cable ntsc? channels with MythTV.

ie: record at one time 2xAnalog, 2xDigital or 1xDigital-1xAnalog 

I already own the HVR-2250 and have never used Linux before; just trying to find out if can proceed without too much difficulty. Thanks.


Right now the analog tuner doesn't work due to a change in the kernel. Also check your cable company most don't even have analog signals sent anymore.

If you need analog tv support (which I can't believe people do), pick a different brand tuner, or use Windows 7.

---

### Post by schlidel on 2011-02-09
> **LowSky said:**
> Right now the analog tuner doesn't work due to a change in the kernel. Also check your cable company most don't even have analog signals sent anymore.

If you need analog tv support (which I can't believe people do), pick a different brand tuner, or use Windows 7.

Yeah, all my channel are analog over cable with some clear QAM thrown in.

Is there a version of th kernel where this is supported?

Thank you.

---

### Post by agamotto on 2011-02-09
> **LowSky said:**
> Right now the analog tuner doesn't work due to a change in the kernel. Also check your cable company most don't even have analog signals sent anymore.

If you need analog tv support (which I can't believe people do), pick a different brand tuner, or use Windows 7.

There are large portions of Canada and Mexico that don't get digital yet, as they haven't formally converted.

---

### Post by nhtrader on 2011-02-09
> **schlidel said:**
> So do both hybrid analog/digital tuners work on the HVR-2250? I want to tune clear QAM channels and analog cable ntsc? channels with MythTV.

ie: record at one time 2xAnalog, 2xDigital or 1xDigital-1xAnalog 

I already own the HVR-2250 and have never used Linux before; just trying to find out if can proceed without too much difficulty. Thanks.


FYI, I have the single tuner version HVR-1250 and use comcast cable.

What's amazing is that I can record 5 SD programs simultaneously with one tuner so you'll be able to much more than I.

As far as your question is concerned, comcast broadcasts the analog on the low channels and the same programming is rebroadcast in digital format in the mid-range (for me QAM 256 channel 81 has 12 sub-channels.) Then again the same programs are rebroadcast on higher channels for HD. So the same program is usually transmitted/broadcasted by the cable company 3 different ways (SD analog, SD digital, and HD).

As far as recording multiple channels per tuner goes, this is a function of two things. One, the settings you use with MythTV and two, your cable company.

First you have to change a setting in MythTV's backend. Under <2. Capture Cards> Select the Recording Options Button and set max number of recordings to 5 (max value allowed). This will allow the tuner to record up to 5 simultaneous programs (or whatever you choose to use: 1-5)

The second variable is in discovering which channels share the same QAM channel. The easiest way to see the QAM channels associated with each station is to use the mythweb plugin.

The MythWeb plugin can be activated by using Mythbuntu Control Centre. Select the plugins button and check Mythweb. Then if you want you can password protect it at that time. But this is optional.

Then you simply open your browser and use this URL: [http://localhost/mythweb/](http://localhost/mythweb/)
Now your connected to MythWeb. 
Select the Tools Icon (key and wrench) to access settings. 
On the left side select TV and on the Right side select the 'Channel Info' Tab

Now you'll see a listing of all your stations/channels. The channels that share the same freqid will be able to be recorded simultaneously. Up to 5 programs or whatever you set the Backend to allow.

Of course, you can experiment to see how many programs your hardware will allow. Maybe your HDD isn't fast enough, or your don't have enough RAM or you clock speed is too slow. Whatever. The point here is that you can experiment and find out what your system's limit is.

I have a AMD X2 245 (2.9Ghz) with 4Gb RAM and a Seagate SATA3.0 HDD and I can record 5 SD digitally broadcast shows simultaneously, and that's only limited b/c MythTV sets the max to 5. Or I can record 2 HD programs simultaneouly, and that's limited by comcast b/c they don't send more than 2 HD stations on one QAM channel.

It's absolutely amazing. So your dual tuner will be able to do double that if your hardware will allow.

---

### Post by schlidel on 2011-02-09
> **nhtrader said:**
> FYI, I have the single tuner version HVR-1250 and use comcast cable. .....

Holy crap, that sounds amazing!  So you can record multiple sub digital channels on the same digital tuner basically?  So theoretically 10 (your numbers) with HVR-2250?

Problem is... I don't get every channel in digital form... That would be great if I could though.

I guess simplest solution for me would be to find out if I can switch plans or switch cable companies to get all digital.

I've never heard of recording multiple sub-channels though but it sounds amazing.  Anyone else have any experience recording multiple sub channels?

Off to check cable plans in my area; anyone have any experience with Time Warner in Kansas?

Edit: I have AMD X2 250 (3.0Ghz) with 2Gb RAM and WD 1TB Green (4k version, that may be a whole 'nother issue) so sounds like I should be good to go on that front. How does it perform when auto comskip starts running in that scenario (with 5 recordings running)?


> **agamotto said:**
> There are large portions of Canada and Mexico that don't get digital yet, as they haven't formally converted.

And apparently Kansas... :) Although, I'm about to find out for sure.

---

### Post by nhtrader on 2011-02-09
I forgot to say that I have only basic cable $17/mo. So again, I get SD analog, SD digital, and HD for local programming. Nothing special.

And if I were to use OTA, this would use ATSC which is now a digital signal. My tuner can use QAM or ATSC only. My tuner doesn't have analog anymore. I got rid of those b/c they are obsolete where I live: NH,USA.

---

### Post by schlidel on 2011-02-09
> **nhtrader said:**
> I forgot to say that I have only basic cable $17/mo. So again, I get SD analog, SD digital, and HD for local programming. Nothing special.

And if I were to use OTA, this would use ATSC which is now a digital signal. My tuner can use QAM or ATSC only. My tuner doesn't have analog anymore. I got rid of those b/c they are obsolete where I live: NH,USA.

I just got off chat with my local cable provider (surewest kc) and apparently they do not broadcast all channels in digital.  They still have analog broadcast so "retirement homes" can still easily access television. Sounds fair.

Who do you have for a provider? I'm chatting with Time Warner now (who also happen to have more HD...).

---

### Post by nhtrader on 2011-02-09
> **nhtrader said:**
> FYI, I have the single tuner version HVR-1250 and use comcast cable.


Comcast Basic Cable Service.

BTW, Comcast started sending HD content two years ago, but they never acknowledged it when I called customer service. I just experimented with my new LCD TV and did a channel scan and found them. No thanks to customer service.

So you should scan your channels using your TV and if you don't have a new digital TV then go to a friend's house who uses the same cable company and has the same cable package and run a new scan. The scan will show if there are any digital channels. This way you know for sure.

Of course you could just set up Mythbuntu like I did two weeks ago and play around with it. Just scan for channels and see what comes of it. 

And if you're nervous about installing mythbuntu. Don't worry. Here's a simple idea for you. Simply switch between two HDDs. I have two HDDs installed in my desktop. And if I want windows I plug in the power connector to the windows HDD. And if I want mythbuntu, I plugin in the myth HDD and unplug the connector from the windows HDD. I just leave the side panel off of my desktop for now as I play around with this. So when the computer is off I simply swap the power connector from one HDD to the other as needed. This way I don't have to get involved with dual booting and possibly corrupting/erasing my windows stuff. This is fool-proof.

If you don't have a spare HDD, a new one is only $40-$100 depending on the size. I'm using a 750Gb HDD b/c it was an old backup spare. When I get this figured out, I'll probably install a 2Tb HDD which is only $100.

---

### Post by schlidel on 2011-02-10
I have plenty of unencrypted QAM channels that I should be able to tune in with Myth and the HVR-2250.

I'm able to get my entire analog lineup plus all QAM channels with BeyondTV in Windows so I know what's available and possible.

Problem is a lot of channels are exclusively sent in analog. Losing Comedy Central (Stewart and Colbert) being the worst case off the top of my head.

I could just buy another PCI dual analog tuner that is supported by Ubuntu and use two cards. Would this be a cheap and viable solution? 

I'm going to research which tuner would be compatible with Linux and is cheap.  (After Ubuntu is done installing on my HTPC and seeing how Myth performs with the 2250)

MythTV should be able to handle an HVR-2250 and some other cheap analog PCI card, or is there some conflict there?

---

### Post by HarrisonFan on 2011-02-28
Hi,

I am running Mythbuntu 10.04 with a single 2250 and using EIT. After installation I was receiving the saa7164_api_i2c_read() errors described earlier in this thread.  These only showed up   So, I grabbed the latest stable drivers and proceeded to compile and install this driver.  It seemed like it went away until last night when these errors showed up:

[ 8803.190066] Event timed out 
[ 8803.190077] saa7164_api_i2c_read() error, ret(1) = 0x32 
[ 8803.190084] s5h1411_readreg: readreg error (ret == -5) 
[ 8805.040130] Event timed out 
[ 8805.040141] saa7164_api_i2c_read() error, ret(1) = 0x32 
[ 8805.040148] s5h1411_readreg: readreg error (ret == -5) 
[ 8812.381727] Event timed out 
[ 8812.381738] saa7164_api_transition_port() error, ret = 0x32 
[ 8812.381745] saa7164_dvb_pause_tsport() pause transition failed, ret = 0x32 
[ 8813.190061] Event timed out [ [ 8813.190073] saa7164_api_i2c_write() error, ret(1) = 0x32 
[ 8813.190081] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)

Any ideas?  I am planning on turning off EIT to see if that would help, but other than that I am at a loss. 

Thanks,
Zac


Edit: Also please let me know if this should be a different thread.

---

### Post by mrz80 on 2011-03-27
AAAARGH!!!!

Ok, is there someplace *else* we can go to download 2250 firmware than [www.steventoth.net](www.steventoth.net) ?  It would appear not to be running a functioning webserver at present.

---

### Post by mrz80 on 2011-03-27
> **mrz80 said:**
> AAAARGH!!!!

Ok, is there someplace *else* we can go to download 2250 firmware than [www.steventoth.net](www.steventoth.net) ?  It would appear not to be running a functioning webserver at present.

Wooop.  Never mind.  It looks as though it's up now.  I'm just an impatient old git is all. :)

---

### Post by LowSky on 2011-03-28
> **mrz80 said:**
> AAAARGH!!!!

Ok, is there someplace *else* we can go to download 2250 firmware than [www.steventoth.net](www.steventoth.net) ?  It would appear not to be running a functioning webserver at present.

> **mrz80 said:**
> Wooop.  Never mind.  It looks as though it's up now.  I'm just an impatient old git is all. :)

I decided to host the firmware on my webserver just in case this happens again

[http://www.robotbeard.com/hvr-2250/](http://www.robotbeard.com/hvr-2250/)

The files are in a different order, but are all there.

---

### Post by katumba1 on 2011-04-01
> **LowSky said:**
> I decided to host the firmware on my webserver just in case this happens again

[http://www.robotbeard.com/hvr-2250/](http://www.robotbeard.com/hvr-2250/)

The files are in a different order, but are all there.

LowSky, I'm trying to get this card working and have been sifting through these different posts all night... Do you mind posting the steps needed to install the 2250 using the firmware that you are now hosting?

As the ~stoth files seem to be down.

Thank you! Kat

---

### Post by LowSky on 2011-04-01
Hi Kat

Here is the the short version as 10.10 has driver support, and just needs the firmware installed.

download this file
[http://www.robotbeard.com/hvr-2250/HVR-2250_firmware.zip](http://www.robotbeard.com/hvr-2250/HVR-2250_firmware.zip)

unzip the file
then copy the .fw files to /lib/firmware (you need sudo access to nautilus)

or here is how by command line

```
wget -c http://www.robotbeard.com/hvr-2250/HVR-2250_firmware.zip
unzip HVR-2250_firmware.zip
sudo cp *fw /lib/firmware
```

---

### Post by katumba1 on 2011-04-01
Thank you for that. How do I know if it's working? lol.

I've added the card (both) in the backend. However, I can't get any channels to come in when I scan.

What am I doing wrong?

I had this working with an HVR-1600 fine. Just wanted to get the HD stuff working. I only have the basic 60 channels, plus the 3-1, 5-1 HD channels.
Do I still need the 1600 in the box or can the 2250 do all that?

Would really appreciate any help. Thank you! Kat

---

### Post by katumba1 on 2011-04-01
I installed Win7 on the box just to make sure it was all working. Audio through HDMI, High Res, HD channel reception on QAM256.

---

### Post by LowSky on 2011-04-02
> **katumba1 said:**
> Thank you for that. How do I know if it's working? lol.

I've added the card (both) in the backend. However, I can't get any channels to come in when I scan.

What am I doing wrong?

I had this working with an HVR-1600 fine. Just wanted to get the HD stuff working. I only have the basic 60 channels, plus the 3-1, 5-1 HD channels.
Do I still need the 1600 in the box or can the 2250 do all that?

Would really appreciate any help. Thank you! Kat

Kat, Sorry for the delay. I have been playing around with a Viewsonic G Tablet in the search the the Android ROM that fits me.

To your problem. Did you add a schedulesdirect.org account properly?

The HVR-2250 will handle digital channels just fine. if you need analog support keep the 1600

---

### Post by katumba1 on 2011-04-02
Thanks for getting back to me.  I thought that this card can handle both?  I've read some other posts where people setup 1/2 the card as IVTV for my basic cable feed and the digital 1/2 for the 12 or so HD channels I get.

When I go into capture cards, and try to add it under IVTV, is says 'failed to open 'dev'.

Really appreciate any help.

---

### Post by LowSky on 2011-04-03
> **katumba1 said:**
> Thanks for getting back to me.  I thought that this card can handle both?  I've read some other posts where people setup 1/2 the card as IVTV for my basic cable feed and the digital 1/2 for the 12 or so HD channels I get.

When I go into capture cards, and try to add it under IVTV, is says 'failed to open 'dev'.

Really appreciate any help.

You need to install the driver for analog support, there is a separate thread regarding that. Sorry I don't use analog at all and have not keep up on the development of it. The reason is that the all digital conversion of 2009 in the US left me with zero analog channels. With no access to them I cannot test them. If I can't test them to be working I can't support the use of them. Sorry for the inconvenience.

Like you said and from I remember reading before you loose access to half the card if you want to use analog support. Now why do that if you can use the 1600 you have to handle those recordings and let the 2250 record up to 2+ HD recordings at the same time.

---

### Post by katumba1 on 2011-04-04
Thats a good point about using the 2250 for two HD streams and then getting the 1600 to do the rest. Thanks!  Just wish I had more HD channels!  Its working great as of now. Thanks for all the help! Kat.

---

### Post by katumba1 on 2011-04-04
No go w/ the 1600 in w/ the 2250. Won't boot. Halts at login (loading firmware).  Can log in, but can't start X.  Nvidia video crashes.

Tried to do the analog MPEG install from toth's instructions. Seemed like it went ok, but 'can't find dev' from myth backend to install MPEG card.  Really like to get this working, as I'm only get 12 channels to view/record.  Those 12 look great and the myth interface is amazing.

---

### Post by ranunky on 2011-04-11
__Is any of this different for the 2200 card?

> **LowSky said:**
> [CENTER][FONT=Arial][SIZE=3][B]EDIT: I have updated this tutorial for use with 10.04, here is a direct link:

(...)

[/B][/SIZE][/FONT]then run make
[/CENTER]
 ```
make CONFIG_DVB_FIREDTV:=n
```

Does the 2200 need "CONFIG_DVB_FIRETV=:n"?

---

### Post by eternicode on 2011-04-30
LowSky, thanks for the guide on installing this card.

Unfortunately, in the two releases since 10.04 (11.04 having come out last week), there have been a lot of changes in the kernel (2.6.38-8 as of 11.04's release) that render the saa7164-stable repo (and even its sibling saa7164-dev repo) useless/unbuildable.

Fortunately, I'm a developer and I'm stubborn :D I took the time to track down the build errors and managed to get the card working great on my 11.04 build (brand spankin' new HTPC build, though I still don't have all the parts for it XD )

First, **DISCLAIMERS** (please read before using...):  The repo below is primarily for my personal use, so I have the ability to reinstall *my* card on *my* system without much difficulty -- it's very much a "worksforme" solution, and I really don't have the time to "support" it.  I am, however, perfectly willing to throw it out there in the hopes that it works for others, as well :) .  I am not a kernel developer, and I've never modified kernel module source like this before, so don't get your hopes up that this will work for you!  I really didn't have much clue what I was doing, and was ecstatic that it just built without errors, let alone that it actually worked.

There was one point after the drivers first built without errors that I was adding the card with mythtv-setup, and it seemed like my X server crashed (I was dropped to virtual terminal 1, with errors printed to screen).  Going back to VT 7 (or maybe 8; Ctrl+Alt+F7/F8 ) showed my X was still running, though.  I had missed some needed changes in the dvb_core module code (as the error messages said).  After fixing that, though, the card worked perfectly.

If you get as far as installing the built modules, and your system suddenly doesn't work somehow, you'll likely need to reinstall the entire OS, so I strongly recommend being fully prepared for that possibility before doing anything with this repo.

**further dev?**
The commit messages for the fix-commits in my repo contain URLs (mostly links to patches in mailing lists) that I referenced for the changes I made.  If anyone feels like hacking it further, those are my "sources".  I will tell you, though, it took a lot of source-reading and googling to get as far as I did :P

**usage:**
Basically, you should be able to follow the same [instructions](http://ubuntuforums.org/showthread.php?p=9219191#post9219191) LowSky posted for 10.04, using

```
hg clone https://bitbucket.org/eternicode/saa7164-stable-2.6.38/ saa7164-stable
```

instead of

```
hg clone http://kernellabs.com/hg/saa7164-stable/
```

Also, running make with the FIREDTV option thing didn't really work for me; I had to edit v4l/.config and set 3 or 4 options containing "FIREDTV" to 'n'.


Finally, **my build** (to give some idea of any incompatibilities):
Core i3-2100 CPU (integrated graphics, so no nvidia/ati graphics card drivers to worry about clashing with)
Mythbuntu 11.04 64-bit, installed the day of its release
MythTV 0.24
Kernel 2.6.38-8-generic (it's extremely likely the repo will not work with any other kernel)

---

### Post by leebier on 2011-04-30
Thanks [eternicode]("http://ubuntuforums.org/member.php?u=403886"), this worked for me!

Also, NEVER AGAIN DO I UPDATE MY UBUNTU until the version is 3-4 months old. This is a lesson I ALWAYS FORGET.

---

### Post by smgendler on 2011-05-01
I'm on 10.04 with a working 2250 card, sort of.  I'll be on 10.04 for a while since it does work.  They don't call it LTS for nuttin'!  But I still have a couple of problems that crop up.  

REPEATING MESSAGE ON SHUTDOWN: When I shut down the machine, once or twice a week, I get a quickly repeating message scrolling past the screen that scrolls too fast for me to read. ctrl-s doesn't stop it and I have to power down the machine holding the power button to shut down.  Does anyone else see this?  I would post the message here, but I don't know how to grab it or where to look for it, assuming the system logs it somewhere.

UNAVAILABLE RESOURCES FOR RECORDING: I also get a the message in MythTV on occasion when I attempt to record that says I have no available resources.  I can fix that by running mythtv-setup, make no changes, and get out.  Once mythfilldatabase is done running, I have resources to record with.  Does anyone know why that happens?  Is it preventable?

---

### Post by LowSky on 2011-05-01
Thanks for the work eternicode! 


Some notes for people wanting to upgrade or install a fresh copy of Mythbuntu or MythTV:

1. I just did a fresh install of 11.04 and I had some odd issues appear while trying to use MythTV. The 2250 is recognized, but but fails to open. Oddly if the system is upgraded from a previous working release the system works correctly.
2. You shouldn't need to compile the driver, but adding only the firmware seems to do nothing to get the system working, but like I said earlier, upgrading from a previous working version runs fine.
3. If you wish to use Ubuntu over Mythbuntu, realize you cannot use Unity. You will have to run Ubuntu in classic mode with no desktop effects. Desktop effects can cause MythTV to not run correctly in full screen mode. Blame Compiz.

---

### Post by Wazupy on 2011-05-02
Greetings LowSky,
 I was hoping you could help me out before I pull all my hair out (not that it would be a big loss)
 I started trying to get my HVR2250 on Ubuntu 10.10 (started a week ago, first experience with any Linux).  I could not tell you the any terminal read outs from that version because I had no idea how to do it.  This thread you are responsible has help me come a long way.  The problem I had was the card would seam to install, I could select the card as a DVB card but could not enter a device number and it never seamed to be recognized by Myth backend setup
 I updated to 11.04 thinking that if I was going to the hassle of setting this up, might as well be current.
 Of course I new I would be opening up Pandora's Box it a distro that is only 3 days old (I was thinking a lot of issues may have been worked out in Bata).
 

 Anyway, it looks like my driver is looking for the analog firmware (from what I can tell)
 

 dmesg output:
 ```

 [   12.550038] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300) 
 [   12.550055] saa7164_downloadfirmware() no first image 
 [   12.550063] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw) 
 [   12.628063] saa7164_downloadfirmware() Upload failed. (file not found?) 
 [   12.628065] Failed to boot firmware, no features registered 
 [   12.888117] ata6.00: configured for UDMA/100 
 [   12.889721] ata6: EH complete 
 
```
 Also, the card is recognized (lspci):O:)
 ```

 05:00.0 Multimedia controller: Philips Semiconductors SAA7164 (rev 81)
 
```
 I do get an error when running the “make CONFIG_DVB_FIREDTV:=n” Command
 ```

 make[1]: Entering directory `/home/wazupy/saa7164-stable/v4l' 
 creating symbolic links... 
 make -C firmware prep 
 make[2]: Entering directory `/home/wazupy/saa7164-stable/v4l/firmware' 
 make[2]: Leaving directory `/home/wazupy/saa7164-stable/v4l/firmware' 
 make -C firmware 
 make[2]: Entering directory `/home/wazupy/saa7164-stable/v4l/firmware' 
 make[2]: Nothing to be done for `default'. 
 make[2]: Leaving directory `/home/wazupy/saa7164-stable/v4l/firmware' 
 Kernel build directory is /lib/modules/2.6.38-8-generic/build 
 make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/home/wazupy/saa7164-stable/v4l  modules 
 make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic' 
   CC [M]  /home/wazupy/saa7164-stable/v4l/tea575x-tuner.o 
 /home/wazupy/saa7164-stable/v4l/tea575x-tuner.c: In function 'snd_tea575x_init': 
 /home/wazupy/saa7164-stable/v4l/tea575x-tuner.c:334:3: error: implicit declaration of function 'kfree' 
 make[3]: *** [/home/wazupy/saa7164-stable/v4l/tea575x-tuner.o] Error 1 
 make[2]: *** [_module_/home/wazupy/saa7164-stable/v4l] Error 2 
 make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic' 
 make[1]: *** [default] Error 2 
 make[1]: Leaving directory `/home/wazupy/saa7164-stable/v4l' 
 make: *** [all] Error 2 
 
``` But I don't know the reason.:confused:
 

 Sorry for the long post, but being a FNG, I don't know what is important.
 

 Thanks in advance :),
 Brian

---

### Post by LowSky on 2011-05-02
Hi Brian,

I am having no luck getting this card to work on 11.04 from a fresh install.

I ran into a few issues and decided to install 10.04 then install the driver and firmware, then upgrade to 10.10 then to 11.04 and currently things seems to work fine.
I know for many that does not sound like a good way of doing things, but downloading the LTS (10.04) and following my instructions does seem to work.

I believe the problem is a change in the name of a few files and folders of the newer distro and kernel. When you upgrade those older files stay in place and work alongside the new stuff. When you install fresh the files are not there and we seem to have issues.

I am thinking of trying another distro to see if the issue is just localized to Ubuntu and its forks like Mythbuntu.

---

### Post by smontclair on 2011-05-02
First off, thanks to LowSky for the excellent instructions and help. 

I just did a clean install of 11.4, on both my frontend and backend, and followed LowSky's updated instructions from post 379 of this thread, installing firmware from the terminal, and then his classic instructions from post 212, beginning with the reboot and backend configuration.

And it all works perfectly! I'm not new to linux, but i'm far from an expert, and i have botched these same instructions many times before. But for whatever reason, it worked fine for me. I used the mythbuntu live cd for the backend, and the standard ubuntu live cd with the mythbuntu install secondary for the frontend. no problems. 

for whatever its worth.

Edited to add: unity works fine with mythfrontend once you enable compiz legacy fullscreen support - [http://ubuntuforums.org/showpost.php?p=3526303&postcount=9](http://ubuntuforums.org/showpost.php?p=3526303&postcount=9)

---

### Post by eternicode on 2011-05-02
Wazupy, try using my repo ([details here](http://ubuntuforums.org/showpost.php?p=10745367&postcount=388)).  I recognize the errors you pasted from my bughunt (no promises, though).

> **LowSky said:**
> I believe the problem is a change in the name of a few files and folders of the newer distro and kernel. When you upgrade those older files stay in place and work alongside the new stuff. When you install fresh the files are not there and we seem to have issues.

The recent kernel changes have changed some variable names (no file names afaik) and made some library imports explicit that used to be implicit -- so I bet you'd find the same problem on any distro with a 2.6.38 kernel.

I'm thinking previously compiled drivers are probably forward-compatible with the newer kernels, that's why things haven't broken (yet?) ;)

---

### Post by jimko on 2011-05-02
I get the repeating message on shutdown sometimes when my 2250 goes brain-dead. You can see the message in /var/log/messages or /var/log/kern.log. They are likely about to fill up all available space on your drive if you leave it long enough. If you start getting thousands of those 7164, there is nothing to do but power off. Before you can remove one of the giant log files ```
sudo service rsyslog stop
```You can fix the unavailable resources for recording by adding an upstart rule. It's fixed in the next version, but you can add it yourself by changing this line near the top of /etc/init/mythtv-backend.conf
```
start on (local-filesystems and net-device-up IFACE=lo and started udev-finish)
```You can see [this article]("http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration") for background info

---

### Post by Wazupy on 2011-05-02
Eternicode,
 Thank you so much!  Your code worked!:p
 Thanks for all the help (LowSky too!)
 Now to fine tune my setup
 

 I don't know if you tried it, but the “build your own fractal antenna” really works great.  It cost me all of $3 to build a HD antenna that works great (gets all my channels).
 Wazupy

---

### Post by LowSky on 2011-05-03
Hmmm conflicting reports of the card working with the 11.04 without modifying files.

OK I really need a spare PC and 2250 to test things out.

---

### Post by jeb1248 on 2011-05-06
I'm just getting started using Ubuntu.  I have been using Windows 7 Media Center as a PVR with a Hauppuage 2250 card.  It works well, but I've recently purchased a Sony Bravia 55ex720 and Win7 MC now displays recordings in fits and starts.  

I thought Ubuntu with Mythtv might be a workable substitute.  I have an additional 2250 card so would like to set it up to use both cards.  I'm new to Ubuntu so have been trying to follow the various threads and glean installation instructions for the 2250 cards and Mythtv.  I think I've been more successful in getting confused than informed.

From what I've been able to gather, there's no Analog driver support for the 2250.  Is that true?  If it's out there, where can I find it and how do I install it? (remember: Newbie)  Once I get the driver installed, how can I test it?  If I can get one or both 2250's working what are the next steps to get Mythtv set up?  I understand that there's a backend server, which would be the PC with the 2250 cards, and a frontend, which would be a PC used to access the recordings and display on the TV.  Are there (simplified) instructions for setting them both up?

As I said, I'm new to this and have a singular purpose in mind so any instruction will be greatly appreciated.

---

### Post by LowSky on 2011-05-06
> **jeb1248 said:**
> 
From what I've been able to gather, there's no Analog driver support for the 2250.  Is that true?  If it's out there, where can I find it and how do I install it? (remember: Newbie)  Once I get the driver installed, how can I test it?  If I can get one or both 2250's working what are the next steps to get Mythtv set up?  I understand that there's a backend server, which would be the PC with the 2250 cards, and a frontend, which would be a PC used to access the recordings and display on the TV.  Are there (simplified) instructions for setting them both up?

As I said, I'm new to this and have a singular purpose in mind so any instruction will be greatly appreciated.

Do you really need analog support? Its use is dying, most people get there channels from digital sources. There is some support for it, I just can't speak for it. 

Here is the link to my instructions for Ubuntu 10.04 LTS
[http://ubuntuforums.org/showpost.php?p=9219191&postcount=212](http://ubuntuforums.org/showpost.php?p=9219191&postcount=212)

If you pay attention to the last few post, you can then upgrade easily to 11.04 and have a perfectly fine working system.

Not to gloat but my instructions are probably the easiest out there. If you need help send me a PM

---

### Post by jeb1248 on 2011-05-07
Thanks, LowSky, for the reply.  I have WOW! cable as my source.  When I bought my first tuner card I assumed that ATSC/ClearQAM would be fine for the same reasons that you suggested, that analog is dying.  When I tested the card I found out that it's channel scan could only find 10 - 12 channels.  I guessed that in order to get all the digital channels I'd have to up my cable subscription costs.   That's why I've gone to the Hauppauge 2250 (NTSC/ATSC/ClearQAM).  It sees all of the channels.  And that's why I was looking for Analog support.  Whew! long-winded explaination - sorry.
 
I *will* use your instructions and, if I have questions, will post here if that's OK.

---

### Post by milesnorth on 2011-05-07
With the unbridled optimism of ignorant bliss I just did a fresh install of 11.04 after several years of updating my Kubuntu htpc with Mythtv installed.  Next followed the Lowsky (thanks!) "instructions for 10.04" again and the Mythtv backend now fails to detect the tuner card.  Should have read this thread before I reformatted.

For what its worth:
lspci yields -
> 04:00.0 Multimedia controller: Philips Semiconductors SAA7164 (rev 81)
06:00.0 Multimedia controller: Pinnacle Systems Inc. AV/DV Studio Capture Card
06:00.1 FireWire (IEEE 1394): Pinnacle Systems Inc. Device 0015
06:01.0 Multimedia audio controller: Creative Labs SB X-Fidmesg lists -
> [   14.294409] saa7164 driver loaded
[   14.294477] saa7164 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.295401] CORE saa7164[0]: subsystem: 0070:8891, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   14.295408] saa7164[0]/0: found at 0000:04:00.0, rev: 129, irq: 18, latency: 0, mmio: 0xf7c00000
[   14.295415] saa7164 0000:04:00.0: setting latency timer to 64

[   14.452017] saa7164_downloadfirmware() no first image
[   14.452029] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)

[   15.385359] saa7164_downloadfirmware() Upload failed. (file not found?)
[   15.385366] Failed to boot firmware, no features registered I recall in Kubuntu 10.10 the first image download also failed but the subsequent download worked and Mythtv configured and ran just fine.

I'm not much of a Linux tinkerer, but guess I'll try the Eternicode instructions of post #388 next.   That failing I'll go back to the Lowsky suggestion of reloading 10.04 and upgrading to 11.04.

Thanks for the options guys,
Kurt

---

### Post by tgm4883 on 2011-05-07
> **milesnorth said:**
> With the unbridled optimism of ignorant bliss I just did a fresh install of 11.04 after several years of updating my Kubuntu htpc with Mythtv installed.  Next followed the Lowsky (thanks!) "instructions for 10.04" again and the Mythtv backend now fails to detect the tuner card.  Should have read this thread before I reformatted.

For what its worth:
lspci yields -
dmesg lists -
I recall in Kubuntu 10.10 the first image download also failed but the subsequent download worked and Mythtv configured and ran just fine.

I'm not much of a Linux tinkerer, but guess I'll try the Eternicode instructions of post #388 next.   That failing I'll go back to the Lowsky suggestion of reloading 10.04 and upgrading to 11.04.

Thanks for the options guys,
Kurt

Do you have any real reason to upgrade to 11.04? I usually recommend sticking to LTS releases.

---

### Post by johnlatz on 2011-05-07
The reason I upgraded to 11.04 was specifically  to get the 2.6.38 kernel and with it the SAA7164 driver in order to enable the analog recording capability of the HVR-2250.

I've recorded from both sides (analog and digital) of the card, using a coax from the cable company as input, with the only problem is that I needed to create a recording group.  Recordings are beautiful.  11.04, upgraded from 10.10...

---

### Post by milesnorth on 2011-05-08
The Eternicode  instructions of post #388 worked for the HVR-2250 with Kubuntu 11.04/Mythtv 0.24.

```
hg clone [https://bitbucket.org/eternicode/saa7164-stable-2.6.38/](https://bitbucket.org/eternicode/saa7164-stable-2.6.38/) saa7164-stable
```The following make option from Lowsky also worked.

```
make CONFIG_DVB_FIREDTV:=n
```

Thanks again.

---

### Post by dallas8101 on 2011-05-15
I was running a 9.04 install with the HVR-2250 card.  It was working flawlessly up until a few days ago when for some reason it started saying the disk was full.  The video and recordings directories could be written to, but mythfilldatabase, updates, and the home directories were frozen.  

So I started a 10.04 install using LowSkys's instructions.  I had to hardcode the CONFIG_DVB_FIREDTV=n in the ~saa*/v4l/.config file as someone else had noted.  Finally I was able to get some channels to be recognized, but not all the ones I should.  It found some combination's of QAM unencrypted analog and ASTC digital.  I should be getting ATSC 2,4,5,9,11,23 but I am only finding 2, 23.  I am not certain why it was picking up the analog, since I do not believe any of the code I used was supposed to support it.

Has anyone seen any such issue?  I was hoping to get it done in my 10 hour window before I needed to record, but that's fading fast.

Update:
I went through the scan for channels several times in different combination's.  It eventually added all the channels, plus a lot of misc non functional ones.  I edited the channels list to remove the useless ones.  It appears to be functional, but I am wondering why it is not picking up the channels properly.  Is the HVR-2250 being supported going forward?  I really like the card and its properties, it had worked perfectly, but the support has seemed rather spotty in mythbuntu since 9.04.

As has been the results in every install I have done since 8.04, with the HVR-2250, 1250, and my older PVR150's, the audio is recording, but not playing back out of the box.

---

### Post by mrz80 on 2011-05-18
Clean install of mythbuntu 11.04, with apt-get update/upgrade run this evening

Firmware files downloaded from steventoth.net

root@mythbox:~# dmesg|grep saa7164
[   19.066190] saa7164 driver loaded
[   19.066417] saa7164 0000:02:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
[   19.067078] CORE saa7164[0]: subsystem: 0070:8891, board: Hauppauge WinTV-HVR2250 [card=3,insmod option]
[   19.067084] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfd400000
[   19.067089] saa7164 0000:02:00.0: setting latency timer to 64
[   19.237590] saa7164_downloadfirmware() no first image
[   19.237599] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[   19.305596] saa7164_downloadfirmware() firmware read 4019072 bytes.
[   19.305599] saa7164_downloadfirmware() firmware loaded.
[   19.305608] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[   19.305613] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   19.305615] saa7164_downloadfirmware() BSLSize = 0x0
[   19.305616] saa7164_downloadfirmware() Reserved = 0x0
[   19.305618] saa7164_downloadfirmware() Version = 0x1661c00
[   26.160017] saa7164_downloadimage() Image downloaded, booting...
[   26.264016] saa7164_downloadimage() Image booted successfully.
[   28.384020] saa7164_downloadimage() Image downloaded, booting...
[   30.048020] saa7164_downloadimage() Image booted successfully.

At this point stuff looks to be going awry.  Instead of 

saa7164[0]: Hauppauge eeprom: model=88061

I'm getting

[   30.075197] saa7164_api_i2c_read() error, ret(1) = 0x13
[   30.661599] DVB: registering new adapter (saa7164)
[   30.663083] saa7164_api_i2c_read() error, ret(1) = 0x13
[   30.663158] saa7164_dvb_register() Frontend initialization failed
[   30.663160] saa7164_initdev() Failed to register dvb adapters on portb
[   30.663200] saa7164[0]: registered device video0 [mpeg]
[   30.894169] saa7164[0]: registered device video1 [mpeg]
[   31.105844] saa7164[0]: registered device vbi0 [vbi]
[   31.105881] saa7164[0]: registered device vbi1 [vbi]

mythtv-setup recognizes both analog tuners, and *seems* to recognize only one digital tuner.  Channel scans look to be working on analog and digital.  LiveTV puts up "Please wait..." then just dives right back to the menu.  Scheduling recordings seems to work, but nothing records.

---

### Post by timothy3g on 2011-05-20
```
hg clone https://bitbucket.org/eternicode/saa7164-stable-2.6.38/ saa7164-stable
```instead of


Hi
I cant get it too build. i runing 2.6.38-2-amd64 I get 
bttv-driver.c:3257: error: implicit declaration of function 'lock_kernel'
and from many other files.
It seems to be a problem with "#include <linux/smp_lock.h>"
If i point all files using smp_lock.h at an old smp_lock.h file (/usr/src/linux-headers-2.6.32-5-common/include/linux/smp_lock.h instead of /usr/src/linux-headers-2.6.38-2-common/include/linux/smp_lock.h ) it will build but not work.

So now i am stuck.
can't us built in module as i need card=9  it only support  up to card=8.
can't go back.

Please help.

---

### Post by mrz80 on 2011-05-21
With much thanks to Lowsky and others...  I burned the box down and fell back to my plan "B"...  I installed 10.04, got the nvidia situation sorted out, downloaded/installed the drivers as indicated earlier in the thread, then upgraded my way to 0.24.1.  Both analog and both digital tuners recognized, channel scans complete, mythfilldatabase run.  Looks like the wife'll be able to record her Castle and Grey's Anatomy again after all.  Thanks again, folks!

Now to get mythgame going and load up DescentII :-).

---

### Post by dallas8101 on 2011-05-22
As others have seen, I was having the problem where the mythbackend was starting up before the HVR2250 had finished initializing.  So the only way to get it functioning was go into the mythbackend setup and exit.  Then start mythfrontend again and the card would be available.  There have been several explanations, but none quite specific for the HVR2250.  I used the article that others have linked to, [http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration](http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration), and found that the event that needs to be detected was ```
dvb-device-added KERNEL=dvb0.frontend0
``` (add in file /etc/init/mythtv-backend.conf )

```
start on (local-filesystems and net-device-up IFACE=lo and dvb-device-added KERNEL=dvb0.frontend0)
```

The card has been setup correctly now for a couple of reboots, where it never was before. The only issue is that mythbackend is not running when mythfrontend comes up automatically after the boot.  After a few seconds the mythbackend failure message goes away and the system seems normal.  The delay seems unexpectedly long, so it may be a timeout rather than satisfying the test.  At least the failure  message 
```
DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
eno: No such file or directory (2)
```
is no longer showing up in mythbackend.log

I don't know if this will fix the problem where the card just seems to go away after a recording, but that may be an entirely different problem.

---

### Post by timothy3g on 2011-05-23
> **timothy3g said:**
> ```
hg clone https://bitbucket.org/eternicode/saa7164-stable-2.6.38/ saa7164-stable
```

Hi
I cant get it too build. i runing 2.6.38-2-amd64 I get 
bttv-driver.c:3257: error: implicit declaration of function 'lock_kernel'
and from many other files.
It seems to be a problem with "#include <linux/smp_lock.h>"
If i point all files using smp_lock.h at an old smp_lock.h file (/usr/src/linux-headers-2.6.32-5-common/include/linux/smp_lock.h instead of /usr/src/linux-headers-2.6.38-2-common/include/linux/smp_lock.h ) it will build but not work.

So now i am stuck.
can't use built in module as i need card=9  it only support  up to card=8.
can't go back.

Please help.


Some more reading it seems in the new smp_lock.h ifdef CONFIG_BKL is used to swith off lock_kernel it's calling. where BKL =  big kernel lock.  which they are trying to remove. But I am in over my head.

How did others get the make to work?
Can i just define CONFIG_BKL if so where/how?
if so will it stop working very soon?

else i have to build the whole system from scratch to go back to a working version:-#
 Please help Thanks Tim

---

### Post by markuswells on 2011-06-15
I tried the code from "eternicode" and I also get the same dmesg as "milesnorth"

[http://ubuntuforums.org/showpost.php?p=10783874&postcount=402](http://ubuntuforums.org/showpost.php?p=10783874&postcount=402)

I would bet its because I have run update and installed all the latest fixes/patches.

---

### Post by tuxattack80 on 2011-06-16
[FONT=Arial][SIZE=2]I[/SIZE][/FONT][FONT=Ubuntu][SIZE=2] was able to get my HVR-2250 running under Natty but believe me it took a lot of time and a few screaming and cussing fits. Here is how I got it working and everything including my nvidia driver still seems to work fine.

Step #1 Download and install the Mainstream kernel that matches your systems needs x86 or x86-64 
[http://kernel.ubuntu.com/~kernel-ppa/mainline]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline"). you will need to download the 2.6.38 image.deb, headers-all and headers generic in the natty folders. 

Step #2  Install the .deb packages using the sudo dpkg -i command[/SIZE][/FONT]
 [SIZE=2]
[/SIZE] 
 [FONT=Ubuntu][SIZE=2]Step #3 follow the steps on this page [http://ubuntuforums.org/showthread.php?p=9219191#post9219191](http://ubuntuforums.org/showthread.php?p=9219191#post9219191)  till you get to the hg clone part.[/SIZE][/FONT]
 [SIZE=2]
[/SIZE] 
 [FONT=Ubuntu][SIZE=2]Step #4 Use the hg clone from here instead [http://ubuntuforums.org/showpost.php?p=10745367&postcount=388](http://ubuntuforums.org/showpost.php?p=10745367&postcount=388)[/SIZE][/FONT]
 [SIZE=2]
[/SIZE] 
 [FONT=Ubuntu][SIZE=2]Step #5 Revert back to the instructions on the first page once you get down with [/SIZE][/FONT] hg clone 
 [FONT=Ubuntu][SIZE=2][/SIZE][/FONT][SIZE=2]
[/SIZE] 
 [SIZE=2]
[/SIZE] 
 [FONT=Ubuntu][SIZE=2]You will get some warnings but everything seems to have installed just fine[/SIZE][/FONT]

---

### Post by elsmandino on 2011-06-23
Hi there,

I am an absolute virgin to linux and am having my first go with Mythbuntu 11.04.

I am trying to use a Hauppauge HVR-2200 and am having no luck getting it to work.  I have just read all 42 pages of this read and am now completely confused.

Is there now a finalised way to get this card working?

I did try the instructions from the very first page, but once it got to the bit "make CONFIG_DVB_FIREDTV:=n" it just gave the following error:

[B]make -C /home/alex/saa7164-stable/v4l 
make[1]: Entering directory `/home/alex/saa7164-stable/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/alex/saa7164-stable/v4l/firmware'
make[2]: Leaving directory `/home/alex/saa7164-stable/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/alex/saa7164-stable/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/alex/saa7164-stable/v4l/firmware'
Kernel build directory is /lib/modules/2.6.38-8-generic-pae/build
make -C /lib/modules/2.6.38-8-generic-pae/build SUBDIRS=/home/alex/saa7164-stable/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic-pae'
  CC [M]  /home/alex/saa7164-stable/v4l/tuner-xc2028.o
/home/alex/saa7164-stable/v4l/tuner-xc2028.c: In function 'free_firmware':
/home/alex/saa7164-stable/v4l/tuner-xc2028.c:252:3: error: implicit declaration of function 'kfree'
/home/alex/saa7164-stable/v4l/tuner-xc2028.c: In function 'load_all_firmwares':
/home/alex/saa7164-stable/v4l/tuner-xc2028.c:314:2: error: implicit declaration of function 'kzalloc'
/home/alex/saa7164-stable/v4l/tuner-xc2028.c:314:13: warning: assignment makes pointer from integer without a cast
/home/alex/saa7164-stable/v4l/tuner-xc2028.c:365:21: warning: assignment makes pointer from integer without a cast
/home/alex/saa7164-stable/v4l/tuner-xc2028.c: In function 'xc2028_attach':
/home/alex/saa7164-stable/v4l/tuner-xc2028.c:1314:13: warning: assignment makes pointer from integer without a cast
make[3]: *** [/home/alex/saa7164-stable/v4l/tuner-xc2028.o] Error 1
make[2]: *** [_module_/home/alex/saa7164-stable/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic-pae'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/alex/saa7164-stable/v4l'
make: *** [all] Error 2

[/B]Sorry if I am covering old ground - it seems that I have picked the wrong TV card for someone that has never used Linux before!

I would really appreciate any advice as I don't want to have to give in and go back to windows.

Thanks

---

### Post by bance on 2011-06-23
```
nano ~/v4l-dvb/v4l/.config
```ctrl-W - search for CONFIG_DVB_FIREDTV=m  <<change m to n
Write out the changes(CTRL-O), then quit(CTRL-X).

     
     ```
make all 
```     ```
sudo make install
```reboot

Alternately you could've followed the messages in your own post!

---

### Post by navodeo on 2011-06-24
Just out of curiosity - by working do you mean analog & digital working?  Been trying to 18 months on & off to get this d#$@ card to work.  Get so frustrated from trying to piece together instructions I just quit each time.  Thanks for the instructions - maybe I'll take a chill pill and try again!

> **tuxattack80 said:**
> [FONT=Arial][SIZE=2]I[/SIZE][/FONT][FONT=Ubuntu][SIZE=2] was able to get my HVR-2250 running under Natty but believe me it took a lot of time and a few screaming and cussing fits. Here is how I got it working and everything including my nvidia driver still seems to work fine.

Step #1 Download and install the Mainstream kernel that matches your systems needs x86 or x86-64 
[http://kernel.ubuntu.com/~kernel-ppa/mainline]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline"). you will need to download the 2.6.38 image.deb, headers-all and headers generic in the natty folders. 

Step #2  Install the .deb packages using the sudo dpkg -i command[/SIZE][/FONT]
 [SIZE=2]
[/SIZE] 
 [FONT=Ubuntu][SIZE=2]Step #3 follow the steps on this page [http://ubuntuforums.org/showthread.php?p=9219191#post9219191](http://ubuntuforums.org/showthread.php?p=9219191#post9219191)  till you get to the hg clone part.[/SIZE][/FONT]
 [SIZE=2]
[/SIZE] 
 [FONT=Ubuntu][SIZE=2]Step #4 Use the hg clone from here instead [http://ubuntuforums.org/showpost.php?p=10745367&postcount=388](http://ubuntuforums.org/showpost.php?p=10745367&postcount=388)[/SIZE][/FONT]
 [SIZE=2]
[/SIZE] 
 [FONT=Ubuntu][SIZE=2]Step #5 Revert back to the instructions on the first page once you get down with [/SIZE][/FONT] hg clone 
 [SIZE=2]
[/SIZE] 
 [SIZE=2]
[/SIZE] 
 [FONT=Ubuntu][SIZE=2]You will get some warnings but everything seems to have installed just fine[/SIZE][/FONT]

---

### Post by Car_Ramrod on 2011-06-24
I've read through this thread and tons others...

I have a 2250 on 11.04.  The card seems to be installed fine -
Shows up in dmesg
Can add it in backend setup.

However, when I scan for channels I get nothing.
Using coax from STB into the card and it does work with Windows 7 MC.

Should be QAM 256.

Any ideas/suggestions?

---

### Post by LowSky on 2011-06-25
> **Car_Ramrod said:**
> I've read through this thread and tons others...

I have a 2250 on 11.04.  The card seems to be installed fine -
Shows up in dmesg
Can add it in backend setup.

However, when I scan for channels I get nothing.
Using coax from STB into the card and it does work with Windows 7 MC.

Should be QAM 256.

Any ideas/suggestions?


have you read my installation instructions, or the last few pages and how there are issues with 11.04?

There are work arounds and fixes. The "easiest" approach is to use 10.04 and upgrade it to 11.04 and things work fine. There is also instructions using a modified driver from one of the other posters here (sorry I forgot their name and I'm being lazy).

---

### Post by Car_Ramrod on 2011-06-25
> **LowSky said:**
> have you read my installation instructions, or the last few pages and how there are issues with 11.04?

There are work arounds and fixes. The "easiest" approach is to use 10.04 and upgrade it to 11.04 and things work fine. There is also instructions using a modified driver from one of the other posters here (sorry I forgot their name and I'm being lazy).

Yeah, I followed the modified instructions (different hg clone drivers), but I'll give the 10.04 install a shot and keep ya posted.

Thanks for the reply.  :)

---

### Post by Sketchy on 2011-06-25
Heres how I get my saa7164 going in natty

1. Firmware
[http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/](http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/)
Download the fw file from here. 
Copy to /lib/firmware

2. Modprobe.conf
```
dmesg | grep saa
``` will tell you what card you need to select, mine is card4.
so make a file 
```
nano /etc/modprobe.d/options.conf
```

```
options saa7164 card=4
```

reboot and enjoy

---

### Post by Car_Ramrod on 2011-06-26
> **LowSky said:**
> have you read my installation instructions, or the last few pages and how there are issues with 11.04?

There are work arounds and fixes. The "easiest" approach is to use 10.04 and upgrade it to 11.04 and things work fine. There is also instructions using a modified driver from one of the other posters here (sorry I forgot their name and I'm being lazy).

Okay.  So bypassing the STB yields results.

Is there any way to make this work with the STB?  Analog drivers through the STB?

---

### Post by LowSky on 2011-06-27
> **Car_Ramrod said:**
> Okay.  So bypassing the STB yields results.

Is there any way to make this work with the STB?  Analog drivers through the STB?

If you wanna use a STB get a HD PVR.

---

### Post by movieman on 2011-07-02
Anyway, I just built my new backend and the digital tuner section of the HVR-2250 worked fine after I installed the firmware and added myself to the video group. I now have OTA HD going into the backend, over the LAN to the frontend and playing on the TV.

Though I was interested to see that the Ion frontend can't play the HD video with VDPAU without dropping frames at the TV's 1366x768 native resolution and I had to switch it to 1280x720. I'm guessing Nvidia have some optimisations for HD resolutions that don't work in the general case.

---

### Post by JohnDMo on 2011-08-13
The post from eternicode in #388 worked great for me, I have essentially the exact same build. I did run the FiredTV command, it returned a few errors, however it still works.

Thanks for the great posts Low Sky and eternicode!

---

### Post by LowSky on 2011-08-31
Hello Mythbuntu users.

It pains me to tell you all but I have moved on to Arch Linux. I might be back if Arch doesn't annoy me. And oh it has! In the mean time it delights me to tell you that the 3.0 Kernel shipped with Arch seems to work pretty well with the HVR-2250. My only issue was learning my way around Modules.

I want to give credit to Sketchy's post: [#420]("http://ubuntuforums.org/showpost.php?p=10980475&postcount=420") I'm pretty sure this works

No one should need to upload any kernel drivers using 11.04+, only the firmware is needed.

I created a link on my server to host all of the firmware versions made a while back and will host as long as possible. I may move them to a public dropbox location later. I will update if needed.


Grab the firmware.
```
wget -c http://www.robotbeard.com/hvr-2250/HVR-2250_firmware.zip
```

Unzip the files
```
unzip HVR-2250_firmware.zip
```

copy the files to the /lib/firmware folder
```
sudo cp *fw /lib/firmware
```

Now check if the card can be located and what value the system has given it
```
dmesg | grep saa7164
```

on the 3rd or 4th line you should see what you are looking for it will look like this
```
[card=8,autodetected]
```
What this says is my HVR-2250 was detected at card 8, you may (probably will) get a diferent number.

Now we need to enter this card number into modprobe.d/options.conf file (I like to use gedit)
```
sudo gedit /etc/modprobe.d/options.conf
```

place this line of code in the file
```
options saa7164 card=x
```
*x = your card's number*

Reboot and check mythtv backend to see if it is listed correctly.

---

### Post by shopfloor on 2011-09-16
Followed Lowsky's instructions and installed the non free package:

here are the results, what else to do?
> [    9.813621] saa7164 driver loaded
[    9.813675] saa7164 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.813680] saa7164[0]: Your board isn't known (yet) to the driver.
[    9.813681] saa7164[0]: Try to pick one of the existing card configs via
[    9.813682] saa7164[0]: card=<n> insmod option.  Updating to the latest
[    9.813683] saa7164[0]: version might help as well.
[    9.813686] saa7164[0]: Here are valid choices for the card=<n> insmod option:
[    9.813689] saa7164[0]:    card=0 -> Unknown
[    9.813691] saa7164[0]:    card=1 -> Generic Rev2
[    9.813693] saa7164[0]:    card=2 -> Generic Rev3
[    9.813695] saa7164[0]:    card=3 -> Hauppauge WinTV-HVR2250
[    9.813698] saa7164[0]:    card=4 -> Hauppauge WinTV-HVR2200
[    9.813700] saa7164[0]:    card=5 -> Hauppauge WinTV-HVR2200
[    9.813702] saa7164[0]:    card=6 -> Hauppauge WinTV-HVR2200
[    9.813705] saa7164[0]:    card=7 -> Hauppauge WinTV-HVR2250
[    9.813707] saa7164[0]:    card=8 -> Hauppauge WinTV-HVR2250
[    9.814732] CORE saa7164[0]: subsystem: 0070:8953, board: Unknown [card=0,autodetected]
[    9.814739] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfd800000
[    9.814745] saa7164 0000:02:00.0: setting latency timer to 64
[    9.814758] saa7164_initdev() Unsupported board detected, registering without firmware

---

### Post by dividehex on 2011-09-16
It looks like you have a newer hardware revision which is not recognized by the current stable version.  You will need to download and build the latest dev version of the driver.  

You can see here that Steve added the new revision in to the dev build awhile back.
[http://kernellabs.com/hg/~stoth/saa7164-dev/rev/a73b1f6615a9]("http://kernellabs.com/hg/%7Estoth/saa7164-dev/rev/a73b1f6615a9")

Follow lowsky's instructions but instead of downloading the stable build, you will need the dev build.

[http://ubuntuforums.org/showpost.php?p=9219191&postcount=212](http://ubuntuforums.org/showpost.php?p=9219191&postcount=212)

Just replace this line:
```

hg clone [http://kernellabs.com/hg/saa7164-stable/](http://kernellabs.com/hg/saa7164-stable/)
```with this line:
```
hg clone [http://kernellabs.com/hg/~stoth/saa7164-dev/]("http://kernellabs.com/hg/%7Estoth/saa7164-dev/")
```AND

this line:
```
cd saa7164-stable
```with this line:
```
cd saa7164-dev
```Good Luck.

---

### Post by shopfloor on 2011-09-16
Thanks for the help, :D, I used the -dev firmware and then ran the "make" command

> adrian@mediabox:~/saa7164-dev$ make CONFIG_DVB_FIREDTV:=n
make -C /home/adrian/saa7164-dev/v4l 
make[1]: Entering directory `/home/adrian/saa7164-dev/v4l'
No version yet, using 2.6.38-11-generic-pae
make[1]: Leaving directory `/home/adrian/saa7164-dev/v4l'
make[1]: Entering directory `/home/adrian/saa7164-dev/v4l'
scripts/make_makefile.pl
Updating/Creating .config
Preparing to compile for kernel version 2.6.38

***WARNING:*** You do not have the full kernel sources installed.
This does not prevent you from building the v4l-dvb tree if you have the
kernel headers, but the full kernel source may be required in order to use
make menuconfig / xconfig / qconfig.

If you are experiencing problems building the v4l-dvb tree, please try
building against a vanilla kernel before reporting a bug.

Vanilla kernels are available at [http://kernel.org](http://kernel.org).
On most distros, this will compile a newly downloaded kernel:

cp /boot/config-`uname -r` <your kernel dir>/.config
cd <your kernel dir>
make all modules_install install

Please see your distro's web site for instructions to build a new kernel.

Created default (all yes) .config file
./scripts/make_myconfig.pl
make[1]: Leaving directory `/home/adrian/saa7164-dev/v4l'
make[1]: Entering directory `/home/adrian/saa7164-dev/v4l'
perl scripts/make_config_compat.pl /lib/modules/2.6.38-11-generic-pae/build ./.myconfig ./config-compat.h
creating symbolic links...
ln -sf . oss
make -C firmware prep
make[2]: Entering directory `/home/adrian/saa7164-dev/v4l/firmware'
make[2]: Leaving directory `/home/adrian/saa7164-dev/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/adrian/saa7164-dev/v4l/firmware'
  CC  ihex2fw
Generating vicam/firmware.fw
Generating dabusb/firmware.fw
Generating dabusb/bitstream.bin
Generating ttusb-budget/dspbootcode.bin
Generating cpia2/stv0672_vp4.bin
Generating av7110/bootcode.bin
make[2]: Leaving directory `/home/adrian/saa7164-dev/v4l/firmware'
Kernel build directory is /lib/modules/2.6.38-11-generic-pae/build
make -C /lib/modules/2.6.38-11-generic-pae/build SUBDIRS=/home/adrian/saa7164-dev/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic-pae'
  CC [M]  /home/adrian/saa7164-dev/v4l/tuner-xc2028.o
/home/adrian/saa7164-dev/v4l/tuner-xc2028.c: In function 'free_firmware':
/home/adrian/saa7164-dev/v4l/tuner-xc2028.c:252:3: error: implicit declaration of function 'kfree'
/home/adrian/saa7164-dev/v4l/tuner-xc2028.c: In function 'load_all_firmwares':
/home/adrian/saa7164-dev/v4l/tuner-xc2028.c:314:2: error: implicit declaration of function 'kzalloc'
/home/adrian/saa7164-dev/v4l/tuner-xc2028.c:314:13: warning: assignment makes pointer from integer without a cast
/home/adrian/saa7164-dev/v4l/tuner-xc2028.c:365:21: warning: assignment makes pointer from integer without a cast
/home/adrian/saa7164-dev/v4l/tuner-xc2028.c: In function 'xc2028_attach':
/home/adrian/saa7164-dev/v4l/tuner-xc2028.c:1314:13: warning: assignment makes pointer from integer without a cast
make[3]: *** [/home/adrian/saa7164-dev/v4l/tuner-xc2028.o] Error 1
make[2]: *** [_module_/home/adrian/saa7164-dev/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic-pae'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/adrian/saa7164-dev/v4l'
make: *** [all] Error 2
What is vanilla kernel? This is a virgin install of 11.04 (32 bit)
Being a newb to linux Im a little hesitant, do I proceed with sudo make install?

EDIT: A little snooping leads me to think that I need to install 

[LIST]
[*] kernel-source or kernel-headers
[*] (OpenSuSE and fedora only) kernel-devel
[*] make
[*] gcc
[*] git
[*] patch
[*] patchutils
[*] libproc-processtable-perl
[/LIST]
This is from - [http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

Linux TV for the HVR-2200 suggests ------------([http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200))
__> apt-get install get patchutils lsdiff libproc-processtable-perl build-essential

Unfortunately this falls over, even when using sudo
> adrian@mediabox:~$ sudo apt-get install get patchutils lsdiff libproc-processtable-perl build-essential
[sudo] password for adrian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package get
E: Unable to locate package lsdiff
adrian@mediabox:~$ 




*Rubs chin thoughtfully*

What else?

---

### Post by dividehex on 2011-09-17
Try installing the kernel source
```
sudo apt-get install linux-source
```

---

### Post by shopfloor on 2011-09-18
Thanks again, I tried that and the suggestions from Linux TV, still nothing. 

Little bit lost now.

---

### Post by LowSky on 2011-09-18
can you give us the output of ```
lspci
```

i want to see the revision number it gives your hvr-2200

---

### Post by shopfloor on 2011-09-25
lspci -vv
> 02:00.0 Multimedia controller: Philips Semiconductors SAA7164 (rev 81)
    Subsystem: Hauppauge computer works Inc. WinTV HVR-2200
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 4 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at fd800000 (64-bit, non-prefetchable) [size=4M]
    Region 2: Memory at fd400000 (64-bit, non-prefetchable) [size=4M]
    Capabilities: <access denied>
    Kernel driver in use: saa7164
    Kernel modules: saa7164


> adrian@mediabox:~$ dmesg | grep saa7164
[    8.432894] saa7164 driver loaded
[    8.432948] saa7164 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.432952] saa7164[0]: Your board isn't known (yet) to the driver.
[    8.432953] saa7164[0]: Try to pick one of the existing card configs via
[    8.432954] saa7164[0]: card=<n> insmod option.  Updating to the latest
[    8.432955] saa7164[0]: version might help as well.
[    8.432959] saa7164[0]: Here are valid choices for the card=<n> insmod option:
[    8.432961] saa7164[0]:    card=0 -> Unknown
[    8.432963] saa7164[0]:    card=1 -> Generic Rev2
[    8.432965] saa7164[0]:    card=2 -> Generic Rev3
[    8.432967] saa7164[0]:    card=3 -> Hauppauge WinTV-HVR2250
[    8.432970] saa7164[0]:    card=4 -> Hauppauge WinTV-HVR2200
[    8.432972] saa7164[0]:    card=5 -> Hauppauge WinTV-HVR2200
[    8.432974] saa7164[0]:    card=6 -> Hauppauge WinTV-HVR2200
[    8.432976] saa7164[0]:    card=7 -> Hauppauge WinTV-HVR2250
[    8.432978] saa7164[0]:    card=8 -> Hauppauge WinTV-HVR2250
[    8.433797] CORE saa7164[0]: subsystem: 0070:8953, board: Unknown [card=0,autodetected]
[    8.433804] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfd800000
[    8.433811] saa7164 0000:02:00.0: setting latency timer to 64
[    8.433823] saa7164_initdev() Unsupported board detected, registering without firmwar


---

### Post by shopfloor on 2011-10-01
Got it working it seems!
Formatted and reinstalled, 
Followed the Linux TV instructions for my card
Manually added NXP7164-2010-03-10.1.fw) and v4l-saa7164-1.0.3-3.fw to my firmware folder
> adrian@mediabox:~$ dmesg | grep saa7164
[    9.087425] saa7164 driver loaded
[    9.087481] saa7164 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.091727] CORE saa7164[0]: subsystem: 0070:8953, board: Hauppauge WinTV-HVR2200 [card=10,autodetected]
[    9.091734] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfd800000
[    9.091741] saa7164 0000:02:00.0: setting latency timer to 64
[    9.252011] saa7164_downloadfirmware() no first image
[    9.252021] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[    9.857667] saa7164_downloadfirmware() firmware read 4019072 bytes.
[    9.857670] saa7164_downloadfirmware() firmware loaded.
[    9.857681] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[    9.857687] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[    9.857689] saa7164_downloadfirmware() BSLSize = 0x0
[    9.857691] saa7164_downloadfirmware() Reserved = 0x0
[    9.857693] saa7164_downloadfirmware() Version = 0x1661c00
[   16.712032] saa7164_downloadimage() Image downloaded, booting...
[   16.816037] saa7164_downloadimage() Image booted successfully.
[   18.936030] saa7164_downloadimage() Image downloaded, booting...
[   20.808030] saa7164_downloadimage() Image booted successfully.
[   20.852578] saa7164[0]: Warning: Unknown Hauppauge model #89009
[   20.852580] saa7164[0]: Hauppauge eeprom: model=89009
[   21.197799] DVB: registering new adapter (saa7164)
[   23.835113] DVB: registering new adapter (saa7164)


---

### Post by rmjohnson144 on 2011-11-05
I just installed mythbuntu 11.10 and can't my TV to work.

I have no clue on how to setup this mythtv, but I know a little about Ubuntu.  

here's what I found so far:

lspci -vv output:

02:00.0 Multimedia controller: Philips Semiconductors SAA7164 (rev 81)
	Subsystem: Hauppauge computer works Inc. WinTV HVR-2250
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at fb800000 (64-bit, non-prefetchable) [size=4M]
	Region 2: Memory at fb400000 (64-bit, non-prefetchable) [size=4M]
	Capabilities: <access denied>
	Kernel driver in use: saa7164
	Kernel modules: saa7164

then I ran the dmesg | grep saa7164 and output was:


[    9.733320] saa7164 driver loaded
[    9.733380] saa7164 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.735131] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[    9.735137] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 17, latency: 0, mmio: 0xfb800000
[    9.735144] saa7164 0000:02:00.0: setting latency timer to 64
[    9.894821] saa7164_downloadfirmware() no first image
[    9.894830] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[    9.951274] saa7164_downloadfirmware() Upload failed. (file not found?)

it seems there is a driver, but some firmware update failed.

if you have any clues can you help me at this thread.

[http://ubuntuforums.org/showpost.php?p=11426417&postcount=1](http://ubuntuforums.org/showpost.php?p=11426417&postcount=1)


Thanks for any help
-=Mark=-

---

### Post by agent5150 on 2011-11-08
Hi, I was using Mythtv up until 0.22 version.  Then I switched to Windows 7 MC because my HVR 2250 was such a pain to setup in Mythtv.

I would like to come back to mythtv using mythbuntu but want to know:

-does ubuntu kernel has hvr-2250 drivers or are we still stuck with kernel labs ones.

-does the IR and IR Blasters found on HVR-2250 work under mythbuntu?
-does both HD and SD tuner work under mythbuntu

thanks.

---

### Post by Tasmac on 2011-11-10
I have been trying for three days to get backend installed on my ubuntu 11.10 server. Half of which has been reading thousands of post. So I went to ubuntu 11.10 desktop(that terminal typing and editing in vi got my eyes crossing up)

Hauppauge 2250

Here what I have done so far:

_dmesg|grep saa7164_

```
anthony@Media-server:~/media_build/v4l$ dmesg|grep saa7164
[   21.493708] saa7164 driver loaded
[   21.493758] saa7164 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.494914] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,insmod option]
[   21.494919] saa7164[0]/0: found at 0000:04:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xf2c00000
[   21.494925] saa7164 0000:04:00.0: setting latency timer to 64
[   21.664839] saa7164_downloadfirmware() no first image
[   21.664849] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[   21.698435] saa7164_downloadfirmware() Upload failed. (file not found?)
[ 2436.900130] saa7164 0000:04:00.0: PCI INT A disabled
[ 2486.283948] saa7164 driver loaded
[ 2486.283997] saa7164 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 2486.285508] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,insmod option]
[ 2486.285514] saa7164[0]/0: found at 0000:04:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xf2c00000
[ 2486.285523] saa7164 0000:04:00.0: setting latency timer to 64
[ 2486.443900] saa7164_downloadfirmware() no first image
[ 2486.443910] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[ 2486.445725] saa7164_downloadfirmware() Upload failed. (file not found?)
```_lspci -vv_

```
04:00.0 Multimedia controller: Philips Semiconductors SAA7164 (rev 81)
    Subsystem: Hauppauge computer works Inc. WinTV HVR-2250
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at f2c00000 (64-bit, non-prefetchable) [size=4M]
    Region 2: Memory at f2800000 (64-bit, non-prefetchable) [size=4M]
    Capabilities: <access denied>
    Kernel driver in use: saa7164
    Kernel modules: saa7164

```_compiling V4L-DVB Device Drivers_ according to [http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

```
 CC      /home/anthony/media_build/v4l/zl10039.mod.o
  LD [M]  /home/anthony/media_build/v4l/zl10039.ko
  CC      /home/anthony/media_build/v4l/zl10353.mod.o
  LD [M]  /home/anthony/media_build/v4l/zl10353.ko
  CC      /home/anthony/media_build/v4l/zr36016.mod.o
  LD [M]  /home/anthony/media_build/v4l/zr36016.ko
  CC      /home/anthony/media_build/v4l/zr36050.mod.o
  LD [M]  /home/anthony/media_build/v4l/zr36050.ko
  CC      /home/anthony/media_build/v4l/zr36060.mod.o
  LD [M]  /home/anthony/media_build/v4l/zr36060.ko
  CC      /home/anthony/media_build/v4l/zr36067.mod.o
  LD [M]  /home/anthony/media_build/v4l/zr36067.ko
  CC      /home/anthony/media_build/v4l/zr364xx.mod.o
  LD [M]  /home/anthony/media_build/v4l/zr364xx.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
./scripts/rmmod.pl check
found 496 modules
make[1]: Leaving directory `/home/anthony/media_build/v4l'
**********************************************************
* Compilation finished. Use 'make install' to install them
**********************************************************
anthony@Media-server:~/media_build$ ls
backports  COPYING                INSTALL  Makefile  README.patches
build      dvb-firmwares.tar.bz2  linux    README    v4l
anthony@Media-server:~/media_build$ sudo make install
[sudo] password for anthony: 
make -C /home/anthony/media_build/v4l install
make[1]: Entering directory `/home/anthony/media_build/v4l'

Removing obsolete files from /lib/modules/3.0.0-12-generic/kernel/drivers/media/IR/keymaps:


Removing obsolete files from /lib/modules/3.0.0-12-generic/kernel/drivers/media/video:


Removing obsolete files from /lib/modules/3.0.0-12-generic/kernel/drivers/media/dvb/cinergyT2:


Removing obsolete files from /lib/modules/3.0.0-12-generic/kernel/drivers/media/common:


Removing obsolete files from /lib/modules/3.0.0-12-generic/kernel/drivers/media/dvb/frontends:


Removing obsolete files from /lib/modules/3.0.0-12-generic/kernel/drivers/media/IR:


Hmm... distro kernel with a non-standard place for module backports detected.
Please always prefer to use vanilla upstream kernel with V4L/DVB
I'll try to remove old/obsolete LUM files from /lib/modules/3.0.0-12-generic//updates/dkms:
Installing kernel modules under /lib/modules/3.0.0-12-generic/kernel/drivers/media/:
    video/gspca/m5602/: gspca_m5602.ko 
    /: media.ko 
    video/saa7164/: saa7164.ko 
    video/zoran/: videocodec.ko zr36050.ko zr36016.ko 
        zr36060.ko zr36067.ko 
    video/cpia2/: cpia2.ko 
    dvb/b2c2/: b2c2-flexcop-pci.ko b2c2-flexcop.ko b2c2-flexcop-usb.ko 
    video/hdpvr/: hdpvr.ko 
    video/sn9c102/: sn9c102.ko 
    dvb/dvb-core/: dvb-core.ko 
    video/: adp1653.ko videobuf-dma-contig.ko s5k6aa.ko 
        vpx3220.ko videobuf-dma-sg.ko bt856.ko 
        v4l2-mem2mem.ko ov5642.ko upd64083.ko 
        v4l2-compat-ioctl32.ko videobuf-core.ko noon010pc30.ko 
        ths7303.ko videobuf2-memops.ko tda9840.ko 
        saa7191.ko cx2341x.ko wm8775.ko 
        meye.ko adv7180.ko rj54n1cb0c.ko 
        saa7185.ko mt9p031.ko tuner.ko 
        mt9t031.ko zr364xx.ko ov2640.ko 
        ks0127.ko videobuf-dvb.ko tvaudio.ko 
        tea6420.ko bt866.ko mt9v011.ko 
        imx074.ko msp3400.ko tvp514x.ko 
        mem2mem_testdev.ko tcm825x.ko soc_camera.ko 
        wm8739.ko stkwebcam.ko soc_mediabus.ko 
        sr030pc30.ko tda7432.ko w9966.ko 
        ir-kbd-i2c.ko mt9m001.ko upd64031a.ko 
        tea6415c.ko videobuf2-dma-contig.ko bt819.ko 
        mt9t001.ko ov6650.ko videodev.ko 
        ov9740.ko mxb.ko adv7175.ko 
        vivi.ko soc_camera_platform.ko adv7343.ko 
        cs53l32a.ko s2255drv.ko btcx-risc.ko 
        saa7110.ko saa7115.ko saa6588.ko 
        ak881x.ko tvp7002.ko v4l2-common.ko 
        hexium_gemini.ko hexium_orion.ko tw9910.ko 
        tvp5150.ko mt9m111.ko timblogiw.ko 
        vp27smpx.ko adv7170.ko ov772x.ko 
        ov7670.ko saa7127.ko m52790.ko 
        ov9640.ko mt9v022.ko via-camera.ko 
        videobuf-vmalloc.ko videobuf2-core.ko v4l2-int-device.ko 
        c-qcam.ko tveeprom.ko mt9v032.ko 
        cs5345.ko saa717x.ko videobuf2-dma-sg.ko 
        videobuf2-vmalloc.ko tlv320aic23b.ko bw-qcam.ko 
        mt9t112.ko 
    video/cx23885/: altera-ci.ko cx23885.ko 
    radio/wl128x/: fm_drv.ko 
    dvb/siano/: smssdio.ko smsdvb.ko smsusb.ko 
        smsmdtv.ko 
    video/cx231xx/: cx231xx.ko cx231xx-dvb.ko cx231xx-alsa.ko 
    video/saa7134/: saa6752hs.ko saa7134-empress.ko saa7134-alsa.ko 
        saa7134-dvb.ko saa7134.ko 
    dvb/ttpci/: dvb-ttpci.ko budget-patch.ko ttpci-eeprom.ko 
        budget-av.ko budget.ko budget-core.ko 
        budget-ci.ko 
    radio/si470x/: radio-usb-si470x.ko 
    dvb/frontends/: nxt6000.ko dib7000m.ko dib0090.ko 
        s5h1411.ko drxd.ko dib9000.ko 
        tda665x.ko dib8000.ko tda10071.ko 
        nxt200x.ko stv0367.ko s921.ko 
        lnbp22.ko s5h1409.ko atbm8830.ko 
        cxd2820r.ko dib3000mb.ko ec100.ko 
        lgs8gl5.ko dib3000mc.ko a8293.ko 
        stv0900.ko sp8870.ko tda8083.ko 
        stv0297.ko tda10086.ko zl10353.ko 
        mb86a16.ko lgs8gxx.ko stv0299.ko 
        dvb-pll.ko cx22702.ko tda8261.ko 
        tua6100.ko bcm3510.ko it913x-fe.ko 
        or51211.ko stb0899.ko cx24113.ko 
        tda826x.ko mb86a20s.ko af9013.ko 
        drxk.ko ix2505v.ko au8522.ko 
        si21xx.ko s5h1420.ko stv090x.ko 
        stv0288.ko mt352.ko zl10039.ko 
        isl6405.ko sp887x.ko dibx000_common.ko 
        isl6421.ko mt312.ko or51132.ko 
        tda1004x.ko tda18271c2dd.ko stv6110.ko 
        itd1000.ko stv6110x.ko zl10036.ko 
        lgdt3305.ko dib7000p.ko l64781.ko 
        ves1x93.ko stb6100.ko ves1820.ko 
        dib0070.ko cx22700.ko cx24110.ko 
        dvb_dummy_fe.ko lgdt330x.ko cx24123.ko 
        lnbp21.ko stb6000.ko isl6423.ko 
        tda10023.ko cx24116.ko tda10021.ko 
        tda10048.ko ds3000.ko s5h1432.ko 
    video/bt8xx/: bttv.ko 
    video/cx88/: cx8802.ko cx8800.ko cx88-blackbird.ko 
        cx88-alsa.ko cx88xx.ko cx88-vp3054-i2c.ko 
        cx88-dvb.ko 
    video/gspca/: gspca_xirlink_cit.ko gspca_stk014.ko gspca_spca501.ko 
        gspca_spca500.ko gspca_mars.ko gspca_spca1528.ko 
        gspca_stv0680.ko gspca_sunplus.ko gspca_vc032x.ko 
        gspca_benq.ko gspca_spca505.ko gspca_sn9c20x.ko 
        gspca_zc3xx.ko gspca_vicam.ko gspca_sq930x.ko 
        gspca_topro.ko gspca_sq905c.ko gspca_sonixb.ko 
        gspca_etoms.ko gspca_pac7302.ko gspca_pac207.ko 
        gspca_konica.ko gspca_ov534_9.ko gspca_spca508.ko 
        gspca_nw80x.ko gspca_sq905.ko gspca_t613.ko 
        gspca_sn9c2028.ko gspca_spca561.ko gspca_ov534.ko 
        gspca_tv8532.ko gspca_jeilinj.ko gspca_spca506.ko 
        gspca_se401.ko gspca_sonixj.ko gspca_main.ko 
        gspca_cpia1.ko gspca_conex.ko gspca_mr97310a.ko 
        gspca_kinect.ko gspca_pac7311.ko gspca_ov519.ko 
        gspca_finepix.ko 
    video/cx25821/: cx25821-alsa.ko cx25821.ko 
    rc/: ati_remote.ko lirc_dev.ko redrat3.ko 
        ir-sony-decoder.ko ene_ir.ko mceusb.ko 
        rc-core.ko streamzap.ko ir-nec-decoder.ko 
        ir-rc5-decoder.ko fintek-cir.ko ir-rc6-decoder.ko 
        rc-loopback.ko ir-jvc-decoder.ko nuvoton-cir.ko 
        ir-rc5-sz-decoder.ko ir-mce_kbd-decoder.ko ir-lirc-codec.ko 
        imon.ko ite-cir.ko winbond-cir.ko 
    video/m5mols/: m5mols.ko 
    common/: saa7146_vv.ko saa7146.ko 
    radio/: dsbr100.ko si4713-i2c.ko tef6862.ko 
        radio-wl1273.ko radio-maxiradio.ko saa7706h.ko 
        radio-tea5764.ko radio-si4713.ko radio-timb.ko 
        radio-mr800.ko 
    video/pvrusb2/: pvrusb2.ko 
    dvb/pt1/: earth-pt1.ko 
    rc/keymaps/: rc-tevii-nec.ko rc-terratec-slim.ko rc-adstech-dvb-t-pci.ko 
        rc-pctv-sedna.ko rc-proteus-2309.ko rc-msi-tvanywhere.ko 
        rc-avermedia-dvbt.ko rc-pixelview.ko rc-avermedia-rm-ks.ko 
        rc-snapstream-firefly.ko rc-dm1105-nec.ko rc-encore-enltv-fm53.ko 
        rc-digittrade.ko rc-imon-mce.ko rc-evga-indtube.ko 
        rc-em-terratec.ko rc-hauppauge.ko rc-gadmei-rm008z.ko 
        rc-avermedia-m733a-rm-k6.ko rc-alink-dtu-m.ko rc-dntv-live-dvb-t.ko 
        rc-anysee.ko rc-kworld-plus-tv-analog.ko rc-behold.ko 
        rc-norwood.ko rc-pinnacle-color.ko rc-cinergy-1400.ko 
        rc-leadtek-y04g0051.ko rc-avertv-303.ko rc-msi-digivox-ii.ko 
        rc-total-media-in-hand.ko rc-trekstor.ko rc-ati-x10.ko 
        rc-cinergy.ko rc-tivo.ko rc-manli.ko 
        rc-eztv.ko rc-lme2510.ko rc-kworld-315u.ko 
        rc-twinhan1027.ko rc-avermedia-a16d.ko rc-medion-x10.ko 
        rc-tt-1500.ko rc-videomate-tv-pvr.ko rc-apac-viewcomp.ko 
        rc-terratec-cinergy-xs.ko rc-nebula.ko rc-msi-tvanywhere-plus.ko 
        rc-msi-digivox-iii.ko rc-npgtech.ko rc-ati-tv-wonder-hd-600.ko 
        rc-videomate-m1f.ko rc-pinnacle-pctv-hd.ko rc-iodata-bctv7e.ko 
        rc-pixelview-002t.ko rc-avermedia.ko rc-budget-ci-old.ko 
        rc-imon-pad.ko rc-digitalnow-tinytwin.ko rc-nec-terratec-cinergy-xs.ko 
        rc-winfast-usbii-deluxe.ko rc-flydvb.ko rc-videomate-s350.ko 
        rc-pv951.ko rc-pixelview-mk12.ko rc-winfast.ko 
        rc-lirc.ko rc-encore-enltv2.ko rc-pixelview-new.ko 
        rc-purpletv.ko rc-fusionhdtv-mce.ko rc-technisat-usb2.ko 
        rc-dib0700-rc5.ko rc-gotview7135.ko rc-kaiomy.ko 
        rc-pinnacle-grey.ko rc-powercolor-real-angel.ko rc-terratec-slim-2.ko 
        rc-avermedia-m135a.ko rc-azurewave-ad-tu700.ko rc-encore-enltv.ko 
        rc-flyvideo.ko rc-tbs-nec.ko rc-dib0700-nec.ko 
        rc-behold-columbus.ko rc-streamzap.ko rc-avermedia-cardbus.ko 
        rc-real-audio-220-32-keys.ko rc-genius-tvgo-a11mce.ko rc-rc6-mce.ko 
        rc-dntv-live-dvbt-pro.ko rc-asus-pc39.ko 
    dvb/ttusb-budget/: dvb-ttusb-budget.ko 
    video/au0828/: au0828.ko 
    dvb/dvb-usb/: dvb-usb-opera.ko dvb-usb-vp7045.ko dvb-usb-technisat-usb2.ko 
        dvb-usb-ttusb2.ko dvb-usb-af9015.ko dvb-usb-az6027.ko 
        dvb-usb-gp8psk.ko dvb-usb-af9005.ko mxl111sf-demod.ko 
        dvb-usb-nova-t-usb2.ko dvb-usb-mxl111sf.ko dvb-usb-cinergyT2.ko 
        dvb-usb-umt-010.ko dvb-usb-anysee.ko dvb-usb-gl861.ko 
        dvb-usb-ec168.ko mxl111sf-tuner.ko dvb-usb-dtv5100.ko 
        dvb-usb-cxusb.ko dvb-usb-af9005-remote.ko dvb-usb-dib0700.ko 
        dvb-usb-a800.ko dvb-usb-lmedm04.ko dvb-usb-dibusb-common.ko 
        dvb-usb-pctv452e.ko dvb-usb-au6610.ko dvb-usb-dibusb-mc.ko 
        dvb-usb.ko dvb-usb-digitv.ko dvb-usb-ce6230.ko 
        dvb-usb-friio.ko dvb-usb-dtt200u.ko dvb-usb-vp702x.ko 
        dvb-usb-dibusb-mb.ko dvb-usb-it913x.ko dvb-usb-dw2102.ko 
        dvb-usb-m920x.ko 
    dvb/ddbridge/: ddbridge.ko 
    video/marvell-ccic/: cafe_ccic.ko 
    video/cx18/: cx18.ko cx18-alsa.ko 
    video/ivtv/: ivtvfb.ko ivtv.ko 
    dvb/mantis/: mantis_core.ko mantis.ko hopper.ko 
    common/tuners/: xc4000.ko tuner-xc2028.ko tda18218.ko 
        mt2060.ko tda9887.ko mt2131.ko 
        mc44s803.ko qt1010.ko max2165.ko 
        mt20xx.ko tda827x.ko tda18271.ko 
        tda18212.ko xc5000.ko mxl5007t.ko 
        tea5761.ko tuner-types.ko tda8290.ko 
        tuner-simple.ko mt2266.ko tea5767.ko 
        mxl5005s.ko 
    dvb/firewire/: firedtv.ko 
    dvb/bt8xx/: dst_ca.ko dvb-bt8xx.ko bt878.ko 
        dst.ko 
    video/cx25840/: cx25840.ko 
    dvb/ttusb-dec/: ttusbdecfe.ko ttusb_dec.ko 
    dvb/ngene/: ngene.ko 
    dvb/dm1105/: dm1105.ko 
    video/gspca/gl860/: gspca_gl860.ko 
    video/et61x251/: et61x251.ko 
    ../linux/drivers/misc/altera-stapl/: altera-stapl.ko 
    video/tm6000/: tm6000-alsa.ko tm6000-dvb.ko tm6000.ko 
    dvb/pluto2/: pluto2.ko 
    video/usbvision/: usbvision.ko 
    video/gspca/stv06xx/: gspca_stv06xx.ko 
    video/em28xx/: em28xx-dvb.ko em28xx-alsa.ko em28xx.ko 
    video/tlg2300/: poseidon.ko 
    video/uvc/: uvcvideo.ko 
    video/pwc/: pwc.ko 
/sbin/depmod -a 3.0.0-12-generic 
make -C firmware install
make[2]: Entering directory `/home/anthony/media_build/v4l/firmware'
Installing firmwares at /lib/firmware: vicam/firmware.fw dabusb/firmware.fw dabusb/bitstream.bin ttusb-budget/dspbootcode.bin cpia2/stv0672_vp4.bin av7110/bootcode.bin dvb-fe-bcm3510-01.fw dvb-fe-or51132-qam.fw dvb-fe-or51132-vsb.fw dvb-fe-or51211.fw dvb-fe-xc5000-1.6.114.fw dvb-ttpci-01.fw-261a dvb-ttpci-01.fw-261b dvb-ttpci-01.fw-261c dvb-ttpci-01.fw-261d dvb-ttpci-01.fw-261f dvb-ttpci-01.fw-2622 dvb-usb-avertv-a800-02.fw dvb-usb-bluebird-01.fw dvb-usb-dib0700-1.20.fw dvb-usb-dibusb-5.0.0.11.fw dvb-usb-dibusb-6.0.0.8.fw dvb-usb-dtt200u-01.fw dvb-usb-terratec-h5-drxk.fw dvb-usb-terratec-h7-az6007.fw dvb-usb-terratec-h7-drxk.fw dvb-usb-umt-010-02.fw dvb-usb-vp702x-01.fw dvb-usb-vp7045-01.fw dvb-usb-wt220u-01.fw dvb-usb-wt220u-02.fw v4l-cx231xx-avcore-01.fw v4l-cx23418-apu.fw v4l-cx23418-cpu.fw v4l-cx23418-dig.fw v4l-cx23885-avcore-01.fw v4l-cx23885-enc.fw v4l-cx25840.fw 
make[2]: Leaving directory `/home/anthony/media_build/v4l/firmware'
make[1]: Leaving directory `/home/anthony/media_build/v4l'
anthony@Media-server:~/media_build$ sudo make unload
make -C /home/anthony/media_build/v4l unload
make[1]: Entering directory `/home/anthony/media_build/v4l'
scripts/rmmod.pl unload
found 496 modules
/sbin/rmmod saa7164
Pulseaudio is running with UUID(s): 1000
/sbin/rmmod v4l2_common
/sbin/rmmod videodev
/sbin/rmmod v4l2_compat_ioctl32
/sbin/rmmod media
/sbin/rmmod dvb_core
/sbin/rmmod tveeprom
make[1]: Leaving directory `/home/anthony/media_build/v4l'
anthony@Media-server:~/media_build$ sudo modprobe saa7164
anthony@Media-server:~/media_build$ 

```I got it to compile by "firedtv=m" to "firedtv=n" in the build_media/v4l/.config
and  commented out the CONFIG_RADIO_TIMBERDALE in the build_media/v4l/Makefile.media file.

as you can see it compiled without errors. I have done all what posts have suggested with no hope in site
I can get my card to work if I put the NXP7164-2010-03-10.1.fw in /lib/firmware, it picks up my card in mythtv-backend, but it doesnt let me get my channels :(

I know this was a long post, sorry Im going to go compile again. Im not giving up this wek any time soon. 

p.s. I know my Hauppauge 2250 is good I stuck it make in win7 and worked like a charm :/

---

### Post by Tasmac on 2011-11-10
Sorry for the second post(i couldn't figure out how to edit)
after another effort at compiling still nada. I replaced NXP7164-2010-03-10.1.fw in /lib/firmware
and sure enough it was there(not like I have seen this before though)

_dmesg|grep saa7164_

```
anthony@Media-server:~$ dmesg|grep saa7164
[   21.213797] saa7164 driver loaded
[   21.213855] saa7164 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.214742] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,insmod option]
[   21.214747] saa7164[0]/0: found at 0000:04:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xf2c00000
[   21.214753] saa7164 0000:04:00.0: setting latency timer to 64
[   21.373259] saa7164_downloadfirmware() no first image
[   21.373271] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[   21.998327] saa7164_downloadfirmware() firmware read 4019072 bytes.
[   21.998330] saa7164_downloadfirmware() firmware loaded.
[   21.998338] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[   21.998344] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   21.998345] saa7164_downloadfirmware() BSLSize = 0x0
[   21.998347] saa7164_downloadfirmware() Reserved = 0x0
[   21.998348] saa7164_downloadfirmware() Version = 0x1661c00
[   28.746108] saa7164_downloadimage() Image downloaded, booting...
[   28.849952] saa7164_downloadimage() Image booted successfully.
[   30.890898] saa7164_downloadimage() Image downloaded, booting...
[   32.760098] saa7164_downloadimage() Image booted successfully.
[   32.804370] saa7164[0]: Hauppauge eeprom: model=88061
[   33.428288] DVB: registering new adapter (saa7164)
[   36.309043] DVB: registering new adapter (saa7164)
[   36.309485] saa7164[0]: registered device video0 [mpeg]
[   36.539970] saa7164[0]: registered device video1 [mpeg]
[   36.751104] saa7164[0]: registered device vbi0 [vbi]
[   36.751159] saa7164[0]: registered device vbi1 [vbi]

```But in mytv capture card settings is as follows:
```
1) Analog V4l
2) MJPEG
3) IVTV MPEG-2 
4) H.264 (HD-PVR)
5) DVBTV  (but this one has samsungS5H1411 QAM\ ) instead of Hauppage like the rest.
     and so on and so forth.ect  ect ect maybe I got some settings wrong, I have no idea.
```If you have any thoughts or can point me to a good post Im all ears.....well eyes

---

### Post by rmjohnson144 on 2011-11-10
> **Tasmac said:**
> But in mytv capture card settings is as follows:
```
1) Analog V4l
2) MJPEG
3) IVTV MPEG-2 
4) H.264 (HD-PVR)
5) DVBTV  (but this one has samsungS5H1411 QAM\ ) instead of Hauppage like the rest.
     and so on and so forth.ect  ect ect maybe I got some settings wrong, I have no idea.
```If you have any thoughts or can point me to a good post Im all ears.....well eyes

I haven't been able to get any video yet on 11.10, but on 11.04 I get tuner scans, but no sound or video.  I finally tried Ubuntu 10.04.3 LTS and it has worked in Kaffeine.  I haven't been able to get MythTV configured properly yet.

I have only gotten the DVBV to work.  The Samsung S5H1411 are the name of the two tuner chips on the PCIe card.  I can barely read them they are so small and are just behind the two little metal covers at the rear outputs.

I don't know if we need new firmware for 11.10/11.04 or maybe drivers.  Or I just don't know enough about linux to get it working.  

I'd keep trying with the DVBTV to see if you can get that working.  I heard only digital is working for now.

Good luck
-=Mark=-

---

### Post by jcoles on 2011-11-12
I'm also working with an HVR-2250 card. Your early results are similar to mine. I was also missing NXP7164-2010-03-10.1.fw, downloaded it from [http://www.steventoth.net/linux/](http://www.steventoth.net/linux/) and copied it into /lib/firmware.

MeTV works, but as I found on another machine with an HVR-1250 card, MythTV and MeTV perform poorly -- halting, stuttering unwatchable video. Their code must be quite inefficient. As with most other multimedia playback, VLC is the best. You can try it like this:

scan /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB -o zap | tee channels.conf
vlc channels.conf

---

### Post by Tasmac on 2011-11-12
> **rmjohnson144 said:**
> I haven't been able to get any video yet on 11.10, but on 11.04 I get tuner scans, but no sound or video.  I finally tried Ubuntu 10.04.3 LTS and it has worked in Kaffeine.  I haven't been able to get MythTV configured properly yet.

I have only gotten the DVBV to work.  The Samsung S5H1411 are the name of the two tuner chips on the PCIe card.  I can barely read them they are so small and are just behind the two little metal covers at the rear outputs.

I don't know if we need new firmware for 11.10/11.04 or maybe drivers.  Or I just don't know enough about linux to get it working.  

I'd keep trying with the DVBTV to see if you can get that working.  I heard only digital is working for now.

Good luck
-=Mark=-
well after 5 days of trying to get ubuntu10.04 64bit server or any other server version to work...nada
I gave up and installed ubuntu10.04 64bit desktop, and as Madden would say _BOOM!_ and it worked:P
I found out when I put gnome desktop on the server temporally and to my surprise, my root password only worked to log me in. myqsl, mythtv, and any other administrative tasks my root password failed:confused:
go figure. I have been trying to get something to work, that was going to fail due to a password.
anywho thanks for the info, maybe later on ill figure how to install mythtv on ubuntu10.04 64bit server later in life
Tasmac:popcorn:

p.s. if you could point me to the forum that discusses the problem of connecting front end to a backed, that would be very cool

---

### Post by eaglesflamenco on 2011-11-12
difficult to get a good one

---

### Post by LowSky on 2011-11-12
Wow... Why do so many people still have an issue getting this card or MythTV working? Does anyone actually read?

I'm sitting here with a working card for about 2 years now. I have used this card with 4 flavors of Linux and for the last 5 months Arch. So to say Myth doesn't work, or that the card can't be installed is hogwash. It works. Learn to read instructions. My instructions are so easy, just copy and paste them into a terminal, or read them while tuning myth. I don't use techno-babble or expect a user to know what I'm talking about. I dumb them down so anyone who knows how to read can use them.

If after that you can't get it to run and you come here and ask for results without an idea of what went wrong don't expect much help. We are volunteers, Not technicians. Saying it doesn't work means nothing to us without knowing what you have done. If you don't know what you did and don't want to, and just want it to work out of the box, please, just step away from the PC for a few, go back install something like Windows 7 and use it's media center with none of the mess you see here. $100 and you get what you wanted. Lets be fair I could easily charge that just to get your PC running in the real world.

Also don't post questions to things outside the topic. If you can't get sound/video/database working in MythTV start a new post.

So now that I have easily insulted a few people. Here's my offer. Send me a PM with your info. I use Google Talk, Skype, and AIM, there is a way we can communicate. I will personally get you through setting up the card from a terminal. Heck with the use of Team Viewer I will do it for you. Need help with MythTV I will do the same. Just please stop posting that this card doesn't work, especially if you can't explain why or post what sources you used. I will do this for free. Yes free. Why you may ask, well the simple answer I have nothing better to do.

---

### Post by rmjohnson144 on 2011-11-12
> **Tasmac said:**
> well after 5 days of trying to get ubuntu10.04 64bit server or any other server version to work...nada
I gave up and installed ubuntu10.04 64bit desktop, and as Madden would say _BOOM!_ and it worked:P
I found out when I put gnome desktop on the server temporally and to my surprise, my root password only worked to log me in. myqsl, mythtv, and any other administrative tasks my root password failed:confused:
go figure. I have been trying to get something to work, that was going to fail due to a password.
anywho thanks for the info, maybe later on ill figure how to install mythtv on ubuntu10.04 64bit server later in life
Tasmac:popcorn:

p.s. if you could point me to the forum that discusses the problem of connecting front end to a backed, that would be very cool

ot sure what ypou mean by connecting backed to frontend.  but here's what I did to get things up and running.

Here's my thread.
[http://ubuntuforums.org/showthread.php?t=1875516](http://ubuntuforums.org/showthread.php?t=1875516)

Here are the link to the guides I used.  Posted by LowSky:
[http://ubuntuforums.org/showpost.php?p=11427057&postcount=2](http://ubuntuforums.org/showpost.php?p=11427057&postcount=2)

one thing I had issues with were IP adresses.

There are two address in backend under "General."  I used localhost for both ipaddresses.

There is one address in frondend under "General."  I used localhost for ipaddress.

Here is a link to the mythtv manual setup on configuring a database.  Maybe it will explain it better than I can as I never had to change it.

[http://www.mythtv.org/wiki/User_Manual:Initial_Installation](http://www.mythtv.org/wiki/User_Manual:Initial_Installation)

or try googleing changing passwords in forums.  just make sure the MySQL password you choose is the one in frontend under general settings.

---

### Post by Tasmac on 2011-11-13
> **LowSky said:**
> just step away from the PC for a few, go back install something like  Windows 7 and use it's media center with none of the mess you see here.  $100 and you get what you wanted. Lets be fair I could easily charge  that just to get your PC running in the real world.

I hate Windows, I have all the flavors of the worthless OS and use none

> **LowSky said:**
> 
Also don't post questions to things outside the topic. If you can't get sound/video/database working in MythTV start a new post.

sorry :( , i thought a small p.s. was ok-
actually my whole post was off topic as I don't run mythbunt. I was trying to get myth-backend to run on a server kernel, but this thread has so much usefull information :P. 
Thank you 

> **LowSky said:**
> 
So now that I have easily insulted a few people. Here's my offer. Send  me a PM with your info. I use Google Talk, Skype, and AIM, there is a  way we can communicate. I will personally get you through setting up the card from a terminal. Heck with the use of Team Viewer I will do it for you. Need help with MythTV I will do the same. Just please stop posting that this card doesn't work, especially if you can't explain why or post what sources you used. I will do this for free. Yes free. Why you may ask, well the simple answer I have nothing better to do.

not insulted, your guide for ubuntu desktop works flawlessly and took very little time to set up. its that complete. again thank you

rmjohnson144, thank you. for the links

---

### Post by rmjohnson144 on 2011-11-14
> **LowSky said:**
> Ok so Here's the Tutorial for using 10.04. 

5. Go to video sources, pick your options, I had to setup an account with SchedulesDirect.org, so that I could get local channel guide information in the USA. Your country may have other options.



Do you know of any others?  SchedulesDirect now charges for their service and I just can't afford any extra expenses.

Is this step even necessary?  I don't need a local channel guide.

-=Mark=-

---

### Post by tgm4883 on 2011-11-14
> **rmjohnson144 said:**
> Do you know of any others?  SchedulesDirect now charges for their service and I just can't afford any extra expenses.

Is this step even necessary?  I don't need a local channel guide.

-=Mark=-

That step is required, although IIRC you can set a dummy source.

---

### Post by Mega_Mike on 2011-12-11
The issue I am having 10.10, 64 bit, is that the firmware downloads, registers the card, but scanning channels with mythtv-backend (ATSC) produces nothing.  Its weird since I can hook up the same antenna feed directly to my TV and get a tons of channels with crystal clear picture.  

Its weird because the card was working fine until a recent update of the 2.6.35 kernel.  :(

> **LowSky said:**
> Wow... Why do so many people still have an issue getting this card or MythTV working? Does anyone actually read?

I'm sitting here with a working card for about 2 years now. I have used this card with 4 flavors of Linux and for the last 5 months Arch. So to say Myth doesn't work, or that the card can't be installed is hogwash. It works. Learn to read instructions. My instructions are so easy, just copy and paste them into a terminal, or read them while tuning myth. I don't use techno-babble or expect a user to know what I'm talking about. I dumb them down so anyone who knows how to read can use them.

If after that you can't get it to run and you come here and ask for results without an idea of what went wrong don't expect much help. We are volunteers, Not technicians. Saying it doesn't work means nothing to us without knowing what you have done. If you don't know what you did and don't want to, and just want it to work out of the box, please, just step away from the PC for a few, go back install something like Windows 7 and use it's media center with none of the mess you see here. $100 and you get what you wanted. Lets be fair I could easily charge that just to get your PC running in the real world.

Also don't post questions to things outside the topic. If you can't get sound/video/database working in MythTV start a new post.

So now that I have easily insulted a few people. Here's my offer. Send me a PM with your info. I use Google Talk, Skype, and AIM, there is a way we can communicate. I will personally get you through setting up the card from a terminal. Heck with the use of Team Viewer I will do it for you. Need help with MythTV I will do the same. Just please stop posting that this card doesn't work, especially if you can't explain why or post what sources you used. I will do this for free. Yes free. Why you may ask, well the simple answer I have nothing better to do.

---

### Post by nickrout on 2011-12-12
> **Mega_Mike said:**
> The issue I am having 10.10, 64 bit, is that the firmware downloads, registers the card, but scanning channels with mythtv-backend (ATSC) produces nothing.  Its weird since I can hook up the same antenna feed directly to my TV and get a tons of channels with crystal clear picture.  

Its weird because the card was working fine until a recent update of the 2.6.35 kernel.  :(

Go back to the kernel that worked.

---

### Post by petatkinson on 2011-12-12
> **LowSky said:**
> Wow... Why do so many people still have an issue getting this card or MythTV working? Does anyone actually read?

I'm sitting here with a working card for about 2 years now. I have used this card with 4 flavors of Linux and for the last 5 months Arch. So to say Myth doesn't work, or that the card can't be installed is hogwash. It works. Learn to read instructions. My instructions are so easy, just copy and paste them into a terminal, or read them while tuning myth. I don't use techno-babble or expect a user to know what I'm talking about. I dumb them down so anyone who knows how to read can use them.

If after that you can't get it to run and you come here and ask for results without an idea of what went wrong don't expect much help. We are volunteers, Not technicians. Saying it doesn't work means nothing to us without knowing what you have done. If you don't know what you did and don't want to, and just want it to work out of the box, please, just step away from the PC for a few, go back install something like Windows 7 and use it's media center with none of the mess you see here. $100 and you get what you wanted. Lets be fair I could easily charge that just to get your PC running in the real world.

Also don't post questions to things outside the topic. If you can't get sound/video/database working in MythTV start a new post.

So now that I have easily insulted a few people. Here's my offer. Send me a PM with your info. I use Google Talk, Skype, and AIM, there is a way we can communicate. I will personally get you through setting up the card from a terminal. Heck with the use of Team Viewer I will do it for you. Need help with MythTV I will do the same. Just please stop posting that this card doesn't work, especially if you can't explain why or post what sources you used. I will do this for free. Yes free. Why you may ask, well the simple answer I have nothing better to do.

Just noticed your instructions for the HVR-2250.I wonder have you any experience with the HVR-4000.Gone through all the obvious under 10.04 LTS with no joy.Convinced its down to dodgy firmware drivers.I installed from Mythbuntu under the option "install in existing Ubuntu Desktop"

---

### Post by nickrout on 2011-12-12
> **petatkinson said:**
> Just noticed your instructions for the HVR-2250.I wonder have you any experience with the HVR-4000.Gone through all the obvious under 10.04 LTS with no joy.Convinced its down to dodgy firmware drivers.I installed from Mythbuntu under the option "install in existing Ubuntu Desktop"

According to the experts, this has been supported in linux since 2.6.28. What does dmesg say?

[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000)

---

### Post by tgrav on 2011-12-12
Hello All. I am running into issues with my Hauppauge 2250. I have followed several people including LowSky's instruction on #10. My problem is that I have everything installed, but when I go to my backend to setup the cards my cards are not showing up no matter what I select. I can select the analog, H.264 or the DVB and nothing will make my card appear. 

When I run a lspci -v i can see that my Hauppauge 2250 (please see below)

02:00.0 Multimedia controller: Philips Semiconductors SAA7164 (rev 81)
	Subsystem: Hauppauge computer works Inc. WinTV HVR-2250
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0400000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
	Capabilities: <access denied>
	Kernel driver in use: saa7164
	Kernel modules: saa7164

Can someone tell me what I am doing wrong or what step I am missing? I am just trying to get this card to work and I am not having any luck. I am running Natty. Not sure what other inf is needed. I just find it strange that my card is not showing up in the backend when trying to configure it.

---

### Post by nickrout on 2011-12-12
What do you mean "make my card appear"?

What is dmesg telling you about the card?

what does ```
find /dev|grep dvb
``` tell you?

---

### Post by tgrav on 2011-12-12
Attached is a screen shot of my backend not seeing my card. When I run the code you gave me nothing happens.Below is what I get.

Last login: Mon Dec 12 19:40:33 2011 from 143.16.1.111
tom@mediasvr:~$ find /dev|grep dvb
tom@mediasvr:~$

---

### Post by LowSky on 2011-12-13
> **tgrav said:**
> Attached is a screen shot of my backend not seeing my card. When I run the code you gave me nothing happens.Below is what I get.

Last login: Mon Dec 12 19:40:33 2011 from 143.16.1.111
tom@mediasvr:~$ find /dev|grep dvb
tom@mediasvr:~$


Grab the firmware.
```
wget -c http://www.robotbeard.com/hvr-2250/HVR-2250_firmware.zip
```

Unzip the files
```
unzip HVR-2250_firmware.zip
```

copy the files to the /lib/firmware folder
```
sudo cp *fw /lib/firmware
```

Now check if the card can be located and what value the system has given it
```
dmesg | grep saa7164
```

on the 3rd or 4th line you should see what you are looking for it will look like this
```
[card=8,autodetected]
```
What this says is my HVR-2250 was detected at card 8, you may (probably will) get a diferent number. If your card says "unknown" choose the last option, usually 8.

Now we need to enter this card number into modprobe.d/options.conf file (I like to use gedit)
```
sudo gedit /etc/modprobe.d/options.conf
```

place this line of code in the file
```
options saa7164 card=x
```
*x = your card's number*

Reboot and check mythtv backend to see if it is listed correctly.

---

### Post by tgrav on 2011-12-13
LowSky and nickrout Thank you!! My backend is now seeing my card. I appreciate your help.

---

### Post by petatkinson on 2011-12-13
> **nickrout said:**
> According to the experts, this has been supported in linux since 2.6.28. What does dmesg say?

[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000)

[ 0.289142] pci 0000:00:0b.0: MEM window: 0xe0000000-0xe3ffffff
[ 0.289145] pci 0000:00:0b.0: PREFETCH window: 0x000000d0000000-0x000000dfffffff
[ 0.289150] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:03
[ 0.289153] pci 0000:00:0c.0: IO window: 0xa000-0xafff
[ 0.289156] pci 0000:00:0c.0: MEM window: disabled
[ 0.289159] pci 0000:00:0c.0: PREFETCH window: disabled
[ 0.289164] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:04
[ 0.289166] pci 0000:00:0d.0: IO window: 0x9000-0x9fff
[ 0.289170] pci 0000:00:0d.0: MEM window: disabled
[ 0.289173] pci 0000:00:0d.0: PREFETCH window: disabled
[ 0.289185] pci 0000:00:0a.0: setting latency timer to 64
[ 0.289192] pci 0000:00:0b.0: setting latency timer to 64
[ 0.289199] pci 0000:00:0c.0: setting latency timer to 64
[ 0.289206] pci 0000:00:0d.0: setting latency timer to 64
[ 0.289210] pci_bus 0000:00: resource 0 io: [0x00-0xffff]
[ 0.289213] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[ 0.289216] pci_bus 0000:01: resource 1 mem: [0xe6000000-0xeaffffff]
[ 0.289218] pci_bus 0000:01: resource 3 io: [0x00-0xffff]
[ 0.289221] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
[ 0.289223] pci_bus 0000:02: resource 0 io: [0xb000-0xbfff]
[ 0.289226] pci_bus 0000:02: resource 1 mem: [0xe0000000-0xe3ffffff]
[ 0.289229] pci_bus 0000:02: resource 2 pref mem [0xd0000000-0xdfffffff]
[ 0.289231] pci_bus 0000:03: resource 0 io: [0xa000-0xafff]
[ 0.289234] pci_bus 0000:04: resource 0 io: [0x9000-0x9fff]
[ 0.289275] NET: Registered protocol family 2
[ 0.289383] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 0.289767] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[ 0.290423] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[ 0.290758] TCP: Hash tables configured (established 131072 bind 65536)
[ 0.290760] TCP reno registered
[ 0.290840] NET: Registered protocol family 1
[ 0.371378] pci 0000:02:00.0: Boot video device
[ 0.371575] cpufreq-nforce2: No nForce2 chipset.
[ 0.371601] Scanning for low memory corruption every 60 seconds
[ 0.371724] audit: initializing netlink socket (disabled)
[ 0.371736] type=2000 audit(1323777311.371:1): initialized
[ 0.374107] Freeing initrd memory: 7765k freed
[ 0.382313] highmem bounce pool size: 64 pages
[ 0.382319] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[ 0.383780] VFS: Disk quotas dquot_6.5.2
[ 0.383838] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 0.384421] fuse init (API version 7.13)
[ 0.384507] msgmni has been set to 1636
[ 0.384732] alg: No test for stdrng (krng)
[ 0.384783] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[ 0.384787] io scheduler noop registered
[ 0.384788] io scheduler anticipatory registered
[ 0.384790] io scheduler deadline registered
[ 0.384831] io scheduler cfq registered (default)
[ 0.384994] alloc irq_desc for 24 on node -1
[ 0.384996] alloc kstat_irqs on node -1
[ 0.385005] pcieport 0000:00:0b.0: irq 24 for MSI/MSI-X
[ 0.385012] pcieport 0000:00:0b.0: setting latency timer to 64
[ 0.385102] alloc irq_desc for 25 on node -1
[ 0.385104] alloc kstat_irqs on node -1
[ 0.385109] pcieport 0000:00:0c.0: irq 25 for MSI/MSI-X
[ 0.385115] pcieport 0000:00:0c.0: setting latency timer to 64
[ 0.385202] alloc irq_desc for 26 on node -1
[ 0.385204] alloc kstat_irqs on node -1
[ 0.385210] pcieport 0000:00:0d.0: irq 26 for MSI/MSI-X
[ 0.385215] pcieport 0000:00:0d.0: setting latency timer to 64
[ 0.385277] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 0.385301] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[ 0.385404] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[ 0.385408] ACPI: Power Button [PWRB]
[ 0.385474] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[ 0.385476] ACPI: Power Button [PWRF]
[ 0.385864] processor LNXCPU:00: registered as cooling_device0
[ 0.385903] processor LNXCPU:01: registered as cooling_device1
[ 0.389373] isapnp: Scanning for PnP cards...
[ 0.390744] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[ 0.390842] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 0.391236] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 0.392333] brd: module loaded
[ 0.392794] loop: module loaded
[ 0.392874] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[ 0.393067] pata_acpi 0000:00:08.0: setting latency timer to 64
[ 0.393370] Fixed MDIO Bus: probed
[ 0.393404] PPP generic driver version 2.4.2
[ 0.393436] tun: Universal TUN/TAP device driver, 1.6
[ 0.393438] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[ 0.393526] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[ 0.393799] ACPI: PCI Interrupt Link [AUB2] enabled at IRQ 23
[ 0.393804] alloc irq_desc for 23 on node -1
[ 0.393806] alloc kstat_irqs on node -1
[ 0.393811] ehci_hcd 0000:00:04.1: PCI INT B -> Link[AUB2] -> GSI 23 (level, low) -> IRQ 23
[ 0.393820] ehci_hcd 0000:00:04.1: setting latency timer to 64
[ 0.393823] ehci_hcd 0000:00:04.1: EHCI Host Controller
[ 0.393854] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
[ 0.393881] ehci_hcd 0000:00:04.1: debug port 1
[ 0.393889] ehci_hcd 0000:00:04.1: cache line size of 32 is not supported
[ 0.393903] ehci_hcd 0000:00:04.1: irq 23, io mem 0xeb006000
[ 0.403342] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[ 0.403422] usb usb1: configuration #1 chosen from 1 choice
[ 0.403450] hub 1-0:1.0: USB hub found
[ 0.403457] hub 1-0:1.0: 10 ports detected
[ 0.403515] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[ 0.403776] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 22
[ 0.403779] alloc irq_desc for 22 on node -1
[ 0.403781] alloc kstat_irqs on node -1
[ 0.403786] ohci_hcd 0000:00:04.0: PCI INT A -> Link[AUBA] -> GSI 22 (level, low) -> IRQ 22
[ 0.403794] ohci_hcd 0000:00:04.0: setting latency timer to 64
[ 0.403797] ohci_hcd 0000:00:04.0: OHCI Host Controller
[ 0.403827] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 2
[ 0.403847] ohci_hcd 0000:00:04.0: irq 22, io mem 0xeb007000
[ 0.461389] usb usb2: configuration #1 chosen from 1 choice
[ 0.461414] hub 2-0:1.0: USB hub found
[ 0.461422] hub 2-0:1.0: 10 ports detected
[ 0.461475] uhci_hcd: USB Universal Host Controller Interface driver
[ 0.461550] PNP: PS/2 Controller [PNP0303S2K,PNP0f13S2M] at 0x60,0x64 irq 1,12
[ 0.462018] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 0.462025] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 0.462089] mice: PS/2 mouse device common for all mice
[ 0.462200] rtc_cmos 00:05: RTC can wake from S4
[ 0.462234] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[ 0.462267] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[ 0.462358] device-mapper: uevent: version 1.0.3
[ 0.462446] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[ 0.462505] device-mapper: multipath: version 1.1.0 loaded
[ 0.462508] device-mapper: multipath round-robin: version 1.0.0 loaded
[ 0.462608] EISA: Probing bus 0 at eisa.0
[ 0.462613] Cannot allocate resource for EISA slot 1
[ 0.462635] EISA: Detected 0 cards.
[ 0.462699] cpuidle: using governor ladder
[ 0.462701] cpuidle: using governor menu
[ 0.463112] TCP cubic registered
[ 0.463264] NET: Registered protocol family 10
[ 0.464068] NET: Registered protocol family 17
[ 0.464107] Using IPI No-Shortcut mode
[ 0.464168] PM: Resume from disk failed.
[ 0.464179] registered taskstats version 1
[ 0.464559] Magic number: 7:71:934
[ 0.464620] rtc_cmos 00:05: setting system clock to 2011-12-13 11:55:11 UTC (1323777311)
[ 0.464623] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 0.464625] EDD information not available.
[ 0.485090] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[ 0.742216] isapnp: No Plug & Play device found
[ 0.742235] Freeing unused kernel memory: 684k freed
[ 0.742739] Write protecting the kernel text: 4836k
[ 0.742817] Write protecting the kernel read-only data: 1884k
[ 0.758640] udev: starting version 151
[ 0.767367] usb 1-1: new high speed USB device using ehci_hcd and address 2
[ 0.842508] pata_amd 0000:00:08.0: version 0.4.1
[ 0.842559] pata_amd 0000:00:08.0: setting latency timer to 64
[ 0.863250] scsi0 : pata_amd
[ 0.865159] Floppy drive(s): fd0 is 1.44M
[ 0.867087] scsi1 : pata_amd
[ 0.867805] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[ 0.867808] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[ 0.867972] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[ 0.868240] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[ 0.868244] alloc irq_desc for 21 on node -1
[ 0.868247] alloc kstat_irqs on node -1
[ 0.868254] forcedeth 0000:00:0f.0: PCI INT A -> Link[APCH] -> GSI 21 (level, low) -> IRQ 21
[ 0.868259] forcedeth 0000:00:0f.0: setting latency timer to 64
[ 0.883222] FDC 0 is a post-1991 82077
[ 1.012314] usb 1-1: configuration #1 chosen from 1 choice
[ 1.019366] Initializing USB Mass Storage driver...
[ 1.019439] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1.019518] usbcore: registered new interface driver usb-storage
[ 1.019521] USB Mass Storage support registered.
[ 1.019526] usb-storage: device found at 2
[ 1.019527] usb-storage: waiting for device to settle before scanning
[ 1.148277] ata1.00: HPA unlocked: 976771055 -> 976773168, native 976773168
[ 1.148282] ata1.00: ATA-8: WDC WD5000AAKB-00H8A0, 05.04E05, max UDMA/133
[ 1.148285] ata1.00: 976773168 sectors, multi 16: LBA48 
[ 1.148321] ata1.01: ATAPI: JLMS XJ-HD166S, DS18, max UDMA/33
[ 1.148347] ata1: nv_mode_filter: 0x7f39f&0x7f39f->0x7f39f, BIOS=0x7f000 (0xc7c00000) ACPI=0x7f01f (15:60:0x1f)
[ 1.148351] ata1: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc7c00000) ACPI=0x701f (15:60:0x1f)
[ 1.164927] ata1.00: configured for UDMA/133
[ 1.165367] ata1.01: configured for UDMA/33
[ 1.165659] scsi 0:0:0:0: Direct-Access ATA WDC WD5000AAKB-0 05.0 PQ: 0 ANSI: 5
[ 1.165789] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 1.166089] scsi 0:0:1:0: CD-ROM JLMS XJ-HD166S DS18 PQ: 0 ANSI: 5
[ 1.166271] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[ 1.167614] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[ 1.167618] Uniform CD-ROM driver Revision: 3.20
[ 1.167629] sd 0:0:0:0: [sda] Write Protect is off
[ 1.167633] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1.167666] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1.167726] sr 0:0:1:0: Attached scsi CD-ROM sr0
[ 1.167770] sr 0:0:1:0: Attached scsi generic sg1 type 5
[ 1.167796] sda:
[ 1.167879] ata2: port disabled. ignoring.
[ 1.177551] sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 >
[ 1.245837] sd 0:0:0:0: [sda] Attached SCSI disk
[ 1.248965] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[ 1.248970] alloc irq_desc for 18 on node -1
[ 1.248972] alloc kstat_irqs on node -1
[ 1.248977] ohci1394 0000:01:07.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[ 1.304546] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18] MMIO=[ea004000-ea0047ff] Max Packet=[2048] IR/IT contexts=[4/8]
[ 1.377224] forcedeth 0000:00:0f.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1f:d0:91:2a:00
[ 1.377228] forcedeth 0000:00:0f.0: highdma pwrctl mgmt gbit lnktim msi desc-v3
[ 1.377248] ahci 0000:00:0e.0: version 3.0
[ 1.377562] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[ 1.377567] alloc irq_desc for 20 on node -1
[ 1.377569] alloc kstat_irqs on node -1
[ 1.377576] ahci 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 20 (level, low) -> IRQ 20
[ 1.377620] alloc irq_desc for 27 on node -1
[ 1.377622] alloc kstat_irqs on node -1
[ 1.377629] ahci 0000:00:0e.0: irq 27 for MSI/MSI-X
[ 1.377635] ahci 0000:00:0e.0: controller can do NCQ, turning on CAP_NCQ
[ 1.377697] ahci 0000:00:0e.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[ 1.377700] ahci 0000:00:0e.0: flags: 64bit ncq sntf led clo pmp pio 
[ 1.377704] ahci 0000:00:0e.0: setting latency timer to 64
[ 1.378149] scsi3 : ahci
[ 1.378226] scsi4 : ahci
[ 1.378287] scsi5 : ahci
[ 1.378344] scsi6 : ahci
[ 1.378474] ata3: SATA max UDMA/133 abar m8192@0xeb004000 port 0xeb004100 irq 27
[ 1.378478] ata4: SATA max UDMA/133 abar m8192@0xeb004000 port 0xeb004180 irq 27
[ 1.378480] ata5: SATA max UDMA/133 abar m8192@0xeb004000 port 0xeb004200 irq 27
[ 1.378483] ata6: SATA max UDMA/133 abar m8192@0xeb004000 port 0xeb004280 irq 27
[ 1.584014] usb 2-2: new low speed USB device using ohci_hcd and address 2
[ 1.696023] ata4: SATA link down (SStatus 0 SControl 300)
[ 1.696513] ata5: SATA link down (SStatus 0 SControl 300)
[ 1.696528] ata6: SATA link down (SStatus 0 SControl 300)
[ 1.719321] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[ 1.719326] EXT4-fs (sda6): write access will be enabled during recovery
[ 1.797296] usb 2-2: configuration #1 chosen from 1 choice
[ 1.810531] usbcore: registered new interface driver hiddev
[ 1.816426] input: iPazzPort iPazzPort as /devices/pci0000:00/0000:00:04.0/usb2/2-2/2-2:1.0/input/input4
[ 1.816492] generic-usb 0003:0168:1998.0001: input,hidraw0: USB HID v1.11 Keyboard [iPazzPort iPazzPort] on usb-0000:00:04.0-2/input0
[ 1.824519] input: iPazzPort iPazzPort as /devices/pci0000:00/0000:00:04.0/usb2/2-2/2-2:1.1/input/input5
[ 1.824595] generic-usb 0003:0168:1998.0002: input,hidraw1: USB HID v1.11 Mouse [iPazzPort iPazzPort] on usb-0000:00:04.0-2/input1
[ 1.824615] usbcore: registered new interface driver usbhid
[ 1.824617] usbhid: v2.6:USB HID core driver
[ 1.832216] EXT4-fs (sda6): orphan cleanup on readonly fs
[ 1.832224] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 655370
[ 1.832251] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 655369
[ 1.832261] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 655368
[ 1.832269] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 655367
[ 1.832278] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 655366
[ 1.832285] EXT4-fs (sda6): 5 orphan inodes deleted
[ 1.832288] EXT4-fs (sda6): recovery complete
[ 1.860013] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 1.861026] ata3.00: ATA-8: ST3500418AS, CC37, max UDMA/133
[ 1.861030] ata3.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[ 1.862254] ata3.00: configured for UDMA/133
[ 1.862358] scsi 3:0:0:0: Direct-Access ATA ST3500418AS CC37 PQ: 0 ANSI: 5
[ 1.862488] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 1.862571] sd 3:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[ 1.862627] sd 3:0:0:0: [sdb] Write Protect is off
[ 1.862630] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[ 1.862658] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1.862804] sdb: sdb1 sdb2
[ 1.878626] sd 3:0:0:0: [sdb] Attached SCSI disk
[ 1.965350] EXT4-fs (sda6): mounted filesystem with ordered data mode
[ 2.092529] usb 2-7: new full speed USB device using ohci_hcd and address 3
[ 2.305237] usb 2-7: configuration #1 chosen from 1 choice
[ 2.314438] input: BTC USB Multimedia Cordless Keyboard as /devices/pci0000:00/0000:00:04.0/usb2/2-7/2-7:1.0/input/input6
[ 2.314497] generic-usb 0003:046E:5577.0003: input,hidraw2: USB HID v1.11 Keyboard [BTC USB Multimedia Cordless Keyboard] on usb-0000:00:04.0-7/input0
[ 2.321603] input: BTC USB Multimedia Cordless Keyboard as /devices/pci0000:00/0000:00:04.0/usb2/2-7/2-7:1.1/input/input7
[ 2.321719] generic-usb 0003:046E:5577.0004: input,hiddev96,hidraw3: USB HID v1.11 Mouse [BTC USB Multimedia Cordless Keyboard] on usb-0000:00:04.0-7/input1
[ 2.576123] ieee1394: Host added: ID:BUS[0-00:1023] GUID[007795a100001fd0]
[ 2.624520] usb 2-8: new full speed USB device using ohci_hcd and address 4
[ 2.846177] usb 2-8: configuration #1 chosen from 1 choice
[ 2.849114] hub 2-8:1.0: USB hub found
[ 2.852089] hub 2-8:1.0: 3 ports detected
[ 2.878113] udev: starting version 151
[ 2.902991] Adding 10740728k swap on /dev/sda7. Priority:-1 extents:1 across:10740728k 
[ 3.153054] usb 2-8.2: new full speed USB device using ohci_hcd and address 5
[ 3.277149] usb 2-8.2: configuration #1 chosen from 1 choice
[ 3.293310] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:04.0/usb2/2-8/2-8.2/2-8.2:1.0/input/input8
[ 3.293384] generic-usb 0003:046D:C71E.0005: input,hidraw4: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:04.0-8.2/input0
[ 3.374032] usb 2-8.3: new full speed USB device using ohci_hcd and address 6
[ 3.498247] usb 2-8.3: configuration #1 chosen from 1 choice
[ 3.692767] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[ 3.692789] i2c i2c-1: nForce2 SMBus adapter at 0x1c80
[ 3.708076] vga16fb: initializing
[ 3.708080] vga16fb: mapped to 0xc00a0000
[ 3.708237] fb0: VGA16 VGA frame buffer device
[ 3.778181] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:04.0/usb2/2-8/2-8.3/2-8.3:1.0/input/input9
[ 3.779342] logitech 0003:046D:C71F.0006: input,hiddev97,hidraw5: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:04.0-8.3/input0
[ 3.950748] psmouse serio1: ID: 10 00 64
[ 3.955944] Console: switching to colour frame buffer device 80x30
[ 4.010131] parport_pc 00:0a: reported by Plug and Play ACPI
[ 4.010178] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[ 4.046813] ppdev: user-space parallel port driver
[ 4.053299] Linux agpgart interface v0.103
[ 4.065135] Linux video capture interface: v2.00
[ 4.126061] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input10
[ 4.286490] nvidia: module license 'NVIDIA' taints kernel.
[ 4.286494] Disabling lock debugging due to kernel taint
[ 4.449075] type=1505 audit(1323777315.483:2): operation="profile_load" pid=537 name="/sbin/dhclient3"
[ 4.449786] type=1505 audit(1323777315.483:3): operation="profile_load" pid=537 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[ 4.450180] type=1505 audit(1323777315.483:4): operation="profile_load" pid=537 name="/usr/lib/connman/scripts/dhclient-script"
[ 4.450710] type=1505 audit(1323777315.483:5): operation="profile_replace" pid=532 name="/sbin/dhclient3"
[ 4.451428] type=1505 audit(1323777315.483:6): operation="profile_replace" pid=532 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[ 4.451821] type=1505 audit(1323777315.483:7): operation="profile_replace" pid=532 name="/usr/lib/connman/scripts/dhclient-script"
[ 5.122426] lp0: using parport0 (interrupt-driven).
[ 5.355325] ACPI: PCI Interrupt Link [APC6] enabled at IRQ 16
[ 5.355330] alloc irq_desc for 16 on node -1
[ 5.355332] alloc kstat_irqs on node -1
[ 5.355339] nvidia 0000:02:00.0: PCI INT A -> Link[APC6] -> GSI 16 (level, low) -> IRQ 16
[ 5.355347] nvidia 0000:02:00.0: setting latency timer to 64
[ 5.355351] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=nonew ns=io+mem
[ 5.355558] NVRM: loading NVIDIA UNIX x86 Kernel Module 195.36.24 Thu Apr 22 09:18:20 PDT 2010
[ 5.485855] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
[ 5.486225] cx88[0]: subsystem: 0070:6902, board: Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid [card=68,autodetected], frontend(s): 2
[ 5.486228] cx88[0]: TV tuner type 63, Radio tuner type -1
[ 5.489057] cx2388x alsa driver version 0.0.7 loaded
[ 5.489815] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[ 5.606585] cx88[0]: i2c init: enabling analog demod on HVR1300/3000/4000 tuner
[ 5.618478] type=1505 audit(1323777316.651:: operation="profile_load" pid=763 name="/usr/sbin/ntpd"
[ 5.618487] type=1505 audit(1323777316.651:9): operation="profile_replace" pid=762 name="/usr/sbin/ntpd"
[ 5.684571] HDA Intel 0000:00:09.0: power state changed by ACPI to D0
[ 5.684605] HDA Intel 0000:00:09.0: power state changed by ACPI to D0
[ 5.684870] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[ 5.684875] HDA Intel 0000:00:09.0: PCI INT A -> Link[AAZA] -> GSI 23 (level, low) -> IRQ 23
[ 5.684878] hda_intel: Disable MSI for Nvidia chipset
[ 5.684901] HDA Intel 0000:00:09.0: setting latency timer to 64
[ 5.743170] tuner 2-0043: chip found @ 0x86 (cx88[0])
[ 5.755051] tda9887 2-0043: creating new instance
[ 5.755054] tda9887 2-0043: tda988[5/6/7] found
[ 5.758048] tuner 2-0061: chip found @ 0xc2 (cx88[0])
[ 5.796118] tveeprom 2-0050: Hauppauge model 69009, rev B2D3, serial# 5375849
[ 5.796122] tveeprom 2-0050: MAC address is 00-0D-FE-52-07-69
[ 5.796125] tveeprom 2-0050: tuner model is Philips FMD1216MEX (idx 133, type 7
[ 5.796128] tveeprom 2-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[ 5.796131] tveeprom 2-0050: audio processor is CX882 (idx 33)
[ 5.796133] tveeprom 2-0050: decoder processor is CX882 (idx 25)
[ 5.796136] tveeprom 2-0050: has radio, has IR receiver, has no IR transmitter
[ 5.796138] cx88[0]: hauppauge eeprom: model=69009
[ 5.821354] tuner-simple 2-0061: creating new instance
[ 5.821357] tuner-simple 2-0061: type set to 78 (Philips FMD1216MEX MK3 Hybrid Tuner)
[ 5.825395] input: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:0a.0/0000:01:06.2/input/input11
[ 5.825451] cx88[0]/2: cx2388x 8802 Driver Manager
[ 5.825745] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[ 5.825749] alloc irq_desc for 17 on node -1
[ 5.825752] alloc kstat_irqs on node -1
[ 5.825758] cx88-mpeg driver manager 0000:01:06.2: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[ 5.825766] cx88[0]/2: found at 0000:01:06.2, rev: 5, irq: 17, latency: 32, mmio: 0xe8000000
[ 5.825771] IRQ 17/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[ 5.825832] cx88_audio 0000:01:06.1: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[ 5.825842] IRQ 17/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[ 5.825861] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[ 5.826254] cx8800 0000:01:06.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[ 5.826261] cx88[0]/0: found at 0000:01:06.0, rev: 5, irq: 17, latency: 32, mmio: 0xe6000000
[ 5.826269] IRQ 17/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[ 5.849750] wm8775 2-001b: chip found @ 0x36 (cx88[0])
[ 5.856308] cx88[0]/0: registered device video0 [v4l2]
[ 5.856398] cx88[0]/0: registered device vbi0
[ 5.856485] cx88[0]/0: registered device radio0
[ 5.915271] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[ 5.915274] cx88/2: registering cx8802 driver, type: dvb access: shared
[ 5.915277] cx88[0]/2: subsystem: 0070:6902, board: Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid [card=68]
[ 5.915280] cx88[0]/2: cx2388x based DVB/ATSC card
[ 5.915282] cx8802_alloc_frontends() allocating 2 frontend(s)
[ 5.983792] tuner-simple 2-0061: attaching existing instance
[ 5.983796] tuner-simple 2-0061: couldn't set type to 63. Using 78 (Philips FMD1216MEX MK3 Hybrid Tuner) instead
[ 5.986433] DVB: registering new adapter (cx88[0])
[ 5.986437] DVB: registering adapter 0 frontend 0 (Conexant CX24116/CX2411...
[ 5.989414] DVB: registering adapter 0 frontend 1 (Conexant CX22702 DVB-T)...
[ 6.008204] usb-storage: device scan complete
[ 6.043580] scsi 2:0:0:0: Direct-Access ST310005 28AS CC44 PQ: 0 ANSI: 0
[ 6.044208] sd 2:0:0:0: Attached scsi generic sg3 type 0
[ 6.046560] sd 2:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[ 6.048430] sd 2:0:0:0: [sdc] Write Protect is off
[ 6.048433] sd 2:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 6.048436] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[ 6.051431] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[ 6.051435] sdc: sdc1 sdc2 sdc3 sdc4
[ 6.098428] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[ 6.098433] sd 2:0:0:0: [sdc] Attached SCSI disk
[ 6.404933] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:09.0/input/input12
[ 6.511378] EXT4-fs (sda5): mounted filesystem with ordered data mode
[ 7.552843] EXT4-fs (sda: mounted filesystem with ordered data mode
[ 7.582150] EXT4-fs (sda9): mounted filesystem with ordered data mode
[ 8.199718] EXT4-fs (sda10): mounted filesystem with ordered data mode
[ 11.269404] type=1505 audit(1323777322.303:10): operation="profile_replace" pid=1076 name="/sbin/dhclient3"
[ 11.270129] type=1505 audit(1323777322.303:11): operation="profile_replace" pid=1076 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[ 11.270527] type=1505 audit(1323777322.303:12): operation="profile_replace" pid=1076 name="/usr/lib/connman/scripts/dhclient-script"
[ 11.299178] type=1505 audit(1323777322.331:13): operation="profile_load" pid=1075 name="/usr/share/gdm/guest-session/Xsession"
[ 11.505271] type=1505 audit(1323777322.539:14): operation="profile_load" pid=1079 name="/usr/lib/cups/backend/cups-pdf"
[ 11.506124] type=1505 audit(1323777322.539:15): operation="profile_load" pid=1079 name="/usr/sbin/cupsd"
[ 11.562022] alloc irq_desc for 28 on node -1
[ 11.562025] alloc kstat_irqs on node -1
[ 11.562034] forcedeth 0000:00:0f.0: irq 28 for MSI/MSI-X
[ 11.712851] type=1505 audit(1323777322.747:16): operation="profile_load" pid=1077 name="/usr/bin/evince"
[ 11.722074] type=1505 audit(1323777322.755:17): operation="profile_load" pid=1077 name="/usr/bin/evince-previewer"
[ 11.727648] type=1505 audit(1323777322.759:1: operation="profile_load" pid=1077 name="/usr/bin/evince-thumbnailer"
[ 11.735117] type=1505 audit(1323777322.767:19): operation="profile_replace" pid=1149 name="/usr/sbin/ntpd"
[ 17.849243] __ratelimit: 6 callbacks suppressed
[ 17.849246] type=1505 audit(1323777328.883:22): operation="profile_replace" pid=1289 name="/usr/sbin/mysqld"
[ 18.341850] type=1503 audit(1323777329.375:23): operation="capable" pid=1284 parent=1 profile="/usr/sbin/ntpd" name="dac_override"
[ 22.448006] eth0: no IPv6 routers present
[ 23.284884] CPU0 attaching NULL sched-domain.
[ 23.284890] CPU1 attaching NULL sched-domain.
[ 23.308080] CPU0 attaching sched-domain:
[ 23.308084] domain 0: span 0-1 level MC
[ 23.308087] groups: 0 1
[ 23.308092] CPU1 attaching sched-domain:
[ 23.308094] domain 0: span 0-1 level MC
[ 23.308097] groups: 1 0
[ 27.104108] CPU0 attaching NULL sched-domain.
[ 27.104113] CPU1 attaching NULL sched-domain.
[ 27.136072] CPU0 attaching sched-domain:
[ 27.136076] domain 0: span 0-1 level MC
[ 27.136078] groups: 0 1
[ 27.136083] CPU1 attaching sched-domain:
[ 27.136085] domain 0: span 0-1 level MC
[ 27.136088] groups: 1 0
[ 32.731351] kjournald starting. Commit interval 5 seconds
[ 32.731361] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[ 32.732187] EXT3 FS on sdc2, internal journal
[ 32.732190] EXT3-fs: recovery complete.
[ 32.732193] EXT3-fs: mounted filesystem with ordered data mode.
[ 33.239526] kjournald starting. Commit interval 5 seconds
[ 33.239529] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[ 33.239918] EXT3 FS on sdc1, internal journal
[ 33.239921] EXT3-fs: recovery complete.
[ 33.239924] EXT3-fs: mounted filesystem with ordered data mode.
peter@DownStairs:~$

The is the output of dmesg

---

### Post by nickrout on 2011-12-13
Well the card is clearly recognised isn't it? I actually suggest a new thread as this thread is long enough and is about the 2250, not the 4000.

---

### Post by nickrout on 2011-12-13
> **tgrav said:**
> LowSky and nickrout Thank you!! My backend is now seeing my card. I appreciate your help.

LowSky did it all:

LowSky, how about posting a bug asking those firmware files to be incorporated into linux-firmware-nonfree?

---

### Post by LowSky on 2011-12-17
> **nickrout said:**
> LowSky did it all:

LowSky, how about posting a bug asking those firmware files to be incorporated into linux-firmware-nonfree?

its already a listed bug, please feel free to add your comments to it.

[https://bugs.launchpad.net/ubuntu/+source/linux-firmware-nonfree/+bug/579783](https://bugs.launchpad.net/ubuntu/+source/linux-firmware-nonfree/+bug/579783)


In the mean time I'm looking to turn the instructions into a simple script, or even spin it into a deb package if my skills can increase +40 (sorry bad elder scrolls joke).

---

### Post by dr_nailz on 2011-12-22
Also having problems with Hauppauge WinTV-HVR2200 on Mythbuntu 11.10, kernel 3.0.0-15-generic (x86_64), tried both firmware-only and with drivers from git://linuxtv.org/media_build.git.  The module seems to load and the dev entries are created, but nothing tunes.

If I let modprobe detect the card id it says:
```
[ 2794.678934] CORE saa7164[0]: subsystem: 0070:8940, board: Hauppauge WinTV-HVR2200 [card=9,autodetected]
```

I previously had this working with Mythbuntu 11.04 using card=4.  I've tried all the card ids.  4 and 9 give me the frontend dev entries but neither tune.  The others give various errors.  I guess I'll try downgrading the kernel next.

lspci -vv:
```

        0b:00.0 Multimedia controller: Philips Semiconductors SAA7164 (rev 81)
	Subsystem: Hauppauge computer works Inc. WinTV HVR-2200 (submodel 89619)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at fbc00000 (64-bit, non-prefetchable) [size=4M]
	Region 2: Memory at fb800000 (64-bit, non-prefetchable) [size=4M]
	Capabilities: <access denied>
	Kernel driver in use: saa7164
	Kernel modules: saa7164
```

---

### Post by BigPacks on 2011-12-29
> **LowSky said:**
> Hello Mythbuntu users.

It pains me to tell you all but I have moved on to Arch Linux. I might be back if Arch doesn't annoy me. And oh it has! In the mean time it delights me to tell you that the 3.0 Kernel shipped with Arch seems to work pretty well with the HVR-2250. My only issue was learning my way around Modules.

I want to give credit to Sketchy's post: [#420]("http://ubuntuforums.org/showpost.php?p=10980475&postcount=420") I'm pretty sure this works

No one should need to upload any kernel drivers using 11.04+, only the firmware is needed.

I created a link on my server to host all of the firmware versions made a while back and will host as long as possible. I may move them to a public dropbox location later. I will update if needed.


Grab the firmware.
```
wget -c http://www.robotbeard.com/hvr-2250/HVR-2250_firmware.zip
```

Unzip the files
```
unzip HVR-2250_firmware.zip
```

copy the files to the /lib/firmware folder
```
sudo cp *fw /lib/firmware
```

Now check if the card can be located and what value the system has given it
```
dmesg | grep saa7164
```

on the 3rd or 4th line you should see what you are looking for it will look like this
```
[card=8,autodetected]
```
What this says is my HVR-2250 was detected at card 8, you may (probably will) get a diferent number.

Now we need to enter this card number into modprobe.d/options.conf file (I like to use gedit)
```
sudo gedit /etc/modprobe.d/options.conf
```

place this line of code in the file
```
options saa7164 card=x
```
*x = your card's number*

Reboot and check mythtv backend to see if it is listed correctly.
Lowsky

FYI - I had the HVR2250 working in Mythbuntu 10.04 and I've now got it working  in Mythbuntu 11.10.  But I had to do something slightly different than  your instructions.

Using the **dmesg | grep saa7164** command, my card had [card=0,autodetected].  Creating the options file with **options saa7164 card=0** didn't work, so I checked what I had it set to in Mythbuntu 10.04, which was card=4.

Anyway in summary, these instructions do work for Mythbuntu 11.10.

---

### Post by TheFuzz4 on 2012-01-12
Just a quick question here and if I need to start a new thread please let me know.  I got my card working with Lowsky's how to, so many thanks to you LowSky.  The thing that I'm trying to figure out now is what to do after a channel scan.  
I currently have comcast limited basic (which is all I really want)  I go into scan channels and select cable high qam 256 and tell it to scan.  It scans through just fine.  The only thing that it doesn't do is take 30 mins like my friends did with the same setup.  It reaches about 71% and calls it done after scanning 134 channels at that point and finds a bunch of channels.  The only thing it doesn't do is map them correctly.  Do I need to go through it after the fact and scan through the channels and update the call signs and everything else after the fact?  I saw some posts from people using the scte65scan tool.  I downloaded it but noticed that all of the guides were for using it with a device called a HDHomeRun which I don't have and don't plan on purchasing.  When the scan completes it also doesn't pull the call signs for any of the stations either.  So if this just means that I need to go through after the scan completes and update each channel by hand I'll do it but I am hoping that there might be an easier method.  BTW my backend is just that a backend its running on Ubuntu server 11.10.  Thank you in advance for your help with this.

---

### Post by nickrout on 2012-01-12
doesn't schedules direct do the mapping?

---

### Post by rmjohnson144 on 2012-01-12
> **TheFuzz4 said:**
> Just a quick question here and if I need to start a new thread please let me know.  I got my card working with Lowsky's how to, so many thanks to you LowSky.  The thing that I'm trying to figure out now is what to do after a channel scan.  
I currently have comcast limited basic (which is all I really want)  I go into scan channels and select cable high qam 256 and tell it to scan.  It scans through just fine.  The only thing that it doesn't do is take 30 mins like my friends did with the same setup.  It reaches about 71% and calls it done after scanning 134 channels at that point and finds a bunch of channels.  The only thing it doesn't do is map them correctly.  Do I need to go through it after the fact and scan through the channels and update the call signs and everything else after the fact?  I saw some posts from people using the scte65scan tool.  I downloaded it but noticed that all of the guides were for using it with a device called a HDHomeRun which I don't have and don't plan on purchasing.  When the scan completes it also doesn't pull the call signs for any of the stations either.  So if this just means that I need to go through after the scan completes and update each channel by hand I'll do it but I am hoping that there might be an easier method.  BTW my backend is just that a backend its running on Ubuntu server 11.10.  Thank you in advance for your help with this.

When I ran the scan, I got tons of channels that are scrambled.  You just have to scroll through the list and find any channels to can recognize.  Most of mine were towards the end.  They would usually have the station name and channel number along with the long hdtv number.

I see yours didn't finish, so maybe it didn't reach the end.  Mine took probably a half an hour as well.  How long did yours take?

I can't look this up on my system as I don't have my mythbuntu setup at the moment.  Windows 8 pre-beta wiped all my hard drives when it updated the other day.  I just haven't got around to reinstaling yet.

When I had issues, I had to setup Kaffeine to make sure the card was working properly.  I ended up using mythbuntu 10.04.3 as 11.10 wouldn't work for me.  I see others have had success lately so maybe update fixed things.  But Kaffeine was easy setup and worked great for me to at least let me know my tv card was configured properly and working.

Good luck
-=Mark=-

---

### Post by TheFuzz4 on 2012-01-12
I think that I've got this working now but I am not certain.  I was able to find a better howto for the scte65scan tool [here]("http://www.mythtv.org/wiki/Scte65scan") Just if you don't have a HDHomeRun just ignore any reference to it.  The scantool is actually picking up my locals and mapping them to the right number.  So right now I've got it running generating the sql that I'll use to import it into the mythconverg database.  I'll keep you all posted on how this works.  Thanks.

---

### Post by cheryljosie on 2012-02-18
[http://ubuntuforums.org/showthread.php?t=1567490](http://ubuntuforums.org/showthread.php?t=1567490)

latest information on installing the 2250. posting it here for convenience. It mostly works with 11.10 with some minor issues on the output stream that might interfere with transcoding and viewing outside of mythtv, and another minor issue with the eit (channel scan) on the digital side hanging the backend if the analog is accessed simultaneously. Apparently the mutually exclusive functionality configuration for dig vs analog is not quite working properly when eit is activated, but I posted how to work around it.

---

### Post by km782 on 2012-05-25
Has anyone been able to fix the I2C error problem?  Disabling EIT scanning on one of the tuners seems to lessen how often it happens but I still have to reset my machine about every 3-4 days and end up missing some of my scheduled recordings.

Also, is the driver that is included with Mythbuntu 12.04 the latest version?  I'm not really sure how to tell...

---

### Post by xxrsc on 2012-07-03
I just upgraded to 12.04 and now I get this at the end of dmesg | grep saa

```
saa7164_downloadimage() Image downloaded, booting...
saa7164_dl_wait_clr() timeout (no d/l clr)
```

Haven't seen anybody else having this issue. Now I don't get a /dev/video*. I guess it doesn't like the firmware for some reason.

The kernel version is 3.2.0-26-generic.


Anybody got any ideas how to fix this?

---

### Post by johnlatz on 2012-07-28
This issue has cropped up on me recently.  

First off, I'm on Mythbuntu-Repos, current version:
MythTV Version : v0.25.2-8-g3256849
MythTV Branch : fixes/0.25
Network Protocol : 72
Library API : 0.25.20120506-1
QT Version : 4.8.1

The hardware in question is a Hauppauge-2250 card, DVB input, tuner #2.  I have configured my backend to allow 2 recordings per digital tuner, so I'll refer to tuner 2.1 and tuner 2.2.

My provider (So Cal Time Warner) remapped their digital channels recently, which caused me to have to rescan for new channels.  If I perform a scan using tuner #1, I can find all the new channels with no problem.

If I scan with tuner 2.2, I can find new channels no problem.

If I scan with tuner 2.1 - nothing.

If I attempt to record using tuner 1, no problem.

If I attempt to record on tuner 2.2 (Encoder 20 currently) - MythTV defaults to using tuner 2.1 (Encoder 19).  Thus, I cannot seem to force MythTV to use tuner 2.2 (Encoder 20), the side of that tuner that WAS able to scan for channels.

If I attempt (or am forced to) record on tuner 2.1 (Encoder 19), I get nothing.  Mythweb shows a "B" in the value of filesize under "Recorded Programs".    The Mythweb "Backend Logs" page shows the following:
row  &#8595;             id host application pid tid thread filename line function msgtime level message                      0   732472   Mythbox   mythbackend   7938   8556   SignalMonitor   dvbchannel.cpp   1022   GetSignalStrength   2012-07-28 07:22:05   3   DVBChan(19:/dev/dvb/adapter2/frontend0): Getting Frontend signal strength failed.             eno: Invalid argument (22)repeated numerous (>25) times.

mythbackend.log is a little more thorough:
Jul 28 07:40:13 Mythbox mythbackend[7938]: E SignalMonitor dvbchannel.cpp:1022 (GetSignalStrength) DVBChan(19:/dev/dvb/adapter2/frontend0): Getting Frontend signal strength failed.#012#011#011#011eno: Invalid argument (22)
Jul 28 07:41:14  mythbackend[7938]: last message repeated 880 times

I'm on version 3.2.0-27-generic of the kernel.  I have not installed a custom driver for the HVR-2250, I default to what's delivered with the kernel.


Not a killer - I can use tuner 1 to record digital.  But with the Olympics on, my wife would like those in HD, while my kids still want their Sesame St, so there's some prioritizing going on right now.  And I'd like to figure this out and fix it.

Anyone got any ideas?

---

### Post by tgm4883 on 2012-07-28
> **johnlatz said:**
> This issue has cropped up on me recently.  

First off, I'm on Mythbuntu-Repos, current version:
MythTV Version : v0.25.2-8-g3256849
MythTV Branch : fixes/0.25
Network Protocol : 72
Library API : 0.25.20120506-1
QT Version : 4.8.1

The hardware in question is a Hauppauge-2250 card, DVB input, tuner #2.  I have configured my backend to allow 2 recordings per digital tuner, so I'll refer to tuner 2.1 and tuner 2.2.

My provider (So Cal Time Warner) remapped their digital channels recently, which caused me to have to rescan for new channels.  If I perform a scan using tuner #1, I can find all the new channels with no problem.

If I scan with tuner 2.2, I can find new channels no problem.

If I scan with tuner 2.1 - nothing.

If I attempt to record using tuner 1, no problem.

If I attempt to record on tuner 2.2 (Encoder 20 currently) - MythTV defaults to using tuner 2.1 (Encoder 19).  Thus, I cannot seem to force MythTV to use tuner 2.2 (Encoder 20), the side of that tuner that WAS able to scan for channels.

If I attempt (or am forced to) record on tuner 2.1 (Encoder 19), I get nothing.  Mythweb shows a "B" in the value of filesize under "Recorded Programs".    The Mythweb "Backend Logs" page shows the following:
row  &#8595;             id host application pid tid thread filename line function msgtime level message                      0   732472   Mythbox   mythbackend   7938   8556   SignalMonitor   dvbchannel.cpp   1022   GetSignalStrength   2012-07-28 07:22:05   3   DVBChan(19:/dev/dvb/adapter2/frontend0): Getting Frontend signal strength failed.             eno: Invalid argument (22)repeated numerous (>25) times.

mythbackend.log is a little more thorough:
Jul 28 07:40:13 Mythbox mythbackend[7938]: E SignalMonitor dvbchannel.cpp:1022 (GetSignalStrength) DVBChan(19:/dev/dvb/adapter2/frontend0): Getting Frontend signal strength failed.#012#011#011#011eno: Invalid argument (22)
Jul 28 07:41:14  mythbackend[7938]: last message repeated 880 times

I'm on version 3.2.0-27-generic of the kernel.  I have not installed a custom driver for the HVR-2250, I default to what's delivered with the kernel.


Not a killer - I can use tuner 1 to record digital.  But with the Olympics on, my wife would like those in HD, while my kids still want their Sesame St, so there's some prioritizing going on right now.  And I'd like to figure this out and fix it.

Anyone got any ideas?

Sounds like you've got something setup wrong. You should only need to scan once per video source, so since both sides of the card should be using the same video source, you should only need to scan once.

In mythtv-setup, can you provide a screenshot of step 2 (capture cards)? I'd like to know how many cards are listed there and what they say.

---

### Post by johnlatz on 2012-07-28
> **tgm4883 said:**
> Sounds like you've got something setup wrong. You should only need to scan once per video source, so since both sides of the card should be using the same video source, you should only need to scan once.

In mythtv-setup, can you provide a screenshot of step 2 (capture cards)? I'd like to know how many cards are listed there and what they say.

I have two capture cards:  an older HVR-1600, on which the mechanical coax connector is broken; hence it is only an analog tuner now - that is on /dev/video0.  Then my HVR-2250, on video1/adapter1 and video2/adapter2  (see first image)

Both digital tuners on the HVR-2250 are set up exactly the same way:  DVB-DTV capture card, Samsung S5H1411 QAM is the Frontend ID, Max Recordings 2.  I have had this card for a couple of years, and have found that by setting Max Recordings 2, I can in fact record two digital streams *as long as both streams are broadcast on the same freqid* i.e., I can record 88-172 and 88-173 at the same time, but I cannot record 88-172 and 99-501 at the same time (under those conditions, Myth used to schedule the second tuner to cover the second recording).  Used to work great because TW used to group the different PBS stations on the same freqid.

I've been running this hardware fine for years now (one of the reasons I still have the HVR-1600 around is I bought the 2250 before the analog drivers were finalized).  12.04/0.25 seems to be giving me trouble.


And just to reiterate - I only seem to be having trouble recently with tuner 2.1 (encoder 19).  I agree, I should be able to scan once and have all the tuners rely on that map.  But when I started to get "B" filesize recordings using tuner 2.1, I started to investigate...

---

### Post by nickrout on 2012-07-28
> **johnlatz said:**
> I have two capture cards:  an older HVR-1600, on which the mechanical coax connector is broken; hence it is only an analog tuner now - that is on /dev/video0.  Then my HVR-2250, on video1/adapter1 and video2/adapter2  (see first image)

Both digital tuners on the HVR-2250 are set up exactly the same way:  DVB-DTV capture card, Samsung S5H1411 QAM is the Frontend ID, Max Recordings 2.  I have had this card for a couple of years, and have found that by setting Max Recordings 2, I can in fact record two digital streams *as long as both streams are broadcast on the same freqid* i.e., I can record 88-172 and 88-173 at the same time, but I cannot record 88-172 and 99-501 at the same time 
 yes that's how it works, with any one tuner you can only record off the same mux> (under those conditions, Myth used to schedule the second tuner to cover the second recording).  Used to work great because TW used to group the different PBS stations on the same freqid.

I've been running this hardware fine for years now (one of the reasons I still have the HVR-1600 around is I bought the 2250 before the analog drivers were finalized).  12.04/0.25 seems to be giving me trouble.


And just to reiterate - I only seem to be having trouble recently with tuner 2.1 (encoder 19).  I agree, I should be able to scan once and have all the tuners rely on that map.  But when I started to get "B" filesize recordings using tuner 2.1, I started to investigate...

Are all your digital tuners using the same video source? They should be. You scan a video source when you tie it to a card using input connections.

Can you show a screenie of your input connections in mythtv-setup?

---

### Post by johnlatz on 2012-07-28
> **nickrout said:**
> yes that's how it works, with any one tuner you can only record off the same mux

Are all your digital tuners using the same video source? They should be. You scan a video source when you tie it to a card using input connections.

Can you show a screenie of your input connections in mythtv-setup?

Wife is watching the opening ceremonies right now, so no screen shot.

But to answer your question, yes, both tuner 1 and tuner 2 are using the same video source...

But to reiterate.  Today, right now (were my wife not using the box), I could do a scan using tuner 1, and it would find all of my digital channels (I did this two days ago when TW remapped their channels).  I can do a scan using tuner 2.2, and it will find all digital channels (I did that this morning).  I can do a scan using tuner 2.1, and it will find **_nothing_** (did that last night).  Not a bloody thing.  No signal - nothing.

Correlate this behavior with the error messages that popped up in /var/log/mythtv/mythbackend.log when I was attempting to record a channel today on tuner 2.1:
```
Jul 28 07:40:13 Mythbox mythbackend[7938]: E SignalMonitor dvbchannel.cpp:1022 (GetSignalStrength) DVBChan(19:/dev/dvb/adapter2/frontend0): Getting Frontend signal strength failed.#012#011#011#011eno: Invalid argument (22)
Jul 28 07:41:14  mythbackend[7938]: last message repeated 880 times
Jul 28 07:42:00  mythbackend[7938]: last message repeated 686 times

```

It would appear to me that for some reason, tuner 2.1 (encoder 19:) isn't getting a signal.  Now it isn't hardware, since on the 2250, there is only one wire plugged in the back, and the analog, both legs of tuner 1, and tuner 2.2 are getting signal.  So the card is getting adequate signal.  There's something specific to tuner 2.1 - either something on the card fried, or there's a bug somewhere in the 0.25-repos...  Based on the "invalid argument" listed in the logs, I'm leaning to a software bug.

---

### Post by nickrout on 2012-07-28
Try deleting all your capture cards in mythtv setup (not "all on this machine", but ALL of them). Then add them again, in the order you want them prioritised. You can do more than 2 virtual tuners per physical card if you want, it depends on your mux setup and overall backend IO how much utility this has for you. I have 5 virtual recorders per physical tuner.

Don't worry you won't lose any tuning or channel info, simply connect them to the correct video sources again and you should be done.

The fact that you are up to tuners 19 and 20 in your database suggest to me that you have added and deleted quite few of them. Things CAN get corrupted and confused by this. The above may well fix it, and takes a very short space of time (although I can understand that interrupting the opening ceremony is no go!) I did it the other day and it took more than 5 minutes.

---

### Post by jwhiteIT on 2012-07-29
Hi all,

Just a note on this card.  It caused me massive pain for a while..  I live in Sydney, Australia.  We have 3 "main" stations 7, 9 and 10.  We kept missing a lot of recordings and they were all on one channel (or varying frequencies of it). I had to create two separate input groups and delete channel 9 from it. I'm lucky I have other cards in my system.

---

### Post by johnlatz on 2012-07-29
> **nickrout said:**
> Try deleting all your capture cards in mythtv setup (not "all on this machine", but ALL of them). Then add them again, in the order you want them prioritised. You can do more than 2 virtual tuners per physical card if you want, it depends on your mux setup and overall backend IO how much utility this has for you. I have 5 virtual recorders per physical tuner.

Don't worry you won't lose any tuning or channel info, simply connect them to the correct video sources again and you should be done.

The fact that you are up to tuners 19 and 20 in your database suggest to me that you have added and deleted quite few of them. Things CAN get corrupted and confused by this. The above may well fix it, and takes a very short space of time (although I can understand that interrupting the opening ceremony is no go!) I did it the other day and it took more than 5 minutes.

No Joy - resultant screencaps:

---

### Post by johnlatz on 2012-07-29
```
Jul 29 09:55:52 Mythbox mythbackend[15786]: I Scheduler scheduler.cpp:2093 (HandleReschedule) Scheduled 404 items in 2.1 = 0.58 match + 1.56 place
Jul 29 09:55:52 Mythbox mythbackend[15786]: I TVRecEvent tv_rec.cpp:1536 (HandlePendingRecordings) TVRec(9): ASK_RECORDING 9 0 0 0
Jul 29 09:55:52 Mythbox mythbackend[15786]: I TVRecEvent tv_rec.cpp:1029 (HandleStateChange) TVRec(8): Changing from None to RecordingOnly
Jul 29 09:55:52 Mythbox mythbackend[15786]: I TVRecEvent tv_rec.cpp:3495 (TuningCheckForHWChange) TVRec(8): HW Tuner: 8->8
Jul 29 09:55:52 Mythbox mythbackend[15786]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jul 29 09:55:52 Mythbox mythbackend[15786]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: Mythbox as a client (events: 2)
Jul 29 09:55:52 Mythbox mythbackend[15786]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jul 29 09:55:52 Mythbox mythbackend[15786]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: Mythbox as a client (events: 2)
Jul 29 09:55:53 Mythbox mythbackend[15786]: E TVRecEvent dvbchannel.cpp:1022 (GetSignalStrength) DVBChan(8:/dev/dvb/adapter2/frontend0): Getting Frontend signal strength failed.#012#011#011#011eno: Invalid argument (22)
Jul 29 09:55:53 Mythbox mythbackend[15786]: W TVRecEvent dvbsignalmonitor.cpp:85 (DVBSignalMonitor) DVBSM(/dev/dvb/adapter2/frontend0): Cannot measure Signal Strength#012#011#011#011eno: Invalid argument (22)
Jul 29 09:55:53 Mythbox mythbackend[15786]: E TVRecEvent dvbchannel.cpp:1051 (GetSNR) DVBChan(8:/dev/dvb/adapter2/frontend0): Getting Frontend signal/noise ratio failed.#012#011#011#011eno: Invalid argument (22)
Jul 29 09:55:53 Mythbox mythbackend[15786]: W TVRecEvent dvbsignalmonitor.cpp:87 (DVBSignalMonitor) DVBSM(/dev/dvb/adapter2/frontend0): Cannot measure S/N#012#011#011#011eno: Invalid argument (22)
Jul 29 09:55:53 Mythbox mythbackend[15786]: I TVRecEvent tv_rec.cpp:1536 (HandlePendingRecordings) TVRec(3): ASK_RECORDING 3 0 0 0
Jul 29 09:55:53 Mythbox mythbackend[15786]: N Scheduler autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 7 min
Jul 29 09:55:53 Mythbox mythbackend[15786]: I Scheduler scheduler.cpp:2514 (HandleRecordingStatusChange) Tuning recording: "Susan Lucci's Malibu Pilates": channel 2131 on cardid 8, sourceid 2
Jul 29 09:55:53 Mythbox mythbackend[15786]: E SignalMonitor dvbchannel.cpp:1022 (GetSignalStrength) DVBChan(8:/dev/dvb/adapter2/frontend0): Getting Frontend signal strength failed.#012#011#011#011eno: Invalid argument (22)
Jul 29 09:55:53 Mythbox mythbackend[15786]: E HttpServer92 programinfo.cpp:2278 (GetPlaybackURL) ProgramInfo(2131_20120729095600.mpg): GetPlaybackURL: '2131_20120729095600.mpg' should be local, but it can not be found.
Jul 29 09:55:53 Mythbox mythbackend[15786]: E SignalMonitor dvbchannel.cpp:1022 (GetSignalStrength) DVBChan(8:/dev/dvb/adapter2/frontend0): Getting Frontend signal strength failed.#012#011#011#011eno: Invalid argument (22)
Jul 29 09:55:53 Mythbox mythbackend[15786]: E SignalMonitor dvbchannel.cpp:1022 (GetSignalStrength) DVBChan(8:/dev/dvb/adapter2/frontend0): Getting Frontend signal strength failed.#012#011#011#011eno: Invalid argument (22)
Jul 29 09:55:53 Mythbox mythbackend[15786]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M Susan Lucci's Malibu Pilates
Jul 29 09:55:53 Mythbox mythbackend[15786]: E SignalMonitor dvbchannel.cpp:1022 (GetSignalStrength) DVBChan(8:/dev/dvb/adapter2/frontend0): Getting Frontend signal strength failed.#012#011#011#011eno: Invalid argument (22)
Jul 29 09:55:54  mythbackend[15786]: last message repeated 11 times
Jul 29 09:55:54 Mythbox mythbackend[15786]: I Scheduler scheduler.cpp:2033 (HandleReschedule) Reschedule requested for id 0.
Jul 29 09:55:54 Mythbox mythbackend[15786]: E SignalMonitor dvbchannel.cpp:1022 (GetSignalStrength) DVBChan(8:/dev/dvb/adapter2/frontend0): Getting Frontend signal strength failed.#012#011#011#011eno: Invalid argument (22)
Jul 29 09:55:55  mythbackend[15786]: last message repeated 19 times
Jul 29 09:55:55 Mythbox mythbackend[15786]: I Scheduler scheduler.cpp:2093 (HandleReschedule) Scheduled 404 items in 1.3 = 0.00 match + 1.31 place
Jul 29 09:55:55 Mythbox mythbackend[15786]: E SignalMonitor dvbchannel.cpp:1022 (GetSignalStrength) DVBChan(8:/dev/dvb/adapter2/frontend0): Getting Frontend signal strength failed.#012#011#011#011eno: Invalid argument (22)
Jul 29 09:56:02  mythbackend[15786]: last message repeated 97 times
```


Lather, rinse, repeat until I delete the recording...

---

### Post by johnlatz on 2012-07-29
> **jwhiteIT said:**
> Hi all,

Just a note on this card.  It caused me massive pain for a while..  I live in Sydney, Australia.  We have 3 "main" stations 7, 9 and 10.  We kept missing a lot of recordings and they were all on one channel (or varying frequencies of it). I had to create two separate input groups and delete channel 9 from it. I'm lucky I have other cards in my system.

I've had the card up and running in this rig for several years.  Don't dispute it has issues, but I had most all of them troubleshot for my specific needs.

Something has changed in the last few weeks - either a software/driver bug (I'm on 0.25-repos, and am pretty religious about upgrading the system software as well, Ubuntu just pushed out 3.2.0-27-generic; so if there's a bug in the software, I would have caught it), or my hardware fried.  Simply hoping it is the former...

---

### Post by johnlatz on 2012-08-01
I am now sporadically recording with the second digital tuner on this card - most of the time it fails, sometimes I get a complete recording.

The latest error - I got about 10 seconds of a 30 minute show this morning.  Anyone have a clue on this error?

```
Aug  1 09:30:01 Mythbox mythbackend[31892]: I TVRecEvent tv_rec.cpp:816 (FinishedRecording) TVRec(8): FinishedRecording(2501_2012-08-01T09:00:00) damaged recq:<RecordingQuality overall_score="0" key="2501_2012-08-01T09:00:00" countinuity_error_count="2" packet_count="44450">#012    <Gap start="2012-08-01T09:00:10" end="2012-08-01T09:30:00" duration="1790" />#012</RecordingQuality>

```

The filesize of the result was only 7.5 MB...

---

### Post by nickrout on 2012-08-01
> **johnlatz said:**
> No Joy - resultant screencaps:

where are encoders 4 and 5?

---

### Post by johnlatz on 2012-08-01
> **nickrout said:**
> where are encoders 4 and 5?

I deleted all cards from my machine, then started adding them back.  I have one HVR-1600 with a mechanically failed coax connector, and one HVR-2250.  In the process of adding back all the cards (both analog and digital), I realized I had added the dead HVR-1600 instead of the HVR-2250, so I deleted it.   That much I remember - where encoder 5 went, I probably added and deleted one of the -2250's in the process (simply don't remember).

---

### Post by dperham on 2012-08-26
> **johnlatz said:**
> I've had the card up and running in this rig for several years.  Don't dispute it has issues, but I had most all of them troubleshot for my specific needs.

Something has changed in the last few weeks - either a software/driver bug (I'm on 0.25-repos, and am pretty religious about upgrading the system software as well, Ubuntu just pushed out 3.2.0-27-generic; so if there's a bug in the software, I would have caught it), or my hardware fried.  Simply hoping it is the former...

Same!  I had my hvr 2250 working for two years.  but the day before the Olympic closing ceremonies things went to crap -- suddenly.  I had little SNR.  I tried many things, (I thought my distribution amplifier died) but I finally ordered a new hvr 2250 from amazon only to have the exact same problem.

---

### Post by Barry_IA on 2012-08-31
> **dperham said:**
> Same!  I had my hvr 2250 working for two years.  but the day before the Olympic closing ceremonies things went to crap -- suddenly.  I had little SNR.  I tried many things, (I thought my distribution amplifier died) but I finally ordered a new hvr 2250 from amazon only to have the exact same problem.

[FONT=Palatino Linotype]Any possibility of bad coax? A while back I had a problem with one tuner giving me problems.  The center conductor had slipped, so one end was barely contacting and the other stuck out.  (And this was a commercially manufactured cable.)[/FONT]

---

### Post by dperham on 2012-08-31
> **Barry_IA said:**
> [FONT=Palatino Linotype]Any possibility of bad coax? A while back I had a problem with one tuner giving me problems.  The center conductor had slipped, so one end was barely contacting and the other stuck out.  (And this was a commercially manufactured cable.)[/FONT]

Good suggestion.  I've checked all of the connections, besides, my TV (input is split - one to hvr-2250, the other to my TV) still gets all stations and a great signal.  I've tried to switch the input going to my TV to the input going into the hvr-2250.  Still the same.  I just took the update to mythtv (0.25.2+fixes.20120828.d519276-0ubuntu0mythbuntu4). I then ran mythbackend-setup and deleted my hvr-2250 inputs and added them back in -- and now things are worse.  I would occationally get channel 12 but now that doesn't even come in.  It's crazy.  I am going to install my old hvr-2250 into my windows-7 machine and hook that up and see if it is the hvr-2250 or mythtv.

---

### Post by dperham on 2012-09-01
Okay.  I am an idiot.  Please, ignore me from now on.   I installed my old hvr-2250 (that I thought was not working) in a Windows-7 machine and it exhibited roughly the same poor signal quality as my MythTV box.   I then, as a last ditch effort, replaced my distribution amp (a good one) with a simple coax coupling and voila! MythTV works again.   I had missed noticing the severe drop in power because my built in TV tuner was still able to tune, but the hvr-2250 was not.   By comparison, the power on channel 29 was "65" with the distribution amp and was "98" with just the coupling.  I am just going to get rid of the distribution amp altogether.   MythTV is awesome -- I am sorry for ever having doubted you, MythTV.

---

### Post by Brettvdl on 2012-11-02
Hi everyone, 
This is my first time here and would like some help if possible!

I have read through the previous 50 pages but i cant seem to find an answer. 

I have a 2250 installed in an unraid system and am getting the same errors as others. 

saa7164_cmd_send() No free sequences
saa7164_api_i2c_read() error, ret(1) = 0xc
tda10048_readreg: readreg error (ret == -5)

Was there ever a fix for this problem?
I run an intel system, and my symptoms appear between 1 hour and 5 days, once they appear only 1 channel works, the sys log is flooded, and i cannot access any other channels. Only a reboot solves the problem. 

Regards, 
Brett

---

### Post by km782 on 2012-11-07
> **Brettvdl said:**
> Hi everyone, 
This is my first time here and would like some help if possible!

I have read through the previous 50 pages but i cant seem to find an answer. 

I have a 2250 installed in an unraid system and am getting the same errors as others. 

saa7164_cmd_send() No free sequences
saa7164_api_i2c_read() error, ret(1) = 0xc
tda10048_readreg: readreg error (ret == -5)

Was there ever a fix for this problem?
I run an intel system, and my symptoms appear between 1 hour and 5 days, once they appear only 1 channel works, the sys log is flooded, and i cannot access any other channels. Only a reboot solves the problem. 

Regards, 
Brett

I have posted before about the same problem (I think my error message might be slightly different but very similar).  At one point over the summer after downloading and installing all of the latest updates for Ubuntu and Mythtv the problem went away.  I should have left everything as it was and not touched it again, but my system had a minor video glitch in some of the menus that I was hoping would be fixed.  When I updated again a month later the problem came back.  I was having to restart my system every 1 to 3 days.

I never really found a solution and was considering buying an Intel CPU and motherboard because I had heard that AMD CPU's cause problems for some reason.  Given that you are having the same problem I'm glad I didn't.  I ran the updates again last month and it looks like my problem has been fixed again.

Sorry I can't tell you specifically what changed or was causing the problem.  I am running Mythbuntu 12.04 and am running the most up to date version of Mythtv 0.25 (haven't upgraded to 0.26 yet).  At this point, unless I can find a good way to backup and restore my system to exactly the way it is now I don't think I'm going to bother with the updates any more.

---

### Post by km782 on 2012-11-07
> **km782 said:**
> I have posted before about the same problem (I think my error message might be slightly different but very similar).  At one point over the summer after downloading and installing all of the latest updates for Ubuntu and Mythtv the problem went away.  I should have left everything as it was and not touched it again, but my system had a minor video glitch in some of the menus that I was hoping would be fixed.  When I updated again a month later the problem came back.  I was having to restart my system every 1 to 3 days.

I never really found a solution and was considering buying an Intel CPU and motherboard because I had heard that AMD CPU's cause problems for some reason.  Given that you are having the same problem I'm glad I didn't.  I ran the updates again last month and it looks like my problem has been fixed again.

Sorry I can't tell you specifically what changed or was causing the problem.  I am running Mythbuntu 12.04 and am running the most up to date version of Mythtv 0.25 (haven't upgraded to 0.26 yet).  At this point, unless I can find a good way to backup and restore my system to exactly the way it is now I don't think I'm going to bother with the updates any more.

My system has been up and running for a few weeks straight.  Of course as soon as I say it's fixed, it stops working.  I got home tonight and I was getting the exact same error message that you have.  So, I take back what I said.  It seems like there is still no fix for this issue.

---

### Post by Dougustine on 2012-11-13
I noticed in my system there is no modprobe.d/options.conf file to edit, if I create one my systems hangs.  Any suggestions?  I used ubuntu 12.04

---

### Post by DoubleJ975 on 2012-12-14
Okay, LowSky - In my eyes you are a god with MythBuntu.  Thanks to you I have my WinTV-HVR-2250 set-up and working.  Both Tuners are pulling in my analog Basic Cable service and everything is working perfect off a keyboard.  I am now trying to get it to work with my RC6 remote (aka 1069 new version remote) and after over 10 hours of research I can not get it detected.  Ran Mythbuntu Control Center install for every remote option, and nothing...I am selecting it as a USB/Serial Remote but the ir blaster port is actually built right in the card, and I am running a brand new install of Mythbuntu 12.04 with MythTV 0.25.  Is there any help out there for me?  If you can't tell, I'm the worst kind of newbie coming over to linux from Windows XP of all things, so my knowledge base is very limited...typing command lines into the terminal window was overwhelming :( just by itself.

---

### Post by LowSky on 2012-12-14
> **DoubleJ975 said:**
> Okay, LowSky - In my eyes you are a god with MythBuntu.  Thanks to you I have my WinTV-HVR-2250 set-up and working.  Both Tuners are pulling in my analog Basic Cable service and everything is working perfect off a keyboard.  I am now trying to get it to work with my RC6 remote (aka 1069 new version remote) and after over 10 hours of research I can not get it detected.  Ran Mythbuntu Control Center install for every remote option, and nothing...I am selecting it as a USB/Serial Remote but the ir blaster port is actually built right in the card, and I am running a brand new install of Mythbuntu 12.04 with MythTV 0.25.  Is there any help out there for me?  If you can't tell, I'm the worst kind of newbie coming over to linux from Windows XP of all things, so my knowledge base is very limited...typing command lines into the terminal window was overwhelming :( just by itself.

I am no god. Thanks for the praise but you are way, way, way too kind.
As far as I know there is no support for the built in IR port of the 2250. I have the older model that came with a USB  receiver. I suggest you check newegg, ebay, or amazon for one that will work. I know it means spending more money but its the only thing I know.

for example:
[http://www.amazon.com/Windows-Control-Infrared-Receiver-Ultimate/dp/B00224ZDFY/ref=pd_sim_e_1](http://www.amazon.com/Windows-Control-Infrared-Receiver-Ultimate/dp/B00224ZDFY/ref=pd_sim_e_1)

---

### Post by nickrout on 2012-12-15
Best and cheapest remote I have seen for mythtv:

[http://rtr.ca/sapphire_remote/](http://rtr.ca/sapphire_remote/)

---

### Post by psxstudio on 2012-12-15
Hi.  Finally decided to setup a PVR alongside HTPC.  I'm using hvr-2250 and xbmcbuntu (3.2.0-34-generic-pae) for my HTPC.  I read the whole thread and managed to get the firmware installed on my system.  Checking all the settings, 2250 is recognized and installed properly.  Prior to installing mythtv, I wanted to test the 2250 using mplayer.  When I try to issue the scan cmd to grab OTA channels, I get a FATAL error!

scan /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB | tee channels.conf
scanning /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2284: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy

Any ideas?  Only thing I can think of ATM is that the 2250 is sharing IRQ with the video card (gt610).  I'm thinking of pulling the card out and test on a different ubuntu system (ie 11.10 or 12.04) instead of xbmcbuntu.

JB

---

### Post by psxstudio on 2012-12-15
My problem is now fixed and scans OTA channels.  Now, I just need to adjust my antenna so that I could get all available channels... I was getting around 50 OTA with "rabbit ears" antenna and only getting 35 with the RCA outdoor antenna  =[.  The reason 'adapter0' couldn't be opened was due to tvheadend using the adapter0.  I guess xbmcbuntu installs tvheadend by default and this problem was driving me mad.  DOH!!!

---

### Post by tgm4883 on 2013-02-06
Locking thread as new posts should be in a new thread due to the age of the original post (5 years ago). Many things have changed since then.

---

