---
title: "[SOLVED] Help on setting up MythTV for KWorld ATSC 115 tuner"
date: 2007-12-17
forum: Multimedia &amp; Video
---

### Post by thecoolcat on 2007-12-17
Hi.
I try to setup my Kworld ATSC 115 TV card on my Ubuntu Gusty pc by folowing this howto:
[http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110](http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110)

I believe I have configured it correctly after following the following steps (mostly from posts by user newlinux):
1. Added the following lines to /etc/modprobe.d/kworld_atsc_115
```
alias char-major-81 videodev 
alias char-major-81-0 saa7134 
options saa7134 card=90 
```
2. Then I did the following: Edited my /etc/modules to add:
```
saa7134 
saa7134-dvb
saa7134-alsa
```
3. Placed a copy of the firmware file (dvb-fe-nxt2004.fw) in my /lib/firmware/<linux kernel name>/. directory

From dmesg output, I see that the card is being recognized and nxt2004 is being loaded.

**_My problems:_**
1) I was able to use tvtime and tune analog channels. [COLOR="Red"]I couldn't get audio. [/COLOR]I thought adding saa7134-alsa to /etc/modules would fix it. I also did the following:
```
# v4lctl -c /dev/video0 setattr automute off
# v4lctl -c /dev/video0 volume mute off
```The above didn't help in getting audio either.

2) Using tvtime [COLOR="red"]I could not tune digital (OTA) channels[/COLOR].
3) I  [COLOR="red"]was not able to scan the channels in MythTV setup[/COLOR]. When I try to scan the channels, I see a message, error opening the card or similar one. I am not clear on this portion. I have added it multiple times under Analog, Digital (as the tuner is listed as ATSC 110 which is a single tuner card, rather that ATSC 115 which is a dual tuner card). --> **Edit**: [COLOR="Green"]Got digital OTA to work!![/COLOR]

Can someone please help?

---

### Post by thecoolcat on 2007-12-18
I just added "Analog" and "Digital" to the "video sources" in the MythTV setup and it seems like I'm able to scan. Still working on #3 though --> Got digital OTA to work!!!.

Can someone help me on #1 and #2, please?
Thanks.

---

### Post by thecoolcat on 2007-12-19
Also has anyone tried settong up the remote control for KWORLD ATSC 115? (Or how can I use its IR receiver?)
Thanks.

---

### Post by captevo on 2007-12-21
> **thecoolcat said:**
> Also has anyone tried settong up the remote control for KWORLD ATSC 115? (Or how can I use its IR receiver?)
Thanks.

I'm interested in this as well.  Please help.

---

### Post by hftb on 2007-12-21
to: thecoolcat,
Can you recap what you've got working, and what doesn't work?  Can you record off both connections? NTSC and ATSC (OTA)?
This card looks fairly reasonable off TigerDirect's site. Right now I have a single Hauppauge 150 card, but would also like to record ATSC.  Too bad it doesn't also have MPEG-2 encoder with it. :)

---

### Post by thecoolcat on 2007-12-21
> **hftb said:**
> to: thecoolcat,
Can you recap what you've got working, and what doesn't work?  Can you record off both connections? NTSC and ATSC (OTA)?
This card looks fairly reasonable off TigerDirect's site. Right now I have a single Hauppauge 150 card, but would also like to record ATSC.  Too bad it doesn't also have MPEG-2 encoder with it. :)

Hi hftb:
1) I'm able to configure mythTV to scan OTA ATSC channels without any trouble. Works perfectly. (Both audio and video!) I could pause, rewind, FF, etc. :) All you need to do is force this card to behave like KWorld ATSC-110.
2) I could NOT get NTSC to work. mythTV scans. But I don;t know how to play it. tvtime scans. video appears for 2 seconds and then I get a message "No Signal". Audio does not work at all. :(
3) Remote does not work out of the box. But I haven't had any chance to debug this yet. :(

---

### Post by thecoolcat on 2007-12-21
To watch digital channels without using mythtv do the following:

1) Install dvb-utils
2) Tune channels: Execute the following command, all in one line.

```
$  /usr/bin/scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB > .~/.mplayer/channels.conf
```

3) Watch it using mplayer :)
```

mplayer dvb://

```

(Use h or k to change channels.

Still could not watch analog and could not get remote to work. Anyone can help??

---

### Post by thecoolcat on 2007-12-25
To get the remote to work do I have to modprobe ir-kbd-gpio or ir-kbd-i2c?[COLOR="Red"] Can someone hel[/COLOR]p? When I do ```
sudo modprobe ir-kbd-i2c
```, I don't see any relevant IR  I/O devices in 
 cat /proc/bus/input/devices.

---

### Post by thecoolcat on 2007-12-25
The analog tuner works for 2 seconds and then goes away. (Then I get "No Signal" in tvtime.)
Audio is working if I run the following command in another xterm:
```
arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -
```
Seems like I'm very close on the analog tuner. Can someone help??

---

### Post by thecoolcat on 2007-12-26
From browsing the web, it seems like I can't have both analog and digital at the same time. Is this true? If so how do I switch between analog and digital? Thanks.

---

### Post by thecoolcat on 2007-12-27
update: I can view analog (NTSC) if I stop mythbackend. Seems like mythbackend is locking the tuner card to capture OTA ATSC only. Does anyone know how to switch between ATSC OTA and analog NTSC for this card using MythTV?

---

### Post by newlinux on 2007-12-28
How do you have the card setup in myth? do you have it setup one card with two sources in myth? If so you can press the "c" button to switch between inputs. when I had this working in myth, the first time I switched from analog to digital the picture would be garbled, but if I changed to another analog channel all was fine.

---

### Post by thecoolcat on 2007-12-28
I have to hit a "Y" to switch from digital OTA to analog and back (which would imply that it is been set up as multiple capture cards). When I do that the NTSC video appears for two seconds only and goes away.

How do I set it up as "one card"? I thought I won't be able to do this because the input that scans digital OTA also scans analog NTSC. (Seems like the input is shared between OTA and NTSC.) I believe the other input is exclusively for QAM. Is it possible to force the other input to be analog NTSC as I don't use QAM?

---

### Post by newlinux on 2007-12-28
You should still be able to do this even if they use the same input. I have a dvico fusion 5 lite that only has one input for everything (ATSC/QAM/NTSC) that this works on. 

First, you'll want to delete the separate card you setup as an analog card.
When you view the capture card (the one you have left set to using the DVB driver) in mythtv-setup, do you see an "analog options" button? There was a patch to have this working submitted about a year ago, but I don't know if it made it into the version ubuntu uses. If so this is where you would setup the NTSC input. If not, you will either need to download the patch and compile from source or I can show you how to modify the database to allow you to configure tha analog option (I recommend this option)

I don't know about forcing one input to do one thing and the other to do another. In my experience, sometimes they even switched on reboots, and the inputs were different in windows than they were in Linux. This might not be true of the 115, but it happened this way for me on the 110.

---

### Post by thecoolcat on 2007-12-28
> **newlinux said:**
> 
First, you'll want to delete the separate card you setup as an analog card.
When you view the capture card (the one you have left set to using the DVB driver) in mythtv-setup, do you see an "analog options" button? 

I don't remember seeing the "analog options" button. But I'll double check in few hours today.

> **newlinux said:**
> There was a patch to have this working submitted about a year ago, but I don't know if it made it into the version ubuntu uses. If so this is where you would setup the NTSC input. If not, you will either need to download the patch and compile from source or I can show you how to modify the database to allow you to configure tha analog option (I recommend this option)

I'll first check if the "analog options" button is available and will update this thread.

> **newlinux said:**
> I don't know about forcing one input to do one thing and the other to do another. In my experience, sometimes they even switched on reboots, and the inputs were different in windows than they were in Linux. This might not be true of the 115, but it happened this way for me on the 110.

I see. Its because the driver controls it I'd guess.

Thanks a lot.

---

### Post by newlinux on 2007-12-28
Yep, I bet it is a driver issue.

In case I am not around and you don't get the 
"analog options" option here is the post that describes how to do it in the database (I use phpmyadmin to modify the database directly).

[http://ubuntuforums.org/showpost.php?p=2535085&postcount=42](http://ubuntuforums.org/showpost.php?p=2535085&postcount=42)

---

### Post by thecoolcat on 2007-12-28
> **newlinux said:**
> Yep, I bet it is a driver issue.

In case I am not around and you don't get the 
"analog options" option here is the post that describes how to do it in the database (I use phpmyadmin to modify the database directly).

[http://ubuntuforums.org/showpost.php?p=2535085&postcount=42](http://ubuntuforums.org/showpost.php?p=2535085&postcount=42)

Alright. I could not find the  "analog options" button.
Now, how do I modify the myth database to edit the capturecard table as mentioned in the link? (I don't know how to use phpmyadmin).

Thanks.

---

### Post by newlinux on 2007-12-28
You have to use some frontend to modify the database. I recommend you use phpmyadmin as it is web based. You need to install it, then log into it over the web (use your whatever credentials you use in mysql.txt for your frontends to connect to the database), select the mythconverg database, and then follow the instructions in the above link. Or if you are familiar with some other frontend to the database use that to modify the mythconverg database.

---

### Post by d9000 on 2007-12-29
Here is another request for help setting up the KWorld ATSC 115 remote.  Has anyone gotten this to work in Ubuntu?  I got the tuner portion to work following this thread and the mythtv wiki, but I don't know how to apply the kernel patch for the remote shown here:

[http://www.mythtv.org/wiki/index.php/User:Vprada#Kernel_Modification](http://www.mythtv.org/wiki/index.php/User:Vprada#Kernel_Modification)

I'm not even sure if this would work with Ubuntu 7.10 - any ideas?

---

### Post by goofygrin on 2007-12-30
I've got two of these (and a 110) in my backend.

You need to manually change the database to slave the analog portions off the digital.  You also need to set the digital portion to allow it to be accessed outside of myth (otherwise the analog portion won't work).

You do the first by updating the parentid in the capturecard table:
Stop Mythbackend before doing this
```

mysql -u mythtv -pmythv mythconverg
select cardid, device from capturecard;
update capturecard set parentid=x where cardid=y; -- obviously set x and y
exit;

```
Now run mythsetup and you should only have one card, but under the sources, you'll see that the DVB card has a little sub card that you assign your analog source.

The second is in the card setup in mythsetup. It's one of the checkmarks (that I can't remember the name of).

---

### Post by thecoolcat on 2007-12-30
> **newlinux said:**
> Yep, I bet it is a driver issue.

In case I am not around and you don't get the 
"analog options" option here is the post that describes how to do it in the database (I use phpmyadmin to modify the database directly).

[http://ubuntuforums.org/showpost.php?p=2535085&postcount=42](http://ubuntuforums.org/showpost.php?p=2535085&postcount=42)

I've installed phpmyadmin.
If I try to go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) using firefox, I get the following page:
---```

Not Found

The requested URL /phpmyadmin was not found on this server.
Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.2 Server at localhost Port 80
```
---
What am I doing wrong? Thanks.

---

### Post by thecoolcat on 2007-12-30
> **goofygrin said:**
> I've got two of these (and a 110) in my backend.

You need to manually change the database to slave the analog portions off the digital.  You also need to set the digital portion to allow it to be accessed outside of myth (otherwise the analog portion won't work).

You do the first by updating the parentid in the capturecard table:
Stop Mythbackend before doing this
```

mysql -u mythtv -pmythv mythconverg
select cardid, device from capturecard;
update capturecard set parentid=x where cardid=y; -- obviously set x and y
exit;

```
Now run mythsetup and you should only have one card, but under the sources, you'll see that the DVB card has a little sub card that you assign your analog source.

The second is in the card setup in mythsetup. It's one of the checkmarks (that I can't remember the name of).

Hi goofygrin,

How do I find the correct cardid and parentid?
Once I get " mysql> ", do I just enter:
```
select cardid 1 
``` if my cardid is a 1?
If I do that, i see "->" and anything I type ends with "->"

Can you help?

---

### Post by thecoolcat on 2007-12-30
> **thecoolcat said:**
> I've installed phpmyadmin.
If I try to go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) using firefox, I get the following page:
---```

Not Found

The requested URL /phpmyadmin was not found on this server.
Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.2 Server at localhost Port 80
```
---
What am I doing wrong? Thanks.

I fixed it by adding a soft link in /var/www for phpmyadmin and now I'm able to access phpmyadmin.

When I go to capturecard, I don't see the following:
```
cardid videodevice audiodevice vbidevice cardtype defaultinput parentid
1 0 DVB DVBInput 0
2 /dev/video0 /dev/dsp1 /dev/vbi0 V4L Television 1

``` as mentioned in this post:
[http://ubuntuforums.org/showpost.php?p=2535085&postcount=42](http://ubuntuforums.org/showpost.php?p=2535085&postcount=42)

How do I edit the capture table? Thanks.

---

### Post by newlinux on 2007-12-30
> **thecoolcat said:**
> I fixed it by adding a soft link in /var/www for phpmyadmin and now I'm able to access phpmyadmin.

When I go to capturecard, I don't see the following:
```
cardid videodevice audiodevice vbidevice cardtype defaultinput parentid
1 0 DVB DVBInput 0
2 /dev/video0 /dev/dsp1 /dev/vbi0 V4L Television 1

``` as mentioned in this post:
[http://ubuntuforums.org/showpost.php?p=2535085&postcount=42](http://ubuntuforums.org/showpost.php?p=2535085&postcount=42)

How do I edit the capture table? Thanks.

make sure you are browsing the capturecard table (click browse at top left). once in browse mode click the pencil to edit a record.

---

### Post by thecoolcat on 2007-12-30
> **newlinux said:**
> make sure you are browsing the capturecard table (click browse at top left). once in browse mode click the pencil to edit a record.

Great. I was able to follow your suggestions! Analog audio and video work without any problem using tvtime while myth backend is running. (I had to run "arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -" in another xterm.
Video via NTSC works now in mythtv. But audio doesn't work even if I run the arecord command. I believe there are many posts on this problem for this tuner card. I guess I'll browse through the web and do some research (unless you know the problem already). You've been of great help!

Another question: I tried setting up s-video and composite inputs. When I set them up, why is mythtv trying to scan the channels? Aren't these sources baseband signals (unmodulated)?

Thanks.

---

### Post by stefanst on 2007-12-31
Hi thecoolcat!

It looks like I am trying an almost identical setup to yours. Thanks to this thread I was able to get some pictures and even some sound!

My setup:
- Mythbuntu 7.10 on an AMD 64 bit system (back- and Frontend)
- Kworld ATSC 115
- The KWorld is set up as two different cards in the backend:
    - /dev/video0 (as an analog card)
    - /dvb:0 (as a "DVB DTV capture card"  digital card) 
    - I did not need to change the databse settings directly- all my seetup work was done via the BE setup
- Comcast basic cable (Philadelphia area)
- Dell Laptop set up as additional Frontend

Remarks:
WIth our digital TV we are able to pick up several digital channels from Comcast. They are just sublisted under several analg channels like "29_1", "29_2", "76_1" and so on.

Here is what I found out and what may help you in your quest:

- I can tune inall the NTSC channels as well as some of our DVB channels (but far from all of them)
- I can switch between "cards" by using the "y" key on the keyboard (switches from Analog to digital)
- I don't get any sound when I run the frontend on my backend/frontend combo (except an annnoying whine for the analog channels)
- I do get sound for the digital channels on my othe frontend!
- When I record digital channels and 
                      play them back as recordings on my BE/FE I don't get sound
                      play them back as an mpeg on my BE/FE I get sound!

That means to me that there's soemthing with the FE setup screwy on my BE/FE box


Does anybody know the secret to picking up all the DVB channels broadcast by Comcast?

Thanks and keep trying :-)

---

### Post by newlinux on 2007-12-31
> **stefanst said:**
> Hi thecoolcat!

It looks like I am trying an almost identical setup to yours. Thanks to this thread I was able to get some pictures and even some sound!

My setup:
- Mythbuntu 7.10 on an AMD 64 bit system (back- and Frontend)
- Kworld ATSC 115
- The KWorld is set up as two different cards in the backend:
    - /dev/video0 (as an analog card)
    - /dvb:0 (as a "DVB DTV capture card"  digital card) 
    - I did not need to change the databse settings directly- all my seetup work was done via the BE setup



Setting it up as two different cards can cause problems. e.g. -- Myth won't know they are the same card when you try to schedule an analog and digital recording at the same time that are both on that card, which means you'll have problems with the recordings and possibly screw something up (you can only record one thing on that card at a time, it is not a dual tuner). If you set it up as one card you won't have this problem.
> 
- Comcast basic cable (Philadelphia area)
- Dell Laptop set up as additional Frontend

Remarks:
WIth our digital TV we are able to pick up several digital channels from Comcast. They are just sublisted under several analg channels like "29_1", "29_2", "76_1" and so on.

Here is what I found out and what may help you in your quest:

- I can tune inall the NTSC channels as well as some of our DVB channels (but far from all of them)
- I can switch between "cards" by using the "y" key on the keyboard (switches from Analog to digital)


"y" actually just switches between cards, which works since you have myth setup to think it is two different cards.
> 
- I don't get any sound when I run the frontend on my backend/frontend combo (except an annnoying whine for the analog channels)
- I do get sound for the digital channels on my othe frontend!
- When I record digital channels and 
                      play them back as recordings on my BE/FE I don't get sound
                      play them back as an mpeg on my BE/FE I get sound!

That means to me that there's soemthing with the FE setup screwy on my BE/FE box


Sounds like a correct diagnosis. Do you get sound out of files you watch with mythvideo on your frontend that is giving you problems? What kind of sound output do you have setup (spdif, line out, etc.) What do you have myth's output sound device set to?

> 
Does anybody know the secret to picking up all the DVB channels broadcast by Comcast?

Thanks and keep trying :-)

You can only tune unencrypted QAM channels with a QAM tuner--with most cable providers in most regions what you'll mostly get are the locals (in HD and sometimes also in standard def), shopping channels, and a few random stations. Also, you can remap the stations to different numbers in myth if you don't like 29.1, 76.1, etc.)

---

### Post by stefanst on 2008-01-01
I am getting closer to a solution, but still have a little way to go.
thecoolcat: sorry for hijacking your thread,m but this seems so similar, that I figured we join forces... 
newlinus: I will try your setup suggestion with the "split" card. I did get some crashes of back- and frontends, probably attributable to the duplicate use of the same card.

Analog TV (NTSC):

When I set up the Audio-Device on the analog card to:
DSP1 -> I get sound and video feed, but the voices are squeaky high and the video is interrupted every two seconds or so for maybe half a second and then picks up again where it left off. The same stream *recorded* plays without interruption but too fast and still with the squeaky voices. Looks like the card tries to use a wrong sampling rate... I am clueless here :-(

DSP -> No sound whatsoever
Not e ven when playing back from a recording or on the other frontend- nothing. 

NONE -> Same as DSP

No other settings on the audio part of the setup for the card seem to have ANY effect at all.

It looks to me like the setting "DSP1" is correct, but what the bleep messes with my sampling rate for video and audio?

Digital:
Our Digital TV picks up digital channels from the same cable connection. However, even without having any decoder card or other gizmos, the TV picks up lots of channels the Kworld Card does not get. The ones that the KWorld card gets are also picked up by the TV. I tried going through all combinations of broadcast signals, but I just find those channels.

They both get the sub-channels to analog channel 76 and 77, but the TV also gets sub-channels for analog channel 1,9,29 etc...

Thanks again. Any more ideas/tips?

---

### Post by am_pcguy on 2008-01-02
I've got a Mythbuntu 7.10 setup with the Kworld 115 as well.

I've tried everything to get the card to do NTSC video and audio at the same time.  After asking multiple times in various forums and IRC channels I've given up.  In fact on the MythTV IRC channel I was told to forget it, as the recordings would be poor quality because there is no hardware mpeg2 encoder on the card and it wasn't worth the time I was putting into it.  I had just decided to get a Hauppauge pvr-150 for NTSC recordings. 

I was not aware of the "hack" to make the NTSC tuner a child of the ATSC tuner and I may try that when I get a chance.

---

### Post by thecoolcat on 2008-01-02
> **stefanst said:**
> I am getting closer to a solution, but still have a little way to go.
thecoolcat: sorry for hijacking your thread,m but this seems so similar, that I figured we join forces... 
Absolutely!
> **stefanst said:**
> newlinus: I will try your setup suggestion with the "split" card. I did get some crashes of back- and frontends, probably attributable to the duplicate use of the same card.
As suggested by newlinux, I used phpmyadmin to edit the myth database. It was pretty useful. I used this to change my audio device for analog NTSC.

> **stefanst said:**
> Analog TV (NTSC):
When I set up the Audio-Device on the analog card to:
DSP1 -> I get sound and video feed, but the voices are squeaky high and the video is interrupted every two seconds or so for maybe half a second and then picks up again where it left off. The same stream *recorded* plays without interruption but too fast and still with the squeaky voices. Looks like the card tries to use a wrong sampling rate... I am clueless here :-(
I'm having the same problem as well. The saa7134-alsa module is loaded in /dev/dsp1 for me also. From other posts I found out that  the audiorate should be set to 32000 (32KHz) to avoid this problem. Now I don't know where to set this option.
> **stefanst said:**
> DSP -> No sound whatsoever
Not e ven when playing back from a recording or on the other frontend- nothing. 
I wish it worked! But as I said, for saa7134, alsa module is your best bet which will be /dev/dsp1. So now I'm just working on trying to set the audio rate to 32KHz to avoid the high-pitch sound.

---

### Post by newlinux on 2008-01-02
> **am_pcguy said:**
> I've got a Mythbuntu 7.10 setup with the Kworld 115 as well.

I've tried everything to get the card to do NTSC video and audio at the same time.  After asking multiple times in various forums and IRC channels I've given up.  In fact on the MythTV IRC channel I was told to forget it, as the recordings would be poor quality because there is no hardware mpeg2 encoder on the card and it wasn't worth the time I was putting into it.  I had just decided to get a Hauppauge pvr-150 for NTSC recordings. 

I was not aware of the "hack" to make the NTSC tuner a child of the ATSC tuner and I may try that when I get a chance.

I found the video quality of it to be fine - about equal to my PVR-150. The audio quality was much worse at the beginning... but a few tweaks with the audio settings got it to be pretty good. That said, I had problems with the audio consistently working (however it always worked in tvtime). Since it wasn't reliable enough for me I don't use the analog side anymore.

---

### Post by thecoolcat on 2008-01-02
> **am_pcguy said:**
> I've got a Mythbuntu 7.10 setup with the Kworld 115 as well.

I've tried everything to get the card to do NTSC video and audio at the same time.  After asking multiple times in various forums and IRC channels I've given up.  In fact on the MythTV IRC channel I was told to forget it, as the recordings would be poor quality because there is no hardware mpeg2 encoder on the card and it wasn't worth the time I was putting into it.  I had just decided to get a Hauppauge pvr-150 for NTSC recordings. 

I was not aware of the "hack" to make the NTSC tuner a child of the ATSC tuner and I may try that when I get a chance.

Not having a hardware mpeg2 encoder should not be a problem as long as your CPU is good enough.
On getting a pvr-150, please be aware that some of the pvr-150 purchased have HVR-1600 inside the box. While you may think that it is a good buy, it is not currently supported as there are currently no Linux drivers! But if you do manage to get a pvr-150, make sure you get the one with the MCE remote (that has both IR receiver and blaster) which you can use it to control cable/dish set-top box if necessary. I believe the remote is supported unlike the KWorld atsc 115 (which doesn't work OTB and which I haven't got it to work).

---

### Post by stefanst on 2008-01-02
I just figured something else out:

According to the LinuxTV wiki, the latest Kernel as used in Hardy Heron (2.6.24-2) supports the KWorld ATSC 115 directly out of the box by automatically forcing it to behave like the ATSC 110.

So I upgraded my Kernel and it did indeed recognize it out of the box as an ATSC 110/115, just as promised. Unfortunately now I experienced the problem that the NTSC-Analog picture will come on for a second and then go away. Still no sound, even when downsampling the audio-rate to 32KHz.  And I couldn't get the DVB to lock on ANY channel, even though I got a good signal

I removed the added lines from the /etc/modules and the /etc/modprobe.conf and rebooted- no change in behavior, but it still recognized the card!

Changed back to the old kernel and added the lines back the /etc/modules and /etc/modprobe.conf and I'm back to where I was before.

We'll keep a-tryin'

---

### Post by thecoolcat on 2008-01-02
> **stefanst said:**
> I just figured something else out:

According to the LinuxTV wiki, the latest Kernel as used in Hardy Heron (2.6.24-2) supports the KWorld ATSC 115 directly out of the box by automatically forcing it to behave like the ATSC 110.

So I upgraded my Kernel and it did indeed recognize it out of the box as an ATSC 110/115, just as promised. Unfortunately now I experienced the problem that the NTSC-Analog picture will come on for a second and then go away. Still no sound, even when downsampling the [COLOR="Red"]audio-rate to 32KHz[/COLOR].  And I couldn't get the DVB to lock on ANY channel, even though I got a good signal

I removed the added lines from the /etc/modules and the /etc/modprobe.conf and rebooted- no change in behavior, but it still recognized the card!

Changed back to the old kernel and added the lines back the /etc/modules and /etc/modprobe.conf and I'm back to where I was before.

We'll keep a-tryin'

Hi stefanst: The "no audio" problem can be easily solved. Identify which device your saa7134-alsa is pointing to. May be the kernal was not loading the alsa module when you did the upgrade? Now I have one question for you: How did you downsample the audio-rate to 32KHz when you upgraded the kernal? For me, I get audio but it is high-pitched and not intelligible. So as I mentioned earlier, I want to set my audio sampling rate to 32KHz.

---

### Post by stefanst on 2008-01-02
Hi thecoolcat!

How do I figure out, where my ALSA driver is pointing to?

Changing the sampling frequency was directly in the card configuration. Take a look at the attached screenshot:

[http://picasaweb.google.com/sympatec/MythTV/photo#5151021623131150194]("http://picasaweb.google.com/sympatec/MythTV/photo#5151021623131150194")

Good luck!

---

### Post by thecoolcat on 2008-01-03
> **stefanst said:**
> Hi thecoolcat!

How do I figure out, where my ALSA driver is pointing to?

Changing the sampling frequency was directly in the card configuration. Take a look at the attached screenshot:

[http://picasaweb.google.com/sympatec/MythTV/photo#5151021623131150194]("http://picasaweb.google.com/sympatec/MythTV/photo#5151021623131150194")

Good luck!

Execute arecord -l on an xterm. This will list your audio devices. For me here's the output:
```
desktop:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 1: Intel ICH - MIC ADC [Intel ICH5 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 2: Intel ICH - MIC2 ADC [Intel ICH5 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 3: Intel ICH - ADC2 [Intel ICH5 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SAA7134 [SAA7134], device 0: SAA7134 PCM [SAA7134 PCM]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by stefanst on 2008-01-03
> **thecoolcat said:**
> Execute arecord -l on an xterm. This will list your audio devices. For me here's the output:
```
desktop:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 1: Intel ICH - MIC ADC [Intel ICH5 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 2: Intel ICH - MIC2 ADC [Intel ICH5 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 3: Intel ICH - ADC2 [Intel ICH5 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SAA7134 [SAA7134], device 0: SAA7134 PCM [SAA7134 PCM]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Did that- my output looks very similar:
```

card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SAA7134 [SAA7134], device 0: SAA7134 PCM [SAA7134 PCM]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I noticed, that in hte setup page (see the attched screenshot in my previous post) all I coud select for audio device is "dsp", "dsp1", or "<none>". Nothing that seems like ALSA here....

Thanks so far!

Stefan

---

### Post by stefanst on 2008-01-03
OK, I did a little more reading and realized that with my configuration the "dsp1" device is the one I should be using. 
As I stated earlier in this thread, this is when I get audio and video, but the video feed is choppy (stops every two seconds or so for a half a second) and the sound is squeaky high with the same interruption as the video. When I record this, I get a continuous video with continuous audio, but both are two fast- sort of like playing an old 33rpm record at 45rpm. 

Some frequency seems to get screwed up when I use the dsp1 input. I googled the living daylights out of this problem, but can't seem to get anywhere....

When I select dsp0 for my audio input, I don't get sound, but the video plays smooth and at normal speed. Of course I can then also use the line output from the ATSC card and plug it into my soundcard line input and get good sound, but of course it is then ahead of the video....

Update on the Kernel:

2.6.24 does detect the KWorld ATSC 115 properly and forces it to be recognized as the ATSC 110 automatically!

Thanks for your patience!

Stefan

---

### Post by thecoolcat on 2008-01-03
> **stefanst said:**
> Did that- my output looks very similar:

I noticed, that in hte setup page (see the attched screenshot in my previous post) all I coud select for audio device is "dsp", "dsp1", or "<none>". Nothing that seems like ALSA here....

Thanks so far!

Stefan

Additionally if you do "dmesg|grep -i saa" you'll see something like this:
```
saa7134 ALSA driver for DMA sound loaded
saa7133[0]/alsa: saa7133[0] at 0xf5006000 irq 19 registered as card 1
```

---

### Post by thecoolcat on 2008-01-03
> **stefanst said:**
> OK, I did a little more reading and realized that with my configuration the "dsp1" device is the one I should be using. 
As I stated earlier in this thread, this is when I get audio and video, but the video feed is choppy (stops every two seconds or so for a half a second) and the sound is squeaky high with the same interruption as the video. When I record this, I get a continuous video with continuous audio, but both are two fast- sort of like playing an old 33rpm record at 45rpm. 

Some frequency seems to get screwed up when I use the dsp1 input. I googled the living daylights out of this problem, but can't seem to get anywhere....

When I select dsp0 for my audio input, I don't get sound, but the video plays smooth and at normal speed. Of course I can then also use the line output from the ATSC card and plug it into my soundcard line input and get good sound, but of course it is then ahead of the video....

Update on the Kernel:

2.6.24 does detect the KWorld ATSC 115 properly and forces it to be recognized as the ATSC 110 automatically!

Thanks for your patience!

Stefan

Exactly the same story for me as well. The audio rate for the recording options in mythtv is also set at 32000. I don't  know how to fix the high pitched sound.

---

### Post by stefanst on 2008-01-03
Alright- I am fairly certain that it's a bug in MythTV at this point.

Using the following:

```
mplayer tv://"insert channel" -tv driver=v4l2:device=/dev/video0:chanlist=us-cable:alsa:\
adevice=hw.1,0:amode=1:audiorate=32000:forceaudio:volume=100:immediatemode=0:norm=NTSC
```

I get  perfect video and sound out of mplayer- just like one would wish for. 

When I issue the same command, but with a higher sampling frequency, i.E.:

```
mplayer tv://"insert channel" -tv driver=v4l2:device=/dev/video0:chanlist=us-cable:alsa:\
adevice=hw.1,0:amode=1:audiorate=48000:forceaudio:volume=100:immediatemode=0:norm=NTSC
```

I get the squeaky sound with the frequent stops, just like I get in MythTV. So the frequency setting in the MythTV backend seems to not be working- no matter what I set it to, I get the squeaky sound. Seems like I have to look at the MythTV mailing list- maybe there's something there.

---

### Post by thecoolcat on 2008-01-04
Analog is working now!!!
At the main screen, go to Setup / Utilities -> Setup -> General -> the Audio page.  Here, the sound device is the OUTPUT device and should be configured as the ALSA device.  For me, this field is  ALSA:default.  I changed to /dev/dsp1 and there was no audio.. I changed it back to ALSA: default and it started working. Don't know how!

---

### Post by thecoolcat on 2008-01-04
> **stefanst said:**
> Alright- I am fairly certain that it's a bug in MythTV at this point.

Using the following:

```
mplayer tv://"insert channel" -tv driver=v4l2:device=/dev/video0:chanlist=us-cable:alsa:\
adevice=hw.1,0:amode=1:audiorate=32000:forceaudio:volume=100:immediatemode=0:norm=NTSC
```

I get  perfect video and sound out of mplayer- just like one would wish for. 

When I issue the same command, but with a higher sampling frequency, i.E.:

```
mplayer tv://"insert channel" -tv driver=v4l2:device=/dev/video0:chanlist=us-cable:alsa:\
adevice=hw.1,0:amode=1:audiorate=48000:forceaudio:volume=100:immediatemode=0:norm=NTSC
```

I get the squeaky sound with the frequent stops, just like I get in MythTV. So the frequency setting in the MythTV backend seems to not be working- no matter what I set it to, I get the squeaky sound. Seems like I have to look at the MythTV mailing list- maybe there's something there.

I'll have to agree with you on this! I don't know why it is working for me now, all I did was changed frontend audio setup and reverted it back. 
I'm still having an issue with switching from DVB -> Analog and the channel not tuning without switching to another analog station and then back. Almost as if the dvb dev isn't releasing the tuner.
Did you get composite/s-vdo to work?

---

### Post by am_pcguy on 2008-01-08
> **thecoolcat said:**
> Not having a hardware mpeg2 encoder should not be a problem as long as your CPU is good enough.
On getting a pvr-150, please be aware that some of the pvr-150 purchased have HVR-1600 inside the box. While you may think that it is a good buy, it is not currently supported as there are currently no Linux drivers! But if you do manage to get a pvr-150, make sure you get the one with the MCE remote (that has both IR receiver and blaster) which you can use it to control cable/dish set-top box if necessary. I believe the remote is supported unlike the KWorld atsc 115 (which doesn't work OTB and which I haven't got it to work). I ordered a pvr-150, and a irblaster from irblaster.info. It was cheaper than the pvr-150 with the remote and irblaster.  Is the card going to say HVR-1600 on it when I open the box?  I'll just return it if it's not what I ordered.

I had all of the same problems you are describing. High pitched sound, fast audio, and I had audio with no video at one point.  I had the analog working at one point and the HD tuner quit working.  Like newlinux said he got it working but it wasn't reliable.  I would love for it to work but I don't think it's going to happen.  I put more than $50 worth of my own time into trying to fix my, I cut my losses and bought another card.

---

### Post by thecoolcat on 2008-01-10
> **am_pcguy said:**
> I ordered a pvr-150, and a irblaster from irblaster.info. It was cheaper than the pvr-150 with the remote and irblaster.  Is the card going to say HVR-1600 on it when I open the box?  I'll just return it if it's not what I ordered.

True. I believe you'd see a letter from Hauppauge saying that they have replaced it. On a different note, folks have started working on drivers for HVR-1600. Here's a link: [http://ivtvdriver.org/index.php/Cx18](http://ivtvdriver.org/index.php/Cx18). As you can see many features are still not working for this card. PVR-150 will be best as you can just open a thread and get support from the community.

> I had all of the same problems you are describing. High pitched sound, fast audio, and I had audio with no video at one point.  I had the analog working at one point and the HD tuner quit working.  Like newlinux said he got it working but it wasn't reliable.  I would love for it to work but I don't think it's going to happen.  I put more than $50 worth of my own time into trying to fix my, I cut my losses and bought another card.

I have to agree with you on this!

---

### Post by am_pcguy on 2008-01-11
I bought the pvr-150 card from Amazon it came today, and was a pvr-150 not the 1600.  I installed the card Mythbuntu found it and it was working in minutes.  Now I'm trying to figure out how to configure LIRC for the IRBLASTER.  The fun never ends.

---

### Post by thecoolcat on 2008-01-16
Seems to have been pretty stable for 5 days. Still have issues switching between ATSC and analog. Marking it as solved.

---

### Post by Lido on 2008-01-16
Would you mind posting screenshots of your backend setup that got atsc working for you? Card setup screens, Input Connections and channel scan settings? I'm having some trouble here:

[http://ubuntuforums.org/showthread.php?p=4149194](http://ubuntuforums.org/showthread.php?p=4149194)

---

### Post by themacks on 2008-06-21
I have been experiencing the same issues described above, QAM HD works fine but NTSC shows for a second then goes black, deleting the DVB capture card lets the NTSC work, but with the same audio issues,

the version of mythtv that I'm running ( 0.21.20080304-1 16838 ) doesn't have the parentid field in the database so I'm unable to like the tuners together in that manner, any ideas?

---

