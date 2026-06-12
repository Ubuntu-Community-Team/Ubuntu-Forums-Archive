---
title: "HELP avidemux crash"
date: 2009-10-18
forum: Multimedia Software
---

### Post by utnubu12 on 2009-10-18
Please assist me.
When, in Avidemux, I try to open an avi file that is on my computer, Avidemux disappears.  When I right click the avi video and then click "Open with Avidemux", an Avidemux window opens for a millisecond and then disappears.
WHY DOES THIS HAPPEN AND HOW CAN I FIX IT?!!:confused:

---

### Post by cor2y on 2009-10-18
I dont know why it happens. :)

We need some more information 
What version of ubuntu/kubuntu/xubuntu etc are you using?
Is this avidemux you installed from the repos or one you compiled yourself or a package you downloaded from getdeb etc?

What version of avideumx is it?

Finally launch it from the terminal and post the error message.
To launch from the terminal
Alt+F1, Accessories->Terminal
Then type either avidemux2_gtk or avidemux_gtk if the first doesnt work (this will depend on what version of avidemux you are using a more modern version will use avidemux2_gtk)

Finally the avi file , what are the video and audio codecs?
The easiest way to go about this is to install [mediainfo-gu]("http://mediainfo.sourceforge.net/en")i install the deb files for your ubuntu distro in the download section.

---

### Post by utnubu12 on 2009-10-19
Sorry I didn't provide enough info.  Here it is:

I run Ubuntu 9.04 (Jaunty).
I installed Avidemux from the repos.
The version is Avidemux 2.
I didn't see a clear error message in the Terminal, but the following is what appeared after I tried to open the .avi file:

[B] Riff file detected... 
 AVI file detected...
** opening OpenDML files **
 Main avi header :
Indx found for track 0
Indx found for track 1
Idx1 found at offset 294ee68
Video track is 0
Track 0/2 :
vids (73646976)dvsd (64737664)
Track 1/2 is audio
Not an audio track!
Main header
______________________
dwStreams:        :2
dwMicroSecPerFrame:        :33366
dwMaxBytesPerSec:        :3600000
dwPaddingGranularity:        :512
dwFlags:        :2064
dwTotalFrames:        :358
dwInitialFrames:        :0
dwWidth:        :720
dwHeight:        :480

video stream attached:
______________________
 Extra Data  : 0
 fccType     :vids (73646976)
 fccHandler :dvsd (64737664)
 dwFlags:        :0
 dwInitialFrames:        :0
 dwRate:        :30000
 dwStart:        :0
 dwSampleSize:        :0
 dwScale:        :1001
 dwLength:        :358
 dwQuality:        :-1
 dwSampleSize:        :0
biSize:        :40
biWidth:        :720
biHeight:        :480
biBitCount:        :24
biCompression:        :1685288548
dvsd (64737664)
biSizeImage:        :120000
biXPelsPerMeter:        :0
biYPelsPerMeter:        :0
biClrUsed:        :0

audio stream attached:
______________________

 fccType     :auds (73647561)
 fccHandler : (00000000)
 fccHandler :0x0
 dwFlags:        :0
 dwInitialFrames:        :1
 dwRate:        :0
 dwScale:        :4
 dwStart:        :0
 dwLength:        :0
 dwSuggestedBufferSize:        :8192
 dwQuality:        :0
 dwSampleSize:        :4encoding:        :1
channels:        :2
frequency:        :0
byterate:        :0
blockalign:        :4
bitspersample:        :16
 Extra Data  : 12

 0000 : JUNK......in  4a 55 4e 4b 02 00 00 00 00 00 69 6e
_regularIndex.offset : yes
_Tracks[vidTrack].indx.offset : yes
Building odml video track
Trying ODML super index..
Sizeof OPENDML_INDEX:24
Sizeof OPENDML_ENTRY:16
Sizeof OPENML_SECONDARY_INDEX:24
Master index of 00dc (63643030) found
SubType : 0
We have 1 indeces
Found a grand total of 358 frames
ix00 (30307869)
Building odm audio tracks

Doing track 0 of 1
Trying ODML super index..
Sizeof OPENDML_INDEX:24
Sizeof OPENDML_ENTRY:16
Sizeof OPENML_SECONDARY_INDEX:24
Master index of 01wb (62773130) found
SubType : 0
We have 1 indeces
Found a grand total of 0 frames
ix01 (31307869)Odml indexing succeeded
 we have 12 bytes of extra data in wavheader

 Audio streamer initialized
 Total audio length : 0
OpenDML file successfully read..
Deleting post proc
Initializing postproc
Deleting post proc
updating post proc
Enabled type:3 strength:3
Floating point exception
ben@ben-laptop:~$ 
ben@ben-laptop:~$ 

[/B]I  installed media info and I believe that the video codec of the .avi file is DV and the audio codec is PCM

---

### Post by cor2y on 2009-10-19
Well this could be the problem
> Avidemux can only open type-2 DV files at the moment. Two types of DV files exist: type 1 and type 2. (read [here]("http://www.microsoft.com/whdc/archive/dvavi.mspx") about the differences between them)  However, some cameras produce type-1 DV video. To convert them to type-2 DV, you can either use [this tool from Canopus]("http://www.videohelp.com/tools/Canopus_DV_File_Converter") or [this one from Ulead]("http://www.ulead.com/download/dvconverter/dv.zip"). 
Like i said it COULD be the problem but not necessarily is the cause of the problem, i have read for avi dv files that crash on start up going back to version 2.4.0 of avidemux solved the problem for some people so you may have to look for that version at [getdeb](http://www.getdeb.net/app/Avidemux) or in synaptic.
Also you could try the new 2.5.1 version that was released in september i dont think that is in the repos for jaunty but it is up at[ getdeb]("http://www.getdeb.net/app/Avidemux") or if you feel brave you can compile and install it yourself.

---

