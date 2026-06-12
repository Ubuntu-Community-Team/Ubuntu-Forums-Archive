---
title: "Setting up surround sound through A/V Receiver"
date: 2008-01-30
forum: Multimedia &amp; Video
---

### Post by TrichomeKid on 2008-01-30
Im not sure if setting up surround sound through an Audio/Video Receiver makes much difference as far as configuration goes.  Ive searched the forums, and yes they've been helpful but Im still not sure my speakers are working the way they are supposed to. 
I will list my setup, ALSA configuration, etc...

[LIST]
[*]Ubuntu 7.10
[*]Realtek ALC655 onboard sound card (supposed to support 6 channels)
[*]2 Premier speakers connected to Subwoofer through typical audio cables
[*]Soundcard Line-out connected to TEAC Audio/Video Receiver through Auxliary ports
[*]VCR Out from Receiver connected to Subwoofer (VCR Out may be something different on other Receivers.  This is the only Audio Out port I could find on mine.)
[*]2 RCA surround speakers connected to Rear  R/L on back of Receiver
[*]Dolby surround on receiver: enabled
[*]Channel mode in sound options:  4
[*]Surround Jack mode:  Shared
[*]Duplicate Front: Disabled (Wouldnt this defeat purpose of Surround sound?)
[*]1 Cup strong coffee
[/LIST]
Surround sound bar in Volume Control is turned up, but even if I turn it down it makes no difference.  The thing is when I play music, I hear it coming from all speakers.  But when I do the speaker-test in Terminal when it voices Rear Left and Rear Right, I hear nothing from those speakers.  Weird thing is, I can hear the voice in the rear speakers when it says Front Right/Left.. but its almost like a whisper/distorted.

I´ve added the .asoundrc file ([http://www.newlinuxuser.com/surround-sound-in-ubuntu/](http://www.newlinuxuser.com/surround-sound-in-ubuntu/))  into my Home directory which seemed to do the trick, but the speaker-test still wouldnt work. So I dont believe that the sound coming from the rear speakers when playing music is True Surround Sound.  Is the fact that Im running this all through the receiver have something to do with it?  As I said, Dolby Surround is enabled on the receiver and thats the only way the rear speakers seem to work.

Sorry for the long post, hopefully this will end up helping others.

---

