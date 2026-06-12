---
title: "Karmic Koala: Sound works selectively..."
date: 2010-04-14
forum: Multimedia Software
---

### Post by Gerdion on 2010-04-14
Wierdness involving my recent upgrade all the way from Hardy Heron up to Karmic Koala on my HP laptop. Currently the sound card is working and is recognized by Ubuntu and I can hear the test sounds. I can also open Decibel and listen to music.

What I can't do is listen to audio coming through Firefox or Amarok or even Dwarf Fortress. It seems that my audio is working for some programs but not others. What gives?
:confused:

---

### Post by lidex on 2010-04-14
Did you upgrade directly from hardy to karmic?
Have a look here:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
'Part A' here:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by Gerdion on 2010-04-14
I upgraded from version to version up to Karmic using the Update Manager. I didn't think that it would cause such a problem. 

Tried the links, followed the instructions but still no sound in Firefox or Amarok. In fact, I didn't seem to meet much of it's problem criteria. According to the long Symptom tests, I don't have any problems (at least as far as Pulse Audio is concerned).

 Upon getting back on my machine, I discovered that Dwarf Fortress - Linux Native runs it's sound just fine now. 

Perhaps something else is wrong?

---

### Post by kostkon on 2010-04-14
Did you try to setup your sound (again) in *System &#8594; Preferences &#8594; Sound*?

Also, before doing the setup, you could try deleting the *.pulse* folder in your home and then logging out and in.

Go to your home, select *View &#8594; Show Hidden Files*, find the folder and delete it.

Or you can do it in a terminal
```
rm -rf ~/.pulse
```
Don't forget to logout/login, afterwards. Then, select *System &#8594; Preferences &#8594; Sound*.

---

### Post by Gerdion on 2010-04-14
Very odd. I deleted the hidden pulse folder and logged out, then logged back in again as myself. It was back again! Is it restoring itself? I go back and do what in the Sounds window? Volume is up about midway and not muted. Amarok still not working and neither is Firefox sound.

---

### Post by kostkon on 2010-04-14
> **Gerdion said:**
> I go back and do what in the Sounds window?
Select the appropriate profile, output device, etc.
> **Gerdion said:**
> Amarok still not working and neither is Firefox sound.
Check in Amarok's sound preferences. Try changing the sound driver to ALSA or Gstreamer for example.
Since you upgraded from 8.04, you could try the following:
You could press ALT+F2 and give
```
gstreamer-properties
```
and in the audio tab, in the *Default Output* section, change the *Plugin* to ALSA or PulseAudio and set the *Device* to default.

Also, make sure that you are using Flash 10. If you still have Flash 9, then try reinstalling the package
```
flashplugin-nonfree
```
and then restart firefox.

Also, you could install the *PulseAudio Device Chooser* and then open the pulseaudio volume control. You'll be able to send the sound coming from Flash and Amarok (or other app) to your sound card. Maybe some of your applications are sending their sound to the wrong device.

Hope that helps somehow.

---

### Post by lidex on 2010-04-14
Gerdion,
Did you do this from the page I referenced above:
```
 mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
 rm -r ~/.pulse ~/.asound* 
 sudo rm /etc/asound.conf
```
```
 sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio
```
```
$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound
```

---

### Post by Gerdion on 2010-04-14
@ Kostkon: 
flashplugin-nonfree?? I thought that the page that lidex directed me to told me not to make use of that and in fact told me to remove it. Or is this different?

@ Lidex: Yeah, I did that, but what was strange was that it came back telling me that it couldn't delete /.asound because it didn't exist.

---

### Post by lidex on 2010-04-14
> **Gerdion said:**
> @ Kostkon: 
flashplugin-nonfree?? I thought that the page that lidex directed me to told me not to make use of that and in fact told me to remove it. Or is this different?

@ Lidex: Yeah, I did that, but what was strange was that it came back telling me that it couldn't delete /.asound because it didn't exist.

Yes, it's different. What they refer to is
```
flashplugin-nonfree-extrasound
```
which you don't want. 
kostkon refers to
 ```
flashplugin-nonfree
```
which you do. The /.asound message can safely be ignored.

---

### Post by Yellow Pasque on 2010-04-14
If you have pulseaudio installed, you may need to manually route some apps through it.
Here's a hack for Flash:
[http://ubuntuforums.org/showthread.php?t=1412153](http://ubuntuforums.org/showthread.php?t=1412153)
For Amarok (which will output sound through Phonon/xine), make sure xine is set to use pulseaudio:
```
gedit ~/.xine/config
```
Copy and paste this line into the text file (which will probably be blank unless you already customized xine's config).
```
audio.driver:pulse
```
Save, quit and log out. Log back in and try Amarok

---

### Post by mrebanza on 2010-04-14
The upgrade manage is never as good as a fresh install unfortunately . . . try 

```
sudo apt-get install ubuntu-restricted-extras
```

this give you the official proprietary version of Adobe Flash as well as varies codecs for sound file such as MP3 and MP4 that are not legally allowed to be included in ubuntu by default . . . I think it includes some proprietarydrivers too but im not sure

worst case back your stuff up on the cloud or on a usb stick and do a FRESH INSTALL - That would be the best thing to do anyway . .. Good luck

---

### Post by zilu54 on 2010-04-14
I also got the same problem but it became worse...
[http://ubuntuforums.org/showthread.php?t=1454561](http://ubuntuforums.org/showthread.php?t=1454561)

---

### Post by Gerdion on 2010-04-15
@Temujin: The hack didn't work. Thanks though!
@mrebanza: Youtube works just fine now!

Now trying the Xine thing on Amarok...

EDIT: Nope. Didn't work. Is there a specific formatting I need to keep on this file? Here's a blurb of what's on there...

```

# allow implicit changes to the configuration (e.g. by MRL)
# bool, default: 0
#misc.implicit_config:0

```

I simply copy and pasted the following into the very last line.
```

audio.driver:pulse

```

Did I do it wrong?

---

