---
title: "[SOLVED] How to watch BloombergTV in VLC or Mplayer"
date: 2008-12-29
forum: Multimedia Software
---

### Post by dixonstalbert on 2008-12-29
Bloomberg.com contains a link to watch live Bloomberg TV. Unfortunately it is encapsulated in a javascript which a lot of Firefox media plugins cannot figure out. 
If they do, you end up with no audio, because the content uses Windows Media Audio Speech also known as WMA2 and your media plugins wont decode this without working WMV_DMO codecs linked to them. 

Here's how I got things working:

1. I installed medibuntu codecs (search medibuntu and w32 codecs for instructions on this) and also ubuntu-extras-restricted

2. I found out what the direct mms links were for Bloomberg TV. I installed Gnome 'Gecko' mediaplayer Firefox plugin from Synaptic. (Make sure you uninstalled Totem and VLC firefox plugins first (see excellent 'Comprehensive Multimedia Howto' sticky in this subforum) then went to Bloomberg TV link in Bloomberg.com

I chose "copy link" by right-clicking over running mediaplayer and posted into vlc . VLC opened the link ,without audio,  but it did extract the direct links and I saved them as a playlist. here is the playlist which if you save as "bloomberg.xspf" AND edit the line <location>file:///home/dixon/bloombergTV.xspf</location> so it matches where you saved file.  you should be able to open it with your vlc, but without audio (for now!)

```
<?xml version="1.0" encoding="UTF-8"?>
<playlist version="1" xmlns="http://xspf.org/ns/0/" xmlns:vlc="http://www.videolan.org/vlc/playlist/ns/0/">
	<title>Playlist</title>
	<location>file:///home/dixon/bloombergTV.xspf</location>
	<trackList>
		<track>
			<location>http://ads.bloomberg.com/adstream_sx.ads/bloomberg/tvradio/tv/live/200/1958127952@x40,x50,x70,Middle!Middle</location>
			<extension application="http://www.videolan.org/vlc/playlist/0">
				<vlc:id>0</vlc:id>
			</extension>
		</track>
		<track>
			<location>mms://a627.l2479952251.c24799.g.lm.akamaistream.net/D/627/24799/v0001/reflector:52251</location>
			<creator>Bloomberg L.P.</creator>
			<extension application="http://www.videolan.org/vlc/playlist/0">
				<vlc:id>1</vlc:id>
			</extension>
		</track>
		<track>
			<location>mms://a536.l2479952400.c24799.g.lm.akamaistream.net/D/536/24799/v0001/reflector:52400</location>
			<creator>Bloomberg L.P.</creator>
			<extension application="http://www.videolan.org/vlc/playlist/0">
				<vlc:id>2</vlc:id>
			</extension>
		</track>
		<track>
			<location>mms://a1598.l2489858165.c24898.n.lm.akamaistream.net/D/1598/24898/v0001/reflector:58165</location>
			<title>US Channel (Live 56Kbps)</title>
			<creator>Bloomberg L.P.</creator>
			<extension application="http://www.videolan.org/vlc/playlist/0">
				<vlc:id>3</vlc:id>
			</extension>
		</track>
		<track>
			<location>mms://a1332.l2489859148.c24898.n.lm.akamaistream.net/D/1332/24898/v0001/reflector:59148</location>
			<title>US Channel (Live 56Kbps)</title>
			<creator>Bloomberg L.P.</creator>
			<extension application="http://www.videolan.org/vlc/playlist/0">
				<vlc:id>4</vlc:id>
			</extension>
		</track>
		<track>
			<location>mms://media2.bloomberg.com/btv_US200_n.asf</location>
			<creator>Bloomberg L.P.</creator>
			<extension application="http://www.videolan.org/vlc/playlist/0">
				<vlc:id>5</vlc:id>
			</extension>
		</track>
		<track>
			<location>http://media2.bloomberg.com/btv_USnb_n.asf</location>
			<creator>Bloomberg L.P.</creator>
			<extension application="http://www.videolan.org/vlc/playlist/0">
				<vlc:id>6</vlc:id>
			</extension>
		</track>
	</trackList>
	<extension application="http://www.videolan.org/vlc/playlist/0">
		<vlc:node title="http://www.bloomberg.com/streams/video/LiveBTV200.asxx?RND=958127952&amp;vCat=&amp;A=">
			<vlc:item tid="0" />
			<vlc:item tid="1" />
			<vlc:item tid="2" />
			<vlc:item tid="3" />
			<vlc:item tid="4" />
			<vlc:item tid="5" />
			<vlc:item tid="6" />
		</vlc:node>
	</extension>
</playlist>
```

3. To get sound in vlc, you need its libdmo_plugin.so file in /usr/lib/vlc/codec directory. I got this file from an install of vlc in Fedora 10.

[COLOR="Blue"]I have attached an archived copy of my libdmo_plugin.so to this post[/COLOR]


Actually what I did was backup my /usr/lib/vlc/codec directory and copied the same directory from my Fedora10 install.


  

I tried for about 20 hours to compile vlc for hardy  with --enable-loader switch in order to build this plugin , but current nightly build has a bug in mtime.h which crashes install, and current 0.98 tarball will complete make (after I rebuilt ffmpeg with swscale and zlib switches)   but sudo make install crashes with error in libtool call to libvlc0.

I gave up at this point and installed from repository

[http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) hardy main

This gave me 0.98 version of vlc but still no sound. I still had to get the missing libdmo_plugin.so plugin. (BTW if you want to upgrade your Hardy vlc to this repository's version, uninstall your vlc first, then add the above line to your synaptics 3rd party repository list, then reload repositorys, then install with synaptic)


4. If you prefer mplayer (or gmplayer or smplayer or kmplayer), or you don't want to fiddle with tracking down libdmo_plugin, I have reformated the above xspf file into a pls file. save the code below as 'bloomberg.pls', then open it with  mplayer -playlist bloomberg.pls

```
[playlist]
NumberOfEntries=3

File1=mms://a627.l2479952251.c24799.g.lm.akamaistream.net/D/627/24799/v0001/reflector:52251
Title1=Bloomberg TV 256kp
Length1=-1

File2=mms://a536.l2479952400.c24799.g.lm.akamaistream.net/D/536/24799/v0001/reflector:52400
Title2=Bloomberg TV link2
Length2=-1

File3=>mms://a1598.l2489858165.c24898.n.lm.akamaistream.net/D/1598/24898/v0001/reflector:58165
Title3=Bloomberg TV 56k
Length3=-1

Version=2
```


I made a desktop launcher with```
vlc bloomberg.xspf 
```

Now I can click on it and get the latest depressing news about the market!

---

### Post by Bill49 on 2009-03-14
Thanks for this - a nice piece of work.  I tried and failed to do this several months ago. I have been using zattoo instead, but 2 days ago it removed bloomburg from its schedule so I was back on the hunt and found your post.

I have one small problem; the sound lags behind the video by about one and a half seconds. Does any have any ideas how to cure this ?
Bill

---

### Post by dixonstalbert on 2010-05-10
just did a clean install of 10.04 'lucid' ubuntu.

I was able to get sound with the high speed links after installing libdmo_plugin but the 56k link uses WMA3 and this doesnt work

---

### Post by thetrystero on 2010-11-07
hi, thanks for sharing. could you please post the xspf code for Bloomberg Asia? Thanks.

---

