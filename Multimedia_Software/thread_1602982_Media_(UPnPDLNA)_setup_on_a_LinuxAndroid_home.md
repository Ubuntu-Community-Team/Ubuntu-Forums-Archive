---
title: "Media (UPnP/DLNA) setup on a Linux/Android home"
date: 2010-10-22
forum: Multimedia Software
---

### Post by dabbi2000 on 2010-10-22
I am getting a bit frustrated since I've been spending days to setup a multimedia network at home. My friends have Sonos, playing music all around their house with a remote control.. I have 3x Linux based laptops and 2x Androids (wife and me) and I cannot believe that it's impossible to create a Sonos like setup with Linux?!

To start with, the setup has to use UPnP/DLNA and a 1) media server 2) media controller and 3) media renderer. The Androids should be the media renderers. For this, a very nice app exists called AndroMote. The problem is finding both a media server and renderer supporting this!

XBMC is the only one I've found which AndroMote detects as a UPnP server but XBMC completely clogs my 5 year old laptop since it is also a media player with a almost 3D interface - so the fan is spinning like loud as a helicopter as long as XBMC is running. Although I have to give XBMC credit for good support and active development - they even have a very good Android remote app - but the idea of "one ring to bind them" is not that of XBMC.

Then there is Firefly - promising but not detected by AndroMote.

PS3 media server had problems too.

Then there are tons of others (Rygel, forked DAAPd, miniDLNA, Servioo, MediaTomb...) but how the heck should the amateur me have time to try all these to see if they work with AndroMote?


So I am getting a bit frustrated, seeing my friends with Sonos and Apple just plugging in their systems and running... is this mission impossible?

---

### Post by Munk3y on 2010-10-22
I'm trying to do the same thing. I have MediaTomb up and running that AndroMote sees and connects to. However, I'm having trouble with a Media Renderer. Also, why does AndroMote download entire items to the phone to try and play them rather than streaming? I don't get it and I can't find an alternative to AndroMote.

---

### Post by kroem on 2010-10-22
No. Just get a Squeezebox setup ;)

Or fill your house with fit-pc2/Plug computers.... and then run like MPD. 

I would really go with the Squeezebox, it has a decent DAC aswell.

---

### Post by dabbi2000 on 2010-10-22
> **Munk3y said:**
> I'm trying to do the same thing. I have MediaTomb up and running that AndroMote sees and connects to. However, I'm having trouble with a Media Renderer. Also, why does AndroMote download entire items to the phone to try and play them rather than streaming? I don't get it and I can't find an alternative to AndroMote.

I am trying out MediaTomb. According to AndroMote site there are no options for us Linux users but XBMC as media renderer. That's completely impossible on my 5-7 year old (almost recycled!) laptops... I would kill for compatibility with Rhytmbox/Banshee. Why doesn't it just click with the UPnP plugin, isn't that what UPnP was made for??

---

### Post by tonyscha on 2010-10-27
I am a little confused on what you are asking for...

So there is 3 parts to UPnP (MediaRenderer,MediaServer,Control Point), what device do you want to do what?

Where are you trying to play from?
Where are you trying to push media too



You can use Twonky on android, and it will work as a server, and I think you can renderer to it locally.


**Edit, sorry I read your post again**
> 
To start with, the setup has to use UPnP/DLNA and a 1) media server 2) media controller and 3) media renderer. The Androids should be the media renderers. For this, a very nice app exists called AndroMote. The problem is finding both a media server and renderer supporting this!

I will check out AndroMote, 

As for a media Server, try ushare

you also could try Twonky, but it cost money :(


**Edit #2**

AndroMote is a mediarenderer and control point built in one. I had it streaming off my tversity app on my windows box in about 5 minutes :D

Let me know, I will try to help you.

---

### Post by dabbi2000 on 2010-10-27
Thank you Tonyshca, every input here is golden.

I have now tried out Mediatomb, AndroMote can see the server and list the files but stops while trying to play. Next I am trying out Ampache
[http://ampache.org/](http://ampache.org/)

but it seems from the AndroMote website only XBMC is actually supported so I don't have high hopes.


I am hoping to make this work with Rhythmbox plugins and a remote app for the Android but if that fails too I am giving up this trial project. Seems Linux in 2010 just isn't up to the Sonos "multiroom play and control" yet :-(

---

### Post by jshailes on 2011-01-19
Hi dabbi,

I'm in exactly the same predicament as you - frustrated that android can't tell a computer to play some music with the only simple solution to buy custom hardware; it just seems ridiculous. Did you ever have success? 

I've posted on a couple of forums and someone has recommended squeeze commander, the interface seems good and I think the guy that wrote it had our frustration too. It does integrate with these 'squeezebox' devices it seems to simply be a convenience feature since there is an open source server that can be installed in linux.

Cheers,

James

---

### Post by dabbi2000 on 2011-01-19
Hi James,
no I haven't found anything unfortunately. But it's been 3 months and Android is becoming ever more popular. Something just has to happen, I'm green of envy of my friends who do this from the box with their Apple stuff!

---

### Post by dabbi2000 on 2011-01-19
Hi James,
no I haven't found anything unfortunately. But it's been 3 months and Android is becoming ever more popular. Something just has to happen, I'm green of envy of my friends who do this from the box with their Apple stuff!

---

### Post by desana on 2011-01-19
Not sure if this is what your looking for [http://code.google.com/p/remuco/](http://code.google.com/p/remuco/) should work with most mediaplayers for linux

---

### Post by dabbi2000 on 2011-01-22
Looks promising but on the download page it has a package from 2007 and I cannot find any .apk to install?

---

### Post by fertroya on 2011-02-01
Your search is over. [www.skifta.com](www.skifta.com). What I'd really like now is a unix client to push my Ubuntu desktop's content to my WDTV Live (DLNA enabled) device. That is, phone independent.

---

### Post by dabbi2000 on 2011-02-02
Looks promising! Please let us know of your experiences. This just maybe is the 'one ring to bind em' I've been looking for

---

### Post by drjimmy42 on 2011-02-07
Skifta force closed every time I browsed anything.  I tried andromote but it wasn't much better.  I am having very good luck with 2player. Its in the market.

Are there any good desktop based control points? The phone is cool but sometimes I want to just control things from my laptop.

---

### Post by dabbi2000 on 2011-02-07
It seems the options are growing in number, great!

XBMC is a really cool client but I gave it up since it was really hard on my 5 year laptop, the CPU fan was running constantly. Do you know if there are any hacks/alternatives with lighter UI as that's what's draining the CPU?

---

### Post by loveman on 2011-04-05
Hi dabbi2000 did you get something working yet? 
i have tried a few things and found that Rygel works as a render for audio with Andromote as the controller.
One thing i wondered about what you initially said though - playing music all around the house - you cannot easily do that using multiple computers - if that is what you meant? They will not play in synch. You have to get something like sonos if you want the same music playing through the house in synch, i think. The best app for your phone to play music from a upnp server that i have found is called plugplayer, it looks and works good but it doesn't work with rygel!! The developer said he would be checking this out though so keep your eye on plugplayer. If you don't have m4a files you could try using rhythmbox with the coherence upnp plugin, this does work with plugplayer (as long as your music is not m4a which half mine is!)

---

### Post by loveman on 2011-04-05
> **drjimmy42 said:**
> Skifta force closed every time I browsed anything.  I tried andromote but it wasn't much better.  I am having very good luck with 2player. Its in the market.

Are there any good desktop based control points? The phone is cool but sometimes I want to just control things from my laptop.

Try upnp inspector it shows up all the devices on your local network, right click a device to remote control playback on that device

---

### Post by dabbi2000 on 2011-04-26
I kind of gave up on this after trying out some solutions of which none worked flawlessly. In the meantime I've been using more and more of streaming services like Grooveshark and to control my media computers in the house I just remote-desktop them from my netbook. Not as comfy as using the phone but it works! I will try out Skifta and Rygel, thanks for your tips!

---

### Post by drjimmy42 on 2011-04-26
I've been using 2player for a while and its been great.  So far I only use it to play the media on my phone and not forwarded it to another renderer but its been great.

---

### Post by loveman on 2011-05-03
> **drjimmy42 said:**
> I've been using 2player for a while and its been great. So far I only use it to play the media on my phone and not forwarded it to another renderer but its been great.
 
 
I have tried a lot of apps and all of them have worked great for playing music on the phone itself. It is only when you try to use the phone to control another renderer that everything seems to get a lot less reliable.

---

### Post by topdownjimmy on 2011-06-07
My (newly) working setup uses:

[UPnPlay]("https://market.android.com/details?id=cx.hoohol.silanoid") (control point on Android)
[Rygel]("http://live.gnome.org/Rygel") (UPnP renderer on desktop/HTPC)
[MediaTomb]("http://mediatomb.cc/") (UPnP server on desktop)

---

### Post by nrayever on 2011-06-30
Mmmmm, some interesting ideas. Let's see which one works best. :KS:KS:KS

---

### Post by keithspg on 2011-10-15
Arrgh! There appears to be nothing that 'just works' and supports more than just 'file transfer' type media playing/syncing.

All the apparently 'full featured' android programs cannot see my server (ushare running on my tower). The ones that can see the server just give a list of songs (a couple give a list of albums, Woo Hoo) but will not allow a playlist or copying more than one song at a time to my phone/tablet. I have tried almost all of them, Skifta, Eminent, UPnPlay, ShareMe, BubbleUp, etc. The Program on my Motorola phone (just labeled DLNA) sees the share then allows me to copy multiples, but complains at each one saying that it cannot play the sound format, though it does just fine. Also, I need to 'accept' each transfer which is a pain.

I tried to set up rygel on the tower, but do not know what I did wrong, but I was confused as to how to tell it that my media was in a different directory than 'My Music'. Ushare installed and was easy to configure. I want this to run as a service as on a server and not as a user program. Ushare appears to do that. 

I have forked-daapd running as well, but it cannot be used by the current android progran nor does it allow me to copy an album or all the songs in a playlist to my phone/tablet. 

What am I doing wrong?

K

---

### Post by keithspg on 2012-05-06
Is anyone reading this thread any more? My challenge is purely music (sound, no video).

So in the meantime, I have figured it out. I have forkedDAAPD running and can play the songs on devices that can use the DAAP protocol. 

Also with the upnp/dlna stuff. I currently have the ushare program running. It is great as I can play files on my phone served from the server (linux). It appears that I can use the phone as a 'remote' and select music or playlist to pull music from the server and play it on a 'renderer'. The renderer can be a phone and that appears to 'work'. 

What I want is speakers in the kitchen. I want to control what is playing on them via the android app (either andromote or 2player). The part that is missing is a renderer. I am so confused and cannot figure out what to buy that will work in this seemingly 'normal' setup. All seem to be aimed at TV (video and audio) which require a screen and selection, etc. It appears that a Roku box should work, but it does not appear to be dlna/upnp compliant. It seems like the only solution is to get an apple AIrport Express and configure it in pulse audio as a speaker. It does not appear that this setup would allow it to appears as a 'dlna renderer' in any of the android programs and would, therefore, not work as I wish. 

Can anyone point me in a direction to do this? I can handle the analog amplification if needed also do not want to spend 400.00 to do it (sonos). I have speakers and amplifiers.

Please help.

Keith

---

### Post by freakalad on 2012-07-14
I've got a similar need:
[http://ubuntuforums.org/showthread.php?p=12104072](http://ubuntuforums.org/showthread.php?p=12104072)

Have you built a solution?

---

### Post by keithspg on 2012-07-16
Yes, I did. I bought one of these: [Sony NS 300]("http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0CEkQFjAA&url=http%3A%2F%2Fstore.sony.com%2Fp%2FSA-NS300%2Fen%2Fp%2FSANS300&ei=IQwEULGmB4mlrQG22IiyDA&usg=AFQjCNGeMcszjlBHZ0GKnjj1sAVq1oQ4gQ")

It works ok, but think I will build one out of a Raspberry PI. DLNA is very limited. There should be a better solution. My issue is mainly that I cannot select a point in a podcast. It will only start from the beginning and play through. If I stop and start, it starts over. Really a pain. Also, there are open audio formats that it will not play. Also, It none of the remotes will play an MP4 internet music stream. Probably also related to the format issue. 

Keith

---

### Post by freakalad on 2012-07-16
Sounds like problems related to the DLNA client/renderer, and not the server.
I've used DLNA served up by a few servers on a few renderers without the issues you've indicated.

I have a few ideas of my own for when my RasPi is *eventually* delivered.... either an XBMC/OpenELEC HTPC device serving up DLNA, or something else

---

### Post by dhysk on 2012-07-17
This suggestion was only from a page ago I was just wondering if you tried squeesebox?

That is the way I'm going because any computer can serve as the server, and any computer can also serve as a player.  Also there is a raspberry pi project going that looks promising as well as instructions on how to use a wifi router and sound card dongle as a receiver.

Logitech also sells devices, all can be controlled via a free android or iOS app.  With one server and a bunch of receivers (computer, hacked router, RPi, Logitech equipment, ect.) you can play a different song on each device or play the same song on all of them.

---

### Post by freakalad on 2012-07-18
I've used SqueezeBox waaaaay back in the day when it was still SlimServer.
Not a bad solution, but as with soem such solutions, it's ends up being a fairly narrow vendor-specific solution.

I now try to stay away from such stacks & rather focus my efforts on Open Data & Protocols, so that my clients & servers interact purely at a protocol/API level & not too strongly bound to a specific client/server set.
DLNA is one such vendor-neutral/agnostic solution.

---

### Post by tagawa on 2012-11-11
A bit late to the party but I had the same problem as you - searching for a hardware audio renderer. After a fair bit of research, I bought a Grace Digital radio (GDI-IR2600 - Innovator X). Sure enough, it's a bona fide UPnP renderer. It looks as though all their digital radios are, based on various reviews I've read such as this one:
[http://www.amazon.com/review/R2DBVRHK8CV6MW/ref=cm_srch_res_rtr_alt_1](http://www.amazon.com/review/R2DBVRHK8CV6MW/ref=cm_srch_res_rtr_alt_1)

So I can send songs to the device, remotely change the volume, etc. with regular UPnP requests. Using an inspector, it seems they also have a lot of Grace Digital-only actions for e.g. choosing preset stations. They have iPhone and Android apps which can control this.

The only downside is that it seems to be fussy about what it can play. Some MP3s work, some don't. WMA is mostly OK and OGG seems fine. Haven't tried other formats. Overall, very happy with it so far (no affiliation, by the way).

---

