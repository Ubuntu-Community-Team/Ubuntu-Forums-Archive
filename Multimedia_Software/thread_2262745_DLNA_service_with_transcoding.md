---
title: "DLNA service with transcoding?"
date: 2015-01-27
forum: Multimedia Software
---

### Post by kieran6 on 2015-01-27
Hi there

I've just spent the last few days ripping my hair out over this.

I've been running MiniDLNA for the past week or so with absolutely no problems. Just installed in from the official repositories, changed a couple of lines in the config file and it just works.

However, I'm unable to play some .MKV files that are encoded with FLAC.
I'm also having trouble playing .AVI files encoded with "MPEG-4 Video (DX50)" and "MPEG Audio Layer 1/2/3 (mpga)" - not sure if it's the audio, video or both for this one.
Same problem with .AVI files with "MS MPEG-4 Video v3 (DIV3)" with the same audio as the above AVI.
However, it had no problems playing MPEG-4 Video (XVID) on a different AVI with the same audio.

Anyway, I'm wanting a DLNA server that can transcode these files for me so I can play them on my smartTV. The problem is, I can't seem to find anything that wants to work in the current 14.04 version of Ubuntu Server (Trusty).

I've tried:
- Serviio - won't install unless I manually download java 8 from a ppa and then even after fixing that, throws errors that I can't find fixes for on google or the serviio site or forums
- Rygel - installed from official repositories, throws errors with the config files being in the wrong place, tried moving the config files and then it throws a new set of errors and just continuously causes me nightmares
- PS3 Media Server - installs nicely, runs fine, so far the nicest to work with, however, when it transcodes audio on 1080p videos it just plays an awful loud buzzing sound. There were no fixes for this I could find on google or their website

NOTE: I have ffmpeg installed from the PPAs since none of these seem to like the libav-tools that 14.04 uses instead of ffmpeg.

Basically what I'm asking is if there is a media server that actually works properly with Ubuntu 14.04, or if there is a way to make any of these work properly. I've tried everything I can and followed numerous guides and help threads all to no avail.

Thank you

---

### Post by TheFu on 2015-01-27
Plex Media Server does.  However, the transcode settings are less than easy to manage if it doesn't just work. I've been running Plex for about 6 months on 14.04.

No need to sign up for Plex account, btw.  You can setup a VPN and do everything remote without their service, if so incline. The VPN is much more secure, for obvious reasons.

I don't know whether it can handle flac or not.  Plex uses either ffmpeg or avconv - depends on what is available.  Also, don't know if those come with flac support in the default packaged versions. Could that be the issue with the other media servers?

---

### Post by ajgreeny on 2015-01-27
> **TheFu said:**
> Plex Media Server does.  However, the transcode settings are less than easy to manage if it doesn't just work. I've been running Plex for about 6 months on 14.04.

No need to sign up for Plex account, btw.
I also use Plex, but bear in mind that it is not open-source, if that is important to you.

It is free (of charge) so will cost you nothing, and as TheFu says, there is no need to sign up to the Plex Pass, which in UK costs £3.99 per month; it does give some extra facilities but for my use they are totally unnecessary so did not sign up to it, but even so it manages to serve any audio or video file that I have given it without a problem.

---

### Post by kieran6 on 2015-01-29
Thank you both for the replies, much appreciated. I downloaded and installed plex, and I've managed to successfully install it and add media to the library using the web interface. However when I access the media server from my TV none of the video files are playing any sound, and they're in much lower quality than the source files. I've looked through all the available settings I could find and found no options for transcoding or selecting video quality or anything like that and a couple of hours of google have returned nothing more than simple setup steps that I've already long since been through. There's also an excessive amount of "folders" to navigate through to get to anything such as 'unwatched' and 'recently aired' etc, but I don't think those are optional. I can live with those but I'm going to need to try find a solution to the sound and video quality issues.

---

### Post by TheFu on 2015-01-29
Every page has an "advanced" option.  Did you check there?

No sound?  I'd guess that your ffmpeg/avconv doesn't support flac. Did you check that?

Excessive is not the term I'd use for 2.  Select the content [Movies/TV/Videos], selected "Recently Added" - done.

You know, it wouldn't be too hard to create a tiny script to add AAC to every video file and shove that back into the mkv container.

Since the other DLNA servers are also having the same issue, have you considered that perhaps your ripping process is the issue?

---

### Post by kieran6 on 2015-01-29
> **TheFu said:**
> Every page has an "advanced" option.  Did you check there?

No sound?  I'd guess that your ffmpeg/avconv doesn't support flac. Did you check that?

Excessive is not the term I'd use for 2.  Select the content [Movies/TV/Videos], selected "Recently Added" - done.

You know, it wouldn't be too hard to create a tiny script to add AAC to every video file and shove that back into the mkv container.

Since the other DLNA servers are also having the same issue, have you considered that perhaps your ripping process is the issue?

Yeah I checked all the advanced options, couldn't find what I was looking for.
Not all my video files are encoded by FLAC, most of them are AAC or something similar and play natively on the TV without transcoding. They play fine with sound on other DLNA services, just not in Plex. However the files with FLAC that wouldn't load at all and just returned "File not supported" or "Audio not supported" messages would display video in Plex, just not the audio. I'm unsure if my ffmpeg supports FLAC so I will check that, either way though the AAC files aren't working.

Sorry, what I meant is excessive for my needs. I just want to browse Plex > TV > SeriesName > File but I don't mind the extra layer of folders.

As for the tiny script to add AAC to every video file, I'm not entirely sure how to go about doing that. As far as I'm aware I'd have to re-encode the files from FLAC to AAC which would take hours, if there's an easier way though I'd love to hear more.

I don't believe my ripping process is the issue. I have many different files from MKV, AVI, FLAC, AAC, you get the point. These all work perfectly on my laptop in VLC, and they work fine in the DLNA servers as long as the TV natively supports the codecs used (except for Plex in this case, in which none of them will play sound).

Thanks again for the help so far.

---

### Post by TheFu on 2015-01-29
First, you need to determine if ffmpeg on the system supports FLAC or not. I don't know how to do that - there is probably a way to see the compiled-in codecs. check the manpage. If it doesn't have the support, there isn't any hope to transcode from FLAC to something else until that is resolved. I suppose there was a reason to go with FLAC when the native AC3 is just a copy from most media?

Plex has profiles for every device which determines which files are transcoded and how. Those are buried under /var/lib/plex ...... deeply. If you can't find the one for your specific TV, create one. Look at the log file to see the name of the transcode file for the TV is necessary. I don't know the specifics, but i've had to create this file previously (about 2 yrs ago), so it is possible and does work - provided the transcoder can handle the input and output format.

To re-encode audio to a different format does not require re-encoding the video. Just copy the video, audio and any other files inside the container into a new file while adding the transcoded audio too. Further, MKV containers can hold multiple audio tracks which use different audio codecs.  They can hold multiple video tracks too and pretty much any other file you'd like to add. It is a very flexible container.  Some scripting will handle what you need, if you desire to add an AAC audio track to the container. It might be simple scripting if the input files are all the same type video/audio/subs in the same order inside the same container type. It will be more complex if not. Just look at the file track information to see where the video, audio, subtitles and other files are inside the container.  **mkvinfo** will do this for mkv files.  OTOH, if you insist on point-n-click solutions, then transcoding may be required.

I've added alternate audio tracks to some of my collection due to chromecast being picky and my Plex server running on a slow systeml; can't transcode even audio in real-time. Chromecast doesn't play AC3, it only likes AAC or mp3.  

Sorry I didn't look up each of the commands to accomplish these things. Knowing it is possible should be enough to find how from each of the tool help pages.

Tell Plex it is personal media and it won't bother with much organization.  Many media players support favorites, is that an option?

---

### Post by SeijiSensei on 2015-01-29
> **TheFu said:**
> First, you need to determine if ffmpeg on the system supports FLAC or not. I don't know how to do that - there is probably a way to see the compiled-in codecs. check the manpage.

```
ffmpeg -formats
```

FLAC has been a standard codec in mplayer and its derivatives for years.  It's included with the "avconv" fork of ffmpeg that Ubuntu ships as well.

Neither my LG nor my Sony TV will play anything encoded with FLAC.  I don't think my daughter's Samsung does either. It's especially annoying in the case of my LG, whose operating system is Linux-based.  At least it doesn't barf when presented with a Matroska file like my Sony does.

---

### Post by TheFu on 2015-01-29
```
$ avconv -formats |grep flac
 DE flac            raw FLAC
```

so the default avconv on 14.04 has it (checked 2 systems here). This means that the plex transcode file just needs to be told to do it for the TV.
BTW - "/var/lib/plexmediaserver/Library/Application Support/Plex Media Server" is the path were plex stuff begins.  Idiots, wasting so many characters for nothing.

[https://www.reddit.com/r/PleX/comments/2j5vbe/ac3_audio_on_chromecast_now_working_no/](https://www.reddit.com/r/PleX/comments/2j5vbe/ac3_audio_on_chromecast_now_working_no/) that says AC3 is supported on chromecasts now. I haven't tested myself.

---

### Post by kieran6 on 2015-01-29
Using ffmpeg -formats showed that my version does support FLAC.

It seems that plex does have a profile for my device. The log file shows "Mapped Client to Profile: Pansonic Viera 3D TV using header Panasonic MIL DLNA CP UPnP/1.0 DLNADOC/1.50."
I don't know where to find this profile if I need to edit it though, I could only find dlnaclientprofiles.xml or whatever it's called which doesn't contain this particular profile.

I certainly don't insist on point'n'click solutions though, or I wouldn't be using a terminal based operating system :P I just had no intention of waiting hours and hours for my files to encode. However your method of only encoding the audio seems viable as I'm sure that won't take too long, so I'd be more than happy to give that a go. Thank you for that.

I have to agree with the idiots wasting characters. Who hides a file in a horrible place like:
/var/lib/plexmediaserver/Library/Application Support/Plex Media Server/Plug-ins/System.bundle/Contents/Resources/dlnaclientprofiles.xml
It's bad enough that the filepath has spaces, let alone the insane length of it all.

Thanks again for the help

EDIT: Unfortunately a simple "ffmpeg -i movie.mkv -vcodec copy -scodec copy -acodec ac3 movie1.mkv" didn't produce anything playable. I tried playing with the channels and bitrate and such but that didn't make a difference. Will have to keep looking.

---

### Post by SeijiSensei on 2015-01-29
You could install mkvtoolnix and use mkvextract to separate out the video, audio, and subtitle channels (if any).  Recode the audio to something like AAC or MP3, then use mkvmerge to create a new Matroska file with the recoded audio.

---

### Post by kieran6 on 2015-01-30
I gave that a try using "mkvextract tracks movie.mkv 2:movie.flac"
All I got from that was "Error: failed to create the file 'movie.flac': (13) open file error.

I figured that meant that the movie file was opened by another program so I shut off all my dlna services and such and ran a lsof to make sure it wasn't in use by anything and that didn't help at all.
I couldn't find a single page on google with any reference to this error either. I'm starting to think ubuntu just doesn't like me very much.

I appreciate the response though, thank you for that

EDIT: after using "sudo apt-get purge mkvtoolnix" and "sudo apt-get install mkvtoolnix" I was able to finally extract the FLAC from the MKV.
I used ffmpeg to convert the FLAC to an AC3 and then used mkvmerge to make them back into a single MKV.
This gave the exact same result as directly using FFMPEG on the video file. Should I try converting the FLAC with a different tool? If so which one should I use?

---

### Post by TheFu on 2015-01-30
ffmpeg converts.
mkvmerge adds another audio track.

It is up to you if conversion is ok or if you want to keep the FLAC and add AC3 or AAC or MP3 audio tracks ... or all of them.  After all, you used FLAC for some reason, so why remove it?

---

### Post by kieran6 on 2015-02-02
After still not being able to get it working I decided to give up on plex and go over to the serviio forums to try get some help getting that working since the majority of posts I found said that was the one that worked best for them. Turns out all I needed to do was to get java8 and run the correct script, I was running the script labelled "serviio-console" thinking that was to start the nogui version for headless servers, yet I was meant to be running "serviio.sh."

Anyway the only small problem I had with that was that it wasn't doing subtitles (I watch quite a bit of anime so I need the subtitles as I speak very little Japanese) so I had to rebuild ffmpeg from the latest source so I could add libass functionality which serviio requires for subtitles. After that everything is working perfectly and I couldn't be happier, I added a script to run it automatically on startup so it just sits in the background as a daemon running for me.

Thanks again to everyone who helped me out in this thread, I greatly appreciate it.

---

### Post by FakeOutdoorsman on 2015-02-02
It should be:
```
ffmpeg -codecs | grep -i flac
```

Or even more specific:
```
ffmpeg -decoders | grep -i flac
```

Anyway, ffmpeg has native FLAC encoding and decoding support.

---

