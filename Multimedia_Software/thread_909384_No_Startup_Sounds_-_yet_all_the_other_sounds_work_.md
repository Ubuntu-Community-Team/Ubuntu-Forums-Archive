---
title: "No Startup Sounds - yet all the other sounds work fine!"
date: 2008-09-03
forum: Multimedia Software
---

### Post by andypeter on 2008-09-03
I have Ubuntu 8.04 64 bit installed...

About a week ago I installed Audacity.  It would not record.  I tried to fix it by going to "Preferences > Sound" and making some adjustments.  I must have goofed something up there or when I tried to put on PulseAudio in the terminal to fix the issue.  I am newer to Linux, thus my not understanding why I have no startup or shutdown sounds but yet I can play mp3's, play video with sound and my login screen gives a "bleep" noise like usual. 

What kind of information do you need to help me diagnose and fix this issue?

Thanks so much!!! :)

---

### Post by stoneage on 2008-09-03
I have the same issue. I haven't had logout sound since updating to Hardy, and yesterday the login fanfare stopped, but I still get the login screen 'boink' sound and all other sounds work well. Though I should add that sound is sometimes unstable. Occasionally it will log in to silence and I have to reconfigure(in a very minor way), the sound settings.

I have an SB Audigy soundcard and run it on ALSA, OSS, ESD and Pulseaudio(obviously not all at once - just whichever works).

---

### Post by eggdeng on 2008-09-03
> why I have no startup or shutdown sounds but yet I can play mp3's, play video with sound
This is because gnome uses the ESD driver whereas your multimedia apps will be using ALSA. If you go to System -> Preferences -> Sound, you will see there are distinct tabs where you can enable drivers: **Devices** (ALSA, OSS & co) & **Sounds** (ESD). On the Sounds tab, you should have ticked both checkboxes at the top and have chosen logout and login on the last two drop-down menus.

---

### Post by stoneage on 2008-09-03
(No luck here I'm afraid; used to run just fine on alsa, oss etc. Test works, but no system sounds)

---

### Post by andypeter on 2008-09-07
Thanks!  I was able to check the boxes in Preferences> Sound and on the Sounds tab get enabled ESD.  I am still not able to hear anything with Audacity when I try to play a file.  Is there some setting I am still missing?

Thanks a bunch for your help!

---

### Post by eggdeng on 2008-09-07
I haven't got Audacity installed but I imagine it's just a question of telling it what device / driver to use. You might find this helpful [http://www.guidesandtutorials.com/audacity-preferences.html]("http://www.guidesandtutorials.com/audacity-preferences.html")

---

### Post by andypeter on 2008-09-10
I don't know what's up, but I am still having sound issues.  I tried to create a startup sound file for when the system logs in.  The file plays and is in the wav format.  I select the file instead of "Login" and when I start up my system I hear nothing.  The only sounds I can use as login sounds are the ones that were placed on the system with 8.04 64bit.  What is going on?!  

Can anyone help?  Thanks.

---

### Post by andypeter on 2008-09-10
> **andypeter said:**
> I don't know what's up, but I am still having sound issues.  I tried to create a startup sound file for when the system logs in.  The file plays and is in the wav format.  I select the file instead of "Login" and when I start up my system I hear nothing.  The only sounds I can use as login sounds are the ones that were placed on the system with 8.04 64bit.  What is going on?!  

Can anyone help?  Thanks.

Okay, I figured it out after trial and error.  As it turns out, when you save a file with audacity, if you type in hero.wav and then select the format as wav then it saves the file as "hero.wav.wav"  Which is not very smart, but anyway, when I just typed in "hero" and saved it as a the format wav, everything worked!  Wow that was frustrating!!!

Thanks everyone for the help!

---

