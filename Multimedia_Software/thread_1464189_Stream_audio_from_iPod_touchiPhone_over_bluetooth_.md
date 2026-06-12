---
title: "Stream audio from iPod touch/iPhone over bluetooth to computer"
date: 2010-04-27
forum: Multimedia Software
---

### Post by Ric123 on 2010-04-27
Hi, I was wondering if it is currently possible to connect an iPod touch (or iPhone) over bluetooth and have the audio playing on the iPod stream over to the computer.
In Windows, Windows pretends to be a wireless headset and the iPod recognizes the computer as such and streams the audio over. No applications running; it just works in the background
Basically, I want to listen to the music, videos, etc. that are on my iPod synced from iTunes in Windows (DRM music, etc.), which cannot be played otherwise, through my computer speakers/headphones in combination with the sounds of other applications.
I have paired up my iPod with my Ubuntu machine; the Bluetooth Preferences lists it as an audio device and reports it as being connected, but it seems to be just sitting there. PulseAudio/Sound Preferences gives me no options and the iPod doesn't appear to be recognizing the machine as a 'headset' like in Windows but does say it is connected.

Again, just mostly curious. Has anyone tried this?

I'm using Ubuntu 9.10.

---

### Post by megamanexent on 2010-06-14
I really need this too, I have been looking for over a year for a solution. Found this [http://nohands.sourceforge.net/config.html](http://nohands.sourceforge.net/config.html) 
It stand to reason that if one could have a handsfree experience, then audio should come through. Problem is that it will not even configure on Lucid???? :confused:

Bump

---

### Post by jackflap on 2010-06-17
Check this out: [http://jprvita.wordpress.com/2009/12/15/1-2-3-4-a2dp-stream/](http://jprvita.wordpress.com/2009/12/15/1-2-3-4-a2dp-stream/)

I haven't tested it yet, but it looks like what we're looking for. Please report back with results.

---

### Post by megamanexent on 2010-06-17
^^ This is exactly what i am looking for! However, I cannot find  org.bluez.AudioSource in d-feet and I cannot connect org.bluez.Audio. I  think the reason for the failed connections has to do with the way Apple  implemented A2DP in the iPhone and iTouch. Does anyone have any ideas  to force a connection?

BTW, i am using a Broadcom USB Dongle on Ubuntu 10.04. I have had  success in Windows Xp streaming from the iPhone to the computer, so I  know the Dongle can do it.

---

### Post by jackflap on 2010-06-17
The missing D-Bus AudioSource address might not because of an issue with the iPhone..

I've been fiddling with this, and I've spotted that adding a semi-colon to the end of the Enable=Source; line will not enable the source, and the AudioSource will appear only if you have added 'Enable=Source' alone.

That may be the issue you're experiencing. Generally on mine, the AudioSource.Connect() method appears under the following address:

/org/bluez/942/hci0/dev_00_17_83_D9_FB_B0 -> Interfaces

---

### Post by megamanexent on 2010-06-17
After some more tinkering, I still cannot get   org.bluez.AudioSource to appear. There is no semicolon after Enable=Source. I have restarted bluetoothd several times and even rebooted the computer. Still no dice. What version of bluez do I need? I currently have bluez 4.60 .

---

### Post by jackflap on 2010-06-18
Sounds like you might be right that it's an issue with the iphone (which is a shame since I was going to buy an ipod touch just to stream audio to my sound-server).

I'm on the same version of BlueZ as you are, Ubuntu 10.04, BlueZ 4.60 and I've managed to get it working with an Android phone. But the other phone I tried, a Samsung (Symbian S60v3), could see the AudioSource, but couldn't connect properly.

It might be worth testing with another phone and confirming it's definitely an issue with the iphone. I wouldn't know what to suggest if it is though, perhaps just wait for Ubuntu 10.10 to try again?

Alex

---

### Post by megamanexent on 2010-06-18
Ya, what I think is the iDevice doesn't reveal it supports a2dp unless the remote device is a headset or says its a headset. In windows, that was the only way to stream audio for me. I upgraded bluez to 4.66 to if it will help, but it didn't, now I have to find another phone to see if it will stream. I will report later when i do that. Thanks for your help jackflap!

---

### Post by Ric123 on 2010-06-25
It works! Thanks everyone! jackflap's link worked perfectly! [http://jprvita.wordpress.com/2009/12...4-a2dp-stream/](http://jprvita.wordpress.com/2009/12...4-a2dp-stream/)
I've upgraded to Ubuntu 10.04 by now; I have bluez 4.60 and pulseaudio 0.9.21. 
Here's how I did it for my iPod touch (3.1.3) on my Dell Inspiron 1720:
1. I skipped step one, it was already loaded.
2. Add "Enable=Source" right under "#Disable=Control,Source" in the "[General]" section.
3. Restart the computer (to restart all the bluetooth 'stuff')
4. Pair the iPod touch and the computer by clicking the bluetooth icon -> Set up new device -> Forward. Click PIN options and select '1234', Close. Enable bluetooth on the iPod; on the computer select it in the list, Forward. Type the PIN (1234) on the iPod, Connect.
5. Install d-feet (from Synaptic) and run it (Applications -> Programming -> D-Feet). Then File -> Connect to System Bus. Under Bus Name select org.bluez and a tree will appear on the right. Under Object Paths, expand the /org/bluez/1464/hci0/dev's until you find the one with Interfaces that have org.bluez.AudioSource. Expand the AudioSource and double-click on Methods -> Connect(). A dialog will appear; just click Execute. It should say 'This method did not return anything' (I had to do it twice the first time.)
6. Open a terminal (Accessories -> Terminal) and type pacmd and press enter. 
6a. Then type list-sources and press enter. Find the one with device.description = "Name of your iPod" then scroll up to where it says 'name: ' (under 'index: ') and copy the name somewhere without the < and >(mine was bluez_source.00_...)  
6b. Then type list-sinks and press enter. I only had one (ALSA) and copy the name just as before (mine was alsa.output.pci-000_00...)
6c. Type exit and press enter.
7. Now type 'pactl load-module module-loopback source=YOURSOURCE sink=YOURSINK' (for me, it was pactl load-module module-loopback source=bluez_source.00_... sink=alsa.output.pci-000_00...) and press enter! Viola! Now the iPod should play through the computer as if it were a headset!

Note: Save the number that returns after pactl. When you disconnect your iPod, type pactl unload-module YOURNUMBER and press enter (it changes everytime; for example: pactl unload-module 25)

megamanexent, you have to connect AudioSource, not Audio.

Tell me if it works with the iPhone 4 ;)

---

### Post by megamanexent on 2010-06-25
Thank you thank you Thank you! Ric123,  jackflap

It works for me perfectly on iPhone 3G ( no iPhone 4 till july:(  ). I moved Enable=Source after [General] and AudioSource appeared, I had it at the very top of audio.conf!

---

### Post by jbeamz on 2010-07-14
Did it and it works for me... thanks! 

Now if only I could get it working on my xbmc live!

---

### Post by adityavpratap on 2010-08-06
Hi,
Thanks for such a informative post! However I have a Nokia mobile instead of an Ipod. Will the steps remain the same?
Ric123, I have reached step 5, but am stuck up at step 6.
list-sources in pacmd does not show my mobile.
Any suggestions,
Thanking in advance,

---

### Post by megamanexent on 2010-08-06
The steps should remain the same. Did you list your list-sources while your phone was connected? Look for a source that has the same address as your phone did in d-feet. It should start like bluez_source.xx_xx_xx_xx_xx_xx where the xx are the Bluetooth address for the phone. Some where in that section also there should be device.description = 'xxx' where the xxx is the bluetooth name of the phone. If you never changed it, the name should have Nokia in it.

I hope this helps!

---

### Post by adityavpratap on 2010-08-06
I seem to be missing something. The Nokia mobile is not listed in pacmd. It's mac number is nowhere to be seen in the output of list-sources. Can you share your /etc/bluetooth/audio.conf? I tried these steps in Ubuntu 10.04 aswell as in Linux Mint 8. In Ubuntu, AudioServer itself was missing from d-feet. In Linux Mint 8, I am unable to proceed beyond the 5th step. However audio streaming via bluetooth work in Windoze.:(

---

### Post by megamanexent on 2010-08-06
I'm currently not in front of my computer, but I will post it once I am able to.

---

### Post by megamanexent on 2010-08-06
> **adityavpratap said:**
> I seem to be missing something. The Nokia mobile is not listed in pacmd. It's mac number is nowhere to be seen in the output of list-sources. Can you share your /etc/bluetooth/audio.conf? I tried these steps in Ubuntu 10.04 aswell as in Linux Mint 8. In Ubuntu, AudioServer itself was missing from d-feet. In Linux Mint 8, I am unable to proceed beyond the 5th step. However audio streaming via bluetooth work in Windoze.:(

Don't get frustrated, I had the same problem, I couldn't find **AudioSource** in d-feet either. What solved it was to move Enable=Source to right after [General] . I am on Ubuntu 10.04

Heres my audio.conf 
```
# Configuration file for the audio service

# This section contains options which are not specific to any
# particular interface
[General]
Enable=Source
# Switch to master role for incoming connections (defaults to true)
#Master=true

# If we want to disable support for specific services
# Defaults to supporting all implemented services
#Disable=Control,Source

# SCO routing. Either PCM or HCI (in which case audio is routed to/from ALSA)
# Defaults to HCI
#SCORouting=PCM

# Automatically connect both A2DP and HFP/HSP profiles for incoming
# connections. Some headsets that support both profiles will only connect the
# other one automatically so the default setting of true is usually a good
# idea.
AutoConnect=true

# Headset interface specific options (i.e. options which affect how the audio
# service interacts with remote headset devices)
[Headset]

# Set to true to support HFP, false means only HSP is supported
# Defaults to true
HFP=true

# Maximum number of connected HSP/HFP devices per adapter. Defaults to 1
MaxConnected=1

# Just an example of potential config options for the other interfaces
#[A2DP]
#SBCSources=1
#MPEG12Sources=0
```

---

### Post by adityavpratap on 2010-08-07
Hi!
Thanks for the prompt reply.
My audio.conf is exactly the same as yours. I can find an entry corresponding to my Nokia mobiles bluetooth mac address in d-feet->org.bluez->"Object Path. However, in the corresponding "Interfaces", I fail to see AudioSource. There is only Audio. This is very frustrating!:(

---

### Post by megamanexent on 2010-08-07
I am assuming that you have rebooted your computer or Bluetooth  multiple times and if your audio.conf looks like mine then AudioSource should appear. What model Nokia phone do you have? Does it support A2DP? Try repairng the phone to the computer and see what happens.

---

### Post by adityavpratap on 2010-08-07
It is a low end Nokia model - Nokia 2730, audio-streaming over bluetooth works perfectly over Windows so I assume that A2DP is supported. But I don't know how to confirm. I have followed all the steps religiously, but still AudioSource is missing from d-feet.

---

### Post by megamanexent on 2010-08-07
I can confirm that phone has A2DP support. For Linux Mint 8, you might have to upgrade the bluez package to the latest version, however, Ubuntu 10.04 should work out the box. You need at least BlueZ 4.46 but the latest is probably best. I am not sure why you don't see AudioSource.

---

### Post by adityavpratap on 2010-08-07
You have been very patient with a newbie like me. Thanks for that! :-)
One question though, how do I check the version of Bluez?

---

### Post by megamanexent on 2010-08-07
We all were once newbies, I still consider myself a newbie. LOL. 
But you can open synaptic and type in BlueZ and see which version is currently installed.

---

### Post by megamanexent on 2010-08-07
For those of you who stumble on this thread and really would like a script to somewhat automate the process of connecting your A2DP device, I created such a script. It uses zenity to add a GUI element so you might have to install it from the repos if it is not installed.[COLOR=Black]While doing that, make sure libqt4-dbus is installed to, but it should be there already.[/COLOR][COLOR=Red] UPDATE: [/COLOR][COLOR=Black]libqt4-dbus is no longer needed as the script now uses 'dbus-send'.[/COLOR] Thank you hohlraum!

You still need to add your source and sink from pacmd with list-sources and list-sinks respectively to the script. I left a spot at the top of the script to add them. Leave no space between the '=' and what you type. You can type qdbus --system org.bluez into a terminal to find your device address ( If you do not have the package [COLOR=Black]libqt4-dbus installed, ignore this)[/COLOR]. It should look like /org/bluez/XXXX/hci0/dev_XX_XX_XX_XX_XX_XX where XX are numbers or letters. You only need to type the dev_XX_XX_XX_XX_XX_XX in the script. **Word of cation**, this script creates a file in your home directory called .bluetooth_unload, if you have a file with that name, change the script to not overwrite your file. I tried to make the script as portable as possible, but there may be something I missed so use it with discretion!!!!

Make sure the file is **executable** and your done. You can run the script from console, or add a launcher to your gnome menu to get the full GUI effect. Gnome-Do is also a good launcher too.;)

---

### Post by megamanexent on 2010-08-09
Those of you on Karmic will need to manually load the PulseAudio Bluetooth Module. 
This should install it
```
sudo apt-get install pulseaudio-module-bluetooth
```
This should load it
```
pactl load-module module-bluetooth-discover
```
After you get d-feet to show AudioSource, This should help you find the source while the device is connected
```
pactl list | grep bluez_source
```
This can help find the sink, but pacmd and list-sinks will give you all sinks if you have more than one sound card
```
pactl list | grep alsa_output
```

Follow Rick123 instructions ( or you could use the script above :D )and you should now have A2DP audio!!
[http://ubuntuforums.org/showpost.php?p=9511043&postcount=10](http://ubuntuforums.org/showpost.php?p=9511043&postcount=10)

---

### Post by Tylerc230 on 2010-08-10
I am able to connect to my ubuntu box and hear audio but it is very crackly and seems to be playing too slowly (like powering down a record player).  I'm running a fresh install of ubuntu 10.04 with iPhone 4 ios 4. Any suggestions? I get a similar effect when running an iPad with 3.2 on it. Lots of pitch shifting and echo effect.

---

### Post by megamanexent on 2010-08-10
I noticed this to, but it was off and on. I thought is might be pulseaudio, but looking at this bug report, it might be bluez [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/424215](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/424215)
Any way, there is a suggested fix and im going to try it to see if it helps.

** Update ** 

Seems to work better yes, but this is with an iPhone 3G.
what I did was from the bug report

```
sudo hciconfig hci0 lm ACCEPT,MASTER
```
```
sudo hciconfig hci0 lp HOLD,SNIFF,PARK
```

Now just to add it to udev to run at start-up :D

---

### Post by Tylerc230 on 2010-08-12
Didn't seem to work for me. There are other post regarding pulseaudio and varying playback speed so I think it has something to do with that. I'll post back if I find a solution.

---

### Post by sancelot on 2010-09-23
Hi,
I have tried this with maverick , and my phone, everything went well for setting up, but unfortunately no sound in the computer!

---

### Post by megamanexent on 2010-09-26
> **sancelot said:**
> Hi,
I have tried this with maverick , and my phone, everything went well for setting up, but unfortunately no sound in the computer!

Did you make sure to use the right sink and source when you ran  'pactl load-module module-loopback source=YOURSOURCE sink=YOURSINK'?
Theoretically, it should work on maverick.

---

### Post by TheKent on 2010-09-27
Hello. I have an iPod that I am trying to stream from, but I'm stuck at Ric123's number 6a. I can't find my iPod in 'list-sources'.
There's only 2 sources:

0: device.description = "Monitor of Intern lyd Analog Stereo"
1: device.description = "Intern lyd Analog Stereo"


 Managed to get the Audio-Sources in d-feet, and executed the 'connect ()', but still no luck in list-sources. Suggestions, anyone?

---

### Post by megamanexent on 2010-09-27
> **TheKent said:**
> Hello. I have an iPod that I am trying to stream from, but I'm stuck at Ric123's number 6a. I can't find my iPod in 'list-sources'.
There's only 2 sources:

0: device.description = "Monitor of Intern lyd Analog Stereo"
1: device.description = "Intern lyd Analog Stereo"


 Managed to get the Audio-Sources in d-feet, and executed the 'connect ()', but still no luck in list-sources. Suggestions, anyone?

Use ```
pactl list | grep bluez_source
``` to see if you can find it when your iPod is connected.

How could you have missed this? :lolflag:
[http://ubuntuforums.org/showpost.php?p=9698302&postcount=25](http://ubuntuforums.org/showpost.php?p=9698302&postcount=25)

---

### Post by Ashen001 on 2010-10-13
Even I had the same problem with my iPod touch, but I got it fixed now. Thank you for your help. The steps which you have mentioned are so simple, it does not take much time also. It can be done without any issues.  Now I am able to connect my iPod touch over Bluetooth and have the audio playing.

---

### Post by Sultan-mrm on 2010-10-15
> **Ric123 said:**
> It works! Thanks everyone! jackflap's link worked perfectly! [http://jprvita.wordpress.com/2009/12...4-a2dp-stream/](http://jprvita.wordpress.com/2009/12...4-a2dp-stream/)
I've upgraded to Ubuntu 10.04 by now; I have bluez 4.60 and pulseaudio 0.9.21. 
Here's how I did it for my iPod touch (3.1.3) on my Dell Inspiron 1720:
1. I skipped step one, it was already loaded.
2. Add "Enable=Source" right under "#Disable=Control,Source" in the "[General]" section.
3. Restart the computer (to restart all the bluetooth 'stuff')
4. Pair the iPod touch and the computer by clicking the bluetooth icon -> Set up new device -> Forward. Click PIN options and select '1234', Close. Enable bluetooth on the iPod; on the computer select it in the list, Forward. Type the PIN (1234) on the iPod, Connect.
5. Install d-feet (from Synaptic) and run it (Applications -> Programming -> D-Feet). Then File -> Connect to System Bus. Under Bus Name select org.bluez and a tree will appear on the right. Under Object Paths, expand the /org/bluez/1464/hci0/dev's until you find the one with Interfaces that have org.bluez.AudioSource. Expand the AudioSource and double-click on Methods -> Connect(). A dialog will appear; just click Execute. It should say 'This method did not return anything' (I had to do it twice the first time.)
6. Open a terminal (Accessories -> Terminal) and type pacmd and press enter. 
6a. Then type list-sources and press enter. Find the one with device.description = "Name of your iPod" then scroll up to where it says 'name: ' (under 'index: ') and copy the name somewhere without the < and >(mine was bluez_source.00_...)  
6b. Then type list-sinks and press enter. I only had one (ALSA) and copy the name just as before (mine was alsa.output.pci-000_00...)
6c. Type exit and press enter.
7. Now type 'pactl load-module module-loopback source=YOURSOURCE sink=YOURSINK' (for me, it was pactl load-module module-loopback source=bluez_source.00_... sink=alsa.output.pci-000_00...) and press enter! Viola! Now the iPod should play through the computer as if it were a headset!

Note: Save the number that returns after pactl. When you disconnect your iPod, type pactl unload-module YOURNUMBER and press enter (it changes everytime; for example: pactl unload-module 25)

megamanexent, you have to connect AudioSource, not Audio.

Tell me if it works with the iPhone 4 ;)



Thaaaaaaanks ,, 

Its work with Nexus One

---

### Post by Nephilime on 2010-10-21
I'm trying to stream audio from my iPhone 3GS iOS 4.01 to my linux computer via Bluetooth and A2DP.

**My setup:**
(ArchLinux)
Linux CoreNAS 2.6.34-Custom-Core #10 SMP PREEMPT Thu Aug 5 15:13:53 CEST  2010 i686 Intel(R) Atom(TM) CPU D510 @ 1.66GHz GenuineIntel GNU/Linux

Bluez 4.69

pulseaudio 0.9.21

The stream actually works, but every 1/2 seconds there is a glitch in  the audio. Sometimes there are pitches in the audio. The audio is being  streamed at 44.1Khz and my phone is in an acceptable range of the  bluetooth enabled computer.

Pulseaudio outputs about every 5 seconds:

I: module-loopback.c: Should buffer 36012 bytes, buffered at minimum 92178 bytes
I: module-loopback.c: Old rate 45022 Hz, new rate 45046 Hz
I: module-loopback.c: Loopback overall latency is 63.33 ms + 352.51 ms + 39.51 ms = 455.35 ms

I load the loopback module as follows:

*pactl load-module module-loopback  source=bluez_source.00_26_B0_8D_6F_39  sink=alsa_output.usb-Native_Instruments_Audio_2_DJ_SN-v42x7kbg-00-Audio2DJ.analog-stereo  rate=44100*

Does anybody have a clue or direction to solve this issue? Thanks in advance!

---

### Post by hohlraum on 2010-12-02
> **megamanexent said:**
> For those of you who stumble on this thread and really would like a script to somewhat automate the process of connecting your A2DP device, I created such a script. It uses zenity to add a GUI element so you might have to install it from the repos if it is not installed. While doing that, make sure libqt4-dbus is installed to, but it should be there already. 

You still need to add your source and sink from pacmd with list-sources and list-sinks respectively to the script. I left a spot at the top of the script to add them. Leave no space between the '=' and what you type. You can type qdbus --system org.bluez into a terminal to find your device address. It should look like /org/bluez/XXXX/hci0/dev_XX_XX_XX_XX_XX_XX where XX are numbers or letters. You only need to type the dev_XX_XX_XX_XX_XX_XX in the script. **Word of cation**, this script creates a file in your home directory called .bluetooth_unload, if you have a file with that name, change the script to not overwrite your file. I tried to make the script as portable as possible, but there may be something I missed so use it with discretion!!!!

Make sure the file is executable and your done. You can run the script from console, or add a launcher to your gnome menu to get the full GUI effect. Gnome-Do is also a good launcher too.;)

You mention in your code that it works with 9.10.  That is not my experience.  The instructions (using qdbus) at the beginning of the code and the code that sets the 'device' variable will not work with ubuntu 9.10.   This is because bluez doesn't support introspection in the version included with 9.10.

---

### Post by megamanexent on 2010-12-02
> **hohlraum said:**
> You mention in your code that it works with 9.10.  That is not my experience.  The instructions (using qdbus) at the beginning of the code and the code that sets the 'device' variable will not work with ubuntu 9.10.   This is because bluez doesn't support introspection in the version included with 9.10.

hohlram- see post(s)
[http://ubuntuforums.org/showpost.php?p=9511043&postcount=10](http://ubuntuforums.org/showpost.php?p=9511043&postcount=10)
[http://ubuntuforums.org/showpost.php?p=9698302&postcount=25](http://ubuntuforums.org/showpost.php?p=9698302&postcount=25)

In order to stream audio over bluetooth in Karmic, you have to upgrade the version of bluez from source (unless you find a .deb of the new version)( or use backports?). The new version will have the code for A2DP streaming. 

The problem you're seeing is that you need to have module-bluetooth-discover for pulseaudio installed and loaded. As [http://jprvita.wordpress.com/2009/12/15/1-2-3-4-a2dp-stream/](http://jprvita.wordpress.com/2009/12/15/1-2-3-4-a2dp-stream/) states: "If it’s not loaded you can use **pactl** to load it manually or configure PulseAudio to load it on startup in **/etc/pulse/default.pa**" The script will not set up A2DP streaming entirely in Karmic, which I did mention. You still have to follow the instructions for the initial set-up, then my script will become useful.

---

### Post by hohlraum on 2010-12-02
> **megamanexent said:**
> hohlram- see post(s)
[http://ubuntuforums.org/showpost.php?p=9511043&postcount=10](http://ubuntuforums.org/showpost.php?p=9511043&postcount=10)
[http://ubuntuforums.org/showpost.php?p=9698302&postcount=25](http://ubuntuforums.org/showpost.php?p=9698302&postcount=25)

In order to stream audio over bluetooth in Karmic, you have to upgrade the version of bluez from source (unless you find a .deb of the new version)( or use backports?). The new version will have the code for A2DP streaming. 

The problem you're seeing is that you need to have module-bluetooth-discover for pulseaudio installed and loaded. As [http://jprvita.wordpress.com/2009/12/15/1-2-3-4-a2dp-stream/](http://jprvita.wordpress.com/2009/12/15/1-2-3-4-a2dp-stream/) states: "If it’s not loaded you can use **pactl** to load it manually or configure PulseAudio to load it on startup in **/etc/pulse/default.pa**" The script will not set up A2DP streaming entirely in Karmic, which I did mention. You still have to follow the instructions for the initial set-up, then my script will become useful.

I should have explained a bit better. Karmic and your instructions on the first page work just fine with all existing/available packages for Karmic (no upgrading required).  Your script works fine as well if a few parts are modified to use dbus-send instead of qdbus.

---

### Post by hohlraum on 2010-12-03
So now that everyone is awake has anyone figured out a way to control your phone/device from the computer?  Normally you've got bt headphones (pause/play, skip forward/reverse, vol up/down) controlling (AVRCP profile) the device but since the computer "is/are" the head phones there must be a way to do it via dbus methods maybe?  Didn't see anything obvious using d-peek

---

### Post by megamanexent on 2010-12-05
hohlraum - Ahh! Now I understand, thank you! I'm not to confident in using dbus-send, but I will try to rewrite the script. Sorry about that, I should have personally tested the script on Karmic.


> **hohlraum said:**
> So now that everyone is awake has anyone figured out a way to control your phone/device from the computer? Normally you've got bt headphones (pause/play, skip forward/reverse, vol up/down) controlling (AVRCP profile) the device but since the computer "is/are" the head phones there must be a way to do it via dbus methods maybe? Didn't see anything obvious using d-peek

Using d-feet, I see some control methods under org.bluez.Headset. But I don't think that will help. For now I just use veency with vncviewer !! ;)

Maybe somebody will eventually write something to accomplish this. I would if I knew how.

---

### Post by hohlraum on 2010-12-05
Actually, I'm dumb.  There is no reason to use dbus-send (although it would remove the scripts dependancy on qdbus).  Your method for retreiving the device path is really the only issue as it uses introspection which bluez under karmic doesn't support.  I'll post the fix that doesn't use introspection (its just one extra command to get the bt adapter path).

---

### Post by megamanexent on 2010-12-05
Quick question, is it the bluetooth adapter my script cannot find, or is it the A2DP device?

---

### Post by hohlraum on 2010-12-06
> **megamanexent said:**
> Quick question, is it the bluetooth adapter my script cannot find, or is it the A2DP device?
Bluez won't allow qdbus to just scan and return everything it sees.  This is called introspection.  Let me post my fix tomorrow before you spend any time on it.

---

### Post by hohlraum on 2010-12-06
The issue:

$ qdbus --system --literal org.bluez
/
Cannot introspect object / at org.bluez:
org.freedesktop.DBus.Error.UnknownInterface (Interface 'org.freedesktop.DBus.Introspectable' was not found)

The fix:

qdbus --system --literal org.bluez / org.bluez.Manager.ListAdapters

for each adapter until we find our phone/device:

qdbus --system --literal org.bluez ADAPTERPATH org.bluez.Adapter.ListDevices

However, your script currently just assumes that the user only has one bluetooth adapter (hci0) in the system so:

qdbus --system --literal org.bluez / org.bluez.Manager.DefaultAdapter
qdbus --system --literal org.bluez <DEFAULTADAPTER> org.bluez.Adapter.ListDevices

Right now your script uses:

device=`qdbus --system org.bluez | grep /hci0/$your_device`

and instead could use:

adapter_device=`qdbus --system --literal org.bluez / org.bluez.Manager.DefaultAdapter | sed -n 's:^[^/]*\([^]]*\)]:\1:p'`
device=`qdbus --system --literal org.bluez $adapter_device org.bluez.Adapter.ListDevices | sed -n 's/^.*Path: \([^]]*\)]}]/\1/p' | grep $your_device`

This will work in all versions of ubuntu regardless of how old their bluez version is as long as they have qdbus.

Anything you can do with qdbus you can do with dbus-send if you want to remove the depency on qdbus.  The only issue is that dbus-send returns xml instead of python data structures. The parameters are nearly identical:

qdbus --system --literal org.bluez <everything else is identical>

is the same as:

dbus-send --system --print-reply --dest=org.bluez <everything else is identical>

---

### Post by megamanexent on 2010-12-07
hohlraum - Thank you for your help. I rewritten the script to use dbus-send and included your fix. Hopefully by doing so, other distros besides Ubuntu can use it too.

 Right now I don't have access to Karmic, do you mind if you could test the script out to see if the changes work?

---

### Post by petekalo on 2011-01-01
> **Ric123 said:**
> It works! Thanks everyone! jackflap's link worked perfectly! [http://jprvita.wordpress.com/2009/12...4-a2dp-stream/](http://jprvita.wordpress.com/2009/12...4-a2dp-stream/)
I've upgraded to Ubuntu 10.04 by now; I have bluez 4.60 and pulseaudio 0.9.21. 
Here's how I did it for my iPod touch (3.1.3) on my Dell Inspiron 1720:
1. I skipped step one, it was already loaded.
2. Add "Enable=Source" right under "#Disable=Control,Source" in the "[General]" section.
3. Restart the computer (to restart all the bluetooth 'stuff')
4. Pair the iPod touch and the computer by clicking the bluetooth icon -> Set up new device -> Forward. Click PIN options and select '1234', Close. Enable bluetooth on the iPod; on the computer select it in the list, Forward. Type the PIN (1234) on the iPod, Connect.
5. Install d-feet (from Synaptic) and run it (Applications -> Programming -> D-Feet). Then File -> Connect to System Bus. Under Bus Name select org.bluez and a tree will appear on the right. Under Object Paths, expand the /org/bluez/1464/hci0/dev's until you find the one with Interfaces that have org.bluez.AudioSource. Expand the AudioSource and double-click on Methods -> Connect(). A dialog will appear; just click Execute. It should say 'This method did not return anything' (I had to do it twice the first time.)
6. Open a terminal (Accessories -> Terminal) and type pacmd and press enter. 
6a. Then type list-sources and press enter. Find the one with device.description = "Name of your iPod" then scroll up to where it says 'name: ' (under 'index: ') and copy the name somewhere without the < and >(mine was bluez_source.00_...)  
6b. Then type list-sinks and press enter. I only had one (ALSA) and copy the name just as before (mine was alsa.output.pci-000_00...)
6c. Type exit and press enter.
7. Now type 'pactl load-module module-loopback source=YOURSOURCE sink=YOURSINK' (for me, it was pactl load-module module-loopback source=bluez_source.00_... sink=alsa.output.pci-000_00...) and press enter! Viola! Now the iPod should play through the computer as if it were a headset!

Note: Save the number that returns after pactl. When you disconnect your iPod, type pactl unload-module YOURNUMBER and press enter (it changes everytime; for example: pactl unload-module 25)

megamanexent, you have to connect AudioSource, not Audio.

Tell me if it works with the iPhone 4 ;)


I am trying it with the iphone 4, with a new AZIO bluetooth adapter, and I have been able to get output. However it is essentially unusable because there is an outrageous amount of static, it even slows down the playback speed. Anyone run into this?

---

### Post by Timbo337 on 2011-01-30
Thanks for posting this! I have been wanting to set something like this up since I got my Droid, but just now got around to it.

I have it working with Ubuntu 10.04 and Motorola Droid. The biggest problem was just needing to restart instead of 'bluetoothd restart', to get the Audiosource interface... which wasn't much of a problem.

My plan now is to set this up in my car with something running embedded linux, such as a beagleboard. I only have an aux in on my head unit, but want to go wireless (which will also eliminate the ground-loop problem I have when charging the phone and have the phone plugged into the aux in... no more static when charging!)

---

### Post by brianallred on 2011-02-10
> **petekalo said:**
> I am trying it with the iphone 4, with a new AZIO bluetooth adapter, and I have been able to get output. However it is essentially unusable because there is an outrageous amount of static, it even slows down the playback speed. Anyone run into this?
I am having the exact same issue with 10.10 and my iPhone 4. Haven't yet solved it.

---

### Post by oscrp on 2011-02-13
> **brianallred said:**
> I am having the exact same issue with 10.10 and my iPhone 4. Haven't yet solved it.

Same here with an iPad, albeit there isn't any problems when streaming from my Nexus one through A2DP.. Hope someone find a reason for this bad behaviour

---

### Post by zansatsu0 on 2011-02-25
I figured since this thread got revived, I would share this script I wrote. The script is attached. It wouldn't let me attach the config file, but I'm sure you can do:
```
sudo gedit /etc/bluetooth/audio.conf
```

I have not tested this on any other system and I cannot guarantee that it will even work for you, but I figured someone may find it useful. At the worst, it will just error out on you. At the best, it will work. Enjoy. :)

My sources were two users on these forums and they gave me just enough to get this script done. Thanks goes out to the OP of this thread Ric123, especially this post:
[http://ubuntuforums.org/showpost.php?p=9511043&postcount=10]("http://ubuntuforums.org/showpost.php?p=9511043&postcount=10")

And megamanextent at this thread:
[http://ubuntuforums.org/showpost.php?p=9698302&postcount=25]("http://ubuntuforums.org/showpost.php?p=9698302&postcount=25")

I had to edit my **_/etc/bluetooth/audio.conf_** to look like this:
```
# Configuration file for the audio service

# This section contains options which are not specific to any
# particular interface
[General]

# Switch to master role for incoming connections (defaults to true)
Master=true

# If we want to disable support for specific services
# Defaults to supporting all implemented services
#Disable=Control,Source
Enable=Source

# SCO routing. Either PCM or HCI (in which case audio is routed to/from ALSA)
# Defaults to HCI
#SCORouting=PCM

# Automatically connect both A2DP and HFP/HSP profiles for incoming
# connections. Some headsets that support both profiles will only connect the
# other one automatically so the default setting of true is usually a good
# idea.
AutoConnect=true

# Headset interface specific options (i.e. options which affect how the audio
# service interacts with remote headset devices)
[Headset]

# Set to true to support HFP, false means only HSP is supported
# Defaults to true
HFP=true

# Maximum number of connected HSP/HFP devices per adapter. Defaults to 1
MaxConnected=1

# Just an example of potential config options for the other interfaces
#[A2DP]
#SBCSources=1
#MPEG12Sources=0
```

**_connectBTAudio.sh_**
```
#!/bin/bash
# Credit to Ric123 and megamanextent for the primer material
# found at UbuntuForums.Org
#---------------------------------------------------------------
# Written by Alex Zaballa on 02/24/2011
# Distributed under GPL v.2.
# Use at your own risk. There is no guarantee this will work
# but shouldn't hurt anything.
#---------------------------------------------------------------
# This script is designed to work in Ubuntu Maverick 10.10
# so I can pair my Android to Ubuntu. I have not tested this
# with IPhone in any flavor. Your mileage may vary.
# It requires qdbus and Pulse Audio.
# This also assumes that your audio.conf file in
# /etc/bluetooth is configured properly.

clear

echo "Please pair and connect your device."
read -p "Press any key to initialize audio..." -n 1 garbageVar

# Return Example: /org/bluez/29159/hci0/dev_01_23_45_AB_CD_EF
qPath="$(qdbus --system org.bluez | grep -m 1 "/dev_")"

# Even though the phone says it's connected, it doesn't work
# unless I hard-reset the connection. Also, AudioSource.Disconnect
# won't work reliably in this situation, so I tried the Device.Disconnect
# method which seems to work well for my Gingerbread Hero (Android 2.3).
qdbus --system org.bluez "${qPath}" org.bluez.Device.Disconnect 1> /dev/null
sleep 5
echo "Attempting connection..."
qdbus --system org.bluez "${qPath}" org.bluez.AudioSource.Connect 1> /dev/null


# Return Example: bluez_source.01_23_45_AB_CD_EF
bluezSource="$(pactl list | grep -m 1 "Name: bluez_source" | cut -c 8-)"
echo "Bluez Source: ${bluezSource}"

# Return Example: alsa_output.pci-0000_00_10.1.analog-stereo
alsaSink="$(pactl list | grep -m 1 "Name: alsa_output" | cut -c 8-)"
echo "Alsa Sink: ${alsaSink}"

# Return Example: 25
paID="$(pactl load-module module-loopback source="${bluezSource}" sink="${alsaSink}")"
echo "pactl ID number: ${paID}"

read -p "Press any key to disconnect..." -n 1 garbageVar

pactl unload-module "${paID}"
qdbus --system org.bluez "${qPath}" org.bluez.AudioSource.Disconnect
```

---

### Post by hero809 on 2011-03-09
first timer here but i have managed to follow all the instructions to the best of my ability, everything went as instructed without issues until the last part. **pactl load-module module-loopback source=bluez_source.11_22_33_44_55_66 sink=alsa_output.pci-0000_01_00.1.hdmi-stereo** the source being my evo 4g and my computer a hp dv8. long story short it says **Connection failure: Connection refused. **i dont know what i did wrong. i need help. my computer can play music from my phone. i had windows 7 at one point and it worked fin then but i now have ubuntu 10.10 and i dont know my way around this problem. thank you who ever reads this.

---

### Post by hero809 on 2011-03-09
i reset pulseaudio and now i get this Failure: Module initalization failed

---

### Post by lothar83fr on 2011-03-10
> **hero809 said:**
> i reset pulseaudio and now i get this Failure: Module initalization failed

You can see what happened in /var/log/syslog 

Some one has resolv the iphone 4 issue? I tried many rate but the song still bad and some times the speed increase.
I use bluez 4.60-0ubuntu8, maybe I should update this...

---

### Post by HeinekenPissr on 2011-03-17
OK so I set it up as described and it works but the audio quality is such crap that I would never bother using this.  

I was hoping to be able to watch my movies on my ipad (streaming through airvideo from my linux server) and to be able to get the audio of the movie on my ubuntu 10.10 computer speakers.  This presently works...kind of. But the quality is terrible.

Anyone the static /audio quality problems on this yet?  Does this work perfectly for anyone?  Is there better success with different bluetooth dongles?

---

### Post by sherman on 2011-03-17
I've managed to get my iPhone 4 to connect and play via PulseAudio on Ubuntu 10.10, and I am using a Apple Wireless Keyboard (obviously via bluetooth) and every half second there is an audio interruption that is almost like a lost packet of audio. The audio keeps playing however...

I am assuming this is a combination between something in Bluez, the nondescript bluetooth device I am using and the fact the keyboard is polling the bluetooth stack every half a second at least.

I can't really try this combination in Windows, since this is my work PC and I'm sure they'd fire my *** if I installed Windows myself (not that I want to... *shudders*). Not that it matters... we are getting a fresh install of Windows 7 in a few weeks (cries).

Just thought I'd add my feedback!

---

### Post by HeinekenPissr on 2011-03-19
Ok so now I'm looking for other alternatives for the same objective as this solution is not sufficient due to low quality audio and an audio to video lag of 5 secs when streaming audio over bluetooth. I have 2 more ideas about this.


**Objective:** Airvideo works perfectly streaming from my media center to my IPAD. However sometimes the audio ouput on the ipad is too low and i wish to have louder better quality sound output. I have another computer in my room with a nice speaker systemwhich i would like to use for audio of the movie. 

**Option 1: **I figure I should be able to access the AirVideo stream through VLC on my desktop so that i could simultaneously play the file on the IPAD and my computer to allow for better sound. To do this i need to know what the URL is of the airvideo server to enter into VLC Network Stream. I have found the port number to be 46631 and my the IP of my server is 192.168.3.10. Any ideas about the full network stream?

**Option 2:** I could go the more expensive route of using the airport express to hook up my speakers to. Evidently, native to the iPad is the ability to choose your iPad speakers or speakers hooked up to airstream as audio output. However I am running Ubuntu and It is not clear to me if it is required to run iTunes for this to work. However the movie would be streaming from an air video server running on another Ubuntu box and not through iTunes so I don't see why iTunes would need to be installed.

Any thoughts or other ideas?

---

### Post by HeinekenPissr on 2011-03-19
> **HeinekenPissr said:**
> Ok so now I'm looking for other alternatives for the same objective as this solution is not sufficient due to low quality audio and an audio to video lag of 5 secs when streaming audio over bluetooth. I have 2 more ideas about this.


**Objective:** Airvideo works perfectly streaming from my media center to my IPAD. However sometimes the audio ouput on the ipad is too low and i wish to have louder better quality sound output. I have another computer in my room with a nice speaker systemwhich i would like to use for audio of the movie. 

**Option 1: **I figure I should be able to access the AirVideo stream through VLC on my desktop so that i could simultaneously play the file on the IPAD and my computer to allow for better sound. To do this i need to know what the URL is of the airvideo server to enter into VLC Network Stream. I have found the port number to be 46631 and my the IP of my server is 192.168.3.10. Any ideas about the full network stream?

**Option 2:** I could go the more expensive route of using the airport express to hook up my speakers to. Evidently, native to the iPad is the ability to choose your iPad speakers or speakers hooked up to airstream as audio output. However I am running Ubuntu and It is not clear to me if it is required to run iTunes for this to work. However the movie would be streaming from an air video server running on another Ubuntu box and not through iTunes so I don't see why iTunes would need to be installed.

Any thoughts or other ideas?

So after some more digging around on the internet and at the airvideo forums it appears that Option1 will not be feasible for technical reasons i'm not prepared to get into.

So possible option 2 or some other idea altogether unless of course someone found a way to get this bluetooth to work perfectly without static but then I would still except an audio lag problem

---

### Post by sofiazara on 2011-03-20
Has anyone looked at their bluetooth and wondered why Apple  incorporated it into the iPhone? In my opinion it seems pretty standard  to do these days as every handset adopts it, however i have never ever  used it on my iPhone. It simply doesn't have any function in the iPhone  OS. The most it can do is pair a handset and that is about it. Well here  is a list of 5 features I reckon that Apple and developers ought to  incorporated in the iPhone and its functions.
1. The transfer of  videos, applications and music from iTunes to the iPhone. I realize  there may be many issues but i wonder if it was possible to do that. I  find myself sometimes in a rush and just want to transfer the app across  quickly without having to though my draw and find the sync cable.
2.  Use bluetooth to connect a sort of controller to the iPhone unit. I  realize many games may not be able to use it however it their start to  build add-ons like these, they can greatly increase the amount of  buttons available which would make the gaming experience so much better.
3.  Use bluetooth to connect the iPhone wirelessly to a set of speakers.  Ok! Maybe this is not to best idea when it comes to docking it for the  night as would would have to connect it up and charge it. The benefit  lies in when you walk in the door and want to play music. Simply just  play from the iPhone as it instantly recognizes your bluetooth wireless  speakers. It would be great as you walked through different rooms and  speakers in each room could pick up on the bluetooth transmission from  the iPhone.

---

### Post by krshna_r on 2011-04-06
Hi,
I am trying stream music files from my samsung galaxy to i.Mx51 evalkit which boots Ubuntu.
 
I successfully followed the steps given by Ric123
 
i am able to find source as bluez_source.myphonebluetoothaddr and sink as alsa_output.platform-soc-audio.2.analog-stereo
 
but after giving the cmd 'pactl load-module module-loopback source=MYSOURCE sink=MYSINK and playing the song in my phone i am not able to hear any sound from the speakers connected to eval kit.
 
whr i am going wrong.
plz reply

---

### Post by livinginx on 2011-04-13
I've tried the steps posted by Ric123 but am having issues.

After I restart and pair my computer to my Nokia phone, my pulseaudio stops working.

If I type 'pacmd' into a terminal, I get 'No PulseAudio daemon running, or not running as session daemon.' or 'Failed to kill PulseAudio daemon'

I am running 10.04 but no luck in getting this to work.  Any help?

---

### Post by -gr00ve- on 2011-04-29
Hi,

my Ipod 4G (no jailbreak) connects fine, but i have the same problem with bad quality.
Running Ubuntu 10.10.
The Iphone 3GS and the Ipod Touch is working better ?

Greetings.

---

### Post by gerard187 on 2011-05-24
My Motorola Atrix sounds find but the Ipod Touch 2G sounds like crap. This is all under Natty 11.04.

---

### Post by elysion on 2011-06-28
I have been trying to get this working with Kubuntu 11.04 and Nokia N9. I called the Connect method of org.bluez.AudioSource under the object path of the N9 on the Kubuntu laptop, but I just get the following error:

'org.bluez.Error.Failed: Stream setup failed'

Anyone had this issue? Any ideas how to make this work?

---

### Post by elysion on 2011-06-28
Another thing I was wondering was if it would be possible for bluez to provide a org.bluez.AudioSink.Connect() method on the laptop? That way I could connect to the laptop in similar manner as to any bluetooth headset.

---

### Post by kais on 2011-08-26
> **elysion said:**
> I have been trying to get this working with Kubuntu 11.04 and Nokia N9. I called the Connect method of org.bluez.AudioSource under the object path of the N9 on the Kubuntu laptop, but I just get the following error:
 
'org.bluez.Error.Failed: Stream setup failed'
 
Anyone had this issue? Any ideas how to make this work?
 
 
I met the same issue with Android phone and ubuntu 10.4. After numerous tries, I found the following steps would help:
 
1. unpair the phone with ubuntu and pair again and have a try.
 
2. if the previous step does not work, make sure when you pair phone with ubuntu, you don't make them connect. you only pair it.

---

### Post by kais on 2011-08-26
i met the same issue ocassionally. seems the deamon crashed. 
 
ps -aef | grep pulse 
 
would yield pulseaudio deamon not there.
 
reboot the system would work.
 
> **livinginx said:**
> I've tried the steps posted by Ric123 but am having issues.
 
After I restart and pair my computer to my Nokia phone, my pulseaudio stops working.
 
If I type 'pacmd' into a terminal, I get 'No PulseAudio daemon running, or not running as session daemon.' or 'Failed to kill PulseAudio daemon'
 
I am running 10.04 but no luck in getting this to work. Any help?

---

### Post by kais on 2011-08-26
I had similar experience with destop ubuntu 10.4. After successfully followed the steps, namely finishing 'pactl load-module module-loopback source=bluez_source.xx.xx.xx.xx.xx sink=..." which seems to suceed, I can't hear any music. 
 
What is more, if I play youtube from safari, I can't hear anything. The interesting thing to note is that the sound control icon on the upper right bar changed shape to dot dot shape.
 
Any one has similar experience would like to share your solution?
 
> **krshna_r said:**
> Hi,
I am trying stream music files from my samsung galaxy to i.Mx51 evalkit which boots Ubuntu.
 
I successfully followed the steps given by Ric123
 
i am able to find source as bluez_source.myphonebluetoothaddr and sink as alsa_output.platform-soc-audio.2.analog-stereo
 
but after giving the cmd 'pactl load-module module-loopback source=MYSOURCE sink=MYSINK and playing the song in my phone i am not able to hear any sound from the speakers connected to eval kit.
 
whr i am going wrong.
plz reply

---

### Post by kais on 2011-08-29
Tried a little bit more. 
 
Open system->preference->sound, click input, I do see the A2DP card as input.
However, as soon as I start to steam audio from the phone, I get a popup window saying "Waiting for sound system to respond" forever.
 
> **kais said:**
> I had similar experience with destop ubuntu 10.4. After successfully followed the steps, namely finishing 'pactl load-module module-loopback source=bluez_source.xx.xx.xx.xx.xx sink=..." which seems to suceed, I can't hear any music. 
 
What is more, if I play youtube from safari, I can't hear anything. The interesting thing to note is that the sound control icon on the upper right bar changed shape to dot dot shape.
 
Any one has similar experience would like to share your solution?

---

### Post by drinkmilk on 2011-09-15
It actually seems that a lot of issues were fixed lately since running Ubuntu 11.10 (beta) I can finally get lots of different configurations to work (from different phones to different bluetooth dongles on 3 differents machines) flawlessly. None of these configurations was working (stuttering sound) with 11.04. I would be interested to know which component fixed that if anyone knows: bluez, pulseaudio, the kernel, alsa?

Anyway, that’s a really good news.

---

### Post by jayk_s4 on 2011-11-30
This script worked for me in Ubuntu 11.10, streaming music from a gingerbread droid to a rocketfish bt adapter.  Very cool!

The only thing I have to do in addition to run the script is open the Sound Settings, select Output, and then select my "Internal Audio Digital Stereo (HDMI)" device, and then click back onto the "Internal Audio Analog Stereo" device.  Maybe the script is picking the wrong output device by default?

Second, I want to put this server in my basement out of the way and stream music to it from anywhere in the house.  Obviously if I have to walk all the way to the basement and run this script it isn't going to be very convenient.  Any ideas on how to automate or make it permanent?

Thanks for the help everybody who is looking for a solution.  I hope this includes the ubuntu team and upstream folks...

EDIT : NVM, figured the first problem out.  Changed the alsaSink line to be more specific about which output driver to use.
alsaSink="$(pactl list | grep -m 1 "Name: alsa_output.*analog-stereo" | cut -c 8-)"

> **zansatsu0 said:**
> I figured since this thread got revived, I would share this script I wrote. The script is attached. It wouldn't let me attach the config file, but I'm sure you can do:
```
sudo gedit /etc/bluetooth/audio.conf
```I have not tested this on any other system and I cannot guarantee that it will even work for you, but I figured someone may find it useful. At the worst, it will just error out on you. At the best, it will work. Enjoy. :)

My sources were two users on these forums and they gave me just enough to get this script done. Thanks goes out to the OP of this thread Ric123, especially this post:
[http://ubuntuforums.org/showpost.php?p=9511043&postcount=10](http://ubuntuforums.org/showpost.php?p=9511043&postcount=10)

And megamanextent at this thread:
[http://ubuntuforums.org/showpost.php?p=9698302&postcount=25](http://ubuntuforums.org/showpost.php?p=9698302&postcount=25)

..code clipped...



---

### Post by jamfreak on 2012-09-27
Stupid question... but how do I run this script? Just download it and click on it?


> **zansatsu0 said:**
> I figured since this thread got revived, I would share this script I wrote. The script is attached. It wouldn't let me attach the config file, but I'm sure you can do:
```
sudo gedit /etc/bluetooth/audio.conf
```I have not tested this on any other system and I cannot guarantee that it will even work for you, but I figured someone may find it useful. At the worst, it will just error out on you. At the best, it will work. Enjoy. :)

My sources were two users on these forums and they gave me just enough to get this script done. Thanks goes out to the OP of this thread Ric123, especially this post:
[http://ubuntuforums.org/showpost.php?p=9511043&postcount=10](http://ubuntuforums.org/showpost.php?p=9511043&postcount=10)

And megamanextent at this thread:
[http://ubuntuforums.org/showpost.php?p=9698302&postcount=25](http://ubuntuforums.org/showpost.php?p=9698302&postcount=25)
Stupid question... but how do I run this script? Just download it and click on it?            please help...





I had to edit my **_/etc/bluetooth/audio.conf_** to look like this:
```
# Configuration file for the audio service

# This section contains options which are not specific to any
# particular interface
[General]

# Switch to master role for incoming connections (defaults to true)
Master=true

# If we want to disable support for specific services
# Defaults to supporting all implemented services
#Disable=Control,Source
Enable=Source

# SCO routing. Either PCM or HCI (in which case audio is routed to/from ALSA)
# Defaults to HCI
#SCORouting=PCM

# Automatically connect both A2DP and HFP/HSP profiles for incoming
# connections. Some headsets that support both profiles will only connect the
# other one automatically so the default setting of true is usually a good
# idea.
AutoConnect=true

# Headset interface specific options (i.e. options which affect how the audio
# service interacts with remote headset devices)
[Headset]

# Set to true to support HFP, false means only HSP is supported
# Defaults to true
HFP=true

# Maximum number of connected HSP/HFP devices per adapter. Defaults to 1
MaxConnected=1

# Just an example of potential config options for the other interfaces
#[A2DP]
#SBCSources=1
#MPEG12Sources=0
```**_connectBTAudio.sh_**
```
#!/bin/bash
# Credit to Ric123 and megamanextent for the primer material
# found at UbuntuForums.Org
#---------------------------------------------------------------
# Written by Alex Zaballa on 02/24/2011
# Distributed under GPL v.2.
# Use at your own risk. There is no guarantee this will work
# but shouldn't hurt anything.
#---------------------------------------------------------------
# This script is designed to work in Ubuntu Maverick 10.10
# so I can pair my Android to Ubuntu. I have not tested this
# with IPhone in any flavor. Your mileage may vary.
# It requires qdbus and Pulse Audio.
# This also assumes that your audio.conf file in
# /etc/bluetooth is configured properly.

clear

echo "Please pair and connect your device."
read -p "Press any key to initialize audio..." -n 1 garbageVar

# Return Example: /org/bluez/29159/hci0/dev_01_23_45_AB_CD_EF
qPath="$(qdbus --system org.bluez | grep -m 1 "/dev_")"

# Even though the phone says it's connected, it doesn't work
# unless I hard-reset the connection. Also, AudioSource.Disconnect
# won't work reliably in this situation, so I tried the Device.Disconnect
# method which seems to work well for my Gingerbread Hero (Android 2.3).
qdbus --system org.bluez "${qPath}" org.bluez.Device.Disconnect 1> /dev/null
sleep 5
echo "Attempting connection..."
qdbus --system org.bluez "${qPath}" org.bluez.AudioSource.Connect 1> /dev/null


# Return Example: bluez_source.01_23_45_AB_CD_EF
bluezSource="$(pactl list | grep -m 1 "Name: bluez_source" | cut -c 8-)"
echo "Bluez Source: ${bluezSource}"

# Return Example: alsa_output.pci-0000_00_10.1.analog-stereo
alsaSink="$(pactl list | grep -m 1 "Name: alsa_output" | cut -c 8-)"
echo "Alsa Sink: ${alsaSink}"

# Return Example: 25
paID="$(pactl load-module module-loopback source="${bluezSource}" sink="${alsaSink}")"
echo "pactl ID number: ${paID}"

read -p "Press any key to disconnect..." -n 1 garbageVar

pactl unload-module "${paID}"
qdbus --system org.bluez "${qPath}" org.bluez.AudioSource.Disconnect
```

---

### Post by zander1013 on 2013-01-05
hi,

i have it working on kubuntu 12.10 with iPhone 4 as a source.

it works okay but it does cut-out sometimes.

i will remark pactl was initially returning > alonzo@eartha:~$ pacmd
Daemon not responding.
 i am not sure what happened to get it going. :confused:

also? i am not sure what was meant by "save the number after pactl",,,

here is the output when i ran pactl load-module,,,,
> >>> exit
alonzo@eartha:~$ pactl load-module module-loopback source=bluez_source.7C_C5_37_1D_80_88 sink=alsa_output.pci-0000_00_1b.0.analog-stereo
19
alonzo@eartha:~$ pactl
No valid command specified.
alonzo@eartha:~$ pactl


is the number i should make note of 19?

please advise.

thank you for a great thread!

---

### Post by jianyongng on 2013-02-08
why am I getting this?

```
$ pactl load-module module-loopback source=bluez_source.90_C1_15_7F_F7_58 sink=alsa_card.pci-0000_00_1b.0
Failure: Module initalization failed

```

---

### Post by salinmooch on 2013-02-12
I see that this post is still active.  I recently was struggling through the same thing with my 12.10 - trying to stream audio from my android phone to my workstation which has nice studio speakers on it.  I was disappointed the default bluetooth applet did not support this in a nice GUI way - but I found the old standby blueman did.  Its a bit ugly but gets the job done with a single right click on the device (my phone) and selecting it the audio source (e.g. A2DT) and you are done.

[https://apps.ubuntu.com/cat/applications/precise/blueman/](https://apps.ubuntu.com/cat/applications/precise/blueman/)

[IMG]https://dl.dropbox.com/u/585302/Screenshot%20from%202013-02-12%2013%3A22%3A30.png[/IMG]

---

### Post by ICouldBeAnyone on 2013-06-16
I know this post is old - but for future people wanting a less complicated way of doing this, there is now an application that will let you listen to your iPhone, iPod, or other android device with bluetooth music streaming capability&#8217;s. It is aptly named Listen. After paring your device to your computer, open Listen and select the device from the drop down menu. Then check the check box! :D

Listen seems much more easy than going through all these .config files. Then again, I have never tried the methods in this thread...

EDIT:
Before I forget, here is the link to [Listen!]("apt:pct-listen")

---

### Post by riddelltm on 2014-04-27
Still working in 12.04 LTS with iPhone 5 on iOS 6, one note (may have missed in gloss over trying to get it to work) is that you have to have to go into Sound Settings and under the Input Tab you have to Select the bluetooth device in the "Record Sound from" field, otherwise the audio is not looped through the speakers.

---

### Post by cydewaze on 2015-02-22
Funny, I got this working just using blueman the other day, and now I can't get it to work again to save my life.  When I right click on my phone on the Devices list, I don't get any audio options.  When I refresh services, I get this:

> Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Argh! Any ideas?

EDIT: Turns out I had to do two things.

1) Pull my bluetooth dongle and plug it back in (weird)
2) Update my pulseaudio driver and reloading the module as per this how-to: [http://zach-adams.com/2014/07/bluetooth-audio-sink-stream-setup-failed/](http://zach-adams.com/2014/07/bluetooth-audio-sink-stream-setup-failed/)

FYI, if your sound quality is horrible on the PC speakers, try turning the volume on the phone down and your speakers up instead.

---

