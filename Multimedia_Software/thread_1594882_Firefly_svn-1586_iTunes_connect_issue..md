---
title: "Firefly svn-1586 iTunes connect issue."
date: 2010-10-12
forum: Multimedia Software
---

### Post by dmovad on 2010-10-12
Basically from the web interface all looks fine. In iTunes an incorrect server name shows up!  Instead of the configured name the hostname of the server itself is depicted!  When clicking on the server in iTunes it will not stay selected but immediately jumps off of the server and back up to the music library on the Mac.

I've got an Intel Atom computer running Ubuntu server 10.4.1 and I compiled svn-1586 using the following configuration:

./configure -prefix=/usr --enable-sqlite3 --enable-avahi

I created an Avahi service as follows:

<service-group>

  <name replace-wildcards="yes">%h</name>

  <service>
    <type>_daap._tcp</type>
    <port>3689</port>
  </service>
  
  <service>
    <type>_rsp._tcp</type>
    <port>3689</port>
  </service>[/color]

I also have Netatalk installed and have a service in avahi services and that works perfectly.

My Firefly configuration is pretty basic:

Server Name is the default: "Firefly %v on %h" (an interesting note is that in iTunes is displayed the hostname of the computer instead of what is in the Firefly configuration)!

Port: 3689
Run As: root (was mt-daapd but in my frustration I tried root)

Under Server Status it is finding and accounting for the correct amount of songs so Firefly is seeing the music and recognizing it. I am getting a bunch of "error 401 unauthorized in the error logs:

2010-10-12 17:47:33 (b74efb20): Scanned 9247 songs (was 0) in 1037 seconds
2010-10-12 17:48:40 (b6096b70): Thread 261: Entering ws_returnerror (401: Unauthorized)
2010-10-12 17:48:40 (b6096b70): Thread 261:  could not read: Success
2010-10-12 17:48:41 (b6096b70): Thread 262: Entering ws_returnerror (401: Unauthorized)
2010-10-12 17:48:41 (b6096b70): Thread 262:  could not read: Success
2010-10-12 17:53:24 (b6096b70): Thread 343: Entering ws_returnerror (401: Unauthorized)
2010-10-12 17:53:24 (b6096b70): Thread 343:  could not read: Success
2010-10-12 17:53:25 (b6096b70): Thread 345: Entering ws_returnerror (401: Unauthorized)
2010-10-12 17:53:25 (b6096b70): Thread 345:  could not read: Success
2010-10-12 17:53:26 (b6096b70): Thread 346: Entering ws_returnerror (401: Unauthorized)
2010-10-12 17:53:26 (b6096b70): Thread 346:  could not read: Success


I am baffled and any help would be greatly appreciated.

Thanks...
Dave

---

