---
title: "Netperf, Iperf, Netpipe please help"
date: 2009-03-16
forum: Networking &amp; Wireless
---

### Post by vandinsh on 2009-03-16
Hello!!!! Please help me!!!I have tried netperf, netpipe, iperf!!! :(

But I need a programm, that tests network performance (TCP and UDP tests)
There have to be a possibility to define sending nessage size in bytes.
In an output i would like to see: 
1. how much time did information transaction take ( result in usec);
2. bandwith.

Thanks a lot!!:)

---

### Post by jonobr on 2009-03-16
Hello


You mentioned IPerf, that does exactly what your asking for (unless Im missing something).
If your having a problem with the syntax let us know what you have tried and are not seeing and people will help.

---

### Post by vandinsh on 2009-03-19
I would like to test  network performance, sending 1 GB 5 times, with new TCP connection every time.
In an output would like to see how much time it took for each transaction.
But as I have understood there is no possibility in Iperf to tell how much data I want to transmit (unless Im missing something). :(

---

### Post by netztier on 2009-03-19
> **vandinsh said:**
>  But as I have understood there is no possibility in Iperf to tell how much data I want to transmit (unless Im missing something). :(

Definitely you are missing something!

```
user@host~$ **iperf --help**
Usage: iperf [-s|-c host] [options]
       iperf [-h|--help] [-v|--version]

Client/Server:
  -f, --format    [kmKM]   format to report: Kbits, Mbits, KBytes, MBytes
  -i, --interval  #        seconds between periodic bandwidth reports
  -l, --len       #[KM]    length of buffer to read or write (default 8 KB)
  -m, --print_mss          print TCP maximum segment size (MTU - TCP/IP header)
  -o, --output    <filename> output the report or error message to this specified file
  -p, --port      #        server port to listen on/connect to
  -u, --udp                use UDP rather than TCP
  -w, --window    #[KM]    TCP window size (socket buffer size)
  -B, --bind      <host>   bind to <host>, an interface or multicast address
  -C, --compatibility      for use with older versions does not sent extra msgs
  -M, --mss       #        set TCP maximum segment size (MTU - 40 bytes)
  -N, --nodelay            set TCP no delay, disabling Nagle's Algorithm
  -V, --IPv6Version        Set the domain to IPv6

Server specific:
  -s, --server             run in server mode
  -U, --single_udp         run in single threaded UDP mode
  -D, --daemon             run the server as a daemon

Client specific:
  -b, --bandwidth #[KM]    for UDP, bandwidth to send at in bits/sec
                           (default 1 Mbit/sec, implies -u)
  -c, --client    <host>   run in client mode, connecting to <host>
  -d, --dualtest           Do a bidirectional test simultaneously
[COLOR="Red"]  -n, --num       #[KM]    number of bytes to transmit (instead of -t)[/COLOR]
  -r, --tradeoff           Do a bidirectional test individually
  -t, --time      #        time in seconds to transmit for (default 10 secs)
  -F, --fileinput <name>   input the data to be transmitted from a file
  -I, --stdin              input the data to be transmitted from stdin
  -L, --listenport #       port to recieve bidirectional tests back on
  -P, --parallel  #        number of parallel client threads to run
  -T, --ttl       #        time-to-live, for multicast (default 1)
  -Z, --linux-congestion <algo>  set TCP congestion control algorithm (Linux only)

Miscellaneous:
  -x, --reportexclude [CDMSV]   exclude C(connection) D(data) M(multicast) S(settings) V(server) reports
  -y, --reportstyle C      report as a Comma-Separated Values
  -h, --help               print this message and quit
  -v, --version            print version information and quit

[KM] Indicates options that support a K or M suffix for kilo- or mega-

The TCP window size option can be set by the environment variable
TCP_WINDOW_SIZE. Most other options can be set by an environment variable
IPERF_<long option name>, such as IPERF_BANDWIDTH.

Report bugs to <iperf-users@lists.sourceforge.net>

```

There you are.. some shell-scripting should be able to tell you how long iPerf took to run before it exited...

Some playing around with dd and netcat might also help - do a tcp connection with netcat from host to host, and use dd to pump N Gigabytes of data through the connection - dd should be able to report pretty precise figures.



regards

Marc

---

### Post by vandinsh on 2009-03-19
Thank you for your answer!:)
I've tried 
iperf -c 10.1.2.30 -n 100
But in result, Iperf did not stopped for a long time. When I've stopped it manually in an output I got 2 GB transfered instead of 100 MB
How it is possible and what can I do?

---

### Post by netztier on 2009-03-19
> **vandinsh said:**
> Thank you for your answer!:)
How it is possible and what can I do?

read the --help output:


```
-n, --num       #[KM]    number of bytes to transmit (instead of -t)

...

[KM] Indicates options that support a K or M suffix for kilo- or mega-

```

That would be for you:

```
user@host~$ **iperf -c <serverip> -n 100M**
```


regards

Marc

---

### Post by vandinsh on 2009-03-20
That is great!! Thanks a lot!!!! I have one more question is there possibility to make Iperf show result in mikrosecunds? :)

---

