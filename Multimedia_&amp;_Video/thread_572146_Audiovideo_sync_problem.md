---
title: "Audio/video sync problem"
date: 2007-10-10
forum: Multimedia &amp; Video
---

### Post by Davis_jacob on 2007-10-10
well I am converting using the imtoo DVD ripper platinum, I have been working for about a week now and yet when I watch the video (mp4) on my video ipod or my blackberry 8830 the audio place about 1 second before the mouth actually moves, anyone else with this similar issue or anyone know how to fix it???

---

### Post by GrouchoMarx on 2007-10-17
Unfortunately I'm not familiar with that particular program, but if you are willing to try something else, I can recommend Handbrake for ripping ffmpeg, xvid, or x264 into various formats (avi, mp4, and mkv), including special presets for the ipod:

[http://handbrake.m0k.org/trac/wiki/CLIGuide]("http://handbrake.m0k.org/trac/wiki/CLIGuide")

There is no GUI for Handbrake on linux, but once you get over the sheer length of some of the commands, then you realize how much faster it actually is to copy and paste all the specific configurations into the CLI than it is to set them through the GUI. Here is a list of presets that you can copy and paste, and the ones for ipod are listed as well:

[http://handbrake.m0k.org/trac/wiki/BuiltInPresets]("http://handbrake.m0k.org/trac/wiki/BuiltInPresets")

If you just want to fix the audio sync, and aren't really concerned about encoding, then you can try doing so with Avidemux in simple copy mode. It should be a trivial process of opening the file (you don't need to unpack it), setting the audio shift in milliseconds, and then saving the file.

[http://www.avidemux.org/admWiki/inde...=Audio_filters](http://www.avidemux.org/admWiki/inde...=Audio_filters)

Note: "If you are editing a file with variable bitrate audio, run Audio->Build VBR Time Map before you do any editing. Otherwise your audio will be out of sync."

Hope this helps.

---

