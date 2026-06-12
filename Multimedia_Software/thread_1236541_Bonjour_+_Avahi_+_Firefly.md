---
title: "Bonjour + Avahi + Firefly"
date: 2009-08-10
forum: Multimedia Software
---

### Post by slm on 2009-08-10
This is for audio and running Ubuntu 9.04. 

A little strange.. it says that the webserver is already in use and failed, when I know it's not running (according to the mt-daapd logs in /var/log. Funny thing is, it works... other than that, so far, so good after reading this forum.. but now I have another issue racking my brain for 13 days now.

I am trying to get my Roku to remotely play from my firefly media server. I have made files in /etc/avahi/services folder ( thanks to another thread ;) ) I also running the avahi-discover program that shows that I am indeed broadcasting.. so this should work no? I have also setup and made sure that my router is forwarding 3689 correctly as well.

GRRRR... could it be it has something to do with the laptop local host IP not being found and only showing the mac addy?

here's some snippet from avahi-broadcast

A new main_window has been created
Browsing domain 'local' on -1.-1 ...
Browsing for services of type '_rsp._tcp' in domain 'local' on 4.0 ...
Browsing for services of type '_workstation._tcp' in domain 'local' on 4.0 ...
Browsing for services of type '_daap._tcp' in domain 'local' on 4.0 ...
Found service 'babesa-laptop' of type '_rsp._tcp' in domain 'local' on 4.0.
Found service 'Firefly on musicbox' of type '_rsp._tcp' in domain 'local' on 4.0.
Found service 'babesa-laptop [00:15:e9:12:30:88]' of type '_workstation._tcp' in domain 'local' on 4.0.
Found service 'babesa-laptop' of type '_daap._tcp' in domain 'local' on 4.0.
Found service 'Firefly on musicbox' of type '_daap._tcp' in domain 'local' on 4.0.
Service data for service 'Firefly on musicbox' of type '_rsp._tcp' in domain 'local' on 4.0:
    Host musicbox.local (192.168.1.2), port 3689, TXT data: []
Service data for service 'babesa-laptop' of type '_rsp._tcp' in domain 'local' on 4.0:
    Host babesa-laptop.local (fe80::215:e9ff:fe12:3088), port 3689, TXT data: []


here's the avahi service file

<service-group>
   <name replace-wildcards="yes">Firefly on musicbox</name>

   <service protocol="ipv4">
      <type>_daap._tcp</type>
      <port>3689</port>
      <domain-name>local</domain-name>
      <host-name>musicbox.local</host-name>
   </service>

   <service protocol="ipv4">
      <type>_rsp._tcp</type>
      <port>3689</port>
      <domain-name>local</domain-name>
      <host-name>musicbox.local</host-name>
   </service>


The only other thing *may* be doing wrong is maybe the way I call it from the preset list... IE In the preset list, I would put http:192.168.1.3:3689 ( I put 192 address as example IP only)



Is there any difference or headaches running this setup with 8.10? SHould i revert to that?

---

### Post by tgalati4 on 2009-08-10
I know that jaunty changed some ipv6 hooks so perhaps changing ipv4 to ipv6 in your avahi config file might do the trick.

Also, do you have a firewall running on the server machine?  If so, then you would have to poke a hole in port 3689. 

I would use a fixed IP address for the music server, that would help to reduce translation errors for the clients and router.  Put the servername and IP address in the client's /etc/hosts file.

Check /var/log for error files.  Perhaps there is a webserver error that is balling things up.  Sometimes it's a simple permissions error to write to a file.

---

### Post by slm on 2009-08-17
Just about had it. Things seem just about there, get no error in the logs anymore on start up except for an "unauthorized use" error. the server is up, the protocols are there, even itunes see the library but no songs show up in the list. I've made sure the permissions are as open as possible to the media directory and the songs. 
 
All I am looking to do, is to have Roku stream more than one song on a list remotely. The library shows up and plays fine on the local network, sees the library and all. If the darn thing would just process an .m3u list, would make my life stellar. The only other way that I know that the Roku will play more than one song is if I pre-record a bunch of songs into ONE big mp3. 
 
Anyone else have a soundbridge and manage to get it to stream remotely?
 
got no issues playing stream remotly from my shoutcast server on itunes, amarok, winamp,windows media player... arghhhh 
 
](*,)

---

