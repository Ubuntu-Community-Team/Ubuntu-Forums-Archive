---
title: "UNIX ping dropping packets, WINDOWS ping fine!"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by Mazin on 2009-06-02
I recently acquired a new USB Wi-Fi adapter (Realtek 8187b) and when it works it work.  However, I have been noticing something odd: when I use UNIX ping to ping a website, I lose 3/5 or 4/5 of all the packets in a predictable pattern:

```
PING google.com (74.125.67.100) 56(84) bytes of data.
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=10 ttl=53 time=48.2 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=15 ttl=53 time=49.2 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=20 ttl=53 time=46.1 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=25 ttl=53 time=47.0 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=29 ttl=53 time=48.5 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=30 ttl=53 time=47.0 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=34 ttl=53 time=50.4 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=35 ttl=53 time=48.0 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=39 ttl=53 time=45.7 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=40 ttl=53 time=47.0 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=44 ttl=53 time=48.4 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=45 ttl=53 time=46.5 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=49 ttl=53 time=45.7 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=50 ttl=53 time=55.7 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=54 ttl=53 time=48.5 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=55 ttl=53 time=47.5 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=59 ttl=53 time=49.7 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=60 ttl=53 time=46.2 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=64 ttl=53 time=231 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=65 ttl=53 time=46.4 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=69 ttl=53 time=48.5 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=74 ttl=53 time=47.1 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=75 ttl=53 time=47.6 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=79 ttl=53 time=48.1 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=80 ttl=53 time=47.1 ms

```

It's as if there's an open "window" of time that packets can go through or not.

However, this only happens with UNIX ping.  Using Windows' ping.exe, all the packets go through fine with zero percent packet loss.

Tested with ping on Ubuntu 9.04 and Cygwin ping.exe on Windows, while native Windows ping.exe works fine.

---

