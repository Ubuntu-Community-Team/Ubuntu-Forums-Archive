---
title: "Recording the internal audio is far too complicated task."
date: 2010-07-10
forum: Multimedia Software
---

### Post by moma on 2010-07-10
Hello,
Outputting/recording the internal audio to an ogg file.

Sometimes I listen to the internet radio or similar and want quickly and easily start RECORDING the sound so I can re-play it later (from an file).

It is now possible to do the recording, but it is unncessarily complicated and unintuitive task to do.
This is the current method:

1) Start playing the sound; a local music file or youtube content, what ever audio you like.

2) Install and start the "Sound Recorder" application. 
Start it from the Applications -> Sound & Video menu. Press the red-button to start the recording, "kind of". 

See the attached picture1.png

3) Install and start the PulseAudio Sound Control application. This is the "pavucontrol" package and tool.

4) In the pavucontrol, select the [Recording] tab-page.
 
5) Select the "Monitor + name-of-your-sound-card..." from the list. Now the recording should actually start.

See the attached picture2.png

WTF*!*
------------

This is what an ordinary computer user expects to do when recording adhoc audio to a file for later re-play.

1) Click the loudspeaker icon on the toolbar.
The small popup-dialog with sound controls appears.

2) The dialog has a record button. 
Click the record-button and a small edit field with auto-suggested file name appears. User can change the file name.

3) The loudspeaker icon now indicates that recording is on.

4) User can stop the recording by clicking the icon. 

Output is saved to user's /home/Media directory. This folder replaces the old /home/Video/ directory.
------------

My audio-card is an old SoundBlaster Audigy 2.

---

### Post by Naitsirhc Hsem on 2010-07-10
One word, Audacity

---

### Post by ron999 on 2010-07-10
Hi
I use SoundRecorder with Ubuntu Karmic.

This works for me:-

Setup
1. Install all restricted multimedia packages.
2. System---> Preferences----> Sound
3. “Hardware tab”, select ANALOG STEREO OUTPUT in PROFILES.

Use
4. Play any music or flash video from web.
5. Open Default Gnome sound recorder, Set to CD quality lossless [flac] or other format.
6. Click RECORD.
7. Stop Recording and save file.
;)

---

### Post by moma on 2010-07-14
Hi, thanks for your answers and methods. 

I think the best solution is to create a new GNOME-applet that is attachable to the toolbar. It should have 
* A [REC]/[STOP REC] toogle button.
* Audio source listbox; Record from microphone, from sound card X. 
* Output format listbox; OGA, FLAC, MP3, WAV.
* Editable field for the output filename.
* Use GStreamer to do the actual recording and file format job.

Some samples. Play some audio and record the output from the default sound-card to a file. Type these commands on the command line.
```
  WAV:
  $ gst-launch-0.10 pulsesrc ! queue ! audioconvert ! wavenc ! filesink location=test.wav

  OGG:
  $ gst-launch-0.10 pulsesrc ! queue ! audioconvert ! vorbisenc ! oggmux ! filesink location=test.oga

  FLAC:
  $ gst-launch-0.10 pulsesrc ! queue ! audioconvert ! flacenc ! filesink location=test.flac

  MP3 ("lamemp3enc" is the preferred encoder, "lame" is deprecated):
  $ gst-launch-0.10 pulsesrc ! queue ! audioconvert ! lamemp3enc ! filesink location=test.mp3

  AAC, .m4a (Important: the **-e** option terminates the stream properly when you hit cntr+c):
  $ gst-launch-0.10 -e pulsesrc ! queue ! audioconvert ! faac ! mp4mux ! filesink location=test.m4a

  If PulseAudio (pulsesrc) is not installed, fall back to ALSA source(alsasrc) or even to OSS source (osssrc).
  See "gst-inspect-0.10 | less" and "gst-inspect-0.10 elementname" for more options. 
```

I will simply convert these pipelines to C code and bake it all to a Desktop-button and GNOME-applet.

Looking to start this project very soon.
Whould it be better to create an applet for the new GNOME 3.0 instead of this older GNOME 2.x. I think GNOME 3.0 prefers Javascript and Javascript bindings for Desktop/Applet-programming.

I have also tested this
[http://www.omgubuntu.co.uk/2010/07/quickly-record-soundcard-output-in.html](http://www.omgubuntu.co.uk/2010/07/quickly-record-soundcard-output-in.html)
It's Gambas based. But I really prefer a nice and quick recorder-applet on the toolbar.

---

### Post by moma on 2010-07-25
Re-hello,

OK, I have now coded the first version of the audio-recorder-applet. Here is a demo ;-)

EDIT: See [https://launchpad.net/~osmoma/+archive/rec-applet](https://launchpad.net/~osmoma/+archive/rec-applet)  
and [https://launchpad.net/rec-applet](https://launchpad.net/rec-applet)

BTW: What color does normally indicate "recording on"?

---

### Post by NFblaze on 2010-07-25
Pretty cool app. Much better than the SoundRecorder method.

I normally use arecord. Though this is interesting.

Perhaps you can create a time-limite timer. So it auto stops.

---

### Post by moma on 2010-07-26
>>Perhaps you can create a time-limite timer. So it auto stops.
Very good idea. I will see to it later. 

Will also add a small amplitude indicator to the GUI or applet itself. Pause-button would also be a nice feature.

Also, maybe best to put the "Settings>" to a separate dialog even I like to have "Audio source" (the device) and "File format" immediately available.

---

### Post by moma on 2010-08-05
Re-hello,

Audio Recorder Applet (rec-applet):

The first official version (v 0.1) of "Audio Recorder Applet" is now ready. See video demo: [http://www.futuredesktop.com/tmp/audio-recorder/recorder-applet-v0.1.ogv](http://www.futuredesktop.com/tmp/audio-recorder/recorder-applet-v0.1.ogv)

Source code is avail. on the Launchpad: [https://launchpad.net/rec-applet](https://launchpad.net/rec-applet)
The project name is "rec-applet".
Instructions in [README]("http://bazaar.launchpad.net/~osmoma/rec-applet/trunk/annotate/head%3A/README") and [INSTALL]("http://bazaar.launchpad.net/~osmoma/rec-applet/trunk/annotate/head%3A/INSTALL") files.

I will try to create a PPA-repository for this product. If success, you may download ready-made .deb packages from      [https://launchpad.net/~osmoma](https://launchpad.net/~osmoma)  
See "rec-applet" personal package archive.

Most kindly
 Moma Antero,

---

### Post by VastOne on 2010-08-05
> **moma said:**
> Re-hello,

Audio Recorder Applet (rec-applet):

The first official version (v 0.1) of "Audio Recorder Applet" is now ready. See video demo: [http://www.futuredesktop.com/tmp/audio-recorder/recorder-applet-v0.1.ogv](http://www.futuredesktop.com/tmp/audio-recorder/recorder-applet-v0.1.ogv)

Source code is avail. on the Launchpad: [https://launchpad.net/rec-applet](https://launchpad.net/rec-applet)
The project name is "rec-applet".
Instructions in [README]("http://bazaar.launchpad.net/~osmoma/rec-applet/trunk/annotate/head%3A/README") and [INSTALL]("http://bazaar.launchpad.net/~osmoma/rec-applet/trunk/annotate/head%3A/INSTALL") files.

I will try to create a PPA-repository for this product. If success, you may download ready-made .deb packages from      [https://launchpad.net/~osmoma](https://launchpad.net/~osmoma)  
See "rec-applet" personal package archive.

Most kindly
 Moma Antero,

Hi,

I am trying to get this from the launchpad site but it is reporting that there are no files to download.

I would like to try this out if I can get the source.

---

### Post by moma on 2010-08-06
Hello,

I just managed to create a PPA (personal package archive) and there should be a .tar.gz source available.

Look into:
[https://launchpad.net/~osmoma/+archive/rec-applet/+packages](https://launchpad.net/~osmoma/+archive/rec-applet/+packages)

Click the "rec-applet - 0.1" link and you should see the .tar.gz file there.

The Launchpad's server had not yet (at this moment) compiled the source to installable .deb package. It reported that compilation would start within the next 15 minutes. If success, it will generate both 32 and 64bit .deb packages. 

EDIT: The compilation failed due to missing libgstreamer-plugins-base0.10-dev package. Fixing it and re-uploading.
---

Note: This "rec-applet" has two web pages on the Launchpad.

The 1.st one holds the development code managed by Bazar (bzr).
See: [https://code.launchpad.net/~osmoma/rec-applet/](https://code.launchpad.net/~osmoma/rec-applet/) 

I just wonder if you can get the source code by issuing this command.
$ **bzr branch lp:~osmoma/rec-applet/trunk**
Or do you need special access rights for that?
This will give you the latest code.

Then you would just enter to the directory and 
$ ./configure 
$ make 
$ sudo make install   

The 2.nd page is the PPA that provides ready-made Debian/Ubuntu packages (also .tar.gz ball). 
See: [https://launchpad.net/~osmoma/+archive/rec-applet](https://launchpad.net/~osmoma/+archive/rec-applet)
This will give you the original (old) .tar.gz ball + diff patches. 

I hope other people will contribute to the code, improve the code quality, fix bugs, translate the program to other languages etc.

---

### Post by VastOne on 2010-08-06
Moma,

There was one more dependency that I had to add before ./configure would work, intltool.

Once I added that it compiled and make all went well and I am now recording.

One other issue is cosmetic, as the app uses the the system colors for the panel but it is not transparent like everything else. Not a big deal but it looks strange on my transparent setup.

I am also wondering if it could be setup to use the dbus functions in that it when a dbus change is made, ie a new song starts from the source, if it could then end that file that was recording and begin a new one.

I know that would require a re-write but it could make this a powerful tool.

---

### Post by janerikb on 2010-08-06
Record = red, play = green.

---

### Post by moma on 2010-08-06
Hi,
Thank you for testing it.

Yes, I can now see that the applet is opaque, it does not obey the panel's color setting. It should be easy to fix.

Also the applet is too long. The applet's GtkHBox (if top/bottom panel) expands too much.

That DBus thing could be an interesting feature.

---

### Post by VastOne on 2010-08-06
For anyone using this for the first time please note that there is a status indicator to the right of Start/Stop Recording that will move when you have a correct Audio Source selected.

So, once you start to record, make sure you are seeing activity on this status-bar.  On mine, the Default did not record so I had to select another one from Audio Source and there are multiple choices (at least on mine). I would recommend that you record some test samples of those that work and play them back and judge which is best.

---

### Post by moma on 2010-08-06
Hello,

VastOne: Interesting observation that the "default" device did not produce sound. 

I think the code should use either "gconfaudiosrc" or "autoaudiosrc" element for the Default-device. 

Eg.:
$ gst-launch-0.10 autoaudiosrc ! audioconvert ! wavenc ! filesink location=record.wav

The default value is set in the GConf registry, start gconf-editor, and browse to key /system/gstreamer/0.10/default

See also:
$ gst-inspect-0.10 gconfaudiosrc
$ gst-inspect-0.10 autoaudiosrc

---

### Post by hok00age on 2010-08-07
I've made PPA for rec-applet. Special thank's to Moma.... But I can't wait for your PPA build, so I decided to upload your code to my PPA....
```
sudo add-apt-repository ppa:tldm217/tahutek.net
sudo apt-get update
sudo apt-get install rec-applet
```

All Credits go to Moma

Sorry for my bad English
I'm Indonesian.

---

### Post by moma on 2010-08-08
Hello,

hok00age: Thanks for the PPA.

My upload to Lauchpad/PPA is ok, but the compilation there fails. 

My commands are:
$ cd rec-applet
$ debuild -S -sd
$ cd ..
$ dput ppa:osmoma/rec-applet rec-applet_0.1-1~lucid_source.changes
-----

**EDIT**: Good news.
I just re-uploaded the source and it compiled successfully. hmm.
[https://launchpad.net/~osmoma/+archive/rec-applet/+packages](https://launchpad.net/~osmoma/+archive/rec-applet/+packages)

---

### Post by luctor on 2010-08-08
> **janerikb said:**
> record = red, play = green.
+1

---

### Post by hok00age on 2010-08-08
> **moma said:**
> Hello,

hok00age: Thanks for the PPA.

My upload to Lauchpad/PPA is ok, but the compilation there fails. 

My commands are:
$ cd rec-applet
$ debuild -S -sd
$ cd ..
$ dput ppa:osmoma/rec-applet rec-applet_0.1-1~lucid_source.changes
-----

**EDIT**: Good news.
I just re-uploaded the source and it compiled successfully. hmm.
[https://launchpad.net/~osmoma/+archive/rec-applet/+packages](https://launchpad.net/~osmoma/+archive/rec-applet/+packages)

Congratulation mate!

But you'd better build for karmic and maverick too, and then I'll delete rec-applet from my PPA and let my friends know the official PPA has been created, ppa:osmoma/rec-applet

---

### Post by moma on 2010-08-08
Hi,

hok00age: Keep your PPA around for a while. 
I'll be away several days, hiking and walking on mountains. Thanks.

It should be easy to generate packages for Maverick and Jaunty too. 
Changing the debian/changelog file. But testing on a local machine or VM is also important.

---

### Post by VastOne on 2010-08-08
> **moma said:**
> Hi,

hok00age: Keep your PPA around for a while. 
I'll be away several days, hiking and walking on mountains. Thanks.

It should be easy to generate packages for Maverick and Jaunty too. 
Changing the debian/changelog file. But testing on a local machine or VM is also important.

Enjoy that hike!

---

### Post by hok00age on 2010-08-08
> **moma said:**
> Hi,

hok00age: Keep your PPA around for a while. 
I'll be away several days, hiking and walking on mountains. Thanks.

It should be easy to generate packages for Maverick and Jaunty too. 
Changing the debian/changelog file. But testing on a local machine or VM is also important.

Very well mate! Enjoy your trip...

---

### Post by DayLite on 2010-08-09
> **hok00age said:**
> I've made PPA for rec-applet. 
```
sudo add-apt-repository ppa:tldm217/tahutek.net
sudo apt-get update
sudo apt-get install rec-applet
```All Credits go to Moma


I am new to Ubuntu and don't understand the technical stuff. I did copy the code to my terminal and ran it. I see you in 'software sources'. 

I can't find where rec-applet was installed. Please help me to find it :(

Thank you

---

### Post by VastOne on 2010-08-09
> **DayLite said:**
> I am new to Ubuntu and don't understand the technical stuff. I did copy the code to my terminal and ran it. I see you in 'software sources'. 

I can't find where rec-applet was installed. Please help me to find it :(

Thank you

Right Click on your top panel and Click Add To Panel

From there click on the  Audio Recorder Applet and click Add at the bottom, and then close

Now the Applet is on your Top Panel

---

### Post by DayLite on 2010-08-09
> **VastOne said:**
> Right Click on your top panel and Click Add To Panel

From there click on the  Audio Recorder Applet and click Add at the bottom, and then close

Now the Applet is on your Top Panel

:D Thank you. I have it now and it works GREAT:D

---

### Post by hok00age on 2010-08-10
> **DayLite said:**
> :D Thank you. I have it now and it works GREAT:D

I agree with you, I like this applet too.....

---

### Post by moma on 2010-08-17
Hello again,

I have now released v0.2 of the Audio Recorder Applet.
[https://launchpad.net/~osmoma/+archive/rec-applet](https://launchpad.net/~osmoma/+archive/rec-applet)

It has got a lot of improvements since the first release. See
[https://code.launchpad.net/~osmoma/rec-applet/trunk](https://code.launchpad.net/~osmoma/rec-applet/trunk)

* There are packages for Ubuntu 10.04 (Lucid). 

* Packages for Ubuntu 9.10 (Karmic) should be ready within an hour.

* Unfortunately compilation for Ubuntu 10.10 (Maverick) failed. **So Maverick packages must wait**. Strange enough, I can compile Maverick version on my machine, so grab the source and compile it yourself ;-) The INSTALL file will tell you how.
EDIT: There are some issues when ran on the Maverick. Wait till Maverick has stabilized and rec-applet has been fixed!

I consider this v0.2 release as "[COLOR="Blue"]**final**[/COLOR]" for this season. Going to start a new project that allows you to search and download/paste/copy clipart in a very easy manner. Connecting it to the OpenClipArt library. It's gonna be a useful but also funny gadget to use.

---

### Post by DayLite on 2010-08-17
> **moma said:**
> Hello again,

I have now released v0.2 of the Audio Recorder Applet.
[https://launchpad.net/~osmoma/+archive/rec-applet]("https://launchpad.net/%7Eosmoma/+archive/rec-applet")

It has got a lot of improvements since the first release. See
[https://code.launchpad.net/~osmoma/rec-applet/trunk]("https://code.launchpad.net/%7Eosmoma/rec-applet/trunk")


Hope you enjoyed your vacation. Glad you are back. I am not sure I followed your instructions correctly. This is what my terminal says. I just went to my source editor in Tweak and now have your latest version. Thank you for creating a wonderful applet. It is just what I wanted and you made it a reality, thanks

---

### Post by VastOne on 2010-08-17
Info- I have loaded v.02 successfully and all is running perfectly and the icon has been corrected.

The pulseaudio improvements are very noticeable too..

Great job!

:popcorn:

---

### Post by alanwalterthomas on 2011-01-04
I've tried every possible setting with 10.10 but I only get silence. Any chance of a fix?

---

### Post by moma on 2011-01-21
Hello all,

Rec-applet will be replaced by a new product. If everything goes well, the new "audio-recorder" software will be packaged and launched very soon.

Please read more about the new "audio-recorder" here. Your help is very much needed to test it.
[http://ubuntuforums.org/showthread.php?t=1672679](http://ubuntuforums.org/showthread.php?t=1672679)

Greetings
 Moma Antero.

---

