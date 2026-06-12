---
title: "VLC Not Playing Files"
date: 2009-08-23
forum: Multimedia Software
---

### Post by gamgee911 on 2009-08-23
I had vlc working fine in a previous 64 bit setup, but I upgraded the HD and reinstalled and now VLC is not working. I cannot get neither the vlc in the repos nor goldeneye to load video or audio files. here's what i can get from messages while trying to load an episode of Firefly off my drobo. it seems to instantly reach the end of the file then stop. Any help, i'm not used to troubleshooting VLC just always worked for me before :P  I have tried uninstalling (and using autoremove to remove additional packages) and reinstalling both the version in ubuntu repos and the new beta

```
main debug: processing request item Fierfly HD 1x14.mkv node Playlist skip 0
    main debug: resyncing on Fierfly HD 1x14.mkv
    main debug: Fierfly HD 1x14.mkv is at 4
    main debug: starting new item
    main debug: creating new input thread
    main debug: Creating an input for 'Fierfly HD 1x14.mkv'
    main debug: thread started
    main debug: thread (input) created at priority 10 (input/input.c:230)
    qt4 debug: IM: Setting an input
    qt4 debug: Updating the geometry
    qt4 debug: Updating the geometry
    main debug: using timeshift granularity of 50 MBytes
    main debug: using timeshift path '/tmp'
    main debug: `/media/Drobo/Media/TV Shows/Firefly HD/Fierfly HD 1x14.mkv' gives access `' demux `' path `/media/Drobo/Media/TV Shows/Firefly HD/Fierfly HD 1x14.mkv'
    main debug: creating demux: access='' demux='' path='/media/Drobo/Media/TV Shows/Firefly HD/Fierfly HD 1x14.mkv'
    main debug: looking for access_demux module: 7 candidates
    main debug: TIMER module_need() : 0.184 ms - Total 0.184 ms / 1 intvls (Avg 0.184 ms)
    main debug: creating access '' path='/media/Drobo/Media/TV Shows/Firefly HD/Fierfly HD 1x14.mkv'
    main debug: looking for access module: 7 candidates
    vcd debug: trying .cue file: /media/Drobo/Media/TV Shows/Firefly HD/Fierfly HD 1x14.cue
    vcd debug: could not find .cue file
    main debug: using access module "access_directory"
    main debug: TIMER module_need() : 0.923 ms - Total 0.923 ms / 1 intvls (Avg 0.923 ms)
    main debug: Using AStream*Block
    main debug: pre buffering
    main debug: received first data after 0 ms
    main debug: prebuffering done 160 bytes in 0s - 5387 kbytes/s
    main debug: looking for stream_filter module: 4 candidates
    main debug: TIMER module_need() : 0.124 ms - Total 0.124 ms / 1 intvls (Avg 0.124 ms)
    main debug: looking for stream_filter module: 1 candidate
    main debug: using stream_filter module "stream_filter_record"
    main debug: TIMER module_need() : 0.150 ms - Total 0.150 ms / 1 intvls (Avg 0.150 ms)
    main debug: creating demux: access='' demux='xspf-open' path='/media/Drobo/Media/TV Shows/Firefly HD/Fierfly HD 1x14.mkv'
    main debug: looking for demux module: 1 candidate
    playlist debug: using XSPF playlist reader
    main debug: using demux module "playlist"
    main debug: TIMER module_need() : 0.139 ms - Total 0.139 ms / 1 intvls (Avg 0.139 ms)
    main debug: looking for a subtitle file in /media/Drobo/Media/TV Shows/Firefly HD/
    main debug: `/media/Drobo/Media/TV Shows/Firefly HD/Fierfly HD 1x14.mkv' successfully opened
    main debug: looking for xml module: 2 candidates
    main debug: using xml module "xml"
    main debug: TIMER module_need() : 0.124 ms - Total 0.124 ms / 1 intvls (Avg 0.124 ms)
    playlist debug: parsed 0 tracks successfully
    main debug: removing module "xml"
    main debug: EOF reached
    main debug: finished input
    main debug: removing module "playlist"
    main debug: removing module "stream_filter_record"
    main debug: removing module "access_directory"
    main debug: dead input
    main debug: thread ended
    main debug: changing item without a request (current 4/5)
    main debug: nothing to play
    qt4 debug: IM: Deleting the input
    qt4 debug: Updating the geometry
    qt4 debug: Updating the geometry
    main debug: TIMER input launching for 'Fierfly HD 1x14.mkv' : 17.526 ms - Total 17.526 ms / 1 intvls (Avg 17.526 ms)
```

---

### Post by j7%&lt;RmUg on 2009-08-24
Have you tried just playing an mp3, ogg or avi file?

I know vlc can play alot of formats but im not sure about mkv files.

---

### Post by gamgee911 on 2009-08-27
the mkv was just an example, it doesn't play any files (avi, ogg, etc).

my understanding of mkv is its just a container for a avi file with subtitles.  could be wrong though

---

