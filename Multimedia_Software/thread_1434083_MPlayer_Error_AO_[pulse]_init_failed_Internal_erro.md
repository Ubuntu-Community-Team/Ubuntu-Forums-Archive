---
title: "MPlayer Error AO: [pulse] init failed: Internal error"
date: 2010-03-19
forum: Multimedia Software
---

### Post by cscott0108 on 2010-03-19
Hi all,
Whenever I use the GUI MPlayer to play a song I get the error (AO: [pulse] init failed: Internal error), I did get rid of pulseaudio sound server and replaced it with esound, I am thinking this is the cause, I get audio from the playback just I keep getting that error message and it is really irritating, since it's the only player that caches the song before playback I have ended up tolerating it, but I would like to see if there is a solution for this.

---

### Post by andrew.46 on 2010-03-19
Hi cscott0108,

Can you try to play a file with MPlayer from the commandline as follows:

```

mplayer -ao alsa **[COLOR="Red"]<my_file>[/COLOR]**
mplayer -ao oss **[COLOR="Red"]<my_file>[/COLOR]**

```

with <my_file> being substituted for the actual name of your file of course. This should give an indication of the audio out device that you can substitute for the default of pulse. Try *-ao esd* as well I guess...

All the best,

Andrew

---

### Post by cscott0108 on 2010-03-21
With Alsa = 
chris@chris-laptop-linux:~$ mplayer -ao alsa /media/sda1/Users/Chris/Music/Blink\ 182/Take\ Off\ Your\ Pants\ \&\ Jacket/03\ First\ Date.mp3
MPlayer UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team                                                                                            
mplayer: could not connect to socket                                                                                                        
mplayer: No such file or directory                                                                                                          
Failed to open LIRC support. You will not be able to use your remote control.                                                               

Playing /media/sda1/Users/Chris/Music/Blink 182/Take Off Your Pants & Jacket/03 First Date.mp3.
Audio only file format detected.                                                               
Clip info:
 Title: First Date
 Artist: Blink 182
 Album: Take Off Your Pants & Jacket
 Year: 2001
 Comment:
 Track: 3
 Genre: Alternative Rock
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 192.0 kbit/13.61% (ratio: 24000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...


With OSS = 
chris@chris-laptop-linux:~$ mplayer -ao oss /media/sda1/Users/Chris/Music/Blink\ 182/Take\ Off\ Your\ Pants\ \&\ Jacket/03\ First\ Date.mp3
MPlayer UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team                                                                                           
mplayer: could not connect to socket                                                                                                       
mplayer: No such file or directory                                                                                                         
Failed to open LIRC support. You will not be able to use your remote control.                                                              

Playing /media/sda1/Users/Chris/Music/Blink 182/Take Off Your Pants & Jacket/03 First Date.mp3.
Audio only file format detected.                                                               
Clip info:                                                                                     
 Title: First Date                                                                             
 Artist: Blink 182                                                                             
 Album: Take Off Your Pants & Jacket                                                           
 Year: 2001                                                                                    
 Comment:                                                                                      
 Track: 3                                                                                      
 Genre: Alternative Rock                                                                       
==========================================================================                     
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3                                          
AUDIO: 44100 Hz, 2 ch, s16le, 192.0 kbit/13.61% (ratio: 24000->176400)                         
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)                         
==========================================================================                     
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy                
Failed to initialize audio driver 'oss'                                                        
Could not open/initialize audio device -> no sound.                                            
Audio: no sound                                                                                
Video: no video                                                                                


Exiting... (End of file)


With esd i got the same error as with OSS is there a way to set MPlayer to default at alsa and not pulse?

---

### Post by mc4man on 2010-03-21
In your home directory there should be a hidden folder named
.mplayer and inside a file - config
(if not than create
Just add a line  - 
ao=alsa

Ex. of ~/.mplayer/config
> # Write your default config options here!
ao=alsa
#af = equalizer=0:0:0:0:0:0:0:0:0:0
#af=channels=6
vfm=ffmpeg

---

### Post by andrew.46 on 2010-03-21
And for the gui I would strongly suggest using a frontend such as SMPlayer which will allow you to easily change this preference from:

Options --> Preferences --> General --> Audio --> Output Driver

All the best,

Andrew

---

### Post by cscott0108 on 2010-03-22
Thanks all for helping with this problem, It did not solve the problem, but I think I will use SMPlayer.

---

