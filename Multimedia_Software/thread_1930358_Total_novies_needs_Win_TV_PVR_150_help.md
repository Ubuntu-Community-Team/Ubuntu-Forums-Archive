---
title: "Total novies needs Win TV PVR 150 help"
date: 2012-02-23
forum: Multimedia Software
---

### Post by watson524 on 2012-02-23
Hi all,

I am a total novice and was going to post in beginners but given the video issue, I thought it might be better here.

I used to run 8.04 (I think) and my Win TV PVR 150 card worked fine with TV time. When I upgraded to 10.04 LTS it won't work. TV time just opens and closes quickly when I start it. I think I read something about that not being supported on 10.04 so I tried TV viewer but that doesn't even start up. Click on it, does nothing. Me TV tells me there's no devices there. 

Like I said, I'm very new at all of this and on 8.04 things just "Worked" so I don't know what I should be looking at or where. 

Can anyone help?

thanks!

---

### Post by watson524 on 2012-02-23
I found this thread and was able to get it to work on VLC 

[http://ubuntuforums.org/showthread.php?t=1734916](http://ubuntuforums.org/showthread.php?t=1734916)

which is a great step forward for me but still TV-viewer doesn't start up and I don't want to use a command line to change channels. I actually have a remote for the TV card that used to work and I'd like to get working again as I'm often sitting across the room.

Also, I need to be able to schedule recordings (through a GUI preferably). 

How should I be going about this?

I just ran "tvtime" from a command line and get:

michele@michele-linux:/etc$ tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/michele/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

So I don't know what that means or what to do about it....

thanks!

---

### Post by wolfen69 on 2012-02-23
> **watson524 said:**
> 

but still TV-viewer doesn't start up
What about the TV-Remote I linked to in [my tutorial]("http://ubuntuforums.org/showthread.php?t=1734916")? You need to have java installed, and right click the tv-remote file, properties>open wth>java. And btw, changing channels via command line is not so bad. You don't have to retype the whole command each time, (leave a terminal open) just hit the up arrow and it will repeat what you previously input in the terminal, and then you only have to backspace twice and put in the new channel #.

---

### Post by watson524 on 2012-02-23
Forgive me for being very new at all this. I did look at that (and still might use it) but that doesn't let me change the channel from across the room like the remote that came with my card does. So let's say I get a client call (this is all in my office where I have my work laptop, a windoze machine and my main linux box) and need to hit mute quick. I have to go over to the other machine and do that. Where before I was able to use the remote from afar. 

Also - using VLC won't give me the ability to schedule recordings will it? Or can I do a cron job or something for that?

---

### Post by wolfen69 on 2012-02-23
> **watson524 said:**
> Forgive me for being very new at all this. I did look at that (and still might use it) but that doesn't let me change the channel from across the room like the remote that came with my card does. So let's say I get a client call (this is all in my office where I have my work laptop, a windoze machine and my main linux box) and need to hit mute quick. I have to go over to the other machine and do that. Where before I was able to use the remote from afar. 

Also - using VLC won't give me the ability to schedule recordings will it? Or can I do a cron job or something for that?
You *could* get a wireless keyboard with multimedia capabilities and use that to mute. 

You can get your remote control to work, but it's been a while since I've done it, and don't remember how off hand. [This]("http://www.lirc.org/") will get you started. 

I have used cron for recording, (not as hard as it might seem) but my favorite was TV-Viewer. Did you check the ReadMe (installation notes) for tv-viewer? You can't just click it to run it.

---

### Post by watson524 on 2012-02-23
I will check out the remote link and the install notes. I swear when I had it on 8.04 I did just click on it to run it. Maybe I'm remembering things incorrectly. I'll have a look at things hopefully tomorrow afternoon (otherwise it'll be a bit over a week as I'll be away for a week) and see what I can get sorted. Thanks for the links.

---

### Post by watson524 on 2012-02-24
I'm not actually seeing anything about how to run it [http://tv-viewer.sourceforge.net/mediawiki/index.php/Documentation:Installation](http://tv-viewer.sourceforge.net/mediawiki/index.php/Documentation:Installation)

I didn't do the installation like that because I just got it from the repository and it did the install on its own (I think, again, very new at this).

I found here [http://www.linuxquestions.org/questions/linux-software-2/tvtime-no-xvideo-port-found-which-supports-yuy2-images-ubuntu-9-10-a-775704/](http://www.linuxquestions.org/questions/linux-software-2/tvtime-no-xvideo-port-found-which-supports-yuy2-images-ubuntu-9-10-a-775704/)

where it's something with a bug. I thought I would have grub 2 since I'm on Lucid and that's what Karmic used but I don't have a file /etc/default/grub but I do have /boot/grub/menu.lst

I can't find where to add this GRUB_CMDLINE_LINUX="nomodeset" option tho. Could I just type that at the start of the file and then save, and run the grub update per the article?

---

