---
title: "Creating a &quot;MythTV Extender&quot;??"
date: 2007-01-29
forum: Multimedia &amp; Video
---

### Post by SSTwinrova on 2007-01-29
This upcoming summer I think I'll be able to sell my parents on setting up a HTPC, and one of the big things my dad wants to be able to do is watch TV down in his office. We just moved into this house about 6 months ago, and in the infinite wisdom of the original house builders, there is no cable outlet in his office (but, and I'm not joking, there is one in his bathroom).

So, my original plan was just to play the DRM game with Vista and use Cablecards, Media Center Extenders, etc. to stream live TV down to his office over our network. Well, all the reports I've read appear to say that it just can't be done, regardless of DRM. As I wait to read reviews and experiences with Vista, I figured that starting to develop a backup plan would be a good idea.

I know MythTV can handle pretty much all my streaming and recording needs (minus the Cablecard support, but I can live without that), but I'm curious as to my options for the client end down in my dad's office. I'd like to avoid a full blown PC (he uses his work laptop for everything), so I was thinking maybe something along the lines of this ([http://www.mini-box.com/s.nl/sc.8/category.12/.f]("http://www.mini-box.com/s.nl/sc.8/category.12/.f")).

Does anyone have any experience or suggestions with setting up a MythTV client box that would be similar in nature to a Media Center Extender?? Thanks.

---

### Post by majoridiot on 2007-01-29
that box is more than enough for the job.  all you really need is to run the frontend (mythfrontend)
in you dad's office- the backend will handle the brunt of the work.  mythtv is an AWESOME
package and collection of plugins... the fact that it is free is mind-boggling.

congrats on thinking ubuntu and mythtv over vista.  :D

one caution- you most likely want a wired network.  b wireless can't cut it and g *might*
handle it, but you won't have the bandwidth for any other network traffic to the frontend. 
you  wind up with stuttering livetv and it'll just choke and die.

be sure to follow mario's excellent installation guides for the most painless setup-

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

good luck!

---

### Post by SSTwinrova on 2007-01-30
I had always been planning on a wired connection (well, at least until 802.11n was finalized, but with Linux, I'll definitely stick with wired ;) ). When you say that "the backend will handle the brunt of the work", where does this put me with codec support? My guess is that the streaming live TV and stuff with me MPEG-2, but I'd also really like to be able to let this access my ripped DVD collection (all in Xvid/AAC). Am I going to run into any processing power problems there?

---

### Post by majoridiot on 2007-01-30
> **SSTwinrova said:**
>  I'd also really like to be able to let this access my ripped DVD collection (all in Xvid/AAC). Am I going to run into any processing power problems there?

your media library can all be stored on and served from your backend box and accessed via
the "mythvideo" plugin.  all the frontend box needs to run is the frontend with the necessary
codecs.  more or less, all you need the frontend to do is pull the stream off the network, decode
it and display it.  you would be surprised how little processor power this actually takes... and
you need very little HD to accomodate it, as well.

of the two, the backend needs to be the beefiest of the two boxes, as it needs to be able to
capture,  stream and do other service functions such as filling and serving the program
listings, housekeeping, etc.  you especially want a hearty backend if you plan to record while
watching another channel or will be doing much commercial flagging and transcoding.

---

