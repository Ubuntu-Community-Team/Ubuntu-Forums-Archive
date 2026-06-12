---
title: "Render subtitles to mp4?"
date: 2009-09-12
forum: Multimedia Software
---

### Post by djbushido on 2009-09-12
I am trying to convert a (few) video(s) from a matroska format into just mp4. The video is h.264, and the matroska has subtitles that I would like to merge to the video (playing on mp3 player). If anyone knows of a tool to do this, that would be wonderful.

---

### Post by shirilover on 2009-09-13
Avidemux can do it. It will require extracting the subtitle stream and re-encoding the video.

---

### Post by djbushido on 2009-09-13
Then how would I extract the video/subtitles? Can avidemux do that too?

---

### Post by lovinglinux on 2009-09-13
> **djbushido said:**
> Then how would I extract the video/subtitles? Can avidemux do that too?

mkvtoolnix

---

### Post by djbushido on 2009-09-13
Can it re-merge the streams? I.e. render subtitles using avidemux, and re-merge audio and video to mkv, then convert to mp4. I use ffmpeg for final conversion, maybe have that merge the audio and video?

---

### Post by lovinglinux on 2009-09-13
> **djbushido said:**
> Can it re-merge the streams? I.e. render subtitles using avidemux, and re-merge audio and video to mkv, then convert to mp4. I use ffmpeg for final conversion, maybe have that merge the audio and video?

To do what you want , you would have to use the extraction commands of mkvtoolnix, to get the video, audio and subtitle streams separated from the mkv container. Then you would have to encode them together to a mp4 container, using avidemux. Avidemux has plugin to embed the subtitles in the video. There is no need to mux them back to mkv or make a final conversion with ffmpeg. Muxing back to mkv with mkvtoolnix does not require re-encoding, but that final conversion with ffmpeg does, so you would loose quality and a lot of time with an unnecessary step.

---

### Post by djbushido on 2009-09-13
So I'm trying to convert to mp4 for my mp3 player, and i need to render the subtitles from an mkv video to this new video. What specifically do I need to do? You are really confusing me.

---

### Post by lovinglinux on 2009-09-13
> **djbushido said:**
> So I'm trying to convert to mp4 for my mp3 player, and i need to render the subtitles from an mkv video to this new video. What specifically do I need to do? You are really confusing me.

You have a couple of matroska (mkv) files with subtitles included. The matroska format does not embed the subtitle in the video itself. It has separated subtitle files, called streams, inside the mkv container. The same applies for videos and audio, which basically means you can add any number of subtitle, video and audio streams to a mkv container, without actually physically merging them. 

So, if they are not physically tied together, you can extract them right? Yes, you can extract the subtitles, the videos and the audio streams from the mkv containers, using the extraction command of mkvtoolnix application (consult mkvtoolnix instructions).

Once you have extracted them, you will have at least 3 separated files, one will be the audio, another one the video and another one the subtitles. Then you have to put them back together, but this time physically embedding the subtitles over the video and econding the output (video+audio+subtitle) to the format you want, which is a mp4 container encoded with h.264 codec. You can do that with avidemux. 

You need to open the video stream in avidemux, then add the audio through "Audio >> Second Track". It's not exactly a second track, because the video was separated from the audio stream when you extracted them form the mkv, but this is the way it works. Then click the button below the Video options, next to the video preview and select "MPEG-4 AVC (x264)", which is the encoding method you want. The click "Filters" and select the option "Subtitles" option and then one of the available options, depending on the subtitle format. Click the "+" button and you will be prompted for the subtitle file. Once you add the subtitle, you can start converting your video. Select "File >> Save >> Save Video" to do that.

---

### Post by djbushido on 2009-09-13
Thank you! Now I just have to try and make sure that this works.

---

### Post by xaliqen on 2009-09-13
These are somewhat detailed instructions I wrote for another post on doing the mkv to mp4 conversion and burning in subtitles for PS3, which is probably similar to the setup on your mp3 player.  Also note that you may have to reduce video quality in avidemux, unless you have a really good mp3 player that can handle large video streams.

Please keep in mind the specific video and audio formats that work with the player, because conversions may be in order here as well.

As you and others previously mentioned, most mp3 players (and PS3) don't support optional subtitles (i.e. soft subs). So, you'll have to burn in any subtitles for mp4 (and re-encode) using avidemux or similar.  For the specific instructions of burning in the subtitles and things to keep in mind, look towards the bottom of the post where I detailed the avidemux info.

First, though, it's a good idea to know how to do a simple extraction of each track in the mkv file you're converting, and that's where the command line tools come in.

---
Example: To convert a file named needles.mkv from mkv to mp4 without re-encoding, from the command line enter:

$ sudo apt-get update && sudo apt-get install gpac mkvtoolnix

{This installs the tools you will use for the conversion.}

$ mkvinfo needles.mkv

{This gives you information about each track in the file so that you can perform the extraction properly (for example: track number 1 is video encoded with AVC/mpeg4 at 23.976 fps; track 2 is AAC audio; track 3 is subtitles in SRT format) Be sure to note the fps for the video track, because you will use this later with MP4Box.}

$ mkvextract tracks needles.mkv 1:needles_video.h264 2:needles_audio.aac 3:needles_subtitles.srt

{This extracts the tracks and names them according to what you specify. Be sure to specify names for the tracks that match the information from mkvinfo}

{This next part details how to put your extracted tracks into an mp4 container using MP4Box from the command line.  If you want to burn subtitles into the video itself so that they are non-removable, please skip down to the section where I detail how to do this in avidemux}

$ MP4Box -fps 23.976 -add needles_video.h264 -add needles_audio.aac -add needles_subtitles.srt needles_final.mp4

{this tells MP4Box the source material is running at 23.976 fps (change according to fps information from mkvinfo you noted earlier) and to combine your extracted video, audio and subtitles tracks into an mp4 container named "needles_final.mp4"}

{As a final note on merging subtitle tracks with MP4Box, please keep in mind that it is not compatible with SSA and various other subtitle formats at the moment. Therefore, if you are trying to add soft-subs in this format, you must first convert them to a format MP4Box understands. Just open the subtitles extracted with mkvextract (e.g. needles_subtitles.ssa) using a subtitle-editing program such as Gnome Subtitles. Then save a copy as subrip (srt) or other compatible format, and you're ready to put things together with MP4Box.}
---

So, there's your straight conversion to an mp4 file without re-encoding.

But remember, the subtitles in my example will not display on PS3 or most mp3 players, because they are not burned into the video (i.e. part of the picture and non-removable).

If you want to play files on a device that does not support soft-subs, I suggest using avidemux to re-encode the video with the subtitles filter.

Avidemux subtitle burn-in instructions:

In avidemux, open the original file you want to convert to mp4 (e.g. needles.mkv). Add the subtitle track (e.g. needles_subtitles.srt) extracted using mkvextract to the subtitles filter in avidemux (located under "Filters"). Use the subtitle filter appropriate for the type of subtitles you are using (e.g. subtitler for srt), and be sure to select a ttf font if it asks for one. Remember, you have to re-encode the video for this to work (e.g. select MPEG-4 AVC under video), otherwise the subtitles won't be burned into the video. Finally, select mp4 under "Format", save the video (ctrl+s) and wait for the encode to finish.

Since you are re-encoding the video when you use avidemux to burn in the subtitles, you may notice a loss in visual quality.

There are some steps you can take to minimize the quality lost in an avidemux re-encode. One way is to click on "Configure" and change the encoding mode to "Video Size (two pass)" and make sure the target video size is the same size as the video information in the original file (e.g. same size as needles_video.h264). This works reasonably well when I've tried it.

---

### Post by djbushido on 2009-09-14
Excellent! I just still have to do a conversion from the mp4 to something my mp3 player will understand. Once I re-encode the video, can't ffmpeg merge the streams back together and encode at the same time?

---

### Post by xaliqen on 2009-09-14
You could just re-encode video and audio streams into a format your mp3 player understands in avidemux at the same time you burn in the subtitles.

If you need the audio or video to be below the bitrate of your original file, just select a bitrate-oriented encoding mode under "Configure" for either audio or video (or both audio and video, if you need to change both).

Example (assuming an mp3 player that only plays videos with xvid-video, mp3-audio and avi-container with video and audio quality below a certain bitrate):

Open the video you want to convert and select the subtitle filter options as outlined in the previous post.

Now select "Mpeg-4 ASP (Xvid)" under video and "MP3 (lame)" under audio.  If you need to lower the bitrate of audio or video, do so by selecting an encoding mode where you can determine the bitrate for the appropriate track (e.g. change bitrate to 128 under audio).  Otherwise, try to maximize the quality by keeping sizes and bitrates as close to the original as possible (some tips on this in the previous post).

Select "AVI" as the format and save the file (ctrl+s) to run the encode and burn in the subtitles.  This saves the step of re-encoding again after you burn in the subtitles and just does the burn-in and conversion at the same time.

If the file doesn't play properly, examine the specifications for video playback on the mp3 player closely.  Mp3 players can be pretty picky as far as the type of encode and container they are looking for.  Also pay attention to the resolution of the video in the original file, as you may have to change this to meet the specifications of your mp3 player.  You can change resolution using one of the "resize" filters (located under filters-->transform).

Use whichever combination of video/audio/container format plays best on your particular player.  I used xvid/mp3/avi as an example, because a lot of devices can play this.  So, please use whichever audio/video/container combination yields the highest quality playback for the device in question.

---

### Post by djbushido on 2009-09-14
My mp3 player is incredibly picky - Sony Walkman. Which is why I am adamant about doing it with ffmpeg. It needs VERY specific video and audio, so I am trying to avoid having that much fun again with AVIdemux, a tool that as far as I know is not suited to do the kinds of conversions I need. So - can ffmpeg merge the streams together and output the mp4 container, or no? I can split off the aac and h.264, re-encode h.264 with subtitles, I just need to merge them back. Sorry for being so stubborn, but I really don't want to spend another period of days trying to get AVIdemux working with my mp3 player.

---

### Post by xaliqen on 2009-09-14
I've had better luck using mencoder and MP4Box, but I was doing something slightly different with the videos I worked with.

I don't know if ffmpeg supports muxing with mp4 containers, but my guess is that it probably does.  I would just use mencoder to re-encode and MP4Box to remux, but it all boils down to which program is the easiest to deal with for your needs.

I would be curious to know how well ffmpeg muxes the files.  So, if everything works out, please give us an update.

As a side note, you may also want to investigate using some of the specialized programs for windows through wine.

I know for a fact there are quite a few specialized windows programs for video conversions aimed at PS3 compatibility.  I imagine there are a number that specialize in conversion for personal media devices as well.  I've had success using yamb through wine, and I've also used multiAVCHD and mkv2vob.

---

### Post by djbushido on 2009-09-16
Will let you know if ffmpeg can mux the files, but I think that I'm going to remux it to mp4 through avidemux, then convert for my mp3 player. If I get ffmpeg going, I'll let you know.

---

### Post by lovinglinux on 2009-09-16
> **djbushido said:**
> Will let you know if ffmpeg can mux the files, but I think that I'm going to remux it to mp4 through avidemux, then convert for my mp3 player. If I get ffmpeg going, I'll let you know.

I need to ask again. Why do you wanna do that? Have you tried to play a file muxed and re-encoded with avidemux, using the required codecs and output format? Unless Avidemux cannot output a format that is compatible with your player, there absolute no reason to add a new re-encoding step, which would only result in loss of quality. But as far as I know, Avidemux is perfectly capable of encoding video with the required specs for PS3. Perhaps you are using the wrong settings. You said that you need h.264, aac and mp4 right?

If you audio source is already aac, then use the "Copy" settings for audio in avidemux, so the audio will not be re-encoded, simply muxed. Then select MPEG-4 AVC (x264) for video and MP4 in the format settings. That should be enough to output a compatible file.

---

### Post by djbushido on 2009-09-16
True that I need h.264(x264). However: My mp3 player takes extremely precise settings: I have to set quality options, baseline levels, and all this junk. AVIdemux just does not give me the control I need for it to work.

---

### Post by djbushido on 2009-09-16
AVIDemux now is crashing: running program from console produces this output:```
$ avidemux                                                     
***************************                                                                                                  
  Avidemux v2.4.4                                                                                                            
***************************                                                                                                  
 http://www.avidemux.org                                                                                                     
 Code      : Mean, JSC, Gruntster                                                                                            
 GFX       : Nestor Di , nestordi@augcyl.org                                                                                 
 Design    : Jakub Misak                                                                                                     
 FreeBSD   : Anish Mistry, amistry@am-productions.biz                                                                        
 Audio     : Mihail Zenkov                                                                                                   
 MacOsX    : Kuisathaverat                                                                                                   
 Win32     : Gruntster                                                                                                       

Compiler: GCC 4.3.3
Build Target: Linux (x86)
User Interface: GTK+ (2.16.1)

Large file available: 1 offset

Initialising prefs
Directory /home/brad/.avidemux exists.Good.
Using /home/brad/.avidemux as base directory for prefs/jobs/...
Preferences found and loaded                                   
[cpuCaps]Checking CPU capabilities                             
                MMX detected                                   
                MMXEXT detected                                
                SSE detected                                   
                SSE2 detected                                  
[cpuCaps]End of CPU capabilities check (cpuMask :ffffffff)     

 Registering Encoders
*********************
MJPEG encoder registered
Xvid-4 encoder registered
FFmpeg encoder registered

3 encoder(s) registered

[SDL] Version: 1.2.13
[SDL] Initialisation succeeded
[SDL] Video Driver: x11       


[Locale] setlocale en_US.UTF-8
[Locale] Textdomain was messages
[Locale] Textdomain is now avidemux
[Locale] Files for avidemux appear to be in /usr/share/locale
[Locale] Test: _File                                         

Initializing Dithering tables
[xvid] Initializing global Xvid 4
[xvid] Build: xvid-1.1.2         
[xvid] SIMD supported: (cf)      
                MMX              
                MMXEXT           
                SSE              
                SSE2             
Found 20 video encoder           
Found 9 audio encoder            
Found 13 Format                  
Directory /home/brad/.avidemux/custom exists.Good.
No custom script                                  
Found 0 custom scripts, adding them               
Menu built                                        
The screen seems to be 1024 x 768 px              
/dev/input/event0: Permission denied              
/dev/input/event1: Permission denied              
Not interested in /dev/input/event2: Macintosh mouse button emulation (bus 0017 vendor 0001 product 0001 version 0100)
/dev/input/event3: Permission denied                                                                                  
Not interested in /dev/input/event4: HID 1241:1166 (bus 0003 vendor 1241 product 1166 version 0110)                   
/dev/input/event5: Permission denied                                                                                  
/dev/input/event6: Permission denied                                                                                  
Not interested in /dev/input/event7: IBM IBM ScrollPoint Wireless Mouse (bus 0003 vendor 04b3 product 3104 version 0100)
/dev/input/event8: Permission denied                                                                                    
/dev/input/event9: Permission denied                                                                                    
No physical Jog/Shuttle device found.                                                                                   
Initializing postproc                                                                                                   
Deleting post proc                                                                                                      
updating post proc                                                                                                      
Enabled type:3 strength:3                                                                                               

 Registering Filters
*********************

Using real audio device
Spidermonkey initialized.
No crash file (/home/brad/.avidemux/crash.js)
1000000 -> 1000000                           
Probing : [FILE REFERENCE REMOVED]

Simple loading: 
 file: /[FILE REFERENCE REMOVED], size: 343153025
 found 1 files                                                                                  
Done                                                                                            
Cannot identify /[FILE REFERENCE REMOVED] as mpeg (0/0)
Identified as H264 ES                                                                                 
Probe says it is mpeg                                                                                 
594d4441 -> 594d4441                                                                                  
                                                                                                      
 New mpeg index file detected..                                                                       

  opening d2v file : [FILE REFERENCE REMOVED].idx
For file :[FILE REFERENCE REMOVED]               
Pic      :1280x720, 23976 fps                                                                    
#Gop     :1                                                                                      
#Img     :1                                                                                      

Simple loading: 
 file: [FILE REFERENCE REMOVED], size: 343153025
 found 1 files                                                                                  
Done                                                                                            
Dropping 0 last B/P frames                                                                      
 Creating start sequence (0)..                                                                  
Mmm cound not find a gop start.....                                                             
Reordering mpeg frames                                                                          
Renumbered Gop  1 /1                                                                            
Mpeg index file successfully read                                                               
Deleting post proc                                                                              
Initializing postproc                                                                           
Deleting post proc                                                                              
updating post proc                                                                              
Enabled type:3 strength:3

 *** NO AUDIO ***

 Decoder FCC: H264 (34363248)
Searching decoder (1280 x 720, extradataSize:0)...
[lavc] Build: 3352580
[lavc] Initializing H264 decoder with 0 extradata
[lavc] Decoder init: CODEC_ID_H264 video decoder initialized!

 checking for B-Frames...

 *** NO AUDIO ***
[GTK] Changing size to 1280 720
[GTK] Changing size to 1280 720
[GTK] Changing size to 640 360
Threading error :22 Invalid argument
Cleaning up
[lavc] insufficient thread locking around avcodec_open/close()

Threading error :22 Invalid argument
Threading error :22 Invalid argument
Segmentation fault
```

EDIT:Opening the original .mkv seems to make it not crash. Why? Anyway, proceeding, will post results tomorrow.

---

### Post by Ronok on 2010-12-22
Thanks: **lovinglinux** 
for your previous detailed posts

Spliced-up, cut & Made a .mp4 video with: **Kdenlive V# 0.7.8**
Turned a plain text file into a .srt Subtitle file with: **Subtitle Composer V# 0.5.3**
added Subtitles with: **Avidemux 2.5.3**

OS: Linux Ubuntu 10.10
GNOME: 2.32.0 
Kernel: 2.6.35-24-generic 
SAMSUNG N148 (Laptop)
CPUs: "2" Intel Atom CPU N450 @ 1.66GHz 
L2 Cache: 512 KB
RAM Memory: 1G

Kool Thanks, was glad to find this post
[URL="http://www.gongkuo.com/linuxcli.htm"]Ronok 
[SIZE="1"]My < Linux > Command Line Interface Page[/SIZE][/URL]

---

