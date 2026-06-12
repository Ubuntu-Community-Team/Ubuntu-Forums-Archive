---
title: "Installing Plex Media Server"
date: 2017-09-10
forum: Multimedia Software
---

### Post by MOGuy78 on 2017-09-10
I am wanting to set up a media server, and after looking at different ones, I have decided to use Plex.  To understand the process, I've looked at quite a few videos
from Youtube, and as expected, in all of the tutorials it shows how to install the Plex Media Server app.

But in some of the tutorials, it also shows the Avahi application being installed. What is the purpose of this app; and why is it installed on some of the videos and
not on others?

Also, I am using the Server version of Ubuntu, and therefore I don't have any desktop GUI installed, only the Command Line.

---

### Post by TheFu on 2017-09-10
Avahi is a service announcement for the network.  I avoid it, mainly because it had some terrible issues in the past.  On a correctly setup network, it isn't needed at all.  On a network that is 100% DHCP, it can be helpful.

If your server has a static IP and all the clients can easily find it by name (internal DNS or /etc/hosts), you don't need avahi.

---

### Post by Morbius1 on 2017-09-10
Just curious. What avahi application? Are you talking about avahi-daemon itself?

I wish I could state this as an absolute but I think Ubuntu Server installs it by default. Ubuntu desktop certainly does as do most if not all other desktop Linux distros. By one name or another Linux, macOS, and now even Windows 10 can use it to find and connect to each other.

---

### Post by TheFu on 2017-09-10
None of my 14.04 or 16.04 Ubuntu servers have avahi installed.

---

### Post by MOGuy78 on 2017-09-11
Sorry, the avahi-daemon itself is what I was asking about.  I am using Ubuntu Server 14.04, and no, it was not installed by default.

I do have a Static IP address set up to use with my server.  I have 2 network cards installed, and I've got both of them set up to run on startup.  Just to be for sure they WERE both running, I used the ifconfig command, and it displayed both IP addresses; the Static IP I set up to use with my media devices (Roku, PS3, and a couple computers), and the DHCP connection I'll use to connect to the internet.

---

### Post by TheFu on 2017-09-11
Please post the output using "code tags" for **ifconfig** and **route -n**.
You shouldn't need to use 2 cards, BTW.  This assumes the Plex and other computers are connected to the router.  "[KISS]("https://en.wikipedia.org/wiki/KISS_principle")" Why make it more complicated than necessary?

---

### Post by Morbius1 on 2017-09-12
While doing something else I stumbled upon this from :  [https://www.plex.tv/blog/the-plex-penguin-friendly-media-server/](https://www.plex.tv/blog/the-plex-penguin-friendly-media-server/)
> The only known external dependency it has is [Avahi]("http://avahi.org/"),  which is required to provide
 Bonjour-based discovery. Unless you  install and run Avahi, the server will not show up
 automatically in all  Plex clients.
The key word there is "automatically".

First of all Bonjour is an Apple thing and in Linux it's called Avahi. Having avahi-daemon running by itself won't do anything automatically. All it does is allow another Bonjour / Avahi / Win10 machine access to it by using it's host name with a .local attached to the end. But what plex does is create an avahi / plex service announcement file ( **plex.service**        ) that apparently looks something like this:
> <?xml version="1.0" standalone='no'?><!--*-nxml-*-->
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
    <name replace-wildcards="yes">%h</name>
    <service>
        <type>_plexmediasvr._tcp</type>
        <port>32400</port>
    </service>
</service-group>

As I do not use plex all I can do is use Samba as an analogy. If I set up a samba server with avahi-daemon running the clients to this machine cannot "discover" it automatically unless I create a samba.service file in /etc/avahi which looks a lot like the one above except the <type> and <port> are different.

Once that is in place I can open the file manager in Linux > Network and see the Samba Server listed. In macOS it gets even better since the Avahi announced Samba server will automatically show up under Shared on the left side panel of the mac file manager.

---

### Post by TheFu on 2017-09-12
I do run Plex Server on an ubuntu 14.04 server install. It doesn't have avahi installed or running.

This is no different than using ssh, sftp, or samba on a network.  Clients need to know the IP/DNS for the server. That should be expected.

I don't use official plex clients - don't like their interfaces.  Using Kodi or other DLNA controllers and renderers means having to manually enter the plex server hostname (I have internal DNS) 1 time on the controller.  That's it.  Not a big deal, especially if your network handles name resolution correctly already.  Why NOT have that setup?  Every networked client knows about DNS. All of them.  Most home routers will provide this with just a little setup.  In some, it is automatic with DHCP reservations.

 On a network that has multiple people, advertising plex may not be desirable.  It isn't security, but it is a start.  Add in an outbound firewall rule if you want to block unwanted clients.  Plex doesn't have any security on the LAN, after all.  No DLNA servers do.  The market decided any security for those services was too hard for grandma and sales.

---

