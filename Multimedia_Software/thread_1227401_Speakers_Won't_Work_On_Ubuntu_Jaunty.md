---
title: "Speakers Won't Work On Ubuntu Jaunty"
date: 2009-07-30
forum: Multimedia Software
---

### Post by bonbeeno on 2009-07-30
Hello,

I've recently installed Ubuntu (Jaunty/v9.04) and after installing everything and getting it running I noticed my speakers were not working so then I tried another set of speakers and they were not working either :(.

**First Set Of Speakers:**
[EMachines SP-30A]("http://img1.classistatic.com/cps/kj/090716/426r2/966499_18.jpeg")  <---Link  (Only good link I could find of these sorry)

**Second Set of Speakers:**
[LEFT][COLOR=MediumTurquoise][Harman/kardon HK 206 - PC multimedia speakers  ]("http://reviews.cnet.com/pc-speakers/harman-kardon-hk-206/1707-3179_7-30113412.html")[/COLOR]



[/LEFT]

---

### Post by komputes on 2009-07-30
Hi bonbeeno,

Funny enough, I have both of these speakers and they work great in Jaunty. I doubt the speakers are the issue. I think the soundcard or a config file may be guilty here.

1 - Physical:  Make sure speakers are turned on and the volume regulator is up/unmuted.

2 - Logical: Check software volume levels for low/muted volume. Ubuntu may detect several sound channels and  wrongly guesses the one to enable. Make sure you have the correct device selected by selecting the correct alsa mixer from the pulldown menu.

Click on the speaker icon, in your top panel, Select "Volume Control". Once the Volume Control utility, click Preferences and enable all output channels. Test with the different volume levels while having a media file playing and see if sound comes out. The channels you are looking for (most common among sound cards) which should me raised and unmuted are Master, PCM, Front, Speaker.

You will also want to go to System > Preferences > Sound and make sure that under the "Devices" tab all are set to Autodetect and that the last item "Default Mixer" is set to the Alsa Mixer. 

3- Troubleshooting: Try a guest session or creating a new user, if sound works well for that user then try to remove your user's sound configuration file and restart the session:

```
$ rm ~/.asoundrc ~/.pulse/ ~/.pulse-cookie

```

---

### Post by bonbeeno on 2009-07-30
First of all thank you for responding so quickly

I did your Physical and Logical steps

Bad News (at least for me): The step you gave where I make a guest or a new account did not work and I tried both so my problem is still faced

Also I don't belive it is the sound card cause when I go onto my windows HD and watch a movie or video the sound is as clear as you can get from these speakers

But my sound card is connected to the motherboard so if it is here is the motherboard specs (for the sound card):

[Motherboard Specs Here Sound Specs About Half Way Down Page]("http://reviews.cnet.com/motherboards/elitegroup-945p-a-v3/4507-3049_7-32461144.html?tag=mncol;rnav")

---

### Post by bonbeeno on 2009-07-30
Strange I wnet to plug in headphones and when they were halfway in they worked but fully plugged in they didnt work and same goes for the speakers no joke lol. 


But now my new problem is how do i have it so i plug it in fully so theres no static

---

### Post by komputes on 2009-07-30
If you're not able to crate users, you may have a larger problem. Can you try running the Karmic Koala 9.10 LiveCD without making any changes to your hard drive (don't install just test audio files from the Examples folder in the LiveCD environment). You can get the CD by clicking here:

[PC (Intel x86) desktop CD]("http://cdimage.ubuntu.com/daily-live/current/karmic-desktop-i386.iso")

---

### Post by bonbeeno on 2009-07-30
I can create new users but that didnt do anything but...

when i plug my speakers not all the way in but most of the way the work but have static and same with the headphones

---

