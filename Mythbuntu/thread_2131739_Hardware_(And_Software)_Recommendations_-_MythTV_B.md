---
title: "Hardware (And Software) Recommendations - MythTV Backend &amp; Frontend"
date: 2013-04-02
forum: Mythbuntu
---

### Post by Heide264 on 2013-04-02
Good Evening,

I recently picked up an HDHomeRun Prime along with a cable card for my FiOS subscription. I'd like to do up a nice HTPC, and have been reading around a decent amount. I've found it pretty difficult to piece together some of the information out there regarding the various options. 

Currently, I have windows media center set up and streaming over to my xbox360, but it is a bit slow and I would kind of like to use my laptop again :p. I'm not too happy with the WMC extender interface, either. I am required to open the laptop and such to simply record a show.

I guess the easiest place to start would be my requested features...
Required:
-Girlfriend friendly
-Remote friendly (preferably with a cheap-ish remote)
-Able to watch live TV with pause/rewind/etc
-Able to easily record TV series or movies from the TV tuner
-Fast, responsive, and attractive menus and TV guide
-Backend must be able to "support" at least two frontends at this time
-CableCARD compatible (I don't need the encrypted channels as of now such as HBO/Cinemax - thanks FiOS)
-Under $350

Would be nice:
-Ability to rip blue rays to a high quality format (.mkv I guess)
-Backend and frontend in the same machine
-Ability to hook up a usb controller and play a few emulators
-Under $200

I was looking to use MythTV as my back end and XBMC as a front end. Open to suggestions.

The only curve ball is that I currently have an older Dell D820 sitting around. It's a 2.0Ghz core duo (32 bit apparently... annoyingly) with the Nvidia quattro 110 or 120M in it. I don't believe the video card supports the VDPAU or whatever it is to allow the hardware acceleration using the open source drivers. I currently threw MythBuntu on it to play around with it, but it does not have an HDMI output, and I have not tested its HDTV recording abilities yet. If that would work as a back end, I wouldn't mind buying a dedicated front end.

Anybody have any suggestions? I was thinking of doing a simple i3 build.

---

### Post by uteck on 2013-04-05
I am using MythTV on the backend and XBMC and the normal Mythfrontend.  

XMBC looks nicer by default, but the Mythfrontend theme can be changed to look better.
XBMC support for MythTV has gotten much better in the 12.1 build, but it seems to have to have a problem refreshing the recorded program list.  I have to restart it to refresh.
Scheduling recordings in XMBC is a pain, I either use mythweb, or use mythfrontend on the other TV. 
Auto commercial skip does not work in XMBC, but fast-forward works fine.
XBMC does have a better way of listing recorded programs by grouping shows in a folder and then placing that at the top, so catching up is easier.
XBMC also has a better home screen that can show weather and upcoming recordings.

Overall, I would recommend not using XBMC as a frontend to MythTV at this time.  The old MythTV add-on worked fine in version 11, but it has not been updated to work in 12.

Bluray playback is not going to happen.  I use MakeMKV to rip my disks to a huge .mkv file and store it on my server and play them back that way.  Don't bother using handbreak to re-compress smaller, just get a bigger storage drive. :-)

Get a Nvidia 8400 or better fanless video card and put that in the Dell, and make it a combined back/frontend.  You can connect other frontends to it latter by using the Mythbuntu Control Center.  The backend does not need a lot of power, and mine is about 6 years old now and works fine, AMD 2.2 GHz and 1GB of RAM running the 32-bit build of Mythbuntu.  It used to be a combined front and backend unit, but I moved it to basement along with the cable controller and just use frontend units on the TVs.

---

### Post by Heide264 on 2013-04-08
> **uteck said:**
> Overall, I would recommend not using XBMC as a frontend to MythTV at this time.  The old MythTV add-on worked fine in version 11, but it has not been updated to work in 12.

Okay, that works for me. I can always try switching to an XBMC front down the road if I feel like it or things change.

> Bluray playback is not going to happen.  I use MakeMKV to rip my disks to a huge .mkv file and store it on my server and play them back that way.  Don't bother using handbreak to re-compress smaller, just get a bigger storage drive. :-)

That works for me. I also have a dedicated nice blu-ray player. I will probably just get off my rear end and put the disk in the drive when I want to watch it. With the various issues involved (especially in the audio department it seems)... it may be easier.

I will keep that in mind though.

> Get a Nvidia 8400 or better fanless video card and put that in the Dell, and make it a combined back/frontend.  You can connect other frontends to it latter by using the Mythbuntu Control Center.  The backend does not need a lot of power, and mine is about 6 years old now and works fine, AMD 2.2 GHz and 1GB of RAM running the 32-bit build of Mythbuntu.  It used to be a combined front and backend unit, but I moved it to basement along with the cable controller and just use frontend units on the TVs.

I'm not quite sure what video cards I can throw in the Dell. I've replaced the keyboard in this laptop as well as some of the RAM. Any idea where I can find the limitations of the Dell mobo in that laptop? I am hoping that as long as it's Nvidia's "mobile series" it should physically fit.

Thanks for the help. I'm fairly tech friendly, but been out of the computer game for a while and haven't had as much time to read up on it as I have wanted to.

EDIT: It looks like the D820 has it's GPU soldered straight onto the Mobo and isn't really exchangeable with any of the newer ones. I don't believe that either the 110 or 120M (I forget which one it has) supports the VDPAU hardware encoding, so it looks like I may be picking up another machine, anyhow.

---

