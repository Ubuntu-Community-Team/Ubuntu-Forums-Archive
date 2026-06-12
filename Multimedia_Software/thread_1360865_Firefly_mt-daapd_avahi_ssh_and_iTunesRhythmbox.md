---
title: "Firefly mt-daapd avahi ssh and iTunes/Rhythmbox"
date: 2009-12-21
forum: Multimedia Software
---

### Post by burgundy on 2009-12-21
I've looked around and see various people's problems, but so far nothing seems to work.

I'm trying to use an ssh tunnel & avahi broadcast to share my music with myself over the internet.

Right now both iTunes/Rhythmbox automatically 'see' my music share without me doing anything but I'm getting a "Could not connect to shared music Cannot connect to destination" with Rhythmbox and a connection error -3260 with iTunes.

The Windows firewall is off on the windows machines and as far as I can tell this Ubuntu 9.04 has no active firewall.

I can put [http://ubuntu-desktop:3689/index.html](http://ubuntu-desktop:3689/index.html) into Firefox and see my Firefly server configuration.

I need ideas for why the default initial startup of Rhythmbox doesn't work but the 2nd try does.  If I can get Rhythmbox to work out of the box, iTunes will probably work as well.

I can "Connect to DAAP share..." with Rhythmbox and create a share that shows up as "ubuntu-desktop:3689" and that works, but then I have two Shared listings.  ubuntu-desktop & ubuntu-desktop:3689.

If all I wanted to do was use Rhythmbox I would be done, but the whole point of using mt-daapd was so I could connect to my shared music with iTunes.

This is the afpd.service XML file being used by my local Ubuntu 9.04 machine:

<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
<name replace-wildcards="yes">%h</name>
<service>
<type>_daap._tcp</type>
<port>3689</port>
<txt-record>txtvers=1</txt-record>
<txt-record>iTSh Version=131073</txt-record>
<txt-record>Version=196610</txt-record>
</service>
</service-group>

---

### Post by burgundy on 2009-12-21
OK, while working on my own problem, I discovered that [http://ubuntu-desktop:3689/index.html](http://ubuntu-desktop:3689/index.html) doesn't actually work on the Windows machines running iTunes (only the Ubuntu 9.04 running the avahi service & tunnel).

So I'm guess I need to setup some kind of proxy server on the ubuntu machine to resolve the DNS to for other computers on the network.

I've never setup any sort of proxy server for anything, so this is a totally blind guess.  My search for answers continues...

---

### Post by burgundy on 2009-12-21
After doing more experimentation on the Windows machine I feel like my question has become more of a general networking issue.

By default, Ubuntu (like operating systems) leaves ports closed, so when I create my SSH tunnel to a local port, other computers still can't just type in the IP of this local machine at that port and make a connection.

So, how do I tell Ubuntu that I want outside computers to access a port that isn't a service being run on the local machine?

When I do a port scan on my Ubuntu system IP, 3689 isn't open.  How do I just 'open' this port to work with my SSH tunnel?

this is the SSH tunnel command I'm using:
ssh -C -L localhost:3689:localhost:3689 [email]username@somewhere.org[/email]

---

