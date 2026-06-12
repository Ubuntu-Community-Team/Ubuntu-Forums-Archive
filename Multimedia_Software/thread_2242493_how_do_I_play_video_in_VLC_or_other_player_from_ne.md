---
title: "how do I play video in VLC or other player from network location"
date: 2014-09-02
forum: Multimedia Software
---

### Post by dave131 on 2014-09-02
I really don't anything about this.  I have Raspberry Pi's at a couple of TV's in the house running XBMC and each with their own disk drives and wireless adapter (could not run cable for hard-wiring the network).  I've been able to use XBMC on an Android tablet and point the input video to the Pi'x hard disk.  I would like to try this same type of thing using VLC in Ubuntu to play the same video coming from one of the wireless Pi's.  I did some research on the net and found something about gstreamer and followed what I could find, but have no real clue what the heck, if anything, I'm supposed to do with that.  I tried using the VLC file option for a network stream (?) but I don't what the syntax should be or if that would even work.

For example, a sample path might be something like:
pi_name:/ /media/my_disk/my_moviex/my_moviex.m4k

The Pi also requires a userid and password to logon for things like ssh and if I connect to it via the file manager.

---

### Post by dave131 on 2014-09-08
Bumping this up.  I can't find anything in the way of documentation that says you can open a network file.  I'm sure it must be possible, but I don't know how to do it.  Any help would be appreciated.

---

### Post by dave131 on 2014-09-10
Anyone?  I have used the "stream" option in the past but that was always to "play" something to a disk file.  I've tried the stream option and don't see how to use the network as input.  Under file I don't see anything to open a file on a network.

---

### Post by papibe on 2014-09-10
Hi dave131.

Try this:

Enable Universal Plug and Play on the XBMC on the pi:
```
System -> Settings -> Services -> UPnP
```
Then on VLC:
```
(Menu) View -> Playlist -> (windows' left list) Local Networks -> Universal Plug'n'Play
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by dave131 on 2014-09-10
I'll give that a try in just a second - I found I posted in my other thread about something else when I meant to post here, so I wanted to paste that in before I forgot:
               
Here's a real-life example from my PC:
I used ssh to go to one of the Pi's and worked my way down to one of the movies.  The path and movie are shown in:     Code:```
root:openelec@davepi:/var/media/sda1-usb-Innostor_Ext._HD/ALL-VIDEOS/Titanic(1997) # ls Titanic(1997).nfo  Titanic.mp4 davepi:/var/media/sda1-usb-Innostor_Ext._HD/ALL-VIDEOS/Titanic(1997) #
```[COLOR=#000000]
I know the Pi "openelec" requires the userid  of root and password of openelec when I ssh to it, so I tried to open a  network stream to it in VLC (see the attachment) [/COLOR]I get the following error message:```
     [COLOR=#ff0000]Your input can't be opened:[/COLOR]  [COLOR=#000000]VLC is unable to open the MRL 'root:openelec@davepi//var/media/sda1-usb-Innostor_Ext._HD/ALL-VIDEOS/Titanic(1997)/Titanic.mp4'. Check the log for details.[/COLOR]
``` 
Host davepi is known:```
me@melaptop ~ $ ping -c5 davepi PING davepi (10.0.0.110) 56(84) bytes of data.
   64 bytes from davepi (10.0.0.110): icmp_seq=1 ttl=64 time=1.67 ms64 bytes from davepi (10.0.0.110): icmp_seq=2 ttl=64 time=1.79 ms
   64 bytes from davepi (10.0.0.110): icmp_seq=3 ttl=64 time=1.47 ms 
   64 bytes from davepi (10.0.0.110): icmp_seq=4 ttl=64 time=1.64 ms 
   64 bytes from davepi (10.0.0.110): icmp_seq=5 ttl=64 time=1.98 ms 
--- davepi ping statistics --- 5 packets transmitted, 5 received, 0% packet loss, time 4007ms rtt min/avg/max/mdev = 1.475/1.716/1.988/0.176 ms
me@melaptop ~ $
```

On the Pi in question, the hosts file is created automatically by the installation of the OS - in this case OpenELEC:```
me@melaptop ~ $ sudo ssh 10.0.0.110
root@10.0.0.110's password: 
##############################################
# OpenELEC - The living room PC for everyone #
#...... visit http://www.openelec.tv ...... #
##############################################
OpenELEC (official) Version: 4.0.5
davepi:~ # cat /etc/hosts
# hosts.conf
# This configuration file allows you to manually map hostnames to
# IP addresses
# Format:  <ipaddress> <hostname1> <hostname2>
# Example: 192.168.0.3 openelec openelec.mynetwork
127.0.0.1    localhost davepi
::1    localhost ip6-localhost ip6-loopback davepi
davepi:~ #
``` 

Also, outside of a network connection on the Pi, do I need something else running there in order to open a stream?[INDENT][COLOR=#000000]
[/COLOR]                 
[/INDENT]
            
                                                                               [IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/paperclip.png[/IMG] Attached Thumbnails                      [[IMG]http://ubuntuforums.org/attachment.php?attachmentid=256334&stc=1&thumb=1&d=1410376024[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=256334&d=1410376024")

---

### Post by dave131 on 2014-09-10
> **papibe said:**
> Hi dave131.

Try this:

Enable Universal Plug and Play on the XBMC on the pi:
```
System -> Settings -> Services -> UPnP
```
Then on VLC:
```
(Menu) View -> Playlist -> (windows' left list) Local Networks -> Universal Plug'n'Play
```
Hope it helps. Let us know how it goes.
Regards.

See the attachment - I get that far but then can't figure out how to get to the actual path on the Pi where the videos are.  

Thanks!

---

### Post by papibe on 2014-09-11
Hi again.

I just tested this and it does not work on VLC right now. It freezes **. I believe it is a bug is being work out.

The XBMC UPnP sharing works, nevertheless. I used an android tablet with an UPnP client and it stream successfully from XBMC to the tablet.

You may just need to use another UPnP client. I tested the totem-plugins-extra for totem, but [does not work]("https://github.com/coherence-project/Coherence/issues/4") either.

So the problem is to find a UPnP player/client that works.

I'll try to get back to you if I got more info.

Regards.

EDIT: VLC's UPnP implementation is not the best. Apparently VLC first downloads all the library information before you can select anything. Depending on the size of the library that actually might take several minutes and longer (source [here]("http://askubuntu.com/questions/88754/upnp-dlna-client-player-recommendations")).

---

### Post by dave131 on 2014-09-11
Thanks again SO much!!  You can tell I don't know what the heck I'm doing with this, so I really appreciate the help!

---

### Post by dave131 on 2014-09-12
I can confirm that I get the same errors as mentioned in the link to github even after installing the upnp-coherent "stuff" and making the needed edits.  I'm not sure how to actually look for another player - my attempts at using ubuntu 14 upnp media player in a search string on the net are yielding results I really don't understand.

---

### Post by dave131 on 2014-09-13
I did some more reading all over the net and found that Totem (the default movie player) no longer supports upnp so the coherent "stuff" won't work.  I did find mention of djmount so I installed it via synaptic package manager.  I created a folder "mymedia" and did "djmount mymedia" and all of the available upnp devices show there.  This allowed me to go to VLC, select open file, and look in the mymedia folder.  I selected my Pi, then down through the OpenELEC XBMC folders and eventually got my movie.  This initial searching my folders took quite some time.  I was able to play a movie.  A few little glitches in the video/audio that I didn't experience when using XBMC on my tablet to view a movie from the Pi, both wirelessly.  Perhaps this solar flare is interfering in some way with my wireless (I am in Minnesota)?  At any rate, it's one way to make it work without having to use another program.  I'm going to try Totem in just a minute as I suspect it will work through there as well.

---

### Post by dave131 on 2014-09-13
Ok, works great with Totem (the default movie player - it may say something like "videos" in the menus).

So, now a dumb question I asked in another thread a while ago but for which this would be the perfect example:  is this what they mean by streaming video?  Where XBMC on the Pi, via upnp, is acting like a server and I can view it from another system - like this laptop?  If so, I think I understand now.  It also gives me hope in building a local file/media server.

---

### Post by priyagupta on 2014-09-18
[COLOR=#333333][FONT=UbuntuRegular]I have a home server (Ubuntu Server 12.04) and a laptop (Ubuntu Desktop 12.04) connected to the same local network (both wired to my router).[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]What I am trying to do is to access my server from my laptop (ssh) to play HD movies (located on the server) directly on my laptop (using VLC).[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]It works just fine with 720p format movies, but as soon as I try with 1080p movies, it starts to lag badly.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I have tried all the usual tricks:[/FONT][/COLOR]

[LIST]
[*]Increasing the caching value
[*]Setting the option "Skip the loop filter for H.264 decoding" to "All"
[*]Change the "Video output module" value
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]None of them worked for me. By increasing the caching value though, it actually seemed to work because it "buffers" for a while before starting the video, but after a while the movie stops and starts to "buffer" again...
[/FONT][/COLOR]
[GIS companies in India]("http://www.spageo.co.in/")
[GIS company in India]("http://www.spageo.co.in/")
[GIS companies in Ghaziabad]("http://www.spageo.co.in/")

---

### Post by Tadaen_Sylvermane on 2014-09-18
All these ways of using streaming software... Just set up the videos folder as a samba / nfs share, mount it then run them as if they were right there on your local computer. Easy, works every time. No fuss no muss.

---

### Post by dave131 on 2014-09-20
You may want to open your own thread on this since it is a little different from what I was doing.

> **priyagupta said:**
> [COLOR=#333333][FONT=UbuntuRegular]I have a home server (Ubuntu Server 12.04) and a laptop (Ubuntu Desktop 12.04) connected to the same local network (both wired to my router).[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]What I am trying to do is to access my server from my laptop (ssh) to play HD movies (located on the server) directly on my laptop (using VLC).[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]It works just fine with 720p format movies, but as soon as I try with 1080p movies, it starts to lag badly.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I have tried all the usual tricks:[/FONT][/COLOR]

[LIST]
[*]Increasing the caching value 
[*]Setting the option "Skip the loop filter for H.264 decoding" to "All" 
[*]Change the "Video output module" value 
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]None of them worked for me. By increasing the caching value though, it actually seemed to work because it "buffers" for a while before starting the video, but after a while the movie stops and starts to "buffer" again...
[/FONT][/COLOR]
[GIS companies in India]("http://www.spageo.co.in/")
[GIS company in India]("http://www.spageo.co.in/")
[GIS companies in Ghaziabad]("http://www.spageo.co.in/")

---

### Post by dave131 on 2014-09-20
I tried this before going on to what I've mentioned in this thread.  For whatever reason, Samba sharing seems a little flaky on my Pi in that sometimes the shares just disappear and won't come back until I power-reset the Pi.

> **Tadaen_Sylvermane said:**
> All these ways of using streaming software... Just set up the videos folder as a samba / nfs share, mount it then run them as if they were right there on your local computer. Easy, works every time. No fuss no muss.

---

### Post by dave131 on 2014-09-21
Hey - just thought of what was probably causing my problems on the Pi and Samba!  I have another thread, marked solved now, about how the Pi kept disappearing from the wireless.  Thanks to another very helpful user it turns out it was a timing issue because I had the wireless adapter plugged in to the USB hub.  They suggested moving it directly to the Pi, which I did do, and now it has stayed up for well over a week.  So, Tadean_Sylvermane - I have you to thank!  You got the jobs in the background of my mind working and made the connection - will be trying this later but I'd bet it will work now!

---

### Post by dave131 on 2014-09-22
Okay, I can use Samba, but I don't seem to be able to find them in opening a file.  Instead, I have to go to the file manager and connect to the Pi first, then I can open the file(s).  Is there a way I can somehow "mount" the share to a specific location at startup or login so I don't have to go to the file manager first?

---

### Post by dave131 on 2014-09-27
bump - I "ain't goin' away...."

---

### Post by Mark_du_Preez on 2014-10-20
> **dave131 said:**
> I really don't anything about this.  I have Raspberry Pi's at a couple of TV's in the house running XBMC and each with their own disk drives and wireless adapter (could not run cable for hard-wiring the network).  I've been able to use XBMC on an Android tablet and point the input video to the Pi'x hard disk.  I would like to try this same type of thing using VLC in Ubuntu to play the same video coming from one of the wireless Pi's.  I did some research on the net and found something about gstreamer and followed what I could find, but have no real clue what the heck, if anything, I'm supposed to do with that.  I tried using the VLC file option for a network stream (?) but I don't what the syntax should be or if that would even work.

For example, a sample path might be something like:
pi_name:/ /media/my_disk/my_moviex/my_moviex.m4k

The Pi also requires a userid and password to logon for things like ssh and if I connect to it via the file manager.

Hi Dave

Did you sort this out?

I'm a newbie and I've just removed OpenELEC and installed Raspbian so I can't give much detail, but I can tell you that when I had OpenELEC, I had no problem watching Pi videos at my Ubuntu PC over my wireless network. All I had to do was activate something called Samba in the OpenELEC settings and then click on "File", "Connect to server..." on my Ubuntu PC's file manager.

Sorry if that was no help.

Cheers.

---

### Post by Mark_du_Preez on 2014-10-20
Oops, sorry, I didn't see there was another page to this thread.

---

### Post by SeijiSensei on 2014-10-20
I've had mixed success streaming from Samba.  Use NFS if the client is also running Linux or some other *nix derivative.  I stream from my server to my TV using NFS and a wifi connection without any problems.

---

