---
title: "Sound - Reversing Audio Channels"
date: 2012-08-01
forum: Multimedia Software
---

### Post by vnv727 on 2012-08-01
Hello everyone,

I'm trying to figure out how to reverse the audio output on Ubuntu 12.04. I use headphones exclusively so it would be great to get this resolved. Basically, the left audio track is being sent to my right ear while the right audio track is being sent to my left ear.

I don't see any simple way to swap these channels in the sound panel. I'm essentially brand new to this OS, but liking almost everything so far. Once I can get the music player to recognize my music files from itunes in windows 7, netflix to work, and this all set, I'll be a happy user.

Anyway, if anyone knows how to accomplish this swap, I'd really appreciate the advice.

Thanks in advance for the help :D

---

### Post by vnv727 on 2012-08-02
So I figured it out with a lot of help from google, forums, and a bit of guesswork. Was actually really simple. Figured I'd write down what I did that worked for me. No clue if it would work for anyone else, but here ya go:

Open terminal
1) Type: "sudo nautilus" then hit enter, type in password when prompted and hit enter

2) Then go to file system > usr > share > pulseaudio > alsamixer > profile-sets and open "deault.conf" in the window that pops up from the "sudo nautilus" command.

3) Go to 

"[Mapping analog-stereo]
device-strings = front:%f hw:%f
channel-map = **left,right**"

and change to

"[Mapping analog-stereo]
device-strings = front:%f hw:%f
channel-map = **right,left**"

4) Save and close windows except for Terminal

5) Type "pactl exit" in Terminal and hit enter. (Unsure this is necessary but it seems to restart the sound settings/pulse.)

6) Check to see if the channels are swapped now with the system sound settings test.

7) Enjoy properly routed audio.

---

