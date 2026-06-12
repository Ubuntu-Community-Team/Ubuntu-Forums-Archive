---
title: "pulseaudio-dlna help needed"
date: 2017-07-07
forum: Multimedia Software
---

### Post by bill-lancaster on 2017-07-07
I have a lot of music on my Kubuntu 16.10 box and I'd like to play it on my Sonos system
I have read that sonos will recognize  a DLNA source.
I've installed pulseaudio-dlna but don't know where to go from here
Any help would be appreciated

---

### Post by RobGoss on 2017-07-07
Hello and welcome to the forums, You do realize 16.10 has reached it's end of life you might want to consider upgrading to a newer version of Ubuntu before you put much effort in to this problem

---

### Post by TheFu on 2017-07-07
> **RobGoss said:**
> Hello and welcome to the forums, You do realize 16.10 has reached it's end of life you might want to consider upgrading to a newer version of Ubuntu before you put much effort in to this problem

Definitely.  OP needs to install 16.04, unless reinstalling a new OS every 6 months is planned.  16.04 support is under 2021, so a better choice for any non-Linux-developer.
  
I scanned the Sonos site. Didn't see anything about DLNA there. If they supported it, it would be plastered all over the sales pages, right?

Everything that I've read (in 10 mins) says that Sonos only works with CIFS/Samba.  For audio and if you don't care at all about security, that is fine.

---

### Post by bill-lancaster on 2017-07-07
Thanks for all that advice.

I was encouraged by this post ```
https://en.community.sonos.com/advanced-setups-229000/sonos-dnla-compatible-and-or-sonos-plex-media-server-compatible-4747338
``` which indicates that some dlna sources might play on Sonos.

I'll install 16.04.

Also will look at the cifs/samba route

---

### Post by TheFu on 2017-07-07
I read that same post before posting and saw it completely differently.  

CIFS/Samba is just file sharing. It is based on the microsoft SMB/CIFS network sharing protocol. I consider it the lowest common denominator file sharing method. It is NOT secure - bad authentication, no encryption.  Since Windows has most of the desktops in the world, it is widely used.  BTW, it is also how all those recent viruses have been so effective the last 2 months that harmed the UK NHS and thousands of systems in the Ukraine.  CIFS connected storage was encrypted.

Be certain you have good backups. That is always smart.

---

### Post by pablosquared on 2017-07-07
I can recommend minidlna for Ubuntu, if your Sonos system does support DLNA.

---

### Post by SeijiSensei on 2017-07-07
> **pablosquared said:**
> I can recommend minidlna for Ubuntu, if your Sonos system does support DLNA.
I use minidlna as my DLNA server on Ubuntu, too.  pulseaudio-dlna appears to be an alternative server solution. However that doesn't answer whether the Sonos has a DLNA client.

Minidlna is really easy to set up.  You edit /etc/minidlna.conf and enter a couple of directives that point to where the media files are stored.  That's it.

---

