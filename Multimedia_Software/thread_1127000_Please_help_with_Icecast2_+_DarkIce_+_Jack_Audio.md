---
title: "Please help with Icecast2 + DarkIce + Jack Audio"
date: 2009-04-16
forum: Multimedia Software
---

### Post by kaprodemono on 2009-04-16
**My Questions:**[LIST]
[*]How do I connect the microphone input to DarkIce using Jack Audio through the command line?
[*]When I run DarkIce, I get the error: "DarkIce: LameLibEncoder.cpp:75: lame lib opening underlying sink error [0]". How do I fix this?
[/LIST]

**My Installation Steps:**
> Step 1: Install Ubuntu Server 8.10
[LIST=1]
[*]Full user name: admin
[*]User name: admin
[*]Password: somepassword
[*]leave http proxy information blank
[*]Upgrade management: Install security updates automatically
[*]Install no extra software
[/LIST]

Step 2: Install kubuntu-desktop Package
[LIST=1]
[*]run &#8220;sudo nano /etc/apt/sources.list&#8221;
[*]Add &#8220;deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid universe multiverse&#8221;
[*]Add &#8220;deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid universe multiverse&#8221;
[*]run &#8220;sudo aptitude update&#8221;
[*]run &#8220;sudo aptitude install kubuntu-desktop&#8221;
[*]run &#8220;startx&#8221;
[/LIST]

Step 3: Install Icecast2
[LIST=1]
[*]open the terminal
[*]run &#8220;sudo apt-get install icecast2&#8221; (installed 2.3.2-2)
[/LIST]

Step 4: Configure Icecast2
[LIST=1]
[*]run &#8220;sudo nano /etc/icecast2/icecast.xml&#8221;
[LIST=1][*]Edit the file to match the sample icecast configuration[/LIST]
[*]run &#8220;sudo nano /etc/default/icecast2&#8221;
[*]change &#8220;ENABLE=false&#8221; to &#8220;ENABLE=true&#8221;
[/LIST]

Step 5: Install Lame and Lame libs (for darkice lame support)
[LIST=1]
[*]run &#8220;sudo apt-get install lame&#8221; (installed 3.98-0)
[*]run &#8220;sudo apt-get install libmp3lame0&#8221; (installed 3.98-0)
[*]run &#8220;sudo apt-get install libmp3lame-dev&#8221; (installed 3.98-0)
[/LIST]

Step 6: Install Jack Audio and Jack Audio libs (for darkice jack support)
[LIST=1]
[*]run &#8220;sudo apt-get install jackd&#8221; (installed 0.109.2-3ubuntu1)
[*]run &#8220;sudo apt-get install libjack0&#8221; (installed 0.109.2-3ubuntu1)
[*]run &#8220;sudo apt-get install libjack-dev&#8221; (installed 0.109.2-3ubuntu1)
[/LIST]

Step 7: Install ALSA libs (darkice won't compile without them)
[LIST=1]
[*]run &#8220;sudo apt-get install libalsa-ocaml&#8221;
[*]run &#8220;sudo apt-get install libalsa-ocaml-dev&#8221;
[/LIST]

Step 8: Install g++
[LIST=1]
[*]run &#8220;sudo apt-get install g++&#8221;
[/LIST]

Step 9: Install DarkIce (must be built from source because the intrepid package does not come with lame support)
[LIST=1]
[*]run &#8220;cd /home/admin/Desktop&#8221;
[*]run &#8220;wget [http://darkice.tyrell.hu/dist/0.19/darkice-0.19.tar.gz&#8221;](http://darkice.tyrell.hu/dist/0.19/darkice-0.19.tar.gz&#8221;)
[*]run &#8220;tar -xvvzf darkice-0.19.tar.gz&#8221;
[*]run &#8220;cd darkice-0.19&#8221;
[*]run &#8220;sudo nano src/JackDspSource.cpp&#8221;
[LIST=1][*]insert &#8220;#include "limits.h"&#8221; after &#8220;#include "AudioSource.h"&#8221; (required to get DarkIce to compile)[/LIST]
[*]run &#8220;./configure --with-lame --without-vorbis --without-faac --without-twolame --with-alsa &#8211; with-jack&#8221;
[*]run &#8220;sudo make&#8221;
[*]run &#8220;sudo make install&#8221;
[/LIST]

Step 10: Configure DarkIce
[LIST=1]
[*]run &#8220;sudo nano /etc/darkice.cfg&#8221;
[LIST=1][*]Edit the file to match the sample darkice configuration[/LIST]
[/LIST]

Step 11: Start Jack server
[LIST=1]
[*]run &#8220;jackd -d alsa&#8221;
[/LIST]

Step 12: Start Icecast2
[LIST=1]
[*]run &#8220;sudo /etc/init.d/icecast2 start&#8221;
[/LIST]

Step 13: Start DarkIce
[LIST=1]
[*]run &#8220;darkice&#8221;
[/LIST]


**Icecast2 Configuration:**
```
<icecast>
    <limits>
        <clients>5</clients>
        <sources>1</sources>
        <threadpool>5</threadpool>
        <queue-size>524288</queue-size>
        <client-timeout>30</client-timeout>
        <header-timeout>15</header-timeout>
        <source-timeout>10</source-timeout>
        <burst-on-connect>1</burst-on-connect>
        <burst-size>65536</burst-size>
    </limits>

    <authentication>
        <source-password>apass</source-password>
        <relay-password>anotherpass</relay-password>
        <admin-user>admin</admin-user>
        <admin-password>adminpass</admin-password>
    </authentication>

    <hostname>localhost</hostname>

    <listen-socket>
        <port>8000</port>
    </listen-socket>

    <fileserve>1</fileserve>

    <paths>
        <basedir>/usr/share/icecast2</basedir>
        <logdir>/var/log/icecast2</logdir>
        <webroot>/usr/share/icecast2/web</webroot>
        <adminroot>/usr/share/icecast2/admin</adminroot>
        <alias source="/" dest="status.xsl" />
    </paths>

    <logging>
        <accesslog>access.log</accesslog>
        <errorlog>error.log</errorlog>
        <loglevel>3</loglevel>
        <logsize>10000</logsize>
    </logging>

    <security>
        <chroot>0</chroot>
    </security>
</icecast>
```

**DarkIce Configuration:**
```
[general]
duration      = 0
bufferSecs    = 5

[input]
device        = jack
sampleRate    = 44100
bitsPerSample = 16
channel       = 2

[icecast2-0]
bitrateMode   = cbr
format        = mp3
bitrate       = 128
server        = localhost
port          = 8000
password      = apass
mountPoint    = test
name          = A Test Stream
description   = A test of darkice and icecast 2
url           = http://somewebsiteorwhatever.com
genre         = test
public        = no
```

---

### Post by londondeveloper on 2010-10-20
We seem to be having a similar number of issues with Icecast2 and DarkIce with 10.10. All seems configured properly but of course there is now no /dev/dsp to hook into. We've tried using Alsamixer to set up a default input stream and thus have

```
device = default
```

Alternatively I've set up and run jackd. On both, starting Darkice with

```
darkice -c darkice.cfg
```

always returns with something like

```


DarkIce 0.20.1 live audio streamer, http://darkice.tyrell.hu/
Copyright (c) 2000-2007, Tyrell Hungary, http://tyrell.hu/

Using config file: /usr/share/streaming/darkice.cfg
Using ALSA DSP input device: djack
DarkIce: Util.cpp:263: number conversion error [0]

```

I've not managed to get my "best friend" (ie Google) to tell me an answer to what is causing this number conversion error.

Any ideas anyone? It would really help to have some consolidated instructions on how to get live audio streaming up and running but the fragmented nature of Linux and the vast range of audio hardware just seems to cause confusion.

---

### Post by JackandJohn on 2011-03-29
.

---

### Post by spookybathtub on 2011-07-31
I would also like to know the answer to your first question, kaprodemono.
From what I understand, there are only 2 options for jack in the darkice config file:  You can call the device 'jack' and then patch it manually in JackPilot, or you can call it 'jack_auto' to have it automatically patch the first input device.  I haven't found any documentation explaining how to specify an input.  But the ChangeLog says that feature was implemented way back in version 0.19.  See here: [http://darkice.org/ChangeLog](http://darkice.org/ChangeLog)
Perhaps this may be of help: [http://www.lecentre.net/blog/archives/112](http://www.lecentre.net/blog/archives/112)

Regarding your second question, I think you may have configured darkice with the wrong path for lame.  I noticed that it expects the lame libraries to be in /usr/lib, but the lame install puts them in /usr/local/lib by default.  Try ./configure, make, make install again for darkice, but specifiy --with-lame-prefix=/usr/local.

---

