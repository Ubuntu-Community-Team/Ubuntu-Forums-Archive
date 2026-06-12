---
title: "UPNP module for PulseAudio"
date: 2010-05-09
forum: Multimedia Software
---

### Post by quizzical on 2010-05-09
Hey,

Just wondering if theres a module for puleaudio which would output the sound from pulseaudio to a upnp renderer. I want to stream from my ubuntu laptop to my windows desktop, if there is no module I guess I can just install pulseaudio on windows, does anyone have any experience with how effective that is?

Cheers
Alex

---

### Post by perrti-y02 on 2010-05-14
The package called 'rygel' lets you tick the box in Pulse Device Manager that mentions uPnP. More than this I don't know. Have a look around on Google.

---

### Post by hugovdm on 2010-08-22
Has anyone had any success with this? I would also like to play music from my laptop, controlled by my laptop, but playing via a upnp renderer on my network.

Thanks!
Hugo

---

### Post by dnns on 2010-12-28
Bumping - looking for a similar solution. Need one DLNA/UPnP channel that outputs whatever the computer is playing to a DLNA/UPnP capable media server.

Rygel seems promising in the options it provides (adds a PulseAudio output channel called DLNA/UPnP streaming) but is lacking in actual implementation.

Up to now I'm only able to access the media stored on my PC which makes Rygel on par with Mediatomb in my eyes.

Anyone had luck streaming whatever the PC is playing to a media receiver via UPnP?

(Using WDTV live player, Ubuntu 10.10)

---

### Post by produnis on 2011-01-12
Here comes my short description of what I did here:

1) Install Icecast2 - it will stream the music to your (local) net
2) Install Ices2 and run it with its Pulse-XMLfile. This will stream your current Pulse-output to Icecast2. So, any machine is able to visit your local icecast2-Website and grep the current pulse-output from there
3) Install Mediatomb. This is an upnp-server
3.1) Go to the Mediatomb-Webinterface, click the "+" at the very right, chose "external link" and enter the streaming-adress of your icecast2-stream. Your pulse-output is now available via mediatomb. 

However, some mediaplayers (e.g. the Asus O!Play) are not able to handle these streams... 
...but any PC which connects to either the icecast2-webpage or the mediatomb-webpage is able to grep and play the stream!

---

### Post by produnis on 2011-01-12
Here comes my short description of what I did here:

1) Install Icecast2 - it will stream the music to your (local) net
2) Install Ices2 and run it with its Pulse-XMLfile. This will stream your current Pulse-output to Icecast2. So, any machine is able to visit your local icecast2-Website and grep the current pulse-output from there
3) Install Mediatomb. This is an upnp-server
3.1) Go to the Mediatomb-Webinterface, click the "+" at the very right, chose "external link" and enter the streaming-adress of your icecast2-stream. Your pulse-output is now available via mediatomb. 

However, some mediaplayers (e.g. the Asus O!Play) are not able to handle these streams... 
...but any PC which connects to either the icecast2-webpage or the mediatomb-webpage is able to grep and play the stream!

---

### Post by produnis on 2011-01-12
Here comes my short description of what I did here:

1) Install Icecast2 - it will stream the music to your (local) net
2) Install Ices2 and run it with its Pulse-XMLfile. This will stream your current Pulse-output to Icecast2. So, any machine is able to visit your local icecast2-Website and grep the current pulse-output from there
3) Install Mediatomb. This is an upnp-server
3.1) Go to the Mediatomb-Webinterface, click the "+" at the very right, chose "external link" and enter the streaming-adress of your icecast2-stream. Your pulse-output is now available via mediatomb. 

However, some mediaplayers (e.g. the Asus O!Play) are not able to handle these streams... 
...but any PC which connects to either the icecast2-webpage or the mediatomb-webpage is able to grep and play the stream!

---

### Post by produnis on 2011-01-12
Here comes my short description of what I did here:

1) Install Icecast2 - it will stream the music to your (local) net
2) Install Ices2 and run it with its Pulse-XMLfile. This will stream your current Pulse-output to Icecast2. So, any machine is able to visit your local icecast2-Website and grep the current pulse-output from there
3) Install Mediatomb. This is an upnp-server
3.1) Go to the Mediatomb-Webinterface, click the "+" at the very right, chose "external link" and enter the streaming-adress of your icecast2-stream. Your pulse-output is now available via mediatomb. 

However, some mediaplayers (e.g. the Asus O!Play) are not able to handle these streams... 
...but any PC which connects to either the icecast2-webpage or the mediatomb-webpage is able to grep and play the stream!

---

### Post by produnis on 2011-01-12
Here comes my short description of what I did here:

1) Install Icecast2 - it will stream the music to your (local) net
2) Install Ices2 and run it with its Pulse-XMLfile. This will stream your current Pulse-output to Icecast2. So, any machine is able to visit your local icecast2-Website and grep the current pulse-output from there
3) Install Mediatomb. This is an upnp-server
3.1) Go to the Mediatomb-Webinterface, click the "+" at the very right, chose "external link" and enter the streaming-adress of your icecast2-stream. Your pulse-output is now available via mediatomb. 

However, some mediaplayers (e.g. the Asus O!Play) are not able to handle these streams... 
...but any PC which connects to either the icecast2-webpage or the mediatomb-webpage is able to grep and play the stream!

---

### Post by produnis on 2011-01-14
I finally figured out how my O!Play could play Icecast-Streams. I needed to install the following package and add the stream-adress to my favorite radiostations:
[click here]("http://vip.asus.com/forum/view.aspx?SLanguage=en-us&id=20100630024630343&board_id=19&model=O!Play%20HDP-R1&page=1&count=270")

---

### Post by dnns on 2011-01-16
> **produnis said:**
> I finally figured out how my O!Play could play Icecast-Streams. I needed to install the following package and add the stream-adress to my favorite radiostations:
[click here]("http://vip.asus.com/forum/view.aspx?SLanguage=en-us&id=20100630024630343&board_id=19&model=O!Play%20HDP-R1&page=1&count=270")

Thanks a lot produnis, these seem like some helpful tips - I'll give this a try and report in if it works for me too.

---

### Post by belrik on 2011-03-30
Any news on this? PulseAudio/uPNP integration would be amazing and would open some great possibilities for things such as MPD (Music Player Daemon) by enabling it to use existing consumer devices as endpoints.

---

### Post by bradleee on 2011-07-04
Pulseaudio publishes itself through the DBUS session bus, which the rygel UPnP server can pick up. However, they've had a bit of a DBUS interface version mismatch in 10.04 and 10.10 (not sure about 11.04). Note this is the right thing to do; it's better for PA to focus on audio and for PA and rygel to agree on DBUS interoperability; it's just temporarily out of sync.


[See workaround here]("http://ubuntuforums.org/showpost.php?p=11010331&postcount=4").

Native PA->DBUS->Rygel support broke when rygel went to dbus mediaserver2 before PA left dbus mediaserver1. The above post is a workaround that works for me; hopefully more recent versions of PA support mediaserver2 natively and the PA->DBUS->Rygel chain works again (rather than my PA->gstreamer->wavpack->rygel chain). For the time being though I have this working with my PS3 (which is a UPnP DLNA device and can consume most rygel output).

---

