---
title: "Networked streaming sound and video"
date: 2008-03-13
forum: Multimedia &amp; Video
---

### Post by bigmell2 on 2008-03-13
I have a kind of weird request and I am not sure where to start.  I have an NFS server with about 1 terabyte of sound and video.  Throught the house I have 5 other ubuntu computers that hook up to this server to listen to music and play video via NFS and samba.  

What I would like to do is have the NFS server provide some kind of streaming media server that will allow me to have all the computers in all the different rooms in the house sync up to play the same music or the same movie.  

I.E.  I will start a movie on the server, and all the other ubuntu computers throughout the house can connect to that same stream and begin playing the movie (or music) in sync with all the other computers already hooked up to the stream.

Does anybody have any idea of how to accomplish what I am talking about?  I am not adverse to writing something, I am looking for some starting points.  If something already exists out there that I can use, all the better  :)

---

### Post by sradhakrishna on 2008-03-14
Let me give it a shot.

I understand you have all computers set up on a network and all of 'em talk to each other. 

One crude way to achieve what you are trying to do is to use VLC from [www.videolan.org](www.videolan.org). 

Launch VLC
Open File - launches a Open... dialog
Browse to select a file
Under advanced options, Select Stream/ Save, hit settings
Under Outputs, select UDP, select a multicast address - aka 239.1.1.10 port 3456
say ok.

This will start the video to be streamed out on the network on the said multicast address.

On the other machines, you could 
launch VLC, 
Open Network Stream, launches Open... dialog with Network tab, select UDP/RTP Multicast,
ENter 239.1.1.10, port 3456
and hit ok.

Let me know if you could get this working.

Btw, if the end devices are TVs, you may want to check out mythbuntu ([www.mythbuntu.org](www.mythbuntu.org)).

Regards,
Radha.

---

### Post by bigmell2 on 2008-03-14
Thanks for the response man!

However I tried that with no success.  I am trying to stream a dave chappelle show, I followed all the instructions you gave.

I am trying to stream to 192.168.7.8 first.  Now the show didnt play on 7.7 until I checked "play locally."  Vlc comes up and plays the movie.  I launched vlc on 7.8 and follow your instructions and I get errors and the stream doesnt play, I will paste the output from the message window below...

Basically the VLC gui just sits there blank on the client.  The server is playing but the client just sits there.  Could you explain the multicast address maybe?  I tried it with the server and client ip as the multicast address but that didnt work either.  Here is the error output.

main warning: cannot create a stream_t from access

main debug: removing module "access_udp"

main debug: thread 2980043664 joined (input/input.c:412)

main debug: creating new input thread

main debug: waiting for thread completion

main debug: thread 2980043664 (input) created at priority 0 (input/input.c:265)

main debug: stream=`duplicate'

main debug: looking for sout stream module: 1 candidate

stream_out_duplicate debug: creating 'duplicate'

stream_out_duplicate debug:  * adding `display'

main debug: stream=`display'

main debug: looking for sout stream module: 1 candidate

main debug: using sout stream module "stream_out_display"

main debug: using sout stream module "stream_out_duplicate"

main debug: `udp://@239.1.1.10:3456' gives access `udp' demux `' path `@239.1.1.10:3456'

main debug: creating demux: access='udp' demux='' path='@239.1.1.10:3456'

main debug: looking for access_demux module: 0 candidates

main warning: no access_demux module matched "udp"

main debug: creating access 'udp' path='@239.1.1.10:3456'

main debug: looking for access2 module: 6 candidates

access_udp debug: opening server=:0 local=239.1.1.10:3456

main debug: net: connecting to '[]:0@[239.1.1.10]:3456'

main debug: looking for network module: 1 candidate

ipv6 debug: 239.1.1.10: Address family for hostname not supported

main debug: using network module "ipv6"

main debug: removing module "ipv6"

main debug: looking for network module: 1 candidate

ipv4 debug: resolving 239.1.1.10:3456...

ipv4 debug: resolving :0...

ipv4 debug: IP_ADD_MEMBERSHIP multicast request

main debug: using network module "ipv4"

main debug: removing module "ipv4"

main debug: using access2 module "access_udp"

main debug: pre buffering

---

