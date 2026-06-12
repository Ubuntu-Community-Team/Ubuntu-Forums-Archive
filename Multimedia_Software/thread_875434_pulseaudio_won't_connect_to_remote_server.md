---
title: "pulseaudio won't connect to remote server"
date: 2008-07-30
forum: Multimedia Software
---

### Post by jeffchuck on 2008-07-30
I have pulseaudio set up on my Ubuntu machine, which I want to use as the client, and a Suse box, which I want to use as the server.

I've tried numerous ways to get pulseaudio on Ubuntu to connect to the other box, but nothing is working.  There aren't any errors generated, it simply connects to the local server, apparently without even trying the remote server.

I've tried using the GUI to set the default server using the format:
tcp:xxx.xxx.xxx.xxx:4712
(I've also tried port 4713, different sites list different defaults, and I'm not sure how to check)
I've also tried setting the default in /etc/pulse/client.conf

No matter what I do, when I load the pulseaudio manager through the GUI, it shows a connection to the local server.

Any ideas?

---

### Post by Ademan on 2008-10-03
I, too have been having trouble getting pulseaudio to connect to remote servers... however, if you use padevchooser, setup your remote server like so: [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup) and make sure the avahi/zeroconf module is installed... padevchooser should see your remote server (and at least spare you writing out the address by hand).  That's where *i* am at the moment, but it still refuses to connect...

---

### Post by confy on 2009-04-26
Does anyone has make this to work? 
I'm also interested ...

---

### Post by Fragger on 2009-04-29
I know it has to do with coping .pulse-cookie from the server to the client so the client has authorization to connect or the server needs to be configured to not require authorization.

Lets see here:
.pulse-cookie should be located in /var/run/pulse/.pulse-cookie or ~/.pulse-cookie on the server and then should be copied to ~/.pulse-cookie on the client.

---

