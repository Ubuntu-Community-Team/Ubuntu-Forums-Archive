---
title: "VLC - Take in RTMP stream, kick out multicast broadcast?"
date: 2017-04-04
forum: Multimedia Software
---

### Post by Roasted on 2017-04-04
Hi friends. I'm working on a project and beginning to do some digging on the nitty gritty. I'm still in testing mode and feeling out each possible scenario to see what will work best for our environment. 

This is for a school, particularly morning announcements. OBS Studio is the obvious go-to, so we're pretty sold on that so far. OBS works great but I'm concerned about scaling. So far our major concern (particularly for the larger buildings) is network traffic. Our entire infrastructure supports multicasting, so we're interested in testing that out to see where it goes from here. So far I have the rough details worked out with (let's call it) "option A", which is OBS streaming to an Nginx/RTMP load balancer with the clients pulling from Nginx/RTMP. But in this case, I'm trying to rough out the details of "option B" by leveraging multicasting, then compare in the end to see what fits best.

The catch is, the typical method with OBS is to leverage Nginx + RTMP. This works, but again looking to utilize multicasting for this option. If I throw Nginx + RTMP on this OBS rig, it's very TCP oriented, and doesn't speak the multicast language. OBS users do however have the option to record to a URL within the OBS recording options. If I record to URL and select a multicast address, I can pick up that address over VLC on a client system. There's one snafu: If I record to URL, I cannot simultaneously record to file as well. It's one or the other. This eliminates our ability to record to file + record to URL at once, which would give us the capability to not only multicast, but archive the videos so folks can watch back announcements in the future (which is a requested feature of our staff). 

I'm curious if I could simply put a second box with Ubuntu and VLC in place. In my mind this is what I envision: 

Box 1: OBS/Nginx/RTMP
--Box 1 puts out RTMP stream
Box 2: Just an Ubuntu rig with VLC, ffmpeg, or something similar.
--Box 2 pulls in RTMP stream from box 1, then turns around and re-broadcasts it to a multicast address
Clients: Connect to the multicast URL via VLC, thereby streaming the video from a multicast address

So overall, OBS/Nginx/RTMP >> RTMP's to Box 2 >> broadcasts that RTMP stream as UDP multicast address >> clients connect to multicast for viewing.

So in short, can I take in a stream with VLC and re-distribute that stream to a multicast address? Or perhaps this is a job for ffmpeg? If the answer is ffmpeg I wonder if I could write up a script to make this happen...

EDIT - Or maybe this makes more sense to just run VLC/ffmpeg/or something in the background on the OBS rig and record the stream from there? That could be an easy workaround... In that scenario it would look like just one box altogether.

--OBS spits out stream to multicast URL via record-to-URL option (this addresses multicasting desires)
--OBS streams its own RTMP stream locally and records via VLC/ffmpeg/or something similar (addressing preference to archive)
Eh? Thoughts?

---

### Post by TheFu on 2017-04-04
Perhaps if you record to a file AND push that file somewhere else using a different tool?
I do this all the time with TV recordings. My TV tuner outputs MPEG-TS streams based on a URL.  Recording a channel is just using wget with a specific URL for each channel. That isn't important.  The fact that it writes to a file is.

Then the file being written (as it is written) can be accessed by any other read-only process for any other purposes.  I've played with real-time transcoding the mpeg2-ts into h.264 and from a simple .mpg file into a .mkv container, for example.

This is a normal Unix technique. In fact, Adobe Flash used this for many years in their Unix implementations for video playback.

Anyway, those are my thoughts. Don't know if they can help or not.

---

### Post by Roasted on 2017-04-04
Part of the plan I didn't disclose was to host the archives on an nginx share that anybody internally can access. This would likely be controlled by a cron job that'll move the newly recorded file to the public share a few hours after we expect the recording to be done. Say if announcements are done by 8, by 10 it'll be accessible (or something). I'd likely just script it to append the date to the filename, i.e. ffmpeg -i rtmp://etc/etc Announcements_2017-04-04.mkv. Of course the actual command would need to be refined but that's the general idea in my mind.

The more I think about this, the more I think what's in my edit makes sense. I'll have to test it of course, but it stands to reason that I could just leverage one box for this. OBS running RTMP + Nginx, with the entire purpose of RTMP + Nginx being so ffmpeg can run against itself (the very same box) broadcasting the RTMP stream and record it, preferably to an mkv. But in OBS itself, within the actual recording settings, set that to a multicast UDP URL and boom, off to the network it goes to be multicasted.

Sounds good in theory (I think, anyway), but I'm gearing up with a test environment to see if these pieces fit into place.

---

### Post by TheFu on 2017-04-04
I always transcode in post, since I'm limited to a single Core i7 for OBS use and can't do the heavy transcoding to size-efficient files at the same time I'm creating content.  During content creation, file size is an afterthought and lower CPU use is most important.  YMMV, of course.

---

