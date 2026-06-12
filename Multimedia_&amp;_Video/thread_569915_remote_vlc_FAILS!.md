---
title: "remote vlc FAILS!"
date: 2007-10-07
forum: Multimedia &amp; Video
---

### Post by Meomix on 2007-10-07
i im having trouble playing the vlc player from a remote computer
this laptop with ubuntu installed and has vlc on it does not have enough power to play videos
so i thought i would access this laptop remotely from my powerful solaris computer

i used the ssh command to access the laptop fired up vlc, attempted to launch a video only to have vlc crash, how do i get vlc to play nice with ssh?

i would have used VNC but it literally "takes over the machine" does VNC have a stealth mode, i attempted to run a video though VNC but the video was a blank blue screen.

---

### Post by Meomix on 2007-10-08
bump [-o<

---

### Post by Meomix on 2007-10-08
Bumpity dumpity

---

### Post by Meomix on 2007-10-08
ahh.. im on googles.com second page :popcorn: SERIOUSLY SOMEONE HELP

Ubuntu (has the VLC and VIDEOS)


Solaris (opening VLC on ubuntu using ssh) --------------------------------------> Ubuntu

IT FAILS!!  Solaris ---------------- -link broken - - -> ________ Ubuntu

---

### Post by MeanderingCode on 2007-10-11
I am having this same problem.
Really basic issue.

1) ssh into box.
2) run vlc.
3) opens just fine...open video file...window resizes, about to play video.
4) Where the...did it go??
5) See:

```
user@thebox:~$ vlc
VLC media player 0.8.6 Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title:  WILLOW
libdvdnav: DVD Serial Number: 470BE86800000000
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/user/.dvdnav/ WILLOW.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000016f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001af22f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001b903c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x001cb081
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x001dca9b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x001f6efb
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x002364d0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x00237735
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x00237ef8
libdvdread: Elapsed time 0
libdvdread: Found 9 VTS's
libdvdread: Elapsed time 1
[00000302] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
X Error of failed request:  BadAccess (attempt to access private resource denied)
  Major opcode of failed request:  144 (MIT-SHM)
  Minor opcode of failed request:  1 (X_ShmAttach)
  Serial number of failed request:  51
  Current serial number in output stream:  52

```


Anyone??

Thanks.

Sean

---

### Post by martin.cameron.nz on 2007-12-13
Here's what you need to do to run a vlc session from a remote server to view on your local screen:

1. Log on to the server with ssh as follows:
    ssh -Y username@servername

2. Run vlc to broadcast (either multicast or unicast) as follows:
   vlc -v  "Layer_cake.avi" --sout '#duplicate{dst=standard{access=udp,mux=ts,dst=239.255.12.42},dst=standard{access=udp,mux=ts,dst=192.168.0.204}}'
VLC media player 0.8.6 Janus

Notes:
1. All of the above is on one line
2. This will broadcast the movie Layer Cake to the computer that's hanging off the IP 192.168.0.204.

Here's a perl script that I have written to automate the task:

<code>

#! /usr/bin/perl -w
print "\n\n Usage: Filename Destination1 Destination2 Destination3 DestinationN ...\n\n\n";
$file="\"".$ARGV[0]."\"";

$command="vlc -v  ".$file." --sout '#duplicate{dst=standard{access=udp,mux=ts,dst=239.255.12.4$

my $comma="";
for($i=1;$i<scalar(@ARGV);$i++)
{
         $command.= $comma;
         $comma=",";
         $command .= "dst=standard{access=udp,mux=ts,dst=192.168.0.".$ARGV[$i]."}";
}
$command.= "}'";
print $command."\n";


</code>

To run the file:
stream_avi.pl movie_name 2 204 9 26 75

where 2 204 9 etc are the IP nodes for the various computers that you are streaming to on the 192.168.0. network. If your LAN is not 192.168.0. then edit the script to add in the C-Class for your LAN - for example, your LAN C-Class may be 10.1.1  Chnage the script to reflect this.

---

### Post by martin.cameron.nz on 2007-12-13
ERROR FIX

In the last post, the $coomand line was truncated. It should be:
$command="vlc -v  ".$file." --sout '#duplicate{dst=standard{access=udp,mux=ts,dst=239.255.12.42},";

{NOTE 1}
The above is all on one line.

{NOTE 2}
Also didn't display the final line:

`$command`;

{NOTE 3}
Those little quote marks are ticks - that little thing on the keyboard to the left on the number 1. They're essential to make it go!

---

