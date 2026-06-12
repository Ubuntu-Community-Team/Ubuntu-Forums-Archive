---
title: "How to Create a &quot;Virtual Microphone&quot; for Google Meet or other software"
date: 2020-04-26
forum: Multimedia Software
---

### Post by andrew_howlett on 2020-04-26
Hi everyone,
Someone asked how to do this in 2016 but the thread is closed. I found bits and pieces of the answer in other posts, but here is my solution all put together in case someone else has the same objective.
I want to pipe background music from an mp3 file or maybe youtube to a google meet (used to be called hangouts). In theory this should be easy using pavucontrol but the old desktop computer I'm using doesn't have a microphone. If google meet doesn't see a microphone then it automatically mutes all audio. The easiest solution is to plug an old microphone into the microphone port on the back of the computer but I didn't have an old microphone. So here is the software "recipe". This is done on a clean Ubuntu 20.04 Desktop install with pavucontrol installed.

1. Start pavucontrol, firefox or chrome, whatever software is playing the music - lets say rhythmbox. Log in to the meet and start your background music.

2. Go to pavucontrol and check the configuration tab. There should be one sound card. If no speakers or microphones are connected then it should say Profile: Off.

3. Google Meet will mute the microphone if it can't find a microphone device. This prevents any sound from playing, even if we try to stream something from another sound source on the PC.  It is necessary to trick Google Meet into thinking that a microphone is present. We do this by installing the ALSA loopback device. This creates a virtual sound card with a virtual micophone. From a superuser terminal use this command:

# modprobe snd-aloop

4. Go back to pavucontrol. Under the configuration tab there should now be a second built in sound card. Change the new sound card's profile to analog stereo input. When you do this google meet should automatically detect the fake microphone and unmute your audio. So go to your meet, make sure audio is unmuted.

5. Go back to pavucontrol. Check the playback tab. The level meter should show sound generated from your sound source. That's good. Leave it alone.

6. Change to the Recording tab. You should see "Chrome input: RecordStream from" at the left side (or firefox input, depends which browser you use for meet). On the corresponding right side change the source to Monitor of Dummy Output.

7. That's it, 

It is also possible to set the configuration of the second sound card to Analog Stereo Duplex then set the recording source to Monitor of Built-in Audio Analog Stereo. But AFAIK google meet doesn't do stereo.

---

