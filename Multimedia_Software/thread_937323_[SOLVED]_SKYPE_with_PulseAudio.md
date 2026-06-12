---
title: "[SOLVED] SKYPE with PulseAudio"
date: 2008-10-03
forum: Multimedia Software
---

### Post by markbuntu on 2008-10-03
Since so many people are having such a hard time getting their skype to work, I finally installed it and true, it does not work out of the box but the solution is fairly simple. 

** This is for Hardy Heron 8.04 only!** 

If anyone has gotten Skype working with Pulseaudio in Intrepid 8.10 please make a post here explaining how you did it or post a link to the info. Or let me know if this works as is. If changes are needed for Intrepid will add something to this OP so others can find it. (I have been unable to get any version of Intrepid to even boot on my machine so I am unable to do any testing myself. Your help would be greatly appreciated.)

Thank you.


You can get the skype-static package from Mediabuntu (not the skype-static-oss package):

Edit your ~/.asoundrc file and add this to the end of the file:

```

pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
pcm.pulse {
    type pulse
}

ctl.pulse {
    type pulse
}

```

Save the file, log out and log in. Start skype. Go to Options/Sound Devices and select the new pulse device.  Open the PA Volume Control and see if skype shows up. If you cannot hear it or the mic is not working make sure you have the proper input and output devices selected as defaults in the PA Volume Control.  You can make an /etc/asound.conf file and put these lines in it if you need to do this system wide. 

If you find the sound stuttering and crackling etc on skype but other applications are OK, you can edit the /etc/pulse/daemon.conf file. At the end of the file are two lines like this:
```

;default-fragments = 8
;default-fragment-size-msec = 5

```
Change them to look like this :
```

default-fragments = 5
default-fragment-size-msec = 25

```

Save the file and restart Pulse Audio from terminal.

To kill pulseaudio:
```

killall pulseaudio

```

To restart pulseaudio
```

pulseaudio -D

```

That's it, enjoy.

I got the first part of it from the link below, the Mandriva folks figured it out a while ago I guess. The second part comes from psyke83.

[http://wiki.mandriva.com/en/Releases/Mandriva/2008.0/Errata#Skype_with_PulseAudio](http://wiki.mandriva.com/en/Releases/Mandriva/2008.0/Errata#Skype_with_PulseAudio)


[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

### Post by rousselm on 2008-10-03
Hello,

I've tried what you've posted and many other things as skype didn't seem to work properly....
I found out now that the volume sound in skype is very low and that in fact my mic is working with skype but the sound is really low and really bad quality too (like if the internet connection was very bad or if I was feedling with the mic jack).
When following your post, I don't actually get "pulse" to choose in skype. I guess I might have played around too much with the configuration files trying to solve the problem..... Does someone has a way to redo a clean install of all audio files/pachages and then have skype working well?
Thanks a lot for any help...

Marie

---

### Post by markbuntu on 2008-10-03
Does this happen with other applications using your microphone of just with skype?

You can look in my guide here, which will help you to get back to your default settings, there is a Restore Default Settings Section in there somewhere:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by kuproverto on 2008-10-09
I've followed the instructions here and on your other [post]("http://ubuntuforums.org/showthread.php?t=843012") where I added all the packages but still can't get the mic to work. Also, now I can't hear the Skype test sound either.

The Skype settings for Sound In, Sound Out & Ringing are all pulse. There are 6 other choices available in the drop downs. All begin M Audio Revolution 5.1 then are followed by (hw:Revolution51,0), (plughw:Revolution51,0), (hw:Revolution51,1), (plughw:Revolution51,1), (hw:Revolution51,2), (plughw:Revolution51,2). Sound can't be heard and the mic doesn't work using any of these settings. 

In Volume Control the Device is 0: M Audio Revolution-5.1 (Alsa mixer)

The Playback tab has PCM, Line Loopback, CD Loopback & Mic Loopback none of which are muted.

The Recording tab has PCM Capture which isn't muted

> Open the PA Volume Control and see if skype shows up.

Is that the Volume Control I just referred to? Skype doesn't appear there.

> If you cannot hear it or the mic is not working make sure you have the proper input and output devices selected as defaults in the PA Volume Control. 

In Sound Preferences I Have PulseAudio Sound Server selected for all 4 choices at the top with the Default Mixer Tracks Device being M Audio Revolution-5.1(Alsa mixer)

> You can make an /etc/asound.conf file and put these lines in it if you need to do this system wide.

Which lines? How?

---

### Post by markbuntu on 2008-10-09
You need a mic capture to get mic input to work. In the volume control on the panel choose Open Volume Control/Edit/Preferences and turn on microphone, microphone boost, mic capture and mic boost capture. I am not familiar with the Revolution cards so you may not have all of these but turn on the ones you do. They should then appear in the Volume Control/Recording and you can turn them on and adjust the volumes. The mic should now work. You may have to logout and login or reboot for this to take effect.

Make sure you have also selected the Revolution for the default in the Input and Output Devices section of the Pulse Audio Volume Control.

---

### Post by kuproverto on 2008-10-10
> Open Volume Control/Edit/Preferences and turn on microphone, microphone boost, mic capture and mic boost capture.

I don't have any of those options. Here's a screenshot of what's available and turned on. EDIT: image no longer available, sorry.


> Make sure you have also selected the Revolution for the default in the Input and Output Devices section of the Pulse Audio Volume Control.

Should there be a menu choice for Pulse Audio Volume Control? The closest I see is PulseAudio Preferences but there are no volume options there.

---

### Post by xc3RnbFO8P on 2008-10-10
Volume Control> option, is there **mic** or **front mic**?

---

### Post by markbuntu on 2008-10-10
> **kuproverto said:**
> I don't have any of those options....


Should there be a menu choice for Pulse Audio Volume Control? The closest I see is PulseAudio Preferences but there are no volume options there.

Can you hear your mic at all, anywhere, with any application?

---

### Post by kuproverto on 2008-10-10
> Volume Control> option, is there mic or front mic?

On the Options tab of Volume Control there is Capture Channel. It has 3 options in the drop down, Mic, Line and CD. Mic is selected.

> Can you hear your mic at all, anywhere, with any application?

I guess the only app I can test it with is Sound Recorder and, no, I can't record using the mic.

---

### Post by markbuntu on 2008-10-11
Then this problem, while related to getting skype working, is not really a skype problem, it is more basic than that. Once you figure out your mic, skype will probably work fine. Once you do get the mic working, if you are still having problems with skype, come back here and I will try to help you. 

Have you tried a google search for your specific sound card, maybe you can find some tips to getting the mic working. 

Let me know what you find out, I am curious...

---

### Post by kuproverto on 2008-10-11
> Have you tried a google search for your specific sound card, maybe you can find some tips to getting the mic working.

Thanks, I'll do that and also look on this forum.

---

### Post by ububaba on 2008-11-04
> **kuproverto said:**
> Thanks, I'll do that and also look on this forum.

Was wondering, what happened to your answer?

---

### Post by riyasmp on 2008-11-05
guys i am having a problem with my skype and 8 10.

i was using 8 04 so far and using skype on it was alright. to make skype work on 8 04 i had to go to master volume>options>input source and change the input source from mike to line and put it back to mike. Interestingly skype failed to work if i don do it. I had to do it only once the ubuntu starts up. If i din do it callee couldnt hear my voice but I could hear them. anyway i was OK with that.

when i upgraded to 8 10 the problem was different. I was not able to make a call at all. it started giving me the error message "problem with audio play back" when ever i call anyone. i went sound devices and played with input output source and got it right with option "pulse" for input source, output source and ringing.

now i am able to make calls but the callee cannot hear my sound. I applied the trick i used for 8 04 but its not working. i am not getting the playback message when i call "echo"

i tried recording sound on sound recorder but its not recording instead it hangs whenever i try recording my voice. But on audacity i am able to record my voice and play it without any problem.

The sound device on master volume is set for HDA intel Alsa mixer. i have played with other options as well but its not working.

guys i am not a computer engineer and if anyone can give me some input how to get around it in a simpler way without using computer jargons it would be a great help.

Thanks in advance
riyasmp is online now Report Post   	Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message Thanks
riyasmp
View Public Profile
Send a private message to riyasmp
Find More Posts by riyasmp
Add riyasmp to Your Contacts

---

### Post by GoLinux on 2008-11-09
riyasmp and kuproverto,

I'm having exactly the same problem you have. I'm running 8.10 Intrepid on a Thinkpad T41. Sound output worked out of the box so I didn't think to check sound INPUT. After I installed Skype (downloaded from their website) and tried to get it running, I realized that even recording via microphone with "Sound Recorder" doesn't work.

Initially not even "sound out" and "ringer" worked, but after selecting "pulse" that was fixed. However, selecting "pulse" as "sound in" doesn't help. It does change something, however. In fact, if "pulse" is NOT selected as "sound in", when I try "make a test call" it tells me there is a "problem with audio capture".

With "pulse" selected as "sound in" the test call goes through, but it doesn't record anything from the microphone.

As markbuntu pointed out, the fact that not even "Sound Recorder" actually record anything means there is an issue at system level, not just Skype.

Interestingly, I noticed that if I increase the playback volume through the hardware buttons on the T41, at some point I get the typical microphone/speakers feedback, which means the microphone is actually picking up the ambient noise and "looping" it through the speakers. Also, if I enable the microphone boost, I clearly hear an increase in background hiss from the speakers, which is what you would expect. It seems like the hardware is ok, but for some reason the microphone signal can get to the applications.

As of now, I have not yet found a solution, although I have tried all the options I could think of in the Mixer applications, including activating the "capture" slider and some of the switches.

I have also tried "grep 'audio' /etc/group" in console and it returns "audio:x:29:pulse". Is this normal? I would have expected "audio:x:29:ubuntu", but I'm not familiar with the whole "pulse" situation. I guess I have to study more on the subject.

I'll continue to try and report back. If anybody else has fixed this problem I'd sure appreciate any suggestions!!!

---

### Post by markbuntu on 2008-11-11
It sounds like the capture part of your sound driver is somehow not working correctly. This can happen with some sound cards/chips if the digital IEC958 or SPDIF or is enabled. The mic gets rerouted to the digital output instead of the analog capture. There can also be a problem with mic switching for many HDA devices. OEMs have really messed around with the firmware. You can look here for possible help with that:

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)


[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

For more general troubleshooting, you can look in here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by fINTiP on 2008-11-11
I already have skype installed, but you say to install the medibuntu version- does that mean I should uninstall and reinstall skype? I don't know what package I have, or how to tell.

Would love to have this working, as I currently cannot use skype at any point after I have used firefox and run a page with flash. Interestingly enough, I don't have this problem with epiphany.

L

---

### Post by markbuntu on 2008-11-11
Which version of flash are you using?
If it is flash 9, you need the package

libflashsupport

for it to work properly whcih may eliminate this problem for you without you having to do anything else.

If it does not, the version of skype you have may not work properly with pulseaudio so, if you do not know which version it is, remove the one you have and get the one I reccomend in the OP. Once you have it setup as in the OP, you should not be having this problem with flash.

If you are using Intrepid, skype should work out of the box.

---

### Post by fINTiP on 2008-11-11
How do I tell what version of flash I'm using?

---

### Post by markbuntu on 2008-11-12
> **fINTiP said:**
> How do I tell what version of flash I'm using?

In firefox/Tools/Add-ons/Plugins all the plugins are listed with version info.

---

### Post by GoLinux on 2008-11-13
I got "Sound in" via the built-in microphone in my laptop to work. First, I checked "capture" and "microphone capture" in the "preferences" of the audio mixer, sliders up and unmuted.

Next, I went through the drop-down list in "sound In" and tried all the different names under which the sound card was listed. You'll probably see it listed with several slightly different identifiers. In my case I got the microphone working selecting the one listed right after "pulse". If it doesn't work, try all the others until you get the one which does.

I used the "make a test call" function in Skype options to check wich selection of "sound in" worked. Takes a while, but it worked!

Now Skype works fine, but I still can't record through "Sound Recorder". As all the remaining applications have sound out, at this time that is a secondary issue for me.

---

### Post by deftly_dante on 2008-11-13
I just got Skype to work flawlessly on my Thinkpad T41, as I was having the exact same issue as GoLinux. I changed Sound Out and Ringing to pulse, and tried each 'sound in' device until I found one that worked. Remember to press Apply after you choose each 'sound in' device before performing a test call. For me, the 'sound in' device that worked was Intel 82801DB-ICH4 (hw:I82801DBICH4,0). I owe this solution to the pusleaudio HOWTO ([http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)), as noted under Appendix C: Application Compatibility Guide - Skype. (I did not perform any of the fixes described in the HOWTO.)

---

### Post by GoLinux on 2008-11-13
deftly_dante,

this is the same I had to chose for my T41 as well. Now that you wrote it I remembered it. 

Do you have Ubuntu installed on your T41 HDD? If yes, how long does it take to boot?

For now I'm using Ubuntu 8.10 off a 8Gb Flash Drive and it takes about 5 minutes to get to the desktop from boot.....

After that the system is quite zippy, so I wonder how faster 8.10 Intrepid would be booiting from the HDD

---

### Post by riyasmp on 2008-11-16
> **GoLinux said:**
> riyasmp and kuproverto,

I'm having exactly the same problem you have. I'm running 8.10 Intrepid on a Thinkpad T41. Sound output worked out of the box so I didn't think to check sound INPUT. After I installed Skype (downloaded from their website) and tried to get it running, I realized that even recording via microphone with "Sound Recorder" doesn't work.

Initially not even "sound out" and "ringer" worked, but after selecting "pulse" that was fixed. However, selecting "pulse" as "sound in" doesn't help. It does change something, however. In fact, if "pulse" is NOT selected as "sound in", when I try "make a test call" it tells me there is a "problem with audio capture".

With "pulse" selected as "sound in" the test call goes through, but it doesn't record anything from the microphone.

As markbuntu pointed out, the fact that not even "Sound Recorder" actually record anything means there is an issue at system level, not just Skype.

Interestingly, I noticed that if I increase the playback volume through the hardware buttons on the T41, at some point I get the typical microphone/speakers feedback, which means the microphone is actually picking up the ambient noise and "looping" it through the speakers. Also, if I enable the microphone boost, I clearly hear an increase in background hiss from the speakers, which is what you would expect. It seems like the hardware is ok, but for some reason the microphone signal can get to the applications.

As of now, I have not yet found a solution, although I have tried all the options I could think of in the Mixer applications, including activating the "capture" slider and some of the switches.

I have also tried "grep 'audio' /etc/group" in console and it returns "audio:x:29:pulse". Is this normal? I would have expected "audio:x:29:ubuntu", but I'm not familiar with the whole "pulse" situation. I guess I have to study more on the subject.

I'll continue to try and report back. If anybody else has fixed this problem I'd sure appreciate any suggestions!!!

GoLinux

I am not a software engineer so forgive me if i am talking nonsense. I have atlast got around this issue and my skype is working fine on ubuntu 8 10

1) install skype from the medibuntu repositry ( i removed the skype i installed from the website.i don know by some uknown problem i couldnt even make a test call with that version) while install skype from medibuntu R, install both skype common and skype-static-oss variant (for me it did not work with skype common alone)

2) skype>audio setting and switch to pulse mode for sound in , sound out and ringing. at this point i could make a call to echo which i was not able to before. Beforehand it always gave an error message when i tried to call echo. Eventhough I was able to call echo it was not recording my voice then.

3) I cheked my voice recorder from application>sound recorder.interestingly it was not recording voice either. to fix it i went to master volume and opened recording. For some unknown reason recording device is muted by default. Still i have to double check every time I use recording device that it is not muted. Its found that it is muted automatically after every use!!!!!!!!!!!!
Now i can use my voice recorder fine but still skype cannot record my vocie.

4) To make the skype record vocie i have got an old trick now. mastervolume>options>inout source and change input source from mic to front mic and back to mic again. I don know i have to do it everytime (only once)i restart my ubuntu to make it work.

Please let me   know what is happning

riyas

---

### Post by fINTiP on 2008-11-16
I checked, I have flash 9.n whatever. I installed as instructed above.

And I have the same problem still. :confused:

L

---

### Post by fINTiP on 2008-11-16
I just fixed my skype problems by referring to [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578), and I'm now the happy owner of a laptop that allows me to have skype and firefox both running properly at the same time. :D

After 2 months, it's about time. I really wish they would have just delayed the release of 8.04 until they had it working right, you know...

L

---

### Post by movil on 2010-04-07
Guys what I really don't understand...is :

Why all this worked perfect with Skype 2.0 and not with this 2.1 version ?

The only thing that adds so far...is that it sends SMS ! Who sends SMS in skype ? I bet only 0.1 % of the users.

Personally I'm returning to the previous version

---

