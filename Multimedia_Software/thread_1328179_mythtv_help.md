---
title: "mythtv help"
date: 2009-11-16
forum: Multimedia Software
---

### Post by proevofanatik on 2009-11-16
i use kaffeine on my kubuntu 9.10. but i want to give mythtv a go. i tried setting it up but i dont have a clue what im doing to set it up. can anyone please give me some guidance?

---

### Post by mal on 2009-11-16
proevofanatik,

I suggest you have a look at [http://www.mythbuntu.org/]("http://www.mythbuntu.org/") as a starting point.  There is an installation manual that you can download.  It is a bit outdated, but should still be useful for reference.

The Ubuntu wiki is also useful.  Have a look at [https://help.ubuntu.com/community/MythTV]("https://help.ubuntu.com/community/MythTV").

Note that installing and configuring MythTV can be a bit complicated, so you may need to come back here for more specific advice.

Regards and good luck.

Mal

---

### Post by proevofanatik on 2009-11-17
before i attempt it , is it possible to stream my dvb channels to my dads house? also what kind of quality would i expect? and also cani use a soft cam on mythtv?

---

### Post by mal on 2009-11-17
From my experience, you can stream the video from the MythTV backend to a MythTV frontend over any good network connection, including a wireless network, although I would suggest a 100Mb LAN for reliable results.  If your dad's house has a suitable high bandwidth connection to your MythTV backend, it should work fine.

I did have some problems with a frontend machine that was connected by a wireless link, but I think it was due to the cheap wireless card I was using.

The quality is excellent, pretty much as good as watching standard definition digital TV an a dedicated flat screen television.  MythTV will also handle high definition, although this would depend on the speed of the machines you are using.

I can't really answer your question about the soft cam.

Regards,

Mal

---

### Post by proevofanatik on 2009-11-17
so can i only stream from mythtv to mythtv? cant i stream from my myth tv to my dads windows media player?

also what is the backend and frontend? what do they mean?

---

### Post by NotKeith on 2009-11-17
The backend is the machine that will be doing most of the work, the one with the video card that does all the en/decoding of the tv signal.  You can set up a frontend to view the programs on the backend.


As far as streaming to windows media player, I don't really know, but this thread seems to indicate that it can be done using vlc media player, [http://www.gossamer-threads.com/lists/mythtv/users/174522.]("http://www.gossamer-threads.com/lists/mythtv/users/174522")

---

### Post by proevofanatik on 2009-11-17
so does the backend and front end have to be installed on the one machine? the backend just decodes all the channels, but the front end allows you to watch it on the same machine?

if i stream it i take it the client machine only needs the frontend? while the server machine must have backend and frontend?

---

### Post by mal on 2009-11-17
The backend and frontend can run on the same machine or on separate machines as required.  The backend needs to be on the machine with the dvb tuner(s) and it records scheduled TV programs.  The frontend connects to the backend and displays the recorded programs live TV.  The server machine does not need to have a frontend installed.

It is also possible to have multiple backends and multiple frontends if you really want to get fancy.

I suggest you keep it simple to start with have a go at installing a complete system on one machine.  Note that you can install a full system using the Mythbuntu install CD, although this does not install a full desktop, or you can install MythTV on an existing Ubuntu (or Kubuntu) system.

Hope this helps.

Mal

---

### Post by proevofanatik on 2009-11-18
> **mal said:**
> 

It is also possible to have multiple backends and multiple frontends if you really want to get fancy.





when you say multiple backends and frontends, do you mean i can watch  3 different tv channels at the same time on one computer? and also would i beable to stream all 3 channels at the same time?

---

### Post by proevofanatik on 2009-11-18
is there a kde version of mythbuntu available? i dont really like gnome desktop

---

### Post by mal on 2009-11-19
proevofanatik,

I will try to answer some of your questions:

- MythTV does not depend on any particular linux desktop, it can work with Gnome or KDE or various other desktops.  In fact Mythbuntu comes with an XFCE desktop.

- MythTV displays full screen and is designed to be operated from the lounge with a remote control.  (Although it can also be controlled from a standard keyboard.)

- There are some MythTV frontend programs available for Windows.  I don't have any experience with these, but you should be able to track them down fairly quickly with Google.

- It is also possible to stream MythTV recordings to another machine using a web browser and suitable video applications like Totem or VLC.

- A backend machine can have multiple TV tuners and can simultaneously record or stream live TV from multiple tuners.  I guess the limitation would be the processing power of the machines and the bandwidth of the network connection between backends and frontends.  It is not really practical to view multiple programs on one MythTV frontend, except for the Picture-In-Picture (PIP) capability.

- A server can have a MythTV backend without necessarily having a frontend installed.

- When I mentioned multiple backends and frontends, I was really talking about separate computers.  Each backend can have more than one TV tuner.  

- It is also possible to setup a "diskless client" that boots from the network and loads the frontend system over the network from a server, eliminating the need for a noisy hard disk on the client machine in your viewing room.  On my system, I can take just about any computer and set it to boot from the network and have it up and running as a MythTV frontend in no time, without interfering with the computer's own hard disk or operating system.

Regards,

Mal

---

