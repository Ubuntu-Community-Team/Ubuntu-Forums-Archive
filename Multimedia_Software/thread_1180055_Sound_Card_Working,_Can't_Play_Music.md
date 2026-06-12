---
title: "Sound Card Working, Can't Play Music"
date: 2009-06-06
forum: Multimedia Software
---

### Post by Tsarevich on 2009-06-06
I have Ubuntu Jaunty installed. My soundcard is working properly because I can hear the default sound that comes on the login screen. But the welcome sound does not come out when I have logged in. I can not enlist ay soundcards by aplay -l until I append a sudo in the beginning, but the sound does not even come in root account. I cannot play music with Songbird. What do I do?

---

### Post by bryonak on 2009-06-06
Do you have sound in any other program?
Try playing a music file with Rhythmbox (the default sound app), a movie with the default video player and a youtube video with Firefox.

If they work, something's wrong with Songbird.
If none works, go to System -> Preferences -> Sound and make sure everything is set to AutoDetect or PulseAudio.
Also try to change your device to something that resembles your sound card, prefereably "Playback: xxx (PulseAudio)".

Try the mentioned programs again.
If none works, go to System -> Preferences -> Volume Control and try out the various devices.

If you still have no sound, enter this in a terminal:
```
sudo aptitude install paman paprefs pavucontrol padevchooser
```
This will give you dedicated PulseAudio tools to toy around... but please first try out the aforementioned things.



EDIT:
Could it be that your user is not in the audio group?
Go to System -> Administration -> Users and Groups.
Hit the unlock button, then double click your user, go to User Privileges and make sure that "Use audio devices" is checked.
Then close your user and click on "Manage Groups". Is your username checked in the pulse-access group?
After making these changes, you probably have to log out and back in.

---

