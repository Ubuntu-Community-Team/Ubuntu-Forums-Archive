---
title: "Audacious Wiki-Lyrics Plugin"
date: 2009-11-27
forum: Multimedia Software
---

### Post by Nameless_one on 2009-11-27
Hello. I have written a small Audacious plugin to interface with [this Amarok lyrics script]("http://www.kde-apps.org/content/show.php?content=35151"). It is still in beta stage, but I think it's ready for an initial release. 

It works with Audacious 2.3alpha, and at least version 0.13.4 of the Amarok script. However, the script's interface shouldn't really change, so I bet it will work with future versions, too. 

If needed, I can provide a version compatible with 2.1, as well. Please send me a PM. 

Right now, I can offer instructions to compile from source, but if anyone wants to help me make a .deb, I might get around to doing it. So, to install it, you: 

[LIST=1][*]Install Ruby (unfortunately it's a dependency)
[*]Download the [Wiki-lyrics Amarok script](http://www.kde-apps.org/content/show.php?content=35151) (clickable link), and extract it somewhere. Remember where. 
[*]Download the latest audacious and audacious-plugins (and extract them)
[*]Download the plugin source (it is attached to this post), and extract it into the audacious-plugins/src/ folder. 
[*]Edit the line: 

```
GENERAL_PLUGINS="song_change alarm skins vfstrace gtkui"
```
in the audacious-plugins configure script, to 

```
GENERAL_PLUGINS="song_change alarm skins vfstrace gtkui wikilyrics"
```
(it's line 7,487 or so, look for the line GENERAL_PLUGINS).
[*]Install audacious and audacious-plugins via the normal method (configure, make, make install). You don't actually need to install audacious, but if you don't have the latest version installed, I suggest you do, so that audacious and audacious-plugins are in sync (otherwise audacious might not work, or the plugin might not). 
[/LIST]

To enable the plugin, go to Preferences > Plugins > General, and click the checkbox (it should have appeared under the name "Wiki-lyrics script integration". If not, something went wrong). Then, open the preferences window. Fill in the full path to the wikilyrics.rb script (it is under wiki_lyrics/cli/ in your installation of the amarok script), and click Apply (the one near the text entry). 

Then, choose the sites you want to retrieve lyrics from. I suggest DarkLyrics,Lyriki and LyricWiki for starters, then you can experiment and make your own list. You can also change the order the sites will be queried, higher in the list means queried first. Then click on Apply (the one close to the sites list). Close the window. 

An empty window should have appeared. Start a popular song, and the lyrics will probably appear inside the window (or "Lyrics not found."). That's it. 

Note that the plugin saves the window size and location when the program closes, so resize the window and place it where you like. I also suggest you restart the program for the size and position to be saved, as a crash will prevent it.

NOTE: Right now, the plugin causes audacious to crash when run from Gnome's "Run progam..." dialog (at least in my PC). Please try whether this happens to you, and wether running audacious from the command line solves this. I have no idea why this should happen (it is extremely unexpected), but it will probably be resolved in some later release. 

Also note that this plugin isn't in any way close to working as expected. I hope it will some day. Any comments and feedback appreciated. 

**Known issues:** 
[LIST][*]not running from command line will cause Audacious to crash when the plugin is active
[*]Non-ascii chars in titles or artist names might cause audacious to crash (but mostly don't)
[/LIST]

UPDATE: Now under the GPL. 
UPDATE 2: Updated for 2.3alpha.

Screenshot: 
[[IMG]http://img214.imageshack.us/img214/7639/wikilyrics.th.png[/IMG]](http://img214.imageshack.us/i/wikilyrics.png/)

(if I have to move this to a more suitable forum, please tell me)

---

### Post by moopha on 2010-02-02
How can I use this script width my music site [Taylor Swift Lyrics]("http://www.taylor-swift-lyrics.net") ? 
My site is nothing fancy, mainly hosting a list of songs, lyrics of Taylor (and few music videos).
It's built in PHP w/MySql

---

### Post by Nameless_one on 2010-02-17
You'd have to write a ruby script that parses your site's lyrics pages, or convince the author of the Amarok ruby plugin that I use, to write one for you. None of these is very practical, I am pretty sure that the sites the plugin is currently using have all Taylor Swift lyrics.

---

### Post by Neologist on 2010-05-31
"and extract it into the audacious-plugins/src/ folder."

Oh, I cannot find it!!

Sorry, I'm pretty stupid at this. Can anyone be more specific?

---

### Post by Nameless_one on 2010-06-01
Notice the third step: 

> 3. Download the latest audacious and audacious-plugins (and extract them)

By that I mean download the source of the latest versions of audacious and audacious-plugins (you should find them [here](http://audacious-media-player.org/)). You extract these to a folder of your choice. 

Now, under the folder into which you extracted audacious-plugins, there must be a folder named 'src' (ie source). That's where you should extract my plugin. 

Note that you are compiling audacious from source, which requires some experience. Maybe you should follow a step-by-step guide to compile audacious from source without the plugin first, to get the hang of it.

---

### Post by Neologist on 2010-06-06
Thank you, I got it now.
But I couldn't do it anyway. When I'm going to install Audacious, it asks for "zlib", and everytime I try to install it my Ubuntu stops working. I tried three times, and it happened the same thing: first, Synaptic loads but doesn't open; later, I try to end the session or reinitialize the computer, but it never comes back again. :(

The same thing happens when I try to install Mplayer via command, because it asks for Zlib too. So I have to install it by Synaptic. As you said (if I got it right), Audacious must be installed via command. Therefore I'm not able to use your plugin.

But thanks anyway, I really wish I could use it. And thank you for your attention and for your explanation. 

I'm sorry for the stupid questions and mistakes, that's my first week on Linux. And sorry for my poor English too. :P

Bye! o/

---

### Post by Nameless_one on 2010-06-06
It seems you have a bigger problem with your Ubuntu installation. You probably mistakenly did something very bad :) I suggest you either reinstall Ubuntu or start a thread on these forums to ask for someone's help. 

If you ever solve your problem, you are welcome to come back :) I think I might have a .deb for my plugin so that installation is easier this time! Cheers. :)

---

### Post by Lord93 on 2011-08-24
Hi! It's the only script I found for my Audacious 2.3 (Ubuntu 10.04), so I compiled it, and it crashed Audacious after some trying to play with "Segmentation found". After some debugging I found that strlen function is involved. In fact you must use g_utf8_strlen instead of strlen everywhere, to support utf8.
Thank you for the code!

---

