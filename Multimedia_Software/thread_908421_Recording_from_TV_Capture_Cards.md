---
title: "Recording from TV Capture Cards"
date: 2008-09-02
forum: Multimedia Software
---

### Post by antron on 2008-09-02
I know you looked everywhere, tried everything, looking for a TV tuner program that would record, so you can get your VHS tapes to files.  As far as I can tell it doesn't exist, or doesn't work for Ubuntu. Or does it?

read this:
[http://www.transcoding.org/cgi-bin/transcode?Video4linux_Examples]("http://www.transcoding.org/cgi-bin/transcode?Video4linux_Examples")

put this command in a blank text file and name it capture.sh.:
```
transcode -x v4l2,v4l2 -M 2 -i /dev/video0 -p /dev/dsp0 -y ffmpeg -F msmpeg4v2 -g 720x480 -f 0,4 -I 1 -u 100 -Q 3 -Z 360x240,fast -E 48000,16,2 --lame_preset medium -o clip.avi
```

make the file executable in its properties window.
put it in a folder and double click it.  choose 'run in terminal'

it will dump whatever your tuner card is viewing to an NTSC mpeg4 file in that directory.  to end, press 'Ctrl + C'

you may have to change /dev/video0 to whatever your card is.
I had to change /dev/dsp0 to /dev/dsp to get sound recorded.
I also changed '-y ffmpeg -F msmpeg4v2' to '-y xvid4' to use xvid

you will need to install transcode and ffmpeg or xvid with synaptic first

other TV viewing programs should be turned off, but you must use them to set the channel or input first.

---

### Post by antron on 2008-09-02
I attached the script file; you will need to make it executable.  I added the xvid variant  also.  Remember that you may need to change video0 or dsp0 to what your cards are mapped as.  Run it in a terminal; if you don't you must go kill it in the system monitor or it will fill your hard drive (it will be listed as transcode). Ctrl+C stops the recording in the terminal.

---

