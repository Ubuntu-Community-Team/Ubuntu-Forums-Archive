---
title: "Hauppauge HVR4000 and Scanning for channels *newbie desperate for help"
date: 2007-12-06
forum: Multimedia &amp; Video
---

### Post by Menthol on 2007-12-06
Hi,

After scanning through several thousand posts on different sites and google (well it seems like that) I am starting to loose the will to live.

I'm trying to get my TV tuner card (Hauppauge HVR 4000) to work under linux.  The problem is I dont even know where to start. I've installed various tv applications, Kaffeine, TVTime, XawTV, MythTV, none of which even seem to have the ability to scan for channels. 
Coupled with that problem, I dont even know if the card is working in Linux and dont know how to check. 
I installed some Video4Linux drivers but dont know if they are working, I read somewhere about applying a diff ? for the HVR4000 but no idea what that even means !

I've been trying for what seems like forever to get this thing working and have given up to be honest. My last resort is to post here and pray someone replies.
I'm using Gutsy Gibbon 7.10 AMD64bit version.

Any help really would be appreciated

---

### Post by ARhere on 2007-12-06
You need to explain the steps you have taken in detail or you are doomed to get advice that you have already tried.

1.  Did you find any compiled drivers in your search?
2.  If so, was there any testamony that the driver(s) have worked with your _exact_ hardware.
3.  If not, did you try compiling your own as explained in [this thread]("http://209.85.165.104/search?q=cache:1Oee0oxFZXsJ:www.gossamer-threads.com/lists/mythtv/mythtvnz/293961+Hauppauge+HVR+4000+linux+driver&hl=en&ct=clnk&cd=4&gl=us&client=firefox-a"). (*and several others I have found in a google search.*)

Be explicit.  You said...
> scanning through several thousand posts on different sites and google
Explain what options you have found others are doing.

It helps us help you if your steps and thoughts are listed here.  Otherwise, the only people who will post is that one rare person that already did the work.

-ARhere

---

### Post by Menthol on 2007-12-06
Hi,

I'm really new to this so apologies if I don't make much sense to begin with.
I did look at the thread you linked too, but when he said about applying the "diff" I was totally lost. I'd tried searching how to compile this but its just too far above my head.
I installed the main video4linux drivers from their site and did ./make and then ./make install as they instructed, but I dont know how to apply these "diff" thinggys people are talking about.

The sites I looked at were mainly the mythtv site, linuxtv site and of course here.

Any help on applying this patch or "diff" would be great.
Some people said they have got the DVB-S working well, while others said they got the whole card working, including DVB-T.

There is very little on the HVR-4000 for linux but what I've read is too confusing for me at this early stage of learning linux.

I can't be much more explicit, as I dont even know what I'm doing let alone anyone else :-)

Thanks for the reply, its appreciated.

---

### Post by ARhere on 2007-12-07
A "diff" is slang/short-hand for "difference" and it refers to comparing two sets of code and looking for differences between them.  Unfortunately I am an Electrical Engineer and most Software Engineers won't let me touch their code!  ;-)

It looks like the *.diff link is broken so you appear to have two options here.

1.  Email the poster and ask if he can send you his compiled driver -OR- source files including the *.diff he used to mod the driver.

-OR-

2.  Go buy a new TV tuner card.

You may not like the second option but please keep something in mind.  If this was Windows and you did not have a driver for your card, you would be screwed.  At least with Linux you have the option of creating your own driver without paying $$$ to M$ for the compiler/rights to working with your own system.  But as you said, you are new to this and are already diving into compiling your own driver.  This is _great_ but you need to decide if that is what you want to do as it looks like there is no "click this and it will run" solution.

HINT: Don't get too hung up if you cannot get the tuner card to work.  Unless you spent >$200 on it, just consider getting a new card.  I see tuner cards all over the place for <$50 now that ATI has been Borged by AMD.  In engineering our bosses have to remind us **constantly** that we can walk away form a board and cost $X, or spend weeks troubleshooting it can cost $10*X in time!

Good Luck! :guitar:
-AR

---

### Post by Menthol on 2007-12-07
Hmm, the *diff thing sounds interesting, I'll have a play around again tomorrow to see if I have any luck.  I think if I don't get any luck from it tomorrow I'll do what you've suggested.  The card cost me over $200 about 7 or 8 months ago so I don't want to get rid of it, but I think the other option is to get a cheap and cheerful card for now and wait a bit with the hope a driver will be written eventually for Linux with the HVR4000

I've got most things working nicely with ubuntu now, especially considering I'm using 64bit with an ATI card, which is a bit of a nightmare on its own. The TV card is the only thing left that wont work at all and I can make that sacrifice if it means I don't have to go back to Windows.

Many thanks,  I'll post any updates if I somehow do get the card to work.  :)

---

### Post by sirdilznik on 2007-12-08
As stated earlier a .diff is a patch that makes some changes to the source code.  Generally patches are applied in the following manner.
```

cd </path/to/source/code/directory>
patch -p1 < <filename.diff>

```
Replace </path/to/source....> and <filename.diff> as appropriate.
Note:  If the .diff file is not located inside the main source code directory (where you cd to), then you need to include the full path to the file instead of just the filename. 

Then you compile the program as usual which in most cases would go something like this:
```
./configure;make;sudo make install
```

---

### Post by Menthol on 2007-12-08
Thanks very much sirdilznik, thats a great help :) 

Much appreciated, it'll come in handy knowing that for other stuff too.=D>

---

### Post by Menthol on 2007-12-17
The story moves on - I applied the .diff patch from the link above to the V4L drivers, I've managed to get the analoge signal working b ut no audio, thats by following the directions exactly on the link.

Will update when I get more, with hopefully a proper tutorial of how I got it working once Ive done it

---

### Post by Cirion75 on 2007-12-18
To install this driver: [http://dev.kewl.org/hauppauge/](http://dev.kewl.org/hauppauge/)

I have found out that I can type this set of commands:

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb
wget [http://dev.kewl.org/hauppauge/v4l-dvb-hg-2007-12-09.diff](http://dev.kewl.org/hauppauge/v4l-dvb-hg-2007-12-09.diff)
patch -p1 < v4l-dvb-hg-2007-12-09.diff
make menuconfig
make
make install

Problem is, I have no idea what to do when entering the "make menuconfig"....  I do get a config menu but I do not know what to do there so I exit it.

When trying the make command it works for a looong time and then ends with a few errors I do not understand.

Make install also fails... 

I'm not shure if the error is in the make process or the make menuconfig.

Anyone want to try?

---

### Post by Cirion75 on 2007-12-18
Forgot to say that there is no error when applying the diff...
And if I do not apply the diff I can both make and make install.... But then I dont have drivers for the HVR4000....

---

### Post by Menthol on 2007-12-18
hmm, I've never done the "make menu config" bit before, I just make and make install. The drivers seem to go in correctly.  Ive got the analogue bit of the card working but with no sound, still no luck with the dvb or dvbs side though.
I'll keep you posted

Edit: I just tried the make menu config and I too get errors.  To be honest I've never heard of that menu config before so I'll have a play around later and post my findings.  I'm convinced we're so close to getting this working, its only a matter of time.

Also: remember to Sudo make and Sudo make install, otherwise it wont install properly !! Might be your problem

I'm testing with Kaffeine, KDETV, MythTV, TV Time, Klear and XawTV.

edit:  I am also now getting the error when applying the .diff with the newest v4l driver.  This wasnt happening with the older driver, suggest trying an earlier vestion

---

### Post by Cirion75 on 2007-12-18
If you look at the bottom of this page:[http://dev.kewl.org/hauppauge/](http://dev.kewl.org/hauppauge/)
You will find this:

Building for v4l-dvb
====================

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb
patch -p1 < v4l-dvb-XX-XX-2007.diff
make menuconfig
make
make install

---

### Post by Cirion75 on 2007-12-18
When trying now, I get a error when patching the diff too :(
This is the log:

patching file linux/drivers/media/dvb/frontends/Kconfig
patching file linux/drivers/media/dvb/frontends/Makefile
patching file linux/drivers/media/dvb/frontends/cx24116.c
patching file linux/drivers/media/dvb/frontends/cx24116.h
patching file linux/drivers/media/video/cx88/Kconfig
Hunk #1 succeeded at 57 (offset 1 line).
patching file linux/drivers/media/video/cx88/cx88-cards.c
Hunk #2 FAILED at 1388.
1 out of 7 hunks FAILED -- saving rejects to file linux/drivers/media/video/cx88/cx88-cards.c.rej
patching file linux/drivers/media/video/cx88/cx88-dvb.c
patching file linux/drivers/media/video/cx88/cx88-i2c.c
patching file linux/drivers/media/video/cx88/cx88-input.c
patching file linux/drivers/media/video/cx88/cx88.h
patching file linux/drivers/media/video/ir-kbd-i2c.c
patching file linux/drivers/media/video/tveeprom.c

Anyone know how to get a older version of the v4l-dvb?

---

### Post by Menthol on 2007-12-18
same message I now get.  you just go to the distro list here: [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb) to get older versions

I just tried a couple of older ones and I'm still getting the error message.  I'm sure I never saw that before ! just trying to figure out what the message is about.

I noticed also once compiled and installed, if you reboot there is a message in the boot log about the CX88 not being found.

Its something to do with the CX88-cards.c file.  Just tried messing with it but it didnt work :mad:

I'll post any more relevant findings.

---

### Post by Menthol on 2007-12-22
About ready to give up now :(
I don't think theres currently a way to get this working.  It might have worked once, maby under a 32bit system or something but theres no way these current drivers or driver patches work...not on my system anyway.
I'll post again if I ever see any news but for now its not looking good I'm afraid

---

### Post by mymythtv on 2007-12-24
I got the driver working, but for a Nova-HD-S2 - which is said to be a HVR4000 lite..
( no analog or DVB-T - only DVB-S/S2 )

Abount the errors 
patching file linux/drivers/media/video/cx88/Kconfig
Hunk #1 succeeded at 57 (offset 1 line).
patching file linux/drivers/media/video/cx88/cx88-cards.c
Hunk #2 FAILED at 1388.
1 out of 7 hunks FAILED -- saving rejects to file linux/drivers/media/video/cx88/cx88-cards.c.rej
patching file linux/drivers/media/video/cx88/cx88-dvb.c
patching file linux/drivers/media/video/cx88/cx88-i2c.c
patching file linux/drivers/media/video/cx88/cx88-input.c

It is somewhere in the cx88-cards.c where there are some lines for another card ( not the hvr4000  ). I'm not at home right now so I can't check which card it was ( think to remember something about hvr-1300 ), but i did check the cx88-cards.c file, and the patch was only adding code for the hvr4000.

I compiled with success, and now I got the card working - even my diseqc switch which gave me problems earlier ( somehow it was working wich kaffeine, but not mythtv ?! ). The readme says that there is support for DVB-S2, but I haven't checked that - yet :)

I followed the "guide" - just didn't do the "make menuconfig", but only make and make install...

So for now I will say that it's a succes with the driver...

---

### Post by Menthol on 2007-12-24
I followed the guide and have tried countless times with different techniques but no joy.  Kaffiene wont even look at the card, I get the cant bind info socket and it wont even try.
I even tried compiling a new kernel but that didnt work.  
I tried messing with the patch, I got the make menuconfig working but it then didnt compile properly.
I tried mythtv, kaffiene, xawtv, zapping, tvtime, kdetv.
I've pretty much given up for now and have installed a seperate windows partition to use the card.
Maby its because I'm using a 64 bit system or something.
I'll keep coming back and trying now and again but I've wasted enough time on this for now.
Strangely enough I have analogue working, but with no sound. I cant get the DVB or DVBs to work at all

Congrats on getting you're one to work :) Its good to know someone out there has it working somehow.
Can I ask how you are getting it to scan the DVB-S ? Are you using some sort of channels.conf or have you got a program to scan dvb properly?

---

### Post by Cirion75 on 2007-12-25
I see there is a Christmas present.... A new diff....
Patched ok, running Make now..

---

### Post by Cirion75 on 2007-12-25
No errors in make :)
No errors in make install :)

Now I just have to figure out how to use this card ;)

---

### Post by Cirion75 on 2007-12-25
I now have the driver installed on my LinuxMCE server. I'm running 0710 Beta2.
I have followed the DVB Wiki for LinuxMCE
[http://wiki.linuxmce.org/index.php/DVB](http://wiki.linuxmce.org/index.php/DVB)

Now I'm stuck again... I find no channels. I have edited the Astra19.2E file with a few transponder I know work. The Card is working great in WinXP and the dish is now set to Astra 19.2E

This is what I get when following the DVB Wiki for LinuxMCE:

linuxmce@dcerouter:~$ dsmeg | grep dvb
[   14.408000] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   14.408000] cx88/2: registering cx8802 driver, type: dvb access: shared
linuxmce@dcerouter:~$ sudo scan /usr/share/doc/dvb-utils/examples/scan/dvb-s/Astra-19.2E >channels.conf
[sudo] password for linuxmce:
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-s/Astra-19.2E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 10847000 V 22000000 5
initial transponder 10862000 H 22000000 5
initial transponder 10876000 V 22000000 5
initial transponder 10921000 H 22000000 5
initial transponder 10979000 V 22000000 5
initial transponder 12552000 V 22000000 5
>>> tune to: 10847:v:0:22000
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 10862:h:0:22000
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 10876:v:0:22000
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 10921:h:0:22000
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 10979:v:0:22000
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 12552:v:0:22000
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
dumping lists (0 services)
Done.
linuxmce@dcerouter:~$

---

### Post by Cirion75 on 2007-12-27
Succsess!!

I emailed to Darron and got the help I needed.

I'll try to recreate my steps so you can get this card working too :)

1. Go to [http://dev.kewl.org/hauppauge/](http://dev.kewl.org/hauppauge/) and look for the latest .diff file.
If there is a newer file than v4l-dvb-hg-2007-12-26.diff you have to change the filename below.

2. then enter a console and type the following:

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb
wget [http://dev.kewl.org/hauppauge/v4l-dvb-hg-2007-12-26.diff](http://dev.kewl.org/hauppauge/v4l-dvb-hg-2007-12-26.diff)
patch -p1 < v4l-dvb-hg-2007-12-26.diff
make menuconfig
make
sudo make install

3. Reboot

4. Go here [http://joshyfun.peque.org/transponders/kaffeine.html](http://joshyfun.peque.org/transponders/kaffeine.html)
And download the transponderfile for the sattelite you are scanning.
I scanned Astra and renamed the file I downloaded to just astra

5. Enter a console and type the following:

dmesg | grep dvb

You should se at least one line with cx24116 wich is the HVR4000 card.
If not (like I did, continue)

6. Still in the console, type the following:

sudo apt-get install dvb-utils

This will install the scan tool needed.

7. Scan for channels. In console just replace astra with the name of your transponderfile  you downloaded earlier.

scan astra >channels.conf

(At this point I got only timeouts and 0 channels)
(By typing dmesg | grep dvb again I got a loong list with cx24116 waiting for fw)

8. I got a script from Darron that I included.
Type the following:

sh wget_fw

What the script does, is download a zip file and extract the correct fw file for cx24116.
Type:

sudo nautilus

And copy the file called dvb-fe-cx24116.fw to /lib/firmware and reboot.

Retry step 7 after the reboot and for me it scanned astra and filled my channels.conf. So now I now the card works and I have a channels.conf to use in MythTV,,, Just need to leard how to setup MythTV...

---

### Post by Cirion75 on 2007-12-27
Double post...

---

### Post by Menthol on 2007-12-27
Excellent work :-)

Can't wait to try it when I get home from work.

Congratulations, I'll post my results as soon as I've tried

---

### Post by Menthol on 2007-12-27
Still doesn't work for me :(
when I type dmesg | grep dvb I get this:


[   47.624956] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   47.624961] cx88/2: registering cx8802 driver, type: dvb access: shared
[   47.853016] cx88[0]/2: dvb_register failed (err = -1)

and then errors when I try to scan:

scanning astra
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory

I just noticed your other posts and saw that you're using Linux MCE, it maby that it wont work on 64bit gutsy which is what I'm using


 :sad:oh well, it was worth a try ](*,)

---

### Post by Cirion75 on 2007-12-27
It might be 64bit yes... You could try installing a 32bit os in a second partition or HD.

In LinuxMCE, I'm not able to make the card work in MythTV, that crappy software is not made to handle this many channels... I use a Diseqc rotor with my dish, and have access to 23 sattelites with over 6000 unique channels. I could use just 1 sattelite and spend hours setting up the xml epg, but that would not be enough for me.

I have found that Kaffeine, supports our card without any setup.... Well at least of the program. It works just like any Windows based DVB software, Once the driver was installed it detected the card by itself. I just had to insert a LNB - > Rotor -> Usals and start scanning all my sattelites :) (In linuxmce I had to stop the mythtvbackend before kaffeine was allowed to access the card.)

---

### Post by Menthol on 2007-12-28
Interesting, I've had nothing but trouble with Kaffeine. It wont even look at tha analogue part of my card which does work (with no sound) on some of the other programs.  I dont even get any functions in Kaffeine for scanning or anything (presumably because its not detecting anything)

Not much point in me having a 32bit partition just for the TV card, may as well keep the windows partition for now and just use it on there.

Whats annoying though is there are people who say they have the thing working in 64bit, but how I dont know !

Did you do anything to the make menuconfig when it loaded, as in change any of the options ?

---

### Post by Cirion75 on 2007-12-28
No, I did not run make menuconfig, just make and then sudo make install.

As soon as LinuxMCE 0710 is released I'll be in the same boat... 0710 will be available in 64bit... I just have to try that... Never got the HVR400 to run in Winsta64bit after the release. It worked in the release candidates.

As for kaffeine and analog.. I'm not using my card for analog. I have a Hauppauge PVR USB2 for that. But MythTV is so buggy in LinuxMCE that it really is not usable at all. I bought my HVR4000 for it's digital side which rock!

0710 will also include VDR, and I'll start using that as soon as it's ready. Plugin support is better on VDR than Kaffeine.

As for windows, I still have my windows partition to use my card, but that is going to change as soon as I get CS up and running in Kaffeine.

In case you are wondering what I use in windows, I'm running WinXP with DVBViewer. I have a Nvidia GF 8600GT and use Cyberlink PowerDVD Ultra codec. That combo uses 0% Cpu on unencrypted HD channels like AstraHD, and 2-12% Cpu on encrypted HD channels.

---

### Post by Menthol on 2007-12-28
Thanks for the info.  I dont really need analogue either, I bought the card for the HD-TV Sat side.  BBC HD looks amazing hooked up to an optoma HD70 projector, I've got 80inches of HD goodness :-D

I'm using 32bit XP which does explain why it works in windows.  
I wasnt all that keen on MCE, it looked a bit messy when I installed it a while back.  I'm just using Mythbuntu at the moment, but still not sure about MythTV.

MediaPortal in windows which is open-source is an amazing media center, with tons of really usefull plugins like the TV series plug in, it has great functionality and looks nice.  
I guess its just a matter of giving linux more time with the media stuff.

I'm still not giving up on getting the card to work though.  I'll keep trying and post if I get anywhere !

---

### Post by Menthol on 2007-12-29
Good news, I've got the card to work !!!! :)

It is because of 64bit.  I installed 32bit Mythbuntu on a seperate partition and installed using the previous commands, same as I did with 64bit.  
It's the fw file I think.  The windows driver .sys file it converts it from is 32bit I think, which would explain alot.  As far as I can tell Hauppauge havent written a 64bit driver for windows so its not surprising it wont work in 64bit linux.

The card runs fine and scans in kaffeine on 32bit.

---

### Post by Cirion75 on 2007-12-29
I think you are right. It should only be the firmware if you get no other errors.
And you are in luck too...

I found a newer driver package with 64bit firmware :)
[http://www.wintvcd.co.uk/drivers/88x_2_121_25351_WHQL.zip](http://www.wintvcd.co.uk/drivers/88x_2_121_25351_WHQL.zip)

This was the old package where the script got it's firmware
[ftp://167.206.143.11/outgoing/Oxford/88x_2_119_25023_WHQL.zip](ftp://167.206.143.11/outgoing/Oxford/88x_2_119_25023_WHQL.zip)

The new file contains both 32bit and 64bit firmwares.

Try this:

wget [http://www.wintvcd.co.uk/drivers/88x_2_121_25351_WHQL.zip](http://www.wintvcd.co.uk/drivers/88x_2_121_25351_WHQL.zip)
unzip -jo 88x_2_121_25351_WHQL.zip Driver88/64bit/hcw88bda.sys
dd if=hcw88bda.sys of=/lib/firwmare/dvb-fe-cx24116.fw skip=81768 bs=1 count=32522

That should create a 64bit firmware for you :)

---

### Post by Menthol on 2007-12-29
Excellent, well found :KS

I still get the error with it in 64bit with the 64bit firmware at the moment, but it may be because my 64bit has got very messy now.  I tried to make install some newer v4l drivers and it went completely nuts during the install.
I'm going to quickly reinstall 64bit again now and try it with a clean install.

Good going, now the 64bit firmware is out its only a matter of time :)

Thanks again, I'll post an update as soon as I have one

---

### Post by Menthol on 2007-12-29
Got even further with 64bit !!

I reinstalled my ubuntu 64bit and installed the v4l drivers, patched and put in the 64bit fw.
This time grep read everything as ok !!
Kaffeine comes up with the scanning options and all seems well, however the machine then freezes, unfreezes, freezes every few seconds and terminal says it can not determine type of stream.
This may be because I need to install all the restricted extras which I'm doing now.

I'll edit this post with an update as soon as I have one

Edit: update, success in 64bit !!!!!! ....... with the 32bit driver :confused:

I kept getting the freezes, so I tried copying over the 32bit driver again, and it worked. How I dont know, why I dont know but its working fully in kaffeine on my 64bit system using the 32bit fw in lib/firmware.

Many thanks to Cirion75, I would have given up ages ago if it wasnt for your informative posts.

Kaffeine has now scanned everything and works fantastically :-D

---

### Post by Cirion75 on 2007-12-29
Great news!

If kaffeine is not for you, you probably prefer a more remote friendly program like MythTV. For me MythTV is made to well for analog pvr and it requires a DVB setup that works the same way as a analog pvr card...

I had the same problem with a program called Tvedia in windows. It's really a great PVR software and had a nice HTPC gui. This GUI was also available for Xcard which is what I used to get RGB Scart on my TV. For older SD TV's there is nothing better. When DVB was introduced, it was introduced in the same manner analog cards worked. So it was a horrible manual job setting up channel for channel. Mostly because it needed a XML EPG to be able to zap. Since I do not use just one provider on one satellite, things got complicated. I feel I have to do the same in MythTV....

LinuxMCE (Based on Plutohome) has had MythTV integrated for many years (LinuxMCE is not that old, but Plutohome is) and both have started to go another direction with DVB. The program they are working on now, is called VDR.

This is from the LinuxMCE site: 	
26 Oct 2007
Version 0710 is coming
 
The upcoming release is due by the end of November and will be based on the new Kubuntu 07.10. What's new is:

1. Both a 32 and 64 bit version
2. Support for HD-DVD and Blu-Ray playback, as well as integration with MPlayer
3. 1080p on the nVidia graphics platform
4. Better integration with MythTV
5. The inclusion of VDR, popular with the European Satellite users
6. Naturally lots of bug fixes and tweaks

0710 was never released in November but they managed to release a second Beta before christmas (without DVR). I think release will be sometime in January.

If you want to take a look at VDR, understand this. VDR was made for Premium Cards and had no support for output on VGA cards. This is what you will find if you google it.

But there is a driver wich makes any DVB card wich runs in linux with the v4l driver output to Xine which again lets you output on your VGA card on whatever port you like.

Here is a video with VDR in action:
[http://www.youtube.com/watch?v=_NYIrMsOh2A](http://www.youtube.com/watch?v=_NYIrMsOh2A)

And here you find Xine and VDR for Xine:
[http://home2.vr-web.de/~rnissl/](http://home2.vr-web.de/~rnissl/)
[http://xinehq.de/](http://xinehq.de/)

I'm waiting for the VDR beta for LinuxMCE 0710. And as soon as a 64bit version is released I'll try to get everything up and running there.

---

### Post by Menthol on 2007-12-29
It does all look very promising. Kaffeine happily seems to work now, apart from BBC HD which for some reason is audio only, I probably need the HD codec the BBC broadcasts in or something.

I'll definetly keep a close eye on MCE and all the add-ons for it.  Now I have the card working theres no reason at all for me to go back into windows :)

---

### Post by lukstei on 2008-01-11
> **Cirion75 said:**
> 
8. I got a script from Darron that I included.
Type the following:

sh wget_fw

What the script does, is download a zip file and extract the correct fw file for cx24116.


hi, i'm also try to get my hvr4000 running..
im at the point where he requests the firmware but i can't find anywhere this script 'wget_fw' 
can you please give me a link where i can download it?
thanks

---

### Post by Menthol on 2008-01-12
> **lukstei said:**
> hi, i'm also try to get my hvr4000 running..
im at the point where he requests the firmware but i can't find anywhere this script 'wget_fw' 
can you please give me a link where i can download it?
thanks

Hello,

The easiest thing for you to do is to download this file here: 
[http://www.wintvcd.co.uk/drivers/88x_2_121_25351_WHQL.zip](http://www.wintvcd.co.uk/drivers/88x_2_121_25351_WHQL.zip)

and then copy the file hcw88bda.sys from the zip file into a directory (I just make a tmp directory)

Open a terminal and go to the tmp directory and do 


dd if=hcw88bda.sys of=/lib/firwmare/dvb-fe-cx24116.fw skip=81768 bs=1 count=32522

This will create the .fw file.  Then just copy the .fw file into /lib/firmware (you'll need to do this as root)

Thats all the script does.

Good luck :)

---

### Post by aphex79 on 2008-01-12
im also is trying to get this to work.. but i cannot find any dvb-fe-cx24116.fw file in my firmware folder.. there is only a folder 2.6.22-14generic folder .. and in that folder there is no .fw file with that name.. ?

---

### Post by Menthol on 2008-01-12
> **aphex79 said:**
> im also is trying to get this to work.. but i cannot find any dvb-fe-cx24116.fw file in my firmware folder.. there is only a folder 2.6.22-14generic folder .. and in that folder there is no .fw file with that name.. ?

You make the dvb-fe-cx24116.fw file using the commands I posted above. It creates the file, you then copy it to your firmware folder.

---

### Post by aphex79 on 2008-01-12
aha.. but i got a error, but when i removed the path(lib/firwmare/) i got it to work.. then i copied the file.. now i just have to test it:D thanks

---

### Post by aphex79 on 2008-01-12
i tried scanning channels with kaffeine, and i think its scanning.. but ubuntu crashes half way through.. it seems to crash a lot.. when i try to scan with the terminal window, i get this error: tune_to_transponder:1483: ERROR: Setting frontend parameters failed: 22 Invalid argument. 
any clue? i did all you have written.. but no luck.. what ubuntu are you using, desktop, or server? all i can think of doing wrong, is the make menuconfig.. i got a lot of error messages there... ?

---

### Post by Menthol on 2008-01-12
What do you get when you type 

dmesg | grep dvb 

It could be you've converted the 64bit version of the .sys file. There are 2 versions in the oxford88 zip file, make sure you extract the correct one before converting it to the .fw file

Then manually copy it over to your /lib/firmware directory (sudo nautilus) to do this.

I have it running in 64bit gutsy and 32bit gutsy fine.
It currently wont run in Hardy Herron

---

### Post by Menthol on 2008-01-12
In summery:

[PHP] hg clone http://linuxtv.org/hg/v4l-dvb [/PHP]

This downloads the latest V4L drivers.

[PHP] cd v4l-dvb [/PHP]

Takes you to the V4L directory

Go here:  [http://dev.kewl.org/hauppauge/](http://dev.kewl.org/hauppauge/)

and right click, download this file : v4l-dvb-hg-2007-12-26.diff  

Copy it into your V4L directory then

[PHP] patch -p1 < v4l-dvb-hg-2007-12-26.diff [/PHP]

That patches the driver. Then

[PHP] Make [/PHP]

Compiles the driver, then

[PHP] Sudo make install [/PHP]

Installs the driver.

Download the Oxford88 file and unpack this: hcw88bda.sys from the driver88 directory

Go to the directory you downloaded it to in Terminal or your command editor and type

[PHP] sudo dd if=hcw88bda.sys of=/lib/firmware/dvb-fe-cx24116.fw skip=81768 bs=1 count=32522 [/PHP]

This converts the .sys file into a .fw file and copies it to your lib/firmware directory

REBOOT

Install Kaffeine and scan away :)

---

### Post by aphex79 on 2008-01-13
[   26.100000] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   26.100000] cx88/2: registering cx8802 driver, type: dvb access: shared

i only get this now.. but yesterday it was lots of more text.. i converted the 32bit version.. (my machine is 64bit, but i have 32bit ubuntu, could that be it?)

---

### Post by aphex79 on 2008-01-13
now i tried installing ubuntu fresh.. but now i get a error when i do make.. when i try to do sudo make install, it wont start either.. almost giving up here.. :confused:

---

### Post by Menthol on 2008-01-13
Thats how I felt for a while, but I got it in the end:)

Thats how you're output file should have read !! You had it :-D

You just need to install some stuff in synaptic. Install the Linux-headers and the make commands should work..

If you read back a bit through this thread I think you're stumbling on alot of the problems I encountered. In the end I managed to get the 32bit file working on the 64bit machine. The 64bit file didnt work properly.
By all means give the 64bit file a go though, it cant hurt to try things out

---

### Post by aphex79 on 2008-01-13
which linux header should i install.. there are plenty..  ?

---

### Post by Menthol on 2008-01-13
Just install them all, thats what I did :)
If you dont have room then just try the one for your kernel, which is the one that has a directory in your lib/firmware

---

### Post by aidan_curtis on 2008-03-09
hi there having problems Hvr 4000 looking for help
I was hopeing you might be able to help
I am trying to get a hvr 4000 working on xubuntu 7.10 kernel version 2.6.22-14-generic
and have done as follows
 
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
patch -p1 < v4l-dvb-hg-sfe-latest.diff
 
then i fixed a couple of lines that the diff didnt apply by hand in cx88.h af follows
 
*************** extern struct sram_channel cx88_sram_cha
*** 220,225 ****
  #define CX88_BOARD_POWERCOLOR_REAL_ANGEL   62
  #define CX88_BOARD_GENIATECH_X8000_MT      63
  #define CX88_BOARD_DVICO_FUSIONHDTV_DVB_T_PRO 64
  
  enum cx88_itype {
  	CX88_VMUX_COMPOSITE1 = 1,
--- 220,227 ----
  #define CX88_BOARD_POWERCOLOR_REAL_ANGEL   62
  #define CX88_BOARD_GENIATECH_X8000_MT      63
  #define CX88_BOARD_DVICO_FUSIONHDTV_DVB_T_PRO 64
+ #define CX88_BOARD_HAUPPAUGE_HVR4000       65
+ #define CX88_BOARD_HAUPPAUGE_HVR4000LITE   66
  
  enum cx88_itype {
  	CX88_VMUX_COMPOSITE1 = 1,
 
then a make and sudo make install
the software seemed to install 
I  got the firmware
88x_2_121_25351_WHQL.zip
 
extracted the files and
done the following
 
 dd if=hcw88bda.sys of=dvb-fe-cx24116.fw skip=81768 bs=1 count=32522
 
the resultant file (dvb-fe-cx24116.fw ) i put into /lib/firmware
reboot
and tried 
scan /usr/share/doc/dvb-utils/examples/scan/dvb-s/Astra-28.2E> ./.szap/channels.conf
 
when i do so i get the following
 
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-s/Astra-28.2E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 10773000 H 22000000 5
>>> tune to: 10773:h:0:22000
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
dumping lists (0 services)
Done.
 
the firmware does not appear to load look at the end of the dmesg output 
any help would be much appreiceated as I'm kinda new to this
Thanks
Aidan
 
dmesg gives the following
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bef0000 (usable)
[    0.000000]  BIOS-e820: 000000003bef0000 - 000000003bef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bef3000 - 000000003bf00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 62MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f51e0
[    0.000000] Entering add_active_range(0, 0, 245488) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   245488
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   245488
[    0.000000] On node 0 totalpages: 245488
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 125 pages used for memmap
[    0.000000]   HighMem zone: 15987 pages, LIFO batch:3
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F92A0 checksum 0
[    0.000000] ACPI: RSDP 000F92A0, 0014 (r0 CX700 )
[    0.000000] ACPI: RSDT 3BEF3040, 0030 (r1 CX700  AWRDACPI 30302E32 AWRD        0)
[    0.000000] ACPI: FACP 3BEF30C0, 0084 (r2 CX700  AWRDACPI 30302E32 AWRD        0)
[    0.000000] ACPI: DSDT 3BEF31C0, 3D9A (r1 CX700  AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 3BEF0000, 0040
[    0.000000] ACPI: MCFG 3BEF7080, 003C (r1 CX700  AWRDACPI 30302E32 AWRD        0)
[    0.000000] ACPI: APIC 3BEF6FC0, 005A (r1 CX700  AWRDACPI 30302E32 AWRD        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:10 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3bf00000:a4100000)
[    0.000000] Built 1 zonelists.  Total pages: 243571
[    0.000000] Kernel command line: root=UUID=a8eb65cd-c6a0-4242-9883-8db874e7bf78 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 999.997 MHz processor.
[   14.777018] Console: colour VGA+ 80x25
[   14.777779] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   14.779291] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   14.853236] Memory: 961928k/981952k available (2015k kernel code, 19408k reserved, 915k data, 364k init, 64448k highmem)
[   14.853270] virtual kernel memory layout:
[   14.853274]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   14.853279]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   14.853284]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   14.853288]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   14.853293]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   14.853298]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   14.853303]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   14.853314] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.853419] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   14.933459] Calibrating delay using timer specific routine.. 2001.65 BogoMIPS (lpj=4003314)
[   14.933521] Security Framework v1.0.0 initialized
[   14.933534] SELinux:  Disabled at boot.
[   14.933583] Mount-cache hash table entries: 512
[   14.933814] CPU: After generic identify, caps: 87c9baff 00000000 00000000 00000000 00000081 00000000 00000000
[   14.933838] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   14.933847] CPU: L2 Cache: 128K (64 bytes/line)
[   14.933854] CPU: After all inits, caps: 07c9baff 00000000 00000000 00000000 00000081 00003fcc 00000000
[   14.933878] Compat vDSO mapped to ffffe000.
[   14.933903] Checking 'hlt' instruction... OK.
[   14.949763] SMP alternatives: switching to UP code
[   14.950236] Freeing SMP alternatives: 11k freed
[   14.950974] Early unpacking initramfs... done
[   16.038665] ACPI: Core revision 20070126
[   16.038812] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.045767] CPU0: Centaur VIA Esther processor 1000MHz stepping 09
[   16.045821] Total of 1 processors activated (2001.65 BogoMIPS).
[   16.046014] ENABLING IO-APIC IRQs
[   16.046238] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   16.193660] Brought up 1 CPUs
[   16.193887] Booting paravirtualized kernel on bare hardware
[   16.194002] Time: 13:43:30  Date: 02/09/108
[   16.194048] NET: Registered protocol family 16
[   16.194217] EISA bus registered
[   16.194238] ACPI: bus type pci registered
[   16.200855] PCI: PCI BIOS revision 3.00 entry at 0xfae70, last bus=3
[   16.200863] PCI: Using configuration type 1
[   16.200870] Setting up standard PCI resources
[   16.210961] ACPI: EC: Look up EC in DSDT
[   16.222543] ACPI: Interpreter enabled
[   16.222551] ACPI: (supports S0 S1 S3 S4 S5)
[   16.222595] ACPI: Using IOAPIC for interrupt routing
[   16.233240] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.233266] PCI: Probing PCI hardware (bus 00)
[   16.234692] PCI: Transparent bridge - 0000:00:13.1
[   16.234741] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.235317] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2PE._PRT]
[   16.235611] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2PB._PRT]
[   16.284609] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[   16.285039] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 11 12) *5
[   16.285474] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12)
[   16.285934] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 6 7 10 11 12)
[   16.286309] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   16.286670] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   16.287031] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   16.287391] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   16.287625] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.287649] pnp: PnP ACPI init
[   16.287672] ACPI: bus type pnp registered
[   16.292519] pnp: PnP ACPI: found 10 devices
[   16.292527] ACPI: ACPI bus type pnp unregistered
[   16.292538] PnPBIOS: Disabled by ACPI PNP
[   16.292653] PCI: Using ACPI for IRQ routing
[   16.292662] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.318971] NET: Registered protocol family 8
[   16.318978] NET: Registered protocol family 20
[   16.319108] pnp: 00:01: ioport range 0x400-0x47f has been reserved
[   16.319118] pnp: 00:01: ioport range 0x500-0x50f has been reserved
[   16.319136] pnp: 00:02: iomem range 0xf0000000-0xf0000fff has been reserved
[   16.319164] pnp: 00:08: iomem range 0xe0000000-0xefffffff could not be reserved
[   16.319179] pnp: 00:09: iomem range 0xd0000-0xd3fff has been reserved
[   16.319189] pnp: 00:09: iomem range 0xda000-0xdbfff has been reserved
[   16.319200] pnp: 00:09: iomem range 0xf0000-0xfbfff could not be reserved
[   16.319210] pnp: 00:09: iomem range 0xfc000-0xfffff could not be reserved
[   16.321608] Time: tsc clocksource has been installed.
[   16.349802] PCI: Bridge: 0000:00:01.0
[   16.349809]   IO window: e000-efff
[   16.349820]   MEM window: d8000000-d9ffffff
[   16.349829]   PREFETCH window: a0000000-bfffffff
[   16.349839] PCI: Bridge: 0000:00:13.0
[   16.349846]   IO window: d000-dfff
[   16.349855]   MEM window: dfe00000-dfefffff
[   16.349864]   PREFETCH window: dfd00000-dfdfffff
[   16.349877] PCI: Bridge: 0000:00:13.1
[   16.349883]   IO window: c000-cfff
[   16.349893]   MEM window: da000000-deffffff
[   16.349902]   PREFETCH window: dfc00000-dfcfffff
[   16.349924] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   16.349938] PCI: Setting latency timer of device 0000:00:13.0 to 64
[   16.349951] PCI: Setting latency timer of device 0000:00:13.1 to 64
[   16.349999] NET: Registered protocol family 2
[   16.389696] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.389913] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   16.393506] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   16.394701] TCP: Hash tables configured (established 131072 bind 65536)
[   16.394711] TCP reno registered
[   16.405931] checking if image is initramfs...Switched to high resolution mode on CPU 0
[   17.439430]  it is
[   18.540147] Freeing initrd memory: 7055k freed
[   18.540683] audit: initializing netlink socket (disabled)
[   18.540707] audit(1205070211.364:1): initialized
[   18.540864] highmem bounce pool size: 64 pages
[   18.545648] VFS: Disk quotas dquot_6.5.1
[   18.545782] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.545988] io scheduler noop registered
[   18.545995] io scheduler anticipatory registered
[   18.546001] io scheduler deadline registered
[   18.546056] io scheduler cfq registered (default)
[   18.546088] PCI: VIA PCI bridge detected. Disabling DAC.
[   18.546165] Boot video device is 0000:01:00.0
[   18.546501] isapnp: Scanning for PnP cards...
[   18.900598] isapnp: No Plug & Play device found
[   18.973316] Real Time Clock Driver v1.12ac
[   18.973549] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.976126] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.976593] input: Macintosh mouse button emulation as /class/input/input0
[   18.976821] PNP: No PS/2 controller found. Probing ports directly.
[   18.977380] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.977393] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.977798] mice: PS/2 mouse device common for all mice
[   18.978023] EISA: Probing bus 0 at eisa.0
[   18.978080] EISA: Detected 0 cards.
[   18.978542] TCP cubic registered
[   18.978579] NET: Registered protocol family 1
[   18.978639] Using IPI No-Shortcut mode
[   18.979047]   Magic number: 0:718:735
[   18.979856] Freeing unused kernel memory: 364k freed
[   20.651358] AppArmor: AppArmor initializedaudit(1205070213.364:2):  type=1505 info="AppArmor initialized" pid=1120
[   20.669923] fuse init (API version 7.8)
[   20.683883] Failure registering capabilities with primary security module.
[   22.505095] SCSI subsystem initialized
[   22.519327] libata version 2.21 loaded.
[   22.537155] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   22.537167] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   22.538612] VP_IDE: IDE controller at PCI slot 0000:00:0f.0
[   22.538647] VP_IDE: chipset revision 0
[   22.538653] VP_IDE: not 100% native mode: will probe irqs later
[   22.538670] VP_IDE: VIA cx700 (rev 00) IDE UDMA133 controller on pci0000:00:0f.0
[   22.538684]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[   22.538705]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:pio, hdd:DMA
[   22.538722] Probing IDE interface ide0...
[   22.629775] usbcore: registered new interface driver usbfs
[   22.629831] usbcore: registered new interface driver hub
[   22.629875] usbcore: registered new device driver usb
[   22.632198] USB Universal Host Controller Interface driver v3.0
[   22.989234] hda: WDC WD5000AAKS-00YGA0, ATA DISK drive
[   23.325356] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   23.329133] Probing IDE interface ide1...
[   23.367432] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   23.367447] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[   24.473160] hdd: Optiarc DVD RW AD-7630A, ATAPI CD/DVD-ROM drive
[   24.534732] ide1 at 0x170-0x177,0x376 on irq 15
[   24.539263] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 20 (level, low) -> IRQ 16
[   24.539288] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   24.539947] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   24.539994] uhci_hcd 0000:00:10.0: irq 16, io base 0x0000f800
[   24.541018] usb usb1: configuration #1 chosen from 1 choice
[   24.541435] hub 1-0:1.0: USB hub found
[   24.541457] hub 1-0:1.0: 2 ports detected
[   24.562675] hda: max request size: 512KiB
[   24.587758] hda: 976773168 sectors (500107 MB) w/16384KiB Cache, CHS=60801/255/63, UDMA(33)
[   24.590191] hda: cache flushes supported
[   24.590276]  hda: hda1 hda2 < hda5>
[   24.645342] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 22 (level, low) -> IRQ 17
[   24.645365] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   24.645422] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   24.645460] uhci_hcd 0000:00:10.1: irq 17, io base 0x0000f400
[   24.645697] usb usb2: configuration #1 chosen from 1 choice
[   24.645759] hub 2-0:1.0: USB hub found
[   24.645784] hub 2-0:1.0: 2 ports detected
[   24.689414] hdd: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   24.689436] Uniform CD-ROM driver Revision: 3.20
[   24.749312] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 18
[   24.749335] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   24.749389] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   24.749428] uhci_hcd 0000:00:10.2: irq 18, io base 0x0000f000
[   24.749662] usb usb3: configuration #1 chosen from 1 choice
[   24.749727] hub 3-0:1.0: USB hub found
[   24.749742] hub 3-0:1.0: 2 ports detected
[   24.853572] ACPI: PCI Interrupt 0000:00:10.4[D] -> GSI 23 (level, low) -> IRQ 19
[   24.853600] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   24.853659] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 4
[   24.853721] ehci_hcd 0000:00:10.4: debug port 1
[   24.853749] ehci_hcd 0000:00:10.4: irq 19, io mem 0xdffff000
[   24.853762] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.853959] usb usb4: configuration #1 chosen from 1 choice
[   24.854029] hub 4-0:1.0: USB hub found
[   24.854045] hub 4-0:1.0: 6 ports detected
[   24.957507] ACPI: PCI Interrupt 0000:03:08.0[A] -> GSI 18 (level, low) -> IRQ 20
[   24.962911] eth0: VIA Rhine III at 0x1cc00, 00:40:63:ee:53:03, IRQ 20.
[   24.963636] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[   24.963855] ACPI: PCI Interrupt 0000:03:09.0[A] -> GSI 19 (level, low) -> IRQ 21
[   25.017757] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[deffe000-deffe7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   25.259054] Attempting manual resume
[   25.259063] swsusp: Resume From Partition 3:5
[   25.259070] PM: Checking swsusp image.
[   25.259266] PM: Resume from disk failed.
[   25.329631] kjournald starting.  Commit interval 5 seconds
[   25.329654] EXT3-fs: mounted filesystem with ordered data mode.
[   26.069011] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   26.243782] usb 2-1: configuration #1 chosen from 1 choice
[   26.293160] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[004063500009a7f9]
[   26.500973] usb 2-2: new low speed USB device using uhci_hcd and address 3
[   26.655803] usb 2-2: configuration #1 chosen from 1 choice
[   35.354474] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   35.357972] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   35.597735] Linux agpgart interface v0.102 (c) Dave Jones
[   35.618672] agpgart: Detected VIA CX700 chipset
[   35.627046] agpgart: AGP aperture is 128M @ 0xd0000000
[   37.587314] Linux video capture interface: v2.00
[   37.650206] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   37.650327] ACPI: PCI Interrupt 0000:03:0f.0[A] -> GSI 17 (level, low) -> IRQ 22
[   37.650480] cx88[0]: subsystem: 0070:6902, board: Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid [card=66,autodetected]
[   37.650491] cx88[0]: TV tuner type 63, Radio tuner type -1
[   37.768419] cx88[0]: i2c init: enabling analog demod on HVR1300/3000/4000 tuner
[   38.512805] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   38.538652] [drm] Initialized drm 1.0.0 20040925
[   38.549823] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 23
[   38.549943] [drm] Initialized via 2.6.3 20050523 on minor 0: 
[   38.562989] via_v4l_drv: no version for "via_fb_free" found: kernel tainted.
[   38.563260] via_v4l_drv: disagrees about version of symbol video_devdata
[   38.563268] via_v4l_drv: Unknown symbol video_devdata
[   38.563479] via_v4l_drv: disagrees about version of symbol video_unregister_device
[   38.563487] via_v4l_drv: Unknown symbol video_unregister_device
[   38.563596] via_v4l_drv: disagrees about version of symbol video_register_device
[   38.563604] via_v4l_drv: Unknown symbol video_register_device
[   39.344346] input: PC Speaker as /class/input/input1
[   40.123476] usbcore: registered new interface driver hiddev
[   40.138837] input: Dell Dell USB Keyboard as /class/input/input2
[   40.138926] input: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:10.1-1
[   40.151671] input: HID 413c:3010 as /class/input/input3
[   40.151810] input: USB HID v1.00 Mouse [HID 413c:3010] on usb-0000:00:10.1-2
[   40.151841] usbcore: registered new interface driver usbhid
[   40.151852] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   40.300069] tuner' 1-0043: chip found @ 0x86 (cx88[0])
[   40.300081] tda9887 1-0043: tda988[5/6/7] found
[   40.869226] cx2388x alsa driver version 0.0.6 loaded
[   41.260729] tuner' 1-0061: chip found @ 0xc2 (cx88[0])
[   41.263282] tuner-simple 1-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[   41.265689] tuner' 1-0063: chip found @ 0xc6 (cx88[0])
[   41.310235] tveeprom 1-0050: Hauppauge model 69009, rev B2D3, serial# 3165793
[   41.310249] tveeprom 1-0050: MAC address is 00-0D-FE-30-4E-61
[   41.310258] tveeprom 1-0050: tuner model is Philips FMD1216MEX (idx 133, type 63)
[   41.310270] tveeprom 1-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[   41.310282] tveeprom 1-0050: audio processor is CX882 (idx 33)
[   41.310291] tveeprom 1-0050: decoder processor is CX882 (idx 25)
[   41.310300] tveeprom 1-0050: has radio, has IR receiver, has no IR transmitter
[   41.310309] cx88[0]: hauppauge eeprom: model=69009
[   41.310575] input: cx88 IR (Hauppauge WinTV-HVR400 as /class/input/input4
[   41.310659] cx88[0]/0: found at 0000:03:0f.0, rev: 5, irq: 22, latency: 32, mmio: 0xdd000000
[   41.310773] cx88[0]/0: registered device video0 [v4l2]
[   41.310853] cx88[0]/0: registered device vbi0
[   41.310921] cx88[0]/0: registered device radio0
[   41.312767] cx88[0]/2: cx2388x 8802 Driver Manager
[   41.312797] ACPI: PCI Interrupt 0000:03:0f.2[A] -> GSI 17 (level, low) -> IRQ 22
[   41.312816] cx88[0]/2: found at 0000:03:0f.2, rev: 5, irq: 22, latency: 32, mmio: 0xdb000000
[   41.313876] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 17 (level, low) -> IRQ 22
[   41.313922] PCI: Setting latency timer of device 0000:02:01.0 to 64
[   41.399422] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   41.399434] cx88/2: registering cx8802 driver, type: dvb access: shared
[   41.399446] cx88[0]/2: subsystem: 0070:6902, board: Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid [card=66]
[   41.399457] cx88[0]/2: cx2388x based DVB/ATSC card
[   41.565847] DVB: registering new adapter (cx88[0])
[   41.565860] DVB: registering frontend 0 (Conexant CX24116/CX24118)...
[   41.600706] ACPI: PCI Interrupt 0000:03:0f.1[A] -> GSI 17 (level, low) -> IRQ 22
[   41.600759] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   42.357425] lp: driver loaded but no devices found
[   42.980578] Adding 2835432k swap on /dev/hda5.  Priority:-1 extents:1 across:2835432k
[   43.619335] EXT3 FS on hda1, internal journal
[   45.995822] input: Power Button (FF) as /class/input/input5
[   45.996351] ACPI: Power Button (FF) [PWRF]
[   46.039821] input: Power Button (CM) as /class/input/input6
[   46.040362] ACPI: Power Button (CM) [PWRB]
[   46.063825] input: Sleep Button (CM) as /class/input/input7
[   46.064387] ACPI: Sleep Button (CM) [SLPB]
[   46.470533] No dock devices found.
[   49.271958] ppdev: user-space parallel port driver
[   49.808975] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   49.987171] audit(1205070243.753:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4586 profile="/usr/sbin/cupsd"
[   50.098129] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   50.098142] apm: overridden by ACPI.
[   50.498749] Failure registering capabilities with primary security module.
[   35.696000] Marking TSC unstable due to: cpufreq changes.
[   35.700000] Time: acpi_pm clocksource has been installed.
[   36.392000] Clocksource tsc unstable (delta = -75169481 ns)
[   39.128000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   39.128000] agpgart: Xorg tried to set rate=x12. Setting to AGP3 x8 mode.
[   39.128000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   39.128000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   40.060000] NET: Registered protocol family 17
[   45.172000] NET: Registered protocol family 10
[   45.172000] lo: Disabled Privacy Extensions
[   55.548000] eth0: no IPv6 routers present
[  119.624000] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[  119.664000] cx24116_firmware_ondemand: Waiting for firmware upload(2)...
[  125.372000] cx24116_cmd_execute() Firmware not responding
[  125.372000] cx24116_firmware_ondemand: Writing firmware to device failed
[  125.372000] cx24116_firmware_ondemand: Firmware upload failed
[  125.372000] cx24116_cmd_execute(): Unable initialise the firmware
[  125.940000] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[  125.948000] cx24116_firmware_ondemand: Waiting for firmware upload(2)...
[  131.656000] cx24116_cmd_execute() Firmware not responding
[  131.656000] cx24116_firmware_ondemand: Writing firmware to device failed
[  131.656000] cx24116_firmware_ondemand: Firmware upload failed
[  131.656000] cx24116_cmd_execute(): Unable initialise the firmware
[  131.660000] cx88[0]: irq mpeg  [0x100000] ts_err?*
[  131.660000] cx88[0]/2-mpeg: general errors: 0x00100000
[  148.412000] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[  148.416000] cx24116_firmware_ondemand: Waiting for firmware upload(2)...
[  154.120000] cx24116_cmd_execute() Firmware not responding
[  154.120000] cx24116_firmware_ondemand: Writing firmware to device failed
[  154.120000] cx24116_firmware_ondemand: Firmware upload failed
[  154.120000] cx24116_cmd_execute(): Unable initialise the firmware

---

### Post by Menthol on 2008-03-11
Hi,

It depends on which V4L drivers you've downloaded. Sometimes the latest has modifications in it that makes .Diff patch stop working.
 
All I can suggest at the moment is trying to get hold of an earlier version of V4L (theres stacks there with different dates) and patching one of those.
Alternatively there will probably soon be a new .diff file released that will properly patch the new V4L drivers again.


Hope that made sense :)  

I'd be interested to hear how you get on.

---

### Post by aidan_curtis on 2008-03-12
got it working 
turns out i had the wrong version of the drivers from which i was extracting the firmware
talked to Darron he pointed me in the right direction.
thanks

---

### Post by Menthol on 2008-03-16
Just tried installing the new .diff and its totally screwed up.  Doesnt work at all now, even after a fresh install.  Wheres the old .diff ?  the new ones dont work at all and the old one that did work has been removed :(

not happy

---

### Post by aphex79 on 2008-03-20
any progress?

---

### Post by Menthol on 2008-03-21
None I'm afraid.
Won't even patch the V4L drivers properly any more :(

patching file linux/drivers/media/dvb/frontends/Kconfig
patching file linux/drivers/media/dvb/frontends/Makefile
patching file linux/drivers/media/dvb/frontends/cx24116.c
patching file linux/drivers/media/dvb/frontends/cx24116.h
patching file linux/drivers/media/video/cx88/Kconfig
patching file linux/drivers/media/video/cx88/cx88-cards.c
Hunk #4 succeeded at 2046 (offset 43 lines).
Hunk #5 succeeded at 2149 (offset 51 lines).
Hunk #6 succeeded at 2482 with fuzz 2 (offset 91 lines).
Hunk #7 succeeded at 2548 (offset 105 lines).
patching file linux/drivers/media/video/cx88/cx88-dvb.c
Hunk #4 succeeded at 552 (offset 6 lines).
Hunk #5 succeeded at 797 (offset 6 lines).
Hunk #6 succeeded at 827 (offset 6 lines).
Hunk #7 succeeded at 962 (offset 5 lines).
Hunk #8 succeeded at 975 (offset 5 lines).
Hunk #9 succeeded at 1023 (offset 5 lines).
patching file linux/drivers/media/video/cx88/cx88-i2c.c
patching file linux/drivers/media/video/cx88/cx88-input.c
Hunk #2 succeeded at 411 (offset 7 lines).
Hunk #3 succeeded at 480 (offset 7 lines).
patching file linux/drivers/media/video/cx88/cx88.h
Hunk #1 FAILED at 220.
1 out of 1 hunk FAILED -- saving rejects to file linux/drivers/media/video/cx88/cx88.h.rej
patching file linux/drivers/media/video/ir-kbd-i2c.c
patching file linux/drivers/media/video/tveeprom.c
patching file linux/sound/pci/bt87x.c

And wont Make afterwards:
 
 
/home/user/v4l-dvb/v4l/cx88-cards.c:1438: error: 'CX88_BOARD_HAUPPAUGE_HVR4000' undeclared here (not in a function)
/home/user/v4l-dvb/v4l/cx88-cards.c:1438: error: array index in initializer not of integer type
/home/user/v4l-dvb/v4l/cx88-cards.c:1438: error: (near initialization for 'cx88_boards')
/home/user/v4l-dvb/v4l/cx88-cards.c:1491: error: 'CX88_BOARD_HAUPPAUGE_HVR4000LITE' undeclared here (not in a function)
/home/user/v4l-dvb/v4l/cx88-cards.c:1491: error: array index in initializer not of integer type
/home/user/v4l-dvb/v4l/cx88-cards.c:1491: error: (near initialization for 'cx88_boards')
make[3]: *** [/home/user/v4l-dvb/v4l/cx88-cards.o] Error 1
make[2]: *** [_module_/home/user/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-12-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/user/v4l-dvb/v4l'
make: *** [all] Error 2

---

### Post by green944 on 2008-03-21
edit linux/drivers/media/video/cx88/cx88.h

and add those lines

#define CX88_BOARD_HAUPPAUGE_HVR4000 67
#define CX88_BOARD_HAUPPAUGE_HVR4000LITE       68

just below

#define CX88_BOARD_DVICO_FUSIONHDTV_DVB_T_PRO 64
#define CX88_BOARD_DVICO_FUSIONHDTV_7_GOLD 65
#define CX88_BOARD_PROLINK_PV_8000GT       66


It looks another card made the official v4l-dvb release before the HVR 4000.

I just got the card yesterday and also trying to get it running under linux.

---

### Post by aidan_curtis on 2008-03-23
Ive built a box using a Via EX10000eg mother board and a hvr 4000 heres how 
1.  insert disk and boot pick default install option
2.  when Xserver fails type <CTRL>+<ALT>+<F4>
3.  at the $ prompt type startx<ENTER>
4.  follow the install proceedure
5.  Reboot
6.  when Xserver fails type <CTRL>+<ALT>+<F4>
7.  log in to the console using the username and password setup during the install
8.  at the $ prompt type startx<ENTER>
9.  do the system updates
10. reboot
11. when Xserver fails type <CTRL>+<ALT>+<F4>
12. log in to the console using the username and password setup during the install
13. at the $ prompt type startx<ENTER>
14. Add the restricted multivers and universe and backports and package lists to the distribution using Applications\System\Software Sources
15. run Applications\System\Update Manager, Install any updates
16. reboot.
17. when Xserver fails type <CTRL>+<ALT>+<F4>
18. log in to the console using the username and password setup during the install
19. at the $ prompt type startx<ENTER>
20. using Applications\System\Synaptic Package Manager add the libgl-mesa-dri package 
21. it might be wise to try removing xserver-xorg-video-via
22. sudo apt-get build-dep xserver-xorg-video-via
23. Create a directory src in your home directory
24. download and extract [http://www.viaarena.com/Driver/via_ubuntu710_unichrome-v40072d-kernel-bin-_v0.80.zip](http://www.viaarena.com/Driver/via_ubuntu710_unichrome-v40072d-kernel-bin-_v0.80.zip) to the src directory
25. open a terminal type cd src <ENTER>
26. type chmod 755 VIA_U710_UniChrome-GFX-v40072d.run <ENTER>
27. type sudo ./VIA_U710_UniChrome-GFX-v40072d.run <ENTER> and pick option 1.install
28  reboot and determine display resolution and set it using S3utility and Applications\Settings\Screens and Graplics
29. move the task list, show desktop and trash items from the pannel along the bottom of the screen to the panel at the top
30. remove everything else of the pannel bar along the bottom
31. change the number of workspaces to one using Applications\Settings\Workspace Settings
32. Set the pannel at the top of the screen to a width of 30 and set it's location to the bottom center of the screen using Applications\Settings\Panel Manager
33. reboot.
33a. using Applications\System\Software Sources remove backports
34. Install Filezilla,dvb-utils, rtorrent, mplayer, mplayer-doc, mplayer-fonts & mplayer-skins using using Applications\System\Synaptic Package Manager
35. sudo apt-get install mercurial.
36. hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
37. cd v4l-dvb
38. wget [http://dev.kewl.org/hauppauge/v4l-dvb-hg-sfe-latest.diff](http://dev.kewl.org/hauppauge/v4l-dvb-hg-sfe-latest.diff)
39. patch -p1 < v4l-dvb-hg-sfe-latest.diff
40. edit and fix any problems from previous act. look at the output you'll see which files didnt diff
41. make
42. sudo make install
43. wget [ftp://167.206.143.11/outgoing/Oxford/88x_2_119_25023_WHQL.zip](ftp://167.206.143.11/outgoing/Oxford/88x_2_119_25023_WHQL.zip)
44. decompress what's needed : "unzip -jo 88x_2_119_25023_WHQL.zip Driver88/hcw88bda.sys"
45. sudo dd if=hcw88bda.sys of=dvb-fe-cx24116.fw skip=81768 bs=1 count=32522
46. copy dvb-fe-cx24116.fw to /lib/firmware/2.6.22-14-generic
47. reboot
48. make sure that the xorg.conf is correct i.e. set keyboard to "ie" and Load	"dri" alernatively copy the xorg.conf from src.
49. to test tune mkdir .szap
50. scan /usr/share/doc/dvb-utils/examples/scan/dvb-s/Astra-28.2E > ./.szap/channels.conf
51. run mplayer
52  cp ./.szap/channels.conf ./.mplayer/channels.conf
53. mplayer dvb://UTV
54. firefox to [http://www.mythbuntu.org/existing-ubuntu](http://www.mythbuntu.org/existing-ubuntu)
55. click install mythbuntu and select install packages /select haugauge nova t 500 as the lirc
56. reboot
57. run Applications\System\Mythbuntu Control Centre
58. click system roles
59. setup as primary backend and as frontend
60. reboot
61. run Applications\System\Mythbuntu Control Centre
62. click mythtv configuration
63. launch mythtv setup
64. answer yes to adding user to mythtv group and restart 
65. run Applications\System\Mythbuntu Control Centre
66. click mythtv configuration
67. launch mythtv setup setup inputs do channel scans etc
68. reboot
69. [http://www.nabble.com/MythTV-won't-run-with-VIA-CX700M2-chipset-td15040477s15552.html](http://www.nabble.com/MythTV-won't-run-with-VIA-CX700M2-chipset-td15040477s15552.html)
70. sudo apt-get install build-essential
71. sudo apt-get build-dep mythtv
72. cd src
73. apt-get source mythtv
74. In libs/mythtv/vsync.cpp, comment out the following line in VideoSyn::BestMethod (line 95): //TESTVIDEOSYNC(DRMVideoSync);
75. In libs/mythtv/videoout_xv.cpp, uncomment line 67: #define USE_ATI_PROPRIETARY_DRIVER_XVIDEO_HACK
76. ./configure --enable-dvb --enable-proc-opt --prefix=/usr --enable-xvmc --enable-xvmc-pro --enable-xvmc-vld
77.  qmake mythtv.pro
78. make
79. sudo make install
80. Applications\System\run myth-setup and after that try to run the frontend and reboot
81. run Applications\System\Mythbuntu Control Centre
82. click system roles
83. remove as primary backend and as frontend
84. run Applications\System\Mythbuntu Control Centre
85. click system roles
86. setup as primary backend and as frontend
87. launch frontend
88. reboot if required and relaunch frontend
89. setup settings (notice lack of skins)
90. run Applications\System\Mythbuntu Control Centre
91. click applications & plugins add em all.
92. reboot
93. run Applications\System\Mythbuntu Control Centre
94. click proprietary codecs enable medibuntu proprietary codec support apply
95. it appears that the changes dont finish just run the update manager beside the clock when you get sick waiting.
96. reboot
97. run Applications\System\Mythbuntu Control Centre
98. click proprietary codecs all the available codecs
99. Install the mythtv-themes using Applications\System\Synaptic Package Manager do a search you'll find them.
100. reboot
101. rerun frontend and pick the right theme you will probably have to rerun it a couple of times
102. run Applications\System\Mythbuntu Control Centre
103. click system services enable mysql service and apply
104. click system services enable vnc service , set password and apply
105. click system services enable ssh services and apply
106. reboot
107. run Applications\System\Mythbuntu Control Centre
108. click artwork and login behavour, enable automatic login 
109. reboot 
110. you may  have to edit xorg.conf again.
111. there are are some problems with mythbuntu the links in /www/mythweb/data/ they are pointing to the wrong places fix as follows
112. cd /var/www/mythweb/data
113. sudo rm ./video_covers
114. sudo rm ./video
115. sudo ln -s /var/lib/mythtv/videos ./video
116. sudo ln -s /var/lib/mythtv/videos ./video_covers
117. cd /var/www/mythweb
118. sudo chown root:www-data ./data
119. sudo chmod +t /usr/share/mythtv/mythweb/data (thanks Gary Parker "http://www.parker1.co.uk/mythtv_0.20.php")
120. add www-data to the mythtv group in /etc/group.
120. Install Webmin its a damm good way of managing the box. (personal opinion)
121. the remote control needs some work  again one should have a look at [http://www.parker1.co.uk/mythtv_tips.php](http://www.parker1.co.uk/mythtv_tips.php)
122. use this to back up the disk [http://ping.windowsdream.com/](http://ping.windowsdream.com/)

Thanks to all at the ubuntu forums, lytke, Billdozer, Darron Broad, Menthol, Garry Parker, Eugene Gargan and lots of others
Hope this helps someone else.
Aidan

---

### Post by aphex79 on 2008-03-24
im getting,
/home/htpc/v4l-dvb/v4l/cx24116.c:205: error: unknown field 'parent' specified in initializer
/home/htpc/v4l-dvb/v4l/cx24116.c:218: error: unknown field 'parent' specified in initializer
/home/htpc/v4l-dvb/v4l/cx24116.c:231: error: unknown field 'parent' specified in initializer
/home/htpc/v4l-dvb/v4l/cx24116.c:244: error: unknown field 'parent' specified in initializer
/home/htpc/v4l-dvb/v4l/cx24116.c:257: error: unknown field 'parent' specified in initializer
/home/htpc/v4l-dvb/v4l/cx24116.c:273: error: unknown field 'parent' specified in initializer
/home/htpc/v4l-dvb/v4l/cx24116.c:289: error: unknown field 'parent' specified in initializer
/home/htpc/v4l-dvb/v4l/cx24116.c: In function 'cx24116_attach':
/home/htpc/v4l-dvb/v4l/cx24116.c:1210: error: too few arguments to function 'register_sysctl_table'
make[3]: *** [/home/htpc/v4l-dvb/v4l/cx24116.o] Error 1
make[2]: *** [_module_/home/htpc/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/htpc/v4l-dvb/v4l'
make: *** [all] Error 2

when i do make.. anyone?

aidan_curtis: what version of ubuntu are you using?

---

### Post by aidan_curtis on 2008-03-25
xubuntu ver 7.10 over instaled with mythbuntu

---

### Post by aphex79 on 2008-03-25
the fixes you mention in 40, is it the same that green944 mention? when i try to fix with that, i get an error, but if i remove the two last cards, and write in the two hauppauge cards, i get no error on the patch. further on the make, i get an error that the two cards i removed is missing.. any clues?

---

### Post by non-poster on 2008-03-26
I haven't read this entire thread.  It looks like there is some useful info here: [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000)

---

### Post by luria on 2008-03-27
> **Menthol said:**
> None I'm afraid.
Won't even patch the V4L drivers properly any more :(



Why don't you check out the v4l version that the patch was made against ?  

Go trough v4l changes and find the right version , then check it out with mercurials -v version switch.

---

### Post by Growlizing on 2008-03-27
Been trying to get this card to show me some tv, to no avail.

The modules seams to load fine, so does the firmware:
```
 dmesg | grep cx
cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
cx2388x alsa driver version 0.0.6 loaded
cx88[0]: subsystem: 0070:6902, board: Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid [card=66,autodetected]
cx88[0]: TV tuner type 63, Radio tuner type -1
cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
cx88[0]: i2c init: enabling analog demod on HVR1300/3000/4000 tuner
tuner' 0-0043: chip found @ 0x86 (cx88[0])
tuner' 0-0061: chip found @ 0xc2 (cx88[0])
tuner' 0-0063: chip found @ 0xc6 (cx88[0])
cx88[0]: hauppauge eeprom: model=69009
input: cx88 IR (Hauppauge WinTV-HVR400 as /class/input/input5
cx88[0]/2: cx2388x 8802 Driver Manager
cx88[0]/2: found at 0000:00:08.2, rev: 5, irq: 19, latency: 32, mmio: 0xdd000000
cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
cx88[0]/0: found at 0000:00:08.0, rev: 5, irq: 19, latency: 32, mmio: 0xdb000000
cx88[0]/0: registered device video0 [v4l2]
cx88[0]/0: registered device vbi0
cx88[0]/0: registered device radio0
cx88/2: cx2388x dvb driver version 0.0.6 loaded
cx88/2: registering cx8802 driver, type: dvb access: shared
cx88[0]/2: subsystem: 0070:6902, board: Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid [card=66]
cx88[0]/2: cx2388x based DVB/ATSC card
DVB: registering new adapter (cx88[0])
cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
cx24116_firmware_ondemand: Waiting for firmware upload(2)...
cx24116_load_firmware: FW version 1.20.79.0
cx24116_firmware_ondemand: Firmware upload complete
```

But when I scan, I never find any channels. It's the same with both DVB-T and DVB-S:
```

dvbscan -a 0 /usr/share/dvb/dvb-s/Thor-1.0W
scanning /usr/share/dvb/dvb-s/Thor-1.0W
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 11372000 V 24500000 7
initial transponder 11247000 V 24500000 7
initial transponder 11293000 H 24500000 7
initial transponder 11325000 H 24500000 7
initial transponder 12054000 H 28000000 7
initial transponder 12169000 H 28000000 7
initial transponder 12226000 V 28000000 7
>>> tune to: 11372:v:0:24500
DVB-S IF freq is 1622000
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 11247:v:0:24500
DVB-S IF freq is 1497000
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 11293:h:0:24500
DVB-S IF freq is 1543000
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 11325:h:0:24500

And so on...

Until:
dumping lists (0 services)
Done.
```
w_scan also fails to find anything.

Any tips on where I might go next?
I'll also try the card in windows later today.

---

### Post by aidan_curtis on 2008-03-27
growsling may i ask where you are based?
Aidan

---

### Post by aphex79 on 2008-03-27
luria: that worked! :KS 
checked the diff file, and got the mercurial nr. 127f67dea087, then i found the same nr. at v4l-dvb, here: [http://linuxtv.org/hg/v4l-dvb/rev/127f67dea087](http://linuxtv.org/hg/v4l-dvb/rev/127f67dea087)
The patch, make, and sudo make install worked:D
sooo now i'm on with the rest! (i bet i get stuck in some trouble there too(*,) )

---

### Post by Menthol on 2008-03-28
> **luria said:**
> Why don't you check out the v4l version that the patch was made against ?  

Go trough v4l changes and find the right version , then check it out with mercurials -v version switch.

Sorry for not replying to you earlier Luria, only just noticed your post !
I have indeed tried that but nothing seems to work so I've pretty much given up with it now....been fiddling with this for months now and pretty much had enough.
Thanks for your post though :) hopefully it'll help a few others out.

Thanks again :)

---

### Post by Growlizing on 2008-03-28
> **aidan_curtis said:**
> growsling may i ask where you are based?
Aidan

Norway.

Oh, and the cable is both working and has a signal, as it's working perfectly with the original tuner i got with my satellite.

---

### Post by aphex79 on 2008-03-29
as it seems everything installs right, i cannot seem to manage to scan the channels.
can i use diseqc with this driver? or do i have to bypass my diseqc?
but scanning with kaffeine works like a charm.. hm..

---

### Post by Growlizing on 2008-04-01
Solved my problem...
The HVR-4000 obviously does not work my semi-outdated (:P) MSI MS-6590, as the card worked like a charm straight away in my other computer :-/

---

### Post by aphex79 on 2008-04-01
har du fått dvb s2 drivere å fungere?

---

### Post by dimenos on 2008-04-12
ok this is what i did to fix my hvr 4000:

hg clone -r 127f67dea087 [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb
get latest diff from [http://dev.kewl.org/hauppauge](http://dev.kewl.org/hauppauge)
patch -p1 < NAME OF DIFF FILE
sudo make
sudo make install
restart pc
do dmesg | grep dvb 
should get conformation that tv card is installed

---

### Post by Cresho on 2008-04-12
scanning for channels is easy.

if you have your drivers installed, just look at my quick scan tutorial.

[http://ubuntuforums.org/showthread.php?t=734867](http://ubuntuforums.org/showthread.php?t=734867)

and after all that mess, you can look at my gallery.  I have 2 tv tuners running at the same time.  I dont use the averhd but kworld plustv115.
[http://ubuntuforums.org/g/images/279277/1_realubuntu.jpg](http://ubuntuforums.org/g/images/279277/1_realubuntu.jpg)

---

### Post by frafu on 2008-04-18
Hello, 

Does anybody know whether this also works for the WinTV-Nova-HD-S2? 

(I read that it is the same card as the HVR4000, but it only has the tuner for the satellite.) 

Thanks in advance for any reply. 

Francesco

---

### Post by Tyler_Durden on 2008-04-26
Hi there,
I'm currently desperately getting the WinTV-Nova-HD-S2 to work under the Linux kernel 2.6.24.3. I managed to follow the tutorials out there to compile the v4l-dvb stuff and get the driver to load.

However, whenever an application (e.g., kaffeine) wants to access the card, nothing happens. dmsg then shows me:

```

cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
sysfs: duplicate filename 'i2c-2' can not be created
WARNING: at fs/sysfs/dir.c:424 sysfs_add_one()
Pid: 3100, comm: kdvb-fe-0 Tainted: P        2.6.24.3 #3
 [<c018edc7>] sysfs_add_one+0x54/0xb7
 [<c018f247>] create_dir+0x3c/0x6b
 [<c018f2a3>] sysfs_create_dir+0x2d/0x40
 [<c0215f33>] kobject_get+0xf/0x13
 [<c0216365>] kobject_add+0xf5/0x1a7
 [<c021625d>] kobject_set_name+0x81/0x94
 [<c0276a42>] device_add+0x84/0x447
 [<c021604e>] kobject_init+0x27/0x37
 [<c027b9d2>] _request_firmware+0x11a/0x294
 [<c0307346>] bit_xfer+0x3ad/0x3b7
 [<c027bbe0>] request_firmware+0xf/0x11
 [<f887b5ec>] cx24116_cmd_execute+0xbe/0x5bb [cx24116]
 [<c0303e1b>] i2c_transfer+0x3a/0x42
 [<f887b4f9>] cx24116_writereg+0x6b/0xa0 [cx24116]
 [<f887c34e>] cx24116_initfe+0x6e/0xf2 [cx24116]
 [<c01173fc>] update_curr+0x52/0xc4
 [<f8c6239e>] dvb_frontend_init+0x39/0x5c [dvb_core]
 [<f8c636b6>] dvb_frontend_thread+0x6f/0x2c5 [dvb_core]
 [<c03c550e>] schedule+0x214/0x257
 [<f8c63647>] dvb_frontend_thread+0x0/0x2c5 [dvb_core]
 [<c012a8d9>] kthread+0x36/0x5d
 [<c012a8a3>] kthread+0x0/0x5d
 [<c010484f>] kernel_thread_helper+0x7/0x10
 =======================
kobject_add failed for i2c-2 with -EEXIST, don't try to register things with the same name in the same directory.
Pid: 3100, comm: kdvb-fe-0 Tainted: P        2.6.24.3 #3
 [<c02163e5>] kobject_add+0x175/0x1a7
 [<c021625d>] kobject_set_name+0x81/0x94
 [<c0276a42>] device_add+0x84/0x447
 [<c021604e>] kobject_init+0x27/0x37
 [<c027b9d2>] _request_firmware+0x11a/0x294
 [<c0307346>] bit_xfer+0x3ad/0x3b7
 [<c027bbe0>] request_firmware+0xf/0x11
 [<f887b5ec>] cx24116_cmd_execute+0xbe/0x5bb [cx24116]
 [<c0303e1b>] i2c_transfer+0x3a/0x42
 [<f887b4f9>] cx24116_writereg+0x6b/0xa0 [cx24116]
 [<f887c34e>] cx24116_initfe+0x6e/0xf2 [cx24116]
 [<c01173fc>] update_curr+0x52/0xc4
 [<f8c6239e>] dvb_frontend_init+0x39/0x5c [dvb_core]
 [<f8c636b6>] dvb_frontend_thread+0x6f/0x2c5 [dvb_core]
 [<c03c550e>] schedule+0x214/0x257
 [<f8c63647>] dvb_frontend_thread+0x0/0x2c5 [dvb_core]
 [<c012a8d9>] kthread+0x36/0x5d
 [<c012a8a3>] kthread+0x0/0x5d
 [<c010484f>] kernel_thread_helper+0x7/0x10
 =======================
fw_register_device: device_register failed
cx24116_firmware_ondemand: Waiting for firmware upload(2)...
cx24116_firmware_ondemand: No firmware uploaded (timeout or file not found?)
cx24116_cmd_execute(): Unable initialise the firmware

```

I compiled the drivers as follows:

hg clone -r 127f67dea087 [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
wget [http://dev.kewl.org/hauppauge/v4l-dvb-hg-sfe-latest.diff](http://dev.kewl.org/hauppauge/v4l-dvb-hg-sfe-latest.diff)
patch -d v4l-dvb -p1 < v4l-dvb-hg-sfe-latest.diff
cd v4l-dvb
make
make install

... and obtained the firmware as described earlier in this post as follows:

wget [ftp://167.206.143.11/outgoing/Oxford...25023_WHQL.zip](ftp://167.206.143.11/outgoing/Oxford...25023_WHQL.zip)
unzip -jo 88x_2_119_25023_WHQL.zip Driver88/hcw88bda.sys
dd if=hcw88bda.sys of=dvb-fe-cx24116.fw skip=81768 bs=1 count=32522
cp dvb-fe-cx24116.fw to /lib/firmware/2.6.24.3

(there is no difference whether I place it in /lib/firmware or /lib/firmware/2.6.24.3)


I read somewhere else that the offset of the firmware within the WHQL driver had changed (I really cant remember the page). But extracting the firmware with:

dd if=hcw88bda.sys of=dvb-fe-cx24116.fw skip=88912 bs=1 count=32522

did not make a difference at all.


Is there anything obvious I have overseen? Please help me out.

Thank you very much in advance.

So long,
CU Tyler

---

### Post by frafu on 2008-04-26
Hello, 

I have not got my card yet; so I cannot tell you anything concrete. However I can give you a few links that I have found: 
[http://www.gossamer-threads.com/lists/mythtv/mythtvnz/293961](http://www.gossamer-threads.com/lists/mythtv/mythtvnz/293961)
[http://dev.kewl.org/hauppauge/](http://dev.kewl.org/hauppauge/)

This is not to tell you that it is the cause of the problem, but I wondered why you are still using the 2.6.24-3 kernel? The current kernel in hardy is 2.6.24-16.

By the way, you can see what kernel you are using by typing "uname -a" in the terminal. 

Let us know how if you have some success. 

Francesco

---

### Post by Tyler_Durden on 2008-04-26
Hi there,
thanks for your answer. Unfortunately, your links did not provide any further information, as I have been using exactly these as reference. And btw. I'm not using 2.6.24-3; the kernel on my system (which is a gutsy installation) is 2.6.24.3 (vanilla).

Maybe I'm missing some option in my kernel?

Any hint would really be appreciated.

So long,
CU Tyler

---

### Post by wimo on 2008-04-27
I am triying to compile the driver in my Ubuntu Hardy installation and get the followind:

[PHP] cx88xx: disagrees about version of symbol videobuf_waiton
[   37.790909] cx88xx: Unknown symbol videobuf_waiton
[   37.791431] cx88xx: disagrees about version of symbol videobuf_dma_unmap
[   37.791433] cx88xx: Unknown symbol videobuf_dma_unmap
[   37.791607] cx88xx: disagrees about version of symbol video_device_alloc
[   37.791609] cx88xx: Unknown symbol video_device_alloc
[   37.791991] cx88xx: disagrees about version of symbol video_device_release
[   37.791993] cx88xx: Unknown symbol video_device_release
[   37.792279] cx88xx: disagrees about version of symbol videobuf_to_dma
[   37.792281] cx88xx: Unknown symbol videobuf_to_dma
[   37.793072] cx8800: disagrees about version of symbol videobuf_streamoff
[   37.793075] cx8800: Unknown symbol videobuf_streamoff
[   37.793167] cx8800: Unknown symbol cx88_reset
[   37.793206] cx8800: disagrees about version of symbol videobuf_poll_stream
[   37.793208] cx8800: Unknown symbol videobuf_poll_stream
[   37.793294] cx8800: Unknown symbol cx88_call_i2c_clients
[   37.793343] cx8800: Unknown symbol cx88_wakeup
[   37.793409] cx8800: Unknown symbol cx88_risc_stopper
[   37.793511] cx8800: Unknown symbol cx88_print_irqbits
[   37.793560] cx8800: Unknown symbol cx88_set_scale
[   37.793627] cx8800: Unknown symbol cx88_shutdown
[   37.793665] cx8800: disagrees about version of symbol videobuf_reqbufs
[   37.793668] cx8800: Unknown symbol videobuf_reqbufs
[   37.793716] cx8800: Unknown symbol cx88_vdev_init
[   37.793794] cx8800: Unknown symbol cx88_core_put
[   37.793865] cx8800: Unknown symbol cx88_audio_thread
[   37.793903] cx8800: disagrees about version of symbol videobuf_dqbuf
[   37.793906] cx8800: Unknown symbol videobuf_dqbuf
[   37.793954] cx8800: Unknown symbol cx88_core_irq
[   37.794023] cx8800: Unknown symbol cx88_core_get
[   37.794071] cx8800: Unknown symbol cx88_get_stereo
[   37.794120] cx8800: Unknown symbol cx88_ir_stop
[   37.794176] cx8800: Unknown symbol cx88_set_tvnorm
[   37.794232] cx8800: Unknown symbol cx88_ir_start
[   37.794316] cx8800: disagrees about version of symbol videobuf_stop
[   37.794318] cx8800: Unknown symbol videobuf_stop
[   37.794401] cx8800: Unknown symbol videobuf_queue_pci_init
[   37.794450] cx8800: Unknown symbol cx88_risc_buffer
[   37.794523] cx8800: disagrees about version of symbol videobuf_read_stream
[   37.794525] cx8800: Unknown symbol videobuf_read_stream
[   37.794590] cx8800: disagrees about version of symbol videobuf_querybuf
[   37.794592] cx8800: Unknown symbol videobuf_querybuf
[   37.794640] cx8800: Unknown symbol cx88_set_stereo
[   37.794678] cx8800: disagrees about version of symbol video_unregister_device
[   37.794681] cx8800: Unknown symbol video_unregister_device
[   37.794718] cx8800: disagrees about version of symbol videobuf_qbuf
[   37.794720] cx8800: Unknown symbol videobuf_qbuf
[   37.794780] cx8800: disagrees about version of symbol videobuf_read_one
[   37.794783] cx8800: Unknown symbol videobuf_read_one
[   37.794848] cx8800: Unknown symbol cx88_sram_channels
[   37.794886] cx8800: disagrees about version of symbol video_register_device
[   37.794888] cx8800: Unknown symbol video_register_device
[   37.794937] cx8800: Unknown symbol cx88_set_tvaudio
[   37.794985] cx8800: Unknown symbol cx88_sram_channel_dump
[   37.795060] cx8800: Unknown symbol cx88_sram_channel_setup
[   37.795106] cx8800: disagrees about version of symbol videobuf_iolock
[   37.795108] cx8800: Unknown symbol videobuf_iolock
[   37.795157] cx8800: Unknown symbol cx88_free_buffer
[   37.795194] cx8800: disagrees about version of symbol videobuf_streamon
[   37.795196] cx8800: Unknown symbol videobuf_streamon
[   37.795233] cx8800: disagrees about version of symbol videobuf_queue_cancel
[   37.795235] cx8800: Unknown symbol videobuf_queue_cancel
[   37.795305] cx8800: disagrees about version of symbol video_device_release
[   37.795307] cx8800: Unknown symbol video_device_release
[   37.795344] cx8800: disagrees about version of symbol videobuf_mmap_mapper
[   37.795346] cx8800: Unknown symbol videobuf_mmap_mapper
[   37.795390] cx8800: disagrees about version of symbol videobuf_cgmbuf
[   37.795393] cx8800: Unknown symbol videobuf_cgmbuf
[   37.795444] cx8800: Unknown symbol cx88_newstation
[   37.795502] cx8800: disagrees about version of symbol videobuf_to_dma
[   37.795504] cx8800: Unknown symbol videobuf_to_dma
[   37.795540] cx8800: disagrees about version of symbol videobuf_mmap_free
[   37.795542] cx8800: Unknown symbol videobuf_mmap_free
[   37.796563] cx88xx: disagrees about version of symbol videobuf_waiton
[   37.796566] cx88xx: Unknown symbol videobuf_waiton
[   37.797085] cx88xx: disagrees about version of symbol videobuf_dma_unmap
[   37.797087] cx88xx: Unknown symbol videobuf_dma_unmap
[   37.797260] cx88xx: disagrees about version of symbol video_device_alloc
[   37.797263] cx88xx: Unknown symbol video_device_alloc
[   37.797644] cx88xx: disagrees about version of symbol video_device_release
[   37.797646] cx88xx: Unknown symbol video_device_release
[   37.798242] cx88xx: disagrees about version of symbol videobuf_to_dma
[   37.798245] cx88xx: Unknown symbol videobuf_to_dma
[   37.799488] cx8802: Unknown symbol cx88_reset
[   37.799604] cx8802: Unknown symbol cx88_wakeup
[   37.799757] cx8802: Unknown symbol cx88_risc_stopper
[   37.799911] cx8802: Unknown symbol cx88_print_irqbits
[   37.800067] cx8802: Unknown symbol cx88_shutdown
[   37.800204] cx8802: Unknown symbol cx88_core_put
[   37.800368] cx8802: Unknown symbol cx88_core_irq
[   37.800521] cx8802: Unknown symbol cx88_core_get
[   37.800867] cx8802: Unknown symbol cx88_sram_channels
[   37.800979] cx8802: Unknown symbol cx88_sram_channel_dump
[   37.801108] cx8802: Unknown symbol cx88_sram_channel_setup
[   37.801216] cx8802: disagrees about version of symbol videobuf_iolock
[   37.801221] cx8802: Unknown symbol videobuf_iolock
[   37.801333] cx8802: Unknown symbol cx88_free_buffer
[   37.801526] cx8802: Unknown symbol cx88_risc_databuffer
[   37.801562] cx8802: disagrees about version of symbol videobuf_to_dma
[   37.801564] cx8802: Unknown symbol videobuf_to_dma
[   37.802526] cx88xx: disagrees about version of symbol videobuf_waiton
[   37.802528] cx88xx: Unknown symbol videobuf_waiton
[   37.803047] cx88xx: disagrees about version of symbol videobuf_dma_unmap
[   37.803049] cx88xx: Unknown symbol videobuf_dma_unmap
[   37.803223] cx88xx: disagrees about version of symbol video_device_alloc
[   37.803225] cx88xx: Unknown symbol video_device_alloc
[   37.803606] cx88xx: disagrees about version of symbol video_device_release
[   37.803609] cx88xx: Unknown symbol video_device_release
[   37.803899] cx88xx: disagrees about version of symbol videobuf_to_dma
[   37.803902] cx88xx: Unknown symbol videobuf_to_dma
[   37.805146] cx88_alsa: Unknown symbol cx88_print_irqbits
[   37.805345] cx88_alsa: Unknown symbol cx88_core_put
[   37.805435] cx88_alsa: Unknown symbol videobuf_pci_alloc
[   37.805484] cx88_alsa: Unknown symbol cx88_core_irq
[   37.805550] cx88_alsa: Unknown symbol cx88_core_get
[   37.805973] cx88_alsa: Unknown symbol cx88_sram_channels
[   37.806021] cx88_alsa: Unknown symbol cx88_sram_channel_dump
[   37.806088] cx88_alsa: Unknown symbol cx88_sram_channel_setup
[   37.806201] cx88_alsa: Unknown symbol videobuf_pci_dma_unmap
[   37.806301] cx88_alsa: Unknown symbol videobuf_pci_dma_map
[   37.806365] cx88_alsa: Unknown symbol cx88_risc_databuffer
[   37.806401] cx88_alsa: disagrees about version of symbol videobuf_to_dma
[   37.806404] cx88_alsa: Unknown symbol videobuf_to_dma[/PHP]

---

### Post by Tyler_Durden on 2008-04-27
Hi all,
I can finally report success - though only for gutsy. I have upgraded to the most recent Linux kernel, which is 2.6.25. After recompiling the driver, the firmware did load without problems (I did the same steps again, as I described in my first post).

Currently I'm scanning for channels using Kaffeine, which just finished. Ahhh guys, this so cool. Finally I can boot the windows installation :).

@wimo: I'm not sure what the exact problem is. Could you tell us which kernel you are using (via "uname -a" in a console)?

So long,
CU Tyler

---

### Post by wimo on 2008-04-27
> **Tyler_Durden said:**
> Hi all,

@wimo: I'm not sure what the exact problem is. Could you tell us which kernel you are using (via "uname -a" in a console)?

So long,
CU Tyler
I have installed ubuntu 64 in a clean machine, my kerne
2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux
regards.
this messages are displayes after dmesg |grep cx.

Regards

---

### Post by Tyler_Durden on 2008-04-27
Hi again,
hmm... a similar problem is being discussed here: [http://www.gossamer-threads.com/lists/mythtv/mythtvnz/329861](http://www.gossamer-threads.com/lists/mythtv/mythtvnz/329861)

Are you sure that the driver has been compiled for the correct kernel version? Have you installed the kernel headers (package linux-headers-2.6.24-16)? Have to tried to remove the compiled modules and tried to follow the same steps as I did?

Hmm... another problem could be that there is already some precompiled stuff in the distro-kernel that interfers with the driver (I'm not sure... just guessing).

Regards,
Tyler

---

### Post by frafu on 2008-04-27
> **Tyler_Durden said:**
> Hi all,
I can finally report success - though only for gutsy. I have upgraded to the most recent Linux kernel, which is 2.6.25. After recompiling the driver, the firmware did load without problems (I did the same steps again, as I described in my first post).


That is good news. 

Could you please tell me where to get the kernel 2.6.25 from? 
Did you compile it yourself? 

Thanks in advance. 

Francesco

---

### Post by wimo on 2008-04-27
I have been googling three days and doing all what i find but still my card do not work.
I think that the better solution is wait until kernel 2.25 will be used by ubuntu.

Sorry about my english

---

### Post by Tyler_Durden on 2008-04-28
Hi there,

> **frafu said:**
> That is good news. 

Could you please tell me where to get the kernel 2.6.25 from? 
Did you compile it yourself? 

Thanks in advance.

yes, I did compile the kernel myself (not compiling any dvb etc. support into it). You can get the recent kernel from [http://kernel.org](http://kernel.org). The exact link is: [http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.25.tar.bz2](http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.25.tar.bz2). You'll find several tutorials in the net how to compile a kernel, e.g.: [http://ubuntuforums.org/showthread.php?t=157560](http://ubuntuforums.org/showthread.php?t=157560) or [http://howtoforge.com/kernel_compilation_ubuntu](http://howtoforge.com/kernel_compilation_ubuntu).

---

### Post by eisheiliger on 2008-04-28
> **wimo said:**
> I am triying to compile the driver in my Ubuntu Hardy installation and get the followind:

[PHP] cx88xx: disagrees about version of symbol videobuf_waiton
[   37.790909] cx88xx: Unknown symbol videobuf_waiton
[   37.791431] cx88xx: disagrees about version of symbol videobuf_dma_unmap
...
You must delete the Original Ubuntu-Version of cx88 in /lib/modules/2.6.24-16-generic/ubuntu/media/cx88/ before install the driver...
delete:
```
sudo rm /lib/modules/2.6.24-16-generic/ubuntu/media/cx88/*
```


I have a Nova-HD-S2 in Hardy Heron Kernel 2.6.24-16
A dmesg |grep cx88 says:
```
[   32.868090] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   32.868205] cx88[0]: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=66,autodetected]
[   32.868208] cx88[0]: TV tuner type -1, Radio tuner type -1
[   33.010191] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   33.938970] cx88[0]: hauppauge eeprom: model=69100
[   33.939188] input: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:0c.2/input/input6
[   33.991653] cx88[0]/2: cx2388x 8802 Driver Manager
[   33.991681] cx88[0]/2: found at 0000:00:0c.2, rev: 5, irq: 17, latency: 64, mmio: 0xf9000000
[   33.991967] cx88[0]/0: found at 0000:00:0c.0, rev: 5, irq: 17, latency: 64, mmio: 0xf7000000
[   33.999818] cx88[0]/0: registered device video0 [v4l2]
[   33.999843] cx88[0]/0: registered device vbi0
[   34.943615] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   34.943620] cx88/2: registering cx8802 driver, type: dvb access: shared
[   34.943623] cx88[0]/2: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=66]
[   34.943627] cx88[0]/2: cx2388x based DVB/ATSC card
[   34.994364] DVB: registering new adapter (cx88[0])

```

---

### Post by eisheiliger on 2008-04-28
I forgot...

Sorry for my bad english....

---

### Post by frafu on 2008-05-02
Hello,

I finally got the Nova-HD-S2 card and I am trying to get it to work with the 2.6.24 generic kernel of hardy. 

- I removed everything from the /lib/modules/2.6.24-16-generic/ubuntu/media/cx88/ directory 

- The patch does not apply anymore properly to the current v4l-dvb. Fortunately, I had another version of the v4l-dvb directory that I downloaded some time ago and to which it applies correctly. (I don't know what revision it is.) 

Here is the output of dmesg | grep cx88

```
 
[   46.786465] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   46.786613] cx88[0]: cx88[0]: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=66,autodetected], frontend(s): 1
[   46.786617] cx88[0]: TV tuner type -1, Radio tuner type -1
[   46.961930] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   47.723298] cx88[0]: hauppauge eeprom: model=69100
[   47.724263] input: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:1e.0/0000:03:02.0/input/input5
[   47.743461] cx88[0]/0: found at 0000:03:02.0, rev: 5, irq: 19, latency: 32, mmio: 0xd8000000
[   47.743571] cx88[0]/0: registered device video0 [v4l2]
[   47.743622] cx88[0]/0: registered device vbi0
[   47.743680] cx88[0]/2: cx2388x 8802 Driver Manager
[   47.743712] cx88[0]/2: found at 0000:03:02.2, rev: 5, irq: 19, latency: 32, mmio: 0xda000000
[   47.743720] cx8802_probe() allocating 1 frontend(s)
[   47.807615] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   47.807622] cx88/2: registering cx8802 driver, type: dvb access: shared
[   47.807627] cx88[0]/2: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=66]
[   47.807631] cx88[0]/2: cx2388x based DVB/ATSC card
[   48.072735] cx88[0]/2: frontend initialization failed
[   48.072739] cx88[0]/2: dvb_register failed (err = -22)
[   48.072743] cx88[0]/2: cx8802 probe failed, err = -22

``` 

So it does not work yet. 

Could anybody please upload a copy of the firmware? Unfortunately, the link provided above does not work anymore. 

Thanks in advance. 

Francesco

---

### Post by frafu on 2008-05-02
I found the hcw88bda.sys file in my Windows installation and derived the firmware from it; but I don't know whether it is correct.

Installing the firmware did not help: I still get the same error.


Does anybody have a clue ?

---

### Post by frafu on 2008-05-02
I found the hcw88bda.sys file in my Windows installation and derived the firmware from it; but I don't know whether it is correct.

Installing the firmware did not help: I still get the same error.


Does anybody have a clue ?

---

### Post by frafu on 2008-05-05
It is working now with kernel 2.6.24-17. I followed [these instructions]("http://forum.ubuntuusers.de/topic/119840/30/?p=1372718#1372718") that also contains what revision of v4l-dvb to use.  

However, I changed the following two points:

Instead of deleting everything from the /lib/modules/2.6.24-17-generic/ubuntu/media/cx88/ directory, I created it, because it did not exist. 

I copied the firmware to /lib/firmware/ and to /lib/firmware/2.6.24-17-generic/

Cheers

Francesco

---

### Post by Chafnan on 2008-06-17
Here is a little script that I wrote that will install the firmware and driver for you.

My machine in is running Ubuntu Hardy 64-bit.

My card is the Hauppauge Nova-HD-S2, but as far I know this should work for the HVR-4000.  Not sure how much difference there is between those.

---

### Post by frafu on 2008-06-17
@Chafnan

Really nice script (though I have not tested it) 

For those with a little experience with the terminal, it can even be useful to people that want to do it manually: it contains all the necessary commands. 

Thanks

---

### Post by Chafnan on 2008-06-18
I have updated the script.  I changed the firmware, and it created a problem with extracting it.  So, the script is now working.

```

#!/bin/bash
#
#################################################
# Author: Jonathan Chapman                      #
# Date: June 13, 2008                           #
#                                               #
# This script is to install the drivers for the #
# Happauge WINTV-NOVA-HD-S2.                    #
#                                               #
# Requirements:                                 #
#     * Linux Kernel 2.6.24                     #
#################################################

FIRMWARE_LOCATION=/lib/firmware/`uname -r`

#################################################
# Work Order:                                   #
#  1. Check kernel                              #
#  2. Get required software                     #
#    a. Build-essentials                        #
#    b. Linux-headers                           #
#    c. Mericial                                #
#    d. Zip/Unzip                               #
#  3. Download drivers and software for card    #
#    a. v4l-dvb                                 #
#    b. patch                                   #
#    c. firmware                                #
#  4. Install firmware                          #
#  5. Install driver                            #
#    a. apply patches                           #
#    b. make                                    #
#    c. make install                            #
#  6. Reboot computer                           #
#################################################


#################################################
#  1. Check kernel                              #
#################################################
KERNEL=`uname -r | awk -F . '{ print $3 }' | awk -F - '{ print $1 }'`

if [ $KERNEL -ge 24 ]
  then
    echo Requirements confirmed.
  else
    echo 
    echo Requirements not met.
    echo Linux Kernel => 2.6.24 is needed.
    exit 1
fi

#################################################
#  2. Get required software                     #
#       a. Build-essentials                     #
#       b. Linux-headers                        #
#       c. Mericial                             #
#       d. Zip/Unzip                            #
#################################################

sudo apt-get -y install build-essential

if [ $? -ne 0 ]
  then
    echo
    echo Build-Essential failed to install.
    echo Please run this script again.
    exit 1
fi

sudo apt-get -y install linux-headers-`uname -r`

if [ $? -ne 0 ]
  then
    echo
    echo Linux headers failed to install.
    echo Please run this script again.
    exit 1
fi

sudo apt-get -y install mercurial

if [ $? -ne 0 ]
  then
    echo
    echo Mercurial failed to install.
    echo Please run this script again.
    exit 1
fi

sudo apt-get -y install zip unzip

if [ $? -ne 0 ]
  then
    echo
    echo Zip failed to install.
    echo Please run this script again.
    exit 1
fi

#################################################
#  3. Download drivers and software for card    #
#       a. v4l-dvb                              #
#       b. patch                                #
#       c. firmware                             #
#################################################

if [ -d /tmp/dvb ]
 then
   rm -rf /tmp/dvb
fi

mkdir /tmp/dvb
cd /tmp/dvb

# Currently this is the build that works with the patch
hg clone -r 127f67dea087 http://linuxtv.org/hg/v4l-dvb

if [ $? -ne 0 ]
  then
    echo
    echo Driver software did not download.
    echo Try running script again.
    exit 1
fi

# The patch
wget http://dev.kewl.org/hauppauge/v4l-dvb-hg-sfe-latest.diff

if [ $? -ne 0 ]
  then
    echo
    echo Patch failed to download.
    echp Pleae try running the script again.
    exit 1
fi

# The firmware
wget http://www.wintvcd.co.uk/drivers/88x_2_122_26109_WHQL.zip

if [ $? -ne 0 ]
  then
    echo
    echo The firmware did not download.
    echo Try running the script again.
    exit 1
fi
#################################################
#  4. Install firmware                          #
#################################################

unzip 88x_2_122_26109_WHQL.zip Driver88/64bit/hcw88bda.sys

if [ $? -ne 0 ]
  then
    echo
    echo Firmware: unzip failed.
    echo Try running script again.
    exit 1
fi

dd if=Driver88/64bit/hcw88bda.sys of=dvb-fe-cx24116.fw skip=75504 bs=1 count=32501

if [ $? -ne 0 ]
  then
    echo
    echo Firmware: dd failed.
    echo Try running script again.
    exit 1
fi

sudo cp dvb-fe-cx24116.fw $FIRMWARE_LOCATION

if [ $? -ne 0 ]
  then
    echo
    echo Firmware: cp failed.
    echo Try running script again.
    exit 1
fi

#################################################
#  5. Install driver                            #
#       a. apply patches                        #
#       b. make                                 #
#       c. make install                         #
#################################################

patch -d v4l-dvb -p1 < v4l-dvb-hg-sfe-latest.diff

if [ $? -ne 0 ]
  then
    echo
    echo Patch failed. Probably has been updated.
    echo Need to check out new version and change the version
    echo of the v4l-dvb that was downloaded.
fi

cd v4l-dvb

make

if [ $? -ne 0 ]
  then
    echo
    echo Driver: make failed
    exit 1
fi

sudo make install

if [ $? -ne 0 ]
  then
    echo
    echo Driver: make install failed
    exit 1
fi

#################################################
#  6. Reboot computer                           #
#################################################

echo
echo Would you like to restart your computer now?

exit 0

```

Also, I thought I would attach it as a text file.  Then someone can download it and just run the following commands to get it running on their system.

```

mv hvr_4000_driver.txt hvr_4000_driver.sh
chmod +x hvr_4000_driver.sh
./hvr_4000_driver.sh

```

---

### Post by seawasp on 2008-06-25
Firstly, thank you for all your posts, I'm closer to getting this Nova-HD-S2 card working than I have ever been, but I'm still not quite there yet.

I've followed the instructions in the link posted by frafu and also run the great script by Chafnan, but I don't appear to be able to upload the firmware...

```
dmesg |grep firm
[  160.658440] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[  160.745139] cx24116_firmware_ondemand: Waiting for firmware upload(2)...
[  164.698490] cx24116_firmware_ondemand: Writing firmware to device failed
[  164.698504] cx24116_firmware_ondemand: Firmware upload failed
[  164.698506] cx24116_cmd_execute(): Unable initialise the firmware
```

The driver appears to have installed ok..

```
dmesg |grep cx88
[   32.525169] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   32.525712] cx88[0]: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=66,autodetected]
[   32.525715] cx88[0]: TV tuner type -1, Radio tuner type -1
[   32.554724] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   33.005709] cx88[0]: hauppauge eeprom: model=69100
[   33.006379] input: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:10.0/0000:01:08.0/input/input6
[   33.052427] cx88[0]/0: found at 0000:01:08.0, rev: 5, irq: 16, latency: 32, mmio: 0xfa000000
[   33.052484] cx88[0]/0: registered device video0 [v4l2]
[   33.052503] cx88[0]/0: registered device vbi0
[   33.052608] cx88[0]/2: cx2388x 8802 Driver Manager
[   33.052633] cx88[0]/2: found at 0000:01:08.2, rev: 5, irq: 16, latency: 32, mmio: 0xf8000000
[   33.126785] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   33.126789] cx88/2: registering cx8802 driver, type: dvb access: shared
[   33.126793] cx88[0]/2: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=66]
[   33.126796] cx88[0]/2: cx2388x based DVB/ATSC card
[   33.255551] DVB: registering new adapter (cx88[0])
```

I'm using a 64bit system with a 2.6.24-19-generic kernel, although I have also booted the 2.6.24-16-generic kernel and run Chafnan's script with the same results. I'm using a relatively clean and patched install of Mythbuntu 8.04.
 
Any suggestions?

Once again thank you

Chris

---

### Post by Chafnan on 2008-07-08
Try a different version of the firmware.

---

### Post by seawasp on 2008-07-09
Flat forehead time. Thank you!

Ok, so I installed the firmware from 88x_2_119_25023_WHQL.zip which I found on the German forum...
[http://forum.ubuntuusers.de/topic/119840/30/?p=1372718#1372718]("http://forum.ubuntuusers.de/topic/119840/30/?p=1372718#1372718")

My firmware now looks to have loaded ok...

```

dmesg |grep firm
[  123.230610] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[  123.337212] cx24116_firmware_ondemand: Waiting for firmware upload(2)...
[  126.415590] cx24116_load_firmware: FW version 1.20.79.0
[  126.415607] cx24116_firmware_ondemand: Firmware upload complete

```

When I try to scan though, I get this...

```

scan /usr/share/doc/dvb-utils/examples/scan/dvb-s/Astra-28.2E >channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-s/Astra-28.2E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 10773000 H 22000000 5
initial transponder 11778000 V 27500000 2
>>> tune to: 10773:h:0:22000
WARNING: >>> tuning failed!!!
>>> tune to: 10773:h:0:22000 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 11778:v:0:27500
WARNING: >>> tuning failed!!!
>>> tune to: 11778:v:0:27500 (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.

```

In Kaffeine I get a Signal Strength of 75 to 95% but an SNR of 0%.

Any suggestions?

---

### Post by eisheiliger on 2008-07-10
Have you installed the Multiproto Drivers ?

---

### Post by seawasp on 2008-07-11
No, I don't think so.

After having had a quick read up on the multiproto, it doesn't look like any of the instructions I have followed covered this. Is this something that others on this thread will have installed but not discussed, or is there something about my setup that needs it, but others don't?

Thanks

---

### Post by seawasp on 2008-07-13
Below is the procedure I used to install multiproto, but I don't appear to be any better off than I was before...

Using the instructions for the HVR-4000 at
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000")
and a post at...
[http://linuxtv.org/pipermail/linux-dvb/2008-March/024747.html]("http://linuxtv.org/pipermail/linux-dvb/2008-March/024747.html")


Downloaded
[http://jusst.de/hg/multiproto/archive/ecb96c96a69e.tar.bz]("http://jusst.de/hg/multiproto/archive/ecb96c96a69e.tar.bz")
Unpacked and placed in my home directory under the directory name of multiproto


```

wget http://www.linuxtv.org/pipermail/linux-dvb/attachments/20080128/adee4c88/attachment-0001.bin
mv attachment-0001.bin multiproto-hvr4k-2008-01-28.patch.bz2
bunzip2 multiproto-hvr4k-2008-01-28.patch.bz2
ln -s multiproto a; ln -s multiproto b
patch -p0 < multiproto-hvr4k-2008-01-28.patch
cd multiproto

```

It all goes well up to this point. The instruction then say...
```
run make menuconfig and disable the USB capture cards as the em88 drivers are broken and make sure customise frontends is enabled.
make && make install && reboot
```

so I typed...

```
make menuconfig
```

and at this point I got a whole load of errors, but specifically...

```
.....In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:32:20: error: curses.h: No such file or directory....
```

After a bit of hunting I found I needed to install libncurses5-dev and typing make meuconfig again got me the Kernel Configuration. So following the instructions above....

Multimedia devices ------->  Video capture adapters -------> V4L USB devices -------> < > Empia EM2800/2820/2840 USB video capture support 

Multimedia devices ------->  DVB/ATSC adapters ------>  Customise DVB frontends ------->  [*] Customise the frontend modules to build

```
make
make install
reboot
```

On reboot I scanned for channels again using the scan command and also with Kaffeine, but with same results as before.

---

### Post by eisheiliger on 2008-07-18
Kaffeine don't work with the multiproto driver, for Kaffeine use the driver from my install-guide [http://forum.ubuntuusers.de/topic/119840/30/?p=1372718#1372718](http://forum.ubuntuusers.de/topic/119840/30/?p=1372718#1372718). It works fine with Kaffeine. Reinstall the multiproto driver from the multiproto directory with ```
sudo make distclean
```

---

### Post by Scorpuk on 2008-07-19
Can anyone tell me what has happened to forum.ubuntuusers.de?

Keep on getting a failed to connect message.


Need to follow the guide there again as I have updated my graphics card and my nova-hd s2 has dissapeared.

---

### Post by eisheiliger on 2008-07-19
When you have an earlier install of the driver you go in the v4l-dvb directory and ```
make clean
``````
sudo make distclean
``````
make
``````
sudo make install
```and a reboot...
or here a copy of my install-guide from ubuntusers.de. Sorry, it is german
-------------------------------------------------------------------------------------------------------------------------
Damit die Sachen kompiliert werden können, braucht man, sofern noch nicht installiert:
```
sudo apt-get install build-essential
```

Wichtig! löschen der Ubuntu-Version des cx88, bzw. man kann sich vorher eine Sicherungskopie des Verzeichnisses erstellen.
(bei einem anderem Kernel den Pfad anpassen, hier ist es Kernel 2.6.24-16) .
...löschen:
```
sudo rm /lib/modules/'uname -r'/ubuntu/media/cx88/*
```

Falls noch nicht vorhanden, die Firmware besorgen:
```
wget ftp://167.206.143.11/outgoing/Oxford/88x_2_119_25023_WHQL.zip
```
...dann entpacken mit:
```
unzip -jo 88x_2_119_25023_WHQL.zip Driver88/hcw88bda.sys
```
umbenennen und es an die richtige Stelle kopieren mit:
```
dd if=hcw88bda.sys of=/lib/firmware/dvb-fe-cx24116.fw skip=81768 bs=1 count=32522
``` 


...den Treiber besorgen:
```
hg clone -r 127f67dea087 http://linuxtv.org/hg/v4l-dvb
```1abbd650fe07
den dazugehörigen Patch:
```
wget http://dev.kewl.org/hauppauge/v4l-dvb-hg-sfe-latest.diff
```
...patchen:
```
patch -d v4l-dvb -p1 < v4l-dvb-hg-sfe-latest.diff
```
...ins Verzeichnis wechseln:
```
cd v4l-dvb
```
...den Treiber bauen:
```
make
```
...den Treiber installieren: 
```
sudo make install
```
...und den Rechner neu starten 
```
sudo reboot
```

---

### Post by Scorpuk on 2008-07-19
Thanks eisheiliger.

Must have don something else during updates as doing the simple make / make install didnt work and I had to go back to following the complete guide.


But at least its working again. :-) :KS

---

### Post by frafu on 2008-07-22
Hello, 

Did anybody already succeed to make it work with a 2.6.26.n kernel of Intrepid? 

I get the following error: 

>  
/home/frafu/v4l-dvb/v4l/ivtv-i2c.c: In function 'ivtv_i2c_register':
/home/frafu/v4l-dvb/v4l/ivtv-i2c.c:171: error: 'struct i2c_board_info' has no member named 'driver_name'
make[3]: *** [/home/frafu/v4l-dvb/v4l/ivtv-i2c.o] Error 1
make[2]: *** [_module_/home/frafu/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.26-4-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/frafu/v4l-dvb/v4l'
make: *** [all] Error 2
 

I am using the following revision and patch of the v4l-dvb drivers: 
hg clone -r 127f67dea087 [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
wget [http://dev.kewl.org/hauppauge/v4l-dvb-hg-sfe-latest.diff](http://dev.kewl.org/hauppauge/v4l-dvb-hg-sfe-latest.diff)

Cheers 

Francesco

---

