---
title: "Test throughput between two Servers"
date: 2011-11-15
forum: Networking &amp; Wireless
---

### Post by chrislynch8 on 2011-11-15
Hi,

I have two Server connected via OpenVPN across the Internet. Both have ADSL2 uncontended Internet Connections. 

Server01 -> 12Mbps/1.1Mbps 
Server02 -> 12Mbps/1.1Mbps

On top of these servers I also have another 20+ Server connecting back to Server01 also, but I am running tests between these two.

We use RSYNC for backups and it reports a throughput of approx 102.49KBytes/sec. I've used iperf for test directly between the two servers and it give results averaging 1.05Mbits/sec. The RSYNC runs at night when there should be very little traffic on the servers etc.. The iperf I ran at various time thoroughout the working day. 

If I use the -w 2M option with iperf I then get different results of approx 6.74MBits/sec

Maybe I'm using iperf incorrectly, or I'm half asleep doing it, but this there a tool out there that I could just install on both machine let it sit there for and week or s oand have it report back ot the amount of Incoming and Outgoing traffic between both servers. 

Rgds
Chris

---

### Post by jonobr on 2011-11-15
Hello

iperf is commonly used in the networking industry for testing purposes, also I dont know if this is too much for you but 
I would recommend using SNMP to monitor the devices for throughput as well as other metrics.

You have a few options,
[MRTG]("http://oss.oetiker.ch/mrtg/") 

is probably the most popular 

or [PRTG]("http://www.paessler.com/prtg") 




You could use Plain old SNMPwalk which is a cli based snmp walking tool

or you could use something like
[Opmanager]("http://www.manageengine.com/network-monitoring/") Which is fere for up to 10 nodes

---

### Post by chrislynch8 on 2011-11-16
Hi,

Thanks, I will look at MRTG but that might be too much for what I want to acheive. I installed bandwidthd on both servers and have it monitoring the External Interface to get an idea of the amount of data coming and going. 

Running **_iperf -s_** on server01 and **_iperf -c server01_** on server02 I get the following average after 6 tests

5.88MBytes Transferred
4.635Mbits/sec

I would have thought that the average Throughput of 4.635Mbps wouldn't be possible because both servers only have a max upload speed of 1.1Mbps? I am taking the results the wrong way.

I've tried searching the web, for some decent documentation on the use of iperf and explainations of the output etc, but have come up blank so far.

Rgds
Chris

---

### Post by jonobr on 2011-11-16
Hey there


Your right throughput should be lower then bandwidth
It looks as if you may be reading in the wrong direction, ie your looking at downlink speed and not uplink? Just a guess

It may also be easier to construct statements using jperf 
This is the java based version of iperf and allows you to see all available options for testing,

If you stick with command line heres a few sample IPerf tests
(I used use these when I tested devices on our wireless network, you may want to play around with them a bit.


To test Downlink UDP

on the server 

iperf -f k -s -u -i 5

on the client

iperf -f k -c <serverIP> 1450 -u -b 12m -i 5 -t 100


Downlink TCP
Server
iperf -f k -s -i 5 -w 128k
Client
iperf -f k -c <server IP>  -i 5 -t 100 -w 128k


Uplink UDP


iperf -f k -c <serverIP> -l 1450 -F /dev/urandom -u -b 400k -i 5 -t 100
iperf -f k -s -u -i 5 -B <server IP>


UPlink TCP

iperf -f k -c <serverip> -F /dev/urandom -i 5 -t 100
iperf -f k -s -i 5 -B <serverip>

---

### Post by patch11 on 2011-11-16
> If I use the -w 2M option with iperf I then get different results of approx 6.74MBits/sec


Hi,

for how long are you running your iperf's?

The -w option just changes the initial send-window of TCP.
Thus, the client can directly push 2M into the send-buffer. But this does not mean that they already reached the destination.

If you run iperf with "-t 120 -i 1" you should see, that in the beginning you have a very high bandwidth. And then it drops down to your 1Mbps.

Christoph

---

### Post by jonobr on 2011-11-16
Hey there patch11

I have noticed that with an i of 5  (I think I recommended that initially) that there is an initial bogus spike for the start and then it settles down for the next 5 second period

---

### Post by chrislynch8 on 2011-11-17
Hi

jonobr thanks for the tests.

I've tried the Downlink TCP & UDP ones - The UDP showed as 12Mbps and the TCP show 6.5Mbps

When I am running the upling test, which command is run on the Server and which one on the Client?

Rgds
Chris

---

### Post by jonobr on 2011-11-17
Hi There,

God I am so bored in work, I feel like writing a long response, and add in information you didnt ask for,

Im just in a funky mood today.......


Given the nature of TCP and UDP
UDP in general will most always be a lot faster given the nature of the transfer.
TCP will look for acknowledgement to chunks of data before resending while UDP expects that the network is good enough to transmit connectionless data and just fires the data to the other end expecting the other end to worry about error checking and integrity of the data.
Apologies if you know this already,
If you use services like ssh, ftp, their transport relies on
data integrity and will use a transport protocol like TCP to make sure the data gets there, if not , it will be retransmitted.

UDP will be for transfers that are more delay sensitive,eg voice or video over IP, in that if you loose a packet, or group of packets , you can do without them being retransmitted. If they were transmitted you would receive them out of sequence which would result in voice or video sounding or looking bad.

Most people posting throughput questions, wont actually state transport protocols, or how they did it,
and they dont realize that the type of data shoving and pushing/shoving they are doing will have different rates depending on transport. There are other transports such as SCTP however, thats a whole different ball of wax.

So, depending on the transport you use, you will have different results.

Additionally , and again apologies if you know this,
using iperf for throughput is a lot better then the testing a lot of people do here in the forums.
People most times will compare the windows progress bar of downloading to linux, or will download a file using say ftp and count how long it takes,
The logic is usually, I have a 10 mb file, it took 10 seconds to download via ftp, this is therefore a 1mbps download.
Thats inaccurate.
This would test "goodput"as opposed to "throughput"
To move that 10 mb file requires a packet which has additional information outside of the actual data so it is an inaccurate method for testing throughput.

This is an argument to use something like SNMP to count in and out octets or Iperf.

Anyway, did you get to try jperf? Its a lot easier to look at then Iperf.

As I recall you can switch sides for uplink testing ( i may not have made that clear in my post)
Ie if your downlink testing and A is the server B is the client
Then to uplink test you can hace B as the server and A as the client.

---

### Post by chrislynch8 on 2011-11-18
Hi,

Thanks again. This is my first time using iperf so just trying to get my bearings with it at the moment. I haven't tried jperf at all, from my understand this is Java GUI based program. I am running the tests between to serverswith no GUI.

Rgds
Chris

---

### Post by jonobr on 2011-11-18
Yep its the GUI front endf to Iperf


Whats great about it is that instead of trying to rember syntax you can build your statment from a gui
Ie client server, tcp udp, interval and so on.

It really removes the problem of trying to remember CLI.

It will also show you a bit of a nice graph as well as the full syntax you have constructed if you want to go with cli

---

### Post by chrislynch8 on 2011-11-22
Hi,

Would you be able to explain the following results using the following two iperf commands

**iperf -f k -s -i 5 -w 128k** on a Server with a 18Mbps/2Mbps ADSL connection and 
**iperf -f -k -c 192.168.1.240 -i 5 -t 100 -w 128k** on a remote Server with a 12Mbps/1.1Mbps ADSL connection. See results below

```

------------------------------------------------------------
Client connecting to 192.168.1.240, TCP port 5001
TCP window size:   256 KByte (WARNING: requested   128 KByte)
------------------------------------------------------------
[  3] local 192.168.200.26 port 33101 connected with 192.168.1.240 port 5001
[  3]  0.0- 5.0 sec  3744 KBytes  6134 Kbits/sec
[  3]  5.0-10.0 sec  4136 KBytes  6776 Kbits/sec
[  3] 10.0-15.0 sec  4136 KBytes  6776 Kbits/sec
[  3] 15.0-20.0 sec  3832 KBytes  6278 Kbits/sec
[  3] 20.0-25.0 sec  4064 KBytes  6658 Kbits/sec
[  3] 25.0-30.0 sec  4056 KBytes  6645 Kbits/sec
[  3] 30.0-35.0 sec  3968 KBytes  6501 Kbits/sec
[  3] 35.0-40.0 sec  4136 KBytes  6776 Kbits/sec
[  3] 40.0-45.0 sec  3952 KBytes  6475 Kbits/sec
[  3] 45.0-50.0 sec  4152 KBytes  6803 Kbits/sec
[  3] 50.0-55.0 sec  3584 KBytes  5872 Kbits/sec
[  3] 55.0-60.0 sec  3624 KBytes  5938 Kbits/sec
[  3] 60.0-65.0 sec  4024 KBytes  6593 Kbits/sec
[  3] 65.0-70.0 sec  4080 KBytes  6685 Kbits/sec
[  3] 70.0-75.0 sec  3736 KBytes  6121 Kbits/sec
[  3] 75.0-80.0 sec  4104 KBytes  6724 Kbits/sec
[  3] 80.0-85.0 sec  3752 KBytes  6147 Kbits/sec
[  3] 85.0-90.0 sec  3472 KBytes  5689 Kbits/sec
[  3] 90.0-95.0 sec  4096 KBytes  6711 Kbits/sec
[  3] 95.0-100.0 sec  3784 KBytes  6200 Kbits/sec
[  3]  0.0-100.1 sec  78440 KBytes  6422 Kbits/sec

```


Rgds
Chris

---

### Post by jonobr on 2011-11-22
Hi There


Ill give it a try .... gulp....
its been a while and we used to use this statement for testing CPE.

Bandwidth from your results on face value seem to show a bw of 
6.5ish Mbps for tcp connections.

if you changed to UDP that would be a good bit faster.

The window size (-w statement) in your statement could have an affect on what the results are also. Dropping the -w option, (allowing the thing to auto negotiate it without setting it) will have an affect.

I suppose this is the elephant in the room, and what your question may be referring to.
Lets deal with that (again apologies if you know this already)

Window size or "windowing" is a method for congestion control on a TCP link.
Windowing provides the ability to throttle back data rates so to reduce congestion and therefore data loss.

During regular communication Both sides on a tcp link will negotiate window size . this window size will be auto negotiated based on a few factors.

Setting the window size can be tricky and setting it to the wrong level can give incorrect reports about your throughput.

If you removed the -w option this will allow the OS to auto negotiate.
You will notice the default window size (I think its around 80k or something) will be reported at the start of your output when you drop the window size.

The window size is normally set to give a consistent metric to test your network and where the client cannot do auto tuning.
You can imagine that trying to get reference points for the throughput of your network relies on things staying constant.

As an example, if you set the -w to 8k which is done a lot in throughput testing,
it will set both sides of the link and give a bench mark but will probably give you different results.

When you test the next day with the same -w and the results are a lot lower or higher, you know something is different.
Imagine then if you were to not use -w and the results change, it could be a result of window size changes.

The windowing used in what I provided you was used in our CPE wireless devices.
In your case, maybe running without setting windowing will give you higher results.


That was a long windy story to just say drop -w eh???:D

---

