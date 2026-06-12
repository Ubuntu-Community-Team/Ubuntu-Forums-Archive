---
title: "Accessing mythfrontend control socket via netcat causes segfaults"
date: 2011-01-05
forum: Mythbuntu
---

### Post by newlinux on 2011-01-05
Does anyone use the mythfrontend control socket (telnet control) with netcat? I'm trying to write a script that in part sends some commands to the frontend via the control socket, but when I pipe or redirect a file to to netcat it often causes mythfrontend to to segfault with nothing indicating the segfault in the logs with verbosity turned up.

A command such as:

echo "jump playbackrecordings" | nc localhost 6546

Works sometimes but probably 1 out of every 5 times or so causes a segfault in mythfrontend. Redirecting in a file with the command does the same thing.

Oddly, if I just connect to the frontend socket straight via netcat and type in commands it never segfaults. only when I redirect input to it (which I need to do for a script).

 Any ideas on what's causing this segfault? Or is there another way to send commands to the frontend via a script?

---

### Post by ian dobson on 2011-01-05
Hi,

Why not a little perl script. Something like:-

```

#!/usr/bin/perl
use strict;
use IO::Socket::INET;
my $sock = new IO::Socket::INET (
    PeerAddr => '192.168.0.10',
    PeerPort => 1234,
    Proto => 'tcp',
);

my $Text="whatever you want to send";
    $sock->autoflush(1);
    $sock->send($Text);
    close ( $sock );
exit;

```

Note it's a quick and dirty hack that I can't test at the moment, but it should work.

Regards
Ian Dobson

---

### Post by newlinux on 2011-01-05
> **ian dobson said:**
> Hi,

Why not a little perl script. Something like:-

```

#!/usr/bin/perl
use strict;
use IO::Socket::INET;
my $sock = new IO::Socket::INET (
    PeerAddr => '192.168.0.10',
    PeerPort => 1234,
    Proto => 'tcp',
);

my $Text="whatever you want to send";
    $sock->autoflush(1);
    $sock->send($Text);
    close ( $sock );
exit;

```

Note it's a quick and dirty hack that I can't test at the moment, but it should work.

Regards
Ian Dobson

Thanks, however this perl script method works but still crashes the frontend as often as the netcat command. I need to figure out why it is crashing. No useful information in the logs as at all. Not sure why an interactive session via netcat works but anything that sends a command and closes the connection seems to intermittently crash the frontend.

---

### Post by azmyth on 2011-01-05
The control socket doesn't like piped commands. I tried doing this and had the same results with segfaults. Not sure what you want to do but I ended up using irwatch.pl as I wanted to save position on power off (FE shutting down) if a show was being watched.

[http://www.ronfrazier.net/mythtv/0.22/index.html](http://www.ronfrazier.net/mythtv/0.22/index.html)

---

### Post by ian dobson on 2011-01-05
Hi,

What happens if you add a short delay to nc (-i option), somrthing like:-

nc localhost 6546 -i 1 <<EOS
key f6
quit
EOS

Regards
Ian Dobson

---

### Post by newlinux on 2011-01-05
> **azmyth said:**
> The control socket doesn't like piped commands. I tried doing this and had the same results with segfaults. Not sure what you want to do but I ended up using irwatch.pl as I wanted to save position on power off (FE shutting down) if a show was being watched.

[http://www.ronfrazier.net/mythtv/0.22/index.html](http://www.ronfrazier.net/mythtv/0.22/index.html)


I'll look into that - thanks.
> **ian dobson said:**
> Hi,

What happens if you add a short delay to nc (-i option), somrthing like:-

nc localhost 6546 -i 1 <<EOS
key f6
quit
EOS

Regards
Ian Dobson

I tried using -i with pipes and redirects with the same results and with using EOS. What I have found is that the sending it a jump command makes it crash fairly consistently, but sending a key seems to be stable (done it about 20 times with no problem). Maybe I'll just map a key to what I want to do and go with that if it holds up.

---

### Post by chaumurky on 2011-04-01
Wow, this is the only thread I can find about this issue. It's interesting that mythfrontend appears to react to the command but segfaults later on. Running mythfrontend -v doesn't seem to reveal anything.

---

### Post by ceejay on 2011-08-15
A slightly late reply but I've just been travelling this way myself!

There is a known bug in MythTV - [http://code.mythtv.org/trac/ticket/9545](http://code.mythtv.org/trac/ticket/9545)

I hit this when I was trying to use Network Control to stop any playing before killing mythtv (as to do otherwise was causing XBMC to fail when I started it up afterwards!).

FWIW, ian dobson's proposal of using "nc ... -i 1" worked well for me. 

```

#!/bin/bash
nc localhost 6546 -i 1 << EOF
jump mainmenu
exit
EOF

```

Ceejay

---

