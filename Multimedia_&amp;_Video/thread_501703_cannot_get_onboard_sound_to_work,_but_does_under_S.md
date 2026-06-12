---
title: "cannot get onboard sound to work, but does under SUSE and XP"
date: 2007-07-15
forum: Multimedia &amp; Video
---

### Post by CardUJ on 2007-07-15
Hi

This is a new install of Ubuntu.
Sound has not worked at any point under Ubuntu
Sound does work under SUSE 10.2 install and XP (same h/w configuration)
It is a onboard sound card, (a C-Media CM6501 7.1 channel audio compliant with UAA architecture) on the ASRock AM2NF3 mobo

I have already checked and double checked mute is not on. 

Reading other posts and trawling the internet, I have switched the Sound Preferences -> Sound Events -> Sound Playback to being USB Audio and when i test that i get a constant tone. This is the only sound i have managed to get from speakers. If i leave it on autodetect and test it just closes the window and does not do anything (noticeable). If i try one of the other options (OSS for example) i get the following. "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing"

It surprises me i can hear the test tone described above but nothing else at any point, i assume i am doing something obviously wrong?

I am very, very new to linux assistance and patience would be appreciated.

Thanks

---

### Post by LDRoamer on 2007-07-17
I am not sure if this will help but I will tell you what worked for me. I am using a Turtle Beach usb sound card (which is a c-media device).  Changing all the settings to USB sound gave me some sound but not all sounds worked (for example no system sounds).  I also got the error you describe trying to set it to OSS etc.  Even though this was the only sound card in my system I had to force it to be the default card using asoundconf. I got this idea from another post on this board.

If you run the following in a terminal window:

asoundconf list

your audio device should be listed - in my case it had the somewhat confusing name of "default"

In order to set it to the default I had to do 

asoundconf set-default-card default

replace the word "default" with whatever your device is called. Now reboot and you're done.

Once I had set it is as the default sound card all sounds worked as they are supposed to. I am not sure if it will work for you but it is worth a try.

---

