---
title: "How to change the from Mic Input to Line Input?"
date: 2010-05-01
forum: Multimedia Software
---

### Post by makaki on 2010-05-01
Hi guys, I installed Lucid. I used to have Ubuntu 9.10 and to connect my iPod to my laptop's speakers. There was an option in 9.10 in the Sound Options to change the Mic Input into a Line Input. But now unfortunately I can't find it in Lucid :(

I have only 2 audio ports in the laptop: Headphone port, Mic port.

Please help.

---

### Post by sixthwheel on 2010-05-01
System/Preferences/Sound/Input.

---

### Post by makaki on 2010-05-01
Please how did you get that menu! right-clicking on Input tab doesn't show anything :(

---

### Post by makaki on 2010-05-01
Oh I see. I don't have a Connector. How to display that [connector]?

---

### Post by makaki on 2010-05-01
This is a screenshot.

---

### Post by sixthwheel on 2010-05-01
Wonder why you don't have a "connector" drop box?

---

### Post by makaki on 2010-05-01
does anybody else have an idea why I don't have this in Lucid?

---

### Post by sixthwheel on 2010-05-01
You may want to post this in the general help area. There's a lot more activity going on over there.
Sorry I couldn't be of more help

---

### Post by makaki on 2010-05-01
I don't know how to do that :(

---

### Post by makaki on 2010-05-15
Bang!

---

### Post by lidex on 2010-05-16
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. *_Also helpful is the make/model of your PC/Laptop._*

---

### Post by LugoffSCUser on 2010-05-16
I got Mine to work  here are the details

System/Preference/Multimedia Systems Selector

change the Input and Output to ALSA

Sound Preferences: if you have two cards shown one for HDMI disable this you wont need it
Settings for Selected device:  Analog Stereo Duplex

Input:  Microphone

Output: Analog speakers

Took a lot of trail and error to get to this point   :P:P:P

---

### Post by Graemej on 2010-05-16
Hi Lidex,

I have been following this post as I have exactly the same problem but did have a separate mic and line input when I was using 10.04 RC. It was this which made me decide to forgo windows and move to Linux unly to come unstuck on the LTS release.

Here is my results from the commands you asked for. It may add to your pool of information.

gvj@gvj-laptop:~$ uname -a
Linux gvj-laptop 2.6.31-10-rt #153-Ubuntu SMP PREEMPT RT Tue Jan 12 10:42:21 UTC 2010 i686 GNU/Linux

gvj@gvj-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

gvj@gvj-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.

gvj@gvj-laptop:~$ head -n 1 /proc/asound/card*/codec*
==> /proc/asound/card0/codec#0 <==
Codec: SigmaTel STAC9200

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2bfa
gvj@gvj-laptop:~$

---

### Post by lidex on 2010-05-17
*Graemej*,
That's a fairly old version of alsa. What are you using now, hardy?

Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by Graemej on 2010-05-17
I am using:

Ubuntu
release 10.04 (lucid)
Kernel Linux 2.6.31-10-rt
GNOME 2.30.0

I would have thought Lucid would have shipped with a very recent version. I am a very new and inexperienced Linux user (just so you know what you are dealing with) but with a bit of guidance I guess I could upgrade something not on the distro.

Thanks for responding to me.

---

### Post by Graemej on 2010-05-17
[Code:]
--------
sudo bash utils_alsa-info.sh
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
ALSA Information Script v 0.4.59
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'utils_alsa-info.sh --help' for command line options.

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
Automatically upload ALSA information to www.alsa-project.org? [y/N] : y
Uploading information to www.alsa-project.org ...  Done!

Your ALSA information is located at http://www.alsa-project.org/db/?f=8073cdd451595c3053a780a5bec42694e31c7bb2

Please inform the person helping you.

gvj@gvj-laptop:~/Downloads$ 
[/Code]

---

### Post by lidex on 2010-05-17
*Graemej*,
Ah, your alsa install is somewhat borked. Try upgrading it via the alsa-upgrade link in my sig. But first do this. Update your kernel:
```
sudo apt-get update
sudo apt-get upgrade
```
Now reboot so we can work with the latest kernel. Oh yeah, and remove that custom entry from alsa-base.conf.

---

### Post by Graemej on 2010-05-17
Thank you Lidex,

gvj@gvj-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
gvj@gvj-laptop:~$ 


I think I must have the latest kernel but am about to re-boot anyway.

btw How do I insert code blocks into my message as you do please?

---

### Post by lidex on 2010-05-17
For code blocks, select the text and press the '#' in the editor toolbar or you can copy text to the clipboard, press the '#' and paste. In the second instance the cursor is placed between the code tags by default.

---

### Post by Graemej on 2010-05-17
Thanks, The Alsa upgrade script navigates me to another thread. I see there is an attached file there and I assume I download and execute it as a script. Please confirm.

Also the first alsa-info.sh script was an html link so I copied and pasted with gedit then saved. I wonder if it was meant to be a link to a file to be downloaded that has gone wrong?

---

### Post by Graemej on 2010-05-17
Hi Lidex,

I have run the Alsa upgrade and all seemed to go well. Here are the original commands you first asked me to run. Again many thanks.

```

gvj@gvj-laptop:~$ uname -a
Linux gvj-laptop 2.6.31-10-rt #153-Ubuntu SMP PREEMPT RT Tue Jan 12 10:42:21 UTC 2010 i686 GNU/Linux

gvj@gvj-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

gvj@gvj-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on May 17 2010 for kernel 2.6.31-10-rt (SMP).

gvj@gvj-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: SigmaTel STAC9200

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2bfa
gvj@gvj-laptop:~$ 

```

Unfortunately I don't have the Line and Mic options still, so that did not fix the problem although I suspect it will fix another problem where my machine would lock up sometimes when using sound like in rythmbox or skype. I look forward to the end of that problem.

Please let me know if you want me to run the Alsa Info Script.

---

### Post by lidex on 2010-05-17
* Graemej*,
What is the make/model of the PC?

---

### Post by makaki on 2010-05-17
> **LugoffSCUser said:**
> I got Mine to work  here are the details

System/Preference/Multimedia Systems Selector

change the Input and Output to ALSA

Sound Preferences: if you have two cards shown one for HDMI disable this you wont need it
Settings for Selected device:  Analog Stereo Duplex

Input:  Microphone

Output: Analog speakers

Took a lot of trail and error to get to this point   :P:P:P

Dude there's no "Multimedia Systems Selector" in System/Preference/!!

---

### Post by Graemej on 2010-05-17
Hi Lidex,

The computer is a DELL INSPIRON E1505

---

### Post by Graemej on 2010-05-17
Hi Makaki,

I followed the instructions from LugoffSCUser but it did not work. Still the same.

I needed to go to System-> Preferences -> Main Menu to enable access to "Multimedia Systems Selector"

The pictures are of how the system has done and should look and 2nd pic is how it looks now.

The first pic is not my screenshot but is similar to what I had where I could choose between Line and mic. At present the input is a mic input I suspect as there is 3 volts present on each input which would be to bias an electret mic. I expect a Line input to have no bias voltage. Everything works on the card except being able to change the input socket between line and mic.

---

### Post by LugoffSCUser on 2010-05-17
john@john-laptop:~$ uname -a
Linux john-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
john@john-laptop:~$ aplay -1
aplay: invalid option -- '1'
Try `aplay --help' for more information.
john@john-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
john@john-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
john@john-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD71B7X

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040

==> /proc/asound/card1/codec#0 <==
Codec: ATI RS690/780 HDMI
john@john-laptop:~$

---

### Post by lidex on 2010-05-17
*Graemej*,
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=dell-m25 
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

### Post by Graemej on 2010-05-17
Hi Lidex,

I already had that line in my alsa-base.conf which I had found in a post from Temujin, although he recommended m4. When I checked the dell model list I changed it to m25 but no different result.

I guess you looked at my post to Makaki.

I have posted a screenshot of my alsamixer and I really appreciate the time you are spending with me.

Cheers, Graeme

---

### Post by lidex on 2010-05-17
Try **Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
Use 'Edit -> Sound Card Properties' menu to enable elements.
Soundcard tab to select / adjust levels.

If not installed:
```
sudo apt-get install gnome-alsamixer
```

Other options to try:
```
dell-m81
auto
dell
dell-eq
dell-bios
ref
```

How many analog audio jacks do you have on this PC? Digital?

---

### Post by Graemej on 2010-05-17
Hi Lidex,

Fantastic news!!the last line worked i.e.

```

options snd-hda-intel model=ref

```

I will test the inputs later tonight and make sure they switch correctly but have to go out now. More news tomorrow.

Yet again thanks so much for your trouble.

Graeme

Here is a screen shot of my sound preferences.

---

### Post by Graemej on 2010-05-18
Hi Lidex,

Well the news is not good after further testing. I did have my line and mic controls but they did not work. Also software (Sound Recorder) which I use to test the card could not access it. I am back with m25 which is no different from not having the line in the .conf file at all.

I should give some further historical information. I previously posted that I had it working in 10.04 RC. It was the same as now initially but in the process of installing my EDIROL FA-66 card I magically got the correct controls. Problem is I don't know what I did to get it. I had definitely installed Jack. I had installed either freebob or ffado but am not sure which and possibly (probably) Ubuntu Studio. I can't be sure as I was only experimenting to see if I could move to Linux using 10.04 when the LTS version arrived and did not take any notes as I intended a scratch install if I moved. Well I have moved and burnt my bridges behind me but have got myself into trouble.

Back to the SigmaTel card. I have been testing the input by running Sound Recorder and recording the hum from placing a screwdriver on each input and then playing it back. I have noticed that one channel has significantly more gain than the other even though alsamixer shows matched gain. I also remember that in RC tests alsamixer showed left and right channels for line and mic on their own slider with facilities to link or unlink them. Currently there is a single slider on capture (no line or mic) with no link/unlink facilities. I also suspect that the channels are not in phase but have not found any Linux analyser to check this and suspect my old windows one won't run under wine or virtualbox due to the direct card accesses.

Sorry about the long post but best you have all the information.

Thanks again Graeme

---

### Post by lidex on 2010-05-18
If your mic shows a dual slider (stereo), you need to unlink them and bring the level of one down to zero.

---

### Post by Graemej on 2010-05-19
Hi Lidex,

Yes sorry have now read the alsamixer wiki and see that I can use qwe and zxc to adjust channel gain individually. Still no facilities to switch the sound input input jack from line to mic and vice versa. My mysterious crashes when playing sound seems to have stopped since you walked me through the alsa upgrade. That on its own has put me light years ahead ... now if only I could get the input jack switching going. I suspect I may be stuck on this unless something is done about a SigmaTel driver but thanks for your help and patience.

Cheers, Graeme

---

### Post by oNNogitaar on 2013-02-21
hope you found it the last 2y
type in a terminal "gnome-sound-recorder' select 'open volume control' from menu 'file'

---

### Post by wildmanne39 on 2013-02-21
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

