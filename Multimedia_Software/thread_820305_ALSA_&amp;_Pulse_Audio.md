---
title: "ALSA &amp; Pulse Audio"
date: 2008-06-06
forum: Multimedia Software
---

### Post by Stunts on 2008-06-06
Hi all!
After much tinkering with my Audio setup I have archived the following:

 - I can have multiple applications playing sound trough PulseAudio (eg. Rhytmbox and Battle of Wesnoth);

 - I can have multiple applications playing sound trough ALSA (eg. Neverwinter Nights, which I just can't make work trough PulseAudio and sound test under System -> Preferences -> Sound);

 - My sound card is an integrated laptop card, so it has no hardware mixing capabilities, however I have dmixer enabled, allowing me to use software mixing;

I have followed several HowTo's to accomplish this, the most important one being [http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739) .

What I can't do:

 - Use ALSA and Pulse audio simultaneously. I would like to be able to do this in order to use Neverwinter Nights with Teamspeak (which uses OSS - works fine with pulse using the "padsp" prefix, but doesn't work at all using "aoss" prefix;

I know that this is possible to do since the author of the great HowTo mentioned above can do this as he shows in here: 
[http://www.pulseaudio.org/ticket/285](http://www.pulseaudio.org/ticket/285)

Anyone got any ideas on how to do this? I can post the contents of my sound configuration files if required...

Thanks in advance for any help / tips you may be able to provide!

---

### Post by Stunts on 2008-06-07
Bump...

---

### Post by Stunts on 2008-06-09
Bump again...!

---

### Post by Stunts on 2008-06-11
Last bump try...
Nobody's got a clue?

---

### Post by markbuntu on 2008-06-11
Do you have the libasound2-plugins?

This will allow redirection of pulseaudio OSS and jack through alsa.
asoundconf-gtk will let you choose your default alsa sound card. The first time I used it it had pulseaudio as the default so many things did not work together.

For me it was easier to put everything through alsa and let alsa control the sound card. The automatic selection in System/Preferences/Sound did not work for me as it would switch back and forth from pulseaudio to alsa to oss depending on what app started last so I just changed everything to go through alsa since it has plugins for the others.

---

### Post by Stunts on 2008-06-11
Thank you very much!
I was getting sorta desperate to find an answer.
I do have the plugins you mentioned.
There is an issue with asoundconf-gtk.
When i try to start it it in a terminal I get the folowing:
```
 
You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is! 
```

Both the mentioned files exist, tough ~/.asoundrc.asoundconf is empty.
This does sound like a solution. Afterall, I could do all I mentioned in my first post in 7.10 before pulse audio.
Don't get me wrong, I think pulse audio can be great, but it still needs a little polishing on the edges when it comes to ALSA compatibility - which still is the mainstream (I think - and based soley on my limited experience) in linux sound.

---

### Post by Stunts on 2008-06-11
Double posted! Sorry!

---

### Post by markbuntu on 2008-06-11
asoundconf-gtk lives in System/Preferences as Default Sound Card. A little tiny widow will pop up.

Try that.

---

### Post by JohnLM_the_Ghost on 2008-06-11
Sorry for offtopic, but...
what are (is there any) advantages of PulseAudio?

I reverted to ALSA cause I had strange clicks and poor sound while using Pulse.

---

### Post by Stunts on 2008-06-11
> **markbuntu said:**
> asoundconf-gtk lives in System/Preferences as Default Sound Card. A little tiny widow will pop up.

Try that.

Tried it. I get a new bar in my panel saying "Starting Default Sound card", but it disappears after a few seconds and I get nothing else...

> Sorry for offtopic, but...
what are (is there any) advantages of PulseAudio?

I reverted to ALSA cause I had strange clicks and poor sound while using Pulse.

Well, pulse audio will allow you to control the volume of multiple apps independently, will allow you to stream your audio thru a network and of course listen to streamed audio.

From what I understand it is not meant to be a replacement for ASLA or OSS, but rather a second layer of audio control...

I think a system can live happily without it as much as it can live without... say... desktop effects for the sake of the metaphor. You can do all the same things with it save for a few thing which may not be useful frequently...

Can you purge pulseaudio out of your system? Because it seems like it's just not working 100% for me...

---

### Post by JohnLM_the_Ghost on 2008-06-12
Thanks for clearing that up!

Well I never tried to remove pulseaudio!
I just set everything to ALSA in Sound Device settings.
I'm not even 100% sure it doesn't use Pulse anymore.

---

### Post by markbuntu on 2008-06-12
I had a zillion problems with pulseaudio and finally just turned it off from starting at boot with Boot Up Manager and reenabled the alsa utils in System/Administration/Services.

I had problems like Sound and Multimedia System Selector freezing up every time I tried to change anything or even run test. Also, the alsa default sound card chooser would not even start up. Toetm and vlc had no sound. Rythmbox and firefox would do strange things and crash but could only be killed in a termminal or with system monitor.

I have had no problems since. Flash 10 fixes the problem of flash taking over your sound btw.

Boot Up Manager is handy. It is called bum in the repositories. Be very careful using it.

---

### Post by Stunts on 2008-06-17
I'm going to try and revert everything back to ALSA.
I'll let you guys know how it turned out!
Thanks in advance!

---

### Post by markbuntu on 2008-06-17
This is how I got all the way bask to alsa:

1. Stop pulseaudio from loading at boot with Boot Up Manager (bum). 

2. Put etc/asoundrc in the trash.      !CRITICAL!

3. Edit etc/libao.conf: 

default_driver=alsa       !CRITICAL!

4. Make sure alsa-utils runs at boot (System/Admin../Services)

5. Check with Synaptic that these are all installed:

aconnectgui  (ALSA MIDI connection utility)
alsa-oss  (alsa wrapper for OSS apps)
alsaplayer-alsa  (PCM player for alsa)
alsa-utils  (command line utilities)
asoundconf-gtk  (choose default alsa sound card)
gnome-alsamixer (GUI alsa mixer for Gnome)
gstreamer0.10-alsa (gstreamer plugin)
xmms2-plugin-alsa (xmms2 plugin)
libasound2-plugins (jack, OSS, pulseaudio)
libesd-alsa0 Enlightened Sound Demon (allows  multiple audio streams on one device)

6. System/Preferences/Default Sound Card, choose the sound card. 

7. Sys../Pref.../Mutimedia Systems Selector/Audio, set plugin  to alsa and Device to Default for both input and output.

8. Sys../Pref.../Sound, set all to ALSA. Default mixer tracks to "your sound card" (i.e. ATI IXP) (Alsa )mixer).

9. Reboot. If you are having trouble changing settings in Multimedia Systems Selector or Sound, reboot and then make the changes.

10. alsamixer, alsamixergui, gnome-alsamixer,  configure. Turn stuff on and put up the sliders. check mix, capture, cd, mic, etc, unmute, mute, blah blah blah... If you have a usb mic or headphones turn them on and test them in the gnome-alsa mixer USB section.

11. Test with Rythmbox, vlc, totem, xine, gstreamer, etc. configure all preferences to alsa if available/possible.

12. Test Sound Recorder. set capture/mix level, enable record, turn on mic, unmute, mute etc, etc... fool with mixer until it works right

13.  jackd, set driver to alsa in jack control.

---

### Post by Yellow Pasque on 2008-06-17
Try OSS4 (link in sig).

---

### Post by markbuntu on 2008-06-17
I just spent almost 2 months getting my sound in order and everything works now all the time and now you want me to try something else?!?

Maybe in a few months.

---

### Post by Yellow Pasque on 2008-06-17
Sorry, I didn't see that you had everything working perfectly. In that case, carry on. :)

---

