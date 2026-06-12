---
title: "From video camera to a subtitled short movie online"
date: 2011-05-31
forum: Multimedia Software
---

### Post by Mariane on 2011-05-31
There is certainly more than one way to do it, but the method I relate here is guaranteed to have functioned at least once under Ubuntu 10.10. It is not a detailed "HowTo" - I am no expert, this is my first attempt at video editing. But I hope it can still help people by putting together information I often had to search for piece by piece. 

To start with I used dvgrab to copy the files from the video camera to the computer:

```

sudo dvgrab -f hdv tryvideo

```

There are ways to get dvgrab to function without running it as root but you have to fiddle. The port is called something like ieee raw1934, the camera knows nothing about giving file permissions to your Ubuntu user name... It works harmlessly as root, if you want to fiddle best of luck to you. 

dvgrab created several files called tryvideo001.m2t, tryvideo002.m2t, etc. They could be played back with vlc. But they could not be opened by kdenlive for video editing, so I used avidemux to convert them to .avi. First conversion. Kdenlive allows you to stick the pieces back together again, to select the parts you want to keep very precisely, to add a sound track (i.e. music), etc. Hint: if you want to have music during one part of the video and the original sound (i.e. talk) on another, you can add the 2 pieces of video on 2 different lines of kdenlive. You can mute a whole line (little button at the left of the line), which can contain several pieces of video, but you cannot mute one piece among many on the same line. The first 3 lines are for video, the bottom 2 lines are for sound. 

Kdenlive did not have the options I wanted for sound editing, so I used 3 programs: mplayer, audacity and mencoder. 

mplayer extracts the sound file from the video:

```

mplayer -vo null -ao pcm:file=sound.wav inputvideofile.avi

```

Audacity edits the sound file sound.wav, separate left and right audio tracks, clean the sound, etc. 

Audacity has a bad behaviour, reminding of some non-free software, of always wanting to save in it's own format, which only itself can read. So remember not to save with "File/Save" but with "File/Export". If you plan to go back to work again on the file it is better to save it as .wav, this way you won't loose sound quality through compression. Anyway Avidemux and other video program can change that into mp3 or other formats. If you export as mp3 remember 0 is better than the default value of 2, and 9 is the worst. REMEMBER THE BIT RATE. If it is 160 and some other program later sets it to 128 the sound will be accelerated and will become squeaky.

Hint: Leaving blanks (total silence) in the sound track of a video sounds really strange. You can blank a part by selecting it, doing "Effect/Amplify" and dragging the level to the minimum. Whatever you do don't do "Edit/Cut" because this would shorten the length of your sound track and it would no longer fit with the video. If you want to blank out an unwanted short noise you can select a bit of pure background noise OF THE SAME LENGTH and paste it over the unwanted noise. Background noise may be considered undesirable by purists but it sounds better than a blank when you playback your video. 

Mencoder puts the cleaned sound track back into the video file: 

```

mencoder -o outputvideofile.avi -ovc copy -audiofile sound.wav -oac pcm inputvideofile.avi

```

Mencoder worked at first, a few times. Then it started complaining it couldn't find outputvideofile.avi. I copied inputvideofile.avi to another directory, renamed it outputvideofile.avi, and moved it back to the original directory. This made mencoder happy and it worked again. 

Kdenlive rendered the edited video as avi, but it was huge: 1.2 GB for 5'30'' of video! So I used avidemux again to shrink that to around 100MB. Second and third conversions. 

Then I used subtitlecomposer to write the subtitles. It displayed them in a rather ugly way, jagged and yellow, but this changed later without my having to do anything about it. Subtitlecomposer is easy to use, very intuitive. I saved the subtitles in .as format (spelt with double 's', if I post that it gets censored). The default format is really called like that, I'm not making a silly joke. 

Another subtitling program is subtitleeditor but it didn't work by default on my machine, though other people have reported it works fine for them. 

Hint for subtitling programs: Don't think it is failing if it does not display your video when you do "File/Open". "File/Open" is used to open subtitle files (.as or .srt, etc.). The way to open your video is to do "Video/Open". 

Then I used mkvmerge (mkvtoolnix-gui package and "MKV files creator" in Applications/Multimedia) to group the subtitles file with the video file. This created a file with a .mkv extension which could be viewed with vlc. It was not a bad idea to watch it, though by this time I was sick of this video, because it showed some mistakes in the subtitles. The subtitles were rather too large and white with a thin black border, but this changed later (again).

I had to use mkvmerge before using HandBrake, because I wanted to hard code the subtitles. Leaving them in a separate file meant that some people somewhere were bound to encounter problems when trying to read them - or would simply never notice there were subtitles to this video. Handbrake can only hard code subtitles (in .as format with double 's') which have already been included in the video file by mkvmerge, it cannot hard code subtitles opened as a separate file. 

Handbrake is one of these programs which is in an unusual repository. You have to add the repository to your sources.list file: 

```

sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake

```

Handbrake cannot be launched from the command line but can be found with the mouse in the list of multimedia applications under the name of "DVD Ripper". Handbrake can be used for other things too, for example to crop a video (removing the sides of the picture) or to change the format from 4/3 to 16/9 or whatever you want. It saves in .m4v format and writes nice subtitles in a font which looks like Times New Roman. They are white with thick dark blue sides, easy to read whatever the colour of the background picture. HandBrake did the fourth conversion. Avidemux did the fifth, because I had to get the video back into .avi format. 

Finally, I used Konqueror to upload the file to the server. I also used it at various stages to check the size of the video files and to look online for information about how to do this or that. 

I have used 10 programs: dvgrab, avidemux, mplayer, audacity, mencoder, kdenlive, subtitlecomposer, mkvmerge, handbrake and konqueror. And my poor video file has been converted 5 times. If this was a text file, it would be like using one program to add a title, one program to justify the text, one program to add a picture, one program to add page numbers, etc... Two full days of work for 5 minutes of video! But it's worth it, if you try it you'll feel so proud of your very own video clip :). 

Another apparently well-known video editor is cinelerra, but amd64 packages (this means packages for 64 bits architectures) were unavailable at the time I was looking for a video editor. Now they are available and you can get it: 

```

sudo add-apt-repository ppa:cinelerra-ppa/ppa
sudo apt-get update
sudo apt-get install cinelerra

```

As opposed to kdenlive, cinelerra has a rather forbidding-looking interface and 2 lines, one for video and one for audio, as opposed to kdenlive 5 lines. Maybe this can be configured. I think kdenlive is easier for total beginners. 

I have a souvenir on my desktop. Plugging and unplugging the firewire cable to link the video camera to the computer has triggered the appearance of a yellow note which says "libieee1284-3". This stays in the bottom-right corner of Desktop number 3 whatever I do. I'll have to ask about how to get rid of it on the Ubuntu forums, and meanwhile I have one more reason to be grateful for multiple desktops :). 


Mariane

---

