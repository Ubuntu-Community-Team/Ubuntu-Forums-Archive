---
title: "Soundsystem works fine, but can't listen to radio-livestream in browser"
date: 2010-08-18
forum: Multimedia Software
---

### Post by bd@cb8be8510 on 2010-08-18
I did a clean install of ubuntu10.4 on 2 pc's and got the problem underneath on both of them.

I can play all kinds of cd's, dvd's, ... The soundsystem is working fine. If I want to listen to a radio-station in a browser (be it firefox, be it chromium) I don't hear anything at all. No error-messages are generated. I installed/removed various soundmodules, but all to no avail.

If I paste the url of the strean in VLC or Rythmbox, then I can hear
the music!

At booting-up, I get the following messages in the user.log-file :

Aug 18 20:36:27 Ubuntu-Bernard pulseaudio[1093]: module.c: Failed to load  module "module-rtp-recv" (argument: ""): initialization failed.
Aug 18 20:36:27 Ubuntu-Bernard pulseaudio[1093]: module-gconf.c: pa_module_load() failed
Aug 18 20:36:27 Ubuntu-Bernard pulseaudio[1182]: pid.c: Daemon already running.

I must say that initially I only got the message "pulseaudio[1135]: pid.c: Daemon already running."

By the way. I can listen to some stations, eg. [http://www.bbc.co.uk/radio/](http://www.bbc.co.uk/radio/). In the latter case, an iplayer-console is being opened.

Any clues what exactly goes wrong? Thanks in advance for your help.

---

### Post by Prakram on 2010-08-18
Hi,
I have a similar problem.. loud noise in the background.  Posting this here to avoid a new thread as I think they are related.  

I upgraded to Firefox 3.6.8 yesterday and my online radio stations especially the ones that stream through media player come with a good amount of noise enough to spoil the music.  Not sure whether the upgrade was the culprit.  However, I also use Opera through which, the behaviour is the same, which makes me think twice as to whether this is a problem with PulseAudio or Alsa  or probably the association of the streams with the applications.

I read through the **complete sound problems guide**, yet couldn't resolve this.. Posting this after hours of searching and experiments!

I normally listen to: [http://www.tamilradios.com](http://www.tamilradios.com) which has an mms-stream (can be used as a test)

I've attached the extract from the about:plugins page from firefox.
[ATTACH]166837[/ATTACH]

Any help is much appreciated...:KS

---

### Post by lidex on 2010-08-19
Try using pulse audio preferences (paprefs). 
To run:
Alt + F2 run dialog
```
paprefs
```
If not installed:
```
sudo apt-get install paprefs
```

On the 'Multicast/RTP' tab, enable the first line.
Logout/in

---

### Post by bd@cb8be8510 on 2010-08-19
Hi Lidex,

paprefs was installed and on the 1st tab, the first entry is enabled. The second one is greyed out.

On the second tab, the first 3 ones are enabled, the last 2 ones are greyed out.

On the 3th tab = Multicast/RTP, the first one is enabled, the second one disabled. The last 4 ones are disabled.

On the 4 tab, the first one is enabled.

---

### Post by lidex on 2010-08-19
I would try a reboot and see if it works now and/or if that error message reappears. So if this is still present:
```
pulseaudio[1093]: module.c: Failed to load module "module-rtp-recv" (argument: ""): initialization failed
```
probably need to make a change in one of the pulse config files.

---

### Post by bd@cb8be8510 on 2010-08-20
I have rebooted several times, but the messages persist. It looks indeed like one of the config-files is missing (argument: ""), but how does it come that these have not been properly installed. By means of synaptic I removed some modules from my system and reinstalled them later on, but I never could resolve the audio-problem while listing to the radio-streams.

The problem is that I don't know which package is in error and by consequence don't know for which config-files I have to look after.

---

### Post by lidex on 2010-08-20
Try this. Open this file for editing:
```
gksu /etc/pulse/default.pa
```
Scroll down to line 78. It should look like this:
```
#load-module module-rtp-recv
```
Uncomment it/ remove the pound sign. Reboot.

---

### Post by bd@cb8be8510 on 2010-08-20
Now I get the following messages (It looks as if 2 attempts have occurred):
Aug 20 19:52:48 Ubuntu-Bernard pulseaudio[1078]: module.c: Failed to load  module "module-rtp-recv" (argument: ""): initialization failed.
Aug 20 19:52:48 Ubuntu-Bernard pulseaudio[1078]: main.c: Module load failed.
Aug 20 19:52:48 Ubuntu-Bernard pulseaudio[1078]: main.c: Failed to initialise daemon.
Aug 20 19:52:48 Ubuntu-Bernard pulseaudio[1069]: main.c: Daemon startup failed.
Aug 20 19:52:49 Ubuntu-Bernard pulseaudio[1145]: module.c: Failed to load  module "module-rtp-recv" (argument: ""): initialization failed.
Aug 20 19:52:49 Ubuntu-Bernard pulseaudio[1145]: main.c: Module load failed.
Aug 20 19:52:49 Ubuntu-Bernard pulseaudio[1145]: main.c: Failed to initialise daemon.
Aug 20 19:52:49 Ubuntu-Bernard pulseaudio[1090]: main.c: Daemon startup failed.
Aug 20 20:00:34 Ubuntu-Bernard pulseaudio[1509]: pid.c: Daemon already running.


When I pulseaudio --kill
 and then pulseaudio --start

Only 1 message is forwarded to user.log:
Ubuntu-Bernard pulseaudio[1509]: pid.c: Daemon already running.

---

### Post by bd@cb8be8510 on 2010-08-20
I deleted the file .pulse and .pulse-cookie, but after restart, a new one is created. The messages in user.log persist!

After enabling load-module module-rtp-recv in /etc/pulse/default.pa, the Ubuntu-sound after powering up is not played
any longer. Because we do have now 2 times the message Failed to initialise daemon, it looks like another instance
is scheduling daemon.

---

### Post by lidex on 2010-08-20
May be a bug in pulse. Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by bd@cb8be8510 on 2010-08-21
Lidex, I appreciated your help and advice very much. I filed an ubuntu-bug
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/621888](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/621888).

---

### Post by zipcoi on 2013-01-28
> **lidex said:**
> Try using pulse audio preferences (paprefs). 
To run:
Alt + F2 run dialog
```
paprefs
```If not installed:
```
sudo apt-get install paprefs
```On the 'Multicast/RTP' tab, enable the first line.
Logout/in

this fix my problem.. thx..

---

### Post by nothingspecial on 2013-01-29
Old thread.

Closed.

---

