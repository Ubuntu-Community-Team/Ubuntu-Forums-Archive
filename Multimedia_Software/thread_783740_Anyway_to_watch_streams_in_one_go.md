---
title: "Anyway to watch streams in one go?"
date: 2008-05-06
forum: Multimedia Software
---

### Post by westyonfire on 2008-05-06
Hi,
I have a pretty slow internet, and I like to watch movie trailers on apple trailers from time to time BUT my internet is soo slow that it stops every few seconds. Is there a way to let the movie load whilst on pause and then let in play in one go? any help would be veerrry appeciated.

oh and im currently using the totem/mplayer plugin on firefox.

---

### Post by steefjeqv on 2008-05-06
Hi,

You can enable and enlarge the cache size of Mplayer :

Just start up Mplayer, right-click on it. Choose "Preferences" in the menu. Then click on the "Misc" tab and enable and enlarge the cache size.

Greetings,
Steven

---

### Post by westyonfire on 2008-05-06
thanks for the reply,

...I think I've mixed the players up. Is Mplayer the same as Totem? I have totem and I cant find the preference menu you are talking about...

---

### Post by steefjeqv on 2008-05-06
Hi,

I don't think they're the same.

You can install mplayer and the mplayer-mozilla-plugin with Synaptic.

Then you've to change the plugin preferences in Firefox.
You can do this in the preferences menu (applications) of Firefox.

Greetings,
Steven

---

### Post by westyonfire on 2008-05-06
hey,
ok i installed the real mplayer. Couldn't find mplayer-mozilla-plugin in synaptic but found 'mozilla-mplayer' instead so i installed that. I then went to the Firefox Edit>Preferences>'Content' tab then clicked 'Manage' under the  'File Types' sub menu. I see that quicktime trailers are .mov files but theres no .mov under this menu so I instead tried to change the way firefox handled QT and QTL files but i couldn't change the plug-in from Quicktime plug-in 6.0/7. Any ideas? Firefox is still playing the trailers in totem through Gstreamer it seems...any ideas?

---

### Post by steefjeqv on 2008-05-06
Hi,

You can remove the totem-mozilla-plugin through synaptic.
Only remove the mozilla plugin because Totem is integrated deep into Ubuntu.
Removing Totem completely can get you into trouble.

This should enable the mplayer-plugin.

Greetings,
Steven

---

### Post by westyonfire on 2008-05-06
Oops. I had just removed all of totem before I read your post. I have now reinstalled it, but without the firefox plug-in. I went to play a quicktime trailer and now xine is playing it, theres no progress bar and play button and its stil stopping every few seconds...

---

### Post by steefjeqv on 2008-05-06
Hi,

Type the following in your web adress bar :

aboutplugins (put : between about and plugins, no space bars) (if i try to do this in this post I end up with a smiley instead of :)

This will show you the plugins installed on Firefox.

Totem should be gone. There should be mplayer-3.50 and also a quicktime plugin called .

Mark QuickTime Plug-in 6.0 / 7 in your firefox preferences.

Restart firefox and now mplayer should work.

Greetings,
Steven

---

### Post by westyonfire on 2008-05-06
Hi steefjeqv,
I got into the about:plugins and there is no more totem plugins but under the mplayerplug-in 3.40 section there is no .mov suffix. The .mov suffix is under the Xine Plugin. How do I move the .mov from xine to mplayer plugin?
thanks alot for your help by the way :)

---

### Post by steefjeqv on 2008-05-06
Hi westyonfire,

When browsing about:plugins, there should also be a mention of "QuickTime Plug-in 6.0 / 7". Details about this plugin should say something in the style of "filename:mplayerplug-in-qt.so".	

This plugin should be marked in "Firefox Preferences".


Greetings,
Steven

---

### Post by westyonfire on 2008-05-08
Hi Steefjeqv,
It says "filename:mplayerplug-in-qt.so" under the "QuickTime Plug-in 6.0 / 7" section as you say but now everytime I try to watch a video of any kind it shows an imagine of 'Xine' in the box where the video should be and then firefox freezes. I think I'm going to give up for now unless anyone else has any other ideas...

---

