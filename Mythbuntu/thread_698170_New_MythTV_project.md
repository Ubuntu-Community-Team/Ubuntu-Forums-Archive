---
title: "New MythTV project"
date: 2008-02-16
forum: Mythbuntu
---

### Post by cyruspy on 2008-02-16
Hi, i'm pretty new to MythTV (although not to linux), and would like to know if Mythbuntu has certain features.

- Does it have a FM radio plugin?
- I have a usb internal memory card reader, can it detect new cards (from my digital camera mainly) being inserted and support picture browsing/slideshows?

---

### Post by nasha on 2008-02-18
No FM radio plugin as of yet. Thought it has been marked for future releases im pretty sure.
MythTV itself does have picture browsing capabilities, but to get it to automatically look in the card reader everytime you plug a card in would involve some scripting

---

### Post by ian dobson on 2008-02-19
Hi,

There isn't a FM plugin and from what I've read there won't be one.

I'm currently trying to put together a simple hack that can send a radio signal over a network connection to my myth frontend. At the moment I can send a FM radio stream from a PVR-500 in my server to another PC using the following code:

frontend: nc -l -p 5000 | mplayer -
backend: ivtv-radio -v  -f 104.3 -d /dev/radio0  -c "sox -t raw -r 48000 -w -s -c2 %s -t ogg  -  |nc 192.168.0.2 5000" 

All I need to do is wrap the backend in a perl script and write abit of xml for Myth frontend. It'll take me a while to get it going but maybe I can do it :)

Have a look here for a quick and dirty hack:- [http://www.mythtv.org/wiki/index.php/Fm_radio](http://www.mythtv.org/wiki/index.php/Fm_radio)
Regards
Ian Dobson

---

### Post by ian dobson on 2008-02-21
Hi,

OK the XML was easy, now for the hard bit. Communication between the frontend and backend. 

I'm thinking about just using netcat/bash for both the frontend and the backend. 

One thing I've noticed when I listen to the radio and try to record fron tuner0 (I have a PVR 500) I only get a green screen recorded. So it looks as if I need to tell mythtv that the tuner is busy or an easier solution just add a FM tuner to my backend.

Regards
Ian Dobson

---

### Post by ian dobson on 2008-03-06
Hi,

Finally got round to working on a radio beamer.

The backend deamon (perl script) is working almost all of the time.
The frontend script always starts mplayer with a network pipe from the backend but doesn't always play the selected radio (you hear nothing). 

I think it's a timing problem but I've not had a chance to look at it. Maybe this weekend.

Regards
Ian Dobson

---

### Post by ian dobson on 2008-03-06
Hi,

OK I hacked about in the code abit this evening, and I've got it working almost. The program consists of:-

1) A perl deamon that listens for connections from the frontend
2) A small script on the frontend that tells the backend what frequency to use.
3) A small script that uses the ivtv-radio -s output to generate a xml menu file for mythfrontend

(3) isn't working exactly as it should. the XML file looks OK to me but mythtv crashes when ever I open the radio menu.

So, who is interested in a copy?  I won't create a package, just manual install instructions if enough people say please.

Regards
Ian Dobson

---

### Post by amphibem on 2008-04-25
I am definatly interested in what you have done here, would creatly appreciate if you could post scripts/instructions so I could get radio working with my system  :)

Otherwise I will start to work through that guide you linked, however my Linux skills are limited so don't expect much.

---

### Post by ian dobson on 2008-04-27
Hi amphibem,

Give me afew days and I'll try and put together something together.

You need to manually edit several files but I'll try and get it as automagic as possible.

Regards
Ian Dobson

---

### Post by amphibem on 2008-04-27
> **ian dobson said:**
> Hi amphibem,

Give me afew days and I'll try and put together something together.

You need to manually edit several files but I'll try and get it as automagic as possible.

Regards
Ian Dobson

Ian,

Sorry I had been meaning to get back on this! I appreciate the offer, however I actually have radio working now.

I got it working on my machine following the guide you linked, I hadn't read your posts properly to notice you were talking about getting seperate Frontend/Backend radio working; I only have a single combined machine so it was much simplier.

Im sure others (including myself in the future) may still appreciate if you posted you scripts though :)

---

### Post by silverdulcet on 2008-04-29
> **cyruspy said:**
> Hi, i'm pretty new to MythTV (although not to linux), and would like to know if Mythbuntu has certain features.

- I have a usb internal memory card reader, can it detect new cards (from my digital camera mainly) being inserted and support picture browsing/slideshows?

Mythtv does support importing your pictures to the directory you have set in **Utilities/Setup>Setup>Media Settings>Image Settings**

By default that is /var/lib/mythtv/pictures

To import the pictures from your usb card reader or the camera itself you need to know the directory that it is mounted to. For that just insert the card and/or plug in the camera. Then look in the /media directory to find out where it mounts the device. Then put the path to that mount point into the **Paths to import images from:** box. You can place multiple mount points seperated by colons **:**

Once you have the path to your device(s) then just go to the **Media Library>Image Gallery**, hit the menu key and then import. If your card or camera is plugged in and you have the correct mount point in the settings it will import all the pictures on those device(s) into a folder with the current date. Then you can browse and start slide shows. Unfortunately the current Image Gallery doesn't support manipulating images so they fit on the screen. You can rotate them, but if they are taken portrait style it will cut off the top and bottom of the image (whatever doesn't fit on your screen).

---

### Post by pmbsa on 2008-08-07
Hi Ian, I would be very interested in getting my hands on what you are doing for Radio streaming (if you are still doing anything that is).

cheers
Paul

---

### Post by ian dobson on 2008-08-07
Hi Paul,

I've not done anything on this for a while, but I still have to code on my server/frontend so if you want I'll zip it all up and post a link here sometime this weekend, if I actually manage to leave site.

It won't be a "simple" install. You'll have to manually edit several files/create init scripts and manually edit the myth theme files to all extra buttons but it's not too had to do.

Note if you only have one box (ie not a seperate frontend/backend) you can actually get radio working with a simple hack. Have a look at post number 3 in this thread.

Regards
Ian Dobson

---

### Post by pmbsa on 2008-08-07
Thanks Ian, I have had the simple hack for some time, I want to move away from having a tuner on every client in the house if I can so very interested in streaming option, not worried about the complexity really so I would really appreciate it if you could send me what you have.

thanks
Paul

---

