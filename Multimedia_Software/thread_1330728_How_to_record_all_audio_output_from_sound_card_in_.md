---
title: "How to record all audio output from sound card in Ubuntu 9.10 Karmic Koala"
date: 2009-11-18
forum: Multimedia Software
---

### Post by komputes on 2009-11-18
:-\" Have you ever wanted to capture the audio that gets sent to the speaker and save it in a file?

To do this in Ubuntu 9.10, it is quite simple with kees audio [pa-clone script]("http://outflux.net/software/pa-clone") \\:D/

Simply open a terminal, download the script (review it), make it executable and run it. Then simply play the song and stop the script when the song is over.

```
$ wget [http://outflux.net/software/pa-clone](http://outflux.net/software/pa-clone)
$ chmod u+x pa-clone
$ ./pa-clone output.wav
```Play your song and then return to the terminal and press CTRL-C to stop the pa-clone script from recording.


:guitar:
Rock on and give thanks to kees for the script. =D>
[http://www.outflux.net/blog/archives/2009/04/19/recording-from-pulseaudio/#comment-802](http://www.outflux.net/blog/archives/2009/04/19/recording-from-pulseaudio/#comment-802)

---

### Post by mbuller10 on 2009-11-24
when i try to do this i get

max@max-laptop:~$ sudo ./pa-clone output.wav
Recording to output.wav ...
Ctrl-C or Close this window to stop
./pa-clone: line 21: sox: command not found
write() failed: Broken pipe

please help

---

### Post by fancypiper on 2009-11-24
This may fix it.

sudo apt-get install sox

---

### Post by mbuller10 on 2009-11-24
Fancypiper I got to thank you and the OP a lot, i've been stressing ever since i switched to karmic because audacity's settings have changed but now I've found something better thx

---

### Post by komputes on 2009-11-29
I changed the script a bit, this way, you don't have to define output path in case you need to quickly record something. It will simply write the date and time of the recording in the filename and write it to the home directory.

```
#!/bin/bash
#This script require sox
#sudo apt-get install sox
TIME=$(date +%d-%b-%y_%H%M-%Z)

# Get sink monitor:
MONITOR=$(pactl list | grep -A2 '^Source #' | \
    grep 'Name: .*\.monitor$' | awk '{print $NF}' | tail -n1)

# Record it raw, and convert to a wav
echo "Recording. Ctrl-C or close window to stop"
parec -d "$MONITOR" | sox -t raw -r 44100 -sLb 16 -c 2 - ~/Taped_Recording_$TIME.wav

```

I also add an entry to my .bashrc to make aliases for quick recording.

```
alias tape ="~/bin/soundrip.sh"
```

Can anyone take this and make it a gnome panel applet for quick graphical recording. I think the functionality is already done (take a look at gtk-recordmydesktop code).

---

### Post by d3v1150m471c on 2010-03-20
I've tried several things including this which doesn't work. Audacity has no success. Neither of the recording devices allow me to capture output and there is no mix option. I use alsa, not pulseaudio. arecord is giving me crap saying something like my pcm doesn't exist or cannot be found. My sound works fine but recording from output is looking impossible and incredibly annoying. It shouldn't be this difficult to record sound through my output.

---

### Post by techm3 on 2010-04-10
> **komputes said:**
> I changed the script a bit, this way, you don't have to define output path in case you need to quickly record something. It will simply write the date and time of the recording in the filename and write it to the home directory.

```
#!/bin/bash
#This script require sox
#sudo apt-get install sox
TIME=$(date +%d-%b-%y_%H%M-%Z)

# Get sink monitor:
MONITOR=$(pactl list | grep -A2 '^Source #' | \
    grep 'Name: .*\.monitor$' | awk '{print $NF}' | tail -n1)

# Record it raw, and convert to a wav
echo "Recording. Ctrl-C or close window to stop"
parec -d "$MONITOR" | sox -t raw -r 44100 -sLb 16 -c 2 - ~/Taped_Recording_$TIME.wav

```I also add an entry to my .bashrc to make aliases for quick recording.

```
alias tape ="~/bin/soundrip.sh"
```Can anyone take this and make it a gnome panel applet for quick graphical recording. I think the functionality is already done (take a look at gtk-recordmydesktop code).
Hi Komputers, the script works excellent in a terminal. The only bad thing I found is that the files need much space, there is a way of being able to compress? [IMG]http://www.google.com.pr/images/cleardot.gif[/IMG]Show romanization
Another thing, is there any way to store them in MP3 format instead WAV?



I am doing a graphical application using your script, but when I run it freezes even though continues running, how can i fix it?

---

### Post by komputes on 2010-04-19
[]("http://ubuntuforums.org/member.php?u=950693")hi techm3,

I usually just use another program to convert to mp3 after I edit it.

However you bring up a good point. Looking at the sox manual, compressing to MP3 in realtime should be possible by modifying this line:

```
parec -d "$MONITOR" | sox -t raw -r 44100 -sLb 16 -c 2 - ~/Taped_Recording_$TIME.wav

```

to this:
```
parec -d "$MONITOR" | sox -t mp3 - ~/Taped_Recording_$TIME.mp3
```

However when I try this, I get the error: **SoX was compiled without MP3 encoding support**

---

### Post by Nymrat on 2010-05-01
First, thanks to komputes for sharing this script, it is very handy!
I am using 10.04 Netbook and it works well.

My solution to compressing the output is to add the following to the end of komputes' version of the script (post 5):

```

# Converts the WAV file to OGG then deletes the WAV.
echo "Captured. Converting to a compressed format, please be patient..."
sox ~/Taped_Recording_$TIME.wav ~/Taped_Recording_$TIME.ogg
rm ~/Taped_Recording_$TIME.wav

```

Control-c stops sox, but not the script. This creates an .ogg file from the .wav, then deletes the uncompressed file. It takes a bit of time with long recordings, though.

---

### Post by mbuller10 on 2010-05-03
I switched from pulse audio to alsa because it was skipping so much but now I get this error ./pa-clone: line 21: parec: command not found, please can anyone help

---

### Post by zoli4290 on 2010-05-16
Well, I have tried both scripts i.e. pa-clone and that of komputes'. Both of them created reasonably sized wav files with silence as a content. I use Lucid. What can be wrong?

---

### Post by mbuller10 on 2010-05-18
it just didn't work under alsa, never mind though I went back to pulse audio

---

### Post by Sepero on 2010-07-07
This is great. I can use this to finally record from my speakers audio output and mic at the same time.

---

### Post by techm3 on 2010-07-14
Hey guys!! I made a graphical application for this script:
[http://outrec.sourceforge.net](http://outrec.sourceforge.net)

Enjoy!

---

### Post by braniac5 on 2010-07-15
> **zoli4290 said:**
> Well, I have tried both scripts i.e. pa-clone and that of komputes'. Both of them created reasonably sized wav files with silence as a content. I use Lucid. What can be wrong?

I'm having the same problem, too - it outputs a .wav file but when I play it, there's no sound. This would be a handy application to use, since I can't seem to get Audacity or Sound Recorder to record speaker output...

---

### Post by kvarley on 2010-07-15
You can now do this through a GUI application called "OutRec"

---

### Post by braniac5 on 2010-07-15
> **kvarley said:**
> You can now do this through a GUI application called "OutRec"

Through both terminal and OutRec, it creates a .wav file that's completely silent.

---

### Post by Sepero on 2010-07-15
> **braniac5 said:**
> Through both terminal and OutRec, it creates a .wav file that's completely silent.

You must be sure to be running pulseaudio (the ubuntu default), and not only alsa, oss, or esd.

Also, you should obviously play something through your speakers when you run this. Perhaps try recording something different than what you already tried?

I'm sorry if these tips don't help. There isn't much else I can tell you without some kind of error output.

---

### Post by imbjr on 2010-07-15
> **komputes said:**
> I changed the script a bit, this way, you don't have to define output path in case you need to quickly record something. It will simply write the date and time of the recording in the filename and write it to the home directory.

```
#!/bin/bash
#This script require sox
#sudo apt-get install sox
TIME=$(date +%d-%b-%y_%H%M-%Z)

# Get sink monitor:
MONITOR=$(pactl list | grep -A2 '^Source #' | \
    grep 'Name: .*\.monitor$' | awk '{print $NF}' | tail -n1)

# Record it raw, and convert to a wav
echo "Recording. Ctrl-C or close window to stop"
parec -d "$MONITOR" | sox -t raw -r 44100 -sLb 16 -c 2 - ~/Taped_Recording_$TIME.wav

```

I also add an entry to my .bashrc to make aliases for quick recording.

```
alias tape ="~/bin/soundrip.sh"
```

Can anyone take this and make it a gnome panel applet for quick graphical recording. I think the functionality is already done (take a look at gtk-recordmydesktop code).

Thanks for this. For ages I thought my crappy in-built sound card was to blame. Every attempt I made at recording the speaker output failed, but this script captures the output perfectly.

---

### Post by braniac5 on 2010-07-15
> **Sepero said:**
> You must be sure to be running pulseaudio (the ubuntu default), and not only alsa, oss, or esd.

Also, you should obviously play something through your speakers when you run this. Perhaps try recording something different than what you already tried?

I'm sorry if these tips don't help. There isn't much else I can tell you without some kind of error output.

It works now - wasn't anything wrong with outRec/the script. I re-installed pulseaudio/padevchooser/pavumeter/pavucontrol. Then I changed my sound preferences to "Internal Audio" for hardware, "Internal Analog Stereo" for output, and "Analog Headphones" for connector. Now I can record through outRec and regular ol' gnome sound recorder. 

I'm not sure exactly what I did, but it works now...

---

### Post by yookoala on 2010-07-20
> **komputes said:**
> I changed the script a bit, this way, you don't have to define output path in case you need to quickly record something. It will simply write the date and time of the recording in the filename and write it to the home directory.

```
#!/bin/bash
#This script require sox
#sudo apt-get install sox
TIME=$(date +%d-%b-%y_%H%M-%Z)

# Get sink monitor:
MONITOR=$(pactl list | grep -A2 '^Source #' | \
    grep 'Name: .*\.monitor$' | awk '{print $NF}' | tail -n1)

# Record it raw, and convert to a wav
echo "Recording. Ctrl-C or close window to stop"
parec -d "$MONITOR" | sox -t raw -r 44100 -sLb 16 -c 2 - ~/Taped_Recording_$TIME.wav

```

I also add an entry to my .bashrc to make aliases for quick recording.

```
alias tape ="~/bin/soundrip.sh"
```

Can anyone take this and make it a gnome panel applet for quick graphical recording. I think the functionality is already done (take a look at gtk-recordmydesktop code).


The script is great, thanks first.

I found that it has some problem under different language settings. Because [FONT="Courier New"]pactl[/FONT] honors locale settings and outputs accordingly, that keeps "[FONT="Courier New"]grep 'Name: .*\.monitor$'[/FONT]" from working on some system. I've made some changes to the script to fix this. 

I've also added optional Filename parameter so you may choose to use your own filename or let it generate that for you.

```
#!/bin/bash

# check if user provided the filename
# if not, generate one
if [ "$1" != "" ]; then
  eval LAST_ARG=\$$#
  FILENAME="$LAST_ARG.wav"
else
  TIME=$(date +%d-%b-%y_%H%M-%Z)
  FILENAME="sound_rip-$TIME.wav"
fi


# Get sink monitor:
LANG_SYSTEM_DEFAULT=$LANGUAGE
export LANGUAGE="en"
MONITOR=$(pactl list | grep -A2 '^Source #' | \
    grep 'Name: .*\.monitor$' | awk '{print $NF}' | tail -n1)
export LANGUAGE=$LANG_SYSTEM_DEFAULT

# Record it raw, and convert to a wav
echo "Recording to '$FILENAME'. Ctrl-C or close window to stop"
parec -d "$MONITOR" | sox -t raw -r 44100 -sLb 16 -c 2 - "$FILENAME"
```

I've checked. It also works on Ubuntu 10.04.

---

### Post by Sepero on 2010-07-22
I've actually been looking for something like this for a LONG time. This is a leg up on Microsoft capability.

There is no other program I've ever found for any operating system that allows me to record from both speakers and mic at the same time.

---

### Post by komputes on 2010-07-22
> **Sepero said:**
> I've actually been looking for something like this for a LONG time. This is a leg up on Microsoft capability.

There is no other program I've ever found for any operating system that allows me to record from both speakers and mic at the same time.

@Sepero - You can use opd2d on windows.
[http://www.opcode.co.uk/opd2d/default.asp](http://www.opcode.co.uk/opd2d/default.asp)

From what I know this script is not intended to record the selected PA microphone. If you had to make any changes for this to happen could you publish a script with this feature?

---

### Post by Sepero on 2010-07-22
The standard way of recording from the speakers is to switch the sound card capture from the mic to the speaker output.

With this script, a person can rip speaker output directly from the pulse audio system, while leaving the capture device set to the mic. Currently, I am having to use another program (like Audacity) to record the mic at the same time.

This way it records mic and speakers in realtime to separate files.

If there is a way to use pa* commands to rip from mic input also, then I'd love to do that. Currently, I don't much about these tools.

---

### Post by Sepero on 2010-07-29
Ok, I've now edited my own version of the script to record BOTH speakers and mic. It's "hardcoded" to record in flac format (because I want compression, but I don't like lossy audio like mp3). If you don't want "flac" as your audio format, just edit where it says "flac" to: "mp3", "wav", or "ogg".

Also, like komputes, I've coded it to immediately create the files with generic names including date and timestamp.

It's a great script for recording any two-way conversations on the internet, such as ekiga or skype phone calls, or conversations you might have through flash websites like stickam or paltalk. It records the audio's into 2 separate files which may be combined later with Audacity.

(Note: There is a linux plugin for skype called "skype call recorder" that will allow you to record calls more easily than this script.)

```

#!/bin/bash
# Copyright 2008-2009, Kees Cook <kees@outflux.net>
#
# Records the PulseAudio monitor channel.
# http://www.outflux.net/blog/archives/2009/04/19/recording-from-pulseaudio/
#
# Usage: $0

DATETIME=$(date "+ %Y %b %d_%T")
# AUDIO IN AND OUT FILE NAMES
AOUT_FILE="rec-aout$DATETIME.flac"
AIN_FILE="rec-ain$DATETIME.flac"

# Get aout monitor:
MONITOR=$(pactl list | grep -A2 '^Source #' | \
    grep 'Name: .*\.monitor$' | awk '{print $NF}' | tail -n1)

# Record it raw, and convert to a wav
parec -d "$MONITOR" | sox -t raw -r 44100 -sLb 16 -c 2 - "$AOUT_FILE" &
parec -r | sox -t raw -r 44100 -sLb 16 -c 2 - "$AIN_FILE" &

echo "Recording to $AOUT_FILE ..."
echo "Recording to $AIN_FILE ..."
echo "Press enter to stop recordings"
read i

killall parec

```

This code is admittedly sloppy. It will kill all 'parec' processes on the system. Unfortunately, parec must be killed before sox. I tried using the bash variable "$!", but it grabs the pid of sox instead of parec. No matter what I tried, I could not get the pid of both 'parec' without adding something nasty like 'ps | grep parec'.

If anyone knows a way to simply/easily get the pid's of the 'parec' processes, please let me know.

---

### Post by kealan on 2010-08-14
> **techm3 said:**
> Hey guys!! I made a graphical application for this script:
[http://outrec.sourceforge.net](http://outrec.sourceforge.net)

Enjoy!

Gratitude and thanks to [COLOR="Blue"]**techm3**[/COLOR] for GUIing this very handy script.

I'm perfectly capable of using the command line, but when opening up the terminal and inputting lines of code is the only way to do something it makes using Ubuntu feel like driving my old Datsun: I had to pop the hood and hit the starter with a hammer to get it running.  As a "solution" it worked for me, but it wouldn't be a "solution" for my mom's car. 

Please forgive the far-out analogy, what I mean is: It's little contributions like yours that keep making this OS a more and more realistic alternative to Windows for the average user.

---

### Post by amac777 on 2010-08-15
OutRec works well here. Thanks.

---

### Post by Oltsak on 2010-09-02
> **yookoala said:**
> 
I've checked. It also works on Ubuntu 10.04.

How to record everything into 1 file? E.g. one source is some application and another source is line-in. This worked previously with arecord when 'mix' and 'rec-capture' was selected from alsamixer. 

Now with Pulseaudio (arecord or parec) I can only record either from apps or line-in like in script above. How to mix everything into one file while recording? I would like to do this using cmd-line tools. 

It would be nice to get this working without removing Pulseaudio, because it seems we have to live with it...

---

### Post by baddnady23 on 2010-09-10
This is open source at its best right here.  Thanks for the great script.  I was wondering if it was possible for someone to make it so that when you define the filename as "name.wav", you could do "name.flac" so that you are able to pick the format that you want to record in other than .wav?

---

### Post by Sepero on 2010-09-10
If you name it to .wav, it should come out that way in theory. In reality, you might have to adjust some of the arguments given to sox.

Most likely, you will only have to change it to .wav.

---

### Post by spodhajecki on 2010-10-10
> **Nymrat said:**
> First, thanks to komputes for sharing this script, it is very handy!
I am using 10.04 Netbook and it works well.

My solution to compressing the output is to add the following to the end of komputes' version of the script (post 5):

```

# Converts the WAV file to OGG then deletes the WAV.
echo "Captured. Converting to a compressed format, please be patient..."
sox ~/Taped_Recording_$TIME.wav ~/Taped_Recording_$TIME.ogg
rm ~/Taped_Recording_$TIME.wav

```

Control-c stops sox, but not the script. This creates an .ogg file from the .wav, then deletes the uncompressed file. It takes a bit of time with long recordings, though.

> **komputes said:**
> []("http://ubuntuforums.org/member.php?u=950693")hi techm3,

I usually just use another program to convert to mp3 after I edit it.

However you bring up a good point. Looking at the sox manual, compressing to MP3 in realtime should be possible by modifying this line:

```
parec -d "$MONITOR" | sox -t raw -r 44100 -sLb 16 -c 2 - ~/Taped_Recording_$TIME.wav

```

to this:
```
parec -d "$MONITOR" | sox -t mp3 - ~/Taped_Recording_$TIME.mp3
```

However when I try this, I get the error: **SoX was compiled without MP3 encoding support**

Thanks Komputes for the script, here are a couple of mods.

I have used this to bypass having to re-encode wav to ogg.
```

parec -d "$MONITOR" | sox -t raw -r 44100 -sLb 16 -c 2 - -t raw -| oggenc -b 162 -o "$TIME".ogg --raw -

```

This works for me for going to mp3 using lame.
```

parec -d "$MONITOR" | sox -t raw -r 44100 -sLb 16 -c 2 - -t wav -| lame - "$TIME".mp3

```

This article is worth taking a look at too. [http://linuxgazette.net/issue73/chung.html]("http://linuxgazette.net/issue73/chung.html")

---

### Post by mrowl on 2010-10-11
I've been using outRec successfully for awhile now but recently I moved my Home directory to its own partition and now I'm having problems. I've tried removing it using Synaptic and re-installing but I all I get are empty Wav files. No sound. All other sound seems to be working fine. Any ideas what has gone wrong.

I'm running 10.04 Lucid

---

### Post by mrowl on 2010-10-13
> **mrowl said:**
> I've been using outRec successfully for awhile now but recently I moved my Home directory to its own partition and now I'm having problems. I've tried removing it using Synaptic and re-installing but I all I get are empty Wav files. No sound. All other sound seems to be working fine. Any ideas what has gone wrong.

I'm running 10.04 Lucid

Solved:

Turned out to be a setting on the PulseAudio Volume Control

---

### Post by ridgeland on 2010-10-18
1click_record.sh
Here is how to record the pulse audio stream with a single click.  I had the new bees in mind here so its excessive with detail.

Thanks komputes for this excellent thread. Now I can see value in Pulse Audio.

Using information from this post I created this short script.  To capture your audio with one click just copy this script to a file and give the file execute permission.  Then add a launcher to your panel to run the script. Voilà! One click on the panel and you are recording the stream pulse audio is sending to your speakers.

Some details.  The script is a script.  That's very good news.  You can modify it to do what you want using a simple text editor like gedit or nano.  The script has defaults for DefaultDirectory, DefaultFileName and DefaultExtension.  Edit the script to have the defaults you want.  Extension can be either mp3 or wav.  For mp3 I added -V0 to sox to block a warning message I was getting.  If you don't change the defaults the script will create an mp3 in /tmp/ with a file name like 1click_record_2010_10_18_21:02.mp3.  Again being a script you can change that date stamp format too.

Part 1 the script:
```
#!/bin/bash
#
# 1click_record.sh
# start immediately recording the pulse audio output
#
# written by Ridgeland
# October 18, 2010
# derived from http://ubuntuforums.org/showthread.php?t=1330728
# post and initial script by komputes
#

# Set default output directory - Unique for YOUR PC!
# for my PC I use: DefaultDir="/Data/Music/Temp/"
# for a univeral directory I'll throw out /tmp
# BEWARE: /tmp can get erased from time to time (each boot for me)
DefaultDir="/tmp/"

# For 1 click recording I'll use mp3
# wav works too if you prefer it - just remove the # two lines below
DefaultExtension=".mp3"
# DefaultExtension=".wav"

# create the filename from the current date and time
DefaultFileName="1click_record_$(date +%Y_%m_%d_%H:%M)"
SaveAs=$DefaultDir$DefaultFileName$DefaultExtension
echo; echo "Audio is being saved to file $SaveAs"; echo
echo "Close this pop-up to stop the recording"; echo; echo

# The guts of it - from the forum post
# Get sink monitor:
LANG_SYSTEM_DEFAULT=$LANGUAGE
export LANGUAGE="en"
MONITOR=$(pactl list | grep -A2 '^Source #' | \
grep 'Name: .*\.monitor$' | awk '{print $NF}' | tail -n1)
export LANGUAGE=$LANG_SYSTEM_DEFAULT
# Record it as mp3 or wav
if [[ $DefaultExtension == ".mp3" ]]; then
    parec -d "$MONITOR" | sox -t raw -r 44100 -sLb 16 -c 2 - -t wav - -V0 | lame - "$SaveAs"
else
    parec -d "$MONITOR" | sox -t raw -r 44100 -sLb 16 -c 2 - "$SaveAs"
fi
```

Launch gedit.  Probably Menu -> Accessories -> Text Editor.  Copy the script and paste it into gedit.  Edit the defaults.  Save it as 1click_record.sh.  Use Nautilus File Browser.  Find the script and right click on it.  Select the tab Permissions and turn on Execute: [x] Allow executing file as program.

Part 2 putting it in the panel for a single click launch:
Right click on the panel and select "Add to panel...".  In the Add to Panel window select "Custom Application Launcher" and click [Add].  In the Create Launcher window select Type: "Application in Terminal".  Name: 1 Click Record.  Command: 1click_record.sh, but don't type it in.  Get it from the [Browse] button.  Comment: Record Pulse Audio Output to File.  Right click on the spring board icon and pick something better.  For an icon I am using:
[http://www.wpclipart.com/music/performance/microphone/old_microphone.png.html](http://www.wpclipart.com/music/performance/microphone/old_microphone.png.html)
You can go there and save the image you see, it's in the public  domain.

That's all.  Now a single click on the icon in the panel and the recording begins. Just close the pop-up window to end the recording.

I tested recording from Audacious playing Merle Travis - Deep South - worked fine.  I tested recording from Firefox - ShoutCast - Radio Oh-la-la  Totem launches and it recored fine.  I tested with RealPlayer11 to record Radio Oh-la-la but it failed.  I could hear the radio station but the recording never happened.  RealPlayer is not using PulseAudio I guess.

---

### Post by ridgeland on 2010-10-18
Here is a follow up post.
We seldom use the script 1click_record.sh I posted in the previous post because:
We want to select the directory to use.  We want to select the file name to use.  We want to select if it saves as wav or mp3.  So rather than a single click and use three defaults, this script asks three questions.  The script lets the user stay with the default for each question.

My wife for example wants to record a broadcast from [http://www.metoperafamily.org/stream.aspx](http://www.metoperafamily.org/stream.aspx). 
that broadcasts once a week, next will be 10/20/2010 at 7:00 pm Wisconsin time.  She wants to save it in the directory /Data/Music/MetOperaLive/ with a file name 2010.10.20.Boris_Godunov and as a wav not a mp3 because she will use Audacity later to trim the beginning and end and break it into Acts.  From Audacity she will export it as mp3s to take up less space.  After which she will delete the original.

I want to record Radio Canada from Montréal while I'm outside cutting grass, but I only want to hear it once.  If there is a good song I might record that. So I'm fine with the default directory /Data/Music/Temp and file name with a date stamp but I want mp3 not wav.  

So scripts to the rescue again.  Here is the script we use.  It's long because it tries to be careful with file names.  The core is the same as 1click_record.sh. I named this script audio_record.sh.  We launch it from the panel with a single click like before.

```
#!/bin/bash
#
# audio_record.sh
# written by Ridgeland
# October 18, 2010
# derived from http://ubuntuforums.org/showthread.php?t=1330728
# post and initial script by komputes
#

# Set default output directory - Unique for YOUR PC!
DefaultDir="/Data/Music/Temp/"
# wav is my choice for default file type - .mp3 is an option
DefaultExtension="wav"
# DefaultExtension="mp3"

# loop until the user gives a valid directory and file name 
NeedFileName="Y"
while [ $NeedFileName == "Y" ]
do
    OutDir=$DefaultDir
    YesNo="Y"; echo; echo -n "Use default Directory of "$OutDir" ? Y/n "; read YesNo
    if [[ $YesNo == "Y" || $YesNo == "y" || $YesNo == "" ]]; then
        ### check that the default exists.
        if [ ! -e "$OutDir" ]; then
            echo; echo "Oh Dear! Default Directory does not exist!"
            echo "Edit this script or create the directory"
            echo "Program is crashing and closing in 7 seconds ...."; echo
            sleep 7
            exit
        fi
    else
        echo; echo -n "Enter the directory to use (ex. /home/ridgeland/ ) ";    read OutDir
        # if the user failed to end with a "/" then add one for them
        Strlength=${#OutDir}
        Strlast=$[$Strlength-1]
        chrlast=${OutDir:$Strlast}
        if [ $chrlast != "/" ]; then
            OutDir=$OutDir/
        fi
        if [ ! -e "$OutDir" ] ; then
            echo; echo "What?  Seems "$OutDir" does not exist.  Try again."; echo
            continue
        fi
        echo "Program will save output in directory "$OutDir
    fi
    # create a default filename
    FileTime=$(date +%Y_%m_%d_%H:%M)
    DefaultFileName="audio_record_$FileTime"
    echo; echo "Now enter Output File Name - without the extension (wav or mp3 will be added for you)"
    echo "Don't use spaces in the name!"
    echo "For default file name of $DefaultFileName hit [Enter] or enter file name now: "
    read OutFile
    if [[ $OutFile == "" ]]; then
        OutFile=$DefaultFileName
    fi
    echo
    echo "Now Select the File Type"
    if [[ $DefaultExtension == "wav" ]]; then
        echo -n "For Default of $DefaultExtension hit [Enter] For .mp3 any other entry: "; read FileType_YesNo
        if [[ $FileType_YesNo == "" ]]; then
            ExtToUse=".wav"
        else
            ExtToUse=".mp3"
        fi
    else
        echo -n "For Default of $DefaultExtension hit [Enter] For .wav any other entry: "; read FileType_YesNo
        if [[ $FileType_YesNo == "" ]]; then
            ExtToUse=".mp3"
        else
            ExtToUse=".wav"
        fi
    fi
    # Now put together the Output Directory, the Output FileName and the file extension (type)
    SaveAs=$OutDir$OutFile$ExtToUse
    if [ -e $SaveAs ]; then
        YesNo2="Y"; echo "File "$SaveAs" already exists."; echo -n "Overwrite it? Y/n "; read YesNo2
        if [[ $YesNo2 == "Y" || $YesNo2 == "y" || $YesNo2 == "" ]]; then
            echo "File will be overwritten"
            NeedFileName="N"
        else
            echo "OK then start over..."
            continue
        fi
    else
        NeedFileName="N"
    fi
done
echo; echo "Program will save the output to "$SaveAs; echo

# The guts of it - from the forum post
# Get sink monitor:
LANG_SYSTEM_DEFAULT=$LANGUAGE
export LANGUAGE="en"
MONITOR=$(pactl list | grep -A2 '^Source #' | \
    grep 'Name: .*\.monitor$' | awk '{print $NF}' | tail -n1)
export LANGUAGE=$LANG_SYSTEM_DEFAULT
# Record it as wav or as mp3
echo "Recording to '$SaveAs'."; echo "Ctrl-C or close window to stop"; echo
if [[ $ExtToUse == ".wav" ]]; then
    parec -d "$MONITOR" | sox -t raw -r 44100 -sLb 16 -c 2 - "$SaveAs"
else
    parec -d "$MONITOR" | sox -t raw -r 44100 -sLb 16 -c 2 - -t wav - -V0 | lame - "$SaveAs"
fi
```

---

### Post by IanVaughan on 2010-11-21
I dont know why ppl are using parec? Each to their own... I use rec, into ogg, wrapped up in this script that takes the filename (without ext) and number of hours to record for as parameters.

```
#!/bin/bash
FILENAME=$1
HOURS=$2
SECONDS=$((3600 * ${HOURS}))
echo "Recording ${FILENAME} for ${SECONDS} seconds..."
rec -c 2 ${FILENAME}.ogg trim 0 ${SECONDS}
```

eg: record.sh myfile 1
Would record into myfile.ogg for 1 hour.

---

### Post by tomjennings on 2010-12-08
> **braniac5 said:**
> I'm having the same problem, too - it outputs a .wav file but when I play it, there's no sound. This would be a handy application to use, since I can't seem to get Audacity or Sound Recorder to record speaker output...

metoo... silence in Totem when I double-click it... but loaded into Audacity, it plays fine, so the audio is there. wtf? don't forget there's likely silence at file start if you ran the script then started audio source.

---

### Post by imbjr on 2011-04-25
> **mrowl said:**
> Solved:

Turned out to be a setting on the PulseAudio Volume Control

Agreed. I just found that the script stopped working and then discovered your comment - which turned out to help.

---

### Post by Vesperatus on 2011-05-25
> **imbjr said:**
> Agreed. I just found that the script stopped working and then discovered your comment - which turned out to help.

Please... If you are to tease us with an anwser like that, give more info, like the following :

[http://blog.fulsolabs.com/?p=994](http://blog.fulsolabs.com/?p=994)

Basically, in pulse audio volume control, you have to unmute, under the input devices tab, the "Monitor of internal audio analog stero"

There.

Now back to solving real problems :P

---

### Post by colobix on 2011-12-10
So can any of you figure out how to do this with alsa instead of pulse, plz?

---

