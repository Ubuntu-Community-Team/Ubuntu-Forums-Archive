---
title: "No Dhcp3 server after sleep"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by thieaux on 2009-06-10
I have dhcp3 server working fine, but when the pc goes to sleep and it wakes up, dhcp3 server will not cast ip untill i manually restart it

Any suggestion, someone mnetioned that there is a typo in 
/usr/lib/pm-utils/sleep.d/dhcp3-server , but cant seem to find the file in my setup.

 help!!

---

### Post by jonobr on 2009-06-13
sounds like the process is suspended on sleep.

After it recovers if you do a sudo /etc/init.d/dhcp3 status
what does it say?

Also, if its a DHCP s3erver, Im thinking it should not be going into sleep mode....

It wont answer DHCP requests if the server goes into sleep

---

### Post by thieaux on 2009-06-13
Thaks for the replay, i had some issues with the S1 and S3 modes in the bios, don't know why but the pc refused to load after sleep, changung form s1 to s3 solved the issue, the dchp3 server was for a lan that only needed the addresses once in a while, i opted for static address and reslve the issue.

 thanks.

by the way do you know anything about tcp window sizes and iperf.....I just ran it , usinc mac as server ran great 90MB/s stable to my ubuntu box (9.04) 2.6.28 , but from my ubuntu box to mac i was getting speed all over the place , no stable and packets loss, so i opted to ran iperf with a windows size of 64kB instead of default and ran perfect , how can i make these changes permanetly ?

thanks

---

### Post by jonobr on 2009-06-13
Hello


Glad you got it sorted.

I have ran into issues before running iperf before where I expressed the size being too large and it did show crappy results due to fragenting and so on,
however, your test results are interesting that one way shows it welel and the other doest,
its like one side handles it fine and deals with it and the other doesnt.

I have only really done iperf from a client side (cpe) to a server to do throughput testing on wireless interfaces I have not done the other way round.

What we did was to have a good result with a good config  as a metric using certain paramters, so for example

you set the config run the test and compare against the good one.
That way you dont have to mess around with paramters and you should have a direct comparison between what should be good and what you are getting.

Have you tried jperf?
Its the java based version of the same app and makes it a little easier to use

---

### Post by thieaux on 2009-06-13
Thanjs for the info, last night i did try jeprf, and norrewd down to a 64k Windows size, now i need to learn how ipierf handles the data stream. Im still not confortable using, apparently the server receives the data stream and the client is the sender, i was trying to use the -F functino so i can relate the I/O of hdd  to the speed of the network, so to have an idea to how 'fast" my network really is. But having issues, i have a second hdd that handles my data on the ubuntu box, somehow i cant get iperf to use the data stored in there, keep getting  "Unable to use data stream, using default" or something like that.  

Thanks for the help, you have any suggestion..

---

### Post by jonobr on 2009-06-14
Hello


Although I suggested JPERF I usually just use the cli and not the gui. The CLi is easier to control and using man iperf, it will show you all the options possible.

when using Iperf either side can typically be the client or the the server and you would change which side is doing what based on what you want to test , i.e. upload or download speed.

Heres examples of how prefer to use iperf to test upload and download speeds using either tcp or UDP (note , these values suit me best for my line of work.)
[B][U]
Downlink UDP[/U][/B]

    * Client: iperf -f k -s -u -i 100 (tests for 100 seconds)
    * Server: iperf -f k -c <ipaddressofclient> -l 1450 -u -b 12m -i 100 -t 100

**_Downlink TCP_**

    * Client: iperf -f k -s -i 100 -w 128k
    * Server: iperf -f k -c <ipaddressofclient> -i 100 -t 100 -w 128k

**_Uplink UDP_**

    * Client: iperf -f k -c <IPaddressofserver> -l 1450 -F <location of file to transmit> -u -b 400k -i 100 -t 100
    * Home Agent: iperf -f k -s -u -i 100 -B <IPaddressofserver>

**_Uplink TCP_**

    * Client: iperf -f k -c <IPaddressofserver> -F <location of file to transmit> -i 100 -t 100
    * Server: iperf -f k -s -i 100 -B <IPaddressofserver>

---

### Post by thieaux on 2009-06-14
Thats great thanks for your help, it really helped a lot , just a random question, what limits the tcp window size, i mean what are the limiting factors that makes unreliable to use really large windows , is it hardware or IPV4 protocol?

---

### Post by jonobr on 2009-06-14
hello


going back to my earlier cisco IOS classes :-)
I recall that windowing was used for congestion control, whereby you would have intermediate systems which may not have the same capacity,processing, throughput or performance as other parts of the network.

The result would be bottle necks in the network.

Windowing attempts to compensate for that possible congestion point,
its able to respond back to the sender to slow things down so it can process them in a way not to cause problems.

(Im still going to dive into my cisco book in work tomorrow to confirm this).

You will see problems in networks where devices or application rewrite the window and cause problems for your network resulting in sucky rates, congestion etc.

I looked around for the congestion formula and found this resource, which I found [HERE]("http://www.ncsa.uiuc.edu/~vwelch/net_perf/tcp_windows.html")



> 

**_How big should I set the TCP window size?_**

In theory the TCP window size should be set to the product of the available bandwidth of the network and the round trip time of data going over the network. For example if a network had a bandwidth of 100 Mbits/s and the round trip time was 5 msec, the TCP window should be 100x10^6 times 5x10^-3 or 500x10^3 bits (65 kilobytes). 

The easiest way to determine the round trip time is to use ping from one host to the another and use the response times returned by ping. 

Note that many architectures have limits on the size of the socket buffer and hence the TCP window size. Typically these are on the order of a megabyte. 



You know , I remember 
the battle of Hastings was 1066,

I remember the way of calculating resonant frequency in a  tuned circuit is 

fr= 1 divided by 2(pi)*square root of (l)(c)

And that the round used for the british sa-80 and the Steyr aug assault rifle is the 5.56 mm  SS109d standard nato round.... 
You would think I would remember how to calculate the window size....

Maybe theres very little room left in this nut on my shoulders :-)

---

### Post by thieaux on 2009-06-15
jejejeej  i think you need to defrag the "nut";) jeje... thanks for sharing the knowledge..

---

### Post by jonobr on 2009-06-15
LOL ...

Any more IP qs, Id be glad to assist if and where I can

---

### Post by thieaux on 2009-06-15
you know i've been doing a lot network benchmarking this couple of days, and something is bothering me , i know reaching "real" gigabit speeds over a network is quite an illusion for the average consumer, but my iperf results using ram generated data average 70MB/s, even using the -F to use a stream from my HDD is reaching and average 50MB/s, i know there is protocl overhead and all but using NFS my average is 28 to MB/s thats a rough 40% reduction in speed, im guessing my tcp window is off and not negotiating at all , its between a mac pro and a ubuntu box, im going to see if a i can set the tcp window permanently and try again.

Another thing my card netgear "ga311" odly enough would not link up to gigabit speeds when connected to the switch (gs105 gigabit switch), in a linux enviorement (ubuntu), but put it on a mac or windows box and it would link up perfectly, may be issues with the driver , but thats not important, it was just a comment.

---

