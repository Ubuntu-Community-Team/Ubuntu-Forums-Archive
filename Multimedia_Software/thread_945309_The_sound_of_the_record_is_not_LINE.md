---
title: "The sound of the record is not LINE"
date: 2008-10-12
forum: Multimedia Software
---

### Post by vecerapl on 2008-10-12
Good day,

mode here since morning, one and the same problem. LINE-entry to me is sound in the PC on the headphones can also hear. But if you want to record the sound and silence.

I have new version ubuntu.

Using the latest ubuntu and my sound card is:

Multimedia audio controller:
- Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
- Subsystem: FOXCONN International, Inc.. Unknown device 0df2

Here is the address:
[http://ubuntuforums.org/showthread.php?p=1742116]("http://ubuntuforums.org/showthread.php?p=1742116")

So I made editing the file:
*/etc/modprobe.d/alsa-base*
.... and finally I put radky:
*options snd-hda-intel model=ref*
.... and perform reboot. Everything was held OK.

PC is loaded, and now zkousim record live audio from entry. Again quiet.

Does not, where the hell can only be an error? I do not know at all your advice.

Just upresnite of over alsamixer LINE record is allowed, the maximum. I looked through the terminal on the alsamixer and here, too everything to the maximum.

I noticed that I ubuntu *alsamixer* to newer version **1.0.15** and _1.0.18 think the Internet is_. Think that a newer version is better? The so-called. sam don 't know how to install a newer version:-D

So the placam later into the air. I do not know what to do at all :-(

Thanks a lot for all directors.

---

### Post by vecerapl on 2008-10-13
Help me pls:confused:

---

### Post by markbuntu on 2008-10-13
To record you need to set "capture" in the mixer.

---

### Post by vecerapl on 2008-10-14
But I have capture in alsamixer :mad:

This is amixer *contents*:

numid=14,iface=MIXER,name='Master Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=13,iface=MIXER,name='Master Playback Volume'
  ; type=INTEGER,access=rw---R--,values=1,min=0,max=64,step=0
  : values=64
  | dBscale-min=-64.00dB,step=1.00dB,mute=0
numid=3,iface=MIXER,name='Headphone Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=off,off
numid=15,iface=MIXER,name='PCM Playback Volume'
  ; type=INTEGER,access=rw---RW-,values=2,min=0,max=255,step=0
  : values=255,255
  | dBscale-min=-51.00dB,step=0.20dB,mute=0
numid=7,iface=MIXER,name='Front Mic Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=off,off
numid=6,iface=MIXER,name='Front Mic Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=31,31
  | dBscale-min=-34.50dB,step=1.50dB,mute=0
numid=2,iface=MIXER,name='Front Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=off,off
numid=1,iface=MIXER,name='Front Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=64,step=0
  : values=64,64
  | dBscale-min=-64.00dB,step=1.00dB,mute=0
numid=9,iface=MIXER,name='Line Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=8,iface=MIXER,name='Line Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=31,31
  | dBscale-min=-34.50dB,step=1.50dB,mute=0
numid=5,iface=MIXER,name='Mic Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=off,off
numid=4,iface=MIXER,name='Mic Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=31,31
  | dBscale-min=-34.50dB,step=1.50dB,mute=0
numid=11,iface=MIXER,name='Capture Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=10,iface=MIXER,name='Capture Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=31,31
  | dBscale-min=-13.50dB,step=1.50dB,mute=0
numid=16,iface=MIXER,name='Digital Capture Volume'
  ; type=INTEGER,access=rw---RW-,values=2,min=0,max=120,step=0
  : values=120,120
  | dBscale-min=-30.00dB,step=0.50dB,mute=0
numid=12,iface=MIXER,name='Input Source'
  ; type=ENUMERATED,access=rw------,values=1,items=3
  ; Item #0 'Mic'
  ; Item #1 'Front Mic'
  ; Item #2 'Line'
  : values=2

---

### Post by vecerapl on 2008-10-14
:confused:

---

### Post by vecerapl on 2008-10-14
Is there someone who will help? Unfortunately, this need, or switching to Windows XP ](*,)

---

### Post by markbuntu on 2008-10-14
Please, no threats. All that does is get you ignored by even more people. Anyway, I have some time so if you could answer for me some questions, maybe we can resolve your difficulties.

First, let me try to understand what is going on. You have a line input and you can hear it in your headphones but cannot record it. Is that correct?

---

### Post by vecerapl on 2008-10-15
Yes, exactly

---

### Post by treesurf on 2008-10-15
I also have an ICH7 family snd-intel-hda and found that updating to one of the newer versions of alsa helped a lot.  Here is an easy way to do it:

[http://ubuntuforums.org/showpost.php?p=5792918&postcount=104](http://ubuntuforums.org/showpost.php?p=5792918&postcount=104)

---

### Post by vecerapl on 2008-10-15
Install alsa-driver -> OK. (with ./configure --with-cards=hda-intel	)

Install alsa-lib -> OK.

Then the alsa-utils, which is definitely alsamixer by a newer version ... but I can not kua. In the end make install, which I will output:


alsamixer.c: 2115: error: âKEY_UPâ undeclared (first use in this function)
alsamixer.c: 2120: error: âKEY_DOWNâ undeclared (first use in this function)
alsamixer.c: 2125: error: âKEY_PPAGEâ undeclared (first use in this function)
alsamixer.c: 2130: error: âKEY_NPAGEâ undeclared (first use in this function)
alsamixer.c: 2134: error: âKEY_BEGâ undeclared (first use in this function)
alsamixer.c: 2135: error: âKEY_HOMEâ undeclared (first use in this function)
alsamixer.c: 2138: error: âKEY_LLâ undeclared (first use in this function)
alsamixer.c: 2139: error: âKEY_ENDâ undeclared (first use in this function)
alsamixer.c: 2246: error: âKEY_ICâ undeclared (first use in this function)
alsamixer.c: 2251: error: âKEY_DCâ undeclared (first use in this function)
make [1]: *** [alsamixer.o] Error 1
make [1]: Leaving directory `/ home/radovany/alsa-utils-1.0.17/alsamixer '
make: *** [install-recursive] Error 1


What to do?


I have alsa-driver - 1.0.17, but still not LINE input record. Where the hell could be wrong? :mad: :confused:

---

### Post by markbuntu on 2008-10-15
> **vecerapl said:**
> Yes, exactly

Well, if you can hear the line in in your headphones that means things are working properly so it is just a matter of configuration. Open the PulseAudio Volume Control (pavucontrol if you need to get it) and go to the Input Devices page and change the default device by right clicking on 

"Monitor Source of ALSA PCM....(your sound card) via DMA"

 Then you should be able to record whatever you hear in your speakers with soundrecorder.

---

### Post by vecerapl on 2008-10-15
I install:

sudo apt-get install libasound2-plugins "pulseaudio-*" paman padevchooser paprefs pavucontrol pavumeter libflashsupport


Install all is OK.

I ran pavucontrol, but playback is empty "no Streams Available." Is this okay?

---

### Post by markbuntu on 2008-10-15
No, this is not OK. You should look through my guide here. You can start at the Packages Section and read the next sections to the line:

 *************************

This will get your sound configured properly. Don't forget to reboot after you get all the packages ao they will work.

Sorry, forgot the link:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by vecerapl on 2008-10-16
I have that confused. Can not English, so that thinking what to use and not be in the unfamiliar. Information there is enough praise. But I can not find here the problem of how to resolve LINE recording. Thanks a lot for clarification. :(

---

### Post by markbuntu on 2008-10-16
Ok, we will try. First reboot if you have not. Then go to System/Preferences/Sound in the menu and change the settings to ALSA or PulseAudio. Next, start pavucontrol and Open the Output Devices page. Is there anything in there?

If there is something in there, change to the Playback page. Start Rythmbox and play something, anything. If Rythmbox starts OK then you should see it in the Playback box and hear it in your speakers.

Now we know Pulseaudio is working properly. Now, go to the Input Devices page of pavucontrol and change the default device to "Monitor....something" which is the same as the Output Device but says Monitor.

Now start soundrecorder and make record. What is the result?

---

### Post by vecerapl on 2008-10-17
Recording not. I just tried. Pulse audio (server) I set, the sound is played but not recorded sound.

Sound, which is loaded is more noise and hear here is a very very quiet sound, which I have load.

---

### Post by mocha on 2008-10-17
HDA Intel has a lot of bugs in the Alsa that comes with Hardy.  Either upgrade Alsa as explained in the link already provided, or you have to play with the source for capturing.  For example on my Intel HDA I have to choose "front mic" to record the stereo mix sounds generated from web pages, crazy...  The Line In recording works, but sometimes you have to select and de-select the Line-In as the source within the Alsa mixer until it starts working.  I usually run Audacity with the recording meter showing as well as the pulseaudio recording meter showing.  Then I play with the mixer settings until I see the levels changing.

---

### Post by vecerapl on 2008-10-17
I will try everything, but it is not. Sound is still quiet, there is nothing to hear.

And I do not know what to do. Unfortunately, if it not be, I am forced to move to Windows XP .... this is my last resort :( I am very disappointed.

---

### Post by mocha on 2008-10-17
Did you try to play with all of the mixer settings while playing your audio though the Line-In and watching the meter in Audacity or Pulseaudio?  You need to make sure that the capture sources are selected, not-muted, and the source for the capture is setup properly.  Perhaps you have some configuration problems.  Did you try to upgrade Alsa?  Maybe something is messed up now.

---

