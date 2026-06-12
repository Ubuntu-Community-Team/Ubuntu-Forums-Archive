---
title: "help needed in configuring 5.1 audio"
date: 2011-04-30
forum: Multimedia Software
---

### Post by nevin john on 2011-04-30
I'm really new to ubuntu... installed it yesterday and found that multi channel is not available, but sound plays through 2 speakers. how to configure it?

---

### Post by WannabeFantasma on 2011-04-30
Welcome to the wonderfull world of Ubuntu! :D

Click on the sound icon -> Sound Preferences -> Hardware -> change Profile to 5.1

(or atleast I think....)

---

### Post by nevin john on 2011-05-01
Sorry but i tried that earlier, there are only options,
1. Off
2. Analog stereo input
3. Digital stereo duplex (iec958)
4. Digital stereo (iec958) output+analog stereo input
5. Analog stereo output
6. Analog stereo duplex
As far as i'm concerned, none of these options worked the 5.1 way. I had used windows earlier with 5.1 surround sound. So it's not hardware problem. Do i need to install or alter something. I'm totally new. Please help me if i deserve some help...

---

### Post by WannabeFantasma on 2011-05-02
I'll check this evening on my main PC, see how I did it.

Someone else can probably help you better....

---

### Post by nevin john on 2011-05-02
I think nobody else's interested in sharing there ideas. I'm desperate to enable it. If you don't mind spend some time for it. I'm really new. I tried a lot with the terminal window, did a lot of commands, nothing worked:( . It'd be really nice if you helped me:).. Anyway, thanks for the helping mind...:)

---

### Post by WannabeFantasma on 2011-05-02
I will try to help you as much as I can :) Note that I'm not that experienced with ubuntu myself... (been using it for quite a while but still....)

How are your speakers connected to your pc?
what ubuntu do you use?
what sounds are you talking about (movies, music,...)

What I got in the sound menu 
Analog stereo 
to 
Analog 7.1

---

### Post by nevin john on 2011-05-02
I'm running the 10.10 maverick. My sound system is 5.1, connected to the onboard ports. It's creative sound blaster. I had removed the creative sound card because it became faulty last year. Chipset is intel g31. Southbridge is assigned to hd audio. On windows the realtek drivers are installed and the 5.1 audio works as it should be... When it comes to ubuntu, it is only the right and left (front) speaker working. The profiles that i can configure to in the sound preference window are mentioned in the third post... So i believe that ubuntu recognizes my sound card but in the wrong manner, that is, only 2 channels in the case of 5.1. Reinstalling ubuntu didn't help. Any ways to configure the os to identify the 5.1? I think the moderator here are not interested in giving their replies to my query... Anyway waiting for you to help me...

---

### Post by WannabeFantasma on 2011-05-03
As I said I'm not that experienced myself either....
So you're running sound from your motherboard's sound ports?

Maybe [https://help.ubuntu.com/community/SurroundSound](https://help.ubuntu.com/community/SurroundSound) can help you?

---

### Post by nevin john on 2011-05-04
The instructions were for some other versions, anyway i tried it on 10.10 but didn't work. :(

---

### Post by WannabeFantasma on 2011-05-04
I'm sorry... I have no idea then... :(
Wish someone else had commented on this problem to help you with your "mission" :( but guess I can't help you out...

---

### Post by ratcheer on 2011-05-04
If you click the Speaker icon in the notification applets at the top right of your screen, there should be a menu item for "Sound Preferences". Click it.

The applet that opens should have some tabs.  In the hardware tab, select your sound device. Then, under that, there should be "settings for selected device". Click that and select "Analog surround 5.1 output". 

Now click the Output tab. Select the entry that should be there for your device with 5.1 output. Select the Amplifier connector.

Go back to the Hardware tab and "Test your speakers".

If this does not work, we may have to get into ALSA.

Tim

---

### Post by lidex on 2011-05-04
@ratcheer
OP already mentioned that profile does not exist on his machine.

@nevin john
First try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

Next use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by ratcheer on 2011-05-04
His question got me to looking at mine. It was also set to 2-channel stereo. When I reset it to Audigy 5.1, my sound disappeared, too. :(

Aren't upgrades fun?

Tim

---

### Post by lidex on 2011-05-04
> **ratcheer said:**
> His question got me to looking at mine. It was also set to 2-channel stereo. When I reset it to Audigy 5.1, my sound disappeared, too. :(

Aren't upgrades fun?

Tim

If your Creative Audigy card is not giving you any sound, make sure the analog/digital check box in your sound mixer is unchecked. Updates seem to reset this switch regularly so keep this in mind.

---

### Post by ratcheer on 2011-05-05
Lidex, I do not see any type of checkbox in my mixer. I assume you mean alsamixer, but maybe not. That is the only mixer I know of.

Thanks,
Tim

---

### Post by ratcheer on 2011-05-05
> **ratcheer said:**
> Lidex, I do not see any type of checkbox in my mixer. I assume you mean alsamixer, but maybe not. That is the only mixer I know of.



Ok, I found and installed package gnome-alsamixer. Now I have the checkbox and I unchecked it. But, still no sound.

The funny thing is, I was getting 2-channel stereo before I started trying to get 5.1 output to work. Now I cannot even go back to 2-channel and have it work. :confused:

Tim

---

### Post by nevin john on 2011-05-05
I upgraded to 11.04 to see whethe it'd automatically fix it... Unfortunately, didn't work...but i tried this,
> 
First try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

This is okay, i think:) because it showed error messages as you told and i ignored and restarted.
But,
> 
Next use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
This part didn't work for me, i think...i'm a total newbie to the terminal and it's usage:(... I wrote the code and hit enter but nothing happened. It just waited for sometime and got ready by itself for the next command... I didn't get any response... Please can you spend some time... I need the sound desperately...

---

### Post by ratcheer on 2011-05-05
nevin john, just highlight the code, right click, and select Copy. Then go to your terminal window, right click, and select Paste.

Tim

---

### Post by lidex on 2011-05-05
> **ratcheer said:**
> Ok, I found and installed package gnome-alsamixer. Now I have the checkbox and I unchecked it. But, still no sound.

The funny thing is, I was getting 2-channel stereo before I started trying to get 5.1 output to work. Now I cannot even go back to 2-channel and have it work. :confused:

Tim
Interesting, how about posting your alsa-info? Also try toggling that setting in gnome-alsamixer, then
reload alsa - try it both ways - checked and unchecked.
```
sudo alsa force-reload
```

---

### Post by nevin john on 2011-05-05
> 
Next use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Choose the upload option and provide a link for the output.
This is where my alsa information is located
 [http://www.alsa-project.org/db/?f=ce6008afd30ac22d3455fe21f6a020d4e71211ec](http://www.alsa-project.org/db/?f=ce6008afd30ac22d3455fe21f6a020d4e71211ec)

---

### Post by lidex on 2011-05-05
@nevin john:
What is the make and model of this computer?

---

### Post by nevin john on 2011-05-05
> **lidex said:**
> @nevin john:
What is the make and model of this computer?
It's an assmbled system
Motherboard is ASUS P5KPL-AM/PS.
Processor is Intel Dual core 3.0Ghz
Chipset- Intel G31
RAM- 2GB

---

### Post by lidex on 2011-05-06
> **nevin john said:**
> It's an assmbled system
Motherboard is ASUS P5KPL-AM/PS.
Processor is Intel Dual core 3.0Ghz
Chipset- Intel G31
RAM- 2GB

Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by nevin john on 2011-05-06
> **lidex said:**
> Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**
it gave me the response:
options snd-hda-intel model=auto
then i rebooted but found no difference... but my system is hangingg for sometimes, then it works cool and then hangs and so on.. This is the current situation...:(

I forgot to say this, i had downloaded a package from realtek and installed on context of  my windows XP used realtek drivers to play surround audio...

---

### Post by nevin john on 2011-05-06
Sorry but i'm back on 10.10 maverick since it was terrible hard for me to have atleast a mouse click. My pc hanged on 11.04....:( i'm terrible frustrated.... I know you all are trying your best to help me....:) feels good at least for that...:)

---

### Post by nevin john on 2011-05-06
New reply after the downgrade to 10.10 maverick

> 
Code:
 	wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh 
Choose the upload option and provide a link for the output. 			 		


[http://www.alsa-project.org/db/?f=1983ba922d74f1c40d06ffa349c4eb5f4475d9ef](http://www.alsa-project.org/db/?f=1983ba922d74f1c40d06ffa349c4eb5f4475d9ef)

Do i need to do the next step that you told me earlier?:confused:

---

### Post by ratcheer on 2011-05-06
@lidex, here is my current alsa-info.txt.

Since my last post, I did get sound working again by deleting all the config files and rebooting. However, I am pretty sure it is using the internal system sound card in 2-channel mode.

The Audigy worked just fine in Maverick.

Thanks,
Tim

---

### Post by ratcheer on 2011-05-06
PS - How can it be using the internal sound card if all the speakers are wired to the Audigy?

Tim

---

### Post by ratcheer on 2011-05-06
Ok, I have verified by running padevchooser that my sound is currently playing back via "Internal Audio Analog Stereo". I am totally and officially confused. :confused:

Also, the alsa_info.txt shows that my alsa driver is still at 1.0.23, even though my package alsa-base is at 1.0.24.

Tim

---

### Post by nevin john on 2011-05-06
I'm confused who started the thread!!! ;-) or is it irrespective in this forum?

---

### Post by ratcheer on 2011-05-06
> **nevin john said:**
> I'm confused who started the thread!!! ;-) or is it irrespective in this forum?

I apologize. I thought we more or less have the same problem, so I thought we could explore it together. I will go away.

Tim

---

### Post by nevin john on 2011-05-06
> **ratcheer said:**
> I apologize. I thought we more or less have the same problem, so I thought we could explore it together. I will go away.

Tim
oh my gosh! i didn't expect that! :O  didn't you see the " ;) " smilie in my post?!!! I just wanted to have some fun that's all. Please don't take it serious and go away! Lets be friends :)

---

### Post by ratcheer on 2011-05-06
> **nevin john said:**
> oh my gosh! i didn't expect that! :O  didn't you see the " ;) " smilie in my post?!!! I just wanted to have some fun that's all. Please don't take it serious and go away! Lets be friends :)

Cool. Thank you.

I have made some progress, but still not yet found an actual solution. I disabled my onboard soundcard and now Pulse Audio is picking up my Audigy card as both the source and the sink of sound. I can verify this with padevchooser's monitors. However, no sound is getting to my speakers. Here is my latest alsa-info.txt:

[http://www.alsa-project.org/db/?f=d41789260c59cdbfefaf1516fd912878fed51471](http://www.alsa-project.org/db/?f=d41789260c59cdbfefaf1516fd912878fed51471)

Note that my speakers are connected directly into the output jacks of the Audigy. They were making sound when things were running through the internal onboard card. And they worked in 5.1 mode on Maverick until I upgraded to Natty, about a week ago.

Why is the sound not getting to the speakers?

@nevin john, does your PC have both an onboard sound card and a real plugged in card that you need to use for 5.1 sound?

Tim

---

### Post by nevin john on 2011-05-06
> **ratcheer said:**
> 
@nevin john, does your PC have both an onboard sound card and a real plugged in card that you need to use for 5.1 sound?

Tim
Nope. I don't have an addon card, i'm using creative 5.1 speaker setup., which is plugged in to the boards default audio pins. Hdaudio is enabled in the southbridge of my chipset, and everything ** works well on WindowsXP ** but ** Not on Ubuntu 10.10 Maverick **
. Still no idea why. .. :confused:

---

### Post by nevin john on 2011-05-07
Nothing works! I tried a whole day to enable it. I think i can't do it without someone's help. Lidex, or somebody please help me. Lidex, you gave me some instructions, i've done it and the results are already posted. Why no reply to that? Sorry if you all are busy...

---

### Post by solitaire on 2011-05-07
Having same problems here!! can't get 5.1 audio to work...

---

### Post by ratcheer on 2011-05-07
> **solitaire said:**
> Having same problems here!! can't get 5.1 audio to work...

Details? Sound card, Ubuntu version, etc...

Tim

---

### Post by mc4man on 2011-05-07
With an audigy2 Zs card
I have been using digital out (pulse 5.1 digital), which works fine.

So switched back to analog 5.1 out, initially no sound, but was able to restore in alsamixer by disabling  the Audigy A ( noting I never enabled the switch previously, actually this is the first time I've opened alsamixer on this install
Screen shows

The only difference here from a default install is an asound.conf i put in place to enable the pulse 5.1 digital, maybe i'll rename and do a restart though i'm not sure it matters here.

Edit: it doesn't appear the asound.conf matters for analog 5.1, (is needed for digital 5.1)
As far as the Audigy A switch - doesn't matter if on or off for digital, must be off for analog

---

### Post by solitaire on 2011-05-08
> **ratcheer said:**
> Details? Sound card, Ubuntu version, etc...

Tim

D'oh! clicked before i finished...

My motherboard is a Zotac Nvidia Ion (IONITX-F-E)
I'm running 10.10
latest Nvidia drivers.
On-board sound

5.1 audio works in XP

```

bill@ion:~$ lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
03:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1)

```

---

### Post by lidex on 2011-05-08
@nevin john
Apply that model quirk to your new install.
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

@mc4man
Thank you for that. Audigys have been somewhat of an enigma for me.

@ratcheer
Does mc4man info help you?

---

### Post by ratcheer on 2011-05-08
> **lidex said:**
> 

@ratcheer
Does mc4man info help you?

I am afraid I didn't understand it. I mean, I think understand that he set alsa to PCM instead of analog to get it to work, but I have no idea what setting(s) are used to accomplish that. I felt too stupid to ask about it.

Thanks,
Tim

---

### Post by mc4man on 2011-05-08
> **ratcheer said:**
> I am afraid I didn't understand it. 
Tim
All I did was make sure that the Audigy A switch was OFF. The only thing of interest on that screenshot was what was shown in red
(to enable or disable a switch in alsamixer just hit the m key on keyboard

As far as alsamixer itself - you'll find very few of the sliders actually have any effect - there is a slight 'disconnect' between pulse and alsamixer
(one of the reasons I never use alsamixer, the sole exception being to make sure the Audigy A switch is off if using analog 5.1 out

(there may be an amixer command to set the switch

---

### Post by ratcheer on 2011-05-08
Ok, thank you, I understand, now. It does not help in my case. I have turned that switch off and on 20 times this weekend.

Tim

---

### Post by lidex on 2011-05-08
> **ratcheer said:**
> Ok, thank you, I understand, now. It does not help in my case. I have turned that switch off and on 20 times this weekend.

Tim
Maybe this then:
[http://ubuntuforums.org/showthread.php?t=1750858](http://ubuntuforums.org/showthread.php?t=1750858)

---

### Post by nevin john on 2011-05-09
Do i need to only execute this in the terminal
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```
Or do i need to add something else? I asked this because you mentioned something like ' add model quirk' in your last post... Sorry for these stupid newbie questions... Hope i need to only add that code only. I'l post the result as soon as i get to my pc and execute the command.

---

### Post by ratcheer on 2011-05-09
> **lidex said:**
> Maybe this then:
[http://ubuntuforums.org/showthread.php?t=1750858](http://ubuntuforums.org/showthread.php?t=1750858)

I added the following lines to /etc/modprobe.d/alsa-base.conf:
```
alias snd-card-0 snd-emu10k1
alias sound-slot-0 emu10k1
alias snd-card-1 snd-hda-intel
alias sound-slot-1 snd-hda-intel

```Rebooted. It didn't help. Deleted .pulse and rebooted. It didn't help. I tried it with the alsamixer Analog/Digital Output switch On and Off. It didn't help.

I am very frustrated. :confused:

Tim

---

### Post by ratcheer on 2011-05-09
Dern. I was certain I had found the problem. My userid did not have the "Use audio devices" privilege. I checked it and logged off and back on. No worky. I rebooted. No worky. I used alsamixer to switch the Analog Digital output On and Off.

Still no worky.

Dern.

Tim

---

### Post by mc4man on 2011-05-09
> **ratcheer said:**
> Dern. I was certain I had found the problem. My userid did not have the "Use audio devices" privilege. I checked it and logged off and back on. No worky. I rebooted. No worky. I used alsamixer to switch the Analog Digital output On and Off.

Still no worky.

Dern.

Tim
If you get a chance maybe post a screen of alsamixer, you don't need to fit the whole thing, just starting from far left to whatever ->

Also are you sure that the audigy card is being used vs. your onboard audio?

(while it would be hard to describe, if inclined you can maybe use audacious to do a bit of troubleshooting because of it's extensive audio options

---

### Post by ratcheer on 2011-05-09
> **mc4man said:**
> If you get a chance maybe post a screen of alsamixer, you don't need to fit the whole thing, just starting from far left to whatever ->

Also are you sure that the audigy card is being used vs. your onboard audio?

(while it would be hard to describe, if inclined you can maybe use audacious to do a bit of troubleshooting because of it's extensive audio options

Here is the screenshot. And yes, I am sure it isn't using onboard audio because I disabled it in the BIOS a couple of days ago.

Thanks,
Tim

---

### Post by ratcheer on 2011-05-09
It will be severely painful, but I am just about ready to reinstall Maverick. Or, maybe even another distro. 

Tim

---

### Post by nevin john on 2011-05-10
I should say that the last method you asked me to do too didn't help to fix my trouble. Lidex, are you watching this thread?! :(

---

### Post by ratcheer on 2011-05-11
Is there any way to just set both alsa and PA to their default states and start all over? I have made so many changes, I am not sure how to ever make sure anything is right, anymore.

Thanks,
Tim

---

### Post by nevin john on 2011-05-11
> **ratcheer said:**
> Is there any way to just set both alsa and PA to their default states and start all over? I have made so many changes, I am not sure how to ever make sure anything is right, anymore.

Thanks,
Tim

Hey, buddy, check the starting pages of this thread,  lidex has provided a code which i think is what you need. Not sure, please take a look and confirm yourself. My problem still remains. I think lidex has left watching the forum. Anyway hoping for the best...:)

---

### Post by ratcheer on 2011-05-11
Thanks, nevin john. I did that and now I am able to get sound from alsa to pulse audio, again (according to pavumeter). But, still no actual sound to the speakers.
 
Tim

---

### Post by mc4man on 2011-05-11
@ratcheer
maybe it's something you've done post install, don't know
I believe we have the same card, - I've never had any issue getting analog 5.1 since lucid (I believe in karmic I had to edit a pulse file for 6 channels, but only in karmic.

If you want to test something, maybe there is some logic here, maybe not.

Open audacious and in pref.'s set the 'Current output  plugin' to Alsa.
 Then  in 'Output Plugin Pref.'s' set up as in any of the 1st. 3 screens, one or all should produce some sound, use a regular audio file (wav, flac, mp3, ect. 
(basically bypassing pulse for alsa and specifying the Audigy card directly

If you get actual sound then set as in screen 4 (now trying 'default' mixer device with a working PCM Device
If you still get sound then go back into the audacious pref's and change the 'Current output  plugin' to PulseAudio and see what happens

---

### Post by ratcheer on 2011-05-11
Thanks for that advice. When I have Audacious set to output to ALSA and select my sound card in the Output Plugin Preferences, and play a wav file, it gives an error: [snd_pcm_hw_params_set_channels failed: Invalid argument.]("http://blog.al.com/breaking/2011/05/132_miles_of_devastation_ef-5.html")

So, it seems to me this means I have something set up incorrectly or in conflict with something else.

Tim

PS - I think this can be ignored. When I made selections like in your pictures, the sound is played, but still without output to the speakers.

---

### Post by ratcheer on 2011-05-11
My latest alsa-info.sh output. Something must be messed up.

[http://www.alsa-project.org/db/?f=640faff8211d844e003d74a3d83387940d05e023](http://www.alsa-project.org/db/?f=640faff8211d844e003d74a3d83387940d05e023)

Tim

---

### Post by ratcheer on 2011-05-11
More info: I can even play a Youtube video and, with the padevchooser monitors, they show sound levels of the 5.1 output sink and the stereo input source.

I am very, very frustrated. It is like my speakers are not connected, but I have checked them over and over. Also, they have worked a little during the course of all this troubleshooting, when I tested stereo sound througn the onboard sound device (which I have since diabled in the BIOS).

Tim

---

### Post by lidex on 2011-05-11
> **ratcheer said:**
> My latest alsa-info.sh output. Something must be messed up.

[http://www.alsa-project.org/db/?f=640faff8211d844e003d74a3d83387940d05e023](http://www.alsa-project.org/db/?f=640faff8211d844e003d74a3d83387940d05e023)

Tim
Should probably get back to defaults at this point. I think mc4man stated he did not make any configuration changes. I would remove any edits to alsa-base.conf and see if you can update to the .9 kernel:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
Make sure these are installed:
```
sudo aptitude install linux-firmware alsa-firmware

```
**Reboot**
Next figure out which outputs you are actually using in alsamixer and mute the others then toggle the a/d switch to match. It may be helpful to disable onboard sound during that reboot as well.

@mc4man
Would you be willing to post your alsa-info for comparison purposes?

---

### Post by ratcheer on 2011-05-11
@lidex - Thanks again. I have implemented your latest suggestions, but still no sound output. Maybe my speakers died. :confused:  But, I doubt it.

Note that I have said all along that this stuff worked for me on Maverick. I am 100% certain that 5.1 sound output was working perfectly with the same soundcard and speakers. But, guess what. Just to prove to myself that I'm not crazy, I reinstalled 10.10 on my testing partition. And sound does NOT work there, either! This has just got to be a hardware problem.

Does anyone know a good Linux distro that doesn't use this convoluted  stack of sound infrastructure (ALSA and Pulse Audio)? There are simply  too many variables.

Tim

---

### Post by lidex on 2011-05-11
Do you dual boot? If so, boot into windows and make sure it works there, then reboot into ubuntu. Sometimes the chipset needs to be initialized in windows.

---

### Post by ratcheer on 2011-05-11
> **lidex said:**
> Do you dual boot? If so, boot into windows and make sure it works there, then reboot into ubuntu. Sometimes the chipset needs to be initialized in windows.

No, I can only dual boot between 11.04 and 10.10.

That is a very good point, though. To the best of my knowledge, when I upgraded my main installation from 10.10 to 11.04 is when I lost sound. Before that, I had 11.04 on my test partition and I am fairly sure that sound worked on it, too. But, that was a fresh install.

However, the 10.10 that I recently installed in my test partition was also a fresh install.

Tim

---

### Post by mc4man on 2011-05-11
Here's the alsa info, for the purposes here have set up for 5.1 analog (pulseaudio
 [http://www.alsa-project.org/db/?f=6198dc05c994f40e3229b0b9cf2a1da3a5ff3a3f](http://www.alsa-project.org/db/?f=6198dc05c994f40e3229b0b9cf2a1da3a5ff3a3f)

---

### Post by lidex on 2011-05-11
I am comparing these and will get back to you - my eyes are going out of focus.

---

### Post by nevin john on 2011-05-12
i don't really understand why you guys really avoid my request and hang on with yours!, at least give me a consideration that i'm a newbie, 
thank you :)

---

### Post by lidex on 2011-05-12
> **nevin john said:**
> i don't really understand why you guys really avoid my request and hang on with yours!, at least give me a consideration that i'm a newbie, 
thank you :)

Sorry, I really have nothing at this point-trying to brainstorm and find info elsewhere.

---

### Post by nevin john on 2011-05-12
It's okay bro:) just an info, in windows Xp, i had to install the realtek drivers and along with the drivers a graphical mixer was also installed automatically. I could configure my audio with this mixer. I noticed that only 2 speakers were configured by default... I, then changed it to 6 channel. Any possibility to download and install this realtek drivers and mixer on ubuntu?

---

### Post by WannabeFantasma on 2011-05-13
Looks to be a pretty serious problem...
Hope you solve it eventually :)

I'll keep my fingers crossed for you!

---

### Post by lidex on 2011-05-13
> **nevin john said:**
> It's okay bro:) just an info, in windows Xp, i had to install the realtek drivers and along with the drivers a graphical mixer was also installed automatically. I could configure my audio with this mixer. I noticed that only 2 speakers were configured by default... I, then changed it to 6 channel. Any possibility to download and install this realtek drivers and mixer on ubuntu?

Hmm...if this is the answer, I'll shoot myself.
Look at the screenshot of alsamixer below. Open yours and scroll all the way to the right. Do you have a 'Channel Mode'? If so toggle it to 6ch, close, and open sound preferences. Do you have surround profiles now?

---

### Post by nevin john on 2011-05-14
this is mine

---

### Post by solitaire on 2011-05-14
> **nevin john said:**
> this is mine

Take a look at this thread,
 [http://ubuntuforums.org/showthread.php?t=1754639](http://ubuntuforums.org/showthread.php?t=1754639)
It might help. 
It gave me the chanel option, which fixed my problem.

---

### Post by nevin john on 2011-05-14
Where were you all this time, bro?! Let me say that you've helped me fix it! Party!!! And thanks to lidex  who helped you and tried his level best to help me too.. :) i still don't know why he couldn't lead me the way he adopted to fix your prob, because both of our's problem was the same! Anyway, a big thanks to him, coz it's he who came up with the solution and to all the guys who helped me here, ratcheer and all the others... The 3stack-6ch worked for me, the other code is meant to digital op i guess , right?

---

### Post by solitaire on 2011-05-14
Glad it worked!! ^_^

Think it's a problem with the kernel, it needs to be patched to recognise the HD audio cards correctly. The patch will be in the next kernel buy the looks of it...

---

### Post by lidex on 2011-05-14
> **nevin john said:**
> Where were you all this time, bro?! Let me say that you've helped me fix it! Party!!! And thanks to lidex  who helped you and tried his level best to help me too.. :) i still don't know why he couldn't lead me the way he adopted to fix your prob, because both of our's problem was the same! Anyway, a big thanks to him, coz it's he who came up with the solution and to all the guys who helped me here, ratcheer and all the others... The 3stack-6ch worked for me, the other code is meant to digital op i guess , right?

Yeah, too many distractions, but if you look at posts 20-24 and 40 I was trying to move that direction.

---

### Post by nevin john on 2011-05-14
You did a good job, bro...:) thank you... Just going off topic, i guess you won't mind, will there be any problem to The motherboard or any of the circuits or even the processor, if i shift my monitor from the currently normal computer lcd screen to a sony bravia lcd tv? Earlier when i did this, i had a motherboard and processor complaint. I think it's after the monitor shift it happened. Was the proble due to the monitor shift or was it coincidel?

---

### Post by nevin john on 2011-05-15
Anybody with an answer to my last post?

---

