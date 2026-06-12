---
title: "new mythbuntu install - my experience"
date: 2010-07-08
forum: Mythbuntu
---

### Post by str8g8 on 2010-07-08
Firstly a massive thumbs up to everyone working to make open source a real alternative. It's come a long way since I last tried ubuntu.

I wanted to use an old vaio desktop as a cheap media centre (just playback from a nas box, nothing too fancy)

A fresh install on winxp wouldn't recognize the onboard audio, and I tried unsuccessfully for a couple of days to intall the correct drivers for a SiS audio controller on this custom sony motherboard. Absolutley nothing worked.

I finally gave up and tried mythbuntu and it just ... worked :o. I was gobsmacked - and it's a real testament to the open source community and the progress that has been made - as I said, there was some fairly non-standard hardware to deal with.

Onto the user experience. It was a little tricky to find out how to permanently mount the nas drive share. It took a while to find the right syntax in fstab and getting it working - lots of weird permissions issues. The information I needed was in lots of different places and it tool me a while to piece it all together.  I think this would be a barrier to many people. A graphical interface for mounting shares permanently through the file browser would be great.

My remaining problems are relatively minor, and I'm fairly confident I can solve them:

1. I can't add my shared nas mount to the mythtv frontend - when I add the /mnt/stora/FamilyLibrary fodler it disappears straightaway.

2. DVD playback is flaky from the mythtv front end on the few I have tried so far - pixar movies won't play, castle in the sky gives me a the first menu to select language and then sends me back to the frontend for instance.

For these reasons I have resorted to exiting the frontend and using vlc on the desktop. vlc also has some issues with the DVD playback but it's usually possible to get it to work via scene selection etc.

3. Screen resolution - because I'm running it through a tv the native res is 1360x768 but this doesn't appear as an option so I'm stuck with 1024x768 atm

If anyone can help with these that would be great, but I'm pretty sure I'll figure it out in the end.

Once again, thanks for making it possible. :D

---

### Post by superm1 on 2010-07-08
> **str8g8 said:**
> Firstly a massive thumbs up to everyone working to make open source a real alternative. It's come a long way since I last tried ubuntu.

I wanted to use an old vaio desktop as a cheap media centre (just playback from a nas box, nothing too fancy)

A fresh install on winxp wouldn't recognize the onboard audio, and I tried unsuccessfully for a couple of days to intall the correct drivers for a SiS audio controller on this custom sony motherboard. Absolutley nothing worked.

I finally gave up and tried mythbuntu and it just ... worked :o. I was gobsmacked - and it's a real testament to the open source community and the progress that has been made - as I said, there was some fairly non-standard hardware to deal with.

Thanks for the nice words!

> 
Onto the user experience. It was a little tricky to find out how to permanently mount the nas drive share. It took a while to find the right syntax in fstab and getting it working - lots of weird permissions issues. The information I needed was in lots of different places and it tool me a while to piece it all together.  I think this would be a barrier to many people. A graphical interface for mounting shares permanently through the file browser would be great.

The should have been a utility installed (shares-admin) that I thought should have done this graphically for you.

> 
My remaining problems are relatively minor, and I'm fairly confident I can solve them:

1. I can't add my shared nas mount to the mythtv frontend - when I add the /mnt/stora/FamilyLibrary fodler it disappears straightaway.

Try adding it as a storage group in the backend instead.

> 
2. DVD playback is flaky from the mythtv front end on the few I have tried so far - pixar movies won't play, castle in the sky gives me a the first menu to select language and then sends me back to the frontend for instance.

For these reasons I have resorted to exiting the frontend and using vlc on the desktop. vlc also has some issues with the DVD playback but it's usually possible to get it to work via scene selection etc.

I would recommend trying to update to the latest auto-builds build of mythtv 0.23 ([http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)).  You'll find lots of fixes, that might include yours for DVD playback.  If not, then you'll be more in a position with a current build to be able to file an accurate bug that developers can look over when they get a chance.  Usually one of the first things you'll hear when you file a bug is "Please update to the current version and see if you can reproduce it", so this will cut that step out.

> 
3. Screen resolution - because I'm running it through a tv the native res is 1360x768 but this doesn't appear as an option so I'm stuck with 1024x768 atm

What kind of cable are you hooked up via?  Some TVs don't support their highest or native resolutions via certain cable types.  Also, if there is a closed source driver for your GFX card, have you tried it yet?

---

### Post by LowSky on 2010-07-08
1. Try to add the flder to the backend's storage group as superm1 said.

2. you may require libdvdcss, to play encrypted DVD's, you can get instructions from here:
[https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs](https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs)

3. We need to know your video cards model, if its nvidia or ATI getitng the right resolution may be as simple as using the proprietary driver and setting the resolution from their application. If it is something else it might need a bit more finese.

---

### Post by itlarson on 2010-07-09
Sorry to break the news, but linux dvd playback is fairly broken.  Vlc is your best bet, but I've found disks it cant play either.  All this isn't the fault of linux, but of the content providers and their endless attempts to thwart piracy.

---

