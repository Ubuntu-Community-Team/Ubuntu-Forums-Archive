---
title: "How to include the seektable in an mpeg2 recording?"
date: 2011-01-23
forum: Mythbuntu
---

### Post by fimbar on 2011-01-23
[FONT=Verdana]Hi,[/FONT]
  
  [FONT=Verdana]I’m using MythTV 0.24 and can quite happily view my MythTV recordings via my media streamer (NETGEAR NTV550). The quality is great and life is good. However I am unable to ffwd or rewind with any accuracy; when I stop ffwding or rewinding the video will jump to some random place in the recording. From what I’ve read this is because there is not “seektable” in the recording itself, it is still inside the MythTV database.[/FONT]
  
  [FONT=Verdana]So, my question is, how can I include the seektable contents in the recording itself so ffwd and rewind work properly? I’ve tried using nuvexport but it messes up the aspect ratio, takes forever to run and the quality is terrible. It used to work just fine in previous versions until they removed the –-transcode export_prog.[/FONT]
  
  [FONT=Verdana]Or maybe my question should be; how can I make ffwd and rewind work properly when using something other than the MythTV Frontend to view the recordings?[/FONT]
  
  [FONT=Verdana]Many thanks in anticipation.[/FONT]

---

### Post by fimbar on 2011-01-26
No one able to help me? :(
 
Does anyone else have trouble with ffwd and rewind when viewing MythTV recordings on a streamer? Maybe it's my streamer rather than a seektable problem?

---

### Post by bcg30506 on 2011-01-26
I cannot say for sure, never having used a media streamer, but I think most of them require H264 to stream properly.  It may be that the device doesn't support seeking in an MPEG2 file.  You may need to run a transcode user job on your recordings and stream those?

---

### Post by fimbar on 2011-01-26
> **bcg30506 said:**
> I cannot say for sure, never having used a media streamer, but I think most of them require H264 to stream properly. It may be that the device doesn't support seeking in an MPEG2 file. You may need to run a transcode user job on your recordings and stream those?
 
[SIZE=2]Thanks for the reply.[/SIZE]

[SIZE=2]Well, I'm very much the novice when it comes to containers and codecs etc. I thought I read that with MythTV the seektable is stored in an SQL Table for an mpeg2 recording and without the seektable (also if the seektable gets corrupted) then the MythTV front-end can't ffwd or rewind. My assumption is that the same would apply to my streamer? But as I say, I'm a novice and may be talking rubbish.[/SIZE]
 
[SIZE=2]I've no issue with the prospect of transcoding, the only issue I've had is I can't get nuvexport to "fix" the video (to allow ffwd and rewind) without screwing up the aspect ratio. All my recordings are 16:9 but they come out as 4:3. My TV then tries to stretch them back to 16:9 and they look dreadful. Plus the transcoded video is all pixelated and "blocky". So, it's a toss up between a beautiful picture but no rewind/ffwd and a stretched dreadful picture that I can ffwd or rewind to my heart's content! :lolflag:[/SIZE]

---

### Post by klc5555 on 2011-01-26
I don't know how you've got nuvexport set up to process your recordings, since there are a lot of possibilities.

 But regardless, you can force nuvexport to output to a particular aspect ratio, either at the command line when the script is invoked, or, more simply by using a  .nuvexportrc in your home directory (or a nuvexportrc -without the period-  in the directory "/etc"), which includes the line:

force_aspect = 16:9

See the nuvexport wiki page at: [http://www.mythtv.org/wiki/Nuvexport](http://www.mythtv.org/wiki/Nuvexport)

---

### Post by fimbar on 2011-01-28
> **klc5555 said:**
> I don't know how you've got nuvexport set up to process your recordings, since there are a lot of possibilities.

 But regardless, you can force nuvexport to output to a particular aspect ratio, either at the command line when the script is invoked, or, more simply by using a  .nuvexportrc in your home directory (or a nuvexportrc -without the period-  in the directory "/etc"), which includes the line:

force_aspect = 16:9

See the nuvexport wiki page at: [http://www.mythtv.org/wiki/Nuvexport](http://www.mythtv.org/wiki/Nuvexport)

Thanks for the pointer. Can't remember whether I ever tried the force_aspect option. I tried so many things I can't remember what I tried and what I didn't try.

What export_prog do you use? "transcode" used to work fine but they removed it. :(

---

### Post by BicyclerBoy on 2011-01-28
What do you mean by streaming from your media streamer (netgear)?
Are you streaming from the myth backend 'server' ?

All recordings made by mythtv have a seek-table.
Mythtv uses mpeg2-ts for recordings from tuners (this what tuners output).

Mpeg2-ts is ideal for streaming because playback can stop start anywhere (on key frame).
Mpeg2 PS is not the same as mpeg2-ts.
Mpeg2 & 4 PS can be re-arranged (somehow) to start playing before file is read completely.

AFAIK .mkv, & the .nuv from mythtranscode, seek okay if seektable is regenerated using mythcommflag or mythtranscode.

---

### Post by fimbar on 2011-01-28
> **BicyclerBoy said:**
> What do you mean by streaming from your media streamer (netgear)?
Are you streaming from the myth backend 'server' ?

All recordings made by mythtv have a seek-table.
Mythtv uses mpeg2-ts for recordings from tuners (this what tuners output).

Mpeg2-ts is ideal for streaming because playback can stop start anywhere (on key frame).
Mpeg2 PS is not the same as mpeg2-ts.
Mpeg2 & 4 PS can be re-arranged (somehow) to start playing before file is read completely.

AFAIK .mkv, & the .nuv from mythtranscode, seek okay if seektable is regenerated using mythcommflag or mythtranscode.

Hi BicyclerBoy,

Sorry for not explaining myself very well.

Yes these recordings are made using the mythtv backend using a DVB-T tuner.
So, MythTV records my TV programmes and then I want to view these programmes on my NETGEAR streamers.
Currently I'm not doing any sort of transcoding of the recordings. They  are "asis" although I have used mythlink to present readable filenames to my streamers.

On my streamers I can start and stop the recordings ok and the picture quality is great. It's when I try and ffwd through adverts for example that I get the problem. Once I press the play button to resume playback the recording "jumps" to some random place (+/- a couple of minutes from the moment I hit the play button). This often means I miss the start of the programme or it jumps me back into the adverts again.

I don't see these random jumps when viewing other media files (DVD rips etc) so I don't ***think ***it's a problem with the streamers.

I'm thinking my problem is the seektable (which allows proper ffwd and rewind) is not stored in the recording itself but is still inside the MythTV database (which obviously my streamers don't know about). But as I've mentioned, I'm a total noob and am clutching at straws as to the cause of this issue.

So are you saying that it should work and so my problem is not what I think it is? :confused:

---

### Post by BicyclerBoy on 2011-01-28
You are correct as far as I understand.
The seek-tables are in the database.

I did not understand why you were/are using NETGEAR streamers.
(& I still don't but that's not your fault)

AFAIK myth backend is an UpnP server.
[http://www.mythtv.org/wiki/UPnP](http://www.mythtv.org/wiki/UPnP)

---

### Post by fimbar on 2011-01-29
> **BicyclerBoy said:**
> You are correct as far as I understand.
The seek-tables are in the database.

I did not understand why you were/are using NETGEAR streamers.
(& I still don't but that's not your fault)

AFAIK myth backend is an UpnP server.
[http://www.mythtv.org/wiki/UPnP](http://www.mythtv.org/wiki/UPnP)

I'm using streamers for all the reasons people don't use HTPCs. If your question is why did I choose NETGEAR as opposed to another brand, then the answer is not quite so straight forward. ;-)

Thanks for the tip about UPnP

---

### Post by BicyclerBoy on 2011-01-29
So they (NETGEAR item) can be UPnP clients (& servers) ?

Some of the TVs work okay with Myth. Still some file formats that give problems AFAIK

---

### Post by fimbar on 2011-01-29
> **BicyclerBoy said:**
> So they (NETGEAR item) can be UPnP clients (& servers) ?


Only one of them can (the NTV550), the rest don't support it.

I read that I can transcode to .nuv which does embed the seektable into the recording. Trouble is, my streamers don't support .nuv files :(

Ho hum.

---

### Post by BicyclerBoy on 2011-01-29
AFAIK .nuv nuppelvideo container is not to dissimilar to mpeg2-ts & mkv.
Don't think the seek-table is in the file, just the indexing is very well thought out.

I would think mpeg2-ts is an ideal container for streaming as this was designed for the task.

MythTV recordings from dvb-t tuners are mpeg2-ts.

---

### Post by klc5555 on 2011-01-29
> **fimbar said:**
> 

What export_prog do you use? "transcode" used to work fine but they removed it. :(

Yes, the newer the mythtv release the less generally useful it seems to be. I prefer mencoder to ffmpeg. It may take longer but I find the output to be higher quality at the same settings. Just my opinion.

---

### Post by BicyclerBoy on 2011-01-29
Mencoder & ffmpeg do not have the same parameters so to compare you would need the same bitrates etc.

The whole MythTV transcode process seems to have been overcome by the increased demands of HD etc.

But I think the reality is not that bad. AFAIK MythTV devs could be planning a different approach using complete externally scripted tools.
There is a userjob script for HD lossless cutting.

Myth internal tools are not able to lossless transcode/cut H264 (mpeg4/10).
Mytharchive cuts then transcodes so fails for H264.
mythtranscode does not work with H264.

The biggest problems are not with the MythTV 'tools' but with:
ffmpeg  latm aac just solved 
Avidemux2 latm aac no support.
ProjectX   H264 ?  latm_aac ?

---

