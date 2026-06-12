---
title: "Need help recording streaming audio"
date: 2010-03-09
forum: Multimedia Software
---

### Post by mbrett on 2010-03-09
Hey-

I'm running Dell's Netbook Remix on a Dell Mini 9. I want to record Wolfgang's Vault shows through Audacity or GNOME Sound Recorder. When I use either, I only get sound from the mics. I can't record through the sound card. 

Anyone with any answers?

Mike

---

### Post by inobe on 2010-03-09
there's an app called streamripper you could use.

---

### Post by mbrett on 2010-03-10
Thanks for the tip. Looks like a great app. Unfortunately, it can't record Wolfgang's Vault streams. Don't know why.

From what I read on the web, Audacity is the way to go. That's how I record it from my desktop. The reason I want to use my netbook is that it can pull the stream at 192, while my Vista desktop pulls it in at only 40. Big difference.

Again, let me know if you have any further ideas.

---

### Post by mbrett on 2010-03-12
****Bump, bump.

Anybody with any ideas? Would very much appreciate. 

Thanks ever so much,
Mike

---

### Post by mocha on 2010-03-12
That site probably uses some method to prevent capturing directly from a URL, however Pulseaudio makes this kind of recording easy.  After playing the stream, go into the pulseaudio volume manager and move the playback stream to the "monitor of ..." sound device, then you can use audacity or arecord or whatever and it will record that stream.  You need to get used to the ins and outs of pulseaudio, then you'll be able to master any kind of recordings.

---

### Post by tgalati4 on 2010-03-12
If it's a standard mp3 stream, then you can sometimes find the source URL by clicking on View-->page source (Control-U) during playback and look through the html code and see if you can find the actual streaming address.  Then cut and paste that into streamripper.

Another technique is to use wget:

wget URL_of_stream_I_want_to_record_so_badly_that_Im_going_insane

It will then create a file with the actual stream link embedded in it.  Cut and paste the actual source URL into streamripper.

---

### Post by mocha on 2010-03-12
The particular site the OP is talking about looks like they are using a flash music player probably via RTMPE or something equally nasty.

---

### Post by tgalati4 on 2010-03-13
I checked out the vault.  I listened to a .38 special concert from 1985.  I saw them in concert in 1982.  Brought back memories.

The site uses a Flash 9 player/streamer.  You can capture the flash stream, but that's not helpful.  

Recording from pulse looks like your best bet.

Mixboard recordings are OK.  The sound on the mixboard is set to normalize the house/stadium sound which is usually quite bad.  It makes for tough headphone listening.  If you were at any of those concerts, you probably didn't pay attention to the sound quality--because it was so loud to begin with.

---

