---
title: "Rhythmbox is Using Hidden Tags"
date: 2009-01-18
forum: Multimedia Software
---

### Post by njdube on 2009-01-18
I'm trying to change some tags in my music using Rhythmbox and a few seconds later it reverts back to their old tags.  I've tried EasyTAG, MusicBrainz Picard via WINE, Amarok as well as Banshee and they all show the NEW tags.  But for some reason Rhythmbox goes back to OLD tags.  Here's what I get from playing around in shell.

######################################

nate@Defiant:~$ gst-launch -t playbin uri=file:///home/nate/Music/AC_DC/Ballbreaker/01\ -\ Hard\ As\ A\ Rock.mp3
Setting pipeline to PAUSED ...
Pipeline is PREROLLING ...
FOUND TAG      : found by element "id3demux0".
           title: Hard as a Rock
          artist: AC/DC
     track count: 11
    track number: 1
           album: Ballbreaker
           genre: Heavy Metal / Hard Rock / Metal / Rock / Classic Rock
     ID3v2 frame: buffer of 23 bytes, type: application/x-gst-id3v2-xsop-frame, version=(int)3
                : buffer of 71 bytes, type: application/x-gst-id3v2-txxx-frame, version=(int)3
                : buffer of 55 bytes, type: application/x-gst-id3v2-txxx-frame, version=(int)3
                : buffer of 45 bytes, type: application/x-gst-id3v2-txxx-frame, version=(int)3
                : buffer of 23 bytes, type: application/x-gst-id3v2-tpe2-frame, version=(int)3
                : buffer of 59 bytes, type: application/x-gst-id3v2-txxx-frame, version=(int)3
                : buffer of 57 bytes, type: application/x-gst-id3v2-txxx-frame, version=(int)3
                : buffer of 99 bytes, type: application/x-gst-id3v2-ipls-frame, version=(int)3
                : buffer of 21 bytes, type: application/x-gst-id3v2-tpub-frame, version=(int)3
                : buffer of 87 bytes, type: application/x-gst-id3v2-txxx-frame, version=(int)3
                : buffer of 81 bytes, type: application/x-gst-id3v2-txxx-frame, version=(int)3
 album artist ID: 66c662b6-6e2f-4930-8610-912e24c63ed1
       artist ID: 66c662b6-6e2f-4930-8610-912e24c63ed1
           image: buffer of 30564 bytes, type: image/jpeg, image-type=(GstTagImageType)GST_TAG_IMAGE_TYPE_FRONT_COVER
        track ID: e69763d5-dd38-418e-8b24-b51dc4f9df90
            date: 2005-01-01
        album ID: d6abfd4f-ea99-4773-a735-147ead2676d5

#This is where things get weird.  Rhythmbox  seems to only care about the bottom entry.  The weird part is that none of my other programs will detect or care about or even change the bottom entry.

FOUND TAG      : found by element "id3demux1".
           genre: Pop/Rock
     ID3v2 frame: buffer of 24 bytes, type: application/x-gst-id3v2-priv-frame, version=(int)4
                : buffer of 27 bytes, type: application/x-gst-id3v2-priv-frame, version=(int)4
          artist: AC/DC
           title: Hard As A Rock
           album: Ballbreaker
            date: 1995-01-01
    track number: 1
FOUND TAG      : found by element "mpegaudioparse0".
     audio codec: MPEG 1 Audio, Layer 3 (MP3)
FOUND TAG      : found by element "mpegaudioparse0".
         bitrate: 320000
         has crc: FALSE
    channel mode: stereo
FOUND TAG      : found by element "mad0".
           layer: 3
            mode: stereo
        emphasis: none
         bitrate: 320000
Pipeline is PREROLLED ...
Setting pipeline to PLAYING ...
New clock: GstAudioSinkClock

######################################

Any help getting this sorted out would be appreciated.:guitar:

---

