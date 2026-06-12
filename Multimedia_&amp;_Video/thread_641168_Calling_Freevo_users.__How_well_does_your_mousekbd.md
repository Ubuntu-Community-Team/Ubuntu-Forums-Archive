---
title: "Calling Freevo users.  How well does your mouse/kbd work to control freevo?"
date: 2007-12-15
forum: Multimedia &amp; Video
---

### Post by Mysticle31 on 2007-12-15
I have tried MythTV. However, I use my computer as a computer that is a DVR. Not on a TV, but on a couple of monitors.

I am looking for a program that has the option of being fullscreen on one monitor or being a window placed anywhere. That program also must have good mouse and keyboard support. Alla, I want to be able to go over to the window, click it, scroll up and down to flip though the channels in the OSD, and click again to change the channel. Or some sort of mouse interface. I tried to install freevo, but am having problems.

Will it even be any different than MythTV respect to mouse support? Is it worth the time to make it work?




This is the end of my question here is what I'm looking for if you have any suggestions.

Ultimately I'm looking for a program that has good mouse support, as above. In windows I could all of these:

1) webserver where I can log in and view the guide, set up or cancel a recording..etc.

2) the ability to transcode livetv or a recording over the internet. This never worked well on windows either, so it can be iffy on Linux too, new I know.

3) the ability to host a front end on my other computer over WIFI, sometimes it's nice to watch your favorite show outside.

4)

---

### Post by steefjeqv on 2007-12-15
Hi,

If you're talking about digital tv (DVB), then VDR is a possible solution.

VDR is a complete PVR and it has a large amount of plug-ins available.

For example :

1. VDR-admin : webserver
2. Not sure this is possible, but it may work using the streamdev plugin
3. The streamdev plugin can act as a server/client, enabling you to watch TV on any other VDR frontend (on the same network). You can also use Xine, VLC,.... as a local frontend.

Mouse+keyboard control is possible.

When you're using a budget TV-card (as most of us do) you'll need a plugin to process the mpeg2 signal as VDR was initially designed to be used with Full Featured TV cards.
I'm using the xineliboutput plugin to do this. This plugin can also act as a server, allowing you to stream TV over a network.

A few links :

[http://www.linuxtv.org/vdrwiki/index.php/Main_Page]("http://www.linuxtv.org/vdrwiki/index.php/Main_Page")

[http://www.cadsoft.de/vdr/]("http://www.cadsoft.de/vdr/")

Greetings,
Steven

---

### Post by Mysticle31 on 2007-12-15
Thanks for the recomendation.  It looks like that will do what I want. 

Installing it, however, is very much beyond me.

[http://www.linuxtv.org/vdrwiki/index.php/DEBIAN_Configuring_VDR](http://www.linuxtv.org/vdrwiki/index.php/DEBIAN_Configuring_VDR)

I get to this point.  ps fax | tail | less -S and have no idea what I'm looking at.

I use a PVR-150 too.  They have mpeg2 encoding, but I don't know what catagory it goes under.  I looked at them all, and didn't see it.

I don't even know where to get the plugin..
[http://www.linuxtv.org/vdrwiki/index.php/Xineliboutput-plugin](http://www.linuxtv.org/vdrwiki/index.php/Xineliboutput-plugin)

The homepage link is bad.  I could google it :P

---

### Post by steefjeqv on 2007-12-15
Hi,

VDR is available through the Synaptic Manager. Just use the search function in Synaptic.
The problem is that you need plugins which are not available through Synaptic.

It should be possible to get a PVR-150 working with VDR using the e-Tobi repositories.
This is basically a VDR package which is ready to use in combination with Debian.
As Ubuntu is Debian-based this package should work (not sure though).
It only works with the 32 bit version of Ubuntu and it will take some time configurating.

What you need to do is edit your sources.list.

Type in terminal :

sudo gedit /etc/apt/sources.list


Add the following line to your sources.list :

deb [http://e-tobi.net/vdr-experimental](http://e-tobi.net/vdr-experimental) etch base addons vdr-multipatch

Save and close your sources.list.


Then enter the e-tobi keyring by typing in terminal :

sudo gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys DB90D8FC306B6783
sudo gpg --armor --export DB90D8FC306B6783 | apt-key add -


Upgrade your system by typing in terminal :

sudo apt-get update
sudo apt-get upgrade


Now open the Synaptic Manager and search for "VDR".
You should now be able to find the AnalogTV-plugin (amongst others).
If that's the case, you're using the e-tobi version of VDR.

Install the following through Synaptic (for starters) :

- VDR
- xineliboutput-sfxe
- libxineliboutput-sfxe
- vdr-plugin-xineliboutput
- libxine-xvdr
- vdr-plugin-analogtv
- libxine1


Then you're ready to go configurating.


Greetings,
Steven

---

### Post by Mysticle31 on 2007-12-15
Awesome.  

I had some problelems with adding the second part of the key commands:
steve@Steve:~$ sudo gpg --armor --export DB90D8FC306B6783 | apt-key add -
gpg: error writing keyring `/etc/apt/trusted.gpg': file write error
gpg: can't open `/etc/apt/secring.gpg'
gpg: error reading `-': file write error
gpg: import from `-' failed: file write error

but remedied it with :
apt-get install e-tobi-keyring

Now I can't install any of the apps with the word xine in them.  Some of them rely on libxine-xvdr as a dependency.  And I tried to select just that by itself to see what the error was.  And I get this 
" Depends: libxine1 (<1.1.8) but 1.1.8-2ubuntu2~gutsy1 is to be installed"

I searched for libxine1 (tracing the problem) and find it's installed.

libxine1-x
libxine1-plugins
libxine1-misc-plugins
libxine1-gnome
libxine1-ffmpeg
libxine1-console
libxine1

All installed.

---

### Post by Mysticle31 on 2007-12-16
I re-formated and did it again, I got it all sucessfully installed this time.

How do I actually run the program?  I want to try and see if it displays TV or not yet.  So far all I can make is say is 
"...Using primary device"

---

### Post by steefjeqv on 2007-12-16
Hi,

I just read your last two posts.


First of all you're going to need a channels.conf. This can be created using a small program called w_pvrscan.
I've attached this application to this post. 
After downloading it, untar it and save the file to /usr/local/bin.
Type the following in terminal :

sudo w_pvrscan --plugin analogtv >> /var/lib/vdr/channels.conf
 

To start VDR, type the following in terminal :

sudo vdr-sxfe --post tvtime:method=scalerbob,cheap_mode=0,pulldown=0,use_progressive_frame_flag=1 xvdr:tcp://127.0.0.1


There may be an error mentioning "UTF-8".
If this occurs, you'll have to edit your /etc/default/vdr :

sudo gedit /etc/default/vdr

Add the following lines

LANG="c"
USER=replace this by your username


Greetings,
Steven

---

### Post by Mysticle31 on 2007-12-16
Does it change anything at this point if I tell you that I have set top box hooked to compisite 1 on my PVR-150 and I use an IRBlaster to control my Motorola  DCT-2000 Cable box? 

I can get the IRBlaster all up and working, I've done it many times. 

But can VDR use it?

Does that change the setup or running of VDR at all?

I hope to go try all this when I get off of work tonight :)

---

### Post by steefjeqv on 2007-12-16
Hi,

I'll have to look up if the IRblaster is recognized by VDR. I think it might work using the vdr-remote plugin.

I notice that you've mentioned the use of the composite-out of the PVR-150.
I'm not sure if it's going to be possible to use the tv-out of the PVR-150 together with VDR. This will only work with the PVR-250.
Instead you'll be using "xineliboutput" together with "analogtv" (or "pvrinput-plugin, see below).
The mpeg2 will be handled by your graphics card and cpu, so you'll need a working tv-out on your graphics card.

I also found a plugin which does the same as the "analogtv-plugin", specifically for the Hauppauge PVR.
It's called "Pvrinput-plugin". I don't know if it's included in the e-tobi repo's.
It should be easier to configure then "analogtv".

Something important I forgot to mention :
You need to have the ivtv drivers for your PVR150 installed.
They should be available through Synaptic.

Greetings,
Steven

---

### Post by Mysticle31 on 2007-12-17
I'm using the composite in.  I have no need for any sort of outputs for TV except on my AGP card :P

I just don't use the tuner, since I have it hooked to the cable box.

I'll have to try pvrinput-plugin if I can find it.  I've had a hell of a time with this thing. 

Well, I've had a crash course in Linux the past month! :guitar:  

Thanks for you help, btw!

---

### Post by steefjeqv on 2007-12-17
Hi,

This link should give you some more info :

[http://www.linuxtv.org/vdrwiki/index.php/Pvrinput-plugin]("http://www.linuxtv.org/vdrwiki/index.php/Pvrinput-plugin")

The analogtv-plugin works with composite in.
As the Pvrinput-plugin has the same function it should support composite in too.

Let me know how things work out.

Greetings,
Steven

---

