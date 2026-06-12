---
title: "MythTv mpeg-4 playback jitter"
date: 2009-11-03
forum: Multimedia Software
---

### Post by mlgim on 2009-11-03
Hi all

Not sure this is the right thread-prefix, so please tell me if I'm doing something wrong ;)

I've installed MythBuntu 9.10 and I've very pleased except the internal MythTv viewer/player messes up my mpeg4 playback so it jitters and jumps.

This is true both when showing live tv and recorded shows (DVB-T), but only on my mpeg4/h264 'channnels' - mpeg2 ones work just fine.

Here is a snipplet from /var/log/mythtv/mythfrontend.log:

```

2009-11-03 13:15:28.746 WriteAudio: buffer underrun
2009-11-03 13:15:29.256 [NULL @ 0x3d876c0]non-existing PPS referenced
2009-11-03 13:15:29.257 [h264 @ 0x3d876c0]B picture before any references, skipping
2009-11-03 13:15:29.257 [h264 @ 0x3d876c0]decode_slice_header error                
2009-11-03 13:15:29.258 [h264 @ 0x3d876c0]no frame!                                
2009-11-03 13:15:29.258 [h264 @ 0x3d876c0]non-existing PPS referenced              
2009-11-03 13:15:29.258 [h264 @ 0x3d876c0]B picture before any references, skipping
2009-11-03 13:15:29.258 [h264 @ 0x3d876c0]decode_slice_header error                
2009-11-03 13:15:29.258 [h264 @ 0x3d876c0]no frame!           
.
.
.
2009-11-03 13:15:29.547 [h264 @ 0x3d876c0]number of reference frames exceeds max (probably corrupt input), discarding one
2009-11-03 13:15:29.547 [h264 @ 0x3d876c0]number of reference frames exceeds max (probably corrupt input), discarding one
2009-11-03 13:15:29.755 AFD: Opened codec 0x9274830, id(H264) type(Video)
2009-11-03 13:15:29.755 AFD: codec AAC/LATM has 2 channels
2009-11-03 13:15:29.756 AFD: Opened codec 0x975ed00, id(AAC/LATM) type(Audio)
2009-11-03 13:15:30.107 [h264 @ 0x3d876c0]number of reference frames exceeds max (probably corrupt input), discarding one
2009-11-03 13:15:30.107 [h264 @ 0x3d876c0]number of reference frames exceeds max (probably corrupt input), discarding one
2009-11-03 13:15:30.107 [h264 @ 0x3d876c0]number of reference frames exceeds max (probably corrupt input), discarding one
2009-11-03 13:15:30.107 [h264 @ 0x3d876c0]number of reference frames exceeds max (probably corrupt input), discarding one
2009-11-03 13:15:30.107 [h264 @ 0x3d876c0]number of reference frames exceeds max (probably corrupt input), discarding one
.
.
.
2009-11-03 13:15:30.108 [h264 @ 0x3d876c0]number of reference frames exceeds max (probably corrupt input), discarding one
2009-11-03 13:15:30.410 NVP(3): Prebuffer wait timed out 10 times.
2009-11-03 13:15:31.033 [h264 @ 0x3d876c0]number of reference frames exceeds max (probably corrupt input), discarding one
2009-11-03 13:15:31.146 [h264 @ 0x3d876c0]number of reference frames exceeds max (probably corrupt input), discarding one
2009-11-03 13:15:31.180 [h264 @ 0x3d876c0]mmco: unref short failure
2009-11-03 13:15:31.596 [h264 @ 0x3d876c0]number of reference frames exceeds max (probably corrupt input), discarding one
2009-11-03 13:15:31.713 NVP(3): prebuffering pause

```If I use VLC to playback the recordings, it plays smoothly.
Ofcourse I could use the VLC player, but the internal viewer/player intergrates better.

The Mythbuntu install is plain-vanilla, no bells or whistles.

Thanks in advance!

---

### Post by ondemik on 2009-11-06
Not that it is much help, but I am having the exact same problem. I have just upgraded to an Nvidia ION platform, and VDPAU is excellent but the MPEG4 is still just as bad.  This is with the new Danish MPEG4 channels.

---

### Post by mlgim on 2009-11-06
(ser vi mødes på flere forum :0)

So you have tried VPAU and it didn't help with the mpeg4 h264 playback - that IS great info. Means I won't run out and buy a Nvidia card today :D

Can't believe there are no more google-hits on this issue - I think they run the same DVB-T format in Poland, Belgium ++  (mpeg4 h264 channels in dvb-t, 720*576 with aac audio)

Is it just us that find it strange that VLC plays this content ok and the internal MythTv player (and xine) doesn't.

It's probably a codec issue, but the world of video codes is a huge and scary place, and the only refrences I tend to find are by people who write their own, which is a bit over my head ;)

Anyone ...?

---

### Post by mymythtv on 2009-11-06
hi

Got the same problems - danish DVB-T/MPEG4. First thougt it was the asus GS8400/256Mb not having enough power ( vdpau spec on mythtv ), so i got a 512Mb instead.
Wasn't sure if it was my NOVA-T500 DVB-T card having problems with the new mpeg4 ( shouldn't ), but recording on DVB-S2 also shows mpeg4 problems.

Isn't at home right now, but from short tests last night ( if I remember correct ):
DVB-T MPEG2: Plays just fine.
DVB-T MPEG4: Jitter in video - sound ok.
DVB-S/S2 MPEG2: Plays just fine.
DVB-S/S2 MPEG4: Jitter in video - sound ok.

Recording DVB-S/S2 MPEG4 plays fine in mplayer ! ( mplayer -vo vdpau <recording> ), but not with "internal". Didn't make it to record DVB-T mpeg4 and play it back with mplayer.

Will try to test some more this weekend, but I'm not at home right now..

ahh - forgot hw spec :-)
mythtv 0.22 stable
nova-t500 DVB-T
nova S2-HD DVB-S/S2
asus GS8400/512Mb
Intel E8500 dual core 3,16GHz
4Gb memory

---

### Post by nissekonge on 2009-11-07
Same problem here. As I see it there is no relation between the jittering and the tuner used. I have tried both a Hauppauge and a TechnoTrend Budget with the same result - jittering images. I experimented a bit with the VLC approach and came to the same conclusion. Then I tried transcoding a recording to see if it was a bit-rate issue - it was not - but when I played the transcoded recording in VLC the video had the same jittering as the video played in MythTv. I also tried to play a fresh recording (non transcoded) using mplayer and it had the same jittering. I am wondering whether it might have something to do with the MUX the channel uses. My DR1, DR2, TV2, DR Ramasjang and DR K (Danish channels..;-) are all nice and clear but the pay-channels I have bought are all jittery. Any suggestions?

Hardware spec - also forgot..:-)

Mythtv 0.22RC1 (with Mythbuntu 9.10)
Techno Trend TT-Budget T-1500 with a built in CAM reader
Asus P5QL-EM
Core 2 Duo

---

### Post by mlgim on 2009-11-07
Hi all

Saw this (Danish) blog - seems to be better in MythTv 0.22 revision 22722, so use different apt-source or compile from source. Just info - havn't tried it myself. Here's the link:
[http://forum.recordere.dk/forum_posts.asp?TID=69424&PID=702978#702978](http://forum.recordere.dk/forum_posts.asp?TID=69424&PID=702978#702978)

---

### Post by nissekonge on 2009-11-07
It's good to hear that there is a solution at the end of the road. I think, however, that I will wait for the deb-package instead of installing from source and from svn. As far as I remember it has a tendency to be a bit unstable and makes it difficult to update later...;-) But thanks for the link.

---

### Post by byronmyth on 2009-11-20
Is anyone looking at fixing this?

---

### Post by mlgim on 2009-11-22
Hi there Byronmyth

Yes, sorry. We are all so eager to post when in trouble, but slow to react when we've found a sloution.

The solution was a patch to ffmpeg ( [r20504]("http://svn.mythtv.org/trac/changeset/20504"))
See history here

[http://svn.mythtv.org/trac/ticket/7522](http://svn.mythtv.org/trac/ticket/7522)

Thanks to all the folks who helped to diag & fix this!!!!:p

---

### Post by byronmyth on 2009-11-23
That's fantastic, but being a newbie I've not been able to work out what I need to do to apply this patch :(

---

### Post by mlgim on 2009-11-23
If possible, just wait a week or 2 - then it'll probably be in the mythtv-fixes tree and you can just use apt to update your mythtv installation.

---

### Post by byronmyth on 2009-11-23
Is it that difficult to do then?

---

### Post by mlgim on 2009-11-24
Probably not, but I'd hate to compile from source and potentially break my apt update path. I might have to though :0(

Might have a look at the 'thunk' repo from MythBuntu - seems they have a daily built tree.

---

### Post by byronmyth on 2009-12-01
Seems that as I have the Mythbuntu install I don't have the source to be to apply that patch, and as you say I'm not sure that I'd want to get into that anyway. Any idea when that patch will make it into the fixes, I keep checking but no show yet. I've got relations over at Christmas and I'd really like to be able to show the German HD channels!

---

