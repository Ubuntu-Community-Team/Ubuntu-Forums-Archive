---
title: "Audo Recorder shows wrong song time"
date: 2017-05-05
forum: Multimedia Software
---

### Post by bigjim8499 on 2017-05-05
I use Audio Recorder to record audio from utube. The last few times I have used it, it comes up with the wrong time length for the song. The song might be 3 min. and it will show 25 min. song length in Audacious. Is there any way to change this. It used to work right but now it doesn’t. I can not find a version #. When I play in Audacious it shows the correct play time, but the total time for the play list is way off. Any Ideas.      
JIm

---

### Post by TheFu on 2017-05-05
Skip the recording. Use **youtube-dl** to grab just the audio, then edit the files using whatever audio ending you want.  Best to get youtube-dl from github, not the Ubuntu repos, since it will need to be updated with every change to youtube.

---

### Post by moma on 2017-10-22
Hello,
Audio-recorder uses Gstreamer to do the recording job.  

You can easily debug and test the actual recording command.  
1) Start Audio-recorder and go to  [Additional settings] and select "Recording commands" tab.

2) Press the [Show Cmd] button to see the selected recording command.  

3) Then run the presented "gst-launch-1.0  -e pulsesrc...  bla.. bla..." command in a terminal window (press Cntr + T) to test if it works right with timing and timestamps.

You may need to install "gstreamer1.0-tools" package first. It contains the gst-launch-1.0 command. Run:
sudo apt install gst-launch-1.0

Let us know.
I am the programmer of Ar.
Ref: [https://launchpad.net/~audio-recorder](https://launchpad.net/~audio-recorder)

---

### Post by moma on 2017-11-30
Re-hello,
Edit the MP3 pipeline and remove "! xingmux ! id3mux" from the tail. Press save.
The xingmux may be the cause of erroneous recording length.

Do this:
Start Audio-recorder and go to [Additional settings] and select "Recording commands" tab.
Select mp3 and edit the pipeline. Remove "! xingmux ! id3mux" and save.

---

### Post by bigmell3 on 2018-03-11
I tried removing the xingmux and id3mux and that didnt work.  I increased quality from 2 to 0 while I was there.  The problem is audio-recorder uses vbr but isnt sure how long the file will last while you are recording.  When you hit the stop button it stops instantly but doesnt update the length properly and the length is determined incorrectly because of vbr somehow.  I used to fix this on my windows box using a vb app called vbrfix, but there is a linux version in the universe repository now.  The instructions are as follows.

[COLOR=#000000][FONT=&amp]sudo apt-get install vbrfix[/FONT][/COLOR]

[COLOR=#444444][FONT=&amp]vbrfix is a command line tool. To use it, open a terminal window and navigate to the directory containing the files that you want to fix. Then, issue the command:[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]vbrfix *in-file*.mp3 *out-file*.mp3[/FONT][/COLOR]

[COLOR=#444444][FONT=&amp]Where *in-file.mp3* is the file to be fixed and *out-file.mp3* is the fixed version of that file. You can also allow it to overwrite the old file with the newer, fixed version. Simply use the same file name for output as you use for input.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]vbrfix *file-name*.mp3 *file-name*.mp3[/FONT][/COLOR]

[COLOR=#444444][FONT=&amp]Now, if you would like to fix and overwrite all of the MP3 files in your working directory, you can use a loop like this. Note: this assumes your file extensions are all in lower case (.mp3).[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]for i in *.mp3; do vbrfix $i $i; done[/FONT][/COLOR]

[COLOR=#444444][FONT=&amp]I've never had a problem with vbrfix, but you might consider first copying your files to another directory make sure you don't screw up your original files.

That was a copy paste from tuxtweaks.  It is working for me now on both windows and linux.  Still using winamp.  Still whips the llamas ass.
[/FONT][/COLOR]http://tuxtweaks.com/2012/03/fixing-variable-bit-rate-mp3s-with-vbrfix/
[COLOR=#444444][FONT=&amp]

[/FONT][/COLOR]

---

### Post by robert3385 on 2018-03-13
well you can try this software: :popcorn:
[https://audio-recorder.en.softonic.com/](https://audio-recorder.en.softonic.com/)

---

### Post by mc4man on 2018-03-13
Nothing to do with audio-recorder, it's a longstanding flaw in gstreamer. At this point removing xingmux ! id3mux is ineffectual.
Best way to get good mp3 thru ar is to record to .wav or flac, then use lame to encode which has no such issues.

---

