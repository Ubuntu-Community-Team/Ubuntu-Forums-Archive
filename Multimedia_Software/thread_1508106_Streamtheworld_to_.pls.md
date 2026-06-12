---
title: "Streamtheworld to .pls"
date: 2010-06-12
forum: Multimedia Software
---

### Post by FishRCynic on 2010-06-12
i didn't know this, so i thought i would share
how to make the .pls for rhymthbox (or others) 
from radio stations using streamtheworld 

thanks to 
[http://creations.lochrider.com/?p=84](http://creations.lochrider.com/?p=84)

Get the stream (pls) of a streamtheworld radio

If like me you are listening to some webradios, you probably have faced this problem : a lot of radios are broadcasting over the web via an embedded flash player to force you to go on their website to be able to listen to it.

So if you want to get the actual audio stream URL (pls or m3u), the widely used solution is to take a look at the requests that the player is sending to its server (with the NET tab of Firebug on Firefox per example).
But it sometimes happens that the URL you get is not an audio stream but a flash file with a buffering system so in this case, you cannot use it on your favorite webradio player (or on your N900 like me :p).

So, let’s get to the point of this post : if the radio you want is a streamtheworld stream (like the radio I wanted to get : Radio CKOI), I’ve got a really simple solution for you :
First of all, use Firebug on Firefox to see the requests that the player is doing and try to locate a request that looks like : [http://38.100.101.69/CKOIFMAAC?streamtheworld_user=1&nobuf=1271075550431](http://38.100.101.69/CKOIFMAAC?streamtheworld_user=1&nobuf=1271075550431).
Once that you have done so, you just have to use the stream ID this URL provided you : CKOIFMAAC in this example.

The URL you are looking for is : http://provisioning.streamtheworld.com/pls/{theIDofTheStream}.pls

This entry was posted on Monday, April 12th, 2010 at 11:04 pm

ie for this station
 http://provisioning.streamtheworld.com/pls/{theIDofTheStream}.pls
=  [http://provisioning.streamtheworld.com/pls/CKOIFMAAC.pls](http://provisioning.streamtheworld.com/pls/CKOIFMAAC.pls)

some radio stations i've added
from ontario

Q107   [http://provisioning.streamtheworld.com/pls/CILQFMAAC.pls](http://provisioning.streamtheworld.com/pls/CILQFMAAC.pls)
Vinyl 95.3 [http://provisioning.streamtheworld.com/pls/CINGFMAAC.pls](http://provisioning.streamtheworld.com/pls/CINGFMAAC.pls)

and for headwaters area (not streamtheworld but uniquely varied format)
105.1 [http://wms141.netromedia.net/ches](http://wms141.netromedia.net/ches)

---

### Post by csgrad on 2010-07-07
Thanks, this was very helpful for me :) Needed to know how to add the q107 stream and your instructions worked great. :D

---

### Post by Nullexe on 2010-08-31
Worked great for me.  I added Edge 102:

[http://provisioning.streamtheworld.com/pls/cfnyfm.pls](http://provisioning.streamtheworld.com/pls/cfnyfm.pls)

---

### Post by there.is.only.xul on 2010-11-08
Necropost of necroposts!

Anyway, got a URL I wanna share. WJQX 106.1 in the Michigan area.
[http://provisioning.streamtheworld.com/pls/WJXQFMAAC.pls](http://provisioning.streamtheworld.com/pls/WJXQFMAAC.pls)

---

### Post by Jerriy on 2011-08-17
I also found another, easier (some would say lazier) way to solve this:just go to **radio-locator.com** and see if your radio station isn't already listed there. If so then you'll find a direct link to the streamtheworld media source file and all you do is grab that link and put it in your favorite media player.

That w'd spare you installing firebug and going fishing for a code and all that jazz.

---

