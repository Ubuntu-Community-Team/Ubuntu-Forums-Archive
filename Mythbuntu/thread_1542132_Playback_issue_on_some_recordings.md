---
title: "Playback issue on some recordings"
date: 2010-07-30
forum: Mythbuntu
---

### Post by rvindum on 2010-07-30
Running MythBuntu on a virtual machine, whith a HomeRun HDTV box. All works fine, when I use XBox media center or Myth itself to playback recordings.
 
Purchased a WDS Live TV box so I can see the recordings in my livingroom. However - some recordings won't playback using DLNA, but can play if I play them through the shared files (however hard to find the correct file here).
 
Thought the problem was when the recording was done witht the seconday tuner - but as all episodes of NCIS doesn't work - this is not the case.
 
Furthermore - some recordings can't play when I use Windows media player - and here I can see that mpg header information is somewhat wrong - Datarate 145kps & Total bitrate 337, where working files are above 2500 in both values.
 
Someone got a hint how to fix this issue - as I haven't got a real frontend, only the small WD box.

---

### Post by ian dobson on 2010-07-30
Hi,

Maybe there's a firmware update for your HomeRun or WDS Live TV.

MythTV just reads the video stream from the recorder and writes to to a file so if the stream is screwed then the file saved is screwed (GIGO - garbage in, garbage - out (not FIFO,LIFO)).

Regards
Ian Dobson

---

### Post by rvindum on 2010-07-30
Hi Ian.
 
Wrote with Silicon to ensure that the box didn't crap up the stream headers - and they just stream so the header is from MythSoftware (running the latest HomeRUN beta firmware aswell). 
 
The thing is - that **all **episodes of NCIS won't play using DLNA, but play through the share on the WDS (which also has the latest firmware - not the Beta though). Some episodes and movies won't play on the WDS box (DLNA only) - so it must have to do with how the Myth/DLNA communicates?
 
Regards
 
René

---

### Post by ian dobson on 2010-07-30
Hi,

Is the problem with all recordings from the same channel as NCIS?

Could you try a lossless transcode for a NCIS recording then play it back? It sounds as if the channel is streaming dodgy streams/you've hit a really obscure bug in UPNP/the wds live.

Regards
Ian Dobson

---

### Post by rvindum on 2010-07-30
Hi Again.
 
Just researched a bit more - and you've might be right about this TV Channel. Although I'm sure I saw a similar bug when I recorded two programs at the same time on a different channel.
 
*The recordings still work when using XBMC, MythTV or streaming with mediaplayer from the MythWEB. All recordings work with WDS Live when playing through the share.*
 
I'm fairly new to Myth (Ask me a Windows question instead. ;) ) - but I can't see that Myth is doing a transcode on the files (except commercial flagging) - and the HDTV box streams MPEG2 directly.
 
Might be a bit dumb here - but I've never really worked with Linux and/or Myth until a short time back - so all help is really appreciated.
 
Thanks - René

---

### Post by rvindum on 2010-07-30
Hang on - found a cmd line tool for dooing a transcode - running it now.

---

### Post by ian dobson on 2010-07-30
Hi,

Looks as if you have found an obsure bug in UPNP/wds live.

Sorry I can't help you much more than this. I don't use UPNP and don't use HomeRun, but if it works through a share and doesn't through UPNP then something is screwing up the stream.

Regards
Ian Dobson

---

### Post by rvindum on 2010-07-30
Hi again.
 
Not sure about the lossless transcode process - but tried running the mythtranscode on a "corrupt" file. Didn't do anything, but I found that 95% of the recordings from this channel is having problems.
 
But again - something from the Myth software is ****ing up the stream - but why only with this channel - and why is a few of the recordings working using UPNP?
 
I wish I had an alternate solution - but can't find a cheap and good miniPC to use as a frontend.
 
Regards
 
René
 
**Update**
Set the next recording as lossless and will see what this does. Found that two different channels is having this problem with some (not all) recordings - go figure???

---

### Post by rvindum on 2010-07-30
Even stranger....
 
Tried to stream the Myth files from my Windows machine - which works - so it must be something with MythTV... :(
 
René

---

### Post by ian dobson on 2010-07-30
Hi,

Sorry, I'm not sure. UPNP is nothing more than streaming video per http.

The only thing I can think of is that upnp allows the client to inform the server what formats it supports and the server "should" transcode to a supported format.

Regards
Ian Dobson

---

### Post by rvindum on 2010-07-30
Hi again.
 
Seems like there is something located in the MythDatabase - as I tried to convert a faulty file to a working one - same problem.
 
Nevertheless - the file works, but MythTV can't figure out how to stream. Might try the hacked version of WD Live and see how this runs - but wanna read a bit more about this first.
 
 
Thanks for trying to help though.
 
Regards
 
René
 
______________________________
[[COLOR=gray]*www.b4failure.com*[/COLOR]]("http://www.b4failure.com") [COLOR=black]|[/COLOR] [[COLOR=gray]www.silents.dk[/COLOR]]("http://www.silents.dk")

---

### Post by newlinux on 2010-07-30
If you can do streams over shares and they work all the time and you just don't like the filenames try using:

[http://www.mythtv.org/wiki/Mythlink.pl](http://www.mythtv.org/wiki/Mythlink.pl)

to make better filenames.

Also, I have found it common with various UPnP servers (including myth) that some things don't stream right over UPnP but work fine if accessed directly from the same device. Sometimes the problem has been the client, sometimes the server...

---

### Post by rvindum on 2010-07-31
I saw the script (haven't read much about it though), and it is an option, although a workaround. :( The issue is, that recordings don't get indexed by category and channels - so all recordings will be placed in one long list.
 
Tried to link the files from MythTV to my Windows Media Center, and from here they play without any problems through the WDS aswell. So it seems as the problem is purely Myth related?
 
______________________________
[[COLOR=gray]*www.b4failure.com*[/COLOR]]("http://www.b4failure.com") [COLOR=black]|[/COLOR] [[COLOR=gray]www.silents.dk[/COLOR]]("http://www.silents.dk")

---

### Post by newlinux on 2010-07-31
It's certainly related to myth's UPnP server since only over UPnP is it having problems, but unless you test it with another UPnP server or use myth's server with another UPnP client you don't know which side the problem is on.

---

### Post by rvindum on 2010-07-31
Already tried with Microsoft (think I wrote this earlier?). Anyhow - using the Myth files through mediaservice with the WD Live - it works fine.
 
So yes - it's Myth UPnP which is failing with some recordings?! :(

---

### Post by newlinux on 2010-07-31
you used a microsoft UPnP server with myth files? What do you mean by you "tried it with microsoft" you said to tried to stream files from windows. If it wasn't using a different UPnP server with the same files that doesn't tell you for sure that it myth's UPnP server is the problem. In any event, you have workarounds if you need them.

---

### Post by rvindum on 2010-07-31
Copied Myth files that didn't play from Myth to Microsoft. Streamed the files from Microsoft without any issues - so my best guess is Myth UPnP is having some fouls in the streaming. Files plays through network share on both Myth and Windows.
 
Workarounds ain't my kind of coffee - sorry - just a way of saying that the issue can't be solved properly. So I guess I have to go back to the drawing board and figure out another TV/PVR solution. :(

---

### Post by newlinux on 2010-07-31
yeah, from my experience with UPnP I wouldn't count on it for everything from any server. And I certainly wouldn't call it myth's strongest feature. Find whatever works for your setup.

---

### Post by nickrout on 2010-08-01
myth's upnp delivery is, cough, less than ideal.

Then again the "frontend" you have may not work correctly either. Often these devices are VERY fussy about bitrate, codec, muxing, pretty well every damn thing that might vary in a multimedia file. Also myth's dlna implementation does NOT support re-encoding on the fly, so the client is fed the file as saved by myth, which is as sent by the broadcaster (albeit obviously remuxed).

There are better upnp implementations for linux, like minidlna. 

There is a quite long thread on here about sony bravia tvs and dlna - the search function will find it. It has lots of tips on minidlna.

---

### Post by rvindum on 2010-08-01
Will check it out. 
 
Is is just making UPNP/DLNA and showing the files, or does it work like Myth was supposed to - do you know?
 
Thanks for the idea.

---

### Post by rvindum on 2010-08-09
Just tested the mythlink.pl script - and no dice. :( Doesn't work with WD Live, as it thinks the files are folders and when accessed it just says that they are empty....

---

### Post by nickrout on 2010-08-10
> **rvindum said:**
> Just tested the mythlink.pl script - and no dice. :( Doesn't work with WD Live, as it thinks the files are folders and when accessed it just says that they are empty....

As you said earlier, you are not into workarounds.

So buy a revo and get a real frontend!

---

### Post by rvindum on 2010-08-11
For anyone having the same issue and wanting a cheap frontend for some of the TV's - I did the following.
 
1) Used Mythlink.pl to link-rename the recorded files, through the system event handlers.
2) Installed MiniDLNA and pointed this to the Mythlink.pl destination directory.
 
Can now see ALL files recorded with MythTV using DLNA, and has a useable filename, and directory structure. So this is useable, until MythTV (hopefully) fixes this issue.

---

### Post by mnclayshooter on 2010-11-14
I realize this is slightly old thread, but I'm having a very similar problem that I posted on the forum here a week or so ago.  I've found that the descriptions in the mythconverge database are too long.  If the EPG data is not formatted exactly correctly, Myth seems to use the description as the subtitle.  If it does this, the data is way too long for DLNA... long story short, when I use phpMyAdmin to edit the descriptions to be shorter, it DLNA works flawlessly.  
 
Hope it helps.  I don't know how to solve it, I just know that I've identified a symptom of the problem.  
 
 
My post - if it helps:
 
[http://ubuntuforums.org/showthread.php?t=1615162&highlight=DLNA](http://ubuntuforums.org/showthread.php?t=1615162&highlight=DLNA)

---

### Post by rvindum on 2010-11-17
Hi there.
 
Thanks for the update - you might be right, havent checked the data as you describe them here. Have you reported this to Myth so they can fix this issue?
 
Would be a bit sad that I would have to recompile the code for it to be overwritten once the next update arives. :o(

---

