---
title: "Share TV tuner over network?"
date: 2009-03-13
forum: Multimedia Software
---

### Post by pickarooney on 2009-03-13
I'm just wondering is there a way to do this and which way around I should go about trying it. 

I have a desktop with a TV Tuner running tvtime and a laptop connected over the network to my router and thereby the desktop. 

would it be feasible to either

a) share the device /dev/video1 from the desktop and install and run tvtime on the laptop so that it points to the remote device

b) run tvtime on the desktop and export the display to a screen on a remote machine?

The latter option would make it difficult to change channels/volume, I imagine.


If anyone has another idea, I'm all ears.

---

### Post by issih on 2009-03-13
I know nothing about tv time, and its quite posssible that you specifically need that application for some reason, but I thought I'd just say that this behaviour is a built in part of myth tv.

myth-backend on machine with card.

mth-frontend on any pc within the network you want to watch tv on.

Works beautifully between my desktop and laptop.

Hope that helps.

---

### Post by pickarooney on 2009-03-13
> **issih said:**
> I know nothing about tv time, and its quite posssible that you specifically need that application for some reason, but I thought I'd just say that this behaviour is a built in part of myth tv.

myth-backend on machine with card.

mth-frontend on any pc within the network you want to watch tv on.

Works beautifully between my desktop and laptop.

Hope that helps.

Sounds good, only the last time I tried mythtv I needed to create an extra user and log in as that user, which didn't suit me at all. Is that still the case or was I completely off the mark in the first place? I'll have a scout around for a few tutorials.

> 
You can use VLC with the TV tuner card to set up a pvr stream. Then open VLC on your remote machine and open the stream. This can be done over http without any problem. The easiest way to set up the stream is to use the wizard. File->Wizard. Try it out and see how it goes.


I'll give this a lash. I don't know what a PVR stream is, but I guess I'll soon find out. 

Thanks to both of you :)

---

### Post by pickarooney on 2009-03-13
No luck. I couldn't find a tutorial that uses a version similar to the one I have (from the Intrepid repositories) and so I failed on two fronts - viewing the TV with VLC and sharing anything across the network.

Having failed to capture the TV signal (I just told VNC to open device /dev/video1 (this works for tvtime) and use the local SECAM standard, but nothing came up) I tried opening an AVI to stream it. I went to Media, Streaming, ticked RTP (there's no UDP option in this version) and Prefer UDP over RTP with the IP of my laptop and port 1234. I tried some random options for enapsulation, audio and video and hit Stream. Then I opened VLC on the laptop and tried Open network, selecting UDP port 1234 but nothing happened.

---

### Post by issih on 2009-03-13
Generally myth tv does create a mythtv user, but that is pretty much to have an "identity" for it to run things as, you certainly don't need to be logged in as that user to run the program. Mostly you just use the mythtv user as a login to the sql database, within the myth config apps.

if you feel like giving it a go, just install mythbuntu control centre from synaptic and it will walk you through most of the necessary steps, its got a lot more user friendly in the last few releases.

Once the backend is set up, just install mythfrontend (easiest to just use mythbuntu control centre for that too) on any machine you want to watch on and hey presto one working set up (well once you enter the basic config details in each machine)

I regularly watch tv on my macbook (happily there is a mythfrontend build for OSX), it works perfectly.

Can't really help with the vlc solution I'm afraid as I've not played with it..I am tempted now though :)

---

### Post by pickarooney on 2009-03-13
I'll try mythbuntu tomorrow. Meanwhile I managed to stream an AVI with a simple command line and pick it up on the laptop:

vlc -vvv $1 --sout '#standard{access=http,mux=ogg,url=192.168.1.10:8080'}

Then I somehow managed to open the TV on the desktop with VLC but couldn't change channels or share the picture. 

Just a few more things to figure out and it'll be good I think.

---

### Post by pickarooney on 2009-03-14
So I got the mythbuntu control centre, frontend and backend installed but I'm kind of stuck. I eventually got the MySQL connection done and scanned for channels. I've idea what mythfilldatabase is supposed to do, but when I run it I just get as far as

XMLTV config file is: /home/pickarooney/.mythtv/.xmltv

and then nothing else happens.

I tried mythfilldatabase --manual with the same result.

When I run the frontend it won't connect to the backend either on localhost or 192.168.1.10
It's also impossible to exit the frontend, Escape doesn't work on the main screen.

I ran the backend again to see if something was misconfigured, but now it won't connect to the database any longer.

So I'm stuck there.

[edit]
I ran frontend one more time. It hung. I restarted X. Now the frontend will not run any more. I can see the process running but nothing comes up on the screen.

---

### Post by pickarooney on 2009-03-15
I ended up uninstalling mythtv completely and reinstalling from scratch. Not the best approach, but it worked and I was able to connect with the frontend on the local machine. On the laptop I have two problems.
1. most of the text in the interface is missing and I can't read much
2. I can't connect to the server backend

When I run the frontend from the CLI there's a warning that the blue theme dir is missing. I don't know why it looks for this folder or where to get the theme file. The server machine works fine without this folder.

Mo idea why the laptop won't connect to the backend.

---

### Post by issih on 2009-03-16
Best way to install the front end on the laptop is to install mythbuntu control centre and then tell it to only install a front end on that machine, that way you should guarantee getting a working front end installed.

As for configuration, you need to enable remote access the the mysql database of the server (if you start mythbuntu Control centre on the server it is one of the options within there to do so)

And I think there is a setting in the backend setup to enable remote connections too (I can't check right now as my myth server is down because the fan on its agp card went pop grrrrrrrr).

If both of those are ticked, you should be able to connect.

---

### Post by pickarooney on 2009-03-16
It's enabled all right, but no connection still.
What I don't get is how the backend specifies port 6504 or something whereas the frontend specifies port 3023 or something and both say not to change them unless there's a good reason.

Worse luck, the sound on my tuner card just completely stopped working yesterday. I can just about hear sound by plugging my headphones directly into the card, but it will no longer play via the sound card input (even in tvtime). Looks like I messed this one up big time. Ah well, nothing worth watching on anyhow :)

---

### Post by buntunub on 2009-03-16
Since the tuner is on a PC I will assume its a pci card. If not, then it must be usb. Post the output of lspci | grep *insert tv tuner card name* OR lsusb | grep *insert tv tuner card name*

---

### Post by pickarooney on 2009-03-16
02:00.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
02:00.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)


I think those are the only relevant lines from lspci

---

### Post by buntunub on 2009-03-17
Could be. You need to google for the how to for your particular card. You may find more info from dmesg. You want to look for a line like this - 

```
saa7134[0]: subsystem: 17de:7128, board: Kworld/Tevion V-Stream Xpert TV PVR7134 [card=59,insmod option]
```


That particular line has everything you would need to configure your stuff including subsystem, board, card and tuner options that you would need to insmod in.

---

### Post by pickarooney on 2009-03-17
Do you think the card's sound component just spontaneously uninstalled itself? I didn't have to do anything at all for it to work when I first installed the OS, it worked straight away.

---

### Post by pickarooney on 2009-03-28
Still no luck getting sound to work again. I completely removed Mythtv, removed and reinstalled the 2 modules for the tuner card, but nothing doing. :(

---

### Post by nihat on 2009-04-10
Hello , just one question for tvtime.xtml configuration - how can I use two buttons for one issue. For example I'd like to get fullscreen by ALT+ENTER , or change the canal by (mouse 3 + mouse 4/5).

---

