---
title: "GStreamer problems in Ubuntu Studio 7.04."
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by dysonsphere23 on 2007-11-01
Hello,  I have posted these problems on other threads without any replies, perhaps it isn't reaching the right folks:

I am running Ubuntu Studio 7.04.

Everything was working fine (for over a week since install) then I shut down my laptop after work then restarted at home.

Problem 1.  Gnome volume control won't work, still after start again this morning. The sound card is functional, I am getting sound, but when I try to open the volume control from the pannel I get that same message:

"No volume control GStreamer plugins and/or devices found."

and

"The volume control did not find any elements and/or devices to control. This means either that you do not have the right GStreamer plugins installed, or that you do not have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

I can control volume using the ALSA mixer though.

In Add/Remove programs I have all the GStreamer stuff installed as explained in the sticky of this section.  I tried reinstalling all the gstreamer stuff from Symantec and still nothing.

I can start and stop ALSA in the comand line.

Problem 2. Exaile player won't start since this problem. When I try opening in terminal it gives some output about not finding playbin. Tried uninstall and reinstall, no help.

Sound (MP3/streaming) and video files (AVI/mpeg/streaming)  work fine in VLC player.

Problem 3.  DVD won't play in Totem, get the message:"Totem could not startup. Failed to create a GStreamer play object. Please check your GStreamer installation."

If I try to open the disc using VLC it just doesn't play.

Thanks in advance for any advice/insight.

---

### Post by Quintus Maximus on 2008-04-29
I've got the same problem.
Started in ubuntu 7.10 hoped it would be fixed when i upgrade to 8.04 still nothing. 

The gnome volume control doesn't work and the totem player doesn't work with those Gstreamer errors.

Kaffeine on the other hand works fine. Can change the volume using the alsamixer or the Gnome Alsa Mixer.
So if you want to play DVD's I recommend you try kaffeine.



Also I noticed that if kaffeine is running and playing audio, no other programs such as flash thingies running in firefox can produce sound. As soon as kaffeine is shut down the audio of this other app kicks in.

A solution would be most helpfull. 
And no it's not because I as user no longer belong to the audio group.

---

### Post by Quintus Maximus on 2008-04-29
Just found this thread:
[http://groups.google.com/group/gsb-users/browse_thread/thread/33aec76614f41c02](http://groups.google.com/group/gsb-users/browse_thread/thread/33aec76614f41c02)

They seem to be on the way of finding the problem. Something in the gstreamer library that doesn't seem to be installed correctly.

---

### Post by Quintus Maximus on 2008-04-30
So I've fixed it now, by compiling the entire Gstreamer thing from source.
When you run ./configure in the gst-plugins-base-10.x, gst-plugins-bad-10.x, gst-plugins-good-10.x and in gst-plugins-ugly-10.x. It will say which plugins will be installed and which won't be. 

When you study the output the plugins that won't be installed are probably missing some libraries, so by installing these libraries and running ./configure again, these plugins will now be installed.

Took me a couple of hours to find and install the needed libraries.

when you got everything

./configure
make
sudo make install

in all gst projects.


Hope this helps.

---

