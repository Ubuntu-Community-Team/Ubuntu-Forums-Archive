---
title: "Java Voice Recoring trouble (GStreamer)"
date: 2007-02-09
forum: Multimedia &amp; Video
---

### Post by borgena on 2007-02-09
We need to develop a cross platform voip application to simulate VHF and other navial instruments found on ships. The preffered platform for development is Java with gui build with QT (Jambi bindings). On the recording/mixing/playback I was hoping that we could use JavaSound as it's crossplatform and fast enough at least for 11khz 8 bit voice over ip.

We developed a Windows prototype version that worked fine and was testing on Linux (Ubuntu Edgy) when we ran into troubles. The main issue is that recording fails, it hangs on the query on the microphone. After goggling around I figured out that this has something to do with JavaSound using alsa directly and not Gstreamer. I guess alsa doesn't like to be pulled in two directions? When I test the application it sometimes works fine and sometimes just hangs. When it hangs the System->Preferences->Sound->Test Recording also hangs....:(

So my question is can this be done another way? Is there an SPI driver for JavaSound that used Gstreamer? Should I use the java bindings for Gstreamer? Is there any other alternative?

Please advice? This is really a show stopper for our cross platform application...:(

Thanks 

-=Børge

---

