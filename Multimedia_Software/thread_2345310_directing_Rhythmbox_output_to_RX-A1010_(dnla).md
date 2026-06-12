---
title: "directing Rhythmbox output to RX-A1010 (dnla)"
date: 2016-12-02
forum: Multimedia Software
---

### Post by spraguejd on 2016-12-02
Ubuntu 16.04.   I have maximum RAM and loads of disc space. My machine is a  Toshiba Satellite with an Intel Core i7 processor. Pulseaudio-dlna makes  my Yamaha RX-A1010 (dlna) show up in sound output options.  Although it  shows  Rhythmbox playing into the dlna device there is no sound.  The same thing occurs with VLC.  I have also tried Columbine and Banshee with the same no sound result.  NOTE: The device is recognized and produces sound under Windows 10 (same machine with dual boot).  There are no error messages when I execute this enabling of dlna device.  My goal is to get free of Windows highly unstable file management in order play my music collection to a high quality sound/speaker system under ubuntu 16.04 with reliable file management.  I have been working at this some months but to no avail.  I am new to unbuntu but have a long history of working usefully with computers (I am an old guy).  I am not a programmer but the command line does not frighten me.  I am stumped.
All the players find and use the built in speakers easily.

---

### Post by slickymaster on 2016-12-02
*Thread moved to **Multimedia Software**.*

---

### Post by philhughes on 2016-12-03
I have no experience with pulseaudio-dlna, so cannot help directly with that. However, if you fail to get it working, an alternative approach would be to install a dlna server on the PC and control the music playing from the Yamaha. I have found minidlna (also known as Readymedia) to be a reliable server. For some reason minidlna doesn't show up in the Software Centre, but you can install it with:

```
sudo apt install minidlna
```

[https://sourceforge.net/projects/minidlna/](https://sourceforge.net/projects/minidlna/)

---

### Post by spraguejd on 2016-12-03
Thanks Phil.  I have tried minidlna as well but run into the same problem.  That you noticed the post encourages me to presson.

---

### Post by philhughes on 2016-12-04
That seems strange. My understanding (which may well be wrong) is that when using minidlna (or a similar server), minidlna is just telling the client (ie the Yamaha) what is available on the server to play, and the the Yamaha then just loads the file over the network and all the processing is done on the Yamaha. In other words, in this situation, the Ubuntu sound system is not involved at all. Could you see the files on the PC from the Yamaha?

If my understanding is wrong, hopefully someone will jump in and correct me.

---

### Post by spraguejd on 2016-12-04
Phil:
The RX-A1010 has quite a bit of logic  built in.  One option "straight" essentially disables all local amplifier controls and passes all sound control to the audio player.  This does not enable sound to get to my speakers.  I have run through all the other options on the amp with Rhythmbox playing to the (now silent) RX-A1010 as evidenced in Sound setting or with pavucontrol.  Never get a peep. I think software on my PC must be somehow blocking the signal transmission.  This is reinforced by the ability to stream from windows 10 on this same machine.  I have also tried installing subsonic which comes highly recommended by a tech savvy person but so far I have not succeeded in installing it under linux.  Since subsonic includes library management it might provide a solution in Windows but I have not managed to install it there either.  All my experience with windows and a music library is that the file handling is more often compromised than not.  Subsonic might repair that.  I have lost my library of about 80 gigs of music and will need to reinstall all the cids.  So I am hoping to get the linux player running and then reinstall my music.  (These are old guys problems.)  Somewhere there is a switch, a line of code that needs altering, whatever . . . Thank you.  ---- John (old guy)

---

### Post by spraguejd on 2016-12-04
Phil:
The message from the RX-A1010 is "no content".  When it has worked successfully in the past the playing content is identified and can be displayed on the TV - Samsung.

---

### Post by philhughes on 2016-12-05
I have seen this sort of thing before, where an Android app wouldn't see any content from Windows Media Player, even though other clients could. DLNA interoperability seems quite temperamental.

However, you seem to have tried a number of approaches, so I wonder whether it is something else? The only thing I can think of is a permissions problem on your directories or files. Other than that, I can think of nothing else. Good luck!

---

### Post by spraguejd on 2016-12-05
Phil:
I will investigate the permissions problem as a promising suggestion.  It will probably take me a few days. Thanks again.
--- John

---

