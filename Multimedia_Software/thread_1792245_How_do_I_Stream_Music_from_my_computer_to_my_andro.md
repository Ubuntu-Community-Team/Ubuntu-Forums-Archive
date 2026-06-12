---
title: "How do I Stream Music from my computer to my android device"
date: 2011-06-28
forum: Multimedia Software
---

### Post by h4x0l2 on 2011-06-28
I have found countless things that claim to be able to do this for free. I basically want to use my computer's music on my android device while I am not home. Plug in the headphones, press play, and listen to it. Essentially, turning my own computer into my own personal "cloud streaming service" like Ubuntu One. 

I have gotten none of them to set up properly. any help would be greatly appreciated. I don't want to buy a large microSD card if I don't have to, i'd rather just stream it to my phone from my PC. 

I don't want it to be WIFI only, I need it to work on my normal data connection. Any Ideas?

---

### Post by jocko on 2011-06-28
I'm pretty sure vlc can stream music (but I can't help you with the "how"), and there are some apps in android market that you can use to listen to the streams (just search for "vlc" to find a few).

Seems like all the apps I can find costs money, but there should be free (but limited functionality) versions that you can try before you decide to buy anything...

I guess the main thing is to figure out how to set up vlc (or any other program) to send the stream, and to map the ports in your router to be able to connect from an external network.

---

### Post by aeiah on 2011-06-28
we use music player daemon, and mpdroid. you can control the music and have it play on the main computer, or have it streamed at a click of a button. we only use it on the LAN, but providing your phone's connection is good enough, it will work the same over the internet (once you've opened ports etc)

in the mpd config file (/etc/mpd.conf) you can turn on http streaming, set the port, and set the quality of the mp3 or ogg stream. i dont know if mpdroid accepts ogg streams though. ive just used it with mp3 streams.

perhaps mpdroid has good buffering options for internet use, but it might not :/

---

### Post by h4x0l2 on 2011-06-28
I tried to set up mpdroid, the app on the phone is easy, its setting it up in ubuntu that is the real killer, looks like the instructions are written in gibberish to me. How did you set it up? I think i might be able to figure out the port forwarding/security for 4g stream with no issue...

---

### Post by aeiah on 2011-06-29
i pretty much just installed mpd (the bit that actually plays the music and catalogues the music library) and gmpc for displaying locally.

you need to edit the config file located at /etc/mpd.conf as root - things like http stream (just by uncommenting it), audio card (if you want local playback too, or for testing first), music directory location etc. 

note that old documentation talks about setting up an icecast server to stream your music. this isnt necessary now because http streaming is built in, and is configurable in the audio interface section of mpd.conf

maybe you'll have to do something special for pulse audio, but since you're primarily using this for streaming i wouldnt worry too much.

mpdroid doesnt stream by default, it only controls the playback, but enabling streaming is just a tickbox in its settings area

---

### Post by h4x0l2 on 2011-06-29
> **aeiah said:**
> i pretty much just installed mpd (the bit that actually plays the music and catalogues the music library) and gmpc for displaying locally.

you need to edit the config file located at /etc/mpd.conf as root - things like http stream (just by uncommenting it), audio card (if you want local playback too, or for testing first), music directory location etc. 

note that old documentation talks about setting up an icecast server to stream your music. this isnt necessary now because http streaming is built in, and is configurable in the audio interface section of mpd.conf

maybe you'll have to do something special for pulse audio, but since you're primarily using this for streaming i wouldnt worry too much.

mpdroid doesnt stream by default, it only controls the playback, but enabling streaming is just a tickbox in its settings area




Thats where I am getting lost, I have no idea what I should uncomment and what to leave. I'm still relatively new to the conf files.

---

### Post by mpiter on 2011-07-18
First of all, how to remotely control your MPD server with MPDroid to play music on your computer. You just need to change a few lines of [COLOR="Blue"]/etc/mpd.conf[/COLOR].  First, where your music is stored.  For example:

  [INDENT]music_directory                "/home/mpiter/Music"[/INDENT]

Second, comment out a line to avoid many connection problems:

  [INDENT]#bind_to_address               "localhost"[/INDENT]

Third, to be able to remotely change the volume on your computer:

[INDENT]mixer_type                     "software"[/INDENT]

You should be all set to remotely control with MPDroid your MPD server playing music on your computer.

If your computer does not play music when you request it from MPDroid, check that the lines of [COLOR="blue"]/etc/mpd.conf[/COLOR] that correspond to your audio daemon are commented out.  For example, I use ALSA so I commented out those lines in [COLOR="blue"]/etc/mpd.conf[/COLOR]:


[INDENT]# An example of an ALSA output:
#
audio_output {
	type		"alsa"
	name		"My ALSA Device"
	device		"hw:0,0"	# optional
	format		"44100:16:2"	# optional
	mixer_device	"default"	# optional
	mixer_control	"PCM"		# optional
	mixer_index	"0"		# optional
}
[/INDENT]

Second, how to stream music to your android device from your MPD server.  You just need to uncomment the hppd lines in /etc/mpd.conf:

[INDENT]
#
# An example of a httpd output (built-in HTTP streaming server):
#
audio_output {
	type		"httpd"
	name		"My HTTP Stream"
	encoder		"lame"		# optional, vorbis or lame
	port		"8000"
#	quality		"5.0"			# do not define if bitrate is defined
	bitrate		"128"			# do not define if quality is defined
	format		"44100:16:2"
}
[/INDENT]

I use mp3 instead of vorbis.  You must either set [COLOR="Blue"]quality[/COLOR] or [COLOR="blue"]bitrate[/COLOR], not both.  Be careful with [COLOR="blue"]bitrate[/COLOR].  If you have a fast connection, you can use 320 for the highest possible quality.  If you work with a poor connection or if you use 3G, choose a lower value.  Of course, be specially careful with 3G if the amount of data that you can download each month is limited.  If I remember well, 9 hours of music at 128  eats 500 MB.  For [COLOR="blue"]format[/COLOR], 44100:16:1 is the usual setting to create a mono from a stereo channel.  I am not sure that using a stereo (2 replace 1 at the end of the variable) is a good idea.

You can have many details at [http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki]("http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki").

---

