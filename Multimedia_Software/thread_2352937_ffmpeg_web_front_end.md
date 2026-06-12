---
title: "ffmpeg web front end"
date: 2017-02-17
forum: Multimedia Software
---

### Post by KOUTRONAS_Mixalis on 2017-02-17
Hi to all, those days i setup a ubuntu server with webmin webui. and i would like to use it as a remote encoder for footage. My goal is to have this server where the footage will be on it and i would be able to control ffmpeg via a web interface so i can turnoff my main computer and let the pc encode videos over the night. this server would be use from people that dont know linux commands. thank you

---

### Post by TheFu on 2017-02-17
Not sure I understand.

But if you just want to batch transcode recordings, that is pretty easy.  It is dealing with captions, commercials, and settings for the different types of recording resolutions that makes it hard.
I find handbrake to be faster than ffmpeg of similar settings - about 2x faster.

Or if you like, you don't need to transcode anything. Just use Plex Server and it will transcode as needed for the playback device.

I have a number of mostly automatic scripts that handle recorded TV in the ways I prefer
* recording can be done by any method you like - mpeg2 video is the easiest to handle
* 2x a day, another script runs comskip to location commercial breaks.  It isn't 100% accurate, so manual validation of the breakpoints is needed.  That takes about 30 sec per recording.  Those cut marks are saved into an EDL file which can be batch processed.
* After all the commercials have been removed, I'll grab any captions and store those into SRT files. Usually only 1 set is gotten, but sometimes 2 different languages come out.
* Next transcoding to h.264/vorb/mkv is my preference.  I have different presets based on the resolution from the recording. Anything higher than 720p is transcoded down to 720p.  Anything lower is left at the current resolution.  I don't want 1080p or higher resolutions.
* When all that is completed, the files need to be moved into the playback library. That is a Plex Server here.

Not everything is automated. I spend about 5 min every morning doing manual things.

The simple command is:

```
nice ffmpeg -i - -c:v libx264 -crf 19.5 \
         -vf scale=-1:720 \
         -preset veryfast \
         -c:a libvorbis -q:a 6 "$in.mkv"

```
But the scaling needs to be removed if the input video is less than 720p resolution. Don't want to have a 480i recording exploded up to 720p, right?  Wouldn't be hard to have the script loop over all the mpeg/ts files in a directory.  And if that can be done, why not just make it automatic, daily, using cron?

Hummmmm.  Think I'm convinced. I need to do that here.  I'll create 3 input directories for different types of recordings to keep it simple.  HandbrakeCLI can use existing presets, which will make it really easy to script rather than using ffmpeg.

I know this probably doesn't answer your question (though i'm not sure what you seek). Seems you want some sort of web server?  Please clarify.

---

### Post by KOUTRONAS_Mixalis on 2017-02-17
My cousin do video editing we to need encode video footage and to render the final video as well as encoding videos from dvd or blueray to mkv when needed. we use it with premire and frame server for export. There are software like sorenson sqeeze server and telestream episode that encode video footage and to render the final video. but  1st they are expensive and 2nd they work on windows server edition .  So the best thing for me is to use ubuntu server (i dont want the unity gui thats why i installed webmin so i can control that machine from a web browser )eliminates me to format this machine every time. this machine is also used as a nas server and download torrent server. [https://sye.dk/convert/](https://sye.dk/convert/) mi found this but is working only on windows i would like something similar but for linux
Thank you for your help i appreciate it a lot but the problem is that my cousin dont know about scripting and would like something ease to use.
PS: the tool have to do batch encoding as well.

---

### Post by TheFu on 2017-02-17
You don't have to use Unity.  There must be 50 other GUIs available.  On Linux, the GUI is just another program.  For lighter/quicket GUIs, check out XFCE, LXDE, Mate, or even KDE.

If you need a remote GUI, take a look at x2go. It won't work with Unity, but flies with LXDE/XFCE. x2go is an NX protocol. There are clients for Windows, Linux and OSX.

There are also html5-based desktops for Linux which run inside a browser.  I was always concerned about having any webserver running on a system that wasn't locked down completely. Websites are hacked all the time.  I've never used webmin - tried when I was first learning Unix, but it was much harder to setup back then. Now I know better than to put system administration into a webserver. Others obviously have different opinions, and likely different priorities.

Sorry that I'm not more help.  Good luck.

---

### Post by KOUTRONAS_Mixalis on 2017-02-17
thank you a lot the computer will be used localy so we are not afraid of hacking but x2go is what i need thank you a lot openbox and flux box with puppty and xmin will also do the thing but x2go is what i was looking for . Linux is fantastic.

---

### Post by TheFu on 2017-02-17
Glad to be of help.

You should know that many people use VNC for this, but VNC is 2-3x slower than x2go.  VNC isn't as secure as x2go, so a tunnel with either a VPN or ssh is needed.

x2go has ssh built-into the protocol, but you still must configure it.  It is NOT possible to use x2go without ssh.

To setup x2go, first setup ssh access between the client and server machine. Don't bother going any further until ssh is working.
Next, install the x2go PPA for your specific release following the x2go instructions at their website.  There are client packages and server packages.  Also, there are important steps that must be taken for the x2go client to work from Windows (mainly fonts must be installed).

Because x2go uses ssh, it is considered secure enough for use over the internet.

If you've never used ssh before, be certain to learn about it in depth.  It is one of those few solutions that is both, more secure AND more convenient.  ssh is how Unix systems are managed and how admins connect, transfer files, and do 100+ other things.  ssh is in my top 10 of the worlds greatest inventions.  x2go isn't even in the top 100 list.  Please understand - **ssh is simply amazing** - it can do more than I know, which is a bunch after 25 yrs of this stuff.

---

