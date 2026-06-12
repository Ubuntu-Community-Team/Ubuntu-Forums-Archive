---
title: "Does this stream work for you?"
date: 2007-01-13
forum: Multimedia &amp; Video
---

### Post by cookfromfrozen on 2007-01-13
Hi

I've been battling with streaming WMA / ASF / whatever for a while now, I have all the codecs installed that are suggested in the multimedia codecs section of ubuntuguide.org (including w32codecs) and I still can't get streaming WMA / ASF for work.

Shoutcast / streaming MP3 etc in streamtuner works, and playing WMA files generally work, but streaming ASF doesn;t.

As a test, can anyone get this  stream to play:

**[THIS ONE]("http://a814.l1977144512.c19771.g.lm.akamaistream.net/D/814/19771/v0001/reflector:44512.asf")**

( It's KFI AM 640's stream BTW )..

I've tried totem, VLC, Rhythmbox, XMMS.  None of them play it.  

VLC gives me this error to the terminal
```

[00000341] main input error: no suitable access module for `mms://a814.l1977144512.c19771.g.lm.akamaistream.net/D/814/19771/v0001/reflector:44512.asf'

```
However I definitely have the w32codecs installed.  I know the stream works in XP.

thanks!

---

### Post by gilgongo on 2007-01-13
It works for me (using freshly installed Edgy and having used Automatix to install all the codecs). I just clicked on the link using Firefox which (I assume) used the plugin that's associated with asf - not sure what that is though.

---

### Post by Yleeyas on 2007-01-13
Hello cookfromfrozen,

Similar to gilgongo, my FF (1.5.0.9) kicks into the Mplayer plugin and plays the stream fine. From my 'about plugins' page it looks like .asf file type is handled by the Mplayers 'Windows Media Player Plugin', the mimetype is listed as 'video/x-ms-asf'.

Hope that helps some :-| 

Yleeyas

edit: By the way, it is the KFI radio stream (not video), and I'm listening to some tech talk Q&A show :)

---

### Post by cookfromfrozen on 2007-01-13
Thanks for all the replies.  I tried it in Mplayer and it works through the GUI and the terminal e.g. like this

```

mplayer http://a814.l1977144512.c19771.g.lm.akamaistream.net/D/814/19771/v0001/reflector:44512.asf
```

However, it doesn't work in Totem, Rhythmbox or VLC.  Is this the case with you guys too?

thanks again

---

### Post by Yleeyas on 2007-01-13
Hi cookfromfrozen,

Well I can't get it to work in either totem or rythmbox; they both give me this error:
```
No URI handler implemented for "mmsh".
```
This is not the error you originally quoted is it.  I'm gonna look into this error abit more.

When I try XMMS, it looks like it's trying to connect but is getting rejected with no errors reported?

Sorry I can't be of more help.](*,) 

Just to be on the safe side, you might want to confirm that you have all the required codecs from the 'restricted formats' page (gstreamer0.10-ffmpeg seems to have the asf stuff, as do the xine libs):-k

Later

Yleeyas

edit: don't have VLC so couldn't check, sorry.

---

### Post by cookfromfrozen on 2007-01-14
Thanks for all the help so far.  This is definitely a strange one.  It seems the codecs are installed since it plays in mplayer, but nothing else seems to want to play it.

Also I don't get the error about MMSH when I try totem or Rhythmbox.  Totem connects and displays "Buffering..." as if it is going to play, but then just stops.  XMMS seems like it connects and is about to play but then stops too.

I'll keep trying :)

---

### Post by LaneLester on 2007-01-17
> **cookfromfrozen said:**
> Thanks for all the replies.  I tried it in Mplayer and it works through the GUI and the terminal e.g. like this
I'm new to mplayer and couldn't figure out how to play it through the GUI. But using your code in the terminal worked fine.

And like you, I can't get it to play through Firefox. Totem gives me an error message.  And VLC won't play it, either.

And in FF 2.0.0.1, I can't find the plugins list!

Lane

---

### Post by Zer0Nin3r on 2007-02-01
> **cookfromfrozen said:**
> Hi

I've been battling with streaming WMA / ASF / whatever for a while now, I have all the codecs installed that are suggested in the multimedia codecs section of ubuntuguide.org (including w32codecs) and I still can't get streaming WMA / ASF for work.

Shoutcast / streaming MP3 etc in streamtuner works, and playing WMA files generally work, but streaming ASF doesn;t.

As a test, can anyone get this  stream to play:

**[THIS ONE]("http://a814.l1977144512.c19771.g.lm.akamaistream.net/D/814/19771/v0001/reflector:44512.asf")**

( It's KFI AM 640's stream BTW )..

I've tried totem, VLC, Rhythmbox, XMMS.  None of them play it.  

VLC gives me this error to the terminal
```

[00000341] main input error: no suitable access module for `mms://a814.l1977144512.c19771.g.lm.akamaistream.net/D/814/19771/v0001/reflector:44512.asf'

```
However I definitely have the w32codecs installed.  I know the stream works in XP.

thanks!

I'm getting the same problem here too with Totem & Firefox.  (I'm not liking Totem, and I'm not sure if there is a way to use Xine Movie Player like Totem)  Anyway, I'll try to stream from Netflix (watch previews) and I'll get a similar message.  No dice.  If you find out drop me a line.  I'll do the same.

---

### Post by ridgeland on 2007-03-07
I had the same situation of Firefox won't play the radio station but mplayer will from the command line.  
The problem is Totem.  The problem is Ubuntu tying Totem to the desktop.  The problem is Firefox's use of plugins and not letting the user manage them.
In Firefox I choose Edit->Preferences then in the pop-up Content->File Types [Manage].  This tells me there are only five files types with 'handlers' and asf is not one of them.  But researching I found I should enter the url:
about:plugins
Type that in exactly, without any www or http and it opens your local Firefox's list of plugins.  Many pages of file extensions are defined not just 5!  In one section I see that Totem controls asf files.  Go to Synaptics Package Manager and you'll find you cannot remove Totem without removing ubuntu-desktop!!!.  Ouch!

So change some things for Firefox.  First close Firefox.  I went to /usr/lib/firefox/plugins and moved all the libtotem files out of the plugins folder.  Like so:
$ sudo mkdir /usr/lib/firefox/totem_plugins
$ sudo mv /usr/lib/firefox/plugins/libtot*.* /usr/lib/firefox/totem_plugins
Firefox only refreshes its plugin list (cached) when a new plugin arrives so give it a new time-stamp to see, specifically the mplayer one.
$ sudo touch /usr/lib/firefox/plugins/mplayerplug-in.so
Now start Firefox and you'll have the *.asf location open with mplayer.  (imho you're better off without THAT radio station though)  Check the url about:plugins  again and you'll see Totem is gone :) and that asf is now enabled for mplayer.
If you want to keep some of the Totem plugins then read "about:plugins" carefully to see which one(s) to move, libtotem-gmp-plugin.* (miss-)handled the asf files.  Since you only moved the files you can always put things back the way they were.  The files are really just links.

For the techie folks, here are some interesting links about Firefox plugins:
[http://developer.mozilla.org/en/docs/Gecko_Plugin_API_Reference:Plug-in_Development_Overview](http://developer.mozilla.org/en/docs/Gecko_Plugin_API_Reference:Plug-in_Development_Overview)
[http://developer.mozilla.org/en/docs/NPP_SetValue](http://developer.mozilla.org/en/docs/NPP_SetValue)
If anyone can break through and give us an easy way to assign mplayer as the handler for asf files, please post more.

---

### Post by dumbbeatnix on 2007-03-24
Still doesn't work mate, still getting mmsh uri handler error.:popcorn: 

I have followed what you said and others.  I don't think there is a solution to this.

It seems like an ongoing basis for this problem.  If I find a work around I will post it.

Cheers
dumbbeatnix

---

### Post by ridgeland on 2007-03-24
G'day,
I'm using a backup copy of my Ubuntu partition.  It still had totem links for Firefox and when I tired the asf location it did not work.  I used copy and paste and copied the three terminal lines from my last post and now the asf works fine.  One assumption I did not state is that I'm using mplayer and w32codecs. 
When you go to
about:plugins
what do you find for the program that handles asf?  File name: mplayerplug-in-wmp.so?

---

### Post by wearekosh on 2007-03-24
Hi rigeland

Touching the firefox plugins worked for me - thanks - 
 
It seems moving the totem plugins and giving firefox a touchup has caused mplayer to play the videos in the web-browser - woohoo- no more white screen

thanks

---

### Post by manwe on 2007-03-29
I had a simialr problem listening to streaming radio. If you have the mplayer plugin installed you can simply remove the totem plugin without installing totem altogether.

sudo apt-get remove totem-mozilla


After that mplayer should handle mms and mmsh (I haven't specifically tried mmsh files though)

I too, was alarmed to find that to remove Totem you also had to remove ubuntu desktop.

manwe

---

### Post by Benbow on 2007-05-10
I am running feisty and no way could I get shoutcast radio stream to play, mp3's yes but no radio stream. An earlier posting on this thread suggested that firefox was to blame and not wanting to fiddle around with firefox I switched browser to konqueror - problem solved!!
As I use shoutcast quite a lot I will be sticking to konqueror for now.

---

### Post by ridgeland on 2007-05-10
I was so set with Firefox I had forgotten there were other browsers for Linux.  
I installed Konqueror and found I also needed kmplayer-konq-plugins.  Now I can play shoutcast in Konqueror via Mplayer.  

But that is no reason to punt Firefox.  In Firefox I listen to shoutcast using RealPlayer.  I have several RealPlayer Favorites set from shoutcast links so to play a favorite from shoutcast I don't need a browser at all, just RealPlayer then the Favorite (Bookmark).  I think I remember I could not set a favorite sometimes, depends on the host address I guess.

To setup RealPlayer I clicked a shoutcast "tune in" then "Save to Disk" the something.pls. Let it go for 30 seconds to have a file.  Then right click on that file and set properties to open pls files with RealPlayer and it was done.
To create a Favorite explore RealPlayers File -> Clip Properties -> Clip Source.

One nice thing about Linux is there are so many ways to do something.  I'll try Konqueror on my wife's PC for some sites she says don't work right.

---

### Post by grndslm on 2007-05-29
Yes guys, mmsh:// streams don't work for me either...tried everything short of moving the totem-mozilla plugins & touching the other files, but my mom found this lame station that won't play for her:

mmsh://cas-w.streamadz.com/cas_streamadz/2724_9337.geronmemday.wmv?info&adzID=35062&advertiserID=2724&publisherID=674&viewerID=8016273&d=72da3a9bff64db&MSWMExt=.asf

It's lame in more way than one!  ;)

mmsh sucks donkey balls.

---

### Post by ridgeland on 2007-05-29
YUCK!  :(
Steam Ads 
I wouldn't want to go there.

---

