---
title: "Audio Only, No Video"
date: 2010-08-16
forum: Mythbuntu
---

### Post by irie on 2010-08-16
I'm running Lucid and Mythbuntu 10.04.  I have a Hauppauge PVR-500.  I have everything running for the most part.  When I go to "watch tv", I have audio but no video.  I'm stumped.  I've tried different settings for the capture cards but no avail.  Everything was working at one time under 9.10 then stopped.  I quit messing with it until I upgraded to 10.04.

Any help and figuring out this issue would be great.

---

### Post by ian dobson on 2010-08-17
Hi,

Can you try recording something then try watching it (Is the problem live TV or video in general)

What graphic card are you using?

Have a look in your log files (/var/log/mythtv/mythfrontend.log) to see if it's listing any errors.

Regards
Ian Dobson

---

### Post by irie on 2010-08-17
Same thing with a recorded show.  Audio but no video.  I was googling around and read something about ivtv.  I installed that and nothing changed.

---

### Post by ian dobson on 2010-08-18
Did you try playing the recording on a different computer, with vlc maybe?

Regards
Ian Dobson

---

### Post by irie on 2010-08-19
I just checked, it's recording just fine.  Just for some unknown reason there is no video in mythbuntu.  You can see a slight change in the screen where a video should be but thats it.

---

### Post by ian dobson on 2010-08-19
Hi,

Then have a look in the mythfrontend.log in /var/log/mythfrontend.log.

maybe you'll see an error there.

Regards
Ian Dobson

---

### Post by LowSky on 2010-08-19
I used to have a similar issue every once in a while, it turned out my graphics card wasn't handling VDPAU properly.

On the frontend, Utilities/Setup>Setup>TV Settings>Playback, 3rd screen. 
change the playback profile to something else. Try each one until video looks clean and crisp without haing problems

---

### Post by irie on 2010-08-19
Ian, no log files.
LowSky, I went through all the profiles and nothing.  I even created a test one to see what would happen.  Nothing, screen just said please wait.

It's very frustrating when something worked at one time and now it doesn't.  arrghh

---

### Post by winewood on 2010-08-20
The only times I saw "please wait" was when:
1. My card wasn't active before the backend started and I had to reset my backend.  Then after starting the frontend again, I could see video.
2. The directory for my videos didn't have the right permissions to allow mythweb to read/execute the files.  For troubleshooting purposes I created a new directory /opt/videos and ran 'sudo chmod 777 /opt/videos' , then pointed the video to record in that location, and magically it worked.

---

### Post by irie on 2010-08-21
I just tried what you suggested winewood, nothing has changed.  The cars are active according to the status page.  I tried all of the nvidia drivers also.  nada.

---

### Post by winewood on 2010-08-21
I may have missed it, but what video card do you have?  Some NVidia cards are not supported from the generic/default NVidia release.  Try getting the specific driver from the NVidia website and installing manually.
 
Ian has a great suggesting in using VLC as, if you can play video using it, your graphics card and drivers can be excluded for the most part.  Use a file from your previous install or if not, I suggest using "winscp" to put an .mpg file onto your machine from your "other" machine.  
 
Permissions were a big glitch in my install.  My MythTV application was owned by 'mythtv', but my login name was different at the autolaunch at reboot.  I edited /etc/group and put my username in the same group as 'mythtv'.  (yes, I know there is a command for this, but I am a big ol hack at heart)  I am not saying this is "the" fix, but it got me past a few bugs.
 
If you have not scanned with your capture card and put the "starting channel" of that tuner to a working channel, you may need to re-scan to verifiy a good channel.

---

### Post by irie on 2010-08-27
I have done what you said about installing the Nvidia drivers.  I thought that would fix it.  Nope.  I can record shows, just can't watch them in Myth.  Is there a way to have VLC be the video player in Myth instead?

---

### Post by winewood on 2010-08-28
Please tell me what username the myth frontend runs under.
 
What username owns the directory and what are the permissions? 
 
Is your username running the app and owner of the directory in the 'mythtv' group?

---

