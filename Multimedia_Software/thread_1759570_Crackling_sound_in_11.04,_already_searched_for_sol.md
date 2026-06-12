---
title: "Crackling sound in 11.04, already searched for solutions"
date: 2011-05-15
forum: Multimedia Software
---

### Post by DevinMuffin on 2011-05-15
I've been through what I could find in searches here, but nothing fixed the problem so far. 

Here's the situation: I am using Ubuntu Natty 11.04, dual booting. So I know the sound is fine on the XP system, and also works crisp and clear on my Vista laptop sitting next to me. I've tried the sound through Banshee, Amarok and Exaile all with the same crackling as if the file was ripped off a bad CD. I'll repeat that I've tested the speakers, and also the jack port (being that there are two on my PC) so I am fairly certain it is an issue with Ubuntu. 

Here is the ALSA information report:
[http://www.alsa-project.org/db/?f=ad31c4f7d5da401164783137558b8d1ee19905a5](http://www.alsa-project.org/db/?f=ad31c4f7d5da401164783137558b8d1ee19905a5)

It's not a problem with PCM- the crackling will go away if the level on PCM is like 30~ but then the sound is very quiet even with Master and speaker volume at 100, at which point you can still make out the crackling.

---

### Post by DevinMuffin on 2011-05-16
Bumpity bump

---

### Post by 4Orbs on 2011-05-16
I added the tiny bit of code recommended in [This Post]("http://ubuntuforums.org/showpost.php?p=9948061&postcount=2") and it seems to have fixed the distorted sound on my computer with Xubuntu Natty.

---

### Post by DevinMuffin on 2011-05-17
Thanks, I'll let you know if that works

---

### Post by HeWhoE on 2011-05-29
Has anybody resolved this issue yet? I'm still trying to figure out how to fix this on an HP dv9700 laptop.

---

### Post by ChrisKu on 2011-05-30
I solved a distorted sound problem by playing around with Alsamixer and muting some unneeded channels. It might also help to start Ubuntu from a LiveCD and check whether sound is ok then. Then check the Alsamixer settings in that environment and set the Alsamixer settings to the same values in your installed Ubuntu enviornment.

---

### Post by gustav.franzsen on 2011-06-01
@DevinMuffin - I can confirm the same problem here. Have had 10.10 on a desktop machine (Intel Desktop Board DG33BU) with onboard sound (RealTek ALC888 audio codec
) and everything was fine.

The I upgraded in-situ to 11.04 and immediately expierenced the incessant crackling/popping sound. If I move the mouse around I can hear it etc. I then took a 11.04 iso on a cd and did a clean install. Same problem. Then I decided to do a clean reinstall of 10.10 from iso-disc. The damn problem stayed!

I am now at wit's end. I have installed Alsa Mixer (GUI) and muted everything. Also muted the volumes under Sound Preferences. No change whatsoever.

Have now gone back to a clean install of 11.04 and am searching for ways to solve the problem.

Have seen in some other thread a mention of a kernel rollback that might solve the problem - do not know how to do that though.

Just thought I would confirm your experience lest people think you are nuts ... :)

PS - am posting this from my ThinkPad which is still running a well-behaved 10.10 (sans crackle 'n pop)

---

### Post by lidex on 2011-06-04
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by DevinMuffin on 2011-06-05
In my OP, there is a link to the ASLA info. I will paste it here, again, but updated since I have messed around with things since OP: [http://www.alsa-project.org/db/?f=d1c2ecfd9b6fc4666216cbbf8eee71cad52d6ccf]("http://www.alsa-project.org/db/?f=d1c2ecfd9b6fc4666216cbbf8eee71cad52d6ccf")

Sorry I have taken so long to reply again, however, I tried adding the script 4Orbs recommended, this had no effect. It's a shame because I'm currently enjoying Amarok very much but I can't get over the irritating crackling- testing it more thoroughly through some good headphones, the only other information I can give is that the crackling is coming through only the left channel - BUT- as I said, there is no problem in XP, it is not a hardware issue. I can also hear noise when I move the mouse, a very quiet hum, but I'm not sure if that's connected.

---

### Post by lidex on 2011-06-05
> **DevinMuffin said:**
> In my OP, there is a link to the ASLA info. I will paste it here, again, but updated since I have messed around with things since OP: [http://www.alsa-project.org/db/?f=d1c2ecfd9b6fc4666216cbbf8eee71cad52d6ccf]("http://www.alsa-project.org/db/?f=d1c2ecfd9b6fc4666216cbbf8eee71cad52d6ccf")

Sorry I have taken so long to reply again, however, I tried adding the script 4Orbs recommended, this had no effect. It's a shame because I'm currently enjoying Amarok very much but I can't get over the irritating crackling- testing it more thoroughly through some good headphones, the only other information I can give is that the crackling is coming through only the left channel - BUT- as I said, there is no problem in XP, it is not a hardware issue. I can also hear noise when I move the mouse, a very quiet hum, but I'm not sure if that's connected.

Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

This user has same codec chip:
[http://ubuntuforums.org/showthread.php?t=1506011](http://ubuntuforums.org/showthread.php?t=1506011)

Your mixer has these settings:
```
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',1
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [off]
  Front Right: Playback 64 [100%] [0.00dB] [off]
```

Try muting speaker 0 so they are both muted. Also try enabling speaker 1 alone.

---

### Post by DevinMuffin on 2011-06-06
> rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf

Hot damn that seems to have worked, tested through headphones and speakers and everything seems perfect- the mouse buzz has gone too. 
Excellent, many many thanks :)

---

### Post by gustav.franzsen on 2011-06-06
Thnx for the alert, but alas ... no change here ... still crackling and popping ... also on left channel like you reported ... and right channel really sub-standard sound too ... :(

---

### Post by TheAxeR on 2011-06-06
I would like to join in on the bug hunt. I am having the same exact issue and have yet to be able to resolve it.  I am also using a Intel sound card, though a different family (I think).  I don't know if it will help, but here is my alsa info: [http://www.alsa-project.org/db/?f=36aad250b6301e0579cbf7e32782ddaaf767fc13]("http://www.alsa-project.org/db/?f=36aad250b6301e0579cbf7e32782ddaaf767fc13")

---

### Post by DevinMuffin on 2011-06-06
@ TheAxeR have ye tried the script that worked for me?

---

### Post by lidex on 2011-06-07
> **TheAxeR said:**
> I would like to join in on the bug hunt. I am having the same exact issue and have yet to be able to resolve it.  I am also using a Intel sound card, though a different family (I think).  I don't know if it will help, but here is my alsa info: [http://www.alsa-project.org/db/?f=36aad250b6301e0579cbf7e32782ddaaf767fc13]("http://www.alsa-project.org/db/?f=36aad250b6301e0579cbf7e32782ddaaf767fc13")

You've tried turning down your PCM level, which is maxxed out, BTW and resetting your pulse configuration?
Have you tried changing profile in 'Sound Preferences'?

---

### Post by gustav.franzsen on 2011-06-08
Hi All

My info is here:

[http://www.alsa-project.org/db/?f=55ad6f11562bd0b1947db82a1a0abed6da2d0f54](http://www.alsa-project.org/db/?f=55ad6f11562bd0b1947db82a1a0abed6da2d0f54)

1. I have tried all the 'deletion of configurations and restarts' suggestions.
2. The crackling etc comes from the left channel only
3. If I do a speaker test my left speaker only continues to crackle whilst the right one seems to work correctly
4. If I try to mute ALL output the crackle continues unabated

Weird! :(

---

### Post by gustav.franzsen on 2011-06-08
@lidex - thnx for your advice!

I noticed your link to the ALSA Upgrade Script - do you recommend that I try that maybe?

---

### Post by TheAxeR on 2011-06-08
@DevinMuffin and @lidex I have tried all of the suggestions, to no avail.

---

### Post by DevinMuffin on 2011-06-08
Hmmm... So > rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.confworks for me but every time I fire up my PC I have to enter it in again, which is mildly annoying. Surely there is a reason for this?

---

### Post by lidex on 2011-06-09
What do you get for this in terminal:
```
sudo which alsactl
```

---

### Post by gustav.franzsen on 2011-06-09
Okay ... I am now approaching the point where I go buy a soundcard ... :)

I ran the ALSA Upgrade Script and the output from:

```
 cat /proc/asound/version
```

is:

> Advanced Linux Sound Architecture Driver Version 1.0.24.
Compiled on Jun  9 2011 for kernel 2.6.38-8-generic (SMP)


Alas ... the crackling/popping is still there ... :(

Here is my latest ALSA info:
[http://www.alsa-project.org/db/?f=fee4c52c8ddaffe3b97d53d6604f6bd962b69e13](http://www.alsa-project.org/db/?f=fee4c52c8ddaffe3b97d53d6604f6bd962b69e13)

---

### Post by lidex on 2011-06-09
What are these outputs:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by gustav.franzsen on 2011-06-10
Hi lidex

The output is:

> # dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0004, DMI type 0, 24 bytes
BIOS Information
	Vendor: Intel Corp.
	Version: DPP3510J.86A.0572.2009.0715.2346
	Release Date: 07/15/2009
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 1024 kB
	Characteristics:
		PCI is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		EDD is supported
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Function key-initiated network boot is supported
		Targeted content distribution is supported
	BIOS Revision: 0.0
	Firmware Revision: 0.0

Handle 0x0012, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 1
		enUS
	Currently Installed Language: enUS

------------------------------------------------------------------------------

# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0006, DMI type 2, 20 bytes
Base Board Information
	Manufacturer: Intel Corporation
	Product Name: DG33BU
	Version: AAD79951-405
	Serial Number: AZBU735002VP
	Asset Tag: Base Board Asset Tag
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: Base Board Chassis Location
	Chassis Handle: 0x0007
	Type: Unknown
	Contained Object Handles: 0

Handle 0x000F, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Enabled
	Description: Unknown Video Device

Handle 0x0010, DMI type 10, 6 bytes
On Board Device Information
	Type: Ethernet
	Status: Enabled
	Description: Intel(R) 82566DC Gigabit Ethernet Device

Handle 0x0011, DMI type 10, 6 bytes
On Board Device Information
	Type: Sound
	Status: Enabled
	Description: Intel(R) High Definition Audio Device


BTW - since I ran the ALSA Upgrade Script I have some 'apps' in my Sound & Video menu that are new but do nothing if I click on them ... :)

eg 'Echomixer', Envy24 control, HDSPConf, HDSPMixer etc

---

### Post by lidex on 2011-06-12
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=3stack-6ch-intel" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by unlimited on 2011-06-12
I have the same problem. My front left speaker is making crackling sound. The cable and speaker itself are fine ive checked it. I have alc880 and loaded options snd-hda-intel model=6stack to get my 7.1 surround, but front left speaker is still noisy.

---

### Post by maverick280857 on 2011-06-12
I have the same problem: [http://ubuntuforums.org/showthread.php?p=10928891#post10928891](http://ubuntuforums.org/showthread.php?p=10928891#post10928891)

---

### Post by gustav.franzsen on 2011-06-12
Sorry lidex, no change ... :)

---

### Post by gustav.franzsen on 2011-06-13
Okay ... it looks to me like it has to be a hardware problem in my case after all?

I took a different hard drive and reinstalled Maverick (10.10) on it without any internet connectivity. After the clean install the problem persisted.

---

### Post by virtualXTC on 2011-06-13
> **lidex said:**
> Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```


I think this worked for me as well - must of copied over a bad config file upon upgrade.

---

### Post by drifter2502 on 2011-06-18
I had same problem with my M670 laptop with 11.04 recently installed. This was also compounded with an open mic that was not even enabled under alsamixer! I installed pavucontrol for pulse audio (from package manager) and the crackling stopped and I was also able to disable the laptop mic during recording.

---

### Post by Ryuukumori on 2011-06-18
> **drifter2502 said:**
> I had same problem with my M670 laptop with  11.04 recently installed. This was also compounded with an open mic that  was not even enabled under alsamixer! I installed pavucontrol for pulse  audio (from package manager) and the crackling stopped and I was also  able to disable the laptop mic during recording.

I also tried installing this program to see if this would fix my sound issues. After typing in pavucontrol in ubuntu software center and install it, I open the application to see an error "Connection failed: connection refused". Any idea on how to fix this also?

---

### Post by drifter2502 on 2011-06-18
> **Ryuukumori said:**
> I also tried installing this program to see if this would fix my sound issues. After typing in pavucontrol in ubuntu software center and install it, I open the application to see an error "Connection failed: connection refused". Any idea on how to fix this also?
You tried re-install from Synaptics Package Manager ?

---

### Post by Ryuukumori on 2011-06-18
> **drifter2502 said:**
> You tried re-install from Synaptics Package Manager ?

Great that worked. It wasn't clear as far as what to reinstall, but I managed to do it by reinstalling a VLC pulse audio plugin as well as installing another package that had pulse audio in its name. 

What settings should I set to try to fix the sound?

---

### Post by drifter2502 on 2011-06-18
> **Ryuukumori said:**
> Great that worked. It wasn't clear as far as what to reinstall, but I managed to do it by reinstalling a VLC pulse audio plugin as well as installing another package that had pulse audio in its name. 

What settings should I set to try to fix the sound?

If you have now installed pulseaudio and pavucontrol you should now be able to go to Menu/Sound & Video/Pulse Audio Device Chooser, left click on it and the pulse icon should be in the task bar. In there you will see Volume Control. Some minor tinkering and you should be able playback and record. Try recording something in Sound Recorder whilst having Recording open in Volume Control.  You may have to choose your sound card and stream settings and ensure your alsamixer is set properly via terminal.

---

### Post by TheAxeR on 2011-06-18
> **drifter2502 said:**
> I had same problem with my M670 laptop with 11.04 recently installed. This was also compounded with an open mic that was not even enabled under alsamixer! I installed pavucontrol for pulse audio (from package manager) and the crackling stopped and I was also able to disable the laptop mic during recording.

So bizarre, I installed it and the popping sound disappeared.  I didn't even mess with the settings. Though, right after installing it my speakers didn't do any output, but it was fixed after restarting the computer.

The second weird thing is that the popping is still gone even after uninstalling it.  

Sounds has been and I guess always will be voodoo on Linux.

---

### Post by Ryuukumori on 2011-06-18
> **drifter2502 said:**
> If you have now installed pulseaudio and pavucontrol you should now be able to go to Menu/Sound & Video/Pulse Audio Device Chooser, left click on it and the pulse icon should be in the task bar. In there you will see Volume Control. Some minor tinkering and you should be able playback and record. Try recording something in Sound Recorder whilst having Recording open in Volume Control.  You may have to choose your sound card and stream settings and ensure your alsamixer is set properly via terminal.

The thing is... I don't know if pulseaudio and pavucontrol are 2 separate programs/packages I need to install... In ubuntu software center I type pavucontrol and it only shows one option: "PulseAudio Volume Control". It's what you mentioned though... 

Anyways, here's a quick screenshot of what I did to reduce the crackling, not sure if this is what you wanted me to try...
[IMG]http://img820.imageshack.us/img820/9366/volumecontrol.png[/IMG]

---

### Post by drifter2502 on 2011-06-19
Ryuukumari- Have you got something playing during that screenshot? Your system is behaving differently than mine if you have.  If I play a song in Rythmbox (for instance) then that shows. If nothing is playing then I get a blanc box there. Also has the crackle reduced or stopped?
As I said, installing pavu worked for me ok. Problem is I am also new to 11.04 and sound behavior in Alsa and Pulse differs from Mint 9 in my other partition.  I arrive at good sound by literally ´fiddling about!' Not exactly techi stuff but I usually get there.
Had I not cured crackling I think my next step would have been to try Gnome-Alsamixer which in Mint 9 anyway (ubu 10.04) gives more choices on sound card and channel switching. It might work for you. Hopefully someone else will come along and help you further.

---

### Post by joelstitch on 2011-06-22
> **Ryuukumori said:**
> The thing is... I don't know if pulseaudio and pavucontrol are 2 separate programs/packages I need to install... In ubuntu software center I type pavucontrol and it only shows one option: "PulseAudio Volume Control". It's what you mentioned though... 

Anyways, here's a quick screenshot of what I did to reduce the crackling, not sure if this is what you wanted me to try...
[IMG]http://img820.imageshack.us/img820/9366/volumecontrol.png[/IMG]

This also worked for me on Ubuntu Natty

---

### Post by zcats on 2011-09-11
Hi. Adjusting the volume with pavucontrol worked for me BUT mine crackles when the vol is 70-80% so I chose 60%...:p
Just move the slider and you should immediately see of the crackling changes/stops:popcorn:
YMMV
Ubuntu NAtty

---

### Post by tim|mit on 2011-09-17
Just had crackly sound start on my laptop (had been fine for months). PCM volume changes didn't make any difference but resolved it by simply changing the profile on the hardware device from Analogue Stereo Duplex to Analogue Stereo Input (and having sound output stop) and then back again. On changing back I have nice clear sounds again sans all the horrible crackling that was there.

(right click on the volume control in the top right panel, chose Sound Preferences and then the Hardware tab to get to the profile option).

---

### Post by lidex on 2011-09-18
Sometimes helpful to delete pulse config files when they get "stale". 
```

rm -r ~/.pulse ~/.pulse-cookie 

```

---

### Post by jrschrock on 2011-09-20
Man, I've been working on one audio issue or another for months it seems. I'm getting a lot of conflicting info- there's Team reconfigure Pulseaudio and there's Team get rid of Pulseaudio. I got rid of it, which itself has led to some annoying things like not being able to manipulate sound preferences. And as far as I can tell, no real difference was made. The issues I have are plenty: no internal mic (no it's not muted);  sound stays on in speakers when mic plugged in, crackling noise ala the title of this thread. All this tinkering is driving me nuts! Hopefully, it's cool to put in my alsa project info here and get some good suggestions that put an end to this madness....

the link:    	 	 	 	 	 	  [http://www.alsa-project.org/db/?f=205b4b92cb1a4ebf29c5609084dc46eb86047e08](http://www.alsa-project.org/db/?f=205b4b92cb1a4ebf29c5609084dc46eb86047e08)


If someone could help me out with this, I'd be extremely appreciative. Especially the internal mic woes. Not being able to Skype my daughter sucks!


Oh, and the buzzing sucks too.

---

### Post by Radioactivekid on 2011-12-26
Solution given by LIDEX worked for me. 
Thanks to all
Merry Xmass and nHappy New Year!

---

### Post by lidex on 2011-12-31
> **jrschrock said:**
> Man, I've been working on one audio issue or another for months it seems. I'm getting a lot of conflicting info- there's Team reconfigure Pulseaudio and there's Team get rid of Pulseaudio. I got rid of it, which itself has led to some annoying things like not being able to manipulate sound preferences. And as far as I can tell, no real difference was made. The issues I have are plenty: no internal mic (no it's not muted);  sound stays on in speakers when mic plugged in, crackling noise ala the title of this thread. All this tinkering is driving me nuts! Hopefully, it's cool to put in my alsa project info here and get some good suggestions that put an end to this madness....

the link:    	 	 	 	 	 	  [http://www.alsa-project.org/db/?f=205b4b92cb1a4ebf29c5609084dc46eb86047e08](http://www.alsa-project.org/db/?f=205b4b92cb1a4ebf29c5609084dc46eb86047e08)


If someone could help me out with this, I'd be extremely appreciative. Especially the internal mic woes. Not being able to Skype my daughter sucks!


Oh, and the buzzing sucks too.

Did you ever fix this? Your capture element is muted:
```
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 30 [97%] [28.50dB] [off]
  Front Right: Capture 30 [97%] [28.50dB] [off]
```

---

### Post by jaffro83 on 2012-06-30
I'm sure people are still coming back to this thread to try solve their issues, so I thought I'd post my solution:

I too have a similar Intel chipset to the other users here. I figured it must be a channel issue, so I installed pavucontrol which is a mixer GUI for Pulse audio (I think it might've been mentioned here).

It gave me a few more options than alsamixer did (and alsamixer gui is pretty much useless).

It then allowed me to select a **profile** under the **configuration** tab.

I was playing audio while making the selection, allowing me to hear the differences.

My profile was set to "analog stereo duplex". I noticed that if I changed it to any of the other analog profiles the crackle/static/hiss disappeared.

I know my card has 5.1 channels so I selected "Analog Surround 5.1 Output + Analog Stereo Input".

I then set the volume levels to good mid-range and all was good in the world.

I've yet to see whether it survives reboot.

Some of you might be concerned about input. If that's the case, under the "Input Devices" tab, simply drop the volume (or hit the mute button) of all the traditional output devices such as subwoofer, etc.

You'll then be left with standard input channels.

Hope that helps someone.

---

