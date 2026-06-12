---
title: "Archiving radio recordings"
date: 2009-09-08
forum: Mythbuntu
---

### Post by DrCrispPacket on 2009-09-08
I record a lot of radio programmes that are available on Freeview in the UK and can be captured with a DVB turner; for example I am recording the current series of Promenade concerts from the BBC on Radio 3.

I have no trouble listening to the recordings in MythTV (using the Watch Recordings menu selection) but am having problems archiving them. 

Ideally I would like to write the recordings to a CD/DVD or an MP3 file for an MP3 player. I thought I could use Mytharchive, but when I select the files I want, set them for no re-encoding (otherwise they appear on the list of files for processing as size 0), and then start the DVD writing process going, I get the following error:

> Didn't find any video elements in stream info fileand the process terminates.

Can anyone suggest either a command line or GUI method for processing the files? They appear as .mpg files in directory listings, just like all the tv files with video, but of course they don't have any video component (as the error message says).

I could, of course, apply various command line filters to transcode the files into an mp3 format, but it is difficult to identify the recording from its filename alone - possible though tedious for a single file, horrible for a large number of recordings.

---

### Post by squaregoldfish on 2009-09-08
I use mplayer to convert the files to WAV for editing, but you can convert them to whatever format you like, even if you have to pass the output through lame to make an mp3.

```
mplayer -vc null -vo null -ao pcm:fast:file="$1.wav" "/Media/Recordings/$1"
```Steve.

---

### Post by DrCrispPacket on 2009-09-11
> **squaregoldfish said:**
> I use mplayer to convert the files to WAV for editing, but you can convert them to whatever format you like, even if you have to pass the output through lame to make an mp3.

```
mplayer -vc null -vo null -ao pcm:fast:file="$1.wav" "/Media/Recordings/$1"
```Steve.

Thanks - works a treat

---

### Post by DrCrispPacket on 2010-02-16
I find the easiest way to proceed is:

Use the [COLOR=Navy][Mythrename]("http://www.mythtv.org/wiki/Mythrename.pl")[/COLOR] script to create a subdirectory called show_names containing named links (with descriptive names allowing the recordings to be easily identified) within the recordings folder.

Start up the VLC media player: if you haven't got it, use
```
sudo apt-get install vlc

```Select **Media -> Convert/Save** and navigate to the desired file in the show_names folder, select the file and press **Convert/Save**. You will be presented with a dialog that allows you to select the required output format (WAV, MP3 etc) and the output filename. Then press **Save**. Job done!

---

