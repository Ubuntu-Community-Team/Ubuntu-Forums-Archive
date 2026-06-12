---
title: "Oss audio with usb sound card and flash"
date: 2009-07-18
forum: Multimedia Software
---

### Post by minghio on 2009-07-18
Hi, I use my laptop pc with an external usb sound card that works nice using oss drivers.
When I watch flash video the audio doesn't come frome usb sound card but I hear it from the speakers of the laptop.
How can I manage to route the sound of flash video to the external soundcard?

---

### Post by igorzwx on 2009-07-18
What do you mean by OSS drivers?

Do you have ALSA or OSS4?

---

### Post by minghio on 2009-07-18
I meann Oss4

---

### Post by igorzwx on 2009-07-18
USB audio devices are not supported by OSS4

---

### Post by minghio on 2009-07-18
I hear the sound correctly if I listen to mp3, videogames, avi.
The only thing that I cannot route to the usb soundcard is the sound of flash video.

---

### Post by minghio on 2009-07-21
No one can help me?

---

### Post by igorzwx on 2009-07-21
I looks like you have not OSS4

If you believe that you have OSS4,
execute these commands (terminal):


osstest

ossmix


ossinfo -v3


and publish here the results

---

### Post by martinbaselier on 2009-07-21
@igorzwx according to the arch wiki, oss4 does support usb audio devices. Only the support is still experimental. kernel module : oss_usb

It might be possible to have both alsa and oss if you have 2 devices. I'm not sure about it though. 

So could you trie to start alsamixer too. It should output:
```

alsamixer: function snd_ctl_open failed for default: No such file or directory

```

about the flash sound, what's the output of the following commands. 
```

ls /usr/lib/libflashsupport.so -al
lsmod | grep oss
lsmod | grep snd

```
To copy output from the terminal, select the text with your mouse and press right mouse button, choose copy.

---

### Post by igorzwx on 2009-07-21
Hi!

It might be not so simple to have both ALSA and OSS4 drivers
loaded simultaneously.

I have already tried iMic USB with OSS4.

I will try your commands.

Best,
Igor

---

### Post by martinbaselier on 2009-07-21
I was not suggesting to install both (**do not attempt that unless you feel very experimental**), but it might have happened. That's why I said it. 

to explain the commands:
libflashsupport handles the sound output of flash.
lsmod shows the kernel modules. 
the kernel modules of oss have oss in the name
the alsa kernel modules have snd in the name.

---

### Post by igorzwx on 2009-07-21
$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory

$ ls /usr/lib/libflashsupport.so -al

lrwxrwxrwx 1 root root 38 2009-07-10 19:54 /usr/lib/libflashsupport.so -> /usr/lib/oss/lib/libflashsupport_32.so

$ lsmod | grep oss
oss_usb               117132  2 
oss_ich                27504  6 
osscore               561844  2 oss_usb,oss_ich

this command:
$ lsmod | grep snd

produced nothing.
And it should be so.
snd should be blacklisted.

I have an old box for experiments.
If you have ideas, I would be happy to try.

But this might be better to discuss on OSS4 forum.
They are doing something about this.

Best,
Igor

---

### Post by martinbaselier on 2009-07-21
His card is on the supported hardware list, yours isn't. And since most ubuntu users will try the ubuntu forums first, I think it would be good to have some info about it on here. I've created an ubuntu how to, I'll pm you when it's approved, since you seem to be just as happy about the sound quality of oss  as I am.

---

### Post by igorzwx on 2009-07-21
Hi Martin!

Which card in which list?

My old card is supported or not?
by OSS4? or ALSA?

Could you please make this clear?

Howto is necessary, no doubt.

But this might be the task of the moderators of this forum.
It is so in Audacity forum at list.

Best,
Igor

---

### Post by martinbaselier on 2009-07-21
I did a quick scan and did not see your usb card in this list: 

[http://www.opensound.com/osshw.html](http://www.opensound.com/osshw.html)

It show however some m-audio usb-devices. 

On this forum howtos are created by users and approved by moderators/administrators.

---

### Post by igorzwx on 2009-07-21
Many thanks!

---

### Post by minghio on 2009-07-22
Thanks, I really appreciate your support.
This evening I'll post my outputs.

---

### Post by aaronchall on 2009-09-20
Greetings, I'm having the same problem.  I have a USB sound card / headset adapter.  Early experimentation found that OSS worked for the CD player, but I couldn't get audio for web pages and skype through the card. 

I used sudo to edit /etc/modprobe.d/alsa-base.conf and added my intel card to the prevent index=0 list and commented out the USB ones.

Upon reloading, my USB was then the default for the CD player, but for web pages and skype, I couldn't use it.

I'm attempting to remove the USB lists from the blacklists I've seen in the linux base sound files... maybe this will work...
Nope, it didn't.

I hear the audio in the headphones when the computer comes up, but youtube and skype are sending audio through the laptop speakers.

I am concluding that this issue is a software one stemming from the browser and skype, since both seem unable to output OSS compatible sound.  I suppose I should have looked specifically for a linux compatible usb soundcard, even though I was reassured by my techie friends that if it was plug and play, it should work.  It's probably moot, since I have to switch over to Windows anyways to use it for tutoring (Skype in ubuntu doesn't have screen-sharing...)  If someone knows of alternatives that output OSS, that would be great, if not, no biggie.

Aaron

---

### Post by aaronchall on 2009-09-28
OK, I'm not sure what I did to make the headphones work with youtube and other websites.  I think I updated my alsa (drivers?).  I have recently used the code on this page: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683), the comprehensive multimedia how-to thread, here:
[B]
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar[/B]

I also did this:
[B]
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update[/B]

and I did this: 

**sudo apt-get install libv4l-0**
**sudo apt-get install libv4lconvert**

I honestly don't know if any of these helped exactly, but now I can use my usb card to listen to websites.  Maybe I could have originally without these install commands.  I sometimes mess up my sound and have to fix it again (that is, play around with the various sound options in the sound menu, trial and error).  I am listening to youtube again, but the sound icon by the date (incorrectly) says it's muted.  I can't (trial and error) get the icon to say it's un-muted.  Go figure...

Aaron

---

