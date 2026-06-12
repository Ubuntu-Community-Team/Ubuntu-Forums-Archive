---
title: "Acer aspire one can not record voice from mic"
date: 2008-10-19
forum: Multimedia Software
---

### Post by kmresh on 2008-10-19
hi,

i have Acer aspire one , when using sound recorder,recoding going after that recording its not play.. whats the problem,

I think the microphone is not get any sound.or sound card driver problem.

Kindly advice me..

---

### Post by kmresh on 2008-10-19
i have gotten everything working on Acer aspire one but microphone only not working.

please help!!

---

### Post by overdrank on 2008-10-19
Hi and please do not create multiple threads on the same issue. Threads merged :)

---

### Post by TenPlus1 on 2008-10-19
Try going into System -> Preferences -> Multimedia System Selector and changing the defauly input to OSS, that worked for me...

---

### Post by arfalconi on 2008-10-20
First check the suggestions on:
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

Try commenting the following line on /etc/rc.local  (if you added it previously):
#echo 10 > /sys/module/snd_hda_intel/parameters/power_save

Doble click on the small speaker icon on the task bar, select preferences and mark all the options, after this you should see two more tabs on the volume control window.

Go to the "Recording" tab" and increase the volume for "Capture", the two icons below this control should be enabled.

Go to the "Options" tab and select as "Input Source" Mic

On software like Skype, select HDA Intel (hw:intel,0) for the Sound In option.

If you got the mic working now, play with the options on the Volume control "Front Mic Boost" (Playback Tab), Capture and Capture 1 (Recording tab) and Input Source (Options tab).

-Ariel

---

### Post by kmresh on 2008-10-20
Dear Ariel,

Thank you your reply, 


when going to record the my voice , its recording ,

but not record my voice ,

record output its getting dissonance noise only ,

Kindly advice!

sorry for late reply!!


kmresh
######

---

### Post by kmresh on 2008-10-22
Anybody help me the above problem ,, now i am really struck !!!

---

### Post by martin_h on 2008-10-30
I have a 150 (120gb/512) and struggled with the same prolbem even after following the instructions from the [https://help.ubuntu.com/community/AspireOne]("https://help.ubuntu.com/community/AspireOne"). I went through the motions and it would not work. 

At this threat [http://ubuntuforums.org/showthread.php?t=707231]("http://ubuntuforums.org/showthread.php?t=707231")  i found a reference to another way of approaching the problem and it worked for me. It is a bit of experimenting if it is front_mic or just mic and there is some noise in the background. Not perfect, but there is life. 

Note that the solution is for another model, so don get confused by that. 

good luck.

---

### Post by kmresh on 2008-10-31
hai am  installed ubuntu latest version ,

now it 's working

thank you for your valuable reply and support!!

reds

kumarez.com

---

### Post by jens83 on 2008-10-31
kmresh how did you fix the problem? others (like me) would like to know.

---

### Post by blackest_knight on 2008-11-02
Alsa really needs to be version 1.0.17 (default with intrepid) or 1.0.18 which is better for an aspire one. Hardy is a bit behind and will have more issues.
hence install intrepid and audio will work from the off (more or less). 

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

has 2 methods for updating Alsa, so the audio hardware is fully supported. 

I've got a related issue, my settings are not restored after reboot. 

sudo alsactl store saves them
sudo alsactl restore restores them but i havent got a method to have them restored after reboot.  dropping /sbin/alsactl restore into rc.local  doesnt do it. so I am stuck at this point.

---

### Post by eks on 2009-01-01
Hello,

I have been for a few days trying to find the microphone without success. The weird thing is, on the first time I've installed Xubuntu on the Aspire One the microphone and everything audio related worked out of the box without any tweak. Now on the second, also Intrepid Ibex, I've already tried, I think, all of the options searching for the microphone without success.

**Is there an easier way to *SEARCH* for the microphone? Without having to go through each capture, digital, input boost, mic, front mic, line in, option there is available? Something with the command line maybe?**

lspci -vv just returns 

```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 015b
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at 38540000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [70] Express (v1) Root Complex Integrated Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed unknown, Width x0, ASPM unknown, Latency L0 <64ns, L1 <1us
			ClockPM- Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed unknown, Width x0, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

Without actually telling me which devices I have and where are them.

---

### Post by MrPage on 2009-05-08
I have a brand new aspire one 8.9 running 9.04 UNR (Ubuntu Netbook Remix)

and this is still an issue.
yes it's define in launch pad - I just don't know what the hold up is.
If people can fix it with friggin around, why can't those changes go into the packaging?

except: I've tried going through all of the inputs and check boxes and can't find the working sequence.

---

### Post by rreyes1316 on 2009-05-28
Has anyone fixed the mic? I have been looking for a solution to this problem and have been unsuccessful. I have UNR installed on an Aspire One 10" D150. My Mic does not work with Skype I have made sure that the mic is not on mute in the volume control and also tried to change the audio setting under the Preferences. I have done a complete reinstall and made sure to install medibuntu, restricted extras, keyring, and all codecs. This is just not working. I have tried to download the latest alsa drivers but do not know how to compile them for install or back up the old drivers just in case. Later, It occurred to me that perhaps I should try another app. Sure enough, the mic did not record using other mic supported apps. So that rules out skype as the problem. 

Anyone have a solution?

---

### Post by marvin.engl on 2009-05-31
Hi, this is my first entry on the forum, so I hope I meet all the standards.
 

 I had the same problem as outlined: microphone not working, impossible to get Skype set-up. Audio output was OK, but I could not get the sound input working.  
 

 My starting point:
 

 Acer Aspire One, A110L (512 Mbyte RAM, 16 Gbyte SDRAM storage, no HDD, Limpus Unix pre-installed, but replaced with Ubuntu UNR 9.04 “Intrepid Ibis”).
 

 What worked for me:
 

 It appeared that a) the various drivers were all over the place b) the standard microphone setting seems to be “off”.
 

 Step 1: setting all the drivers to OSS.
 

 a)  
 

 [Preferences] [Sound]  
 Leave “Audio Conference – Sound playback” at “Auto detect”
 Set “Audio Conference – Sound capture” to “OSS – Open Sound System”.
 

 Other settings (top down):
 Sound Events: “Auto detect”
 Music and Movies: “Auto detect”
 Default Mixer Tracks: “Realtek ALC268 (OSS Mixer)”
 [X Close]
 

 b)  
 Single-click speaker icon in the top right corner of the UNR desktop.
 [Volume Control]
 [Preferences]
 Tick “In-Gain Playback”
 [X Close] &#8594; This will close the [Preferences] window and display two scroll selections: “Volume” (was there before) and “In-gain” (which is new).
 

 Set “Device” to “Realtek ALC268 (OSS Mixer)”
 

 Move both “Volume” and “In-gain” to the very top. Make sure the speaker icons do **not** indicate “mute”.
 [X Close]
 

 

 Step 2 - Go back to Skype:
 

 [Internet] [Skype]  
 Login with you user name and password
 Click the Skype icon at the bottom of the window.
 [Options]
 [Sound Devices]
 

 Set “Sound Devices” to:
 

 Sound In: “HDA intel (hw:Intel,0)
 Sound Out: “HDA intel (hw:Intel,0)
 Ringing: “Pulse”
 

 Now comes the interesting bit!
 

 [Make a test call]
 

 Remember that the build-in microphone (two inches left of the webcam) is very, very weak. I had to move my mouth just in front of it in order to get picked up.  
 

 However, it worked!
 

 Hope this fairly simple approach will solve your problem as well!
 

 Good luck!

---

### Post by llazarte on 2009-06-06
Thanks for an excelent summary. After spending the best part of the weekend trying to solve the problem of using Skype with Ubuntu Netbook Remix 9.04 on an AspireOne, I would like to add a few comments to the recipe above.

**Hardware**: Acer AspireOne D150-1669 (manufactured on march 2009), CPU Atom N270 @1.6GHz, 2GB RAM, 160GB HD, 10.1" screen.

**OS**: Ubuntu Netbook Remix 9.04, dated April 17, updated June 6. (I kept the original Windows XP Home edition on another partition).

**Skype**: version 2.0.0.72

**The bottom line:**

[LIST=1]
[*]Now I can use Skype, with an external microphone.
[*]The built-in microphone is still not accessible.
[/LIST]
 **What worked:**

[LIST]
[*]Understanding that the problem was not only with Skype. The microphone was not working (seen as disabled by Clicking once on the small loudspeaker -> Clicking on Volume Control -> then, clicking on the recording tab (if available).
[LIST]
[*]Beware that there are several suggestions of disabling pulseaudio, uninstalling it, removing and reinstalling Skype, etc.
[*]There is one possible solution which I did not try which is installing the latest alsa driver (1.0.20 as of this writing).
[/LIST]
 
[*]Changing the default sound options form ALSA (default), to _**OSS**_ (as instructed by the above post, which I reproduce with small changes):
[LIST=1]
[*]Click twice on the ubuntu icon on the top left of the screen;
[*]Select Preferences, then Sound;
[*]Leave all options as "autodetect", exept for:
[LIST]
[*]Conference audio -> Sound Capture: select _OSS - Open Sound System_, and
[*]Default Mixer Tracks -> Device: select _Realtek ALC272_ (OSS Mixer) [this identification could vary depending on your version of the sound card];
[*]I did select all three options within Default Mixer Tracks: Volume, PCM-2 and In-gain, by clicking on all of them while pressing shift;
[/LIST]
 
[*]Close the sound preferences window.
[/LIST]
 
[*]Change the sound options on the volume control:
[LIST=1]
[*]Click once on the small loudspeaker icon on the top right of the screen;
[*]Click on volume control;
[*]Select your device as Realtec ALC272 (OSS Mixer). That will change the options which are shown;
[*]Go to Preferences, and select all three options to be shown: Volume, PCM-2 and In-gain. Close the preferences window;
[*]Check that all three are active (the loudspeaker does not show a red sign);
[*]Close the Volume Control window.
[/LIST]
 
[*]Change the sound settings on Skype:
[LIST=1]
[*]Click on the Ubuntu icon on the top left corner of the screen;
[*]Select Internet, then Skpe;
[*]Login into Skype whith your username and password;
[*]Click on the bottom left of Skype's window, then choose Options;
[*]In the "general" tab, select "sound devices";
[*]For sound input, select HDA Intel (hw:Intel,0);
[*]For Sound output, select "pulse";
[*]For Ringing, selct "pulse".
[*]Click Apply;
[*]Make a test call. (I hope after all this effort, the call will be successfull) :D
[/LIST]
 
[/LIST]
 **NB**: In my case, I was not lucky with my built-in microphone. I even tried to imagine that I was hearing some very weak sound, but no, that was just static. Fortunately, with an external micro, I can now communicate with the world!



> **marvin.engl said:**
> Hi, this is my first entry on the forum, so I hope I meet all the standards.
 

 I had the same problem as outlined: microphone not working, impossible to get Skype set-up. Audio output was OK, but I could not get the sound input working. 
 

 My starting point:
 

 Acer Aspire One, A110L (512 Mbyte RAM, 16 Gbyte SDRAM storage, no HDD, Limpus Unix pre-installed, but replaced with Ubuntu UNR 9.04 “Intrepid Ibis”).
 

 What worked for me:
 

 It appeared that a) the various drivers were all over the place b) the standard microphone setting seems to be “off”.
 

 Step 1: setting all the drivers to OSS.
 

 a)  
 

 [Preferences] [Sound]  
 Leave “Audio Conference – Sound playback” at “Auto detect”
 Set “Audio Conference – Sound capture” to “OSS – Open Sound System”.
 

 Other settings (top down):
 Sound Events: “Auto detect”
 Music and Movies: “Auto detect”
 Default Mixer Tracks: “Realtek ALC268 (OSS Mixer)”
 [X Close]
 

 b)  
 Single-click speaker icon in the top right corner of the UNR desktop.
 [Volume Control]
 [Preferences]
 Tick “In-Gain Playback”
[X Close] &#8594; This will close the [Preferences] window and display two scroll selections: “Volume” (was there before) and “In-gain” (which is new).
 

 Set “Device” to “Realtek ALC268 (OSS Mixer)”
 

 Move both “Volume” and “In-gain” to the very top. Make sure the speaker icons do **not** indicate “mute”.
 [X Close]
 

 

 Step 2 - Go back to Skype:
 

 [Internet] [Skype]  
 Login with you user name and password
 Click the Skype icon at the bottom of the window.
 [Options]
 [Sound Devices]
 

 Set “Sound Devices” to:
 

 Sound In: “HDA intel (hw:Intel,0)
 Sound Out: “HDA intel (hw:Intel,0)
 Ringing: “Pulse”
 

 Now comes the interesting bit!
 

 [Make a test call]
 

 Remember that the build-in microphone (two inches left of the webcam) is very, very weak. I had to move my mouth just in front of it in order to get picked up. 
 

 However, it worked!
 

 Hope this fairly simple approach will solve your problem as well!
 

 Good luck!

---

### Post by micdhack on 2009-06-12
Problem still existis. i have an acer aspire one d150-bw. What if we updated to latest alsa?

UPDATE: I decided to go on with the source installation

```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2
tar xjvf alsa-driver-1.0.20.tar.bz2
cd alsa-driver-1.0.20
sudo apt-get install build-essential module-assistant
sudo m-a update
sudo m-a prepare
./configure --with-cards=all
make
sudo make install 
```

After the installation, unmute the appropriate channels and you will have sound and mic working.

---

### Post by PerJensen on 2009-06-14
I have an Acer One, model ZG5 with SSD and no harddisk.

OS: Jaunty Remix

Built in recorder app. worked out of the box.

Skype 2.0.0.72 sound options:
==============================
Sound out: pulse
Ringing:  pulse
Sound in: HDA Intel (hw:Intel:0)

Video: works out of the box


/Per

---

### Post by meeples on 2009-06-14
i have an aspire one, had no idea it even had a mic in it till i was testing with skype between my 2 computers and heard my voice. thats after maybe 6 months of having it LOL

---

### Post by mervmjc on 2009-06-20
Thank you llazarte.  Your guide worked a treat :-)

---

### Post by llazarte on 2009-07-12
> **mervmjc said:**
> Thank you llazarte.  Your guide worked a treat :-)

I'm glad it worked for someone else! ;)

As it did not work for others, I wander if there are small variations in hardware, or if there is something intrinsically unstable, either with ALSA, or with Skype (or both! :confused: )

---

### Post by johnsky on 2009-07-15
Micdhack was right on the money.

This worked on the following :
ACER ASPIRE 1 D150
Freshly Installed UNR 9.04

First, you will need to use this code in terminal.

> wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2)
tar xjvf alsa-driver-1.0.20.tar.bz2
cd alsa-driver-1.0.20
sudo apt-get install build-essential module-assistant
sudo m-a update
sudo m-a prepare
./configure --with-cards=all
make
sudo make install

(Scroll up to Micdhack's post if you can't see all of it.)

The above code should take about 20 minutes to do... so have patience with the make commands.

Credit goes to user : Micdhack on Ubuntuforums.org for the code segment.

Don't bother trying to check what it did just yet, you will want to restart first.

After restarting, go to Preferences > Sound.
Change the sound capture option to : OSS (Open Sound System)
Close the sound options.

Now open your Volume Control settings by clicking on the speaker icon top right. Click Volume Control.
In the Device drop-down, select [Realtek ALC272 (OSS Mixer)]
Click on the Preferences button.
Place a check-mark next to In-Gain.
Close this small window.
Slide the newly available In-Gain slider to the top.
Close Volume Control.

Open sound recorder, hit record, viola! The interference from inside the room can't be eliminated as far as I can tell, the mic is a tiny mic and is very sensitive to higher frequency sounds.


I wrote a guide regarding this here :
[http://seventhverse.blogspot.com/2009/07/unr-904-aspire-one-d150.html](http://seventhverse.blogspot.com/2009/07/unr-904-aspire-one-d150.html)

I also covered Cheeze, and Online Flash based Webcam Apps on that guide.


As I said, that works for UNR9.04 on ASPIRE1 D150, I don't know if it will help other units.

---

### Post by espee838 on 2009-07-22
thanks so much Micdhack & johnsky.....that did the trick for me!

---

### Post by a2cno on 2009-07-31
Hi Johnsky,

I tried to upgrade my alsa driver to 1.0.20 just like you wrote. However, it is still using the old driver (which is 1.0.16). I did it 3x, but still the same. The library is changed to 1.0.20, but not the driver and utils...:(. Any idea how to solved? Thx.

---

### Post by barlaventoexpert on 2009-09-24
Thanks also here!

Acer Aspire ZG5
Ubuntu 9.0.4 UNR
Implemented above script using alsa-driver-1.0.21.tar.bz2.

Fixed tinny static filled Skype service to serviceable quality.

Many Thanks

---

### Post by micdhack on 2009-09-24
i upgraded to ubuntu 9.10 unr and the problem seems to have been fixed out of the box. Although, because it is currently as Alpha version, it has lots of quirks and bugs so i wouldnt recommend an upgrade.
So if your problem is the mic just apply the procedure thats been given in this topic.

barlaventoexpert can you verify that 1.0.21 version can fix the problem too?

---

### Post by llazarte on 2009-09-27
> **micdhack said:**
> i upgraded to ubuntu 9.10 unr and the problem seems to have been fixed out of the box. Although, because it is currently as Alpha version, it has lots of quirks and bugs so i wouldnt recommend an upgrade.

I am currently using an eeePC with 9.10. When karmic koala gets stable, I'll see if my wife lets me update her Aspire One :) to check if the internal mic is working with Skype.

---

### Post by Eyebee on 2009-10-19
> **marvin.engl said:**
> Hi, this is my first entry on the forum, so I hope I meet all the standards.
 
....
 

 Hope this fairly simple approach will solve your problem as well!
 

 Good luck!

I followed your instructions and the mic works. The quality is abysmal, but I can hear my own voice thru the internal microphone. Thanks very much. I don't supposed I will use this much, but it's certainly useful to have, and anyway, I like to have everything working as it is supposed to!

---

### Post by Hugo Bio on 2009-10-22
I think i figured it out. I have one Acer Aspire 5050 (its a notebook, not a netbook), and was experiencing the same issue. I tried a lot of things before i went to alsamixer and changed the capture device to "FrontMic", instead of simply "mic". Skype works great now!

For anyone trying to do the same thing, open a terminal window and type:

```
alsamixer
```

Then, press TAB to switch to Capture, and press the right key to go to InputSo. Press up and down to select "Front Mi". Press ESC to quit.
You may try it now, and see if it works. If it did, save the changes permanently, by typing in a terminal window:

```
sudo alsactl store 0
```

---

### Post by johnaaronrose on 2010-03-14
On karmic unr on a A110L, no 'Front Mic' entry for 'Input So'. Only entries are Internal, Mic & Line. Neither Internal or Mic work as Sound Recorder just plays back static.

---

### Post by yooy on 2010-05-04
Hi there, it's a very well known bug (you can check on the bugs launchpad). 

What will follow worked for me with lucid and Karmic ... and it's very easy  :

You have to install pavucontrol 

sudo apt-get install padevchooser

launch it, click on the tray icon in the panel and choose volume control
Click on the tab "input devices", unlock (click on the locker icon) and set the input  level of one of the two channel at zero. The other one have to be at the maximum. You can't do that without unlocking first.... 

that's it that's all, it allows the internal mic to work. I did it twice on 2 aspire one A150 and it works flawlessly.

---

### Post by Goatrancer on 2010-05-08
That worked for me too, although I had to monkey with the input devices at first. For a while I could only record or play back, had to switch between "analog input" and "analog ouput" to record an listen respectively. When I selected digital output + analog input" I could listen but only record what was playing through the soundcard (ie a youtube video). After turning off that setting and then going back to it all worked fine!

---

### Post by FearsomeOrange on 2010-05-24
> **yooy said:**
> Hi there, it's a very well known bug (you can check on the bugs launchpad). 

What will follow worked for me with lucid and Karmic ... and it's very easy  :

You have to install pavucontrol 

sudo apt-get install padevchooser

launch it, click on the tray icon in the panel and choose volume control
Click on the tab "input devices", unlock (click on the locker icon) and set the input  level of one of the two channel at zero. The other one have to be at the maximum. You can't do that without unlocking first.... 

that's it that's all, it allows the internal mic to work. I did it twice on 2 aspire one A150 and it works flawlessly.


THIS!!

Weeks of monkeying around, and this was my solution.  Just turning off one of the channels in PADevChooser did the trick.  Thank you!

Fearsome.:guitar:

---

### Post by jpmorelli on 2010-06-14
One year looking for the solution and this work for me in my AAO-D150 !!!
Thank you, thank you !!! :lolflag:

Using Ubuntu 10.04 Lucid Lynx and Skype 2.1 beta from canonical partner repositories.

---

### Post by yooy on 2010-06-14
My pleasure

---

### Post by Jragon on 2010-12-21
I need help with is as well, I got a Acer Aspire One with 10.10 installed. I have no idea why it isn't working, and I need it for my band. Also does anyone know of a way I can plug  my bass straight in to my computer and it amplify it with out going through the amp?

---

### Post by leofishman on 2011-02-04
> **yooy said:**
> Hi there, it's a very well known bug (you can check on the bugs launchpad). 

What will follow worked for me with lucid and Karmic ... and it's very easy  :

You have to install pavucontrol 

sudo apt-get install padevchooser

launch it, click on the tray icon in the panel and choose volume control
Click on the tab "input devices", unlock (click on the locker icon) and set the input  level of one of the two channel at zero. The other one have to be at the maximum. You can't do that without unlocking first.... 

that's it that's all, it allows the internal mic to work. I did it twice on 2 aspire one A150 and it works flawlessly.

Thanks a lot!!!

---

### Post by wjamoore on 2011-06-23
the mute one channel didn't work for me on 3820TZ Aspire TimelineX

Anyone know of anything else?

wjam

---

### Post by michal.grno on 2011-08-24
I have the same problem with Acer TravelMate and Ubuntu 11.04
Please, can you help me? :(

---

### Post by joshthewhistler on 2011-09-04
I'm on ubuntu 11.04 with an aspire one ZG5. I solved the issue by doing
```
sudo pavucontrol
```
and using the resulting window to put one of the two sliders for the mic to 0. However, GoogleTalk still insists that it knows how to adjust my microphone levels and gets it wrong every time. Very annoying. Why does the microphone record (or rather: not record) in stereo anyway? As far as I can tell there's only one mic...

---

### Post by pollin8 on 2011-09-11
> **joshthewhistler said:**
> I'm on ubuntu 11.04 with an aspire one ZG5. I solved the issue by doing
```
sudo pavucontrol
```and using the resulting window to put one of the two sliders for the mic to 0. However, GoogleTalk still insists that it knows how to adjust my microphone levels and gets it wrong every time. Very annoying. Why does the microphone record (or rather: not record) in stereo anyway? As far as I can tell there's only one mic...


Same Ubuntu version, same netbook model, running Skype 2.2.0.35 (BETA) - This solution worked for me, so simple!
Thanks Josh!

---

### Post by vervelover on 2011-10-16
Doesn't trick doesn't for me anymore in Ubuntu Oneiric! Anybody tried with it?

---

### Post by vervelover on 2011-10-24
Really no one tried out Oneiric on a Aspire One?

---

### Post by forestcomber on 2011-11-03
anyone find a solution for this on Oneric ?

---

### Post by zmago on 2012-06-23
pavucontrol works in precise. solution is that for the microphone settings you unselect option locking left and right level of microphone and only manage level of one (left or right)... this wont affect output level but only input (microphone)... for me this works now.. thank you for all the help. without you i wouldn't find this solution :)

cheers

---

