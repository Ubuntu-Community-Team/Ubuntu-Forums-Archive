---
title: "Command-line tools to get GPS data"
date: 2013-06-24
forum: Networking &amp; Wireless
---

### Post by younlee on 2013-06-24
Dear all,

I'm trying to make a script (or an application) which get GPS data from the serial GPS device, then send it to another laptop via wireless connection.

I checked the gps signal (cat /dev/ttys0): it's OK.

===cat /dev/ttyS0 result===============
[SIZE=2]laptop:~$ cat /dev/ttyS0[/SIZE]
[SIZE=2]$GPZDA,095720.00,12,12,2012,00,00*6E[/SIZE]
[SIZE=2]$GPGGA,,,,,,0,,,,,,,,*66[/SIZE]
[SIZE=1][SIZE=2]$GPGSV,4,2,15,16,38,106,,18,34,003,,11,25,214,,01,12,219,*7B[/SIZE]
[SIZE=2]===============================[/SIZE]

[/SIZE]
Then I installed gpsd & gpsd-clients, and I indicated the GSP device path to gpsd (gpsd /dev/ttyS0): to tell gpsd where to look for the GPS device.
After that I tried to use "gpspipe" tool to get GPS data (gpspipe -w -n 5), but, gpspipe seems not recognizing the GPS device: "class":"DEVICES","devices":[]

===gpspipe -w -n 5 result===============
laptop:~$ gpspipe -w -n 5
{"class":"VERSION","release":"2.92","rev":"svn","proto_major":3,"proto_minor":1}
{"class":"DEVICES","devices":[]}
{"class":"WATCH","enable":true,"json":true,"nmea":false,"raw":0,"scaled":false,"timing":false}
laptop:~$ 
===============================

How can I fix the problem of "class DEVICES" ?

After that, if I will have the "TPV" class, how can I extract the GPS data and send them to another laptop using Wireless connection ?

Regards,

---

### Post by Cheesehead on 2013-06-24
Class DEVICES may not be the problem - the posted example simply shows that no devices are attached. If a device were attached, it would be followed by five location sentences. That usually means that gpsd is not, in fact, recieving the serial stream.

- Check your baud rate. I had a gps dongle that only produced results in a specific range.

- Use the cgps or xgps tools included with gpsd to verify successful connectivity with the device.



My solution for transmitting is for your application on the GPS-using laptop (server) to listen for sentences from gpsd, convert it into XML, and puts it on an http server. Python, for example, has several good gpsd interfaces written already for you.

Your other (client) laptop's application to sends an http request to the server, and decodes the xml into whatever format you wish. Python has some good pre-made tools there, too.

If not http, you can get more complex with JSON or ssh or raw sockets for transmitting the data. Http is simple, has well-known tools, and does not require mucking about with permissions.

---

