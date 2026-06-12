---
title: "Audio input on TV tuner... no sound?"
date: 2006-06-07
forum: Multimedia &amp; Video
---

### Post by Donshyoku on 2006-06-07
First off, the specifications...

C-Media CMI9880 sound chip
--It is onboard, classified under Intel's Azalia audio configuration.  I have line-in and CD in support from the Volume Control applet.

Winfast TV2000 XP RM
--The card is supported under the bttv driver and I've seen a few people on this forum mention they have it working.  While I can't get the coax input to work, the S and Composite do and since I am running it from the satellite reciever, S is the way to go.

Now, I have the S-Video running to the card and in tvtime I am getting a beautiful image.  However, I have no sound!  The tuner itself does not have an audio input.  The sound is running from the card to my sound chips's CD line and then from the reciever to the Line-In on my sound chip.  It sounds strange, but it is all according to the guide on Leadtek's website.

In the Volume Control applet, I have the CD and the Line-In set as my input sources.  The volume is maxed and unmuted on each.  Also, I do have audio playback for files that are native to the system.

But no TV sound?  Any thoughts?

---

### Post by eight_car on 2006-06-07
[QUOTE=Donshyoku]First off, the specifications...

C-Media CMI9880 sound chip
--It is onboard, classified under Intel's Azalia audio configuration.  I have line-in and CD in support from the Volume Control applet.

Winfast TV2000 XP RM
--The card is supported under the bttv driver and I've seen a few people on this forum mention they have it working.  While I can't get the coax input to work, the S and Composite do and since I am running it from the satellite reciever, S is the way to go.

Now, I have the S-Video running to the card and in tvtime I am getting a beautiful image.  However, I have no sound!  The tuner itself does not have an audio input.  The sound is running from the card to my sound chips's CD line and then from the reciever to the Line-In on my sound chip.  It sounds strange, but it is all according to the guide on Leadtek's website.

In the Volume Control applet, I have the CD and the Line-In set as my input sources.  The volume is maxed and unmuted on each.  Also, I do have audio playback for files that are native to the system.

But no TV sound?  Any thoughts?[/QUOTE]

The Coax, first, hook it to a regular TV to make sure yo are getting a signal there. Next, if that is working, make sure the settings are on NTSC (not PAL - European standard), then comes the most intresting (ie frustrating part).

These TV cards are not all the same. You most likely need to set the tuner properly.  My card would work half-crappy until I set the tuner to the correct setting.

Use the following below

cd /etc/modprobe.d
sudo vi bbtv

options bttv card=X tuner=Y

:wq

For me card=34 tuner=42 worked, and you may have the same one I have, if it don't work, do what I did - search the internet for the correct settings.


Hope this helps
reboot

---

### Post by sou1980 on 2006-06-08
Hello everybody.

I have a similar problem. I have a CMI9880 on board sound card and a PixelView USB TV tuner. Using the usbvision driver, I have managed to make the tuner work but I don't get any sound at all. When connecting the speakers directly on the TV-tuner sound plays ok.

I have tested that all of the sound card outputs are enabled. However, no sound. I am sure this has something to do with the setup of the sound card. Any thoughts? How can the playback of the audio input be enabled on CMI9880 sound cards?

Thank you for your help. Let us make ubuntu the dominant OS!

Stavros

---

### Post by Donshyoku on 2006-06-08
[QUOTE=eight_car]The Coax, first, hook it to a regular TV to make sure yo are getting a signal there. Next, if that is working, make sure the settings are on NTSC (not PAL - European standard), then comes the most intresting (ie frustrating part).

These TV cards are not all the same. You most likely need to set the tuner properly.  My card would work half-crappy until I set the tuner to the correct setting.

Use the following below

cd /etc/modprobe.d
sudo vi bbtv

options bttv card=X tuner=Y

:wq

For me card=34 tuner=42 worked, and you may have the same one I have, if it don't work, do what I did - search the internet for the correct settings.


Hope this helps
reboot[/QUOTE]

I've done this all.  I had to manually set my card before it worked at all according to [www.bttv.de;](www.bttv.de;)  I also have my coax running into the TV set personally and I do have picture and sound.

---

### Post by eight_car on 2006-06-08
Try using differednt numbers to see if you can get it to come in correctly. 

Like I said, the TV tuner card you have was manufactored in many places, the tuner and card number may have to be adjusted.

try expierementing with different numbers.

Also check the log of your box and see what card number is reported.

If you have any other info, I'll try to help.

---

### Post by Donshyoku on 2006-06-08
What numbers should I try?  There are probably hundreds of combinations!  I am so lost!  ](*,)

---

### Post by eight_car on 2006-06-08
[QUOTE=Donshyoku]What numbers should I try?  There are probably hundreds of combinations!  I am so lost!  ](*,)[/QUOTE]

Well I found my card also listed as 35, so you could try that.

Its been a while since I looked this stuff up, do a search on your card on the internet and see what all is reported.

I found different numbers fo rmy same card.  Sorry I can only remember the one right now

---

### Post by cblanquer on 2006-06-11
Hello I have an ASUS my cinema dual card, no hardware audio plug i.e. no wire form the card to the any audio plug on my mobo so that non from tvtime, xawtv nor zappingtv delivered audio.
I found out some people solved by running a terminal command "sox" to copy the digital audio signal from its output devide (/dev/dsp1, /dev/dsp2,.../dev/dspn depending on the system) to the soundcard device (/dev/dsp).
This worked after some finetuning. There is still a little sound delay but I do not consider it relevant anymore.
However I do not know yet how to launch a terminal session with this command automatically when opening any of those applications.

My command is:
sox -r 32000 -w -t ossdsp /dev/dsp2 -t ossdsp /dev/dsp

References in :
[http://tvtime.sourceforge.net/help.html#audioconnect](http://tvtime.sourceforge.net/help.html#audioconnect)
[http://linuxcommand.org/man_pages/sox1.html](http://linuxcommand.org/man_pages/sox1.html)
[http://linuxcommand.org/man_pages/soxexam1.html](http://linuxcommand.org/man_pages/soxexam1.html)
[http://www.linuxtv.org/](http://www.linuxtv.org/) (I have not recorded the exact link here)

If anyone can tell me how to run the command automatically I would be thankfull.

---

