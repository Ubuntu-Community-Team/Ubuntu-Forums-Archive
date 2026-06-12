---
title: "Streaming Audio"
date: 2008-11-10
forum: Multimedia Software
---

### Post by famico666 on 2008-11-10
Hi all,

I have a specific site that I want to be able to stream audio from in Linux, but I can't find out how to get it to work:

[http://www.radio3net.ro/1001](http://www.radio3net.ro/1001)

I seem to remember it needing a Windows Media Player plugin before.

Help would be much appreciated. My gift to you is knowledge of the above site - it's great!


:)

---

### Post by famico666 on 2008-11-11
No one have any ideas?

I don't like to bump up my own posts, but I'm assuming it'll never get seen again if I don't. :)

---

### Post by famico666 on 2008-11-11
OK, legitimate bump this time...

I found this [http://ubuntuforums.org/showthread.php?t=572337](http://ubuntuforums.org/showthread.php?t=572337)

Same problem I was having. Except I don't understand how to install W32codecs. I found this page:

[http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/](http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/)

...but it didn't make much sense to me. I'm only a one-day-old in the linux world and don't really know how to install things using text commands yet. Tried following that page word-for-word and it failed. When I got to...


> 
. Import the gpg key for the Medibuntu repository to ensure that the packages are installed without warnings/errors regarding trust:
To do this, run the following command from the terminal:
wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

...I got an error which said "no valid Open PGP data found".

Is there an easier way to install these codecs? Is it definitely these codecs I need?

it's awfully quiet in here. I can hear my own echo-echo-echo-echo...

---

### Post by famico666 on 2008-11-11
Further self-help. apparently it is "Windows media 10+ with it's DRM stream".
That's what some evil Mac users says here: [http://macosx.com/forums/mac-os-x-system-mac-software/303959-trouble-streaming-audio.html](http://macosx.com/forums/mac-os-x-system-mac-software/303959-trouble-streaming-audio.html)

---

### Post by famico666 on 2008-11-11
Hello again Famico, it's me Famico again...


I found this:
[http://www.ubuntugeek.com/install-and-enable-dvd-playback-and-w32codecs-in-ubuntu-system.html](http://www.ubuntugeek.com/install-and-enable-dvd-playback-and-w32codecs-in-ubuntu-system.html)

Unfortunately, I don't know which version of Ubuntu I'm using. It's the latest one, 8.10. downloaded from ubuntu.com yesterday. So am I dapper or edgy? My online dating profile says I'm both, but I guess I have to be one or the other here.

---

### Post by famico666 on 2008-11-13
Nobody?

Latest update - I've installed w32 codecs and stil nothing.

---

### Post by psyke83 on 2008-11-13
> **famico666 said:**
> Nobody?

Latest update - I've installed w32 codecs and stil nothing.

It's impossible to "strip" encrypted WMV streams on Linux, even if you've got the w32codecs installed. Hell, it's hard work even on a native Windows installation.

Under Windows XP, you would need to download a beta version of Windows Media Player 11 (not the final, it's patched against this exploit) and a custom application (called FairUse4WM) in order to strip the DRM and get an "exact" copy.

Alternatively, you can perform a lossy decode and recode of the media in Windows (I think it doesn't require a patched WMP, but the resulting quality will be low) using one of millions of those "WinAVI" programs or its derivatives.

Another option is to install a "virtual" sound card driver for Windows that's designed to save streamed audio - this is just a more sophisticated variation of the decode/recode applications.

---

### Post by famico666 on 2008-11-13
Hi psyke. 

I'm not trying to save it. I'm just trying to listen!

---

### Post by markbuntu on 2008-11-13
That site works for me. I was just listening to Frank Sinatra with the mplayer plugin. If you want to get all the codecs etc. get the

ubuntu-restricted-extras

package with synaptic. 

You can also get codecs from mediabuntu:

[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

---

### Post by famico666 on 2008-11-13
Oh thanks... Erm, when I try to install that, it tells me I have conflicting installations so I need to switch to Synaptics to resolve it the conflict. But I don't know how... I've installed Synaptics (it's ticked in the Add/Remove list, anyway) but I can't see how to use it...

I tried your two links - the first just says to install the same thing as above, and the othe says install the w32 stuff, which I think I already have.

So hopefully if i can just figure out Synaptics, I'll be away. I found [http://ubuntuforums.org/showthread.php?t=136611](http://ubuntuforums.org/showthread.php?t=136611) but I don't get what Thoffland is saying and the link aysiu gives doesn't work.

So... what next? Thanks guys!

---

### Post by famico666 on 2008-11-13
OK, found Synaptics in System > Admin... But I can't find ubuntu-restricted-extras in there. How do I install it?

Thanks.

---

### Post by famico666 on 2008-11-13
OK. seems that using the terminal (
sudo apt-get install ubuntu-restricted-extras) is working... we'll see...

---

### Post by famico666 on 2008-11-13
It didn't work...

I'll try restarting...

I saw some errors in the Terminal. Unfortunately, it seems that so much happened in the Terminal that a lot of the info scrolled off the top. This is what I managed to copy.


---------------------------------------------------------------------------
to the file name or packaging format.

--2008-11-14 01:26:01--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--2008-11-14 01:26:06--  [http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
Resolving prdownloads.sourceforge.net... 216.34.181.60
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://puzzle.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://puzzle.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) [following]
--2008-11-14 01:26:08--  [http://puzzle.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://puzzle.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving puzzle.dl.sourceforge.net... 195.141.111.5
Connecting to puzzle.dl.sourceforge.net|195.141.111.5|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198384 (194K) [application/octet-stream]
Saving to: `./andale32.exe'

100%[======================================>] 198,384     11.7K/s   in 2m 1s   

2008-11-14 01:29:06 (1.61 KB/s) - `./andale32.exe' saved [198384/198384]

--2008-11-14 01:29:06--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe)
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/arialb32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/arialb32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--2008-11-14 01:29:06--  [http://prdownloads.sourceforge.net/corefonts/arialb32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/arialb32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
Resolving prdownloads.sourceforge.net... 216.34.181.60
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://puzzle.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe](http://puzzle.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe) [following]
--2008-11-14 01:29:06--  [http://puzzle.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe](http://puzzle.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe)
Resolving puzzle.dl.sourceforge.net... 195.141.111.5
Connecting to puzzle.dl.sourceforge.net|195.141.111.5|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 168176 (164K) [application/octet-stream]
Saving to: `./arialb32.exe'

100%[======================================>] 168,176     89.4K/s   in 1.8s    

2008-11-14 01:29:41 (89.4 KB/s) - `./arialb32.exe' saved [168176/168176]

--2008-11-14 01:29:41--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe)
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--2008-11-14 01:29:42--  [http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
Resolving prdownloads.sourceforge.net... 216.34.181.60
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://superb-east.dl.sourceforge.net/sourceforge/corefonts/arial32.exe](http://superb-east.dl.sourceforge.net/sourceforge/corefonts/arial32.exe) [following]
--2008-11-14 01:29:42--  [http://superb-east.dl.sourceforge.net/sourceforge/corefonts/arial32.exe](http://superb-east.dl.sourceforge.net/sourceforge/corefonts/arial32.exe)
Resolving superb-east.dl.sourceforge.net... 209.160.66.130
Connecting to superb-east.dl.sourceforge.net|209.160.66.130|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=superb-east.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=superb-east.dl.sourceforge.net) [following]
--2008-11-14 01:29:43--  [http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=superb-east.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=superb-east.dl.sourceforge.net)
Reusing existing connection to prdownloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://superb-east.dl.sourceforge.net/sourceforge/corefonts/arial32.exe](http://superb-east.dl.sourceforge.net/sourceforge/corefonts/arial32.exe) [following]
--2008-11-14 01:29:43--  [http://superb-east.dl.sourceforge.net/sourceforge/corefonts/arial32.exe](http://superb-east.dl.sourceforge.net/sourceforge/corefonts/arial32.exe)
Connecting to superb-east.dl.sourceforge.net|209.160.66.130|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=superb-east.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=superb-east.dl.sourceforge.net) [following]
--2008-11-14 01:29:44--  [http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=superb-east.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=superb-east.dl.sourceforge.net)
Reusing existing connection to prdownloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://jaist.dl.sourceforge.net/sourceforge/corefonts/arial32.exe](http://jaist.dl.sourceforge.net/sourceforge/corefonts/arial32.exe) [following]
--2008-11-14 01:29:44--  [http://jaist.dl.sourceforge.net/sourceforge/corefonts/arial32.exe](http://jaist.dl.sourceforge.net/sourceforge/corefonts/arial32.exe)
Resolving jaist.dl.sourceforge.net... 150.65.7.130
Connecting to jaist.dl.sourceforge.net|150.65.7.130|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 554208 (541K) [application/octet-stream]
Saving to: `./arial32.exe'

100%[======================================>] 554,208     78.6K/s   in 7.2s    

2008-11-14 01:29:52 (75.4 KB/s) - `./arial32.exe' saved [554208/554208]

--2008-11-14 01:29:52--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/comic32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/comic32.exe)
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/comic32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/comic32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--2008-11-14 01:29:52--  [http://prdownloads.sourceforge.net/corefonts/comic32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/comic32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
Resolving prdownloads.sourceforge.net... 216.34.181.60
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://optusnet.dl.sourceforge.net/sourceforge/corefonts/comic32.exe](http://optusnet.dl.sourceforge.net/sourceforge/corefonts/comic32.exe) [following]
--2008-11-14 01:29:52--  [http://optusnet.dl.sourceforge.net/sourceforge/corefonts/comic32.exe](http://optusnet.dl.sourceforge.net/sourceforge/corefonts/comic32.exe)
Resolving optusnet.dl.sourceforge.net... 211.29.132.142
Connecting to optusnet.dl.sourceforge.net|211.29.132.142|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/comic32.exe?download&failedmirror=optusnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/comic32.exe?download&failedmirror=optusnet.dl.sourceforge.net) [following]
--2008-11-14 01:29:53--  [http://prdownloads.sourceforge.net/corefonts/comic32.exe?download&failedmirror=optusnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/comic32.exe?download&failedmirror=optusnet.dl.sourceforge.net)
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://heanet.dl.sourceforge.net/sourceforge/corefonts/comic32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/comic32.exe) [following]
--2008-11-14 01:29:54--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/comic32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/comic32.exe)
Resolving heanet.dl.sourceforge.net... 193.1.193.66
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 246008 (240K) [application/octet-stream]
Saving to: `./comic32.exe'

100%[======================================>] 246,008      142K/s   in 1.7s    

2008-11-14 01:29:56 (142 KB/s) - `./comic32.exe' saved [246008/246008]

--2008-11-14 01:29:56--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe)
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--2008-11-14 01:29:56--  [http://prdownloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
Resolving prdownloads.sourceforge.net... 216.34.181.60
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://optusnet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe](http://optusnet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe) [following]
--2008-11-14 01:29:56--  [http://optusnet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe](http://optusnet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe)
Resolving optusnet.dl.sourceforge.net... 211.29.132.142
Connecting to optusnet.dl.sourceforge.net|211.29.132.142|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=optusnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=optusnet.dl.sourceforge.net) [following]
--2008-11-14 01:29:57--  [http://prdownloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=optusnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=optusnet.dl.sourceforge.net)
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://nchc.dl.sourceforge.net/sourceforge/corefonts/courie32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/courie32.exe) [following]
--2008-11-14 01:29:58--  [http://nchc.dl.sourceforge.net/sourceforge/corefonts/courie32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/courie32.exe)
Resolving nchc.dl.sourceforge.net... 211.79.60.17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 646368 (631K) [application/x-msdownload]
Saving to: `./courie32.exe'

100%[======================================>] 646,368      148K/s   in 7.0s    

2008-11-14 01:30:06 (90.8 KB/s) - `./courie32.exe' saved [646368/646368]

--2008-11-14 01:30:06--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/georgi32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/georgi32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--2008-11-14 01:30:06--  [http://prdownloads.sourceforge.net/corefonts/georgi32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/georgi32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
Resolving prdownloads.sourceforge.net... 216.34.181.60
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://puzzle.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://puzzle.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe) [following]
--2008-11-14 01:30:06--  [http://puzzle.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://puzzle.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
Resolving puzzle.dl.sourceforge.net... 195.141.111.5
Connecting to puzzle.dl.sourceforge.net|195.141.111.5|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 392440 (383K) [application/octet-stream]
Saving to: `./georgi32.exe'

100%[======================================>] 392,440      146K/s   in 2.6s    

2008-11-14 01:30:35 (146 KB/s) - `./georgi32.exe' saved [392440/392440]

--2008-11-14 01:30:35--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe)
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--2008-11-14 01:30:35--  [http://prdownloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
Resolving prdownloads.sourceforge.net... 216.34.181.60
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://belnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe) [following]
--2008-11-14 01:30:35--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe)
Resolving belnet.dl.sourceforge.net... 193.190.198.97
Connecting to belnet.dl.sourceforge.net|193.190.198.97|:80... failed: Connection timed out.
Giving up.

--2008-11-14 01:30:40--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/impact32.exe)
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=mesh.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=mesh.dl.sourceforge.net) [following]
--2008-11-14 01:30:40--  [http://prdownloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=mesh.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=mesh.dl.sourceforge.net)
Resolving prdownloads.sourceforge.net... 216.34.181.60
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://mesh.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/impact32.exe) [following]
--2008-11-14 01:30:41--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/impact32.exe)
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=mesh.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=mesh.dl.sourceforge.net) [following]
--2008-11-14 01:30:41--  [http://prdownloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=mesh.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=mesh.dl.sourceforge.net)
Reusing existing connection to prdownloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe) [following]
--2008-11-14 01:30:41--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe)
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--2008-11-14 01:30:41--  [http://prdownloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://master.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://master.dl.sourceforge.net/sourceforge/corefonts/impact32.exe) [following]
--2008-11-14 01:30:42--  [http://master.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://master.dl.sourceforge.net/sourceforge/corefonts/impact32.exe)
Resolving master.dl.sourceforge.net... 216.34.181.56
Connecting to master.dl.sourceforge.net|216.34.181.56|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 173288 (169K) [application/octet-stream]
Saving to: `./impact32.exe'

100%[======================================>] 173,288      120K/s   in 1.4s    

2008-11-14 01:30:46 (120 KB/s) - `./impact32.exe' saved [173288/173288]

--2008-11-14 01:30:46--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/times32.exe)
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/times32.exe?download&failedmirror=mesh.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/times32.exe?download&failedmirror=mesh.dl.sourceforge.net) [following]
--2008-11-14 01:30:46--  [http://prdownloads.sourceforge.net/corefonts/times32.exe?download&failedmirror=mesh.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/times32.exe?download&failedmirror=mesh.dl.sourceforge.net)
Resolving prdownloads.sourceforge.net... 216.34.181.60
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://ufpr.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://ufpr.dl.sourceforge.net/sourceforge/corefonts/times32.exe) [following]
--2008-11-14 01:30:47--  [http://ufpr.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://ufpr.dl.sourceforge.net/sourceforge/corefonts/times32.exe)
Resolving ufpr.dl.sourceforge.net... 200.236.31.1, 200.17.202.1
Connecting to ufpr.dl.sourceforge.net|200.236.31.1|:80... failed: Connection timed out.
Connecting to ufpr.dl.sourceforge.net|200.17.202.1|:80... failed: Connection timed out.
Giving up.

--2008-11-14 01:30:57--  [http://dfn.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://dfn.dl.sourceforge.net/sourceforge/corefonts/times32.exe)
Resolving dfn.dl.sourceforge.net... 194.95.236.6
Connecting to dfn.dl.sourceforge.net|194.95.236.6|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/corefonts/times32.exe?download&failedmirror=dfn.dl.sourceforge.net](http://downloads.sourceforge.net/corefonts/times32.exe?download&failedmirror=dfn.dl.sourceforge.net) [following]
--2008-11-14 01:30:57--  [http://downloads.sourceforge.net/corefonts/times32.exe?download&failedmirror=dfn.dl.sourceforge.net](http://downloads.sourceforge.net/corefonts/times32.exe?download&failedmirror=dfn.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.60
Connecting to downloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://ufpr.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://ufpr.dl.sourceforge.net/sourceforge/corefonts/times32.exe) [following]
--2008-11-14 01:30:58--  [http://ufpr.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://ufpr.dl.sourceforge.net/sourceforge/corefonts/times32.exe)
Resolving ufpr.dl.sourceforge.net... 200.236.31.1, 200.17.202.1
Connecting to ufpr.dl.sourceforge.net|200.236.31.1|:80... failed: Connection timed out.
Connecting to ufpr.dl.sourceforge.net|200.17.202.1|:80... failed: Connection timed out.
Giving up.

--2008-11-14 01:31:08--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/times32.exe)
Resolving heanet.dl.sourceforge.net... 193.1.193.66
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 661728 (646K) [application/octet-stream]
Saving to: `./times32.exe'

100%[======================================>] 661,728      200K/s   in 3.2s    

2008-11-14 01:31:11 (200 KB/s) - `./times32.exe' saved [661728/661728]

--2008-11-14 01:31:11--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe)
Resolving heanet.dl.sourceforge.net... 193.1.193.66
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 357200 (349K) [application/octet-stream]
Saving to: `./trebuc32.exe'

100%[======================================>] 357,200      172K/s   in 2.0s    

2008-11-14 01:31:14 (172 KB/s) - `./trebuc32.exe' saved [357200/357200]

--2008-11-14 01:31:14--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe)
Resolving heanet.dl.sourceforge.net... 193.1.193.66
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 351992 (344K) [application/octet-stream]
Saving to: `./verdan32.exe'

100%[======================================>] 351,992      114K/s   in 3.0s    

2008-11-14 01:31:18 (114 KB/s) - `./verdan32.exe' saved [351992/351992]

--2008-11-14 01:31:18--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe)
Resolving heanet.dl.sourceforge.net... 193.1.193.66
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 185072 (181K) [application/octet-stream]
Saving to: `./webdin32.exe'

100%[======================================>] 185,072      170K/s   in 1.1s    

2008-11-14 01:31:19 (170 KB/s) - `./webdin32.exe' saved [185072/185072]

Extracting cabinet: andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
Extracting cabinet: arialb32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
Extracting cabinet: arial32.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
Extracting cabinet: comic32.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: courie32.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: georgi32.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: impact32.exe
  extracting fontinst.exe
  extracting Impact.TTF
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: times32.exe
  extracting fontinst.inf
  extracting Times.TTF
  extracting Timesbd.TTF
  extracting Timesbi.TTF
  extracting Timesi.TTF
  extracting FONTINST.EXE

All done, no errors.
Extracting cabinet: trebuc32.exe
  extracting FONTINST.EXE
  extracting trebuc.ttf
  extracting Trebucbd.ttf
  extracting trebucbi.ttf
  extracting trebucit.ttf
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: verdan32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting Verdanab.TTF
  extracting Verdanai.TTF
  extracting Verdanaz.TTF
  extracting Verdana.TTF

All done, no errors.
Extracting cabinet: webdin32.exe
  extracting fontinst.exe
  extracting Webdings.TTF
  extracting fontinst.inf
  extracting Licen.TXT

All done, no errors.
All fonts downloaded and installed.
Updating fontconfig cache for /usr/share/fonts/truetype/msttcorefonts
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for ZenHei-CNS, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for ZenHei, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.

Setting up ubuntu-restricted-extras (25) ...
Setting up unrar (1:3.8.2-1) ...

Setting up sun-java6-bin (6-10-0ubuntu2) ...

Setting up sun-java6-jre (6-10-0ubuntu2) ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'


Setting up sun-java6-plugin (6-10-0ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

---

### Post by famico666 on 2008-11-13
Nope. Still doesn't work. Ho hum.

---

### Post by markbuntu on 2008-11-13
> **famico666 said:**
> OK, found Synaptics in System > Admin... But I can't find ubuntu-restricted-extras in there. How do I install it?

Thanks.

You need to have the multiverse repository enabled in synaptic and then reload. If the connection times out, which happened to you, synaptic will pick it up again where it left off.

---

### Post by famico666 on 2008-11-14
Hi,

I went to Settings in Synaptic to enable the multiverse repository but it said it already was. This time I found the ubuntu-restricted-extras but it said it had already been installed. I chose to reinstall it. It did so (very quickly - too quickly?)

Tried the site again - still nothing.

I'll try to restart and see if that has any effect.

Thanks again for all your help.

---

### Post by canoemoose on 2008-11-14
You may have to choose the option to "mark for complete removal", apply, then find the package and choose "mark for installation" as if you hadn't installed in the first place.

This is because the original (corrupted) installation files were still on your system and were used to reinstall the package.  My trick deletes the files and causes new ones to be downloaded.

---

### Post by famico666 on 2008-11-14
Thanks. I'll try that now.

By the way, before I read your message I tried to close Synaptic and got this:

> W: Duplicate sources.list entry [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty/all Packages (/var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages)


Anyway, I'll try what you suggested.

---

### Post by famico666 on 2008-11-14
Tried all that... still nothing.

:(

---

### Post by canoemoose on 2008-11-14
> **famico666 said:**
> Tried all that... still nothing.

:(
Oh. :(
I just picked up on the synaptic bit, and don't know much about the rest.  You've got me hooked though so I'll have a look.

---

### Post by famico666 on 2008-11-14
Haha. Thanks.

Only one person has said he's got that site to work on Ubuntu. I'd like to know exactly what audio format is being used on that site so we could be sure of which codecs it needs.

---

### Post by canoemoose on 2008-11-15
> **famico666 said:**
> Haha. Thanks.

Only one person has said he's got that site to work on Ubuntu. I'd like to know exactly what audio format is being used on that site so we could be sure of which codecs it needs.
I can't get the site to work :(
I've tried to get it working but can't.

---

### Post by markbuntu on 2008-11-15
Did you follow the other links I gave you in my previous post and get the w32 codecs from mediabuntu?

You may need to install mplayer and the mplayer plugins. The mplayer plugin is what played it for me.

At the top of this forum is a guide to multimedia,  try that.

---

### Post by famico666 on 2008-11-15
Hi Mark,

I didn't use that link, but I did install those codecs,

It all went fine apart from this:
> W: Duplicate sources.list entry [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty/all Packages (/var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems


When I try to play the files on that page, mplayer doesn't come up - totem does. Right-clicking does offer me "Open with Movie Player" (is "Movie Player" the same as mplayer?") but that gives me "error - location not found".

I'm starting to lose patience with this... :( May have to wait until I meet a flesh and blood Linux user to sort this out for me!!

Of course, please continue with suggestions if you have any!

---

### Post by markbuntu on 2008-11-15
I am looking in firefox/preferences/applications at which formats the mplayer plugin is set to play. Here is the list:

AU file
FLI file
M3U file
MP4 file
MID file
MPEG video
MPGA file
OGG file
VIV file

All the other formats use other plugins. Most likely the stream is and AU, M3U, OGG, or MPGA. And no, Movie Player is not the same as mplayer. You should check in firefox/tools/add-ons/plugins that the mplayer plugin is there and then you can choose it in firefox/preferences/applications for those formats.

---

### Post by famico666 on 2008-11-16
I think I have found the problem. I have the mplayer plugin installed, but I don't have all of the formats in my list (unless they're listed differently). For me, mplayer is set to play:

3GPP
FLAC
Flash video
FLIC
MP3 audio
MP3 audio streamed
MPEG4 video
MPEG video
Ogg
Ogg multimedia
ULAW

I'm using FF3 if that is relevant.

---

### Post by markbuntu on 2008-11-16
OOPs, I was running Mandriva when I wrote that last post. Stand by while I switch back to Ubuntu and see what mplayer is doing there.


Ok, I am back in hardy, listening to Credence Clearwater from that site with the mplayer plugin on firefox 3.04 with the mplayer plug-in 3.50. The only content type that my mplayer plugin is set to in firefox/preferences/applications is 3 GPP multimedia so that must be it. It does not always work on the first try and only wants to play single songs and takes a little while to get going. The stream says it is wma.

This is the stream address for Derek and the Dominoes, I looked away.

[http://library.radio3net.ro/test-af2007681cb6492e9720db95b6b939d3-9219-c-p-t.wma](http://library.radio3net.ro/test-af2007681cb6492e9720db95b6b939d3-9219-c-p-t.wma)

---

### Post by famico666 on 2008-11-16
Hmm... I have FF 3.03 and mplayer 3.50. But it appears to try to use Totem for me for that site.

You're clicking on the link and then clicking on a single track, are you? I've been clicking on the red headphones on the main page. When I click on the link and click on a track, the window launches and it says "Transfering data from library..." but nothing happens.

When I click on that link you've pasted above, it says "Not a valid player!"

A couple of questions:

1) How is it 3GPP if it says the stream is wma? I've looked up 3GPP in wikipedia but I don't really get it.
2) Can I or should I change my wma setting to use mplayer? How can I do that? I don't know where my mplayer plugin is stored.
3) Why hasn't FF updated to 3.04 for me? I thought it was automatic. I installed this less than a week ago. That sounds like it's the only difference between your settings and mine.

Ho hum.  Thanks anyway.

---

### Post by zink23 on 2008-12-06
Hi there!

I've recently been trying out Ubuntu (booted from within Windows with Wubi) and one of the things I was missing was being able to play back albums from the radio3net.ro 1001 albums site (as it's something I've got fairly addicted to in recent times).

In trying to work out how I could get the site to work on Linux, I came across this thread. I followed all the steps (both 1 and 2) on the links provided by markubuntu and it does now work for me with Mplayer but only to play back individual tracks.

When I try to play back a full album, it accesses the site then fails at the getting playlist stage.

If I copy the link into the external Mplayer player:

[http://library.radio3net.ro/test-43c0206d3008e74d93a396e599d411ff-1699-c-a-t.asx](http://library.radio3net.ro/test-43c0206d3008e74d93a396e599d411ff-1699-c-a-t.asx)

I get the error:

Couldn't resolve name for AF_INET6: library.radio3net.ro

Perhaps this is because my Mplayer/Mplayer plugin is not set up right to handle .asx playlists? Or perhaps Mplayer just has problems with some asx playlists??

I've also seen on forums elsewhere that the above error is related to IPv6 support and that it can be solved by recompiling Mplayer without IPv6 support. But that sounds like a potential red herring to me.

My feeling is that the problem is site-side and the admins have just made it impossible to stream whole albums off there in any other player than WMP (to avoid the risk of people pulling the music industry's most prominent 1001 albums off there too easily - if that was possible I guess that part of the site would be shut down pretty promptly!!)

Still if anyone has any ideas on how you might get Mplayer to play back whole albums from the .asx link or on how to solve the above Mplayer error, I'd be very interested to know more (I tried looking for ways of automatically building full album playlists from the individual track links that I *can* play but of course the track links are randomized every time you start a new playback :-()

Looking forward to hearing from anyone who can help as it's a real shame to have to boot back into Windows just to be able to listen to a full album.

Oh and thanks to Markubuntu for at least getting me up and running for single track playback ;-)

---

