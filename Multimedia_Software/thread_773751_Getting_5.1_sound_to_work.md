---
title: "Getting 5.1 sound to work"
date: 2008-04-29
forum: Multimedia Software
---

### Post by hellmet on 2008-04-29
I've a nVidia MCP61 5.1 integrated sound card with a Logitech 5.1 speaker system.
I'm not able to get surround sound on either Movie Player or Amarok. I even tested using 5.1 sample files from the internet. 
Works wonderfully on Windows, so you know there is no problem with my sound card or speaker system.
Any help on this?
Thanks in advance!

---

### Post by ThinkDave on 2008-04-29
Probably not gonna be helpful but have run "alsamixer" and checked that all the surround channels aren't muted or volume turned down. It did that to me when I first installed gutsy took me a while to figure out what was happening.

---

### Post by irshadcharm on 2008-04-29
please help people waiting for a proper fix for 5.1 surround in hardy....almost exhausted searching for 2 days regarding this issue...none is working...

---

### Post by DkkD on 2008-04-29
Have you edited your */etc/pulse/daemon.conf* file?

If you haven't, enter this in your terminal:
```
sudo nano /etc/pulse/daemon.conf
```

Find and uncomment line:
*default-sample-channels* 
and change value from 2 to the number of speakers you have.

---

### Post by egroeg85 on 2008-04-29
This solution sort of worked for me.  I got 6 channels, all working.  I used it that way for a few days.  Then I decided to try Pulse Audio's network streaming so I could play music over my 5.1 desktop speakers from my laptop.  I set it up and it works for something like one song, then I get the "Connection refused" error on my desktop.  Sound still works locally but I can't use the Pulse utilities and network streaming stops.  I can't get it to reconnect so I have to log out and log back in again, then it repeats.  

If I comment out the "default-sample-channels = 6" line in /etc/pulse/daemon.conf then it works just fine, only I am back to two channels.  If I run grep pulse /var/log/* I get this error message:

/var/log/user.log:Apr 29 16:01:56 george pulseaudio[8997]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.

Here I was hoping pulse audio would rid me of my alsa woes, but alas, it seems I will never be rid of this plague.

Does anyone have any idea of how to fix this?  I tried making an .asoundrc file but it made no difference.  Even with pulse set to two channels,  "speaker-test -c 6" gets me sound out of all 6.  Even if alsa thinks I only have 2 channels, it's playing out of all 6 of them.

---

### Post by chris_x1 on 2008-04-29
hi guys, this may help but read the WHOLE post first!
if you have a 5.1 system, try this code 
```
[COLOR="Red"] ###  in your /etc/asound.conf file (create one)  
pcm.!default{
type plug
slave {
pcm surround51
channels 6
}
ttable{
0.0 1    # front left
1.1 1    # front right
0.2 1    # rear left
1.3 1     #rear right
0.4 0.5  # centre 
1.4 0.5  # centre 
0.5 0.5  # sub
1.5 0.5  # sub    		
}
   }[/COLOR]
```
then make sure you have all the analogue or digital channels unmuted 
i could not get 5.1 working properly in "hardy" yet. i got as far as 
```
[COLOR="Red"]uncommenting this line in /etc/pulse/default.pa 
load-module module-alsa-sink[/COLOR]
```
which worked with the asound.conf file but the sound went all erratic.
i just uninstalled everything pulse related in synaptic (search "pulse") and now sound is only handled by alsa, like in "gutsy" where i learned to do all this successfully
look here 
[http://www.pulseaudio.org/ticket/25](http://www.pulseaudio.org/ticket/25)
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/109439](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/109439)
maybe there is a way to use pulse properly but i will sort that one later i guess
i would recommend non-experts who are happy with their current ubuntu, not to automatically upgrade to a new release until you have fully tested (from another partition) i have it on a separate HD still (working fine) and haven't rushed into replacing gutsy yet. For the new features that are there its not worth inconveniencing yourself with any issues for hours on end, just use it as your own personal "testing" system until you are sure.

---

### Post by egroeg85 on 2008-04-29
Well, none of this seems to help here.  I just don't understand why I can set pulse to 6 channels and it works fine as long as I have networking turned off.  But then when I turn on networking it disconnects after a few seconds.  Why should the networking make the difference?  The alsa error message doesn't seem to be the thing that kills it, but when I comment out that line in daemon.conf it both works and I don't get the error, so I assumed correlation.

---

### Post by hellmet on 2008-04-29
Btw, what the heck is pulseaudio ?
I didn't see it in the previous releases.. and now everybody is talking about it..

---

### Post by egroeg85 on 2008-04-29
It's the new audio thing (technical term) that comes installed in Hardy.  It has some cool features, like controlling the volume of individual programs.  For the most part it makes no difference to the average user, unless you really want to use the extra features.  I'm sure there are some more important differences but I'm not that smart. :)  One thing it can do that I'm trying to set up is play from one computer (my laptop) through the speakers of another (my desktop).  It's nice because my desktop has 5.1 surround speakers.  Now if only I could get all the channels working right...

---

### Post by hellmet on 2008-04-30
Hehe.. thanks for clarifying.
So, pulse allows you to play thru speakers of another system, but doesn't play all 5 speakers on the current system. Thats pathetic!!

---

### Post by irshadcharm on 2008-04-30
> **hellmet said:**
> Hehe.. thanks for clarifying.
So, pulse allows you to play thru speakers of another system, but doesn't play all 5 speakers on the current system. Thats pathetic!!

> **DkkD said:**
> Have you edited your */etc/pulse/daemon.conf* file?

If you haven't, enter this in your terminal:
```
sudo nano /etc/pulse/daemon.conf
```

Find and uncomment line:
*default-sample-channels* 
and change value from 2 to the number of speakers you have.

I've changed the default sample channels from 2 to 6 but there is no o/p in the rear,center and sub...wat else can be done? thx for the reply...

---

### Post by egroeg85 on 2008-05-01
You could try looking at the switches under Volume Control.  I think one friend of mine got his to work by checking the "Mix" switch.  I still don't really know what exactly got mine working.  I tried just about every switch and volume slider in there before some seemingly random combination fixed it.  

I've found sound to be the most frustrating part of Ubuntu.  It seems strange to me that we can have desktop effects via compiz that are better than vista's, but we can't get sound to work easily, something Microsoft has had since Windows 3.1.

---

### Post by irshadcharm on 2008-05-01
Please help guys ...waiting for a response for the past two days...really frustrated with this sound issue...i made all the changes in .asoundrc file as well as in the daemon.conf file and changed everything to pulsse as well as alsa but of no use....any detailed tutorials wud be appreciated from the core of my heart...waiting for a prompt reply...

Motherboard: Intel d945gnt
Soundcard: Sigmatel Hidefinition audio
Series : STAC9221 series...

---

### Post by hellmet on 2008-05-01
I gave up!! :D

---

### Post by irshadcharm on 2008-05-01
If any one could help in this issue which ive posted early....

---

