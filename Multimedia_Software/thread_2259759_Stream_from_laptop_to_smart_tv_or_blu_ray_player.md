---
title: "Stream from laptop to smart tv or blu ray player"
date: 2015-01-06
forum: Multimedia Software
---

### Post by Hugh_Barstead on 2015-01-06
Hello all, I am new to Ubuntu and enjoying this OS very much (Version 14.04 LTS Desktop). However I am in need of some advice regarding software to wirelessly stream (or cast) video and audio from my Dell Inspiron 15 - 7537 to a Samsung smart TV or attached Sony Blu Ray player.

The kind of functionallity I am after is contained in the software called Popcorn Time, which when after a movie is chosen allows me to select either the laptop screen, Samsung TV or the Blu Ray player as the display device. Simple, fast, and effective even at 1080p resolution. The problem I have with Popcorn Time is that you may only select video from their sources, and not from any of the video already stored on my laptop. I want to play my videos, not theirs, on my TV. A wired connection is not an option.

The included-with-Ubuntu video player does not seem to offer this function, nor does VLC Media Player, XBMC or any of the other simple players which I have tried. Plex is capable of doing this in a different way ("Pull" from the TV rather than "Push" from the laptop) but Plex is huge and cumbersome and eats up far too many resources on my little laptop. (It is also the devil to get rid of).

Can anyone recommend a video player which includes the Popcorn Time style "Push" streaming functionality, or, failing that, identify the software agents being used to provide this service? Thank you in advance for any advice you may have to offer.

Hugh Barstead

---

### Post by papibe on 2015-01-06
Hi Hugh_Barstead. Welcome to the forum ):P

I believe most 'smart' TVs function as a DLNA/UPnP client. So you would need a UPnP server.

Take a look at [mediatomb]("https://help.ubuntu.com/community/MediaTomb"), or [MiniDLNA]("https://help.ubuntu.com/community/MiniDLNA").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by mooreted on 2015-01-06
I don't suppose your TV has the Plex app? I love Plex.

---

### Post by Hugh_Barstead on 2015-01-07
Hello papibe, thank you for your response. I did try mediatomb but it seemed to stutter with 1080p material. Perhaps I should try it again. I have not tried MiniDLNA and will give it a whirl. It is my experience that  the DLNA / UPnP servers work with "Pull" technology, that is I have to get the TV to pull the video from the server. What I am really looking for is the "Push" technology where I can just tell the laptop to send the stream to the TV. Popcorn Time implements that so well that I am sure there must be another app which uses it. Oddly, when I install Popcorn Time on the Windows side of the laptop, it does not give me the option to push the video to the TV. I am half convinced that the resources to do this are already built in to Ubuntu, but have no idea at all what they might be.

I will try MiniDLNA, and if I have to live with "Pull" technology I will (no big deal). I do like the "Push" method better though, and will keep looking for that.

Thanks again for your help,

Hugh Barstead

---

### Post by Hugh_Barstead on 2015-01-07
mooreted, hello, and thanks. Both the TV and the Blu Ray can easily read the Plex server, but the server itself on my limited laptop was not the best solution. I could see dedicating a machine to a Plex server, but for my intended usage it is overkill. Plus, it still doesn't use the "Push" technology I am looking for. Thank you for your input.

Hugh Barstead

---

### Post by mooreted on 2015-01-07
I have Plex on a very powerful desktop. Works great. Hopefully the other DLNA solutions will work for you.

Have fun.

---

### Post by MartyBuntu on 2015-01-07
I've used MediaTomb until about a year ago...I switched to PS3 Media Server last year.

Both can transcode "on-the-fly".

---

### Post by Hugh_Barstead on 2015-01-07
I have installed miniDNLA and like it a lot. Fast and efficient, and very easy on my laptop's limited resources. I can pull a 2 GB large video with the Blu Ray player (in 1080p) and while it is playing I can start and watch the same video on my pad without either of them stuttering, all while I am surfing the net or answering email. The home theatre amp (a Pioneer) reads audio .wav files in 24/96 format from miniDNLA without issue. The Samsung TV is a little more iffy, sometimes it sees the server and sometimes not - no idea why. It doesn't matter though because the Blu Ray player provides redundant functionality anyway.

I am still looking for software which works  the way Popcorn Time does. With that software I can be watching broadcast TV, get bored with it, fire up Popcorn Time on the laptop, select a movie or TV show, select the TV (or Blu Ray player) from a pop up menu and press play. Without having to touch the remote the TV will go black for about 1 second and then just start playing the selected program. NOTE: I am in no way endorsing Popcorn Time as a product, and I do have issues with the quasi legal status of some of their content, but I just love the way it "pushes" the content to the selected device without other intervention. If such a feature could be implemented in the standard video player in Ubuntu I would not need a server like miniDNLA at all. If anyone knows of any other software which works this way I would be very interested to hear about it.

In any case, I am satisfied for the moment. Thanks to all for all you input. Happy Ubunting!

Hugh Barstead

---

