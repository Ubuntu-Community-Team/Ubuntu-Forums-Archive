---
title: "Sounds dies after a few minutes"
date: 2008-03-18
forum: Multimedia &amp; Video
---

### Post by batman01 on 2008-03-18
I have Mythbuntu installed on a Jetway J7F2 miniITX mobo. It used the Via 8372 audio chip and after booting works for several minutes.

Sound then craps out and requires a reboot to bring it back. You might occasionaly get the odd burst of corrupted staticy vaguely recognisable sound but VERY occasionaly. Restarting X has no effect.

There are no messages in dmesg, there are no relevant messages in /var/log/messages. You can open amixer and play with settings nothing complains about any problem, just no sound.

If I boot from the CD, mount the harddrive and play music that way it works for hours. Boot from HD and it dies adter several minutes. Playing video's causes the same problem, sound dies, same symptoms.

I found a post on a similar, not the same, problem and followed intructions there on downloading and compiling the latest ALSA drivers which I think are 1.0.16. This made not one jot of difference.

I'm considering installing straight ubuntu to see if it has the same problem, then reinstalling Mythbuntu to see if that fixes it.

Otherwise I'm at a loss. Why should it work booted from CD but not from the install from the same CD? 

Any suggestions as to where I can look next would be appreciated.

Cheers

Pete

---

### Post by haraldmilz on 2008-03-18
Have you checked which sound device is being used during HDD and Live CD playback? If "Autodetect" is selected, maybe you want to play around and try all your 'playable' devices. Good luck!!

---

### Post by batman01 on 2008-03-18
Thanks for replying so quickly. I've exited the front-end and just used the speaker-test command. I tried the different devices as you suggested and get nothing except the occasional bit of static.

I've done rmmod snd_via82xx, then modprobe snd_82xx, the sound is now working again.
I'm leaving the speaker-test on for a while to see if it craps out, but the fact that if I bounce the driver it works again isn't looking good for the alsa driver is it?

cheers

Pete

---

### Post by batman01 on 2008-03-18
OK I've done away with X. Just from the command line, if I do "aplay test.wav" I get about 10 seconds of audio before it cuts out.

rmmod and modprobe on snd_via82xx brings the sound back. "speaker-test" plays for at least an hour which is as long as I've left it so far. aplay on my test.wav file kills it again in seconds.

I can repeat it at will. still no sign in dmesg or /var/log/messages that anything is amiss.

Suggestions anyone?

cheers

Pete

---

### Post by haraldmilz on 2008-03-18
OK. After seeing the commands you typed, I assume you&#341;e no linux beginner, so here goes a longshot: The audio driver from the live CD works, right? Look for the audio driver and perform the up/downgrade of your current audio device.

I have no idea how this is done, I am just using common sense here (that is what I would do!) :) :)

---

### Post by batman01 on 2008-03-18
Not a TOTAL newbie, no.... :)

I have to assume that the installed driver is the same one as the install disc. Unless its been updated and the update killed it? 

I'm not sure how you find out what driver is being used. lspci doesn't show you that does it? Is it going to be in /proc/something or other? I'll have a nose about

Cheers

Pete

---

### Post by haraldmilz on 2008-03-18
I wonder if this behavior replicates on a clean install... does anybody know if there's an update for the Via 8372 audio device driver after a clean install? Thanks

---

### Post by batman01 on 2008-03-18
I may just reinstall it, but I'm trying to avoid that cos I had to fiddle with the graphics drivers to get them to work and i'm not sure I wrote down what I did! ooops.

---

### Post by batman01 on 2008-03-19
OK,if anyone is interested - 

After a fresh install with just the w32codecs added, sound has been working for 20mins so far.
Going to get the openchrome driver going next to see if anything changes.

---

### Post by batman01 on 2008-03-22
For anyone thats interested -

The re-install seems to have fixed the sound. I have re-enabled the openchrome drivers and the TV card drivers and run all system updates bar MythTV to 0.21 cos that breaks MythTV. Sound is till OK, so it was just Mythbuntu getting its knickers in a twist.

Cheers

Pete

---

