---
title: "no sound in mpeg,wmv,avi, etc, but..."
date: 2006-06-01
forum: Multimedia &amp; Video
---

### Post by s0ad on 2006-06-01
I can hear audio streams (online radio stations) and individual mp3 files. what information do you need from me to help you help me?  I have 6.06 installed, w32codecs package installed. the system I am using is a Dell dimension 4300, and my audio output is a logitech usb headset.

---

### Post by Sutekh on 2006-06-02
I can only really go on the [Ubuntu Wiki - Restricted Formats]("https://wiki.ubuntu.com/RestrictedFormats") page.

You should start with installing these packages after [enabling the universe and multiverse repositories](https://wiki.ubuntu.com/AddingRepositoriesCliHowto)
> sudo apt-get gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-main1 libxine-extracodecs 

---

### Post by s0ad on 2006-06-05
well, I have just installed xubuntu dapper drake release. i went through the 'restricted formats' page and i also ran "automatix".  i still can't listen to mp3s.  I don't know if I did something wrong or not, but can someone please help me?

---

### Post by gandalf100 on 2006-06-05
[QUOTE=s0ad]well, I have just installed xubuntu dapper drake release. i went through the 'restricted formats' page and i also ran "automatix".  i still can't listen to mp3s.  I don't know if I did something wrong or not, but can someone please help me?[/QUOTE]

first you should find out, wether you have sounds at all:
/usr/share/sounds
you can try some sounds

if yes:

this howto ist written for kubuntu its a small solution and propably helps you:
[http://kubuntuforums.net/forums/index.php?topic=5683.0](http://kubuntuforums.net/forums/index.php?topic=5683.0)

---

### Post by s0ad on 2006-06-05
hey gandalf, 

I do have .wav files in that directory.  When I first tried to play them they worked, but I got no sound.  But then I remembered I had a soundcard installed, but it's not supported by Linux, so I decided to take it out.  I also decided to turn off my integrated audio, so now the only sound device of any kind hooked up to my computer is my pair of usb headphones.  Then I started the computer back up, and bame, I could play mp3s, I got sound from video files, and I could hear those .wav files.  I should have done that in the beginning, but I totally didn't think about it. 


I do have 2 new questions though, for you or anyone else

1.  Now I can hear all this audio, but I can't seem to control the volume level.     I have some volume control things on the top panel, but they don't seem to be working.  And I also have a volume control directly tied onto the usb cord of the headphones, but it also doesn't work.


edit: It seems the volume control in Rhythmbox works, but it doesn't in xfmedia,vlc,and some others.

2.  I am using Rhythmbox for my music library and music player.  It seems nice, its features and setup and all, but it refreshes/remakes the library everytime I start the software.  Is there any way I can have it stop doing this, as I have a large music collection and it takes some time to complete.

Thanks again for the help.

---

