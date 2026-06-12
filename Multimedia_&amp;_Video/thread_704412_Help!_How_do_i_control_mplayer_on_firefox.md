---
title: "Help! How do i control mplayer on firefox?"
date: 2008-02-22
forum: Multimedia &amp; Video
---

### Post by ferdinando_villa on 2008-02-22
Hello,
I've finally managed to play streaming radio on the internet with the mplayer plugin on Firefox, but once i click on th mms link, I get a prompt to open mplayer, and when the radio starts playing, there are no controls for it on the website, and mplayer itself doesn't show, so the only way i could turn it off was to shut down the computer!
Now, is there a way to make mplayer controls visible? 
There is probably a very easy solution for this, but i'm really new to Linux, so sorry if it's really obvious...
thanks!

---

### Post by cozmicharlie on 2008-02-22
Right click on the mplayer screen.

---

### Post by ferdinando_villa on 2008-02-22
But the thing is, there is no mplayer screen; the radio starts playing without any visible screen, and if I open mplayer, it opens as a new section, without anything playing.

---

### Post by cozmicharlie on 2008-02-22
OK - I see - I tried it on my computer and was able to see what you mean.  First, you should not have to shut down the computer to stop it.  If you open the stream by right clicking and open in a new window or tab then to stop just close the window or tab.

Try this thread and see if it helps.   [http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

### Post by ferdinando_villa on 2008-02-22
I tried just that, and, oddly, when i close the new tab the radio keeps playing... do you have any other suggestions? Thanks for all the help!
Just in case, the link to the streaming is mms://media.itatiaia.com.br/Itatiaia

---

### Post by cozmicharlie on 2008-02-22
I could not open the link.  Is it a link from a web site?  Send me the link to the web site and I can see what happens when I try to play it.

Not sure why this is happening to you.  I might be able to help with stopping the process so you do not have to shut down the computer though.  When it is stuck on - open System>administrator>System monitor under the processes tab you should see mplayer (or totem) running.  You can "kill" the process and it should shut it down.  However, this is not a permanent fix.  

FYI - you can add a force quit to your menu bar that acts like alt-cntrl-del.  Right click on the menu bar>Add to panel- under "desktop and windows" is "Force Quit", click to highlight then click add.  Now you can use this to shut down programs that are locked.

Sorry I cannot be of any help - I am sure someone will come along that knows more about this than I do.

---

### Post by cozmicharlie on 2008-02-22
OK - got it.

I can open the stream in the terminal using
mplayer mms://media.itatiaia.com.br/Itatiaia

When I do it gives a message that 

```
mms://media.itatiaia.com.br/Itatiaia
```

When I do this is the output:  Note it says "failed to open LIRC support.  You will not be able to use remote control."  Might be an issue with the site.  What happens if you try to stream from other sites?  


MPlayer dev-SVN-r25873-4.1.2 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Pentium(R) D CPU 2.80GHz (Family: 15, Model: 4, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing mms://media.itatiaia.com.br/Itatiaia.
STREAM_ASF, URL: mms://media.itatiaia.com.br/Itatiaia
Resolving media.itatiaia.com.br for AF_INET6...
Couldn't resolve name for AF_INET6: media.itatiaia.com.br
Resolving media.itatiaia.com.br for AF_INET...
Connecting to server media.itatiaia.com.br[200.251.164.68]: 1755...
connect error: Connection refused
Resolving media.itatiaia.com.br for AF_INET6...
Couldn't resolve name for AF_INET6: media.itatiaia.com.br
Resolving media.itatiaia.com.br for AF_INET...
Connecting to server media.itatiaia.com.br[200.251.164.68]: 80...
Resolving media.itatiaia.com.br for AF_INET6...
Couldn't resolve name for AF_INET6: media.itatiaia.com.br
Resolving media.itatiaia.com.br for AF_INET...
Connecting to server media.itatiaia.com.br[200.251.164.68]: 80...
Cache size set to 64 KBytes
Cache fill: 12.50% (8192 bytes)   
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 name: Rádio Itatiaia
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 16000 Hz, 1 ch, s16le, 16.0 kbit/6.25% (ratio: 2000->32000)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))

---

### Post by ferdinando_villa on 2008-02-23
Thank you very much for all the help and effort! I'm new to Linux and it's very encouraging to see that the community really works, and it's very supportive, so thanks, i really appreciate it.

But about the mplayer, i've tried some other sites that offer streaming on mms, and the same thing happens - it is indeed odd, i don't know what is going on. However, i can for the moment terminate the process with System Monitor, that works fine. The shortcut to 'force quit' on the panel doesn't work in this case, for it tells you to click on the window of the program you want to quit...

The website of the radio station is [http://www.itatiaia.com.br/](http://www.itatiaia.com.br/) - it's in portuguese, but the link to the streaming is a small blue button near the top that says ''ouça".

Once again, thank you very much for your trouble in trying to solve this issue! If we can't figure out what is going on, it's not very serious, so don't worry.

---

### Post by cozmicharlie on 2008-02-24
Well after trying many different suggestions I have found a way for you to play and have controls which is the good news - the bad news is I could not get it to work in the browser.  I have listed a few methods that you may want to try at the bottom of the post.  The method I used to get it to work is as follows:

[LIST=1]
[*]Install vlc from synaptic
[*]open the link in a terminal using this command
```
vlc mms://media.itatiaia.com.br/Itatiaia
```
[*]It will open in vlc and you will have all the commands (stop, play etc) at your disposal.
[/LIST]

Or, to make it easy write a small scrip to launch it:
[LIST=1]
[*]Open a terminal and type or cut and paste the following.
```
mkdir ~/bin
```
```
cd ~/bin
```
*This creates a new folder in your home directory called bin.  We are going to place the script there.  For now, leave the terminal open.
[/LIST]
[LIST=1]
[*]Open a text editor (any text editor).
[*]Write or cut and paste the following:[INDENT]
#!/bin/sh
cd usr/bin 
vlc mms://media.itatiaia.com.br/Itatiaia[/INDENT]
[*]Save it to the home/bin directory you created - name it Itatiaia
[*]Now we need to change the mode: Go back to the terminal that you left open and at ~/bin prompt type or cut and paste:
[*]```
chmod +x Itatiaia
```
*This changes the mode and makes it executable.
[/LIST]

At this point there are a number of options - you could move it to the desktop or I like to add them to the menus.  right click Applications on the panel>edit menus> under menus click internet (or wherever you want it added)> click anywhere in the &#8220;show&#8221; &#8220;item&#8221; box > click new item and the create launcher dialog box should open type the following:
[INDENT]Type: Applications
Name: Itatiaia
Command: browse to the script you created above (in your home/bin folder and add it)[/INDENT]
Comment: whatever you want to call it - stream Itatiaia
*This is optional: you can browse to the images and use an image

Now when you want to listen just go to your menu and click on it.  Give it a few minutes to connect and you should be listening in vlc with all controls.

A bit of a workaround but it works - gooooooooooooooooooooooooooooooooooooooooooooooooal
Enjoy

As per other methods, you could try these and see if they work for you.

media play connectivity as described here [http://ubuntuforums.org/showthread.php?t=647611&highlight=mms](http://ubuntuforums.org/showthread.php?t=647611&highlight=mms)
(note though all you have to do to install is go to the Firefox add-on page)

Or you could try totem-xine some report this works - it did not for me.

---

### Post by wolfen69 on 2008-02-24
it works for me.

download vlc player from synaptic.
go to website.
right click the ouca link and copy link address.
open vlc>file>open network stream>select http/https/ftp/mms
paste in link address, then OK

this not a pretty solution, but it works. give the stream a while to start up.

also, this solution works for other web sites as well, where regular methods will not. vlc is a very powerful media player/streamer.

---

### Post by cozmicharlie on 2008-02-24
> **wolfen69 said:**
> it works for me.

download vlc player from synaptic.
go to website.
right click the ouca link and copy link address.
open vlc>file>open network stream>select http/https/ftp/mms
paste in link address, then OK

this not a pretty solution, but it works. give the stream a while to start up.

also, this solution works for other web sites as well, where regular methods wont.


That will work - it is basically the same as doing this in the terminal - 
```
vlc mms://media.itatiaia.com.br/Itatiaia

```
For those that have terminal phobia, wolfen69 method will also work fine

---

### Post by wolfen69 on 2008-02-24
> For those that have terminal phobia, wolfen69 method will also work fine
that is exactly why i post the gui method. some people are more comfortable with point and click. plus they get to open up vlc and see some of the other functions it has.

---

### Post by ferdinando_villa on 2008-02-25
Yes, the script solution works very well, and in fact now that it is on the menu is even much easier than going to the website!
Thank you very much for the time and effort, i really appreciate it!

---

### Post by cozmicharlie on 2008-02-25
Great - also, you can add it to your desktop.  Right click on it in the menu and you have an option to add it to your desktop.

If you feel this is solved then please mark it solved in the thread.

Enjoy

---

