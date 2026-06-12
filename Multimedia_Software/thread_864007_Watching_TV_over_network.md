---
title: "Watching TV over network"
date: 2008-07-19
forum: Multimedia Software
---

### Post by Ck.asdf on 2008-07-19
Hello, I was wondering if it's possible to watch television over the network - to have a tv tuner in my desktop server, and watch tv using a laptop on the same network.

I currently use my main desktop (which I may sell to fund the laptop) to watch tv.
/dev/video0 is the device, I just type "totem /dev/video0" to run the video app, then use ivtv-utils to change the channel.

I know that mythTV has the capability to do what I'm asking, but I couldn't even get it completely set up locally, and the simple solution here works fine for me.

I tried SSHing from the server to the desktop and type the "totem /dev/video0" but it said "cannot open display."  I do have gnome installed on the server (Ubuntu Server Edition), but I'm guessing it needs something special to show video from another computer.


/dev/video0 is the video through the coaxial cable ... my tv tuner has composite input; how do I get access to it?

Another question: what's the minimum hardware requirements for a tv tuner:
A) watching, and B) recording?
The server I have is pretty old & limited in hardware.  The computer originally had Windows 98 on it, and has 256MB of memory and Intel Pentium 3 processor.

---

### Post by Ck.asdf on 2008-07-19
One thought I had of sharing video over the network would be to use:
"totem /dev/video0 > tv.mpg" and then share the video ... but I'm not sure of how to do that.

---

### Post by jelofson on 2008-09-04
I would use VLC on your box with the tuner to set up a pvr stream. Then open VLC on your remote machine and open the stream. I am doing that over http right now.

I find the easiest way to set up the stream is to use the wizard. File->Wizard. Try it out and see how it goes.

---

### Post by Ck.asdf on 2008-09-04
> **jelofson said:**
> I would use VLC on your box with the tuner to set up a pvr stream.

I meant to mention that I had actually got this working, but I forgot ... so with the tuner in the server, being served by VLC, it will work.  But what about recording?  how do I do that?  And, how do I get access to the composite audio/video input?  I can only get it to show the cable input.

---

### Post by Erlander on 2008-09-05
kaffeine will do this for you and is easy to set up.

Its in the repositories too.

Rob

---

### Post by Ck.asdf on 2008-09-05
could you please be a little more descriptive? Kaffeine will do which task, and how?

---

### Post by Erlander on 2008-09-05
If you open Kaffeine and go to Settings/Configure KaffeinePlayer/dvb Client and enable the client you can then broadcast over your network by going to File/Networkbroadcasting/Send Broadcast Stream.

Then on the pc you want to receive the broadcast on go to File/Network Broadcasting to enable it to receive the stream broadcast onto your network by the pc with the tuner card.

On both pc's I leave the port as the default but enter the correct network addresses.

I haven't done it for a while but had no trouble getting it going.

Rob

---

### Post by xdac on 2008-10-02
I have had real problems getting Kaffeine to stream DVB-T over the local network. Everywhere I look I get the comments its really easy to setup therefore I must be really stupid. Please let me know what I am doing wrong. A simple keystroke howto would be nice!

How I have set it up:

The host computer with DVB card running Kaffeine (0.8.7) works perfectly. I upgraded as I had TV channel scanning, CODEC install infinite loop which was all reported as a bug which has been fixed.

On the host (Ubuntu 8.04 Hardy Heron) I have selected:

DVB->Configure DVB->Broadcasting and entered

192.168.1.255 as my broadcast address as taken from ifconfig
Broadcast port as 8080
Info port as 8081

Seems happy with this (if you select PC IP address get info port error)

On the client a laptop running same OS and version of Kaffeine as host

I have setup DVB CLient

Settings -> Configure Kaffeine Player-> DVB Client

Clicked "enable DVB Client"

Broadcast address 192.168.1.255 etc - details as above.

All closes with no errors

I then click on DVB client on splash screen.

I get a black video screen

Select File-> Network Broadcasting-> Receive  Broadcast stream

I get a box asking for broadcast address and port.

If I enter the broadcast address 192.168.1.255, port 8080 I get a blue screen which says "Opening" and thats it.

If I enter IP address of the host, port 8080 I get a black screen (sometimes blue) and the correct audio but no picture.

Firewalls are off, router I have looked at. I can connect the computers using tsclient/ vnc for remote desktop hence computers are talking. The refresh rate using VNC is too slow for TV.


Any ideas ?????

---

### Post by xc3RnbFO8P on 2008-10-02
> Select File-> Network Broadcasting-> Receive Broadcast stream

I get a box asking for broadcast address and port.

Find the IP number of the broadcasting computer (mine is 192.168.0.4).
Right click on the network connection icon, choose connection information.
Put your IP number in the box **Sender address**
Remember same Port on both computer, (8080)

---

### Post by Erlander on 2008-10-02
I just did it again as in post #7 above. I'm don't watch much tv lately so I haven't done it recently.

I had trouble getting it to work until I realised that I also had to click on the "Player Window" icon on the left of the screen in the client pc.  That got it going again.

Rob

---

### Post by xdac on 2008-10-03
Thanks for the responses - I have now managed to fix the problem. 

Kaffeine was displaying a blue screen as it had problems with the X configuration. I had to change my /etc/xorg.conf - DefaultDepth from 24 to 32 and now it works! An error message would have been nice but c'est la vie.

Refer:
[http://kubuntuforums.net/forums/index.php?topic=3082585.15](http://kubuntuforums.net/forums/index.php?topic=3082585.15)

---

