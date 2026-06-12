---
title: "Unknown Stream connections"
date: 2011-04-16
forum: Networking &amp; Wireless
---

### Post by buntuser2 on 2011-04-16
This is a section of the results from sudo netstat:

```

unix  3      [ ]         STREAM     CONNECTED     14090    1640/dbus-daemon    @/tmp/dbus-Xrandom
unix  3      [ ]         STREAM     CONNECTED     14089    1819/gdu-notificati 
unix  3      [ ]         STREAM     CONNECTED     14052    1179/dbus-daemon    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14051    1819/gdu-notificati 
unix  3      [ ]         STREAM     CONNECTED     14049    1353/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14048    1819/gdu-notificati 
unix  3      [ ]         STREAM     CONNECTED     14013    1605/gnome-session  @/tmp/.ICE-unix/1600
unix  3      [ ]         STREAM     CONNECTED     14012    1805/pulseaudio     
unix  3      [ ]         STREAM     CONNECTED     13984    1353/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13983    1805/pulseaudio     
unix  2      [ ]         DGRAM                    13942    1805/pulseaudio     
unix  3      [ ]         STREAM     CONNECTED     13928    1805/pulseaudio     /home/myusername/.pulse/290c89b9fc5a28fbjusdghsd723458g4324-runtime/native
unix  3      [ ]         STREAM     CONNECTED     13927    1652/gnome-settings 
unix  3      [ ]         STREAM     CONNECTED     13924    1811/gconf-helper   /tmp/orbit-myusername/linc-713-0-dcffc53e9c29
unix  3      [ ]         STREAM     CONNECTED     13923    1645/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     13920    1645/gconfd-2       /tmp/orbit-myusername/linc-66d-0-162b86178678
unix  3      [ ]         STREAM     CONNECTED     13919    1811/gconf-helper   
unix  3      [ ]         STREAM     CONNECTED     13862    1179/dbus-daemon    /


```


Where are these coming from? I have UFW set to block all connections except the connections I allow, and none of these are allowed.

Are those numbers the ports? I have a rule for these ports to be blocked in UFW so how are they connecting? Why are they streaming? Why is gconf-helper connected to the internet? Why are there all these things connected to the internet???????

There are about 50 more in the actual results displayed in terminal.

---

### Post by espressobeanie on 2011-04-16
I'm not familiar with 'stream connections' but I think they come from a web-browser, say when you connect to a video streaming service or something.

---

