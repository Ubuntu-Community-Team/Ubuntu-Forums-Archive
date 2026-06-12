---
title: "Streaming Audio over Network for any content"
date: 2010-09-17
forum: Multimedia Software
---

### Post by gurinderc on 2010-09-17
Hi All,

I have a desktop (Lucid) which is connect to my Home Theatre System and advanced sound system and working without any issue.

Now I got a laptop (Lucid) which I usually use to watch streaming contents (Youtube and all) and play music (local and internet radio). I like to stream all of my audio (not video) to the Deskop so I can use my Home Theatre speaker for the purpose.

I was wondering if this is possible by any how using ALSA/esound or something else?

Any question on setup, please ask.

Many Thanks

---

### Post by nothingspecial on 2010-09-17
Is the music on your laptop or desktop?

I mean, are you wanting to control the desktop with your laptop?

Or do you want to send the music from your laptop to your desktop?

Or both?

There are loads of ways to do this, for example, if you want to play the radio through your home theatre pc, but start and stop it with your laptop then

```
ssh -X username@ipaddress_of_pc
export DISPLAY=:0.0
mplayer url_of_radio_stream
```

That`s just one way of doing one of the things I think you might want to do. If the music is on your laptop then you can mount your laptops music folder to your pc or use vlc to stream it over ssh or use mt-daapd to share your music. I just need to know what exactly you want to do, and specifically, where the music is.

---

### Post by gurinderc on 2010-09-17
Hello Sorry for the confusing question - 

Scenario 1 - 

Playing Movie or Youtube Video on Laptop, I like its Video to be remain on my Laptop but Audio on my Media Center Desktop.


Scenario 2 - 

Playing audio files on my Laptop Harddisk and output is from Media Centre Desktop.

I don't want to use VNC or any other mechanism of remote desktop. Idea is have a sound server running on Media Centre Desktop which accept audio stream and play it with default output device. So in all I'm looking for ALSA to dispatch my Audio over the network rather then trying to play it locally. And the server running on remote Media Center accept this stream and play it using ALSA with default output device.

I hope I'm clear this time.

Thanks

---

### Post by Takkat on 2010-09-20
Isn't that exactly what pulseaudio is supposed to do? 

In **paprefs** RTP/Multicast settings you just enable 'receiver' or 'sender'. This would send audio output from your soundcard via your LAN/WLAN to any receiver. Worked somehow on my systems but sound sent from desktop to the nettop was awfully distorted :( (most likely because of my wrong settings).

Good luck

---

### Post by corcomp84 on 2010-09-20
I thought tangerine was going to be promising.. it was a daap server that allowed you to stream music from a computer to any music player that supported daap, like banshee or rythmbox.. only problems I had was stability issues.. But once it was running it worked great.. I used it with 4,000 songs with limited problems.. U can down load it right through synpact manager..

---

### Post by corcomp84 on 2010-10-07
I think the simplest way to do this would be to use either a blue-tooth music adapter and send your music straight to the stereo directly.. or use your head phone jack with a wireless FM transmitter.. I would assume you could share your sound card over the network but that would be a big pain.. I was just looking up the Belkin Bluetooth Music Receiver, and it might work for you.. I also know that if you don't have a blue tooth adapter the one that Wal-Mart has works perfect on Ubuntu 10.04.. If you want the make and model let me know..

---

### Post by Takkat on 2010-10-07
> **corcomp84 said:**
> I think the simplest way to do this would be to use either a blue-tooth music adapter and send your music straight to the stereo directly.. or use your head phone jack with a wireless FM transmitter.. I would assume you could share your sound card over the network 

Bluetooth like other network streaming solutions has the disadvantage of some immanent delay thus limiting all those solutions for games or video appliances. FM-transmitters have a more or less poor sound quality and get easily disorted by electric smog.

One additional way to get your music to your stereo is to set up an internet radio stream (e.g. using Icecast) or a UPnP stream to an internet capable receiver (are not too expensive). For a summary of solutions including Bluetooth, and support for Apple AirTunes there is an easy to use GUI: check out stream2ip at [https://launchpad.net/stream2ip](https://launchpad.net/stream2ip).

---

