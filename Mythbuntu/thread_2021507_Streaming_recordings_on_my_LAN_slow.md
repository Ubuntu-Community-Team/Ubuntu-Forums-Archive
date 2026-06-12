---
title: "Streaming recordings on my LAN slow?"
date: 2012-07-09
forum: Mythbuntu
---

### Post by JamerTheProgrammer on 2012-07-09
Hey!
Im using the following setup:
Mythbuntu 10.10
3GB DDR2 Ram
GTS 250 1Gb
250GB 7200rpm HDD

Everything works brilliantly except streaming over my LAN. If I go to Mythweb on another computer and download a ASX stream and use it with VLC it plays fine for 1 second then has to buffer. I have noticed while the video is buffering the setup using MythTV laggs like hell.
Whats going on here? 
Our router can handle up to 54MBps and I can receive full broadband speeds just fine.

---

### Post by tgm4883 on 2012-07-09
> **JamerTheProgrammer said:**
> Hey!
Im using the following setup:
Mythbuntu 10.10
3GB DDR2 Ram
GTS 250 1Gb
250GB 7200rpm HDD

Everything works brilliantly except streaming over my LAN. If I go to Mythweb on another computer and download a ASX stream and use it with VLC it plays fine for 1 second then has to buffer. I have noticed while the video is buffering the setup using MythTV laggs like hell.
Whats going on here? 
Our router can handle up to 54MBps and I can receive full broadband speeds just fine.

Are you trying to play back HD or SD recordings? If you plug into wired ethernet, does it work?

Also, your router most likely cannot handle 54MBps (MegaBytes per second), but instead 54Mbps (MegaBits per second). This is only around 6.4 Megabytes per second and isn't enough for HD content.

---

### Post by JamerTheProgrammer on 2012-07-09
> **tgm4883 said:**
> Are you trying to play back HD or SD recordings? If you plug into wired ethernet, does it work?

Also, your router most likely cannot handle 54MBps (MegaBytes per second), but instead 54Mbps (MegaBits per second). This is only around 6.4 Megabytes per second and isn't enough for HD content.

Its all wireless. Either way it doesn't make a difference. The content is SD.
Thanks

---

### Post by tgm4883 on 2012-07-09
> **JamerTheProgrammer said:**
> Its all wireless. Either way it doesn't make a difference. The content is SD.
Thanks

So your backend is wired into the router and your computer is wired into the router and it's still slow. Odd. What does the CPU load look like when you are trying to stream it from mythweb?

Are you getting any error messages in the apache log or mythtv logs?

---

### Post by JamerTheProgrammer on 2012-07-10
> **tgm4883 said:**
> So your backend is wired into the router and your computer is wired into the router and it's still slow. Odd. What does the CPU load look like when you are trying to stream it from mythweb?

Are you getting any error messages in the apache log or mythtv logs?

Nope. No errors what so ever.
I have just looked into it more and I have realised the system doesnt lag at all but rather it makes any kind of keyboard or mouse input unresponsive/laggy.
I have no idea whats going on at all. :S  Its not completely necessary  to have this feature, but I would  love to be able to stream my recordings to my Xbox Media Centre in another room.
Any more ideas?
Thanks :)

---

### Post by JamerTheProgrammer on 2012-07-13
Bump.
Anyone? Please help.

---

### Post by ijumpship on 2012-07-13
found that problem with the stock routers such as Cisco/Linksys,Tenda,dlink and Netgear.These I have tested.

This is because of the way they manage traffic so if your significant other is watching nexflix,somebody using the web and so on and so on.you will definitely see this. 

I think if you deploy your own Homebrew router such as Pfsense,IPcop,Firestarter,you might see some improvement.just tweak the Quality of Service.

I have a HDhomerun,on a P4 3.2 with 2g of Ram.works fine for me.I cannot however play the asx stream on 64bit windows home premium WMP without glitches and buffer problem.

Any way look at the codec information in VLC it will tell you about packets drops and enable logging on your router and have a look at it.

Most router carries logging  in the system maintenance but its disable because it increase trafiic.Temporarily enable it then read the reports.

I wish you success.

---

### Post by JamerTheProgrammer on 2012-07-13
> **ijumpship said:**
> found that problem with the stock routers such as Cisco/Linksys,Tenda,dlink and Netgear.These I have tested.

This is because of the way they manage traffic so if your significant other is watching nexflix,somebody using the web and so on and so on.you will definitely see this. 

I think if you deploy your own Homebrew router such as Pfsense,IPcop,Firestarter,you might see some improvement.just tweak the Quality of Service.

I have a HDhomerun,on a P4 3.2 with 2g of Ram.works fine for me.I cannot however play the asx stream on 64bit windows home premium WMP without glitches and buffer problem.

Any way look at the codec information in VLC it will tell you about packets drops and enable logging on your router and have a look at it.

Most router carries logging  in the system maintenance but its disable because it increase trafiic.Temporarily enable it then read the reports.

I wish you success.
Thanks for replying!
Im using a Belkin54G and the streaming was done when no one was using any computers on the network.
This is what I am getting from VLC:

main debug: Stream buffering done (2591 ms in 9514 ms)
main debug: Decoder buffering done in 0 ms
main warning: PTS is out of range (24717), dropping buffer
main warning: PTS is out of range (766), dropping buffer
main warning: PTS is out of range (-23207), dropping buffer
main warning: picture is too late to be displayed (missing 80 ms)
main warning: computed PTS is out of range (28781), clearing out
main warning: PTS is out of range (28781), dropping buffer
main warning: computed PTS is out of range (28910), clearing out
main warning: PTS is out of range (4910), dropping buffer
main warning: computed PTS is out of range (28950), clearing out
main warning: PTS is out of range (-19050), dropping buffer
main warning: computed PTS is out of range (28987), clearing out
main error: ES_OUT_SET_(GROUP_)PCR  is called too late (jitter of 5797 ms ignored)
main error: ES_OUT_RESET_PCR called

main debug: End of audio preroll

ts warning: discontinuity received 0xa instead of 0x9 (pid=2826)

main debug: End of video preroll
main debug: Received first picture

main debug: Stream buffering done (2573 ms in 10679 ms)
main debug: Decoder buffering done in 0 ms
main warning: PTS is out of range (-37357), dropping buffer
main warning: audio output out of sync, adjusting dates (-40372 us)
main warning: not synchronized (-40372 us), resampling
main warning: buffer too early (-40372), down-sampling
main error: ES_OUT_SET_(GROUP_)PCR  is called too late (jitter of 6983 ms ignored)
main error: ES_OUT_RESET_PCR called
main debug: Buffering 0%
main debug: End of audio preroll
main debug: Stream buffering done (2595 ms in 11041 ms)
main debug: Decoder buffering done in 0 ms
main warning: PTS is out of range (-6180), dropping buffer
main warning: PTS is out of range (-30127), dropping buffer
main error: ES_OUT_SET_(GROUP_)PCR  is called too late (jitter of 7344 ms ignored)
main error: ES_OUT_RESET_PCR called
main warning: early picture skipped

main debug: End of audio preroll

main debug: End of video preroll
main debug: Received first picture

ts warning: first packet for pid=3001 cc=0x1

main debug: Stream buffering done (2582 ms in 11321 ms)
main debug: Decoder buffering done in 0 ms
main warning: PTS is out of range (11431), dropping buffer
main warning: PTS is out of range (-12534), dropping buffer
main warning: PTS is out of range (-36516), dropping buffer
main error: ES_OUT_SET_(GROUP_)PCR  is called too late (jitter of 7706 ms ignored)
main error: ES_OUT_RESET_PCR called
main debug: End of audio preroll

main debug: End of video preroll
main debug: Received first picture

main debug: Stream buffering done (2563 ms in 10513 ms)
main debug: Decoder buffering done in 0 ms
main warning: PTS is out of range (51940), dropping buffer
main warning: PTS is out of range (27991), dropping buffer
main warning: PTS is out of range (4017), dropping buffer
main warning: PTS is out of range (-19966), dropping buffer
main error: ES_OUT_SET_(GROUP_)PCR  is called too late (jitter of 6837 ms ignored)
main error: ES_OUT_RESET_PCR called

main debug: End of audio preroll

main debug: End of video preroll
main debug: Received first picture

main debug: Stream buffering done (2578 ms in 11517 ms)
main debug: Decoder buffering done in 0 ms
main error: ES_OUT_SET_(GROUP_)PCR  is called too late (jitter of 7829 ms ignored)
main error: ES_OUT_RESET_PCR called
main debug: End of audio preroll

main debug: End of video preroll
main debug: Received first picture

main debug: Stream buffering done (2576 ms in 9478 ms)
main debug: Decoder buffering done in 0 ms
main warning: PTS is out of range (39140), dropping buffer
main warning: PTS is out of range (15188), dropping buffer
main warning: PTS is out of range (-8785), dropping buffer
main warning: PTS is out of range (-32768), dropping buffer
main error: ES_OUT_SET_(GROUP_)PCR  is called too late (jitter of 5778 ms ignored)
main error: ES_OUT_RESET_PCR called
main warning: early picture skipped
main debug: End of audio preroll


main debug: End of video preroll
main debug: Received first picture


I have weeded out the buffering lines as they are not needed.
Any idea whats going on?

---

### Post by ijumpship on 2012-07-13
By now you will see that packet loss and buffering when using VLC is sometimes a mystery.

Notice how packets are arriving late and dropping.but This may just be one of your problem as outline in this post [http://www.silicondust.com/forum/viewtopic.php?t=5877]("http://http://www.silicondust.com/forum/viewtopic.php?t=5877")  on the type of encryption you have on your Wi-Fi.

If we all list the number of things that cause the packet loss,it would be as many as the post here.

[B]A place to start is the file  and its size that you are streaming.
I would recommend you use some form of uPNP server so that your files can be transcode before they leave your mythbox.[/B]

I use Handbrake  in a script (35 Lines)  with a userjob at nights to transcode all my files to MP4/MKV tweak the settings a little and I watch my streams on a settop box. Yes those small processor box (there is 4 in my house) on a P4 backend

**I recommended this post [http://ubuntuforums.org/showthread.php?t=1768917](http://ubuntuforums.org/showthread.php?t=1768917)**

or more reading and geeky stuff here [https://help.ubuntu.com/community/Xbox360Media](https://help.ubuntu.com/community/Xbox360Media).

Do not worry too much about those buffering and packet loss,you could be here until next year trying to sort it out and all the network engineer would be recommending so much to do.

MPG/MPG2,AVI and many other codecs really have a drag on your network compressing them gives you better performance.

One thought though.VLC is one of the best player out there but for me when it come to streaming,I am on the fence.

And believe me an homebrew Router firewall in the future warm things up.Might be another point of failure by some thoughts,I only check mine every 6 months for general updates,but security updates are push automatically

---

### Post by ijumpship on 2012-07-19
Check this out.
I bought a cheap wireless router from a local deal they have it on sale (**Tenda)**.not trendnet
I bought the wr311,its a wireless N with 150Mbps.
This Thing have some marvellous feature such as bandwidth control it plays my videos from mythweb perfectly and on the Playstations without buffering.I am returning it.A pity,but I have enough gadget.but is worth a try.
The distance is poor though at 30ft you get about 48mbps.but it carries two additional feature I like.
(1) Wireless Network bridge so with two of them bridge I get 100ft at 110mbps
(2) WMM  Wifi MultiMedia which reall enhance streaming

another feature I wish was there was MIMO.I guess is on the 300mbps

I paid $14 each for them.

---

