---
title: "Just installed Mythbuntu minor issues"
date: 2008-04-15
forum: Mythbuntu
---

### Post by pinkmonkey on 2008-04-15
I just stated using Mythbuntu beta 8.04 for the first time after my MCE crashed and burned. First off I installed it over MCE that wouldn't load even in safe mode. I don't know if that had anything to do with it but I just thought I would bring it up. The problems I've seen are.
  The guide is very slow ( like it's freezing every time I press a button but then eventually catches up)
   My IR Blaster doesn't change the channel. It's not even trying ( no flashy lights)
   My remote wont adjust the volume. The volume comes up but doesn't actually adjust anything. Physically it's running from my STB to the audio in on my WinTV  PVR 250 (red & white) 

My set up is as follows
Board: ASUS P4S800D X
Processor: P4 2.4
1 G' of ram
Tuner: WinTV 250
Video Card: Geforce 6200
MCE Remote... and IR reciever/blaster

these might be problems with the beta.. Mythtv in general... or just something I've done but for just having used it for a couple hours it's pretty awsome. Anyway any help appreciated.

---

### Post by tgm4883 on 2008-04-15
First problem:  Did you install the restricted drivers?

Second:  Did you set the remote blaster up in MCC?

Third:  Try changing what the audio controls control (internal/external) in the setup.  It should be under general settings in the frontend.

---

### Post by pinkmonkey on 2008-04-15
Thanks TGM4883

I tried Your recommendations.

If by Restricted Drivers you mean the Nvidia drivers You can install through MCC in the Proprietary drivers tab. Yes I installed  them yesterday before I posted the message.All the menues work fine it's just the guide that is locking up.

As for the MCE Blaster/Remote  As far as I know It's what I have set up in the MCC. For remote I have MCE remote new version..., and the IR blaster I have set up is the MCE V2 usb. It recieves remote commands but doesn't transmit over the blaster to the STB.

Audio wise I couldn't find a setting that fits the description you described . In the General Settings, In the Front End there is what seems a audio page but there isn't and inter external setting.

I hope I'm not being dense and I would  like to get a mythbuntu up and running. So any help would be greatly appreciated.

---

### Post by adubas on 2008-05-22
> **pinkmonkey said:**
> Thanks TGM4883

I tried Your recommendations.

If by Restricted Drivers you mean the Nvidia drivers You can install through MCC in the Proprietary drivers tab. Yes I installed  them yesterday before I posted the message.All the menues work fine it's just the guide that is locking up.

As for the MCE Blaster/Remote  As far as I know It's what I have set up in the MCC. For remote I have MCE remote new version..., and the IR blaster I have set up is the MCE V2 usb. It recieves remote commands but doesn't transmit over the blaster to the STB.

Audio wise I couldn't find a setting that fits the description you described . In the General Settings, In the Front End there is what seems a audio page but there isn't and inter external setting.

I hope I'm not being dense and I would  like to get a mythbuntu up and running. So any help would be greatly appreciated.

Ever get the audio resolved? I have a Creative Labs Sound Blaster Audigy SE sound card which works great. Music, live tv, all work great.. can pause live TV with remote etc. The problem is my MCE USB remote does not change the volume on the sound card. The volume indicator goes up and down when I press the volume button but the sound does not actually go up or down. I did find another thread and adjusted the ALSA:default for the mixer etc but did not fix. The only bummer with my setup now is that I have to get up to go to my actual speaker volume to adjust the sound level... all of the other MCE remote functions work great...

---

### Post by akendall1966 on 2008-05-22
can you change vol on the keyboard OK F10 F11 keys if so mythtv probabably OK key mapping from you remote might not be set up right

AK

---

### Post by adubas on 2008-05-22
> **akendall1966 said:**
> can you change vol on the keyboard OK F10 F11 keys if so mythtv probabably OK key mapping from you remote might not be set up right

AK

When I press the f10, f11 keys the volume indicator does move up and down (same as on remote) on the screen but does not change the sound level. It does the same thing the remote does but does not change the actual volume... just goes through the motions...:(

---

### Post by akendall1966 on 2008-05-23
OK the only other sugestions which might be a dead end depending on what sound out you are using. On my system I am using onboard HDMI to my TV and I had to use alsamixer to unmute the digital output as it was set to muted on install not sure from your post if you are using digital out or not.

Hope this helps if not sorry I am out of ideas :(

---

### Post by adubas on 2008-05-23
Not using digital. I have a set of computer speakers in the normal jack output... The sound works great for everything I need it for, I just can't change the volume level without walking up and manually adjusting the volume knob on the speaker... I have tried a lot of different settings and will keep plugging away and post back if I find anything new... Thanks for your replies anyway...

---

### Post by boffyflow on 2008-05-27
> **pinkmonkey said:**
> Thanks TGM4883

Audio wise I couldn't find a setting that fits the description you described . In the General Settings, In the Front End there is what seems a audio page but there isn't and inter external setting.



I think the settings referred to are on page 3 of the settings titled "Audio". By default the checkbox "Use internal volume controls" is enabled. If you turn off the dialog will hide the internal options and it should use the external volume controls.

BTW: I have the same issue as you have and I just stumbled over this thread. I will give a try tonight and report back.

---

### Post by adubas on 2008-05-27
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/192382]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/192382")

I think this whole issue is bug related. I have tried a lot of options and no matter what settings I use, I am unable to control my sound with my remote control or f10 keys etc. When I press the volume up and down on my remote control, the volume on screen indicator goes up and down but it does in no way change the actual sound level...

The only way I am able to change volume is to walk up to the speakers and maually adjust the knob...

---

### Post by Dewey_Oxberger on 2008-05-27
I'm having this problem but I can't tell from the traffic on the bug report if the bug is really fixed or what the fix really was.  

Anyone fixed this and can offer a suggestion?

---

