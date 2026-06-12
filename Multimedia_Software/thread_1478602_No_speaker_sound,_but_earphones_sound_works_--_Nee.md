---
title: "No speaker sound, but earphones sound works -- Need Advise"
date: 2010-05-09
forum: Multimedia Software
---

### Post by Kleos04 on 2010-05-09
I have just installed Ubuntu 10.04 and everything works great! Except  for one thing, I can't get my speakers to play any sound. I know that my  sound card and hardware is working normal because when I use my  earphones I hear perfect sound. Also, when I boot into Windows 7  everything works fine. The problem is probably really simple to fix, but  I dont know ubuntu or linux at all.  

If someone could list the steps I need to do to fix the sound problem I  would be grateful.

My machine is a gateway NV79
Intel i3 330M
500 GB HDD
4 GB
Built-in audio

---

### Post by fdmille on 2010-05-15
I bought the same laptop about a month ago and I have the same exact problem.  Earphones work -- speakers do not.  Same problem using 32-bit or 64-bit 10.4.  Windows 7 - audio works OK.  I've been searching for a solution, but nothing has worked yet.  I tried downloading and installing the Realtek driver, but I get compile errors.  I tried using KDE and get the following error message "The audio playback device HDA Intel (ALC272) does not work."

---

### Post by Bucky Ball on 2010-05-15
Are you using PulseAudio? If so, see my final post #6, in this thread:

[http://ubuntuforums.org/showthread.php?t=1478754](http://ubuntuforums.org/showthread.php?t=1478754)

If you have Applications->Sound and Video->Pulse Audio Device Chooser, open, left click, choose Volume Control. Get something playing and you will see the stream in the Playback Stream window. Right click on the stream and 'Move Stream' to change it to the desired device. 

You can also play around with output and input devices. Not sure if Pulse is being used in 10.04 but that might help.

---

### Post by jaskeerat888 on 2010-05-15
Hi im jaskeerat, i m very new to ubuntu. ubuntu wz working very fine. untill this sound problem occured, When i attach my headphones, the sound comes from both--the laptop and the headphones. i love ubuntu so please help me how to get rid of this thing. I have acer 5336 laptop. please.

[email]jaskeerat888@yahoo.com[/email]

---

### Post by fdmille on 2010-05-15
Ok, when I open PulseAudio audio control, and go to the Playback tab, I have a MPlayer: audio stream.  The only choice that I get when I right click on the audio stream is Terminate Playback.  I tried all input and output devices and get the same.  Sound from headphones work but no sound from the speakers.

---

### Post by fdmille on 2010-05-15
> **jaskeerat888 said:**
> Hi im jaskeerat, i m very new to ubuntu. ubuntu wz working very fine. untill this sound problem occured, When i attach my headphones, the sound comes from both--the laptop and the headphones. i love ubuntu so please help me how to get rid of this thing. I have acer 5336 laptop. please.

[email]jaskeerat888@yahoo.com[/email]

You should start you're own stream, because your problem is different from the one started in this stream for Gateway NV79 laptops.

---

### Post by Bucky Ball on 2010-05-16
In Pulseaudio Volume Control->Output devices, what is there? Your device is not muted or turned down? Right click in there and make your desired device the default. You may need to log out and in or restart the machine to notice changes.

---

### Post by fdmille on 2010-05-16
> **Bucky Ball said:**
> In Pulseaudio Volume Control->Output devices, what is there? Your device is not muted or turned down? Right click in there and make your desired device the default. You may need to log out and in or restart the machine to notice changes.

Internal Audio Analog Stereo

Port: Analog Speakers
      Analog Output
      Analog Headphones

Front Left  100%

Front Right 100%

The sound bar which is moving with the audio.

That's it.  My device is not muted or turned down.  As mentioned before, headphones work fine.

---

### Post by lidex on 2010-05-16
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=3stack-dig 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by fdmille on 2010-05-18
Ok, I edited alsa-base.conf and added the option line at the bottom and rebooted.  I then opened alsamixer and checked everything.  Everything looked ok.  I opened system>preferences>sound and the only thing I see under the hardware tab is "Internal Audio" under "Choose a device to configure:".  Still no sound from the speakers.

---

### Post by KevG on 2010-05-18
I had the same problem with a SONY Core i3 laptop, although it is ALC269 so this might not help you?? I think this somehow enables the amplifier which was switched off by default.

My system details are:

SONY VPCEB1M0E

$ aplay -l 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC269
Codec: Intel G45 DEVIBX

$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset  High Definition Audio (rev 05)

This fixed sound for me:

Download hda-verb from [ftp://ftp.suse.com/pub/people/tiwai/...erb-0.3.tar.gz]("ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.3.tar.gz").

decompress with:
gunzip hda-verb-0.3.tar.gz
untar with:
tar -xf hda-verb-0.3.tar
make and install with:
cd hda-verb-0.3 ; sudo make ; sudo cp hda-verb  /usr/bin/

just before exit(0) in /etc/rc.local add the following line to enable  audio amp at reboot

hda-verb /dev/snd/hwC0D0 0x19  SET_PIN_WIDGET_CONTROL 0x22

Got any more info on your system?

Also this thread might be useful:
[http://ubuntuforums.org/showthread.p...light=hda-verb]("http://ubuntuforums.org/showthread.php?t=1043568&highlight=hda-verb")

---

### Post by KevG on 2010-05-18
My previous post described how to make a permanent change to your system (works after reboot), you can try the fix more quickly using this python script (which won't work after reboot).

Go here :

[http://www.alsa-project.org/main/index.php/HDA_Analyzer](http://www.alsa-project.org/main/index.php/HDA_Analyzer)

run the first two commands in a terminal.

Look for Node[0x19] PIN then change in the "Widget Control" group box  the value "VREF" from whatever it is to HIZ or GRD.
Close the application and select No when it asks you if you want to  revert the changes you just made.

---

### Post by fdmille on 2010-05-18
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC272 Digital [ALC272 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: INTEL HDMI 1 [INTEL HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC272
Codec: Conexant ID 2c06
Codec: Intel G45 DEVIBX

$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)

---

### Post by fdmille on 2010-05-18
> **KevG said:**
> My previous post described how to make a permanent change to your system (works after reboot), you can try the fix more quickly using this python script (which won't work after reboot).

Go here :

[http://www.alsa-project.org/main/index.php/HDA_Analyzer](http://www.alsa-project.org/main/index.php/HDA_Analyzer)

run the first two commands in a terminal.

Look for Node[0x19] PIN then change in the "Widget Control" group box  the value "VREF" from whatever it is to HIZ or GRD.
Close the application and select No when it asks you if you want to  revert the changes you just made.

I tried this but it did not do any good.  However, one thing is interesting.  In the Output amplifier block, Mute: is True.

---

### Post by fdmille on 2010-05-18
> **KevG said:**
> I had the same problem with a SONY Core i3 laptop, although it is ALC269 so this might not help you?? I think this somehow enables the amplifier which was switched off by default.

My system details are:

SONY VPCEB1M0E

$ aplay -l 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC269
Codec: Intel G45 DEVIBX

$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset  High Definition Audio (rev 05)

This fixed sound for me:

Download hda-verb from [ftp://ftp.suse.com/pub/people/tiwai/...erb-0.3.tar.gz]("ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.3.tar.gz").

decompress with:
gunzip hda-verb-0.3.tar.gz
untar with:
tar -xf hda-verb-0.3.tar
make and install with:
cd hda-verb-0.3 ; sudo make ; sudo cp hda-verb  /usr/bin/

just before exit(0) in /etc/rc.local add the following line to enable  audio amp at reboot

hda-verb /dev/snd/hwC0D0 0x19  SET_PIN_WIDGET_CONTROL 0x22

Got any more info on your system?

Also this thread might be useful:
[http://ubuntuforums.org/showthread.p...light=hda-verb]("http://ubuntuforums.org/showthread.php?t=1043568&highlight=hda-verb")

I downloaded and installed hda-verb.  I added the line in rc.local file and rebooted.  The speakers still do not have any audio out.  But, thanks for the help anyway.

---

### Post by lidex on 2010-05-18
3stack-dig should work. Have you upgraded to alsa 1.0.23? If not follow the alsa-upgrade link in my sig.

---

### Post by fdmille on 2010-05-23
OK, here is how I was able to finally get sound working through the speakers:

Go to [https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds) and read about Installing Mainline Kernels.

I installed the most recent kernel and rebooted.  Works fine now!

That's it!:P

---

### Post by mainak_sen on 2010-08-29
I was having the exact same problem as the original author of the current thread viz. "No speaker Sound, but earphones sound works". I followed the advice of lidex in post #9 of this thread...but that did not solve the problem. Then, as per lidex's advice in post #16 here I tried to upgrade ALSA. 
That completely broke the sound...now there is NO SOUND...not even the earphones are working any longer. 

I have posted the details of ALSA update script run in the respective thread here:

[http://ubuntuforums.org/showthread.php?p=9781405#post9781405](http://ubuntuforums.org/showthread.php?p=9781405#post9781405)

(see under post# 1064 in page 107).

Can anybody please help??

Thanks in advance!

---

### Post by lidex on 2010-08-29
> **mainak_sen said:**
> I was having the exact same problem as the original author of the current thread viz. "No speaker Sound, but earphones sound works". I followed the advice of lidex in post #9 of this thread...but that did not solve the problem. Then, as per lidex's advice in post #16 here I tried to upgrade ALSA. 
That completely broke the sound...now there is NO SOUND...not even the earphones are working any longer. 

I have posted the details of ALSA update script run in the respective thread here:

[http://ubuntuforums.org/showthread.php?p=9781405#post9781405](http://ubuntuforums.org/showthread.php?p=9781405#post9781405)

(see under post# 1064 in page 107).

Can anybody please help??

Thanks in advance!
First of all, do you have a Gateway NV79? That fix in post #9 was specifically for the OP. I would imagine removing that line from alsa-base.conf would bring your sound back. If you need more help, please start a new thread.

---

### Post by mainak_sen on 2010-08-29
> **lidex said:**
> First of all, do you have a Gateway NV79? That fix in post #9 was specifically for the OP. I would imagine removing that line from alsa-base.conf would bring your sound back. If you need more help, please start a new thread.

Thanks for your response, lidex.

No I don't have a Gateway...mine is a Compaq Presario CQ62 laptop.

I am sorry, I misunderstood your suggestion in post #9 to be generic.

That line is no longer there in alsa-base.conf file... and i still don't have sound. 

I am starting a new post at 
[http://ubuntuforums.org/showthread.php?p=9782187#post9782187](http://ubuntuforums.org/showthread.php?p=9782187#post9782187)

Kindly help if you can

Thanks in advance!

---

