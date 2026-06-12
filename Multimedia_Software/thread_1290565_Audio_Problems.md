---
title: "Audio Problems"
date: 2009-10-13
forum: Multimedia Software
---

### Post by eddtox on 2009-10-13
Hello, I've been messing about with linux (Ubuntu & openSUSE mainly) for a few days and I can't seem to get my audio working properly. I've tried various different walkthroughs and fixes but they don't seem to work. 

I have a Compaq SR1629UK (Standard except for ATI AIW 2006 graphics upgrade) and when I install linux (Ubuntu/openSUSE) the audio is really quiet (probably less than 25% as loud as it would be in windows). I have checked the volume controls, tried modifying alsa-base.conf, tried gnome-alsamixer, padevchooser etc etc etc. Whenever I manage to get the sound to be louder it becomes heavily distorted.

 Any help would be greatly appreciated as I would love to be able to use linux.

Thanks,
ed

---

### Post by eddtox on 2009-10-16
Hello?

---

### Post by eddtox on 2009-10-17
BUMP

Because im wondering how on earth i manage to get ignored by the largest and most helpful community on the net.

---

### Post by eddtox on 2009-10-21
Hello???  Where is everyone?

---

### Post by eddtox on 2009-10-29
[message deleted]

---

### Post by tuahaa on 2009-10-29
Calm down kiddo. 

Try the general help thread

---

### Post by karimruan on 2009-10-29
Take a look at this, it helped me alot: [http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

---

### Post by karimruan on 2009-10-29
After re-reading your thread, if none of stuff in the above link works (which I doubt, it should work fine) you should try to make sure that the volume is all the way up in alsamixer. Go to Applications>Accessories>Terminal and type in "alsamixer" without the quotes.

When alsamixer comes up (it is text based) make sure that Master is turned all the way up. You just select it with the arrow keys, and press up to turn the volume up.

Let me know how these two things work for you!

---

### Post by eddtox on 2009-10-29
> **tuahaa said:**
> Calm down kiddo. 

Try the general help thread

Sorry for flaming, but I started this thread 2 weeks ago, after spending a couple of weeks trying to get it working on my own, so I'm fairly frustrated atm. BTW, I've downloaded the 9.10 RC and I'm having the same problem there (sound is quiet and distorted).

Thanks for the reply though

---

### Post by karimruan on 2009-10-29
Try the steps above. Also, make sure you have all the updates. And make sure you have every package listed in my link posted above! I know what it is like to have a problem with ubuntu and not be able to get an answer. Next time, just repost the thread. That's what I do! :)

---

### Post by eddtox on 2009-10-29
> **karimruan said:**
> After re-reading your thread, if none of stuff in the above link works (which I doubt, it should work fine) you should try to make sure that the volume is all the way up in alsamixer. Go to Applications>Accessories>Terminal and type in "alsamixer" without the quotes.

When alsamixer comes up (it is text based) make sure that Master is turned all the way up. You just select it with the arrow keys, and press up to turn the volume up.

Let me know how these two things work for you!

I have tried the alsamixer fix, but it distorts the sound badly if I turn the volume up too high.

I'll look into the thread you suggested though. I'm in 9.10 RC LiveCD atm but that has the same problems.

Thanks

---

### Post by eddtox on 2009-10-29
Back in Jaunty now. I've put the sound for "Master" "PCM" and "Front" up to max in alsamixer. Trying to work through the instructions in the thread. 

I've checked the packages and i have them all, however I've hit a problem. When I try to go to volume control in padevchooser I get an error: "Connection Failed: Connection Refused". 

Also, under "Sound Preferences/Devices" when I select Pulse Audio Sound Server and click "Test" I get: audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused . 

I've checked the "Users Settings" and both root and User are part of "pulse", "pulse-access", and "pulse-rt". 

Any help would be greatly appreciated.

Thanks,
 ed

---

### Post by karimruan on 2009-10-29
Wow! I have to admit, I am stumped. I am not sure if ubuntu has an HCL or not, to check if your sound card is supported. But, if you get SOME sound, that should mean you might be able to get it sounding RIGHT! Let me check around, see what I can do for you. In the meantime, try to google your error messages, and try to post them here so we can see!

---

### Post by eddtox on 2009-10-29
Just to confirm, if I select "HDA Intel ALC880 Analog (ALSA)" in soundprefs/devices it tests fine, as do all other ALSA and OSS options. It's only Pulse Audio Sound Server that kicks up that error.

---

### Post by oliv66 on 2009-10-29
set up PCM at the maximum level in your preferences.

It will work.

Olivier

---

### Post by eddtox on 2009-10-29
> **oliv66 said:**
> set up PCM at the maximum level in your preferences.

It will work.

Olivier

> **eddtox said:**
> I've put the sound for "Master" "PCM" and "Front" up to max in alsamixer.

Thanks for your reply, but I think I've already tried that. As I have mentioned above, my problem is twofold. Firstly, the sound output is very quiet and secondly, the sound quality is poor ( it sounds distorted).

Thanks, 
ed

---

### Post by karimruan on 2009-10-29
Type in 

"lspci" into terminal, without the quotations, and post the output here so we can see what sound card you have.

---

### Post by karimruan on 2009-10-29
Also, try this:
> 
Lets’ play something. Start Rythmbox and play one of the radio stations. Rythmbox should show up in the Playback tab with the volume bar moving with the sound. Click Output Devices, you should see the same thing in your output device. You can adjust the volume or mute the individual stream in Playback or the entire device in Output Devices

If you have more than one device and rythmbox is playing in the wrong one go back to the playback tab, right click on the volume bars and choose move stream to move it to the correct device. You can also go back to the padevchooser and open Configure Local Sound Server/Simultaneous Output and check to box. That will create a new Simultaneous output…. Virtual Stream in Output Devices. You can move any playing stream to the new device and have sound everywhere all at once.


Not sure if you got that far in the how-to I pointed you to. This is what got it working for me.

---

### Post by eddtox on 2009-10-29
Ok, firstly, here is my lspci output 

```
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 0e)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 05)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 05)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 05)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 05)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 05)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d5)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 05)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300]
01:00.1 Display controller: ATI Technologies Inc RV515 [Radeon X1300] (Secondary)
02:02.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 05)
02:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)

```

Now, for Rythmbox. It workks with Pulse audio Sound Server selected in devices, even though the test button doesn't work. I still cant get into the volume control to check if the levels are moving, though.

Thanks,
ed

---

### Post by karimruan on 2009-10-29
I can't find many solutions on google for your sound card. If anyone asks, it is an  Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family).

The last thing I can suggest is to open rythmbox and play a song. Then open pulse audio applet volume control and right click on the volume slider. This will allow you to move the sound to another device. Try switching devices until you get clear sound. Try that.

Other than that, I really don't know what else to do. I did what I could though! Hopefully somebody else can help you! I feel you though, there really isn't much online, just keep searching, try EVERYTHING you find, and see what happens!

---

### Post by eddtox on 2009-10-29
> **karimruan said:**
> I can't find many solutions on google for your sound card. If anyone asks, it is an  Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family).

The last thing I can suggest is to open rythmbox and play a song. Then open pulse audio applet volume control and right click on the volume slider. This will allow you to move the sound to another device. Try switching devices until you get clear sound. Try that.

Other than that, I really don't know what else to do. I did what I could though! Hopefully somebody else can help you! I feel you though, there really isn't much online, just keep searching, try EVERYTHING you find, and see what happens!

I can't open the volume control applet to check because I get the connection failed error. Thanks for your help, though. I will keep trying. Any other ideas would be appreciated. As I said, I get this problem in openSUSE and in 9.10RC as well.

Thanks, 
ed

---

### Post by karimruan on 2009-10-29
Sorry I couldn't be of more help. Good luck though!

---

### Post by eddtox on 2009-10-30
> **karimruan said:**
> Sorry I couldn't be of more help. Good luck though!
No problem, thanks a lot for trying :-)

ed

---

