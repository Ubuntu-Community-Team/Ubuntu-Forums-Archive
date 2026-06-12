---
title: "How to set up streaming sound server"
date: 2010-06-19
forum: Multimedia Software
---

### Post by tdn on 2010-06-19
One of my friends happens to be a Mac user. When he plays music in iTunes on his Mac Book, he can select that the sound should be played from the laptop speakers or from his remote speakers (i.e. his hifi stereo connected to an Airport Extreme wifi access point). If he chooses to play using the remote speakers, iTunes will stream sound via wifi to the Airport Extreme, which will then output to the hifi stereo speakers.

So, my question is, can I do something similar with Ubuntu/Kubuntu?

I have a setup like this:
 * I have three laptops running Kubuntu 10.04, Ubuntu 10.04 and Ubuntu Netbook Edition 10.04.
 * I have a server (fit-PC) running Debian Lenny connected
All machines are connected to my local wifi network.
The server is connected to some good speakers.

So, what do I need to install/set up on the server and the clients in order to have, say, mplayer, stream sound to the server which will then output it through its sound card?

---

### Post by xzero1 on 2010-06-19
I believe there is a way to do it with pulse audio. A quick and dirty method with ffmpeg,mplayer:

Sending machine:
```
ffmpeg -i MP3FILE.mp3 -acodec copy -vcodec none -re -f mp3 udp://192.168.0.77:1234
```

Playing machine:
```
mplayer udp://192.168.0.22:1234
```

Of course, you must change the mp3 filename and address for your network. To initialize, start the sending command first as mplayer will timeout if nothing is being sent. Give mplayer time for the initial sync. You can use a similar method with video!

I would suggest you keep your volume down until you feel comfortable that this method works well for you.

---

### Post by sandy8925 on 2010-06-20
I think you can also use vlc for something like this. use vlc on one of the laptops to stream audio/video. then start vlc on the server and point it to the correct address and it should start playing the streamed video. this obviously isn't what you wanted because you'll have to walk over to the server and start vlc each time you want to play something on the server.

---

