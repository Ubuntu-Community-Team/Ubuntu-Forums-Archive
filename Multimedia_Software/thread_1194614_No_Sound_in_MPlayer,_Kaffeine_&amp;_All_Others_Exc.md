---
title: "No Sound in MPlayer, Kaffeine &amp; All Others Except SMPlayer. How can I Fix??"
date: 2009-06-22
forum: Multimedia Software
---

### Post by OzzyFrank on 2009-06-22
OK, seems this started happening after a bunch of updates (I assume), but I can no longer get sound in the majority of media players, and these are a mix of ones based on **both GStreamer and Xine**. In many of these, you can't even choose the audio device, but I never needed to in the past as it all worked fine. The only player working fine in this regard is my favourite, **[COLOR="Indigo"]SMPlayer[/COLOR]**. It lists the audio device as [COLOR="Purple"]**alsa (1.0 - Audigy 2 ZS [2001])**[/COLOR] (I have a Creative Audigy 2 ZS soundcard).

In programs like **Kaffeine**, I can choose other audio devices (like a standard [COLOR="Purple"]**alsa**[/COLOR]) but to no avail. In others like **MPlayer**, there is a list of devices, but no apparent way to change between them ([COLOR="#800080"]**oss**[/COLOR] is at the top of the list so assume that is the one being used). In **KMPlayer**, I can choose [COLOR="#800080"]**alsa**[/COLOR] but then the clip refuses to play whatsoever (there is another [COLOR="#800080"]**alsa**[/COLOR] in the list and using that plays the clip with no sound). In **Movie Player**, all I can do is choose to have it stereo, so is of no use.

Please note that **this isn't a case where the master volume is muted or the PCM is turned all the way down** (I have had programs do both and have posted on this forum about them). Also, I have indeed played in **System > Preferences > Sound** since this began, and any fiddling there just means that even **SMPlayer** has no sound, so the answer does not seem to lie there either (at least not with anything I have tried). All I can say is this started happening all at once to all but **SMPlayer** without me fiddling with anything that could have upset things. Also, the audio device that works in this program (as listed above) is not a choice in the others (just plain old **[COLOR="#800080"]alsa[/COLOR]**) so that probably makes a difference too.

I would appreciate any input on this (but please no "This isn't happening to me" posts, hehe). Cheers.

PS: All my audio-only programs like **Rhythmbox** seem to be working fine, in case you were going to ask.

---

### Post by fooman on 2009-06-22
when i have problems like these,  one of the first things i try is deleting the offending apps config files in my /home directory.

if you look there,  you should find a .xine and a .gstreamer folder...you might try deleting those (new ones will be created when you reopen the associated apps) and see if it makes any difference.

---

### Post by OzzyFrank on 2009-06-23
Hey fooman, that's a good trick to know for the future... but in this case did not do a thing, unfortunately. I renamed those folders and watched new ones being created when I tried to open vids in the offending apps. I kept deleting those after each app just in case, but so far only **SMPlayer** is working right. I find it really weird that the app it is based on, MPlayer, does not give me audio but SMPlayer does, hehe. I tried a few more, being **VLC**, **Dragon Player**,  and even **Miro**, but all tell me the volume is full yet give me no sound. I'm glad it isn't some major sound issue where not even SMPlayer gives me any volume, but it makes this even stranger that all the apps don't give me sound except SMPlayer (and, like I said, all audio apps are working fine). Hopefully someone reading this knows what is going on and can help. Cheers

---

### Post by MindGuerrillas on 2009-06-24
I've having exactly the same issues with sound on my system. It only started to happen in the last day or so before that everything was fine.  I've made no changes to my system in that time so it looks as though some recent update has ruined it.

#########
EDIT

Just looked in the logs and found the following error

>> module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy

After a quick look on google it appears that this is caused by JAVA.  I did have a JAVA program running at the time and shutting it down restored my sound.

Does anyone know why running a Java based program would cause this issue and if so how to go about fixing it?

I use the Java program as part of my daily work and so need to have it running at all times. It would be nice to also be able to listen to some tunes when I work from time to time though :(

---

### Post by OzzyFrank on 2009-10-17
Still no sound in anything but SMPlayer. This is a drag when trying to listen to sound samples on web pages when using either Opera or Firefox, as these seem to use an MPlayer plugin or something. I can't believe this is still not fixed in an update or something, so can't assume it will be soon. Any ideas guys?

---

