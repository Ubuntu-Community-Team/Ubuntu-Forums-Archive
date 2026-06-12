---
title: "BBC iPlayer version of Flash"
date: 2008-12-31
forum: Multimedia Software
---

### Post by Stephen Shellard on 2008-12-31
> POST SCRIPT 7th February 2009 - Strongly suggest you divert to the following thread [http://ubuntuforums.org/showthread.php?p=6686395#post6686395](http://ubuntuforums.org/showthread.php?p=6686395#post6686395) in which I got some excellent assistance and answers to not just one but several problems associated with Flash not working, sound not working in utube not working, sound not working in BBC Radio iPlayer freezing up etc. etc.  


I have been struggling to get BBC iPlayer to stream radio and work with listen again (and have been trying to use information from forums to help me, but have found this hard to follow and at times contradictory. I have Hardy Heron 8.04 installed.

One thing I notice is that when the iPlayer consul loads up and I right click on it, it provides me with info on Flash Player 9.  However Synaptic tells me I have Flash Player 10 installed and does not list other versions.  

When I look at the add ons for Firefox [Tool/Add-ons/plugins] it lists Shockwave Flash 9.0 r152  and Shockwave Flash 7.0 r68, but no Flash 10. 

Other perhaps relevant information:  I have real player installed and have suceeded in using it with listen again, using links from the web page iPlayer Real Converter: [http://www.iplayerconverter.co.uk/](http://www.iplayerconverter.co.uk/) 

I also have Gnome MPlayer and Mplayer Move Player installed.

---

### Post by Stephen Shellard on 2009-01-02
See below

---

### Post by Stephen Shellard on 2009-01-02
I have now removed Flash 10 and whilst this has not resolved the above problem,  it has restored audio to utube - which was playing vision only.

This puzzlingly has removed Flash 9 from the Firefox plugins leaving only Flash 7.  (Synaptic tells me that I have Flash Plugin non free installed, and Adobe Flash Player plugin installer - it sounds like this should take care of things.)

I then found that when I clicked on a BBC listen live or listen again link, iPlayer would load and offer only the option of Totem Movie Player, but would then report an error (argument failure I think).  

I disabled relevant plugins from Firefox (Tools/Add-ons)  and this produced a sort of result in that iPlayer now loads when I click on a link, but asks that I install Real Player. 

Real Player is already installed (as reported above). However I followed the link provided and this produced a newer version of Real Player, though cautioned against installing it saying that the earlier version in my library might be better supported.  I pressed on and installed this latest version. (11 Gold).  However this has made no difference to iPlayer which continues to tell me to install Real Player.  

How do I communicate to iPlayer that Real Player is already installed?

Post script.  Real Player Gold was failing to play MP3 files, and in other ways performing oddly. I have reinstalled the earlier version.

---

### Post by Stephen Shellard on 2009-01-10
Finally got this to work, though I had to disable the Helix real player plugin on Firefox.  This I think is allowing one or other of the totem plugins to do its job (or perhaps a combination?),  

So under the tools/add-ons menu in Firefox I have enabled the following Totem 2.22.1  compatible plugins:  Quick Time; Browser plugin; VLC multimedia plugin; Windows media player plugin.  Also enabled is flash 7 and doubtless not relevant, but for the record, Adobe reader 8, Mozplugger, Default plugin;Demo print plugin; divX web player.

---

