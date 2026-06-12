---
title: "Howto install and setup of Mythbuntu 12.04 (64bit) for DVC-B using the Hauppauge WinT"
date: 2012-05-14
forum: Mythbuntu
---

### Post by Morten ML on 2012-05-14
**Installing and setup of Mythbuntu 12.04 (64bit) for DVC-B using the Hauppauge WinTV-HVR-930C and the PCTVSystems QuatroStick-nano 520e tutorial**

**Please note:**
This tutorial is a work in progress as it is pretty comprehensive. Therefore I will update it when i have time, so please come back and check it every now and then.

This tutorial describes the scenario of having the back and frontend on the same machine.

Table of Contents
[LIST=1]
[*]Goal for this post	
[*]Why I wrote this	
[*]Why I chose the 520e, the 930c and not the 930c-HD
[*]Different versions of both tuners	
[*]How to install the firmware for both the 930c and the 520e	
[*]Why and how to install the v4l-dvb program	
[*]How to check if the firmware is recognized	
[*]How to setup the Mythtv backend for solely using DVB-C	
[*]How to make Mythtv use two other disk drives other than the OS drive for recorded data	
[*]How to backup and restore you setup of Mythtv	
[*]Why the 520e stick is not really working and how to fix it	
[*]How to setup mythtv's backend use of the two usb sticks	
[*]How to use w_scan to figure out which frequencies your tv provider uses	
[*]What is EIT	
[*]That's it
[/LIST]


**Goal for this post**
The goal for this post is to provide a complete tutorial for setting up the backend of MythBuntu 12.04 for the use of two different tuner cards for DVB-C. Though the hardware is able to get other signals than DVB-C these will not be used. It is assumed that the back and frontend are on the same machine. 

If your setup is not completely like mine you still might find some of the topics usefull. 


**Why i wrote this**
I made this, so I can look it up when I have forgotten how I did things. I hope others can use it too.

**Why I chose the 520e, the 930c and not the 930c-HD**
I chose the PCTVSystems QuatroStick-nano 520e because it should be compatible with linuxtv and because it supported mpeg4.
See this link for hauppauge (and pctv) linux compatible tvtuners:
[http://www.linuxtv.org/wiki/index.php/Hauppauge]("http://www.linuxtv.org/wiki/index.php/Hauppauge")

The Hauppauge WinTV-HVR-930C I also chose because it was compatible with linuxtv. Actually I first bought Hauppauge WinTV-HVR-930C-HD. The HD version is not supported by linuxtv. Or atleast that is what I am guessing that all HD versions have the same USB ID. The HD version had USB ID 2040:b130 and the normal version have USB ID 2040:1605. 

I have made a note about it on the page: [http://www.linuxtv.org/wiki/index.php/Hauppauge]("http://www.linuxtv.org/wiki/index.php/Hauppauge")

Another thing about the 930c-not-HD version is that even if it says mpeg2 only in the stores I believe that it is able to get mpeg4. Somewhere I read that it is the computer that decompress the signal and not the tvtuner. Unfortunately I can't remember where. But with the 930c-not-HD I am able to get all the HD signals my provider sends. 

The HD channels my provider (yousee) sends are in mpeg4. So I can confirm that the normal 930c-not-hd can show the mpeg4 channels.

Wirbel2 confirms this in his post below. To qoute him:> ...mpeg4 as its getting a mpeg ts stream, independed of its actual content. Instead, the software is responsible here.
With that in mind I would recommend the the 930c-not-hd as the best choice for watching dvb-c tv. The 520e has a problem which I will address later.
Wirbel2 states that the 930c - I assume he means the not HD - can have some problems. I have not myself had any problems whatsoever with it. Maybe the problems is only for the DVB-T?
Again I'll let the reader decide what to do.

Thank you Wirbel2 for you confirmations, corrections and advices.

**Different versions of both tuners**
Apparently there are two versions of the 520e. The 23079 and the 23077.[http://www.cinemagic.dk/shop/pctv-quatrostick-nano-26978p.html]("http://www.cinemagic.dk/shop/pctv-quatrostick-nano-26978p.html") and [http://www.cinemagic.dk/shop/pctv-quatrostick-nano-26977p.html]("http://www.cinemagic.dk/shop/pctv-quatrostick-nano-26977p.html").
For the record the one I am using is the 23079. I have not tried the 23077 version and I do not know if it will work. From the post on linuxtv.com it is not clear if it works for all versions or just the 23079.
[http://www.linuxtv.org/wiki/index.php/PCTVSystems_QuatroStick-nano_520e]("http://www.linuxtv.org/wiki/index.php/PCTVSystems_QuatroStick-nano_520e")

And for the Hauppauge WinTV HVR-930C it is the same. More than one version of the non-HD. The one i have is model: 1279, which is working great, and can be found here (danish site sry) [930c 1279]("http://dhd.dk/hauppauge-wintv-hvr-930c-pc-and-mac.html"). The rest, there is the 01244 [930c 01244]("http://www.cinemagic.dk/shop/hauppauge-wintv-hvr-930c-10292p.html"), the [01309]("http://www.bj-trading.dk/bjshop/default.asp?skvare=4226888&f=edbp"), which I do not know if works or not.
Furthermore there is the 01239, which i think is for the german market.[http://www.hauppauge.tv/site/products/data_hvr930c.html]("http://www.hauppauge.tv/site/products/data_hvr930c.html")
This (the 01239) does not work, since it has the USB ID 2040:b130. 
[http://forums.debian.net/viewtopic.php?f=7&t=77512]("http://forums.debian.net/viewtopic.php?f=7&t=77512")  

Please do not buy this one: [Hauppauge WinTV HVR-930C HD Analog + DVB-T + DVB-C, USB]("http://www.computersalg.dk/produkt/636294?varenummer=636294&utm_source=EDBpriser&utm_medium=edbpriserLINK&utm_campaign=EDBpriser") as it is HD and I don't believe it will work. It's model number is: 1252.

If you have another version of either of the sticks please let me know if it works or not - and if it only works for DVB-C/T or what, then i will update this post and the linuxtv acordingly. 


**How to install the firmware for both the 930c and the 520e**
For the 930c the installation instructions is found here:
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-930C]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-930C")

go to directory Desktop (cd //home/&#8221;username&#8221;/Desktop)
```
mkdir 930c; cd  930c
wget http://www.wintvcd.co.uk/drivers/HVR-9x0_5_10_325_28153_SIGNED.zip
sudo apt-get install unzip
 unzip HVR-9x0_5_10_325_28153_SIGNED.zip
 dd if=HVR-900/emOEM.sys of=dvb-usb-hauppauge-hvr930c-drxk.fw bs=1 skip=71600 count=42692
 sudo cp dvb-usb-hauppauge-hvr930c-drxk.fw /lib/firmware/
cd ..
```

And for the 520e instructions are found here: [http://www.linuxtv.org/wiki/index.php/PCTVSystems_QuatroStick-nano_520e]("http://www.linuxtv.org/wiki/index.php/PCTVSystems_QuatroStick-nano_520e")
using your browser goto [http://www.linuxtv.org/wiki/index.php/PCTVSystems_QuatroStick-nano_520e]("http://www.linuxtv.org/wiki/index.php/PCTVSystems_QuatroStick-nano_520e")
and find :"*Alternatively, you can download the extracted firmware directly from*this link*"
and download the file &#8220;dvb-demod-drxk-pctv.fw&#8221;
copy the file into the &#8220;~/Desktop/520e&#8221; folder
from a terminal goto the folder &#8220;~/Desktop/520e&#8221; folder and
```
sudo cp dvb-demod-drxk-pctv.fw /lib/firmware/
cd ..
```

**Why and how to install the v4l-dvb program**
This program needs to be installed as it is what makes linux and the dvb communicate.
Before installing this we need:
```

sudo apt-get install libproc-processtable-perl
sudo apt-get install build-essential
sudo apt-get install linux-headers-$(uname -r) 
sudo apt-get install unzip
sudo apt-get install git
sudo apt-get install patchutils

```
Information copied from this link: [http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers]("http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers")
From you Desktop directory:
```
mkdir v4l-dvb; cd v4l-dvb;
sudo apt-get install git
git clone git://linuxtv.org/media_build.git
cd media_build 
sudo apt-get install  patchutils
./build
go make some coffee.
sudo make install
```

and reboot

**How to check if the firmware is recognized**
use some or all of these commands to check if the firmware is loaded and the sticks recognized. 
```
ls -l /dev/dvb/
ls -l /dev/dvb/adapter0
ls -l /dev/dvb/adapter*
```

OBS these commands will not work if you haven't installed v4l-dvb.
Stolen from
[http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers]("http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers")

**How to setup the Mythtv backend for solely using DVB-C**
see these links:
[http://beckustech.wordpress.com/2012/02/27/setting-up-a-home-server-with-ubuntu-11-10-part-2-mythtv/]("http://beckustech.wordpress.com/2012/02/27/setting-up-a-home-server-with-ubuntu-11-10-part-2-mythtv/")

For now we are not gonna scan for channels and instead we are going to set up the tuners properly.
Open the mythtv backend:
*Applications->System->MythTV Backend Setup*
Go into *1: General*
on the first page remember your pin code.
On the second enter your tv format and channel frequencies. Your &#8220;local time&#8221; you can leave at auto.
On a later page it says:&#8221;Maximum simultaneuos jobs on this backend&#8221; set this to the number of tuners you have times 2. so if you have one tuner enter 2. On the same page you can enter CPU usage. I have a fast machine so I entered high, but honestly I have no idea what this is so you can probably leave it at low.
Leave the rest, as is, in **1. General**.
In **2. Capture** cards select New capture card. Move the cursor to &#8220;Card type&#8221; and select &#8220;DVB DTV capture card (v3.x)&#8221;. In &#8220;DVB device&#8221; select something like OBS HUSK AT SKRIVE DETTE!!!. And make sure your subtype is DVB-C. Leave everything else as is.
Do the same for the other card.

Goto **4. video sources** and select &#8220;new video source&#8221;. Under listing grabber find you country and click yes to &#8220;Perform EIT scan&#8221;. Set &#8220;channel frequency table&#8221; to &#8220;try-all&#8221;. Select &#8220;configure&#8221; and set up your provider. Then finish and go back to main menu.
We gonna leave 5. and 6. for now and take a closer look at **7. storage devices**. So exit the mythbuntu backend for now.

**How to make Mythtv use two other disk drives other than the OS drive for recorded data**
Go to the folder 
/var/lib/
and copy the folder &#8220;mythtv&#8221;
Go to the drive and folder where you would like mythtv to save data and paste it.
Now change permissions so that folder &#8220;mythtv&#8221; is owned by you (username) and the group &#8220;mythtv&#8221; have read and write permissions.
This is not enough though. The group &#8220;mythtv&#8221; has to have read and write permissions to the &#8220;/&#8221; of that drive. Hence if a drive is mounted in /media/EXTsdb1 and in the file manager viewed as &#8220;EXTsdb1&#8221; then the group mythtv has to have read and write permissions to that drive &#8211; EXTsdb1. When this is done open Mythtv backend setup
applications->system->mythtv backend setup
go to **7 storage directories**
now you get a list that says 
[LIST=1]	
[*]Default
[*]livetv
[*]DB backups
[/LIST]
etc.

Enter the default and type in the path to the folder where you want to have mythtv store its recordings. Do this for all of these folders. You can now delete the paths /var/lib/mythtv/recordings etc. If I remember correct you use &#8220;d&#8221; to delete.
Exit the Mythtv backend.

**How to backup and restore you setup of Mythtv**
Information stolen from this page: [http://www.mythtv.org/wiki/Database_Backup_and_Restore]("http://www.mythtv.org/wiki/Database_Backup_and_Restore")
Two files have been made which are used for this. They are in 
/usr/share/mythtv
and are called:
&#8220;mythconverg_backup.pl&#8221; and &#8220;mythconverg_restore.pl&#8221;
When &#8220;mythconverg_backup.pl&#8221; is executed the backup file is saved in the folder we defined earlier ~/mythtv/db_backups.
For you own safety make a backup now. We gonna make another after having scanned for channels as this is time consuming and we do not wanna do it twice.

**Why the 520e stick is not really working and how to fix it**
The 520e has a problem. It is to sensitive and this can course it not to be able to get a lock on channels and when it does the image is pixelated and just bad. Due to this I recommend to use the other tuner &#8211; the 930c &#8211; to search for channels first. 
To fix the 520e your need and attenuater:
[http://www.mythtv.org/wiki/Adding_Digital_Cable_Channels_(For_ATSC/QAM_Tuner_Cards_--_USA/Canada)#Attenuators]("http://www.mythtv.org/wiki/Adding_Digital_Cable_Channels_(For_ATSC/QAM_Tuner_Cards_--_USA/Canada)#Attenuators")
[http://www.sadoun.com/Sat/Products/S/20DB-Attenuator.htm]("http://www.sadoun.com/Sat/Products/S/20DB-Attenuator.htm")

**How to setup mythtv's backend use of the two usb sticks**
Now we gonna set up the tv channels. If you can find out which frequencies and symbolrate your tv provider uses you can read on. For my company (Yousee) information can be found here:
[http://www.dkscan.dk/TV/yousee_hovedstaden.htm]("http://www.dkscan.dk/TV/yousee_hovedstaden.htm")
This site is in danish but the &#8220;Frekvens Digital&#8221; is the frequencies and the symbolrate I got from one of  these site:
[http://jamesoft.dk/?page_id=301]("http://jamesoft.dk/?page_id=301")
[http://www.suodenjoki.dk/yousee_dvbc_channels.htm]("http://www.suodenjoki.dk/yousee_dvbc_channels.htm")
The symbolrate is usually the same for all frequencies.
If you can not you should read the section &#8220;How to use w_scan to figure out which frequencies your tv provider uses&#8221; first. If you come from there remember to restart the myth-backend server.
```

sudo service mythtv-backend start

```

Make a list of the frequencies and bare in mind that some channels are encrypted and some are not. This can course problems. My provider has one channel encrypted on one frequency and not encrypted on another. If I scan for the non encrypted first and the encrypted later, the encrypted will overwrite the non encrypted, so you list should order all the frequencies with encrypted channels first.
Now open the MythTV backend again, select &#8220;5. Input connections&#8221; and select one of the tuners you set up earlier. Go to &#8220;video source&#8221; and change it from &#8220;none&#8221; to empty. Select the button &#8220;scan for channels&#8221; which should be activated now. 
Now for the time consuming and boring work of scanning for channels. 
Change the value for "*scan type*" until you see frequency, symbolrate, FEC, inversion and two more. Change the frequency and the symbolrate to the desired values and press "Next". Wait and let it scan. If it has found some channels keep clicking "Next" until you can click finish. If it didn't find any channels you can press back and change the frequency to the next value on your list. Repeat this for all frequencies. 

Do yourself a favor and backup your system after having found all the channels.

If this has been succesfull you can skip the next step.

**How to use w_scan to figure out which frequencies your tv provider uses**
You should only read this section if you do not know what frequencies your provider uses.
The &#8220;w_scan&#8221; program can help you to figure out which frequencies you provider uses but it is not a bulletproof way as some frequencies might be skipped by this program. 
The w_scan program uses you location (country) as a guideline for which frequencies to scan. I encourage you to use not just you own country code (DK for Denmark, DE for Germany etc) but try different ones. I found some channels using the DE instead of DK. 
Wirbel2 comments that you should only use your own country code and that the scans are the same for DE and DK. I remember it differently but i can be wrong. I let it be up to the reader to decide. 
To use the w_scan make sure you installed it and make sure you stop the myth-backend first:
```

sudo service mythtv-backend stop
cd //usr/share/dvb/dvb-c
w_scan -fc -c DE -X -O 1 -F -t 3 -Q 0 -S 1 >> //home/username/Desktop/channels.conf 
```
Maybe the -X should be left out I can't remember.

This will create a channels.conf file in the format:
NickHD:394000000:INVERSION_AUTO:6875000:FEC_AUTO:QAM_64:3700:3701:3700
for each found channel.
And here it is easy to see the frequency and the Symbolrate.
Do not import this channel.conf file into the MythTV backend because MythTV will not be able to get EIT in that way, and EIT is something we all want.

After having found the frequencies go back to **How to setup mythtv's backend use of the two usb sticks**.


**What is EIT**
Electronic Information Technology.
The TV provider uses the same frequency and symbolrate to send information about when what is aired. This means MythTV will be able to present a lovely overview of the channels and what is on.

**That's it**
That was that. you should have a working backend now. How to use the frontend is beyond the scope of this tutorial. You are very welcome to leave critique, comments or even thank yous if you feel like it. 
Hope you could use this.

Best regards
Morten

---

### Post by wirbel2 on 2012-05-14
> 
I encourage you to use not just you own country code (DK for Denmark, DE for Germany etc) but try different ones

No. You should not. You should pass *your* country code to w_scan, nothing else. And you can omit this for satellite.

> 
I found some channels using the DE instead of DK.

Both are doing for those countries exactly(!) the same. If you need to repeat a scan, your hardware&&driver setup doesnt work reliable. Thats true for all channel scanners.



Another comment, not the dvb device is responsible if you can receive mpeg4 as its getting a mpeg ts stream, independed of its actual content. Instead, the software is responsible here.
For most USB dvb devices, the difference for a 'HD' device is only a windows software codec, which you cannot use on linux anyway. So choose your device better by linux support and google around. The hvr930c has sometimes problems.

---

### Post by Morten ML on 2012-05-14
Hi Wirbel2
Thx for your corrections. 
I will update my post accordingly when i have time.

With regards to the 930c i haven't had any problems at all with it - can it be that the problems are only occurring if you use it for DVB-T?

Best Regards
Morten

---

### Post by torsten.st on 2012-05-15
hi,
it looks promising to finally get the 520e to work . . . but I cannot compile it. The build aborts with and error in ov534.c saying: linux/fixp-arith.h: No such file or directory

Any suggestions 
T

---

### Post by torsten.st on 2012-05-15
Hi again,

the file seems to be back . . . I just waited for some hours and did the whole process again . . . now it still "builds"

T

---

### Post by Morten ML on 2012-05-15
Hi Torsten.st

EDIT: I see we posted at the same time. Good to know you got it working. If you have another problem please post again.

EDIT2: I have updated the info about the 520e. There are two versions of it. please see: **Why I chose the 520e, the 930c and not the 930c-HD**

With that name you wouldn't happen to be a dane aswell? - just curious...

You shouldn't compile anything for the 520e. Simply copy the *.fw file to the /lib/firmware directory. keep in mind that the owner of that file should be root.

The thing that needs to be compiled and installed is the V4L-DVB program. I assume you followed the guide...

Are u using 32 or 64 bit and the 12.04 version? If you give me the precise specs i will make an VM and see if i can get the same error...

BTW: I have the 520e up and running. I needed a attenuater though, but it works now. I have only tried it for the DVB-C though. So you should ofc also be able to.

Best regards
Morten

---

### Post by torsten.st on 2012-05-15
Hi again,

thanks a lot . . . so far I could not see if it really works. DVB-T did not find anything, DVB-C just scans. I am now setting up MythTV. Seems it added the digital TV stuff into gnome . . . so far so good. 

I do run the 64 bit version  ):P and I am on of your southern neighbors . . . just the middle of Germany.
T

---

### Post by torsten.st on 2012-05-15
Hi again,
so . . . neither DVB-C nor DVB-T find any channel. 
The lsusb still shows "Pinnacle unknown " 
This is what w_scan for DVB-T returns
w_scan version 20111203 (compiled for DVB API 5.4)
using settings for GERMANY
DVB aerial
DVB-T Europe
frontend_type DVB-T, channellist 4
output format czap/tzap/szap/xine
output charset 'UTF-8', use -C <charset> to override
Info: using DVB adapter auto detection.
	/dev/dvb/adapter0/frontend0 -> DVB-C "DRXK DVB-C DVB-T": specified was DVB-T -> SEARCH NEXT ONE.
main:3079: FATAL: ***** NO USEABLE DVB-T CARD FOUND. *****
Please check wether dvb driver is loaded and
verify that no dvb application (i.e. vdr) is running.


For DVB_C it scans but .... nothing back


T

---

### Post by Morten ML on 2012-05-15
Hi Neighbor :)

Do you have an attenuater betweeen the antenna cable and your 520e?
If you do not the scan will not give any signals as the tuner can not get a lock without it. I have an attenuater that gives -20 dB and it still seems that i could use one more...

Another thing that just occurred to me is that there are different versions of the 520e. Do you have the PCTV QuatroStick nano 520e (23079) or the (23077)? 

I have the 23079 working...

EDIT: I have updated the original post. I forgot you have to shut down the mythtv-backend before using w_scan.

---

### Post by fixitdude on 2012-05-15
I originally had VDR installed and I think when you install it they automatically start it.

If you are testing I would think you need to shut down anything that is accessing the device. I uninstalled VDR

Is there a command to check to see if anything is accessing the device?

And why doesn't any of these scanning programs detect if the device is busy and TELL US it is?

---

### Post by Morten ML on 2012-05-16
Hi fixitdude

According to torsten.st's last post it is actually saying something like it> verify that no dvb application (i.e. vdr) is running.
Anywho I forgot that the mythtv-backend is ofcourse using the device, so it has to be stoppet before scanning. I have updated the toturial. Please see the section:
**How to use w_scan to figure out which frequencies your tv provider uses**

And remember an attenuater if you are using the 520e.

/Morten

---

### Post by torsten.st on 2012-05-16
HI again,
so far I didn`t use an attenuator ( have to get one ) but the stick works just fine on a Vista machine. 
How can I figure out which version of the stick I am using ?
cheers 
T

---

### Post by Morten ML on 2012-05-16
Hi T

If you read here under "known issues":[http://www.linuxtv.org/wiki/index.php/PCTVSystems_QuatroStick-nano_520e]("http://www.linuxtv.org/wiki/index.php/PCTVSystems_QuatroStick-nano_520e")

The amplifier can be turned off when using windoze so therefore it works on vista without attenuater. 

With regards to the version of it i looked at the box... If you don't have that anymore we can compare USB ID's. 
I have 2013:0251 for the 23079.
If you type:
```
lsusb
```
and look for the (Pinnaccle?) thing and look for the numbers.

Also on the back of my 520e there is a number: 01167
I don't know if this can be used to identify it, but maybe you could check this also.

/Morten

---

### Post by torsten.st on 2012-05-16
Yepp, I thought it must be the reason . . .disabling the amplifier is an option on the first page.
Ok, we do have the same device . .. 
cheers
T

---

### Post by fixitdude on 2012-05-18
An attenuator could be as simple as moving it to a place where TV signals are typically weak.

You could test a few scans while placing the device inside a metal can or box with different parts of it opened letting just a little signal in.

You get the idea.

I tried it on mine just in case the "amplifier" situation was in play but it seems that this HD stuff likes a strong signal. Plus these things have got to have some kind of AGC built in.

You could tell in the scan where it is trying to simply find stations with ANY signal. If you are way too attenuated then it never picks up any signal.

w_scan looks like it's detecting ANY signal carrier first, then goes back to those frequencies it found in a second pass and looks for proper HD decoding. That's where mine fails for some reason.

---

### Post by Morten ML on 2012-05-20
Hi fixitdude

Thx for chipping in on this thread. 

My post was intended originally for DVB-C which is what Mr T is using it for also. Your advice of putting the tvtuner inside a metal box (faraday cage) or moving to a place with low signal strenght will not work for DVB-C but only for DVB-T. 

Instead one could try using a very long cable as an "attenuater" for DVB-C. 
Another note on this topic is that different channels might have different attenuater needs. I thought I had mine adjusted just right, but some channels still gave me trouble. I switched channels back and forth while adjusting the attenuater until it was just right. (Mine went from -0 dB to -20 dB). Now when i change channel some channels look weird and wrong for 2 seconds maybe and then the tuner locks correctly and the signal is good. 

Do you use the 23079 version of the 520e also? I am hoping that the 23077 will also work, so if you have that and it works let us know please.

/Morten

---

### Post by fixitdude on 2012-05-22
> **Morten ML said:**
> Hi fixitdude

Thx for chipping in on this thread. 

My post was intended originally for DVB-C which is what Mr T is using it for also. Your advice of putting the tvtuner inside a metal box (faraday cage) or moving to a place with low signal strenght will not work for DVB-C but only for DVB-T. 

Instead one could try using a very long cable as an "attenuater" for DVB-C. 
Another note on this topic is that different channels might have different attenuater needs. I thought I had mine adjusted just right, but some channels still gave me trouble. I switched channels back and forth while adjusting the attenuater until it was just right. (Mine went from -0 dB to -20 dB). Now when i change channel some channels look weird and wrong for 2 seconds maybe and then the tuner locks correctly and the signal is good. 

Do you use the 23079 version of the 520e also? I am hoping that the 23077 will also work, so if you have that and it works let us know please.

/MortenDidn't catch the "C" part, I guess you could take two cables (with connectors and the little wire sticking out on the end, or just stripped ends) and move them slowly away from each other, a sort of air attenuator.

I wouldn't go spending good money until I knew that was the problem.

Later you could build a box and switch with resistors in it and if you had two stations that like different signal strength you could switch the switch.

I think radio shack sold a small box with a knob on it (simple pot in a box and two connectors on the end).

---

### Post by torsten.st on 2012-05-22
Hi again, 
I just tried a bit more . . there are several ways to make a cable connection "bad" ... just pull the plug a bit out to get the signal weaker . . . it works now on DVB-C 
It still ignore -T 

cheers
T

---

### Post by Morten ML on 2012-05-22
Hi T

Are you trying to get a DVB-T signal and a DVB-C at the same time?

/Morten

---

### Post by torsten.st on 2012-05-22
nope, and another thing when I try Gnome-dvb stuff it constantly wants me to configure the device ... in between the dvb-utilities crash but that is Python related I guess ... the device is never accepted as being configured.
cheers
T

---

### Post by Morten ML on 2012-05-23
Can you show the output of 
```
lsusb
ls -l /dev/dvb/
dmesg | grep 520
```

/Morten

---

### Post by torsten.st on 2012-05-23
Hi again,

seems I have some more work suddenly . . . the whole device disappeared from the system. I think the recent updates kicked in . . . the modules are not loaded 
I will check later
cheers
T

---

### Post by torsten.st on 2012-05-23
back in business 

lsusb: 
Bus 002 Device 002: ID 2013:0251 Unknown (Pinnacle?)

ls -l 
drwxr-xr-x 2 root root 120 Mai 23 13:23 adapter0

dmesg
[    0.242520] pnp 00:09: [irq 4]
[    0.250520] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    4.220054] em28xx: New device PCTV Systems PCTV 520e @ 480 Mbps (2013:0251, interface 0, class 0)
[    4.537989] em28xx #0: Identified as PCTV QuatroStick nano (520e) (card=86)

cheers
T

---

### Post by Morten ML on 2012-05-23
I don't see why it shouldn't work. Have you tried to scan for channels from mythtvbackend?

/Morten

---

### Post by torsten.st on 2012-05-24
Hi again,
yes, mythtv works fine . . . actually the Gnome part isn t that important I guess that will fix "itself" over time 
I got it working once yesterday ... and cannot remember what I did before that :-)


But still, what do I have to do to get it to work with DVB-T ? Also in Myth it only recognited the subtype DVB-C for the device
cheers
T

---

### Post by Morten ML on 2012-05-24
Hi T

I cannot help you with that. You should be able to change the subtype, but for reasons not known to me you cannot.

I made a note about it here: [http://ubuntuforums.org/showthread.php?t=1972322]("http://ubuntuforums.org/showthread.php?t=1972322")

And then i forgot all about that problem. 

If i recall correctly the subtype was DVB-T after i installed the firmware, but after i changed it to DVB-C i could not change it back. If you need DVB-T maybe you could try to reinstall and see if it is set to DVB-T, but to be honest this is guesswork.

I hope you find a solution and if you do maybe you could provide a link?

/Morten

---

### Post by torsten.st on 2012-05-24
Hi, 
I will keep testing . . . any idea what this is about 
 146.833584] drxk: SCU_RESULT_INVPAR while sending cmd 0x0203 with params:
[  146.833597] drxk: 02 00 00 00 10 00 07 00 03 02                    ..........
[  150.209621] drxk: SCU_RESULT_INVPAR while sending cmd 0x0203 with params:
[  150.209634] drxk: 02 00 00 00 10 00 07 00 03 02               

it is dmesg | grep drxk output and is repeated constantly in the log
cheers
T

---

### Post by Morten ML on 2012-05-24
No not really.

google gave me this :
[http://comments.gmane.org/gmane.linux.drivers.video-input-infrastructure/43886]("http://comments.gmane.org/gmane.linux.drivers.video-input-infrastructure/43886")

Did you install the firmware for both the 930 and the 520?

/Morten

---

### Post by torsten.st on 2012-05-25
Hi,
at least intentionally I only installed the 520e firmware ... 
I will keep trying with a "from sratch" installation of the entire system the next days 
cheers
T

---

### Post by torsten.st on 2012-07-18
Hi,
it's me again.It worked until some days ago. After a new update ( and compiling etc) MythTV claims that all tuners are buys 
lsusb says: 
Bus 002 Device 011: ID 2013:0251 Unknown (Pinnacle?) 
and some dmesg output

[  334.502379] em28xx: New device PCTV Systems PCTV 520e @ 480 Mbps (2013:0251, interface 0, class 0)
[  334.502387] em28xx: Audio Vendor Class interface 0 found
[  334.502392] em28xx: Video interface 0 found
[  334.502397] em28xx: DVB interface 0 found
[  334.502621] em28xx #0: chip ID is em2884
[  334.808506] em28xx #0: Identified as PCTV QuatroStick nano (520e) (card=86)
[  334.808622] em28xx #0: Config register raw data: 0x14
[  334.809383] em28xx #0: AC97 vendor ID = 0x23bc23bc
[  334.809755] em28xx #0: AC97 features = 0x23bc
[  334.809760] em28xx #0: Unknown AC97 audio processor detected!
[  334.839868] em28xx #0: v4l2 driver version 0.1.3
[  334.879062] em28xx #0: V4L2 video device registered as video0
[  334.879632] em28xx-audio.c: probing for em28xx Audio Vendor Class
[  334.879638] em28xx-audio.c: Copyright (C) 2006 Markus Rechberger
[  334.879642] em28xx-audio.c: Copyright (C) 2007-2011 Mauro Carvalho Chehab
[  334.884991] drxk: frontend initialized.
[  334.885014] tda18271 0-0060: creating new instance
[  334.936509] tda18271_read_regs: [0-0060|M] ERROR: i2c_transfer returned: -19
[  334.936520] Unknown device (16) detected @ 0-0060, device not supported.
[  334.936529] tda18271_attach: [0-0060|M] error -22 on line 1274
[  334.936536] tda18271 0-0060: destroying instance
[  334.942877] Registered IR keymap rc-pinnacle-pctv-hd
[  334.943099] input: em28xx IR (em28xx #0) as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/rc/rc1/input15
[  334.943244] rc1: em28xx IR (em28xx #0) as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/rc/rc1
[  334.950739] drxk: status = 0x639260d9
[  334.950748] drxk: detected a drx-3926k, spin A3, xtal 20.250 MHz
[  334.976892] BUG: unable to handle kernel paging request at ffffc90005263002
[  334.976905] IP: [<ffffffffa0f2ae33>] init_drxk+0x483/0xb20 [drxk]
[  334.976925] PGD 12701a067 PUD 12701b067 PMD 11fa24067 PTE 0
[  334.976939] Oops: 0000 [#1] SMP 
[  334.976948] CPU 1 
[  334.976952] Modules linked in: des_generic md4 nls_utf8 cifs rc_pinnacle_pctv_hd(O) em28xx_rc(O) rc_core(O) dm_crypt usb_storage snd_usb_audio uvcvideo(O) videobuf2_core(O) videobuf2_vmalloc(O) videobuf2_memops(O) snd_usbmidi_lib joydev tda18271(O) pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) drxk(O) em28xx_dvb(O) dvb_core(O) em28xx_alsa(O) snd_hda_codec_realtek em28xx(O) snd_hda_intel v4l2_common(O) videodev(O) snd_hda_codec media(O) videobuf_vmalloc(O) videobuf_core(O) nvidia(P) tveeprom(O) snd_hwdep arc4 snd_pcm pcmcia snd_seq_midi snd_rawmidi btusb snd_seq_midi_event psmouse serio_raw snd_seq yenta_socket pcmcia_rsrc pcmcia_core irda crc_ccitt snd_timer snd_seq_device iwl4965 iwl_legacy mac80211 snd bnep rfcomm cfg80211 parport_pc bluetooth fujitsu_laptop ppdev mac_hid binfmt_misc soundcore snd_page_alloc lp parport vesafb usbhid hid firewire_ohci firewire_core crc_itu_t sdhci_pci sdhci video e1000e
[  334.977113] 
[  334.977120] Pid: 3484, comm: firmware/dvb-de Tainted: P           O 3.2.0-27-generic #43-Ubuntu FUJITSU SIEMENS LIFEBOOK E8410/FJNB1D0
[  334.977133] RIP: 0010:[<ffffffffa0f2ae33>]  [<ffffffffa0f2ae33>] init_drxk+0x483/0xb20 [drxk]
[  334.977149] RSP: 0018:ffff8800c0b1de40  EFLAGS: 00010246
[  334.977155] RAX: ffff8800c08b8040 RBX: ffff8800c9221800 RCX: 0000000000000000
[  334.977162] RDX: 00000000c08b8b00 RSI: ffff8800c37a8bc9 RDI: ffff8800c9221c98
[  334.977169] RBP: ffff8800c0b1de90 R08: 0000000000000001 R09: 0000000000000000
[  334.977175] R10: dead000000200200 R11: 0000000000000001 R12: ffffc90005263000
[  334.977182] R13: ffffffff81402840 R14: 0000000000000000 R15: 0000000000000000
[  334.977189] FS:  0000000000000000(0000) GS:ffff88012bd00000(0000) knlGS:0000000000000000
[  334.977197] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  334.977203] CR2: ffffc90005263002 CR3: 0000000001c05000 CR4: 00000000000006e0
[  334.977209] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  334.977215] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  334.977222] Process firmware/dvb-de (pid: 3484, threadinfo ffff8800c0b1c000, task ffff880122688000)
[  334.977228] Stack:
[  334.977232]  ffff8800c0b1de60 c08b8b00813f256e 00000001c0b1de60 000b8800639260d9
[  334.977245]  ffff8800c0b1deb0 ffff8800c9221800 ffff8800c08b8040 ffffffff81402840
[  334.977258]  0000000000000000 0000000000000000 ffff8800c0b1deb0 ffffffffa0f2bbab
[  334.977270] Call Trace:
[  334.977284]  [<ffffffff81402840>] ? _request_firmware+0x270/0x270
[  334.977297]  [<ffffffffa0f2bbab>] load_firmware_cb+0x3b/0xa8 [drxk]
[  334.977307]  [<ffffffff81402881>] request_firmware_work_func+0x41/0x80
[  334.977318]  [<ffffffff8108a58c>] kthread+0x8c/0xa0
[  334.977328]  [<ffffffff816643f4>] kernel_thread_helper+0x4/0x10
[  334.977337]  [<ffffffff8108a500>] ? flush_kthread_worker+0xa0/0xa0
[  334.977346]  [<ffffffff816643f0>] ? gs_change+0x13/0x13
[  334.977350] Code: 88 5b fd ff ff 48 8b 83 d8 07 00 00 48 85 c0 0f 84 c6 00 00 00 83 3d 34 44 00 00 00 8b 10 4c 8b 60 08 89 55 bc 0f 85 7b 06 00 00 <41> 0f b6 54 24 02 41 0f b6 44 24 03 c1 e2 08 09 d0 0f b7 c0 85 
[  334.977452] RIP  [<ffffffffa0f2ae33>] init_drxk+0x483/0xb20 [drxk]
[  334.977465]  RSP <ffff8800c0b1de40>
[  334.977470] CR2: ffffc90005263002
[  334.977476] ---[ end trace f2fb0d6509597f43 ]

Do you have an idea ?
cheers
T

---

### Post by Morten ML on 2012-07-19
Hi Torsten

I am sorry I can not help you. 

I bought more tuners (Anysee E30 C plus) and since these are better than the 520 I am not using this anymore.

I did however try to test it in a VM, with no succes. Even though I had compiled V4L and installed the driver I could not get it to work on a completely updated system.

Best regards
Morten

---

### Post by torsten.st on 2012-07-19
Hi again,
yeah it is a pitty . . . each update already required a recompile and now ... dead.
The Anysee looks interesting seems to work with Linux out of the box ???
cheers
Torsten

---

### Post by Morten ML on 2012-07-19
> **torsten.st said:**
> 
The Anysee looks interesting seems to work with Linux out of the box ???

Well yes and no.
Yes you do not need to compile anything. All you have to do is plug it in and "System settings->Additional drivers->and enable some dvb". Very easy. And they work after all the updates I have done.

No becaouse some of the frequencies the tuner can not lock onto. I bought 3 of those and I entered different allowed lock times on each one - and used and attenuator on one. In this way I managed to get the tuners to lock onto different frequencies.
Between these three and my 930c I was finally able to cover all frequencies I wanted.

These tuners do seem to be more sensitive to noise, so i had to move my MC closer to the antenna cable outlet...
Oh and these tuners dont have QAM auto so you need to enter it manually -64 for me...

I don't know if i can recommend these or not, since I only know of these three tuners (Anysee, 520e and 930.) I believe that the Anysee is better than the 520e and it seemed to be able to pick up some frequencies the 930c couldn't. 

If I was to do it all again I would have bought 2*930 and 2*Anysee.

If you choose to buy the Anysee E30 C plus i will gladly help you. 

You can read more about it here: [http://www.opencompany.dk/blog/index.php/2011/05/linux-support-for-anysee-usb-tv-tuners-english/]("http://www.opencompany.dk/blog/index.php/2011/05/linux-support-for-anysee-usb-tv-tuners-english/")

It seems like a lot of Danes has used this tuner... If needed I can translate if google cannot.

Best regards
M

---

### Post by jojo75 on 2012-08-14
Hi, I have bought the PCTV usb stick 520e (the right one 23079), but I still have no /dev/dvb after following (many times) the tutorial on my asrock htpc (kernel 3.2.0.29) with integrated graphics from Intel. If I install the card on a lenovo laptop (kernel 3.2.0.27) with core2Duo and ATI card, it works.

I also got this warning when building v4l, I don't know if it matters or not:

<<Hmm... distro kernel with a non-standard place for module backports detected.
Please always prefer to use vanilla upstream kernel with V4L/DVB
I'll try to remove old/obsolete LUM files from /lib/modules/3.2.0-29-generic//updates/dkms:>>

The output of dmesg:
[    5.736195] DRXK driver version 0.9.4300
[    5.807444] tda18271_read_regs: [15-0060|M] ERROR: i2c_transfer returned: -19
[    5.807450] Unknown device (2) detected @ 15-0060, device not supported.
[    5.807454] tda18271_attach: [15-0060|M] error -22 on line 1274
[    5.807457] tda18271 15-0060: destroying instance
[    5.807486] Em28xx: Initialized (Em28xx dvb Extension) extension
[    5.841851] Registered IR keymap rc-pinnacle-pctv-hd
[    5.841961] input: em28xx IR (em28xx #0) as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/rc/rc1/input13
[    5.842056] rc1: em28xx IR (em28xx #0) as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/rc/rc1
[    5.843281] Em28xx: Initialized (Em28xx Input Extension) extension

Should I just give up and wait for updates?
Thanks for any reply
Jonathan

---

### Post by Morten ML on 2012-08-14
Hi Jonathan

I personally gave up on the 520e. As you can read from the thread both me and Torsten had problems with it. After some kernel updates i was not able to get the 520e to work - and since i could only support 4 hd tuners with my comp - i used the three Anysee i had and the one 930c. 

I believe that somewhere among the updates they forgot the support for the 520e. 

At every kernel update (and sometimes other updates) I have to reinstall the 930c and recompile V4l. this is not a big problem as i simply made a shell script to automate the process...

It has been a hassle to make it work properly - but having it work is great.
In retroperspective I would have considered buying a harddiskrecorder instead... Medion have some affordable ones... I believe this is a cheaper and easier solution - however not so "professional". The browser interface in mythtv is just brilliant, just to name one feature that you (as far as i know) don't get from a harddisk recorder...

If you need help with some of the other tuners I will gladly help, but i do not have time to investigate further into why the 520e doesn't work. Sorry.

Best regards
M

---

### Post by MastaG on 2012-09-10
Antti Palosaari has posted a patch to disable the builtin amplifier on the 520e.
[http://www.mail-archive.com/linux-media@vger.kernel.org/msg46857.html](http://www.mail-archive.com/linux-media@vger.kernel.org/msg46857.html)

I don't know if they have been merged yet.
Could anyone please test them for me?

Also, here in holland they only seem to sell the 23077 instead of the 23079.
I'm going to give it a shot unless somebody already tried it and can confirm it works (or not).

Thanks

---

### Post by Morten ML on 2012-09-11
Hi MastaG

It sounds great if you are able to disable the auto gain. But unfortunately I haven't used the 520e for some time now. There seems to be a problem with the driver as you can gather from the posts in this thread.

I hope you get it to work. 

Best regards
Morten

---

### Post by MastaG on 2012-09-18
Well good news :)

The 23077 works pretty much out of the box when using kernel 3.5.0-13-generic.
I'm running Ubuntu 12.04 with the xorg-edgers ppa which gets me the latest kernel/xorg-stack/nvidia drivers for my htpc.

Here my dmesg without the firmware installed
```
[421900.224042] usb 6-2: new high-speed USB device number 2 using xhci_hcd
[421900.244066] usb 6-2: New USB device found, idVendor=2013, idProduct=0251
[421900.244076] usb 6-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[421900.244082] usb 6-2: Product: PCTV 520e
[421900.244087] usb 6-2: Manufacturer: PCTV Systems
[421900.244092] usb 6-2: SerialNumber: 00000010GZ63
[421900.286064] Linux video capture interface: v2.00
[421900.293893] em28xx: New device PCTV Systems PCTV 520e @ 480 Mbps (2013:0251, interface 0, class 0)
[421900.293901] em28xx: Audio Vendor Class interface 0 found
[421900.293904] em28xx: Video interface 0 found
[421900.293907] em28xx: DVB interface 0 found
[421900.294313] em28xx #0: chip ID is em2884
[421900.602823] em28xx #0: Identified as PCTV QuatroStick nano (520e) (card=86)
[421900.603197] em28xx #0: Config register raw data: 0x06
[421900.603202] em28xx #0: v4l2 driver version 0.1.3
[421900.619114] em28xx #0: V4L2 video device registered as video0
[421900.621868] usbcore: registered new interface driver em28xx
[421900.677947] drxk: status = 0x639260d9
[421900.677957] drxk: detected a drx-3926k, spin A3, xtal 20.250 MHz
[421900.729988] drxk: Could not load firmware file dvb-demod-drxk-pctv.fw.
[421900.729995] drxk: Copy dvb-demod-drxk-pctv.fw to your hotplug directory!
[421900.777076] DRXK driver version 0.9.4300
[421900.814447] drxk: frontend initialized.
[421900.819457] tda18271 3-0060: creating new instance
[421900.843080] TDA18271HD/C2 detected @ 3-0060
[421901.519225] DVB: registering new adapter (em28xx #0)
[421901.519236] DVB: registering adapter 0 frontend 0 (DRXK DVB-C DVB-T)...
[421901.521672] em28xx #0: Successfully loaded em28xx-dvb
[421901.521682] Em28xx: Initialized (Em28xx dvb Extension) extension
[421901.568051] Registered IR keymap rc-pinnacle-pctv-hd
[421901.568250] input: em28xx IR (em28xx #0) as /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/usb6/6-2/rc/rc0/input19
[421901.568421] rc0: em28xx IR (em28xx #0) as /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/usb6/6-2/rc/rc0
[421901.572227] Em28xx: Initialized (Em28xx Input Extension) extension
```

Here my dmesg with the firmware installed:
```
[    1.172080] usb 6-2: new high-speed USB device number 2 using xhci_hcd
[    1.192071] usb 6-2: New USB device found, idVendor=2013, idProduct=0251
[    1.192081] usb 6-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.192096] usb 6-2: Product: PCTV 520e
[    1.192101] usb 6-2: Manufacturer: PCTV Systems
[    1.192106] usb 6-2: SerialNumber: 00000010GZ63
[    1.560079] usb 4-2: new full-speed USB device number 2 using uhci_hcd
[    2.669437] Linux video capture interface: v2.00
[    2.676317] em28xx: New device PCTV Systems PCTV 520e @ 480 Mbps (2013:0251, interface 0, class 0)
[    2.676323] em28xx: Audio Vendor Class interface 0 found
[    2.676326] em28xx: Video interface 0 found
[    2.676329] em28xx: DVB interface 0 found
[    2.676714] em28xx #0: chip ID is em2884
[    2.989117] em28xx #0: Identified as PCTV QuatroStick nano (520e) (card=86)
[    2.989473] em28xx #0: Config register raw data: 0x06
[    2.989480] em28xx #0: v4l2 driver version 0.1.3
[    3.030616] em28xx #0: V4L2 video device registered as video0
[    3.134603] drxk: status = 0x639260d9
[    3.134614] drxk: detected a drx-3926k, spin A3, xtal 20.250 MHz
[    3.937378] DRXK driver version 0.9.4300
[    3.975760] drxk: frontend initialized.
[    3.991539] tda18271 0-0060: creating new instance
[    4.015129] TDA18271HD/C2 detected @ 0-0060
[    4.715011] DVB: registering new adapter (em28xx #0)
[    4.715021] DVB: registering adapter 0 frontend 0 (DRXK DVB-C DVB-T)...
[    4.716328] em28xx #0: Successfully loaded em28xx-dvb
[    4.716341] Em28xx: Initialized (Em28xx dvb Extension) extension
[    4.768046] Registered IR keymap rc-pinnacle-pctv-hd
[    4.768249] input: em28xx IR (em28xx #0) as /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/usb6/6-2/rc/rc0/input4
[    4.768434] rc0: em28xx IR (em28xx #0) as /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/usb6/6-2/rc/rc0
[    4.772148] Em28xx: Initialized (Em28xx Input Extension) extension
```

Seems to work with the firmware in place.
However PCTV forgot to supply a nice MCX to COAX-female (or f-connector) plug so  I can't connect my home cable atm.
I hope to get one this afternoon or else I'll have to find one online.

Also I'm curious wetter Antti's patch made it in kernel 3.5 (which disables the internal amplifier) if not, then I'll simply get the media_tree.git and apply the patches myself.

I'll keep you guys posted :)
Looking forward to setup XBMC /w libcmyth and oscam !

---

### Post by MastaG on 2012-09-20
Well for the PCTV Quatrostick nano 520e (I've only tried the 23077).
You have two options.

1. Use kernel 3.5 or 3.6 and the external firmware in /lib/firmware and you'll get DVB-C and DVB-T working.
Firmware can be found here: [http://www11.zippyshare.com/v/17827014/file.html|dvb-demod-drxk-pctv.fw]("http://www11.zippyshare.com/v/17827014/file.html%7Cdvb-demod-drxk-pctv.fw")
For the kernel you can install the xorg-edgers ppa:
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-image-generic
```Now reboot and it will work:)
However I don't know if the internal lna (amplifier) will be enabled or not.
Also you'll get some warnings in your dmesg when using it:
```
[  693.929230] drxk: SCU_RESULT_INVPAR while sending cmd 0x0203 with params: [  693.929239] drxk: 02 00 00 00 10 00 07 00 03 02
```


2. Use the latest media_build.git which has broken firmware loading at this time of writing.
However the PCTV 520e will also work without external firmware but only DVB-C will be enabled.
DVB-T won't work since it relies on the external firmware.
The internal lna will be disabled so no artifacts due to overgaining anymore :)
Also it will not spit any warnings to your dmesg.
Prepare it using:
```
git clone git://linuxtv.org/media_build.git
cd media_build
make download untar
```
Now edit linux/drivers/media/usb/em28xx/em28xx-dvb.c and disable loading the firmware by commenting out:
```
.microcode_name = "dvb-demod-drxk-pctv.fw",
```
So it looks like:
```
// .microcode_name = "dvb-demod-drxk-pctv.fw",
```
Now compile and install with:
```
make
sudo make install
```
Reboot and you'll have fully working DVB-C without the lna enabled and no warnings/errors in dmesg :)

Thanks to user "crope" on #linuxtv @ freenode.net for the patch!

---

### Post by os2 on 2013-01-06
Before getting bogged down the Media Centers, better to do a test to check your DVB setup is working correctly. That means your drivers and firmware all functioning properly. You can do this right away by tuning a MUX with VLC.

---

