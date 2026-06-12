---
title: "VLC - Stream almost real time, an easier way..."
date: 2007-11-26
forum: Multimedia &amp; Video
---

### Post by human-ness on 2007-11-26
I understand that VLC has been covered very well here in the Ubuntu forums.  However, I have found that streaming live via your MIC is not that easy for some people, depending on what hardware they have and how VLC handles it.

Here is a way, to stream via your microphone or line in, without having to address the hardware directly.  (Hardware meaning your soundcard.)

You will need:

gnome-sound-recorder (Audacity does not cut it in this case, as it uses multiple temp files)

sudo apt-get install gnome-sound-recorder

VLC

sudo apt-get install vlc

Instructions:

Open gnome-sound-recorder - This will automatically create a temp file in your /tmp/ directory, that sound recorder will use, while recording on the fly.  The file will look something like this gsr-record-Untitled-12743.MRNJ2T except it will have different letters and numbers at the end.

Change your recording mode in Sound Recorder, to MP3.  I found that ogg was not working on the client machine, but MP3 was.

Open VLC, blow that sexy little program a kiss and then click:
  File
  Open File
  Browse

Now click on FILE SYSTEM in the panel to the left, then in the selection area, double click TMP.  You should now see the temp file that I spoke of earlier, looking something like this gsr-record-Untitled-12743.MRNJ2T.

Double click it.

Now that we have selected the temp file that we will soon be streaming, we need to configure how we are going to stream it.  I use this for personal networking streams, so I choose UDP.  You can use whatever it is that tickles your fancy.  Streaming has been covered before, but I will cover UDP yet again, so that I can finish showing you the way for streaming a temp file.

Tick on Stream/Save and then click the Settings button.

Tick on UDP and then type in the IP address, of the computer that you are going to be streaming to.  In my case, it's 192.168.1.102...

Leave the port as 1234 or change it to what you wish.  It matters not as long as you have that port firewalled.  (I am talking in the case of a private lan stream)

Have you setup your streaming properties?  Well done.

Now listen carefully people, or you will start to wonder why there is nothing coming from your client computer.

Click OK once!  Do NOT click OK on the next page (the open file page) until we have done the last step for Sound Recorder.

Now press record on Sound Recorder, wait 5 seconds into recording and then Click OK on the last page open in VLC.

Your Server computer, for VLC is now streaming the temp file of Sound Recorder with a 5 second delay.  (5 secs leaves room for small mistakes in the stream, 10 is probably better, but I have had no problem at 5)

Now, you are not only streaming in almost real time, from another source, but you are recording it with Sound Recorder on your host machine as well.

If you record in MIX mode, you can record everything you like at the same time, as well as streaming it to a client computer.

If you have any questions, please ask and I will do my best to answer them.

As far as I know, this way of streaming almost real time has not been covered, so feed back would be much appreciated.  I won't be happy until I know that I can get this working, for even the most un-savvy computer human.

Cheers fellow Linux humans.

---

### Post by human-ness on 2007-11-26
I have done some testing on some lower end computers.  They seem to have problems when it comes to syncing, sometimes leading to the stream to stop after a while, because the recording/encoding isn't quick enough to keep up with the stream.

I have experimented with this problem and so far have had success.

If you are running a low end machine, when you click FILE > OPEN FILE > STREAM/SAVE, also be sure to tick CACHING on and then change the 300 to 1024.  I'm not sure if the 300 represents memory used or milliseconds.  I am thinking memory, because 1024 is working perfectly on my 700MHZ laptop with 192MB RAM.

Now that you have done the caching, go into the STREAM/SAVE settings, and set AUDIO CODEC in TRANSCODING OPTIONS, to mp3.  Set the BITRATE kb/s to 32 and your CHANNELS to 1.

I use MPEG TS for my encapsulation, but you can have a fiddle with that and see what works best for you.

Now click RECORD on your Sound Recorder, wait 10 secs and then click OK on both pages that are open in VLC.

Happy streaming.

---

