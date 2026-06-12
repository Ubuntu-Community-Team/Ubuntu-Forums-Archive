---
title: "FTP/TCP problem resulting in corrupted download"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by ekristia on 2011-05-16
Main symptom of problem: File downloaded by ftp is corrupted. The corruption consists of insertion of "junk" at several places in the file. See below for details.

Server: UBUNTU 10.04; vsftpd; Wireshark.
All is pretty much a standard installation, and I have not been playing around with the network software or configuration, as far as I know.
MTU=1500; MSS=1460 (the value reported in the SYN packet)

Client: Windows Vista; Filezilla; Wireshark
MTU=1500; MSS=1460 (the value reported in the SYN packet)

For detailed tests reported below, client and server were connected through Ethernet switch.

Several other setups and clients tested: Using router instead of switch; Vista command line ftp client; Filezilla client on Windows NT connected through Internet; ANDROID cllient connected trough Internet; using a different ftp server. These configurations were not investigated in detail, but the main symptom of a corrupted file was confirmed in all cases.

All this seems to point to a server-side problem.

Detailed investigation:

Wireshark at the server shows packets that are a multiple of the MSS. For example, the first packet was 2960B and starts like this (The data in the original file is an ASCII text consisting of a HEX dump of a file unrelated to the test - makes it easy to distinguish data from junk):

First packet. IP length 2960B
0000  00 17 42 94 c7 f5 e0 cb  4e d6 14 0e 08 00 45 08   ..B..... N.....E.
0010  0b 90 8d 5b 40 00 40 06  bc 7e c0 a8 b2 1f c0 a8   ...[@.@. .~......
0020  b2 15 c1 5d f9 a4 db 53  eb fe 64 9e d1 1b 50 10   ...]...S ..d...P.
0030  00 5c f1 08 00 00 30 30  30 30 30 30 30 20 64 38   .\....00 00000 d8
0040  66 66 20 65 31 66 66 20  34 35 39 61 20 37 38 34   ff e1ff  459a 784
0050  35 20 36 36 36 39 20 30  30 30 30 20 34 39 34 39   5 6669 0 000 4949
0060  20 30 30 32 61 0a 30 30  30 30 30 32 30 20 30 30    002a.00 00020 00
0070  30 38 20 30 30 30 30 20  30 30 30 62 20 30 31 30   08 0000  000b 010

The header seems perfectly OK, but it is surprising that the length is larger than MSS. Some later packets were even larger.

Looking at packet and byte counts with ifconfig before and after the file transfer, it seems that the large packets were broken down into packets with proper MTU size before going on the wire. The average packet size was slightly below 1500B. I haven't got the tools to sniff directly on the wire.
It is not clear to me where this happens, and why Wireshark shows the long packets rather than the packets after splitting. This seems to suggest that the splitting happens very low in the protocol stack.

Wireshart at the client side sees this first packet being broken down into two packets each starting like this:

First packet. IP length 1500B 
0000  00 17 42 94 c7 f5 e0 cb  4e d6 14 0e 08 00 45 08   ..B..... N.....E. 
0010  05 dc 8d 5b 40 00 40 06  c2 32 c0 a8 b2 1f c0 a8   ...[@.@. .2...... 
0020  b2 15 c1 5d f9 a4 db 53  eb fe 64 9e d1 1b 50 10   ...]...S ..d...P. 
0030  00 5c 2c 90 00 00 00 17  42 94 c7 f5 e0 cb 4e d6   .\,..... B.....N. 
0040  14 0e 08 00 45 08 0b 90  8d 5b 40 00 40 06 00 00   ....E... .[@.@... 
0050  c0 a8 b2 1f c0 a8 b2 15  c1 5d f9 a4 db 53 eb fe   ........ .]...S.. 
0060  64 9e d1 1b 50 10 00 5c  e5 8c 00 00 30 30 30 30   d...P..\ ....0000 
0070  30 30 30 20 64 38 66 66  20 65 31 66 66 20 34 35   000 d8ff  e1ff 45 
0080  39 61 20 37 38 34 35 20  36 36 36 39 20 30 30 30   9a 7845  6669 000 
0090  30 20 34 39 34 39 20 30  30 32 61 0a 30 30 30 30   0 4949 0 02a.0000 
00a0  30 32 30 20 30 30 30 38  20 30 30 30 30 20 30 30   020 0008  0000 00 
00b0  30 62 20 30 31 30 65 20  30 30 30 32 20 30 30 32   0b 010e  0002 002 
00c0  30 20 30 30 30 30 20 30  30 39 32 0a 30 30 30 30   0 0000 0 092.0000 
00d0  30 34 30 20 30 30 30 30  20 30 31 30 66 20 30 30   040 0000  010f 00 
00e0  30 32 20 30 30 31 38 20  30 30 30 30 20 30 30 62   02 0018  0000 00b 
00f0  32 20 30 30 30 30 20 30  31 31 30 0a 30 30 30 30   2 0000 0 110.0000 
0100  30 36 30 20 30 30 30 32  20 30 30 30 65 20 30 30   060 0002  000e 00 
 
Second packet. IP length 1500B 
0000  00 17 42 94 c7 f5 e0 cb  4e d6 14 0e 08 00 45 08   ..B..... N.....E. 
0010  05 dc 8d 5c 40 00 40 06  c2 31 c0 a8 b2 1f c0 a8   ...\@.@. .1...... 
0020  b2 15 c1 5d f9 a4 db 53  f1 b2 64 9e d1 1b 50 10   ...]...S ..d...P. 
0030  00 5c cf 79 00 00 32 30  61 20 30 30 30 35 20 30   .\.y..20 a 0005 0 
0040  30 30 31 20 30 30 30 30  20 30 33 31 36 20 30 30   001 0000  0316 00 
0050  30 30 20 39 32 37 63 0a  30 30 30 30 37 34 30 20   00 927c. 0000740  
0060  30 30 30 37 20 31 63 65  38 20 30 30 30 30 20 30   0007 1ce 8 0000 0 
0070  34 32 30 20 30 30 30 30  20 39 32 38 36 20 30 30   420 0000  9286 00 
0080  30 37 20 30 30 37 65 0a  30 30 30 30 37 36 30 20   07 007e. 0000760 

The IP and TCP headers look OK. 
BUT the TCP/IP header of the original 2960B packet is inserted following the header of the first packet.
The inserted data seems to be identical to the original header, EXCEPT the IP and TCP checksums are changed.
This insertion happens for all the large packets that are broken into smaller ones.

This header becomes part of the data seen by the client. And this is exactly the corruption I find back in the corrupted file: Insertion into the file of these headers of the original sent packets.

My conclusions so far:

There are two problems:

1. TCP sends packets that are a multiple of the MSS. I don't think this was supposed to happen, according to what I have been able to find on the net. However, if the splitting into smaller packets had worked correctly, this should not be a problem.

2. The splitting of these oversize packets does not work correctly The original header of the large packet is copied, with slight modifications, into the data part of the first split packet.
I note that large TCP packets are split into smaller TCP packets. It is NOT IP fragmentation. And, actually, the Don't Fragment bit is set in all packets.

Fixing either of these problems would make things work, as far as I can see.



Has anybody seen this before? Have you got any ideas what exactly is happening and how to fix it?

---

### Post by ekristia on 2011-05-29
I have been digging a bit deeper into the problem. Here is what I found so far:

1. The segmentation of large TCP packets is done by the network interface. Wireshark snifs between the computer and the interface card, so it is normal that it sees large packets, that are later broken into smaller ones before going on the wire (according to Wireshark help file). 

2. I found on a Debian forum a report of a similar problem of corrupted data (though with sendfile, not ftp):

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=623059](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=623059)

That post says the bug has been fixed in version 2.6.32-34. I am currently on 2.6.32-31.

Since I am not really in a hurry, I will wait for the next Ubuntu version to come out, to see if the fix is included.

I will update this thread when I know more.

---

### Post by ekristia on 2011-06-20
:D Found a solution:

In /etc/vsftpd.conf add:

use_sendfile=NO

Apparently, the problem is with sendfile.

---

