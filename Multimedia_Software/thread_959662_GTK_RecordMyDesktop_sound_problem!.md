---
title: "GTK RecordMyDesktop sound problem!"
date: 2008-10-26
forum: Multimedia Software
---

### Post by Rytron on 2008-10-26
Hi,
I can record video with no problems with GTKRecordMyDesktop. The problem is, I cannot record with sound.

I have JACK Control installed.

When I try to record with sound enabled I get the message(attachment).

Also there is an attachment of the settings.

---

### Post by Toadmund on 2008-10-26
I just got my sound working, I will tell you how I did it.
Disable (un- X) the x you have for jack as it shows in your attachment.
Use your sound card settings instead.

Gp to synaptic package manager, download 'Gnome ALSA mixer'
Open it up, enable 'mix' see attachment.

Then make sure the sound card option in the volume control (little speakers up top) matches your sound card settings in recordmydesktop, now try it out.

---

### Post by Rytron on 2008-10-26
Cheers Toadmund,
I will try that now.
Cool cat avatar. Black & White cats are my favourite.

---

### Post by Rytron on 2008-10-26
I dont have any 'mix' option.
:confused:

---

### Post by Toadmund on 2008-10-26
Hmmm, seems you have a different version of Gnome ALSA mixer.
Go to 'synaptic package manager' and see if it has an update.

PS, that is Oreo in the avatar, she is very nice!

---

### Post by Toadmund on 2008-10-26
Just wondering, is the 'mix' option just out of view?
Is there a slider on the side?

---

### Post by Rytron on 2008-10-26
The version of gnome-alsamixer I have is 0.9.7.
No, there is no sign of 'mix' anywhere.

---

### Post by Toadmund on 2008-10-27
My version is 0.9.7

---

### Post by Rytron on 2008-10-27
> **Toadmund said:**
> My version is 0.9.7


I made a typo. My version is also 0.9.7 (my typo above has been corrected!)

---

### Post by Toadmund on 2008-10-27
Perhaps my ALSA mixer is different because I have a different soundcard?
Can anyone answer this?

---

### Post by Toadmund on 2008-10-27
OK, try this, open your ALSA mixer,

Click on edit>sound card properties
See if you can enable everything that is there.

---

### Post by Toadmund on 2008-10-27
See the attachment.

---

### Post by Rytron on 2008-10-28
Unfortunetely I already have all those ticked.

I can record my voice in Audacity(perfectly, even with a basic microphone) and then make a video in GTK RecordMyDesktop with no audio, then I join them in Window Movie Maker.

Its a bit awkward but must suffice for now.

This is really baffling though. :confused:

We will get there eventually though.

---

### Post by the_hack on 2008-11-07
I was able to record sound through my mic by using DEFAULT for sound, killing skype, and making sure my mic volume was up.

My problem is I want to capture sound from a video, not the mic, and I can't seem to figure that out.  Anyone?

---

### Post by the_hack on 2008-11-07
If you're just wanting to record through your mic.  Follow this tutorial:  [http://www.youtube.com/watch?v=T-tyN2EbYNs](http://www.youtube.com/watch?v=T-tyN2EbYNs)

---

### Post by andr3w on 2009-01-27
> **the_hack said:**
> If you're just wanting to record through your mic.  Follow this tutorial:  [http://www.youtube.com/watch?v=T-tyN2EbYNs](http://www.youtube.com/watch?v=T-tyN2EbYNs)

jc, like a viral video.

---

### Post by dddw on 2009-04-01
#14
> **the_hack said:**
> I was able to record sound through my mic by using DEFAULT for sound, killing skype, and making sure my mic volume was up.

My problem is I want to capture sound from a video, not the mic, and I can't seem to figure that out.  Anyone?

#15
> **the_hack said:**
> If you're just wanting to record through your mic.  Follow this tutorial:  [http://www.youtube.com/watch?v=T-tyN2EbYNs](http://www.youtube.com/watch?v=T-tyN2EbYNs)

ahum... that is not an anwser, issue is how to capture the sound of a movie.
For example, screencapture a bit of video from a website (which isn´t youtube, there are many tools for that (such as youtube-dl).
anyway... QUestion reamains: Is there a setting you can add to the sound settings of GTK-recordmydesktop that will capture the playback sound of anything you play during the recording??

Any help or ideas??

---

### Post by dddw on 2009-04-01
> **dddw said:**
> #14

Any help or ideas??

I found one, connect a stereojack cable from my headset connector to my microphone connector :D

But yet this is offcourse not my preferred method. (and the sound quality is quite bad too).

---

### Post by mocha on 2009-04-01
Look here

[http://ubuntuforums.org/showthread.php?t=986966]("http://ubuntuforums.org/showthread.php?t=986966")

---

### Post by CaptainMark on 2009-10-17
opening an old post here but im having this same issue, can anyone help

edit: without using jack that is, is it possible

---

### Post by nomnex on 2009-12-02
> **CaptainMark said:**
> opening an old post here but im having this same issue, can anyone help

Found your post cleaning my bookmarks. It works for me, so I am not sure I can help, but I recall an old thread (guide) I had used for the settings

Link: [http://ubuntuforums.org/showthread.php?t=986966](http://ubuntuforums.org/showthread.php?t=986966)

You might want to take a look?

---

### Post by Rytron on 2009-12-02
Thank you nomnex, I will check that link.

---

### Post by darkazurka on 2011-01-05
> **CaptainMark said:**
> opening an old post here but im having this same issue, can anyone help

edit: without using jack that is, is it possible

All my previous searches were pretty much in vain, but I've found the solution! I'm using the PulseAudio (cross-platform, networked sound server) and the only thing I had to type in recordMyDesktop under Advanced -> Sound(tab) -> Device -> was "pulse" just as seen in the screenshot, and it works!

---

### Post by cmxiv on 2012-08-26
the recorder is working fine, the problem is with the default settings in ubuntu... the mic is by default mute! to check this just goto system> Preferences >sound 
This would open the sound preferences. Now go to the input tab and just un-check the mute box adjacent to the input volume control.... it would work magical!

---

