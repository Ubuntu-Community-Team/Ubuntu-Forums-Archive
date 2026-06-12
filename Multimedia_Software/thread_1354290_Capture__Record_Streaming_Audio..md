---
title: "Capture / Record Streaming Audio."
date: 2009-12-13
forum: Multimedia Software
---

### Post by tm-hart on 2009-12-13
[B]Capture / Record Streaming Audio with Ubuntu 9.04 and VLC
[/B]
To record streaming audio:

(a) Install the VLC media player with Synaptic.  VLC includes vlc, vlc-nox, vlc-data, libviccore0, libvlc2, libvcdinfo0 and libavcodec52. 

(b) Determine target web address.  This may require testing Listen Now,  MP3 or Media Player options on the web site and saving and reading a shortcut file.  

Examples:  A local college radio station offers a “Media Player” option.  Choose “Save File” to create a “.wax” file.  Open the file with a text editor and copy the site address.

The local NPR station offers a “Listen With” option for “MP3”.  Saving the link creates a “.m3u” file. Open the file with a text editor and copy the site address.

(c) Test the audio stream with VLC.  The menu commands are:

- MEDIA.
- OPEN NETWORK.
- [ enter site address ]
- PLAY.

(d) Test saving the audio stream to a file.  The menu commands are:

- MEDIA.
- CONVERT / SAVE.
- NETWORK.
- [ enter site address ]
- CONVERT / SAVE.
- OUTPUT options:
- Check FILE box and enter NAME.
- PROFILE options:
- The AUDIO CODEC is MPEG-2. 
- Check the AUDIO box. 
- Select MPEG AUDIO.  [Test other options if needed.]
- Do not check the STREAM ALL box.
- SAVE
- This will create the audio file.  
- Click STOP to finish.

 **Capture / Record Streaming Audio with Ubuntu 9.10 and VLC**

To record streaming audio:

(a) Install the VLC media player with Synaptic.  VLC includes: vlc, vlc-nox, vlc-data, vlc-plugin-pulse, libviccore2, libvlccore-dev,  libvcdinfo0 and libavcodec-unstripped-52.
 
(b) Determine target web address.  This may involve going to a Listen Now,  MP3 or Media Player  option on the web site and saving a file.  

Examples:  A local college radio station offers a “Media Player” option.  Choose “Save File” to create a “.wax” file.  Open the file with a text editor and copy the site address.

The local NPR station offers a “Listen With” option for “MP3”.  Saving the link creates a “.m3u” file. Open the file with a text editor and copy the site address.

(c) Test the audio stream with VLC.  The menu commands are:

- MEDIA
- OPEN NETWORK
- [ enter site address ]
- PLAY

(d) Test saving the audio stream to a file.  The menu commands are:

- MEDIA
- CONVERT / SAVE
- NETWORK
- [ enter site address ]
- CONVERT / SAVE
- DESTINATION:
- Enter path and audio file name.
- Note:  If the DISPLAY THE OUTPUT box is checked, the audio plays and saves.  Left unchecked, audio is saved, not played.
- PROFILE:
- Set to MP3.
- START 
- Press STOP to finish.

---

