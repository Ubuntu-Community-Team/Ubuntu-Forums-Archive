---
title: "Chrome 7.0.517.44, Totem 2.30.2 and .wmv"
date: 2010-11-06
forum: Multimedia Software
---

### Post by shortmort37 on 2010-11-06
I have a phpBB website with uploaded .wmv files.  These play fine under Windows, using Windows Media Player, with any browser; but with Chrome on Ubuntu 10.04 LTS, I just get a black box.  I hit the "play" button underneath, but the button goes to "pause" and the black box persists; I can toggle back and forth with no effect.  If I right-click on the box and select "About", it announces that it is Totem Browser Plugin 2.30.2.  If I click the up arrow to the lower right on the player control panel and choose Open with "Movie Player", the video launches and plays -  while playing, if I select Help -> About it announces that it is Totem Movie Player 2.30.2.

Any ideas about what's wrong?

adTHANKSvance
Dan

---

### Post by shortmort37 on 2010-11-07
<bump=up> ... </bump>

---

### Post by oregonbob on 2010-11-07
I'm no expert but you are probably missing some codecs, decoders etc. Check out the medibuntu package and also search Chrome extensions for "Windows Media Player"

---

### Post by shortmort37 on 2010-11-07
Well, I'd be inclined to agree with you - but if I download the file and play it, it plays with Totem Movie Player 2.30.2.  But it won't play in the Chrome browser with Totem Browser Plugin 2.30.2.  Doesn't that suggest I have the codecs I need, but there's a problem with the "glue" between the plugin and the player?

Love the beagle pic, BTW!  So does "Bode" (my beagle).

Dan

---

### Post by anders_c_ on 2010-11-07
Have you tried adding it with the html5 video tag instead? I think chromes built in player may be better than using totem plugin. You can try to install the mplayer plugin for browsers also...pretty much everything is better than totem in my opinion.

Edit: Does it work in firefox with the totem plugin?

---

### Post by shortmort37 on 2010-11-07
> **anders_c_ said:**
>  You can try to install the mplayer plugin for browsers also...pretty much everything is better than totem in my opinion.

Edit: Does it work in firefox with the totem plugin?

It does not!  Hmmm...

Where do I find the "mplayer plugin for browsers"?

Dan

---

### Post by shortmort37 on 2010-11-07
I just installed WMPlayer Inline 1.2.1 - it appears in my Chrome extensions, while Totem does not.  Still, the webpage presents with the Totem embedded player.  Not sure why that is so; do I need to resort to removing Totem from Ubuntu, in order for Chrome not to default to it?

Dan

---

### Post by shortmort37 on 2010-11-07
FWIW, here's the source code on the rendered page:


```
			<object width="320" height="285" classid="CLSID:6BF52A52-394A-11d3-B153-00C04F79FAA6" id="wmstream_2016"> 
				<param name="url" value="./download/file.php?id=2016" /> 
				<param name="showcontrols" value="1" /> 
				<param name="showdisplay" value="0" /> 
				<param name="showstatusbar" value="0" /> 
				<param name="autosize" value="1" /> 
				<param name="autostart" value="0" /> 
				<param name="visible" value="1" /> 
				<param name="animationstart" value="0" /> 
				<param name="loop" value="0" /> 
				<param name="src" value="./download/file.php?id=2016" /> 
				<!--[if !IE]>--> 
					<object width="320" height="285" type="video/x-ms-wmv" data="./download/file.php?id=2016"> 
						<param name="src" value="./download/file.php?id=2016" /> 
						<param name="controller" value="1" /> 
						<param name="showcontrols" value="1" /> 
						<param name="showdisplay" value="0" /> 
						<param name="showstatusbar" value="0" /> 
						<param name="autosize" value="1" /> 
						<param name="autostart" value="0" /> 
						<param name="visible" value="1" /> 
						<param name="animationstart" value="0" /> 
						<param name="loop" value="0" /> 
					</object> 
				<!--<![endif]--> 
			</object> 
```

---

### Post by Yellow Pasque on 2010-11-07
> **shortmort37 said:**
> Not sure why that is so; do I need to resort to removing Totem from Ubuntu, in order for Chrome not to default to it?
You can just purge totem-mozilla package if you want to keep the standalone totem player. If mplayer plugin doesn't work, you can also try xine-plugin or mozilla-vlc-plugin.

---

### Post by anders_c_ on 2010-11-07
the mplayer plugin i was refering to was "gecko-mediaplayer", just as the name suggests it's written for gecko(firefox) but it might just end up working for chrome or chromium too.

---

### Post by shortmort37 on 2010-11-07
> **Temüjin said:**
> You can just purge totem-mozilla package if you want to keep the standalone totem player. If mplayer plugin doesn't work, you can also try xine-plugin or mozilla-vlc-plugin.

I purged the totem-mozilla package.  xine-plugin was already installed.  I installed mozilla-plugin-vlc (I think that must be it, didn't see any mozilla-vlc-plugin), shut down every Chrome instance and reloaded the page.  Where I formerly saw the totem player with controls but a black window, I now see nothing; although, there's space for a player.

Any more thoughts?

Dan

---

### Post by shortmort37 on 2010-11-07
> **anders_c_ said:**
> the mplayer plugin i was refering to was "gecko-mediaplayer", just as the name suggests it's written for gecko(firefox) but it might just end up working for chrome or chromium too.

It's already installed.  Still no vid.

Dan

---

### Post by shortmort37 on 2010-11-07
FWIW, Firefox is also still busted - but, in the same way it's always been; it displays "XINE" and "Buffering... 0%", but it's locked there (see attachment).

Yet, if I go to the page with a Windows machine, it plays fine.

BTW - here's the page:

[http://www.59sportfury.net/59forum/viewtopic.php?p=6992#p6992](http://www.59sportfury.net/59forum/viewtopic.php?p=6992#p6992)

Dan

---

### Post by anders_c_ on 2010-11-07
Opened the page in FireFox 4 from daily ppa on Maverick and it worked flawlessly, so just update =)

The About window said this:
Totem Browser Plugin 2.32.0
Browser Plugin using GStreamer 0.10.30

Edit: Chromium from daily ppa didn't work though, the plugin appeared but when i press play the icon just switches to pause and nothing happens.

---

### Post by shortmort37 on 2010-11-07
Well, this is taking me a bit far afield - I started off asking about why it doesn't work with Chrome.  Even so, I did the sudo apt-get-repository thing for the firefox ppa, installed every firefox 4.0 component I can find - yet, firefox still reports its at version 3.6.12.  Not sure what that's all about.

And it's still busted.  For both Firefox, and Chrome.

Seems to me there ought to be a way to diagnose why it's unhappy.

No?

Dan

---

### Post by shortmort37 on 2010-11-08
Bump?

---

