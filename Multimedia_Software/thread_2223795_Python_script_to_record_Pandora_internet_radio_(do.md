---
title: "Python script to record Pandora internet radio (done!)"
date: 2014-05-12
forum: Multimedia Software
---

### Post by inexplikibled on 2014-05-12
Hello all. Here's my second Ubuntu forums thread. This time I've written a rough Python script to record streaming Pandora audio. 
The goals of the project were as follows:
1. No use of the web interface which would mean using flash. Use pianobar program as backend instead, 
2. Sort songs into a folder hierarchy. Artist/Album/Song. Basically create the non-existent ones on the fly.
3. Save as either .ogg or .mp3 with same quality as the sound coming out of the speakers.

The goals at this time do not include interaction. It's just run it and sit back while it builds you a local library.

This script uses python's popen methods to communicate with a pianobar process(play) and a avconv process(record). Avconv simply grabs the audio output from the speakers and records it in this case. Unfortunately, this means that anything else coming through the sound card will be recorded along with the song. This wasn't a concern for me because I was thinking of just having a headless machine in the corner set up to record.
[B]
For this to work you will need to:[/B]
**1.** Install libav-tools package and pianobar package from the software center.
**2.** edit the line in /etc/pulse/daemon.conf that looks like this:
```
;default-sample-rate = whatever it was before
```
and change it to this:
 ```
default-sample-rate = 48000
```

So basically uncomment that line and change the rate to 48000.

**3.**
Here is the original code for recording indefinetely to a file from your speakers:
```
avconv -f pulse -i alsa_output.pci-0000_00_14.2.analog-stereo.monitor -acodec libvorbis -ac 2 -ar 48000 -vn out.ogg
```
Note that this is set up for my specific sound card output. So this is the next task.
Open a terminal and enter this:
```
pactl list sources
```
Your most likely looking for Source #0 and you will have to copy and paste what shows up under Name: into my python code in place of what I have there for my soundcard.
Mine was this:
```
 alsa_output.pci-0000_00_14.2.analog-stereo.monitor
```
So just edit that one line of my script, but be careful not to remove the quotes.

To run the script, open a terminal and cd to the script, then do:
```
python record-pandora_1.0.py
```

Here's the script:
```
import subprocess, time, os

def startRecord(playingInfo1, playingInfo2, playingInfo3):
    global p2
    try: #try to create new artist dir if not already there
        if(not os.path.exists("music/" + playingInfo1)):
            os.mkdir("music/" + playingInfo1)
            print "Created new Artist dir"
        #create new Album dir if not already there
        if(not os.path.exists("music/" + playingInfo1 + "/" + playingInfo2)):
            os.mkdir("music/" + playingInfo1 + "/" + playingInfo2)
            print "Created new Album dir"
        #record new song if not already recorded
        if(not os.path.exists("music/" + playingInfo1 + "/" + playingInfo2 + "/" + playingInfo3 + ".ogg")):
            try: ### the next line is for specific sound card, edit it
                avconvCmd = "avconv", "-f", "pulse", "-i", "alsa_output.pci-0000_00_14.2.analog-stereo.monitor", "-acodec", "libvorbis", "-ac", "2", "-ar", "48000", "-vn" , 'music/' + playingInfo1 + '/' + playingInfo2 + '/' + playingInfo3 + '.ogg'
                p2 = subprocess.Popen(avconvCmd)
                print "Created new Song file, now recording...\n"
            except:
                print "Error opening avconv! Is libav-tools installed?\n"
    except:
        print "Couldn't create new Song file!\n"
                
        


### program start here ###

#variables and lists
p2 = ""

#create music dir if it doesn't exist
if(not os.path.exists("music")):
    os.mkdir("music")

#try to run pianobar
try:
    cmd = "pianobar"
    p = subprocess.Popen(cmd, stdout=subprocess.PIPE, stdin=subprocess.PIPE)
    output = p.stdout.readline()
except:
    print "Error opening pianobar! Is it installed?\n"

while(output):
    if('|>  "' in output): #beginning of songs playing
        try:
            p2.kill() #kill recording of last song
        except:
            print
        try: #try to clean up and format pianobar's output
            cleanPianobarChars = output.split('|>  "', 1)
            songName = cleanPianobarChars[1].split('" by "', 1)
            artistName = songName[1].split('" on "', 1)
            albumName = artistName[1].split('"', 1)
            #put Artist name, Album name and Song name into a list
            playingInfo1 = artistName[0]
            playingInfo2 = albumName[0]
            playingInfo3 = songName[0]
            print "\nArtist: " + playingInfo1 + "\nAlbum: " + playingInfo2 + "\nSong: " + playingInfo3 + "\n"
            #start dir check or creation and record to file
            startRecord(playingInfo1, playingInfo2, playingInfo3)
        except:
            print "Something went wrong with cleaning up pianobar output...\n"
    output = p.stdout.readline()


```

Enjoy!

---

### Post by inexplikibled on 2014-07-27
Hello again,

I've revised and updated the code and instructions somewhat.
Differences in code and functionality:
1. Bugfixes: Now records whole song instead of cutting off the last few seconds
2. Now supports configuration files! no need to edit the code for your specific sound card. Eg: record-pandora.conf
3. Now supports ads detection. In my experience, in odd cases ads can slip through and play through pianobar. On the second line of record-pandora.conf, put a number Eg: 800. This is the minimum recorded file size to keep after recording. Any song this number size and under will be deleted.
4. Now supports artist whitelist. Eg: whitelist-artists.txt This will not skip the non-whitelisted song (too many issues) it will simply not record it.

Instructions:
1. You don't need to edit /etc/pulse/daemon.conf Just run this:
```
pactl list sources
```
and get the Source. Mine was this: 
```
alsa_output.pci-0000_00_1b.0.analog-stereo.monitor
```
and put it in record-pandora.conf as the first line.

2. Put your preferred Kilobyte size on the second line of record-pandora.conf. Example conf file would be:
```
alsa_output.pci-0000_00_1b.0.analog-stereo.monitor
800
```
This line is for new feature 3 listed above.

3. Optional, create a whitelist-artists.txt file with the names of the artists you only want to hear/record. Each line must be capitalized as pianobar shows them and the last line must have a blank line under it. Example:
```
Modest Mouse
Pink Floyd


```

4. You must set up pianobar prior to running this script. First make a pianobar conf file: /home/username/.config/pianobar/config  It should contain: At least a user = pandorausername line and a password = pandorapassword line. Thats 2 seperate lines. 

4.1 Then run pianobar for the first time and select the station to play. Then press q. This is all that is needed in pianobar to run my script. If you want to change stations repeat this step.

5. All config files must be in the same directory as the record-pandora.py  and make sure you have packages libav-tools and pianobar installed and  then open a terminal in the same directory as the record-pandora.py and  do:
```
./record-pandora.py
```

Enjoy!

Here's the revised code to save into a new file:

```

#!/usr/bin/python
import subprocess, time, os

def startRecord(playingInfo1, playingInfo2, playingInfo3):
    try: #try to create new artist dir if not already there
        if(not os.path.exists("music/" + playingInfo1)):
            os.mkdir("music/" + playingInfo1)
            print "Created new Artist dir"
        #create new Album dir if not already there
        if(not os.path.exists("music/" + playingInfo1 + "/" + playingInfo2)):
            os.mkdir("music/" + playingInfo1 + "/" + playingInfo2)
            print "Created new Album dir"
        #record new song if not already recorded
        if(not os.path.exists("music/" + playingInfo1 + "/" + playingInfo2 + "/" + playingInfo3 + ".ogg")):
            try: ### the next line is for specific sound card, edit it
                os.system('avconv -loglevel panic -f pulse -i ' + audioDevName + ' -acodec libvorbis -ac 2 -vn "music/' + playingInfo1 + '/' + playingInfo2 + '/' + playingInfo3 + '.ogg" &')
                print "Created new Song file, now recording...\n"
            except:
                print "Error opening avconv! Is libav-tools installed?\n"
    except:
        print "Couldn't create new Song file!\n"
                

### program start here ###

#variables and lists
p2 = ""

#create music dir if it doesn't exist
if(not os.path.exists("music")):
    os.mkdir("music")
    
#read configuration file
try:
    if(os.path.exists("record-pandora.conf")):
        confFile = open("record-pandora.conf", "r")
        audioDevName = confFile.readline()
        audioDevName = audioDevName.rstrip("\n")
        delFileSize = confFile.readline()
        delFileSize = delFileSize.rstrip("\n")
        confFile.close()
    else:
        print "record-pandora.conf not found, please create it\nwith your audio device name and desired delete file size in bytes.\n"
        print "Example:\nalsa_output.pci-0000_00_14.2.analog-stereo.monitor\n800"
except:
    print "Error trying to read conf file"

### whitelist section ###
def whiteListArtists():
    try:
        if(os.path.exists("whitelist-artists.txt")):
            whitelistArtists = open("whitelist-artists.txt", "r")
            whitelistArtistsList = whitelistArtists.readlines()
            whitelistArtists.close()
        else:
            whitelistArtistsList = ""
            print "Couldn't find whitelist-artists.txt.\nWill play/record all. "
    except:
        print "Error tying to read whitelist-artists.txt"
    
    return(whitelistArtistsList)
### end whitelist section ###
    
#try to run pianobar
try:
    cmd = "pianobar"
    p = subprocess.Popen(cmd, stdout=subprocess.PIPE, stdin=subprocess.PIPE)
    output = p.stdout.readline()
except:
    print "Error opening pianobar! Is it installed?\n"

while(True):
    if('|>  "' in output): #beginning of songs playing
        try:
            #kill recording of last song
            os.system("killall avconv")
            if(os.path.getsize("music/" + playingInfo1 + "/" + playingInfo2 + "/" + playingInfo3 + ".ogg") <= int(delFileSize)):
                os.remove("music/" + playingInfo1 + "/" + playingInfo2 + "/" + playingInfo3 + ".ogg")
                print "Removed: music/" + playingInfo1 + "/" + playingInfo2 + "/" + playingInfo3 + ".ogg"
        except:
            print
        try:
            #try to clean up and format pianobar's output
            cleanPianobarChars = output.split('|>  "', 1)
            songName = cleanPianobarChars[1].split('" by "', 1)
            artistName = songName[1].split('" on "', 1)
            albumName = artistName[1].split('"', 1)
            #put Artist name, Album name and Song name into a list
            playingInfo1 = artistName[0]
            playingInfo2 = albumName[0]
            playingInfo3 = songName[0]
            #skip all artists not in whitelist
            whiteList = whiteListArtists()
            if(playingInfo1 + "\n" in whiteList or whiteList == ""):
                print "\nArtist: " + playingInfo1 + "\nAlbum: " + playingInfo2 + "\nSong: " + playingInfo3 + "\n"
                #start dir check or creation and record to file
                startRecord(playingInfo1, playingInfo2, playingInfo3)
            else:
                print "Not recording\nArtist: " + playingInfo1 + "\nAlbum: " + playingInfo2 + "\nSong: " + playingInfo3 + "\n(Not in whitelist)\n"
        except:
            print "Something went wrong with cleaning up pianobar output...\n"
    output = p.stdout.readline()

```

---

### Post by yuriy31 on 2014-08-02
What would the difference in quality be between using this script, great work by the way, and inspecting elements on the pandora page and downloading the song from the source?

---

### Post by inexplikibled on 2014-08-02
While I haven't done much research into how pandora web client works(I think it uses flash), I believe pianobar (what my script uses) and pithos (a great gui pandora app) both use tags in pandoras site to stream the music as is anyway. So I guess my answer would be: Unless you have a pay for Pandora account, the quality whould be the same with web or with pianobar. Of couse pay for Pandora accounts provide higher quality streaming access, so that would probably improve the quality of the end recording. Thanks for the complement too!

Also, I've updated the code in my second post so that the whitelist-artists.txt file can be edited while the script is running so you don't have to stop recording. It re-reads it on every new song.

---

### Post by sparky5 on 2014-12-25
[LIST]
[*] 	 		 			:razz: 		
 	
[/LIST]
Anyone have this running on raspberry pi?

thanks..

---

### Post by inexplikibled on 2014-12-26
Hi sparky5 in reply to a message from you in my email (can't seem to find that post here):
Does it also at some point say:
sh: 1: avconv: not found
If that's the case, have you installed libav-tools so that avconv is available to my script?
```
sudo apt-get install libav-tools
```

Each time you start the script it will say: 
avconv: no process found
as it's first output, but thats only because the first action is to kill all avconv processes that may be running so that it can start a new one to record. Since there was no avconv process running yet, it outputs that message.

As far as it working on the raspberry pi... Well honestly that would be great. It consumes very little power so leaving it running wouldn't be an issue. However I'm not sure if the pi has enough processing power to actually encode the audio to a file in real time without stutter or something. I have thought about trying this out on one of my pi's but never have yet. I might give it a try sometime though and post back with results. A good size USB drive would probably be a good idea to store the recordings if it did work.

---

### Post by sparky5 on 2014-12-26
Thanks for the reply. I found that I had not insgtalled libav-tools.. and the first avconv: no process found message had distracted me. I have it running on an old laptop under ubuntu. I started trying to get your code running on a raspberry, with no luck. pianobar runs fine, and your code starts and creates the directories, but no music files. Now that I have it running on a different system, I'll go back and see what I can do again on the raspberry. 
Thanks again

---

### Post by nanoViral on 2015-06-17
I can't seem to get the script to work. I have the libav-tools installed, and it's not giving any of those libav related messages like the replies above. When I execute the script with ./, I get this message:
```

jake@jake-MS-7759:~/.config/pianobar$ ./record-pandora.py
from: can't read /var/mail/pithos.plugin
from: can't read /var/mail/pithos.pithosconfig
from: can't read /var/mail/mutagen.mp4
import: unable to open image `os': Permission denied @ error/blob.c/OpenBlob/2709.
from: can't read /var/mail/shutil
from: can't read /var/mail/glob
./record-pandora.py: line 24: syntax error near unexpected token `('
./record-pandora.py: line 24: `class SavePlugin(PithosPlugin):'

```

When I invoke python to run the command, I get less text output. It looks like this:

```

jake@jake-MS-7759:~/.config/pianobar$ python record-pandora.py
Traceback (most recent call last):
  File "record-pandora.py", line 17, in <module>
    from pithos.plugin import PithosPlugin
ImportError: No module named pithos.plugin

```

Anyone know how to get it working?

---

### Post by inexplikibled on 2015-06-17
Hello nanoViral, Can you give me some more info?

1. What version of Ubuntu are you running?
2. Did you install pianobar?

The errors you're getting don’t look like they're actually related to my script.

Your .config/pianobar/config file should look like this with two lines:
user = yourpandorausername
password = yourpandorapassword

You have to run pianobar itself first before running my script so that you can set it up to play the stations you want. So in a terminal:
```
pianobar
```

Another thing you may want to try is to put record-pandora.py in a standard directory such as /home/yourusername/Documents/record-pandora.py or in another standard directory and then run it from there. I'm guessing some of the problem may be related to running it in the hidden .config/pianobar/ directory. That is, if that's where your running it from...

Last, double check that you copied all the code for my script correctly.

---

### Post by nanoViral on 2015-06-19
So, I had the code from a completely different script (written by someone else haha) instead of yours, but named the same and with the config file unchanged. It kinda works now...I followed your advice and put the script-config in documents. It ran, and created a music folder. But no matter how many times I run the script, hit q, and restart pianobar, (pianobar and the script running in different terminals) no music is created in the music folder. It doesn't print anything after I run the script either, but It's definitely since it created the folder. (Plus it doesn't print the working directory, so it's running.) My config looks like this:

alsa_output.pci-0000_00_1b.0.analog-stereo.monitor
128

I'm running ubuntu 15.04.

---

### Post by inexplikibled on 2015-06-19
Oh, ok then lol,

You only need to run pianobar by itself when you need to set it up, like changing the station or whatever. So basically open a terminal and run 
```
pianobar
```
then, select your preferred station or quickmix or whatever. Then, after it starts to play just press q to quit pianobar. Now it's set up to play that station when you run my script.
So now run 
```
./record-pandora.py
```
or
```
python record-pandora.py
```
(without running any other instance of pianobar in any other terminal)

I think whats happening is that pianobar is open in your other terminal and is not letting another instance of itself start when my script calls it. 
My script kinda works as a non-interactive front end to pianobar so when you run the script, it actually opens pianobar in the background in order to play the stations.
But if you're trying to run pianobar twice (once in a terminal and once from the script) with the same login to pandora, it will likely cause issues.

---

### Post by marke1 on 2015-09-16
Just a couple of notes on this script:

- The volume of a recorded track is determined by the volume of the speakers on your system

- If you want to record to MP3 instead of OGG use something like this, assuming you have libmp3lame installed: 

os.system('avconv -loglevel panic -f pulse -i ' + audioDevName + ' -acodec libmp3lame -aq 3 -ac 2 -vn "music/' + playingInfo1 + '/' + playingInfo2 + '/' + playingInfo3 + '.mp3" &')

---

### Post by marke1 on 2015-09-16
Here's an updated version of this script with two new features: Blacklisting artists and recording format choice ( ogg or mp3 )

Blacklisting works similar to whitelisting. Create a file named blacklist-artists.txt in the same directory as this script and put the artist names in the file one per line. If the artist is in the list then recording the track will be skipped, *but pianobar will still play it. *

To select between ogg and mp3 recording formats you must use the config file already supported by the original script ( record-pandora.conf ).  On the 3rd line of the config file put "ogg" or "mp3" without the quotes. If you omit that in the file the script assumes ogg format. *To use mp3 format you must have libmp3lame installed. *

NOTE: I do not provide any support for these modifications. They have been tested and work on my system. 

```

#!/usr/bin/python
import subprocess, time, os

# Requires Pulse audio to be in use

# record-pandora.conf - config file. LINE 1: Audio source | LINE 2 - min output file size per track, anything smaller is deleted | LINE 3 - output format, ogg or mp3
# To get the parm for line 1 do this at the command line: pactl list sources

# EXAMPLE CONFIG FILE: 

# alsa_output.pci-0000_00_1b.0.analog-stereo.monitor
# 800
# mp3


# whitelist-artists.txt -- a list of artists to record, one per line, case sensitive, names must match Pandora name output exactly

# blackist-artists.txt -- a list of artists to NOT record, one per line, case sensitive, names must match Pandora name output exactly


def startRecord(playingInfo1, playingInfo2, playingInfo3):
    try: #try to create new artist dir if not already there
	    
        if(not os.path.exists("Music/" + playingInfo1)):
            os.mkdir("Music/" + playingInfo1)
            print "Created new artist dir"
            
        #create new Album dir if not already there
        if(not os.path.exists("Music/" + playingInfo1 + "/" + playingInfo2)):
            os.mkdir("Music/" + playingInfo1 + "/" + playingInfo2)
            print "Created new album dir"
            
        #record new song if not already recorded
        if(not os.path.exists("Music/" + playingInfo1 + "/" + playingInfo2 + "/" + playingInfo3 + "." + outputType)):
            try: ### the next line is for specific sound card, edit it
                
                if(outputType == "" or outputType == "ogg"):
                    os.system('avconv -loglevel panic -f pulse -i ' + audioDevName + ' -acodec libvorbis -ac 2 -vn "Music/' + playingInfo1 + '/' + playingInfo2 + '/' + playingInfo3 + '.ogg" &')
                elif (outputType == "mp3"):
                    # -aq 0 >= 320kbps, -aq 2 >= 166kbps -aq 3 >= 118kbps -aq 5 >= 96kbps
                    os.system('avconv -loglevel panic -f pulse -i ' + audioDevName + ' -acodec libmp3lame -aq 3 -ac 2 -vn "Music/' + playingInfo1 + '/' + playingInfo2 + '/' + playingInfo3 + '.mp3" &')

                print "Created new song file, now recording...\n"
            except:
                print "Error opening avconv! Is libav-tools installed?\n"
    except:
        print "Couldn't create new song file!\n"
                

### program start here ###

#variables and lists
p2 = ""

#create music dir if it doesn't exist
if(not os.path.exists("Music")):
    os.mkdir("Music")
    
#read configuration file
try:
    if(os.path.exists("record-pandora.conf")):
	print "Loading config file...\n"
	confFile = open("record-pandora.conf", "r")
        audioDevName = confFile.readline()
        audioDevName = audioDevName.rstrip("\n")
        delFileSize = confFile.readline()
        delFileSize = delFileSize.rstrip("\n")
        outputType = confFile.readline()
        outputType = outputType.rstrip("\n")
        confFile.close()
        if(outputType == ""):
		outputType = "ogg"
	elif(outputType != "ogg" and outputType != "mp3"):
		outputType = "ogg"
	print "Recording format: " + outputType + "\n"
    else:
        print "record-pandora.conf not found, please create it\nwith your audio device name and desired delete file size in bytes.\n"
        print "Example 1:\nalsa_output.pci-0000_00_14.2.analog-stereo.monitor\n800\nogg\n"
        print "Example 2:\nalsa_output.pci-0000_00_14.2.analog-stereo.monitor\n800\nmp3\n"
except:
    print "Error trying to read conf file"

### whitelist section ###
def whiteListArtists():
    try:
        if(os.path.exists("whitelist-artists.txt")):
            whitelistArtists = open("whitelist-artists.txt", "r")
            whitelistArtistsList = whitelistArtists.readlines()
            whitelistArtists.close()
        else:
            whitelistArtistsList = ""
            print "No whitelist-artists.txt found.\n"
    except:
        print "Error tying to read whitelist-artists.txt"
    
    return(whitelistArtistsList)
### end whitelist section ###
    
### blacklist section ###
def blackListArtists():
    try:
        if(os.path.exists("blacklist-artists.txt")):
            blacklistArtists = open("blacklist-artists.txt", "r")
            blacklistArtistsList = blacklistArtists.readlines()
            blacklistArtists.close()
        else:
            blacklistArtistsList = ""
            print "No blacklist-artists.txt found.\n"
    except:
        print "Error tying to read blacklist-artists.txt"
    
    return(blacklistArtistsList)
### end whitelist section ###
    
    
#try to run pianobar
try:
    print "Running pianobar...\n"
    cmd = "pianobar"
    p = subprocess.Popen(cmd, stdout=subprocess.PIPE, stdin=subprocess.PIPE)
    output = p.stdout.readline()
except:
    print "Error opening pianobar! Is it installed?\n"

while(True):
    if('|>  "' in output): #beginning of songs playing
        try:
            #kill recording of last song
            os.system("killall avconv")
            if(os.path.getsize("Music/" + playingInfo1 + "/" + playingInfo2 + "/" + playingInfo3 + "." + outputType) <= int(delFileSize)):
                os.remove("Music/" + playingInfo1 + "/" + playingInfo2 + "/" + playingInfo3 + "." + outputType)
                print "Removed file - too small: Music/" + playingInfo1 + "/" + playingInfo2 + "/" + playingInfo3 + "." + outputType
        except:
            print "Exception, avconv is not running\n"
        try:
            #try to clean up and format pianobar's output
            cleanPianobarChars = output.split('|>  "', 1)
            songName = cleanPianobarChars[1].split('" by "', 1)
            artistName = songName[1].split('" on "', 1)
            albumName = artistName[1].split('"', 1)
            #put Artist name, Album name and Song name into a list
            playingInfo1 = artistName[0]
            playingInfo2 = albumName[0]
            playingInfo3 = songName[0]
            #skip all artists not in whitelist
            whiteList = whiteListArtists()
            blackList = blackListArtists()
            if(blackList and playingInfo1 + "\n" in blackList):
                print "Skipping blacklisted artist: " + playingInfo1 + "\n"
            elif(playingInfo1 + "\n" in whiteList or whiteList == ""):
                    print "\nArtist: " + playingInfo1 + "\nAlbum: " + playingInfo2 + "\nSong: " + playingInfo3 + "\n"
                    #start dir check or creation and record to file
                    startRecord(playingInfo1, playingInfo2, playingInfo3)
            else:
                print "Not recording\nArtist: " + playingInfo1 + "\nAlbum: " + playingInfo2 + "\nSong: " + playingInfo3 + "\n(Not in whitelist)\n"
        except:
            print "Something went wrong with cleaning up pianobar output...\n"
    output = p.stdout.readline()


```

---

### Post by inexplikibled on 2015-09-17
Hey, nice job Marke1! I have actually implemented the blacklist feature already but I haven't uploaded the changes. Also the mp3 format option was something I intended to do as well but never got to because i had no need to do mp3 versus ogg but for most regular portable mp3 players the mp3 format is important, so thank you. To be honest I haven't been listening to pandora for a while so this script kind of fell into the background.

---

### Post by sicvolo on 2015-09-21
For those looking for a Pandora stream saver with a graphical interface, I forked Pithos into Pithosfly and gave it the magic mp3 saving abilities.

[https://github.com/SicVolo/Pithosfly](https://github.com/SicVolo/Pithosfly)

---

### Post by inexplikibled on 2015-09-21
Oh wow! That's really awesome sicvolo! I see it says you started that in 2010. Is that right? Anyway, that sounds pretty nice! 

Also, I wanted to mention to anyone interested: If you run my script in a virtual machine and basically let it run forever, you have the option to mute the virtual machine in the host OS but it will keep recording inside the VM itself without interruption. This is because the script is using the virtual sound card within the guest OS and you're simply muting the stream from the VM in the host.

---

### Post by joalheagney on 2015-09-29
Hi marke1, I made the following changes to lines 37 to 41 (Only lines 38 and 41 were actually changed).
```
                if(outputType == "" or outputType == "ogg"):
                    os.system('avconv -loglevel panic -f pulse -i ' + audioDevName + ' -acodec libvorbis -ac 2 -metadata artist="' + playingInfo1 + '" -metadata album="' + playingInfo2 + '" -metadata title="' + playingInfo3 + '" -vn "Music/' + playingInfo1 + '/' + playingInfo2 + '/' + playingInfo3 + '.ogg" &')
                elif (outputType == "mp3"):
                    # -aq 0 >= 320kbps, -aq 2 >= 166kbps -aq 3 >= 118kbps -aq 5 >= 96kbps
                    os.system('avconv -loglevel panic -f pulse -i ' + audioDevName + ' -acodec libmp3lame -aq 3 -ac 2 -metadata artist="' + playingInfo1 + '" -metadata album="' + playingInfo2 + '" -metadata title="' + playingInfo3 + '" -vn "Music/' + playingInfo1 + '/' + playingInfo2 + '/' + playingInfo3 + '.mp3" &')
```
This adds tags to the created file.

Thank you for the script. :D

---

### Post by inexplikibled on 2015-09-29
Here (finally) is an updated script available for download from my google drive. You will need all three files in the folder there.

[https://drive.google.com/folderview?id=0B9TMONbImIEdMDJqSjFFOEtNN00&usp=sharing](https://drive.google.com/folderview?id=0B9TMONbImIEdMDJqSjFFOEtNN00&usp=sharing)

Features:
1. Blacklist and whitelist support.
2. A more complete config file in JSON format. With options for: audio device, automatic ad deletion based on recorded file size, specify "blacklist" or "whitelist", location of list, save format, save directory.
3. Automatic prompting of installation of pianobar and libav-tools through apt-get.
4. First run of script sets up pianobar for station selection and pianobar config file for Pandora username and password.
5. Automatic deletion of incomplete recordings if user presses Ctrl + C.

Run the script: 
```
python record-pandora_9-29-15.py --conf config.json
```

Have fun!

---

### Post by KEYofR on 2016-01-19
Re-encoding the audio output is lossy and has all the other problems shown in this thread.
There is already a fork of pianobar which saves the incoming mp3 or aac data with no loss and no issues with volume and other audio events getting mixed in etc.
Google "pianobarfly"
[https://github.com/nega0/pianobarfly](https://github.com/nega0/pianobarfly)

---

