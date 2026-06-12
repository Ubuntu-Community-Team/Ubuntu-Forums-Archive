---
title: "When will VLC 1.1.0 be available"
date: 2010-06-22
forum: Multimedia Software
---

### Post by up2early on 2010-06-22
Does anyone know when we may see the update to VLC 1.1.0 for Ubuntu 10.04 (Lucid Lynx)?

---

### Post by snowpine on 2010-06-22
Probably never; that's not how Ubuntu updates work. :)

You can install it yourself from:

[https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc)

or:

[http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

---

### Post by maverick340 on 2010-06-22
> **up2early said:**
> Does anyone know when we may see the update to VLC 1.1.0 for Ubuntu 10.04 (Lucid Lynx)?

i would like to know too

---

### Post by JohnnyC35 on 2010-06-22
> **up2early said:**
> Does anyone know when we may see the update to VLC 1.1.0 for Ubuntu 10.04 (Lucid Lynx)?

Looks like 1.1.0 is already available: [http://www.videolan.org/](http://www.videolan.org/)
To add the PPA go here: [http://ubuntulife.wordpress.com/2010/06/21/vlc-1-1-0-final/](http://ubuntulife.wordpress.com/2010/06/21/vlc-1-1-0-final/)
... or rather I'll paste it 

> 
sudo add-apt-repository ppa:c-korn/vlc && sudo apt-get  update


---

### Post by Eyeron on 2010-06-22
Many thanks for your help Johnny

---

### Post by howefield on 2010-06-22
> **maverick340 said:**
> i would like to know too

This page gives provides an outline of the Ubuntu policy in providing updated software versions.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by urbanus on 2010-06-22
Does the hw accel only work with Nvidia Binary drivers?

---

### Post by iraparks on 2010-06-22
which Application do you choose to open the "apturl" file when chosen from the link above? Thanks

---

### Post by gufide on 2010-06-22
Yea! Thank you JohnnyC35, it work for me!:popcorn: __[]("http://swiss.ubuntuforums.org/member.php?u=1023521")

---

### Post by hachel on 2010-06-22
my system tells me it can only do a partial upgrade, holding back all files from that ppa

---

### Post by XSAlliN on 2010-06-22
> **hachel said:**
> my system tells me it can only do a partial upgrade, holding back all files from that ppa

Try by Synaptic.

---

### Post by shantiq on 2010-06-22
[B][COLOR="Blue"]full two lines are

[/COLOR][/B]```
[B]sudo add-apt-repository ppa:c-korn/vlc && sudo apt-get update
sudo apt-get install vlc mozilla-plugin-vlc[/B]
```

---

### Post by ron999 on 2010-06-22
Hi
I'm already subscribed to the korn ppa, but my VLC isn't upgraded yet.
It's still v1.0.5.

---

### Post by shantiq on 2010-06-22
> **ron999 said:**
> Hi
I'm already subscribed to the korn ppa, but my VLC isn't upgraded yet.
It's still v1.0.5.


[B][COLOR="Blue"]well Ron run those two lines in your terminal

```
sudo add-apt-repository ppa:c-korn/vlc && sudo apt-get update
sudo apt-get install vlc mozilla-plugin-vlc
```


one at a time

then go applications/sound and video/vlc

then click on help/about

and it should show picture in attachment. Good luck it should work

[/COLOR][/B]

---

### Post by ron999 on 2010-06-22
Nope, still the same.
Maybe because I'm still using Karmic.

---

### Post by shantiq on 2010-06-22
> **ron999 said:**
> Nope, still the same.
Maybe because I'm still using Karmic.
[B][COLOR="Blue"]
It might using data not present in Karmic.  Sorry but it is beyond my knowledge. Someone will know. Maybe a new post asking that question might yield the right answer

Best of luck.[/COLOR][/B]

---

### Post by XSAlliN on 2010-06-22
> **ron999 said:**
> Nope, still the same.
Maybe because I'm still using Karmic.

Have you tried synaptic, search for VLC and select the files for UPGRADE.

---

### Post by W00ster on 2010-06-22
Not so fast.

I had 1.0.6 installed, even after adding the PPA, I could not upgrade from 1.0.6. 

Removed the old installation of vlc and reinstalled.
Here is the output of a start attempt:

$ /usr/bin/vlc
VLC media player 1.1.0-pre1 The Luggage (revision c8209ec)
vlc: unknown option or missing mandatory argument `--user-agent="VLC media player"'
Try `vlc --help' for more information.

It's not the release version which gets downloaded and installed but a pre-release and it will not start.

---

### Post by ron999 on 2010-06-22
Look at the website here:-[https://launchpad.net/~c-korn/+archive/vlc?field.series_filter=lucid]("https://launchpad.net/~c-korn/+archive/vlc?field.series_filter=lucid")
The **filter** button shows it's only Lucid that's at v1.1.0

---

### Post by northwestuntu on 2010-06-22
deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) lucid main 

this got it done 4 me :p

---

### Post by shantiq on 2010-06-22
**[COLOR="Blue"]well it seems ok for all versions[/COLOR]**

---

### Post by ron999 on 2010-06-22
> **shantiq said:**
> **[COLOR="Blue"]well it seems ok for all versions[/COLOR]**

Not when you click the _**filter**_ button.
[IMG]http://img824.imageshack.us/img824/3811/updateef.png[/IMG]

---

### Post by mc4man on 2010-06-22
> Does the hw accel only work with Nvidia Binary drivers?

Not sure if 'only', though probably you could sub 'well'

Taking a quick look at korn's diff - it doesn't appear hw accel (vaapi) was built in anyway.

---

### Post by XSAlliN on 2010-06-22
> **ron999 said:**
> Not when you click the _**filter**_ button.
[IMG]http://img824.imageshack.us/img824/3811/updateef.png[/IMG]

You're right, Korn only updated Lucid and Maverik, so this lives you with this alternatives:

**ppa:webupd8team/vlc**   

Which is VLC 1.1.0 with no vaapi, or...

**ppa:nvidia-vdpau/cutting-edge-multimedia**

...which can go as far as 1.1.0 for Karmic and 1.2.0 beta for Lucid. This is optimised to work with VA-API - yet not sure if it will work with ATi cards. Never used video acceleration under Linux, being still new and mostly beta (or even alpha) so, can say I miss it and guess same goes for most. So if it works, that's good if not that's the way it always was so... :)

---

### Post by ron999 on 2010-06-22
Hi
Thanks for that XSAlliN.
I probably don't need any of that vaapi stuff anyway.
For now I'm gonna stay with my v1.0.5.
If I need to update later I'll use the ppa:webupd8team/vlc option.
:guitar:

---

### Post by shantiq on 2010-06-22
> **ron999 said:**
> Not when you click the _**filter**_ button.
[IMG]http://img824.imageshack.us/img824/3811/updateef.png[/IMG]

[COLOR="Blue"]**whoops i see I did not realize you had to click on it   DERRRRRRR:p:p**[/COLOR]

---

### Post by bruno9779 on 2010-06-22
EDIT: slow reply, so many had posted already, lol

---

### Post by Linuxforall on 2010-06-22
c.korn has updated his ppa to latest final vlc 1.1.0 for Lucid and Meerkat, its working fine here under x64 Lucid.

---

### Post by vDub2000 on 2010-06-22
I'm having a hard time adding the repository. It times out when it tries to retrieve the key from keyserver.ubuntu.com but when I actually visit the site, I get the "it works!" message.

---

### Post by shantiq on 2010-06-23
**[COLOR="Blue"]i would suggest trying at different times of day. Probably a traffic volume problem.[/COLOR]**

---

### Post by nilarimogard on 2010-06-23
> **ron999 said:**
> Hi
Thanks for that XSAlliN.
I probably don't need any of that vaapi stuff anyway.
For now I'm gonna stay with my v1.0.5.
If I need to update later I'll use the ppa:webupd8team/vlc option.
:guitar:

I removed the webupd8team/vlc PPA because I don't plan on maintaining it so please use the c-korn PPA instead.

As for vaapi - the c-korn PPA does not have vaapi support. Any PPA which has VLC 1.1.0 built with vaapi will break all other packages that depend on ffmpeg because it needs newer ffmpeg/gstreamer (so if there are no ffmpeg packages in the PPA, it clearly doesn't have vaapi support). That's what the bleeding edge multimedia PPA does. It also comes with mplayer so that will work too, but video editors, other video players and so on will be broken!

More info [here]("http://www.webupd8.org/2010/06/how-to-install-vlc-110-final-in-ubuntu.html").

---

### Post by up2early on 2010-06-23
Thanks for everyones help, for me using

```
sudo add-apt-repository ppa:c-korn/vlc && sudo apt-get update
sudo apt-get install vlc mozilla-plugin-vlc
```

has me perfectly updated to VLC media player 1.1.0 The Luggage

---

### Post by andrew.46 on 2010-07-22
Hi up2early,

> **up2early said:**
> ...perfectly updated to VLC media player 1.1.0 The Luggage

Just as the next version rolls out :)

[http://www.videolan.org/vlc/releases/1.1.1.html](http://www.videolan.org/vlc/releases/1.1.1.html)

Andrew

---

### Post by up2early on 2010-07-22
Here we go again!

---

### Post by Linuxforall on 2010-07-22
> **andrew.46 said:**
> Hi up2early,



Just as the next version rolls out :)

[http://www.videolan.org/vlc/releases/1.1.1.html](http://www.videolan.org/vlc/releases/1.1.1.html)

Andrew

Says GPU decoding for Linux, would be interesting to see that implemented on Lucid.

---

### Post by mc4man on 2010-07-22
> Says GPU decoding for Linux, would be interesting to see that implemented on Lucid.

In the lucid ubuntu repo it will probably never happen, same for most ppa versions. You'd need a ppa that[ supplied new ffmpeg libs  ]("https://launchpad.net/~nvidia-vdpau/+archive/cutting-edge-multimedia") (or build yourself.

In maverick, currently 1.1.0, vaapi is not enabled, it hopefully will get a rebuild to 1.1.1 which fixes a few things, again not too sure vaapi will be enabled. (I'd guess it won't, but maverick ppa's should be able to easily enable.

As to the value of vaapi in vlc I'd think it will come down as usual to your hardware, at least here while it works ok, mplayer with vdpau is vastly superior.

---

### Post by bsmith1051 on 2010-07-22
> **nilarimogard said:**
> Any PPA which has VLC 1.1.0 built with vaapi will break all other packages that depend on ffmpeg because it needs newer ffmpeg/gstreamer
Wasn't the whole point of VLC to have a 'monolithic' self-contained app?  It certainly is on Windows, i.e., it doesn't have any dependencies on DirectX codecs or demuxers.  I thought the only 'dependency' it would have would be the video driver/version.

---

### Post by mc4man on 2010-07-22
> Wasn't the whole point of VLC to have a 'monolithic' self-contained app? 
A large amount of decoding and encoding support in vlc is provided thru avcodec.
In the repo versions (official or ppa), avcodec is supplied by the shared ffmpeg libs (libavcodecXX in particular.

So a newer vlc is only as capable as the ffmpeg it is built off of and  the shared libs it depends on.

It is certainly possible ( and preferred imo) to statically link vlc when building, then support is 'built-in' so to speak.
In other words I can remove all the shared ffmpeg libs here (and any other lib i statically link), and vlc will work fine.

I'm not aware of any ppa that does this with vlc (build with internal avcodec support), ubuntu can't.
(possibly you can't in ppa also , don't know

---

### Post by Linuxforall on 2010-07-22
c.korn's ppa updates to latest vlc 1.1.1 :) good job and that was prompt.

---

