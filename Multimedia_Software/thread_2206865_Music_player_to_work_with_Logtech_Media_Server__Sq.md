---
title: "Music player to work with Logtech Media Server / Squeezeboxserver"
date: 2014-02-21
forum: Multimedia Software
---

### Post by Keith_Beef on 2014-02-21
I'm losing patience with RhythmBox. I don't know exactly what the root cause(s) is (are), but two annoyances have crept in over the past couple of years.
[LIST=1]
[*]Any MP3 file I have gets big gaps during playback. The file might beging to play, the cursor moves along the time elapsed, but there will be portions from a few seconds to a few minutes where there is just silence. This also happens, though less frequently, with OGG Vorbis files.
[*]The app will just hang for no apparent reason.
[/LIST]

I tried increasing the buffer (I used gconf-editor to increase the value of the /apps/rhythmbox/player/network_buffer_size key), but this didn't cure the gaps. I don't have any good idea why the app would just hang, unless it is because my collection is getting quite big (by my terms, anyway) at around 5000 files. Updating the index takes a loooong time.

But my collection is on a ReadyNAS NV+ with the Logitech Media Server installed, so I can stream to a Logitech Squeezebox.

Now, I've seen threads on installing the Media Server on an Ubuntu computer, so as to stream to Logitech devices, and thought that I could maybe go the other way round. That is to say, keep the server as it is now and stream from it to a player on my Ubuntu computer.

I did some searching around, and didn't turn anything up.

Any ideas?

---

### Post by Keith_Beef on 2014-02-21
Something crossed my mind, so I tried it out&#8230;

I can get the Logitech Media Server to send out a stream (by going to [http://nas-xx-xx-xx.local:9000/](http://nas-xx-xx-xx.local:9000/) I get a control panel for the server) and then catch that and play it as audio through the Squeezebox. So I should be able to point any stream player at that same stream and hear it, right?

So I tried pointing Guayadeque at [http://nas-xx-xx-xx.local:9000/stream.mp3](http://nas-xx-xx-xx.local:9000/stream.mp3) (as per [Logitech's instructions]("http://wiki.slimdevices.com/index.php/Remote_streaming")), but I don't hear anything through Guayadeque. On the other hand, the Squeezebox plays the stream just fine.

---

### Post by Keith_Beef on 2014-02-22
[LIST]
[/LIST]
I thought that this would be relatively easy, and that I can't be the first person to want to set up a house-wide audio system.

Here's more detail of what I have available and what thought I'd be able to do.

Audio files are on a NetGear ReadyNAS NV+ running the following streaming services:
[LIST]
[*]Squeezecenter (Logitech Media Server)
[*]iTunes Streaming Server
[*]ReadyDLNA
[*]Home Media Streaming Server
[/LIST]

I wanted to control the server on the NAS to order it to broadcast a stream over the home network; then any device on the home network would catch that stream and decode it back to audio. As I understood it, this was the very point of UDP.

The NAS is connected to a hub, to which I could connect a Respberry Pi in order to get the files by CIFS and then stream them over the network, if I really need to go down that road (i.e., if it turns out to be impossible to control the servers on the NAS to get them to do what I want, and if VLC, XBMC or Myth turns out to be a better solution).

---

