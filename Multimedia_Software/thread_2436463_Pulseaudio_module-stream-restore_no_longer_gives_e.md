---
title: "Pulseaudio module-stream-restore no longer gives expected behaviour"
date: 2020-02-06
forum: Multimedia Software
---

### Post by joebuntu99 on 2020-02-06
Having upgraded from 19.04 to 19.10 my audio streams no longer restore as expected when my bluetooth sink is connected.

I have the pulse audio module-stream-restore loaded with defaults but it does not provide the behaviour I enjoyed previously.

An experiment to demonstrate:

With bluetooth speaker connected I have 3 audio output streams: mpd, firefox, vlc.
Using pavucontrol I send mpd to bluetooth, firefox to onboard audio, vlc to onboard audio.
I disconnect the bluetooth speaker.
As expected mpd is now sent to onboard audio.
I reconnect the bluetooth speaker.
All three output streams are automatically sent to bluetooth speaker.

Here the expected behaviour given the setup is that mpd is "restored" to the bluetooth speaker but vlc and firefox remain at onboard audio.

Further experimentation shows that upon changing the "fallback output" in the pavucontrol output tab all audio streams are switched to that output. This is also unexpected behaviour and not previously the case.

It has been suggested that the fallback table is being ignored. My research suggests that the stream-restore database should be handling this behaviour as I expect.

I have removed the contents of ~/.config/pulse/ but to no avail. I do not know where the fallback table or stream-restore database is located or how they are built.

Any help would be appreciated. Thanks.

I have previously posted about this issue [here]("https://ubuntuforums.org/showthread.php?t=2436438")

---

### Post by coffeecat on 2020-02-06
Duplicate. Thread closed. Please do not cross-post. 

This is not a multimedia software question. Please see the strapline for the Multimedia Software sub-forum. Your thread in General Help is in an appropriate section.

---

