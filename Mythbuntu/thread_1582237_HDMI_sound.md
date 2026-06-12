---
title: "HDMI sound"
date: 2010-09-26
forum: Mythbuntu
---

### Post by axelsvag on 2010-09-26
I have trouble getting my HDMI sound inside mythtv. I have tried the suggestions 
Mostly from this [HTML]http://ubuntuforums.org/showthread.php?t=1498992[/HTML]

And I have succeded in getting a perfect sound outside mythtv and inside mythtv if I play from the music library. But playing a recording from my hvr1120 or playing an MP4 file in the video library does not seems to work as expected. The recordings is completely silent and the mp4 sound gives a very distorted sound with a whining sound. Does anyone have any suggestions where I should start?

---

### Post by barbex on 2010-09-26
I can't read that ubuntuforums post, it's too convoluted. 

Here's what I know: HDMI is a standard to transport video and audio through the same connection. In theory. I practice this seldom works, a lot of people use some kind of breakout cable to get the audio from the soundcard separately.

So how did you connect your system?

---

### Post by ian dobson on 2010-09-26
Hi,

Can you supply abit more information about your hardware/how is the sound being feed into the HDMI?

Can you add the output of aplay -l and aplay -L.

On my frontend I'm using a NVidia 9600gt with a SPDIF cable from my soundcard to the graphic card and have configured the Frontend to output audio to ALSA:default and configured ALSA to use the SPDIF output as the default output.

Regards
Ian Dobson

---

### Post by axelsvag on 2010-09-26
I am sorry I was a little bit short on information. The situation is like this. I have  a 64 bit Mythbuntu 10.04 with a GT240 card (suppose to give HDMI without a spdif extra connection)  installed, updated the alsa to 1.0.23 and when I enter the alsamixer I can choose the HDA Nvidia and it says alsa 1.0.23 in the top border.
So I hope everyting is alright so far. When I play a sound file outside mythtv everything is alright both on Totem, vlc and smplayer. When I enter Mythtv I can play sound from musiclibrary through mythtv, play movies from movies library except mp4 high def files, which give a very distorted sound with a high pitch.. 

Now I come to the problem which could be connected to my capture card which is a hvr-1120. If I schedule a recording with the analog side of the capture card the recording works as it suppose to. But when I watch it, the recording lacks sound. If I transform the nuv file using ffmpeg the mpg file also lacks sound. If I try to use the watch tv option I can a "wait" message for 5 sec and then I am kicked back to main menu. So the problem is more related to the capture card hvr-1120 and the mp4 problem in movies is a sideproblem.

---

### Post by ian dobson on 2010-09-26
Hi,

Can you try playing a recording with vlc or some other media player, just to see if the recording actually has sound.

If it doesn't the the problem is with your tuner.

Regards
Ian Dobson

---

### Post by axelsvag on 2010-09-26
Yes i have played the recording with vlc and totem since they do not seems to like the nuv file created I had to transform the file using ffmpeg to get a playable mpg or avi file. And no sound was present. But the mp4 mythtv problem could there be an easy solution there?

---

### Post by ian dobson on 2010-09-26
Hi,

It looks like it could be a "standard problem", see here [http://mythtv.org/pipermail/mythtv-users/2010-January/276554.html](http://mythtv.org/pipermail/mythtv-users/2010-January/276554.html)

Regards
Ian Dobson

---

### Post by axelsvag on 2010-09-26
It seems like that. But any suggestion for the mp4 problem. That seems to be a separate problem doesn't it?

---

### Post by axelsvag on 2010-09-27
I made some thinking about the problem. Maybe the problem come from the fact that I use the GT240 for both video and sound. Could it be some setting I have to do, to make the capture card hvr-1120 agree on the sound with the nvidia GT240?

---

### Post by scudderwagg on 2010-09-27
I have a Zontac GT220 card and I got the sound to work using the xbmc wiki entry ([http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)).  If you have sound working outside of Myth then the main problem might be with the sound setup in Myth.  Once I had sound working outside myth, I had to set mine to ALSA:hdmi in the setup.  Also make sure you have setup the sound.conf properly, that could cause issues if you system thinks you have more than one sound card.

---

### Post by GaryP2 on 2010-09-27
[FONT=Calibri][SIZE=3]In the MythTV frontend setup, try changing the following:[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Utilities > Setup > General > Audio System > Audio output device: **ALSA:plughw:0,7**[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Choosing **ALSA:plughw:0,7** was the magic that got my GT220 sound to output from HDMI with the MythTV frontend app. Try that value or others (such as **ALSA:hdmi** as the previous poster suggested). I give credit to this post in getting it to work (even though this is for XBMC). Look at some of the other suggestions, such as turning off onboard sound, to simplify things and help you get it working.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]_[COLOR=#0000ff][http://forum.xbmc.org/showpost.php?p=574448&postcount=147](http://forum.xbmc.org/showpost.php?p=574448&postcount=147)[/COLOR]_[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Don't give up ... you're probably just a setting or two away from making it work ... and when you finally get it working, you'll be elated![/SIZE][/FONT]

---

### Post by axelsvag on 2010-09-29
Maybe I got the the sound working  since it works with movies (except mp4) and music and outside mythtv. I have a weak theory that there could be a mismatch between the sound card and the sound piping through to the GT240. Am I completely wrong?

---

### Post by novellahub on 2010-09-29
Please display the output of the following commands:

```
aplay -l
```

```
aplay -L
```

I have a eVGA GT240 card working successfully with HDMI sound. Here are some of my setup notes:

[http://mythtvmadness.blogspot.com/2010/05/alsa-1023-upgrade.html](http://mythtvmadness.blogspot.com/2010/05/alsa-1023-upgrade.html)

---

### Post by axelsvag on 2010-10-07
I found something interesting in this "blog" [HTML]http://www.pindundin.de/[/HTML] If I understand the text right mythbuntu sees the capture card as a sound device and therefore the sound is going somewhere else. Can someone think of any suggestion, considering the info given.

---

