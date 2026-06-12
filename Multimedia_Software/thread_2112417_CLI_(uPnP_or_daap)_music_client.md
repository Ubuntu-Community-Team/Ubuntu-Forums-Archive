---
title: "CLI (uPnP or daap) music client"
date: 2013-02-04
forum: Multimedia Software
---

### Post by mr_mop on 2013-02-04
I have a uPnP/daap server, hosting all of my music.  I want to play this music from the server.
I've tried vlc-nox and that doesn't appear to do what I want.

Anyone got any idea on how to stream from my server using a CLI client?

---

### Post by tgalati4 on 2013-02-04
Install djmount:

```
sudo apt-get install djmount
```

Make a directory in ~/Music

```
cd
cd Music
mkdir Freenas_Music
```

My music is served by a uPnP freenas server, so I chose Freenas_Music, but you can use any name you want.

Run djmount in the Music directory:

```
djmount Freenas_Music
```

Install command line music player and run it:

```
sudo apt-get install moc
mocp
```

Navigate to your Music Directory and play some tunes.

---

### Post by mr_mop on 2013-02-05
That is absolutely perfect! Thank you very much.

---

### Post by spazzeri on 2013-03-26
On my 12.10 ubuntu system (64-bit), djmount segfaults (when I try to access a file on the share, e.g. read its Properties in nautilus)
 and syslog contains something like:

djmount[13880]: segfault at 7ff7000001f0 ip 00007ff75cda7f0b sp 00007ff75664b9f0 error 4 in libupnp.so.6.3.1[7ff75cd97000+34000]

djmount did work weeks ago; I was on 12.04 at the time.

Is there a workaround ?

---

### Post by tgalati4 on 2013-03-26
Looks like something is broken!!!

tgalati4@Mint14-Extensa ~/Music $ ls -la
ls: cannot access Freenas_Music: Transport endpoint is not connected
total 8
drwxr-xr-x  3 tgalati4 tgalati4 4096 Mar 26 18:14 .
drwxr-xr-x 39 tgalati4 tgalati4 4096 Mar 26 18:15 ..
d?????????  ? ?        ?           ?            ? Freenas_Music

I don't know of a work-around, because I don't know exactly what is wrong.  It was working back in Feb when I wrote the above tutorial.  Regressions are no fun!

------------------

You can use the -d switch with djmount to output debugging:

] GetHttp url 'http://192.168.1.162:49152/MediaServer/AudioItems/0000007867.mp3' size 4096 offset 3272704 (file_size 3274559)
[D] GetHttp truncate to size 1855
2013-03-26 18:31:38 0x7F0299A78700 httpreadwrite.c:1897 DOWNLOAD URL : [http://192.168.1.162:49152/MediaServer/AudioItems/0000007867.mp3](http://192.168.1.162:49152/MediaServer/AudioItems/0000007867.mp3)
2013-03-26 18:31:38 0x7F0299A78700 httpreadwrite.c:1927 HOSTNAME : 192.168.1.162:49152/MediaServer/AudioItems/0000007867.mp3 Length : 19
2013-03-26 18:31:38 0x7F0299A78700 httpreadwrite.c:1942 HTTP Buffer:
GET /MediaServer/AudioItems/0000007867.mp3 HTTP/1.1
HOST: 192.168.1.162:49152
Range: bytes=3272704-3274559
DATE: Wed, 27 Mar 2013 01:31:38 GMT
CONNECTION: close
USER-AGENT: Linux/3.5.0-26-generic, UPnP/1.0, Portable SDK for UPnP devices/1.6.17


----------END--------
2013-03-26 18:31:38 0x7F0299A78700 httpreadwrite.c:513 >>> (SENT) >>>
GET /MediaServer/AudioItems/0000007867.mp3 HTTP/1.1
HOST: 192.168.1.162:49152
Range: bytes=3272704-3274559
DATE: Wed, 27 Mar 2013 01:31:38 GMT
CONNECTION: close
USER-AGENT: Linux/3.5.0-26-generic, UPnP/1.0, Portable SDK for UPnP devices/1.6.17


buf_length=252, num_written=252
------------
Segmentation fault


It loads the database OK, I can see it in mocp, but as soon as I try to play it, it crashes.

You can use *sudo umount Freenas_Music* to disconnect the mount and start again.  But I'm not sure what is causing the segfault.

The file dates are not correct:  (This does not appear to be relevant, since they are wrong on the developer page:  [http://djmount.sourceforge.net/](http://djmount.sourceforge.net/))

tgalati4@Mint14-Extensa ~/Music/Freenas_Music $ ls -la
total 6
dr-xr-xr-x 4 root     root      512 Jan  1  2000 .
drwxr-xr-x 3 tgalati4 tgalati4 4096 Mar 26 18:14 ..
dr-xr-xr-x 4 root     root      512 Jan  1  2000 .debug
-r--r--r-- 1 root     root        8 Jan  1  2000 devices
dr-xr-xr-x 4 root     root      512 Jan  1  2000 freenas

-------------------------

Rhythmbox 2.97 works with my DAAP share, so the DAAP framework works with my Freenas box.  When I get some time, I will check my 32-bit laptop to see if still works under 12.10.  After reading the man page, djmount only detects uPnP streams, not DAAP streams.

--------------------------

I installed *upnp-inspector* and ran it.  It picks up the server and pulls down the services offered:

tgalati4@Mint14-Extensa /tmp/a3a80248-2ad2-4fe1-b190-1c846e0a89a3 $ cat device-description.xml 
<?xml version="1.0" encoding="UTF-8"?>
<root xmlns="urn:schemas-upnp-org:device-1-0"><specVersion><major>1</major><minor>0</minor></specVersion><URLBase>http://192.168.1.162:49152/</URLBase><device><UDN>uuid:a3a80248-2ad2-4fe1-b190-1c846e0a89a3</UDN><friendlyName>freenas</friendlyName><manufacturer>Ulrich Voelkel</manufacturer><manufacturerURL>http://www.ulrich-voelkel.de</manufacturerURL><modelDescription>Free UPnP Media Server licensed under the terms of the GPL</modelDescription><modelName>Free UPnP Entertainment Service 0.660</modelName><modelNumber>0.660</modelNumber><modelURL>http://fuppes.ulrich-voelkel.de</modelURL><serialNumber>0123456789</serialNumber><deviceType>urn:schemas-upnp-org:device:MediaServer:1</deviceType><serviceList><service><serviceType>urn:schemas-upnp-org:service:ContentDirectory:1</serviceType><serviceId>urn:upnp-org:serviceId:ContentDirectory</serviceId><SCPDURL>/UPnPServices/ContentDirectory/description.xml</SCPDURL><controlURL>/UPnPServices/ContentDirectory/control/</controlURL><eventSubURL>/UPnPServices/ContentDirectory/event/</eventSubURL></service><service><serviceType>urn:schemas-upnp-org:service:ConnectionManager:1</serviceType><serviceId>urn:upnp-org:serviceId:ConnectionManager</serviceId><SCPDURL>/UPnPServices/ConnectionManager/description.xml</SCPDURL><controlURL>/UPnPServices/ConnectionManager/control/</controlURL><eventSubURL>/UPnPServices/ConnectionManager/event/</eventSubURL></service></serviceList><presentationURL>index.html</presentationURL></device></root>

---

