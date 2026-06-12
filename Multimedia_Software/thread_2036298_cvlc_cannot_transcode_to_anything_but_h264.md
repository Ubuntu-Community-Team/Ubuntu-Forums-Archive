---
title: "cvlc cannot transcode to anything but h264"
date: 2012-08-01
forum: Multimedia Software
---

### Post by richpowell on 2012-08-01
Hi all,

I'm using cvlc to transcode and stream (http) from a HVR-1250 capture card out to the other computers in my house. The streaming works perfectly if I avoid transcoding and just stream it as it's received. The problem is that HD is ~15mbit which is just too much. I would like to transcode it down to ~6-8mbit.

The problem I'm having is that cvlc seems to think I don't have any codecs available no matter what I try and transcode to. Here's an example commandline I give to cvlc:

```
cvlc -vvv channels.conf -I http --http-host=xxx.xxx.xxx.xxx --http-src='/usr/share/vlc/lua/http/' --sout-keep --sout '#transcode{vcodec=mp4v,acodec=mpga,vb=3000,ab=256,venc=ffmpeg{keyint=80,hurry-up,vt=800000},deinterlace}:std{access=http,mux=ts,dst=xxx.xxx.xxx.xxx:8181}'
```

When I run this I receive the following errors in the output:

```
[0x7f9280006fc8] stream_out_transcode stream out error: cannot find audio encoder (module:any fourcc:mpga). Take a look few lines earlier to see possible reason.
[0x7f9270001088] main generic debug: removing module "a52"
[0x7f9280006fc8] stream_out_transcode stream out error: cannot create audio chain
[0x7f9280560968] main decoder error: cannot create packetizer output (a52 )

```

I've installed libavcodec-extra-53 and restricted extras. I've even enabled the medibuntu repo and reinstalled ffmpeg from there. Right now I've run out of ideas so I'm crying out for help :)

If anyone can assist I'd appreciate it.

Thanks!

---

### Post by ron999 on 2012-08-01
> **richpowell said:**
> 
When I run this I receive the following errors in the output:


Hi
Try with simplified commands to eliminate things.

Change this:-
```
{vcodec=mp4v,acodec=mpga,vb=3000,ab=256,venc=ffmpeg{keyint=80,hurry-up,vt=800000},deinterlace}
```
To this:-
```
{vcodec=mp4v,acodec=none}
```
Then this:-
```
{vcodec=mp4v,acodec=mpga}
```

If it's OK, add more options.
:P

---

### Post by richpowell on 2012-08-01
OK, I changed it to:

```
cvlc channels.conf -I http --http-src='/usr/share/vlc/lua/http/' --sout-keep --sout '#transcode{vcodec=mp4v,acodec=none}:std{access=http,mux=ts,dst=:8181}'
```

And I'm still getting:

```
[0x7f6ff04cd678] stream_out_transcode stream out error: cannot find audio encoder (module:any fourcc:none). Take a look few lines earlier to see possible reason.
[0x7f6ff04cd678] stream_out_transcode stream out error: cannot create audio chain
[0x7f6ff0560698] main decoder error: cannot create packetizer output (a52 )

```

and

```
[0x7f6ff04cd678] stream_out_transcode stream out error: cannot find video encoder (module:any fourcc:mp4v). Take a look few lines earlier to see possible reason.
[0x7f6ff04cd678] stream_out_transcode stream out error: cannot create video chain
[0x7f6ff04d7188] main decoder error: cannot create packetizer output (mpgv)

```

So it doesn't appear to have helped. Any other suggestions? :)

---

### Post by ron999 on 2012-08-01
> **richpowell said:**
> Any other suggestions? :)


Hi
Try transcoding a (small) video file first, instead of a stream.
```
cvlc [COLOR="Red"]<filename>[/COLOR] -vvv --sout="#transcode{vcodec=mp4v,acodec=mpga}:std{access=file,mux=mkv,dst='filename.mkv'}" vlc://quit
```

---

