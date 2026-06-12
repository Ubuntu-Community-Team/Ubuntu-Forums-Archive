---
title: "Abstracted media server"
date: 2012-07-14
forum: Multimedia Software
---

### Post by freakalad on 2012-07-14
I've been using a series of different systems on a number of hosts on my network to achieve certain outcomes, but I've been thinking about rearranging my setup.

What I've got atm is:
* FreeNAS hosting my content
* XBMC as my HTPC - pretty spec machine, serving video up over HDMI & 5.1 surround sound through a 2nd soundcard to a relatively cheapish Logitech set
* MPD on a number of systems, including my HTPC. MPD does a much better job of serving up music that XBMC gets even close to
* We have a number of Android devices in & around the house, and I've been making use of a number of apps to drive my current systems: Coversal to send mpc (MPD client) commands over SSH (other Android MPD client apps all fail in spectacular fashion with large playlists), MediaHouse or UPnPlay as my DLNA client & MoboPlayer as the renderer

Recently I've been gifted a nice TV with native DLNA capabilities - this seems to be the way things are moving.

What I've been thinking is that I'd like to abstract these media services into a VM (KVM+libvirt) & then have my clients (TV, desktops, mobiles, etc) connect to it from anywhere on the local network.

The VM guest setup I'm envisioning is something along these lines:
* XBMC, serving up audio up via PulseAudio and/or GUI via SPICE (this might be a bit of a pipedream, but could be very cool if I slave a RasPi or Cotton Candy off it) - not a pressing priority for this setup right now
* MPD for music, serving up audio outputs over both PulseAudio & DLNA, so that I can get the same music stream coming from multiple clients, including my DLNA-capable TV (found [this reference]("http://askubuntu.com/questions/28039/how-to-stream-music-over-the-network-to-multiple-computers") of interest)
* As a lightweight alternative to using XBMC as the DLNA server, I'm considering running another (such as PSM, miniDLNA, Rygel, MediaTomb, Serviio, etc)

What I need some help with, for now, is setting MPD to output audio to multiple simultaneous streams/sinks, ie. to POSIX/Linux hosts running PA, but in particular I need it to output audio to DLNA, so that DLNA clients, such as my TV or Androids, can connect to the stream & play the same audio the rest of the PA clients are.

I'd also be interested in other novel & interesting ways that I can build on this system, and use this "virtual media center" for my media needs

---

### Post by m3topaz on 2012-07-15
I set up MediaTomb on Ubuntu as my kickaround media server. It works nicely - but if I recall correctly you need to have a user logged in to start the daemon, and you also might need to amend one of the config files to make it work with an out of the box DLNA client. I had to add a config line to MediaTomb in order to fully support a Samsung LED TV.

MediaTomb works without config change with the PS3. It also works with various clients on Android and iOS, including the Samsung DLNA renderers.

In terms of Ubuntu clients, I'm using unmodified Rhythmbox 2.96, which is current on Precise. It can 'see' uPnP servers natively, but is a little unstable if you bash it hard (e.g. shuffle + advance repeatedly).

For standards compliant DLNA source devices since added, everything else I've brought in just works with everything. For instance, Nokia N9, Nokia N900, Western Digital My Book Live.

For remotes, not much experience here - but the Android and iOS devices just work, I believe.

---

