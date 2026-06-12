---
title: "[SOLVED] Rhythm Box stopped playing MP3s"
date: 2008-01-16
forum: Multimedia &amp; Video
---

### Post by jslmg on 2008-01-16
Rhythmbox played MP3s very nicely until today. It still loads and sees my library, which is on an external hard drive. However, when I try to play any track I only get a red emblem in the "speaker" column at far left. Clicking on the emblem, I see this message: "Playback error: Resource busy or not available."

I have made sure my ext. HD is set with all users "read and write." MP3s will still play in Gxine and Exaile (based on Amarok), though also not in Banshee.

I have all the audio codecs installed for gstreamer, plus the w32codecs, the whole ubuntu-restricted-extras package. I can compile a complete list of these later if anyone thinks that would help you to provide help.

I am wondering if my recent work getting gxine and mplayer functioning had anything to do with this. Can anyone steer me in the right direction on what to check so I can get Rhythmbox to play as before, while still having full function in gxine as well?

---

### Post by jslmg on 2008-01-17
Well, I suppose I could just use Exaile--it's nice and all, but Rhythmbox has some features that other players don't and it's the most intuitive, so I want it back...

BUMP!

---

### Post by jslmg on 2008-01-17
I was thinking this would be a fairly common issue, and that help would be forthcoming. Maybe it's not so common, and that's why there's so much silence in the room.

To help great minds get moving again, here's a list of all the gstreamer files I have installed, followed by a list of all the xine plugins. Are there other audio systems/plugins I should consider?

I've also attached two png's. One shows the message I get for each audio file in my library, while the other shows the message for a stream. Keep in mind that Rhythmbox DOES see the directory containing these files; when I right-click on a song, I select properties, then I see the path to the file. I even tried removing and reloading the library.

Gstreamer        
gstreamer0.10-alsas  
gstreamer0.10-esd             
gstreamer0.10-ffmpeg        
gstreamer0.10-fluendo-mp3    
gstreamer0.10-fluendo-mpegdemux
gstreamer0.10-gl    
gstreamer0.10-gnomevfs                                                    
gstreamer0.10-pitfdll 
gstreamer0.10-plugins-bad    
gstreamer0.10-plugins-bad-dbg    
gstreamer0.10-plugins-bad-multi 
gstreamer0.10-plugins-bad-multi 
gstreamer0.10-plugins-base 
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-dbg  
gstreamer0.10-plugins-ugly-mult
gstreamer0.10-plugins-ugly-mult 
gstreamer0.10-sdl       
gstreamer0.10-tools 
gstreamer0.10-x 
kaffeine-gstreamer
libgstreamer-plugins-base0.10-0
libgstreamer-plugins-pulse0.10-0                                
libgstreamer0.10-0 
totem-gstreamer 
w32codecs


xine:
amarok-xine 
gxine   
gxineplugin    
kaffeine-xine 
libxine-xvdr 
libxine1                        
libxine1-console  
libxine1-ffmpeg  
libxine1-gnome     
libxine1-plugins
libxinerama-dev  
libxinerama1  
w32codecs                    
x11proto-xinerama-dev            
xine-plugin

---

### Post by jslmg on 2008-01-18
Update:

I opened Rhythmbox using terminal to see what sorts of messages were passing through. There were several "CRITICAL" errors. The one that came up when I double-clicked a song to play it was:

```
(rhythmbox:10910): RhythmDB-CRITICAL **: rhythmdb_entry_get_string: assertion `entry != NULL' failed

```

The other errors messages are actually the same two, recurring:

```
** (rhythmbox-metadata:11324): CRITICAL **: h_rewindNbits: assertion `bb->buf_byte_idx >= byte_off' failed

** ERROR **: file mp3-c.c: line 519 (III_huffman_decode): assertion failed: (i <= SSLIMIT * SBLIMIT)
aborting...

```

---

### Post by jslmg on 2008-01-18
Solved. In all my fiddling around to get Gxine and web Flash audio working, I'd changed one setting in the system sound preferences, and that threw RB off.

---

### Post by DaV|d on 2008-03-30
Do you remember what setting(s) you changed? I'm geting the same problem, but I can't find which setting :(

---

### Post by DaV|d on 2008-03-30
Actually, I think it's a gstreamer related bug, as even totem is crashing on the same song.

EDIT: Ok i think its related to this bug => [https://bugs.launchpad.net/ubuntu/+source/gst-fluendo-mp3/+bug/73373]("https://bugs.launchpad.net/ubuntu/+source/gst-fluendo-mp3/+bug/73373")
Removing gst-fluendo-mp3 solved the problem :)

---

