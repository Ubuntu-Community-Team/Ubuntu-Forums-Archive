---
title: "Sound error: &quot;Could not open resource for writing&quot;"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by PurplePenguin on 2007-04-21
After a clean install of Ubuntu 7.04, I don't have any sound.  Actually, the strange thing is that I'm sure I heard it when I booted, but when I'm actually logged in - nothing. 

Trying to test my sound in the System->Prefs->Sound dialog gives me this error for each "Test" button:
> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

I've seen other people with this error fix it by using kmix under kubuntu.  I've tried fooling with alsamixer(and -gui), and even installed kmix into my kde-less system, but no luck.

Anybody have any ideas?
Thanks!

EDIT: An update.  If I go into the Sound preferences, I can get sound by switching to OSS.  ALSA gives me the error.  I do have two soundcards - one onboard that I have connected to my speakers, the other a SB Live that I have my headphones / mic attached to.

---

### Post by Skrewdriver on 2007-05-05
I'm having the same problem, haven't worked it out yet but one thing I did discover is that the problem only occurs for one of the users on my system (me!)
Nobody else has this problem, and if I create a new user it works fine.
Create a new user and see if the sound works for them or not.

---

### Post by chipwebber on 2007-06-07
try:
 sudo chmod a+rwx /dev/dsp

This will all users to write to sound card.  I experienced the same problem using FC6 and Banshee.  In my case I could play music as root, but not as a normal user.

---

### Post by daydreamer2025 on 2007-07-07
I am getting the same problem with Fedora Core 6. All my movie players (xine, mplayer, vlc, ...) used to work properly. Now after doing an upgrade, all the audio has stopped working for everything except the system beep.

Error with mplayer

 open /dev/snd/pcmC0D0p failed: No such file or directory

Error with vlc
[00000372] jack audio output error: failed to connect to JACK server
[00000372] oss audio output error: cannot open audio device (/dev/dsp)
[00000372] esd audio output error: cannot open esound socket (format 0x00001021 at 44100 Hz)
[00000372] arts audio output error: arts_init failed (can't connect to aRts soundserver)

The volume control button toolbar completely loses all controls related to sound mixing....

System->Sound->Autodetect gives:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

Changing the permission codes for /dev/dsp doesn't work.

But /dev/snd/pcmC0D0p doesn't exist either..

rpm -qa | grep alsa provides:

alsa-driver-devel-1.0.14-61.fc6
alsa-lib-1.0.14-0.1.rc1.fc6
alsa-tools-1.0.12-4.fc6
alsa-driver-1.0.14-61.fc6
alsa-lib-devel-1.0.14-0.1.rc1.fc6
alsa-utils-1.0.14-0.2.rc1.fc6
alsa-kmdl-2.6.20-1.2952.fc6-1.0.14-61.fc6

---

### Post by eamann on 2007-12-06
Hello!

Try the very simple solution proposed by LinuxTechie at

[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

It worked for me.

Best of luck!

---

### Post by Lido on 2008-01-27
I have a recurring problem with sound under Gnome in Gutsy 7.10 where sometimes my sound doesn't work. At the login prompt I don't hear the drums and then there's no sound again once I'm logged in. The problem seems to be that sometimes when the machine starts up the alsamixer is set to one of my capture card sound devices rather than the onboard audio. Usually messing with the settings in prefs->sound and rebooting (sometimes more than once) ends up working. I'd like to set things so this never happens, but I'm not sure how. Could I remove the sound out devices on the capture cards from whatever list the system looks at while starting so its only option is the onboard audio?

---

